![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fcomponents%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Componentes](/docs/whatsapp/business-management-api/message-templates/components)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)
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

[Template components](#template-components)

[Text header](#text-header)

[Creation syntax](#creation-syntax)

[Creation parameters](#creation-parameters)

[Creation example](#creation-example)

[Media header](#media-header)

[Creation syntax](#creation-syntax-2)

[Creation parameters](#creation-parameters-2)

[Creation example](#creation-example-2)

[Location header](#location-header)

[Creation syntax](#creation-syntax-3)

[Creation parameters](#creation-parameters-3)

[Creation example](#creation-example-3)

[Send syntax](#send-syntax)

[Send parameters](#send-parameters)

[Send example](#send-example)

[Body](#body)

[Creation syntax](#creation-syntax-4)

[Creation parameters](#creation-parameters-4)

[Creation example](#creation-example-4)

[Footer](#footer)

[Syntax](#syntax)

[Properties](#properties)

[Example](#example)

[Buttons](#buttons)

[Copy code buttons](#copy-code-buttons)

[Multi-product message buttons](#multi-product-message-buttons)

[One-time password buttons](#one-time-password-buttons)

[Phone number buttons](#phone-number-buttons)

[Quick reply buttons](#quick-reply-buttons)

[SPM buttons](#spm-buttons)

[URL buttons](#url-buttons)

[Limited-time offer](#limited-time-offer)

[Example requests](#example-requests)

[Seasonal promotion](#seasonal-promotion)

[Order confirmation](#order-confirmation)

[Order delivery update](#order-delivery-update)

[Webhooks](#webhooks)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/message-templates/components/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 21 de nov
Atualização em Português (Brasil): 7 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# Template components

Templates are made up of four primary components which you define when you create a template: header, body, footer, and buttons. The components you choose for each of your templates should be based on your business needs. The only required component is the body component.

Some components support variables, whose values you can supply when using the Cloud API or On-Premises API to send the template in a template message. If your templates use variables, you must include sample variable values upon template creation.

## Text header

Text headers are optional elements that can be added to the top of template messages. Each template may include only one text header. Please note that markdown special characters are not supported in this component, so we recommend avoiding their use.

Text headers support 1 [parameter](/docs/whatsapp/business-management-api/message-templates#parameter-formats).

### Creation syntax

```
<!-- No parameter syntax -->
{
  "type": "header",
  "format": "text",
  "text": "<HEADER_TEXT>"
}

<!-- Named parameter syntax -->
{
  "type": "header",
  "format": "text",
  "text": "<HEADER_TEXT>",
  "example": {
    "header_text_named_params": [
      {
        "param_name": "<NAMED_PARAMETER_NAME>",
        "example": "<PARAMETER_EXAMPLE_VALUE>"
      }
    ]
  }
}

<!-- Positional parameter syntax -->
{
  "type": "header",
  "format": "text",
  "text": "<HEADER_TEXT>",
  "example": {
    "header_text": [
      "<PARAMETER_EXAMPLE_VALUE>"
    ]
  }
}
```

### Creation parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<HEADER_TEXT>`  *String* | **Required.**  Header body text string. Supports 1 [parameter](/docs/whatsapp/business-management-api/message-templates#parameter-formats).  If this string contains a parameter, you must include the `example` property and example parameter value.  Maximum 60 characters. | `Our new sale starts {{sale_start_date}}!` |
| `<NAMED_PARAMETER_NAME>`  *String* | **Required if using a named parameter.**  [Named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters) name. | `{{sale_start_date}}` |
| `<PARAMETER_EXAMPLE_VALUE>`  *String* | **Required if using a parameter.**  [Parameter](/docs/whatsapp/business-management-api/message-templates#parameter-formats) example value. | `December 1st` |

### Creation example

This example uses 1 named parameter.

```
{
  "type": "HEADER",
  "format": "TEXT",
  "text": "Our new sale starts {{sale_start_date}}!",
  "example": {
    "header_text_named_params": [
      {
        "param_name": "sale_start_date",
        "example": "December 1st"
      }
    ]
  }
}
```

## Media header

Media headers can be an image, video, gif, or a document such as a PDF. All media must be uploaded with the [Resumable Upload API](/docs/graph-api/guides/upload). The syntax for defining a media header is the same for all media types.

Note: Gifs are currently only available for [Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-lite-api/features). Gifs are mp4 files with a max size of 3.5MB and larger files will be displayed as video messages.

### Creation syntax

```
{
  "type": "HEADER",
  "format": "<FORMAT>",
  "example": {
    "header_handle": [
      "<HEADER_HANDLE>"
    ]
  }
}
```

### Creation parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<FORMAT>` | Indicates media asset type. Set to `IMAGE`, `VIDEO`, `GIF`, or `DOCUMENT`. | `IMAGE` |
| `<HEADER_HANDLE>` | Uploaded media asset handle. Use the [Resumable Upload API](/docs/graph-api/guides/upload) to generate an asset handle. | `4::aW...` |

### Creation example

```
{
  "type": "HEADER",
  "format": "IMAGE",
  "example": {
    "header_handle": [
      "4::aW..."
    ]
  }
}
```

## Location header

Location headers appear as generic maps at the top of the template and are useful for order tracking, delivery updates, ride-hailing pickup/dropoff, locating physical stores, etc. When tapped, the app user's default map app will open and load the specified location. Locations are specified when you send the template.

Location headers can only be used in templates categorized as `UTILITY` or `MARKETING`. Real-time locations are not supported.

### Creation syntax

```
{
  "type": "header",
  "format": "location"
}
```

### Creation parameters

None.

### Creation example

```
{
  "type": "header",
  "format": "location"
}
```

### Send syntax

```
{
  "type": "header",
  "parameters": [
    {
      "type": "location",
      "location": {
        "latitude": "<LOCATION_LATITUDE>",
        "longitude": "<LOCATION_LONGITUDE>",
        "name": "<LOCATION_NAME>",
        "address": "<LOCATION_ADDRESS>"
      }
    }
  ]
}
```

### Send parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<LOCATION_ADDRESS>` | Location address. | `101 Forest Ave, Palo Alto, CA 94301` |
| `<LOCATION_LATITUDE>` | Location latitude in decimal degrees. | `37.44211676562361` |
| `<LOCATION_LONGITUDE>` | Location longitude in decimal degrees. | `122.16155960083124` |
| `<LOCATION_NAME>` | Location name. | `Philz Coffee` |

### Send example

```
{
  "type": "header",
  "parameters": [
    {
      "type": "location",
      "location": {
        "latitude": "37.44211676562361",
        "longitude": "-122.16155960083124",
        "name": "Philz Coffee",
        "address": "101 Forest Ave, Palo Alto, CA 94301"
      }
    }
  ]
}
```

## Body

The body component represents the core text of your message template and is a text-only template component. Templates are limited to one body component.

The message text in the body component accepts multiple [parameters](/docs/whatsapp/business-management-api/message-templates#parameter-formats).

### Creation syntax

```
<!-- No parameters syntax -->
{
  "type": "body",
  "text": "<BODY_TEXT>"
}

<!-- Named parameters syntax -->
{
  "type": "body",
  "text": "<BODY_TEXT>",
  "example": {
    "body_text_named_params": [
      {
        "param_name": "<NAMED_PARAMETER_NAME>",
        "example": "<PARAMETER_EXAMPLE_VALUE>"
      }
      <!-- Additional named parameters go here, if using -->
    ]
  }
}

<!-- Positional parameters syntax -->
{
  "type": "body",
  "text": "<BODY_TEXT>",
  "example": {
    "body_text": [
      "<PARAMETER_EXAMPLE_VALUE>"
      <!-- Additional positional parameters go here, if using -->
    ]
  }
}
```

### Creation parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BODY_TEXT>`  *String* | **Required.**  Body text string. Supports multiple [parameters](/docs/whatsapp/business-management-api/message-templates#parameter-formats).  Maximum of 1024 characters. | `Thank you, {{first_name}}! Your order number is {{order_number}}.` |
| `<NAMED_PARAMETER_NAME>`  *String* | **Required if using a named parameter.**  [Named parameter](/docs/whatsapp/business-management-api/message-templates#named-parameters) name. | `{{order_number}}` |
| `<PARAMETER_EXAMPLE_VALUE>`  *String* | **Required if using a parameter.**  [Parameter](/docs/whatsapp/business-management-api/message-templates#parameter-formats) example value. | `December 1st` |

### Creation example

```
{
  "type": "body",
  "text": "Thank you, {{first_name}}! Your order number is {{order_number}}.",
  "example": {
    "body_text_named_params": [
      {
        "param_name": "first_name",
        "example": "Pablo"
      },
      {
        "param_name": "order_number",
        "example": "860198-230332"
      }
    ]
  }
}
```

## Footer

Footers are optional text-only components that appear immediately after the body component. Templates are limited to one footer component.

### Syntax

```
{
  "type": "FOOTER",
  "text": "<TEXT>"
}
```

### Properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<TEXT>` | Text to appear in template footer when sent.   60 characters maximum. | `Use the buttons below to manage your marketing subscriptions` |

### Example

```
{
  "type": "FOOTER",
  "text": "Use the buttons below to manage your marketing subscriptions"
}
```

## Buttons

Buttons are optional interactive components that perform specific actions when tapped.

Templates can have a combination of up to 10 button components in total, although there are limits to individual buttons of the same type as well as combination limits, which are described below. In addition, templates composed of 4 or more buttons, or a quick reply button and one or more buttons of another type, cannot be viewed on WhatsApp desktop clients. WhatsApp users who receive one of these template messages will be prompted to view the message on a phone instead.

Buttons are defined within a single buttons component object, packed into a single `buttons` array. For example, this template uses a phone number button and a URL button:

```
{
  "type": "BUTTONS",
  "buttons": [
    {
      "type": "PHONE_NUMBER",
      "text": "Call",
      "phone_number": "15550051310"
    },
    {
      "type": "URL",
      "text": "Shop Now",
      "url": "https://www.luckyshrub.com/shop/"
    }
  ]
}
```

If a template has more than three buttons, two buttons will appear in the delivered message, and the remaining buttons will be replaced with a **See all options** button. Tapping the **See all options** button reveals the remaining buttons.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/362692024_651522560374555_6131765669860446689_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=DuQwUrQ7TMwQ7kNvwEvLhYl&_nc_oc=AdnqEi9PFObGbHpwxRNW68VKnpivieClsibUoUm3Ckk59lJrlSzRf9q5oS4Y9CWuvoc&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=vUyOsXMivHAgw0KkHE9O4g&oh=00_AfjfhPD9NWwZsCJG_Tq_7_JydlsCP4XKClV0e5diWWsgkA&oe=69405FBB)

### Copy code buttons

Copy code buttons copy a text string (defined when the template is sent in a template message) to the device's clipboard when tapped by the app user. Templates are limited to one copy code button.

#### Syntax

```
{
  "type": "COPY_CODE",
  "example": "<EXAMPLE>"
}
```

#### Properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<EXAMPLE>` | String to be copied to the device's clipboard when tapped by the app user.   Maximum 15 characters. | `250FF` |

#### Example

```
{
  "type": "COPY_CODE",
  "example": "250FF"
}
```

### Multi-product message buttons

Multi-product message buttons are special, non-customizable buttons that, when tapped, display up to 30 products from your ecommerce catalog, organized in up to 10 sections, in a single message. See [Multi-Product Message Templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates).

### One-time password buttons

One-time password buttons are a special type of [URL button](#url-buttons) component used with authentication templates. See [Authentication Templates](/docs/whatsapp/business-management-api/authentication-templates).

### Phone number buttons

Phone number buttons call the specified business phone number when tapped by the app user. Templates are limited to one phone number button.

#### Syntax

```
{
  "type": "PHONE_NUMBER",
  "text": "<TEXT>",
  "phone_number": "<PHONE_NUMBER>"
}
```

#### Properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<PHONE_NUMBER>` | Alphanumeric string. Business phone number to be called when the user taps the button.  Note that some countries have special phone numbers that have leading zeros after the country calling code (for example, +55-0-955-585-95436). If you assign one of these numbers to the button, the leading zero will be stripped from the number. If your number will not work without the leading zero, assign an alternate number to the button, or add the number as message body text.  20 characters maximum. | `15550051310` |
| `<TEXT>` | Button label text.   25 characters maximum. | `Call` |

#### Example

```
{
  "type": "PHONE_NUMBER",
  "text": "Call",
  "phone_number": "15550051310"
}
```

### Quick reply buttons

Quick reply buttons are custom text-only buttons that immediately message you with the specified text string when tapped by the app user. A common use case is a button that allows your customer to easily opt-out of any marketing messages.

Templates are limited to 10 quick reply buttons. If using quick reply buttons with other buttons, buttons must be organized into two groups: quick reply buttons and non-quick reply buttons. If grouped incorrectly, the API will return an error indicating an invalid combination.

Examples of valid groupings:

* Quick Reply, Quick Reply
* Quick Reply, Quick Reply, URL, Phone
* URL, Phone, Quick Reply, Quick Reply

Examples of invalid groupings:

* Quick Reply, URL, Quick Reply
* URL, Quick Reply, URL

When using the API to send a template that has multiple quick reply buttons, you can use the index property to designate the order in which buttons appear in the template message.

#### Syntax

```
{
  "type": "QUICK_REPLY",
  "text": "<TEXT>"
}
```

#### Properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<TEXT>` | Button label text.   25 characters maximum. | `Unsubscribe` |

#### Example

```
{
  "type": "QUICK_REPLY",
  "text": "Unsubscribe from Promos"
}
```

### SPM buttons

Single-product message (SPM) buttons are special, non-customizable buttons that can be mapped to a product in your product catalog. When tapped, they load details about the product, which it pulls from your catalog. Users can then add the product to their cart and place an order. See [Single-Product Message Templates](/docs/whatsapp/business-management-api/message-templates/spm-templates) and [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates).

### URL buttons

URL buttons load the specified URL in the device's default web browser when tapped by the app user. Templates are limited to two URL buttons.

#### Syntax

```
{
  "type": "URL",
  "text": "<TEXT>",
  "url": "<URL>",

  # Required if <URL> contains a variable
  "example": [
    "<EXAMPLE>"
  ]
}
```

#### Properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<EXAMPLE>` | URL of website. Supports 1 variable.   If using a variable, add sample variable property to the end of the URL string. The URL loads in the device's default mobile web browser when the customer taps the button.   2000 characters maximum. | `https://www.luckyshrub.com/shop?promo=summer2023` |
| `<TEXT>` | Button label text. 25 characters maximum. | `Shop Now` |
| `<URL>` | URL of website that loads in the device's default mobile web browser when the button is tapped by the app user.   Supports 1 variable, appended to the end of the URL string.   2000 characters maximum. | `https://www.luckyshrub.com/shop?promo={{1}}` |

#### Example

```
{
  "type": "URL",
  "text": "Shop Now",
  "url": "https://www.luckyshrub.com/shop?promo={{1}}",
  "example": [
    "summer2023"
  ]
}
```

## Limited-time offer

Limited-Time Offer components are special components used to create [limited-time offer templates](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates).

## Example requests

### Seasonal promotion

An example request to create a marketing template with the following components:

* a text header with a variable and sample value
* a text body with variables and sample values
* a text footer
* two quick-reply buttons

```
curl -L 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Authorization: Bearer EAAJB...' \
-H 'Content-Type: application/json' \
-d '
{
  "name": "seasonal_promotion",
  "language": "en_US",
  "category": "MARKETING",
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT",
      "text": "Our {{1}} is on!",
      "example": {
        "header_text": [
          "Summer Sale"
        ]
      }
    },
    {
      "type": "BODY",
      "text": "Shop now through {{1}} and use code {{2}} to get {{3}} off of all merchandise.",
      "example": {
        "body_text": [
          [
            "the end of August","25OFF","25%"
          ]
        ]
      }
    },
    {
      "type": "FOOTER",
      "text": "Use the buttons below to manage your marketing subscriptions"
    },
    {
      "type":"BUTTONS",
      "buttons": [
        {
          "type": "QUICK_REPLY",
          "text": "Unsubscribe from Promos"
        },
        {
          "type":"QUICK_REPLY",
          "text": "Unsubscribe from All"
        }
      ]
    }
  ]
}'
```

### Order confirmation

An example request to create a utility template with the following components:

* a document header with a sample value
* a text body with variables and sample values
* a phone number button
* a URL button

```
curl -L 'https://graph.facebook.com/v16.0/102290129340398/message_templates' \
-H 'Authorization: Bearer EAAJB...' \
-H 'Content-Type: application/json' \
-d '
{
  "name": "order_confirmation",
  "language": "en_US",
  "category": "UTILITY",
  "components": [
    {
      "type": "HEADER",
      "format": "DOCUMENT",
      "example": {
        "header_handle": [
          "4::YX..."
        ]
      }
    },
    {
      "type": "BODY",
      "text": "Thank you for your order, {{1}}! Your order number is {{2}}. Tap the PDF linked above to view your receipt. If you have any questions, please use the buttons below to contact support. Thank you for being a customer!",
      "example": {
        "body_text": [
          [
            "Pablo","860198-230332"
          ]
        ]
      }
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "PHONE_NUMBER",
          "text": "Call",
          "phone_number": "15550051310"
        },
        {
          "type": "URL",
          "text": "Contact Support",
          "url": "https://www.luckyshrub.com/support"
        }
      ]
    }
  ]
}'
```

### Order delivery update

An example request to create a utility template with the following components:

* a location header
* a text body with variables and sample values
* a footer
* a quick reply button

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "order_delivery_update",
  "language": "en_US",
  "category": "UTILITY",
  "components": [
    {
      "type": "HEADER",
      "format": "LOCATION"
    },
    {
      "type": "BODY",
      "text": "Good news {{1}}! Your order #{{2}} is on its way to the location above. Thank you for your order!",
      "example": {
        "body_text": [
          [
            "Mark",
            "566701"
          ]
        ]
      }
    },
    {
      "type": "FOOTER",
      "text": "To stop receiving delivery updates, tap the button below."
    },
    {
      "type":"BUTTONS",
      "buttons": [
        {
          "type": "QUICK_REPLY",
          "text": "Stop Delivery Updates"
        }
      ]
    }
  ]
}'
```

## Webhooks

Subscribe to the [message\_template\_components\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_components_update) webhook field to be notified of changes to a template's components.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template components](#template-components)

[Text header](#text-header)

[Creation syntax](#creation-syntax)

[Creation parameters](#creation-parameters)

[Creation example](#creation-example)

[Media header](#media-header)

[Creation syntax](#creation-syntax-2)

[Creation parameters](#creation-parameters-2)

[Creation example](#creation-example-2)

[Location header](#location-header)

[Creation syntax](#creation-syntax-3)

[Creation parameters](#creation-parameters-3)

[Creation example](#creation-example-3)

[Send syntax](#send-syntax)

[Send parameters](#send-parameters)

[Send example](#send-example)

[Body](#body)

[Creation syntax](#creation-syntax-4)

[Creation parameters](#creation-parameters-4)

[Creation example](#creation-example-4)

[Footer](#footer)

[Syntax](#syntax)

[Properties](#properties)

[Example](#example)

[Buttons](#buttons)

[Copy code buttons](#copy-code-buttons)

[Multi-product message buttons](#multi-product-message-buttons)

[One-time password buttons](#one-time-password-buttons)

[Phone number buttons](#phone-number-buttons)

[Quick reply buttons](#quick-reply-buttons)

[SPM buttons](#spm-buttons)

[URL buttons](#url-buttons)

[Limited-time offer](#limited-time-offer)

[Example requests](#example-requests)

[Seasonal promotion](#seasonal-promotion)

[Order confirmation](#order-confirmation)

[Order delivery update](#order-delivery-update)

[Webhooks](#webhooks)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2IXmIq_Ltltsm0eXx1hPDw&oh=00_AfhZdme7DIoYScMoMLWHHnEw4J9jL5uBmECavOpbafdjzQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2IXmIq_Ltltsm0eXx1hPDw&oh=00_AfhLYz01NuuTaw8KceWrncbKEi2jtu3xyVIGmn8mc_gFog&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2IXmIq_Ltltsm0eXx1hPDw&oh=00_AfiL6sgcE12bJ05CDDfIxTOe0qx7VnGb2R4JwpPd5s9G3Q&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2IXmIq_Ltltsm0eXx1hPDw&oh=00_AfjBjypG0dmSRMBlvxlfZ7yHoFjuw56vdgoJBF6cMiPbWg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=2IXmIq_Ltltsm0eXx1hPDw&oh=00_Afj-WRNGuvuszw0ojQzx3N5WqdESXlsp0JvtsCwfFp2YQQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2KjYVoGX3xyyUMs-SLvBaub5CT-8dJnFvty13U9gRfAUgCcdjuKWkg3ttE7WrWMCXEo-N4rMocxna_Yz4nFpTQjR1mRQ28ohAndZ0Eff87yYTeGqbNfGfcQtqEaIw830h_lbaC-8k69Ijo8ZZayQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)