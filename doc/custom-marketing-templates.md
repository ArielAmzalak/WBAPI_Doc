+++
id = "custom-marketing-templates"
title = "Custom marketing templates"
summary = "Learn how to create and send a custom marketing template."
source = "https://developers.facebook.com/docs/whatsapp/custom-marketing-templates"
lang = "en"
tags = ["whatsapp-business-platform", "marketing-messages-lite-api", "templates"]
+++
# Custom marketing templates

Learn how to create and send a custom marketing template.

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
