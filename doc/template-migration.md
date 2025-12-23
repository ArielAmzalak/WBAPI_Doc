![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-migration%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)
  + [Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)
  + [Componentes](/docs/whatsapp/business-management-api/message-templates/components)
  + [Management](/docs/whatsapp/business-management-api/message-templates/template-management)
  + [Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)
  + [Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)
  + [Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)
  + [Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)
  + [Review](/docs/whatsapp/business-management-api/template-review)
  + [Languages](/docs/whatsapp/business-management-api/message-templates/supported-languages)
  + [Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)
  + [Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)
  + [Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)
  + [Groups](/docs/whatsapp/business-management-api/message-templates/template-groups)
  + [Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)
  + [Time-to-live](/docs/whatsapp/business-management-api/time-to-live)
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

[Template migration](#template-migration)

[Limitations](#limitations)

[Request syntax](#request-syntax)

[Parameters](#parameters)

[Response](#response)

[Response properties](#response-properties)

[Example request](#example-request)

[Example response](#example-response)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/message-templates/template-migration/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 14 de nov
Atualização em Português (Brasil): 18 de abr

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# Template migration

This document describes how to migrate templates from one WhatsApp Business Account (WABA) to another. Note that migration doesn't move templates, it recreates them in the destination WABA.

## Limitations

* Templates can only be migrated between WABAs owned by the same Meta business.
* Only templates with a status of `APPROVED` and a `quality_score` of either `GREEN` or `UNKNOWN` are eligible for migration.

## Request syntax

Use the [WhatsApp Business Account > Migrate Message Templates](/docs/graph-api/reference/whats-app-business-account/migrate_message_templates/) endpoint to migrate templates from one WABA to another.

```
curl -X POST "https://graph.facebook.com/<API_VERSION>/<DESTINATION_WABA_ID>/migrate_message_templates" \
-H "Authorization: Bearer <ACCESS_TOKEN>" \
-H "Content-Type: application/json" \
-d '
{
  "source_waba_id": "<SOURCE_WABA_ID>",
  "page_number": <PAGE_NUMBER>,
  "count": <COUNT>

  <!-- only if migrating specific templates that failed to migrate -->
  "template_ids": [<TEMPLATE_IDS>]
}'
```

### Parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<COUNT>`  *Integer* | **Optional.**  Overrides the default batch size with a maximum count of 500.  If the request takes longer than 30 seconds to execute and times out, reduce the count number. | `200` |
| `<DESTINATION_WABA_ID>`  *WhatsApp Business Account ID* | **Required.**  Destination WhatsApp Business Account ID. | `104996122399160` |
| `<PAGE_NUMBER>`  *Integer* | **Optional.**  Indicates amount of templates to migrate as sets of 500. Zero-indexed. For example, to migrate 1000 templates, send one request with this value set to `0` and another request with this value set to `1`, in parallel. | `0` |
| `<TEMPLATE_IDS>`  *Array of strings* | **Optional.**  Only use to migrate specific template IDs with a max array length of 500. For example, to migrate failed template IDs, add the specific template ID to the array. | `["35002248699842","351234565148","54382248699842"]` |
| `<SOURCE_WABA_ID>`  *WhatsApp Business Account ID* | **Required.**  Source WhatsApp Business Account ID. | `102290129340398` |

## Response

```
{
  "migrated_templates": [<MIGRATED_TEMPLATES>],
  "failed_templates": [<FAILED_TEMPLATES>]
}
```

### Response properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<MIGRATED_TEMPLATES>`  *List* | List of template IDs that were successfully duplicated in the destination WhatsApp Business Account. | `"1473688840035974","6162904357082268","6147830171896170"` |
| `<FAILED_TEMPLATES>`  *Map* | Map identifying templates that were not duplicated in the destination WhatsApp Business Account.   Keys are template IDs and values are failure reasons. | `"1019496902803242":"Incorrect category",` `"259672276895259":"Formatting error - dangling parameter",` `"572279198452421":"Incorrect category"` |

## Example request

```
curl -X POST 'https://graph.facebook.com/v24.0/104996122399160/migrate_message_templates?source_waba_id=102290129340398&page_number=0' \
-H 'Authorization: Bearer EAAJB...'
```

## Example response

```
{
  "migrated_templates": [
    "1473688840035974",
    "6162904357082268",
    "6147830171896170"
  ],
  "failed_templates": {
    "1019496902803242": "Incorrect category",
    "259672276895259": "Formatting error - dangling parameter",
    "572279198452421": "Incorrect category"
  }
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template migration](#template-migration)

[Limitations](#limitations)

[Request syntax](#request-syntax)

[Parameters](#parameters)

[Response](#response)

[Response properties](#response-properties)

[Example request](#example-request)

[Example response](#example-response)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W9GU83VZURprVCc0xMOLYw&oh=00_AfhzE-eBn8rWGQZ6zVbqhmW_tr7kBQGfUwafE7IPbsoX6g&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W9GU83VZURprVCc0xMOLYw&oh=00_AfiniobHCQQXVSRBKpwDGElpUjJyLwjt4yQEcjEfh2D_6Q&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W9GU83VZURprVCc0xMOLYw&oh=00_AfholUMJESz5_tIb-35KxgTrV_rCqrjVSCMQDQrqfLiitA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W9GU83VZURprVCc0xMOLYw&oh=00_Afg1-kG9wE7jWqDvvQVcEw6IGB388FkSzsO35hOmBZXCdw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W9GU83VZURprVCc0xMOLYw&oh=00_AfjytzDl094h1ux24zaFP_MOWAx-CczeHzIJkChVcF8vBA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2Zzsx1LSKbDEh0Y5VOAuE9Wmh-UZaSoZeaG94sq2tk2fKcfp1uEGAO6p0b5DnMK-t4G-U_wueUPLBxCedHYr6UrUNcZk1B_M2PPqli61zjszZwBwQDzDUq7bpvadzPbuZr_aRE8USq9-3qOSHI2Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)