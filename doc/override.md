![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Foverride%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)[Substituições de webhook](/docs/whatsapp/cloud-api/webhooks/override)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)

  + [Create a webhook endpoint](/docs/whatsapp/webhooks/create-webhook-endpoint)
  + [Create a test webhook endpoint](/docs/whatsapp/cloud-api/guides/set-up-whatsapp-echo-bot)
  + [Substituições de webhook](/docs/whatsapp/cloud-api/webhooks/override)
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

[Webhook overrides](#webhook-overrides)

[Requirements](#requirements)

[Set WABA alternate callback](#set-waba-alternate-callback)

[Request syntax](#request-syntax)

[Post body](#post-body)

[Body parameters](#body-parameters)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

[Get WABA alternate callback](#get-waba-alternate-callback)

[Example Response](#example-response-2)

[Delete WABA alternate callback](#delete-waba-alternate-callback)

[Set phone number alternate callback](#set-phone-number-alternate-callback)

[Request syntax](#request-syntax-2)

[Post body](#post-body-2)

[Body parameters](#body-parameters-2)

[Response](#response-2)

[Example request](#example-request-2)

[Example response](#example-response-3)

[Get phone number alternate callback](#get-phone-number-alternate-callback)

[Request syntax](#request-syntax-3)

[Response](#response-3)

[Example request](#example-request-3)

[Example response](#example-response-4)

[Delete phone number alternate callback](#delete-phone-number-alternate-callback)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/webhooks/override/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 7 de nov
Atualização em Português (Brasil): 10 de jan

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Webhook overrides

[Messages](/docs/whatsapp/cloud-api/webhooks/reference/messages) webhooks are sent to the callback URL set on your app, but you can override this for your own app by designating an alternate callback URL for the WhatsApp Business Account (WABA) or business phone number.

When a messages webhook is triggered, we will first check if your app has designated an alternate callback URL for the business phone number associated with the message. If set, we will send the webhook to your alternate callback URL. If the phone number has no alternate, we will check if the WABA associated with the number has an alternate callback URL, and if set, send it there. If the WABA also has no alternate, we will then fallback to your app's callback URL.

## Requirements

Before setting an alternate callback URL, make sure your app is [subscribed to webhooks for the WABA](/docs/whatsapp/embedded-signup/webhooks#subscribe-to-a-whatsapp-business-account) and verify that your alternate callback endpoint can receive and process messages webhooks correctly.

## Set WABA alternate callback

Use the [**POST /<WABA\_ID>/subscribed\_apps**](/docs/graph-api/reference/whats-app-business-account/subscribed_apps/#Creating) endpoint to set an alternate callback URL on a WABA.

### Request syntax

```
POST /<WABA_ID>/subscribed_apps
```

### Post body

```
{
  "override_callback_uri":"<WABA_ALT_CALLBACK_URL>",
  "verify_token":"<WABA_ALT_CALLBACK_URL_TOKEN>"
}
```

### Body parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<WABA_ALT_CALLBACK_URL>` | **Required.**  Alternate callback URL where messages webhooks should be sent.  Maximum 200 characters. | `https://my-waba-alternate-callback.com/webhook` |
| `<WABA_ALT_CALLBACK_URL_TOKEN>` | **Required.**  Alternate callback URL [verification token](/docs/graph-api/webhooks/getting-started#verification-requests).  No maximum. | `myvoiceismypassport?` |

### Response

Upon success:

```
{
  "success": true
}
```

### Example request

```
curl -X POST \
'https://graph.facebook.com/v24.0/102290129340398/subscribed_apps' \
-H 'Authorization: Bearer EAAJi...' \
-H 'Content-Type: application/json' \
-d '
{
  "override_callback_uri":"https://my-waba-alternate-callback.com/webhook",
  "verify_token":"myvoiceismypassport?"
}'
```

### Example response

```
{
  "success": true
}
```

## Get WABA alternate callback

Use the [**GET /<WABA\_ID>/subscribed\_apps**](/docs/graph-api/reference/whats-app-business-account/subscribed_apps/#Reading) endpoint to get a list of all apps subscribed to webhooks on the WABA. The response should include an `override_callback_uri` property and value.

### Example Response

```
{
  "data" : [
    {
      "whatsapp_business_api_data" : {
        "id" : "670843887433847",
        "link" : "https://www.facebook.com/games/?app_id=67084...",
        "name" : "Lucky Shrub"
      },
      "override_callback_uri" : "https://my-waba-alternate-callback.com/webhook"
    }
  ]
}
```

## Delete WABA alternate callback

Use the [**POST /<WABA\_ID>/subscribed\_apps**](/docs/graph-api/reference/whats-app-business-account/subscribed_apps/#Creating) endpoint to subscribe your app to webhooks on the WABA [as you normally would](/docs/whatsapp/embedded-signup/webhooks#subscribe) (i.e. without any post body parameters). This will remove the alternate endpoint's callback URL from the WABA, and messages webhooks for the WABA will once again be sent to the callback URL set in the App Dashboard.

## Set phone number alternate callback

Use the [**POST /<BUSINESS\_PHONE\_NUMBER\_ID>**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Creating) endpoint to set an alternate callback URL on the business phone number.

### Request syntax

```
POST /<BUSINESS_PHONE_NUMBER_ID>
```

### Post body

```
{
  "webhook_configuration": {
    "override_callback_uri": "<PHONE_ALT_CALLBACK_URL>",
    "verify_token": "<PHONE_ALT_CALLBACK_URL_TOKEN>"
  }
}
```

### Body parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<PHONE_ALT_CALLBACK_URL>` | **Required.**  Alternate callback URL where messages webhooks should be sent.  Maximum 200 characters. | `https://my-phone-alternate-callback.com/webhook` |
| `<PHONE_ALT_CALLBACK_URL_TOKEN>` | **Required.**  Alternate callback URL [verification token](/docs/graph-api/webhooks/getting-started#verification-requests).  No maximum. | `myvoiceismypassport?` |

### Response

Upon success:

```
{
  "success": true
}
```

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "webhook_configuration": {
    "override_callback_uri": "https://my-phone-alternate-callback.com/webhook",
    "verify_token": "myvoiceismypassport?"
  }
}'
```

### Example response

```
{
  "success": true
}
```

## Get phone number alternate callback

Use the [**GET /<BUSINESS\_PHONE\_NUMBER\_ID>**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) endpoint and request the `webhook_configuration` field to verify that the business phone number has an alternate callback URL.

### Request syntax

```
GET /<BUSINESS_PHONE_NUMBER_ID>
  ?fields=webhook_configuration
```

### Response

Upon success:

```
{
  "webhook_configuration": {
    "phone_number": "<PHONE_ALT_CALLBACK_URL>",
    "whatsapp_business_account": "<WABA_ALT_CALLBACK_URL>",
    "application": "<APP_CALLBACK_URL>"
  },
  "id": "106540352242922"
}
```

Note that `whatsapp_business_account` is only included if the WABA associated with the business phone number also has an alternate callback URL set.

### Example request

```
curl 'https://graph.facebook.com/v17.0/106540352242922?fields=webhook_configuration' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "webhook_configuration": {
    "phone_number": "https://my-phone-alternate-callback.com/webhook",
    "whatsapp_business_account": "https://my-waba-alternate-callback.com/webhook",
    "application": "https://my-production-callback.com/webhook"
  },
  "id": "106540352242922"
}
```

## Delete phone number alternate callback

To delete a business phone number's alternate callback URL, use the [**POST /<BUSINESS\_PHONE\_NUMBER\_ID>**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Creating) endpoint with the `override_callback_uri` property set to an empty string:

```
{
  "webhook_configuration": {
    "override_callback_uri": "",
  }
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Webhook overrides](#webhook-overrides)

[Requirements](#requirements)

[Set WABA alternate callback](#set-waba-alternate-callback)

[Request syntax](#request-syntax)

[Post body](#post-body)

[Body parameters](#body-parameters)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

[Get WABA alternate callback](#get-waba-alternate-callback)

[Example Response](#example-response-2)

[Delete WABA alternate callback](#delete-waba-alternate-callback)

[Set phone number alternate callback](#set-phone-number-alternate-callback)

[Request syntax](#request-syntax-2)

[Post body](#post-body-2)

[Body parameters](#body-parameters-2)

[Response](#response-2)

[Example request](#example-request-2)

[Example response](#example-response-3)

[Get phone number alternate callback](#get-phone-number-alternate-callback)

[Request syntax](#request-syntax-3)

[Response](#response-3)

[Example request](#example-request-3)

[Example response](#example-response-4)

[Delete phone number alternate callback](#delete-phone-number-alternate-callback)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=GrmRzLm27zcT1XjAgL_M8g&oh=00_AfhGdD-fU31KNI1DCVAHINc3A-5JAYiRJ1GusVn63acumA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=GrmRzLm27zcT1XjAgL_M8g&oh=00_AfjjScQETMmFeZU-gCRaIaauuEM7CeL_gJSavtNlJR_Bug&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=GrmRzLm27zcT1XjAgL_M8g&oh=00_AfhO-a7kAsFlGrAuHid40p4xD8vn1B_vRuWLZ8-FCedCng&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=GrmRzLm27zcT1XjAgL_M8g&oh=00_AfiQ5VLIMLjyzZPSCY3qQVsC5OlWS0JqcJ7fude11pZzdQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=GrmRzLm27zcT1XjAgL_M8g&oh=00_AfgRm9L3BujzZWt3RN2tYa7NfHHsGN_hf7tRmGJ4quramQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Jvt0L2dGq0BqRHsJmfX2EVmxAbebsYFQtgyI0UUgp9pgBU_QoJ914-EAl5ENjXsf1VEjCKue71MLcGvbap9BKcRgj1TiKTZpWadzHOZVI2fa3jpYTWK9ekWxNpKt2FR_0bxRuJ4KTi9QCDiy5uw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)