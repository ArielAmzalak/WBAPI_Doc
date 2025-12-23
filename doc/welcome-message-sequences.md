![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fads%2Fwelcome-message-sequences%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)[Guides](/docs/whatsapp/business-management-api/guides)[Welcome Message Sequences](/docs/whatsapp/business-management-api/ads/welcome-message-sequences)

[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)

* [Começar](/docs/whatsapp/business-management-api/get-started)
* [Access tokens](/docs/whatsapp/access-tokens)
* [Permissions](/docs/whatsapp/permissions)
* [Configuração de webhooks](/docs/whatsapp/business-management-api/guides/set-up-webhooks)
* [Guides](/docs/whatsapp/business-management-api/guides)

  + [Análise](/docs/whatsapp/business-management-api/analytics)
  + [Templates](/docs/whatsapp/business-management-api/guides/templates-stub)
  + [Recuperar números de telefone](/docs/whatsapp/business-management-api/manage-phone-numbers)
  + [Migrate numbers via Embedded Signup](/docs/whatsapp/business-management-api/guides/migrate-numbers-via-es-redirect)
  + [Migrate Numbers Programmatically](/docs/whatsapp/business-management-api/guides/migrating-phone-numbers-between-wabas-programmatically)
  + [QR codes](/docs/whatsapp/business-management-api/qr-codes)
  + [Monitorar sinais de qualidade](/docs/whatsapp/guides/how-to-monitor-quality-signals)
  + [Welcome Message Sequences](/docs/whatsapp/business-management-api/ads/welcome-message-sequences)
* [Referência](/docs/whatsapp/business-management-api/reference)
* [Error Codes](/docs/whatsapp/business-management-api/error-codes)

Nesta Página

