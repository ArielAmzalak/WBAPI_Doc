![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fguides%2Fhow-to-monitor-quality-signals%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)[Guides](/docs/whatsapp/business-management-api/guides)[Monitorar sinais de qualidade](/docs/whatsapp/guides/how-to-monitor-quality-signals)

[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)

* [Começar](/docs/whatsapp/business-management-api/get-started)
* [Access tokens](/docs/whatsapp/access-tokens)
* [Permissions](/docs/whatsapp/permissions)
* [Configuração de webhooks](/docs/whatsapp/business-management-api/guides/set-up-webhooks)
* [Guides](/docs/whatsapp/business-management-api/guides)

  + [Análise](/docs/whatsapp/business-management-api/analytics)
  + [Templates](/docs/whatsapp/business-management-api/guides/templates-stub)
  + [Recuperar números de telefone](/docs/whatsapp/business-management-api/manage-phone-numbers)
  + [Migrate numbers via Embedded Signup](/docs/whatsapp/business-management-api/guides/migrate-numbers-via-es-redirect)
  + [Migrate Numbers Programmatically](/docs/whatsapp/business-management-api/guides/migrating-phone-numbers-between-wabas-programmatically)
  + [QR codes](/docs/whatsapp/business-management-api/qr-codes)
  + [Monitorar sinais de qualidade](/docs/whatsapp/guides/how-to-monitor-quality-signals)
  + [Welcome Message Sequences](/docs/whatsapp/business-management-api/ads/welcome-message-sequences)
* [Referência](/docs/whatsapp/business-management-api/reference)
* [Error Codes](/docs/whatsapp/business-management-api/error-codes)

Nesta Página

