![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsell-products-and-services%2Freceive-responses%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)[Receiving Responses](/docs/whatsapp/cloud-api/guides/sell-products-and-services/receive-responses)

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

[Receive responses from customers](#receive-responses-from-customers)

[Sent message status](#sent-message-status)

[Asking for information](#asking-for-information)

[Orders](#orders)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Receive responses from customers

After receiving single- or multi-product messages, WhatsApp users can ask for more information about a product or place an order. These actions are communicated via [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages) webhook.

## Sent message status

Sent message statuses (sent, delivered, read) are described in [status messages webhooks](/docs/whatsapp/cloud-api/webhooks/reference/messages/status).

## Asking for information

Whenever a WhatsApp user receives a single- or multi-product message, they can ask for more information by sending you a text message in an existing WhatsApp thread, or by tapping a **Message business** or **Message** button when viewing a specific product.

Messages sent after tapping a **Message business** or **Message** button are described in [text messages webhooks](/docs/whatsapp/cloud-api/webhooks/reference/messages/text) and a `context` property will be included, whose value is an object describing the product the user was viewing when they tapped the button.

## Orders

When a WhatsApp user adds one or more products to their WhatsApp shopping cart and places an [order messages webhook](/docs/whatsapp/cloud-api/webhooks/reference/messages/order) is triggered, describing the contents of the order. Use the order contents to fulfill the order.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Receive responses from customers](#receive-responses-from-customers)

[Sent message status](#sent-message-status)

[Asking for information](#asking-for-information)

[Orders](#orders)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=19b47_dChe_pfCGG436NNg&oh=00_Afi6GQ183obM8383k-cuSWMsQ7cfGtsrY42J2aor0eiTuQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=19b47_dChe_pfCGG436NNg&oh=00_AfgX9VI3byFjgGteDyflbYoBiZ6klcDI_HrKO73Y9bUJ4Q&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=19b47_dChe_pfCGG436NNg&oh=00_AfiQQz2BbaRJQmjvxMOsnK3RWLK1mZjo8f6IM6FYx75xrw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=19b47_dChe_pfCGG436NNg&oh=00_AfjEaPgcTN9LdrFblCLz_-AuD_FugxnFOlI-3GodagRAqQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=19b47_dChe_pfCGG436NNg&oh=00_AfjlpocnAaQIvCDGw8_oXgLSjXnV_oGuiC3vRvlWQ9oSKA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2RN1O8vVbB_jJFuqcBYcd3y6TE3y3TYcmcI-wP-j1IEfu_j5IxOIwhdWtP0Pe5GQCebkmI8fhajSZm2OmqaHYBect2s79nGtn2odZvYMGS3-4R5TJv2Il68sCx6TZiu43AA_FKnYNHW2oyg85cXw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)