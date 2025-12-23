![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-messaging-limits%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)

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

[Per-user marketing template message limits](#per-user-marketing-template-message-limits)

[What is it?](#what-is-it-)

[Why it's important](#why-it-s-important)

[Aligning Per-User Marketing Limits with Upcoming Per Message Pricing Changes](#aligning-per-user-marketing-limits-with-upcoming-per-message-pricing-changes)

[How We Notify via Error Code](#how-we-notify-via-error-code)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Per-user marketing template message limits

**Upcoming changes**

*Starting March 3, 2025*, we will take into account the overall volume of personal and business messages in a user’s inbox in addition to their recent marketing message read rates when determining if a given WhatsApp user should receive fewer marketing template messages, and what their limit should be. This means that if a person has low inbox activity or they have not engaged with many of the marketing messages they received lately they may receive fewer marketing messages to ensure a healthy balance of messages in their inbox. From late Q2 we will also align the per user marketing limit with upcoming per-message pricing changes so that all marketing messages delivered will now count towards the per user marketing limit.

*Starting April 1, 2025*, we will temporarily pause delivery of all marketing template messages to WhatsApp users who have a United States phone number (a number composed of a +1 dialing code and a US area code). This pause is intended to allow us to focus on building a better consumer experience in the US, which will ultimately lead to improved outcomes for businesses. Attempting to send a template message to a WhatsApp user with a US phone number after this date will [result in an error](#how-we-notify-via-error-code).

## What is it?

WhatsApp may limit the number of marketing template messages a person receives from any business in a given period of time where users are less likely to be receptive and engage with them. This is determined based on a number of factors, including a dynamic view of an individual’s recent marketing message read rate and how many messages they currently have in their inbox from friends, family and businesses.
Starting April 1, 2025, to focus on building the consumer experience, WhatsApp will not deliver any marketing template messages to individuals with United States phone numbers (numbers composed of a +1 dialing code and a US area code).

## Why it's important

WhatsApp has found that per-user marketing template limits maximize marketing message engagement and improve the user experience, measured through improvements in user read rates and sentiment. This limit helps WhatsApp users find business messaging more valuable and feel less like they receive too many business messages.
How this Applies to Your Business

Our per user marketing limit adapts automatically over time based on a person’s recent engagement levels. While this may mean delivering fewer messages to some users during periods of lower marketing read rates or overall inbox activity, rest assured your ability to reach people when they are most engaged will not change.

## Aligning Per-User Marketing Limits with Upcoming Per Message Pricing Changes

Gradually rolling out from late Q2 2025, the per user marketing limit will align with upcoming per-message [pricing changes](/docs/whatsapp/pricing/). Previously, the limit only applied to marketing template messages that would normally open a new marketing conversation, and businesses could send one additional marketing template message if a marketing conversation is already open between you and a WhatsApp user.

Now businesses will be able to send an unlimited number of marketing messages, however each message delivered will now count towards the per user marketing limit. One exception is, if a person responds to a marketing message it will start a 24h [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows). Marketing messages sent within this window will not count towards a person’s limit.

## How We Notify via Error Code

If a marketing template message is not sent due to per-user marketing template limit enforcement, a messages webhook will be triggered with status set to failed and (error) code set to `131049` (for Cloud API).

If you do receive this error code and suspect it is due to the limit, wait at least 24 hours before resending the template message. Doing so will only result in another error response since the limit may be in effect for differing periods of time.

We will continue to refine our approach, and we appreciate your partnership as we invest in making WhatsApp the best possible experience for your business and your customers.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Per-user marketing template message limits](#per-user-marketing-template-message-limits)

[What is it?](#what-is-it-)

[Why it's important](#why-it-s-important)

[Aligning Per-User Marketing Limits with Upcoming Per Message Pricing Changes](#aligning-per-user-marketing-limits-with-upcoming-per-message-pricing-changes)

[How We Notify via Error Code](#how-we-notify-via-error-code)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=5kGAjqd1Ndk326BSa0D4iw&oh=00_AfjTK3GeSnnRiUWRftRDQ0FrSSGzHVKJnKmWkzCX9uyQzA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=5kGAjqd1Ndk326BSa0D4iw&oh=00_AfgSW6uTSpgbfVv-QfEFkQ-KjY0AHjAgS19dwBQUrQEHOg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=5kGAjqd1Ndk326BSa0D4iw&oh=00_AfjoOoeWFJ9CryM21fUQBs-5NX-w5XWl-U0jLrSzW59hBA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=5kGAjqd1Ndk326BSa0D4iw&oh=00_AfiNFvkLFBxvholjqFFb7lDmMEI-QO53klHQapB1cyJ8mA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=5kGAjqd1Ndk326BSa0D4iw&oh=00_AfhGXlu2zh87ZOA0ccExrIn6NTFZY2mRUXihJWrxgTFc2A&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2U8OKIrmYn_KDy_wFTpmf2Nk2anZJPlvWiQ6VsqYTyQR1bKt4qOIG068nVpDYXjbpSqCC98njbfpFo5KBkkId223r5xZZkwoXVjnwBavdVRtvQ0ppfcYO31YmVDeZ4dcXoPYmdbYqWMuk3-R7hsg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)