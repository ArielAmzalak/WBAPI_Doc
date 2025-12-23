![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fcustom-marketing-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates)

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

[Custom marketing templates](#custom-marketing-templates)

[Supported components](#supported-components)

[Create a custom marketing template](#create-a-custom-marketing-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Send a custom marketing template](#send-a-custom-marketing-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Custom marketing templates

Learn how to create and send a custom marketing template.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/555070362_1180641373877493_714272106387148710_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=31Q9G2blyaAQ7kNvwFDqFDv&_nc_oc=AdnO5HEeeQnVX1qWcMRnycJe28Q2EqJPBJQBOzawOwK5_wDL2_FN-KZkn36ip7PWA48&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Ulngg-PmdritNfLX6xbF2A&oh=00_AfhatEb0gh6S72lP_s1jUG9ioxW0yOPFhz0Gnh_NCTaD9w&oe=694070AA)

## Supported components

Custom marketing templates support the following components:

* 1 header (optional; all types supported)
* 1 body (required)
* 1 footer (optional)
* Up to 10 buttons (optional; all types supported)

## Create a custom marketing template

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/#Creating) endpoint to create a custom marketing template.

### Request syntax

This example syntax creates a template with an image header, body text with 3 named parameters, a footer, and 3 buttons (url, phone number, and quick-reply).

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
      "format": "image",
      "example": {
        "header_handle": [
          "<HEADER_ASSET_HANDLE>"
        ]
      }
    },
    {
      "type": "body",
      "text": "<BODY_TEXT>",
      "example": {
        "body_text_named_params": [
          {
            "param_name": "<BODY_PARAMETER_NAME>",
            "example": "<BODY_PARAMETER_EXAMPLE_VALUE>"
          },
          <!-- additional parameters and example values go here -->
        ]
      }
    },
    {
      "type": "footer",
      "text": "<FOOTER_TEXT>"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "<URL_BUTTON_LABEL_TEXT>",
          "url": "<URL_BUTTON_URL>"
        },
        {
          "type": "phone_number",
          "text": "<PHONE_NUMBER_BUTTON_LABEL_TEXT>",
          "phone_number": "<PHONE_NUMBER_BUTTON_PHONE_NUMBER>"
        },
        {
          "type": "quick_reply",
          "text": "<QUICK_REPLY_BUTTON_LABEL_TEXT>"
        }
      ]
    }
  ]
}'
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token. | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<BODY_PARAMETER_EXAMPLE_VALUE>`  *String* | **Required if using a body component string that includes one or more parameters.**  Example parameter value. You must supply an example for each parameter defined in your body component string. | `WELCOME20` |
| `<BODY_PARAMETER_NAME>`  *String* | **Required if using named parameters.**  Parameter name. You must supply a name for each parameter defined in your body component string. Must be a unique string, composed of lowercase characters and underscores, wrapped in double curly brackets. | `{{discount_code}}` |
| `<BODY_TEXT>`  *String* | **Required.**  Template body text. Variables are supported.  Maximum 1024 characters. | `Welcome to Lucky Shrub, {{first_name}}!\\n\\nUse code *{{discount_code}}* to get {{discount_amount}} off of your first purchase!` |
| `<FOOTER_TEXT>`  *String* | **Optional.**  Footer text.  Maximum 60 characters. | `Lucky Shrub: Your gateway to succulents!` |
| `<PARAMETER_FORMAT>`  *String* | **Optional.**  [Parameter format](/docs/whatsapp/business-management-api/message-templates#parameter-formats). Value can be:   * `named` * `positional`   If the `parameter_format` property is omitted, the template will use positional formatting. | `Lucky Shrub: Your gateway to succulents!` |
| `<HEADER_ASSET_HANDLE>`  *String* | **Required if using a header with a media asset.**  Header [media asset handle](https://developers.facebook.com/docs/graph-api/guides/upload). | `4::aW1hZ2UvcG5n:ARYpf5zqqUjggwGfsZOJ2_o26Zs8ntcO2mss2vKpFb8P_IvskL043YXKpehYTD7IxqEB4t-uZcIzOTxOFRavEcN_tZLhk1WXFb3IOr4S8UKJcQ:e:1759093121:634974688087057:100089620928913:ARYyOAh63uQLhDpqOdk` |
| `<PHONE_NUMBER_BUTTON_LABEL_TEXT>`  *String* | **Required if using a phone number button.**  Button label text. Maximum 25 characters. Alphanumeric characters only. | `Call us` |
| `<PHONE_NUMBER_BUTTON_PHONE_NUMBER>`  *String* | **Required if using a phone number button component.**  Business phone number to be called in the WhatsApp user's default phone app when tapped by the user. Note that some countries have special phone numbers that have leading zeros after the country calling code (e.g., +55-0-955-585-95436). If you assign one of these numbers to the button, the leading zero will be stripped from the number. If your number will not work without the leading zero, assign an alternate number to the button, or add the number as message body text.  Maximum 20 characters. Alphanumeric characters only. | `15550051310` |
| `<QUICK_REPLY_BUTTON_LABEL_TEXT>` | **Required if using a quick-reply button.**  Button label text. Maximum 25 characters. Alphanumeric characters only. | `Unsubscribe` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name. Must be unique, unless existing templates with the same name have a different template language.  Maximum 512 characters. Lowercase, alphanumeric characters and underscores only. | `reservation_confirmation` |
| `<URL_BUTTON_URL>`  *String* | **Required if including a URL button.**  URL to be loaded in WhatsApp user's default web browser when tapped. | `https://www.luckyshrubeater.com/reservations` |
| `<URL_BUTTON_LABEL_TEXT>`  *String* | **Required if using a URL button.**  Button label text.  Maximum 25 characters. Alphanumeric characters only. | `View deals` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `546151681022936` |

