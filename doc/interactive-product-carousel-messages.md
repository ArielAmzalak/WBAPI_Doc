![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Finteractive-product-carousel-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Interactive product carousel](/docs/whatsapp/cloud-api/messages/interactive-product-carousel-messages)

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

[Interactive product carousel messages](#interactive-product-carousel-messages)

[How to build a product carousel message](#how-to-build-a-product-carousel-message)

[The card object](#the-card-object)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Card Object Parameters](#card-object-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Interactive product carousel messages

This message type will be available for delivery to WhatsApp users on November 11.

The interactive product carousel message enables businesses to send horizontally scrollable product cards within WhatsApp conversations, allowing users to browse and engage with products directly in-thread.

This format integrates with the Product Catalog and supports Single Product Message (SPM) actions on each card, providing a seamless and interactive shopping experience via the WhatsApp Business APIs and mobile clients

## How to build a product carousel message

The product carousel message contains a `card` object. You must add 2 card objects to your message, and can add a maximum of 10. Each card exists in a `cards[]` array and must be given a `"card_index"` value of `0` through `9`.

The type of each card must be set to `"product"`, and each card must reference the same `"catalog_id"`.

You must add a message body to the message, and no header, footer, or buttons are allowed.

Lastly, each card must specify the product and catalog identifiers `"product_retailer_id"` (string, required) and `"catalog_id"`.

### The `card` object

```
...
{
  "card_index": 0,
  "type": "product",
  "action": {
    "product_retailer_id": "abc123xyz",
    "catalog_id": "123456789"
}
...
```

## Request Syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<WHATSAPP_USER_PHONE_NUMBER>",
    "type": "interactive", // must be interactive
    "interactive": {
      "type": "carousel", // must be carousel
      "body": {
        "text": "<MESSAGE_BODY_TEXT>"
      },
      "action": {
        "cards": [
          {
            "card_index": 0,
            "type": "product",
            "action": {
              "product_retailer_id": "abc123xyz",
              "catalog_id": "123456789"
            }
          }
          // additional product cards
        ]
      }
    }
  }'
```

## Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<MESSAGE_BODY_TEXT>`  *String* | **Required.**  Maximum 1024 characters. | `Which option do you prefer?` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Card Object Parameters

```
...
{
  "card_index": <INDEX>,
  "type": "product",
  "action": {
    "product_retailer_id": "<PRODUCT_RETAILER_ID>",
    "catalog_id": "<CATALOG_ID>"
}
...
```

| Placeholder | Description | Sample value |
| --- | --- | --- |
| `<INDEX>`   *Integer* | **Required**   Unique index for each card (0-9). Must not repeat within the message. | `2` |
| `<PRODUCT_RETAILER_ID>`   *String* | **Required**   The unique retailer ID of the product in the catalog. | `"0JkSUu4qizuXv"` |
| `<CATALOG_ID>`   *String* | **Required**   The unique ID of the catalog containing the product. | `"Lq1ZtoWL5OkljTerAW"` |

## Example Request

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "1234567890",
  "type": "interactive",
  "interactive": {
    "type": "carousel",
    "body": {
      "text": "Check out our featured products!"
    },
    "action": {
      "cards": [
        {
          "card_index": 0,
          "type": "product",
          "action": {
            "product_retailer_id": "abc123xyz",
            "catalog_id": "123456789"
          }
        },
        {
          "card_index": 1,
          "type": "product",
          "action": {
            "product_retailer_id": "def456uvw",
            "catalog_id": "123456789"
          }
        }
      ]
    }
  }
}
```

## Example Response

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
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Interactive product carousel messages](#interactive-product-carousel-messages)

[How to build a product carousel message](#how-to-build-a-product-carousel-message)

[The card object](#the-card-object)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Card Object Parameters](#card-object-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfjfoeoKct6d34Yjp4mZp9NloIPH_Rr9fXOPzIw5XzVAww&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfhKZVDHl8zsDV5N-6BDdf4lw1VEUIJWfNfI1Ph8P5kM-A&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfjmVRnVo2MArgPlTHRME5Fd8sRZGPpIHaLsXh57C54OAQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0goUCS5fo9S3Z-ZFwJQvCsBnVVlUBzuS3qetRhtL5IUxb2qQmAoaq0sWlPVMmcAFd8LfRUY6xYsus0CwXU5wiqILOtm1rvaOSyk_IVH-CUGfdrD8KbIAhnfNXd0HEfNV_LDmZDiFeyFbQuQ7HCww)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfhMTG1X4HgMm1kIyU8VhdwlG5LJi9mSDWtZvWle5jEM4w&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT18lHRe9Ok_1ghkK2aJ72ZsgH96bdUW_WGRyU167kd6krynUKim-1XS1KFN6xGLLG2V4gqI_D6Dn2VMcC7gOf4Ekbr40cCNCRIDQYllwlba-pre_ImGBRHT31C67qzqjGn8MQ1dpV-hBs7Obn3vzg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfjF04G6mUWzqs5eb8F0AA5YTvlgM0spL-WiWIL3xvjxlA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2vImOdjNxWgI9FEBgS5Pxyab7Jq4IbvwEhS1oDl18Pkay1WMHF6CO9A-5MRbd-9YQ-OZpS5UmXqDdsML1-BGqy8HJbecUv8KoqhCbsu4Lpcbx9_E4Dx_89C-ij3uAiZY77TewWWcOs0zWIuiYudQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfiyVgy53JFXkwmsxEM_B4UqAMe_FV1Z8wF9fJRxnPFYSw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0tdmy-LtJHAImQ872muLw8DwJ069poIHRhJsZ4ost73a_PT3RyRuGiD3MYgacOfxoA0FeRw0u0ZiPlanMm1IEWZ7Lyye5gwK5ymqvP1OEvSirDAs2D40xzCKMAoNjikoGOBPLU3x5kkiozeH5HOA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0Fehkof-LfQBYB5CVFDrIQq3mCtF36vjDA5Qx7umNRByOVNxmqkMPtHGJnVgYg-9M_Err6klyRWBNUFDhtR8XK5UHSBO1z_07KX9S1jQGiVAF7G0yM72ppyku8LeJTuOxY6QjbkHelDZ8XQxzHWw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3QUJFfURO3chD6S97L-jYo8uh1-lCOfcG9UmIeEjFdWw9HEpblcdKQDQkhKWRecyqX5kkZFc6_qSZrmWCwk_5UF9gUETuc3m7W0pIXFWXazYARhaILYLp9X2ONh37tEmbjgGTDyy63MMXFrctM5Q)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfgZDqZrWoaRGKMQFR-Czav9EFRMnfacbtjr-sY5TKb5Eg&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfjDTwgJsAWaeqAFNC8JN9NsEWz5NpUtLyFQ9lHqdB8F1w&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3oQ-MngL7yYpV3QSwKhBymVzd8PrNAhIWcKK4Nzapazke4idE9lSBGAbdezss8J1Kn6E_yLVeR_kgpCuePNjHJpjLSND3hZdIy8iMVPuR_JXT0Xhrbuc7d5rHvjmgZS-F5dBAdOA0NAsggi5AQvA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_Afg0vcLt50tOkRibq212TCZmQzWW5bpy-1KV4VKgHJx0Cg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3pHVrI19Wi4vnbroxV9M5uGSZPFTTcKXEhvM9bIoT7b951P1RN9WZ2pxWtQUSD8myqX7VGuv7-elFEQSuSGNKTBKt_6VgEavi4g_2J5-FeHFFO-ZyEIozysi0Oo1glUMcz_-Z1udTDvYRHQ1JrGg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_Afj7PEW0QO9qlDqJyrOfcmYbBSB23sckHhVm67-2CDH39A&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0MAB249SWdlzmsnVMsAPshT8XUjc5YzNbq_K0CE8Z9xkb9AYoM6naB7Fh3FwCxw-_KstNDkbzPVZCbLc0WQK1-9MyUQ7zX-B7rvr90A2zDjyn2Qv3jjsP2BWupDuTg4fPhrYTehFkuTfFFUXhmrg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=ZXQ2Dprslck5_AAhBrhbWg&oh=00_AfjIHEJMQktNMOVkY0URKGJ0dKB4O9HqjwM3ddU5dLituw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0EiHta_tuj-9Mp_5PEa_MtYqM99VUbU8RmvsOIQMnxGgxdfq8mUKShMBPJENEMGJaSHPO7m3KujMJ7OrUnGrSiIWsksPV-Sncl9qTQjnsYMm1npvA-pnSJRw2MIAihuc-AMuc7WTPCsmQvEe-VWw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3npNd78O7eXbRPJ4waqjM-snpcX0_Zb7ESt2nSQQr0pC2IlWfhytVoiCpyrnnnSeScQBM47-u2oImGB6Jo3AXQwXktWapCcAikEVR4m-L10pjhWIU9KP-8NU5rsNSyXE1_OXZ5BqHzLI-eDYWGEA)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)