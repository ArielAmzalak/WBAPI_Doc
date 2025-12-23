![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Finteractive-cta-url-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Interactive Call-To-Action URL](/docs/whatsapp/cloud-api/messages/interactive-cta-url-messages)

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

[Interactive Call-to-Action URL Button Messages](#interactive-call-to-action-url-button-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example Response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Interactive Call-to-Action URL Button Messages

WhatsApp users may be hesitant to tap raw URLs containing lengthy or obscure strings in text messages. In these situations, you may wish to send an interactive call-to-action (CTA) URL button message instead. CTA URL button messages allow you to map any URL to a button so you don't have to include the raw URL in the message body.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/498114174_2231456237292792_1964702441845433307_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=_xEOP6NYj2kQ7kNvwHK9Ej5&_nc_oc=Adko6wj0cJ0vPO1dfIWHJKdj6iofJPYJhhze0fBCWAgJgksLqI2b3NGnq4qQMufhyRQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2CRaaRJNpPM-ebQ3uKgfwg&oh=00_AfhWkuqroizX8gF5YOQO5R3jIDgFBW6WJaOqXc9uqJq9HA&oe=69404551)

## Request syntax

Endpoint: [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/)

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "interactive",
  "interactive": {
    "type": "cta_url",

    <!-- If using document header, otherwise omit -->
    "header": {
      "type": "document",
      "document": {
        "link": "<ASSET_URL>"
      }
    },

    <!-- If using image header, otherwise omit -->
    "header": {
      "type": "image",
      "image": {
        "link": "<ASSET_URL>"
      }
    },

    <!-- If using text header, otherwise omit -->
    "header": {
      "type": "text",
      "text": "<HEADER_TEXT>"
      }
    },

    <!-- If using video header, otherwise omit -->
    "header": {
      "type": "video",
      "video": {
        "link": "<ASSET_URL>"
      }
    },

    "body": {
      "text": "<BODY_TEXT>"
    },
    "action": {
      "name": "cta_url",
      "parameters": {
        "display_text": "<BUTTON_LABEL_TEXT>",
        "url": "<BUTTON_URL>"
      }
    },

    <!-- If using footer text, otherwise omit -->
    "footer": {
      "text": "<FOOTER_TEXT>"
    }
  }
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<ASSET_URL>`  *String* | **Required if using a header with a media asset.**  Asset URL on a public server. | `https://www.luckyshrub.com/assets/lucky-shrub-banner-logo-v1.png` |
| `<BODY_TEXT>`  *String* | **Required.**  Body text. URLs are automatically hyperlinked.  Maximum 1024 characters. | `Tap the button below to see available dates.` |
| `<BUTTON_LABEL_TEXT>`  *String* | **Required.**  Button label text. Must be unique if using multiple buttons.  Maximum 20 characters. | `See Dates` |
| `<BUTTON_URL>` | **Required.**  URL to load in the device's default web browser when tapped by the WhatsApp user. | `https://www.luckyshrub.com?clickID=kqDGWd24Q5TRwoEQTICY7W1JKoXvaZOXWAS7h1P76s0R7Paec4` |
| `<FOOTER_TEXT>`  *String* | **Required if using a footer.**  Footer text. URLs are automatically hyperlinked.  Maximum 60 characters. | `Dates subject to change.` |
| `<HEADER_TEXT>`  *String* | **Required if using a text header.**  Header text.  Maximum 60 characters. | `New workshop dates announced!` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "interactive",
  "interactive": {
    "type": "cta_url",
    "header": {
      "type": "image",
      "image": {
        "link": "https://www.luckyshrub.com/assets/lucky-shrub-banner-logo-v1.png"
      }
    },
    "body": {
      "text": "Tap the button below to see available dates."
    },
    "action": {
      "name": "cta_url",
      "parameters": {
        "display_text": "See Dates",
        "url": "https://www.luckyshrub.com?clickID=kqDGWd24Q5TRwoEQTICY7W1JKoXvaZOXWAS7h1P76s0R7Paec4"
      }
    },
    "footer": {
      "text": "Dates subject to change."
    }
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

[Interactive Call-to-Action URL Button Messages](#interactive-call-to-action-url-button-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example Response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Y1vn32vbHpwsxTjz-8Lx0Q&oh=00_AfijiA_98zfhOzQd8oCQ-r02pCJIKggpJxztWnHiXtO4Qw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Y1vn32vbHpwsxTjz-8Lx0Q&oh=00_AfgejQrUHISxEVzDS3Jf9C5udMIeCrQA71jAStDsONhBOg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Y1vn32vbHpwsxTjz-8Lx0Q&oh=00_Afi9iT43_ghaV_ezHSVBxB54UWrxki1iHS0MRYIVl-WwCg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Y1vn32vbHpwsxTjz-8Lx0Q&oh=00_AfgziiduvsPah6N0u1HsJuTcP5p7lV-rEqDE3Vj5WyKyhA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Y1vn32vbHpwsxTjz-8Lx0Q&oh=00_AfjfPumjMY6QRxVnzcILUPsmN7EraEOlmwmsCvk_7CnwUQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0yZMy4mV5spAoeW7VrlWJRKO_gzDacOhrZbvUoA3nEq1J-USbyXxqbFEkOWu3VIUiyXYMf66-n0jt-8EL5FLfChq3MSa0MMV3O3p5JyiVQFOBf8CMuBpa2wPllv8ofQGq_tOAQuNVVFTJR5BDlwA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)