![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fpayments-api%2Fpayments-br%2Fpayment-links%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)[Payment Links](/docs/whatsapp/cloud-api/payments-api/payments-br/payment-links)

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
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)

  + [Orders](/docs/whatsapp/cloud-api/payments-api/payments-br/orders)
  + [Pix](/docs/whatsapp/cloud-api/payments-api/payments-br/offsite-pix)
  + [Payment Links](/docs/whatsapp/cloud-api/payments-api/payments-br/payment-links)
  + [Boleto](/docs/whatsapp/cloud-api/payments-api/payments-br/boleto)
  + [One Click Payments](/docs/whatsapp/cloud-api/payments-api/payments-br/one-click-payments)
  + [Order Details Template](/docs/whatsapp/cloud-api/payments-api/payments-br/orderdetailstemplate)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Payment links](#payment-links)

[Before You Start](#before-you-start)

[Integration steps](#integration-steps)

[1. Send an order details message](#1--send-an-order-details-message)

[2. Send an order status update](#2--send-an-order-status-update)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Payment links

Payments API also enables businesses to collect payments from their customers via WhatsApp using Payment Links.

When using this integration, WhatsApp only facilitates the communication between merchants and buyers. Merchants are responsible for integrating with a PSP from which they can generate Payment Links, and confirm their payment.

## Before You Start

1. Familiarize yourself with the [Orders API](https://developers.facebook.com/docs/whatsapp/cloud-api/payments-api/payments-br/orders). Orders are the entrypoint for collecting payments in WhatsApp.
2. You will need an existing integration with a PSP to generate Payment Links and do automatic reconciliation when a payment is made.
3. You must update the order status as soon as a payment is made.

## Integration steps

The following sequence diagram shows the typical integration with Payment Links.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=915761436977610&version=1722361997)

### 1. Send an order details message

Follow the full integration guide in the [Orders API page](https://developers.facebook.com/docs/whatsapp/cloud-api/payments-api/payments-br/orders).

If Payment Link payment is available on this order, you will need to provide a `payment_link` to the `payment_settings` attribute.

#### Parameters object

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| `payment_settings` | Optional | [Payment Settings Object](#paymentsettingsobject) | List of payment related configuration objects. |

#### Payment settings

| Field Name | Optional? | Type | Description |
| --- | --- | --- | --- |
| `type` | Required | String | Must be `payment_link`. |
| `payment_link` | Required | [Payment Link Object](#paymentlinkobject) | Payment Link object that will be used to render the option to buyers during the checkout flow. |

#### Payment link object

| **Field Name** | **Optional?** | **Type** | **Description** |
| --- | --- | --- | --- |
| `uri` | Required | String | The Payment Link's uri which will be opened in the web browser, when user taps on the Payment Link CTA button. |

#### Payload example

```
POST: /v1/messages
{
 "recipient_type": "individual",
 "to": "[recipient-wa-id]",
 "type": "interactive",
 "interactive": {
   "type": "order_details",
   "body": {
     "text": "Your message content"
   },
   "action": {
     "name": "review_and_pay",
     "parameters": {
       "reference_id": "unique-reference-id",
       "type": "digital-goods",
       "payment_type": "br",
       "payment_settings": [
         {
           "type": "payment_link",
           "payment_link": {
             "uri": "https://my-payment-link-url",
           }
         }
       ],
       "currency": "BRL",
       "total_amount": {
         "value": 50000,
         "offset": 100
       },
       "order": {
         "status": "pending",
         "tax": {
           "value": 0,
           "offset": 100,
           "description": "optional text"
           },
         "items": [
           {
             "retailer_id": "1234567",
             "name": "Cake",
             "amount": {
               "value": 50000,
               "offset": 100
             },
             "quantity": 1
           }
         ],
         "subtotal": {
           "value": 50000,
           "offset": 100
         }
       }
     }
   }
 }
}
```

### 2. Send an order status update

Once the payment is confirmed, you must send an order status update. Follow the integration guide in the [Orders API page](https://developers.facebook.com/docs/whatsapp/cloud-api/payments-api/payments-br/orders).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Payment links](#payment-links)

[Before You Start](#before-you-start)

[Integration steps](#integration-steps)

[1. Send an order details message](#1--send-an-order-details-message)

[2. Send an order status update](#2--send-an-order-status-update)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lHQaFY29k6CVdIbDZ0EGWA&oh=00_AfiqxB21T9X3dJ5IxJTK2Hv0XZAQ2TkRalfAxJE1ignLbA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lHQaFY29k6CVdIbDZ0EGWA&oh=00_AfimGgOMmHXk0jw2NCJ4FY_dpFzw2QS48qEsYumCRVc9UA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lHQaFY29k6CVdIbDZ0EGWA&oh=00_AfjT1O5FaQgVmIh-jom00yBx1XsStO11EZUs47rXCge5kw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lHQaFY29k6CVdIbDZ0EGWA&oh=00_AfjJyJ8xPlJV6DPIH4egGerZyhDU5MiybbrphUGRkheixQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lHQaFY29k6CVdIbDZ0EGWA&oh=00_Afh6C3x9L3kesSWgfh5XidqJXNdHxcHEmG4TzEY1XFQ5Qw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2wz1-hC3h4UMRPgxsXTjRPSeZf-B2jiSvbJPPlL3dnbz2CwvV_Xkst5Etl5aWYKP6CQTXA1l6xUhJPsyMBNlZ50VDDdVQ3Qd2b2Y2XJ8toG8A61095Q6QEEWRh6O-m_N8hM24b0dHVnTkJfQ9UYg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)