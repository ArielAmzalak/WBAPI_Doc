![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fbusiness_capability_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update)

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

[business\_capability\_update webhook reference](#business-capability-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Payload example](#payload-example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `business_capability_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **business\_capability\_update** webhook.

The **business\_capability\_update** webhook notifies you of WhatsApp Business Account or business portfolio capability changes ([messaging limits](/docs/whatsapp/messaging-limits/#increasing-your-limit), [phone number limits](/docs/whatsapp/cloud-api/phone-numbers#registered-number-cap), etc.).

## Triggers

* A WhatsApp Business Account is created.
* A WhatsApp Business Account or business portfolio business capability (e.g. [messaging limits](/docs/whatsapp/messaging-limits/#increasing-your-limit), [phone number limits](/docs/whatsapp/cloud-api/phone-numbers#registered-number-limits)) is increased or decreased.

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
            "max_daily_conversation_per_phone": <MAX_DAILY_CONVERSATIONS_PER_PHONE>,
            "max_daily_conversations_per_business": <MAX_DAILY_CONVERSATIONS_PER_BUSINESS>,
            "max_phone_numbers_per_business": <MAX_PHONES_PER_BUSINESS_PORTFOLIO>,
            "max_phone_numbers_per_waba": <MAX_PHONES_PER_WHATSAPP_BUSINESS_ACCOUNT>
          },
          "field": "business_capability_update"
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
| `<MAX_DAILY_CONVERSATIONS_PER_PHONE>`  *Integer* | **This parameter will be removed in February, 2026. Use `max_daily_conversations_per_business` instead.**  Business portfolio's [messaging limit](/docs/whatsapp/messaging-limits). Values can be:   * `250` * `2000` * `10000` * `100000` * `-1`   A value of `-1` indicates unlimited messaging. | `2000` |
| `<MAX_DAILY_CONVERSATIONS_PER_BUSINESS>`  *Integer* | Business portfolio's [messaging limit](/docs/whatsapp/messaging-limits).  Value can be:   * `TIER_250` * `TIER_2K` * `TIER_10K` * `TIER_100K` * `TIER_UNLIMITED` | `TIER_UNLIMITED` |
| `<MAX_PHONES_PER_BUSINESS_PORTFOLIO>`  *Integer* | Maximum number of business phone numbers the business portfolio can have.  This property is only included if `max_daily_conversation_per_phone` is set to `250`. | `2` |
| `<MAX_PHONES_PER_WHATSAPP_BUSINESS_ACCOUNT>`  *Integer* | Maximum number of business phone numbers allowed per WABA.  This property is only included if `max_daily_conversation_per_phone` is **not** set to `250`. | `25` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Payload example

```
{
  "entry": [
    {
      "id": "524126980791429",
      "time": 1739321024,
      "changes": [
        {
          "value": {
            "max_daily_conversations_per_business": 2000,
            "max_phone_numbers_per_waba": 25
          },
          "field": "business_capability_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[business\_capability\_update webhook reference](#business-capability-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Payload example](#payload-example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=oehMmObefZfT8hJ7a3j9tQ&oh=00_AfgEhLLIeZPawhnNP6A2iox4tVIBQQSm3cpiHTdzVXDDiQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=oehMmObefZfT8hJ7a3j9tQ&oh=00_Afhg6_rZnde86MDdGNi1dWuoDe-_K_tg6yg434P41QFnIg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=oehMmObefZfT8hJ7a3j9tQ&oh=00_AfjwB_wNZ8B05Ov2NDiJptpUseg9aN2OdGG_gPYslHfaRA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=oehMmObefZfT8hJ7a3j9tQ&oh=00_AfjC46pneJPFjZ3W2Tl4cFHef7Vh-V-r2logenoOH4pyIQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=oehMmObefZfT8hJ7a3j9tQ&oh=00_AfganOTtR5m5B6LpsGipRNwdbNua9Nm44JsXqtYJ_UPtBg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3X6ttqu3SAlgUoLsZ6wFxatdBlzr3Tif0veJprI0o-QqpvkPK3MU2DGamuloTVx5w2SUT_rv6wIvGKdxhQJ5ourkZwnOfvB9_2OgBKLifiEmMZS3YH_8fWc6if7mGoxe2NekwAVlfDKsFGvinSAg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)