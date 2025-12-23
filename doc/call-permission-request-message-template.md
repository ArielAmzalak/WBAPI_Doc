+++
id = "call-permission-request-message-template"
title = "Call permission request message template"
summary = "Create a call permission request template message that your business can send to users outside of the customer service window."
source = "https://developers.facebook.com/docs/whatsapp/call-permission-request-message-template"
lang = "en"
tags = ["whatsapp-business-platform", "messaging", "templates", "authentication"]
+++
# Call permission request message template

Create a call permission request template message that your business can send to users outside of the customer service window.

## Create call permission request message template

### Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates/?locale=en_US#Creating) endpoint to create a call permission request message template.

```
curl -X POST \
  'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "sample_cpr_template",
    "language": "en",
    "category": "<CATEGORY>",
    "components": [
      {
        "type": "BODY",
        "text": "We would like to call you to help support your order.",
      },
      {
        "type": "call_permission_request"
      }
   ]
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<CATEGORY>` | **Required.**  Template category  Marketing or Utility | `Marketing` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>` | **Required.**  Whatsapp business account ID. | `106540352242922` |

### Response syntax

```
{
  "id": "<ID>",
  "status": "<STATUS>",
  "category": "<CATEGORY>"
}
```

## Send a call permission request message template

### Request syntax

Use the [POST /<PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send a call permission request message template to a WhatsApp user.

```
curl -X POST \
  'https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>/messages' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<WHATSAPP_USER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<LANGUAGE_AND_LOCAL_CODE>"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "<BODY_TEXT>"
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
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BODY_TEXT>`  *String* | **Required.**  Body text. URLs are automatically hyperlinked.  Maximum 4096 characters. | `John Smith` |
| `<LANGUAGE_AND_LOCAL_CODE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Name of template. | `august_promotion` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example response

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