[Welcome Message Sequences](#welcome-message-sequences)

[Requirements](#requirements)

[Endpoints](#endpoints)

[Create a Sequence](#create-a-sequence)

[Endpoint](#endpoint)

[Sample Request](#sample-request)

[Sample Response](#sample-response)

[Parameters](#parameters)

[Change an Existing Sequence](#change-an-existing-sequence)

[Endpoint](#endpoint-2)

[Sample Request](#sample-request-2)

[Sample Response](#sample-response-2)

[Parameters](#parameters-2)

[Get a List of Sequences](#get-a-list-of-sequences)

[Endpoint](#endpoint-3)

[Sample Request](#sample-request-3)

[Sample Response](#sample-response-3)

[Get a Specific Sequence](#get-a-specific-sequence)

[Endpoint](#endpoint-4)

[Sample Request](#sample-request-4)

[Sample Response](#sample-response-4)

[Delete a Sequence](#delete-a-sequence)

[Endpoint](#endpoint-5)

[Sample Request](#sample-request-5)

[Sample Response](#sample-response-5)

[Webhook](#webhook)

[Marketing API Experience](#marketing-api-experience)

[Ads Manager Experience Walkthrough](#ads-manager-experience-walkthrough)

[Error Codes](#error-codes)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Welcome Message Sequences

When creating ads that Click-to-WhatsApp, you can connect a Welcome Message Sequence from a messaging partner app. A sequence can include text, prefilled message, and FAQs.

This guide explains how to manage Welcome Message Sequences via the API endpoint.

## Requirements

Your app must be granted the **whatsapp\_business\_management** permission.

## Endpoints

```
// Create a new sequence / Change an existing sequence
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

```
// Get a list of sequences / Get a specific sequence
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

```
// Delete a sequence
DELETE /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

## Create a Sequence

To upload a new welcome message sequence, send a `POST` request to the `WHATSAPP_BUSINESS_ACCOUNT_ID/welcome_message_sequences` endpoint.

### Endpoint

```
// Create a new sequence
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

### Sample Request

```
curl -X POST\
-F 'welcome_message_sequence=
      {
       "text":"This is a welcome message authored in a 3P tool",
"autofill_message": {"content": "Hello! Can I get more info on this!"},
"ice_breakers":[
    {"title":"Quick reply 1"},
           {"title":"Quick reply 2"},
           {"title":"Quick reply 3"}
        ]
      }' \
-F 'name="Driver sign-up"' \
"https://graph.facebook.com/v14.0/WhatsappBusinessAccount/welcome_message_sequences"
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Sample Response

In response, a welcome message sequence ID is returned.

```
{"sequence_id":"186473890"}
```

### Parameters

| Parameter | Description | Sample Value |
| --- | --- | --- |
| `sequence_id`  *String* | **Required**   Identifier of the sequence. | `186473890` |
| `name`  *String* | **Required**   Name of the sequence. | `Driver sign-up` |
| `welcome_message_sequence`  *JSON Object* | **Required**   The welcome message JSON that will be sent upon clicking the ad. | ``` {   "text":"This is a welcome message authored in a 3P tool",    "autofill_message": {"content": "Hello! Can I get more info on this!"},   "ice_breakers":[     {"title":"Quick reply 1"},     {"title":"Quick reply 2"},     {"title":"Quick reply 3"}   ] } ``` |

## Change an Existing Sequence

A sequence linked to an active ad cannot be deleted.

To update an existing sequence, send a `POST` request to the `WHATSAPP_BUSINESS_ACCOUNT_ID/welcome_message_sequences` endpoint with:

* The `sequence_id` parameter set to the ID of the sequence being updated
* Other parameters, like `name` or `welcome_message_sequence`, that need to be updated.

### Endpoint

```
// Change an existing sequence
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

### Sample Request

```
curl -X POST\
-F 'sequence_id="186473890"'\
-F 'name="Driver sign-up updated name"' \
"https://graph.facebook.com/v14.0/395394933592466/welcome_message_sequences"
-H 'Authorization: Bearer BEAiil...'
```

### Sample Response

In response, a success message or an error message is returned.

```
{"success": true}
```

### Parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `sequence_id`  *String* | **Required**   Identifier of the sequence. | `186473890` |
| `name`  *String* | **Optional**   Name of the sequence. | `Driver sign-up` |
| `welcome_message_sequence`  *JSON Object* | **Optional**   The welcome message JSON that will be sent upon clicking the ad. | ``` {   "text":"This is a welcome message authored in a 3P tool",    "autofill_message": {"content": "Hello! Can I get more info on this!"},   "ice_breakers":[     {"title":"Quick reply 1"},     {"title":"Quick reply 2"},     {"title":"Quick reply 3"}   ] } ``` |

## Get a List of Sequences

To get an existing sequence, send a `GET` request to the `WHATSAPP_BUSINESS_ACCOUNT_ID/welcome_message_sequences` endpoint with:

### Endpoint

```
// Update an existing sequence
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

### Sample Request

```
curl -X GET "https://graph.facebook.com/v14.0/395394933592466/welcome_message_sequences"
     -H 'Authorization: Bearer BEAiil...'
```

### Sample Response

On success, a list of sequences is returned for that particular app.

```
[
  {
    "sequence_id":"8716291",
    "name":"Driver Sign up",
    "welcome_message_sequence":"<JSON_OBJECT>",
    "is_used_in_ad": true,
  },
  {
    "sequence_id":"4362",
    "name":"Basic Triage",
    "welcome_message_sequence":"<JSON_OBJECT>",
    "is_used_in_ad": false
  },
  {
    "sequence_id":"0139138",
    "name":"Appointment Schedule",
    "welcome_message_sequence":"<JSON_OBJECT>",
    "is_used_in_ad": true
  }
  ...
  ...
  ...,
  {
    "sequence_id":"6987565",
    "name":"Car Leads",
    "welcome_message_sequence":"<JSON_OBJECT>",
    "is_used_in_ad": false
  },
]
```

## Get a Specific Sequence

To get a specific sequence, send a `GET` request to `WHATSAPP_BUSINESS_ACCOUNT_ID/welcome_message_sequences` with the `sequence_id` parameter set to the id of the sequence you want to query.

### Endpoint

```
// Update an existing sequence
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

### Sample Request

```
curl -X GET \
-F 'sequence_id="6987565"'
"https://graph.facebook.com/v14.0/395394933592466/welcome_message_sequences"
-H 'Authorization: Bearer BEAiil...'
```

### Sample Response

On success, a list of sequences is returned for that particular app.

```
[
  {
    "sequence_id":"6987565",
    "name":"Driver Sign up",
    "welcome_message_sequence":"<JSON_OBJECT>",
    "is_used_in_ad": false
  },
]
```

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `sequence_id`  *String* | **Optional**   Identifier of the sequence. | `186473890` |
| `limit`  *int* | **Optional**   Number of sequences to fetch. | `5` |

## Delete a Sequence

A sequence linked to an active ad cannot be deleted.

To delete a sequence, send a `DELETE` request to `WHATSAPP_BUSINESS_ACCOUNT_ID/welcome_message_sequences` with the `sequence_id` parameter set to the id of the sequence you want to delete.

### Endpoint

```
// Update an existing sequence
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/welcome_message_sequences
```

### Sample Request

```
curl -X DELETE \
-F 'sequence_id="1234567890"'
"https://graph.facebook.com/v14.0/395394933592466/welcome_message_sequences"
-H 'Authorization: Bearer BEAiil...'
```

### Sample Response

On success, a list of sequences is returned for that particular app.

```
{"success":true}
```

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `sequence_id`  *String* | **Optional**   Identifier of the sequence. | `186473890` |

## Webhook

The following webhook is triggered when a conversation is started after a user clicks an ad with a Click to WhatsApp’s call-to-action.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "contacts": [
              {
                "profile": {
                  "name": "NAME"
                },
                "wa_id": "ID"
              }
            ],
            "messages": [
              {
                "referral": {
                  "source_url": "AD_OR_POST_FB_URL",
                  "source_id": "ADID",
                  "source_type": "ad or post",
                  "headline": "AD_TITLE",
                  "body": "AD_DESCRIPTION",
                  "media_type": "image or video",
                  "image_url": "RAW_IMAGE_URL",
                  "video_url": "RAW_VIDEO_URL",
                  "thumbnail_url": "RAW_THUMBNAIL_URL",
                  "ctwa_clid": "CTWA_CLID",
                  "ref": "REF_ID",  // New field in referral

                },
                "from": "SENDER_PHONE_NUMBERID",
                "id": "wamid.ID",
                "timestamp": "TIMESTAMP",
                "type": "text",
                "text": {
                  "body": "BODY"
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

## Marketing API Experience

Once welcome message sequences have been successfully submitted over the API, the sequence ID can be used to configure ads through the marketing API.

In the ad creative, the sequence ID can be set as follows:

```
{
  "name": "creative",
  "object_story_spec": {...},
  "asset_feed_spec": {
    "additional_data": {
      "partner_app_welcome_message_flow_id": "<SEQUENCE_ID_RETURNED_FROM_POST_REQUEST>"
    }
  }
}
```

For more information about messaging ads, please refer to [Messaging Ads](https://developers.facebook.com/docs/marketing-api/ad-creative/messaging-ads) in the Marketing API documentation.

## Ads Manager Experience Walkthrough

1: In the **Message Template** section of the Ad Creative, select **Partner App**

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1503629760253987&version=1763416624&transcode_extension=webp)

2: Under **Partner app**, click the dropdown and select the appropriate messaging partner app.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=859572632450175&version=1763416624&transcode_extension=webp)

3: Under **Message sequence**, select the Welcome Message Sequence that you submitted via the API.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=855509433210850&version=1763416624&transcode_extension=webp)

4: Preview your message sequence and click the **Save** button

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1674566360031272&version=1763416624&transcode_extension=webp)

## Error Codes

| Code | Description | Possible Solutions |
| --- | --- | --- |
| `4027001`  Invalid input data | Some or all of the input data is not of the required format. | Check all the fields and parameters passed into the request are of the correct type and format, and that all required parameters are present. |
| `4027005`  Unable to create a welcome message sequence | An error occurred while trying to create a new welcome message sequence. | Check that the access token has all the required permissions for the WhatsApp business account. |
| `4027006`  Unable to update a welcome message sequence | Unable to update the welcome message sequence. | Check all fields and the sequence ID for correctness. Check that the access token has the necessary permissions for the WhatsApp business account. |
| `4027007`  API unavailable | The API being accessed is not available for use yet. | Wait a day or two for the API to become available and try again. |
| `4027010`  Missing parameter | One or more required parameters is missing. | Check all the documentation and ensure the required parameters are present. |
| `4027012`  Sequence used in an ad | The welcome message sequence is linked to an active ad and cannot be updated or deleted. | Disconnect the sequence from the ad and try again. |
| `4027017`  Could not load the sequence | Could not load the sequence being updated or deleted. | The welcome message sequence either does not exist, or you do not have permission to access it. Please check the access token and make sure you have the required permissions. |

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Welcome Message Sequences](#welcome-message-sequences)

[Requirements](#requirements)

[Endpoints](#endpoints)

[Create a Sequence](#create-a-sequence)

[Endpoint](#endpoint)

[Sample Request](#sample-request)

[Sample Response](#sample-response)

[Parameters](#parameters)

[Change an Existing Sequence](#change-an-existing-sequence)

[Endpoint](#endpoint-2)

[Sample Request](#sample-request-2)

[Sample Response](#sample-response-2)

[Parameters](#parameters-2)

[Get a List of Sequences](#get-a-list-of-sequences)

[Endpoint](#endpoint-3)

[Sample Request](#sample-request-3)

[Sample Response](#sample-response-3)

[Get a Specific Sequence](#get-a-specific-sequence)

[Endpoint](#endpoint-4)

[Sample Request](#sample-request-4)

[Sample Response](#sample-response-4)

[Delete a Sequence](#delete-a-sequence)

[Endpoint](#endpoint-5)

[Sample Request](#sample-request-5)

[Sample Response](#sample-response-5)

[Webhook](#webhook)

[Marketing API Experience](#marketing-api-experience)

[Ads Manager Experience Walkthrough](#ads-manager-experience-walkthrough)

[Error Codes](#error-codes)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=FTLmJPZtiM8q_jrvZitFNw&oh=00_AfixPjGjSpbb9RkDfmVgWTnG1ea-RPQF1jvzA9DOVjcMTQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=FTLmJPZtiM8q_jrvZitFNw&oh=00_AfiBJBsJQJPGpPfG3Jr7lLnYOdx_a10yL2JrKjbamwf4rA&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=FTLmJPZtiM8q_jrvZitFNw&oh=00_AfiFt6pKsqCBR12Fh3xle8LmsNaPDU3QvsOF40l7tHPTnQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=FTLmJPZtiM8q_jrvZitFNw&oh=00_AfhECkpNqPe_peLG3jg4B7jXF1IYtkG2pdRQ6FPcDww1Kg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=FTLmJPZtiM8q_jrvZitFNw&oh=00_AfiVMcNLTAxp2UxG4rww3YNXRbYhLXjqvMBYOnto5WQm-A&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0ITmENIUEvvUP2mKKoTXpQ7oFTyGgdKD-7fU8s1rPRehMnr2jTaDk0ElfwV6YZyuUvoIf2CZhCSyMtGvXv2hDmFRiqgu43qv6lEyMYFaQRM5Jeu--G-U_8kJWCATTKfTdP0Q--lzKGQww7goysbg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)