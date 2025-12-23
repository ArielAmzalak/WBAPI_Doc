![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fmedia-card-carousel-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates)

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

[Media card carousel templates](#media-card-carousel-templates)

[Media cards](#media-cards)

[Creating media card carousel templates](#creating-media-card-carousel-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending Media Card Carousel Templates](#sending-media-card-carousel-templates)

[Request Syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Media card carousel templates

Media card carousel templates allow you to send a single **marketing template** message accompanied by a set of up to 10 product media cards in a horizontally scrollable view:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/461961248_1048610163180196_3907313698557856900_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=vdPyjxZ_Hf4Q7kNvwHlHzj1&_nc_oc=AdkEPZWsbsd-BVhZWBnrTj6cdqLtMmDZ4H6vyNaxjqSNALnqVJlDTH2djfJAMVlglQw&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=SFDWa-OK8QvzrwDt4gHaLw&oh=00_AfiUPJN4MSn2XB_Oa1J8sEdfTo4kyH-3eHzNLTeHLFhTAQ&oe=69407B3C)

When a user taps a media card's **URL** button to buy a product, the URL mapped to the button is loaded in the device's default web browser, thus taking the user out of the WhatsApp client experience. If you prefer to keep the user in the WhatsApp client, see [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates). Note that carousel cards are only available for marketing template messages.

## Media cards

Carousel templates consist of a message body text and up to 10 product media cards. Each card in the template has an image or video header asset and can optionally include a body text and up to two buttons. Button combinations can be a mix of [quick reply buttons](/docs/whatsapp/business-management-api/message-templates/components#quick-reply-buttons), [phone number buttons](/docs/whatsapp/business-management-api/message-templates/components#phone-number-buttons), and [URL buttons](/docs/whatsapp/business-management-api/message-templates/components#url-buttons).

All cards defined on a template must have the same components.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/461975373_1069581831199988_6558232856590657854_n.png?stp=dst-webp&_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=T_RvG66KcwkQ7kNvwFSpDFM&_nc_oc=AdnCb51tdYl2N3Gu0EAfDQ9yhk61GCmruZ0YZyv3bNnRqWc502vGtwehxUT0odbRUpE&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=SFDWa-OK8QvzrwDt4gHaLw&oh=00_AfjcM6QsrBg5kiUYsZqeXbVxpJgmp8YS-KHkpfR5NGXtnw&oe=69405C13)

WhatsApp users who place an order do so outside of the WhatsApp client, so no webhooks are triggered describing their order.

## Creating media card carousel templates

Use the [**POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates**](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create a media card carousel template.

### Request syntax

It is necessary to define the exact number of product cards (minimum 2 and maximum 10) upon template creation. An approved template can only be used to send the same number of cards as defined during its creation. If any card in the carousel includes a card body text, then all cards must include a card body text to ensure consistent card heights.

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "name": "<TEMPLATE_NAME>",
    "language": "<TEMPLATE_LANGUAGE>",
    "category": "marketing",
    "components": [
      {
        "type": "body",
        "text": "<MESSAGE_BODY_TEXT>",
        "example": {
          "body_text": [
            [
              "<MESSAGE_BODY_TEXT_VARIABLE_EXAMPLE_1>",
              "<MESSAGE_BODY_TEXT_VARIABLE_EXAMPLE_2>"
            ]
          ]
        }
      },
      {
        "type": "carousel",
        "cards": [
          {
            "components": [
              {
                "type": "header",
                "format": "<CARD_HEADER_FORMAT>",
                "example": {
                  "header_handle": [
                    "<CARD_HEADER_ASSET_HANDLE>"
                  ]
                }
              },
              {
                "type": "buttons",
                "buttons": [
                  {
                    "type": "quick_reply",
                    "text": "<QUICK_REPLY_BUTTON_LABEL_TEXT>"
                  },
                  {
                    "type": "url",
                    "text": "<URL_BUTTON_LABEL_TEXT>",
                    "url": "<URL_BUTTON_URL>",
                    "example": [
                      "<URL_BUTTON_URL_VARIABLE_EXAMPLE>"
                    ]
                  },
                  {
                    "type": "phone_number",
                    "text": "<PHONE_NUMBER_BUTTON_LABEL_TEXT>",
                    "phone_number": "<PHONE_NUMBER>"
                  }
                ]
              }
            ]
          }
          // Add additional cards here, following the same structure
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<CARD_HEADER_ASSET_HANDLE>`  *String* | **Required.**  Uploaded media asset handle. Use the [Resumable Upload API](/docs/graph-api/guides/upload) to generate an asset handle.  Media assets are automatically cropped to a wide ratio based on the WhatsApp user's device. | `4::anBlZw==:ARa525ZJ1g0J-8egeiRvb4Z4r9RSi9qeKF7-wXsUiaDFsll5CKbu5H7h_9mTW0TDfA8LEGHC4bAeXtJJiVQADMp5Ooe2huQlhpBxMadJiu3qVg:e:1724535430:634974688087057:100089620928913:ARaQoFQMm6BlbI3MYo4` |
| `<CARD_HEADER_FORMAT>`  *String* | **Required.**  Card header format. Value can be `image` or `video`. | `image` |
| `<MESSAGE_BODY_TEXT>`  *String* | **Required.**  Message body text. Supports variables.  Maximum 1024 characters. | `Rare succulents for sale! {{1}}, add these unique plants to your collection. Each of these rare succulents are {{2}} if you checkout using code {{3}}. Shop now and add some unique and beautiful plants to your collection!` |
| `<MESSAGE_BODY_TEXT_VARIABLE_EXAMPLE>`  *String* | **Required if message body text string uses variables.**  Message body text example variable string(s). Number of strings must match the number of variable placeholders in the message body text string.  If message body text uses a single variable, `body_text` value can be a string, otherwise it must be an array containing an array of strings. | `20OFF` |
| `<PHONE_NUMBER>`  *String* | **Required if using a phone number button.**  Alphanumeric string. Business phone number to be called when the WhatsApp user taps the button.  Maximum 20 characters. | `+15550051310` |
| `<PHONE_NUMBER_BUTTON_LABEL_TEXT>`  *String* | **Required if using a phone number button.**  Phone number button label text.  Maximum 25 characters. | `Call` |
| `<QUICK_REPLY_BUTTON_LABEL_TEXT>`  *String* | **Required if using a quick-reply button.**  Quick-reply button label text.  Maximum 25 characters. | `Send more like this!` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `carousel_template_media_cards_v1` |
| `<URL_BUTTON_LABEL_TEXT>`  *String* | **Required if using a URL button.**  URL button label text.  25 characters maximum. | `Shop` |
| `<URL_BUTTON_URL>`  *String* | **Required if using a URL button.**  URL to be loaded in the device's default web browser when the WhatsApp user taps the button.  Supports 1 variable. Variable placeholder must be appended to the end of the URL string.  Maximum 2000 characters. | `https://www.luckyshrub.com/rare-succulents/{{1}}` |
| `<URL_BUTTON_URL_VARIABLE_EXAMPLE>`  *String* | **Required if URL button URL uses a variable.**  URL button URL example variable string.  Maximum 2000 characters. | `BUDDHA` |

### Example request

This example request creates a media card carousel template with a message that uses 3 variables and 3 media cards. Each media card has a quick reply button, and a URL button that uses a variable.

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "carousel_template_media_cards_v1",
  "language": "en_US",
  "category": "marketing",
  "components": [
    {
      "type": "body",
      "text": "Rare succulents for sale! {{1}}, add these unique plants to your collection. Each of these rare succulents are {{2}} if you checkout using code {{3}}. Shop now and add some unique and beautiful plants to your collection!",
      "example": {
        "body_text": [
          [
            "Pablo",
            "30%",
            "30OFF"
          ]
        ]
      }
    },
    {
      "type": "carousel",
      "cards": [
        {
          "components": [
            {
              "type": "header",
              "format": "image",
              "example": {
                "header_handle": [
                  "4::an..."
                ]
              }
            },
            {
              "type": "buttons",
              "buttons": [
                {
                  "type": "quick_reply",
                  "text": "Send me more like this!"
                },
                {
                  "type": "url",
                  "text": "Shop",
                  "url": "https://www.luckyshrub.com/rare-succulents/{{1}}",
                  "example": [
                    "BLUE_ELF"
                  ]
                }
              ]
            }
          ]
        },
        {
          "components": [
            {
              "type": "header",
              "format": "image",
              "example": {
                "header_handle": [
                  "4::an..."
                ]
              }
            },
            {
              "type": "buttons",
              "buttons": [
                {
                  "type": "quick_reply",
                  "text": "Send me more like this!"
                },
                {
                  "type": "url",
                  "text": "Shop",
                  "url": "https://www.luckyshrub.com/rare-succulents{{1}}",
                  "example": [
                    "BUDDHA"
                  ]
                }
              ]
            }
          ]
        },
        {
          "components": [
            {
              "type": "header",
              "format": "image",
              "example": {
                "header_handle": [
                  "4::an..."
                ]
              }
            },
            {
              "type": "buttons",
              "buttons": [
                {
                  "type": "quick_reply",
                  "text": "Send me more like this!"
                },
                {
                  "type": "url",
                  "text": "Shop",
                  "url": "https://www.luckyshrub.com/rare-succulents{{1}}",
                  "example": [
                    "BLACK_PRINCE"
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}'
```

## Sending Media Card Carousel Templates

This document describes how to send approved [media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates) to WhatsApp users.

### Request Syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<WHATSAPP_USER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<TEMPLATE_LANGUAGE>"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            { "type": "text", "text": "<MESSAGE_BODY_TEXT_VARIABLE_1>" },
            { "type": "text", "text": "<MESSAGE_BODY_TEXT_VARIABLE_2>" }
          ]
        },
        {
          "type": "carousel",
          "cards": [
            {
              "card_index": 0,
              "components": [
                {
                  "type": "header",
                  "parameters": [
                    {
                      "type": "<MESSAGE_HEADER_FORMAT>",
                      "<MESSAGE_HEADER_FORMAT>": {
                        "id": "<MESSAGE_HEADER_ASSET_ID>"
                      }
                    }
                  ]
                },
                {
                  "type": "body",
                  "parameters": [
                    { "type": "text", "text": "<CARD_BODY_VARIABLE_1>" },
                    { "type": "text", "text": "<CARD_BODY_VARIABLE_2>" }
                  ]
                },
                {
                  "type": "button",
                  "sub_type": "quick_reply",
                  "index": 0,
                  "parameters": [
                    {
                      "type": "payload",
                      "payload": "<QUICK_REPLY_BUTTON_PAYLOAD>"
                    }
                  ]
                },
                {
                  "type": "button",
                  "sub_type": "url",
                  "index": 1,
                  "parameters": [
                    {
                      "type": "text",
                      "text": "<URL_BUTTON_URL_VARIABLE>"
                    }
                  ]
                }
              ]
            }
            // Add additional cards here, following the same structure
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BUTTON_INDEX>`  *Integer* | **Required.**  Zero-indexed order in which button appears at the bottom of the template message. `0` indicates the first button, `1` indicates second button, etc.  Note that if any buttons use variables, the type and order of buttons must match the type and order defined on the template, so you can't use the index values to arrange the order of the buttons in the sent template.  For example, if the template defines a phone number button first (which equates to index `0`) and a URL button that supports a single variable second (which equates to index `1`), if you attempt to send the template with the URL button index set to `0` , the API would return an error ("Parameter value for URL was expected but was not found") because it's expecting a button object with an index of `1` to be present in the post body payload. | `0` |
| `<CARD_BODY_VARIABLE>`  *Object* | **Required if the template card body text uses variables, otherwise omit.**  Object describing a card body variable. If the template uses multiple variables, you must define an object for each variable.  Supports `text`, `currency`, and `date_time` types. See [Messages Parameters](/docs/whatsapp/cloud-api/reference/messages#parameter-object).  There is no maximum character limit on this value, but does count against the card body text limit of 160 characters. | ``` {   "type":"text",   "text": "Pablo" } ``` |
| `<CARD_INDEX>`  *Integer* | **Required.**  Zero-indexed order in which card should appear within the card carousel. `0` indicates first card, `1` indicates second card, etc. | `0` |
| `<MESSAGE_BODY_TEXT_VARIABLE>`  *Object* | **Required if template message body text uses variables, otherwise omit.**  Object describing a message variable. If the template uses multiple variables, you must define an object for each variable.  Supports `text`, `currency`, and `date_time` types. See [Messages Parameters](/docs/whatsapp/cloud-api/reference/messages#parameter-object).  There is no maximum character limit on this value, but it does count against the message body text limit of 1024 characters. | ``` {   "type":"text",   "text": "Pablo" } ``` |
| `<MESSAGE_HEADER_ASSET_ID>`  *String* | **Required.**  Header asset's uploaded media asset ID. Use the [**POST /<BUSINESS\_PHONE\_NUMBER\_ID>/media**](/docs/whatsapp/cloud-api/reference/media#upload-media) endpoint to generate an asset ID. | `1558081531584829` |
| `<MESSAGE_HEADER_FORMAT>`  *String* | **Required.**  Indicates header type and a matching property name.  Note that the `<MESSAGE_HEADER_FORMAT>` placeholder appears twice in the post body example above, as it serves as a placeholder for the type property's value and its matching property name.  Value can be `image` or `video`. | `image` |
| `<QUICK_REPLY_BUTTON_PAYLOAD>`  *String* | **Optional.**  Value to be included in messages webhooks (`messages.button.payload`) when the button is tapped. | `more-aloes` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `carousel_template_media_cards_v1` |
| `<URL_BUTTON_URL_VARIABLE>`  *String* | **Required if the URL button URL uses a variable.**  URL button variable value. | `blue-elf` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example request

This example request sends a media card carousel template named "carousel\_template\_media\_cards\_v1". It supplies three body text variables (which the template requires) and contents for three cards (which the template also requires). For each card, the request supplies an image asset ID, a quick-reply button payload (to be included in webhooks when the button is tapped), and a text string to be injected into the URL mapped to the card's URL button (which is defined on the template).

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "template",
  "template": {
    "name": "carousel_template_media_cards_v1",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "Pablo"
          },
          {
            "type": "text",
            "text": "20%"
          },
          {
            "type": "text",
            "text": "20OFF"
          }
        ]
      },
      {
        "type": "carousel",
        "cards": [
          {
            "card_index": 0,
            "components": [
              {
                "type": "header",
                "parameters": [
                  {
                    "type": "image",
                    "image": {
                      "id": "1558081531584829"
                    }
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "quick_reply",
                "index": "0",
                "parameters": [
                  {
                    "type": "payload",
                    "payload": "more-aloes"
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "url",
                "index": "1",
                "parameters": [
                  {
                    "type": "text",
                    "text": "blue-elf"
                  }
                ]
              }
            ]
          },
          {
            "card_index": 1,
            "components": [
              {
                "type": "header",
                "parameters": [
                  {
                    "type": "image",
                    "image": {
                      "id": "861236878885705"
                    }
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "quick_reply",
                "index": "0",
                "parameters": [
                  {
                    "type": "payload",
                    "payload": "more-crassulas"
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "url",
                "index": "1",
                "parameters": [
                  {
                    "type": "text",
                    "text": "buddhas-temple"
                  }
                ]
              }
            ]
          },
          {
            "card_index": 2,
            "components": [
              {
                "type": "header",
                "parameters": [
                  {
                    "type": "image",
                    "image": {
                      "id": "1587064918516321"
                    }
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "quick_reply",
                "index": "0",
                "parameters": [
                  {
                    "type": "payload",
                    "payload": "more-echeverias"
                  }
                ]
              },
              {
                "type": "button",
                "sub_type": "url",
                "index": "1",
                "parameters": [
                  {
                    "type": "text",
                    "text": "black-prince"
                  }
                ]
              }
            ]
          }
        ]
      }
    ]
  }
}'
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Media card carousel templates](#media-card-carousel-templates)

[Media cards](#media-cards)

[Creating media card carousel templates](#creating-media-card-carousel-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending Media Card Carousel Templates](#sending-media-card-carousel-templates)

[Request Syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jqbjgBhh4ZzY47VbEvLHZg&oh=00_Afi2NWxB0m6U0jDwvjV7IW2x3vWdKmKYyG29hZoMkaJMXQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jqbjgBhh4ZzY47VbEvLHZg&oh=00_Afhwe48JNtZGhzWRsNAtsAuDNuxfwosYjn6Kcp_vEoQFHA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jqbjgBhh4ZzY47VbEvLHZg&oh=00_AfjtP3no9dBgklwtOzjwOP_Ib3Q-oTYGsCz35L1ujKFfEQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jqbjgBhh4ZzY47VbEvLHZg&oh=00_AfiJWiHj3fWUkQBu-IoYdvDfoD5f5k1Hb41Bvpf9Vws5DA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=jqbjgBhh4ZzY47VbEvLHZg&oh=00_AfjsBCnNGU7DbhS4nmtBvBCgGRsdKQ4jsGqbzLuSgXBjIg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06EyhKh4SYMIRivB0gWWVRk1gfb8tsq3Fff-y6c9gOq5SDkjLcZ9tdcE_lTf7w8isWSQvL_V_7BdFHXNBc61UorMYFC3pqfNL60GxEALG22DskBkQ1tpode3uPEY3BJput8oTehLZantIpKbe5Tg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)