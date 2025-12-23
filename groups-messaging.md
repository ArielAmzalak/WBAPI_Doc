![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Fgroups-messaging%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Group messaging](#group-messaging)

[Overview](#overview)

[Subscribe to groups metadata webhooks](#subscribe-to-groups-metadata-webhooks)

[Send group message](#send-group-message)

[Example group message send](#example-group-message-send)

[Webhooks](#webhooks)

[Receive group messages](#receive-group-messages)

[Webhooks](#webhooks-2)

[Pin and unpin group message](#pin-and-unpin-group-message)

[Limits](#limits)

[Request Syntax](#request-syntax)

[Request body](#request-body)

[Body parameters](#body-parameters)

[Response body](#response-body)

[Webhooks](#webhooks-3)

[Group message status webhooks](#group-message-status-webhooks)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Group messaging

## Overview

This document provides comprehensive information on the APIs and webhooks available for sending and receiving messages within groups. It details support for various message types, including:

* Text messages
* Media messages
* Text-based templates
* Media-based templates

## Subscribe to groups metadata webhooks

In order to receive webhook notifications for metadata about your groups, please subscribe to the following webhook fields:

* `group_lifecycle_update`
* `group_participants_update`
* `group_settings_update`
* `group_status_update`

For a full reference of webhooks for the Groups API, please visit our [Webhooks for Groups API reference](/docs/whatsapp/cloud-api/groups/webhooks).

## Send group message

To send a group message, use the existing send message endpoint:

`POST /<BUSINESS_PHONE_NUMBER_ID>/messages`

This endpoint has been extended to support group messages in the following way:

* The `recipient_type` field now supports `group` as well as `individual`.
* The `to` field now supports the `group ID` that is obtained when using the Groups API.

### Example group message send

```
curl 'https://graph.facebook.com/v24.0/756079150920219/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAAu...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "group",
  "to": "Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD",
  "type": "text",
  "text": {
      "preview_url": true,
      "body": "This is another destination option: https://www.luckytravel.com/DDLmU5F1Pw"
  }
}'
```

### Webhooks

#### Group message sent example

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
                   "recipient_id": "<GROUP_ID>",
                   "recipient_type": "group",
                   "status": "sent",
                   "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
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

#### Group message failed example

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
                   "recipient_id": "<GROUP_ID>",
                   "recipient_type": "group",
                   "status": "failed",
                   "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                   "errors": [
                     {
                       "code": "<ERROR_CODE>",
                       "title": "<ERROR_TITLE>",
                       "message": "<ERROR_MESSAGE>",
                       "error_data": {
                         "details": "<ERROR_DETAILS>",
                       },
                       "href": "/docs/whatsapp/cloud-api/support/error-codes/"
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

## Receive group messages

You can use the following webhooks to receive statuses on messages received in the group.

The `message` object includes a `group_id` field to indicate this is a group message. The `from` field in the `message` object and the contact object point to the same participant who sends this message.

### Webhooks

#### Receive group message webhook sample

```
{
  "object": "whatsapp_business_account",
  "entry": [{
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [{
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                  "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
                  "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
              },
              "contacts": [{
                  "profile": {
                    "name": "<WHATSAPP_USER_NAME>"
                  },
                  "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>"
                }],
              "messages": [{
                  "from": "<GROUP_PARTICIPANT_PHONE_NUMBER>",
                  "group_id": "<GROUP_ID>",
                  "id": "<WHATSAPP_MESSAGE_ID>",
                  "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                  "text": {
                    "body": "<MESSAGE_BODY>"
                  },
                  "type": "text"
                }]
          },
          "field": "messages"
        }]
  }]
}
```

#### Receive unsupported group message webhook sample

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
                   "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              },
              "contacts": [
                {
                  "profile": {
                    "name": "<WHATSAPP_USER_NAME>"
                  },
                  "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>"
                }
              ],
              "messages": [
                {
                  "from": "<GROUP_PARTICIPANT_PHONE_NUMBER>",
                  "group_id": "<GROUP_ID>",
                  "id": "<WHATSAPP_MESSAGE_ID>",
                  "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                  "errors": [
                    {
                      "code": 130501,
                      "message": "Message type is not currently supported",
                      "title": "Unsupported message type",
                      "error_data": {
                        "details": "<ERROR_DETAILS>"
                      }
                    }
                  ],
                  "type": "unsupported"
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

## Pin and unpin group message

Pinning a message highlights its relevance.

The display order of the pinned messages is based on the chronological order of parent messages, newest first. If three messages are already pinned when a new pin request is made, the oldest pinned message will be automatically unpinned.

### Limits

1. When calling the API, only one message can be pinned at a time.
2. Only the group admin can pin or unpin messages.
3. A maximum of 3 pinned messages can exist at any time.

### Request Syntax

`POST /<BUSINESS_PHONE_NUMBER_ID>/messages`

**Note: You will receive an error in the sync response if the `recipient_type` and `to` type do not match.**

### Request body

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "group",
  "to": "<GROUP_ID>",
  "type": "pin",
  "pin": {
    "type": "<PIN_OPERATION>",
    "message_id": "<MESSAGE_ID>",
    "expiration_days": "<EXPIRATION>"
  }
}
```

### Body parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required**  The group in which you are pinning a message. | `Y2FwaV9ncm91cDoxOTUwNTU1MDA3OToxMjAzNjMzOTQzMjAdOTY0MTUZD` |
| `<PIN_OPERATION>`  *String* | **Required**  The pinning operation you are performing on the group.  Can either be `"pin"` or `"unpin"` | `pin` |
| `<MESSAGE_ID>`  *String* | **Required**  A unique identifier for the message you are pinning or unpinning in the group. | `wamid.HBgLM...` |
| `<EXPIRATION>`  *Integer* | **Required when `PIN_OPERATION` is `pin`**   Pin duration in days. Can be 1 to 30 days. | `4` |

### Response body

```
      {
        "messaging_product": "whatsapp",
        "contacts": [
          {
            "input": "Y2FwaV9ncm91cDo....",
            "wa_id": "Y2FwaV9ncm91cDo...."
          }
        ],
        "messages": [
          {
            "id": "wamid.HBgLM..."
          }
        ]
  }
```

### Webhooks

Subscribe to the `messages` webhook topic to receive message status notifications. Standard sent and delivered statuses webhooks will be received for the `message_id` in the response.

[Learn more about the messages `status` webhook object here](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)

## Group message status webhooks

When you send messages to a group, you will receive a webhook when the message is delivered or read.

Instead of sending multiple webhooks for each status update, we will send an aggregated webhook.

This means that if you send a message and are set to receive several `read` or `delivered` statuses, we will send you a single, aggregated webhook that contains multiple `status` objects.

Each webhook you receive is only ever in reference to a single message sent to a single group and a single status type.

[Learn more about the Group Message Status webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-message-status-webhooks)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Group messaging](#group-messaging)

[Overview](#overview)

[Subscribe to groups metadata webhooks](#subscribe-to-groups-metadata-webhooks)

[Send group message](#send-group-message)

[Example group message send](#example-group-message-send)

[Webhooks](#webhooks)

[Receive group messages](#receive-group-messages)

[Webhooks](#webhooks-2)

[Pin and unpin group message](#pin-and-unpin-group-message)

[Limits](#limits)

[Request Syntax](#request-syntax)

[Request body](#request-body)

[Body parameters](#body-parameters)

[Response body](#response-body)

[Webhooks](#webhooks-3)

[Group message status webhooks](#group-message-status-webhooks)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfgiLXY9K7ADcKx7FCpF2K856AWULRGVeInVQZYm7MdGyg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfgLvWmcyIUV4tSG0fVbtOvaNX-hJQOkFpnTRuug1pgo8w&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfibAYHpuxSGGjDCN2wXjhLbyJFkq7tBIt7UbuRk9eWr0w&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0to0BMJHc9LwBSnq70I8MwjspveR6qHOQsDGwbUaLLRlYum_7LKZXw9LhuceTQcVhqYDaLkgsHvh1uUNDo_korhgpdKyfMxlmHGQLjHjDh4ZbK658UE3ybKVeSnGlTvJF48tItVV6Jz8fUmsoOOA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfgdwCjmaDge9c6dPmR9uzqBFX7JmfjctHVe0pYsNrHnsw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0JiM4UCNNNc7QTFhxAX91QtreVuZKnbCgw-k6gbKhNU8iTqvq1jm60zsd5kMTFBtPDTsy3olWnBTSXknch_2HaFfT5f_0Ba6AzbeWJa39tWcvAfkY7dtVS0Rj40m4AJxFQEcFBxCksWZQh0l3k1y8qDP60mTAqlCM)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfjyXbViyKyBo3MglJn336H35JlI51cwScYqzF9MX9driA&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3qQDiKAJHX1LtGLgSeSjff-_J4T0QQxOMUpVXConR8DofSKOqdWz7kveJrHfkBz1KsxBBlC1RNS0RYZOlIzr53nC8QIfOJWOMdpKGr4CPgVdxu6APylWNnm9Lp1eP88TnNr5ivL_XqmpLLaIjnLA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_Afjky2u_-52-63m5NOLeEeH9p5xgrPpgWKu8S1Tve99NZQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3R4IpBFBqmH48_oGxeAZUI-7zeIqhL1O6SPSi-3GaTKVxCnyNOWtQxqnnQiRqOeZ6A8fz3nHrxIyons5kRPww0O_x3hZSlgBqE6Jv4wTZys5e1LmOvUDBAa3PlbXvALu7XT1008sQSwbgXxx_p1A)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1N98yHLAjOLtK9B5iKFG1smE6wgEgDKzuzV6ViO4QCfYp4i8rzg8eicgbk-os0Uj78Xw6zvwRffCCioVJNKzLJxX365_Iaa9lEE_WzLlmdyHLmKWdqv2303MbzIXWV-nxJe91rppE5J5ArOfrbsA)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3e4GVDGKdV0NozBW8suDozjMA3t95wQANQqlvwYGnyablh432-0R6tjQYIsOzFPgAHtWGOtnScIa2EXMAOqGrGJe8vOQLZt1nKFwjbX9xunuMvltQnnm_Qsy02C4DxkrU1wNlbrd2VFUTnwyYeZxU-H9IhCYCFeQ8)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfhQ_2IIE5lV2XvONYrcrZDuxTHEyty9Oyf7Rzr6Eq5LPA&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_Afhs72fFZ_pInk0T_m3h6X3G__3rpXNhFzpLUeRSNHFhvw&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2w_TFm0aIbQP8CaGkAb2ci_Yr7h12w-vY2Ei1MiUNSQRpDJ3Hzkesjm8ehT72ZJ1QgNJdENjecx0vdkHFwdn0jppPs8ZAEj6iSXp7_0jyISheBGojgokEO6ZYecuTtocMn4rqCS2Wc7PCiFfPvMQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfhRGhNaE1vBa6u20cPVyF6LULTJQiK2n5waSDLDg-eofw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3rrWWw5b2gJFtMCKC_AL4UWBAB9hh7JRqzBk8GGB8DiOhc07zsMUI4_dmW9Y49Zlsvz5D7U7eH8ZG47AEYl__mPHdhdUctKTKlSwqWMDQ_klS5nExSVDgGIgQ-vEYoWYUoLLFrozxMGaNlxiKPFA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfgVqt8b6LI9-GHanIMLQgSun3WQkxfshY1HndRsfO9x9A&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT21SiAIBEFYd3_1cLFaKvlbllHq5A-TqilrqW_p5Th00zPlTxEdTyzDL6OQOqFBxpQnibEioyRvq0NIN2D_7nnf3CPMR7yGkLSvA4AnCUk__aH4VCtrx99kY_U942A4K59xydIVlBtOHt-C5iQQ3649i5Im0AqdUFw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vDq8fLbAOZNuD06LB44fPA&oh=00_AfhvhyOIWh0wrZpeoxdE-Yy6f5yhhU1gOt0pRWuC0aqxXw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0NUB2URBgJv8FWt1m8XSBCxT8_S7iEeiokfTcD9ay6DZZtraVOfVuG5Ove2RdkK3_gUQr_-DJim7ngTMExW5P4qzvZu7sJcDOiI-AJdBrcNpBvqPlY0ltJkScpjongEboDB5gAeJm_CKFaU4JNfQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2fVBCi3lBOMmFT--jDG-XjcvEGqUAfFeEuj0REkseynCZz5iGvo8MBx2AH3mgNtdg70-CgLUl6JDTiLvYR_X5dFnKRTFtocXkFEtRlnXZZNlfXVQ_7MpI6EkYuEJnxrDlKb925ghJ9X4-fXYGsGw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)