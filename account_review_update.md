![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Faccount_review_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[account\_review\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_review_update)

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

[account\_review\_update webhook reference](#account-review-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Payload parameters](#payload-parameters)

[Example payload](#example-payload)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `account_review_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account `account_review_update` webhook.

The **account\_review\_update** webhook notifies you when a WhatsApp Business Account has been reviewed against our policy guidelines.

## Triggers

* A WhatsApp Business Account is approved.
* A WhatsApp Business Account is rejected.
* A decision on a WhatsApp Business Account approval has been deferred or is awaiting more information.

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
            "decision": "<DECISION>"
          },
          "field": "account_review_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

## Payload parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<DECISION>`  *String* | Indicates WhatsApp Business Account ("WABA") review outcome.  Values can be:  `APPROVED` — Indicates WABA approved and ready for use.  `REJECTED` — Indicates WABA was rejected because it doesn't meet our policy requirements and cannot be used with our APIs.  `PENDING` — Indicates a review decision is still pending and WABA currently cannot be used with our APIs.  `DEFERRED` — Indicates a review decision has been deferred and the WABA currently cannot be used with our APIs. | `APPROVED` |
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
          "value": {
            "decision": "APPROVED"
          },
          "field": "account_review_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[account\_review\_update webhook reference](#account-review-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Payload parameters](#payload-parameters)

[Example payload](#example-payload)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=6EhUxD6dYCAQVHei-BuRlw&oh=00_AfifENW1Nc85RpqhrrVoMRTowZyUHcf9E4jjdrbmIXKdnA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=6EhUxD6dYCAQVHei-BuRlw&oh=00_Afh3_o07d-iOK6kYO5-PerKcPMtg91nXd4uEY_dG2Axasg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=6EhUxD6dYCAQVHei-BuRlw&oh=00_AfgZQSpHhm0AeZm_vG_BVU-nk48twu3drM70e8bMY0WYRg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=6EhUxD6dYCAQVHei-BuRlw&oh=00_Afh6xVebo6c0-1to4XliRmhx7H90vtnKXwM3IADljrdkbA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=6EhUxD6dYCAQVHei-BuRlw&oh=00_Afg3R1WHr0myyIdzV6bF5rTdv309UBfj1oKiYLWg6LLyKA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT06TqJIHyOFZFmqfCi_HXfPEC3eN5xW4uuXjlrIGEquyPMiwW4BTayrpeImJpjvVPOKf7oVAzwLUz1_wP-S1ZZ6aKGOVEs8Mpyqx_xQvkBHBctcNLS2D2uwmPhy4dog0y9CeNvOZLO-y4axK7K6Sg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)