![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Freference%2Fregistration%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Referência da API](/docs/whatsapp/cloud-api/reference)[Registro](/docs/whatsapp/cloud-api/reference/registration)

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

[Registration](#registration)

[Register a Business Phone Number](#register)

[Limitations](#limitations)

[Parameters](#parameters)

[Example Request without Local Storage](#example-request-without-local-storage)

[Example Request with Local Storage](#example-request-with-local-storage)

[Deregister a Business Phone Number](#deregister)

[Limitations](#limitations-2)

[Example](#example)

[See Also](#see-also)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/reference/registration/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 4 de nov
Atualização em Português (Brasil): 10 de abr

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Registration

To use your business phone number with Cloud API you must register it. Register your business phone number in the following scenarios:

* Account Creation: When you implement this API, you need to register the business phone number you want to use to send messages. We enforce setting two-step verification during account creation to add an extra layer of security to your accounts.
* Name Change: In this case, your phone is already registered and you want to change your display name. To do that, you must [first file for a name change on WhatsApp Manager](https://www.facebook.com/business/help/378834799515077). Once the name is approved, you need to register your phone again under the new name.
* Migrating your number from On-Premises API to Cloud API. See [Migration Exception](#migration-exception).

Before you can register your business phone number you must first [verify its ownership](/docs/whatsapp/cloud-api/reference/phone-numbers#verify).

### Migration Exception

If you are migrating a phone number from the On-Premises API to the Cloud API, there are extra steps you need to perform before registering a phone number with the Cloud API. See [Migrate From On-Premises API to Cloud API](/docs/whatsapp/cloud-api/guides/migrating-from-onprem-to-cloud) for the full process.

## Register a Business Phone Number

To register your verified business phone number, make a `POST` call to `PHONE_NUMBER_ID/register`. Include the parameters listed below.

| Endpoint | Authentication |
| --- | --- |
| `PHONE_NUMBER_ID/register`  (consulte [Get Phone Number ID](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers)) | Solution Partners must authenticate themselves with an access token with the `whatsapp_business_management` and `whatsapp_business_messaging` permissions. |

### Limitations

Requests to the registration endpoint are limited to 10 requests per business number in a 72 hour moving window.

When you make a registration request, we will check how many registration requests you have made to register that number in the last 72 hours. If you have already made 10 requests, the API will return error code `133016`, and the number will be prevented from being registered for the next 72 hours.

### Parameters

| Name | Description |
| --- | --- |
| `messaging_product` | **Required.**  Messaging service used. Set this to `"whatsapp"`. |
| `pin` | **Required.**  If your verified business phone number already has two-step verification enabled, set this value to your number's 6-digit two-step verification PIN. If you cannot recall your PIN, you can change it. See [Two-step verification](/docs/whatsapp/cloud-api/phone-numbers#two-step-verification).  If your verified business phone number does not have two-step verification enabled, set this value to a 6-digit number. This will be the newly verified business phone number's two-step verification PIN. |
| `data_localization_region` | **Optional.**   If included, enables [local storage](/docs/whatsapp/cloud-api/overview/local-storage/) on the business phone number. Value must be a 2-letter ISO 3166 country code (e.g. `IN`) indicating the country where you want data-at-rest to be stored.   Supported values:   **APAC**   * Australia: `AU` * Indonesia: `ID` * India: `IN` * Japan: `JP` * Singapore: `SG` * South Korea: `KR`   **Europe**   * EU (Germany): `DE` * Switzerland: `CH` * United Kingdom: `GB`   **LATAM**   * Brazil: `BR`   **MEA**   * Bahrain: `BH` * South Africa: `ZA` * United Arab Emirates: `AE`   **NORAM**   * Canada: `CA`   Once enabled, cannot be disabled or changed directly. Instead, you must [deregister](#deregister) the number and register it again without this parameter (to disable), or include the parameter with the new country code (to change).   To enable local storage on a number that has already been registered, you must deregister the number, then register it again and include this parameter. |

### Example Request without Local Storage

```
curl 'https://graph.facebook.com/v24.0/106540352242922/register ' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "212834"
}
```

### Example Request with Local Storage

```
curl 'https://graph.facebook.com/v24.0/106540352242922/register ' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "212834",
  "data_localization_region": "CH"
}
```

All API calls require authentication with access tokens.

Developers can authenticate their API calls with the access token generated in the **App Dashboard** > **WhatsApp** > **API Setup**.

Solution Partners must authenticate themselves with an access token with the `whatsapp_business_messaging` and `whatsapp_business_management` permissions. See [System User Access Tokens](/docs/whatsapp/business-management-api/get-started#system-user-access-tokens) for information.

## Deregister a Business Phone Number

Deregistering a business phone number makes it no longer usable with Cloud API and disables [local storage](/docs/whatsapp/cloud-api/overview/local-storage/) on the number, if it had been enabled.

To deregister a business phone number, make a `POST` call to `PHONE_NUMBER_ID/deregister`:

| Endpoint | Authentication |
| --- | --- |
| `PHONE_NUMBER_ID/deregister`  (consulte [Get Phone Number ID](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers)) | Solution Partners must authenticate themselves with an access token with the `whatsapp_business_management` and `whatsapp_business_messaging` permissions. |

### Limitations

* This endpoint cannot be used to deregister a business phone number that is in use with [both Cloud API and the WhatsApp Business app](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users).
* Deregistration does not delete a number or its message history. To delete a number and its history, see [Delete Phone Number from a WABA](/docs/whatsapp/cloud-api/phone-numbers#deleting-business-phone-numbers).
* Requests to the deregistration endpoint are limited to 10 requests per business number in a 72-hour moving window. If you exceed this amount, the API will return error code `133016`, and the business phone number will be prevented from being deregistered for the next 72 hours.

### Example

Sample Request:

```
curl -X POST \
 'https://graph.facebook.com/v24.0/FROM_PHONE_NUMBER_ID/deregister' \
 -H 'Authorization: Bearer ACCESS_TOKEN'
```

A successful response looks like:

```
{
  "success": true
}
```

## See Also

* [Resetting your PIN](/docs/whatsapp/cloud-api/phone-numbers#changing-your-pin-via-whatsapp-manager)
* [Cloud API Local Storage](/docs/whatsapp/cloud-api/overview/local-storage/)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Registration](#registration)

[Register a Business Phone Number](#register)

[Limitations](#limitations)

[Parameters](#parameters)

[Example Request without Local Storage](#example-request-without-local-storage)

[Example Request with Local Storage](#example-request-with-local-storage)

[Deregister a Business Phone Number](#deregister)

[Limitations](#limitations-2)

[Example](#example)

[See Also](#see-also)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_Afh9opnPihANgpoHqb7MLy2-qmXRGhpZ9OTn_ufVK05E9A&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfgSbbb9ayQ_CNiR-V-tlU9zqY3mj3_LbkRw1v83N72trg&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfhSwuh8rBpCPJwmfrOielzRRhVPNKAvejgfdxNbprRqBg&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2QiWK4q-CGBqOmMM8xqn83vZ9b7N3FTvJv5XW0S2IzvSWd8fLTkcf96ek3eaoWzzUUK3016PP-0smDdHJzo_F_VGC3M4pjuIfsSU1OpqS7R2IHDlo4FlTB_lIc4ToUiLdGTAh6BDfzHwlgGJpCLQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfhokJkygLy-pVg-KDMOMs4h_uYVzfAwjJuer-AGnZSjEw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3xA3WzoIZznd54dWL7uUewRC3ikVUfSin837iMywhlHQiEQYHTEAOXYnARfZ3sfMQ95H2Xl6nM-gACUQefq8gHMLo39WKppbAtjG1h0A68EGDvLvP-zk248KJ86vNC246A3nuu6cIjgmK7feAPuw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_Afi6dbEAR8xT_LKTGikSmAxHFhK-agpp9VMdx1VzdKSg2g&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2PDGR6HS9VbzZE1Eje2SD6lQPLzLU6Gj_rquTVwVE_bKbddChbH66_rQk6UCiQKmoD1BnLhGV5zqh1QEaswyynDIDrPqnTl6w7X9dn-jt5RMI78qvmcAz2jE1AWOkuYO2E6qDBm-ASORks2qw_YA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_Afi45z7ok9yVfD3jClCPY8ZjtckJmgy8K5k8-i78MC1NFA&oe=694035F0)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1cjHN3LyGCmNDTUp3mSls_dTk4AGtmfYWzukMJ7V7SQVjbdJ812_ewT6TEWZNTFoTn6Zuvwxfj3lkX2EmuB6J4aG7aUW-BSJfDazQ52AxfxfTDRh1IVDoIBh7FdfbD9Qof6yRg571HZDYu7TrJsQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1gkb0TLpXt4PldAz7cQ9Y2OTCDkppUigS_0n4ZLRMoHNADeQkTvlmnT8RpX-fbLl9GhCnvk4iIPIiRfxQum2-p1I-9GkrZqLIDlLFBf_MEyrUDEcKvmiwT89yBxTJrRBSdBwcAfWBkQXzbeX-qsg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3xSFcLFRiTukiccP8oz5ZJ7ocp2-QX9xPFOINqSCguFEKSwgx-QHOO7RGN3Qrj5Q-Bb3u0z47gFUtwwGGeAz2c_cx4xGPIAMLFpuxC_lkJgtmUsDnrWcym1tsVHz-p2bC1nvoBo5RiP11J-3PYYA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfhOCpyxW9657sy8A4iynyRtOFs2VqsyGQbPoguo2AATDA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfgRcKhZvATWEdgswvLkiDSN6jawt0cwrJ8S8Zn-07YplQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3w3bR7nmaNTD_9HV9y-f0R9EF4zbqL-0mctsojpvfkY71Yivtm2HHn6C7g4A5IVy42dart-nkiXdILQ5VwdMtRY1PjR_uoUQZeR1t_CnLEOaia-bdKvAAxRvi_4NadDpmakEgs3ROhJ9OwZHiXGQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfhXB4vB0YyfLipkUnjyifmwyhqOCTpTUZyEwRc9pGJlPA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3FrY5uyUZqn6WRfeSTVfQaxyJE8jbJ3KQ_lFqOyIBS4tHamqGgmYVw9LXMmzNOfANgJI9yeXs6D39WVSp9DMmkX2X_dbtkw22LYWy_qJvUHChJgBpc7aiJciPIbcQGC3bMMbTH_V_vZCj-gymPwg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfiKCP6t8U3kcCoNmgy-ExC5_hLjUalxA9sOEXoBG68-XQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1QUmuFWp_Pk8747On8aw9XqZCrIaYhLqO1S2mqwz29Xj4NZeEFRooL4xS3bq6zWrC3kufGIvE-0PE5Mt2NZxIfsBEeLYJgU3DlLDsufUEejQDQxk5n_4IY26ztKxvJ_iycRNOyREOk9WJz7MPkQQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=3AEmdng9ddPq46tJYvGcJA&oh=00_AfjYE-MoN1LrH9ywXygDpVLakp1Kb2PEekw1F3ZvYtPdnw&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2W4s1UN5j48YACaLjPZycbIESPmV8GeAhBSpTf0udRtCXKAH_osd2jAGIqSLOkhNl37mtAbJjzTONH99K6cpk7-5wUrStXFz_oExxjLZuMqVPSjs3F5wG9H4I0FLfWXver1jyN-ZjKCK6AvOPU3g)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2t02efrhcyUp9eqoJ5yJRoA_uKDu1FhQtFMIsQ9SYb3T1AJVhg51bDn_kAJyXu5Q0vzgpHpBape0O4hXA7z31bqJqdBMGFQSz0Of_4P5EVZUfF5cbOHcWYt_8mdiMKJ1QnwK-DlpPEqCtJDnrF7w)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)