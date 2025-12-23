+++
id = "qr-codes"
title = "QR Codes and Short Links"
summary = "WhatsApp QR codes and short links create a digital doorstep for businesses, enabling them to stay connected with their existing customers and connect with new ones."
source = "https://developers.facebook.com/docs/whatsapp/qr-codes"
lang = "en"
tags = ["whatsapp-business-platform", "messaging", "rate-limits"]
+++
# QR Codes and Short Links

WhatsApp QR codes and short links create a digital doorstep for businesses, enabling them to stay connected with their existing customers and connect with new ones. This way, customers can simply scan QR codes with their mobile device camera or type in a short link to begin a chat thread, without needing to input a phone number.

Veja, crie, edite e exclua QR codes e links curtos na [API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api/qr-codes) ou na [interface do usuario do Gerenciador de Negocios](https://www.facebook.com/business/help/890732351439459).

### Limitations

* Um numero de telefone da conta do WhatsApp Business (WABA, pelas iniciais em ingles) nao pode ser associado a mais de 2.000 QR codes e links curtos.
* A QR code scan can initiate a pre-filled message containing up to 140 characters of text.
* As analises nao estao disponiveis para QR codes e links curtos, ja que limitamos a quantidade de dados registrada para proteger a privacidade dos usuarios.

## Create QR code

To create a QR code, send a POST request to the [WhatsApp Business Phone Number > Message Qrdls](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/message_qrdls/) endpoint.

In your post body, include an object with a `prefilled_message` property set to your message text and a `generate_qr_image` property set to your preferred image format, either `SVG` or `PNG`.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/message_qrdls' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "prefilled_message": "Cyber Monday",
  "generate_qr_image": "SVG"
}'
```

### Example response

```
{
  "code": "4O4YGZEG3RIVE1",
  "prefilled_message": "Cyber Monday 1",
  "deep_link_url": "https://wa.me/message/4O4YGZEG3RIVE1",
  "qr_image_url": "https://scontent-iad3-2.xx.fbcdn.net/..."
}
```

## Get a list of QR codes and short links

To get a list of all QR codes on a business phone number, send a GET request to the [WhatsApp Business Phone Number > Message Qrdls](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/message_qrdls/) endpoint. To use the Business Manager to get a list of existing QR codes, see the [Help Center article](https://www.facebook.com/business/help/890732351439459).

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/message_qrdls' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [
    {
      "code": "4O4YGZEG3RIVE1",
      "prefilled_message": "Cyber Monday",
      "deep_link_url": "https://wa.me/message/4O4YGZEG3RIVE1"
    },
    {
      "code": "WOMVT6TJ2BP7A1",
      "prefilled_message": "Tell me more about your production workshop",
      "deep_link_url": "https://wa.me/message/WOMVT6TJ2BP7A1"
    }
  ]
}
```

## Get a QR code

To get information about a specific QR code, send a GET request to the [WhatsApp Business Phone Number > Message Qrdls](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/message_qrdls/) endpoint and append the QR code ID as a path parameter.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/message_qrdls/4O4YGZEG3RIVE1' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [
    {
      "code": "4O4YGZEG3RIVE1",
      "prefilled_message": "Cyber Monday",
      "deep_link_url": "https://wa.me/message/4O4YGZEG3RIVE1"
    }
  ]
}
```

## Update a QR code

To update a QR code, send a POST request to the [WhatsApp Business Phone Number > Message Qrdls](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/message_qrdls/) endpoint.

In the post body, include a `code` property set to the ID of the QR code you wish to update, and a `prefilled_message` property set to the new QR code text.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/message_qrdls' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
    "code": "4O4YGZEG3RIVE1",
    "prefilled_message": "Cyber Tuesday"
}'
```

### Example response

```
{
  "code": "4O4YGZEG3RIVE1",
  "prefilled_message": "Cyber Tuesday",
  "deep_link_url": "https://wa.me/message/4O4YGZEG3RIVE1"
}
```

### Delete QR code

