![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fmessage_template_components_update%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[message\_template\_components\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_components_update)

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

[message\_template\_components\_update webhook reference](#message-template-components-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `message_template_components_update` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account `message_template_components_update` webhook.

The **message\_template\_components\_update** webhook notifies you of changes to a template's components.

## Triggers

* A template is edited.

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
            "message_template_id": <TEMPLATE_ID>,
            "message_template_name": "<TEMPLATE_NAME>",
            "message_template_language": "<TEMPLATE_LANGUAGE_AND_LOCALE_CODE>",
            "message_template_element": "<TEMPLATE_BODY_TEXT>,

            <!-- only included if template has a text header -->
            "message_template_title": "<TEMPLATE_HEADER_TEXT>",

            <!-- only included if template has a footer -->
            "message_template_footer": "<TEMPLATE_FOOTER_TEXT>",

            <!-- only included if template has a url or phone number button -->
            "message_template_buttons": [
              {
                "message_template_button_type": "<BUTTON_TYPE>",
                "message_template_button_text": "<BUTTON_LABEL_TEXT>",

                <!--only included for url buttons -->
                "message_template_button_url": "<BUTTON_URL>",

                <!--only included for phone number buttons -->
                "message_template_button_phone_number": "<BUTTON_PHONE_NUMBER>"
              }
            ]
          },
          "field": "message_template_components_update"
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
| `<BUTTON_LABEL_TEXT>`  *String* | Button label text. | `Email support` |
| `<BUTTON_PHONE_NUMBER>`  *String* | Button phone number. | `+15550783881` |
| `<BUTTON_TYPE>`  *String* | [Button type](/docs/whatsapp/business-management-api/message-templates/components#buttons).  Values can include:   * `CATALOG` * `COPY_CODE` * `EXTENSION` * `FLOW`, `MPM` * `ORDER_DETAILS` * `OTP` * `PHONE_NUMBER` * `POSTBACK` * `REMINDER` * `SEND_LOCATION` * `SPM` * `QUICK_REPLY` * `URL` * `VOICE_CALL` | `URL` |
| `<BUTTON_URL>`  *String* | Button URL. | `https://www.luckyshrub.com/support` |
| `<TEMPLATE_BODY_TEXT>`  *String* | Template body text. | `Thank you for your order, {{1}}! Your order number is {{2}}. If you have any questions, contact support using the buttons below. Thanks again!` |
| `<TEMPLATE_FOOTER_TEXT>`  *String* | Template footer text. | `Lucky Shrub: the Succulent Specialists!` |
| `<TEMPLATE_HEADER_TEXT>`  *String* | Template header text. | `Your order is confirmed!` |
| `<TEMPLATE_ID>`  *Integer* | Template ID. | `1315502779341834` |
| `<TEMPLATE_LANGUAGE_AND_LOCALE_CODE>`  *String* | Template [language and locale](/docs/whatsapp/business-management-api/message-templates/supported-languages) code. | `en_US` |
| `<TEMPLATE_NAME>`  *String* | Template name. | `order_confirmation` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
{
  "entry": [
    {
      "id": "102290129340398",
      "time": 1751250234,
      "changes": [
        {
          "value": {
            "message_template_id": 1315502779341834,
            "message_template_name": "order_confirmation",
            "message_template_language": "en_US",
            "message_template_title": "Your order is confirmed!",
            "message_template_element": "Thank you for your order, {{1}}! Your order number is {{2}}. If you have any questions, contact support using the buttons below. Thanks again!",
            "message_template_footer": "Lucky Shrub: the Succulent Specialists!",
            "message_template_buttons": [
              {
                "message_template_button_type": "PHONE_NUMBER",
                "message_template_button_text": "Phone support",
                "message_template_button_phone_number": "+15550783881"
              },
              {
                "message_template_button_type": "URL",
                "message_template_button_text": "Email support",
                "message_template_button_url": "https://www.luckyshrub.com/support"
              }
            ]
          },
          "field": "message_template_components_update"
        }
      ]
    }
  ],
  "object": "whatsapp_business_account"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[message\_template\_components\_update webhook reference](#message-template-components-update-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qdEf1-lYH_iqcZvbVLAfow&oh=00_Afj-KNl-7bDhZj-1eOD3XqM1puJudsFzNpELz8-4Gpjc3Q&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qdEf1-lYH_iqcZvbVLAfow&oh=00_Afg1-dJRscmGJsEuahCWaaxyykgXkiI7abLIRRj2icMxRg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qdEf1-lYH_iqcZvbVLAfow&oh=00_Afi-tArO_93Nl_eYjGYspildL4jvYKK0cJ1ugYKnYBBnow&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qdEf1-lYH_iqcZvbVLAfow&oh=00_Afgd2atnz7j_msDN3CGi4LANyoFPLZU9V2c1QNsRO-iVZQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qdEf1-lYH_iqcZvbVLAfow&oh=00_AfjKQ5KE9bPT1fb4-0xoZBeHSePzl2lS2uTYCs1koGQfcg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0wQvgW9rnix9Q8i-n0z84jNdVpGuXuExOADjD7vc_ilYFjJ3Yl0XNEPLbDrV4jeL-76HiXkf6lEOaAJLlkR6Mu5lHqElGGVhuZja3ms_GxmY32fonPWCWKZV-FX5eb3-ZlIFM6-vaLDDXbs_f6hw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)