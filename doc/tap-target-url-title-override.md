+++
id = "tap-target-url-title-override"
title = "Tap target title URL override"
summary = "This document explains how to send approved message templates using the taptargetconfiguration component within a template message."
source = "https://developers.facebook.com/docs/whatsapp/tap-target-url-title-override"
lang = "en"
tags = ["whatsapp-business-platform"]
+++
# Tap target title URL override

This document explains how to send approved message templates using the `tap_target_configuration` component within a template message. Tap target override enables image-based, text-based, and header-less message templates to function as interactive Call-to-Action URL buttons. These buttons display a custom title and open the destination linked to the first URL button.

WhatsApp Business Accounts (WABAs) must be fully verified and consistently maintain high-quality standards to ensure compliance and access to this component.

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a text message template to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
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
      "code": "<LANGUAGE_AND_LOCALE_CODE>"
    },
    "components": [
      {
        "type": "tap_target_configuration",
        "parameters": [
          {
            "type": "tap_target_configuration",
            "tap_target_configuration": [
              {
                "url": "<URL>",
                "title": "<TITLE>"
              }
            ]
          }
        ]
      },
          <!-- Add additional components -->
    ]
  }
}
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<LANGUAGE_AND_LOCAL_CODE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Name of template. | `august_promotion` |
| `<TITLE>`  *String* | **Required.**  URL Title. | `Offer Details!` |
| `<URL>`  *String* | **Required.**  URL. | `https://www.luckyshrubs.com` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

Example request to send a template message with the `tap_target_configuration` type.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+1233214532",
  "type": "template",
  "template": {
    "name": "august_promotion",
    "language": {
      "code": "en"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "image",
            "image": {
              "link": "https://www.luckyshrubs.com"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "Hello Andy..."
          }
        ]
      },
      {
        "type": "tap_target_configuration",
        "parameters": [
          {
            "type": "tap_target_configuration",
            "tap_target_configuration": [
              {
                "url": "https://www.luckyshrubs.com/",
                "title": "Offer Details"
              }
            ]
          }
        ]
      }
    ]
  }
}'
```

## Example response

```
{
   "messaging_product": "whatsapp",
   "contacts": [
       {
           "input": "+1233214532",
           "wa_id": "1233214532"
       }
   ],
   "messages": [
       {
           "id": "wamid.HBgLMTMyMzI4NjU2NzgVAgARGBJBQzRBRDBEMDEwQzVBM0M0QkIA",
           "message_status": "accepted"
       }
   ]
}
```
