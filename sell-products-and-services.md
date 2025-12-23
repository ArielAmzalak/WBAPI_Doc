![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsell-products-and-services%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)

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
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)

  + [Upload Inventory](/docs/whatsapp/cloud-api/guides/sell-products-and-services/upload-inventory)
  + [Definir configurações comerciais](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings)
  + [Compartilhar produtos](/docs/whatsapp/cloud-api/guides/sell-products-and-services/share-products)
  + [Receiving Responses](/docs/whatsapp/cloud-api/guides/sell-products-and-services/receive-responses)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Sell Products & Services](#sell-products---services)

[Policies](#policies)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/guides/sell-products-and-services/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 4 de nov
Atualização em Português (Brasil): 26 de nov de 2024

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Sell Products & Services

Businesses using the WhatsApp Business API can showcase and share their products and services with customers for them to browse items and add to a cart without leaving the chat. To use the API for commerce use cases, follow these guides:

1. [**Upload inventory to Meta**](/docs/whatsapp/cloud-api/guides/sell-products-and-services/upload-inventory): Upload the business's inventory to Meta using the API or the [Meta Commerce Manager](https://business.facebook.com/commerce/).
2. [**Connect an Ecommerce Catalog to the WABA**](https://www.facebook.com/business/help/158662536425974): Connect a catalog that has been categorized as **Ecommerce** to the WhatsApp Business Account.
3. [**Set Commerce Settings**](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings): Set the business phone number's commerce settings.
4. [**Share Products With Customers**](/docs/whatsapp/cloud-api/guides/sell-products-and-services/share-products): Use Multi and Single Product Messages to send products to customers.
5. [**Receive Responses From Customers**](/docs/whatsapp/cloud-api/guides/sell-products-and-services/receive-responses): Track webhooks to get questions and orders from customers.

## Policies

Never send messages that violate our Commerce and Business Policies. Additionally, Multi and Single Product Messages are subject to the existing enforcement and data sharing rules for product catalogs:

* Rejection at product catalog level: WhatsApp automatically reviews items added to a catalog connected to a WABA. If a policy violating item is added, the product is flagged and the business is directed to the WhatsApp Commerce Policies.
* Reporting options for the user at the product catalog level: Users can report a specific product they receive via message. If a user reports a product, it gets reviewed for violations.

Businesses can appeal for disapproved items directly in the [Meta Commerce Manager](https://business.facebook.com/commerce/).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Sell Products & Services](#sell-products---services)

[Policies](#policies)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ColYk9NT1nQczxF3nNOG6g&oh=00_Afhrd9uLQTPy4f3RYz8DA7Eqfsjel3SZqCIkqwNVa7jDGg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ColYk9NT1nQczxF3nNOG6g&oh=00_AfjKAF-jrG-IpACuxACZoM4hAczuCdqwvThlYhBn8boo1A&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ColYk9NT1nQczxF3nNOG6g&oh=00_AfiXoi1mVumxauvNI7eFd76Oacg05CtVpER0K4dvVm8H_w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ColYk9NT1nQczxF3nNOG6g&oh=00_AfjqNpf-l06kCklCJZKrNhxCmpVEijIjO14723xJH6cv2A&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ColYk9NT1nQczxF3nNOG6g&oh=00_Afjq0bkQzegrPNqkKqkHA1-sdbXHB3MtAwWDkO9zxojaaw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT16t3RroLA6nTgEu7F-pzvFa-W-OqgNoh8X3EcSSrkHLWoiry8Xm4FxLRQODHR2X9d2y18RLOzubKHvkSst6P8ovLhQTTicZadOLBXwSALS6SMza27-6xmLbNDCf2q2Lwj6U2i2542L0jxuAA1MXg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)