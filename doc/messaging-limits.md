![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmessaging-limits%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Limites de mensagens](/docs/whatsapp/messaging-limits)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)
* [Preços](/docs/whatsapp/pricing)
* [Limites de mensagens](/docs/whatsapp/messaging-limits)

  + [Upcoming changes](/docs/whatsapp/messaging-limits/upcoming-changes)
* [Webhooks](/docs/whatsapp/webhooks)
* [Parceiros de soluções](/docs/whatsapp/solution-providers)
* [Cadastro Incorporado](/docs/whatsapp/embedded-signup)
* [Prévias de links](/docs/whatsapp/link-previews)
* [Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[Messaging Limits](#messaging-limits)

[Increasing your limit](#increasing-your-limit)

[Scaling paths](#scaling-paths)

[Approvals](#approvals)

[Denials](#denials)

[Automatic scaling](#automatic-scaling)

[Checking your limit](#checking-your-limit)

[Via Meta Business Suite](#via-meta-business-suite)

[Via API](#via-api)

[Voltar para Português (Brasil)](/docs/whatsapp/messaging-limits/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 30 de out
Atualização em Português (Brasil): 22 de out

# Messaging Limits

This document describes messaging limits for the WhatsApp Business Platform.

Messaging limits are the maximum number of unique WhatsApp user phone numbers your business can deliver messages to, outside of a [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows), within a moving 24-hour period.

Messaging limits are calculated and set at the business portfolio level and are shared by all business phone numbers within a portfolio. This means that if a business portfolio has multiple business phone numbers, it's possible for one number to consume all of the portfolio's messaging capability within a given period.

Newly created business portfolios have a messaging limit of 250, but this limit can be increased to:

* 2,000 (by completing a [scaling path](#scaling-paths))
* 10,000 (via [automatic scaling](#automatic-scaling))
* 100,000 (via automatic scaling)
* Unlimited (via automatic scaling)

## Increasing your limit

You can increase your messaging limit to 2,000 by completing one of the [scaling paths](#scaling-paths) below. After that, we will automatically increase your limit to the next higher limit if you meet our [automatic scaling criteria](#automatic-scaling).

### Scaling paths

* [Verify your business](https://www.facebook.com/business/help/2058515294227817)
* Have your [solution provider verify your business](/docs/whatsapp/solution-providers/partner-led-business-verification) (if you were onboarded by one)
* Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality).

Once you complete one of these paths, we will analyze your [message quality](/docs/whatsapp/cloud-api/guides/send-messages#message-quality). Based on this analysis, your number's eligibility for automatic scaling will either be approved or denied.

### Approvals

If your request is approved, we will immediately increase your business phone number's messaging limit to 2,000 and notify you by email and developer alert. In addition, a [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update) webhook will be triggered with `max_daily_conversations_per_business` (for webhooks v24.0 and newer) and `max_daily_conversation_per_phone` (for v23.0 and older, until February, 2026) set to the new limit.

Additional messaging limit increases for your number can now happen automatically, via [automatic scaling](#automatic-scaling).

### Denials

If your request is denied, we will maintain your business phone number's messaging limit at its current level and notify you via email and developer alert. In addition, an [account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts) webhook will be triggered, with the `alert_type` and `alert_description` properties indicating alternate methods you can pursue to increase your limit.

| `alert_type` Value | Action you can take |
| --- | --- |
| `INCREASED_CAPABILITIES_ELIGIBILITY_DEFERRED` | Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers in a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |
| `INCREASED_CAPABILITIES_ELIGIBILITY_FAILED` | Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |
| `INCREASED_CAPABILITIES_ELIGIBILITY_NEED_MORE_INFO` | [Verify your identity](https://www.facebook.com/business/help/587323819101032), or send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |

## Automatic scaling

Once your business portfolio's messaging limit has been increased to 2,000, we will determine if it should be increased further according to the following criteria:

* You are sending [high-quality messages](/docs/whatsapp/cloud-api/guides/send-messages#message-quality) across all of your business phone numbers and templates
* In the last 7 days, your business has utilized at least half of your current messaging limit

If these criteria are met, we will increase your portfolio's limit by one level within 6 hours.

## Checking your limit

### Via Meta Business Suite

Your business phone number's current messaging limit is displayed in the [WhatsApp Manager](https://business.facebook.com/wa/manage/home/) > **Account tools** > **Messaging limits** panel:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/535132607_2167690997071606_2519788358245522587_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=OYr5Biu4bhAQ7kNvwHd3wxl&_nc_oc=Adk6SmUspBu4emTm_ZxQVTW-SXhORBQSdMfh2QbiGVGom4QOP-aQ-mnO73er72QGhK0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfhV4HEBSwSDxPYh_9MA9HBozNIY6YMP_xFr7FSFkz9TDA&oe=69406D59)

### Via API

Use the [GET /<BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) endpoint and request the `whatsapp_business_manager_messaging_limit` field (for v24.0 and newer) or `messaging_limit_tier` field (for 23.0 and older) to get a business phone number's current messaging limit.

#### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922?fields=whatsapp_business_manager_messaging_limit' \
-H 'Authorization: Bearer EAAJB...'
```

#### Example response

```
{
  "whatsapp_business_manager_messaging_limit": "TIER_250",
  "id": "106540352242922"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Messaging Limits](#messaging-limits)

[Increasing your limit](#increasing-your-limit)

[Scaling paths](#scaling-paths)

[Approvals](#approvals)

[Denials](#denials)

[Automatic scaling](#automatic-scaling)

[Checking your limit](#checking-your-limit)

[Via Meta Business Suite](#via-meta-business-suite)

[Via API](#via-api)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfhQSFLC4bhDOteRnbs9qfyfXpmNEODd21OCnITXeHY0lQ&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_Afi4oOh9ro8KqU10F47oyVRjbs7pLoFlLKKeHE8g8psyFA&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfhAEZ3qtdkW2xQMrFswBBOgzsgca8AbKVnX8SAyuigZZw&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3Z4iW8QH87SD3c8_cL0-HPEInUTartGK-IvOKGv8w2XPqcrCU5Gy8WHF87BBrYPuyfHiH0Nr0vbM7AraD1FxoIz-Aagn118mF9PRMIqvDeIrs0IZOP58ZxyGIcDhV6NI14xSRECODxnnmaj4jeSA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfghKd7HHNPdTdTasyOadxBmRE4k5NqLvSmXfrRhFAGWxA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1b65Hkt8Cpv1Ehkt49r3ZIRIbn9cL24EHQi7ndrsRjuxrCxtmcaEti7-1-SqAM0xnFmXJYr09yH6Jrydch_pTyy7Owd5qcR4iIeLI7almDEpwhFX3D_NK4_Ew5Kg2zgbMqOe6iqEfP9v0Hp8Z_cg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_Afih6XOyIrO60lX3xte3rlC-bSgx_PclS0UQfUJ84F5lJQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2HT_fm7NJNrPMbhIu_qn3yqrzGuM_1q_HDWxdiii2TFqEsFSxCN_FE5vKRDShR1v4_VX7924sMh2HFlajGjHlEY2XTedSDTjBLQX01Dqx1kXPEpRiYO_Ztj1m3XgCJzunfD6dXvbrkYmE36uZiMQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfgR8JVhCsGhDYzG6uA448_R-crkwu13lXzPt8ZJDN89uQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3cKLPWaEYkBKAb4lb52D-_ic8CQQ9luXsH_eWPFnWjtjZqNJ9hJeVqIgm1AJ5M79Yn9Nh42omTDi2i5N5S2m-F63BCn0HvZzyh8OY-WqFWCFGhaQboBmVYzWmM2dCWGLV4lCSlfRI9MWW-GbSRFQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3wYVxwU9hxhVMoaQ9JhtU-jfXPdjTcWuOhAVZ27lp9dr8kVMLr2rrf9M6R-NJN5x8qFE-HTqwzRZA2c2OKFsbfpsZxIMFHlAdB4Ia7nKnHz-8uaW2PTXNCTPqvUBkC9fp8Ln7jLRLHS2LRV310Uw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT07j41Bcm07yhkzm9mpFWnuMqB83bBfBdPooJC2cUCq7fnGnVz-x0mT9VLfJhfoVdB0AN8lra6qR8R3A4Ydrtno37xv8K-Zc2EYu72rDfwfr7PkJio13w1Ws9l4pWPMm1xynlr5qoX6R0ynLKVRtyxX-xggsFs_al4)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfgLF6tBmjf474t69mWMGCF6QM_iBs-eBHYOlmHl3BApGg&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfiCXBlNo8uez2yAR_dJt2t_QQcxUnp3CXmt80_vUiJJHQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3BPjns78kdctiw_u5PaKNvw_CNPkq_2ym5VsbNJrhhCPdYawvmQm_F7V2OY4wLJe2ndt5__euZONczydu27rYGGzR4JJkonk0s_Ky3oK7XPc5lwT2Psn3ICwqI8JB4eoiKUqgISv6M9wzwD582mcUtv7EpZU0TolM)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfjYBDdQSQ-XC09jmpV_xHxhvlgr7bHkdtq7wWv55mN1yA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1FHQWpFEgSJR2xgEqXcjAtI2cxx4O18JzDwcW2ntt_JwYyhZKladnPD1ekqefg0ODMZuo5tlUAnlcdaSY_9A4TPwnS3eyxEdPHvxtJ9_46qxx-ILbMAp9uj9bo0CKYxCQjYZTswQErSQ-4fpO45w)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfiWk0CcFk0xuVhnAuGavJH8hZuc5OShJPBbohhd1maqCw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT11pXzsrCEvKREn2atjfkl9T-Vk3UycKEHVnfqWFxFwS5OiHy4xDu9XFSU8SP_-5CyihtGPCiqsNsQANdZ_2msDWBNHt1Zhgnyylk4AglnKj0YOeAudhKSfemnBs-jjESESql1-lV0VHXPEo0_4IQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-C6O8rdZ0PPHxUKBo7nhcA&oh=00_AfjiK8wAr3rWZWwRPoJJbqFevRQ6Iro7aSg2K11lb3nGzQ&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1z-dCm-XI_AbBZ9geXj_3k72OCFbDr-YLXua1KFWtp8up2p2IGv8skGtEYuOxP-FaxJUBGsNHeeY17W0PbAaGkjx5sGsVLX1cjg6Wo1C2omzVVzUIcpfTG4RrHJfasiBwebwRPqRFa4T7Ih-0QEw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3YbEsrJCECDmKjAVLe76HtOLgOanwtL1aGzdrIuWD4hc0lVrlSF_2l7lEEl5hR7pndw0oIxiZp2EHsmAAY9Nqrw7DsSXgYIXOSt-wxlJYE0eS-pYyqnmlNmPTAuOZ7Z1Nf4az1IFWDLjK4HEUnFg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)