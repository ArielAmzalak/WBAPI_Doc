![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fmark-message-as-read%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Confirmações de leitura](/docs/whatsapp/cloud-api/guides/mark-message-as-read)

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

[Mark messages as read](#mark-messages-as-read)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/guides/mark-message-as-read/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 3 de nov
Atualização em Português (Brasil): 28 de abr

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Mark messages as read

When you get a **messages** webhook indicating an [incoming message](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/), you can use the `message.id` value to mark the message as read.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/491643461_603380552708521_8284248965365504291_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=OnmPmNmYmigQ7kNvwGbgAU2&_nc_oc=AdlsLSWy8e2qbFTQGfECRonK606upgrlzv768cUL9BYn6grGiaV5lKErMY8rAKweagw&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=rnTA_isKHikn5a3Dikvq6g&oh=00_AfiQEo2reWzFMT7KNzQJPmiGUhj0DAAbsNTAaCE1aom73Q&oe=69406C70)

It's good practice to mark an incoming messages as read within 30 days of receipt. Marking a message as read will also mark earlier messages in the thread as read.

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to mark a message as read.

```
curl -X POST \
'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages'
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Content-Type: application/json' \
-d '
{
  "messaging_product": "whatsapp",
  "status": "read",
  "message_id": "<WHATSAPP_MESSAGE_ID>"
}'
```

## Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | **Required.**  WhatsApp message ID. This ID is assigned to the `messages.id` property in **received message** [messages](/docs/whatsapp/cloud-api/webhooks/payload-examples#received-messages) webhooks. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJDQjZCMzlEQUE4OTJBMTE4RTUA` |

## Response

Upon success:

```
{
  "success": true
}
```

## Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "status": "read",
  "message_id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJDQjZCMzlEQUE4OTJBMTE4RTUA"
}'
```

## Example response

```
{
  "success": true
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Mark messages as read](#mark-messages-as-read)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=MVSY6H0qLyqbFHsMxyZZ5A&oh=00_Afh2qPGuwiYo4DfNexBxVWS6Pn9xMWFK1ghZ2aQPTNMVvg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=MVSY6H0qLyqbFHsMxyZZ5A&oh=00_Afj8n7iIjokJxKA6m0z7hu84eBMhNuO48yTPBrLyhuRsPA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=MVSY6H0qLyqbFHsMxyZZ5A&oh=00_AfixVSXmtn7wF-3I2KzQfH2W86shFxHEmkAPdIw_A9SBfQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=MVSY6H0qLyqbFHsMxyZZ5A&oh=00_AfiONRdWWQX_2K1ROu3f55CYjRpEBKkZp8mhVrHtgjq5SA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=MVSY6H0qLyqbFHsMxyZZ5A&oh=00_Afh503Th8hS_2EbcGpYnjeLXj1tFD2O-EJ3nNaAK2D6koQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ZKH6L79oeKws6OR4a5C5a79-w1QduY1bsIypD9qFv5moPMqC8xE2raS44o__at7IJEyPLAUGraJVwhosMnc7nI7WlKf24-8eZlUps2hVDWMR-YcYs6yhDjyAq4dBw8OAb8q2zTfnxK6hQhFKE8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)