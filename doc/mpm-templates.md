![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fmpm-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates)

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

[Multi-product message templates](#multi-product-message-templates)

[Requirements](#requirements)

[Limitations](#limitations)

[Creating MPM templates](#creating-mpm-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Components](#components)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Sample response](#sample-response)

[Webhooks](#webhooks)

[Webhook syntax](#webhook-syntax)

[Webhook contents](#webhook-contents)

[Sample webhook](#sample-webhook)

[Sending MPM template messages](#sending-mpm-template-messages)

[Components](#components-2)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Multi-product message templates

This document describes multi-product message ("MPM") templates, their uses, and how to use them.

MPM templates are marketing templates that allow you to showcase up to 30 products from your ecommerce catalog, organized in up to 10 sections, in a single message.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/345336924_1476472873159435_9050004394387774321_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=Bo6oPwvRcMkQ7kNvwGSZi2i&_nc_oc=Adn4Z4JHKUJ94BwBXvcfl0-pXHq669Xpdpa-D6l45awTbFH7Gt2106-B9k_RhS4Bt6s&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Du98TOiA02J0SSdh7ecUYQ&oh=00_Afh53I9veKmJAvcypGI2XLZ9OAwOoblevi0wkDlhRKiEfw&oe=69407DDC)

Customers can browse products and sections within the message, view details for each product, add and remove products from their cart, and submit their cart to place an order. Orders are then sent to you via a webhook.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/345301814_777009393786308_8675106872073624223_n.png?stp=dst-webp&_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=NeABZRiWVpAQ7kNvwEfeed5&_nc_oc=AdnG4ZyOtoxxh8E5LWsW-QOHeV_XGE4QJuxphgWK0kDs1X75UuZEKpeGzW2uysvobow&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Du98TOiA02J0SSdh7ecUYQ&oh=00_AfgIBhP3uJKZFQz1AfOjU0WBCgje_feYdiewGbYymcau8g&oe=694064A9)

See our help center article [About Multi-product message templates on WhatsApp](https://www.facebook.com/business/help/978451836847222) for common use cases and tips on how to make the most of MPM templates.

## Requirements

In order to create and use MPM templates you must have an ecommerce product catalog, with inventory, connected to your WhatsApp Business Account. See the Cloud API [Commerce](/docs/whatsapp/cloud-api/guides/sell-products-and-services) guide.

## Limitations

* Customers must be using WhatsApp v2.22.24 or greater.
* MPM templates cannot be forwarded to other customers.

## Creating MPM templates

You can create MPM templates using the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates/) endpoint or the [**WhatsApp Manager**](https://business.facebook.com/wa/manage/home/) > **Account tools** > **Message templates** panel. Once your template is approved, you can use Cloud API or On-Premises API to send it in a template message.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "<NAME>",
    "category": "<CATEGORY>",
    "language": "<LANGUAGE>",
    "components": [<COMPONENTS>]
  }'
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<CATEGORY>` | **Required.**   Template category. Set this to `MARKETING`. | `MARKETING` |
| `<COMPONENTS>` | **Required.**   Array of objects that describe the components that make up the template. See [Components](#components) below. | See [Components](#components) below. |
| `<LANGUAGE>` | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<NAME>` | **Required.**   Template name.   Maximum 512 characters. | `abandoned_cart` |

### Components

The `components` value must be an array of objects that describes each component that makes up the template. MPM templates must have the following components:

* a single header component
* a single body component
* a single footer component (optional)
* a single MPM button component

```
[
  {
    "type": "HEADER",
    "format": "TEXT",
    "text": "<HEADER_TEXT>",

    /* Example required if header uses a variable */
    "example": {
      "header_text": [
        "<HEADER_EXAMPLE_TEXT>"
      ]
    }
  },
  {
    "type": "BODY",
    "text": "<BODY_TEXT>",

    /* Example required if body uses variables */
​​    "example": {
      "body_text": [
        [
          "<BODY_EXAMPLE_TEXT>"
        ]
      ]
    }
  },
  {
    "type": "FOOTER",
    "text": "<FOOTER_TEXT>"
  },
  {
    "type":"BUTTONS",
    "buttons": [
      {
        "type": "MPM",
        "text": "View items"
      }
    ]
  }
]
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<BODY_EXAMPLE_TEXT>` | String or array of strings. Example body variable value(s). | `10OFF` |
| `<BODY_TEXT>` | Template body text. Supports multiple variables.   If the string contains variables, you must include the example property and sample variable values.   1024 characters maximum. | `Forget something, {{1}}?` |
| `<FOOTER_TEXT>` | Template footer text.   60 characters maximum. | `Lucky Shrub, 1 Hacker Way, Menlo Park, CA 94025` |
| `<HEADER_EXAMPLE_TEXT>` | Example header variable value. | `Pablo` |
| `<HEADER_TEXT>` | Template header text. Supports 1 variable.   If the string contains a variable, you must include the example property and a sample variable value.   60 characters maximum. | `Looks like you left these items in your cart, still interested? Use code {{1}} to get 10% off!` |

### Response

Upon success, the API will respond with:

```
{
  "id": "<ID>",
  "status": "<STATUS>",
  "category": "MARKETING"
}
```

### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<ID>` | Template ID. | `546151681022936` |
| `<STATUS>` | Template status. Only templates with an `APPROVED` status can be sent in a template message. | `PENDING` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "abandoned_cart",
  "language": "en_US",
  "category": "MARKETING",
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT",
      "text": "Forget something, {{1}}?",
      "example": {
        "header_text": [
          "Pablo"
        ]
      }
    },
    {
      "type": "BODY",
      "text": "Looks like you left these items in your cart, still interested? Use code {{1}} to get 10% off!",
      "example": {
        "body_text": [
          [
            "10OFF"
          ]
        ]
      }
    },
    {
      "type":"BUTTONS",
      "buttons": [
        {
          "type": "MPM",
          "text": "View items"
        }
      ]
    }
  ]
}'
```

### Sample response

```
{
  "id": "546151681022936",
  "status": "PENDING",
  "category": "MARKETING"
}
```

## Webhooks

When a customer adds one or more products to their cart and submits an order, we will send you a webhook that describes the order.

### Webhook syntax

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<ENTRY.ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<NAME>"
                },
                "wa_id": "<WA_ID>"
              }
            ],
            "messages": [
              {
                "from": "<FROM>",
                "id": "<MESSAGES.ID>",
                "timestamp": "<TIMESTAMP>",
                "type": "order",
                "order": {
                  "catalog_id": "<CATALOG_ID>",
                  "product_items": [
                    {
                      "product_retailer_id": "<PRODUCT_RETAILER_ID>",
                      "quantity": <QUANTITY>,
                      "item_price": <ITEM_PRICE>,
                      "currency": "<CURRENCY>"
                    }
                  ]
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

### Webhook contents

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<CATALOG_ID>` | Ecommerce product catalog ID. | `1537566713439863` |
| `<CURRENCY>` | Item currency. | `USD` |
| `<DISPLAY_PHONE_NUMBER>` | Business phone number display number. | `15550051310` |
| `<ENTRY.ID>` | WhatsApp Business Account ID. | `102290129340398` |
| `<ITEM_PRICE>` | Item price. | `99.99` |
| `<MESSAGES.ID>` | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJDOEI3ODgxNzQzMjJBQTdEQTcA` |
| `<NAME>` | Customer's name. | `Pablo Morales` |
| `<PHONE_NUMBER_ID>` | Business phone number ID. | `106540352242922` |
| `<PRODUCT_RETAILER_ID>` | The item SKU number. Labeled as **Content ID** in the Commerce Manager. | `2lc20305pt` |
| `<QUANTITY>` | Number of items ordered (for this particular item). | `1` |
| `<TIMESTAMP>` | UNIX timestamp indicating when we sent you the webhook. | `1677522117` |
| `<WA_ID>` | Customer's WhatsApp phone number. | `16505551234` |

### Sample webhook

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
              "display_phone_number": "15550051310",
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
                "from": "16505551234",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTMxNzA1QzNENEI4ODY0OTY2MAA=",
                "timestamp": "1683223069",
                "type": "order",
                "order": {
                  "catalog_id": "1537566713439863",
                  "product_items": [
                    {
                      "product_retailer_id": "n6k6x0y7oe",
                      "quantity": 1,
                      "item_price": 99.99,
                      "currency": "USD"
                    }
                  ]
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

## Sending MPM template messages

This document explains how to send [multi-product message (MPM) templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates) in template messages.

### Components

MPM template messages must have:

* a **header** component (only required if template uses a header variable)
* a **body** component (only required if template uses a body variable)
* a single **MPM button** component

Use the MPM button component to define sections and their titles that will appear when the customer taps the **View items** button, and to designate which products appear in each of those sections.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/345454978_257502929976881_8980265032321705247_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=ZESGrGTGOmwQ7kNvwG9aguz&_nc_oc=AdmFh0ZI8aqkBNMd1EsvXUMCjzqMfvDJlDG0sTYq2T8_Wg27gd9VjHffIflNk1HRhjU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Du98TOiA02J0SSdh7ecUYQ&oh=00_Afg_AS4aWP9bKOtlRNw3Sa7A00JvC0AiZkslgvum3pq0lg&oe=6940518B)

To send an approved MPM template in a template message, send a POST request to the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint. Use the POST body to define the contents of the message and to describe any variables to inject into the template itself.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<TO>",
    "type": "template",
    "template": {
      "name": "<NAME>",
      "language": {
        "code": "<CODE>"
      },
      "components": [
        {
          "type": "header",
          "parameters": [
            {
              "type": "text",
              "text": "<HEADER_TEXT>"
            }
          ]
        },
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "<BODY_TEXT>"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "mpm",
          "index": 0,
          "parameters": [
            {
              "type": "action",
              "action": {
                "thumbnail_product_retailer_id": "<THUMBNAIL_PRODUCT_RETAILER_ID>",
                "sections": [
                  {
                    "title": "<TITLE>",
                    "product_items": [
                      {
                        "product_retailer_id": "<PRODUCT_RETAILER_ID_1>"
                      },
                      {
                        "product_retailer_id": "<PRODUCT_RETAILER_ID_2>"
                      }
                      // ... Add up to 30 product items per section
                    ]
                  }
                  // ... Add up to 10 section objects as needed
                ]
              }
            }
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<BODY_TEXT>` | **Required if template uses variables.**   String or array of strings. Text to replace body variable(s) defined in the template. | `10OFF` |
| `<CODE>` | Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<HEADER_TEXT>` | **Required if template uses a variable.**   Text to replace header variable defined in the template. | `Pablo` |
| `<NAME>` | Template name. | `abandoned_cart` |
| `<PRODUCT_RETAILER_ID>` | SKU number of the item you want to appear in the section.   SKU numbers are labeled as **Content ID** in the Commerce Manager.   Supports up to 30 products total, across all sections. | `2lc20305pt` |
| `<THUMBNAIL_PRODUCT_RETAILER_ID>` | Item SKU number. Labeled as **Content ID** in the Commerce Manager.   The thumbnail of this item will be used as the template message's header image. | `2lc20305pt` |
| `<TITLE>` | Section title text.   You can define up to 10 sections.   Maximum 24 characters. Markdown is not supported. | `Popular Bundles` |
| `<TO>` | Customer phone number. | `16505551234` |

### Response

Upon success, the API will respond with:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<INPUT>",
      "wa_id": "<WA_ID>"
    }
  ],
  "messages": [
    {
      "id": "<ID>"
    }
  ]
}
```

### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<ID>` | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJDOEI3ODgxNzQzMjJBQTdEQTcA` |
| `<INPUT>` | Customer WhatsApp phone number. | `16505551234` |
| `<WA_ID>` | Customer WhatsApp ID. | `16505551234` |

### Example request

This example sends an approved template named "abandoned\_cart" and injects a variable (the customer's first name) into the template header and a discount code into the template body. It also defines two sections ("Popular Bundles" and "Premium Packages") and identifies the products (a total of 3) that should be injected into those sections.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "abandoned_cart",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "text",
            "text": "Pablo"
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "10OFF"
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "mpm",
        "index": 0,
        "parameters": [
          {
            "type": "action",
            "action": {
              "thumbnail_product_retailer_id": "2lc20305pt",
              "sections": [
                {
                  "title": "Popular Bundles",
                  "product_items": [
                    {
                      "product_retailer_id": "2lc20305pt"
                    },
                    {
                      "product_retailer_id": "nseiw1x3ch"
                    }
                  ]
                },
                {
                  "title": "Premium Packages",
                  "product_items": [
                    {
                      "product_retailer_id": "n6k6x0y7oe"
                    }
                  ]
                }
              ]
            }
          }
        ]
      }
    ]
  }
}'
```

### Example response

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
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBJDOEI3ODgxNzQzMjJBQTdEQTcA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Multi-product message templates](#multi-product-message-templates)

[Requirements](#requirements)

[Limitations](#limitations)

[Creating MPM templates](#creating-mpm-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Components](#components)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request)

[Sample response](#sample-response)

[Webhooks](#webhooks)

[Webhook syntax](#webhook-syntax)

[Webhook contents](#webhook-contents)

[Sample webhook](#sample-webhook)

[Sending MPM template messages](#sending-mpm-template-messages)

[Components](#components-2)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response-2)

[Response parameters](#response-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vhEay_vqUB0q5cfI2zYcCA&oh=00_AfiyW4qk09pzCmXXauIS_B_l7Ky53J65zBIckOta_ekzTQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vhEay_vqUB0q5cfI2zYcCA&oh=00_AfhesEpW_hLv2jH5HkjVN0ptJ9gd3iqwiFMigYwDJx1xGw&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vhEay_vqUB0q5cfI2zYcCA&oh=00_AfiH7WDOwKglaL9H_Vrjg7S0vjboADZ5IOz6u2pnHWk0Dw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vhEay_vqUB0q5cfI2zYcCA&oh=00_AfgaQjDZpit8RsrYC_9nI0svtEZly_9QTv-Uggym1rw8qA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vhEay_vqUB0q5cfI2zYcCA&oh=00_AfhYguE8DY3KCru_oNNFY8cG7gVAVuUn1kbzuSNFNWt_MQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3aJHuhuA0ku2PxbPVm_LF5F8Ljqy_zKdDZ_aucruGBxXK09BVF8iCbZIF_D2Cu9b__CKlGssjouw2VMyer9wv-HHO1cXLxCy3rxe3w3smX7Yw1aA3E9YJN0voeruJ4gWuZfRU4tdUMTm9T2iQQKQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)