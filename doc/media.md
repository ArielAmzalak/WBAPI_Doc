![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Freference%2Fmedia%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Referência da API](/docs/whatsapp/cloud-api/reference)[Mídia](/docs/whatsapp/cloud-api/reference/media)

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
* [Referência da API](/docs/whatsapp/cloud-api/reference)

  + [Account Migration](/docs/whatsapp/cloud-api/reference/account-migration)
  + [Business Compliance](/docs/whatsapp/cloud-api/reference/business-compliance)
  + [Business Profiles](/docs/whatsapp/cloud-api/reference/business-profiles)
  + [Mídia](/docs/whatsapp/cloud-api/reference/media)
  + [Mensagens](/docs/whatsapp/cloud-api/reference/messages)
  + [Números de telefone](/docs/whatsapp/cloud-api/reference/phone-numbers)
  + [Registro](/docs/whatsapp/cloud-api/reference/registration)
  + [Two-Step Verification](/docs/whatsapp/cloud-api/reference/two-step-verification)
  + [WhatsApp Business Accounts](/docs/whatsapp/cloud-api/reference/whatsapp-business-accounts)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Media](#media)

[Get media ID](#get-media-id)

[Upload media](#upload-media)

[Parameters](#parameters)

[Request](#request)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

[Get media URL](#get-media-url)

[Request syntax](#request-syntax)

[Response syntax](#response-syntax)

[Delete media](#delete-media)

[Request syntax](#request-syntax-2)

[Example response](#example-response-2)

[Download media](#download-media)

[Request syntax](#request-syntax-3)

[Supported media types](#supported-media-types)

[Audio](#audio)

[Document](#document)

[Image](#image)

[Sticker](#sticker)

[Video](#video)

[Media message download constraints](#constraints-media)

[Learn more](#learn-more)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/reference/media/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 17 de nov
Atualização em Português (Brasil): 22 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Media

You use 4 different endpoints to manage your media:

| Endpoint | Uses |
| --- | --- |
| [`POST /PHONE_NUMBER_ID/media`](#upload-media) | Upload media. |
| [`GET /MEDIA_ID`](#get-media-url) | Retrieve the URL for a specific media. |
| [`DELETE /MEDIA_ID`](#delete-media) | Delete a specific media. |
| [`GET /MEDIA_URL`](#download-media) | Download media from a media URL. |

See [Supported Media Types](#supported-media-types) for supported types and size limits.

## Get media ID

Some of the API requests described in this document require a media ID. Media IDs are returned by the API when [uploading media](#upload-media), and are included in incoming media messages webhooks ([image messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/image), [video messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/video), etc.)

Media IDs returned by the API expire after 30 days. Media IDs in webhooks expire after 7 days.

## Upload media

To upload media, make a `POST` call to `/PHONE_NUMBER_ID/media` and include the parameters listed below. All media files sent through this endpoint are encrypted and persist for 30 days, unless they are deleted earlier.

| Endpoint | Authentication |
| --- | --- |
| `/PHONE_NUMBER_ID/media`  (consulte [Get Phone Number ID](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers)) | Developers can authenticate their API calls with the access token generated in the **App Dashboard** > **WhatsApp** > **API Setup**.   Solution Partners must authenticate themselves with an access token with the `whatsapp_business_messaging` permission. |

### Parameters

| Name | Description |
| --- | --- |
| `file` | **Required.**  Path to the file stored in your local directory. For example: "@/local/path/file.jpg". |
| `type` | **Required.**  Type of media file being uploaded. See [Supported Media Types](#supported-media-types) for more information. |
| `messaging_product` | **Required.**  Messaging service used for the request. In this case, use `whatsapp`. |

### Request

```
curl 'https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>/media' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-F 'messaging_product=whatsapp' \
-F 'file=@<FILE_PATH_AND_NAME>;type=<MIME_TYPE>'
```

### Response

Upon success:

```
{
  "id": "<MEDIA_ID>"
}
```

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/media' \
-H 'Authorization: Bearer EAAJB...' \
-F 'messaging_product=whatsapp' \
-F 'file=@/media/template_assets/black_friday_2025.mp4;type=video/mp4'
```

### Example response

```
{
  "id": "1037543291543636"
}
```

## Get media URL

You can query a [media ID](#get-media-id) directly to get a media URL, which you can then query directly with your access token to [download the media asset](#download-media).

Starting November 12, 2025, incoming media messages webhooks ([image messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/image), [video messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/video), etc.) will include the media url automatically, and assign it to a new `url` property. **This property is being released to developers gradually over several weeks, so may not be available to you immediately.**

Media URLs **expire after 5 minutes**, after which you must query the ID again to get a new URL.

### Request syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<MEDIA_ID>?phone_number_id=<BUSINESS_PHONE_NUMBER_ID>' \
-H 'Authorization: Bearer EAAJB'
```

Note that `phone_number_id` is optional. If included, the request will only be processed if the business phone number ID included in the query matches the ID of the business phone number that the media was uploaded on.

### Response syntax

A successful response includes an object with a media url. The URL is only valid for 5 minutes. To use this URL, see [Download Media](#download-media).

```
{
  "messaging_product": "whatsapp",
  "url": "<MEDIA_URL>",
  "mime_type": "<MEDIA_MIME_TYPE>",
  "sha256": "<SHA_256_HASH>",
  "file_size": "<MEDIA_FILE_SIZE>",
  "id": "<MEDIA_ID>"
}
```

## Delete media

Use the **DELETE /<MEDIA\_ID>** endpoint to delete a media asset.

### Request syntax

```
curl -X DELETE 'https://graph.facebook.com/<API_VERSION>/<MEDIA_ID>?phone_number_id=<BUSINESS_PHONE_NUMBER_ID>' \
-H 'Authorization: Bearer EAAJB...'
```

Note that `phone_number_id` is optional. If included, the request will only be processed if the business phone number ID included in the query matches the ID of the business phone number that the media was uploaded on.

### Example response

```
{
  "success": true
}
```

## Download media

To download media, make a `GET` request on the media URL and include your access token. **If you omit your token, the request will fail.**

Note that when retrieving a media from a media ID received via webhook, the media ID will only be available to download for 7 days.

### Request syntax

```
curl '<MEDIA_URL>' \
-H 'Authorization: Bearer EAAJB...' \
-o '<DESIRED_FILE_NAME>'
```

Upon success, the API will respond with the binary data of the media asset. Response headers contain a content-type header to indicate the mime type of returned data. Check [supported media types](#supported-media-types) for supported media types.

If the download attempt fails, you will receive a `404 Not Found` response code. In that case, we recommend you try to [get a new media URL](#get-media-url) and download it again. If doing so doesn't resolve the issue, renew your access token and attempt to download the media asset again.

## Supported media types

### Audio

| Audio Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| AAC | .aac | audio/aac | 16 MB |
| AMR | .amr | audio/amr | 16 MB |
| MP3 | .mp3 | audio/mpeg | 16 MB |
| MP4 Audio | .m4a | audio/mp4 | 16 MB |
| OGG Audio | .ogg | audio/ogg (OPUS codecs only; base audio/ogg not supported; mono input only) | 16 MB |

### Document

| Document Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Text | .txt | text/plain | 100 MB |
| Microsoft Excel | .xls | application/vnd.ms-excel | 100 MB |
| Microsoft Excel | .xlsx | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 100 MB |
| Microsoft Word | .doc | application/msword | 100 MB |
| Microsoft Word | .docx | application/vnd.openxmlformats-officedocument.wordprocessingml.document | 100 MB |
| Microsoft PowerPoint | .ppt | application/vnd.ms-powerpoint | 100 MB |
| Microsoft PowerPoint | .pptx | application/vnd.openxmlformats-officedocument.presentationml.presentation | 100 MB |
| PDF | .pdf | application/pdf | 100 MB |

### Image

Images must be 8-bit, RGB or RGBA.

| Image Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| JPEG | .jpeg | image/jpeg | 5 MB |
| PNG | .png | image/png | 5 MB |

### Sticker

WebP images can only be sent in [sticker messages](/docs/whatsapp/cloud-api/messages/sticker-messages).

| Sticker Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Animated sticker | .webp | image/webp | 500 KB |
| Static sticker | .webp | image/webp | 100 KB |

### Video

Only H.264 video codec and AAC audio codec supported. Single audio stream or no audio stream only.

| Video Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| 3GPP | .3gp | video/3gpp | 16 MB |
| MP4 Video | .mp4 | video/mp4 | 16 MB |

Note that mismatched MIME type (`131053`) is a common error. We recommend that you inspect your media files to verify their MIME type, and make sure that your file name extensions reflect their types. For example, if you are using UNIX, you can inspect a file via the command line to determine its MIME type:

`file -I your-image-asset.png`

## Media message download constraints

The maximum supported file size for media messages on Cloud API is 100MB. In the event the customer sends a file that is greater than 100MB, you will receive a webhook with error code [131052](/docs/whatsapp/cloud-api/support/error-codes#other-errors) and `title`:

*"Media file size too big. Max file size we currently support: 100MB. Please communicate with your customer to send a media file that is smaller than 100MB"*.

We advise that you send customers a warning message that their media file exceeds the maximum file size when this webhook event is triggered.

## Learn more

WhatsApp Business Blog – [Sending WhatsApp media messages from an app](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2Fblog%2Fmedia-messages-via-app&h=AT0FJsBLHHTQwv0RnxnRe5qKmu1k_38l0_QQi0XjtbCoYy-6oZ8aIzf4_8TikSesQryI4DVBu7dGkwE0J_PbfmnQRIjqB-DOL5erqq998RjUr8aKgipdnGz6KzIamVkCQUPo93R8YUVE16iLr4T7-g)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Media](#media)

[Get media ID](#get-media-id)

[Upload media](#upload-media)

[Parameters](#parameters)

[Request](#request)

[Response](#response)

[Example request](#example-request)

[Example response](#example-response)

[Get media URL](#get-media-url)

[Request syntax](#request-syntax)

[Response syntax](#response-syntax)

[Delete media](#delete-media)

[Request syntax](#request-syntax-2)

[Example response](#example-response-2)

[Download media](#download-media)

[Request syntax](#request-syntax-3)

[Supported media types](#supported-media-types)

[Audio](#audio)

[Document](#document)

[Image](#image)

[Sticker](#sticker)

[Video](#video)

[Media message download constraints](#constraints-media)

[Learn more](#learn-more)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TKOIlYbv-SA6v5UuC5XwDA&oh=00_AfjSlUF1yNXVDfPmd4-qsYsmpyOhUou_2fTdW3ja47_pQw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TKOIlYbv-SA6v5UuC5XwDA&oh=00_AfjyNq4da5JtHCHqSfh-xRdcNV-9PORajn-S1uni-NwyNg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TKOIlYbv-SA6v5UuC5XwDA&oh=00_AfjYay6D8OHydJRBO5AOcqUhzno9u_1MF8wq3cjougo2iA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TKOIlYbv-SA6v5UuC5XwDA&oh=00_Afg0Q715VBEiOyE4jBGZTApmP4U1cN_a1akLLBqepaZTIw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TKOIlYbv-SA6v5UuC5XwDA&oh=00_AfjWIzWLYFA1kmkfug1TcpCgz6YSXilVlBbMPUFjvPmo7A&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0V4ayXSjOkYz6Nhr368NqDNlKgn3zV_EGgBDA-1T5v_NFrcHxAlqLx6azL3UnXu1kZ70YVRYYfhoCFdL6DvQec_ZYmH6Dqkyj8O5LY_rQwF6daKYFzP5O-DJkxxd1g9rl6tL1YSi1F3s9dxubSJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)