![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Fcopy-code-button-authentication-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Copy Code](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates)

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

[Copy code authentication templates](#copy-code-authentication-templates)

[Limitations](#limitations)

[Creating authentication templates](#creating-authentication-templates)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

[Example webhook](#example-webhook)

[Sample app](#sample-app)

[Sending authentication templates](#sending-authentication-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request-2)

[Example response](#example-response-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Copy code authentication templates

Copy code authentication templates allow you to send a one-time password or code along with a copy code button to your users. When a WhatsApp user taps the copy code button, the WhatsApp client copies the password or code to the device's clipboard. The user can then switch to your app and paste the password or code into your app.

Note: The "I didn't request a code" button is currently in beta and is being rolled out incrementally to business customers.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/545560391_1347895570098676_5955248492889407175_n.png?stp=dst-webp&_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=hGKIlCwMYLQQ7kNvwGYUaAn&_nc_oc=Adlb4Kfoth-cdgDK35kduHtjHqU3hHI4VQsshExM1c2fFBWZbHEUj8J9GkRMJf4rtBs&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=g3qAM7_p1pbXqhg_3eckOw&oh=00_AfhRM_D3fvdo8SPJ3gjIK_4itNDKx6VR_Ojsr4V7AcirDQ&oe=69405937)

Copy code button authentication templates consist of:

* Preset text: *<VERIFICATION\_CODE> is your verification code.*
* An optional security disclaimer: *For your security, do not share this code.*
* An optional expiration warning (optional): *This code expires in <NUM\_MINUTES> minutes.*
* A copy code button.

## Limitations

URLs, media, and emojis are not supported.

## Creating authentication templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates) endpoint to create authentication templates.

### Request Syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer EAAJB...' \
  -d '
{
    "name": "<TEMPLATE_NAME>",
    "language": "<TEMPLATE_LANGUAGE>",
    "category": "authentication",
    "message_send_ttl_seconds": <TIME_TO_LIVE>,  // Optional
    "components": [
      {
        "type": "body",
        "add_security_recommendation": <SECURITY_RECOMMENDATION>  // Optional
      },
      {
        "type": "footer",
        "code_expiration_minutes": <CODE_EXPIRATION>  // Optional
      },
      {
        "type": "buttons",
        "buttons": [
          {
            "type": "otp",
            "otp_type": "copy_code",
            "text": "<COPY_CODE_BUTTON_TEXT>"  // Optional
          }
        ]
      }
    ]
  }'
```

Note that in your template creation request the button `type` is designated as `OTP`, but upon creation the button `type` will be set to `URL`. You can confirm this by performing a GET request on a newly created authentication template and analyzing its components.

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<CODE_EXPIRATION>`  *Integer* | **Optional.**   Indicates the number of minutes the password or code is valid.   If included, the code expiration warning and this value will be displayed in the delivered message.   If omitted, the code expiration warning will not be displayed in the delivered message.   Minimum 1, maximum 90. | `5` |
| `<COPY_CODE_BUTTON_TEXT>`  *String* | **Optional.**   Copy code button label text.   If omitted, the text will default to a pre-set value localized to the template's language. For example, `Copy Code` for English (US).   Maximum 25 characters. | `Copy Code` |
| `<SECURITY_RECOMMENDATION>`  *Boolean* | **Optional.**   Set to `true` if you want the template to include the string, *For your security, do not share this code.* Set to `false` to exclude the string. | `true` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**   Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**   Template name.   Maximum 512 characters. | `verification_code` |
| `<TIME_TO_LIVE>`  *Integer* | **Optional.**   Authentication message time-to-live value, in seconds. See [Time-To-Live](/docs/whatsapp/business-management-api/authentication-templates#time-to-live) below. | `60` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_copy_code_button",
  "language": "en_US",
  "category": "authentication",
  "message_send_ttl_seconds": 60,
  "components": [
    {
      "type": "body",
      "add_security_recommendation": true
    },
    {
      "type": "footer",
      "code_expiration_minutes": 5
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "otp",
          "otp_type": "copy_code",
          "text": "Copy Code"
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "id": "594425479261596",
  "status": "PENDING",
  "category": "AUTHENTICATION"
}
```

## Webhooks

The [button messages webhook](/docs/whatsapp/cloud-api/webhooks/reference/messages/button) is triggered whenever a user taps the "I didn't request a code" button within the message.

### Example webhook

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "320580347795883",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "12345678",
              "phone_number_id": "1234567890"
            },
            "contacts": [
              {
                "profile": {
                  "name": "John"
                },
                "wa_id": "12345678"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "12345678",
                  "id": "wamid.HBgLMTIxMTU1NTE0NTYVAgARGBJDMDEyMTFDNTE5NkFCOUU3QTEA"
                },
                "from": "12345678",
                "id": "wamid.HBgLMTIxMTU1NTE0NTYVAgASGCBBQ0I3MjdCNUUzMTE0QjhFQkM4RkQ4MEU3QkE0MUNEMgA=",
                "timestamp": "1753919111",
                "from_logical_id": "131063108133020",
                "type": "button",
                "button": {
                  "payload": "DID_NOT_REQUEST_CODE",
                  "text": "I didn't request a code"
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

## Sample app

See our [WhatsApp One-Time Password (OTP) Sample App](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-OTP-Sample-App&h=AT1hMa6HeO7NPC5wSwj-Fif_IY0Upr-9IHO9r4A7m2ga6KF6EMo2xx1jgZ8Xy_dOxoKMB-QW3JnTH0unb1Ns61mwyohcXOft36rHzeo-0pcqNRuG5oqi2tnz35UTc2FjJcIlMHN9F6h37xwaOB_PNQ) for Android on Github. The sample app demonstrates how to send and receive OTP passwords and codes via the API, how to integrate the one-tap autofill and copy code buttons, how to create a template, and how to spin up a sample server.

## Sending authentication templates

This document explains how to send approved [authentication templates with one-time password buttons](/docs/whatsapp/business-management-api/authentication-templates).

Note that **you must first initiate a handshake** between your app and the WhatsApp client. See [Handshake](#handshake) above.

### Request syntax

```
curl -X POST "https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
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
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "<ONE-TIME PASSWORD>"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": "0",
          "parameters": [
            {
              "type": "text",
              "text": "<ONE-TIME PASSWORD>"
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
| `<CUSTOMER_PHONE_NUMBER>` | The customer's WhatsApp phone number. | `12015553931` |
| `<ONE-TIME PASSWORD>` | The one-time password or verification code to be delivered to the customer.   Note that this value must appear twice in the payload.   Maximum 15 characters. | `J$FpnYnP` |
| `<TEMPLATE_LANGUAGE_CODE>` | The template's [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>` | The template's name. | `verification_code` |

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
| `<INPUT>`  *String* | The customer phone number that the message was sent to. This may not match `wa_id`. | `+16315551234` |
| `<WA_ID>`  *String* | WhatsApp ID of the customer who the message was sent to. This may not match `input`. | `+16315551234` |
| `<ID>`  *String* | WhatsApp message ID. You can use the ID listed after "wamid." to track your message status. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI3N0EyQUJDMjFEQzZCQUMzODMA` |

### Example request

```
curl -L 'https://graph.facebook.com/v24.0/105954558954427/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '{
      "messaging_product": "whatsapp",
      "recipient_type": "individual",
      "to": "12015553931",
      "type": "template",
      "template": {
        "name": "verification_code",
        "language": {
          "code": "en_US"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "J$FpnYnP"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": "0",
          "parameters": [
            {
              "type": "text",
              "text": "J$FpnYnP"
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
      "input": "12015553931",
      "wa_id": "12015553931"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI4Qzc5QkNGNTc5NTMyMDU5QzEA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Copy code authentication templates](#copy-code-authentication-templates)

[Limitations](#limitations)

[Creating authentication templates](#creating-authentication-templates)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

[Example webhook](#example-webhook)

[Sample app](#sample-app)

[Sending authentication templates](#sending-authentication-templates)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=CvOxhzaxwXNL3xKuXLq33A&oh=00_Afg2Tbm0eekIf4CBNTAN1ICwjOoYDBTIpbfJOSPy3xpjtA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=CvOxhzaxwXNL3xKuXLq33A&oh=00_AfiSrmyePcYY4kc87LRfvGx-PoLva27MsILCZ-Srr_JYvQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=CvOxhzaxwXNL3xKuXLq33A&oh=00_Afh2SvFaSd0mMAAiV9XfNfWUuzVh5zWtQDYN6mANuniS6w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=CvOxhzaxwXNL3xKuXLq33A&oh=00_AfhDoWRLOIhrU48Oc3NGmYlhDQYB3_0EQXET0m2jI9fnJw&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=CvOxhzaxwXNL3xKuXLq33A&oh=00_AfhtneMVdRtDixn7i3FoAV2zZyO7_xPoa86zBcZPy715-A&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0k6q7B15rkvqAZn-ONdBXWLmEehdttCTFvOD7YOaftbYzP9qRvPz1QsUruHNJ3wYlw0Pnhp6L8obXmAY4zLJO-1-LQvunGi0q2OGbXhFJJdZAwzlAAi4NRMa-ZQ8ftnlmWhxBlnaiM6C0BTzOtjw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)