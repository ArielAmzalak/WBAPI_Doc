![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Futility-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)
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

[Utility templates](#utility-templates)

[Supported components](#supported-components)

[Create a utility template](#create-a-utility-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Send a utility template](#send-a-utility-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Utility templates

This document describes how to create and send utility templates.

Utility templates are typically sent in response to a user action or request, such as an order confirmation or update.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/555914197_770920925705616_2187359258791538369_n.png?stp=dst-webp&_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=SbKZXKDWX9wQ7kNvwHHr3F4&_nc_oc=Adm1hAX0yH2dUg2fk5V-GviF6ZrBodXBUbFvxKK_kviDHMhCv4LEnso6FiCVLO57bfw&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfhxNPkOlOVev18Tvne-Eh48rL9-EWgVNO2EetVC5FLRxQ&oe=69406F2F)

Utility templates have strict content requirements, particularly around marketing material. If you attempt to create or update a utility template with marketing material, the template will automatically be re-categorized as a marketing template.

See our [template categorization](/docs/whatsapp/updates-to-pricing/new-template-guidelines#utility-template-guidelines) documentation for content guidelines.

## Supported components

Utility templates support the following components:

* 1 header (optional; all types supported)
* 1 body
* 1 footer (optional)
* Up to 10 buttons (optional). Supported types:
  + Call request
  + Copy code
  + Phone number
  + Quick-reply
  + URL

## Create a utility template

### Request syntax

Use the `POST/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates` endpoint to create a utility template.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE>",
  "category": "utility",
  "parameter_format": "<PARAMETER_FORMAT>",
  "components": [

    <!-- header component optional -->
    {
      "type": "header",
      "format": "<HEADER_TYPE>",
      "example": {
        "header_handle": [
          "<HEADER_HANDLE>"
        ]
      }
    },

    <!-- body component required -->
    {
      "type": "body",
      "text": "<BODY_TEXT>",

      <!-- example required if <BODY_TEXT> contains one or more parameters -->
      "example": {
        "body_text_named_params": [
          {
            "param_name": "<PARAMETER_NAME>",
            "example": "<PARAMETER_EXAMPLE_VALUE>"
          },

          <!-- additional parameters would follow, if using multiple parameters -->
        ]
      }
    },

    <!-- footer component optional -->
    {
      "type": "footer",
      "text": "<FOOTER_TEXT>"
    },

    <!-- button components optional -->
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "<URL_BUTTON_LABEL_TEXT>",
          "url": "<URL>"
        },
        {
          "type": "phone_number",
          "text": "<PHONE_BUTTON_LABEL_TEXT>",
          "phone_number": "<PHONE_NUMBER>"
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

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BODY_TEXT>`  *String* | **Required.**   Template body text. Variables are supported.   Maximum 1024 characters. | `You're all set! Your reservation for {{number_of_guests}} at Lucky Shrub Eatery on {{day}}, {{date}}, at {{time}}, is confirmed. See you then!` |
| `<FOOTER_TEXT>`  *String* | **Optional.**  Template footer text. Variables are supported  Maximum 60 characters. | `Lucky Shrub Eatery: The Luckiest Eatery in Town!` |
| `<HEADER_ASSET_HANDLE>`  *String* | **Required if using a header with a media asset.**  Asset handle of example media asset uploaded on your WhatsApp Business Account.  Maximum 60 characters. | `4::aW1hZ2UvcG5n:ARYpf5zqqUjggwGfsZOJ2_o26Zs8ntcO2mss2vKpFb8P_IvskL043YXKpehYTD7IxqEB4t-uZcIzOTxOFRavEcN_tZLhk1WXFb3IOr4S8UKJcQ:e:1759093121:634974688087057:100089620928913:ARYyOAh63uQLhDpqOdk\n4::aW1hZ2UvcG5n:ARZW8t9-cBNjpdmxV5Z9wcRAMhfmw4ATpJcJiHT0nY62hXq4ppOeBaTWaGI0IwX-twF2IkeKo-_MyW2pEDuBAE5vyw2oHTNgPZQkntclrgWMGg:e:1759093121:634974688087057:100089620928913:ARZE4NC5MrxnZUe5GRw` |
| `<HEADER_TYPE>`  *String* | **Required if using a header.**  Header format. Values can be:   * documentation * image * location * text * video | `image` |
| `<PARAMETER_EXAMPLE_VALUE>`  *String* | **Required if using a body component string that includes one or more parameters.**  Example parameter value. You must supply an example for each parameter defined in your body component string. | `Saturday` |
| `<PARAMETER_NAME>`  *String* | **Required if using named parameters.**  Must be a unique string, composed of lowercase characters and underscores, wrapped in double curly brackets. | `{{day}}` |
| `<PHONE_BUTTON_LABEL_TEXT>`  *String* | **Required if using a phone number button.**  Button label text.  Maximum 25 characters. Alphanumeric characters only. | `Change reservation` |
| `<PHONE_NUMBER>`  *String* | **Required if using a phone number button component.**  Business phone number to be called in the WhatsApp user's default phone app when tapped by the user.  Note that some countries have special phone numbers that have leading zeros after the country calling code (e.g., +55-0-955-585-95436). If you assign one of these numbers to the button, the leading zero will be stripped from the number. If your number will not work without the leading zero, assign an alternate number to the button, or add the number as message  Maximum 20 characters. Alphanumeric characters only. | `15550051310` |
| `<QUICK_REPLY_BUTTON_LABEL_TEXT>` | **Required if using a quick-reply button.**  Button label text.  Maximum 25 characters. Alphanumeric characters only. | `Cancel reservation` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  [Template language code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name. Must be unique, unless existing templates with the same name have a different template language.  Maximum 512 characters. Lowercase, alphanumeric characters and underscores only. | `reservation_confirmation` |
| `<URL>`  *String* | **Required if including a URL button.**  URL to be loaded in WhatsApp user's default web browser when tapped. | `https://www.luckyshrubeater.com/reservations` |
| `<URL_BUTTON_LABEL_TEXT>`  *String* | **Required if using a URL button.**  Button label text.  Maximum 25 characters. Alphanumeric characters only. | `Change reservation` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>` | **Required.**  WhatsApp Business Account ID. | `546151681022936` |

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
| `<TEMPLATE_CATEGORY>` | [Template category](/docs/whatsapp/updates-to-pricing/new-template-guidelines). | `UTILITY` |
| `<TEMPLATE_ID>` | Template ID. | `546151681022936` |
| `<TEMPLATE_STATUS>` | [Template status](/docs/whatsapp/business-management-api/message-templates#template-status). | `PENDING` |

### Example request

This example request creates a utility template with:

* an image header component
* a body component with a string that has 4 named parameters
* a footer component
* a URL button component
* a phone number button component
* a quick-reply button component

```
curl 'https://graph.facebook.com/v23.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "reservation_confirmation",
  "language": "en_US",
  "category": "utility",
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
      "text": "*You're all set!*\n\nYour reservation for {{number_of_guests}} at Lucky Shrub Eatery on {{day}}, {{date}}, at {{time}}, is confirmed. See you then!",
      "example": {
        "body_text_named_params": [
          {
            "param_name": "number_of_guests",
            "example": "4"
          },
          {
            "param_name": "day",
            "example": "Saturday"
          },
          {
            "param_name": "date",
            "example": "August 30th, 2025"
          },
          {
            "param_name": "time",
            "example": "7:30 pm"
          }
        ]
      }
    },
    {
      "type": "footer",
      "text": "Lucky Shrub Eatery: The Luckiest Eatery in Town!"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "Change reservation",
          "url": "https://www.luckyshrubeater.com/reservations"
        },
        {
          "type": "phone_number",
          "text": "Call us",
          "phone_number": "+15550051310"
        },
        {
          "type": "quick_reply",
          "text": "Cancel reservation"
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "id": "546151681022936",
  "status": "PENDING",
  "category": "UTILITY"
}
```

## Send a utility template

### Request syntax

Use the [`POST/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/message`](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an approved utility template in template message.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESSS_PHONE_NUMBER_ID>/messages' \
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

      <!-- Only required if the template uses a media header component -->
      {
        "type": "header",
        "parameters": [
          {
            "type": "<MEDIA_HEADER_TYPE>",
            "<MEDIA_HEADER_TYPE>": {
              "id": "<MEDIA_HEADER_ASSET_ID>"
            }
          }
        ]
      },

      <!-- Only required if the template uses body component parameters -->
      {
        "type": "body",
        "parameters": [
          {
            "type": "<NAMED_PARAM_TYPE>",
            "parameter_name": "<NAMED_PARAM_NAME>",
            "text": "<NAMED_PARAM_VALUE>"
          },

          <!-- Additional parameters values would follow, if needed -->

        ]
      }
    ]
  }
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional**  API version. If omitted, defaults to the newest API version available to your app. | `v24.0` |
| `<MEDIA_HEADER_ASSET_ID>`  *String* | **Required if template uses a media header component.** | `2871834006348767` |
| `<MEDIA_HEADER_TYPE>`  *String* | **Required if template uses a media header component.**  Media header type. Values can be:   * document * image * video   Note that this placeholder appears twice in the request syntax above. | `image` |
| `<NAMED_PARAM_NAME>` | **Required if template uses body component parameters.**  Name of parameter as defined in the template body component text string. | `number_of_guests` |
| `<NAMED_PARAM_TYPE>` | **Required if template uses body component parameters.**  Parameter type. Set to text. | `text` |
| `<NAMED_PARAM_VALUE>` | **Required if template uses body component parameters.**  Parameter value. | `4` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  [Template language code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name. Must be unique, unless existing templates with the same name have a different template language.  Maximum 512 characters. Lowercase, alphanumeric characters and underscores only. | `reservation_confirmation` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>` | **Required.**  WhatsApp Business Account ID. | `546151681022936` |
| `<WHATSAPP_USER_PHONE_NUMBER>` | **Required.**  WhatsApp user phone number. | `16505551234` |

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

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<PACING_STATUS>` | [Template pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing) status. | `accepted` |
| `<WHATSAPP_MESSAGE_ID>` | WhatsApp Message ID.  This ID is included in status [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks for delivery status purposes. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJBRkJENzExMTRFRjk2NTI1OTEA` |
| `<WHATSAPP_USER_ID>` | WhatsApp user's WhatsApp ID. May not match input value. | `16505551234` |
| `<WHATSAPP_USER_PHONE_NUMBER>` | WhatsApp user's WhatsApp phone number. May not match wa\_id value. | `16505551234` |

### Example request

This is an example request that sends the template created in the example template creation request above.

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
    "name": "reservation_confirmation",
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
              "id": "2871834006348767"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "number_of_guests",
            "text": "4"
          },
          {
            "type": "text",
            "parameter_name": "day",
            "text": "Saturday"
          },
          {
            "type": "text",
            "parameter_name": "date",
            "text": "August 30th, 2025"
          },
          {
            "type": "text",
            "parameter_name": "time",
            "text": "7:30 pm"
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
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJBRkJENzExMTRFRjk2NTI1OTEA",
      "message_status": "accepted"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Utility templates](#utility-templates)

[Supported components](#supported-components)

[Create a utility template](#create-a-utility-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Send a utility template](#send-a-utility-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_Afj-eHSBUyUExXLLxrqBb8hwi5bqq_QmfAWmYk4Eqc10lw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfipFxu5oPvQkEJDVwe3Sh-91C2Kvc1at6ppkZNC5oVZUw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfgSR8jkuz_ccr3xJczhSUK3ZzoZNvXqXHjUD60KYXVfOQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2Nv_uvrD8w-2VKkFS1sjLoTO60uEAqEkdWBmCV27zrvtwAro6yx5MTkxyF13ghWA4X1My7t__fwdnWxBCOm_ulP0f71UJJHseT_QW_BrAJ5NdNL2n-T5lYDeV7es27zLbLCB7jycE_AVCP2yifQQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_Afix3K_FOQqtuojMtIXwEBbGMsOKYhxjyS1_1d1gZtJr5Q&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2J04mhykYlXaQJb4prNh1lYTgfmO4tYBbhwWWP0ksedY4y_67xPlBspdiLkE6n5g1sQlvjWr_y435vywCV1hDy5Tc7sxyHVqL-Kd8g6Z63w0ukypCxMptEGOJFHq3AHHwEZ0O2AQzPEwo48XkHfw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfhdVDS1-HpghrMYPPk7DX98O3x8wKAxU_RBCmyrN_Q4gQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1AEkpHUOCjCpYtNUQjkUx_cI1iucGSWJXXn1346s4pcdnx0bZOaX3CEYtsh85hCoBl_bpg-hoUXQe9YiAIVOiHJ1_R_welqPH0e9_qtxb_1LTgyNxkMvHV1Rk8D45s3AWlilwj7abuvC6mVRMeKA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfiD1gLcGxhDB9pxAf9HwTpnYn6xza4FqxRJMoW8jKP_pA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3hXMw6AcmlDtcRju6ISouVq4h5zwQeHnheCDWFeMOQIPcV0u88d_f07nPnoe2JzYc3Aqy_WE4kEzWdUs--EoXoKme_BkHZnmwwhNo4u1DwBYc1Z7hSfurmfFaRIEpOF7vJLF7Mf5aGUqFct6YJXA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT18PW6AWC-c9O5x5PgTebteBT72X46qsM64k2vphgZ7NigTwP_SR5pyDqXhn5manFli0Z9vrANov-WUHm-dNB2swuoskhXl4H_llgI5HIBHr9VmUmGEKeYvCb0Wp1Tagxuy22qGGLZWiLgjw3GIow)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2nBtoNqWT4M8Hh1O7NW3_r9KxWkDiHfcHnlY7d_gmrW5ymIHaxmawjDU1SOM3KrUegmdhFHgjIAL_HLnX7CZ0FL1vleLirKnBKdAIzJV9Lf5Yb3KwgeAv8wCBKRqVUA-Ucr4NxvQXYN7yrvtso-w)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfhLCVCYWCPqIkTXsGVbZQTMvF1GqSfLs6fkTkRl7skNHQ&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfiRxAvNYkZILQbiH66kmXEgdf4GsSHaKXgYAbRe3s_6sw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT08U2QumoL5uMvK-rFY37P7TlYp-W82HGzT15tHJdRLDgJFyYp2NXHiMLKMZfTG80FlsxYLsil7Dr48DPk9hYXGxJwaPojh8efAummeoTBOs7FnhSW1srF5hnDBLai9FfQvURanIptylunRjnudEw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_Afgio8IDbKIy6x8_zp-veJicN8S09yaFNNWpcrgACUvYEg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT17G5HmNLgM7VYKof-cK-7r1lP4SkY_SdqNLQ2Jd3F0KXY3q2UOoV27dnFu1zEcjt-NkHlP7Gtu03gqw_yCBMbwwZ6MBnw4yhk0Koyj7sbQFtqJt-rxbI0ZjvekOqy8tstAzF-_Qixt2zLuMTDi7A)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_AfjnKItevPpIBhYXj4nV3jIii44nE1ml4Hmhc_7q0JrH9g&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3ojnhxVjC4trdriYXCat_UKK5Evof38Q2UTIr0_PxEWuUULZvA5sODmlzJAtfNy-bXush1kslB8l0O3g3duHGNOtXn83kWf0PX2-8Bw-GaHYls6OXdKDz21s8bxJ-9x8bGCwf38KLc8TJWBE4Ddvzx7b5M0Jo_AYE)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=zvaAYYuQXgkZeAExB4lCGg&oh=00_Afjn63K2zIDAkdCIBbawekN7cgfuP0I6VwNLZB7_9KbMog&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2Dlr3JSQ7mDL6ukJkZFL5T_wurX4OWz3Wpjl6T_xvpp0A2M9_tnf4jVFI2fhb5FrjjzGF-WsbVF4O-GUBC9PxSmSe6jFr9QgD1WJ_F8i7bf4SrqoRlRPoU3_HiNP6I9-CIU-JEiJXEqA7dsamM6ApcEJR7RjzNyjo)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3gABtgeY8B0dMQmanlRsVgLCrnDR4RUyscj-9XoJfy8RKOKrjim40Q_YC82KGTVSxHFtSl3F_a-MV5SRc6769l5Due-oQvtk4ovWZoJaIYsq2NJ-fIecbne1_gua9b3duvQcKtSFE82dPS8Ulthg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)