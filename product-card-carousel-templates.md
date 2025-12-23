![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fproduct-card-carousel-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates)

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

[Product card carousel templates](#product-card-carousel-templates)

[Product cards](#product-cards)

[View buttons](#view-buttons)

[URL buttons](#url-buttons)

[Catalogs](#catalogs)

[Webhooks](#webhooks)

[Creating product card carousel templates](#creating-product-card-carousel-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending product card carousel templates](#sending-product-card-carousel-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Product card carousel templates

Product card carousel templates allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456451243_832660229062364_6760679807399209749_n.png?stp=dst-webp&_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=GkdwnchPbQAQ7kNvwHpoZVb&_nc_oc=Adl5ySnqRavQIOb_hSHSvujOf0DXYWqQw2t4cc49dPsR6xYcdIsfvCW4wR_JMxSE5Uo&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_AfivZx-iVF-in30PSvuh1P9QDZ5d8huQ4aRiXXuLRcZMkA&oe=69406223)

When a WhatsApp user taps the **View** button, they can view more information about the product, add the product to a shopping cart, and place an order, all without leaving the WhatsApp client experience. If instead you prefer to send the user to your website when they click the button, see [Media Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates).

## Product cards

Carousel templates support up to 10 product cards, composed of message body text, a product image, product title, product price, and a single View button or URL button. All cards defined on a template must have the same components.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456183425_819329683713319_8287896812760303277_n.png?stp=dst-webp&_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=9mpi9qaN-G8Q7kNvwHS8UEU&_nc_oc=Admm_f5aEK0CgftIgEiODhAJYjhH7kT4i1KcAIdPqSIhUhOVuuxAdh9EWOMNQErNteE&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_AfhwUDdyZdQGQjUyL_2b5VzOARAkFfBjzw3deTp0oHK0kA&oe=69406C7A)

## View buttons

When a WhatsApp user taps the button, the product details view appears, displaying product information pulled from your product catalog.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456536571_1403706086934453_4366317090049712342_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=1Xr1oKa7pFQQ7kNvwH2a27n&_nc_oc=Adn8Ax2Wk2cPJIvegMOhAjbHEf_4jNpUjjzjOzABbu3aNxx0Yj_45FQQruZkPSranBY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_Afiva7bqnaKmBcQwjSycMjJjTqOTtenhI3FgIiUBI60ggw&oe=694072FA)

Users can then add the product to a cart and place an order.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456294794_1915042982315160_3191620650033958999_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=KsLDDIV2glcQ7kNvwEWgKT0&_nc_oc=AdlpIpZK1kIu_Kvayv3r98vuiDSu-9ybNQ8JW1hOXKIr0dksrNf6oCtkxbZo4cqkYkA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_Afjk-i09v6nr2d_n68p7dXHzSeXoC7msGoJscAcpPM6c6Q&oe=69406B2E)

When a user submits the cart, a [webhook](#webhooks) will be triggered describing the order, and an order confirmation message will appear in the message thread.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456482022_473045605708419_6165153125141611284_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=L2ROOh74ymQQ7kNvwH_owLD&_nc_oc=AdkpZ3ShpM-ODMoTRCiq5eQ9xqLwh8RxIpjt7G1FwgOid3dmOLewX1TzErfNmWOtVbE&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_Afg1vkiKP5jpYXdq467UKHaXpXbYAXiTAAwHZvsuSm0kEA&oe=694048E1)

Users who have placed an order can see the contents of the order by tapping the **View details** button.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456576172_505851605146576_6951890413402171834_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=85_r6YDzktAQ7kNvwEIRODz&_nc_oc=AdmGBKJA3-9sOTrkMXv_lSoM3lfuddN5s05_y6AZRBFgaZ927HEsjIhF1mcWg8ajvHE&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=dK-i5L5Rb61LDb2XaTwd9Q&oh=00_Afi5GMSTfkzs8-iCHnzQv7INUcd30LImbUb04QLDNYh65A&oe=69405601)

## URL buttons

Instead of **View** buttons you may wish to use **URL** buttons. When a WhatsApp user taps a URL button to buy a product, the URL mapped to the button is loaded in the device's default web browser, which takes the user out of the WhatsApp client experience. This can be useful if, for example, you wish to load the product in your mobile checkout page where users can add promo codes and find related products.

WIth URL button flows, since order placement happens outside of the WhatsApp client, webhooks describing the order are not triggered.

## Catalogs

To use product card carousel templates, you must have an ecommerce product catalog, with inventory, connected to your WhatsApp Business Account. See the Cloud API [Commerce](/docs/whatsapp/cloud-api/guides/sell-products-and-services) guide to learn more about connecting a catalog to your account.

## Webhooks

If you send a carousel template composed of product cards that use a **View** button, when a customer adds one or more products to their cart and submits an order, an [order messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/order) webhook is triggered, describing the order.

## Creating product card carousel templates

Use the [**POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates**](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create a product card carousel template.

### Request syntax

It is only necessary to define two product cards upon template creation. An approved template with two product cards can be used to send up to 10 cards in a template message.

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
                "format": "product"
              },
              {
                "type": "buttons",
                "buttons": [
                  {
                    "type": "spm",
                    "text": "View"
                  }
                  // OR, for a URL button, use the following instead:
                  // {
                  //   "type": "url",
                  //   "text": "<URL_BUTTON_LABEL_TEXT>",
                  //   "url": "<URL_BUTTON_URL>",
                  //   "example": [
                  //     "<URL_BUTTON_URL_VARIABLE_EXAMPLE>"
                  //   ]
                  // }
                ]
              }
            ]
          }
          // Add a second product card here, following the same structure as above
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<MESSAGE_BODY_TEXT>`  *String* | **Required.**  Message body text. Supports variables.  Maximum 1024 characters. | `Rare succulents for sale! {{1}}, add these unique plants to your collection.` |
| `<MESSAGE_BODY_TEXT_VARIABLE_EXAMPLE>`  *String* | **Required if message body text string uses variables.**  Message body text example variable string(s). Number of strings must match the number of variable placeholders in the message body text string.  If message body text uses a single variable, `body_text` value can be a string, otherwise it must be an array containing an array of strings. | `Pablo` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `carousel_template_product_cards_v1` |
| `<URL_BUTTON_LABEL_TEXT>`  *String* | **Required if using a URL button.**  URL button label text.  25 characters maximum. | `Buy now` |
| `<URL_BUTTON_URL>`  *String* | **Required if using a URL button.**  URL to be loaded in the device's default web browser when the WhatsApp user taps the button.  Supports 1 variable. Variable placeholder must be appended to the end of the URL string.  Maximum 2000 characters. | `https://www.luckyshrub.com/rare-succulents/{{1}}` |
| `<URL_BUTTON_URL_VARIABLE_EXAMPLE>`  *String* | **Required if URL button URL uses a variable.**  URL button URL example variable string.  Maximum 2000 characters. | `BUDDHA` |

### Example request

This example request creates a product card carousel template with a message body that uses a single variable and two product cards. Once approved, it can be used to send up to 10 product cards in a template message.

```
curl 'https://graph.facebook.com/v24.0/161311403722088/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "carousel_template_product_cards_v1",
  "language": "en_US",
  "category": "marketing",
  "components": [
    {
      "type": "body",
      "text": "Rare succulents for sale! {{1}}, add these unique plants to your collection. All three of these rare succulents are available for purchase on our website, and they come with a 100% satisfaction guarantee. Whether you're a seasoned succulent enthusiast or just starting your plant collection, these rare succulents are sure to impress. Shop now and add some unique and beautiful plants to your collection!",
      "example": {
        "body_text": "Pablo"
      }
    },
    {
      "type": "carousel",
      "cards": [
        {
          "components": [
            {
              "type": "header",
              "format": "product"
            },
            {
              "type": "buttons",
              "buttons": [
                {
                  "type": "spm",
                  "text": "View"
                }
              ]
            }
          ]
        },
        {
          "components": [
            {
              "type": "header",
              "format": "product"
            },
            {
              "type": "buttons",
              "buttons": [
                {
                  "type": "spm",
                  "text": "View"
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

## Sending product card carousel templates

### Request syntax

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send an approved product card carousel template to a WhatsApp user.

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
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
                      "type": "product",
                      "product": {
                        "product_retailer_id": "<PRODUCT_ID_1>",
                        "catalog_id": "<CATALOG_ID>"
                      }
                    }
                  ]
                }
                // Add additional components (e.g., buttons) here if your template defines them
              ]
            }
            // Add additional cards here, incrementing card_index for each
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<CARD_INDEX>`  *Integer* | **Required.**  Zero-indexed order in which card should appear within the card carousel. `0` indicates first card, `1` indicates second card, etc. | `0` |
| `<CATALOG_ID>`  *String* | **Required.**  ID of [connected ecommerce catalog](https://www.facebook.com/business/help/158662536425974) containing the product. | `194836987003835` |
| `<MESSAGE_BODY_TEXT_VARIABLE>`  *Object* | **Required if template message body text uses variables, otherwise omit.**  Object describing a message variable. If the template uses multiple variables, you must define an object for each variable.  Supports `text`, `currency`, and `date_time` types. See [Messages Parameters](/docs/whatsapp/cloud-api/reference/messages#parameter-object).  There is no maximum character limit on this value, but it does count against the message body text limit of 1024 characters. | ``` {   "type":"text",   "text": "Pablo" } ``` |
| `<PRODUCT_ID>`  *String* | **Required.**  Product ID. | `vrpj01fvwp` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `carousel_template_media_cards_v1` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example request

This example request sends an approved template named "carousel\_template\_product\_cards\_v1". It supplies a single body text variable value (which the template requires) and three product cards. Each card identifies where it should appear in the carousel (card\_index), as well as the product ID and catalog ID where the card's product details (title, description, price, etc.) can be found.

```
curl 'https://graph.facebook.com/v24.0/179776755229976/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "template",
  "template": {
    "name": "carousel_template_product_cards_v1",
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
                    "type": "product",
                    "product": {
                      "product_retailer_id": "vrpj01fvwp",
                      "catalog_id": "194836987003835"
                    }
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
                    "type": "product",
                    "product": {
                      "product_retailer_id": "va2l5ioeat",
                      "catalog_id": "194836987003835"
                    }
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
                    "type": "product",
                    "product": {
                      "product_retailer_id": "sqpjv0mgde",
                      "catalog_id": "194836987003835"
                    }
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

[Product card carousel templates](#product-card-carousel-templates)

[Product cards](#product-cards)

[View buttons](#view-buttons)

[URL buttons](#url-buttons)

[Catalogs](#catalogs)

[Webhooks](#webhooks)

[Creating product card carousel templates](#creating-product-card-carousel-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Sending product card carousel templates](#sending-product-card-carousel-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pUeBvdOoZh581DYTe4sWYQ&oh=00_AfhJqWksn1Uspfw-vmgf1qP6UsZmfOAHuCCZUriwqAGKoQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pUeBvdOoZh581DYTe4sWYQ&oh=00_Afja7x2DvJDbWW4wYdZd_eqtAwaNa-_snNqGpmXayKK6SA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pUeBvdOoZh581DYTe4sWYQ&oh=00_AfiI590-MrDEskeSAuxEa6QAiLs58elqjCB-0RUi2y8v-w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pUeBvdOoZh581DYTe4sWYQ&oh=00_AfglTSbMyzWLp9RYi9qlwvazIJ1EKyUANyF_81rEcGaO5Q&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pUeBvdOoZh581DYTe4sWYQ&oh=00_Afj32av9txYycCMzWfO0UVB4DEgELtDsFxXFsWLIQD3TBw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT230amWEvSIxF8JxAQsb9WZ3waQDNRhNCGddFpZ0aCLUglYzplkEZS1HESq9L0La5tCtoHvADdPYjg2ITu1XygoBxohlJreljJjnrCO8iWSmDBIEW9r2JI4zEx9IyHiipJH8xb0rKkkp_pkETd2jA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)