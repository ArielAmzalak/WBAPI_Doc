![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Faccount_alerts%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts)

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

[account\_alerts webhook reference](#account-alerts-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `account_alerts` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account `account_alerts` webhook.

The **account\_alerts** webhook notifies you of changes to a business phone number's [messaging limit](/docs/whatsapp/messaging-limits/), [business profile](/docs/whatsapp/cloud-api/phone-numbers#business-profiles), and [Official Business Account](/docs/whatsapp/overview/business-accounts#official-business-account) status.

## Triggers

* An increase to the messaging limit of all of a business portfolio's phone numbers is denied, a decision on the increase has been deferred, or more information is needed before a decision can be made.
* A business phone number Official Business Account status is approved or denied.
* A business phone number's business profile photo is deleted.

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
          "field": "account_alerts",
          "value": {
            "entity_type": "<ENTITY_TYPE>",
            "entity_id": "<ENTITY_ID>",
            "alert_info": {
              "alert_severity": "<ALERT_SEVERITY>",
              "alert_status": "<ALERT_STATUS>",
              "alert_type": "<ALERT_TYPE>",
              "alert_description": "<ALERT_DESCRIPTION>"
            }
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
| `<ALERT_DESCRIPTION>`  *String* | Alert description.  Values can be:   * `Additional verification is required for your business {NAME}. Go to Security Center in Meta for Business to complete identity verification. To continue without completing additional verification, your business can use WhatsApp Business platform actively for several days and follow our messaging policies.` * `Based on your activity, limits cannot be increased for your business. Contact support for more information.` * `Limits cannot be increased for your business <BUSINESS_PORTFOLIO_NAME>. Use WhatsApp Business platform actively for several days and follow our messaging policies.` * `Limits cannot be increased at this time for your business <BUSINESS_PORTFOLIO_NAME>. Limits cannot be increased as your identity verification submission was rejected. To continue without additional verification, use WhatsApp Business platform actively for several days and follow our messaging policies.` * `Please reupload your profile picture` * `This phone number now has a green badge next to its name showing that it's an authentic and notable business account. Add more details to your business profile to increase customer trust.` * `We do not grant official business accounts to individuals. Your display name must be directly associated with your business. Edit the display name and submit a new request.` * `Your messaging quality was too low to unlock more capabilities at this time. Alternatively, your business can unlock more capabilities by submitting business documents to verify your business.` | `Limits cannot be increased for your business <BUSINESS_PORTFOLIO_NAME>. Use WhatsApp Business platform actively for several days and follow our messaging policies.` |
| `<ALERT_SEVERITY>`  *String* | Alert severity. Values can be:  `CRITICAL` — Indicates a rejection or denial. The `alert_description` value may describe actions that can be taken to resolve the underlying reason for the rejection or denial.  `INFORMATIONAL` — Indicates webhook contain only informational data and no action is needed.  `WARNING` — Indicates action may be needed. The `alert_description` value describes possible actions that can be taken. | `WARNING` |
| `<ALERT_STATUS>` | Alert status.  Values can be:   * `ACTIVE` * `NONE` | `ACTIVE` |
| `<ALERT_TYPE>`  *String* | Alert type.  Values can be:  `INCREASED_CAPABILITIES_ELIGIBILITY_DEFERRED` — Indicates we don't have enough message signal to make a determination, identity verification was rejected, or your message quality is too low. Possible solutions are to increase your [messaging limit](/docs/whatsapp/messaging-limits) or get your [business verified](https://www.facebook.com/business/help/2058515294227817).  `INCREASED_CAPABILITIES_ELIGIBILITY_FAILED` — Indicates messaging limits cannot be increased due to past messaging activity. Possible solutions are to [request an increase](/docs/whatsapp/messaging-limits#request-an-increase) or get your [business verified](https://www.facebook.com/business/help/2058515294227817).  `INCREASED_CAPABILITIES_ELIGIBILITY_NEED_MORE_INFO` — Indicates messaging limits cannot be increased due to past messaging activity. Possible solutions are to [verify your identity](https://www.facebook.com/business/help/587323819101032) or increase your [messaging limit](/docs/whatsapp/messaging-limits).  `OBA_APPROVED` — Indicates Official Business Account status approved.  `OBA_REJECTED` — Indicates Official Business Account ("OBA") status denied. Review OBA [criteria](/docs/whatsapp/overview/business-accounts#criteria) and edit your [display name](/docs/whatsapp/cloud-api/phone-numbers#display-names) after reviewing our display name guidelines.  `PROFILE_PICTURE_LOST` — Indicates the business phone number's business profile photo has been deleted. Upload a new photo using [WhatsApp Manager](/docs/whatsapp/cloud-api/phone-numbers#viewing-or-updating-your-profile-via-whatsapp-manager) or the [API](/docs/whatsapp/cloud-api/phone-numbers#updating-your-profile-via-api). | `INCREASED_CAPABILITIES_ELIGIBILITY_DEFERRED` |
| `<ENTITY_ID>`  *String* | Entity ID. Value can be a business portfolio ID or business phone number ID. | `506914307656634` |
| `<ENTITY_TYPE>`  *String* | Entity type. Values can be:  `BUSINESS` — Indicates a change associated with a business portfolio.  `PHONE_NUMBER` — Indicates a change associated with a business phone number.  `CURRENT_STATUS_ID` — Indicates a change associated with a business phone number's [business profile](/docs/whatsapp/cloud-api/phone-numbers#business-profiles). | `BUSINESS` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "time": 1745612159,
      "changes": [
        {
          "field": "account_alerts",
          "value": {
            "entity_type": "BUSINESS",
            "entity_id": "506914307656634",
            "alert_info": {
              "alert_severity": "WARNING",
              "alert_status": "ACTIVE",
              "alert_type": "INCREASED_CAPABILITIES_ELIGIBILITY_DEFERRED",
              "alert_description": "Limits cannot be increased for your business <BUSINESS_PORTFOLIO_NAME>. Use WhatsApp Business platform actively for several days and follow our messaging policies."
            }
          }
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[account\_alerts webhook reference](#account-alerts-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xl2XwVPJFjszd3iR7NeOZA&oh=00_AfjAOETq07ZE5HiRGIj4ys6mCgXDshalLKHzBM-Icxn8Qw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xl2XwVPJFjszd3iR7NeOZA&oh=00_AfhYbGxnGvlFYMgkl_sRMWEdrHEU2YwCcq7XV9aa9lR0Kg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xl2XwVPJFjszd3iR7NeOZA&oh=00_AfgfrNzrElaj__PblH-fFaBlVUZ7Cud3itrisr2BlJrrdA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xl2XwVPJFjszd3iR7NeOZA&oh=00_Afgf382rheT7bkGVv-a0_tGUV5TIusu-6eHbA78fra8YLA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=xl2XwVPJFjszd3iR7NeOZA&oh=00_AfjfgPcxCyQ1BtWFHplf0MIWbX8dcbYeOEBJOt_Ncdg7VA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2yW4abZHzOTwkNEKEq0ndEdV4l_d1fuDeywcSOF07qdgtml5f-WFuUt2HpJiQu_hKKBLHXXnCd02LMJ4vhWTkoy-l-RafWqJi0LUyJd0SIT_joZi9I_Jz0nlfe9xqYlZhcRVF1mtvsvR2R34o81g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)