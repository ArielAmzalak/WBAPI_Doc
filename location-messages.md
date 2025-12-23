![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Flocation-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Location](/docs/whatsapp/cloud-api/messages/location-messages)

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

[Location messages](#location-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Location messages

Location messages allow you to send a location's latitude and longitude coordinates to a WhatsApp user.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440753150_1614554799358194_4095127988263974385_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=1YsIzRH0WXUQ7kNvwG7FBuP&_nc_oc=Adl5LrLKoOqCKVDjQLzLreYx7wWb6vytnhvqXOXpgjglu3_x8zPQeC5b8RH_z3teI7U&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_Afi3p5tlzB4Y0XPrs20wOU8-GavZiVFoRYW11aV7sPeQcQ&oe=69406AE1)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a location message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "location",
  "location": {
    "latitude": "<LOCATION_LATITUDE>",
    "longitude": "<LOCATION_LONGITUDE>",
    "name": "<LOCATION_NAME>",
    "address": "<LOCATION_ADDRESS>"
  }
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<LOCATION_ADDRESS>`  *String* | **Optional.**  Location address. | `101 Forest Ave, Palo Alto, CA 94301` |
| `<LOCATION_LATITUDE>`  *String* | **Required.**  Location latitude in decimal degrees. | `37.44216251868683` |
| `<LOCATION_LONGITUDE>`  *String* | **Required.**  Location longitude in decimal degrees. | `-122.16153582049394` |
| `<LOCATION_NAME>`  *String* | **Optional.**  Location name. | `Philz Coffee` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

Example request to send a location message with a name and address.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "location",
  "location": {
    "latitude": "37.44216251868683",
    "longitude": "-122.16153582049394",
    "name": "Philz Coffee",
    "address": "101 Forest Ave, Palo Alto, CA 94301"
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
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Location messages](#location-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfhKF-InzafdEM08CTv7uJkjG5sS4Svyx2BiH3iDZS-4lA&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfiNqs_1aq8EzaeqtCZYSa693JgqceJKlzYla5Y7vH5TaA&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfimSom_uzpRyFjHN6SGHDJncHo-XGw4easkdgEaAAsftA&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT12zScwFveEFWwfZmOVOeReuncsN0VDGXDMEQyxY54e2RhIbjHIlwazh811KHmqh9Rtw7zEa82T0s6nwuoIX5l-aexOWwEbBdTzQrPT61_HNKNDCdGVMx8DNc0sSU03_-1-7RkgZfkauS6j3VpYEg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_Afjpsms-XeTztwxvv05ALSjn2g59CT-bjAF53x7JO-ZYjg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT049NrEnlsGNoMit1NWVa5AprTGa5FaIrweUll5WeOhY9zMOt9Hti6whhVv24TAvBBNqoq01KsOx7cDAN8Vvnna4jchQqfdfHgCkfdSLWRe4qzCckAbbb8nJgR6VBrkURmuy-lp5a4kmFO_33AKOg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfhDhfXpJOBnzjg3EK2UGkSAGfMLnQC_yUOW_uimhY_a6A&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3ctuUTexwx8T3eIEwYevkkUlbup4P7Z9Tn0n0Daey2H32gt-dDH2vXdUPE7BowWKrWknPPkt5kCQm9hE-mligYHwEG_rRg5uB4cw8WoFkrbpPbWEk6hWhJq-F3yVmz4V2n8IaIOeEPZxf47loCVA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfitMHBjzVEeHNUoFKyxxpYsdydL3X5HFNHpbN-2_15EFg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3Y6sc4sNj5nt-OaswAV9UObcP00uTTm7leCNoHirC9nZwGEea_dD7VkqvIThjdaMGLSA83eKLLgBuXUA0ZNWpsEVo37efZdRRWzaBOg-YsUEzH9KUUCV2Kuqm4ln91sr-o-_XMwfY5yG7VbaWv7A)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT2QhIdTe6QBfuaeqN42nlav3l-GqgUse-MbcOo-m0mblPllU1wGjp0nwTT3BPaOxk8XhFYaoTAX8lhsoO5xq7sVwyYAUdBJtubk2M1et-MDVu4735fsKmwmmzSqMzEote6GR8QbdyiiKi8PC-x72g)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT02-5E86n_5DqQgQaWib8PVjmRmSKqQbMr8_adMh6ctd-_AGnW7YfF4B-CZS4CP7FDGGNeKIS2HCZiCgMQ6rrtrwtG3zbgeiIWclyky-jsqWOjnPHv7iXWxZQ19RdmA1aW4M619CJioXwFHtJJ56A)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfikGQERHETBmtNM3G3JxlXx2yMnLsrSde7_YzhvoGqpHQ&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfiOLNnl7FRCGkzUpOPthNVmO8ca2tyyOfHZLnrVFQujrA&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT16h8n7Rfo6MRpF__aroydNaA7oAyQ5u_Z3XORVUcif8jjqee8rS5JZx2yIrN4oXdKE1jw0cZcBlU8eZz3CJprD-4xAFyYTLiZr75_UAw4z97oBAP1iUEFnKeMcbiJI7-7pi-GGgl3clmF2YjuYWQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfgZHcsNEPd08tNm_reRjSuiWfI64BYBlSRQKaKzwYtLxQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT00O9CfRC_G63GEq_ug09RtGPSEg2G7YJTKfZ47nqa761sYqfssFzYDkIe7yjxKsvKw2t38TP0UneQg6Qe7pGI9ALib845ZaoAEYeyqMTTNzfSXHaWZS1oTULVB1JPCYHpTF7hWn8bcq6Tb1FKkDw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AfjxxsekstF6owJa2GCyn1PR36uVZN36l7xkTfReajWngw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0Ohxxruqy36NmivXrTpGJNlFWeaE2aQz4Ebqe46PJIDLeuCNc_GoFQ_Lt1MON002clNWdhgT3Qe5ENyvUGZOtt4QIrLL4NzUNH7z0U1PjqSsAKsO21Z5sXs_g5H2LGk8l-e2-GM7qX0iRU-_iQ2Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=jGfrBMjFXMuo4GCpMvsu2A&oh=00_AficUVPRyrvz3ON_PAMjr6gSLxHfy73JNsSdPGXOa0QuIw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0aoT-RJb5ACZNzyYTZP7YFPkVnFXUS52aivyx6Lrbjxe_wWzRQVZpTIP_U1IDZvUZMlJ2I7Yu6D_mXm_7aggSg2oKB9e-aFQsf_XM1uVm-Zh2du7QIkvVYk1qc7A1pCQ-eGs1FNJzRMeq3UAarAw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2dART5j9qGADCKtzub-XL6-WDdNlxTRbRftINzwbuhEjsmzO6mYp6LVK7jrpTj5HhfWpLzVs35fcdz0tYDly5YDMA-i-dYMWRfXUZXGxT5DbIfTL6CpGldMLuqmX3Qa8P4AiH0GaFks0AYJ00YvQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)