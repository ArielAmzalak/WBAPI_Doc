![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Faddress-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Address](/docs/whatsapp/cloud-api/messages/address-messages)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)

  + [Address](/docs/whatsapp/cloud-api/messages/address-messages)
  + [Áudio](/docs/whatsapp/cloud-api/messages/audio-messages)
  + [Contacts](/docs/whatsapp/cloud-api/messages/contacts-messages)
  + [Document](/docs/whatsapp/cloud-api/messages/document-messages)
  + [Image](/docs/whatsapp/cloud-api/messages/image-messages)
  + [Interactive Call-To-Action URL](/docs/whatsapp/cloud-api/messages/interactive-cta-url-messages)
  + [Interactive List](/docs/whatsapp/cloud-api/messages/interactive-list-messages)
  + [Interactive product carousel](/docs/whatsapp/cloud-api/messages/interactive-product-carousel-messages)
  + [Interactive media carousel](/docs/whatsapp/cloud-api/messages/interactive-media-carousel-messages)
  + [Interactive Reply Buttons](/docs/whatsapp/cloud-api/messages/interactive-reply-buttons-messages)
  + [Location](/docs/whatsapp/cloud-api/messages/location-messages)
  + [Solicitação de localização](/docs/whatsapp/cloud-api/guides/send-messages/location-request-messages)
  + [Reação](/docs/whatsapp/cloud-api/messages/reaction-messages)
  + [Sticker](/docs/whatsapp/cloud-api/messages/sticker-messages)
  + [Modelo](/docs/whatsapp/cloud-api/guides/send-message-templates)
  + [Text](/docs/whatsapp/cloud-api/messages/text-messages)
  + [Video](/docs/whatsapp/cloud-api/messages/video-messages)
  + [Confirmações de leitura](/docs/whatsapp/cloud-api/guides/mark-message-as-read)
  + [Contextual replies](/docs/whatsapp/cloud-api/guides/send-messages/contextual-replies)
  + [Typing indicators](/docs/whatsapp/cloud-api/typing-indicators)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Address Messages](#address-messages)

[Sample API call](#sample-api-call)

[Error Handling](#error-handling)

[Address Message Steps](#address-message-steps)

[Additional Action Parameters](#additional-action-parameters)

[Send Address Message to a User](#send-address-message-to-a-user)

[Check Your Response](#response)

[Send an Address Message with Validation Errors](#send-an-address-message-with-validation-errors)

[Receive Notifications for Address Submissions](#receive-notifications-for-address-submissions)

[Feature Not Supported](#feature-not-supported)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Address Messages

This feature is only available for businesses based in India and their India customers.

Address messages give your users a simpler way to share the shipping address with the business on WhatsApp.

Address messages are interactive messages that contain the 4 main parts: `header`, `body`, `footer`, and `action`. Inside the action component business specifies the name “address\_message” and relevant parameters.

Below table outlines the fields that are supported by the address message.

| Field Name | Display Label | Input Type | Supported Countries | Limitations |
| --- | --- | --- | --- | --- |
| `name` | Name | text | India | None |
| `phone_number` | Phone Number | tel | India | Valid phone numbers only |
| `in_pin_code` | Pin Code | text | India | Max length: 6 |
| `house_number` | Flat/House Number | text | India | None |
| `floor_number` | Floor Number | text | India | None |
| `tower_number` | Tower Number | text | India | None |
| `building_name` | Building/Apartment Name | text | India | None |
| `address` | Address | text | India | None |
| `landmark_area` | Landmark/Area | text | India | None |
| `city` | City | text | India | None |
| `state` | State | text | India | None |

## Sample API call

This is a sample API call for the address message. The `country` attribute is a mandatory field in the action parameters. If it is not included, there will be a validation error.

```
curl -X  POST \
'https://graph.facebook.com/<API_VERSION>/<FROM_PHONE_NUMBER_ID>/messages' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<PHONE_NUMBER>",
  "type": "interactive",
  "interactive": {
    "type": "address_message",
    "body": {
      "text": "Thanks for your order! Tell us what address you’d like this order delivered to."
    },
    "action": {
      "name": "address_message",
      "parameters": {
        "country": "<COUNTRY_ISO_CODE>"
      }
    }
  }
}'
```

## Error Handling

If the area code of the phone number for the given country is not correct, businesses will be unable to request the address message from the recipient. For example, businesses will be unable to request an address message from a recipient that has the country as “India” but has a phone number with an area code of "65".

Once the address message is sent, the business waits for the user to fill in the address and send it back. The user entered address is shared through the [webhook](/docs/whatsapp/cloud-api/guides/set-up-webhooks) registered in the [setup process](/docs/whatsapp/cloud-api/guides/set-up-webhooks).

## Address Message Steps

The steps involved in an Address Message are the following:

1. Business sends an address message with the action name `address_message` to the user
2. User interacts with the message by clicking on the CTA, which brings up an Address Message screen. The user fills out their address and submits the form
3. After the address message form is submitted by the user, the partner receives a webhook notification, which contains the details of the address submitted by the user

**Sample India Address Message**

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1030635057904903&version=1762569937)![](https://lookaside.fbsbx.com/elementpath/media/?media_id=947149619943058&version=1762569937)![](https://lookaside.fbsbx.com/elementpath/media/?media_id=207793345356649&version=1762569937)![](https://lookaside.fbsbx.com/elementpath/media/?media_id=930527574813449&version=1762569937)

The following sequence diagram shows a typical integration flow for an address message.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1404215443696882&version=1743456538)

## Additional Action Parameters

The business can pass additional attributes such as `values`, `validation_errors`, or `saved_addresses` as part of the interactive action parameters. You can find information on each of their usage below.

| Action Parameter | Usage |
| --- | --- |
| `values` | Businesses prefill this for address fields (eg. prefilling the city address field with “India”) |
| `saved_addresses` | For businesses, they can pass in saved addresses previously associated with the user.    For users, they are presented with the option to choose the saved address instead of manually filling it in |
| `validation_errors` | Businesses can throw errors in the address fields and WhatsApp will prevent the user from submitting the address until the issue(s) are/is resolved. |

### Send Address Message to a User

Make a `POST` call to `/<PHONE_NUMBER_ID/messages` using the WhatsApp API to send an end-to-end encrypted address message to the user:

```
curl -X  POST \
'https://graph.facebook.com/<API_VERSION>/<FROM_PHONE_NUMBER_ID>/messages' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<PHONE_NUMBER>",
  "type": "interactive",
  "interactive": {
    "type": "address_message",
    "body": {
      "text": "Thanks for your order! Tell us what address you’d like this order delivered to."
    },
    "action": {
      "name": "address_message",
      "parameters": "JSON Payload"
    }
  }
}'
```

To send an address message without any saved addresses, WhatsApp will prompt the user or business with an address form to enter a new address.

```
curl -X  POST \
'https://graph.facebook.com/<API_VERSION>/<FROM_PHONE_NUMBER_ID>/messages' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+91xxxxxxxxxx",
  "type": "interactive",
  "interactive": {
    "type": "address_message",
    "body": {
      "text": "Thanks for your order! Tell us what address you’d like this order delivered to."
    },
    "action": {
      "name": "address_message",
      "parameters": {
        "country": "IN",
        "values": {
          "name": "<CUSTOMER_NAME>",
          "phone_number": "+91xxxxxxxxxx"
        }
      }
    }
  }
}'
```

To send an address message with saved addresses, WhatsApp will prompt the user or business with an option to select among the saved addresses or add an address option. Users can ignore the saved address and enter a new address.

```
curl -X  POST \
'https://graph.facebook.com/<API_VERSION>/<FROM_PHONE_NUMBER_ID>/messages' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "91xxxxxxxxxx",
  "type": "interactive",
  "interactive": {
    "type": "address_message",
    "body": {
      "text": "Thanks for your order! Tell us what address you’d like this order delivered to."
    },
    "action": {
      "name": "address_message",
      "parameters": {
        "country": "IN",
        "saved_addresses": [
          {
            "id": "address1",
            "value": {
              "name": "<CUSTOMER_NAME>",
              "phone_number": "+91xxxxxxxxxx",
              "in_pin_code": "400063",
              "floor_number": "8",
              "building_name": "",
              "address": "Wing A, Cello Triumph,IB Patel Rd",
              "landmark_area": "Goregaon",
              "city": "Mumbai"
            }
          }
        ]
      }
    }
  }
}'
```

## Check Your Response

A successful response includes a `messages` object with an ID for the newly created message.

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<PHONE_NUMBER>",
      "wa_id": "<WHATSAPP_ID>"
    }
  ],
  "messages": [
    {
      "id": "wamid.ID"
    }
  ]
}
```

An unsuccessful response contains an error message. See [Error and Status Codes](/docs/whatsapp/cloud-api/support/error-codes) for more information.

## Send an Address Message with Validation Errors

An address message should be re-sent to the user in the case of a validation error on the business server. The business should send back the set of values previously entered by the user, along with the respective validation errors for each invalid field, as shown in the sample payloads below.

```
curl -X  POST \
'https://graph.facebook.com/<API_VERSION>/<FROM_PHONE_NUMBER_ID>/messages' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d
'{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "91xxxxxxxxxx",
  "type": "interactive",
  "interactive": {
    "type": "address_message",
    "body": {
      "text": "Thanks for your order! Tell us what address you’d like this order delivered to."
    },
    "action": {
      "name": "address_message",
      "parameters": {
          "country": "IN",
          "values": {
             "name": "CUSTOMER_NAME",
             "phone_number": "+91xxxxxxxxxx",
             "in_pin_code": "666666",
             "address": "Some other location",
             "city": "Delhi"
          },
          "validation_errors": {
             "in_pin_code": "We could not locate this pin code."
          }
       }
    }
  }
}'
```

## Receive Notifications for Address Submissions

Businesses will receive address submission notifications through [webhooks](/docs/whatsapp/webhooks/reference), such as the one shown below.

```
{
  "messages": [
    {
      "id": "gBGGFlAwCWFvAgmrzrKijase8yA",
      "from": "&lt;PHONE_NUMBER>",
      "interactive": {
        "type": "interactive",
        "action": "address_message",
        "nfm_reply": {
          "name": "address_message",
          "response_json": "<response_json from client>",
          "body": "<body text from client>"
        },
        "timestamp": "1670394125"
      }
    }
  ]
}
```

The webhook notification has the following values.

| Field Name | Type | Description |
| --- | --- | --- |
| `interactive` | Object | Holds the response from the client |
| `type` | String | Would be `nfm_reply` indicating it is a Native Flow Response (NFM) from the client |
| `nfm_reply` | Object | Holds the data received from the client |
| `response_json` | String | The values of the address fields filled by the user in JSON format that are always present |
| `body` (Optional) | String | Body text from client, what the user sees |
| `name` (Optional) | String | Would be `address_message` indicating the type of NFM action response from the client |

An address message reply as an NFM response type for an India address message request is shown below.

```
{
  "messages": [
    {
      "context": {
        "from": "FROM_PHONE_NUMBER_ID",
        "id": "wamid.HBgLMTIwNjU1NTAxMDcVAgARGBI3NjNFN0U5QzMzNDlCQjY0M0QA"
      },
      "from": "<PHONE_NUMBER>",
      "id": "wamid.HBgLMTIwNjU1NTAxMDcVAgASGCA5RDhBNENEMEQ3RENEOEEzMEI0RUExRDczN0I1NThFQwA=",
      "timestamp": "1671498855",
      "type": "interactive",
      "interactive": {
        "type": "nfm_reply",
        "nfm_reply": {
          "response_json": "{\"saved_address_id\":\"address1\",\"values\":{\"in_pin_code\":\"400063\",\"building_name\":\"\",\"landmark_area\":\"Goregaon\",\"address\":\"Wing A, Cello Triumph, IB Patel Rd\",\"city\":\"Mumbai\",\"name\":\"CUSTOMER_NAME\",\"phone_number\":\"+91xxxxxxxxxx\",\"floor_number\":\"8\"}}",
          "body": "CUSTOMER_NAME\n +91xxxxxxxxxx\n 400063, Goregaon, Wing A, Cello Triumph,IB Patel Rd, Mumbai, 8",
          "name": "address_message"
        }
      }
    }
  ]
}
```

## Feature Not Supported

In the case where the client does not support `address_message`, messages are silently dropped and an error message is sent back to the business in a webhook. The webhook notification that would be sent back is shown below:

```
{
  "statuses": [
    {
      "errors": [
        {
          "code": 1026,
          "href": "https://developers.facebook.com/docs/whatsapp/api/errors/",
          "title": "Receiver Incapable"
        }
      ],
      "id": "gBGGFlAwCWFvAgkyHMGKnRu4JeA",
      "message": {
        "recipient_id": "+91xxxxxxxxxx"
      },
      "recipient_id": "91xxxxxxxxxx",
      "status": "failed",
      "timestamp": "1670394125",
      "type": "message"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Address Messages](#address-messages)

[Sample API call](#sample-api-call)

[Error Handling](#error-handling)

[Address Message Steps](#address-message-steps)

[Additional Action Parameters](#additional-action-parameters)

[Send Address Message to a User](#send-address-message-to-a-user)

[Check Your Response](#response)

[Send an Address Message with Validation Errors](#send-an-address-message-with-validation-errors)

[Receive Notifications for Address Submissions](#receive-notifications-for-address-submissions)

[Feature Not Supported](#feature-not-supported)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=abNkLqWrO83Ez67ZqxxscQ&oh=00_Afiroa4rubIPGgkdzkrLXWY4o9U4aub30l8lFhItASEfhw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=abNkLqWrO83Ez67ZqxxscQ&oh=00_AfiDDjREy8oBepTm2nTKdhNq85meZY-5Mxxj2DhuTxTrDw&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=abNkLqWrO83Ez67ZqxxscQ&oh=00_AfgqOgRm5ocBBrxp9z5xFZa8jcBxLW9zasWP16yXuXvBmA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=abNkLqWrO83Ez67ZqxxscQ&oh=00_AfjOcGxY0iY6W4hjUzQKaJ09IxE3ZE07NIjszN2MdYrR0g&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=abNkLqWrO83Ez67ZqxxscQ&oh=00_AfjNWpXBgB8AEVo0U1hKhU2Pg7-6zQe23wbnCZPgVGmO2g&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT34Ds-uOIQTMcvQe5CJmQWV41ZanvJJipcZHj7HllpgRXzgv04wtDS1-zGlsEdH85DfRR7QD_q6-teilNCixnPPiEAEQdosGPBlloedmrsCGDSngDJr-CpQcPnWq2V80JqEDfIwjD6DYMTakci4bg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)