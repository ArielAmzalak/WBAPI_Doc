![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-pacing%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)

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

[Template pacing](#template-pacing)

[Utility template pacing](#utility-template-pacing)

[API Behavior](#api-behavior)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template pacing

Template pacing is a mechanism that allows time for customers to provide early feedback on templates. This identifies and [pauses templates](/docs/whatsapp/message-templates/guidelines#template-pausing) that have received poor feedback or engagement, giving you enough time to adjust their contents before they are sent to too many customers, thereby reducing the likelihood of negative feedback impacting your business.

Template pacing is valid for marketing and utility templates. Newly created templates, paused templates that are unpaused, and templates that may have been created previously but don’t have a `GREEN` quality rating are potentially subject to pacing. Template quality history — for example, low quality resulting in a template pause — is one of the primary reasons for template pacing and you may see other templates get paced.
When a template is paced, messages will be sent normally until an unspecified threshold is reached. Once this threshold is reached, subsequent messages using that template will be held to allow enough time for customer feedback. Once we receive a good quality signal, subsequent messages using that template will be scaled to the entire target audience. If we receive a bad quality signal, subsequent messages using that template will be dropped, giving you the opportunity to adjust content, targeting, etc.

## Utility template pacing

Utility templates are subject to pacing only if you have had a utility template paused. Once a utility template has been paused, newly created templates, paused templates that are unpaused, and templates that may have been created previously but don’t have GREEN quality rating are potentially subject to pacing for the next 7 days.

## API Behavior

The immediate response from the messages endpoint will indicate if the message was sent or held with the new `message_status` property in the `messages` object. This response will be available on all versions of the API.

* Cloud API will always include a `message_status` property that will have a value of `accepted` for messages that are processed, and `held_for_quality_assessment` for messages that are held. Messages that are accepted will trigger the `sent` and `delivered` webhooks when they are actually sent (this is the same behavior that existed before pacing). A full example response can be found in the Cloud API docs.

If the feedback is positive and changes the template's quality rating to high quality, the held messages will be released and sent normally. The `message_template_quality_update` will send the quality update and the `messages` webhook will send the sent and delivered updates.

If the feedback is negative and changes the template's quality to low quality:

* The template's `status` will be set to `PAUSED`
* A `message_template_status_update` will be sent with an event value of `paused`
* Each held message will be dropped and trigger a `messages` webhook with `"status":"failed"` and `"code":"132015"` (Cloud API users).
* A `message_template_quality_update` webhook will be triggered with the quality change
* Admins of the WhatsApp Business Account owning business will be informed of the dropped messages by Meta Business Suite notification, WhatsApp Manager banner, and email

See [Template Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing) to learn how to unpause a template that has been paused due to pacing.

Note that we have internal guardrails in place to ensure that we evaluate and make a pacing decision within a reasonable time to avoid impact on time sensitive campaigns. Our goal is that even if paced, campaign messages with highest throughput still get delivered within an hour (99 percentile).

Thus, if our internal guardrails are reached before a template has received enough feedback to change its quality to high or low, the held messages will be released normally along with any appropriate messages webhooks.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template pacing](#template-pacing)

[Utility template pacing](#utility-template-pacing)

[API Behavior](#api-behavior)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=0Y3twSs6BDIvB_V7WqET7Q&oh=00_Afiyvr9f4HYiyiIpuKLwlzzMUOucXuzlzX6OS_D2uEMOyA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=0Y3twSs6BDIvB_V7WqET7Q&oh=00_AfhT5RT_UlIXsFDVIRKn6-mKyTRroLg-wBl5u_72f2payA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=0Y3twSs6BDIvB_V7WqET7Q&oh=00_AfiJzadSAwakmWPLRIRurkcZuHn3XDNG0aYe1ZJGy210CQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=0Y3twSs6BDIvB_V7WqET7Q&oh=00_AfguC1AVVcM8iEy1HfvfrEGmgdvfyHPuA98RmvSaT_nycg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=0Y3twSs6BDIvB_V7WqET7Q&oh=00_AfgZzb5v7hZFTeYGRJDly4AAEjg1RPGBx5YWUD4UnS5Wvw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1C-8B3aLsFHOFROS5OHaHMnPtloV-x3a93Iy-Yrqn-G2PmSorZ_VmbmA9QtJM_jk-RK_Xy5ZQFvApyjy0_5zWSz-QZSX_XiRd963IRL7Xu_2DREQBpdgG0C8dt4m_qa-wXzzATmaRFdlGz6wuV-w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)