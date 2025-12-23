![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Ftext-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Text](/docs/whatsapp/cloud-api/messages/text-messages)

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

[Text messages](#text-messages)

[Request syntax](#request-syntax)

[Link preview](#link-preview)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Text messages

Text messages are messages containing only a text body and an optional link preview.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440742591_797870012016470_1123226266833971975_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=in1m7b7pPM8Q7kNvwHRJCtc&_nc_oc=AdnNpHGpbUXGcr9cwUBgPtXt4PjBOtOFC6uo5FY3vhJxW5ZJaja59_VZ1gKuqL75ZJo&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_Afh193fHbP5DSl0RkFjqfRZIKa6DMRcOXPwGYzl_ea1YVw&oe=69405A6B)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a text message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "text",
  "text": {
    "preview_url": <ENABLE_LINK_PREVIEW>,
    "body": "<BODY_TEXT>"
  }
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BODY_TEXT>`  *String* | **Required.**  Body text. URLs are automatically hyperlinked.  Maximum 4096 characters. | `As requested, here's the link to our latest product: https://www.meta.com/quest/quest-3/` |
| `<ENABLE_LINK_PREVIEW>`  *Boolean* | **Optional.**  Set to `true` to have the WhatsApp client attempt to render a link preview of any URL in the body text string.  See [Link Preview](#link-preview) below. | `true` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Link preview

You can have the WhatsApp client attempt to render a preview of the first URL in the body text string, if it contains one. URLs must begin with `http://` or `https://`. If multiple URLs are in the body text string, only the first URL will be rendered.

If omitted, or if unable to retrieve a link preview, a clickable link will be rendered instead.

## Example request

Example request to send a text message with link previews enabled and a body text string that contains a link.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "text",
  "text": {
    "preview_url": true,
    "body": "As requested, here'\''s the link to our latest product: https://www.meta.com/quest/quest-3/"
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

[Text messages](#text-messages)

[Request syntax](#request-syntax)

[Link preview](#link-preview)

[Example request](#example-request)

[Example response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfgvuEsUlN3Hvr0iR68-KW_IhUWBUUliH1Yr1L-aajiXbA&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_Afj1oLiFZ0sCm8-I-o32y185ioDMmQts1sFG-Vj0UJgb8w&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfgxxjAJZ0bVsgjFr5cAFfclug09SOSWWYjoxls2mTSTEQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT131nUhj4Zp4jEMqz7_nCaUzAvi4IRui90pzSwgfdXkJJL0AJkds0Jbj_tu07iupmJ5csFesLla1jSaMZJIy7BffY0E5Xaouvb5iUE3h4Z-MOt1QQLtip3HyeNOkq2HKQWJ2BUtfT3-oFEuS_KuhA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfjzjXno8Txm7Jb5BQAXgDI7MVQT32_OZt_FtDYmCxNQHQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0YqzW1pVK6vRRbBgwNYat1FRr2Forub1USBzCzAAgGCNMPAcGO0_yeB73pdcX7u8IhT_ql39s9FB8-zjkgE8mHU11XApz46dOJJq4fEpLOfBU_r1XxeqlwrQ2q6eNuQYe34ODoWPykuTuU5vHa_w)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfjX7SzhNscJOi-ZsQfP2qMoWLyuJJHqlw8dmgS3VxRgqw&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2L4dcohbI15NtWOBolRmDVHz9FgtuCLN2hRBfuiumra-oNghL7oDQeYWiaej-S4SSsNIiqtVEsQJlng9nzKjVeHhopdkkQKJe_6VRAe86BqA4n9IcvlzOSAVEGwha15rjkB900TaZKU4ETS6anew)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_Afi3nnEwfockMPaAooiinOHXODOwfp0w5Gkh20ZQ5yZykQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1IndrlWtOceKEH2SdV0yWYGGDpfSuNDLhIxFEH_i3-8dWkdA4chxv4yDOUnAH2JIpsV2Y8qM1evbjVCjIWHvgCg2-EBRoN6C2ZGRdKbcSRy1ScQSPr48sms_yM9X2QrB6SSNyfMmsDlefqY-5V4A)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0PE-Zlkf5JDmqfixZtiYOvGxyRxICjxzrsOcLF-94i71qaiTOFvSR1DyiWIQhSfOUtpQ-IfNqEUGWVVt14af7rJOtWqXGpMtPuiV6cBsDhj9OUhmC-GZcJFEBiR8LSWYqKnSOy-lNhqpeJnVtGSw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2j6aRkLv36_LFYjcgw_AB4szYGeLI2aZyzaik-Rb-QJ0HS7ZI8VrIU8eau3eK5dL8Q2v-XpIXVFAdB2jWoh8wmFjextzmNAlvhDsuO1W-Fg7i9XCHW23ow5yxhZYKNyMm5dp05O3cJwzH6ivi2ng)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfjCqDHmvATNrGUhJdEE6FP6R27t3yR-X1gbVFekLGi62g&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfjDrRI76RrzEtuOOu4WnfQYILnfIfeZUWUfnmkIvIsmRg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Cme65iWi-RVFSLfuBHhu5GY5PW1iIFqYp65aI11dxVAKjxmCVEk_vbqEbuXDaHYqkmmwqedcMtx32m3hvOks07-Tl1NKDa3rp2z6NC-K5O2GD57PLm9agYnHqhep_ArfPSThcq7KQmF5FEonW2Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfgLZN4fqjKcce1dHL4Zo3xaE5yXZAfLjg9Lux5v8papRQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3SE1xp-0NGd1B5OcwFYaN1m7fAlyW_JKUqPsxWOJG-YrABEMw-DOApq44QQvlA74fu3sHz9XuhsM8bOtEmvmlXBpApw-AqA3EXjSSeYPcu8mqupKZLyVPaNxSYz7geZDzBVO0Nrx5FYNfMzgMnlQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_AfhbNCy6doWe4XmIzJlf3R9XLnr2BMWlebXy0BEwg1wWrQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1IguhxPfskv1R6BXdizRm3NiKWaShawvAh8EmBfH43ENkvK5aS2TRa0RMil53CAyR2MsSdvrwnVUYaYKJHkStXjEsBwAUrePxspjWM7p8-CmZqL6OpOgKRu253IISN_TP7w4X5bU4xdOrjgXEbRw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=nkJvFDcUireIGUFBDhYnrA&oh=00_Afh2ZSd7UIwLQx-RHczzMyRkCvG_0HIO3aijlftMipQsTA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1YRl2rd2uHoPiIhObd7yR68MUb_q0YaO4rFb0n5J0xifTIpnCQyEitmZVbR1M-YEtI6HXyA7THou087ZinvoFN7ilbi0-rlKxkXzfuxkom0XmOZ44WLf96Ca1X-O7R7t3Shwrtm2LW7d12Ek_y9g)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0ntV-NLVkN0_GE3VzhFObHzs-HN6tASW5xrFp556XBnttTdF_0VXuwyY6uwW-HUhEnpOQIwCRXUfxVfWb6t2TlFcJZ8CKWRa6wTwLwYCP_-CAMEL6nMqGfTFVP_avJtQwGuQJktHOWxzNH91Dq3g)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)