### Response syntax

Upon success:

```
{
  "id": "<TEMPLATE_ID>",
  "status": "<TEMPLATE_STATUS>",
  "category": "<TEMPLATE_CATEGORY>"
}
```

### Response parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<TEMPLATE_CATEGORY>` | [Template category](/docs/whatsapp/updates-to-pricing/new-template-guidelines). | `MARKETING` |
| `<TEMPLATE_ID>` | Template ID. | `1627019861106475` |
| `<TEMPLATE_STATUS>` | [Template status](/docs/whatsapp/business-management-api/message-templates#template-status). | `PENDING` |

### Example request

```
curl 'https://graph.facebook.com/v23.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "welcome_discount_template",
  "language": "en_US",
  "category": "marketing",
  "parameter_format": "named",
  "components": [
    {
      "type": "header",
      "format": "image",
      "example": {
        "header_handle": [
          "4::aW..."
        ]
      }
    },
    {
      "type": "body",
      "text": "Welcome to Lucky Shrub, {{first_name}}!\n\nUse code *{{discount_code}}* to get {{discount_amount}} off of your first purchase!",
      "example": {
        "body_text_named_params": [
          {
            "param_name": "first_name",
            "example": "Pablo"
          },
          {
            "param_name": "discount_code",
            "example": "WELCOME20"
          },
          {
            "param_name": "discount_amount",
            "example": "20%"
          }
        ]
      }
    },
    {
      "type": "footer",
      "text": "Lucky Shrub: Your gateway to succulents!"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "View deals",
          "url": "https://www.luckyshrub.com/deals"
        },
        {
          "type": "phone_number",
          "text": "Call us",
          "phone_number": "+15550051310"
        },
        {
          "type": "quick_reply",
          "text": "Unsubscribe"
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "id": "1627019861106475",
  "status": "PENDING",
  "category": "MARKETING"
}
```

## Send a custom marketing template

Use the [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send an approved marketing template.

### Request syntax

This example syntax is for sending the template described in the [create syntax](#request-syntax) above, which expects a header image asset, and 3 body text parameter values which will replace their parameter placeholders in the body text string.

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
            "type": "image",
            "image": {
              "id": "<HEADER_ASSET_ID>"
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
          <!-- additional parameters and values go here -->
        ]
      }
    ]
  }
}'
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<HEADER_ASSET_ID>`  *String* | **Required if template uses a header media.**  Header [media asset ID](/docs/whatsapp/cloud-api/reference/media#upload-media). | `1339522734477770` |
| `<PARAMETER_NAME>`  *String* | **Required if template uses one or more named parameters.**  Name of [named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters). | `discount_code` |
| `<PARAMETER_VALUE>`  *String* | **Required if template uses one or more named parameters.**  [Named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters) value. | `WELCOME25` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  [Template language](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name. | `welcome_discount_template` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `16505551234` |

### Response syntax

Upon success:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<WHATSAPP_USER_PHONE_NUMBER>",
      "wa_id": "<WHATSAPP_USER_ID>"
    }
  ],
  "messages": [
    {
      "id": "<WHATSAPP_MESSAGE_ID>",
      "message_status": "<PACING_STATUS>"
    }
  ]
}
```

