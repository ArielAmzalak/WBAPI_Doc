![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fcoupon-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Modelos de cupom](/docs/whatsapp/business-management-api/message-templates/coupon-templates)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)

    - [Custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates)
    - [Modelos de catálogo](/docs/whatsapp/business-management-api/message-templates/catalog-templates)
    - [Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template)
    - [Modelos de cupom](/docs/whatsapp/business-management-api/message-templates/coupon-templates)
    - [Modelos de oferta por tempo limitado](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates)
    - [Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates)
    - [Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates)
    - [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates)
    - [Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates)
  + [Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)
  + [Componentes](/docs/whatsapp/business-management-api/message-templates/components)
  + [Management](/docs/whatsapp/business-management-api/message-templates/template-management)
  + [Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)
  + [Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)
  + [Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)
  + [Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)
  + [Review](/docs/whatsapp/business-management-api/template-review)
  + [Languages](/docs/whatsapp/business-management-api/message-templates/supported-languages)
  + [Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)
  + [Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)
  + [Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)
  + [Groups](/docs/whatsapp/business-management-api/message-templates/template-groups)
  + [Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)
  + [Time-to-live](/docs/whatsapp/business-management-api/time-to-live)
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

[Coupon code templates](#coupon-code-templates)

[Limitations](#limitations)

[Creating coupon code templates](#creating-coupon-code-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Sending coupon code templates](#sending-coupon-code-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters-2)

[Example Request](#example-request-2)

[Example Response](#example-response-2)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/message-templates/coupon-templates/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 3 de nov
Atualização em Português (Brasil): 10 de nov de 2023

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# Coupon code templates

Coupon code templates are marketing templates that display a single copy code button. When tapped, the code is copied to the customer's clipboard.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/365756533_1756280054770140_7287687181799037425_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=WNAi-9JViF8Q7kNvwFvjqJx&_nc_oc=Adlr7UPgtyTJNXjeGLtlywvFfA6AR19CHdbKfEhwJtL5X5r6MinlDQYfm0fGg10ZHOI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mLEyvn3-VOnI2dQx68urhw&oh=00_Afh-75atTF1QeHiXEabplHNlMqXrc8qiwItwEtjDw8tpuw&oe=69407A25)

## Limitations

* Coupon code templates are currently not supported by the WhatsApp web client.
* Codes are limited to 15 characters.
* Button text cannot be customized.
* Templates are limited to one copy code button.

## Creating coupon code templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates) endpoint to create coupon code templates.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "<NAME>",
    "language": "<LANGUAGE>",
    "category": "MARKETING",
    "components": [
      {
        "type": "BODY",
        "text": "<BODY_TEXT>"
      },
      {
        "type": "BUTTONS",
        "buttons": [
          {
            "type": "COPY_CODE",
            "example": "<EXAMPLE>"
          }
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<NAME>`  *String* | **Required.**   Template name.   Maximum 512 characters. | `fall2023_promotion` |
| `<LANGUAGE>`  *Enum* | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<EXAMPLE>`  *String* | **Required.**   Coupon code to be copied when tapped.   Maximum 15 characters. | `25OFF` |

### Response

Upon success, the API will respond with the following:

```
{
   "category" : "<CATEGORY>",
   "id" : "<ID>",
   "status" : "<STATUS>"
}
```

### Response parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<CATEGORY>`  *Enum* | Template category. | `MARKETING` |
| `<ID>`  *Numeric string* | Template ID. | `1924084211297547` |
| `<STATUS>`  *Enum* | Template status. | `PENDING` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "coupon_code_fall2023_25off",
  "language": "en_US",
  "category": "MARKETING",
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT",
      "text": "Our Fall Sale is on!"
    },
    {
      "type": "BODY",
      "text": "Shop now through November and use code {{1}} to get {{2}} off of all merchandise!",
      "example": {
        "body_text": [
          [
            "25OFF",
            "25%"
          ]
        ]
      }
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "QUICK_REPLY",
          "text": "Unsubscribe"
        },
        {
          "type": "COPY_CODE",
          "example": "250FF"
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "category" : "MARKETING",
  "id" : "1924084211297547",
  "status" : "PENDING"
}
```

## Sending coupon code templates

### Request syntax

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an approved coupon template in a template message.

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "messaging_product": "whatsapp",
    "to": "<TO>",
    "type": "template",
    "template": {
      "name": "<NAME>",
      "language": {
        "code": "<CODE>"
      },
      "components": [
        {
          "type": "button",
          "sub_type": "COPY_CODE",
          "index": <INDEX>,
          "parameters": [
            {
              "type": "coupon_code",
              "coupon_code": "<COUPON_CODE>"
            }
          ]
        }
        // ... Add other components if needed
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<TO>`  *String* | **Required.**   The WhatsApp ID or phone number of the customer to send the message to. See [Phone Number Formats](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/). | `+16505551234` |
| `<NAME>`  *String* | **Required.**   Name of the template to be sent. | `coupon_code_fall2023_25off` |
| `<CODE>`  *String* | **Required.**   The template's language and locale code. | `en_US` |
| `<INDEX>`  *Integer* | **Required.**   Indicates order in which button should appear, if the template uses multiple buttons.   Buttons are zero-indexed, so setting value to `0` will cause the button to appear first, and another button with an index of `1` will appear next, etc. | `0` |
| `<COUPON_CODE>`  *String* | **Required.**   The coupon code to be copied when the customer taps the button. Only accepting alphanumeric characters. | `25OFF` |

### Response syntax

Upon success the API will respond with:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<WHATSAPP_USER_PHONE_NUMBER>",
      "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>"
    }
  ],
  "messages": [
    {
      "id": "<WHATSAPP_MESSAGE_ID>",
      "group_id": "<GROUP_ID>", <!-- Only included if messaging a group -->
      "message_status": "<PACING_STATUS>" <!-- Only included if sending a template -->
    }
  ]
}
```

### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | The string identifier of a group made using the Groups API.  This field shows when messages are sent, received, or read from a group.  [Learn more about the Groups API](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) | `Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD` |
| `<PACING_STATUS>`  *String* | Indicates [template pacing](/docs/whatsapp/message-templates/guidelines#template-pacing) status. The `message_status` property is only included in responses when sending a [template message](/docs/whatsapp/cloud-api/guides/send-message-templates) that uses a template that is being paced. | `wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI4MjZGRDA0OUE2OTQ3RkEyMzcA` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | WhatsApp user's WhatsApp phone number. May not match `wa_id` value. | `+16505551234` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user's WhatsApp ID. May not match `input` value. | `16505551234` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp Message ID. This ID appears in associated **messages** webhooks, such as sent, read, and delivered webhooks. | `wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI4MjZGRDA0OUE2OTQ3RkEyMzcA` |

### Example Request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "coupon_code_fall2023_25off",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "25OFF"
          },
          {
            "type": "text",
            "text": "25%"
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "COPY_CODE",
        "index": 1,
        "parameters": [
          {
            "type": "coupon_code",
            "coupon_code": "25OFF"
          }
        ]
      }
    ]
  }
}'
```

### Example Response

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "16505551234",
      "wa_id": "16505551234"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBIxRjk1REYzMDBERDE3RUI0RDYA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Coupon code templates](#coupon-code-templates)

[Limitations](#limitations)

[Creating coupon code templates](#creating-coupon-code-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Sending coupon code templates](#sending-coupon-code-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response syntax](#response-syntax)

[Response parameters](#response-parameters-2)

[Example Request](#example-request-2)

[Example Response](#example-response-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=He3hiVfxZkr7cgUIRCj9ag&oh=00_AfgGq6SmmcL2dNhLIe0nkgilIgLmqvhMseVNgdnzSQCmsw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=He3hiVfxZkr7cgUIRCj9ag&oh=00_AfioJTFLyNHquWC3vMrClKasgATzsSS_Kb6Gbi_NYc9MxA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=He3hiVfxZkr7cgUIRCj9ag&oh=00_AfiEd_FkY3dLOv7v1MdcbNnYfxrI1Yjz5fN_mlqw6E25RQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=He3hiVfxZkr7cgUIRCj9ag&oh=00_AfhMuxtEsEx1G3YrftXBWkGhJHUprrRBZj84Y0Y7_A38FQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=He3hiVfxZkr7cgUIRCj9ag&oh=00_AfilnJITveeCpJr-X0opqNG3MGCR5p_ZfPFBeg1YSz4Tpg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT05243TgtNXrnqOCMZK_pLnpHSTmNcV3pXVSJ-ZIGoe6wmAX2KBpiHo4GLkpENtGRpYm5SbW3XoSuOEJkG5TU0AQLJ7-wtsOBN1to4_3TGw6CiJCl8yeLwU4N98DYu4f5_F2byBQGuUsz4OwgD82A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)