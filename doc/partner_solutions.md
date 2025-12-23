![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fpartner_solutions%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[partner\_solutions](/docs/whatsapp/cloud-api/webhooks/reference/partner_solutions)

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

[partner\_solutions webhook reference](#partner-solutions-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `partner_solutions` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **partner\_solutions** webhook.

The **partner\_solutions webhook** describes changes to the status of a [Multi-Partner Solution](/docs/whatsapp/solution-providers/multi-partner-solutions/).

## Triggers

* A multi-partner solution is saved as a draft.
* A multi-partner solution request is sent to a partner.
* A multi-partner solution partner accepts a solution request.
* A multi-partner solution partner rejects a solution request.
* A multi-partner solution partner requests deactivation of a solution.
* A multi-partner solution is deactivated.

## Syntax

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "partner_solutions",
          "value": {
            "event": "<EVENT>",
            "solution_id": "<SOLUTION_ID>",
            "solution_status": "<SOLUTION_STATUS>"
          }
        }
      ],
      "id": "<BUSINESS_PORTFOLIO_ID>",
      "time": <WEBHOOK_TRIGGER_TIMESTAMP>
    }
  ],
  "object": "whatsapp_business_account"
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<BUSINESS_PORTFOLIO_ID>`  *String* | Business portfolio ID. | `506914307656634` |
| `<EVENT>`  *String* | Change event. Values can be:  `SOLUTION_CREATED` - Indicates a new solution was saved as a draft or sent as a request to a partner.  `SOLUTION_UPDATED` - Indicates an existing solution has been updated. | `SOLUTION_CREATED` |
| `<SOLUTION_ID>`  *String* | Solution ID. | `774485461512159` |
| `<SOLUTION_STATUS>`  *String* | Solution status. Values can be:  `ACTIVE` - The solution partner accepted the solution request and the solution can now be used.  `DEACTIVATED` - The solution has been deactivated.  `DRAFT` - The solution has been drafted but an invitation request has not been sent to a partner.  `INITIATED` - The solution has been created and the invitation request sent, but it has not been accepted or rejected yet.  `PENDING_DEACTIVATION` - The solution owner requested deactivation of the solution but the solution partner has yet to accept or decline the deactivation request.  `REJECTED` - The solution partner has rejected the solution request. | `INITIATED` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |

## Example

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "partner_solutions",
          "value": {
            "event": "SOLUTION_CREATED",
            "solution_id": "774485461512159",
            "solution_status": "INITIATED"
          }
        }
      ],
      "id": "506914307656634",
      "time": 1739321024
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[partner\_solutions webhook reference](#partner-solutions-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Q4WnerCItRSph759KkxdtQ&oh=00_AfgngAdmZGo8teoqfq4S5Sb25Zgy5vDeA6q-U-9lJhLHLw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Q4WnerCItRSph759KkxdtQ&oh=00_AfjBtZ5TNdcAgf0IP4_lKUzzbDEX2K3ZNy1xYzvR-XFTxg&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Q4WnerCItRSph759KkxdtQ&oh=00_AfjLeZ8-E0mi4us0lIfc7BFiGeIPOLMNUfFYvKORye59GA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Q4WnerCItRSph759KkxdtQ&oh=00_Afi7iNlcRzpV7aXPuzDo3crQhsm4shXIycOsnKlGVMW2WQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Q4WnerCItRSph759KkxdtQ&oh=00_AfgB6ulETWgaoOxM92XTCbT_0qXyznfeRXoyO6yvrTkEyA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT24qOESv4vwv-VM-VC_kLkNltx4zvoAqZg1xyzNp7x_89cGrD7nm76F1u2f5-saguDittFCLaGHOfnfc09hidi3khGKkUKMm0JZcQAAwUqA-csyenoeq-bRughbMZTn4yjMgDZVHyikI1D-idQk0w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)