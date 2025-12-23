![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fthroughput%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)[Throughput](/docs/whatsapp/throughput)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)

  + [Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components)
  + [Throughput](/docs/whatsapp/throughput)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Throughput](#throughput)

[WhatsApp Business app phone numbers](#whatsapp-business-app-phone-numbers)

[Higher throughput](#higher-throughput)

[Eligibility](#eligibility)

[Webhooks](#webhooks)

[Media messages](#media-messages)

[Getting throughput level](#getting-throughput-level)

[Migration](#migration)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Throughput

For each registered business phone number, Cloud API supports up to 80 messages per second (mps) by default, and up to [1,000 mps](#higher-throughput) by automatic upgrade.

Throughput is inclusive of inbound and outbound messages and all message types. Note that business phone numbers, regardless of throughput, are still subject to their WhatsApp Business Account [rate limit](/docs/whatsapp/overview#rate-limits) and [template messaging limits](/docs/whatsapp/messaging-limits).

If you attempt to send more messages than your current throughput level allows, the API will return error code `130429` until you are within your allowed level again. Also, throughput levels are intended for messaging campaigns involving different WhatsApp user phone numbers. If you attempt to send too many messages to the same WhatsApp user number, you may encounter a pair [rate limit](/docs/whatsapp/overview#rate-limits) error.

## WhatsApp Business app phone numbers

In order to remain compatible with the WhatsApp Business app, business phone numbers that are in use with both the WhatsApp Business app and Cloud API ("[coexistence numbers](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users)") have a fixed throughput of 20 mps.

## Higher throughput

If you meet our [eligibility requirements](#eligibility), we will automatically upgrade your business phone number to 1,000 mps at no cost to you. Higher throughput does not incur additional charges or affect pricing.

The upgrade process itself can take up to 1 minute. During this time the number will not be usable on our platform. If used in an API request, the API will return error code `131057`. Once a business phone number has been upgraded, it will automatically be upgraded for any future throughput increases with no downtime.

Once your number is upgraded to higher throughput, a [phone\_number\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_quality_update) webhook will be triggered with `event` set to `THROUGHPUT_UPGRADE` and `max_daily_conversations_per_business` set to `TIER_UNLIMITED`.

## Eligibility

* The business portfolio associated with the phone number must have an unlimited [messaging limit](/docs/whatsapp/messaging-limits).
* The business phone number must be used to message 100K or more unique WhatsApp user phone numbers, outside of a [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows), within a moving 24-hour period.
* The business phone number must have a `quality_score` of `YELLOW` (shown as a **Medium** [quality rating](https://www.facebook.com/business/help/896873687365001) in WhatsApp Manager) or higher.

## Webhooks

Your webhook servers should be able to withstand 3x the capacity of outgoing message traffic and 1x the capacity of expected incoming message traffic. For example, if sending 1,000 mps with a 30% expected response rate, your servers should be able to process up to 3000 message status webhooks plus an additional 300 incoming message webhooks.

We attempt to deliver webhooks concurrently, so we recommend you configure and load test your webhook server to handle concurrent requests with the following latency standard:

* Median latency not to exceed 250ms.
* Less than 1% latency exceeds 1s.

We will attempt to re-deliver failed webhooks for up to 7 days, with exponential backoff.

## Media messages

To take full advantage of higher throughput, we recommend that you [upload your media assets](/docs/whatsapp/cloud-api/reference/media#upload-media) to our servers and use the returned media IDs, instead of hosting the assets on your own servers and using media asset URLs, when [sending messages](/docs/whatsapp/cloud-api/guides/send-messages) that include a media asset. If you prefer (or must) host the assets on your own servers, we recommend that you use [media caching](/docs/whatsapp/cloud-api/guides/send-messages#media-http-caching).

## Getting throughput level

Use the [WhatsApp Business Phone Number](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/) endpoint to get a phone number's current throughput level:

```
GET /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>?fields=throughput
```

## Migration

If you [migrate a business phone number](/docs/whatsapp/cloud-api/guides/migrate-between-on-premises-and-cloud-api) that has multiconnect running 2 or more shards from On-Premises API to Cloud API, it will automatically be upgraded to higher throughput.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Throughput](#throughput)

[WhatsApp Business app phone numbers](#whatsapp-business-app-phone-numbers)

[Higher throughput](#higher-throughput)

[Eligibility](#eligibility)

[Webhooks](#webhooks)

[Media messages](#media-messages)

[Getting throughput level](#getting-throughput-level)

[Migration](#migration)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=I-1YtVrX1P0c02lNFHpnYA&oh=00_AfhiG4yK023BV9ijsi2jnVE7IoExGuHIJwU_j_nNFm65Ng&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=I-1YtVrX1P0c02lNFHpnYA&oh=00_Afju75MNpcWkPhLf-_qPOw6Wo7haX5-Vt7UBwj6-3RNadw&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=I-1YtVrX1P0c02lNFHpnYA&oh=00_AfidHsu4XrnjGX8hQE9Tt7bqr2tw3QnHAgCWxYIBluLlCg&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=I-1YtVrX1P0c02lNFHpnYA&oh=00_AfiGjGGyLf-HBs6aydoSefn9ovzsovhNik8uOjTiU247oA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=I-1YtVrX1P0c02lNFHpnYA&oh=00_AfjpTBgfvKACVgkjAeF-E0hfwe5mQiVqaUJvFPhAv1Q53A&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1za4tZPYq86-WWmviR9_RWgrCtn_nKUmXQhP7ooeaPQf6Qe6ZqVg3M0wxg-jgUjyWfuP1jzjvXwG2bakTzT2N0NasgbfvIAC3ScYD_TITWSv-3f0gAaAaNpDH2ZSOAEJKRhNzrcLWH6WqWv0dIPw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)