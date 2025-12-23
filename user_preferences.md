![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fuser_preferences%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[user\_preferences](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences)

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

[user\_preferences webhook reference](#user-preferences-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `user_preferences` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **user\_preferences** webhook.

The **user\_preferences** webhook notifies you of changes to a WhatsApp user's [marketing message preferences](/docs/whatsapp/business-management-api/message-templates/marketing-templates#user-preferences-for-marketing-messages).

## Triggers

* A WhatsApp user stops marketing messages.
* A WhatsApp user resumes marketing messages.

## Syntax

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<WHATSAPP_USER_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>"
              }
            ],
            "user_preferences": [
              {
                "wa_id": "<WHATSAPP_USER_ID>",
                "detail": "<PREFERENCE_DESCRIPTION>",
                "category": "marketing_messages",
                "value": "<PREFERENCE>",
                "timestamp": <WEBHOOK_SENT_TIMESTAMP>
              }
            ]
          },
          "field": "user_preferences"
        }
      ]
    }
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<PREFERENCE>`  *String* | [Marketing message preference](/docs/whatsapp/business-management-api/message-templates/marketing-templates#user-preferences-for-marketing-messages).  Values can be:  `stop` — Indicates the WhatsApp users has opted to stop receiving marketing messages from you.  `resume` — Indicates the WhatsApp users has opted to resume receiving marketing messages from you. | `stop` |
| `<PREFERENCE_DESCRIPTION>`  *String* | Description of [marketing message preference](/docs/whatsapp/business-management-api/message-templates/marketing-templates#user-preferences-for-marketing-messages).  Values can be:   * `User requested to stop marketing messages` * `User requested to resume marketing messages` | `User requested to stop marketing messages` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user ID. Note that a WhatsApp user's ID and phone number may not always match. | `16505551234` |
| `<WHATSAPP_USER_PROFILE_NAME>`  *String* | WhatsApp user's name as it appears in their profile in the WhatsApp client. | `Sheena Nelson` |

## Example

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "contacts": [
              {
                "wa_id": "16505551234"
              }
            ],
            "user_preferences": [
              {
                "wa_id": "16505551234",
                "detail": "User requested to resume marketing messages",
                "category": "marketing_messages",
                "value": "resume",
                "timestamp": 1731705721
              }
            ]
          },
          "field": "user_preferences"
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[user\_preferences webhook reference](#user-preferences-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yR2BdmStEsmC_l_FCERRGw&oh=00_Afji1_jurUtekCYqv-99tkiqx77B0VheH4vkbsUphXXbIA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yR2BdmStEsmC_l_FCERRGw&oh=00_AfgSaJwbrBaJBgFC8hO6SBm-iU54a_8Z0oVQC3r9AoY1uA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yR2BdmStEsmC_l_FCERRGw&oh=00_AfiCBM3_aOmlRWwD1OzGOB6RFB8bqVtZeNNZ0p-PC1o8xg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yR2BdmStEsmC_l_FCERRGw&oh=00_AfgvpJYZQVX_0I3GuairhvjHryhgtSRGzrZF4Ko-ZMvqEA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=yR2BdmStEsmC_l_FCERRGw&oh=00_AfiFLEXvvGpiZeRcSw6grCNqG3Hh16vorNw24ou7hDjXVg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Zy8EkCC5pNSxZIOu_WQEKL1n7o1qo3548tWm1O6nPo11gZ2AW8SkFI-lToBg4IuBLoD5DzBLIcI0es5H21gUCr3nXif_osY3LC7CUEMDnlwdJgX0_KtBk3WkWLAGvUdcmm5S5jWny7b3728F57g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)