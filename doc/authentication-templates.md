![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)

    - [Preenchimento automático com um toque](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates)
    - [Zero-Tap](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates)
    - [Copy Code](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates)
    - [Authenticating Users](/docs/whatsapp/business-management-api/authentication-templates/authentication-best-practices)
    - [Bulk management](/docs/whatsapp/business-management-api/authentication-templates/bulk-management)
    - [Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals)
    - [Template preview](/docs/whatsapp/business-management-api/authentication-templates/template-preview)
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

[Authentication templates](#authentication-templates)

[Linked device security](#linked-device-security)

[One-tap autofill authentication templates](#one-tap-autofill-authentication-templates)

[Copy code authentication templates](#copy-code-authentication-templates)

[Zero-tap authentication templates](#zero-tap-authentication-templates)

[Best practices](#best-practices)

[Customizing time-to-live](#customizing-time-to-live)

[Template previews](#template-previews)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Bulk management](#bulk-management)

[Request syntax](#request-syntax-2)

[Post Body](#post-body)

[Properties](#properties)

[Example copy code request](#example-copy-code-request)

[Example one-tap autofill request](#example-one-tap-autofill-request)

[Example response](#example-response-2)

[Sample app](#sample-app)

[Learn more](#learn-more)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/authentication-templates/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 14 de nov
Atualização em Português (Brasil): 6 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# Authentication templates

If your mobile app offers users the option to receive one-time passwords or verification codes via WhatsApp, you must use an authentication template.

Authentication templates consist of:

* Fixed, non-customizable **preset text**: *<VERIFICATION\_CODE> is your verification code.*
* An optional **security disclaimer**: *For your security, do not share this code.*
* An optional **expiration warning**: *This code expires in <NUM\_MINUTES> minutes.*
* Either a **one-tap autofill** button, a **copy code** button, or no button at all if using [zero-tap](#zero-tap-authentication-templates).

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/391704029_868992307740251_3073203578067340408_n.png?stp=dst-webp&_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=SavFP4S9_SUQ7kNvwGS6Zkc&_nc_oc=AdkiFBH2UKblOWkJNlNkomLymhJDU08YfVVzclTEGUIwe-5_AkhxLNr8HEWc8_AsiME&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_Afh7cOGEEkjIObMk7CLLzEAKL2KQ9Y7yu-cCsfPHrdMedg&oe=6940765E)

One-tap autofill buttons are the preferred solution as they offer the best user experience. However, one-tap autofill buttons are currently only supported on Android and require additional changes to your app's code.

## Linked device security

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458481136_1204876024064039_8216873060873003926_n.png?stp=dst-webp&_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=E6hGLCS3OqEQ7kNvwF3N6MG&_nc_oc=Adnmd4YRBBI3gSZjOsp5tzesWsIG3EsWw64FFMM3Efbpwls_7MhVAl4G0M3nSMR81hE&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_Afhro2aWgq2LnuiX3_gQvb5wJFA_dnWv6z4oy8Pw0A16jA&oe=69404126)

Authentication templates now feature linked device security. This means that authentication messages are only delivered to a user's primary WhatsApp device.

Authentication messages that are sent to a user's linked devices are masked with a prompt instructing the user to view the message on their primary device.

This feature is enabled by default and does not require code changes. It cannot be configured or customized. Only available on Cloud API.

## One-tap autofill authentication templates

Authentication templates include a one-tap autofill button.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/393789031_872892117564016_6400271480127333734_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=yNIJACo9YGIQ7kNvwF6tEcq&_nc_oc=AdlQaRCrqti9epyKxk0rpgrfWsi0-gD2Y4GbVujDPlHSB8sTmvoc1FliKmay7rmbq2c&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_Afj5aRZv8QzTcLAKC4DL0gW950jNplBa8c_0bWTN0yfT3A&oe=69405428)

When a WhatsApp user taps the autofill button, the WhatsApp client triggers an activity which opens your app and delivers it the password or code.

See [One-Tap Autofill Authentication Templates](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates) to learn how to use them.

## Copy code authentication templates

Copy code authentication templates allow you to send a one-time password or code along with a copy code button to your users.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/391709210_6733218460105388_4204949555628827374_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eIv_Q6QSKYQ7kNvwH592Hn&_nc_oc=AdlH2UGFwOsKMWSP4m0BUEtss0kVbwP4HTbDN5umGQKd4HTussdCZwFPLN1ObynXOpQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfinP9kbcSSQ266D97gDq5Io6ImPoZfBLRBprqKjxw2Pmw&oe=6940627D)

When a WhatsApp user taps the copy code button, the WhatsApp client copies the password or code to the device's clipboard. The user can then switch to your app and paste the password or code into your app.

See [Copy Code Authentication Templates](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates) to learn how to use them.

## Zero-tap authentication templates

Zero-tap authentication templates allow your users to receive one-time passwords or codes via WhatsApp without having to leave your app.

When a user in your app requests a password or code and you deliver it using a zero-tap authentication template, the WhatsApp client broadcasts the included password or code, which your app can then capture with a broadcast receiver.

See [Zero-Tap Authentication Templates](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates) to learn how to use them.

## Best practices

* Confirm the user's WhatsApp phone number before sending the one-time password or code to that number.
* Make it clear to your user that the password or code will be delivered to their WhatsApp phone number, especially if you offer multiple ways for the user to receive password or code delivery. See [Getting Opt-In](/docs/whatsapp/overview/getting-opt-in) for additional tips.
* When the user pastes the password or code into your app, or your app receives it as part of the one-tap autofill button flow, make it clear to the user that your app has captured it.

See also [Best practices for authenticating users via WhatsApp](/docs/whatsapp/business-management-api/authentication-templates/authentication-best-practices).

## Customizing time-to-live

See [Time-to-live](/docs/whatsapp/business-management-api/time-to-live).

## Template previews

You can generate previews of authentication template text in various languages that include or exclude the security recommendation string and code expiration string using the [**GET /<WABA\_ID>/message\_template\_previews**](/docs/graph-api/reference/whats-app-business-account/message_template_previews/#Reading) endpoint.

### Request syntax

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_template_previews
  ?category=AUTHENTICATION,
  &language=<LANGUAGE>, // Optional
  &add_security_recommendation=<ADD_SECURITY_RECOMMENDATION>, // Optional
  &code_expiration_minutes=<CODE_EXPIRATION_MINUTES>, // Optional
  &button_types=<BUTTON_TYPES> // Optional
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<LANGUAGE>`  *Comma-separated list* | **Optional.**   Comma-separated list of [language codes](/docs/whatsapp/business-management-api/message-templates/supported-languages) of language versions you want returned.   If omitted, versions of all supported languages will be returned. | `en_US,es_ES` |
| `<ADD_SECURITY_RECOMMENDATION>`  *Boolean* | **Optional.**   Set to `true` if you want the security recommendation body string included in the response.   If omitted, the security recommendation string will not be included. | `true` |
| `<CODE_EXPIRATION_MINUTES>`  *Int64* | **Optional.**   Set to an integer if you want the code expiration footer string included in the response.   If omitted, the code expiration footer string will not be included.   Value indicates number of minutes until code expires.  Minimum `1`, maximum `90`. | `10` |
| `<BUTTON_TYPES>`  *Comma-separated list of strings* | **Required.**   Comma-separated list of strings indicating button type.   If included, the response will include the button text for each button in the response.   For authentication templates, this value must be `OTP`. | `OTP` |

### Example request

```
curl 'https://graph.facebook.com/v17.0/102290129340398/message_template_previews?category=AUTHENTICATION&languages=en_US,es_ES&add_security_recommendation=true&code_expiration_minutes=10&button_types=OTP' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [
    {
      "body": "*{{1}}* is your verification code. For your security, do not share this code.",
      "buttons": [
        {
          "autofill_text": "Autofill",
          "text": "Copy code"
        }
      ],
      "footer": "This code expires in 10 minutes.",
      "language": "en_US"
    },
    {
      "body": "Tu código de verificación es *{{1}}*. Por tu seguridad, no lo compartas.",
      "buttons": [
        {
          "autofill_text": "Autocompletar",
          "text": "Copiar código"
        }
      ],
      "footer": "Este código caduca en 10 minutos.",
      "language": "es_ES"
    }
  ]
}
```

## Bulk management

Use the [**POST /<WABA\_ID>/upsert\_message\_templates**](/docs/graph-api/reference/whats-app-business-account/upsert_message_templates/#Creating) endpoint to bulk update or create authentication templates in multiple languages that include or exclude the optional security and expiration warnings.

If a template already exists with a matching name and language, the template will be updated with the contents of the request, otherwise, a new template will be created.

### Request syntax

```
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/upsert_message_templates
```

### Post Body

```
{
  "name": "<NAME>",
  "languages": [<LANGUAGES>],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": <ADD_SECURITY_RECOMMENDATION> // Optional
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": <CODE_EXPIRATION_MINUTES> // Optional
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "<OTP_TYPE>",
          "supported_apps": [
            {
              "package_name": "<PACKAGE_NAME>", // One-tap and zero-tap buttons only
              "signature_hash": "<SIGNATURE_HASH>" // One-tap and zero-tap buttons only
            }
          ]
        }
      ]
    }
  ]
}
```

### Properties

All template creation properties are supported, with these exceptions:

* The `language` property is not supported. Instead, use `languages` and set its value to an array of [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages) strings. For example: `["en_US","es_ES","fr"]`.
* The `text` property is not supported.
* The `autofill_text` property is not supported.

### Example copy code request

This example creates three authentication templates in English, Spanish, and French, with copy code buttons. Each template is named "authentication\_code\_copy\_code\_button" and includes the security recommendation and expiration time.

```
curl 'https://graph.facebook.com/v17.0/102290129340398/upsert_message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_copy_code_button",
  "languages": ["en_US","es_ES","fr"],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": true
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": 10
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "COPY_CODE"
        }
      ]
    }
  ]
}'
```

### Example one-tap autofill request

This example (1) updates an existing template with the name "authentication\_code\_autofill\_button" and language "en\_US", and (2) creates two new authentication templates in Spanish and French with one-tap autofill buttons. Both newly created templates are named "authentication\_code\_autofill\_button" and include the security recommendation and expiration time.

```
curl 'https://graph.facebook.com/v17.0/102290129340398/upsert_message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_autofill_button",
  "languages": ["en_US","es_ES","fr"],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": true
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": 15
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "ONE_TAP",
          "supported_apps": [
            {
              "package_name": "com.example.luckyshrub",
              "signature_hash": "K8a/AINcGX7"
            }
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
  "data": [
    {
      "id": "954638012257287",
      "status": "APPROVED",
      "language": "en_US"
    },
    {
      "id": "969725527415202",
      "status": "APPROVED",
      "language": "es_ES"
    },
    {
      "id": "969725530748535",
      "status": "APPROVED",
      "language": "fr"
    }
  ]
}
```

## Sample app

See our [WhatsApp One-Time Password (OTP) Sample App](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-OTP-Sample-App&h=AT2eqNDKq4w_BaFt9FcL_yCjG7439ZW5TdtI8GWKE2NyEvGNRiFDF4szETep6f0HSYO31eqzRG4hkVTmKUsIXHrqA3Xr0Buxcif2IwPhgnaMDwVESqYbxc3eO7gGJ6ijifg7SGOvigEFcxgKLScO3Q) for Android on Github. The sample app demonstrates how to send and receive OTP passwords and codes via the API, how to integrate the one-tap autofill and copy code buttons, how to create a template, and how to spin up a sample server.

## Learn more

* [Official Business Account](/docs/whatsapp/official-business-accounts) — You may wish to request Official Business Account status to build trust with your users, which will reduce the likelihood that they dismiss or ignore your messages.
* [Status messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks — We recommend that you subscribe to the messages webhook field so you can be notified when a user receives and reads your authentication template with an OTP button.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Authentication templates](#authentication-templates)

[Linked device security](#linked-device-security)

[One-tap autofill authentication templates](#one-tap-autofill-authentication-templates)

[Copy code authentication templates](#copy-code-authentication-templates)

[Zero-tap authentication templates](#zero-tap-authentication-templates)

[Best practices](#best-practices)

[Customizing time-to-live](#customizing-time-to-live)

[Template previews](#template-previews)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Bulk management](#bulk-management)

[Request syntax](#request-syntax-2)

[Post Body](#post-body)

[Properties](#properties)

[Example copy code request](#example-copy-code-request)

[Example one-tap autofill request](#example-one-tap-autofill-request)

[Example response](#example-response-2)

[Sample app](#sample-app)

[Learn more](#learn-more)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfhQf10YFSyW-fKGfdDfNoY8ywUmwCW1Ga9Fvq021oov2Q&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfgpZY1Qg_3Y12xVE8YNbWcGYV8K7K6OT7rsaCTPRF1SZw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfjIp0M44-JyNDmvYNOHh_A6Y2Gku4GnyEHR8W2HCm5Gew&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT11f6lthRHQu20q3fhn5pmoggGZEQxqkFgua4xo20sCtGgd1HOsXxN7K4ndjyGNB3xFrg3xxyU0YkeGvqiOSyxMJgyKxsQEnh0RahRig3m2LZ3qxU85qMjES8Rzq50KQgH7_XgFtA_iYJlaqfz75g)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfgDqGgOFB6yo-ty-QVBLzkgSV639nt5JYMsYYDtVsLcBA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2Ya5GYlgeXsGXWCNGWEuGxeHFQ58PjfhkSqZD3UQ_gAn2MoRQGLjdvgqRwEdB5qm7y11-mFetvoLS7nPy_L45mtu3ACz_rXLDaIMCoVLx4cAIKy2TRFTLU7ex3Gpl4q-eHCkD280G8Nsy5eY4ccg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfjCKet69jkvHgPLvAl_hCjkUuZo5PS4AwvMMZeGfAEiaQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2lIRK7tm0POBOJGURCjIhNQYv7K2VDvnW6y--BOt1l9YsdMrsF1l_YelWdM284t7NUiAubtXWVDeqm394nv1kUq6ba2JT1rQ0GKTfdWOzdIUWBfV7mcaPjo6zdDdSDT2DONvQYUuaDAvoZdu9ZJQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfggfIsOnxM3j0K7KScUlP0gx_qKy45GIs1XbnF2j8HCqA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3w3e3Q-pvglNakZjOz5IKut43fBzWO8FUhCFcaWSp5dMFhu1SU64fNQTLK-I5qp4sZbbtx_afRx2znmmGs4ZOGMYjPHveAnrzDs34AloC4UEYKUm_KWZ1iEbFymUKXWyYiD7Gt37hPgLWtIEW96HyzUHilTAmrd4I)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0Hq4u3j1yvRENDICtU8GmbWz2IKMYE55NoOvV8_XdxZiBk6CFlF8R9Pf_UfrXa3GnZTb0ftXP2wsdHVhYcis3hXhw2wtFwQcpDVCIQkzp3XXEyMjr9nZULn4QHNRsN01bUWWU89QxjIafkQJCEqw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0wDhpJUFo3LjOi7RUuC_L8Xv3iH6zCCXlmVCFzfcnp44BvAJZ-LPopGAASRYTvi0zFqndviLJwmvlT_e4l7uAIaG7602iNkxfaueRbjtLHnXg_xQGz3Q0l0l0jdzsV_0_C9ap_lk6mNw4WV7yMqA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfhQJus4_Kl1uRJDeNNdB2gpenrEWz2bXFO0aOospZSGCw&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfhEDfLS_PxVB4t8RDfvhk3YuN4z16Iq0V0SAL6T_8J2Tw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2U8XUqDL3-AgTYHk4MbIc7Oi91X07evBGaUXH5hF8sG2o4CS2iNkoiCTu3hE0QtErO2mvejjLrGz_6ggsUx4pX9_g8UMu7OYMEtdYPafh8xIjIUzRu3PNg6dSMocbMICnCzq7g-QlWaMeQjhFBUQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_Afh0gdEAmp-y3tDQYplmRZuBEdajZBqJPuSmTyqhcrkpVA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2i6K6NFGvA2QF5gWbey0y1VBqhUI-8bAvgP7bVDHdj4ZjbW0u3lgXAQh9Rg_qjrDBgls1X-BTyYlqZ0arjV1SLtyqoRsStPMIJf4j6_3aHjJyqWQYMaANgo7F-NZGDilggQjJ9IXzeEkzRZxPhdg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfgHy7hQR11veTQ24u1qatexoku8drX3Ki4ysBSCVSf8ig&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3hPJ32q9y0pEiFU04zpROaWBtu1C1HBOZUeWbHfrhCNw4mftGbzofZ5ct4sr6aH_FsbwBujLJd-Cv6s7Qr8ZbAVQFnwwc8jtWZxLZwOf3VXH5XXdbCPjUGxcycYv2EQvuTLHbJ60YBSWuF0KZleg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XOH0AeAGol65atFprmocng&oh=00_AfgMt_hOPMBlDpL1qh8AgQrDQXmE-UtQwDo_v9W_hYMgAA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2CIQnzeyc17NN9uIX8en5pymBYRTeg8X8i76GNzxfIj_WnmE5iIDRFTqj5MyT5aUUTwkJsCEevdv2J-B_XLHuSlk-QCBFEFyNFuN5pl_uMUhaLRIrD4IKqsU74DEnOJz4tZlFHo-Wo5FqZDIbnfw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1dDtWAv4XUJAdcbFbe-tXzIn6v9MAP5Jg0ObtoHIM7IgVuWo3rPCESYcwxymuDzFednnVGARe0pVse2BBV5GjYXcDcoXUjCn6xvu5e6yr9QtWayb-weDqKK_crWRDubN2Betpzgi8Z19raFbhj1w)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)