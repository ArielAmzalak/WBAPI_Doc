![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fpayments-api%2Fpayments-br%2Forders%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)[Orders](/docs/whatsapp/cloud-api/payments-api/payments-br/orders)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)

  + [Orders](/docs/whatsapp/cloud-api/payments-api/payments-br/orders)
  + [Pix](/docs/whatsapp/cloud-api/payments-api/payments-br/offsite-pix)
  + [Payment Links](/docs/whatsapp/cloud-api/payments-api/payments-br/payment-links)
  + [Boleto](/docs/whatsapp/cloud-api/payments-api/payments-br/boleto)
  + [One Click Payments](/docs/whatsapp/cloud-api/payments-api/payments-br/one-click-payments)
  + [Order Details Template](/docs/whatsapp/cloud-api/payments-api/payments-br/orderdetailstemplate)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Orders](#orders)

[Sending order messages](#sending-order-messages)

[Order details example](#order-details-example)

[Order status example](#order-status-example)

[Message response](#message-response)

[Full API Reference](#full-api-reference)

[Order Details](#order-details)

[Order Status](#order-status)

[Errors and Statuses](#errors-and-statuses)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Orders

Payments API introduces two new types of [interactive messages](/docs/whatsapp/cloud-api/guides/send-messages#interactive-messages): `order_details` and `order_status`. They are the entrypoint to collect payment in WhatsApp.

1. `order_details` messages are sent to create an order in the buyer's WhatsApp client app. This message includes a list of the items being purchased, any fees being charged, and the payment settings used to collect payment. The payment settings will vary depending on the integration type ([Pix](/docs/whatsapp/cloud-api/payments-api/payments-br/offsite-pix), [payment links](/docs/whatsapp/cloud-api/payments-api/payments-br/payment-links), [Boleto](/docs/whatsapp/cloud-api/payments-api/payments-br/boleto)).
2. `order_status` messages are sent when businesses update the order status either based on the WhatsApp payment status change notification or based on their internal processes.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=634034961253028&version=1763148365)

Orders start in `pending` status. When the merchant has fully fulfilled the order and the buyer should not expect any further updates, it must be marked as `completed`.

## Sending order messages

Both message types contain the same 4 main components of an interactive message: *header*, *body*, *footer*, and *action*. The parameters in the *action* component will vary based on the message type.

Once the interactive message object is assembled, make a POST call to the [messages endpoint](/docs/whatsapp/cloud-api/reference/messages#messages). Remember to set the type to `interactive`.

### Order details example

```
{
 "recipient_type": "individual",
 "to": "[recipient-wa-id]",
 "type": "interactive",
 "interactive": {
   "type": "order_details",
   "body": {
     "text": "Your message content"
   },
   "action": {
     "name": "review_and_pay",
     "parameters": {
       "reference_id": "unique-reference-id",
       "type": "digital-goods",
       "payment_type": "br",
       "payment_settings": [
         {
           "type": "payment_link",
           "payment_link": {
             "uri": "https://my-payment-link-url"
           }
         }
       ],
       "currency": "BRL",
       "total_amount": {
         "value": 50000,
         "offset": 100
       },
       "order": {
         "status": "pending",
         "tax": {
           "value": 0,
           "offset": 100,
           "description": "optional text"
           },
         "items": [
           {
             "retailer_id": "1234567",
             "name": "Cake",
             "amount": {
               "value": 50000,
               "offset": 100
             },
             "quantity": 1
           }
         ],
         "subtotal": {
           "value": 50000,
           "offset": 100
         }
       }
     }
   }
 }
}
```

### Order status example

```
{
  "recipient_type": "individual",
  "to": "whatsapp-id",
  "type": "interactive",
  "interactive": {
    "type": "order_status",
    "body": {
      "text": "your-mandatory-text-body-content"
    },
    "footer": {
      "text": "your-optional-text-footer-content"
    },
    "action": {
      "name": "review_order",
      "parameters": {
        "reference_id": "unique-reference-id",
        "order": {
          "status": "processing"
        }
        "payment": {
          "status": "captured",
          "timestamp": 1722445231
        }
      }
    }
  }
}
```

### Message response

For either type, if your message is sent successfully, you will get the following response:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "[PHONE_NUMBER_ID]",
      "wa_id": "[PHONE-NUMBER_ID]"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDUwNzY1MjAVAgARGBI5QTNDQTVCM0Q0Q0Q2RTY3RTcA"
    }
  ]
}
```

For all errors that can be returned and guidance on how to handle them, see [Cloud API Errors Codes](/docs/whatsapp/cloud-api/support/error-codes/).

## Full API Reference

### Order Details

To send an order\_details message, businesses must assemble an interactive object of type order\_details with the following components:

#### Interactive Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| type | Required | String | Must be `order_details`. |
| header | Optional | Object | Thumbnail image for order details message. It has the following fields:   * `type`: Must be `image`. * `image`: See [Image Object](#imageobject).   If the header is not present, the API finds the first product with an image and uses that for the thumbnail image. |
| body | Required | Object | An object with the body of the message. The object contains the following field:   * `text` string: The content of the message. Emojis and markdown are supported. Maximum length is 1024 characters. |
| footer | Optional | Object | An object with the footer of the message. The object contains the following field:   * `text` string: **Required** if footer is present. The footer content. Emojis, markdown, and links are supported. Maximum length is 60 characters. |
| action | Required | Action Object | See [Action Object](#actionobject) below. |

#### Image Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| link | Required | String | Url of the image. |
| provider | Optional | String | Name of the url provider. |

#### Action Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| name | Required | String | Must be `review_and_pay`. |
| parameters | Required | Parameters Object | See [Parameters Object](#paramsobject). |

#### Parameters Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| reference\_id | Required | String | Unique identifier for the order or invoice provided by the business. This cannot be an empty string and can only contain English letters, numbers, underscores, dashes, or dots, and should not exceed 60 characters.  The reference\_id must be unique for each order\_details message for the same business. If the partner would like to send multiple order\_details messages for the same order, invoice, etc. it is recommended to include a sequence number in the reference\_id to ensure reference\_id uniqueness. |
| type | Required | String | Must be one of `digital-goods` or `physical-goods`. |
| payment\_type | Required | String | Must be `br`. |
| payment\_settings | Optional | [Payment Settings Object](#paymentsettingsobject) | List of payment related configuration objects. |
| currency | Required | String | ISO 4217 currency code for the order. Must be `BRL` (Brazilian Real). |
| total\_amount | Required | Amount Object | See [Amount Object](#amountobject).  `total_amount.value` must be equal to `order.subtotal.value` + `order.tax.value` + `order.shipping.value` - `order.discount.value` |
| order | Required | Order Object | See [Order Object](#orderobject). |

#### Payment Settings

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| `type` | Required | String | One of `pix_dynamic_code`, `payment_link`, `boleto`. |
| One of the following objects: `pix_dynamic_code`, `payment_link`, `boleto`. | Required | Object | Payment instructions which will be displayed to buyers during the checkout process. |

#### Order Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| status | Required | String | Status of the order. Only supported value here is `pending`. |
| catalog\_id | Optional | String | Unique identifier of the Facebook catalog being used by the business. |
| expiration | Optional | Expiration Object | Expiration for that order. The CTA for payment will be disabled after expiry on the user end. See [Expiration Object](#expirationobject). |
| items | Required | List of Item Objects | List must have at least one item. See [Item Object](#itemobject). |
| subtotal | Required | Amount Object | See [Amount Object](#amountobject).  The value **must be equal** to sum of (`item.amount.value` or `item.sale_amount.value`) \* `item.quantity`.  The following fields are part of the `subtotal` object:  `offset` string   * **Required.** Must be `100` for `BRL`.   `value` string   * **Required.** Positive integer representing the amount value multiplied by offset. For example, S$12.34. has value 1234 |
| tax | Required | Amount With Description Object | The tax information for this order. Even though the object is required, the amount can be zero. When zero is used, the tax line is not rendered in the client. See [Amount With Description Object](#amountdescriptionobject). |
| shipping | Optional | Amount With Description Object | See [Amount Object](#amountdescriptionobject). |
| discount | Optional | Discount Object | The discount for the order. See [Discount object](#discountobject). |

#### Expiration Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| timestamp | Required | String | UTC time in seconds. Minimum threshold is 300 seconds. |
| description | Required | String | Text explanation for when the order will expire. Max character limit is 120 characters. |

#### Item Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| retailer\_id | Required | String | Content ID for an item in the order from your catalog. |
| name | Required | String | The item’s name to be displayed to the user. Cannot exceed 60 characters. |
| amount | Required | Amount Object | The price per item. See [Amount Object](#amountobject). |
| quantity | Required | Integer | Number of items in this order. |
| sale\_amount | Optional | Amount Object | The discounted price per item. This should be less than the original amount. If included, this field is used to calculate the subtotal amount. See [Amount Object](#amountobject). |

#### Discount Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| value | Required | Integer | Positive integer representing the amount value multiplied by offset. For example, 12.34 BRL has value 1234. |
| offset | Required | Integer | Must be `100` for `BRL`. |
| description | Optional | String | Max character limit is 60 characters. |
| discount\_program\_name | Optional | String | Text used for defining incentivised orders. If order is incentivised, the merchant needs to define this information. Max character limit is 60 characters. |

#### Amount Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| value | Required | Integer | Positive integer representing the amount value multiplied by offset. For example, 12.34 BRL has value 1234. |
| offset | Required | Integer | Must be `100` for `BRL`. |

#### Amount Object (With Description)

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| value | Required | Integer | Positive integer representing the amount value multiplied by offset. For example, 12.34 BRL has value 1234. |
| offset | Required | Integer | Must be `100` for `BRL`. |
| description | Optional | String | Max character limit is 60 characters. |

### Order Status

To send an order\_status message, businesses must assemble an interactive object of type order\_details with the following components:

#### Interactive Object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| type | Required | String | Must be `order_status`. |
| header | Optional | Object | Optional object for the message's header for the message. |
| body | Required | Object | An object with the body of the message. The object contains the following field:   * `text` string: The content of the message. Emojis and markdown are supported. Maximum length is 1024 characters. |
| footer | Optional | Object | An object with the footer of the message. The object contains the following field:   * `text` string: **Required** if footer is present. The footer content. Emojis, markdown, and links are supported. Maximum length is 60 characters. |
| action | Required | Action Object | See [Action Object](#statusactionobject) below. |

#### Action Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| name | Required | String | Must be `review_order`. |
| parameters | Required | Parameters Object | See [Parameters Object](#statusparamsobject). |

#### Parameters Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| reference\_id | Required | String | The unique ID provided in the `order_details` message. |
| order | Required | Order Object | See [Order Object](#statusorderobject). |
| payment | Optional | Payment Object | See [Payment Object](#statuspaymentobject). |

#### Order Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| status | Required | String | The new order status. [See supported order status](#orderstatussupported). |
| description | Optional | String | Optional text for sharing status related information in order-details page. Could be useful while sending cancellation. Length should not exceed 120 characters. |

#### Payment Object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| status | Required | String | The new payment status. [See supported payment status](#paymentstatussupported). |
| timestamp | Optional | Integer | Optional epoch timestamp in seconds |

#### Supported Order Status

Currently we support the following order status values:

| Value | Description |
| --- | --- |
| `pending` | Order is pending / not processed yet. |
| `processing` | Merchant/partner is fulfilling the order, performing service, etc. |
| `partially-shipped` | Part of the products in order have been shipped by the merchant. |
| `shipped` | All the products in order have been shipped by the merchant. |
| `completed` | The order is completed and no further action is expected from the user or the partner/merchant. |
| `canceled` | The partner/merchant would like to cancel the order\_details message for the order/invoice. The status update will fail if there is already a successful or pending payment for this order\_details message. |

#### Supported Payment Status

Currently we support the following payment status values:

| Value | Description |
| --- | --- |
| `pending` | Payment is pending. |
| `captured` | Payment was successfully captured. Receiving this payment status will update the order bubble to include the "paid" label (with green checkmark). |
| `failed` | Payment failed. |

## Errors and Statuses

These are the relevant errors for the WhatsApp Payments API:

| Error Code | Description |
| --- | --- |
| `2040 - Message is not supported` | The message you are trying to send cannot be received by this user |
| `2046 - Order status invalid transition` | The order status cannot be updated from the existing value to the new one |
| `2047 - Order cancellation failure` | The order could not be cancelled |

For a comprehensive list with detailed descriptions of error codes and HTTP status codes, please refer to these our [Error Codes](/docs/whatsapp/cloud-api/support/error-codes) document.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Orders](#orders)

[Sending order messages](#sending-order-messages)

[Order details example](#order-details-example)

[Order status example](#order-status-example)

[Message response](#message-response)

[Full API Reference](#full-api-reference)

[Order Details](#order-details)

[Order Status](#order-status)

[Errors and Statuses](#errors-and-statuses)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ewqf8Bf0tnvqV6EeECFWwA&oh=00_AfiyupasVGspQzWZzTo9wFQ01BoJFZfZdEeaNGeL12_4Tg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ewqf8Bf0tnvqV6EeECFWwA&oh=00_AfjiHAOv8cB_JBiKA_zODzOf3y9r9jxtibt4O9kW2Htn3g&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ewqf8Bf0tnvqV6EeECFWwA&oh=00_AfhXWKxAc3o6eD2rzu4Zl4r2X1cnrNOK0gStfywSbSYswg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ewqf8Bf0tnvqV6EeECFWwA&oh=00_AfhVmsH3g7SBi1QxMDD9nhCjlOAUTrdelNrWYWUeXnh70w&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ewqf8Bf0tnvqV6EeECFWwA&oh=00_Afho2-jSNXlg1lPtaZy71LEctoQvuk7TUm0tFDdXil5Fyw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0tOh6sKs8G-NkQtTgFPluxcv70ytDYRVGNufXMRiZlSqFzGbJpI4wn1ucUnqPW43sW1Uxr88rVODhKuUOM8nm8mBjJtCAzOutdPSNmzJ-FmOFFil1_TpNZsbEzJ-hgENAvnMYYw5mt5owDG4iUQg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)