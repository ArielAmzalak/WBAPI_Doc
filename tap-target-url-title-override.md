![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsend-message-templates%2Ftap-target-url-title-override%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)

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

[Tap target title URL override](#tap-target-title-url-override)

[Request syntax](#request-syntax)

[Example request](#example-request)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Tap target title URL override

This document explains how to send approved message templates using the `tap_target_configuration` component within a template message. Tap target override enables image-based, text-based, and header-less message templates to function as interactive Call-to-Action URL buttons. These buttons display a custom title and open the destination linked to the first URL button.

WhatsApp Business Accounts (WABAs) must be fully verified and consistently maintain high-quality standards to ensure compliance and access to this component.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/520579996_716872931262110_1406523760843053750_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=5SGK-bdN_hYQ7kNvwEJeFUG&_nc_oc=AdmYPyD6LhwZd_UuDrHq_yb6gnmN7VPU_eLJO4z6KLh0-8AJXXHz5JeHacS32e-BwgU&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=WdAMW-KRCqnSrZ5WfzB42Q&oh=00_Afi6JaBVGXstSAgo0GERxPvy79Uiy81Retwh7E44eAxiDw&oe=69407F75)

## Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send a text message template to a WhatsApp user.

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "template",
  "template": {
    "name": "<TEMPLATE_NAME>",
    "language": {
      "code": "<LANGUAGE_AND_LOCALE_CODE>"
    },
    "components": [
      {
        "type": "tap_target_configuration",
        "parameters": [
          {
            "type": "tap_target_configuration",
            "tap_target_configuration": [
              {
                "url": "<URL>",
                "title": "<TITLE>"
              }
            ]
          }
        ]
      },
          <!-- Add additional components -->
    ]
  }
}
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<LANGUAGE_AND_LOCAL_CODE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Name of template. | `august_promotion` |
| `<TITLE>`  *String* | **Required.**  URL Title. | `Offer Details!` |
| `<URL>`  *String* | **Required.**  URL. | `https://www.luckyshrubs.com` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

## Example request

Example request to send a template message with the `tap_target_configuration` type.

```
curl 'https://graph.facebook.com/v24.0/106540352242922/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+1233214532",
  "type": "template",
  "template": {
    "name": "august_promotion",
    "language": {
      "code": "en"
    },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "image",
            "image": {
              "link": "https://www.luckyshrubs.com"
            }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          {
            "type": "text",
            "text": "Hello Andy..."
          }
        ]
      },
      {
        "type": "tap_target_configuration",
        "parameters": [
          {
            "type": "tap_target_configuration",
            "tap_target_configuration": [
              {
                "url": "https://www.luckyshrubs.com/",
                "title": "Offer Details"
              }
            ]
          }
        ]
      }
    ]
  }
}'
```

## Example response

```
{
   "messaging_product": "whatsapp",
   "contacts": [
       {
           "input": "+1233214532",
           "wa_id": "1233214532"
       }
   ],
   "messages": [
       {
           "id": "wamid.HBgLMTMyMzI4NjU2NzgVAgARGBJBQzRBRDBEMDEwQzVBM0M0QkIA",
           "message_status": "accepted"
       }
   ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Tap target title URL override](#tap-target-title-url-override)

[Request syntax](#request-syntax)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XjI8nfQTopIkZb1qn9txYA&oh=00_AfjHLZEBc81PdS3NPipPasL9BKqRL2fDsMHqiBiiiwdTjw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XjI8nfQTopIkZb1qn9txYA&oh=00_AfjoiAlufEi4gm_B0h4yPBOADbHKr0c7AgAmZJWCCDzH5Q&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XjI8nfQTopIkZb1qn9txYA&oh=00_AfgmTPWJD9nw6JyqIXJya4gel5ZYSsCnqAY_p6w2nVR8eA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XjI8nfQTopIkZb1qn9txYA&oh=00_Afgfjr2o4LhIxompDOv1LQnt-31Twz70S02EZLBHHmBw_w&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=XjI8nfQTopIkZb1qn9txYA&oh=00_AfisZ-iItQVshBxxgCYoEW8MtEw1ptyX9yM09bEFx_K9iA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0QfkRQp3vDcisi7iTxN5tqUt455_5AD3uiAuEsGYuCwSw_7Odcw7qO5Es1v6wDzcaVvF5lsyQbaKO-jqY7IiNTTFMrIho-PGAzDhOBdNq_6LehcNtmfvrWUYQePgoGuaBto6uxpTFjzkAEAGVIug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)