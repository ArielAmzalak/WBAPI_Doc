![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-management%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Management](/docs/whatsapp/business-management-api/message-templates/template-management)

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

[Template management](#template-management)

[Get templates](#get-templates)

[Get all templates](#get-all-templates)

[Get all templates and specific fields](#get-all-templates-and-specific-fields)

[Get all approved and rejected templates](#get-all-approved-and-rejected-templates)

[Edit templates](#edit-templates)

[Limitations](#limitations)

[Edit template category](#edit-template-category)

[Edit template components](#edit-template-components)

[Delete templates](#delete-templates)

[Limitations](#limitations-2)

[Delete template by name](#delete-template-by-name)

[Delete template by ID](#delete-template-by-id)

[Example response](#example-response)

[Get template namespace](#get-template-namespace)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template management

Learn about common endpoints used to manage templates.

## Get templates

Use the [`GET/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates`](/docs/graph-api/reference/whats-app-business-account/message_templates#Reading) endpoint to get a list of templates in a WhatsApp Business Account.

### Get all templates

Example request to get all templates (default fields):

```
curl 'https://graph.facebook.com/v23.0/102290129340398/message_templates' \
-H 'Authorization: Bearer EAAJB...'
```

Example response, truncated (`...`) for brevity:

```
{
  "data": [
    {
      "name": "reservation_confirmation",
      "parameter_format": "NAMED",
      "components": [
        {
          "type": "HEADER",
          "format": "IMAGE",
          "example": {
            "header_handle": [
              "https://scontent.whatsapp.net/v/t61..."
            ]
          }
        },
        {
          "type": "BODY",
          "text": "*You're all set!*\n\nYour reservation for {{number_of_guests}} at Lucky Shrub Eatery on {{day}}, {{date}}, at {{time}}, is confirmed. See you then!",
          "example": {
            "body_text_named_params": [
              {
                "param_name": "number_of_guests",
                "example": "4"
              },
              {
                "param_name": "day",
                "example": "Saturday"
              },
              {
                "param_name": "date",
                "example": "August 30th, 2025"
              },
              {
                "param_name": "time",
                "example": "7:30 pm"
              }
            ]
          }
        },
        {
          "type": "FOOTER",
          "text": "Lucky Shrub Eatery: The Luckiest Eatery in Town!"
        },
        {
          "type": "BUTTONS",
          "buttons": [
            {
              "type": "URL",
              "text": "Change reservation",
              "url": "https://www.luckyshrubeater.com/reservations"
            },
            {
              "type": "PHONE_NUMBER",
              "text": "Call us",
              "phone_number": "+16467043595"
            },
            {
              "type": "QUICK_REPLY",
              "text": "Cancel reservation"
            }
          ]
        }
      ],
      "language": "en_US",
      "status": "APPROVED",
      "category": "UTILITY",
      "id": "1387372356726668"
    },
    {
      "name": "coupon_expiration_reminder_number_vars",
      "parameter_format": "POSITIONAL",
      "components": [
        {
          "type": "HEADER",
          "format": "TEXT",
          "text": "Act fast, {{1}}!",
          "example": {
            "header_text": [
              "Pablo"
            ]
          }
        },
        {
          "type": "BODY",
          "text": "Just a quick reminder—your exclusive coupon code, {{1}}, *expires in only {{2}} days!* Don’t miss out on our special deals. Use your code at checkout before it’s too late.\n\nHappy shopping! 😃",
          "example": {
            "body_text": [
              [
                "SUMMER20",
                "10"
              ]
            ]
          }
        },
        {
          "type": "FOOTER",
          "text": "Lucky Shrub Succulents"
        },
        {
          "type": "BUTTONS",
          "buttons": [
            {
              "type": "URL",
              "text": "See deals",
              "url": "https://www.luckyshrub.com/deals"
            },
            {
              "type": "QUICK_REPLY",
              "text": "Unsubscribe"
            }
          ]
        }
      ],
      "language": "en",
      "status": "APPROVED",
      "category": "MARKETING",
      "sub_category": "CUSTOM",
      "id": "1304694804498707"
    },

    ...

  ],
  "paging": {
    "cursors": {
      "before": "QVFIU...",
      "after": "QVFIU..."
    },
    "next": "https://graph.facebook.com/v23.0/10229..."
  }
}
```

### Get all templates and specific fields

Example request to get the name, category, and status of all templates in a WhatsApp Business Account, limiting the response to 5 templates per result set:

```
curl 'https://graph.facebook.com/v23.0/102290129340398/message_templates?fields=name,category,status&limit=5' \
-H 'Authorization: Bearer EAAJB...'
```

Example response:

```
{
  "data": [
    {
      "name": "reservation_confirmation",
      "category": "UTILITY",
      "status": "APPROVED",
      "id": "1387372356726668"
    },
    {
      "name": "coupon_expiration_reminder_number_vars",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "1304694804498707"
    },
    {
      "name": "coupon_expiration_reminder_named_vars",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "1625063511800527"
    },
    {
      "name": "address_update",
      "category": "UTILITY",
      "status": "PENDING",
      "id": "1137051647947973"
    },
    {
      "name": "reservation_confirmation_short_banner",
      "category": "UTILITY",
      "status": "REJECTED",
      "id": "1166414785519855"
    }
  ],
  "paging": {
    "cursors": {
      "before": "QVFIU...",
      "after": "QVFIU..."
    },
    "next": "https://graph.facebook.com/v23.0/10229..."
  }
}
```

### Get all approved and rejected templates

Example request to get all approved templates and their name, category, and status (swap `status=approved` with `status=rejected` to get rejected templates instead):

```
curl 'https://graph.facebook.com/v23.0/102290129340398/message_templates?fields=name,category,status&status=approved' \
-H 'Authorization: Bearer EAAJB...'
```

Example response:

```
{
  "data": [
    {
      "name": "reservation_confirmation",
      "category": "UTILITY",
      "status": "APPROVED",
      "id": "1387372356726668"
    },
    {
      "name": "coupon_expiration_reminder_number_vars",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "1304694804498707"
    },
    {
      "name": "coupon_expiration_reminder_named_vars",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "1625063511800527"
    },
    {
      "name": "calling_permission_request",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "1092999222892024"
    },
    {
      "name": "location_request_v1",
      "category": "MARKETING",
      "status": "APPROVED",
      "id": "3373761659571648"
    },
    {
      "name": "order_confirmation",
      "category": "UTILITY",
      "status": "APPROVED",
      "id": "1667696820637468"
    }
  ],
  "paging": {
    "cursors": {
      "before": "QVFIU...",
      "after": "QVFIU..."
    },
    "next": "https://graph.facebook.com/v23.0/10229..."
  }
}
```

## Edit templates

Use the [POST /<TEMPLATE\_ID>](/docs/graph-api/reference/whats-app-business-hsm/#Updating) endpoint to edit a template. You can also use the [Message templates](https://business.facebook.com/latest/whatsapp_manager/message_templates) panel in WhatsApp Manager to edit templates.

### Limitations

* Only templates with an `APPROVED`, `REJECTED`, or `PAUSED` status can be edited.
* You can only edit a template's category, components, or time-to-live.
* You cannot edit individual template components; all components will be replaced with the components in the edit request payload.
* You cannot edit the category of an approved template.
* Approved templates can be edited up to 10 times in a 30 day window, or 1 time in a 24 hour window. Rejected or paused templates can be edited an unlimited number of times.
* After editing an approved or paused template, it will automatically be approved unless it fails template review.

### Edit template category

Example request:

```
curl 'https://graph.facebook.com/v23.0/1252715608684590' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "category": "MARKETING"
}'
```

Example response:

```
{
  "success": true
}
```

### Edit template components

Example request to overwrite a template's existing components with new components.

```
curl 'https://graph.facebook.com/v23.0/564750795574598' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT",
      "text": "Our {{1}} is on!",
      "example": {
        "header_text": [
          "Spring Sale"
        ]
      }
    },
    {
      "type": "BODY",
      "text": "Shop now through {{1}} and use code {{2}} to get {{3}} off of all merchandise.",
      "example": {
        "body_text": [
          [
            "the end of April",
            "25OFF",
            "25%"
          ]
        ]
      }
    },
    {
      "type": "FOOTER",
      "text": "Use the buttons below to manage your marketing subscriptions"
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "QUICK_REPLY",
          "text": "Unsubscribe from Promos"
        },
        {
          "type": "QUICK_REPLY",
          "text": "Unsubscribe from All"
        }
      ]
    }
  ]
}'
```

## Delete templates

Use the [DELETE /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates#Deleting) endpoint to delete a template by name or ID.

### Limitations

* If you delete a template that has been sent in a template message but has yet to be delivered (e.g. because the customer's phone is turned off), the template's status will be set to `PENDING_DELETION` and we will attempt to deliver the message for 30 days. If you are an *On-Premises API*, after this time you will receive a `Structure Unavailable` error and the customer will not receive the message.
* If you delete an approved template, you cannot create a new template with the same name for 30 days.
* Templates that are in a disabled status cannot be deleted.

### Delete template by name

Deleting a template by name deletes all templates that match that name (meaning templates with the same name but different languages will also be deleted).

Example request:

```
curl -X DELETE 'https://graph.facebook.com/v23.0/102290129340398/message_templates?name=order_confirmation' \
-H 'Authorization: Bearer EAAJB...'
```

Example response:

```
{
  "success": true
}
```

### Delete template by ID

To delete a template by ID, include the template's ID along with its name in your request; only the template with the matching template ID will be deleted.

Example request:

```
curl -X DELETE 'https://graph.facebook.com/v23.0/102290129340398/message_templates?hsm_id=1407680676729941&name=order_confirmation' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "success": true
}
```

## Get template namespace

*On-Premises API users only.*

Use the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account/#Reading) endpoint and include the `message_template_namespace` field to get a template's namespace.

Example request syntax:

```
1. curl 'https://graph.facebook.com/v23.0/102290129340398?fields=message_template_namespace' \
2. -H 'Authorization: Bearer EAAJB...'
```

Example response:

```
{
  "message_template_namespace": "ba30dd89_2ebd_41e4_b805_f2c05ae04cc9",
  "id": "102290129340398"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template management](#template-management)

[Get templates](#get-templates)

[Get all templates](#get-all-templates)

[Get all templates and specific fields](#get-all-templates-and-specific-fields)

[Get all approved and rejected templates](#get-all-approved-and-rejected-templates)

[Edit templates](#edit-templates)

[Limitations](#limitations)

[Edit template category](#edit-template-category)

[Edit template components](#edit-template-components)

[Delete templates](#delete-templates)

[Limitations](#limitations-2)

[Delete template by name](#delete-template-by-name)

[Delete template by ID](#delete-template-by-id)

[Example response](#example-response)

[Get template namespace](#get-template-namespace)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hMyv3jMTmymomB_0CVDNjQ&oh=00_AfgB5U6haXb8FfS8zutv9wRIiueWAyUUhscQEFjHpQzrvw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hMyv3jMTmymomB_0CVDNjQ&oh=00_AfgXVFbYZGmqVngMfl_K8vaxX6eB1tqQymF8LwKcXR8rZQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hMyv3jMTmymomB_0CVDNjQ&oh=00_Afhxt5_lJlqq11inywVZJDr_90fof0bBawUi6a17VLPKCw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hMyv3jMTmymomB_0CVDNjQ&oh=00_AfiZ14KAlH1LQ1Z4hQ0ZjpnfSS8FiO_-UhhxNC3wLGPMrQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hMyv3jMTmymomB_0CVDNjQ&oh=00_AfhtkC2HsV8is0E684b-bZNUZh-EAjVUrAEJcsw9H1AOkw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3BuP4rFQhRPUw4kPPORV9jMstgPlma6BYxV_Aiv-L2SV8z9LyYXLEyU5LQax6uSl8ZWceY7fp6r3ViYdjNFRUIPFQyFetuok3VPXKy6BGfeCmyHzleKfuQ1jssHWzwAOcK70Ooq0Z4XittF7pwiQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)