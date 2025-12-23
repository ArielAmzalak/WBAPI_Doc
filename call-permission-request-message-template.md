![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fcall-permission-request-message-template%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)[Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)

    - [Custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates)
    - [Modelos de catálogo](/docs/whatsapp/business-management-api/message-templates/catalog-templates)
    - [Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template)
    - [Modelos de cupom](/docs/whatsapp/business-management-api/message-templates/coupon-templates)
    - [Modelos de oferta por tempo limitado](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates)
    - [Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates)
    - [Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates)
    - [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates)
    - [Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates)
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

[Call permission request message template](#call-permission-request-message-template)

[Create call permission request message template](#create-call-permission-request-message-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Send a call permission request message template](#send-a-call-permission-request-message-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example response](#example-response)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Call permission request message template

Create a call permission request template message that your business can send to users outside of the customer service window.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/543369275_3208571362625810_4384114346853497205_n.png?stp=dst-webp&_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=X0edjUjksi8Q7kNvwEyKhWI&_nc_oc=AdmCctuArgeQlCKiXhwWPeMdzM6Q1slC1fRw6M4AGXjF4M5rPIyBgidKSSRVg22DhEM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RduM1Q1ppK22DKX3lL0Yag&oh=00_AfhBYysPLXgSm3DdqoaDXStTFPuPtoz3HnhFzW9pw3jckA&oe=69406970)

## Create call permission request message template

### Request syntax

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates/?locale=en_US#Creating) endpoint to create a call permission request message template.

```
curl -X POST \
  'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "sample_cpr_template",
    "language": "en",
    "category": "<CATEGORY>",
    "components": [
      {
        "type": "BODY",
        "text": "We would like to call you to help support your order.",
      },
      {
        "type": "call_permission_request"
      }
   ]
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<CATEGORY>` | **Required.**  Template category  Marketing or Utility | `Marketing` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>` | **Required.**  Whatsapp business account ID. | `106540352242922` |

### Response syntax

```
{
  "id": "<ID>",
  "status": "<STATUS>",
  "category": "<CATEGORY>"
}
```

## Send a call permission request message template

### Request syntax

Use the [POST /<PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send a call permission request message template to a WhatsApp user.

```
curl -X POST \
  'https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>/messages' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<WHATSAPP_USER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<LANGUAGE_AND_LOCAL_CODE>"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "<BODY_TEXT>"
            }
          ]
        }
      ]
   }
}'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<BODY_TEXT>`  *String* | **Required.**  Body text. URLs are automatically hyperlinked.  Maximum 4096 characters. | `John Smith` |
| `<LANGUAGE_AND_LOCAL_CODE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Name of template. | `august_promotion` |
| `<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required.**  WhatsApp business phone number ID. | `106540352242922` |
| `<WHATSAPP_USER_PHONE_NUMBER>`  *String* | **Required.**  WhatsApp user phone number. | `+16505551234` |

### Example response

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

[Call permission request message template](#call-permission-request-message-template)

[Create call permission request message template](#create-call-permission-request-message-template)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Response syntax](#response-syntax)

[Send a call permission request message template](#send-a-call-permission-request-message-template)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IapyQqyFtddkPTpvsxBq1A&oh=00_AfhSj_sTPX458EFiNU_hFGSQQ9UXy0rm0ul_tdm0TY3BoA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IapyQqyFtddkPTpvsxBq1A&oh=00_AfgPnZB4HQcCz259vwxW9TNm3WQfddddhT7ior4EJqf02A&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IapyQqyFtddkPTpvsxBq1A&oh=00_AfjtB-p9UL1ND-pLlyHXLZ63qJ878SFa6VU8vbzQOBKJzA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IapyQqyFtddkPTpvsxBq1A&oh=00_AfgNDZT0IilNS4i6jpD32QcF9lJ2CuH8TNucX3PpBTf8lQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IapyQqyFtddkPTpvsxBq1A&oh=00_AfjEmqsbztGyvx7JmBRCAF1_lZd1lo6bqvhHix3NMJGxTw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3PCAkmyGGq8zPtnch6KxF_TAHBTmrSTs9TCUFyoelsarAB_m9VQlbZ47ve8jPIvLszw_LamUgWO5liuFoRoWDtAjRR1WZmfmZKfYedWbcwNCSGmLIEopJYgg12G6i-ba8-SgoQCByX2d_2ab95ZQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)