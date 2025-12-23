![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Finteractive-media-carousel-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Interactive media carousel](/docs/whatsapp/cloud-api/messages/interactive-media-carousel-messages)

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

[Interactive media carousel messages](#interactive-media-carousel-messages)

[How to build a media carousel message](#how-to-build-a-media-carousel-message)

[The card object](#the-card-object)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Card Object Parameters](#card-object-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Interactive media carousel messages

This message type will be available for delivery to WhatsApp users on November 11.

The interactive media carousel message enables businesses to send horizontally scrollable cards with images or videos, each with a call-to-action button, within WhatsApp conversations. This format allows users to browse multiple offers or content in a single message, providing a rich and engaging experience via the WhatsApp Business APIs and mobile clients.

## How to build a media carousel message

The media carousel message contains a `card` object. You must add at least 2 card objects to your message, and can add a maximum of 10. Each card exists in a `cards[]` array and must be given a `card_index` value of `0` through `9`.

The type of each card must be set to `"cta_url"`, and all cards must have the same header type (`"image"` or `"video"`). Each card must include a header, a unique index, and a call-to-action button with display text and a URL.

You must add a message body to the message (max 1024 characters). No header, footer, or buttons are allowed outside the cards.

### The `card` object

```
...
{
  "card_index": 0,
  "type": "cta_url",
  "header": {
    "type": "image",
    "image": {
      "link": "https://example.com/image1.png"
    }
  },
  "body": {
    "text": "Exclusive deal #1"
  },
  "action": {
    "name": "cta_url",
    "parameters": {
      "display_text": "Shop now",
      "url": "https://shop.example.com/deal1"
    }
  }
}
...
```

## Request Syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<PHONE_NUMBER>",
    "type": "interactive",
    "interactive": {
      "type": "carousel",
      "body": {
        "text": "Check out our latest offers!"
      },
      "action": {
        "cards": [
          {
            "card_index": 0,
            "type": "cta_url",
            "header": {
              "type": "image",
              "image": {
                "link": "https://example.com/image1.png"
              }
            },
            "body": {
              "text": "Exclusive deal #1"
            },
            "action": {
              "name": "cta_url",
              "parameters": {
                "display_text": "Shop now",
                "url": "https://shop.example.com/deal1"
              }
            }
          },
          {
            "card_index": 1,
            "type": "cta_url",
            "header": {
              "type": "image",
              "image": {
                "link": "https://example.com/image2.png"
              }
            },
            "body": {
              "text": "Exclusive deal #2"
            },
            "action": {
              "name": "cta_url",
              "parameters": {
                "display_text": "Shop now",
                "url": "https://shop.example.com/deal2"
              }
            }
          }
        ]
      }
    }
  }'
```

## Request parameters

| Field | Description | Sample Value |
| --- | --- | --- |
| `<API_VERSION>`   *String* | **Required**   API version to use | `v19.0` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`   *String* | **Required**   WhatsApp Business phone number ID | `1234567890` |
| `<ACCESS_TOKEN>`   *String* | **Required**   Access token for authentication | `EAAG...` |
| `<PHONE_NUMBER>`   *String* | Recipient's WhatsApp phone number | `16505551234` |
| `<MESSAGE_BODY_TEXT>`   *String* | **Required.** Maximum 1024 characters. | `Check out our latest offers!` |

## Card Object Parameters

| Field | Description | Sample Value |
| --- | --- | --- |
| `card_index`   *Integer* | **Required**   Unique index for each card (0-9). | `0` |
| `type`   *String* | **Required**   Must be `"cta_url"`. | `"cta_url"` |
| `header.type`   *String* | **Required**   `"image"` or `"video"` (all cards must match). | `"image"` |
| `header.image.link`   *String* | Required if header.type is `"image"`. | `"https://example.com/image1.png"` |
| `header.video.link`   *String* | Required if header.type is `"video"`. | `"https://example.com/video1.png"` |
| `body.text`   *String* | *Optional*   Max 160 chars, and up to 2 line breaks. | `"Exclusive deal #1"` |
| `action.name`   *String* | **Required**   Must be `"cta_url"`. | `"cta_url"` |
| `action.parameters.display_text`   *String* | Button display text. Max 20 chars. | `"Shop now"` |
| `action.parameters.url`   *String* | Button URL | `"https://shop.example.com/deal1"` |

## Example Request

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "1234567890",
  "type": "interactive",
  "interactive": {
    "type": "carousel",
    "body": {
      "text": "Check out our latest offers!"
    },
    "action": {
      "cards": [
        {
          "card_index": 0,
          "type": "cta_url",
          "header": {
            "type": "image",
            "image": {
              "link": "https://example.com/image1.png"
            }
          },
          "body": {
            "text": "Exclusive deal #1"
          },
          "action": {
            "name": "cta_url",
            "parameters": {
              "display_text": "Shop now",
              "url": "https://shop.example.com/deal1"
            }
          }
        },
        {
          "card_index": 1,
          "type": "cta_url",
          "header": {
            "type": "image",
            "image": {
              "link": "https://example.com/image2.png"
            }
          },
          "body": {
            "text": "Exclusive deal #2"
          },
          "action": {
            "name": "cta_url",
            "parameters": {
              "display_text": "Shop now",
              "url": "https://shop.example.com/deal2"
            }
          }
        }
      ]
    }
  }
}
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

[Interactive media carousel messages](#interactive-media-carousel-messages)

[How to build a media carousel message](#how-to-build-a-media-carousel-message)

[The card object](#the-card-object)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Card Object Parameters](#card-object-parameters)

[Example Request](#example-request)

[Example Response](#example-response)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfgUqiuyvbsn7glvFY4MLVSy8mXZkiSkqgxrdzJGZsLDsw&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_Afg2H79Kf5oQg9o1wlYOR4w-cNg6wMF--8O2u48sTCTPGg&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfgAtItmFhQ6UBsMlht6t-KLCWiAZGp0pMwSruKH_OwdnQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0Xho6ihnbz6u4eKwRt-Rykc6AycLjSWYPHa497Wh9jPZp5sgUcZYl1nEoGVZxNwIQYkY-m6l86ay89LxcnmVxoONM-GahyxXG_fjMc69TEkx5ALYwnZvhX-Ln09U8Z1jBhIBr2VlRJ4W-7YTe-vA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfjcgxOOe_p64dHquwT_3i7LK2Hd7hsRVxUnAXPrrMca2w&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT18HGmRi8KBWPhYoKEQk7uFQSniEkiKIXuTXWx_zd9S98ep2TfVkcHs_xseYAmWiy4rik8f4RA3gMzvtZsFdJLxXmGRpNe-VfJDcBsjitFRHGN3DYL9ICrajBB_pfFBEud2a0824K5SsS0PcdiZKg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfgPX6CODtQ8bw6ZtqPdJcdr4oregnX3UEXXLFps9qJV8g&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0Io9KVRfSduB8nnzM_v8XIn14mVbvH5zZaojo_oDuuj8up6p1bLJkHjjtvIAzUhVLVv2YfS9aT4qDzGMPDeysDhozRGEwGDuL81ujowIJXvjwFSb6he5G8iPsaC-aRemNvt00a7sc_YJkSdBK4Pg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfjPRpsq1SvatlyzDgot8dGncEKB2e0RJr_71dhNd4aKbw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3FrhjIjTeM7beRkC5r8wf-PdTNl0feHz0kbuYPPP5pmNQwUbCP-JDzubV_suRfjYMNiFS9L-n5qPirC_KgqjnzfYzrbN_LxorzRAgaGOdyk5DVCKWCbCWrPNAXA6FPKiXT05Urg-iWNK6EkxE7Ow)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0qKy5dk71Ic5mDR818PciU_M5_844wC53n7Q9KD2Qz1_z6DWBTLYNLEupvg6YLZvE1BZ0NPSCXl0w33rHLDIfURvD56sgmhPmu3bsb04WigVw7350rL5RY_MjsfDRCi_aN79HRQctofydfNgdKeQ)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0PYxzVUvFjiHNhU2yspCGIwrfh5EefPx6o7838vso7Ym45AWsRs8EOIQGfS7tGFaOFHQf0WHUAlJhhr3u8Jax-zpZQkT2RUslYEegnapUDvMxm819YTjxuiMOJVfMrKNUKXfWkULnBkaRGlXE2Ug)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfhPfIcBiUOhFJsFJtr6REwnbZh0B6vpbpzUZ0pip18ZyA&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfjDSpumYpc73-9kLrAoDIiz_gUltFVxGQhn4uCGdv-hQQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1DsNgnwaP5FvahO19sGu12JhU436kYAReLc-oDLCkz6bWFv2WEfKXmQTgcbrvoblYd1pBwZII3eQpCzNC9d6CkuiH9zvERFSY2it3BU6ngotJy9fDLC-RjCOFmtgFcKkURm95Pve7ZUXxDca4d8A)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfiDyotCgtYdK4E70utesy0bPszCI5RyAR3fDU9nvORYCw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT07rCIeocNH89kc0HlGb1lt4YITOCurNvZwLWFulARXzl0Ugjy0_yTmCws8PEU7qd6wxmp0JsbtS_T6e6tFgPWRZogGxJY7blTGixENiHRp63bAjosEq12XhpWPvZQg8LhSrdpdnh802MsuCZ1ohQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfhaD_jPMkMC2AAbdKQlZvrhyLHB4opM3wXPsO6Yf-LOMw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3crIqqIu1XYFgdal6CfqsWEkyCM6l9W0Yqac3pru0ZKsdXfJal-4xGPssO0DPNu-_hmHQHVUHjsQcDg8l0TAidNCez9Lwr0thjFgHjV1M5xhhQFpgeWHWjnWgDTFeRXrDRVh7FesEzjKXUcn4Hqw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=j_lvVKHCcwqA5v1x2Kl5ZQ&oh=00_AfgnsHRh-GsHqkqZBJbtnUtvCnjIcCNCzSZy-D0MmMcQwQ&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3uJUYnW_DYExxcbAgq_sOPaHhnYkO3xt8Oxcg4-y4qoGPnq-TbIu4L7E_aecbotzYxIykTJ4or9Xbo6MRUr_3gieMGvXtmo0PCW9Wa5eTjHAiQAXXn2HFGXBI_u-LXEViXPAFo97VUx75RTdt_Gw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1eFaICgpPVQCZixt7hbUAgSa2PiXmAIKPv3RSx2IJTbBrd8ch1iwHoMhPu0pN1XVKmTb2epZZIZDZi7tbKRrR5XsV78U_Tf0n_DijPy6C1aafFGe4TwRMlIkhFU3CPPiXrz9Vd049xl8OU3SFRxw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)