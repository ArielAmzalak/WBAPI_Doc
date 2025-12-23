![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Foverview%2Fqr-codes%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)

  + [Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)
  + [Official Business Accounts](/docs/whatsapp/official-business-accounts)
  + [Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)
  + [Business profiles](/docs/whatsapp/business-profiles)
  + [Display names](/docs/whatsapp/display-names)
  + [Receber aceitação](/docs/whatsapp/overview/getting-opt-in)
  + [Identity Change](/docs/whatsapp/overview/identity-change)
  + [Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)
* [Preços](/docs/whatsapp/pricing)
* [Limites de mensagens](/docs/whatsapp/messaging-limits)
* [Webhooks](/docs/whatsapp/webhooks)
* [Parceiros de soluções](/docs/whatsapp/solution-providers)
* [Cadastro Incorporado](/docs/whatsapp/embedded-signup)
* [Prévias de links](/docs/whatsapp/link-previews)
* [Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[QR Codes and Short Links](#qr-codes-and-short-links)

[Create QR code](#create-qr-code)

[Example request](#example-request)

[Example response](#example-response)

[Update a QR code](#update-a-qr-code)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Prefilled messages](#prefilled-messages)

[User experience](#user-experience)

[Best practices](#best-practices)

[Format](#format)

[Appearance](#appearance)

[FAQs](#faq)

[Voltar para Português (Brasil)](/docs/whatsapp/overview/qr-codes/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 31 de out
Atualização em Português (Brasil): 20 de jan de 2023

# QR Codes and Short Links

WhatsApp QR codes and short links create a digital doorstep for businesses, enabling them to stay connected with their existing customers and connect with new ones. This way, customers can simply scan QR codes with their mobile device camera or type in a short link to begin a chat thread, without needing to input a phone number.

Veja, crie, edite e exclua QR codes e links curtos na [API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api/qr-codes) ou na [interface do usuário do Gerenciador de Negócios](https://www.facebook.com/business/help/890732351439459).

### Limitations

* Um número de telefone da conta do WhatsApp Business (WABA, pelas iniciais em inglês) não pode ser associado a mais de 2.000 QR codes e links curtos.
* A QR code scan can initiate a pre-filled message containing up to 140 characters of text.
* As análises não estão disponíveis para QR codes e links curtos, já que limitamos a quantidade de dados registrada para proteger a privacidade dos usuários.

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

[Como faço para criar um código QR ou um link curto?](#faq_560003134683818)

Veja, crie, edite e exclua QR codes e links curtos na [API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api/qr-codes) ou na [interface do usuário do Gerenciador de Negócios](https://www.facebook.com/business/help/890732351439459).

[Link permanente](#faq_560003134683818)

[Quantos QR codes e links curtos posso criar?](#faq_291487228701047)

Um número de telefone da conta do WhatsApp Business (WABA, pelas iniciais em inglês) não pode ser associado a mais de 2.000 QR codes e links curtos.

[Link permanente](#faq_291487228701047)

[Qual é o melhor formato para otimizar a qualidade de impressão dos QR codes?](#faq_1202965523389527)

Para obter a melhor qualidade possível em materiais impressos, recomendamos usar o formato de arquivo `.svg`.

[Link permanente](#faq_1202965523389527)

[Qual é a melhoria dos links curtos em relação aos links wa.me atuais?](#faq_2683797565272531)

Com os novos links curtos, será possível editar ou excluir a qualquer momento as mensagens preenchidas automaticamente que estiverem associadas a um link. Além disso, a sintaxe da URL será reduzida a um código aleatório. Isso eliminará a necessidade de incorporar mensagens à URL e ocultará o telefone.

[Link permanente](#faq_2683797565272531)

[What happens if a user clicks a short link on a desktop?](#faq_260711435155407)

If the user has the WhatsApp desktop client installed, it will launch a chat thread with your business. If not, the user will be prompted to install the WhatsApp desktop client.

[Link permanente](#faq_260711435155407)

[O que acontecerá se um usuário ler um código QR ou clicar em um link curto que foi excluído?](#faq_282264656160456)

Caso um usuário tente acessar um código QR ou um link curto que foi excluído, uma mensagem de erro será exibida para indicar que esse código/link expirou.

[Link permanente](#faq_282264656160456)

[Qual é a diferença em relação aos QR codes gerados atualmente no meu ambiente de desenvolvimento?](#faq_271388994178981)

Agora, é possível gerar e gerenciar QR codes diretamente na WhatsApp Business Management API. Os usuários podem fazer a leitura do QR code com a câmera do WhatsApp, do iOS ou do Android.

Além disso, os QR codes do WhatsApp trazem as seguintes vantagens:

* As mensagens preenchidas automaticamente são totalmente personalizáveis e podem ser alteradas ou excluídas a qualquer momento.
* Os usuários sempre acessam o app diretamente, sem passar por uma página intersticial.
* Em caso de QR code expirado, a experiência no app enviará uma mensagem vazia ao usuário.

[Link permanente](#faq_271388994178981)

[Como posso garantir que os usuários leiam o código no idioma certo?](#faq_740574250086603)

Você é responsável por usar um QR code adequado à localização e ao idioma provável dos usuários.

[Link permanente](#faq_740574250086603)

[Será possível usar análises para monitorar as leituras de QR codes?](#faq_679778482866633)

As análises não estão disponíveis para QR codes e links curtos, já que limitamos a quantidade de dados registrada para proteger a privacidade dos usuários.

[Link permanente](#faq_679778482866633)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[QR Codes and Short Links](#qr-codes-and-short-links)

[Create QR code](#create-qr-code)

[Example request](#example-request)

[Example response](#example-response)

[Update a QR code](#update-a-qr-code)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Prefilled messages](#prefilled-messages)

[User experience](#user-experience)

[Best practices](#best-practices)

[Format](#format)

[Appearance](#appearance)

[FAQs](#faq)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfgDj9ly4KcDw6yBTqICmb43Jc2xgUtpeWdn3leXkYOOjQ&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfiwzVae9Wb-xz075Mh_EhrY1x79Y7EM5gbSmX4ya6eVUg&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfhpsL0_M12og-THhCBCwvoBtdM7g4XGn5v8Us8rPXBlTQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2V-9CL97qeK16OAI9QewwE_zhBhZtHi-CuJnhWZpRTsm9hdcohOjkpvN4lfsRyqe0VS-lAcuQwny0XxgiPlU_unl5TBoIkQfZIVz18Hk0pCbaoAYvGrS8oV8QO4H6g3HaxGTbMyMOZ6dPPf5Wzwg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_Afj8sv8QsyeynJqcCTNvBsa--NgSnboawIzjAsnWcB9Mxw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1PCV5bRQ7zuPZ22fLEOaSzjHWup3u1HAvxLRSyTo3klWIy_SjjpsK34bsUNJyzvOB9wvpjwNGW6feo08HKTwXX4wzSM08gtsecZPM-wTr-gcUszoRqCDmehyhC12UuOwULLXKxieBC52XzhTUgaA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfgPJ7O3eEKi59AzcUzlGLFz4SQGOfJP1Tgk9eUZ4EHz3g&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2hgL_HreBqWqvWPZvjuHoYJ4wJ0MqWyxq0WgdDr0WjPjBLQy8IOClKi7YJojY06tA_SMNv5W9QN_yvUaTBmYmZ_1udSGPHXE1PODv6kgNIx6xC6menrf-E4TttuXBsQqJJ9kxlHWgBM7qAVWMg6w)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfjamHjhQ55a6pEmk1YS5Q9vU6YhJ9Ts6lqMaSqBXBCwCA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT19VBxVA2yFLo7GwD3_ikcf06Gnd3aK7YXTqN_WfEXRXkvZLFI93j7RvSnfF3jpj9n9ppNQ2bGaw5OX90pSxzW5GlWlIiY8CXPNfL61zCwGUamuUOghuApIzYaX0mDkiUVi-p0bdFaCgombQtuoXQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0RWqQW2UXsqaam7Vqlhcv5sqTc4F9KP2GFUyc5FI4oTuuVA8sPUfBenDWgP5KVa1mKM1_r1WTqQSm3mXk9JffnR9BBAOmvr2MWkNQtFPf4UBUu_QHZnzSpAkJXN2FKL2w9WwFXZjS-eWh1OSARtQ)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0AaQOEWU_lyIyUnII5mgmYy5wtyyyzXSA6mJn7Y1Kduq16_eb0sHeGZcbY27-9TWCthVNxP3r_AbMyZDuZ6ayC4yKfhWDPPkVbCV5N_1XIAwpueA4l2oftiflj3K_9bB3Mlg5WqCvGYwiz15sDCQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_Afj5aDFhTCPBhPEAqKHxrC5QKMQrKTL1fsBaCW5UmeMNJA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfjnsmaFNGp_5tMFhWmpDCUAlwP9GSRv-SEywp-y3f1wnw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3iPH2c3bDhO8kzFhLAY5w9g4aHb8ptp2EXWs_eopIClwPZeSw5Mx0dlJTuMWxk_t1ZiP2CJ_JRQ7qYzc4DnHySjUfRoa3r_ilp8-J84b13aPDfg95fGNNcYnz0kuTT_dwan5viVG3SuIx-rZrxpA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_Afh6ngwtQN7eflTXd1NxbojmUKdvUD7qr_qbvtrQxVOHSQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2mZZx8nzHJjy5iS0sTSSD_c-QfO6IigB5jmCFRWbSpfiIR2uW4rXSOZk-YgAdVnjVnbe2W3Gv5z4AN3xiyafHZm0pZhwK93vsnE00tQ7anSexQJVFfaK32m1Lvf6S_XZQxH8qQWDkBsyoA8T8Cyw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_Afhfp7Ko9sknmkkjDyhAY8mD6GVAToe-NGup2QAKV6tNKg&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2I2HMcgvXiJJTpZQx1omcDa9wIw41nBtSsR1YM1WmqBWuYafIBgiYclbvB-YFzrH9wDFnQDiuZpGw_dyCernPu50pvnmi_sZW3H_hRat7Iwt_2k0Nt89Rnqrs2d7apLMMHV6vfYUp2Lm07vJMFlg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4_NAlc-tLyMIUu3vB6ysGg&oh=00_AfjNkyUdJjQiJzG_3ZRkLdqkUIFIcxrNbEIk_d8JXPC8Yw&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2iYOKbwOQ9wehP0sZigRnYIW8XCzHtHE-stgqjAM3oIB18rEOuz5XRBsMZECL0vyNHw82JSRF_Bo7WfnyeuwSM_1WYZwSfV48gi_rgmjoaowqJz7qGdVGT7LisfPVb-ezTglOpJbZKFj6OK05mbQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0sbM-Nh-t7VEBwNMiBILYqywUEHV2t1MHCQnPXQDCuk2vIO7FhP-3fdtE3V1WWJBz-mgBKyKzpHizXIQrBTlECfxnkBThw7FmU_zVkmqSxO3jAJbuuriMyVHCk0PyhH9a5sIn04WbjrmV0vraqYA)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)