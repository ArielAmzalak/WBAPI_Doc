![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Fbulk-management%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Bulk management](/docs/whatsapp/business-management-api/authentication-templates/bulk-management)

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

[Bulk management](#bulk-management)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Bulk management

Use the [POST /<WABA\_ID>/upsert\_message\_templates](/docs/graph-api/reference/whats-app-business-account/upsert_message_templates/#Creating) endpoint to bulk update or create authentication templates in multiple languages that include or exclude the optional security and expiration warnings.

If a template already exists with a matching name and language, the template will be updated with the contents of the request, otherwise, a new template will be created.

### Request syntax

```
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/upsert_message_templates
```

### Post Body

```
{
  "name": "<NAME>",
  "languages": [<LANGUAGES>],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": <ADD_SECURITY_RECOMMENDATION> // Optional
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": <CODE_EXPIRATION_MINUTES> // Optional
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "<OTP_TYPE>",
          "supported_apps": [
            {
              "package_name": "<PACKAGE_NAME>", // One-tap and zero-tap buttons only
              "signature_hash": "<SIGNATURE_HASH>" // One-tap and zero-tap buttons only
            }
          ]
        }
      ]
    }
  ]
}
```

### Properties

All [template creation properties](/docs/whatsapp/business-management-api/authentication-templates#properties) are supported, with these exceptions:

* The `language` property is not supported. Instead, use `languages` and set its value to an array of [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages) strings. For example: `["en_US","es_ES","fr"]`.
* The `text` property is not supported.
* The `autofill_text` property is not supported.

### Example copy code request

This example creates three authentication templates in English, Spanish, and French, with copy code buttons. Each template is named "authentication\_code\_copy\_code\_button" and includes the security recommendation and expiration time.

```
curl 'https://graph.facebook.com/v24.0/102290129340398/upsert_message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_copy_code_button",
  "languages": ["en_US","es_ES","fr"],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": true
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": 10
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "COPY_CODE"
        }
      ]
    }
  ]
}'
```

### Example one-tap autofill request

This example (1) updates an existing template with the name "authentication\_code\_autofill\_button" and language "en\_US", and (2) creates two new authentication templates in Spanish and French with one-tap autofill buttons. Both newly created templates are named "authentication\_code\_autofill\_button" and include the security recommendation and expiration time.

```
curl 'https://graph.facebook.com/v24.0/102290129340398/upsert_message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_autofill_button",
  "languages": ["en_US","es_ES","fr"],
  "category": "AUTHENTICATION",
  "components": [
    {
      "type": "BODY",
      "add_security_recommendation": true
    },
    {
      "type": "FOOTER",
      "code_expiration_minutes": 15
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "OTP",
          "otp_type": "ONE_TAP",
          "supported_apps": [
            {
              "package_name": "com.example.luckyshrub",
              "signature_hash": "K8a/AINcGX7"
            }
          ]
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "data": [
    {
      "id": "954638012257287",
      "status": "APPROVED",
      "language": "en_US"
    },
    {
      "id": "969725527415202",
      "status": "APPROVED",
      "language": "es_ES"
    },
    {
      "id": "969725530748535",
      "status": "APPROVED",
      "language": "fr"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Bulk management](#bulk-management)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=gdBsz16XNogPMxXy_rw4Jw&oh=00_Afh7r9Z6BBig-o72rL9uRCQItZwr8g6eKPzK0IXtkXhWcg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=gdBsz16XNogPMxXy_rw4Jw&oh=00_Afgbnf7LJUPh02argZ58H7EcuBZ3hSW7beMcZxiaVWyGkA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=gdBsz16XNogPMxXy_rw4Jw&oh=00_Afhfz_l9LOKzV4iRoDqsYu8QKiLvVoEWrR6QjATtDlr_cw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=gdBsz16XNogPMxXy_rw4Jw&oh=00_AfijYTiCoNZeWCCylw3hhbgX2MXlDo6QxOB0O6GlkyQZ4A&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=gdBsz16XNogPMxXy_rw4Jw&oh=00_Afhy5NkBLfN_qHvtQh1kET0IWJa3gQ68_JxcNW1xlfP7sQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0zUZMXjKkqTb8Bp_TxK9yG6FDGbsnSJNpm54eXt_n5L6360wqda-ExA5R8kw0XbZ1oaxEPjmCLfqZSob-ZQRX-ViXDk8nkrafB8-Ub2JMvBPQj487ERkw_Lp-YhbNTrLBmJGfZQyZU3H1UgZ6-6Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)