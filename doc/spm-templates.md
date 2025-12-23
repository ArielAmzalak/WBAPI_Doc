![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fspm-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)

    - [Custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates)
    - [Modelos de catálogo](/docs/whatsapp/business-management-api/message-templates/catalog-templates)
    - [Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template)
    - [Modelos de cupom](/docs/whatsapp/business-management-api/message-templates/coupon-templates)
    - [Modelos de oferta por tempo limitado](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates)
    - [Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates)
    - [Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates)
    - [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates)
    - [Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates)
  + [Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)
  + [Componentes](/docs/whatsapp/business-management-api/message-templates/components)
  + [Management](/docs/whatsapp/business-management-api/message-templates/template-management)
  + [Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)
  + [Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)
  + [Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)
  + [Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)
  + [Review](/docs/whatsapp/business-management-api/template-review)
  + [Languages](/docs/whatsapp/business-management-api/message-templates/supported-languages)
  + [Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)
  + [Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)
  + [Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)
  + [Groups](/docs/whatsapp/business-management-api/message-templates/template-groups)
  + [Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)
  + [Time-to-live](/docs/whatsapp/business-management-api/time-to-live)
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

[Single-product message templates](#single-product-message-templates)

[Limitations](#limitations)

[Catalogs](#catalogs)

[Webhooks](#webhooks)

[Creating SPM templates](#creating-spm-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending single-product template messages](#sending-single-product-template-messages)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Single-product message templates

This document describes single-product message (SPM) templates, their uses, and how to use them.

SPM templates are marketing templates that allow you to present a single product from your ecommerce catalog, accompanied by a product image, product title, and product price (all pulled from your product within your catalog), along with customizable body text, optional footer text, and an interactive **View** button.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456611074_369667709517740_8197750041061962345_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=PeO2wueboKsQ7kNvwFNa-TE&_nc_oc=AdnSaP5oj1_hQaVgBlq1xpVCeUd-osw3J8uUWLOSqoa1PZz7llRgekp1g-CKC6o020c&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=uQjW353Rn7_qspMtQji_fQ&oh=00_AfgIVvKwH6KbTEhNAN7WO0l6hQOfpz2K3MMj5eeAXK6vgw&oe=6940538A)

WhatsApp users can tap the button to see details about the product, and can add or remove the product from the WhatsApp shopping cart:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/455731119_491422670275236_7231575948344280249_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=3zVRaNxnrkAQ7kNvwF7Ng5Y&_nc_oc=AdlCniIDat4hokP4MSQUAu4DBvlKYcHmZgbtPZO8yRQggLXtvDhk_Q2F9P3RTSG6Kvk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=uQjW353Rn7_qspMtQji_fQ&oh=00_Afiu2zUVLsvMfZlfDNcgIYbyUNgBOkxZA8vOvdLoWZxCqw&oe=69406F3F)

If the WhatsApp user adds the product to the carts and submits an order, you will be notified via webhook and the user will see that an order has been placed:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/455346606_8499522813412387_6714135406583255031_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=gYSHUQNtwZ4Q7kNvwFvYwHT&_nc_oc=AdleefV4M_y8kUKXHghIJOdtx_wF-mQVgHXZsVNP0kpOLmSunJ5OSvw0yprLKsghNng&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=uQjW353Rn7_qspMtQji_fQ&oh=00_Afjuv4gXu7BgY3PIUqzqsMsyvAWYw1CSr707auxO4y3dbA&oe=69405E85)

Users who place an order are also able to use the View details button to see information about the order:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/455798578_1140213730376391_4808743486596066303_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=kmyGYjaJyV4Q7kNvwHLVl7s&_nc_oc=AdmmcYe9TuNOjBZOkDE4mYcHkgF706FqPYOhmUTJ-U-Gv4oqUEpwCg7hWkOtXMeJq5I&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=uQjW353Rn7_qspMtQji_fQ&oh=00_AfixmyLtf2PB_nqbRTHfSWQJkGlnLd8HuoGlexHQLoB0Qg&oe=69404CFF)

## Limitations

* Customers must be using WhatsApp v2.22.24 or greater.
* Message forwarding is disabled for SPM templates.

## Catalogs

You must have an ecommerce product catalog, with inventory, connected to your WhatsApp Business Account. See the Cloud API [Commerce](/docs/whatsapp/cloud-api/guides/sell-products-and-services) guide to learn more about connecting a catalog to your account.

## Webhooks

When a customer adds one or more products to their cart and submits an order, an [order messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/order) webhook is triggered, describing the order.

## Creating SPM templates

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create an SPM template.

### Request syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE>",
  "category": "marketing",
  "parameter_format": "<PARAMETER_FORMAT>",
  "components": [
    {
      "type": "header",
      "format": "product"
    },
    {
      "type": "body",
      "text": "<CARD_BODY_TEXT>",

      <!-- Example parameter values required, if body text contains parameters -->
      "example": {
        "body_text_named_params": [
          {
            "param_name": "<PARAMETER_NAME>",
            "example": "<PARAMETER_EXAMPLE>"
          },
          <!-- Additional parameters would follow -->
        ]
      }

    },
    {
      "type": "footer",
      "text": "<CARD_FOOTER_TEXT>"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "spm",
          "text": "View"
        }
      ]
    }
  ]
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token. | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<CARD_BODY_TEXT>`  *String* | **Required.**  Card body text. Supports variables.  Maximum 160 characters. | `Use code {{1}} to get {{2}} off our newest succulent!` |
| `<CARD_FOOTER_TEXT>`  *String* | **Optional.**  Footer text.  Maximum 60 characters. | `September 30, 2024` |
| `<PARAMETER_NAME>`  *String* | **Required if body text uses parameters.**  Example parameter value string(s). You must include a parameter example for each parameter in your body text. | `25OFF` |
| `<PARAMETER_FORMAT>`  *String* | **Optional.**  [Parameter format](/docs/whatsapp/business-management-api/message-templates#parameter-formats). Value can be:   * `named` * `positional`   If the `parameter_format` property is omitted, the template will use positional formatting. | `Lucky Shrub: Your gateway to succulents!` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `abandoned_cart_offer` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `546151681022936` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/161311403722088/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "spm_template_named_params",
  "language": "en_US",
  "category": "marketing",
  "parameter_format": "named",
  "components": [
    {
      "type": "header",
      "format": "product"
    },
    {
      "type": "body",
      "text": "Use code {{code}} to get {{percent}} off our newest succulent!",
      "example": {
        "body_text_named_params": [
          {
            "param_name": "code",
            "example": "15OFF"
          },
          {
            "param_name": "percent",
            "example": "15%"
          }
        ]
      }
    },
    {
      "type": "footer",
      "text": "Offer ends September 22, 2024"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "spm",
          "text": "View"
        }
      ]
    }
  ]
}'
```

