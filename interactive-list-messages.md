![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Finteractive-list-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Interactive List](/docs/whatsapp/cloud-api/messages/interactive-list-messages)

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

[Interactive list messages](#interactive-list-messages)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Interactive list messages

Interactive list messages allow you to present WhatsApp users with a list of options to choose from (options are defined as rows in the request payload):

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/439906651_815131396632137_2393939757123941379_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=OSNqgLoqJr8Q7kNvwF6G9UT&_nc_oc=AdmRpihZFpP3Afm9G8gyMGhOlzc13g01eACgewerSj9JbuhP3or43OSQf_Wie5J20_c&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=3Kc-mQm6CRJtquAFoT09pg&oh=00_Afhbeyyznw_KE3pFPOUiEQTgiAms0ayVZosD-HVK_MA_zw&oe=694050D1)

When a user taps the button in the message, it displays a modal that lists the options available:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/440772174_1215031642793437_4263879536705453309_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=HjgX2T9ahI4Q7kNvwGqWTkv&_nc_oc=AdnEyp38ggFT5ojJCFolyPY0gFGVMzIvr7Evv2YvSOTrIiteUnQBVv9KUy2lXU6hByc&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=3Kc-mQm6CRJtquAFoT09pg&oh=00_Afh-DKvGDXvCu0duBNEd90T48Tvfmz2KGAITqSyGSDL5ZA&oe=69407243)

Users can then choose one option and their selection will be sent as a reply:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/440751989_956441365805448_2344471884869029846_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=aaFZEtspdfIQ7kNvwErUTuF&_nc_oc=Admvfi8k8GkinYj-V6euy-0XQ-XKaw6ykk_LYb-gQQdlOlTjB0CBWzfhc0uGdz2Vb1k&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=3Kc-mQm6CRJtquAFoT09pg&oh=00_Afgt2bpnDTFfkndpuQqsgLAJhOeI_MD-RpGoKNEjnp3glQ&oe=694052D3)

This triggers a webhook, which identifies the option selected by the user.

Interactive list messages support up to 10 sections, with up to 10 rows for all sections combined, and can include an optional header and footer.

## Request Syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an interactive list message to a WhatsApp user.

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
    "type": "list",
    "header": {
      "type": "text",
      "text": "<MESSAGE_HEADER_TEXT>"
    },
    "body": {
      "text": "<MESSAGE_BODY_TEXT>"
    },
    "footer": {
      "text": "<MESSAGE_FOOTER_TEXT>"
    },
    "action": {
      "button": "<BUTTON_TEXT>",
      "sections": [
        {
          "title": "<SECTION_TITLE_TEXT>",
          "rows": [
            {
              "id": "<ROW_ID>",
              "title": "<ROW_TITLE_TEXT>",
              "description": "<ROW_DESCRIPTION_TEXT>"
            }
            <!-- Additional rows would go here -->
          ]
        }
        <!-- Additional sections would go here -->
      ]
    }
  }
}'
```

## Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BUTTON_TEXT>`  *String* | **Required.**  Button label text. When tapped, reveals rows (options the WhatsApp user can tap). Supports a single button.  Maximum 20 characters. | `Shipping Options` |
| `<MESSAGE_BODY_TEXT>`  *String* | **Required.**  Message body text. Supports URLs.  Maximum 4096 characters. | `Which shipping option do you prefer?` |
| `<MESSAGE_FOOTER_TEXT>`  *String* | **Optional.**  Message footer text.  Maximum 60 characters. | `Lucky Shrub: Your gateway to succulents™` |
| `<MESSAGE_HEADER_TEXT>`  *String* | **Optional.**  The `header` object is optional. Supports `text` header type only.  Maximum 60 characters. | `Choose Shipping Option` |
| `<ROW_DESCRIPTION_TEXT>`  *String* | **Optional.**  Row description.  Maximum 72 characters. | `Next Day to 2 Days` |
| `<ROW_ID>`  *String* | **Required.**  Arbitrary string identifying the row. This ID will be included in the webhook payload if the user submits the selection.  At least one row is required. Supports up to 10 rows.  Maximum 200 characters. | `priority_express` |
| `<ROW_TITLE_TEXT>`  *String* | **Required.**  Row title. At least 1 row is required. Supports up to 10 rows.  Maximum 24 characters. | `Priority Mail Express` |
| `<SECTION_TITLE_TEXT>`  *String* | **Required.**  Section title text. At least 1 section is required. Supports up to 10 sections.  Maximum 24 characters. | `I want it ASAP!` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

Example request to send an interactive list message with a header, body, footer, and two sections containing two rows each.

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
    "type": "list",
    "header": {
      "type": "text",
      "text": "Choose Shipping Option"
    },
    "body": {
      "text": "Which shipping option do you prefer?"
    },
    "footer": {
      "text": "Lucky Shrub: Your gateway to succulents™"
    },
    "action": {
      "button": "Shipping Options",
      "sections": [
        {
          "title": "I want it ASAP!",
          "rows": [
            {
              "id": "priority_express",
              "title": "Priority Mail Express",
              "description": "Next Day to 2 Days"
            },
            {
              "id": "priority_mail",
              "title": "Priority Mail",
              "description": "1–3 Days"
            }
          ]
        },
        {
          "title": "I can wait a bit",
          "rows": [
            {
              "id": "usps_ground_advantage",
              "title": "USPS Ground Advantage",
              "description": "2–5 Days"
            },
            {
              "id": "media_mail",
              "title": "Media Mail",
              "description": "2–8 Days"
            }
          ]
        }
      ]
    }
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

## Webhooks

When a WhatsApp user selects an option and sends their message, a **messages** webhook is triggered identifying the ID (`id`) of the option they chose.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "contacts": [
              {
                "profile": {
                  "name": "Pablo Morales"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "15550783881",
                  "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBIwMjg0RkMxOEMyMkNEQUFFRDgA"
                },
                "from": "16505551234",
                "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQTZDMzFGRUFBQjlDMzIzMzlEQwA=",
                "timestamp": "1712595443",
                "type": "interactive",
                "interactive": {
                  "type": "list_reply",
                  "list_reply": {
                    "id": "priority_express",
                    "title": "Priority Mail Express",
                    "description": "Next Day to 2 Days"
                  }
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Interactive list messages](#interactive-list-messages)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=isevGS3qJ3ZxrqwHMaYq-g&oh=00_AfhvdckC2Rxnnippmt14oMYdMX4t5Ng-bUsSIz4_yUbpIA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=isevGS3qJ3ZxrqwHMaYq-g&oh=00_Afha29CfTrcEFKK2R0XkAgGc9RjoaGm_Bnv7CBdYXN12ng&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=isevGS3qJ3ZxrqwHMaYq-g&oh=00_AfgLlagrOHrBkdUbY-mGWIBMptR2Nnl0-nWvsEUjVu-PNw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=isevGS3qJ3ZxrqwHMaYq-g&oh=00_Afj-8fStKFPdOKbswI144duXvgzGbIqKqTygEX_eeeeD0A&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=isevGS3qJ3ZxrqwHMaYq-g&oh=00_AfjmCMUJV3SpxbdKQuQWc_4WO--5F6qabUzHDMha_m1ftw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2OmMhhgkFQEXEpKCFUf7MQV7XRTx2tomksgOgZMh4Q61DyjZbm_ll0Hu8C2lAyW3Qrjn0gsskK8CI-soe_bc8auOHv4-0WPmY01IacdL3ReCOApf6-lXthZxuKbByvy5Y8tMRN1OOhPeITppKE8g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)