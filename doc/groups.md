![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)

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

[Groups API](#groups-api)

[How it works](#how-it-works)

[Get Started](#get-started)

[Quick Facts](#quick-facts)

[Analytics](#analytics)

[Limits](#limits)

[Pricing](#pricing)

[Features and reference](#features-and-reference)

[Group management features](#group-management-features)

[Group messaging features](#group-messaging-features)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/groups/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 14 de nov
Atualização em Português (Brasil): 16 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Groups API

The Groups API enables you to programmatically create groups for messaging and collaboration.

## How it works

Groups are an invite-only experience where participants join using a group invite link you send them. This invite link provides context about the group, helping the user decide whether they want to join.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/583332263_2097826120969757_476207660850437421_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=nnIKM9Xvk_QQ7kNvwG8jib-&_nc_oc=AdnsD4cJ1cUktjBbUlkBDTrCQ0dpoSok_0PgxAEMQKOowQ8e4x3zLTTGCx2S5ESTUV8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfhzOZAtXjzEs7JVaXZqN78EsP_7JDi__axD6UiOX58tAQ&oe=69407EFB)

## Get Started

When you are ready to start using the Groups API, head on over to our "Get Started" guide for more information:

[Get Started with Groups API](/docs/whatsapp/cloud-api/groups/getting-started)

## Quick Facts

* **Max group participants:** 8
* **Supported message types:** Text, media, text-based templates, and media-based templates
* **Max groups you can create:** 10,000 per business number
* **Max Cloud API businesses per group:** 1

## Analytics

**Performance metrics are not available for message templates used in Groups.**

Please create new templates specifically for Groups use instead of repurposing templates used for one-to-one messaging.

## Limits

**Eligibility for Groups API**

To qualify for groups features, your business must meet the following requirements:

* Have a messaging limit of at least 100,000 business-initiated conversations in a rolling 24-hour period
* Be an [Official Business Account (OBA)](/docs/whatsapp/official-business-accounts)

[Learn more about Quality Ratings and Messaging Limits](/docs/whatsapp/messaging-limits/)

*Groups are **not available** for [Coexistence users](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users/) and phone numbers onboarded to [Multi-solution Conversations](/docs/whatsapp/multi-solution-conversations)*.

*The [Calling API](/docs/whatsapp/cloud-api/calling) is not supported in groups.*

* **Non-supported message types:**
  + Calling
  + Disappearing messages
  + View-once
  + Auth
  + Commerce messages
  + Interactive messages

* **Non-supported actions:**
  + Admin hide group participant list
  + Edit message
  + Delete message
  + Marking message as read

## Pricing

The Groups API uses [per-message pricing](/docs/whatsapp/pricing).

[Learn more about Groups API pricing here](/docs/whatsapp/cloud-api/groups/pricing)

## Features and reference

### Group management features

* [Create and delete group](/docs/whatsapp/cloud-api/groups/reference/#create-group)
* [Groups with join requests enabled](/docs/whatsapp/cloud-api/groups/reference#groups-with-join-requests)
* [Get and reset group invite link](/docs/whatsapp/cloud-api/groups/reference/#get-and-reset-group-invite-link)
* [Send group invite link template message](/docs/whatsapp/cloud-api/groups/reference#send-group-invite-link-template-message)
* [Remove group participants](/docs/whatsapp/cloud-api/groups/reference/#remove-group-participants-endpoint)
* [Get group info](/docs/whatsapp/cloud-api/groups/reference/#get-group-info)
* [Get active groups](/docs/whatsapp/cloud-api/groups/reference/#get-active-groups)
* [Update group settings](/docs/whatsapp/cloud-api/groups/reference/#update-group-settings)

[*View Group Management reference*](/docs/whatsapp/cloud-api/groups/reference/)

### Group messaging features

* [Send group messages](/docs/whatsapp/cloud-api/groups/groups-messaging#send-group-message)
* [Receive group messages](/docs/whatsapp/cloud-api/groups/groups-messaging#receive-group-messages)
* [Pin and unpin group message](/docs/whatsapp/cloud-api/groups/groups-messaging#pin-and-unpin-group-message)

[*View Group Messaging reference*](/docs/whatsapp/cloud-api/groups/groups-messaging)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Groups API](#groups-api)

[How it works](#how-it-works)

[Get Started](#get-started)

[Quick Facts](#quick-facts)

[Analytics](#analytics)

[Limits](#limits)

[Pricing](#pricing)

[Features and reference](#features-and-reference)

[Group management features](#group-management-features)

[Group messaging features](#group-messaging-features)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_Afja8iIuJTJZ6ArmlvMOJO6Qa08uZ2sOsvpLo-ifdn5R3w&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfgBNu_N1ZaZPZMwkh7gMfdNTEMOiR8ViITDTLXFvc17OA&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfhWU3Eqw0NE25BtKB2BGeBKjCkn-unnucB8q9IWhbdoUg&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT04ohR_BS2oYT9YXKHWzwGyV4nm9sT-7A1jJGC7sxH--ZuaQNkvUwdmlybpTw1mxcy7w8eCEzGk-kmDKjw_A9yOtP60KbfND_Oq1b5ouY4nT3ewJDHxwwwWgAU4jQBR-LiwY4eOICepevG-ypC4CQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfjVNDKC-5wS-Osbf9s7X7d59bcfO0XN4WO-28rPXgOaxQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0-V7xybWkFNNhJ2cwvtYgQOpVZqwVMBo135q4bO_5NI6c6h62VvuYsXByMW-KrPNRV9qwSwq_WC19wfkPTmhrOMv2h_ADDslbOYFAv0cVQsZ17Vp6zp-dRrCKQZRdWb2tZ59nondBGa4PJQEDIZg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_Afjnmuzfe9PgUTWx1Fv3fi2njxSNuy2XtD321Oo64DLihg&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1W07eIz0LYjiLhkeVa9_KIsUelHd2IAW02ADdVR5QUDBrW-2CxQJdzlnsmAenOEFYxLiCAA66TH2Swy0Dj14yuE6O1fq7Z_9ByWI7j7IsfDWi1bTozupa64P2SLTu9jRZMiwvdJ2KN7r4JbQySBA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfgQO1rzpx7vrlofi7xohR7wT3LgYDVUUlxWmYz5z1pEWg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT25LvnqgZ7Anp3C5L4RSBzPUJQmn7K6mvkgZ50XWuwMjlM8l21T5Kerc38BXEakk7IOQqd3f_8kGfe-cS8YQQ8Y6YBgYGh_KhCXsoJNGGo24SK-VA06nOAGHJ5ucLxC8blsMEbMOn0LBt11XoGM5w)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3P0zP1Z60NFZt-d8KR6AebV119DM03tvAVcWxpX2kEPDjmfDv-jWy8zx74WKohmt0S4HDSCbtn7t8rdnq0TzQ_L-Xdzcvf_TlR9P3veJEXiZe0h7zxVxIAuDreVYou4XLnBIYn0BUoUKopHItqkw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT02gst1Ujsce9UVv9WX8ZfkzKTUubONMz--pyCOo_Fok7g8Kw-mvl7s8yCZZgy_PuTdjWdBA-nMxCgs1aHNoXDaGs6-3U5FKlDSPtjohLR9vR5dY8iHr7o8w_DtF8p8Vlh8PFc-CAgRe8rwCqNUSA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfhK9A3ifvOBEFJoB-JxU-Tq-gfmtRJVVGNtr-yC-BXQcw&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfgW0yB-f72yVnnJoP5qMAK40HcwIXWJqQJ0IIutdIK03g&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT08fEre5h9bSppdeTJoAUCzXJGskgLCF26S1S7Jjx3tT6q527J8L4lChmjz8qIrVGPd_9g45zLmoGkfvCdXgqw-zThWWHnty3eo0TKTK1CJxtlzarAo0XGK0kAWGOYZTljF94AHVA9MUOfxZRdfSQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfjAbn-Z1AxNX6-QJsKrXPoldNeTEjXVl34slwqmVtE3mA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT069Hav22DNAiBDlHLMZjmwCCG4puv1p7Uc2DnE3Urii99sU3mPBjz3GNbPLqwblE8ySwbQGSsHUFk65FZ2OWcbDQszd8QOOpjIgW1rMXYsq3XCdVgEROKYpi5urJOUICUn-S7uoXFPYfB22CJWIA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_AfgiYb68rLZZUqd2zwRYmbM50yGIfpfOLvy1vn5wntajdA&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2idEWQm7oDGlO_4XAazjtMCu5A3AukrUbYpQPC2JTNm-39Zloy8l5oMaBNVplUOVm1X5c__7GGn0mUyPEO0Of4dDyF09zFJS9E5AFRjXD-0X9zU6KT7M8maiEzsUpST9XeXh_rLRN5Oujx8EP3Zw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=RQKAVCuBj8RVEEiHFpGmXQ&oh=00_Afjxp2nEZrEkG6cHBnxcLbE0pmsP8Q9Cvbx8dmoWdwjEcA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT08HIrdOHcLMQ8NuG0zcOLtDyiQ8lk2_mvMQaMNzc16vBHoQ9LHl4DB5PChHztaspUW1v5yPCSenEWfFclzunE85fFNrBnbjrv7St7b67iSUKqkhzXmYAsM8U6Zx8bfga13RmUB6Yx5JpnP9UnURg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2ZWau3HcxcRS5PVmJ8VBw6JNRPCgYR5LUGQ5ihmipi5N21ejRxEPpaNU556o09USAV17DoVuH6ATrlep_KjVVqfsQ-VhC_8ZIiKSToP9D1MifiqirPeWkkeEob2AI4BmDkBMApxE1YWq0tXFA7oQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)