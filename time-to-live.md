![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Ftime-to-live%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Time-to-live](/docs/whatsapp/business-management-api/time-to-live)

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

[Time-to-live](#time-to-live)

[Defaults, Min/Max Values, and Compatibility Table](#defaults--min-max-values--and-compatibility-table)

[Customize the TTL](#customize-the-ttl)

[Valid message\_send\_ttl\_seconds property values](#valid-message-send-ttl-seconds-property-values)

[Example request](#example-request)

[Sample Response](#sample-response)

[When TTL is exceeded: Dropped messages](#when-ttl-is-exceeded--dropped-messages)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Time-to-live

If we are unable to deliver a message to a WhatsApp user, we will retry the delivery for a period of time known as a time-to-live ("TTL"), or the message validity period.

You can customize the default TTL for authentication and utility templates sent via Cloud API, and for marketing templates sent via Marketing Messages Lite API ("MM Lite API").

We encourage you to set a TTL for all of your authentication templates, preferably equal to or less than your code expiration time, to ensure your customers only get a message when a code is still usable.

## Defaults, Min/Max Values, and Compatibility Table

|  | Authentication | Utility | Marketing |
| --- | --- | --- | --- |
| **Default TTL** | 10 minutes  30 days for authentication templates created before October 23, 2024 | 30 days | 30 days |
| **Compatibility** | Cloud API + On-Premise API | Cloud API only | Marketing Messages (MM) Lite API |
| **Customizable range** | 30 seconds to 15 minutes | 30 seconds to 12 hours | 12 hours to 30 days |

## Customize the TTL

To set a custom TTL on an authentication, utility, or marketing template, include and set the value of the `message_send_ttl_seconds` property in the `POST /<PHONE_NUMBER_ID>/message_templates` call.

You can change the TTL on a previously configured template using this method, as well.

TTL can be customized in 1 second increments.

### Valid `message_send_ttl_seconds` property values

* Authentication templates: `30` to `900` seconds (30 secs to 15 mins)
* Utility templates: `30` to `43200` seconds (30 secs to 12 hours)
* Marketing templates: `43200` to `2592000` (12 hours to 30 days)

For authentication and utility templates, you can set the `message_send_ttl_seconds` property value to `-1`, which will set a custom TTL of 30 days.

### Example request

```
curl 'https://graph.facebook.com/v21.0/102290129340398/message_templates' \
      -H 'Authorization: Bearer EAAJB...' \
      -H 'Content-Type: application/json' \
      -d '
      {
        "name": "test_template",
        "language": "en_US",
        "category": "MARKETING",
      	// Configure your TTL in seconds below
        "message_send_ttl_seconds": "120",
        "components": [
          {
            "type": "BODY",
            "text": "Shop now through {{1}} and use code {{2}} to get {{3}} off of all merchandise.",
            "example": {
              "body_text": [
                [
                  "the end of August","25OFF","25%"
                ]
              ]
            }
          },
          {
            "type": "FOOTER",
            "text": "Use the buttons below to manage your marketing subscriptions"
          },
        ]
      }'
```

### Sample Response

```

{
  "id": "572279198452421",
  "status": "PENDING",
  "category": "MARKETING"
}
```

### When TTL is exceeded: Dropped messages

Messages that are unable to be delivered within the default or customized TTL are dropped.

If you do not receive a [delivered message webhook](/docs/whatsapp/cloud-api/webhooks/payload-examples#status--message-delivered) before the TTL is exceeded, assume the message was dropped.

If you send a message that [fails to deliver](/docs/whatsapp/cloud-api/webhooks/payload-examples#status--message-failed), there could be a minor delay before you receive the webhook, so you may wish to build in a small buffer before assuming the message was dropped.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Time-to-live](#time-to-live)

[Defaults, Min/Max Values, and Compatibility Table](#defaults--min-max-values--and-compatibility-table)

[Customize the TTL](#customize-the-ttl)

[Valid message\_send\_ttl\_seconds property values](#valid-message-send-ttl-seconds-property-values)

[Example request](#example-request)

[Sample Response](#sample-response)

[When TTL is exceeded: Dropped messages](#when-ttl-is-exceeded--dropped-messages)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tnopLxNRqHx8HC28nW_L_g&oh=00_Afg1PnXXZVi01Nbt2L9GZ3DMuugn0UEwXpfNi5o0DMUdEg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tnopLxNRqHx8HC28nW_L_g&oh=00_AfjRYFO-rC1nh1txDXTYK8sz4xL7u-kVRIUO2SrVRpcjJQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tnopLxNRqHx8HC28nW_L_g&oh=00_Afgowjwd1Cy8QfeDNd5mMKPj23LNIcO6u41_o51TtPqdpQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tnopLxNRqHx8HC28nW_L_g&oh=00_Afh8J4zU19GqC8GPwNGHF1AqUvKjik1rMIEjOwNRJSbs_A&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tnopLxNRqHx8HC28nW_L_g&oh=00_Afh8OIZl5u3mtBYeWCHi52u3bRw3uay8cXt2i4W_CwgXMw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0DJqvhJzeXYzikrrIdbdLSEg0ywY3i1VTOjjokalLBmLWjqMdIjmBuETzppzuJylbw0OOD0Btiq-OT_MLci7izHTVEx0rqoW416qdzLBhs7_UWPyc9V70r_fcz2mm5U0V02QRoroeeD23FH8Fy4A)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)