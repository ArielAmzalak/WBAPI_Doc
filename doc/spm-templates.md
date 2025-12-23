+++
id = "spm-templates"
title = "Single-product message templates"
summary = "This document describes single-product message (SPM) templates, their uses, and how to use them."
source = "https://developers.facebook.com/docs/whatsapp/spm-templates"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "messaging", "templates", "rate-limits"]
+++
# Single-product message templates

This document describes single-product message (SPM) templates, their uses, and how to use them.

SPM templates are marketing templates that allow you to present a single product from your ecommerce catalog, accompanied by a product image, product title, and product price (all pulled from your product within your catalog), along with customizable body text, optional footer text, and an interactive **View** button.

WhatsApp users can tap the button to see details about the product, and can add or remove the product from the WhatsApp shopping cart:

If the WhatsApp user adds the product to the carts and submits an order, you will be notified via webhook and the user will see that an order has been placed:

Users who place an order are also able to use the View details button to see information about the order:

## Limitations

* Customers must be using WhatsApp v2.22.24 or greater.
* Message forwarding is disabled for SPM templates.

## Catalogs

You must have an ecommerce product catalog, with inventory, connected to your WhatsApp Business Account. See the Cloud API [Commerce](/docs/whatsapp/cloud-api/guides/sell-products-and-services) guide to learn more about connecting a catalog to your account.

## Webhooks

When a customer adds one or more products to their cart and submits an order, an [order messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/order) webhook is triggered, describing the order.

## Creating SPM templates

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create an SPM template.

### Request syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE>",
  "category": "marketing",
  "parameter_format": "<PARAMETER_FORMAT>",
  "components": [
    {
      "type": "header",
      "format": "product"
    },
    {
      "type": "body",
      "text": "<CARD_BODY_TEXT>",

      <!-- Example parameter values required, if body text contains parameters -->
      "example": {
        "body_text_named_params": [
          {
            "param_name": "<PARAMETER_NAME>",
            "example": "<PARAMETER_EXAMPLE>"
          },
          <!-- Additional parameters would follow -->
        ]
      }

    },
    {
      "type": "footer",
      "text": "<CARD_FOOTER_TEXT>"
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
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token. | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<CARD_BODY_TEXT>`  *String* | **Required.**  Card body text. Supports variables.  Maximum 160 characters. | `Use code {{1}} to get {{2}} off our newest succulent!` |
| `<CARD_FOOTER_TEXT>`  *String* | **Optional.**  Footer text.  Maximum 60 characters. | `September 30, 2024` |
| `<PARAMETER_NAME>`  *String* | **Required if body text uses parameters.**  Example parameter value string(s). You must include a parameter example for each parameter in your body text. | `25OFF` |
| `<PARAMETER_FORMAT>`  *String* | **Optional.**  [Parameter format](/docs/whatsapp/business-management-api/message-templates#parameter-formats). Value can be:   * `named` * `positional`   If the `parameter_format` property is omitted, the template will use positional formatting. | `Lucky Shrub: Your gateway to succulents!` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `abandoned_cart_offer` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `546151681022936` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/161311403722088/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "spm_template_named_params",
  "language": "en_US",
  "category": "marketing",
  "parameter_format": "named",
  "components": [
    {
      "type": "header",
      "format": "product"
    },
    {
      "type": "body",
      "text": "Use code {{code}} to get {{percent}} off our newest succulent!",
      "example": {
        "body_text_named_params": [
          {
            "param_name": "code",
            "example": "15OFF"
          },
          {
            "param_name": "percent",
            "example": "15%"
          }
        ]
      }
    },
    {
      "type": "footer",
      "text": "Offer ends September 22, 2024"
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
}'
```

## Sending single-product template messages

### Request syntax

Use the [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an SPM template message.

```
curl 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
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
        "type": "header",
        "parameters": [
          {
            "type": "product",
            "product": {
              "product_retailer_id": "<PRODUCT_ID>",
              "catalog_id": "<CATALOG_ID>"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "<PARAMETER_NAME>",
            "text": "<PARAMETER_VALUE>"
          },
          <!-- Additional parameter values would follow, if required by template -->
        ]
      }
    ]
  }
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  Access token | `EAAAN...` |
| `<API_VERSION>`  *String* | **Optional.**  API version. If omitted, defaults to the newest API version available to your app. | `v23.0` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<CATALOG_ID>`  *String* | **Required.**  ID of [connected ecommerce catalog](https://www.facebook.com/business/help/158662536425974) containing the product. | `194836987003835` |
| `<PARAMETER_NAME>`  *String* | **Required if template uses one or more named parameters.**  Name of [named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters). | `code` |
| `<PARAMETER_VALUE>`  *String* | **Required if template uses one or more named parameters.**  [Named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters) value. | `10OFF` |
| `<PRODUCT_ID>`  *String* | **Required.**  Product ID. | `nqryix03ez` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `spm_template_named_params` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example request

This example sends an approved template named "spm\_template\_named\_params" which injects parameters (a discount code and the percentage discounted) into the template body, and which includes a footer. The product image is pulled from the catalog and displayed in the message header.

```
curl 'https://graph.facebook.com/v24.0/179776755229976/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505551234",
  "type": "template",
  "template": {
    "name": "spm_template_named_params",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "product",
            "product": {
              "product_retailer_id": "nqryix03ez",
              "catalog_id": "194836987003835"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "parameter_name": "code",
            "text": "25OFF"
          },
          {
            "type": "text",
            "parameter_name": "percent",
            "text": "25%"
          }
        ]
      }
    ]
  }
}'
```
