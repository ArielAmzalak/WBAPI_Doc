+++
id = "audio-messages"
title = "Mensagens de audio"
summary = "E possivel usar a API de Nuvem para enviar mensagens de voz e mensagens de audio basicas."
source = "https://developers.facebook.com/docs/whatsapp/audio-messages"
lang = "en"
tags = ["whatsapp-business-platform", "messaging"]
+++
# Mensagens de audio

E possivel usar a API de Nuvem para enviar mensagens de voz e mensagens de audio basicas.

## Mensagens de voz

Uma mensagem de voz (tambem chamada de recado de voz, mensagem de audio ou apenas audio) e uma gravacao de uma ou mais pessoas falando e pode incluir sons de fundo, como musica. As mensagens de voz incluem recursos como download automatico, foto do perfil e icone de voz, que nao estao disponiveis em mensagens de audio basicas. Se o usuario tiver definido a transcricao de [mensagem de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT1w8scbA_dBzDgrmOpSi1qRKRuwLpuTOUmIgEBNWH7javf5fWXHRjRPKaVYk-eqIh8po5aeVPXUkCrasm9b3jEnFrL5Hvgj7pU6F9lLbfmbEaamdMOuI3HluUGBk_EjNZ0w_0Yz0l_0cPgMyqb0Lg) como **Automatica**, uma transcricao de texto da mensagem tambem sera incluida.

* As mensagens de voz exigem arquivos .ogg codificados com o codec **OPUS**. Caso voce envie um tipo de arquivo diferente ou um arquivo codificado com um codec diferente, a transcricao da mensagem de voz falhara.
* O icone de reproducao so aparecera se o arquivo tiver 512 KB ou menos. Caso contrario, ele sera substituido por um icone de download (uma seta voltada para baixo).
* A imagem do perfil da empresa e usada como imagem do perfil, acompanhada por um icone de microfone.
* As transcricoes de voz aparecem somente se o usuario tiver habilitado a opcao **Transcricao automatica** [de mensagens de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT3_wILVPQT_qDnfIHIJy_x_5HaNsmKTd7doSTziZ8bMoFPYpt1rTBLKLRYE48rfb-nO8ZxXP--PF8f79ve1mwPI5kioFjnQCSgWL3pk1khyQCk3NPM2WJ7k6y41PLGVu9QaPGl-8-iH_-d5r0YXow). Se o usuario tiver definido essa opcao como **Manual**, o texto "Transcrever" aparecera e o texto transcrito sera exibido ao tocar nessa opcao. Se o usuario tiver definido a transcricao de mensagens de voz como **Nunca**, nenhuma transcricao sera exibida.

## Mensagens de audio basicas

As mensagens de audio basicas exibem um icone de download e um icone de musica. Quando o usuario do WhatsApp toca no icone de reproducao, ele precisa baixar manualmente a mensagem de audio para que o cliente do WhatsApp carregue e reproduza o arquivo.

* O icone de download sera substituido por um icone de reproducao se o usuario do WhatsApp tiver ativado o [download automatico](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F366146522333492%2F&h=AT1HYe7iaa6tN5dFuAbrwxg7R7a05AHcgbJG3r3dKI2QEdZGA7nvyerBpcEkQeaxF9LiCnO3NqsjbZspfY2Q9-jHxlPAfs3ZHZOMeMOcmHwZMzwB94_pt-gFyuYHQ83dmVoJ1Y076P9XFKB_DgKzOQ) de midias de audio e se as condicoes para o download automatico forem atendidas (por exemplo, o aparelho estiver conectado a uma rede Wi-Fi).
* Se voce enviar um arquivo .ogg codificado com o codigo OPUS como uma mensagem de audio basica, o icone de musica sera substituido por um icone de microfone. Alem disso, se o usuario tiver habilitado a [transcricao de mensagens de voz](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F241617298315321%2F&h=AT2hEH9WechkJIABX7APVW8YpI6PYpPsJI_46JrZA-SbnVoULD3tERaH6Ot513AH-QdrvSS7yH4XerVPZZ12iAib2T5Qajc02WxSvSjlvzIA_Y01OBQfQiO5ric2eSOKDNb-Hg_3mQT2qfMwvOyzkw)**Automatica** ou **Manual**, um texto de transcricao ou o texto "Transcrever" acompanhara a mensagem.

## Sintaxe da solicitacao

Use o ponto de extremidade [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) para enviar uma mensagem de audio a um usuario do WhatsApp.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \ -H 'Content-Type: application/json' \ -H 'Authorization: Bearer <ACCESS_TOKEN>' \ -d ' { "messaging_product": "whatsapp", "recipient_type": "individual", "to": "<WHATSAPP_USER_PHONE_NUMBER>", "type": "audio", "audio": { "id": "<MEDIA_ID>", <!-- Only if using uploaded media --> "link": "<MEDIA_URL>", <!-- Only if using hosted media (not recommended) --> "voice": <IS_VOICE?> <!-- Only include if sending voice message --> } }'
```

## Parametros de solicitacao

| Espaco reservado | Descricao | Valor de exemplo |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<IS_VOICE?>`  *Booliano* | **Opcional.**  Defina como `true` se estiver enviando uma [mensagem de voz](#voice-messages). As mensagens de voz devem ser arquivos Ogg codificados com o codec **OPUS**.  Para enviar uma [mensagem de audio basica](#basic-audio-message), defina como `false` ou omita totalmente. | `true` |
| `<MEDIA_ID>`  *String* | **Required if using uploaded media, otherwise omit.**  ID of the [uploaded media asset](/docs/whatsapp/cloud-api/reference/media#upload-media). | `1013859600285441` |
| `<MEDIA_URL>`  *String* | **Required if using hosted media, otherwise omit.**  URL of the media asset hosted on your public server. For better performance, we recommend using `id` and an [uploaded media asset ID](/docs/whatsapp/cloud-api/reference/media#upload-media) instead. | `https://www.luckyshrub.com/media/ringtones/wind-chime.mp3` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Formatos de audio compativeis

| Audio Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| AAC | .aac | audio/aac | 16 MB |
| AMR | .amr | audio/amr | 16 MB |
| MP3 | .mp3 | audio/mpeg | 16 MB |
| MP4 Audio | .m4a | audio/mp4 | 16 MB |
| OGG Audio | .ogg | audio/ogg (OPUS codecs only; base audio/ogg not supported; mono input only) | 16 MB |

Os erros mais comuns associados a arquivos de audio sao tipos MIME incompativeis (o tipo MIME nao corresponde ao tipo de arquivo indicado pelo nome do arquivo) e codificacao invalida para arquivos Ogg (somente codec OPUS). Caso ocorra um erro ao enviar uma mensagem com um arquivo de midia, verifique se o tipo MIME real do arquivo de audio corresponde ao tipo listado acima. Para arquivos Ogg, certifique-se de codificar com o codec OPUS.

## Exemplo de solicitacao

Exemplo de solicitacao para enviar uma mensagem de imagem usando uma identificacao de midia carregada e uma legenda.

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
