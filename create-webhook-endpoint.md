![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fwebhooks%2Fcreate-webhook-endpoint%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)[Create a webhook endpoint](/docs/whatsapp/webhooks/create-webhook-endpoint)

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

[Create a webhook endpoint](#create-a-webhook-endpoint)

[TLS/SSL](#tls-ssl)

[mTLS](#mtls)

[GET requests](#get-requests)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Validation](#validation)

[Response](#response)

[POST requests](#post-requests)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Validation](#validation-2)

[Response](#response-2)

[Batching](#batching)

[Configure webhooks](#configure-webhooks)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Create a webhook endpoint

Learn about webhook requests and responses so you can set up and configure your own webbook endpoint on a public server.

Before you can use your app in a production capacity, you must create and configure your own webhook endpoint on a public server that can accept and respond to GET and POST requests, and that can validate and capture webhook payloads.

## TLS/SSL

Your webhook endpoint server must have a valid TLS or SSL digital security certificate, correctly configured and installed. Self-signed certificates are not supported.

## mTLS

Webhooks support mutual TLS (mTLS) for added security. See Graph API's [mTLS for webhooks](/docs/graph-api/webhooks/getting-started#mtls-for-webhooks) document to learn how to enable and use mTLS.

Note that enabling and disabling mTLS is not supported at the WABA or business phone number level. If you have more than one application accessing the platform, you will need to enable mTLS for each application.

## GET requests

GET requests are used to verify your webhook endpoint. Anytime you [set or edit the **Callback URL** field or the **Verify token** field](#configure-webhooks) in the App Dashboard, we will send a GET request to your webhook endpoint. You must validate and respond to this request.

### Request syntax

```
GET <CALLBACK_URL>
  ?hub.mode=subscribe
  &hub.challenge=<HUB.CHALLENGE>
  &hub.verify_token=<HUB.VERIFY_TOKEN>
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<CALLBACK_URL>` | Your webhook endpoint URL.  Add this URL to the **Callback URL** field in the App Dashboard when you [configure webhooks](#configure-webhooks) later. | `https://www.luckyshrub.com/webhooks` |
| `<HUB.CHALLENGE>` | A random string that we will generate. | `1158201444` |
| `<HUB.VERIFY_TOKEN>` | A verification string of your own choosing. Store this string on your server.  Add this string to the **Verify token** field in the App Dashboard when you [configure webhooks](#configure-webhooks) later. | `vibecoding` |

### Validation

To validate GET requests, compare the `hub.verify_token` value in the request to the verification string you have stored on your server. If the values match, the request is valid, otherwise it is invalid.

### Response

If the request is valid, respond with HTTP status `200` and the `hub.challenge` value. If the request is invalid, respond with a 400-level HTTP status code, or anything other than status `200`.

When you [configure webhooks](docs/whatsapp/cloud-api/guides/set-up-webhooks#configure-webhooks), we will send a GET request to your webhook endpoint. If it returns status `200` and the `hub.challenge` value included in the request, we will consider your webhook endpoint verified, and begin sending you webhooks. If your webhook endpoint responds with anything else, however, we will consider your webhook endpoint unverified, and webhooks will not be sent to your endpoint.

## POST requests

Anytime a webhook event is triggered for any webhook fields you are subscribed to, a POST request will be sent to your webbook endpoint, containing a JSON payload describing the event.

### Request syntax

```
POST <CALLBACK_URL>
Content-Type: application/json
X-Hub-Signature-256: sha256=<SHA256_PAYLOAD_HASH>
Content-Length: <CONTENT_LENGTH>

<JSON_PAYLOAD>
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<CALLBACK_URL>` | Your webhook endpoint URL. | `https://www.luckyshrub.com/webhooks` |
| `<CONTENT_LENGTH>` | Content length in bytes. | `492` |
| `<JSON_PAYLOAD>` | Post body payload, formatted using JSON. | See [Fields](/docs/whatsapp/cloud-api/guides/set-up-webhooks#fields) references for example payloads. |
| `<SHA256_PAYLOAD_HASH>` | HMAC-SHA256 hash, calculated using the post body payload and your [app secret](/docs/development/create-an-app/app-dashboard/basic-settings#app-secret) as the secret key. | `b63bb356dff0f1c24379efea2d6ef0b2e2040853339d1bcf13f9018790b1f7d2` |

### Validation

To validate the request:

Generate an HMAC-SHA256 hash using the JSON payload as the message input and your [app secret](/docs/development/create-an-app/app-dashboard/basic-settings#app-secret) as the secret key.
Compare your generated hash to the hash assigned to the `X-Hub-Signature-256` header (everything after `sha256=`).

If the hashes match, the payload is valid. Capture the payload and digest its contents according to business needs. If they do not match, consider the payload invalid.

Note that we do not offer APIs for fetching historical webhook data, so capture and store webhook payload accordingly.

### Response

If the request is valid, respond with HTTP status 200. Otherwise, respond with a 400-level HTTP status, or anything other than status 200.

### Batching

POST requests are aggregated and sent in a batch with a maximum of 1000 updates. However batching cannot be guaranteed so be sure to adjust your servers to handle each POST request individually.

If any POST request sent to your server fails, we will retry immediately, then try a few more times with decreasing frequency over the next 36 hours. Your server should handle deduplication in these cases.

Unacknowledged responses will be dropped after 36 hours.

## Configure webhooks

Once you have created your webhook endpoint, navigate to the **[App Dashboard](/apps)** > **WhatsApp** > **Configuration** panel, and add your webhook endpoint URL to the **Callback URL** field, and your verification string to **Verify token** field.

Note that if you created your app using the **Connect with customers through WhatsApp** use case, navigate to **[App Dashboard](/apps)** > **Use cases** > **Customize** > **Configuration** instead.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/518348561_1679202599393717_3427225193188619311_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=ERZHbUR8GmIQ7kNvwEn7RPL&_nc_oc=Adk6Q1rAmQH3Y6ji5QLKiCgiTQ9rRnd-RCfcGi1K1-Cx0gRO7dWQudNTcke9pFFSrMY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=1UIdJ5md1fKjCVpzzD6tQA&oh=00_AfjvB6Nk6FU4OD_8VJ3FMGKpVpeQLBxHgDy2bgq-juB2Rg&oe=69405C70)

If your webhook endpoint is responding to webhook verification GET requests properly, the panel will save your changes, and a list of fields you can subscribe to will appear. You can then [subscribe to any fields](/docs/whatsapp/cloud-api/guides/set-up-webhooks#fields) that fulfill your business needs.

Note that you can use the [POST Application Subscriptions](https/docs/graph-api/reference/app/subscriptions#creating) endpoint to configure webhooks as an alternative method, but it requires the use of an [app token](/docs/facebook-login/guides/access-tokens#apptokens). See Graph API's [Subscriptions edge](/docs/graph-api/webhooks/subscriptions-edge) document to learn how to do this, and use whatsapp\_business\_account as the object value.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Create a webhook endpoint](#create-a-webhook-endpoint)

[TLS/SSL](#tls-ssl)

[mTLS](#mtls)

[GET requests](#get-requests)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Validation](#validation)

[Response](#response)

[POST requests](#post-requests)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Validation](#validation-2)

[Response](#response-2)

[Batching](#batching)

[Configure webhooks](#configure-webhooks)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YMa-_TDLh43paIWoh6-VeA&oh=00_AfiFyCAh2nNSbJaGBy_atXru6eVKvlukR4ctg03xrx8fbA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YMa-_TDLh43paIWoh6-VeA&oh=00_AfjiumQfaKCreoZz6q18hYai42ohxvxcn3lwBM29-6gWLA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YMa-_TDLh43paIWoh6-VeA&oh=00_AfgOFJxcCr4I-GBzIwGFJoy7kO2tuPbYDpOOEL9NQ2Azpw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YMa-_TDLh43paIWoh6-VeA&oh=00_Afg6KLQtoJXQVD5y8SpQDHvy8U7dbt398T4_cEATigxEqw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YMa-_TDLh43paIWoh6-VeA&oh=00_AfgT7KJ59P-AdEvjrohrQ-DVKtyt52xoqHihNgeCrxtf2w&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3R59UkxepcnAUTY2VHyKr803yh4T0qJYiiOe-rDnifMfktkbARfS_SIlfLHcLcHq5w57Om1KttA4pSCzm3xzfPkerBRvXct_FWgiYw_yUSwBeOdaP1tTVMwXlFhbpHx8FF8oNfbVX4N69hJafRfQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)