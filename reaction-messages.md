![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Freaction-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Reação](/docs/whatsapp/cloud-api/messages/reaction-messages)

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

[Reaction messages](#reaction-messages)

[Limitations](#limitations)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/messages/reaction-messages/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 3 de nov
Atualização em Português (Brasil): 19 de set

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Reaction messages

Reaction messages are emoji-reactions that you can apply to a previous WhatsApp user message that you have received.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440791676_2613895758778914_1777908069161322734_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=O_N0JE_ArF8Q7kNvwFy22o6&_nc_oc=AdnePbsygK2szk6jmwKrTfmoM56ecaF_sgknxWNDGpTNl8QZSNcoEF8cMYXUFlTOaIQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfjImTgS5KvSUDL7ash9s9gTx5I0CQiAFV1EhHjT-GvBiw&oe=69404F31)

## Limitations

When sending a reaction message, only a [sent message webhook](/docs/whatsapp/cloud-api/webhooks/payload-examples#status--message-sent) (`status` set to `sent`) will be triggered; delivered and read message webhooks will not be triggered.

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to apply an emoji reaction on a message you have received from a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "reaction",
  "reaction": {
    "message_id": "<WHATSAPP_MESSAGE_ID>",
    "emoji": "<EMOJI>"
  }
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<EMOJI>`  *String* | **Required.**  Unicode escape sequence of the emoji, or the emoji itself, to apply to the user message. | Unicode escape sequence example:  `\uD83D\uDE00`  Emoji example:  😀 |
| `<WHATSAPP_MESSAGE_ID>`  *String* | **Required.**  WhatsApp message ID of message you want to apply the emoji to.  If the message you are reacting to is more than 30 days old, doesn't correspond to any message in the chat thread, has been deleted, or is itself a reaction message, the reaction message will not be delivered and you will receive a **messages** webhook with error code `131009`. | `wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQUZCMTY0MDc2MUYwNzBDNTY5MAA=` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

Example request to apply the grinning face emoji (😀) to a previously received user message.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "reaction",
  "reaction": {
    "message_id": "wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQUZCMTY0MDc2MUYwNzBDNTY5MAA=",
    "emoji": "\uD83D\uDE00"
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

[Reaction messages](#reaction-messages)

[Limitations](#limitations)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfhvYuuLbHFL_eeDdWh6gfFh3wi8yeZOVqvKd4AJaR_NsA&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfifhXC9GaiRJrngAPWnIF51_fb9jIxfpi872DhouYbLYA&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfgN9LAaPUkOcqmXAv2I9WmwZKlcgs3d1UKTvIK_BeW-FQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3yLqClI25d-aSQIqtBVghIlkAGmZd39dafmzF2_vbZDVuLI6ENdALs0ciCxLyYmk2hKsHJgVjqs-tp3EMU5ruWfwAtcSzAkMKxsLWkPTF4TVqf6uboYTAfOLh29WoFwStOyAKOtDWEs6pjujKGaw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfjzcWpK8EPs9SZHIahsdC0jcXBQO1ypI24dAldEMbXKCg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3wQfnSY4KYUfkdvgOPfYYCfxUnctJBBR3sT2QWS_Yk8I2ZeMKYCHGm0GFOJ2hosp0_dXicGwrx8Xa4bJhK8GYBHFmRSjWgVCG_WvSnNQ4FsuLJVH8kNU_sbxQWIPzu-LL4uMar11lRIYswgzNq1A)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfghFBFwoMwqSErvHsmAIsUZTXD0E0KhfBAZeBfY6yy2SQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0DAWM_HIGMxq-ujflyBU3GkJ4cZtoU8glVp6riey4gLmt0nQzrYZ7A0x9q5hX8YjDB41oGLfpv_pIOLlmNTuBF3XMDhfEwnjdxpWmKY5sEvtqiGlJnra683aorZZW1FnZl4HT02coPDQbHqyOJnQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfgTKDEhqUY0zxOj8J0VAB25pNtMkJkxMqQpkuBnGqAHKA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3aMv_dhOBL9T4hmot5_iVkYH2BtISw0afR-7iWzQVaRbQA91-Ioimz8ZecA6dPGGmFsXxDrT7sx5XvESVrHr8s3LinD1PhM9elW4i7mOA6ASZZwRKKp-Ozn8zTHL7GgBAsi_yQaXWkCI5k5m0LTg)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT2v9zLfV1Zzb-xjnuF93F6n4snOPt12bPfhEGh-PiUOMvebNK9jHDGmwPTo96hwbjL-pcCILjNgzocLOUojd-6b589PBDThmQMcF53rsYeY_DapFkA8cCXJUt51phS6wKhJxk1UDktyI5QNJiNqpbs3KuAkKwE97hs)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3_7fMlnxqL3oq_Lm0kzOPNZxBxRTYz9jxrPnn2nPGacSXs2XpXy3uR6vaE4z1Vbgd1B5e0TFjP3zE8g_uWrBdZROobrvpfJDkGNRNOTzCpnHZ1DrMoYbtR7JMNpRuIOoDz_1bVsx7l9iXItiuMwQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_Afh9tmXlo9Qnqsw-SuvEaqLcrZxw8mqPjKn7EPCtSVgA0g&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfiHThDHOqg4Qr6XnuxBciXGsU3VNmiRMkKQEfbbAZM90w&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2M0AskeCZnceoj1WaWdHzdDEv8RaPDIqZFdRLeBru5Ff6AUnts6H6uI7YUuu8-cVsU6_8qj-3j5k7o0w_MsqeoLLfkCLQlGN9_5HuvdGuEgkSZ6TmmBxT1vANwri7Q-2KZGjT96Uukg1KclwoUwA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfiNyOYWVPxwxG9D8rTf6XvhbUOACpFP2QI3JkFhMmN0cQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1mBsiwCFzsdsctho9kzrsL5MtpiKISRzvZAzXnMt7VCm0ZoObYcLjGH0t2oGCWhVWTFmefD076zMuuBMXan6JxXrtI89Cij3MBCYw8rxgU1zHKN6ei5gwHtc_xjIGr7WKwC1y_ERQc4dElFmuGmQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_Afgx4qtopdxhLc2PFQeYm_-2G9eUYWFh2afrpp5TrVJfog&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0MZMcWXr5IijK4TMWTQ8uGvjllP9P4oFyR3eqHr8qqRnaVUNGMMB0CYFEq6roh9AF7eLzk3Y8AELJCa458eSD3MoAUXKd7O89iDJQ_fnCQS4wtcoVIOWIIxJcGP-y7-TVCXktTnWZqSQW4nqzkwA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qYDbVL92i9FW1NHCpCna6w&oh=00_AfiXs7zkcwH3hvg-SLna_6-AWIOt0qdzOHFVM2J4hQJKKg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0bWyanLJ-7lwAnTmPUKnN1MgL253d-cyae-RvbuEG8hrWt2baMZTk5OktnAZwQbcs37Q_isxXUZmu8KnGUqPCm7rxRfK8uQyOTKi_a9O0TaIEamW_2pcRA__mdml_OuC2a6V3lHoeIc5Vxi-Pj_g)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2JIH2uoXOQSg8OqHra8duu3hyew6Opd14vjKYbqV_zzJ_oY8bxMNKZ0a4r9kxXVHdyGUduDq2VYpBj-kyYFd3SYIp24_Z11goygEHRbK3BdN4v-OPNjpb5B_rhYSgA-2NwF7SgwODIUYyur3v6Fw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)