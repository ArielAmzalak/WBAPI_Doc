![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fmessages%2Fcontacts-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)[Contacts](/docs/whatsapp/cloud-api/messages/contacts-messages)

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

[Contacts messages](#contacts-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Button behavior](#button-behavior)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Contacts messages

Contacts messages allow you to send rich contact information directly to WhatsApp users, such as names, phone numbers, physical addresses, and email addresses.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441381765_2668119610015051_1596469393832242771_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=C6M1Wkw3Du0Q7kNvwEDNRb6&_nc_oc=AdkQTXzhGxEE3u8faO3nn97HqeTyv69RqTI3iEQ_rukAs_9DJIqKAM99hRDf8eu6Ulk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HVFXf10MUmVjdeoKPUZ9pg&oh=00_AfjgY_AKFnKnyygEQm63JQz_llTKVjq4wuzVvbUQu1C40A&oe=69404FF2)

When a WhatsApp user taps the message's profile arrow, it displays the contact's information in a profile view:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441391825_1516000578987481_5920245070887074504_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=B381Xx14r7cQ7kNvwEXD_8J&_nc_oc=Adk6Fmn8Q6bQwdfqSN8EXSqF5WqGtxlmkBSnu7i5yKgFEf7MwJ83diuS4EympogvUDk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HVFXf10MUmVjdeoKPUZ9pg&oh=00_AfhNvZKlYGuCfbjD7go1dh0lZ8KWJqEbPWVPM7BP0ZuDtQ&oe=69404CA7)

Each message can include information for up to 257 contacts, although it is recommended to send fewer for usability and negative feedback reasons.

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a contacts message to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "contacts",
  "contacts": [
    {
      "addresses": [
        {
          "street": "<STREET_NUMBER_AND_NAME>",
          "city": "<CITY>",
          "state": "<STATE_CODE>",
          "zip": "<ZIP_CODE>",
          "country": "<COUNTRY_NAME>",
          "country_code": "<COUNTRY_CODE>",
          "type": "<ADDRESS_TYPE>"
        }
        <!-- Additional addresses objects go here, if using -->
      ],
      "birthday": "<BIRTHDAY>",
      "emails": [
        {
          "email": "<EMAIL_ADDRESS>",
          "type": "<EMAIL_TYPE>"
        }
        <!-- Additional emails objects go here, if using -->
      ],
      "name": {
        "formatted_name": "<FULL_NAME>",
        "first_name": "<FIRST_NAME>",
        "last_name": "<LAST_NAME>",
        "middle_name": "<MIDDLE_NAME>",
        "suffix": "<SUFFIX>",
        "prefix": "<PREFIX>"
      },
      "org": {
        "company": "<COMPANY_OR_ORG_NAME>",
        "department": "<DEPARTMENT_NAME>",
        "title": "<JOB_TITLE>"
      },
      "phones": [
          "phone": "<PHONE_NUMBER>",
          "type": "<PHONE_NUMBER_TYPE>",
          "wa_id": "<WHATSAPP_USER_ID>"
        }
        <!-- Additional phones objects go here, if using -->
      ],
      "urls": [
        {
          "url": "<WEBSITE_URL>",
          "type": "<WEBSITE_TYPE>"
        }
        <!-- Additional URLs go here, if using -->
      ]
    }
  ]
}'
```

## Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<ADDRESS_TYPE>`  *String* | **Optional.**  Type of address, such as home or work. | `Home` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BIRTHDAY>`  *String* | **Optional.**  Contact's birthday. Must be in YYYY-MM-DD format. | `1999-01-23` |
| `<CITY>`  *String* | **Optional.**  City where the contact resides. | `Menlo Park` |
| `<COMPANY_OR_ORG_NAME>`  *String* | **Optional.**  Name of the company where the contact works. | `Lucky Shrub` |
| `<COUNTRY_CODE>`  *String* | **Optional.**  ISO two-letter country code. | `US` |
| `<COUNTRY_NAME>`  *String* | **Optional.**  Country name. | `United States` |
| `<DEPARTMENT_NAME>`  *String* | **Optional.**  Department within the company. | `Legal` |
| `<EMAIL_ADDRESS>`  *String* | **Optional.**  Email address of the contact. | `bjohnson@luckyshrub.com` |
| `<EMAIL_TYPE>`  *String* | **Optional.**  Type of email, such as personal or work. | `Work` |
| `<FIRST_NAME>`  *String* | **Optional.**  Contact's first name. | `Barbara` |
| `<FORMATTED_NAME>`  *String* | **Required.**  Contact's formatted name. This will appear in the message alongside the profile arrow button. | `Barbara J. Johnson` |
| `<JOB_TITLE>`  *String* | **Optional.**  Contact's job title. | `Lead Counsel` |
| `<LAST_NAME>`  *String* | **Optional.**  Contact's last name. | `Johnson` |
| `<MIDDLE_NAME>`  *String* | **Optional.**  Contact's middle name. | `Joana` |
| `<PHONE_NUMBER>`  *String* | **Optional.**  WhatsApp user phone number. | `+16505559999` |
| `<PHONE_NUMBER_TYPE>`  *String* | **Optional.**  Type of phone number. For example, cell, mobile, main, iPhone, home, work, etc. | `Home` |
| `<PREFIX>`  *String* | **Optional.**  Prefix for the contact's name, such as Mr., Ms., Dr., etc. | `Dr.` |
| `<STATE_CODE>`  *String* | **Optional.**  Two-letter state code. | `CA` |
| `<STREET_NUMBER_AND_NAME>`  *String* | **Optional.**  Street address of the contact. | `1 Lucky Shrub Way` |
| `<SUFFIX>`  *String* | **Optional.**  Suffix for the contact's name, if applicable. | `Esq.` |
| `<WEBSITE_TYPE>`  *String* | **Optional.**  Type of website. For example, company, work, personal, Facebook Page, Instagram, etc. | `Company` |
| `<WEBSITE_URL>`  *String* | **Optional.**  Website URL associated with the contact or their company. | `https://www.luckyshrub.com` |
| `<WHATSAPP_USER_ID>`  *String* | **Optional.**  WhatsApp user ID. If omitted, the message will display an Invite to WhatsApp button instead of the standard buttons.  See [Button Behavior](#button-behavior) below. | `19175559999` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |
| `<ZIP_CODE>`  *String* | **Optional.**  Postal or ZIP code. | `94025` |

## Button behavior

If you include the contact's WhatsApp ID in the message (via the `wa_id` property), the message will include a **Message** and a **Save contact** button:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441399296_815661620463689_7258599973025915055_n.png?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=B6fS_IC3vXcQ7kNvwEbsQA9&_nc_oc=AdnCXAyzRF7h0ytFX1Q_Ji5GHRCEMZGvX4EvvMqVUqpOYzlropS7dgzG5eRT5ltTZfQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HVFXf10MUmVjdeoKPUZ9pg&oh=00_AfgSwoVVCmBoPMZv5NUs0uCHLM8m4SrSptA46Cow_b9VwA&oe=6940566A)

If the WhatsApp user taps the **Message** button, it will open a new message with the contact. If the user taps the **Save contact** button, they will be given the option to save the contact as a new contact, or to update an existing contact.

If you omit the `wa_id` property, both buttons will be replaced with an **Invite to WhatsApp** button:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/441366594_855962089669296_5557083162637364924_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=-3MjX_pkMPgQ7kNvwGTghFv&_nc_oc=AdnCB9Qt8b5w8cghK0Ay5JqlDZbrsktDorAO2adxwraE3aM6MaNnXOnXvQCbCKRKLX0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HVFXf10MUmVjdeoKPUZ9pg&oh=00_AfgsO3XeCzHCjjY3rE0uhd8OU6D9vFozKvuwDoQ3XQMFIQ&oe=69407497)

