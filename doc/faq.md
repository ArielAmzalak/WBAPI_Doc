![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Ffaq%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[FAQ](/docs/whatsapp/cloud-api/groups/faq)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Groups API FAQ](#groups-api-faq)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Groups API FAQ

### What happens when I delete a group?

* No members, including you, will be able to message the group.
* If any messages or statuses were received by Cloud API before the group was deleted, you may still receive webhooks for those.

### Why can’t a participant join the group using my invite link?

Some possible reasons include:

* The invite link may have been deleted.
* You may have removed the participant from the group previously.
* The group may already be full.

### How can I send my invite link to users?

* You can send the invite link over a 1:1 conversation.
* A new utility template is available in the [Template Library](https://business.facebook.com/wa/manage/template-library) to [send group invite links](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/reference#send-group-invite-link-template-message).
* You may also create custom, free-form marketing templates.

### What countries is Groups available in?

* Groups is available in [all countries Cloud API is available in](https://developers.facebook.com/docs/whatsapp/cloud-api/support/#country-restrictions).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Groups API FAQ](#groups-api-faq)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfiytKhmQCsp1fYIc4dKD7pFw0RNo3xJGr1KQkOQLvWQzg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfgN9Z7NniRALx_3-Z2-Bzv0j1OS-31byDOGynyRa-7AEw&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfiYHQU8kRJDu3q-KMGxHefK483Ht8IdYB5_JpdVln2VpQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1BzVdYHhKYZ7ugh9efAp3l20Zzxz9yAprXWHIrCiqP5vdGP-pUMSkKKJcGNeQoy4DX3z4p4HKLyQATr5PKNjHaReBsTer6mfcQjmy4j5ux2SBrDf0ijQoJ22Wvk8DjIR2Gji1vImMhLuLcYAREAg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfhE_OT7WXT4WjzioYEXlkXCNgkJ2b-lUmlu5ZN7J35x-A&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1RDljGTAqLrJ0uK6OZBlQMZWfUHF9F0c1xRi_ogoJ84FrvoEAo1jlGbm6gFDoWnXUGAAa0KRv_SxMa10lsMtiQ_F7bAStIpX0IJxIdsNOYHnq9Y7yZgQMfzTd1EwXgBCgceN3kmosmzc4R3d8s2TBsHEefie8Wsds)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfhR4Gyb9Kzt7UjJHCxgpKWyzF1xKgrCdajOvEXUsm_tiQ&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2Sh-UEpSIg4whGKEiRxw5mde5Y8GjnkcDzYMkIt4-4GdASRejwSUOrkys7q_YXq8RJCgaMc_lRqDW_0Stqaqwlc8hYsWgWujVr4y5KJSctNNtBQUhLmtug_jJqp7KEnqa3wtclRlGFecdArhCJrg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfgtnoBbvEgIMpnuG9xannwiU9PnP8n4XaJdvZUOWT6WeQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT31PdICXc0Ab4LxvMvJtVPMgpL45rf8aVblQzlVDt9WvV7Wc-pw7aA1RkWLxTSksBQqPvVRaqyTLZsbPBysb-nRRYCcHNwhUjwcT__qMb29A0jA0gsJCtx2K565AG38k9MEsOsLG7jiG9prf7E-HQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3FIsMIrVe9YcKOZt1UcvgBPWREuCZdjk7wmrMlxL_dDvQ8lUi1YCMtGrbK3eqg1Gn3e6WuCRT0RgWnJH8PMQLCqPiApjauM-ioF314z7FTIAtvuhp3X_a8dGrXFhQ-WgO7db008u0DcmwdyYBElQ)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0hgY-BRoRY65PMRSdB-ZohzKlPv08QaJS6UciVJdt8tmEVrNR-vCA4oCqqdfC4OP6QSF2su717L8jYCGac9l43PNanwO-6S3iO2S4YVxCo2li1GDLksO-WqE6uK3W0Y_jEZtYDatIZF8BnBaCIkw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfipCqGsCpSK7b3AuqvsNpMkFHn-XC5EONraStFue60bgw&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_Afg8F9LGakebI0SLoNwYk8KxUB4UMqCzkKeSGzaKKUYxXA&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1bq0S_O6xse0KlvOqDgg2YuIAC6urgLu_6ci-Pqr8t3bpfIhq4SJa-wmm3AD3nAwogi_hXm7AHoHXlmN5LWNMqhqOJY29UlogVadcS8hfJB_2QKBwl1G8sdX5lemJDdG-IdC0h399uzjf6M_UgnA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_Afg85bMxj50bjImJ9YGFotduI39LQEpliv7xXnavecGfhg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1m2chFCxiDuqrRYYJCOApoxrfEwnRS42sNQDZbrAaXEpZjG0xHX5wqZsE1xACeSGui0TDXzEFPE17icc-TC87UyQSJPDZx1cSg2gpqZ-INcrs3tf1SmuigajFuEbs3991BmDANhWzJsOienHQKvw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_Afhbqad5vLh19N_ZrZtxVbEpesVh5fpOCEtr65g5fM_sew&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT01VhQI1TY0M0HeC9T7sMvIJfzg--Kl3tHmfHJBHWmwt4naUSTdy6aTittWzk5z6RP8em7UBpzoq9qN9yKhVSMnsV1RdpXF8r6kit9kpvr5hM7W-O2QNzF71dvEQweWUdcJqIkUZUOBBf1hFD-dIQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BbTSolgdW247vBledVsAUQ&oh=00_AfhQqaDW52_2VkfvGHR1_z0XBRF1IuNqTUXpgI5g4lXt6A&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3kMecyAdEWF_Kt3OpA2tPOT-xEpxUCw_IgPmS46rvfDm9FBIUMLVHkv-1gXdkUxPo8stvqERek6f3jgVL3ZlU9bfDLkgjd8_7pRVS9m4KA5XI6uwKt0fhwg3hln9US4qtgMy0h0JKl27RuFgHqnw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ohdYnNPGX90WoXLfqO_qvw9cXIyPC5IuNkP0ztcJXljYfW3KHirHxKcGyEycuW9AQnDJr_4puprZnUZGAzNk8bcIKFkpynGHlaZtzM3j2Kdj6O0JxFyr8ehtVSVz-Pljym45SiM0-jdExrGPtIw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)