### Response parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<PACING_STATUS>` | Template [pacing status](/docs/whatsapp/business-management-api/message-templates/template-pacing). | `accepted` |
| `<WHATSAPP_MESSAGE_ID>` | WhatsApp Message ID.  This ID is included in status [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks for delivery status purposes. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJBRkJENzExMTRFRjk2NTI1OTEA` |
| `<WHATSAPP_USER_ID>` | WhatsApp user's WhatsApp ID. May not match `input` value. | `16505551234` |
| `<WHATSAPP_USER_PHONE_NUMBER>` | WhatsApp user's WhatsApp phone number. May not match `wa_id` value. | `16505551234` |

### Example request

```
curl 'https://graph.facebook.com/v23.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "welcome_discount_template",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "image",
            "image": {
              "id": "1339522734477770"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "first_name",
            "text": "Jessica"
          },
          {
            "type": "text",
            "parameter_name": "discount_code",
            "text": "WELCOME25"
          },
          {
            "type": "text",
            "parameter_name": "discount_amount",
            "text": "25%"
          }
        ]
      }
    ]
  }
}'
```

### Example response

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "16505551234",
      "wa_id": "16505551234"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBIyQjM2RTlERTY4QjFGNzUwNDgA",
      "message_status": "accepted"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Custom marketing templates](#custom-marketing-templates)

[Supported components](#supported-components)

[Create a custom marketing template](#create-a-custom-marketing-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Send a custom marketing template](#send-a-custom-marketing-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=2FX9RpyvjS01NaVvC7Si9A&oh=00_AfgGm6vzcxFEdinrsCLCsPY3ScNIe5wYQd8jPxRWXDEy2g&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=2FX9RpyvjS01NaVvC7Si9A&oh=00_AfgGhGKH0jBRIgKbdajRrGtLtxwQROSrYa166Fv-7Tt0zg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=2FX9RpyvjS01NaVvC7Si9A&oh=00_AfjuIXjTwO0eZ5anDWgG2cJ2h5m6qoCFV3qC3nfwe1dKPA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=2FX9RpyvjS01NaVvC7Si9A&oh=00_Afg1LrOGbWV6UpDO0O7K77sf_w7NKoeW6pZE1-nCSU_DaA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=2FX9RpyvjS01NaVvC7Si9A&oh=00_Afh95gf1x7m5-ujG6JqFFMBO6NjCdpH0_V9eNcG8_I61rA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0e805pb7bA65XmdY65biJgIyuHkWsETmYLohZU8Oak0apeUX7LGh9LrJ3xo0BV-_9jXoyYzGFGr-EMDzscbXcOrCyF_jDrSA0dOw-JdzN6LNdU2SPC9JwxV9VRqOgZ2W7d_--IubZj2zVV4blU7Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)