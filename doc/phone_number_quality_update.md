![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fphone_number_quality_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[phone\_number\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_quality_update)

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

[phone\_number\_quality\_update webhook reference](#phone-number-quality-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `phone_number_quality_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **phone\_number\_quality\_update** webhook.

The **phone\_number\_quality\_update** webhook notifies you of changes to a business phone number's [throughput level](/docs/whatsapp/throughput).

## Triggers

* A business phone number's throughput level changes.

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
              "event": "<EVENT>",
              "old_limit": "<OLD_LIMIT>", <!-- only included for messaging limit changes -->
              "current_limit": "<CURRENT_LIMIT>",
              "max_daily_conversations_per_business": "<MAX_DAILY_MESSAGES_LIMIT>"
            },
            "field": "phone_number_quality_update"
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
| `<CURRENT_LIMIT>`  *String* | **This field will be removed in February, 2026. Use `max_daily_conversations_per_business` instead.**  Indicates current [messaging limit](/docs/whatsapp/messaging-limits) or [throughput](/docs/whatsapp/cloud-api/overview#throughput) level.  Values can be:  `TIER_50` — Indicates a messaging limit of 50.  `TIER_250` — Indicates a messaging limit of 250.  `TIER_2K` — Indicates a messaging limit of 2,000.  `TIER_10K` — Indicates a messaging limit of 10,000.  `TIER_100K` — Indicates a messaging limit of 100,000.  `TIER_NOT_SET` — Indicates the business phone number has not been used to send a message yet.  `TIER_UNLIMITED` — Indicates the business phone number has higher throughput. | `TIER_UNLIMITED` |
| `<EVENT>`  *String* | [Messaging limit](/docs/whatsapp/messaging-limits) change or [throughput](/docs/whatsapp/cloud-api/overview#throughput) change event.  Values can be:  `ONBOARDING` — Indicates the business phone number is still being registered.  `THROUGHPUT_UPGRADE` — Indicates the business phone number's throughput level has increased to higher throughput. | `THROUGHPUT_UPGRADE` |
| `<MAX_DAILY_MESSAGES_LIMIT>`  *String* | Indicates a change to the owning business portfolio's [messaging limit](/docs/whatsapp/messaging-limits) or [throughput](/docs/whatsapp/cloud-api/overview#throughput) change.  Values can be:  `TIER_50` — Indicates a messaging limit of 50.  `TIER_250` — Indicates a messaging limit of 250.  `TIER_2K` — Indicates a messaging limit of 2,0001,000.  `TIER_10K` — Indicates a messaging limit of 10,000.  `TIER_100K` — Indicates a messaging limit of 100,000.  `TIER_NOT_SET` — Indicates the business phone number has not been used to send a message yet.  `TIER_UNLIMITED` — Indicates the business phone number has higher throughput. | `TIER_2K` |
| `<OLD_LIMIT>`  *String* | **This parameter will be removed in February, 2026. Use `max_daily_conversations_per_business` instead.**  Indicates old [messaging limit](/docs/whatsapp/messaging-limits).  Values can be:  `TIER_50` — Indicates a messaging limit of 50.  `TIER_250` — Indicates a messaging limit of 250.  `TIER_2K` — Indicates a messaging limit of 2,000.  `TIER_10K` — Indicates a messaging limit of 10,000.  `TIER_100K` — Indicates a messaging limit of 100,000.  `TIER_NOT_SET` — Indicates the business phone number has not been used to send a message yet. | `TIER_UNLIMITED` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
{
  "entry": [
    {
      "id": "102290129340398",
      "time": 1748454394,
      "changes": [
        {
          "value": {
            "display_phone_number": "15550783881",
            "event": "THROUGHPUT_UPGRADE",
            "current_limit": "TIER_UNLIMITED"
          },
          "field": "phone_number_quality_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[phone\_number\_quality\_update webhook reference](#phone-number-quality-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HMT9OPYRShkaLsgjbkaIsw&oh=00_Afjtv7cPzVQQrultQvg3-xW-jJ7qirh7ShT4NftNFW7QNA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HMT9OPYRShkaLsgjbkaIsw&oh=00_AfgEBPL9i7WGkaS5PS6vYAMvfBReGUlh89yk33KkVprHJw&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HMT9OPYRShkaLsgjbkaIsw&oh=00_AfglC7DgYqV_l2pTqxB4hD_NCejNfdZpT1IKRmdvTVIxSg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HMT9OPYRShkaLsgjbkaIsw&oh=00_AfhZ_nxnZQIZi5-oOFTBzdLrUhqe2Jh94WS0zn3H4HLpJg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=HMT9OPYRShkaLsgjbkaIsw&oh=00_Afhctk2VZiAzUf_PTzg5jLnVfIqbsdROlzCLhVTYzzn8hw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1-xc_Mcr8SUzY1Q2VcLA2Vb8YmJGhDFFkdz-5MaaLUJtGGC2cIRfucfJKZdJ2m78NOHAGUCY9XkRbgiSfdJyR6H3agIGPxFhP5qkqoCTAaYGZXlR395mqo2zzpXr4ghQHc96TkCH3B2d-EoxhFtQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)