![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fmessages%2Fcontacts%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)[contacts](/docs/whatsapp/cloud-api/webhooks/reference/messages/contacts)

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
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)

  + [account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts)
  + [account\_review\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_review_update)
  + [account\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_update)
  + [automatic\_events](/docs/whatsapp/cloud-api/webhooks/reference/automatic_events)
  + [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update)
  + [history](/docs/whatsapp/cloud-api/webhooks/reference/history)
  + [message\_template\_components\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_components_update)
  + [message\_template\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_quality_update)
  + [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update)
  + [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)

    - [audio](/docs/whatsapp/cloud-api/webhooks/reference/messages/audio)
    - [button](/docs/whatsapp/cloud-api/webhooks/reference/messages/button)
    - [contacts](/docs/whatsapp/cloud-api/webhooks/reference/messages/contacts)
    - [document](/docs/whatsapp/cloud-api/webhooks/reference/messages/document)
    - [errors](/docs/whatsapp/cloud-api/webhooks/reference/messages/errors)
    - [group](/docs/whatsapp/cloud-api/webhooks/reference/messages/group)
    - [image](/docs/whatsapp/cloud-api/webhooks/reference/messages/image)
    - [interactive](/docs/whatsapp/cloud-api/webhooks/reference/messages/interactive)
    - [location](/docs/whatsapp/cloud-api/webhooks/reference/messages/location)
    - [order](/docs/whatsapp/cloud-api/webhooks/reference/messages/order)
    - [reaction](/docs/whatsapp/cloud-api/webhooks/reference/messages/reaction)
    - [status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)
    - [sticker](/docs/whatsapp/cloud-api/webhooks/reference/messages/sticker)
    - [system](/docs/whatsapp/cloud-api/webhooks/reference/messages/system)
    - [texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)
    - [unsupported](/docs/whatsapp/cloud-api/webhooks/reference/messages/unsupported)
    - [video](/docs/whatsapp/cloud-api/webhooks/reference/messages/video)
  + [partner\_solutions](/docs/whatsapp/cloud-api/webhooks/reference/partner_solutions)
  + [payment\_configuration\_update](/docs/whatsapp/cloud-api/webhooks/reference/payment_configuration_update)
  + [phone\_number\_name\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_name_update)
  + [phone\_number\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_quality_update)
  + [security](/docs/whatsapp/cloud-api/webhooks/reference/security)
  + [smb\_app\_state\_sync](/docs/whatsapp/cloud-api/webhooks/reference/smb_app_state_sync)
  + [smb\_message\_echoes](/docs/whatsapp/cloud-api/webhooks/reference/smb_message_echoes)
  + [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update)
  + [user\_preferences](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Contacts messages webhook reference](#contacts-messages-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Contacts `messages` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **messages** webhook for messages containing one or more contacts.

## Triggers

* A WhatsApp user sends one or more contacts to a business.
* A Whatsapp user sends one or more contacts to a business via a Click to WhatsApp ad.

## Syntax

Note that many contact object properties may be omitted if the WhatsApp user chooses not to share them, or their device prevents them from being shared.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<WHATSAPP_USER_PROFILE_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>",
                "identity_key_hash": "<IDENTITY_KEY_HASH>" <!-- only included if identity change check enabled -->
              }
            ],
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "contacts",
                "contacts": [
                  {
                    "addresses": [
                      {
                        "city": "<CONTACT_CITY>",
                        "country": "<CONTACT_COUNTRY>",
                        "country_code": "<CONTACT_COUNTRY_CODE>",
                        "state": "<CONTACT_STATE>",
                        "street": "<CONTACT_STREET>",
                        "type": "<CONTACT_ADDRESS_TYPE>",
                        "zip": "<CONTACT_ZIP>"
                      }
                    ],
                    "birthday": "<CONTACT_BIRTHDAY>",
                    "emails": [
                      {
                        "email": "<CONTACT_EMAIL>",
                        "type": "<CONTACT_EMAIL_TYPE>"
                      }
                    ],
                    "name": {
                      "formatted_name": "<CONTACT_FORMATTED_NAME>",
                      "first_name": "<CONTACT_FIRST_NAME>",
                      "last_name": "<CONTACT_LAST_NAME>",
                      "middle_name": "<CONTACT_MIDDLE_NAME>",
                      "suffix": "<CONTACT_NAME_SUFFIX>",
                      "prefix": "<CONTACT_NAME_PREFIX>"
                    },
                    "org": {
                      "company": "<CONTACT_ORG_COMPANY>",
                      "department": "<CONTACT_ORG_DEPARTMENT>",
                      "title": "<CONTACT_ORG_TITLE>"
                    },
                    "phones": [
                      {
                        "phone": "<CONTACT_PHONE>",
                        "wa_id": "<CONTACT_WHATSAPP_PHONE_NUMBER>",
                        "type": "<CONTACT_PHONE_TYPE>"
                      }
                    ],
                    "urls": [
                      {
                        "url": "<CONTACT_URL>",
                        "type": "<CONTACT_URL_TYPE>"
                      }
                    ]
                  }
                ],

                <!-- only included if message sent via a Click to WhatsApp ad -->
                "referral": {
                  "source_url": "<AD_URL>",
                  "source_id": "<AD_ID>",
                  "source_type": "ad",
                  "body": "<AD_PRIMARY_TEXT>",
                  "headline": "<AD_HEADLINE>",
                  "media_type": "<AD_MEDIA_TYPE>",
                  "image_url": "<AD_IMAGE_URL>",
                  "video_url": "<AD_VIDEO_URL>",
                  "thumbnail_url": "<AD_VIDEO_THUMBNAIL>",
                  "ctwa_clid": "<AD_CLICK_ID>",
                  "welcome_message": {
                    "text": "<AD_GREETING_TEXT>"
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

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<AD_CLICK_ID>`  *String* | Click to WhatsApp ad click ID.  The `ctwa_clid` property is omitted entirely for messages originating from an ad in WhatsApp Status ([WhatsApp Status ad placements](https://www.facebook.com/business/help/1074444721456755)). | `Aff-n8ZTODiE79d22KtAwQKj9e_mIEOOj27vDVwFjN80dp4_0NiNhEgpGo0AHemvuSoifXaytfTzcchptiErTKCqTrJ5nW1h7IHYeYymGb5K5J5iTROpBhWAGaIAeUzHL50` |
| `<AD_GREETING_TEXT>`  *String* | Click to WhatsApp ad greeting text. | `Hi there! Let us know how we can help!` |
| `<AD_HEADLINE>`  *String* | Click to WhatsApp ad headline. | `Chat with us` |
| `<AD_ID>`  *String* | Click to WhatsApp ad ID. | `120226305854810726` |
| `<AD_IMAGE_URL>`  *String* | Click to WhatsApp ad image URL. Only included if the ad is an image ad. | `https://scontent.xx.fbcdn.net/v/t45.1...` |
| `<AD_MEDIA_TYPE>`  *String* | Click to WhatsApp ad media type. Values can be:  `image` — Indicates an image ad.  `video` — Indicates a video ad. | `image` |
| `<AD_PRIMARY_TEXT>`  *String* | Click to WhatsApp ad primary text. | `Summer succulents are here!` |
| `<AD_URL>`  *String* | Click to WhatsApp ad URL. | `https://fb.me/3cr4Wqqkv` |
| `<AD_VIDEO_THUMBNAIL>`  *String* | Click to WhatsApp ad video thumbnail URL. Only included if ad is a video ad. | `https://scontent.xx.fbcdn.net/v/t45.3...` |
| `<AD_VIDEO_URL>`  *String* | Click to WhatsApp ad video URL. Only included if ad is a video ad. | `https://scontent.xx.fbcdn.net/v/t45.2...` |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<CONTACT_ADDRESS_TYPE>`  *String* | Type of address, such as home or work. | `Home` |
| `<CONTACT_BIRTHDAY>`  *String* | Contact birthday. | `1999-01-23` |
| `<CONTACT_CITY>`  *String* | City mentioned in the contact address. | `Menlo Park` |
| `<CONTACT_COUNTRY_CODE>`  *String* | ISO country code on the contact address. | `US` |
| `<CONTACT_COUNTRY>`  *String* | Country mentioned in the contact address. | `United States` |
| `<CONTACT_EMAIL_TYPE>`  *String* | Type of email, such as personal or work. | `Personal` |
| `<CONTACT_EMAIL>`  *String* | Email address of the contact. | `bjohson@socialtsunami.com` |
| `<CONTACT_FIRST_NAME>`  *String* | Contact's first name. | `Barbara` |
| `<CONTACT_FORMATTED_NAME>`  *String* | Contact's formatted name. | `Barbara J. Johnson` |
| `<CONTACT_LAST_NAME>`  *String* | Contact's last name. | `Johnson` |
| `<CONTACT_MIDDLE_NAME>`  *String* | Contact's middle name. | `Joana` |
| `<CONTACT_NAME_PREFIX>`  *String* | Contact's name prefix. | `Dr.` |
| `<CONTACT_NAME_SUFFIX>`  *String* | Contact's name suffix. | `Esq.` |
| `<CONTACT_ORG_COMPANY>`  *String* | Name of the company where the contact works. | `Social Tsunami` |
| `<CONTACT_ORG_DEPARTMENT>`  *String* | Name of the department where the contact works. | `Engineering` |
| `<CONTACT_ORG_TITLE>`  *String* | Contact's job title. | `Software Engineer` |
| `<CONTACT_PHONE_TYPE>`  *String* | Type of phone number. For example, cell, mobile, main, iPhone, home, work, etc. | `CELL` |
| `<CONTACT_PHONE>`  *String* | Contact's phone number. | `+14125550829` |
| `<CONTACT_STATE>`  *String* | State mentioned in the contact address. | `CA` |
| `<CONTACT_STREET>`  *String* | Street mentioned in the contact address. | `1 Hacker Way` |
| `<CONTACT_URL_TYPE>`  *String* | Type of website. For example, company, work, personal, Facebook Page, Instagram, etc. | `Company` |
| `<CONTACT_URL>`  *String* | Website URL associated with the contact or their company. | `socialtsunami.com` |
| `<CONTACT_WHATSAPP_PHONE_NUMBER>`  *String* | Contact's WhatsApp number. | `14125550829` |
| `<CONTACT_ZIP>`  *String* | Zip code in the contact address. | `94025` |
| `<IDENTITY_KEY_HASH>`  *String* | Identity key hash. Only included if you have enabled the [identity change check](/docs/whatsapp/cloud-api/reference/phone-numbers#identity-change-check) feature. | `DF2lS5v2W6x=` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *String* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |
| `<WHATSAPP_MESSAGE_ID>`  *String* | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user ID. Note that a WhatsApp user's ID and phone number may not always match. | `16505551234` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | WhatsApp user phone number. This is the same value returned by the API as the `input` value when sending a message to a WhatsApp user. Note that a WhatsApp user's phone number and ID may not always match. | `+16505551234` |
| `<WHATSAPP_USER_PROFILE_NAME>`  *String* | WhatsApp user's name as it appears in their profile in the WhatsApp client. | `Sheena Nelson` |

## Example

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
                  "name": "Sheena Nelson"
                },
                "wa_id": "16505551234"
              }
            ],
            "messages": [
              {
                "from": "16505551234",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTRBNjU5OUFFRTAzODEwMTQ0RgA=",
                "timestamp": "1744344496",
                "type": "contacts",
                "contacts": [
                  {
                    "name": {
                      "first_name": "Barbara",
                      "last_name": "Johnson",
                      "formatted_name": "Barbara J. Johnson"
                    },
                    "org": {
                      "company": "Social Tsunami"
                    },
                    "phones": [
                      {
                        "phone": "+1 (415) 555-0829",
                        "wa_id": "14125550829",
                        "type": "MOBILE"
                      }
                    ]
                  }
                ]
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

[Contacts messages webhook reference](#contacts-messages-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=QQ1yGh-tc-MWFSMDZEIkWQ&oh=00_AfilUP0OCZmFsynrJI-bFfElhrIJxpFmGN_F-BCJ4_2Jvg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=QQ1yGh-tc-MWFSMDZEIkWQ&oh=00_Afg5qGGcQoAQmEy6YGSl3x0k4HWkpN2XkHkz3yA4VSppOA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=QQ1yGh-tc-MWFSMDZEIkWQ&oh=00_Afhsr6wZ5ipklPy5eJ4N9VGcy1NMIXZLe7B49GOrl6qDBw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=QQ1yGh-tc-MWFSMDZEIkWQ&oh=00_AfgrD5gMbWy1X77bzK76MGgiekpYzo15vECkc0jl5lqv4A&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=QQ1yGh-tc-MWFSMDZEIkWQ&oh=00_AfixXc79STpXD935XJqCcPdLKeyDyzILf0UuoKMP0AvszQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1lqSpxxYSaxlI-5co-30w8PdiEgFZ9BDH1g-nPlTwt4sO2A-pirElWLfpQ6ykoGc7EnUjy1ltV2Fh1WgDqTQucNpDF2DoOGLuvt3mO2zlL_MJ_kDd7xAXnF1boYqOjbIZHvQyFMG0GESMsxjGioA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)