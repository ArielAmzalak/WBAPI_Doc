+++
id = "errors"
title = "Errors `messages` webhooks reference"
summary = "This reference describes trigger events and payload contents for the WhatsApp Business Account messages webhook for errors messages."
source = "https://developers.facebook.com/docs/whatsapp/errors"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "messaging"]
+++
# Errors `messages` webhooks reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **messages** webhook for errors messages.

## Triggers

* We are unable to process a request due to a system level problem.
* We are unable to process a request due to an app or account level problem.

## Syntax

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "errors": [
              {
                "code": <ERROR_CODE>,
                "title": "<ERROR_TITLE>",
                "message": "<ERROR_MESSAGE>",
                "error_data": {
                  "details": "<ERROR_DETAILS>"
                },
                "href": "<ERROR_CODES_URL>"
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<ERROR_CODE>`  *Integer* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/). | `130429` |
| `<ERROR_CODES_URL>`  *String* | Link to [error code documentation](/docs/whatsapp/cloud-api/support/error-codes/). | `https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/` |
| `<ERROR_DETAILS>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) details. | `Message failed to send because there were too many messages sent from this phone number in a short period of time` |
| `<ERROR_MESSAGE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) message. This value is the same as the `title` property value. | `Rate limit hit` |
| `<ERROR_TITLE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) title. This value is the same as the `message` property value. | `Rate limit hit` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "errors": [
              {
                "code": 130429,
                "title": "Rate limit hit",
                "message": "Rate limit hit",
                "error_data": {
                  "details": "Message failed to send because there were too many messages sent from this phone number in a short period of time"
                },
                "href": "https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/"
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```
