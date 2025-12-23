![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fmessages%2Fstatus%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)[status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
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

  + [account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts)
  + [account\_review\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_review_update)
  + [account\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_update)
  + [automatic\_events](/docs/whatsapp/cloud-api/webhooks/reference/automatic_events)
  + [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update)
  + [history](/docs/whatsapp/cloud-api/webhooks/reference/history)
  + [message\_template\_components\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_components_update)
  + [message\_template\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_quality_update)
  + [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update)
  + [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)

    - [audio](/docs/whatsapp/cloud-api/webhooks/reference/messages/audio)
    - [button](/docs/whatsapp/cloud-api/webhooks/reference/messages/button)
    - [contacts](/docs/whatsapp/cloud-api/webhooks/reference/messages/contacts)
    - [document](/docs/whatsapp/cloud-api/webhooks/reference/messages/document)
    - [errors](/docs/whatsapp/cloud-api/webhooks/reference/messages/errors)
    - [group](/docs/whatsapp/cloud-api/webhooks/reference/messages/group)
    - [image](/docs/whatsapp/cloud-api/webhooks/reference/messages/image)
    - [interactive](/docs/whatsapp/cloud-api/webhooks/reference/messages/interactive)
    - [location](/docs/whatsapp/cloud-api/webhooks/reference/messages/location)
    - [order](/docs/whatsapp/cloud-api/webhooks/reference/messages/order)
    - [reaction](/docs/whatsapp/cloud-api/webhooks/reference/messages/reaction)
    - [status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)
    - [sticker](/docs/whatsapp/cloud-api/webhooks/reference/messages/sticker)
    - [system](/docs/whatsapp/cloud-api/webhooks/reference/messages/system)
    - [texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)
    - [unsupported](/docs/whatsapp/cloud-api/webhooks/reference/messages/unsupported)
    - [video](/docs/whatsapp/cloud-api/webhooks/reference/messages/video)
  + [partner\_solutions](/docs/whatsapp/cloud-api/webhooks/reference/partner_solutions)
  + [payment\_configuration\_update](/docs/whatsapp/cloud-api/webhooks/reference/payment_configuration_update)
  + [phone\_number\_name\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_name_update)
  + [phone\_number\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_quality_update)
  + [security](/docs/whatsapp/cloud-api/webhooks/reference/security)
  + [smb\_app\_state\_sync](/docs/whatsapp/cloud-api/webhooks/reference/smb_app_state_sync)
  + [smb\_message\_echoes](/docs/whatsapp/cloud-api/webhooks/reference/smb_message_echoes)
  + [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update)
  + [user\_preferences](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Status messages webhook reference](#status-messages-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Status `messages` webhook reference

This reference describes trigger events and payload contents for WhatsApp Business Account status **messages** webhook.

## Triggers

* Your message is sent to a WhatsApp user.
* Your message is delivered to a WhatsApp user's device.
* Your message is displayed (i.e. "read") in the WhatsApp client on a WhatsApp user's device.
* Your message is unable to be sent to a WhatsApp user.
* Your message is unable to be delivered to a WhatsApp user's device.
* Your message is sent to a WhatsApp user in a group chat.
* Your voice message is played by the WhatsApp user's device.

Note that the triggers above also apply to a WhatsApp user who is part of a group chat.

A status is considered read only if it has been delivered. In some cases, like when a user receives a message while in the chat screen, the message is both delivered and read at the same time. In these cases, the "delivered" webhook is not sent because it's implied that the message was delivered since it was read. This behavior is due to internal optimization.

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
            "statuses": [
              {
                "id": "<WHATSAPP_MESSAGE_ID>",
                "status": "<STATUS>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "recipient_id": "<USER_PHONE_NUMBER_OR_GROUP_ID>",
                "recipient_type": "group", <!-- Only included if message sent to a group -->
                "recipient_participant_id": "<GROUP_PARTICIPANT_USER_PHONE_NUMBER>", <!-- Only included if message sent to a group -->
                "recipient_identity_key_hash": "<IDENTITY_KEY_HASH>", <!-- Only included if identity change check enabled -->
                "biz_opaque_callback_data": "<BUSINESS_OPAQUE_DATA>", <!-- Only included if message sent with biz_opaque_callback_data -->

                <!-- (1) Only included with sent status, and one of either delivered or read status
                     (2) Omitted entirely for v24.0+ unless webhook is for a free entry point conversation -->
                "conversation": {
                  "id": "<CONVERSATION_ID>",
                  "expiration_timestamp": "<CONVERSATION_EXPIRATION_TIMESTAMP>",
                  "origin": {
                    "type": "<CONVERSATION_CATEGORY>"
                  }
                },

                <!-- only included with sent status, and one of either delivered or read status -->
                "pricing": {
                  "billable": <IS_BILLABLE?>,
                  "pricing_model": "<PRICING_MODEL>",
                  "type": "<PRICING_TYPE>",
                  "category": "<PRICING_CATEGORY>"
                },

                <!-- only included if failure to send or deliver message -->
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
| `<BUSINESS_OPAQUE_DATA>`  *String* | String assigned by the business to the `biz_opaque_callback_data` property in the send message request.  Only included if the business set a `biz_opaque_callback_data` value when [sending](/docs/whatsapp/cloud-api/reference/messages#messages) the message. | `1744434060` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<CONVERSATION_CATEGORY>`  *String* | [Conversation category](/docs/whatsapp/pricing#conversation-categories). Values can be:  `authentication` — Indicates an authentication conversation.  `authentication_international` — Indicates an [authentication-international](/docs/whatsapp/pricing/authentication-international-rates/) conversation.  `marketing` — Indicates a marketing conversation.  `marketing_lite` — Indicates a [Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp/) conversation.  `referral_conversion` — Indicates a free entry point conversation.  `service` — Indicates a service conversation.  `utility` — Indicates a utility conversation. | `service` |
| `<CONVERSATION_EXPIRATION_TIMESTAMP>`  *String* | Unix timestamp indicating when the conversation will expire.  The expiration\_timestamp property is only included for `sent` status. | `1744434060` |
| `<CONVERSATION_ID>`  *String* | Version 24.0 and higher:  The `conversation` object will be omitted entirely, unless the webhook is for a message sent within an open free entry point window, in which case the value will be unique per window.  Version 23.0 and lower:  Value will now be set to a unique ID per-message, unless the webhook is for a message sent with an open free entry point window, in which case the value will be unique per window. | `8f842dbba350821654c9dfed31f5635c` |
| `<ERROR_CODE>`  *Integer* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/). | `131050` |
| `<ERROR_CODES_URL>`  *String* | Link to [error code documentation](/docs/whatsapp/cloud-api/support/error-codes/). | `https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/` |
| `<ERROR_DETAILS>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) details. | `In order to maintain a healthy ecosystem engagement, the message failed to be delivered.` |
| `<ERROR_MESSAGE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) message. This value is the same as the `title` property value. | `This message was not delivered to maintain healthy ecosystem engagement.` |
| `<ERROR_TITLE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) title. This value is the same as the `message` property value. | `This message was not delivered to maintain healthy ecosystem engagement.` |
| `<GROUP_PARTICIPANT_USER_PHONE_NUMBER>`  *String* | WhatsApp user phone number. Property only included if message was sent to a [group](/docs/whatsapp/cloud-api/groups). | `16505551234` |
| `<IDENTITY_KEY_HASH>`  *String* | Identity key hash. Only included if you have enabled the [identity change check](/docs/whatsapp/cloud-api/reference/phone-numbers#identity-change-check) feature. | `DF2lS5v2W6x=` |
| `<IS_BILLABLE?>`  *Boolean* | Indicates if the message is billable (`true`) or not (`false`).  Note that the `billable` property will be deprecated in a future versioned release, so we recommend that you start using `pricing.type` and `pricing.category` together to determine if a message is billable, and if so, its billing rate. | `true` |
| `<PRICING_CATEGORY>`  *String* | Pricing category ([rate](/docs/whatsapp/pricing#rates)) applied if billable. Values can be:  `authentication` — Indicates authentication rate applied.  `authentication-international` — Indicates authentication-international rate applied.  `marketing` — Indicates marketing rate applied.  `marketing_lite` — Indicates a [Marketing Messages Lite API](/docs/whatsapp/marketing-messages-lite-api/) pricing applied.  `referral_conversion` — Indicates a [free entry point conversation](/docs/whatsapp/pricing#free-entry-point-conversations).  `service` – Indicates service rate applied.  `utility` — Indicates utility rate applied. | `service` |
| `<PRICING_MODEL>`  *String* | Pricing model. Values can be:  `CBP` — Indicates conversation-based pricing applies. Will only be set to this value if the webhook was sent before July 1, 2025.  `PMP` — Indicates [per-message pricing](/docs/whatsapp/pricing) applies. | `PMP` |
| `<PRICING_TYPE>`  *String* | Pricing type.  `regular` — Indicates the message is billable.  `free_customer_service` — Indicates the message is free because it was either a utility template message or non-template message sent within a customer service window.  `free_entry_point` — Indicates the message is free because it was sent within an open free entry point window. | `regular` |
| `<STATUS>`  *String* | Message status. Values can be:  `delivered` — Indicates message was successfully delivered to the WhatsApp user's device.   * WhatsApp UI equivalent: Two checkmarks.   `failed` — Indicates failure to send or deliver the message to the WhatsApp user's device.   * WhatsApp UI equivalent: Red error triangle.   `played` — Indicates the first time a voice message is played by the WhatsApp user's device.   * WhatsApp UI equivalent: Blue microphone.   `read` — Indicates the message was displayed in an open chat thread in the WhatsApp user's device.   * WhatsApp UI equivalent: Two blue checkmarks.   `sent` — Indicates the message was successfully sent from our servers.   * WhatsApp UI equivalent: One checkmark. | `read` |
| `<USER_PHONE_NUMBER_OR_GROUP_ID>`  *String* | WhatsApp user phone number or group ID.  Value set to the WhatsApp user's phone number if the message was sent to their phone number, or set to a [group ID](/docs/whatsapp/cloud-api/groups) if sent to a group ID. If sent to a group ID, the WhatsApp user's phone number is instead assigned to the `recipient_participant_id` property. | `16505551234` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *String* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=` |

## Examples

This example webhook describes a marketing message that has been successfully sent from our servers.

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
            "statuses": [
              {
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=",
                "status": "sent",
                "timestamp": "1750030073",
                "recipient_id": "16505551234",
                "conversation": {
                  "id": "72b14d6bd5407799e66f64d1b338e567",
                  "expiration_timestamp": "1750116480",
                  "origin": {
                    "type": "marketing"
                  }
                },
                "pricing": {
                  "billable": true,
                  "pricing_model": "PMP",
                  "type": "regular",
                  "category": "marketing"
                }
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

This example v24.0 webhook describes a marketing message that has been displayed in the WhatsApp client (i.e. "read"). Notice that in this case, the `conversation` object is omitted because it's a v24.0 webhook, and the `pricing` object is omitted because it happened to be displayed in an associated delivered status messages webhook (the object can only appear in one or the other).

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
            "statuses": [
              {
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=",
                "status": "sent",
                "timestamp": "1750030073",
                "recipient_id": "16505551234"
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

This example describes a message that failed to be sent.

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
            "statuses": [
              {
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI0QUQ2MjA4NEYyRkExNjMyREUA",
                "status": "failed",
                "timestamp": "1751142888",
                "recipient_id": "16505551234",
                "errors": [
                  {
                    "code": 131049,
                    "title": "This message was not delivered to maintain healthy ecosystem engagement.",
                    "message": "This message was not delivered to maintain healthy ecosystem engagement.",
                    "error_data": {
                      "details": "In order to maintain a healthy ecosystem engagement, the message failed to be delivered."
                    },
                    "href": "https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/"
                  }
                ]
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

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Status messages webhook reference](#status-messages-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=_Sv617JQT3sZP5E5_OMKrA&oh=00_AfhJitAD8bfwb6Wt7AIzXB7mTYblan_N_9hc3FmNMSr6dg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=_Sv617JQT3sZP5E5_OMKrA&oh=00_AfhdsTbfHRRrVBfVkmrVet2oShMAQgq_dmIOEBUh05sdhw&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=_Sv617JQT3sZP5E5_OMKrA&oh=00_AfjFbgjb_lTbnA3VI7FWwNunvZ-KjfDrBerWHNaFWj4NCQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=_Sv617JQT3sZP5E5_OMKrA&oh=00_Afi_siX7PHhsFSsdWzbWAxLrfZxbhuZKCOYmoCFOA8OkNg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=_Sv617JQT3sZP5E5_OMKrA&oh=00_AfgVkSGAOl7XaCmgQ1O4Mbbf00H6EQ25NivzzqjLXQISKg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT25mMQsmpyEVGU84WZXCj5g5jNlS8xRmOZACKb5CZpEUihA9OThrCD_edEmqE59BSHHngpRJjelS0TQyYlaMq0_cj3_Aw8RLnUx4BRuiKCh0kOl_NPukWlBmb5LI6a1_K48eaXo439gcnn8ZreLIQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)