## Sending single-product template messages

### Request syntax

Use the [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an SPM template message.

```
curl 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "template",
  "template": {
    "name": "<TEMPLATE_NAME>",
    "language": {
      "code": "<TEMPLATE_LANGUAGE>"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "product",
            "product": {
              "product_retailer_id": "<PRODUCT_ID>",
              "catalog_id": "<CATALOG_ID>"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "<PARAMETER_NAME>",
            "text": "<PARAMETER_VALUE>"
          },
          <!-- Additional parameter values would follow, if required by template -->
        ]
      }
    ]
  }
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token | `EAAAN...` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<CATALOG_ID>`  *String* | **Required.**  ID of [connected ecommerce catalog](https://www.facebook.com/business/help/158662536425974) containing the product. | `194836987003835` |
| `<PARAMETER_NAME>`  *String* | **Required if template uses one or more named parameters.**  Name of [named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters). | `code` |
| `<PARAMETER_VALUE>`  *String* | **Required if template uses one or more named parameters.**  [Named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters) value. | `10OFF` |
| `<PRODUCT_ID>`  *String* | **Required.**  Product ID. | `nqryix03ez` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `spm_template_named_params` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example request

This example sends an approved template named "spm\_template\_named\_params" which injects parameters (a discount code and the percentage discounted) into the template body, and which includes a footer. The product image is pulled from the catalog and displayed in the message header.

```
curl 'https://graph.facebook.com/v24.0/179776755229976/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "spm_template_named_params",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "product",
            "product": {
              "product_retailer_id": "nqryix03ez",
              "catalog_id": "194836987003835"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "code",
            "text": "25OFF"
          },
          {
            "type": "text",
            "parameter_name": "percent",
            "text": "25%"
          }
        ]
      }
    ]
  }
}'
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Single-product message templates](#single-product-message-templates)

[Limitations](#limitations)

[Catalogs](#catalogs)

[Webhooks](#webhooks)

[Creating SPM templates](#creating-spm-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending single-product template messages](#sending-single-product-template-messages)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=wnUO9ufGhFXHgZkZ0Z4LCQ&oh=00_AfiELmya1iMUN9HXTZs92y-oX65XzqexS0_Biyst9wev1Q&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=wnUO9ufGhFXHgZkZ0Z4LCQ&oh=00_Afgo96gviukIiHPQAK8RMI7w93X0Lbamc09XwA2zrRwv0w&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=wnUO9ufGhFXHgZkZ0Z4LCQ&oh=00_Afg1R_cAZHcUVB8UyUbjSwBm86Ac91wLmc8HYdUCodje6w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=wnUO9ufGhFXHgZkZ0Z4LCQ&oh=00_AfjTTORt5ZUPuwU4-w7vRtk3wZ3MXjCvoFtL1tH7mmtfOw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=wnUO9ufGhFXHgZkZ0Z4LCQ&oh=00_AfgBVRLq0QBKk-jtYv0PT92e-7XesJchdQyO6SOrVFZaYQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1ZqzBaW2ZcHOW29iD3AoLkIid37hLzA4U1XUXVUBX-QiLgkB7vgLiYDfyTeaNPrcjILBBsO3xHB0hl2RPwVjkLyBHBAbnwomd9lUnbbm8juy2_LYQxbI6vQKJwQwqsR1fvvH3YVc4izJzT-aF4kw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)