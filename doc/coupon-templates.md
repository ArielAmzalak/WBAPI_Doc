+++
id = "coupon-templates"
title = "Coupon code templates"
summary = "Coupon code templates are marketing templates that display a single copy code button. When tapped, the code is copied to the customer's clipboard."
source = "https://developers.facebook.com/docs/whatsapp/coupon-templates"
lang = "en"
tags = ["whatsapp-business-platform", "templates", "rate-limits"]
+++
# Coupon code templates

Coupon code templates are marketing templates that display a single copy code button. When tapped, the code is copied to the customer's clipboard.

## Limitations

* Coupon code templates are currently not supported by the WhatsApp web client.
* Codes are limited to 15 characters.
* Button text cannot be customized.
* Templates are limited to one copy code button.

## Creating coupon code templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates) endpoint to create coupon code templates.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "<NAME>",
    "language": "<LANGUAGE>",
    "category": "MARKETING",
    "components": [
      {
        "type": "BODY",
        "text": "<BODY_TEXT>"
      },
      {
        "type": "BUTTONS",
        "buttons": [
          {
            "type": "COPY_CODE",
            "example": "<EXAMPLE>"
          }
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<NAME>`  *String* | **Required.**   Template name.   Maximum 512 characters. | `fall2023_promotion` |
| `<LANGUAGE>`  *Enum* | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<EXAMPLE>`  *String* | **Required.**   Coupon code to be copied when tapped.   Maximum 15 characters. | `25OFF` |

### Response

Upon success, the API will respond with the following:

```
{
   "category" : "<CATEGORY>",
   "id" : "<ID>",
   "status" : "<STATUS>"
}
```

### Response parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<CATEGORY>`  *Enum* | Template category. | `MARKETING` |
| `<ID>`  *Numeric string* | Template ID. | `1924084211297547` |
| `<STATUS>`  *Enum* | Template status. | `PENDING` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "coupon_code_fall2023_25off",
  "language": "en_US",
  "category": "MARKETING",
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT",
      "text": "Our Fall Sale is on!"
    },
    {
      "type": "BODY",
      "text": "Shop now through November and use code {{1}} to get {{2}} off of all merchandise!",
      "example": {
        "body_text": [
          [
            "25OFF",
            "25%"
          ]
        ]
      }
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "QUICK_REPLY",
          "text": "Unsubscribe"
        },
        {
          "type": "COPY_CODE",
          "example": "250FF"
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "category" : "MARKETING",
  "id" : "1924084211297547",
  "status" : "PENDING"
}
```

## Sending coupon code templates

### Request syntax

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an approved coupon template in a template message.

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "messaging_product": "whatsapp",
    "to": "<TO>",
    "type": "template",
    "template": {
      "name": "<NAME>",
      "language": {
        "code": "<CODE>"
      },
      "components": [
        {
          "type": "button",
          "sub_type": "COPY_CODE",
          "index": <INDEX>,
          "parameters": [
            {
              "type": "coupon_code",
              "coupon_code": "<COUPON_CODE>"
            }
          ]
        }
        // ... Add other components if needed
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<TO>`  *String* | **Required.**   The WhatsApp ID or phone number of the customer to send the message to. See [Phone Number Formats](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/). | `+16505551234` |
| `<NAME>`  *String* | **Required.**   Name of the template to be sent. | `coupon_code_fall2023_25off` |
| `<CODE>`  *String* | **Required.**   The template's language and locale code. | `en_US` |
| `<INDEX>`  *Integer* | **Required.**   Indicates order in which button should appear, if the template uses multiple buttons.   Buttons are zero-indexed, so setting value to `0` will cause the button to appear first, and another button with an index of `1` will appear next, etc. | `0` |
| `<COUPON_CODE>`  *String* | **Required.**   The coupon code to be copied when the customer taps the button. Only accepting alphanumeric characters. | `25OFF` |

### Response syntax

Upon success the API will respond with:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<WHATSAPP_USER_PHONE_NUMBER>",
      "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>"
    }
  ],
  "messages": [
    {
      "id": "<WHATSAPP_MESSAGE_ID>",
      "group_id": "<GROUP_ID>", <!-- Only included if messaging a group -->
      "message_status": "<PACING_STATUS>" <!-- Only included if sending a template -->
    }
  ]
}
```

### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | The string identifier of a group made using the Groups API.  This field shows when messages are sent, received, or read from a group.  [Learn more about the Groups API](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) | `Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD` |
| `<PACING_STATUS>`  *String* | Indicates [template pacing](/docs/whatsapp/message-templates/guidelines#template-pacing) status. The `message_status` property is only included in responses when sending a [template message](/docs/whatsapp/cloud-api/guides/send-message-templates) that uses a template that is being paced. | `wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI4MjZGRDA0OUE2OTQ3RkEyMzcA` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | WhatsApp user's WhatsApp phone number. May not match `wa_id` value. | `+16505551234` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user's WhatsApp ID. May not match `input` value. | `16505551234` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp Message ID. This ID appears in associated **messages** webhooks, such as sent, read, and delivered webhooks. | `wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI4MjZGRDA0OUE2OTQ3RkEyMzcA` |

### Example Request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "coupon_code_fall2023_25off",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "25OFF"
          },
          {
            "type": "text",
            "text": "25%"
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "COPY_CODE",
        "index": 1,
        "parameters": [
          {
            "type": "coupon_code",
            "coupon_code": "25OFF"
          }
        ]
      }
    ]
  }
}'
```

### Example Response

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
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBIxRjk1REYzMDBERDE3RUI0RDYA"
    }
  ]
}
```
