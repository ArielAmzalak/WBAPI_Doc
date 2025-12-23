![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fhistory%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[history](/docs/whatsapp/cloud-api/webhooks/reference/history)

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

[history webhook reference](#history-webhook-reference)

[Triggers](#triggers)

[Chat history sharing approved](#chat-history-sharing-approved)

[Chat history contents](#chat-history-contents)

[Phases and chunks](#phases-and-chunks)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

[Chat history sharing declined](#chat-history-sharing-declined)

[Syntax](#syntax-2)

[Parameters](#parameters-2)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `history` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account `history` webhook.

The **history** webhook is used to synchronize the [WhatsApp Business app chat history](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) of a business customer onboarded by a solution provider.

## Triggers

* a solution provider [synchronize the WhatsApp Business app chat history](#step-2--initiate-message-history-synchronization) of a business customer who they have onboarded with a WhatsApp Business app phone number, and who has agreed to share their chat history
* a solution provider [synchronize the WhatsApp Business app chat history](#step-2--initiate-message-history-synchronization) of a business customer who they have onboarded with a WhatsApp Business app phone number, but the customer has declined to share their chat history

## Chat history sharing approved

### Chat history contents

If the business customer has already approved chat history sharing when the solution provider requests the business's chat history, a series of history webhooks will be triggered, describing all messages sent or received within 180 days of the time when the business was onboarded onto Cloud API.

* Messages that are part of a group chat will not be included.
* Media messages will not include media asset IDs. Instead, additional history webhooks containing media message asset IDs will be sent separately, but only for media messages sent within 14 days of onboarding.

Note that for efficiency purposes, a single webhook could potentially describe thousands of messages, so we recommend that you capture its contents first, then process the contents asynchronously.

### Phases and chunks

Webhooks are divided into three history phases, where day 0 indicates the time when the business was onboarded onto Cloud API:

* phase 0: day 0 through day 1
* phase 1: day 1 through day 90
* phase 2: day 90 through day 180

For each phase, chat history webhooks may be sent in separate chunks, depending on the total number of messages that comprise the thread.

* You can use the `chunk_order` parameter value to arrange these chunks in their sequential order, as they may not be delivered sequentially.
* You can use the `phase` parameter value to monitor phase progress. A value of `2` indicates that the current phase is complete.
* You can use the `progress` parameter value to monitor the overall progress. A value of `100` indicates that synchronization is complete.

If there is no chat history available for a given phase, no corresponding webhooks will be sent.

### Syntax

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<CUSTOMER_WABA_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<CUSTOMER_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<CUSTOMER_PHONE_NUMBER_ID>"
            },
            "history": [
              {
                "metadata": {
                  "phase": <PHASE>,
                  "chunk_order": <CHUNK_ORDER>,
                  "progress": <PROGRESS>
                },
                "threads": [
                  /* First chat history thread object */
                  {
                    "id": "<WHATSAPP_USER_PHONE_NUMBER>",
                    "messages": [
                      /* First message object in thread */
                      {
                        "from": "<BUSINESS_OR_WHATSAPP_USER_PHONE_NUMBER>",
                        "to": "<WHATSAPP_USER_PHONE_NUMBER>", // only included if SMB message echo
                        "id": "<WHATSAPP_MESSAGE_ID>",
                        "timestamp": "<DEVICE_TIMESTAMP>,
                        "type": "<MESSAGE_TYPE>",
                        "<MESSAGE_TYPE>": {
                          <MESSAGE_CONTENTS>
                        },
                        "history_context": {
                          "status": "<MESSAGE_STATUS>"
                        }
                      },
                      /* Additional message objects in thread would follow, if any */
                    ]
                  },
                  /* Additional chat history thread objects would follow, if any */
                ]
              }
            ]
          },
          "field": "history"
        }
      ]
    }
  ]
}
```

### Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<BUSINESS_OR_WHATSAPP_USER_PHONE_NUMBER>`  *String* | The business customer's phone number, or the WhatsApp user's phone number.  If the value is the business's phone number, the message object describes a message sent by the business to a WhatsApp user.  If the value is the WhatsApp user's phone number, the message object describes a message sent by the WhatsApp user to the business. | `15550783881` |
| `<CHUNK_ORDER>`  *Integer* | Indicates [chunk](#phases-and-chunks) number, which you can use to order sets of webhooks sequentially. | `1` |
| `<CUSTOMER_WABA_ID>`  *String* | The business customer's WhatsApp Business Account ID. | `102290129340398` |
| `<CUSTOMER_DISPLAY_PHONE_NUMBER>`  *String* | The business customer's business phone number. | `15550783881` |
| `<CUSTOMER_PHONE_NUMBER_ID>`  *String* | The business customer's business phone number ID. | `106540352242922` |
| `<DEVICE_TIMESTAMP>`  *String* | Unix timestamp indicating when the message was received by the recipient's device. | `1738796547` |
| `<MESSAGE_CONTENTS>`  *Object* | An object describing the message's contents. This value will vary based on the message type, as well as the contents message.  For example, if a business sends an `image` message without a caption, the object would not include the `caption` property.  See [Sending messages](/docs/whatsapp/cloud-api/guides/send-messages) for examples of payloads for each message type. | `{"body":"Here's the info you requested! https://www.meta.com/quest/quest-3/"}` |
| `<MESSAGE_STATUS>`  *String* | Indicates the message's most recent delivery stats. Values can be:   * `DELIVERED` * `ERROR` * `PENDING` * `PLAYED` * `READ` * `SENT` | `READ` |
| `<MESSAGE_TYPE>`  *String* | [Message type](/docs/whatsapp/cloud-api/webhooks/components#messages-object). Note that this placeholder appears twice in the syntax above, as it serves as a placeholder for the `type` property's value and its matching property name. See the [example payload below](#example-history-approved) for a thread with various message types.  If this value is set to `media_placeholder`, the message object describes a message that contained a media asset. In this case, the message contents will be omitted. Instead, a separate history webhook will follow, describing the content of the message and the media asset ID, but only if the message was sent within the last two weeks of your query. See the [example payload below](#example-media-asset) describing a media message's contents. | `text` |
| `<PHASE>`  *Integer* | Indicates history [phase](#phases-and-chunks). Values can be:   * `0` — indicates messages are from day 0 (business onboarding time) through day 1 * `1` — indicates messages are from day 1 through day 90 * `2` — indicates messages are from day 90 through day 180 | `1` |
| `<PROGRESS>`  *Integer* | Indicates percentage total of synchronization progress.  Minimum `0`, maximum `100`. | `55` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | The WhatsApp user's phone number.  The `to` property is only included if the message object represents an [SMB message echo](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users#step-3--mirror-new-whatsapp-business-app-messages). | `16505551234` |

### Examples

This example webhook describes two message threads: (1) a thread containing a text message and video message sent to a WhatsApp user, and the WhatsApp user's response, and (2) a text message sent to a different WhatsApp user, thanking them for their order.

Note that the media message's contents in the first thread are not described. Instead, a [second webhook](#example-media-asset) is triggered, describing the media message's contents.

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
            "history": [
              {
                "metadata": {
                  "phase": 0,
                  "chunk_order": 1,
                  "progress": 55
                },
                "threads": [
                  {
                    "id": "16505551234",
                    "messages": [
                      {
                        "from": "15550783881",
                        "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBIyNDlBOEI5QUQ4NDc0N0FCNjMA",
                        "timestamp": "1739230955",
                        "type": "text",
                        "text": {
                          "body": "Here's the info you requested! https://www.meta.com/quest/quest-3/"
                        },
                        "history_context": {
                          "status": "READ"
                        }
                      },
                      {
                        "from": "15550783881",
                        "id": "wamid.QyNUEHBgLMTY0NjcwNDM1OTUVAgARGBI1Rj3NEYxMzAzMzQ5MkEA",
                        "timestamp": "1739230970",
                        "type": "media_placeholder",
                        "history_context": {
                          "status": "PLAYED"
                        }
                      },
                      {
                        "from": "16505551234",
                        "id": "wamid.N0FCNjMAHBgLMTY0NjcwNDM1OTUVAgARGBIyNDlBOEI5QUQ4NDc0",
                        "timestamp": "1739230970",
                        "type": "text",
                        "text": {
                          "body": "Thanks!"
                        },
                        "history_context": {
                          "status": "READ"
                        }
                      }
                    ]
                  },
                  {
                    "id": "12125557890",
                    "messages": [
                      {
                        "from": "15550783881",
                        "id": "wamid.BIyNDlBOEI5N0FCNjMAHBgLMTY0NjcwNDM1OTUVAgARGQUQ4NDc0",
                        "timestamp": "1739230970",
                        "type": "text",
                        "text": {
                          "body": "Thanks for your order! As a thank you, use code THANKS30 to get 30% of your next order."
                        },
                        "history_context": {
                          "status": "DELIVERED"
                        }
                      }
                    ]
                  }
                ]
              }
            ]
          },
          "field": "history"
        }
      ]
    }
  ]
}
```

This example webhook describes a media message's contents.

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
            "messages": [
              {
                "from": "16505551234",
                "id": "wamid.QyNUEHBgLMTY0NjcwNDM1OTUVAgARGBI1Rj3NEYxMzAzMzQ5MkEA",
                "timestamp": "1738796547",
                "type": "image",
                "image": {
                  "caption": "Black Prince echeveria",
                  "mime_type": "image/jpeg",
                  "sha256": "3f9d94d399fa61c191bc1d4ca71375a035cd9b9f5b1128e1f0963a415c16b0cc",
                  "id": "24230790383178626"
                }
              }
            ]
          },
          "field": "history"
        }
      ]
    }
  ]
}
```

## Chat history sharing declined

### Syntax

```
{
  "messaging_product": "whatsapp",
  "metadata": {
    "display_phone_number": "<CUSTOMER_DISPLAY_PHONE_NUMBER>",
    "phone_number_id": "<CUSTOMER_PHONE_NUMBER_ID>"
  },
  "history": [
    {
      "errors": [
        {
          "code": 2593109,
          "title": "History sync is turned off by the business from the WhatsApp Business App",
          "message": "History sync is turned off by the business from the WhatsApp Business App",
          "error_data": {
            "details": "History sharing is turned off by the business"
          }
        }
      ]
    }
  ]
}
```

### Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<CUSTOMER_DISPLAY_PHONE_NUMBER>`  *String* | The business customer's business phone number. | `15550783881` |
| `<CUSTOMER_PHONE_NUMBER_ID>`  *String* | The business customer's business phone number ID. | `106540352242922` |

### Example

```
{
  "messaging_product": "whatsapp",
  "metadata": {
    "display_phone_number": "15550783881",
    "phone_number_id": "106540352242922"
  },
  "history": [
    {
      "errors": [
        {
          "code": 2593109,
          "title": "History sync is turned off by the business from the WhatsApp Business App",
          "message": "History sync is turned off by the business from the WhatsApp Business App",
          "error_data": {
            "details": "History sharing is turned off by the business"
          }
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[history webhook reference](#history-webhook-reference)

[Triggers](#triggers)

[Chat history sharing approved](#chat-history-sharing-approved)

[Chat history contents](#chat-history-contents)

[Phases and chunks](#phases-and-chunks)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

[Chat history sharing declined](#chat-history-sharing-declined)

[Syntax](#syntax-2)

[Parameters](#parameters-2)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4Qb5StoM6yQhUbCol9DL3A&oh=00_AfgPGwA3TX4NjCFEBH0sexfMK2fsZU0qHRI0CWWIH4Go-Q&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4Qb5StoM6yQhUbCol9DL3A&oh=00_AfiNi4TFFBiPzTYU0FgYi1VSWqJ8VWZQV52xX6vgefhH9w&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4Qb5StoM6yQhUbCol9DL3A&oh=00_Afgcn6IsHx121pNCKNMiwiYAok7xBgMFNWxVpa3O46XNIQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4Qb5StoM6yQhUbCol9DL3A&oh=00_Afi6-I_LwRUBwlX8kPzpf3IjI2b23WFpGbFp60Exf_5VEA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4Qb5StoM6yQhUbCol9DL3A&oh=00_AfhWyHGrd6-0UbORX3zw69YXvD91CSqNs_RAcGyAV0W-qA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0odf_ZmDX9TFlqYEG2Sw8t79TjJbGJS43SNIaFn-VaVz-Q7HeCKizIKNHoEhReaUx8d7LYL33UTKeeT_wPe9sO56iLVDxVQ8OsN7gOjaslmDrqAjnGjTVe3Xd30XNf30dPyTIfb0BQaOH6XLXh9w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)