## Example request

Example request to send a contacts message with two physical addresses, two email addresses, two phone numbers, and two website URLs.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "to": "+16505551234",
  "type": "contacts",
  "contacts": [
    {
      "addresses": [
        {
          "street": "1 Lucky Shrub Way",
          "city": "Menlo Park",
          "state": "CA",
          "zip": "94025",
          "country": "United States",
          "country_code": "US",
          "type": "Office"
        },
        {
          "street": "1 Hacker Way",
          "city": "Menlo Park",
          "state": "CA",
          "zip": "94025",
          "country": "United States",
          "country_code": "US",
          "type": "Pop-Up"
        }
      ],
      "birthday": "1999-01-23",
      "emails": [
        {
          "email": "bjohnson@luckyshrub.com",
          "type": "Work"
        },
        {
          "email": "bjohnson@luckyshrubplants.com",
          "type": "Work (old)"
        }
      ],
      "name": {
        "formatted_name": "Barbara J. Johnson",
        "first_name": "Barbara",
        "last_name": "Johnson",
        "middle_name": "Joana",
        "suffix": "Esq.",
        "prefix": "Dr."
      },
      "org": {
        "company": "Lucky Shrub",
        "department": "Legal",
        "title": "Lead Counsel"
      },
      "phones": [
        {
          "phone": "+16505559999",
          "type": "Landline"
        },
        {
          "phone": "+19175559999",
          "type": "Mobile",
          "wa_id": "19175559999"
        }
      ],
      "urls": [
        {
          "url": "https://www.luckyshrub.com",
          "type": "Company"
        },
        {
          "url": "https://www.facebook.com/luckyshrubplants",
          "type": "Company (FB)"
        }
      ]
    }
  ]
}'
```

## Example response

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

[Contacts messages](#contacts-messages)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Button behavior](#button-behavior)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMsD5xexkumPei_5YrO5Ww&oh=00_Afj40uW27HD-noFSGzg8KLCaDsSVSCoKVYYl5xKkOj_cQg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMsD5xexkumPei_5YrO5Ww&oh=00_AfjcxI0tHwxpprx3MIm5n5DBS95WzbSH_LzBrFo8TKnjtA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMsD5xexkumPei_5YrO5Ww&oh=00_Afi_Iqol4VmNKyd2R6WmVP5yExXu2S9ktUzOmFplhkW2qg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMsD5xexkumPei_5YrO5Ww&oh=00_AfgIq_gmGqLums_JyeEIH-dZWIFvVye9JUSJLhkhlyKeXQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMsD5xexkumPei_5YrO5Ww&oh=00_AfiVmlRB4cm2GzZtUdqV150iL_oXMCMjKxvpoCi4W1g0XA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3RGa7a6HJz6fyHZe_oOEafpsc9eyMMCjkARASH7DbUqJh_IK4MdhtGSkhleowFpVQDizK_exoM4sMIJmEXPI4b9E2FMgJF0fdvDjYOiLC89ynMv7eFeIvtv1IrDGKoubOvNy0LGKUogeqXUw6G1A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)