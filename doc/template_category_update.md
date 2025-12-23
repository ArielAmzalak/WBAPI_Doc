![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Ftemplate_category_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update)

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

[template\_category\_update webhook reference](#template-category-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `template_category_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **template\_category\_update** webhook.

The **template\_category\_update** webhook notifies you of changes to template's [category](/docs/whatsapp/updates-to-pricing/new-template-guidelines).

## Triggers

* The existing category of a WhatsApp template is going to be changed by an [automated process](/docs/whatsapp/updates-to-pricing/new-template-guidelines#how-we-update-a-template-s-category-after-initial-approval).
* The existing category of a WhatsApp template is changed manually or by an [automated process](/docs/whatsapp/updates-to-pricing/new-template-guidelines#how-we-update-a-template-s-category-after-initial-approval).

## Syntax

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "time": <WEBHOOK_TRIGGER_TIMESTAMP>,
      "changes": [
        {
          "field": "template_category_update",
          "value": {
            "message_template_id": <TEMPLATE_ID>,
            "message_template_name": "<TEMPLATE_NAME>",
            "message_template_language": "<TEMPLATE_LANGUAGE>",

            <!-- impending category change notifications only -->
            "correct_category": "<CORRECT_CATEGORY>",
            "new_category": "<CURRENT_CATEGORY>",
            "category_update_timestamp": <CATEGORY_UPDATE_TIMESTAMP>

            <!-- completed category change notifications only -->
            "previous_category": "<PREVIOUS_CATEGORY>",
            "new_category": "<NEW_CATEGORY>"

          }
        }
      ]
    }
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<CORRECT_CATEGORY>`  *String* | The category that the template will be [recategorized](/docs/whatsapp/updates-to-pricing/new-template-guidelines/#how-we-update-a-template-s-category-after-initial-approval) as in 24 hours. | `MARKETING` |
| `<CURRENT_CATEGORY>`  *String* | The template's current [category](/docs/whatsapp/business-management-api/message-templates#template-categories). | `MARKETING` |
| `<NEW_CATEGORY>`  *String* | The template's new [category](/docs/whatsapp/business-management-api/message-templates#template-categories). | `MARKETING` |
| `<CATEGORY_UPDATE_TIMESTAMP>`  *Integer* | The Unix timestamp (in seconds) indicating when the template's category will be updated to the `<CORRECT_CATEGORY>` specified in the webhook. This value represents the moment the update is scheduled to occur. | `1760711433` |
| `<PREVIOUS_CATEGORY>`  *String* | The template's previous [category](/docs/whatsapp/business-management-api/message-templates#template-categories). | `UTILITY` |
| `<TEMPLATE_ID>`  *Integer* | Template ID. | `278077987957091` |
| `<TEMPLATE_LANGUAGE>`  *String* | Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en-US` |
| `<TEMPLATE_NAME>`  *String* | Template name. | `welcome_template` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Examples

This example webhook describes a template that will be recategorized as `MARKETING` in 24 hours. Note that `new_category` indicates its *current* category:

```
{
 "entry": [
   {
     "id": "102290129340398",
     "time": 1746082800,
     "changes": [
       {
         "field": "template_category_update",
         "value": {
           "message_template_id": 278077987957091,
           "message_template_name": "welcome_template",
           "message_template_language": "en-US",
           "new_category": "UTILITY",
           "correct_category": "MARKETING",
           "category_update_timestamp": 1746169200
         }
       }
     ]
   }
 ],
 "object": "whatsapp_business_account"
}
```

This example webhook describes a template that has been recategorized as `MARKETING`:

```
{
 "entry": [
   {
     "id": "102290129340398",
     "time": 1746169200,
     "changes": [
       {
         "field": "template_category_update",
         "value": {
           "message_template_id": 278077987957091,
           "message_template_name": "welcome_template",
           "message_template_language": "en-US",
           "previous_category": "UTILITY",
           "new_category": "MARKETING"
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

[template\_category\_update webhook reference](#template-category-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Examples](#examples)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=caeM0xC3LSTqXUt61PAXVQ&oh=00_AfhkG3e-Rl1qQW4sUHHK_U3CMJMVYxqfW2ZEzQa6lJJdPQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=caeM0xC3LSTqXUt61PAXVQ&oh=00_AfgwEC9Y0K7DuKKfmQJ__6dlEOkgNb27gF4mCfE89BdF0A&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=caeM0xC3LSTqXUt61PAXVQ&oh=00_AfiPAAV7zWaEXfnhkbEHvqRnKkMtG4y_Sb2l9Br0LRxrzA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=caeM0xC3LSTqXUt61PAXVQ&oh=00_AfjO4nGhqO17OxUEwHdS1C-9fMPvswTCaFTuk6SqQe5X0g&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=caeM0xC3LSTqXUt61PAXVQ&oh=00_Afi0qGvtNu82uw8WKM8qZywVhny_OA7gecsMw6yXhv5NxA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0bATd3y5YJHkHoyYRIijyR9zxqtT2ilNm8Ke6OxOtMP-0l4E-vDkQrpBoV9pWBca0aTLfCdW-zwmZtHge1JdLm9tlc7ymFxZYzqTgdAqwWGHNEHtDulf-rcSQC5IgrE1v4KzAXVnEoLLYEqb3X5w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)