QR codes do not expire automatically. To delete a QR code, send a DELETE request to the [WhatsApp Business Phone Number > Message Qrdls](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/message_qrdls/) endpoint and append the ID of the QR code you wish to retire as a path parameter. To use the Business Manager to delete QR codes, see the [Help Center article](https://www.facebook.com/business/help/890732351439459).

### Example request

```
curl -X DELETE 'https://graph.facebook.com/v24.0/106540352242922/message_qrdls/4O4YGZEG3RIVE1' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "success": true
}
```

## Prefilled messages

QR codes and short links can be programmed to populate a prefilled message. Prefilled messages can contain up to 140 characters of text. These messages are fully customizable and can be updated or deleted at any time.

## User experience

| User Scenario | Expected Behavior |
| --- | --- |
| User tries to access a code or link that has been deleted. | User sees an error message saying "This QR code [short link] has expired". |
| User scans the QR code or types in the short link of a business they previously blocked. | User gets a prompt asking if they would like to unblock the business to continue messaging them. |
| User clicks a short link on a desktop browser. | Desktop client launches with message populated in chat thread. If there is no client installed, user is prompted to install it. |

## Best practices

### Format

We recommend outputting the QR code as a scalable vector graphic (`.svg`) file. You can resize your QR Code to develop product packaging, signage, etc.

### Appearance

While we do not offer the capability to natively customize QR codes, you can do so by downloading and editing QR codes with the software of your choice. We recommend you do not customize the color or look and feel of the code itself in order to preserve readability.

## FAQs

[Como faco para criar um codigo QR ou um link curto?](#faq_560003134683818)

Veja, crie, edite e exclua QR codes e links curtos na [API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api/qr-codes) ou na [interface do usuario do Gerenciador de Negocios](https://www.facebook.com/business/help/890732351439459).

[Link permanente](#faq_560003134683818)

[Quantos QR codes e links curtos posso criar?](#faq_291487228701047)

Um numero de telefone da conta do WhatsApp Business (WABA, pelas iniciais em ingles) nao pode ser associado a mais de 2.000 QR codes e links curtos.

[Link permanente](#faq_291487228701047)

[Qual e o melhor formato para otimizar a qualidade de impressao dos QR codes?](#faq_1202965523389527)

Para obter a melhor qualidade possivel em materiais impressos, recomendamos usar o formato de arquivo `.svg`.

[Link permanente](#faq_1202965523389527)

[Qual e a melhoria dos links curtos em relacao aos links wa.me atuais?](#faq_2683797565272531)

Com os novos links curtos, sera possivel editar ou excluir a qualquer momento as mensagens preenchidas automaticamente que estiverem associadas a um link. Alem disso, a sintaxe da URL sera reduzida a um codigo aleatorio. Isso eliminara a necessidade de incorporar mensagens a URL e ocultara o telefone.

[Link permanente](#faq_2683797565272531)

[What happens if a user clicks a short link on a desktop?](#faq_260711435155407)

If the user has the WhatsApp desktop client installed, it will launch a chat thread with your business. If not, the user will be prompted to install the WhatsApp desktop client.

[Link permanente](#faq_260711435155407)

[O que acontecera se um usuario ler um codigo QR ou clicar em um link curto que foi excluido?](#faq_282264656160456)

Caso um usuario tente acessar um codigo QR ou um link curto que foi excluido, uma mensagem de erro sera exibida para indicar que esse codigo/link expirou.

[Link permanente](#faq_282264656160456)

[Qual e a diferenca em relacao aos QR codes gerados atualmente no meu ambiente de desenvolvimento?](#faq_271388994178981)

Agora, e possivel gerar e gerenciar QR codes diretamente na WhatsApp Business Management API. Os usuarios podem fazer a leitura do QR code com a camera do WhatsApp, do iOS ou do Android.

Alem disso, os QR codes do WhatsApp trazem as seguintes vantagens:

* As mensagens preenchidas automaticamente sao totalmente personalizaveis e podem ser alteradas ou excluidas a qualquer momento.
* Os usuarios sempre acessam o app diretamente, sem passar por uma pagina intersticial.
* Em caso de QR code expirado, a experiencia no app enviara uma mensagem vazia ao usuario.

[Link permanente](#faq_271388994178981)

[Como posso garantir que os usuarios leiam o codigo no idioma certo?](#faq_740574250086603)

Voce e responsavel por usar um QR code adequado a localizacao e ao idioma provavel dos usuarios.

[Link permanente](#faq_740574250086603)

[Sera possivel usar analises para monitorar as leituras de QR codes?](#faq_679778482866633)

As analises nao estao disponiveis para QR codes e links curtos, ja que limitamos a quantidade de dados registrada para proteger a privacidade dos usuarios.

[Link permanente](#faq_679778482866633)
