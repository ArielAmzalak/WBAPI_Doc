![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Ftemplate-quality%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)

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

[Template quality rating](#template-quality-rating)

[Get template quality rating via API](#get-template-quality-rating-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Get template quality rating via WhatsApp Manager](#get-template-quality-rating-via-whatsapp-manager)

[See also](#see-also)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template quality rating

Every template has a quality rating based on usage, customer feedback, and engagement. Templates can have the following ratings, as reported by the API:

* `GREEN` — Indicates high quality. The template has received little to no negative feedback from WhatsApp users. The template can be sent.
* `YELLOW` — Indicates medium quality. The template has received negative feedback from multiple WhatsApp users, or low read-rates, and may soon become paused or disabled. Message templates with this status can still be sent.
* `RED` — Indicates low quality. The template has received negative feedback from multiple WhatsApp users, or low read-rates. The template can be sent, but is in danger of being paused or disabled soon. We recommend that you address the issues that users are reporting. are reporting.
* `UNKNOWN` — Indicates a quality score is still pending, because it has yet to receive WhatsApp user feedback or read-rate data. The template can be sent.

Newly created templates have a quality score of `UNKNOWN`, but their rating will change automatically as usage, feedback, and engagement signal is collected over time.

Quality ratings factor into [template pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing) and [template pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing), which can affect template delivery. If a template continuously receives negative feedback or low engagement, it can eventually affect the template's status. If the status changes to anything other than `APPROVED`, the template cannot be sent in template messages unless its `APPROVED` status is restored.

## Get template quality rating via API

Use the [GET /<TEMPLATE\_ID>](/docs/graph-api/reference/whats-app-business-hsm/#Reading) endpoint and request the `quality_score` field to get a template's quality score.

### Example request

```
curl 'https://graph.facebook.com/v24.0/1105258428396250?fields=quality_score' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "quality_score": {
    "score": "GREEN",
    "date": 1758754645
  },
  "id": "1387372356726668"
}
```

## Get template quality rating via WhatsApp Manager

The [Manage templates](https://business.facebook.com/latest/whatsapp_manager/message_templates) panel in WhatsApp Manager also displays template quality ratings for templates that have an approved status:

* Active - **Quality pending** (equates to an `UNKNOWN` quality score)
* Active - **High quality** (equates to a `GREEN` quality score)
* Active - **Medium quality** (equates to a `YELLOW` quality score)
* Active - **Low quality** (equates to a `RED` quality score)

## See also

* [About your WhatsApp Business message template’s quality rating](https://www.facebook.com/business/help/766346674749731)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template quality rating](#template-quality-rating)

[Get template quality rating via API](#get-template-quality-rating-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Get template quality rating via WhatsApp Manager](#get-template-quality-rating-via-whatsapp-manager)

[See also](#see-also)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TokB_tgdjRs2BjD9-8A09w&oh=00_AfiVssFFVTk7lxqvfFDBwEs3WC2ypNUvyQZOBLZry4_Tfw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TokB_tgdjRs2BjD9-8A09w&oh=00_Afjzoy99eTep2P_CfMb8-t5BKK2J1udWABAizGye_rp9Og&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TokB_tgdjRs2BjD9-8A09w&oh=00_Afid-x8_5MAZDgKP4VLEX65NEctFxKAPA5i-e2x35lSyWA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TokB_tgdjRs2BjD9-8A09w&oh=00_AfgmFon7CrZM52R1P1VEXERpMRVzh4IgwDmkgiPhPEpYYg&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TokB_tgdjRs2BjD9-8A09w&oh=00_AfgxzBepX_0MOX7o9o-lk4l6SLCb4fLJBPSIcYBQExqJ0g&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1oSoTFCf0Dxy459zUl5_lA4JbDwrkvndoF_yLUEeXvZ_HDPXXLXWz4wATTIQCU4dHpJRdqnkIj4dQctN_eeyWT1BPBHJlWv7rVA-FaeZ7DRcIZK0OyEefCEp4Ql_Y5gWL7YzetNGj64KVjK7QJuw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)