![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsend-messages%2Flocation-request-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Solicitação de localização](/docs/whatsapp/cloud-api/guides/send-messages/location-request-messages)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)

  + [Address](/docs/whatsapp/cloud-api/messages/address-messages)
  + [Áudio](/docs/whatsapp/cloud-api/messages/audio-messages)
  + [Contacts](/docs/whatsapp/cloud-api/messages/contacts-messages)
  + [Document](/docs/whatsapp/cloud-api/messages/document-messages)
  + [Image](/docs/whatsapp/cloud-api/messages/image-messages)
  + [Interactive Call-To-Action URL](/docs/whatsapp/cloud-api/messages/interactive-cta-url-messages)
  + [Interactive List](/docs/whatsapp/cloud-api/messages/interactive-list-messages)
  + [Interactive product carousel](/docs/whatsapp/cloud-api/messages/interactive-product-carousel-messages)
  + [Interactive media carousel](/docs/whatsapp/cloud-api/messages/interactive-media-carousel-messages)
  + [Interactive Reply Buttons](/docs/whatsapp/cloud-api/messages/interactive-reply-buttons-messages)
  + [Location](/docs/whatsapp/cloud-api/messages/location-messages)
  + [Solicitação de localização](/docs/whatsapp/cloud-api/guides/send-messages/location-request-messages)
  + [Reação](/docs/whatsapp/cloud-api/messages/reaction-messages)
  + [Sticker](/docs/whatsapp/cloud-api/messages/sticker-messages)
  + [Modelo](/docs/whatsapp/cloud-api/guides/send-message-templates)
  + [Text](/docs/whatsapp/cloud-api/messages/text-messages)
  + [Video](/docs/whatsapp/cloud-api/messages/video-messages)
  + [Confirmações de leitura](/docs/whatsapp/cloud-api/guides/mark-message-as-read)
  + [Contextual replies](/docs/whatsapp/cloud-api/guides/send-messages/contextual-replies)
  + [Typing indicators](/docs/whatsapp/cloud-api/typing-indicators)
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
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Location request messages](#location-request-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Webhook syntax](#webhook-syntax)

[Webhook parameters](#webhook-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Example webhook](#example-webhook)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/guides/send-messages/location-request-messages/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 3 de nov
Atualização em Português (Brasil): 22 de mai

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Location request messages

Location request messages display **body text** and a **send location button**. When a WhatsApp user taps the button, a location sharing screen appears which the user can then use to share their location.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/411712787_1346691626211128_4092487602815472288_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=UE9p7A39V8AQ7kNvwHcZ80e&_nc_oc=Adkage7JuowtW-zpMEUAusSPajn5GOQNBSueqY6mQvdn6VDy4mS1moHpMJ3bVhh_SUc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_Afi95azXy_loKznGMaLklaPeNulKEt2B4PH90Bahic92yw&oe=6940656A)

Once the user shares their location, a **messages** webhook is triggered, containing the user's location details.

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a location request message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "type": "interactive",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "interactive": {
    "type": "location_request_message",
    "body": {
      "text": "<BODY_TEXT>"
    },
    "action": {
      "name": "send_location"
    }
  }
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BODY_TEXT>`  *String* | **Required.**  Message body text. Supports URLs.  Maximum 1024 characters. | `Let's start with your pickup. You can either manually *enter an address* or *share your current location*.` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Webhook syntax

When a WhatsApp user shares their location in response to your message, a **messages** webhook is triggered containing the user's location details.

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
              "display_phone_number": "<WHATSAPP_BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<WHATSAPP_USER_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "<WHATSAPP_BUSINESS_PHONE_NUMBER>",
                  "id": "<WHATSAPP_CONTEXT_MESSAGE_ID>"
                },
                "from": "<WHATSAPP_USER_ID>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<TIMESTAMP>",
                "location": {
                  "address": "<LOCATION_ADDRESS>",
                  "latitude": <LOCATION_LATITUDE>,
                  "longitude": <LOCATION_LONGITUDE>,
                  "name": "<LOCATION_NAME>"
                },
                "type": "location"
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

