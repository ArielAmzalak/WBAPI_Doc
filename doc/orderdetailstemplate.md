![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fpayments-api%2Fpayments-br%2Forderdetailstemplate%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)[Order Details Template](/docs/whatsapp/cloud-api/payments-api/payments-br/orderdetailstemplate)

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

[Send order details template message](#send-order-details-template-message)

[Overview](#overview)

[Creating an order details template on Whatsapp Manager](#creating-an-order-details-template-on-whatsapp-manager)

[Creating an order details template using template creation APIs](#creating-an-order-details-template-using-template-creation-apis)

[Sending order details template message](#sending-order-details-template-message)

[Post order details template message flow](#post-order-details-template-message-flow)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Send order details template message

## Overview

Order details message template is a template with [interactive components](/docs/whatsapp/business-management-api/message-templates#components) that extends the call-to-action button to support sending order details and provides a richer experience compared to templates with only text components.

Once your Order details message templates have been created and approved, you can use the approved template to send the template message with order or bill information to prompt customers to make a payment.

Before sending an order details template message, businesses need to create a template with an “order details” call-to-action button. See [Create Message Templates for Your WhatsApp Business Account](https://www.facebook.com/business/help/2055875911147364?id=2129163877102343) for more information on prerequisites and how to create a template.

## Creating an order details template on Whatsapp Manager

To create an order details template, business needs a business portfolio with a WhatsApp Business Account.

In **WhatsApp Manager** > **Account tools**:

1. Click on `create template`
2. Select `Utility` or `Marketing` category to see the `Order details` template format option.
3. Select `Order details` template format, and click **Next**
4. Enter the desired `template name` and supported `locale`
   * Depending on the number of `locales` selected there will be an equal number of template variants and businesses need to fill in the template details in respective locale.
5. Fill in template components such as `Header`, `Body` and optional `footer` text.
   * For the `Header`, you can choose one of three media types: `Text`, `Image` or `Document`. Choose `Document` if you want to send **PDF files** in the header of this template.
6. Click submit.
7. Once submitted, templates will be [categorized as per the guidelines](/docs/whatsapp/updates-to-pricing/new-template-guidelines#template-category-guidelines) and undergo the [approval process](/docs/whatsapp/message-templates/guidelines#approval-process).
8. The template will be approved or rejected after the template components are verified by the system.
   * If business believe the category determined is not consistent with our template category guidelines, please confirm there are no [common issues](/docs/whatsapp/message-templates/guidelines#common-rejection-reasons) that leads to rejections and if you are looking for further clarification you may [request a review](/docs/whatsapp/updates-to-pricing/new-template-guidelines#requesting-review) of the template via [Business Support](https://business.facebook.com/business-support-home/)
9. Once approved template [status](/docs/whatsapp/message-templates/guidelines#statuses) will be changed to `ACTIVE`
   * Please be informed that template's status can change automatically from `ACTIVE` to `PAUSED` or `DISABLED` based on customer feedback and engagement. We recommend that you [monitor status changes](/docs/whatsapp/message-templates/guidelines#monitoring-status-changes) and take appropriate actions whenever such change occurs.

## Creating an order details template using template creation APIs

To create a template through API and understand the general syntax, required categories and
components please refer to [templates API](/docs/whatsapp/business-management-api/message-templates/#creating-templates). All the guidelines outlined above in creating templates apply through API as well.

Order details template can be categorized as “Utility” or "Marketing" template and apart from ‘name’ and ‘language’ of
choice, it has general template components such as HEADER, BODY, FOOTER and a fixed BUTTON with “ORDER\_DETAILS” type.

```
POST https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates
{
  "name": "<TEMPLATE_NAME>",
  "language": "<LANGUAGE_CODE>",
  "category": "UTILITY or MARKETING",
  "display_format": "ORDER_DETAILS",
  "components": [
    {
      "type": "HEADER",
      "format": "TEXT" OR "IMAGE" OR "DOCUMENT",
      "text": "<HEADER_TEXT>"
    },
    {
      "type": "BODY",
      "text": "<BODY_TEXT>"
    },
    {
      "type": "FOOTER",
      "text": "<FOOTER_TEXT>"
    },
    {
      "type": "BUTTONS",
      "buttons": [
        {
          "type": "ORDER_DETAILS",
          "text": "<COPY_PIX_CODE>"
        }
      ]
    }
  ]
}
```

## Sending order details template message

Order details template message allows the businesses to send invoice (order\_details) message as predefined `order details` call-to-action button component parameters. It supports businesses to send all payment integration (such as [Dynamic Pix code](/docs/whatsapp/cloud-api/payments-api/payments-br/offsite-pix), [Payment Links](/docs/whatsapp/cloud-api/payments-api/payments-br/payment-links), [Boleto](/docs/whatsapp/cloud-api/payments-api/payments-br/boleto), etc) integration as button parameters.

To send an order details template message, make a `POST` call to `/PHONE_NUMBER_ID/messages` endpoint and attach a message object with `type=template`. Then, add a template object with a predefined `order details` call-to-action button.

You can optionally include a **PDF file** as attachment in the `header` component of the template message. To do so, you use `type=document` in the `parameter` object of the `header` component object, as described in our [Components](/docs/whatsapp/business-management-api/message-templates/components#media-header) document.

For example following sample describes how to send [Copy Pix code](/docs/whatsapp/cloud-api/payments-api/payments-br/offsite-pix) in order details template message parameters to prompt the consumer to make a payment.

```
POST https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>/messages
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<PHONE_NUMBER>",
  "type": "template",
  "template": {
    "name": "<TEMPLATE_NAME>",
    "language": {
      "policy": "deterministic",
      "code": "<LANGUAGE_AND_LOCALE_CODE>"
    },
    "components": [
      {
        "type": "button",
        "sub_type": "order_details",
        "index": 0,
        "parameters": [
          {
            "type": "action",
            "action": {
              "order_details": {
                "reference_id": "<UNIQUE_REFERENCE_ID>",
                "type": "digital-goods",
                "payment_type": "br",
                "payment_settings": [
                  {
                    "type": "pix_dynamic_code",
                    "pix_dynamic_code": {
                      "code": "00020101021226700014br.gov.bcb.pix2548pix.example.com...",
                      "merchant_name": "Account holder name",
                      "key": "39580525000189",
                      "key_type": "CNPJ"
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
        ]
      }
    ]
  }
}
```

Once the order details template message is delivered, a successful response will include an object with an identifier prefixed with wamid. Use the ID listed after wamid to track your message status.

```
{
    "messaging_product": "whatsapp",
    "contacts": [
        {
            "input": "<PHONE_NUMBER>",
            "wa_id": "<WHATSAPP_ID>"
        }
    ],
    "messages": [
        {
            "id": "wamid.ID"
        }
    ]
}
```

## Post order details template message flow

After the order details template message delivery the rest of the payment flow is the same as “Sending invoice in customer session window” and depends on the chosen [payment integration](/docs/whatsapp/cloud-api/payments-api/payments-br) order details parameters.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Send order details template message](#send-order-details-template-message)

[Overview](#overview)

[Creating an order details template on Whatsapp Manager](#creating-an-order-details-template-on-whatsapp-manager)

[Creating an order details template using template creation APIs](#creating-an-order-details-template-using-template-creation-apis)

[Sending order details template message](#sending-order-details-template-message)

[Post order details template message flow](#post-order-details-template-message-flow)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Wnbnu6r82wk_ORodLCPfkA&oh=00_AfhMap-yaaxjdLAbvrn8aMAuDUO42J8mVrZ8byesEKtxJg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Wnbnu6r82wk_ORodLCPfkA&oh=00_AfjFJG_OuwmZhXSAh2TDeGfK_VmN87MtCirsh_S6UGUu6w&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Wnbnu6r82wk_ORodLCPfkA&oh=00_AfhkKs3xQneG0l-KX9fRkFffoItR0fxnOSNTWCYr8iygSA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Wnbnu6r82wk_ORodLCPfkA&oh=00_AfjTovOT4ZmsdESXWzc4GEPyhc8VS5xXw0ZNs2iXOEnHXA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Wnbnu6r82wk_ORodLCPfkA&oh=00_Afiu9b4Jon9_xFQZY9bzTIv1iZ0PoSPMBpmN9GMme2iPxA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3fkUqoJ41XuOQ_jGcgQTH3SxHxaqlfoBLanWApCCL4015LSJSz053cE2dmbyjVSdq3fkoGuAIIAVkkhVwHfpzPIsPjqcXB59LiFJs89axW74goB2jkyk1WMZSleaRFy1aLy8JxO2BJtMLjNb-tYQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)