+++
id = "product-card-carousel-templates"
title = "Product card carousel templates"
summary = "Product card carousel templates allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view:"
source = "https://developers.facebook.com/docs/whatsapp/product-card-carousel-templates"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "templates"]
+++
# Product card carousel templates

Product card carousel templates allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view:

When a WhatsApp user taps the **View** button, they can view more information about the product, add the product to a shopping cart, and place an order, all without leaving the WhatsApp client experience. If instead you prefer to send the user to your website when they click the button, see [Media Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates).

## Product cards

Carousel templates support up to 10 product cards, composed of message body text, a product image, product title, product price, and a single View button or URL button. All cards defined on a template must have the same components.

## View buttons

When a WhatsApp user taps the button, the product details view appears, displaying product information pulled from your product catalog.

Users can then add the product to a cart and place an order.

When a user submits the cart, a [webhook](#webhooks) will be triggered describing the order, and an order confirmation message will appear in the message thread.

Users who have placed an order can see the contents of the order by tapping the **View details** button.

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
| `<MESSAGE_BODY_TEXT_VARIABLE>`  *Object* | **Required if template message body text uses variables, otherwise omit.**  Object describing a message variable. If the template uses multiple variables, you must define an object for each variable.  Supports `text`, `currency`, and `date_time` types. See [Messages Parameters](/docs/whatsapp/cloud-api/reference/messages#parameter-object).  There is no maximum character limit on this value, but it does count against the message body text limit of 1024 characters. | ``` {
   "type":"text",
   "text": "Pablo"
 } ``` |
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
