![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Fdocument-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Document](/docs/whatsapp/cloud-api/messages/document-messages)

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

[Document messages](#document-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Supported document types](#supported-document-types)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Document messages

Document messages are messages that display a document icon, linked to a document, that a WhatsApp user can tap to download.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441287424_3695370760733536_48188157634176922_n.png?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=VcRp1MhHOo0Q7kNvwEZvTsf&_nc_oc=AdlVwQ1pS7GQ0XI7vkWYi7kPEenIuuAMpqksvuKRYo1ITlhdpOdriP9MvmYkxt08j3s&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yqoe3FJcBRu89I58ZgcQgQ&oh=00_AfjX6NThEvhc20VP4vWBv-erIh0DFcm84mppuZ24Dy12_g&oe=69407288)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a document message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "document",
  "document": {
    "id": "<MEDIA_ID>", <!-- Only if using uploaded media -->
    "link": "<MEDIA_URL>", <!-- Only if using hosted media (not recommended) -->
    "caption": "<MEDIA_CAPTION_TEXT>",
    "filename": "<MEDIA_FILENAME>",
    "caption": "<MEDIA_CAPTION_TEXT>"
  }
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<MEDIA_CAPTION_TEXT>`  *String* | **Optional.**  Media asset caption text.  Maximum 1024 characters. | `Lucky Shrub Invoice` |
| `<MEDIA_FILENAME>`  *String* | **Optional.**  Document filename, with extension. The WhatsApp client will use an appropriate file type icon based on the extension. | `lucky-shrub-invoice.pdf` |
| `<MEDIA_ID>`  *String* | **Required if using uploaded media, otherwise omit.**  ID of the [uploaded media asset](/docs/whatsapp/cloud-api/reference/media#upload-media). | `1013859600285441` |
| `<MEDIA_URL>`  *String* | **Required if using hosted media, otherwise omit.**  URL of the media asset hosted on your public server. For better performance, we recommend using `id` and an [uploaded media asset ID](/docs/whatsapp/cloud-api/reference/media#upload-media) instead. | `https://www.luckyshrub.com/invoices/FmOzfD9cKf/lucky-shrub-invoice.pdf` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Supported document types

| Document Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Text | .txt | text/plain | 100 MB |
| Microsoft Excel | .xls | application/vnd.ms-excel | 100 MB |
| Microsoft Excel | .xlsx | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 100 MB |
| Microsoft Word | .doc | application/msword | 100 MB |
| Microsoft Word | .docx | application/vnd.openxmlformats-officedocument.wordprocessingml.document | 100 MB |
| Microsoft PowerPoint | .ppt | application/vnd.ms-powerpoint | 100 MB |
| Microsoft PowerPoint | .pptx | application/vnd.openxmlformats-officedocument.presentationml.presentation | 100 MB |
| PDF | .pdf | application/pdf | 100 MB |

## Example request

Example request to send a PDF in a document message with a caption to a WhatsApp user.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "document",
  "document": {
    "id": "1376223850470843",
    "filename": "order_abc123.pdf",
    "caption": "Your order confirmation (PDF)"
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

[Document messages](#document-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Supported document types](#supported-document-types)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=njThtTyiDoZn5qZQta2Z8g&oh=00_Afi6ic2p285nSbeCD2j1zzJ6ow4iGmGn-1RZ7SjOxDdXzg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=njThtTyiDoZn5qZQta2Z8g&oh=00_AfhA1defRljXqiw2jSsLr38pRom5ZrP4_As9nyMRcKyBEQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=njThtTyiDoZn5qZQta2Z8g&oh=00_AfhkEB7-msI47pBrfV2iyvFbqFIBHe7iiMiMc4E_sjKRuA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=njThtTyiDoZn5qZQta2Z8g&oh=00_AfhoirihjKmxNxJked6hbxqfFizK65-i9EqAXsXLS0jkIQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=njThtTyiDoZn5qZQta2Z8g&oh=00_AfjzRhVou11c7WrvaXWKuxZoPi_XrJP5-TIzNEI3nQLZXA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1sAv6qiS7ekWxifhS0HoCc3DzgsvZmj1mevp7CtBy-nyHQBlQt7F0yYLyfDdNmQG1OC_63uVof24WLXfLilzNucvej56827J-Gd2KnkFK-Uv-cmmc47UoJzI-jO_rDayee1BGGyZV67KFw2bJ3qA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)