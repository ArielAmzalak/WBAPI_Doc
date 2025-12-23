![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fmessages%2Ftext%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)[texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)

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

[Referência de webhook de messages de texto](#refer-ncia-de-webhook-de-messages-de-texto)

[Gatilhos](#gatilhos)

[Sintaxe](#sintaxe)

[Parâmetros](#par-metros)

[Exemplos](#exemplos)

[Mensagem de texto](#mensagem-de-texto)

[Botão Conversar com a empresa](#bot-o-conversar-com-a-empresa)

[Anúncio de clique para o WhatsApp](#an-ncio-de-clique-para-o-whatsapp)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Referência de webhook de `messages` de texto

Esta referência descreve os eventos de gatilho e o conteúdo da carga do webhook de **mensagens** da conta do WhatsApp Business para mensagens contendo apenas texto.

## Gatilhos

* Um usuário do WhatsApp envia uma mensagem de texto para um número de telefone do WhatsApp Business.
* Um usuário do WhatsApp encaminha uma mensagem de texto para um número de telefone comercial.
* Um usuário do WhatsApp usa o botão **Conversar com a empresa** em uma [mensagem de catálogo, de produto único ou de vários produtos](/docs/whatsapp/cloud-api/guides/sell-products-and-services) para enviar uma mensagem à empresa.
* Um usuário do WhatsApp envia um SMS para a empresa por meio de um [anúncio de clique para o WhatsApp](https://www.facebook.com/business/help/447934475640650?id=371525583593535) (um anúncio com **destino de mensagem** do WhatsApp).

## Sintaxe

```
{ "object": "whatsapp_business_account", "entry": [ { "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>", "changes": [ { "value": { "messaging_product": "whatsapp", "metadata": { "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>", "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>" }, "contacts": [ { "profile": { "name": "<WHATSAPP_USER_PROFILE_NAME>" }, "wa_id": "<WHATSAPP_USER_ID>", "identity_key_hash": "<IDENTITY_KEY_HASH>" <!-- only included if identity change check enabled --> } ], "messages": [ { "from": "<WHATSAPP_USER_PHONE_NUMBER>", "id": "<WHATSAPP_MESSAGE_ID>", "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>", "type": "text", "text": { "body": "<MESSAGE_TEXT_BODY>" }, <!-- only if message originated from a "Message business" button --> "context": { "from": "<BUSINESS_DISPLAY_PHONE_NUMBER>", "id": "<CONTEXTUAL_WHATSAPP_MESSAGE_ID>", "referred_product": { "catalog_id": "<PRODUCT_CATALOG_ID>", "product_retailer_id": "<PRODUCT_ID>" } }, <!-- only if message forwarded to business by a user --> "context": { "forwarded": true, <!-- only included if forwarded 5 times or less --> "frequently_forwarded": true <!-- only included if forwarded more than 5 times --> }, <!-- only included if message sent via a Click to WhatsApp ad --> "referral": { "source_url": "<AD_URL>", "source_id": "<AD_ID>", "source_type": "ad", "body": "<AD_PRIMARY_TEXT>", "headline": "<AD_HEADLINE>", "media_type": "<AD_MEDIA_TYPE>", "image_url": "<AD_IMAGE_URL>", "video_url": "<AD_VIDEO_URL>", "thumbnail_url": "<AD_VIDEO_THUMBNAIL>", "ctwa_clid": "<AD_CLICK_ID>", <!-- omitted if message sent via a WhatsApp Status ad placement --> "welcome_message": { "text": "<AD_GREETING_TEXT>" } } } ] }, "field": "messages" } ] } ] }
```

## Parâmetros

| Espaço reservado | Descrição | Valor de exemplo |
| --- | --- | --- |
| `<AD_CLICK_ID>`  *String* | Click to WhatsApp ad click ID.  The `ctwa_clid` property is omitted entirely for messages originating from an ad in WhatsApp Status ([WhatsApp Status ad placements](https://www.facebook.com/business/help/1074444721456755)). | `Aff-n8ZTODiE79d22KtAwQKj9e_mIEOOj27vDVwFjN80dp4_0NiNhEgpGo0AHemvuSoifXaytfTzcchptiErTKCqTrJ5nW1h7IHYeYymGb5K5J5iTROpBhWAGaIAeUzHL50` |
| `<AD_GREETING_TEXT>`  *String* | Click to WhatsApp ad greeting text. | `Hi there! Let us know how we can help!` |
| `<AD_HEADLINE>`  *String* | Click to WhatsApp ad headline. | `Chat with us` |
| `<AD_ID>`  *String* | Click to WhatsApp ad ID. | `120226305854810726` |
| `<AD_IMAGE_URL>`  *String* | Click to WhatsApp ad image URL. Only included if the ad is an image ad. | `https://scontent.xx.fbcdn.net/v/t45.1...` |
| `<AD_MEDIA_TYPE>`  *String* | Click to WhatsApp ad media type. Values can be:  `image` — Indicates an image ad.  `video` — Indicates a video ad. | `image` |
| `<AD_PRIMARY_TEXT>`  *String* | Click to WhatsApp ad primary text. | `Summer succulents are here!` |
| `<AD_URL>`  *String* | Click to WhatsApp ad URL. | `https://fb.me/3cr4Wqqkv` |
| `<AD_VIDEO_THUMBNAIL>`  *String* | Click to WhatsApp ad video thumbnail URL. Only included if ad is a video ad. | `https://scontent.xx.fbcdn.net/v/t45.3...` |
| `<AD_VIDEO_URL>`  *String* | Click to WhatsApp ad video URL. Only included if ad is a video ad. | `https://scontent.xx.fbcdn.net/v/t45.2...` |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<CONTEXTUAL_WHATSAPP_MESSAGE_ID>`  *String* | ID da mensagem do WhatsApp que o usuário usou para acessar o botão Conversar com a empresa. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGA9wcm9kdWN0X2lucXVpcnkA` |
| `<IDENTITY_KEY_HASH>`  *String* | Identity key hash. Only included if you have enabled the [identity change check](/docs/whatsapp/cloud-api/reference/phone-numbers#identity-change-check) feature. | `DF2lS5v2W6x=` |
| `<MESSAGE_TEXT_BODY>`  *String* | Corpo de texto da mensagem. | `Is it available in another color?` |
| `<PRODUCT_CATALOG_ID>`  *String* | [Identificação do catálogo de produtos](/docs/whatsapp/cloud-api/guides/sell-products-and-services). | `194836987003835` |
| `<PRODUCT_ID>`  *String* | [ID do produto](/docs/whatsapp/cloud-api/guides/sell-products-and-services). | `di9ozbzfi4` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *String* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user ID. Note that a WhatsApp user's ID and phone number may not always match. | `16505551234` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | WhatsApp user phone number. This is the same value returned by the API as the `input` value when sending a message to a WhatsApp user. Note that a WhatsApp user's phone number and ID may not always match. | `+16505551234` |
| `<WHATSAPP_USER_PROFILE_NAME>`  *String* | WhatsApp user's name as it appears in their profile in the WhatsApp client. | `Sheena Nelson` |

## Exemplos

### Mensagem de texto

Este exemplo descreve uma mensagem de texto enviada por um usuário do WhatsApp (que digitou algo no campo de conversa e enviou).

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
                  "name": "Sheena Nelson"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "from": "16505551234",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTRBNjU5OUFFRTAzODEwMTQ0RgA=",
                "timestamp": "1749416383",
                "type": "text"
                "text": {
                  "body": "Does it come in another color?"
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

### Botão Conversar com a empresa

Este exemplo descreve uma mensagem de texto enviada por um usuário do WhatsApp que usou o botão **Conversar com a empresa** ao [visualizar um único produto](/docs/whatsapp/cloud-api/guides/sell-products-and-services) para enviar a mensagem.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "419561257915477",
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
                  "name": "Sheena Nelson"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "15550783881",
                  "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGA9wcm9kdWN0X2lucXVpcnkA",
                  "referred_product": {
                    "catalog_id": "194836987003835",
                    "product_retailer_id": "di9ozbzfi4"
                  }
                },
                "from": "16505551234",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTA2NTUwRkNEMDdFQjJCRUU0NQA=",
                "timestamp": "1750016800",
                "text": {
                  "body": "Is this still available?"
                },
                "type": "text"
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

### Anúncio de clique para o WhatsApp

Este exemplo descreve um SMS enviado por um usuário do WhatsApp que tocou em um [anúncio de clique para o WhatsApp](https://www.facebook.com/business/help/447934475640650) e enviou a mensagem gerada para a empresa.

Para mensagens originadas de um anúncio no Status do WhatsApp ([posicionamentos de anúncio no Status do WhatsApp](https://www.facebook.com/business/help/1074444721456755)) a propriedade `referral.ctwa_clid` é omitida por completo.

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
                  "name": "Sheena Nelson"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "referral": {
                  "source_url": "https://fb.me/3cr4Wqqkv",
                  "source_id": "120226305854810726",
                  "source_type": "ad",
                  "body": "Summer Succulents are here!",
                  "headline": "Chat with us",
                  "media_type": "image",
                  "image_url": "https://scontent.xx.fbcdn.net/v/t45.1...",
                  "ctwa_clid": "Aff-n8ZTODiE79d22KtAwQKj9e_mIEOOj27vDVwFjN80dp4_0NiNhEgpGo0AHemvuSoifXaytfTzcchptiErTKCqTrJ5nW1h7IHYeYymGb5K5J5iTROpBhWAGaIAeUzHL50",
                  "welcome_message": {
                    "text": "Hi there! Let us know how we can help!"
                  }
                },
                "from": "16505551234",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUQ0N0VFMDA2MTQ0RkJFNkNDNAA=",
                "timestamp": "1750275992",
                "text": {
                  "body": "Can I get more info about this?"
                },
                "type": "text"
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

[Referência de webhook de messages de texto](#refer-ncia-de-webhook-de-messages-de-texto)

[Gatilhos](#gatilhos)

[Sintaxe](#sintaxe)

[Parâmetros](#par-metros)

[Exemplos](#exemplos)

[Mensagem de texto](#mensagem-de-texto)

[Botão Conversar com a empresa](#bot-o-conversar-com-a-empresa)

[Anúncio de clique para o WhatsApp](#an-ncio-de-clique-para-o-whatsapp)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xpWfsfe7rIvzOeQhhNxSrw&oh=00_AfjqxTQoCFviOFH_gJ1yNxDs_zQ-LoTwwV54ERjM2xzk_A&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xpWfsfe7rIvzOeQhhNxSrw&oh=00_AfjpqchDbH3hXHv5noyEDaiiSsoLCXalO77fBbzBTnjKVQ&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xpWfsfe7rIvzOeQhhNxSrw&oh=00_AfjZi9EqBYQEUhuI-8N_qRVaKFjaSwA_AS3w2eEprmJq7w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xpWfsfe7rIvzOeQhhNxSrw&oh=00_AfggAxXzD4BtIsuAnp7fqeh4bKGcL5jbJJwTuH3htBEw5w&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xpWfsfe7rIvzOeQhhNxSrw&oh=00_Afi4uVWVb50SKDR8n6PNxtZJoSQo8l4-quCzW2I1rkm3MA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0UkE1IGyngVaksr-_h11YwSNozx-8GcqbGY-Gr1uuz84jyMbWA_ZP1B69HG_2gPm95V1_6_RFI15SpCEKY-EMQnGMkaD1VEGEF5-bnO2JqJysZpUnH967SrH4APYILcfMiglx8ssJon7wxVVcnRg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)