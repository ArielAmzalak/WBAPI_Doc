![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Faudio-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Áudio](/docs/whatsapp/cloud-api/messages/audio-messages)

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

[Mensagens de áudio](#mensagens-de--udio)

[Mensagens de voz](#mensagens-de-voz)

[Mensagens de áudio básicas](#mensagens-de--udio-b-sicas)

[Sintaxe da solicitação](#sintaxe-da-solicita--o)

[Parâmetros de solicitação](#par-metros-de-solicita--o)

[Formatos de áudio compatíveis](#formatos-de--udio-compat-veis)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo de resposta](#exemplo-de-resposta)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Mensagens de áudio

É possível usar a API de Nuvem para enviar mensagens de voz e mensagens de áudio básicas.

## Mensagens de voz

Uma mensagem de voz (também chamada de recado de voz, mensagem de áudio ou apenas áudio) é uma gravação de uma ou mais pessoas falando e pode incluir sons de fundo, como música. As mensagens de voz incluem recursos como download automático, foto do perfil e ícone de voz, que não estão disponíveis em mensagens de áudio básicas. Se o usuário tiver definido a transcrição de [mensagem de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT1w8scbA_dBzDgrmOpSi1qRKRuwLpuTOUmIgEBNWH7javf5fWXHRjRPKaVYk-eqIh8po5aeVPXUkCrasm9b3jEnFrL5Hvgj7pU6F9lLbfmbEaamdMOuI3HluUGBk_EjNZ0w_0Yz0l_0cPgMyqb0Lg) como **Automática**, uma transcrição de texto da mensagem também será incluída.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/562379210_2249057198900177_5743647093897895635_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=w_43L5o6RfgQ7kNvwH-vfcs&_nc_oc=AdkuCYQXd-cwC4wiFfsb6IP0VM5BC-pD_RW_lb61Uob_wXikAtSdCNEPt4qZNZMb63U&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=b9oIp8J9Q2BpLdTeI9W9Tw&oh=00_AfjFbpe3ZktW0W056NIOzSFKkLRurairwYDgIc0_-3Ajug&oe=6940668C)

* As mensagens de voz exigem arquivos .ogg codificados com o codec **OPUS**. Caso você envie um tipo de arquivo diferente ou um arquivo codificado com um codec diferente, a transcrição da mensagem de voz falhará.
* O ícone de reprodução só aparecerá se o arquivo tiver 512 KB ou menos. Caso contrário, ele será substituído por um ícone de download (uma seta voltada para baixo).
* A imagem do perfil da empresa é usada como imagem do perfil, acompanhada por um ícone de microfone.
* As transcrições de voz aparecem somente se o usuário tiver habilitado a opção **Transcrição automática** [de mensagens de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT3_wILVPQT_qDnfIHIJy_x_5HaNsmKTd7doSTziZ8bMoFPYpt1rTBLKLRYE48rfb-nO8ZxXP--PF8f79ve1mwPI5kioFjnQCSgWL3pk1khyQCk3NPM2WJ7k6y41PLGVu9QaPGl-8-iH_-d5r0YXow). Se o usuário tiver definido essa opção como **Manual**, o texto "Transcrever" aparecerá e o texto transcrito será exibido ao tocar nessa opção. Se o usuário tiver definido a transcrição de mensagens de voz como **Nunca**, nenhuma transcrição será exibida.

## Mensagens de áudio básicas

As mensagens de áudio básicas exibem um ícone de download e um ícone de música. Quando o usuário do WhatsApp toca no ícone de reprodução, ele precisa baixar manualmente a mensagem de áudio para que o cliente do WhatsApp carregue e reproduza o arquivo.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/561815849_2827972817396551_127160148973074084_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=H6uluGfRjhoQ7kNvwHHucTG&_nc_oc=Adm1KrQJTDt2tO56uOvXkKdd7-TPUQGcEAzymTm78iWfgSBe2q9Or8xHg4i2dGB542w&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=b9oIp8J9Q2BpLdTeI9W9Tw&oh=00_AfjOT43OZ9yDrvyL6BS9snRqjpvwasB4QgovouA7ZUGcNw&oe=69406BE0)

* O ícone de download será substituído por um ícone de reprodução se o usuário do WhatsApp tiver ativado o [download automático](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F366146522333492%2F&h=AT1HYe7iaa6tN5dFuAbrwxg7R7a05AHcgbJG3r3dKI2QEdZGA7nvyerBpcEkQeaxF9LiCnO3NqsjbZspfY2Q9-jHxlPAfs3ZHZOMeMOcmHwZMzwB94_pt-gFyuYHQ83dmVoJ1Y076P9XFKB_DgKzOQ) de mídias de áudio e se as condições para o download automático forem atendidas (por exemplo, o aparelho estiver conectado a uma rede Wi-Fi).
* Se você enviar um arquivo .ogg codificado com o código OPUS como uma mensagem de áudio básica, o ícone de música será substituído por um ícone de microfone. Além disso, se o usuário tiver habilitado a [transcrição de mensagens de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT2hEH9WechkJIABX7APVW8YpI6PYpPsJI_46JrZA-SbnVoULD3tERaH6Ot513AH-QdrvSS7yH4XerVPZZ12iAib2T5Qajc02WxSvSjlvzIA_Y01OBQfQiO5ric2eSOKDNb-Hg_3mQT2qfMwvOyzkw)**Automática** ou **Manual**, um texto de transcrição ou o texto "Transcrever" acompanhará a mensagem.

## Sintaxe da solicitação

Use o ponto de extremidade [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) para enviar uma mensagem de áudio a um usuário do WhatsApp.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \ -H 'Content-Type: application/json' \ -H 'Authorization: Bearer <ACCESS_TOKEN>' \ -d ' { "messaging_product": "whatsapp", "recipient_type": "individual", "to": "<WHATSAPP_USER_PHONE_NUMBER>", "type": "audio", "audio": { "id": "<MEDIA_ID>", <!-- Only if using uploaded media --> "link": "<MEDIA_URL>", <!-- Only if using hosted media (not recommended) --> "voice": <IS_VOICE?> <!-- Only include if sending voice message --> } }'
```

## Parâmetros de solicitação

| Espaço reservado | Descrição | Valor de exemplo |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<IS_VOICE?>`  *Booliano* | **Opcional.**  Defina como `true` se estiver enviando uma [mensagem de voz](#voice-messages). As mensagens de voz devem ser arquivos Ogg codificados com o codec **OPUS**.  Para enviar uma [mensagem de áudio básica](#basic-audio-message), defina como `false` ou omita totalmente. | `true` |
| `<MEDIA_ID>`  *String* | **Required if using uploaded media, otherwise omit.**  ID of the [uploaded media asset](/docs/whatsapp/cloud-api/reference/media#upload-media). | `1013859600285441` |
| `<MEDIA_URL>`  *String* | **Required if using hosted media, otherwise omit.**  URL of the media asset hosted on your public server. For better performance, we recommend using `id` and an [uploaded media asset ID](/docs/whatsapp/cloud-api/reference/media#upload-media) instead. | `https://www.luckyshrub.com/media/ringtones/wind-chime.mp3` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Formatos de áudio compatíveis

| Audio Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| AAC | .aac | audio/aac | 16 MB |
| AMR | .amr | audio/amr | 16 MB |
| MP3 | .mp3 | audio/mpeg | 16 MB |
| MP4 Audio | .m4a | audio/mp4 | 16 MB |
| OGG Audio | .ogg | audio/ogg (OPUS codecs only; base audio/ogg not supported; mono input only) | 16 MB |

Os erros mais comuns associados a arquivos de áudio são tipos MIME incompatíveis (o tipo MIME não corresponde ao tipo de arquivo indicado pelo nome do arquivo) e codificação inválida para arquivos Ogg (somente codec OPUS). Caso ocorra um erro ao enviar uma mensagem com um arquivo de mídia, verifique se o tipo MIME real do arquivo de áudio corresponde ao tipo listado acima. Para arquivos Ogg, certifique-se de codificar com o codec OPUS.

## Exemplo de solicitação

Exemplo de solicitação para enviar uma mensagem de imagem usando uma identificação de mídia carregada e uma legenda.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "audio",
  "audio": {
    "id" : "1013859600285441",
    "voice": true
  }
}'
```

## Exemplo de resposta

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

[Mensagens de áudio](#mensagens-de--udio)

[Mensagens de voz](#mensagens-de-voz)

[Mensagens de áudio básicas](#mensagens-de--udio-b-sicas)

[Sintaxe da solicitação](#sintaxe-da-solicita--o)

[Parâmetros de solicitação](#par-metros-de-solicita--o)

[Formatos de áudio compatíveis](#formatos-de--udio-compat-veis)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo de resposta](#exemplo-de-resposta)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=rn8i3c0xSf3YphNj92qNSw&oh=00_AfiVnEIGhPa63PjrLS-iOcUNT_wvexgX5B9GvNnfCv-Bgg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=rn8i3c0xSf3YphNj92qNSw&oh=00_AfgEqcY6MWbm-CEEsTT3E0DUMqj17HhTeDCSV6SQb7P0RA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=rn8i3c0xSf3YphNj92qNSw&oh=00_Afj43yfgbnFeG9rnGZ7mLDdpG4bgof5dnFucThTWLmtANA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=rn8i3c0xSf3YphNj92qNSw&oh=00_AfhEJqFTQyDDJKWoysy_zgeXvarE85x8bV8X9EzxibssVQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=rn8i3c0xSf3YphNj92qNSw&oh=00_Afj3mCZCZ_wXnbqSiVPyQn45z_heE6yJDCSk96HSHU7Juw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2fcLf5Er-B6CYvcDRBvgKLnhS_VNWaqogWemkgour1VcSaEpzJ2Mg5lnL0KW8V0QLrK8ZIb60TrCJsj8LPVUGXSrBKsjbfXhLI-hkzhGafAKHOmeFUyS4-Q0FMubR2cl_Or9QtCOSEWyMn3oRKbA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)