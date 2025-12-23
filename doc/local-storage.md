![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Foverview%2Flocal-storage%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Visão geral](/docs/whatsapp/cloud-api/overview)[Armazenamento Local](/docs/whatsapp/cloud-api/overview/local-storage)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)

  + [Privacidade e segurança de dados](/docs/whatsapp/cloud-api/overview/data-privacy-and-security)
  + [Armazenamento Local](/docs/whatsapp/cloud-api/overview/local-storage)
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
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Local Storage](#local-storage)

[How local storage works](#how-local-storage-works)

[Data in scope](#data-in-scope)

[Available Regions](#available-regions)

[Limitations](#limitations)

[Enabling Local Storage](#enabling-local-storage)

[Step 1: Enable local storage on the number](#step-1--enable-local-storage-on-the-number)

[Step 2: Register the number](#step-2--register-the-number)

[Getting Local Storage Settings](#getting-local-storage-settings)

[Disabling Local Storage](#disabling-local-storage)

[Enabling Local Storage (v20 and older)](#enabling-local-storage--v20-and-older-)

[Step 1: Check verification status](#step-1--check-verification-status)

[Step 2: Request a verification code](#step-2--request-a-verification-code)

[Step 3: Verify the business phone number](#step-3--verify-the-business-phone-number)

[Step 4: Reregister the business phone number](#step-4--reregister-the-business-phone-number)

[Disabling Local Storage (v20 and older)](#disabling-local-storage--v20-and-older-)

[FAQs](#faqs)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/overview/local-storage/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 21 de out
Atualização em Português (Brasil): 25 de fev

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Local Storage

Local storage offers an additional layer of data management control, by giving you the option to specify where your message data is stored at rest. If your company is in a regulated industry such as finance, government, or healthcare, you may prefer to have your message data stored in a specific country when at rest because of regulatory or company policies.

## How local storage works

Local storage is controlled by a setting enabled or disabled at a WhatsApp business phone number level. Both Cloud API and MM Lite API support local storage, and the setting will apply to any messages sent via either API if enabled.

When Local storage is enabled, the following constraints are applied to message content for a business phone number:

* **Data-in-use:** When message content is sent or received by Cloud API or MM Lite API, message content may be stored on Meta data centers internationally while being processed.
* **Data-at-rest:** After the data-in-use period, message content is deleted from Meta data centers outside of the specified local storage region, and persisted only in data centers within the local storage region selected. Note that the data-in-use period differs between Cloud API and MM Lite API as specified below:
  + When using local storage for Cloud API, the data-in-use period is up to 60 minutes.
  + When using local storage for MM Lite API, the data-in-use period is up to 90 minutes.

The local storage feature supplements other [WhatsApp Business Platform privacy and security controls](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2Ftrust-and-safety%3Ffbclid%3DIwZXh0bgNhZW0CMTEAYnJpZBExNkRZWTlJbDFSMDBUVlRLZwEe2Qq3X5Y-XnlgB832KjRawCRQOBQGgvzV0IgHxrk5kplGc2LAfA7cvutA9ms_aem_HXrl5zwbIRR1MUiy5tf6Cw&h=AT0j2LFzT6mRfzRLEZpUdGa5SEBnFjH8JqSn5aB2iuEI0s21fjDvfQLdMcAXMSms6-7ClgJ3bY0D6OCLj0yUqy6qS0llzdQl0JYdjxTwnQKVPCbIBN5MX6uf7QjmroPa2dDZO3pHPYjV5Vc99igGop4ChjvohSwi0z4), and allows customers to ensure a higher level of compliance with local data protection regulations.

## Data in scope

Local storage applies to message content (text and media) sent and/or received via Cloud API and MM Lite API. The following message content are in scope of the local storage feature:

* Text messages: text payload (message body)
* Media messages: media payload (audio, document, image or video)
* Template messages (static template + parameters passed at message send time): components with text / media payload

In addition, a limited set of metadata attributes is included with the locally stored message content, in order to correctly associate the encrypted message payload with the originally processed message, and to audit the fact of localization. The stored metadata is protected with tokenization and encryption.

## Available Regions

To see what regions are supported by local storage, see the `data_localization_region` parameter in the [documentation on phone number registration](/docs/whatsapp/cloud-api/reference/registration/#register).

## Limitations

* Media files uploaded by a business phone number with local storage enabled are only accessible to that specific phone number, and cannot be shared with other phone numbers associated with the business.

## Enabling Local Storage

Follow the steps below to enable local storage for an unregistered business phone number using API version 21.0 or newer. If you are using an older API version, see [Enabling Local Storage (v20 and older)](/docs/whatsapp/cloud-api/overview/local-storage#enabling-local-storage--v20-and-older-).

### Step 1: Enable local storage on the number

Local storage can only be enabled or disabled on WhatsApp business phone numbers when they are in an unregistered state. If a phone number is currently registered, it must be unregistered and re-registered with local storage enabled.

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/settings**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/settings/#Updating) endpoint to enable local storage on the unregistered business phone number:

#### Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/settings

{
  "storage_configuration": {
    "status": "IN_COUNTRY_STORAGE_ENABLED",
    "data_localization_region": "<COUNTRY_CODE>"
  }
}
```

Set `<COUNTRY_CODE>` to the [country code](#available-regions) of the country where data-at-rest should be stored.

#### Response Syntax

```
{
  "success": <SUCCESS>
}
```

Upon success, `<SUCCESS>` will be set to `true`.

#### Example Request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/settings' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "storage_configuration": {
    "status": "IN_COUNTRY_STORAGE_ENABLED",
    "data_localization_region": "BR"
  }
}'
```

#### Example Response

```
{
  "success": true
}
```

### Step 2: Register the number

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/register**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/register/#Creating) endpoint to register the business phone number.

#### Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/register

{
  "messaging_product": "whatsapp",
  "pin": "<TWO_STEP_PIN>"
}
```

Set `<TWO_STEP_PIN>` to the desired two-step verification PIN for the business phone number.

#### Response Syntax

```
{
  "success": <SUCCESS>
}
```

Upon success, `<SUCCESS>` will be set to `true`.

#### Example Request

```
curl 'https://graph.facebook.com/v21.0/v24.0/register' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "123456"
}'
```

#### Example Response

```
{
  "success": true
}
```

## Getting Local Storage Settings

Use the [**GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/settings**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/settings#Reading) endpoint to get local storage settings on a WhatsApp Business Phone Number. For example:

```
curl 'https://graph.facebook.com/v24.0/179776755229976/settings' \
-H 'Authorization: Bearer EAAJB...'
```

This returns a [node that represents the local storage settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status-settings/) on the business phone number. For example:

```
{
  "storage_configuration": {
    "status": "IN_COUNTRY_STORAGE_ENABLED",
    "data_localization_region": "BR"
  }
}
```

## Disabling Local Storage

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/settings**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/settings/#Updating) endpoint to disable local storage on an unregistered business phone number using API version 21.0 or newer. If you are using an older API version, see [Disabling Local Storage (v20 and older)](#disabling-local-storage--v20-and-older-).

#### Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID/>settings

{
  "storage_configuration": {
    "status": "IN_COUNTRY_STORAGE_DISABLED"
  }
}
```

Set `<COUNTRY_CODE>` to the [country code](#available-regions) of the country where data-at-rest should be stored.

#### Response Syntax

```
{
  "success": <SUCCESS>
}
```

Upon success, `<SUCCESS>` will be set to `true`.

#### Example Request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/settings' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "storage_configuration": {
    "status": "IN_COUNTRY_STORAGE_DISABLED"
  }
}'
```

#### Example Response

```
{
  "success": true
}
```

## Enabling Local Storage (v20 and older)

To enable local storage for an unregistered business phone number using API version 20.0 or older:

### Step 1: Check verification status

Use the [**GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER>**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) endpoint and request the `code_verification_status` field. If the code verification status is `VERIFIED`, skip to step 4. Otherwise, proceed to step 2.

### Step 2: Request a verification code

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/request\_code**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/request_code/#Creating) endpoint to request a verification code. Upon success, the API will respond with `true` and a verification code will be sent to the business phone number via the method specified in the `code_method` parameter.

For example, this query requests a verification code to be sent via SMS in the English language (US locale).

```
curl -X POST 'https://graph.facebook.com/v20.0/110200345501442/request_code?code_method=SMS&language=en_US' \
-H 'Authorization: Bearer EAAJB...'
```

Use the code in the delivered message in the next step.

### Step 3: Verify the business phone number

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/verify\_code**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/verify_code/#Creating) endpoint to verify the business phone number using the verification code included in the message you received from the previous step.

For example:

```
curl -X POST 'https://graph.facebook.com/v20.0/110200345501442/verify_code?code=123830' \
-H 'Authorization: Bearer EAAJB...'
```

### Step 4: Reregister the business phone number

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/register**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/register/#Creating) endpoint to register the business phone number. Indicate the country where data-at-rest should be stored using the `data_localization_region` parameter.

For example, this request enables local storage on a business phone number, and sets the country where data should be stored to India:

```
curl 'https://graph.facebook.com/v20.0/110200345501442/register' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "123456",
  "data_localization_region": "IN"
}'
```

## Disabling Local Storage (v20 and older)

Use the [**POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/deregister**](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/deregister/#Creating) endpoint to disable local storage on a business phone number using API version 20.0 or older.

For example:

```
curl -X POST 'https://graph.facebook.com/v24.0/110200345501442/deregister' \
-H 'Authorization: Bearer EAAJB...'
```

Note that this deregisters the business phone number so it cannot be used with WhatsApp Cloud API. If you want to continue using it with Cloud API but without local storage enabled, you must reregister it without including the `data_localization_region` parameter.

## FAQs

**Q. What are the migration paths for moving a phone number to the Cloud API version with Local Storage?**

We support all migration paths to Cloud API version with Local Storage, this includes:

* Existing On-Premise API number migrating to Cloud API version with Local Storage
* Existing Cloud API number migrating to Cloud API version with Local Storage
* New Cloud API number enabling Local Storage

In all these scenarios you would need to send a POST request to the [/register](/docs/whatsapp/cloud-api/reference/registration#register) endpoint for the selected phone number, specifying the target country for which data to be localized in a new parameter `data_localization_region`.

**Q. Are there any migration risks? Any downtime associated with this?**

No migration risks, this is a similar process as migrating from On-Premise API to Cloud API. See our [developer documentation here](/docs/whatsapp/cloud-api/guides/migrating-from-onprem-to-cloud). Downtime is typically less than 5 minutes and no re-verification of the business phone number is required.

**Q. Is there any downtime associated with enabling local storage for a business phone number?**

If a business phone number is already registered, you will need to de-register and re-register the phone number with local storage enabled. This process typically takes less than 5 minutes. No re-verification of the business phone number is required during this process.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Local Storage](#local-storage)

[How local storage works](#how-local-storage-works)

[Data in scope](#data-in-scope)

[Available Regions](#available-regions)

[Limitations](#limitations)

[Enabling Local Storage](#enabling-local-storage)

[Step 1: Enable local storage on the number](#step-1--enable-local-storage-on-the-number)

[Step 2: Register the number](#step-2--register-the-number)

[Getting Local Storage Settings](#getting-local-storage-settings)

[Disabling Local Storage](#disabling-local-storage)

[Enabling Local Storage (v20 and older)](#enabling-local-storage--v20-and-older-)

[Step 1: Check verification status](#step-1--check-verification-status)

[Step 2: Request a verification code](#step-2--request-a-verification-code)

[Step 3: Verify the business phone number](#step-3--verify-the-business-phone-number)

[Step 4: Reregister the business phone number](#step-4--reregister-the-business-phone-number)

[Disabling Local Storage (v20 and older)](#disabling-local-storage--v20-and-older-)

[FAQs](#faqs)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfjgXZRURPV1HyuNraXC9dOT8C_fLmr6C8BWnef64-VTKw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgzjhineygvF2qlzcJzSSlzlao8IkfonTwpfOMCnm_qtQ&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgKiT6uY4X6EaZ95wmOoCmVjn_TlDGastnaqhMvm4xG4Q&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3hPNFLtAryRiJ-4egtZ438j99CYpUubv6LgAuwYhBBn4Q4QwC8P-GYTmygxaotv3wqvuN3_ju65pRfB1SIz2HwV5I-C57i3-AB2lVxwRImQSx1iRzVzTR9bogKLVbjJVKdgRDUBDohmYPDfmw77Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_Afjep-yNxVPET3Q7dQv7e1xqnLept1baasYLVc0-li_hsw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT17bDdAkVbt7LbKKCsUplQAMBOrBVwaIEzeye3EsvqEZpO45I9BzJTqY_2QEBhfqjuy7iltVsaJNfpp6jpCqToldAM-5aeYlA6UaiDrrMyBTA8Ioyi7DmUN4heMe25HY5L_-P4NSmR473Til94TeA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgXKMRyEBe8l_pIMPTexllTa8EgYSGOgBHUG9KRUXFYWQ&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1bKj7DOiQV6iUl7FlZ36XJmtiTuXbHoKBjEN7kVH-HTCK0SX4KkzmXCE0QL_EznR6Kh-XB_vSQ7gY3yMEN_DL0aCXD4NSPFIpXjAYaF-kLop_aK3MBr5IYL8lCKzDou8t-7A74waBLa0_j9Ph-ug)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgrrxZeAZNzD_iCHPjEZVIOsU3HLcUUCdbwnojvbK1ecg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1kv5K9ixmwA06cMUK3xjOJxH8Vt2_VYituN-sP9pkq1tRwmNacuamjAdCkp_rDtKR0iTNJiwn22t6TEBo-YbK5e4wwRmTItip4GWFcv0vHZUhTHEItU3WNTH1vm5PHbQRHiL2uRis_XuFwVocY2g)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0r317RYFdYIYtFA9SGYbzH1cffkPcUcvg7GC0ENFDSkLJvGoMZ_Be4eO2mkx8dsZFB41pBS0NRAo9Nu7mRRlYc-YptcFoX1-KgViVbhMGBhRYjQ300HCxWPHC-nx3_Xw6q7F1sYzi_45Y1RAXHXw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0CbOsOdfyO0njjd047w3v9yzewWyq1yKgrZa8HNUKqe3gR2ILfktGyCDT-fJc_snTzxYnXTbRit7v01EovKawRBEuwqKAEPDL6hjlxT0BN48MWuSyqL18blotJFtIrwleDLTAodC51EeEAYXErbA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_Afhx_4z8vEEa_0vNVWW9EAx2W-r8ktRKdaI_HMP7_72gJw&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfhUC-eFulz4Vuqrh_qaZ4YwMYJ8WsZ9fqB-gM3GOSNa-w&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1L2Nebn5Uh3m1PP5bE0lu8JEjUuC46-JZbWVUQCXLr0dOYT8aXWln2ANUh7G8a48QVxNehBDEp_yfnIRiXsxp1Xf6EY9iIp_6eh6OBl8CUib6NYocbbuggSuaxQWsnSbhGYMNQIyq9mMlTZrUu4g)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgJkEymcbx1N2UZnfuqDX0V2CtQTibu6bbLe6z60-WjCw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3OCd26k21tJxfG2iIi8jyk4IWdU1AiI3Ox0WznJ0DbGa2F8pFPIpVFb8nZe8wP3Z-vjWqDf1K_sJRI4EQLXsU3ByOUYDgppjb3-hgUasiLndhY-wm0FgVTHBNpV7DpHseEU8R5UqX-wVg6xp1zkA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfgjB7zo4gkzTLQIxA49840WYDF_rR9mvh_0SC5ctlBgPg&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1jplwesjqZHpNFSalWEs4BuP-5BoC9FJtho1ok_I1D9sd_PMRI6frhUj1B1Cqg-jw-o1DTa4xOp_E5vZtyndVvtIfe975aNdk7PXEPPcq0Nkl9d_5ZsiO0tm0B-pAiZua1X9OClD4F-QP2UUtn7w)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=lESw1BGQ0KXwpWu5Uf5R3Q&oh=00_AfhWQh9rbjlu9Dk5fC9y0cloOUGJE2WWsedN-HuZee-KGQ&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3hoeBoZz3Jz873nyF-MsUb-7gp5vmW9eCAJmrtY6HNhxDqje0D_sD-oUKg8Mi2txifnTsy9mOng_q-2NrOsjvjAva-EzfzK9GP_K0vdcS6bv6bquCg5t1yeIDKyEYxwu9ah2KxD7JznVAwmHOkig)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2UTrl94F2tfNJtdy5XNIltE58-2_r8gJxPClSruaC8ClhpA8zK7LGAUTMtKAg23lop8IvbcmjVuXYW3b4YEqST-PWaoJ40xmKp4m6TexRNEeGXWHbvYLgMO18qHswlnOMZb0HZj_fFxO4sos39Fg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)