![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Ftemplate-preview%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Template preview](/docs/whatsapp/business-management-api/authentication-templates/template-preview)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)

    - [Preenchimento automático com um toque](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates)
    - [Zero-Tap](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates)
    - [Copy Code](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates)
    - [Authenticating Users](/docs/whatsapp/business-management-api/authentication-templates/authentication-best-practices)
    - [Bulk management](/docs/whatsapp/business-management-api/authentication-templates/bulk-management)
    - [Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals)
    - [Template preview](/docs/whatsapp/business-management-api/authentication-templates/template-preview)
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

[Template previews](#template-previews)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template previews

You can generate previews of authentication template text in various languages that include or exclude the security recommendation string and code expiration string using the [**GET /<WABA\_ID>/message\_template\_previews**](/docs/graph-api/reference/whats-app-business-account/message_template_previews/#Reading) endpoint.

### Request syntax

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_template_previews
  ?category=AUTHENTICATION,
  &language=<LANGUAGE>, // Optional
  &add_security_recommendation=<ADD_SECURITY_RECOMMENDATION>, // Optional
  &code_expiration_minutes=<CODE_EXPIRATION_MINUTES>, // Optional
  &button_types=<BUTTON_TYPES> // Optional
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<LANGUAGE>`  *Comma-separated list* | **Optional.**   Comma-separated list of [language and locale codes](/docs/whatsapp/business-management-api/message-templates/supported-languages) of language versions you want returned.   If omitted, versions of all supported languages will be returned. | `en_US,es_ES` |
| `<ADD_SECURITY_RECOMMENDATION>`  *Boolean* | **Optional.**   Set to `true` if you want the security recommendation body string included in the response.   If omitted, the security recommendation string will not be included. | `true` |
| `<CODE_EXPIRATION_MINUTES>`  *Int64* | **Optional.**   Set to an integer if you want the code expiration footer string included in the response.   If omitted, the code expiration footer string will not be included.   Value indicates number of minutes until code expires.  Minimum `1`, maximum `90`. | `10` |
| `<BUTTON_TYPES>`  *Comma-separated list of strings* | **Required.**   Comma-separated list of strings indicating button type.   If included, the response will include the button text for each button in the response.   For authentication templates, this value must be `OTP`. | `OTP` |

### Example request

```
curl 'https://graph.facebook.com/v17.0/102290129340398/message_template_previews?category=AUTHENTICATION&languages=en_US,es_ES&add_security_recommendation=true&code_expiration_minutes=10&button_types=OTP' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [
    {
      "body": "*{{1}}* is your verification code. For your security, do not share this code.",
      "buttons": [
        {
          "autofill_text": "Autofill",
          "text": "Copy code"
        }
      ],
      "footer": "This code expires in 10 minutes.",
      "language": "en_US"
    },
    {
      "body": "Tu código de verificación es *{{1}}*. Por tu seguridad, no lo compartas.",
      "buttons": [
        {
          "autofill_text": "Autocompletar",
          "text": "Copiar código"
        }
      ],
      "footer": "Este código caduca en 10 minutos.",
      "language": "es_ES"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template previews](#template-previews)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=vbEYsWClPgoelCOztNlFdQ&oh=00_Afjy0LA8_sdnB9fCzwcN983ThgbR8n3zpAK9Mif_MXd1jA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=vbEYsWClPgoelCOztNlFdQ&oh=00_Afi0n3LQ58TDK_MuUdEYHRRc9H6ftibaiKjequSwNDoZqA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=vbEYsWClPgoelCOztNlFdQ&oh=00_Afjmhu7k2mZa45mV4-W4-ZPEdz78e7aUF4qxLy8ZNhYv3Q&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=vbEYsWClPgoelCOztNlFdQ&oh=00_Afh3gqxlzUmrx-CAgL1aBzvuUH9jIfOAoT-EMhYGIB58bg&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=vbEYsWClPgoelCOztNlFdQ&oh=00_AfjAp3Uhloj6LfPGg6Fm59MkDwdovvrBrNSJ_fcGR5QvHA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0Vt9md6KRoOmylz96VO3-6GbaZLFA-q_WAZPoO4tB7zVkHsqCfOPsCt_3XfWXcqo4ny26vaZtZz9MGi45omOUSko0RjCjLnKvpIcUZCdh5F0NNrrejeDLNIUxKNtegDSbSMJif61VDyh2zqeqPmQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)