[Monitor Quality Signals](#monitor-quality-signals)

[Monitor Quality Signals Programmatically](#monitor-quality-signals-programmatically)

[Phone Numbers](#phone-numbers)

[Message Templates](#message-templates)

[Check Quality Signals on the UI](#check-quality-signals-on-the-ui)

[Phone Numbers Tab](#phone-numbers-tab)

[Message Templates tab](#message-templates-tab)

[Implement Internal Trackers](#implement-internal-trackers)

[Voltar para Português (Brasil)](/docs/whatsapp/guides/how-to-monitor-quality-signals/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 17 de nov
Atualização em Português (Brasil): 1 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Monitor Quality Signals

It is important to build and maintain a high quality customer experience on WhatsApp, so that customers can keep using this channel to communicate with your business.
To protect our users, WhatsApp has a reporting and blocking mechanism. If a user doesn't like the experience they get, they might block or report your business number.

A block or report action against your business keeps you from contacting those users and impacts your phone number reach and the template availability. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs and [Message Template Guidelines](/docs/whatsapp/message-templates/guidelines) docs.

To help you keep a high quality experience for your customers, we recommend that you **monitor the quality signals** (via WhatsApp Business Management API and WhatsApp Manager UI) to assess how your messages are being received by users and act on relevant updates as quickly as possible.

## Monitor Quality Signals Programmatically

We recommend using [webhooks](/docs/whatsapp/business-management-api/webhooks) to monitor phone number and message template quality. Then, you can act whenever there is a need, like when quality is Low or status is Flagged.

If the information you need is still not available via webhooks, you can alternatively call the [WhatsApp Business Management API](/docs/whatsapp/business-management-api).

The following webhooks and APIs provide real-time information and updates. For now, they don't provide historical data —check the next section of this document to learn how to use the WhatsApp Manager UI to get the last 30 days’ quality ratings.

### Phone Numbers

#### [Webhooks](/docs/whatsapp/business-management-api/webhooks)

To get notified when a phone number quality status changes, subscribe to the `phone_number_quality_update` webhook. You must subscribe to each WhatsApp Business Account you'd like to get the updates.

**What to watch for:** the **Flagged** status in WhatsApp Manager, or a `phone_number_quality_update` webhook with `EVENT` set to `FLAGGED`. Flagged status occurs when the quality rating reaches a low state. If the message quality improves to a high or medium state and maintains this for 7 days, your business phone number status will return to **Connected** in WhatsApp Manager, and its [`status` field](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#fields) will be set to `CONNECTED`. If the quality rating doesn't improve within 7 days, however, it will still return to a connected status, but its messaging limit will be downgraded. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs.

#### [API](/docs/whatsapp/business-management-api/phone-numbers)

Make [this call](https://developers.facebook.com/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers) once in a while to follow your phone number’s quality rating:

```
curl -X GET \
'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/phone_numbers?access_token=<ACCESS_TOKEN>'
```

Be mindful these calls will count against the [API limits](/docs/whatsapp/business-management-api/using-the-api#api-limits), while the webhooks will not.

**What to watch for:** Any quality ratings different than **High**. They indicate negative feedback from users and may impact the phone number reach. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs.

### Message Templates

#### [Webhooks](/docs/whatsapp/business-management-api/webhooks)

Subscribe to the `message_template_status_update` webhook to get notified when the message template status changes, by being approved or rejected, or if it has been disabled. You must subscribe to each WhatsApp Business Account you'd like to get the updates.

## Check Quality Signals on the UI

On **Business Manager**, go to the **WhatsApp Manager** and look for the following tabs:

### Phone Numbers Tab

* Check the current phone number quality rating column. Mouse over to see the reason users gave for their negative feedback, if available.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=590562328518557&version=1760728552)

* Go to Insights and check the quality for the last 30 days.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=3941097566008054&version=1760728552)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=835125220736155&version=1760728552)

### Message Templates tab

* Check the current message template quality rating column:

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=586129649018947&version=1760728552)

## Implement Internal Trackers

We also recommend you to implement your own internal trackers on the chat thread. This way, once you receive a signal on webhooks that indicates negative feedback from users or low read-rates (quality rating = medium or low, status = Flagged), you can investigate your own trackers to try to understand where you can improve the chat experience.

As an example, these are a two places you can add internal trackers to:

#### Response time

Monitor how much time it takes for you to answer client messages. Ideally this should be instant, so watch out for increases and peaks. Important metrics: first message response time and average response time.

#### Customer messaging journey steps

Check if users are getting through the entire messaging journey you planned.

A few questions to help you analyze metrics:

* Are users dropping on an unexpected step?
* Is there a specific message that is causing confusion?
* Are users getting looped in a sequence of steps?
* Are users completing the final action you want them to perform?

With this measurement in place you can run A/B testing and see if changes in the experience improves user feedback. Some things you could try to test if it improves the experience:

* Change the phrasing
* Split the question into more questions,
* Aggregating multiple questions into one

After the test, analyze the new metrics and compare them to the old ones.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Monitor Quality Signals](#monitor-quality-signals)

[Monitor Quality Signals Programmatically](#monitor-quality-signals-programmatically)

[Phone Numbers](#phone-numbers)

[Message Templates](#message-templates)

[Check Quality Signals on the UI](#check-quality-signals-on-the-ui)

[Phone Numbers Tab](#phone-numbers-tab)

[Message Templates tab](#message-templates-tab)

[Implement Internal Trackers](#implement-internal-trackers)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=AEg3dGaKXK3nTZ-Hjc7azg&oh=00_Afh39cZJjsYvluxS4HwNYaKcf5cxgyBqK7xx-CO9fMLnVQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=AEg3dGaKXK3nTZ-Hjc7azg&oh=00_AfieMhTn4fZH269rab2HVXsI9tN3VwA-XVLjsP_sbj8VFA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=AEg3dGaKXK3nTZ-Hjc7azg&oh=00_Afi86bPMDk7NwTBRA14pb7t43wcn67DVNps60vGkaIyhqg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=AEg3dGaKXK3nTZ-Hjc7azg&oh=00_AfjkDxi2D5ojT_fJprlrw30Kh57tSmGwnisuR6DV2lArzg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=AEg3dGaKXK3nTZ-Hjc7azg&oh=00_AfjgmlOmES65yFXg0NXVCqGB4f8TyHMDy2FeKdGF7i_m9Q&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0HvQXsmu7B0mCtHZL_f-hgnNp0IVGTQaFu_iHKIP4mrXvYP7pdXv_-YCGg6ZH-R2UIkgD3Jr10Tk4zIwMCk1Ptrle8zEdRLLqKFITlNrAIx53N_PrpnnF1wdsfxkvfETrhf75LDDjusJMX9WfUsw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)