## Webhook parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<LOCATION_ADDRESS>`  *String* | Location address.  This parameter will only appear if the WhatsApp user chooses to share it. | `1071 5th Ave, New York, NY 10128` |
| `<LOCATION_LATITUDE>`  *Number* | Location latitude in decimal degrees. | `40.782910059774` |
| `<LOCATION_LONGITUDE>`  *Number* | Location longitude in decimal degrees. | `-73.959075808525` |
| `<LOCATION_NAME>`  *String* | Location name.  This parameter will only appear if the WhatsApp user chooses to share it. | `Solomon R. Guggenheim Museum` |
| `<TIMESTAMP>`  *String* | UNIX timestamp indicating when our servers processed the WhatsApp user's message. | `1702920965` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |
| `<WHATSAPP_BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | WhatsApp business phone number's display number. | `15550783881` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER>`  *String* | WhatsApp business phone number. | `15550783881` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_CONTEXT_MESSAGE_ID>`  *String* | WhatsApp message ID of message that the user is responding to. | `wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1QjJGRjI1RDY0RkE4Nzg4QzcA` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp message ID of the user's message. | `wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQTRCRDcwNzgzMTRDNTAwRTgwRQA=` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user's WhatsApp ID. | `16505551234` |
| `<WHATSAPP_USER_NAME>`  *String* | WhatsApp user's name. | `Pablo Morales` |

## Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "type": "interactive",
  "to": "+16505551234",
  "interactive": {
    "type": "location_request_message",
    "body": {
      "text": "Let'\''s start with your pickup. You can either manually *enter an address* or *share your current location*."
    },
    "action": {
      "name": "send_location"
    }
  }
}'
```

