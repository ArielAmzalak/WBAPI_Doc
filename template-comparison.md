![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-comparison%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)
  + [Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)
  + [Componentes](/docs/whatsapp/business-management-api/message-templates/components)
  + [Management](/docs/whatsapp/business-management-api/message-templates/template-management)
  + [Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)
  + [Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)
  + [Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)
  + [Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)
  + [Review](/docs/whatsapp/business-management-api/template-review)
  + [Languages](/docs/whatsapp/business-management-api/message-templates/supported-languages)
  + [Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)
  + [Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)
  + [Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)
  + [Groups](/docs/whatsapp/business-management-api/message-templates/template-groups)
  + [Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)
  + [Time-to-live](/docs/whatsapp/business-management-api/time-to-live)
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
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Template Comparison](#template-comparison)

[Requirements](#requirements)

[Limitations](#limitations)

[Comparing templates](#comparing-templates)

[Request Syntax](#request-syntax)

[Query parameters](#query-parameters)

[Timeframes](#timeframes)

[Response](#response)

[Response contents](#response-contents)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template Comparison

You can compare two templates by examining how often each one is sent, which one has the lower ratio of blocks to sends, and each template's top reason for being blocked.

## Requirements

* A [User](/docs/whatsapp/business-management-api/get-started#user-access-tokens) or [System User](/docs/whatsapp/business-management-api/get-started#system-user-access-tokens) access token.
* The [whatsapp\_business\_management](/docs/permissions/reference/whatsapp_business_management) permission.

## Limitations

* Only two templates can be compared at a time.
* Both templates must be in the same WhatsApp Business Account.
* Templates must have been sent at least 1,000 times in the queries specified timeframe.
* Lookback windows are limited to 7, 30, 60 and 90 days from the time of the request.

## Comparing templates

Use the [WhatsApp Message Template > Compare](/docs/graph-api/reference/whats-app-business-hsm/compare) endpoint to target one template and compare it with another.

### Request Syntax

```
GET /<WHATSAPP_MESSAGE_TEMPLATE_ID>/compare
  ?template_ids=[<TEMPLATE_IDS]
  &start=<START>
  &end=<END>
```

### Query parameters

| Placeholder | Description |
| --- | --- |
| `<WHATSAPP_MESSAGE_TEMPLATE_ID>` | ID of the WhatsApp Message Template to target. |
| `<TEMPLATE_IDS>` | ID of the WhatsApp Message Template to compare the target to. |
| `<START>` | UNIX timestamp indicating start of timeframe. See [Timeframes](#timeframes). |
| `<END>` | UNIX timestamp indicating end of timeframe. See [Timeframes](#timeframes). |

### Timeframes

Timeframes (lookback windows) are limited to 7, 30, 60 and 90 days from the time of the request. To define a timeframe, set your end date to the current time as a UNIX timestamp, then subtract the number of days for your desired timeframe, in seconds, from that value:

* Subtract `604800` for a 7 day window.
* Subtract `2592000` for a 30 day window.
* Subtract `5184000` for a 60 day window.
* Subtract `7776000` for a 90 day window.

### Response

Upon success, the API will return a list of [WhatsApp Business Template Comparison](/docs/graph-api/reference/whats-app-business-hsm-comparison/) nodes describing each template's block rate, number of times sent, and top reason for being blocked.

```
{
  "data": [
    {
      "metric": "BLOCK_RATE",
      "type": "RELATIVE",
      "order_by_relative_metric": [<ORDER_BY_RELATIVE_METRIC>]
    },
    {
      "metric": "MESSAGE_SENDS",
      "type": "NUMBER_VALUES",
      "number_values": [<NUMBER_VALUES>]
    },
    {
      "metric": "TOP_BLOCK_REASON",
      "type": "STRING_VALUES",
      "string_values": [<STRING_VALUES>]
    }
  ]
}
```

### Response contents

| Placeholder | Description |
| --- | --- |
| `<ORDER_BY_RELATIVE_METRIC>` | Array of template ID strings, in increasing order of block rate (ratio of blocks to sends). |
| `<NUMBER_VALUES>` | Array of message send number value objects. Objects have the following properties:    * `key` — *String.* WhatsApp Message Template ID. * `value` — *Integer.* Number of times sent in a template message. |
| `<STRING_VALUES>` | Array of top block reason string value objects. Objects have the following properties:    * `key` — *String.* WhatsApp Message Template ID. * `value` — *String.* Top block reason.   Block reasons can be:    * `NO_LONGER_NEEDED` * `NO_REASON` * `NO_REASON_GIVEN` * `NO_SIGN_UP` * `OFFENSIVE_MESSAGES` * `OTHER` * `OTP_DID_NOT_REQUEST` * `SPAM` * `UNKNOWN_BLOCK_REASON`   See the [View metrics for your WhatsApp Business message template](https://www.facebook.com/business/help/511126334359303/) help center topic for descriptions of these reasons. |

### Example request

```
curl -X GET 'https://graph.facebook.com/v24.0/5289179717853347/compare?template_ids=[1533406637136032]&start=1674844791182&end=1674845395982' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [
    {
      "metric": "BLOCK_RATE",
      "type": "RELATIVE",
      "order_by_relative_metric": [
        "1533406637136032",
        "5289179717853347"
      ]
    },
    {
      "metric": "MESSAGE_SENDS",
      "type": "NUMBER_VALUES",
      "number_values": [
        {
          "key": "5289179717853347",
          "value": 1273
        },
        {
          "key": "1533406637136032",
          "value": 1042
        }
      ]
    },
    {
      "metric": "TOP_BLOCK_REASON",
      "type": "STRING_VALUES",
      "string_values": [
        {
          "key": "5289179717853347",
          "value": "UNKNOWN_BLOCK_REASON"
        },
        {
          "key": "1533406637136032",
          "value": "UNKNOWN_BLOCK_REASON"
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template Comparison](#template-comparison)

[Requirements](#requirements)

[Limitations](#limitations)

[Comparing templates](#comparing-templates)

[Request Syntax](#request-syntax)

[Query parameters](#query-parameters)

[Timeframes](#timeframes)

[Response](#response)

[Response contents](#response-contents)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Z6_dPtg2okfnorb6N-7A9g&oh=00_AfitYEkP719WUUFfhRxzUFS9Fzx-peoe_5upKWUTzOh1UQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Z6_dPtg2okfnorb6N-7A9g&oh=00_Afjlf98ZlRVTk2LYO3HZRWeGlwxDsIh9k5cVi8mFUiqnUg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Z6_dPtg2okfnorb6N-7A9g&oh=00_AfjiO_eQYBsahwddD9BIRLUKs48m1Ze0dJCl6j6WKhRSmQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Z6_dPtg2okfnorb6N-7A9g&oh=00_AfiQuQNSjQQMGHKpB83lFDE7D9OrqlBK8NkEv4iNzecasg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Z6_dPtg2okfnorb6N-7A9g&oh=00_AfhXrbSiRfpzvmEM54oosl3aa1G9UfkRhKyskzxdvoW7TA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT11UDdsSEbzmw1WwPjlt7T98a-XedrPwVH6sCbX_J53SUlt8fkE7Fd-QzaSUusqtOdC2EmrrH3d4qDiSMVUXk7PB7ma-cqOPIMcKp133k9lYTbd-TMPeu8IO39GpQFxGPLafl3_T4zmbaM9HJUCSw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)