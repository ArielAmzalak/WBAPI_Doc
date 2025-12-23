![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-pausing%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)

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

[Template pausing](#template-pausing)

[Pause Notifications](#pause-notifications)

[Unpausing](#unpausing)

[Appeals](#appeals)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template pausing

If a message template reaches the lowest quality rating (a status of **Active - Low quality** in WhatsApp Manager, or a `quality_score` of `RED` via API), it will automatically be paused for a period of time to protect the quality rating of phone numbers that have used the template. Pausing durations are as follows:

* 1st Instance: Paused for 3 hours
* 2nd Instance: Paused for 6 hours
* 3rd Instance: Disabled

When a message template is paused (status of **Paused**) it can't be sent to customers, so you should halt any automated messaging campaigns that rely on that template. Although you won't be charged for attempting to send a paused message template to a customer, and the attempt won't count against your messaging limit, the API will reject these attempts anyway. You should only resume these campaigns when the template's status has been set to Active again.

You may wish to edit a paused template if you feel that editing its content will reduce the amount of negative feedback it may receive and increase user engagement. Keep in mind, however, that once you edit a message template and resubmit it for approval, its status will change to In Review and it can't be sent to customers again until it has been re-approved and its status set to Active.

You may also wish to make changes to your business logic (targeting, delivery parameters, etc.) if you feel it is contributing to negative feedback or low engagement.

Pausing will initially not impact the business phone number from which the message template was sent. Other high quality message templates can continue to be sent from the phone number. However, if a business consistently sends message templates that reach a Low quality status, the phone number may eventually be impacted.

## Pause Notifications

When a message template has been paused we will notify you by WhatsApp Manager notification, email, and a [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update) webhook will be triggered.

### Unpausing

A template will unpause on its own after satisfying the pause duration outlined above. Once unpaused, the template's status will be set to **Active** and you may begin sending it to customers again. If you didn't halt any automated messaging campaigns that relied on a paused template, they should start working again. However, we recommend that you halt any campaigns that rely on a template that has been paused until it is unpaused, because our APIs will reject your requests anyway.

The template's [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality) will also be reset to a value based on the most recent customer feedback the template has received.

Similar to pause notifications, we will notify you by WhatsApp Manager notification, email, and webhook once the template's status has been set to Active.

Applies to businesses in Brazil, Colombia, and Singapore, starting September 12, 2023. Applies to all businesses starting October 12, 2023.

With the introduction of Template Pacing, we’re also introducing the ability to unpause any paused template through:

* The API by making a POST request to `/{whats_app_message_template_id}/unpause`
* WhatsApp Manager by clicking the **manually unpause it** link highlighted in the screenshots below.

Note that templates paused during Template Pacing must be manually unpaused (API or WhatsApp Manager) before they can be used again.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/554797102_3175363515964237_8084410644890844296_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=6d4n0JtDJbwQ7kNvwEToM-s&_nc_oc=AdnocPZBm7Nr8RxC5SQfOqPOZmGkDCxLxDOJRRi87QDSLaAhLMZ0XzNiYKrLdOIBKb8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=EVTWiUYGaScCy0n8RSaMTA&oh=00_AfhSbAQnKFgOBBDKslnchSxfv59F9M9w09p4mx_KHFmFXQ&oe=694053D8)![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/554106571_1492926028278417_4141428697407616298_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=ruyc6q-d6YQQ7kNvwFN-SCL&_nc_oc=Adl8jt_Er3LZg-T29dTI7CCcxpQLRiYR1Oq6AzZ7RnIkEqRZnf-5qz1Ox9U9O402Em4&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=EVTWiUYGaScCy0n8RSaMTA&oh=00_AfhKrpCH9yRla6idM8To-QLaevZEUlitD0gpGT0QmxDNqA&oe=694063D1)

### Appeals

If your submission is rejected you may file an appeal. Note that appeals must include a sample. If an approved template has become disabled, you may also edit it and resubmit it for approval.

In the WhatsApp Manager:

1. Mouseover the suitcase icon (**Account tools**) and click **Message templates**.
2. If you have multiple WhatsApp Business Accounts, use the dropdown menu in the top-right corner to select the account whose templates you want to manage.
3. Find the message template that you would like to edit and click it.
4. Edit the template's contents.
5. Click the **Add Sample** button and add sample variable values and images.
6. Click **Submit**.

The appeal will be reviewed and a decision made within 24 hours.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template pausing](#template-pausing)

[Pause Notifications](#pause-notifications)

[Unpausing](#unpausing)

[Appeals](#appeals)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tLRe5S6kcUrQdMq_IDcWBw&oh=00_AfiC6F8wLBYSFRBEpCCFFG10cMfwDdJRI3jF5_j85IRMIg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tLRe5S6kcUrQdMq_IDcWBw&oh=00_AfgVup6h68Sq__iuodYjxC4DUdzqSeM37DK2rAvRAPOByQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tLRe5S6kcUrQdMq_IDcWBw&oh=00_AfhWlmLyWFYvO_4DPwDrHRCz45EgZh-FcKh1WVsG-kAsgg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tLRe5S6kcUrQdMq_IDcWBw&oh=00_Afggmy8SSoZBrWN3CuQ12bKXMT9APaMWvuYTVeDgCQ0DpQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tLRe5S6kcUrQdMq_IDcWBw&oh=00_Afg4JjXKEwGyUvuudIlyUqhX-XPWwBLJ0df2-OaZNqs7SQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2-CaZJZjm4D7lMn8GXM4IGKUH2G6_0EnzgOfmeONGtnvL4TiQFE4W2xcp8N1QjOTLckHHzpre5191vlMsKn5ptJb1n-u-FnAfPgQslO7_s0wJdix8DvVevs_8A2l1mbm-dY6Gfasokr5OMj03zOg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)