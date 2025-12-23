![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Fsticker-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Sticker](/docs/whatsapp/cloud-api/messages/sticker-messages)

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

[Sticker messages](#sticker-messages)

[Request syntax](#request-syntax)

[Post Body Parameters](#post-body-parameters)

[Supported Sticker Formats](#supported-sticker-formats)

[Example Request](#example-request)

[Example Response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Sticker messages

Sticker messages display animated or static sticker images in a WhatsApp message.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/441292863_1203428507688350_9164958282076997505_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=Su-_ZBL5gl0Q7kNvwGFeKwz&_nc_oc=AdnNHecw1wEYKixppqIYxErmNHM6f4gOevhbI2D68wxsYYUspyZkVklGN1xdDoYUfyQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_Afil4QTxoSTX6WiaTt3kCoYxfNHL0_U18S7neCEN73JhEQ&oe=6940557C)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a sticker message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "sticker",
  "sticker": {
    "id": "<MEDIA_ID>", <!-- Only if using uploaded media -->
    "link": "<MEDIA_URL>", <!-- Only if using hosted media (not recommended) -->
  }
}'
```

### Post Body Parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<MEDIA_ID>`  *String* | **Required if using uploaded media, otherwise omit.**  ID of the [uploaded media asset](/docs/whatsapp/cloud-api/reference/media#upload-media). | `1013859600285441` |
| `<MEDIA_URL>`  *String* | **Required if using hosted media, otherwise omit.**  URL of the media asset hosted on your public server. For better performance, we recommend using `id` and an [uploaded media asset ID](/docs/whatsapp/cloud-api/reference/media#upload-media) instead. | `https://www.luckyshrub.com/assets/animated-smiling-plant.webp` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Supported Sticker Formats

| Sticker Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Animated sticker | .webp | image/webp | 500 KB |
| Static sticker | .webp | image/webp | 100 KB |

## Example Request

Example request to send an animated sticker image to a WhatsApp user.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "sticker",
  "sticker": {
    "id" : "798882015472548"
  }
}'
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

[Sticker messages](#sticker-messages)

[Request syntax](#request-syntax)

[Post Body Parameters](#post-body-parameters)

[Supported Sticker Formats](#supported-sticker-formats)

[Example Request](#example-request)

[Example Response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfjPp5Nmm_zb8tODgYv7MXcmRo19EBMGPpjBrCIk1aq_0w&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfgzWq4ITuxp9nKhNKwsfxf1oc_8EqFa4uF8-rwBdBF9Lw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfgEBLrVu3ssBTy1_YErm4p7_s683Z9VzE4PVuCEOvVXkQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0qNUuxLnxGr7mp2y8QiWqeOJUAi_cF8VzkiE0cZVrUKQ722iqrKLO_h2LW09VQKjgW2s2RkHQfWjkz58QjQP9as5OkkT-bCIuL9v1h81R0htF8PqA5u2ABKfx_luAwKars1ekwdijPYpwx8J2HfA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_Afj11VfFS32SyGosrfKvoKJR-fZCDA8KNb97gumXzOqF2Q&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2mpOYF8bE_usQy6lz5CDIjDdWYfSN1eB-QYgtQLCxab1JIOto9EG6HIIh9iJ8yHrWniPekt2Hz-IXaNoMzD8F-xW3twu5P60Iuq7che9fFk6n3TTEUFv2gcZZGoH6qfsVGxGnT6OvMl71zKiXrbQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfhL5rmde2A2iTREDFiw-ODZE3nMsHwVcc_sGNP9J4wOCA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT29n7yemqXNi7E-s6uz3KmXcJ1A4nDCgmYSxRaTw2ZQnd7W7Wvo6KY0qL2H_lxWUgbXzKr6wn5VMIaari3s7AMgDNPOqsHOyKJdqpQdfL2rapimEvhH8fSdtxhcRbZiTn46myyzWC5y9MK-CNAS7g)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_Afg9rWuSO8Bi2OQqEodrPqTwS4OV_rYDL-6BexOpbc8xJA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3uR-hX2fMnEIgObGDy9NGGkZFJw8aLf98XQTs-gC9xTx97OzQmn5DW3HDnlYPB6OYn-aypkoQTyoS0kNAoLG_tW1jkvM9WzERmpcCf6YeZL5uWm7iBsiZaOd7osottl4hrHKnFeGYfGNaaoN0pOw)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3EhVu6OlLN2i0jx4enzD-xQJB8O3s_aaxJ9VwapXiqtUZNMv2PLgvVd6conYF3S5G_Z1b4HdtcVbzW94u-c3Z1ySqMlNvhuVeWzMdCFxf3Zt83ttNnTsIgkAuXkWP8db-gKwU9tC8bwfyUtCTVBg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2xw8VBI8NDWcW4-sVi214DDV9nxUKavVQRCfryTkpn0g6ggqYb_kpURabyhS50CsTcScvw-yAgP0opz3iA1IYUYU9SpiuhvIMf7hDPYXFjMYsR5nwphn3pz1z3_-7ZnHCPZrKso5DmroFyNTq-Tg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_Afip6fixLUvjKpXswcrdGTrqXQaon9p1xKTHWSaXf6m_lw&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfhcBNSQcggbGvxk_Z6IruGoQQxuvm5tf0h8YnJVxf6uXw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0Z_E-_Qu6UGvEG4arxVHUaVWARmS574aobE66QDFCT_qPqixXWJUlQqiIF8IZp9zYjRoFNUI7-f5omBo_kmYx6U2Mx-1NTdPvDd4MkrA0pxO2AIZM2uOcCE_wpejtOjiVNaEbQH3E8o_DfThzoFg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfgSR-M5UJtZDXEz-_RCmRjco0IVEgLobxzf6tGR1lZMxA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT30PcJNNbWmB-vjgkIGTrbC-Ro-ktIdj8kKls91wcc1w56lAroCuMhgZndFuHlqtKQZI5xp1MROWuc2xF4rGOa9gDTo0vsq_vBgFSwvaC9Ig75B1jqtmwRInnDTRh32MxTfQEmVoNS52wznhReheQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfgmVTvy9d-Kl9xOK4aH8EarEo5Ot0OKMdUHqQ0SuSt0tA&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT017-FZwnmN0aWbMo0TBnX5-nFZ5BsJanMsKv8V113moqMc8rBspTb9wILkwkS8W0Qxkq3l15qvDzFiA3lzDym85aNNSlsG4TpWy_e3xyuq0So-CczFnUxbFKLD7umL90HIMoQDDpavlRdcLHZpdA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lfV43J3-_r0zdi6dxegoBg&oh=00_AfgfxC0rX2gq9hnsaGOKEbd4wtGc4_ToOB0GPyFaJ224lw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0IdZTzT9NCFwcjOgv5vdK1-Lc3M6lnTYyMWe9Ut5FLH0t0hiT-u85GcFLcZaPoPL6DrouxFGxVkDAwYLuItx7wtJtfqHfJwDUZjAcC2O5qRJxlcFgnAekSD6GI57Z1qVk4K_J0LRM1yVmehCv-rg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3kv-ZPNGlnpWT8HM262j_FNDbqh6mSiilmQjCvUhdqqocU_xalHEVKJL2Yf21v4p5uKtRIMXZxXiLSq6QttE10QWpqqusq2-mL_lt_NmeG0LFqDEeTfShpDDGKKvVp9ZopbcDId_i3R3x-I2dniQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)