## Example response

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "+16505551234",
      "wa_id": "16505551234"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBJCNUQ5RUNBNTk3OEQ2M0ZEQzgA"
    }
  ]
}
```

## Example webhook

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
            "contacts": [
              {
                "profile": {
                  "name": "Pablo Morales"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "15550783881",
                  "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1QjJGRjI1RDY0RkE4Nzg4QzcA"
                },
                "from": "16505551234",
                "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQTRCRDcwNzgzMTRDNTAwRTgwRQA=",
                "timestamp": "1702920965",
                "location": {
                  "address": "1071 5th Ave, New York, NY 10128",
                  "latitude": 40.782910059774,
                  "longitude": -73.959075808525,
                  "name": "Solomon R. Guggenheim Museum"
                },
                "type": "location"
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

[Location request messages](#location-request-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Webhook syntax](#webhook-syntax)

[Webhook parameters](#webhook-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Example webhook](#example-webhook)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfjkLRzm8sMzOEGGOPGs5TQmMYHcbJYV_M-uxO_ph4ouTw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfgvJByjBWREzDsRGKQqczSev4kCUXJ2r0MYAxqQUY4EWg&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfiTcHnrATUM9Tq-v-wwgiTt7cvpPLKVa8GJKR3l0jm8ng&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3JDxB8nNk7UJd0l8G3jJfU_YJ6T8WT_1LYKFk_eOBXI9GDuPDcpPmkRNFafA6YIsAH-3cTmqe-36eitEhlqSQ-w4huZYnIc6znvgW-S7Pz2pVlpx8AsVQSsa1CMNuUqrk57TLxpvZftmkcomwA2A)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_Afh9Y9tcp7lMIZOv7_dSOnlvFhISX6oWhOqEkQN1r_RTcQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1FAeY7N9tNgOaSZ97TD9_YvcvzmFHrFAkgb6FVzxeIZ1GuwWaY3--zi50ayxJl8sTeiSKuLZSjtNr3fKlOh0uRjMzNQ4bnYNQa72S7FDAuVdn-nGB7nttNZQFAtQYqJBe1ZnIRMFivqlSBqKZKHw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfhDGhxMkRg42ZKRnHBd9cB84lEvX6loPu9O9UOIcrRmDw&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1Ljjr-LSIYwf99oTR1xsxayUI3b717inb_Hbipt48yydtdR5KS-TtPvxaSpU0NxMxBxUHSpxrrUdvrQjPhi5lVFNjWpttwdbZNGiyikvQMUcCHsKqAJCwBsGBxppHtguROIERlnopPgRgtNwQmqQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfhApUMKnRMo8FOtYy0iaf7tD7Id_PZOPYm1eHDoPxjmFg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2GWV2XwQckWbF2h8iJRnpydojoDabJQZardhFzjLGijnLIblIe1qbE2R1OgH9h3rpYoXGZvjQmianPMZx43nCspXyLZEVnD4_1RXlmytgXYNJsNzgCO_IrCnMnHPr2xwsol-ecYzB56NgRDYAx6Q)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3_VFFjb55bXtDcEBVZ22jdTOdFPhAaUXUDnoe1LbhK6Gyri8KDP54gBqdCLbDuUUB8h9XqmWGhAk8mVVqv3yTIs97lvG-ljlIZBr3wD_8TzF8zeCxO2W_gtN-Z6BHA-WMlX6zBsBFyrermRUHjEA)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1N1ukC2_540TR0Jks8Xbz-NXXfJiTN-s8pBJ87mPa3TLMYmKl98LvIRXFo1NI5dhvrgFKG_52E4UvQuU8fS8yao8WGbBEgLbmcj_6Du-c0_f7ahMY0OpLzgFdReQHmZubLK2eTv0Z9y_akvjOSLQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_Afj6Ljzeowomht6yIqnou_EcTWn7kiz0n55kawIPV6Hvfg&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfhLvpuWf1QNkwlsQ_UWEeUdFiGGuhy2faaTLdjb7pJwFw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2yoXR8C9-AunEOyYwcywTMh7D4EPgS7CS22-dmbGl00qtaJpsIzWpS4wwX1ix7tksWQ3NF5XitN3T6S-BByoV4n1It0RDtCZSDxG_k6xvg4s7-kzKom4KNQlr51CNGD-vdlp-dYi_FGWKKkeHDXg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_Afi5-fn_TSclRDAQJNnOCeFCU5HPTp6dqN3Rv3SalHai7w&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0tE_zsZLDNAA17qdN6a-Os7c2JNyJn2Ulh-WvoG9Msw9W43c8yzRXkicVrzs4R5pHw9Yj6zQ34BMsohbTHqMZ797avf9epnC4Up5X-13oKJPwDtQnHOzWP_ErvCsLkXhoHCGJGkhsUuv_-yWNNgg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_AfijaH0oIbnDmqB00oHyWf2BPucV9V8JatwSehgFSay-qw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0MAXNoCdhOwQWalYFEtQSf0VHmzdZ3UcwDMl2qa4I8_aI5MqZdAWdO3Z1SlbGyTeLz79oKPET46sTtuENfbfdOM8R2kEi8XkL5WoTpeFmfc1VXPk0SxJZSffDFTaSGYObInrJApXXNagfYcfMH1A)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=MQaMZGy71fO28uxxiOZHew&oh=00_Afjkb2I_6XawCuPWNl2xbFw4uqok0gZx08SRfTblU4lYeA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT28aDXm-A2ZJCWsZ49XaUHt0Pfddj3WvygEsw1KegPOcz7lHBNUAY9xEs0lTDPGqGlAjDf8uRcBKtHxltymdy6FCN2iuKDfXddBEcQIEQKucmsVnigqu42rSPYFaQyADZhNcOtJJce-1x1wbEVsLg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT02RHq3vDabpqumTTpCg3_L51u-FpPWWhS7ZcMMcABh-tcaQaqQbllSxwBU5ceRFs2z8GjW0poOwtdTYcKGHyMvOFf1Xx1QchqjpPaOH9_5-ZnyrtZULWuHt2QL51eXsZUOh0slruzyfnQ4r5h7Yw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)