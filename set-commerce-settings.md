![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fsell-products-and-services%2Fset-commerce-settings%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)[Definir configurações comerciais](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings)

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

[Set Commerce Settings](#set-commerce-settings)

[Requirements](#requirements)

[Get Business Phone Numbers](#get-business-phone-numbers)

[Enable/Disable Cart](#enable-disable-cart)

[Request Syntax](#request-syntax)

[Parameters](#parameters)

[Sample Request](#sample-request)

[Sample Response](#sample-response)

[Enable/Disable Catalog](#enable-disable-catalog)

[Request Syntax](#request-syntax-2)

[Parameters](#parameters-2)

[Sample Request](#sample-request-2)

[Sample Response](#sample-response-2)

[Get Commerce Settings](#get-commerce-settings)

[Request Syntax](#request-syntax-3)

[Parameters](#parameters-3)

[Sample Request](#sample-request-3)

[Sample Response](#sample-response-3)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/guides/sell-products-and-services/set-commerce-settings/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 14 de nov
Atualização em Português (Brasil): 8 de mai

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Set Commerce Settings

You can enable or disable the shopping cart and the product catalog on a per-business phone number basis. By default, the shopping cart is enabled and the storefront icon is hidden for all business phone numbers associated with a WhatsApp Business Account.

## Requirements

* A [system token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [user token](/docs/whatsapp/access-tokens#user-access-tokens).
* The [whatsapp\_business\_management](/docs/permissions/reference/whatsapp_business_management) permission.
* If using a [system token](/docs/whatsapp/access-tokens#system-user-access-tokens), the system user must be granted full controll over the WhatsApp Business Account.
* Businesses based in India must [comply with all online selling laws](https://www.facebook.com/help/1104628230079278).

## Get Business Phone Numbers

Use the [WhatsApp Business Account > Phone Numbers](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers) endpoint to get a list of all business phone numbers associated with a WhatsApp Business Account.

## Enable/Disable Cart

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to enable or disable the shopping cart for a specific business phone number.

When enabled, cart-related buttons appear in the chat, catalog, and product details views:

![Three WhatsApp messenger screenshots with callout of various cart UI components displayed](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/513870481_1426428692034436_5288360534924361904_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=Oi8Rd6Mq_d0Q7kNvwEejK5Q&_nc_oc=AdlDoI-VJDf7vxr0sHRXTl5jqHol15QSMaHm3K15eqxJYia0Su75f-LGrTDy9YP3BrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DjCR21SqblXVGgdpRlYQcQ&oh=00_AfhTMYBAsyHQHT4XXEe1oTG7HfwPWeJtq-DJKcQPKEO3Lg&oe=69406256)

When the cart is disabled, customers can see products and their details, but all cart related buttons will not appear in any view.

### Request Syntax

```
POST /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
  ?is_cart_enabled=<IS_CART_ENABLED>
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |
| `<IS_CART_ENABLED>` | `true` | Boolean. Set to `true` to enable cart or `false` to disable it. Default value is `true`. |

### Sample Request

```
curl -X POST 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings?is_cart_enabled=true' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "success": true
}
```

## Enable/Disable Catalog

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to enable or disable the product catalog for a specific business phone number.

When enabled, the catalog storefront icon and catalog-related buttons appear in chat views and business profile views:

![Two WhatsApp messenger screenshots with callout of various catalog UI components displayed](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/513359223_1234792844894756_6573923522221485884_n.png?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=w8mtcHUk-P0Q7kNvwG8Usr8&_nc_oc=AdkQ3FxVvbuL1TxDRyjYBq5LnSHPvqkTQX_9b-EQQREA2kq-naufCw4Pxnj8VLzcgLo&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DjCR21SqblXVGgdpRlYQcQ&oh=00_AfioSzCWdakwA6f0XVywwq9XzieRWHEau6GpEauz0Op9QA&oe=69405CB3)

When the catalog is disabled, the storefront icon and catalog-related buttons will not appear in any views and the catalog preview with thumbnails will not appear in the business profile view.

If you disable the catalog, wa.me links to your catalog, as well as the **View catalog** button that appears when you send your catalog link in a message will display an **Invalid catalog link** warning when tapped.

### Request Syntax

```
POST /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
  ?is_catalog_visible=<IS_CATALOG_VISIBLE>
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |
| `<IS_CATALOG_VISIBLE>` | `true` | Boolean. Set to `true` to show catalog storefront icon or `false` to hide it. Default value is `false`. |

### Sample Request

```
curl -X POST 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings?is_catalog_visible=true' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "success": true
}
```

## Get Commerce Settings

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to get an individual business phone number's commerce settings.

### Request Syntax

```
GET /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |

### Sample Request

```
curl -X GET 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "data": [
    {
      "is_cart_enabled": true,
      "is_catalog_visible": true,
      "id": "727705352028726"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Set Commerce Settings](#set-commerce-settings)

[Requirements](#requirements)

[Get Business Phone Numbers](#get-business-phone-numbers)

[Enable/Disable Cart](#enable-disable-cart)

[Request Syntax](#request-syntax)

[Parameters](#parameters)

[Sample Request](#sample-request)

[Sample Response](#sample-response)

[Enable/Disable Catalog](#enable-disable-catalog)

[Request Syntax](#request-syntax-2)

[Parameters](#parameters-2)

[Sample Request](#sample-request-2)

[Sample Response](#sample-response-2)

[Get Commerce Settings](#get-commerce-settings)

[Request Syntax](#request-syntax-3)

[Parameters](#parameters-3)

[Sample Request](#sample-request-3)

[Sample Response](#sample-response-3)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DIh3JNgmCoacfJU7P8dFDg&oh=00_AfjD9RwQbrw-VWnv-ZYYcBUInEswj1lJDsCYPfxbWt0cYg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DIh3JNgmCoacfJU7P8dFDg&oh=00_Afizrqw2H4t9p3hAPRTdomC3040YwcRPbPN22gXC2dlcoQ&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DIh3JNgmCoacfJU7P8dFDg&oh=00_AfgeNarMXU0CLi5SJNbXOqjBP7bKPSJvJF2bfBgsp6fVQA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DIh3JNgmCoacfJU7P8dFDg&oh=00_AficCj0UaHuKdfQQRdt64qbsazHyfJ-6aJslfe6GKuJMgA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=DIh3JNgmCoacfJU7P8dFDg&oh=00_AfiKt4oAhw845yGVG8o503zUENAE0xkI2evdchcnlqQg7Q&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2x24Es6025poSwnD-nRDN082DemAVPeSaJJ3i3SYj87HLiLr7-FWvrOnAFEOkInjXmpi1Tth0vgO2YJ2H1wAIQvbKvrMNOzshXXEQzG7eXm491OZvEMHOjGB8SwzDCN0z26pPLMMSaaonXRdwvbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)