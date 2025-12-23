+++
id = "limited-time-offer-templates"
title = "Limited-time offer templates"
summary = "This document describes limited-time offer templates and how to use them."
source = "https://developers.facebook.com/docs/whatsapp/limited-time-offer-templates"
lang = "en"
tags = ["whatsapp-business-platform", "templates", "rate-limits"]
+++
# Limited-time offer templates

This document describes limited-time offer templates and how to use them.

Limited-time offer templates allow you to display expiration dates and running countdown timers for offer codes in template messages, making it easy for you to communicate time-bound offers and drive customer engagement.

## Limitations

* Only templates categorized as `MARKETING` are supported.
* Footer components are not supported.
* Users who view a limited-time offer template message using that WhatsApp web app or desktop app will not see the offer, but will instead see a message indicating that they have received a message but that it's not supported in the client they are using.

## Creating limited-time offer templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create a limited-time offer template.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "name": "<TEMPLATE_NAME>",
    "language": "<TEMPLATE_LANGUAGE>",
    "category": "marketing",
    "components": [
      {
        "type": "header",
        "format": "<HEADER_FORMAT>",
        "example": {
          "header_handle": [
            "<HEADER_ASSET_HANDLE>"
          ]
        }
      },
      {
        "type": "limited_time_offer",
        "limited_time_offer": {
          "text": "<LIMITED_TIME_OFFER_TEXT>",
          "has_expiration": <HAS_EXPIRATION>
        }
      },
      {
        "type": "body",
        "text": "<BODY_TEXT>",
        "example": {
          "body_text": [<BODY_TEXT_VARIABLE_EXAMPLES>]
        }
      },
      {
        "type": "buttons",
        "buttons": [
          {
            "type": "copy_code",
            "example": "<OFFER_CODE_EXAMPLE>"
          },
          {
            "type": "url",
            "text": "<URL_BUTTON_TEXT>",
            "url": "<URL_BUTTON_URL>",
            "example": [
              "<URL_EXAMPLE_WITH_VARIABLE_EXAMPLE>"
            ]
          }
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BODY_TEXT>`  *String* | **Required.**   Body component text. Supports variables.   Maximum 600 characters. | `Good news, {{1}}! Use code {{2}} to get 25% off all Caribbean Destination packages!` |
| `<BODY_TEXT_VARIABLE_EXAMPLES>`  *Array of strings* | **Required if body component text uses variables.**   Array of example variable strings.   Must supply examples for all placeholders in `<BODY_TEXT>` string.   No maximum, but counts against `<BODY_TEXT>` maximum. | `["Pablo","CARIBE25"]` |
| `<HAS_EXPIRATION>`  *Boolean* | **Optional.**   Set to `true` to have the [offer expiration details](#offer-expiration-details) appear in the delivered message. | `true` |
| `<HEADER_ASSET_HANDLE>`  *Media asset handle* | **Required if using an image or video header.**   Uploaded media asset handle. Use the [Resumable Upload API](/docs/graph-api/guides/upload) to generate an asset handle. | `4::aW...` |
| `<HEADER_FORMAT>`  *Enum* | **Required if using a header.**   Can be `IMAGE`, or `VIDEO`. | `IMAGE` |
| `<LIMITED_TIME_OFFER_TEXT>`  *String* | **Required.**   Offer details text.   Maximum 16 characters. | `Expiring offer!` |
| `<OFFER_CODE_EXAMPLE>`  *String* | **Required.**   Example offer code.   Maximum 15 characters. | `CARIBE25` |
| `<TEMPLATE_LANGUAGE>`  *Enum* | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**   Template name.   Maximum 512 characters. | `limited_time_offer_caribbean_pkg_2023` |
| `<URL_BUTTON_TEXT>`  *String* | **Required.**   [URL button](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) label text. Supports 1 variable.   25 characters maximum. | `Book now!` |
| `<URL_BUTTON_URL>`  *String* | **Required.**   URL of website that loads in the device's default mobile web browser when the [URL button](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) is tapped by the WhatsApp user.   Supports 1 variable appended to the end of the URL string.   Maximum 2000 characters. | `https://awesomedestinations.com/offers?code={{1}}` |
| `<URL_EXAMPLE_WITH_VARIABLE_EXAMPLE>`  *String* | **Required if URL uses a variable.**   Example URL with example variable appended to the end.   No maximum, but value counts against `<URL_BUTTON_URL>` maximum. | `https://awesomedestinations.com/offers?ref=n3mtql` |

### Offer expiration details

The delivered message can display an offer expiration details section with a heading, an optional expiration timer, and the offer code itself.

The expiration timer is a text string that is not customizable, but it will change to red text if the message is viewed and the offer code is expiring within the next hour. (You include the actual offer code and its expiration timestamp when you send the template in a template message.)

### Example request

This is an example request to create a limited-time offer template that uses:

* an image header component
* body text component with variables
* the limited time offer component
* a copy code button
* a button URL with a variable

```
curl 'https://graph.facebook.com/v17.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "limited_time_offer_caribbean_pkg_2023",
  "language": "en_US",
  "category": "marketing",
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
      "type": "limited_time_offer",
      "limited_time_offer": {
        "text": "Expiring offer!",
        "has_expiration": true
      }
    },
    {
      "type": "body",
      "text": "Good news, {{1}}! Use code {{2}} to get 25% off all Caribbean Destination packages!",
      "example": {
        "body_text": [
          [
            "Pablo",
            "CARIBE25"
          ]
        ]
      }
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "copy_code",
          "example": "CARIBE25"
        },
        {
          "type": "url",
          "text": "Book now!",
          "url": "https://awesomedestinations.com/offers?code={{1}}",
          "example": [
            "https://awesomedestinations.com/offers?ref=n3mtql"
          ]
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
  "category": "MARKETING"
}
```

## Sending limited-time offer templates

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an approved limited-time offer template in a template message.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<CUSTOMER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<TEMPLATE_LANGUAGE_CODE>"
      },
      "components": [
        {
          "type": "header",
          "parameters": [
            {
              "type": "<HEADER_TYPE>",
              "<HEADER_TYPE>": {
                "id": "<HEADER_ASSET_ID>"
              }
            }
          ]
        },
        {
          "type": "body",
          "parameters": [
            <BODY_VARIABLES>
          ]
        },
        {
          "type": "limited_time_offer",
          "parameters": [
            {
              "type": "limited_time_offer",
              "limited_time_offer": {
                "expiration_time_ms": <EXPIRATION_TIME>
              }
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "copy_code",
          "index": 0,
          "parameters": [
            {
              "type": "coupon_code",
              "coupon_code": "<OFFER_CODE>"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": <URL_BUTTON_INDEX>,
          "parameters": [
            {
              "type": "text",
              "text": "<URL_VARIABLE>"
            }
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BODY_VARIABLES>`  *Array of objects* | **Required if template body text uses variables.**   Body text variable values. Define each variable as an individual object. | `{"type":"text","text":"Pablo"},{"type":"text","text":"CARIBE25"}` |
| `<CUSTOMER_PHONE_NUMBER>`  *String* | **Required.**   Phone number of customer who the template message should be sent to. | `+16505555555` |
| `<EXPIRATION_TIME>`  *Unix timestamp* | **Required.**   Offer code expiration time as a UNIX timestamp in milliseconds. | `1698562800000` |
| `<HEADER_ASSET_ID>`  *Media asset ID* | **Required.**   Uploaded media asset ID. Use the [/PHONE\_NUMBER\_ID/media](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to generate an ID. | `1602186516975000` |
| `<HEADER_TYPE>`  *String* | **Required.**   Header type used by the template. Values can be `image` or `video`. | `image` |
| `<OFFER_CODE>`  *String* | **Required if template uses a copy code button.**   Offer code.   Maximum 15 characters. | `CARIBE25` |
| `<TEMPLATE_LANGUAGE_CODE>`  *Enum* | **Required.**   The template's [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**   The template's name. | `limited_time_offer_caribbean_pkg_2023` |
| `<URL_BUTTON_INDEX>`  *Integer* | **Required.**   URL button index. If the template uses a copy code button, value must be `1`.   If the template does not use a copy code button, the value must be `0`. | `1` |
| `<URL_VARIABLE>`  *String* | **Required if URL uses a variable.**   URL variable value.   No maximum but value counts against URL string maximum of 2000 characters. | `n3mtql` |

### Example request

Example request to send a limited-time offer template that uses:

* an image header
* body text variables
* the offer expiration details
* a copy code button
* a URL button with a variable

```
curl 'https://graph.facebook.com/v17.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505555555",
  "type": "template",
  "template": {
    "name": "limited_time_offer_caribbean_pkg_2023",
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
              "id": "1602186516975000"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "Pablo"
          },
          {
            "type": "text",
            "text": "CARIBE25"
          }
        ]
      },
      {
        "type": "limited_time_offer",
        "parameters": [
          {
            "type": "limited_time_offer",
            "limited_time_offer": {
              "expiration_time_ms": 1209600000
            }
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "copy_code",
        "index": 0,
        "parameters": [
          {
            "type": "coupon_code",
            "coupon_code": "CARIBE25"
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "url",
        "index": 1,
        "parameters": [
          {
            "type": "text",
            "text": "n3mtql"
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
      "input": "16505555555",
      "wa_id": "16505555555"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDUwNzY1MjAVAgARGBI5QTNDQTVCM0Q0Q0Q2RTY3RTcA"
    }
  ]
}
```
