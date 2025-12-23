![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Fvideo-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Video](/docs/whatsapp/cloud-api/messages/video-messages)

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

[Video Messages](#video-messages)

[Sending Video Messages](#sending-video-messages)

[Request Syntax](#request-syntax)

[Post Body](#post-body)

[Post Body Parameters](#post-body-parameters)

[Supported Video Formats](#supported-video-formats)

[Example Request](#example-request)

[Example Response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Video Messages

Video messages display a thumbnail preview of a video image with an optional caption. When the WhatsApp user taps the preview, it loads the video and displays it to the user.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440793312_1179905419842171_7706273386179077435_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=tQB-NmveBTwQ7kNvwG4jdYW&_nc_oc=AdnJQGia09Bn5B5GqvBW7Axr-IPxYEPXxpCOVXEvyeSouAVCQObJoEBTe9HBefVwfaU&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_Afhoevq25OxwAdC0DspGrZxWfCYvxjAQvWmvz6-TYrFr9A&oe=69407213)

## Sending Video Messages

Use the **[POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/)** endpoint to send a video message to a WhatsApp user.

### Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages
```

### Post Body

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "{{wa-user-phone-number}}",
  "type": "video",
  "video": {
    "id" : "<MEDIA_ID>", /* Only if using uploaded media */
    "link": "<MEDIA_URL>", /* Only if linking to your media */
    "caption": "<VIDEO_CAPTION_TEXT>"
  }
}
```

### Post Body Parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<VIDEO_CAPTION_TEXT>`  *String* | **Optional.**  Video caption text.  Maximum 1024 characters. | `A succulent eclipse!` |
| `<MEDIA_ID>`  *String* | **Required if using an uploaded media asset (recommended)**.  [Uploaded media](/docs/whatsapp/cloud-api/reference/media#upload-media) asset ID. | `1166846181421424` |
| `<MEDIA_URL>`  *String* | **Required if linking to your media asset (not recommended)**  URL of video asset on your public server. For better performance, we recommend that you [upload your media asset](/docs/whatsapp/cloud-api/reference/media#upload-media) instead. | `https://www.luckyshrub.com/assets/lucky-shrub-eclipse-viewing.mp4` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Supported Video Formats

Only H.264 video codec and AAC audio codec supported. Single audio stream or no audio stream only.

| Video Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| 3GPP | .3gp | video/3gpp | 16 MB |
| MP4 Video | .mp4 | video/mp4 | 16 MB |

## Example Request

Example request to send a video message with a caption to a WhatsApp user.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "video",
  "video": {
    "id" : "1166846181421424",
    "caption": "A succulent eclipse!"
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

[Video Messages](#video-messages)

[Sending Video Messages](#sending-video-messages)

[Request Syntax](#request-syntax)

[Post Body](#post-body)

[Post Body Parameters](#post-body-parameters)

[Supported Video Formats](#supported-video-formats)

[Example Request](#example-request)

[Example Response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_Afi3WyQjJcA56RId4QympLyripfw33zYW-Z6g87joQJ-bw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_Afjtnv18MQz8MDuh3KTYzGw-XKm_rqcQZIrLdlUfU0egow&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfjiQPAk0p14AOSnHuoHXlsFENuibm1-LLiheqxUfCx-xQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3NQ3aEGIucb7L9TaWpYC375DZXPPgYwNOA3zOj06pg2vKdBAMaqcUTGjxkCWYnyaZVsUJujRpvDOEtZCOgURLHAmWUKayNceB5ciscNS-S98IDXK0z7oycbBYyItyJO1ZblLF_KvbkJ8Z7zd9rlg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfiScpatBE6GLLCdMVwUUHcTOETCqe8KerszIbz7emeQXA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3pHAlHpO1skjW_F2sg8je5LFnoRac6jeaZ4gHlJat11Z_1zP9pE69p9ZFjvdPA6z0tpoSrsFziTxwEp7cg3g1Pf4CDeN4GCN95mdff3pya9nh7WS6sHOf3S47sVH99hSQjPuX_RO91MCoVYeeSDA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfighLjBL5oNQnykSVoQK2D4C4opuHTdORmpH6jsm9EGAQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT28gCAtham0f9Rq5oprJmznW7TfJkzsF93RPgFCWxmUKHLZVdTU1qvFOr123sidS8j4mabQwLJo8gVa8i1aqcs6GjNgg4g-0s6XaHaWlWGg3qz9-8EQNTmNwO3XHTZUWlxRFOgj8hmUDYgRgNmZUQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfidQUqpSBrBnlsNM4zQWj19x3HKZDpkdsRJrW6m5JDFDw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0i2ORfVa5uXImVibuuOCHa-p_aYWsRTreUm_N-zTfGawbVG6uLhylFRP4iOO4a9bqViUCUgBmjJxi6YcgsIex1h6PFrmivSjum1SLDvFXwrWx7oPs04n7OFzT67Gppm_632Dr_A4AEkQecIyWfWw)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0xMWatWp8LFdpaStTtsOzcyrP-SqegMhI0Xe7co8vXhEOmW6wRWTF8ng_ymSx82SpLFJimX32Gr_xF0lAI59vLJcGMCKAWAegHNhOoTbuv0RYKQlBQ0jHy7tHwfwjBztG9MIgzbl88KFEKSUlGpA)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3-DSlwbiB_v_nryrUGLaZs9GCS7y3kT6Po7aGcWoDdKoQNZcCh6SPpsOMVxMZc2xXpQQQibblcHK4baeZkA0b_eGnzIb2BSecNuFV9neP0tkg7Hor8IZtMPD9xgPTR7PwnfShveZjBTUckpJLj9Q)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_Afjd4vEVJqekzCday2w2cakR25qzihVQEOlFXpy6WMTI6Q&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfgdyVOJykKZE7Ro4Evm9sHdY9RPD8SOzLnQn07T9NCFyg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3geIFrdG4RiJ7uhkrHkfSPlkykPebZtTZb7aZlv7coJ8p2ScyZtaNcg4pQxpJ6DFifB3cvekSyb_XCcnEwo95ictXWTTMui9pYcaronm5RAzDiFI0uc42Yhtl0nMc7RDmOay2S9Uid26d2pgrCUg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfiKHYYfJtrcsLFddn-Qm6fe3-ng6GX4A5DH2Eo3FXxHAA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3ORtYT57UtNqzc-KNH6dkBgk2xOLfSdMMa44d6GVOVk4fdZdkbQvJU2jmK0f8fHgeBEjMfNXGswIuMbmnDtBx5wNNV9gYDCdPBugpxI-gx4VUQT7UNtKY3uLHc8-qCyiKBb_cnypRTkxOm4QSFUw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_Afi1Wkd_iwVtLmy6ywf4UsYbVORqsBmBi3yS3Voc0AZ8tQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3DtEIsuVhwi4OCQdo7JF9cW1WT6Je3Ppg6WE7EeEaiVItzStIG2lOWp0EnDdOq2gSBpu-YMHC03qgvA7SaWuFlr6k6FidzMNTbE8v5JjT8m9_gQiWRTuovFCPy5tBYycdwXHNXNaqP-8ZCnnrS8w)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xbI9BM-R375Xnll_1BW65w&oh=00_AfjmubOsR3eytq7Xc16SK3GmlamhfiP4xc2OZUra6v1E_Q&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2GdaFS7edSn9aMdGkHIJVkS7ECcyhQP5x0ddu7eBJ6TiXzAXxG9Kh_LSR4crk0sF3B7tLGTQVZSyZPcSkgvN2_T0JngGjlvV7_X7HpZ3yCLr49GizAUnXc4IJVEZ_vnytBL4bVftpPLHh8um8Mbw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3zWZp4pyIRpMxn9bTtpRDUkpudiOQGPgS1NhfUIKzyzF8mlRZU-j8NUSqpLhUVy3bSPC8tXke2L8VtbgAofc992-l0IG81AXGDC1tAMF435-H9DXaGXByOodnxGLsW4r9CRjab99qg7CjtgdNMDw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)