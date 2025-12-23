![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsell-products-and-services%2Fshare-products%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)[Compartilhar produtos](/docs/whatsapp/cloud-api/guides/sell-products-and-services/share-products)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)

  + [Upload Inventory](/docs/whatsapp/cloud-api/guides/sell-products-and-services/upload-inventory)
  + [Definir configurações comerciais](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings)
  + [Compartilhar produtos](/docs/whatsapp/cloud-api/guides/sell-products-and-services/share-products)
  + [Receiving Responses](/docs/whatsapp/cloud-api/guides/sell-products-and-services/receive-responses)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Share products with WhatsApp users](#share-products-with-whatsapp-users)

[Catalog messages](#catalog-messages)

[Requirements](#requirements)

[Request syntax](#request-syntax)

[Post body](#post-body)

[Properties](#properties)

[Example request](#example-request)

[Example response](#example-response)

[Catalog template messages](#catalog-template-messages)

[Catalog Link messages](#catalog-link-messages)

[Checkout button templates](#checkout-button-templates)

[Media card carousel templates](#media-card-carousel-templates)

[Multi-product message templates](#multi-product-message-templates)

[Product card carousel templates](#product-card-carousel-templates)

[Product messages](#product-messages)

[Overview](#overview)

[Expected Behavior for Messages](#expected-behavior-for-messages)

[Limitations](#limitations)

[Product updates](#product-updates)

[Shopping cart experience](#shopping-cart-experience)

[Why you should use them](#why-you-should-use-them)

[Why you should use it](#why-you-should-use-it)

[Sending product messages](#sending-product-messages)

[Step 1: Assemble the interactive object](#step-1--assemble-the-interactive-object)

[Step 2: Add common message parameters](#step-2--add-common-message-parameters)

[Step 3: Send a request to the messages endpoint](#step-3--send-a-request-to-the-messages-endpoint)

[Single-product message templates](#single-product-message-templates)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/guides/sell-products-and-services/share-products/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 6 de nov
Atualização em Português (Brasil): 19 de set

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Share products with WhatsApp users

You have multiple ways to share products with your customers.

## Catalog messages

Catalog messages are messages that allow you to showcase your product catalog entirely within WhatsApp.

Catalog messages display a product thumbnail header image of your choice, custom body text, a fixed text header, a fixed text sub-header, and a **View catalog** button.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/353831413_931793014769642_1489938023342123500_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=AaF8MWiokYIQ7kNvwFeZvQF&_nc_oc=Adn7gfSiu95n8nTwRn1F2tczQSnmK-hSFwYztiX6rifH09d4Sp4eJyfanBxclre5fCQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_AfgwAgJqKfIDSkC7zz0lCWgd3hy0G280KiTMMLqbdKFZSQ&oe=69406AD5)

When a customer taps the **View catalog** button, your product catalog appears within WhatsApp.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/353808079_9331603410246288_3629219693038191737_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=dMOBq3BvMEoQ7kNvwEnpOY-&_nc_oc=AdmfMAnczjQ9SP1hqVDxKAfr9XtKEERQHWSPRHhhx4gYIlK1i1R3NP3_6GU-cQ1tljk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_AfhGPIy18xLz554tr_cqZ8Gl0N1rcq1zWfcI1tqzPPMeAA&oe=69405FE8)

### Requirements

You must have [inventory uploaded to Meta](/docs/whatsapp/cloud-api/guides/sell-products-and-services/upload-inventory) in an ecommerce catalog [connected to your WhatsApp Business Account](https://www.facebook.com/business/help/158662536425974).

### Request syntax

Use the **WhatsApp Business Phone Number > Messages** endpoint to send a catalog message.

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages
```

### Post body

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<TO>",
  "type": "interactive",
  "interactive" : {
    "type" : "catalog_message",
    "body" : {
      "text": "<BODY_TEXT>"
    },
    "action": {
      "name": "catalog_message",

      /* Parameters object is optional */
      "parameters": {
        "thumbnail_product_retailer_id": "<THUMBNAIL_PRODUCT_RETAILER_ID>"
      }
    },

    /* Footer object is optional */
    "footer": {
      "text": "<FOOTER_TEXT>"
  }
}
```

### Properties

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<BODY_TEXT>`  *String* | **Required.**   Text to appear in the message body.   Maximum 1024 characters. | `Hello! Thanks for your interest. Ordering is easy. Just visit our catalog and add items to purchase.` |
| `<FOOTER_TEXT>`  *String* | **Optional.**   Text to appear in the message footer.   Maximum 60 characters. | `Best grocery deals on WhatsApp!` |
| `<THUMBNAIL_PRODUCT_RETAILER_ID>`  *String* | **Optional.**   Item SKU number. Labeled as **Content ID** in the Commerce Manager.   The thumbnail of this item will be used as the message's header image.   If the `parameters` object is omitted, the product image of the first item in your catalog will be used. | `2lc20305pt` |
| `<TO>`  *String* | Customer phone number. | `+16505551234` |

### Example request

```
curl 'https://graph.facebook.com/v17.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "type": "interactive",
  "interactive": {
    "type": "catalog_message",
    "body": {
      "text": "Hello! Thanks for your interest. Ordering is easy. Just visit our catalog and add items to purchase."
    },
    "action": {
      "name": "catalog_message",
      "parameters": {
        "thumbnail_product_retailer_id": "2lc20305pt"
      }
    },
    "footer": {
      "text": "Best grocery deals on WhatsApp!"
    }
  }
}'
```

### Example response

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
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI0ODVEREUwQzEzQkVBRjQ1RUUA"
    }
  ]
}
```

## Catalog template messages

Catalog template messages are template messages containing a button that, when tapped, displays your product catalog within WhatsApp.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/354047426_125269187252102_7173148343631613735_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=b5R6jfDxH9EQ7kNvwHJqBCf&_nc_oc=AdnSVBYegy4Cq1XYLX9S3mq81YIfBeDZBgOqz4-xUBNqCViGA3nKZcpZgBty0opk0Ac&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_Afg4Hxkunar43OFMBpmi9dv36JUOLmwMreebQNQR3596UA&oe=69405A26)

See [Catalog Templates](/docs/whatsapp/business-management-api/message-templates/catalog-templates) to learn how to create and send these templates.

## Catalog Link messages

You can send a link to your entire product catalog by assembling a wa.me link and including it in a standard [text message](/docs/whatsapp/cloud-api/guides/send-messages#text-messages). When sending a text message, you can use the optional `preview_url` set to `true` to have the message render a set of product catalog thumbnails of any URL in the message `body` string.

Note that if you [disable the catalog](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings#enable-disable-catalog), wa.me links and the **View Catalog** button in catalog link messages will display a **Invalid catalog link** message when tapped.

To assemble wa.me link, append your business phone number, including country code, to the end of the following string:

```
https://wa.me/c/
```

For example:

```
https://wa.me/c/15555455657
```

## Checkout button templates

Checkout button templates allow India-based businesses to showcase one or more products that WhatsApp users in India (with India country calling codes) can purchase, without having to leave the WhatsApp client.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/461864193_1053025166222560_1984323495828319066_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=OXfP_Hh4c3MQ7kNvwEe2qkT&_nc_oc=AdlPfcoLIlid_b00n8_DOwlUoIrx-yqdZUrkv5WvwxyafBoeDDWI9uk4KQ2m5h1jqXk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_AfjWrgBKHR17Jwn36wD2s1QzwlTB4dWgI9srzqjcqAnYHQ&oe=6940627C)

See [Checkout Button Templates](/docs/whatsapp/cloud-api/payments-api/payments-in/checkout-button-templates) to learn how to create and send these templates.

## Media card carousel templates

Media card carousel template messages allow you to send a single text message accompanied by a set of up to 10 cards in a horizontally scrollable view:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/461961248_1048610163180196_3907313698557856900_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=vdPyjxZ_Hf4Q7kNvwHlHzj1&_nc_oc=AdkEPZWsbsd-BVhZWBnrTj6cdqLtMmDZ4H6vyNaxjqSNALnqVJlDTH2djfJAMVlglQw&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_Afi1z3GEj8GrDL6IjH5trZnmG0GX4QVzDljCs3NWahW5Pg&oe=69407B3C)

See [Media Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates) to learn how to create and send these templates.

## Multi-product message templates

Multi-Product Message (MPM) template messages present product information for up to 30 products from your ecommerce catalog, organized customizable by sections.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/345336924_1476472873159435_9050004394387774321_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=Bo6oPwvRcMkQ7kNvwGSZi2i&_nc_oc=Adn4Z4JHKUJ94BwBXvcfl0-pXHq669Xpdpa-D6l45awTbFH7Gt2106-B9k_RhS4Bt6s&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_Afi1-cTlsSwVX1dtTzusxp0UFLS6bv5ensWjnB8fqUfeyA&oe=69407DDC)

See [Multi-Product Message Templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates) to learn how to create and send MPM templates.

## Product card carousel templates

Product card carousel template messages allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456451243_832660229062364_6760679807399209749_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=GkdwnchPbQAQ7kNvwHpoZVb&_nc_oc=Adl5ySnqRavQIOb_hSHSvujOf0DXYWqQw2t4cc49dPsR6xYcdIsfvCW4wR_JMxSE5Uo&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_AfiBkW0YBKbaXm4v_LiOv3osVYJWARD0NQSxIyB4qSguQQ&oe=69406223)

See [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates) to learn how to create and send these templates.

## Product messages

Both Multi-Product Messages and Single-Product Messages are types of interactive messages.

|  |  |
| --- | --- |
| *Multi-Product message example:* | *Single-Product message example:* |
| ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1395416064274007&version=1762443742) | ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=827995641720475&version=1762443742) |
| *Menu triggered when user clicks on Start Shopping:* | *Product Detail Page example:* |
| ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=2914485018850726&version=1762443742) | ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=707961307104719&version=1762443742) |

### Overview

Customers that receive Multi- and Single-Product Messages can perform 3 main actions:

1. View products: Customers can see a list of products or just one product. Whenever a customer clicks on a specific item, we fetch the product's latest info and display the product in a Product Detail Page (PDP) format. Currently, PDPs only support product images — any videos and/or GIFs added to the product won’t be displayed in the PDP.
2. Add products to a cart: Whenever a user adds a product to the shopping cart, we fetch the item’s latest info. If there has been a state change on any of the items, we display a dialog saying "One or more items in your cart have been updated" — See [Product Updates](#product-updates) for more information. A cart persists in a chat thread between you and your customer until the cart is sent to you — See [Shopping Cart Experience](#shopping-cart-experience) for details.
3. Send a shopping cart to you: After adding all needed items, customers can send their cart to you. After that, you can define the next steps, such as requesting delivery info or giving payment options.

If your customer has multiple devices linked to their account, the Multi-Product and Single-Product Messages will be synced between devices. However, the shopping cart is local to each specific device. See [Shopping Cart Experience](#shopping-cart-experience) for details.

Currently, these types of messages can be received in the following platforms:

* iOS: 2.21.100 (Multi-Product Messages) and 2.21.210 (Single-Product Messages).
* Android: 2.21.9.15 (Multi-Product Messages) and 2.21.19 (Single-Product Messages).
* Web: The web client that supports these features has been launched.

If the customer's app version does not support Multi- or Single-Product Messages, they will instead receive a message explaining that they were unable to receive a message because they are using an outdated version of WhatsApp. We will also send you a webhook notification indicating the message was unable to be delivered due to the customer using an outdated version of WhatsApp.

### Expected Behavior for Messages

Multi-Product Messages and Single-Product Messages can be:

* Forwarded by one user to another.
* Reopened by a user within the same chat thread.

Multi-Product Messages and Single-Product Messages cannot be:

* Sent as notifications. They can only be sent as part of existing chat threads.

### Limitations

Unlike product messages sent via the WhatsApp Business app, messages sent via the Cloud API currently do not display a shopping cart icon in the chat thread header.

### Product updates

You may need to update properties of items in your catalog. Depending on the updated property, this is how we handle any messages mentioning that product:

| Updated Property | Update Process |
| --- | --- |
| Product's price, title, description, and image. | 1. You send a Multi or Single-Product Message containing product A. 2. You update product A's properties on their catalog. 3. The screens that display that product are updated as soon as the customer client learns about the change from the server. |
| Availability change | 1. You send a customer a Multi- or Single-Product Message containing product B. 2. You sell all units of product B available. Then, you update your catalog saying that product B is no longer available 3. If a customer has already added product B to a cart, the item will be removed from the cart. The shopping cart displays a dialog saying "One or more items in your cart have been updated". 4. If a customer has not added product B to the cart, the Multi- or Single-Product Message now shows the item as unavailable. |

### Shopping cart experience

After viewing products, a customer can add them to their shopping cart and send that cart to you. For the purposes of commerce on WhatsApp, a shopping cart:

* Is unique to a customer/business chat thread in a specific device: Only one cart is created per chat thread between you and a customer, and carts do not persist across multiple devices. Once a cart is sent, the customer can open another cart with you and start the process again.
* Has no expiration date: The cart persists in the chat thread until it is sent to you. Once sent, the cart is cleared.

Customers can add up to 99 units of each single catalog item to a shopping cart, but there is no limit on the number of distinct items that can be added to a cart.

Once a cart has been sent, no edits can be made. Customers can send a new cart if they need new items, or would like to change their order. You cannot send carts to customers.

|  |  |
| --- | --- |
| ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=357660539835692&version=1762443742) | ![](https://lookaside.fbsbx.com/elementpath/media/?media_id=571456757903275&version=1762443742) |

*Shopping cart experience example and expected behavior for item state change.*

### Why you should use them

Both Multi- and Single-Product Messages lend themselves best to user experiences that are simple and personalized, where it's a better experience to guide the customer to a subset of items most relevant to them, rather than browsing your full inventory.

#### Simple and efficient

Combining the features with navigation tools like NLP, text search or List Messages and Reply Buttons to get to what the customer is looking for fast.

#### Personal

Populated dynamically so can be personalized to the customer or situation. For example, you can show a Multi-Product Message of a customer’s most frequently ordered items.

#### Business outcomes

A performant channel for driving orders, during testing businesses had an average 7% conversion of Multi-Product Messages sent to carts received.

#### No templates

Interactive messages do not require templates or pre-approvals. They are generated in real-time and will always reflect the latest item details, pricing and stock levels from your inventory.

### Why you should use it

Multi-Product Messages are best for guiding customers to a specific subset of your inventory, such as:

* Shopping in a conversational way. For example, using search functionality to allow customers to type a shopping list and send back a Multi-Product Message in response.
* Navigating to a specific category. For example, fitness apparel.
* Personalized offers or recommendations.
* Re-ordering previously ordered items. For example, a user can re-order their regular take-out order of less than 30 items.

Single-Product Messages are best for guiding customers to one specific item from your inventory, offering quick responses from a limited set of options, such as:

* Responding to a customer’s specific request.
* Providing a recommendation.
* Reordering a previous item.

Both features can also be used as part of a human agent flow, however you need to build the tooling to allow the human agent to generate a Multi-Product Message or Single-Product Message in thread.

### Sending product messages

Before sending product messages, follow the get started best suited for your needs:

* [Direct developers](/docs/whatsapp/cloud-api/get-started)
* [Solution providers](/docs/whatsapp/solution-providers)

All API calls mentioned in this guide must be authenticated with an access token. Developers can authenticate their API calls with the access token generated in the **App Dashboard** > **WhatsApp** > **API Setup** panel. Solution Partners must authenticate themselves with an access token with the [whatsapp\_business\_messaging](/docs/permissions/reference/whatsapp_business_messaging) permission.

### Step 1: Assemble the interactive object

#### Single-Product Messages

To send a Single-Product Message, assemble an `interactive` object of type `product` with the following components:

| Required Components | Optional Components |
| --- | --- |
| * Action Object — Must include both catalog\_id and product\_retailer\_id. | * Body Object * Footer Object |

See [Messages, Interactive Object](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) for full information. By the end of the process, the interactive object should look something like this:

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "PHONE_NUMBER",
  "type": "interactive",
  "interactive": {
    "type": "product",
    "body": {
      "text": "BODY_TEXT"
    },
    "footer": {
      "text": "FOOTER_TEXT"
    },
    "action": {
      "catalog_id": "CATALOG_ID",
      "product_retailer_id": "ID_TEST_ITEM_1"
    }
  }
}
```

#### Multi-product messages

To send a Multi-Product Message, assemble an `interactive` object of type `product_list` with the following components:

| Required Components | Optional Components |
| --- | --- |
| * Header Object — Header’s type must be set to text. Remember to add a text object with the desired content. * Body Object * Action Object - Must include catalog\_id and sections.    + Sections must be an array of objects describing each section using title and product\_items.      - Each section's product\_items value must be an array describing each product in the section using product\_retailer\_id and the product's SKU number. | * Footer Object |

See [Messages, Interactive Object](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) for full information. By the end of the process, the interactive object should look something like this:

```
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "PHONE_NUMBER",
  "type": "interactive",
  "interactive": {
    "type": "product_list",
    "header":{
      "type": "text",
      "text": "HEADER_CONTENT"
    },
    "body": {
      "text": "BODY_CONTENT"
    },
    "footer": {
      "text": "FOOTER_CONTENT"
    },
    "action": {
      "catalog_id": "CATALOG_ID",
      "sections": [
        {
          "title": "SECTION_TITLE",
          "product_items": [
            { "product_retailer_id": "PRODUCT-SKU" },
            { "product_retailer_id": "PRODUCT-SKU" },
            ...
          ]

        },
        {
          "title": "SECTION_TITLE",
          "product_items": [
            { "product_retailer_id": "PRODUCT-SKU" },
            { "product_retailer_id": "PRODUCT-SKU" },
            ...
          ]
        }
      ]
    }
  }
}
```

#### Missing items

If none of the items provided in the API calls above matches a product from your product catalog, an error message is sent and the Multi- or Single-Product Message is not sent to the user.

For Multi-Product Message, at least one item from the products list must match an item from your product catalog. In this case:

* Messages are sent successfully
* Items without a match are dropped
* You receive an error message asking for a catalog update

### Step 2: Add common message parameters

Once the interactive object is complete, append the other parameters that make a message: `recipient_type`, `to`, `messaging_product`, and `type`. Remember to set the `type` to `interactive`.

```
curl -X  POST https://graph.facebook.com/v24.0/FROM_PHONE_NUMBER/messages \
 -H 'Authorization: Bearer ACCESS_TOKEN' \
 - d '{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "PHONE_NUMBER",
  "type": "interactive",
  "interactive": {
  // INTERACTIVE OBJECT GOES HERE
}'
```

For all available parameters, see [Reference, Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/).

### Step 3: Send a request to the messages endpoint

Send a POST request to the [`/PHONE_NUMBER_ID/messages`](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint with the JSON object you have assembled in steps 1 and 2. If your message is sent successfully, you get the following response:

```
{
  "messaging_product": "whatsapp",
  "contacts": [{
      "input": "PHONE_NUMBER",
      "wa_id": "WHATSAPP_ID",
    }]
  "messages": [{
      "id": "wamid.ID",
    }]
}
```

## Single-product message templates

Single-Product Message (SPM) template messages present a single product from your ecommerce catalog, accompanied by a product image, product title, and product price (all pulled from your product within your catalog), along with customizable body text, optional footer text, and an interactive **View** button.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/456334558_1165670014537761_4619872146080155046_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=w2ixZ6vqf5oQ7kNvwF_WplR&_nc_oc=Adnt8-hstwClCwz3RSTFuiKBiPilL9mHMiQTsEqsMqD2kruj5yScRn88OPVX-wpsplw&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hSc3hSdS2mlF-82aAcj-3w&oh=00_AfhF6mVvduFTF6WxRqC0HS-YQyusvtM22rGAjhqxh2DOXw&oe=6940884E)

See [Single-Product Message Templates](/docs/whatsapp/business-management-api/message-templates/spm-templates) to learn how to create and send SPM templates.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Share products with WhatsApp users](#share-products-with-whatsapp-users)

[Catalog messages](#catalog-messages)

[Requirements](#requirements)

[Request syntax](#request-syntax)

[Post body](#post-body)

[Properties](#properties)

[Example request](#example-request)

[Example response](#example-response)

[Catalog template messages](#catalog-template-messages)

[Catalog Link messages](#catalog-link-messages)

[Checkout button templates](#checkout-button-templates)

[Media card carousel templates](#media-card-carousel-templates)

[Multi-product message templates](#multi-product-message-templates)

[Product card carousel templates](#product-card-carousel-templates)

[Product messages](#product-messages)

[Overview](#overview)

[Expected Behavior for Messages](#expected-behavior-for-messages)

[Limitations](#limitations)

[Product updates](#product-updates)

[Shopping cart experience](#shopping-cart-experience)

[Why you should use them](#why-you-should-use-them)

[Why you should use it](#why-you-should-use-it)

[Sending product messages](#sending-product-messages)

[Step 1: Assemble the interactive object](#step-1--assemble-the-interactive-object)

[Step 2: Add common message parameters](#step-2--add-common-message-parameters)

[Step 3: Send a request to the messages endpoint](#step-3--send-a-request-to-the-messages-endpoint)

[Single-product message templates](#single-product-message-templates)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=fXyIm5N6P0a5Lyy3WdI9Ug&oh=00_Afi079lbeUb6QhaIDbKBC9ZoT_MxxpdtkEURUEG3mW330g&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=fXyIm5N6P0a5Lyy3WdI9Ug&oh=00_AfixVgPWcKW-b910eQfDSAOvJafVjurjOxE6bGeT-XtGuw&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=fXyIm5N6P0a5Lyy3WdI9Ug&oh=00_AfjbUafcJT3WRcIkt_OtXFCgqO6d-UhXFe5zeLLeHgOt1A&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=fXyIm5N6P0a5Lyy3WdI9Ug&oh=00_AfjFtefk1GxJT4rJaz7uPROSyOmW71trjR3N3L_l2odvsg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=fXyIm5N6P0a5Lyy3WdI9Ug&oh=00_AfiveALaGQyFNjWmP5W6BHeE_OIAPRrTkggR3FNsF4MmxA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3kdF2-M2J0pMcw-vHw-j-AsdEyLU7xruT2tOu2fMWZ4SFOWJXy2y0BGNJauwehoMsYb7RvSB87d7l71c3EyyMlC1DJWl5UdCClUDB2cK12VKyFDx1yQY4We68K7UppYblXdBlHRzi3Y8nKKMwzqw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)