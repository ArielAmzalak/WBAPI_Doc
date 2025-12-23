![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fpayment_configuration_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[payment\_configuration\_update](/docs/whatsapp/cloud-api/webhooks/reference/payment_configuration_update)

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

[payment\_configuration\_update webhook reference](#payment-configuration-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example payload](#example-payload)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `payment_configuration_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **payment\_configuration\_update** webhook.

The **payment\_configuration\_update** webhook notifies you of changes to payment configurations for [Payments API India](/docs/whatsapp/cloud-api/payments-api/payments-in) and [Payments API Brazil](/docs/whatsapp/cloud-api/payments-api/payments-br).

## Triggers

* The payment configuration associated with a WhatsApp Business Account has been connected to a payment gateway account.
* The payment configuration associated with a WhatsApp Business Account has been disconnected from a payment gateway account.
* The payment configuration associated with a WhatsApp Business Account is now active.

## Syntax

```
{
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "time": <WEBHOOK_TRIGGER_TIMESTAMP>,
      "changes": [
        {
          "field": "payment_configuration_update",
          "value": {
            "configuration_name": "<PAYMENT_CONFIGURATION_NAME>",
            "provider_name": "PAYMENT_GATEWAY_PROVIDER_NAME",
            "provider_mid": "<PAYMENT_GATEWAY_MERCHANT_ACCOUNT_ID>",
            "status": "<PAYMENT_CONFIGURATION_STATUS>",
            "created_timestamp": <PAYMENT_CONFIGURATION_CREATION_TIMESTAMP>,
            "updated_timestamp": <PAYMENT_CONFIGURATION_UPDATE_TIMESTAMP>
          }
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<PAYMENT_CONFIGURATION_CREATION_TIMESTAMP>`  *Integer* | UNIX timestamp indicated when the payment configuration was created. | `1748827100` |
| `<PAYMENT_CONFIGURATION_NAME>`  *String* | Payment configuration name to be used in the Order Details messages. | `razorpay-prod` |
| `<PAYMENT_CONFIGURATION_STATUS>`  *String* | Payment configuration status.  Values can be:  `Active` — Indicates the payment configuration has been tested in WhatsApp manager and can now be used with Payments API.  `Needs Connecting` — Indicates the payment configuration has been disconnected from the payment gateway and needs to be connected again.  `Needs Testing` — Indicates the payment configuration has been connected to the payment gateway but still needs testing in WhatsApp Manager. | `Needs Connecting` |
| `<PAYMENT_CONFIGURATION_UPDATE_TIMESTAMP>`  *Integer* | UNIX timestamp indicated when the payment configuration was updated. | `1749320300` |
| `<PAYMENT_GATEWAY_MERCHANT_ACCOUNT_ID>`  *String* | Payment gateway merchant account ID. | `acc_GP4lfNA0iIMn5B` |
| `<PAYMENT_GATEWAY_PROVIDER_NAME>`  *String* | Name of the payment gateway provider associated with the payment configuration. Values can be:   * `billdesk` * `payu` * `razorpay` * `zaakpay` | `razorpay` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example payload

```
{
  "entry": [
    {
      "id": "102290129340398",
      "time": 1739321024,
      "changes": [
        {
          "field": "payment_configuration_update",
          "value": {
            "configuration_name": "razorpay-prod",
            "provider_name": "razorpay",
            "provider_mid": "acc_GP4lfNA0iIMn5B",
            "status": "Needs Testing",
            "created_timestamp": 1748827100,
            "updated_timestamp": 1749320300
          }
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[payment\_configuration\_update webhook reference](#payment-configuration-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example payload](#example-payload)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pKf4yr3k9CS8Sc0WSAD_Dg&oh=00_Afil3XZbmKuIvW75GCkSz1wkobxF1EfHqjfUYaOkYs3W1w&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pKf4yr3k9CS8Sc0WSAD_Dg&oh=00_Afh_lJTtJeXBsBCME8ec-PeVdb16Tsxmj2aUtBtt8XWrtA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pKf4yr3k9CS8Sc0WSAD_Dg&oh=00_AfjPP3LZfnRrJLK0udVWgiSoqILvU-4MmyR1Dzn7FTiOfA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pKf4yr3k9CS8Sc0WSAD_Dg&oh=00_AfjD3qqLAB6bi7GDW54qL-WEod5PaBay3wYKaz7OM7Uv-A&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=pKf4yr3k9CS8Sc0WSAD_Dg&oh=00_AfiAkBEeZzshzU8m3CKZDyiasLnwYLgte6m9rp15iJBqmQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT37cpH4iUXkhQccpaVmYetD5NbbqV1GCxiFj-eNbp0NmSYZX_Lb1--elO-W_Vw71R_wdNIne-yXXxgBMWUTRy-85BYAUroq1quWhiWZlvL8xrksZ0LI6RI4yXfIbce8tEK3QzNC59XhnnZBeJ7JWA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)