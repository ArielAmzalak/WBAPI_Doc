![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Finteractive-reply-buttons-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Interactive Reply Buttons](/docs/whatsapp/cloud-api/messages/interactive-reply-buttons-messages)

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

[Interactive reply buttons messages](#interactive-reply-buttons-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

[Webhooks](#webhooks)

[Example Webhook](#example-webhook)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Interactive reply buttons messages

Interactive reply buttons messages allow you to send up to three predefined replies for users to choose from.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440749535_402938502645501_9105062754221017983_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=5jwcZYuQiVsQ7kNvwFc9ER_&_nc_oc=AdlQmSW7za2Vq2ZLJu4x3hh5Aa7bEaLjxY2f5KeQUlnjWBBqopZ8BDRsQizZmMidrlQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afg6OdPnseH5plrALO5-LWsmFA6yy1C5s7RnzAzp0Bf7TA&oe=694046F1)

Users can respond to a message by selecting one of the predefined buttons, which triggers a messages webhook describing their selection.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/440803070_1108181003739406_7014741695346688945_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=I6pn1mSRB3oQ7kNvwFqzVR5&_nc_oc=AdnZ3hKrBdfaLk-EskcEG2I5YRweTtnEG4Qpzoax4Sbi2-8ZpFOPSlmsyFxJRr90PII&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afgtdyvwy62Vo4VBYdTsMZ-ju-gbDgJJjtLMBZm73fobDQ&oe=69405086)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send an interactive reply buttons message to a WhatsApp user.

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
    "type": "button",
    "header": {<MESSAGE_HEADER>},
    "body": {
      "text": "<BODY_TEXT>"
    },
    "footer": {
      "text": "<FOOTER_TEXT>"
    },
    "action": {
      "buttons": [
        {
          "type": "reply",
          "reply": {
            "id": "<BUTTON_ID>",
            "title": "<BUTTON_LABEL_TEXT>"
          }
        }
        <!-- Additional buttons would go here (maximum 3) -->
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
| `<BODY_TEXT>`  *String* | **Required.**  Body text. URLs are automatically hyperlinked.  Maximum 1024 characters. | `Hi Pablo! Your gardening workshop is scheduled for 9am tomorrow. Use the buttons if you need to reschedule. Thank you!` |
| `<BUTTON_ID>`  *String* | **Required.**  A unique identifier for each button. Supports up to 3 buttons.  Maximum 256 characters. | `change-button` |
| `<BUTTON_LABEL_TEXT>`  *String* | **Required.**  Button label text. Must be unique if using multiple buttons.  Maximum 20 characters. | `Change` |
| `<FOOTER_TEXT>`  *String* | **Required if using a footer.**  Footer text. URLs are automatically hyperlinked.  Maximum 60 characters. | `Lucky Shrub: Your gateway to succulents!™` |
| `<MESSAGE_HEADER>`  *JSON Object* | **Optional.**  Header content. Supports the following types:   * `document` * `image` * `text` * `video`   Media assets can be sent using their [uploaded media](/docs/whatsapp/cloud-api/reference/media#upload-media) `id` or URL `link` (not recommended). | Image header example using uploaded media ID (same basic structure for all media types):   ``` {   "type": "image",   "image": {     "id": "2762702990552401" } ```   Image header example using hosted media:   ``` {   "type": "image",   "image": {     "link": "https://www.luckyshrub.com/media/workshop-banner.png" } ```   Text header example:   ``` {   "type":"text",   "text": "Workshop Details" } ``` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example Request

Example request to send an interactive reply buttons message with an image header, body text, footer text, and two quick-reply buttons.

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
    "type": "button",
    "header": {
      "type": "image",
      "image": {
        "id": "2762702990552401"
      }
    },
    "body": {
      "text": "Hi Pablo! Your gardening workshop is scheduled for 9am tomorrow. Use the buttons if you need to reschedule. Thank you!"
    },
    "footer": {
      "text": "Lucky Shrub: Your gateway to succulents!™"
    },
    "action": {
      "buttons": [
        {
          "type": "reply",
          "reply": {
            "id": "change-button",
            "title": "Change"
          }
        },
        {
          "type": "reply",
          "reply": {
            "id": "cancel-button",
            "title": "Cancel"
          }
        }
      ]
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

## Webhooks

When a WhatsApp user taps on a reply button, a **messages** webhook is triggered that describes their selection in a `button_reply` object:

```
"button_reply": {
  "id": "<BUTTON_ID>",
  "title": "<BUTTON_LABEL_TEXT>"
}
```

* `<BUTTON_ID>` — The button ID of the button tapped by the user.
* `<BUTTON_LABEL_TEXT>` — The button label text of the button tapped by the user.

### Example Webhook

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
                  "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBJBM0Y4RUU0RUNFQkFDMjYzQUMA"
                },
                "from": "16505551234",
                "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgASGBQzQThBREYwNzc2RDc2QjA1QTIwMgA=",
                "timestamp": "1714510003",
                "type": "interactive",
                "interactive": {
                  "type": "button_reply",
                  "button_reply": {
                    "id": "change-button",
                    "title": "Change"
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

[Interactive reply buttons messages](#interactive-reply-buttons-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

[Webhooks](#webhooks)

[Example Webhook](#example-webhook)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfgHSp-CHudxEmBzh83ZwbG4BMrX6ty7EaqunXX-SufhOw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afigf8zBrtj3M2yaY4KDypNEdUz6BbJ7Ej_GVdoEALaAow&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfjziM6-cwLFt_u_wjVTZplF0LTsR0vCdU3U0K8C7XvKEw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Pewu5nVKJfFdog7lK0yA9RCk_qKlG5sL05803An3FpvB9lZNaXsgKAQmzCEuR5E060lf3IiK8M31JdBL6Sd_Fn0XjDt0gzbPMQC6PNEHlldAwfyALZekFodhO_2Ez5JG3KqCH_yXBKZ8SyodEKA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfiS6Qdxg5-1sjagjI8vnHZ-G4zdA-Vgt0qUyhNz7AtGjg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3AFKb4VWysExjsvjbvifO7sze_80owkyW9CFYpCSloD7ccchUx66wY5WzNLP2N9W4KHTsv5dGjQcb5WOcrlDXr_OqVMJDiGKqQ1Sc_QJ-YN6RfpMpuklNvqDhB4scRqM-onlqetmC7iIk1kOZuVg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfgBxgD_VFKDqPVwbuRvMHqf4ckZoEFrASfpGfY5Sy1EoQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1u5cI0Ntb_d3Eg3LrxyuVRjNNTxXHUaZW9-XKrXdjoUs1BmwYBdmC7pxHrMS2-wfng15cd2fYyNFol4DpiedkbUgKYS4Wpt5Q8vK4w6EnnSZHDCkwxUx901QcHedlujHjXje87zRNwOCBBY_02AA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afic9n5T8VeXT3MuJc1h57LULxoOPk9gMT8sboZcgBDhhg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2FEEudabUW_uZ7LgE1Q6PwMVJplNm53x5Bh6FOaBBYouXMsVWnKK-lKo8fGo1YUHhNjlzaS33C9vVV2fwvdCTGzhH8dwzg7aka4vcjGJr3TTmXD6hTNaGctv62KnX-lf5jCORrzpWDi2R9_SFWEA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0mXRprxB3GZS1es2fozLSXyID26xogdS3f5z1PuIv8hKvB9Qq05n9LHyGrLGzrfC_qcw_yNdnJgAW4ftn9WD2P99w6JrNdst-hTgkoQgEvgIeaVQ-NLNsSBn9EABc9Ug0jH0H0Bmr8pdMap-8MLw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1GbUUqLilRdwtZfpWXCToXOW7QR1GgD46FHGsLLjxIfV_EkUPmmwGW_vXpycQaD9htdeWS05iNEHUKm-5MNY2gUlr_EiUxc9594SiEjVDgB1-I2aYFLl2dsL4fcUaaamYu2EJAwMTvDdpHo2oC6g)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfgTByQhraNK4Ag-sriT9r4bSu0xBHnu6r9RYXzbh3LOfA&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afi77-NvjDJaHIYeTi7yEMdLoH_meyB_Two2UzizFS6Xkg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2aGi3XUuuioxdBParctRxqI5Wa-qPCYT_w-H3CeB2gp8n8p1w5rbc8KurcIINkVBXrMCNa0i1Tyu0rCs9HwFjl5tQbcTDPR5wNrXC4ljEVmlLPM0RAG-7hSS73lnHtPC3My4lgOW_rERuqp0Bvcw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_Afg66NBqH4VIwB98Yj79JYg3uJPShTEn21A-A4H-O15CNQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2M6R4VhLzl-YH-Ymnq9993IXPhLBI2HE29dspGaqALSrfUwpLzQ4izi59CGxoINi2Kg15gg5Uaf540fjcxnxLR2wgTva3bKkFmyI09ZYw-rzqyT3jE28GWU1Oq9EKq8VQAbrXek2oU1zYYNzL63Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfiMtKd860PNjT-vmifLFU_j8KNLnD1VqvdBFAtnFHc2LA&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2x8NJ6Q_KFiwIq1WVZGW_ZZsa5L6RV_SXEYJ5jnSynPYjGPIYZyHfsBGphvGItuuaR0qPGdl7dmmug686CrFA4a5GE0i4YqZXGilzUgg87bmOLy_7Du1o1JMQG9_-QmaB8xzJ1qScE389Y8HMRtg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qURTKcqRavReN6uB49W4Ww&oh=00_AfjKqAvIwQI__6pTgmgh4YO-SkvlS7XkW32o20JT3pVKpw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1kN_sYM0jU0BIdo92ITUKvdoGMcgeQ-sSzsqyOWmdyArleu1c-0ISCdM32xc9Nd-Hj7Objk-EzBg-7SbgQNwUYiB4tBlxYHoVXajCnAGqWx85muZ7tmG22irHVj2cVyZjeYPgtsUKiDhy6bkMn3w)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1yBgcBHsCp7uaU51kcO72z1p9JoHrECS4hQ-B8ff4d75EACwfsIoa48bnEk6Xsih7R4yAMRvga7uVKw3GfFdogBiZUc_jN4aKWP_YgECbPZnf3-IIze2Mm2ZBpH7WEDX5i_YMroYPz-6sdtCVNLg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)