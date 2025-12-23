![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fphone_number_name_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[phone\_number\_name\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_name_update)

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

[phone\_number\_name\_update webhook reference](#phone-number-name-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `phone_number_name_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **phone\_number\_name\_update** webhook.

The **phone\_number\_name\_update** webhook notifies you of business phone number [display name verification](/docs/whatsapp/display-names#display-name-verificationn) outcomes.

## Triggers

* A newly created business phone number's display name is reviewed.
* A business phone number's already approved display name is edited and reviewed.

## Syntax

```
{
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "time": <WEBHOOK_TRIGGER_TIMESTAMP>,
      "changes": [
        {
          "value": {
            "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
            "decision": "<DECISION>",
            "requested_verified_name": "<REQUESTED_DISPLAY_NAME>",
            "rejection_reason": "<REJECTION_REASON>"
          },
          "field": "phone_number_name_update"
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
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<DECISION>`  *String* | Indicates the outcome of the business phone number [display name verification](/docs/whatsapp/cloud-api/phone-numbers#display-name-verification) process.  `APPROVED` — Indicates the display name has been approved and will now appear at the top of the business phone number's profile in the WhatsApp client.  `DEFERRED` — Indicates a decision has been deferred.  `PENDING` — Indicates a decision is still pending further review.  `REJECTED` — Indicates the display name has been rejected. You can edit the name using [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/overview/). Review our [display name guidelines](https://www.facebook.com/business/help/757569725593362) before editing. | `APPROVED` |
| `<REJECTION_REASON>`  *String* | The reason why the business phone number display name was rejected, if it was rejected. Review our display name guidelines for common rejection reasons.  Values can be:  `NAME_EMPLOYEE_ISSUE` — Rejected because the display name inclined a person's name or employee identifier.  `NAME_ENDCLIENT_NOTRELATED` — Rejected because the display name inclined an unrelated business's name.  `NAME_FORMAT_UNACCEPTABLE` — Rejected because the display name used an unacceptable format.  `NAME_INDIVIDUAL_ISSUE` — Rejected because the display name inclined a person's name or employee identifier. `NAME_NOT_CONSISTENT` — Rejected because the display name was not consistent with the business's branding.  `null` — Indicates name was accepted.  `UNKNOWN` — Rejected for an unknown reason. Please contact support. | `APPROVED` |
| `<REQUESTED_DISPLAY_NAME>`  *String* | The business phone number display name collected when the number was created, or name submitted when editing an already approved display name. | `Lucky Shrub` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
{
  "entry": [
    {
      "id": "102290129340398",
      "time": 1739321024,
      "changes": [
        {
          "value": {
            "display_phone_number": "15550783881",
            "decision": "APPROVED",
            "requested_verified_name": "Lucky Shrub",
            "rejection_reason": null
          },
          "field": "phone_number_name_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[phone\_number\_name\_update webhook reference](#phone-number-name-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mY47V-3wgU-Un1bZXd0GGg&oh=00_AfiXAgRJcgZgcv43G937B5BhsPEkUEoXeIRPyPoV2fY_XA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mY47V-3wgU-Un1bZXd0GGg&oh=00_Afh7TTop-3ECC6ErKSub9Q-Qp20ThzksNGAVSBBHLln93g&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mY47V-3wgU-Un1bZXd0GGg&oh=00_Afh_wjSlSuUEYw-yt9FfdTg8ZDplsSC3C-gktCBOjf-7wQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mY47V-3wgU-Un1bZXd0GGg&oh=00_AfjUCX7vMaOZ_hKpypzNNNnxFVf-Btyl2OUjZ8QcvWSULA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mY47V-3wgU-Un1bZXd0GGg&oh=00_AfggtyGcVIosfMzLPwzWBWxe39KW0-HlG_p3TWOmnkncyQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2VF_kwSR9Lvyq4wbUuMVT4oKj4K651PoOUvP-08V2Xw5hJjLNPJKD0z4MhAL4y_Ftsh7HXkjAdfcFOnfgT1CxLwdS51RsfPTWnRsBig_FtQHaVHq-BybP3Zw9iMHpEl-0o2O97h9JtnLhWsi08Bw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)