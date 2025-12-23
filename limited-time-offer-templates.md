![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Flimited-time-offer-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Modelos de oferta por tempo limitado](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates)

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

[Limited-time offer templates](#limited-time-offer-templates)

[Limitations](#limitations)

[Creating limited-time offer templates](#creating-limited-time-offer-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Offer expiration details](#offer-expiration-details)

[Example request](#example-request)

[Example response](#example-response)

[Sending limited-time offer templates](#sending-limited-time-offer-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 4 de nov
Atualização em Português (Brasil): 1 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# Limited-time offer templates

This document describes limited-time offer templates and how to use them.

Limited-time offer templates allow you to display expiration dates and running countdown timers for offer codes in template messages, making it easy for you to communicate time-bound offers and drive customer engagement.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/385485492_1044097420371007_6435130166952753459_n.png?stp=dst-webp&_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=brr9Mr1oS58Q7kNvwHJnvW1&_nc_oc=Adn2mdv5yUNS9k05s0rVchcg_g_RjLlwRiQ2pPuVXc-B5OopBHWVOJocHMgJUZKAEU8&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Bx9dzIcMCJ4WuC83hPUH5w&oh=00_AfguEcKpjKujpMD6r_lpKBKEGigses2lqYlIDaFK75U_-Q&oe=6940543F)

## Limitations

* Only templates categorized as `MARKETING` are supported.
* Footer components are not supported.
* Users who view a limited-time offer template message using that WhatsApp web app or desktop app will not see the offer, but will instead see a message indicating that they have received a message but that it's not supported in the client they are using.

## Creating limited-time offer templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates/#Creating) endpoint to create a limited-time offer template.

### Request syntax

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
        "type": "header",
        "format": "<HEADER_FORMAT>",
        "example": {
          "header_handle": [
            "<HEADER_ASSET_HANDLE>"
          ]
        }
      },
      {
        "type": "limited_time_offer",
        "limited_time_offer": {
          "text": "<LIMITED_TIME_OFFER_TEXT>",
          "has_expiration": <HAS_EXPIRATION>
        }
      },
      {
        "type": "body",
        "text": "<BODY_TEXT>",
        "example": {
          "body_text": [<BODY_TEXT_VARIABLE_EXAMPLES>]
        }
      },
      {
        "type": "buttons",
        "buttons": [
          {
            "type": "copy_code",
            "example": "<OFFER_CODE_EXAMPLE>"
          },
          {
            "type": "url",
            "text": "<URL_BUTTON_TEXT>",
            "url": "<URL_BUTTON_URL>",
            "example": [
              "<URL_EXAMPLE_WITH_VARIABLE_EXAMPLE>"
            ]
          }
        ]
      }
    ]
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BODY_TEXT>`  *String* | **Required.**   Body component text. Supports variables.   Maximum 600 characters. | `Good news, {{1}}! Use code {{2}} to get 25% off all Caribbean Destination packages!` |
| `<BODY_TEXT_VARIABLE_EXAMPLES>`  *Array of strings* | **Required if body component text uses variables.**   Array of example variable strings.   Must supply examples for all placeholders in `<BODY_TEXT>` string.   No maximum, but counts against `<BODY_TEXT>` maximum. | `["Pablo","CARIBE25"]` |
| `<HAS_EXPIRATION>`  *Boolean* | **Optional.**   Set to `true` to have the [offer expiration details](#offer-expiration-details) appear in the delivered message. | `true` |
| `<HEADER_ASSET_HANDLE>`  *Media asset handle* | **Required if using an image or video header.**   Uploaded media asset handle. Use the [Resumable Upload API](/docs/graph-api/guides/upload) to generate an asset handle. | `4::aW...` |
| `<HEADER_FORMAT>`  *Enum* | **Required if using a header.**   Can be `IMAGE`, or `VIDEO`. | `IMAGE` |
| `<LIMITED_TIME_OFFER_TEXT>`  *String* | **Required.**   Offer details text.   Maximum 16 characters. | `Expiring offer!` |
| `<OFFER_CODE_EXAMPLE>`  *String* | **Required.**   Example offer code.   Maximum 15 characters. | `CARIBE25` |
| `<TEMPLATE_LANGUAGE>`  *Enum* | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**   Template name.   Maximum 512 characters. | `limited_time_offer_caribbean_pkg_2023` |
| `<URL_BUTTON_TEXT>`  *String* | **Required.**   [URL button](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) label text. Supports 1 variable.   25 characters maximum. | `Book now!` |
| `<URL_BUTTON_URL>`  *String* | **Required.**   URL of website that loads in the device's default mobile web browser when the [URL button](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) is tapped by the WhatsApp user.   Supports 1 variable appended to the end of the URL string.   Maximum 2000 characters. | `https://awesomedestinations.com/offers?code={{1}}` |
| `<URL_EXAMPLE_WITH_VARIABLE_EXAMPLE>`  *String* | **Required if URL uses a variable.**   Example URL with example variable appended to the end.   No maximum, but value counts against `<URL_BUTTON_URL>` maximum. | `https://awesomedestinations.com/offers?ref=n3mtql` |

### Offer expiration details

The delivered message can display an offer expiration details section with a heading, an optional expiration timer, and the offer code itself.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/384988489_703197894993408_6289249753669812858_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=4qcc3qwdBDUQ7kNvwGcaYNp&_nc_oc=Adkg-dHXPVc1IV1CmWSW8TpmhzDpJVAXR1gqg4sjp03tQL3QEKUhDQv2N6oM4hVM_pw&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Bx9dzIcMCJ4WuC83hPUH5w&oh=00_Afhom7VVJGLHGMhZNrX_pnDu2Fn3VOVlk-moEOHR1s6vBg&oe=694060E1)

The expiration timer is a text string that is not customizable, but it will change to red text if the message is viewed and the offer code is expiring within the next hour. (You include the actual offer code and its expiration timestamp when you send the template in a template message.)

### Example request

This is an example request to create a limited-time offer template that uses:

* an image header component
* body text component with variables
* the limited time offer component
* a copy code button
* a button URL with a variable

```
curl 'https://graph.facebook.com/v17.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "limited_time_offer_caribbean_pkg_2023",
  "language": "en_US",
  "category": "marketing",
  "components": [
    {
      "type": "header",
      "format": "image",
      "example": {
        "header_handle": [
          "4::aW..."
        ]
      }
    },
    {
      "type": "limited_time_offer",
      "limited_time_offer": {
        "text": "Expiring offer!",
        "has_expiration": true
      }
    },
    {
      "type": "body",
      "text": "Good news, {{1}}! Use code {{2}} to get 25% off all Caribbean Destination packages!",
      "example": {
        "body_text": [
          [
            "Pablo",
            "CARIBE25"
          ]
        ]
      }
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "copy_code",
          "example": "CARIBE25"
        },
        {
          "type": "url",
          "text": "Book now!",
          "url": "https://awesomedestinations.com/offers?code={{1}}",
          "example": [
            "https://awesomedestinations.com/offers?ref=n3mtql"
          ]
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "id": "546151681022936",
  "status": "PENDING",
  "category": "MARKETING"
}
```

## Sending limited-time offer templates

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an approved limited-time offer template in a template message.

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<CUSTOMER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<TEMPLATE_LANGUAGE_CODE>"
      },
      "components": [
        {
          "type": "header",
          "parameters": [
            {
              "type": "<HEADER_TYPE>",
              "<HEADER_TYPE>": {
                "id": "<HEADER_ASSET_ID>"
              }
            }
          ]
        },
        {
          "type": "body",
          "parameters": [
            <BODY_VARIABLES>
          ]
        },
        {
          "type": "limited_time_offer",
          "parameters": [
            {
              "type": "limited_time_offer",
              "limited_time_offer": {
                "expiration_time_ms": <EXPIRATION_TIME>
              }
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "copy_code",
          "index": 0,
          "parameters": [
            {
              "type": "coupon_code",
              "coupon_code": "<OFFER_CODE>"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": <URL_BUTTON_INDEX>,
          "parameters": [
            {
              "type": "text",
              "text": "<URL_VARIABLE>"
            }
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<BODY_VARIABLES>`  *Array of objects* | **Required if template body text uses variables.**   Body text variable values. Define each variable as an individual object. | `{"type":"text","text":"Pablo"},{"type":"text","text":"CARIBE25"}` |
| `<CUSTOMER_PHONE_NUMBER>`  *String* | **Required.**   Phone number of customer who the template message should be sent to. | `+16505555555` |
| `<EXPIRATION_TIME>`  *Unix timestamp* | **Required.**   Offer code expiration time as a UNIX timestamp in milliseconds. | `1698562800000` |
| `<HEADER_ASSET_ID>`  *Media asset ID* | **Required.**   Uploaded media asset ID. Use the [/PHONE\_NUMBER\_ID/media](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to generate an ID. | `1602186516975000` |
| `<HEADER_TYPE>`  *String* | **Required.**   Header type used by the template. Values can be `image` or `video`. | `image` |
| `<OFFER_CODE>`  *String* | **Required if template uses a copy code button.**   Offer code.   Maximum 15 characters. | `CARIBE25` |
| `<TEMPLATE_LANGUAGE_CODE>`  *Enum* | **Required.**   The template's [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**   The template's name. | `limited_time_offer_caribbean_pkg_2023` |
| `<URL_BUTTON_INDEX>`  *Integer* | **Required.**   URL button index. If the template uses a copy code button, value must be `1`.   If the template does not use a copy code button, the value must be `0`. | `1` |
| `<URL_VARIABLE>`  *String* | **Required if URL uses a variable.**   URL variable value.   No maximum but value counts against URL string maximum of 2000 characters. | `n3mtql` |

### Example request

Example request to send a limited-time offer template that uses:

* an image header
* body text variables
* the offer expiration details
* a copy code button
* a URL button with a variable

```
curl 'https://graph.facebook.com/v17.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16505555555",
  "type": "template",
  "template": {
    "name": "limited_time_offer_caribbean_pkg_2023",
    "language": {
      "code": "en_US"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "image",
            "image": {
              "id": "1602186516975000"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "Pablo"
          },
          {
            "type": "text",
            "text": "CARIBE25"
          }
        ]
      },
      {
        "type": "limited_time_offer",
        "parameters": [
          {
            "type": "limited_time_offer",
            "limited_time_offer": {
              "expiration_time_ms": 1209600000
            }
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "copy_code",
        "index": 0,
        "parameters": [
          {
            "type": "coupon_code",
            "coupon_code": "CARIBE25"
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
            "text": "n3mtql"
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
      "input": "16505555555",
      "wa_id": "16505555555"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDUwNzY1MjAVAgARGBI5QTNDQTVCM0Q0Q0Q2RTY3RTcA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Limited-time offer templates](#limited-time-offer-templates)

[Limitations](#limitations)

[Creating limited-time offer templates](#creating-limited-time-offer-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Offer expiration details](#offer-expiration-details)

[Example request](#example-request)

[Example response](#example-response)

[Sending limited-time offer templates](#sending-limited-time-offer-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=unMD0p_YkhKX4oQAaO7c7A&oh=00_AfinFCmyHVUG7SAaverX4V9Ul8EpApu_eg2karm4aXdRGw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=unMD0p_YkhKX4oQAaO7c7A&oh=00_AfjCLjsNfUbSmtz3azu7kKrMOEvCrIuZZY9ArdllQfUQvQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=unMD0p_YkhKX4oQAaO7c7A&oh=00_AfjRABCiHTOGkZspbuxbNWmhOlt1Ll_G9AlbIbIhrj-fig&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=unMD0p_YkhKX4oQAaO7c7A&oh=00_AfjqvAc2XRBYMXQ0y6pX4scILJpnz1FDDpWGNgsWcX9ciQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=unMD0p_YkhKX4oQAaO7c7A&oh=00_AfjlqMi9Jcl-Twtv2Ucd72ww7ZAZLezp-DlmngcnZgZcDg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0RxTFKcACQAdcKb21zRd-2INEkbfkCVnFJlMkN4oO--SoOGnCDB7dotIyGH2fEw1aqk9-JL_AvjeJDvtdlfqsjGzVZ6HAM8U20tMjNUQmK5gYZrvblUPf_WvNMKn7kB9lSVHQ1JLVBifaCclGX2w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)