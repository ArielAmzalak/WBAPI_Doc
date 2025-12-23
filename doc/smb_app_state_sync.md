+++
id = "smb_app_state_sync"
title = "`smb_app_state_sync` webhook reference"
summary = "This reference describes trigger events and payload contents for the WhatsApp Business Account smb\\app\\state\\_sync webhook."
source = "https://developers.facebook.com/docs/whatsapp/smb_app_state_sync"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks"]
+++
# `smb_app_state_sync` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **smb\_app\_state\_sync** webhook.

The **smb\_app\_state\_sync** webhook is used for synchronizing contacts of [WhatsApp Business app users who have been onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) via a solution provider.

## Triggers

* A solution provider [synchronizes the WhatsApp Business app contacts](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users#step-1--initiate-contacts-synchronization) of a business customer with a WhatsApp Business app phone number who the provider has [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider adds a contact to their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT3V4rMGusBQbxes_DTsWxZe0YWW_TCgdv6FkAvGej0Bdb_XRYOsjTm3FJEO81MrR1xq_DGu6TZGjFgIMMAFdQ-XyxQ_mjL9JDNQcjJrDImDXY2rkM5BzXoJGW_gleTDF8FY5p5xpPnpMRPUEqIFTg).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider removes a contact from their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT2rFhs80M2VXq48m0Ce5--UFCVklogzkh_U44jhJuoYgvvE-7sPj2zHsin9bkIYnCdtuabKhq1MEE1JCfFwi0NsbdEr52onnslgLxvjUGHCt2Z39jy1tj4IYg7-vRu5oc-g0jVFQrzhfA4QxkSyCg).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider edits a contact in their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT0VfY8K1suOLK1fF-uMqqrGH4rzdqcM-jP-El4CeTrUcT3QebrLYaelO0gJ0-iiKVEVGIdJY9oDctqU0Q6PQrYgZiW-rrqdmdMZq8JMUtsOxN7IQ0dv379FeDGvI5swhZNiimD3EdkeQgVqk8UPnQ).

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
            "state_sync": [
              {
                "type": "contact",
                "contact": {
                  "full_name": "<CONTACT_FULL_NAME>",
                  "first_name": "<CONTACT_FIRST_NAME>",
                  "phone_number": "<CONTACT_PHONE_NUMBER>"
                },
                "action": "<ACTION>",
                "metadata": {
                  "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>"
                }
              },
              <!-- Additional contacts would follow, if any -->
            ]
          },
          "field": "smb_app_state_sync"
        }
      ]
    }
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACTION>`  *String* | Indicates if the business customer added, edited, or deleted a contact from their WhatsApp Business app phone address book.  Values can be:  `add`  Indicates the WhatsApp Business app user added or edited a contact.  `remove`  Indicates the WhatsApp Business app user removed a contact. | `add` |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<CONTACT_FIRST_NAME>`  *String* | The contact's first name, as it appears in the business customer's WhatsApp Business app phone address book.  Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo` |
| `<CONTACT_FULL_NAME>`  *String* | The contact's full name, as it appears in the business customer's WhatsApp Business app phone address book.  Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo Morales` |
| `<CONTACT_PHONE_NUMBER>`  *String* | The contact's WhatsApp phone number. | `16505551234` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
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
            "state_sync": [
              {
                "type": "contact",
                "contact": {
                  "full_name": "Pablo Morales",
                  "first_name": "Pablo",
                  "phone_number": "16505551234"
                },
                "action": "add",
                "metadata": {
                  "timestamp": "1739321024"
                }
              }
            ]
          },
          "field": "smb_app_state_sync"
        }
      ]
    }
  ]
}
```
