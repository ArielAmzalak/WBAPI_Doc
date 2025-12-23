![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsend-messages%2Fcontextual-replies%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Contextual replies](/docs/whatsapp/cloud-api/guides/send-messages/contextual-replies)

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

[Contextual replies](#contextual-replies)

[Limitations](#limitations)

[Request Syntax](#request-syntax)

[Post Body](#post-body)

[Post Body Parameters](#post-body-parameters)

[Example Request](#example-request)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Contextual replies

Contextual replies are a special way of responding to a WhatsApp user message. Sending a message as a contextual reply makes it clearer to the user which message you are replying to by quoting the previous message in a contextual bubble:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441349069_1363509007609494_6528221959622289637_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=0v3UXHvPmAQQ7kNvwHUSitr&_nc_oc=AdmkHuoiJH4OVk9F0pDtINVexlj_svpCZpcZHgQv3I7Vnmll4iEfQEOGzojDQptAS58&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=35oIr58X531GvzLWrkwEcA&oh=00_AfjIwLOov7YK0kFgMMQ7-oYRCkhLFMxtHk_QooQJTDBWqQ&oe=6940706B)

## Limitations

* You cannot send a [reaction message](/docs/whatsapp/cloud-api/messages/reaction-messages) as a contextual reply.

The contextual bubble will not appear at the top of the delivered message if:

* The previous message has been deleted or moved to long term storage (messages are typically moved to long term storage after 30 days, unless you have enabled [local storage](/docs/whatsapp/cloud-api/overview/local-storage/)).
* You reply with an [audio](/docs/whatsapp/cloud-api/messages/audio-messages), [image](/docs/whatsapp/cloud-api/messages/image-messages), or [video message](/docs/whatsapp/cloud-api/messages/video-messages) and the WhatsApp user is running KaiOS.
* You use the WhatsApp client to reply with a [push-to-talk](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F657157755756612%2F%3Fcms_platform%3Dweb&h=AT1Sd5f6pM71xFskcycUMwdh6ErJa9w2z-tZYPQQhKk3qf3HEQ6_Vd4G_Xt9LueFbS9Ekp7d4lJv68INFvznnO_juE7FFINjOmGWyotGplym3VvgfYXe_6131yWzPCpKCUQPVf4wSYlVbExuEVrdrw) message and the WhatsApp user is running KaiOS.
* You reply with a [template message](/docs/whatsapp/cloud-api/guides/send-message-templates).

## Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages
```

### Post Body

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "context": {
    "message_id": "WAMID_TO_REPLY_TO"
  },

  /* Message type and type contents goes here */

}
```

### Post Body Parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<WAMID_TO_REPLY_TO>`  *String* | **Required.**  WhatsApp message ID (wamid) of the previous message you want to reply to. | `wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQTdCNTg5RjY1MEMyRjlGMjRGNgA=` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example Request

Example of a text message sent as a reply to a previous message.

```
curl 'https://graph.facebook.com/v19.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "context": {
    "message_id": "wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQTdCNTg5RjY1MEMyRjlGMjRGNgA="
  },
  "type": "text",
  "text": {
    "body": "You'\''re welcome, Pablo!"
  }
}'
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Contextual replies](#contextual-replies)

[Limitations](#limitations)

[Request Syntax](#request-syntax)

[Post Body](#post-body)

[Post Body Parameters](#post-body-parameters)

[Example Request](#example-request)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jHY5hmXrFIcuNit8kVa28Q&oh=00_AfhswHFjPXt-rkTFiFvCkNEFBWBJTocZMnUlCM8a4_x6Jg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jHY5hmXrFIcuNit8kVa28Q&oh=00_AfjJwdq251wGi0CwB6s3u62eLtJJLEveqeHoBoTJWwe39Q&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jHY5hmXrFIcuNit8kVa28Q&oh=00_Afj608OxoW_D0ys-7O4Qtx-PlEOuYAzP5K8hYlbNmX1oYQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jHY5hmXrFIcuNit8kVa28Q&oh=00_AfhhSEFBrSqGaHHPlFyLVhVhM08REMAi-pwIqrWnpi4WCw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jHY5hmXrFIcuNit8kVa28Q&oh=00_AfghYb3JbGvn8Zp74l0oZRUMCf9My00E54qa1bNALCFdtg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Ml4UeVNagVzEtRcyw1M-h-CtlhY4Gd8oYiEZkigw3qNfh89v-u_aiyC5qQKfR5lbI-v70KB-Ll3_lrsrURI87K39Nat4V81LFaQA5opwSI_IyW2DSRe2y4FWZDFLBtaGZ6GVGXLVkLTDgUfvLHw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)