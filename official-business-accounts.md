![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fofficial-business-accounts%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Official Business Accounts](/docs/whatsapp/official-business-accounts)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)

  + [Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)
  + [Official Business Accounts](/docs/whatsapp/official-business-accounts)
  + [Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)
  + [Business profiles](/docs/whatsapp/business-profiles)
  + [Display names](/docs/whatsapp/display-names)
  + [Receber aceitação](/docs/whatsapp/overview/getting-opt-in)
  + [Identity Change](/docs/whatsapp/overview/identity-change)
  + [Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)
* [Preços](/docs/whatsapp/pricing)
* [Limites de mensagens](/docs/whatsapp/messaging-limits)
* [Webhooks](/docs/whatsapp/webhooks)
* [Parceiros de soluções](/docs/whatsapp/solution-providers)
* [Cadastro Incorporado](/docs/whatsapp/embedded-signup)
* [Prévias de links](/docs/whatsapp/link-previews)
* [Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[Official Business Accounts](#official-business-accounts)

[Eligibility](#eligibility)

[Notability](#notability)

[Denied Requests](#denied-requests)

[Requesting OBA status via WhatsApp Manager](#requesting-oba-status-via-whatsapp-manager)

[Requesting OBA status via API](#requesting-oba-status-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Getting OBA status via API](#getting-oba-status-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

# Official Business Accounts

An Official Business Account ("OBA") is a business phone number owned by a business that has been verified as an authentic and notable brand according to specific [criteria](#criteria). Official Business Account business phone numbers have a blue checkmark beside their name in the contacts view.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456954377_453386597161620_5745766558871976538_n.png?stp=dst-webp&_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=RVUKnZvUKHwQ7kNvwGm9rK2&_nc_oc=AdkZqodK9sCoxtEofKO_BcKGgFCQJ0s3Vf-xX9eaRH97dway-nW__lH2ybiUUNAhQM0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfifQSDOl__MxBLO0DvGc3BXHQtrlu4kuajyvsDGrMllCg&oe=69404273)

You can request OBA status for a business phone number using WhatsApp Manager or API. Once we've reviewed your request, you will receive a notification letting you know if your business phone has been granted OBA Number status or not. If your request is rejected, you can submit a new request after 30 days.

We do not grant OBA status to business employees, test accounts, and WhatsApp Business app phone numbers.

## Eligibility

To be eligible for OBA, the following criteria must be met:

* The business must comply with the [WhatsApp Business Messaging Policy](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2Fpolicy&h=AT2olSyvZgFoyQNw3kS2OPQWBgbtNWW9UGqI1BMy7HBNm6d4wfe9eFQ16uLS08vNTqBYfSsa7WTx3WYnOn506PtGP3XwSig7bOjTrrZBWvTKNT14MF12JtfvZLp36npZ9-x1CxOV_TZthSzbjLA77g).
* The business must be registered on the WhatsApp Business Platform for at least 30 days.
* The business represents a [notable](#notability), well-known, and frequently searched for business, brand, or entity.
* The business portfolio that owns the number has been verified through [Business Verification](https://www.facebook.com/business/help/2058515294227817).
* The business phone number has enabled [two-step verification](/docs/whatsapp/cloud-api/phone-numbers#two-step-verification).
* The business phone number's display name has been [approved](/docs/whatsapp/cloud-api/phone-numbers#display-name-verification).

If you meet the above criteria but do not see an option to apply for OBA in [WhatsApp Manager](https://business.facebook.com/wa/manage/), please reach out to your Meta point-of-contact, Solution Provider support, or Meta Support to check if you are eligible for the application process.

**Note:** If a business phone number is not an Official Business Account (OBA), it will not appear in search results when users search for it within the WhatsApp application. However, if a user adds the number to their contacts, the display name will appear in their search results. For improved discoverability, we recommend applying for OBA status.

## Notability

Notability requires a business to represent a well-known, often searched brand or entity. This should not be taken as a signal of the authenticity of the business.

Notability, on the other hand, reflects substantial presence in online news articles. Notability is assessed based on an account’s presence in news articles from publications with sizable audiences. We do not consider paid or promotional content as sources for review, including business or app listings.

OBA Number status is issued at the business phone number and display name level. We assess notability for the display name of the business phone number that is requesting OBA status. If the display name is changed after receiving OBA Number status, we will need to re-assess the new display name for notability and [display name compliance](https://www.facebook.com/business/help/338047025165344).

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/457272592_1239953843829647_8265325653823058853_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=pfWKuTIg4lcQ7kNvwFSNehw&_nc_oc=AdnNansGNof-_qR1v8_N9imOjj0-ILOJH6nrHjPqpa4ofZg4oWW4VCD5__QAKcMbDz4&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_Afg6Aj1whGhKzGQstR6SQEili62Gnr3C8P4_B06Vt7xdDQ&oe=69405B91)

Additionally, previous OBA status approvals for other business phone numbers owned by a given Whatsapp Business Account do not guarantee approval for all business phone numbers owned by the WABA. If the WABA contains one main parent brand and the phone number associated with that brand meets notability requirements, we suggest updating the display names for the child brands as follows: {{sub-brand name}} by {{notable name}}

## Denied Requests

If your request has been denied, it means our team has carefully reviewed your account and determined that it is not eligible for OBA Number status at that time. Currently, these decisions cannot be appealed. You can continue to grow their business presence and wait 30 days before submitting another request.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/457031264_766028162210302_4155505657500024802_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=tZbJIpWb4iQQ7kNvwHtnEpx&_nc_oc=Adk3STy8ieMmzApalzvSF5GlUYGdaPdmnbmHwlL2fsJF40A8B5yoIG2t2KuHp0a7MEY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfidoyYWcPvjsEGCTMZzOBZHiNVYKNSvYluivc76WEzTfw&oe=69404082)

In the meantime, this decision does not limit your ability to share your business details. Each business phone number also has a business profile which includes the profile picture, email, website, and business description. These are fields that you can edit at any time.

## Requesting OBA status via WhatsApp Manager

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=426986416058896&version=1759625960&transcode_extension=webp)

* Access [**WhatsApp Manager**](https://business.facebook.com/latest/whatsapp_manager/) > **Overview**, and click the business phone number:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456997811_1368661294090266_2491166291934528895_n.png?stp=dst-webp&_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=pCrCp1xkttMQ7kNvwEGlSsa&_nc_oc=AdnfqOcfEiSmM4AUPYF9Wph807dpnusY8M6uN9Z0zesunxoW0Hf-er-zM-HpDfQUtgQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_Afi-E-DLX-nS_ufNbk92hNcNszUTAyGV2iA4L-ThTtHo4w&oe=69406504)

* Enable two-step verification if it isn't enabled already.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456954365_532463442507497_4571397701593651380_n.png?stp=dst-webp&_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=2ICj7NrtKX0Q7kNvwFviTQS&_nc_oc=Adk3W54HT0EdMfFERH1l19-VVxTBQRu2OQf4X8bl68MdiHCcihV7zUpX0cvwKvk7QOI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfiJsbJW9CRfQCR8vVBVK_HnYiSOTWfaJqLbLTIrb8UpJw&oe=69403F22)

* Click on the **Submit Request** button and fill out the form.
  + You can submit up to 5 supporting links especially from renowned publications (e.g., India Today, Economic times, Wall Street Journal, Reuters, Wikipedia, Business Insider) to show that the business is notable, which helps us determine notability.
  + Fields like Country(s) of operation, parent business or brand (esp. if it is a well known brand) and Primary language helps us to further understand your brand and eligibility for OBA.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/457106823_1745186199576875_630331601567021999_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=79l1H7_9wJQQ7kNvwFN6r5Q&_nc_oc=AdlJ8IZVYzAGaYRPMwYX1BPgzFsMZ9QOLk4E1M8xB4_VbPsoXMnSGkuyqZHCDob4pDI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfhmP7Ya9gjo1Xp4ncHHHXxWewAJofTUIPGQ8ssPq7U5rQ&oe=6940568E)

## Requesting OBA status via API

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/official\_business\_account](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/official_business_account#Creating) endpoint to submit a request for OBA status for your business phone number.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/official_business_account' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "additional_supporting_information": "We are also featured in Planet Succulent and Prickly Digest",
  "business_website_url": "https://www.luckyshrub.com",
  "parent_business_or_brand": "Lucky Shrub LLC",
  "primary_country_of_operation": "United States of America",
  "primary_language": "English",
  "supporting_links": [
    "https://www.retailreview.com/gardening/2025/lucky-shrub",
    "https://www.faster-company.com/2025/online-nursies-are-making-green-waves",
    "https://www.succulentscene.com/2025/new-online-retailers",
    "https://www.pricklypages.com/2025/succullents/where-to-buy",
    "https://www.spinyliving.com/2025/latest-news"
  ]
}'
```

### Example response

Upon success:

```
{
  "success": true
}
```

Note that `true` does not indicate approval, only successful submission.

## Getting OBA status via API

Use the [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/official_business_account#Reading) endpoint to request the `official_business_account` field on your business phone number to get the status of an OBA request.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922?fields=official_business_account' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```

{
  "official_business_account": {
    "oba_status": "NOT_STARTED"
  },
  "id": "106540352242922"
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Official Business Accounts](#official-business-accounts)

[Eligibility](#eligibility)

[Notability](#notability)

[Denied Requests](#denied-requests)

[Requesting OBA status via WhatsApp Manager](#requesting-oba-status-via-whatsapp-manager)

[Requesting OBA status via API](#requesting-oba-status-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Getting OBA status via API](#getting-oba-status-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfgCnQJZZC9hDv9h_JfsBc510OWFu6Y3vOKYPXg1i01CLA&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfioXFGbvFdOOCJnqMJyipKMwTXOaezCPamBcreGDqIoIw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_Afj0v0ezswi8RtI1XpreXRpgWgRDQcauF5xBxQF_z22ltQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT11F6H4x8o8B5ASAgllvsIR5p5PuC1AxAF0qf05WXOeJLmpH-O2gJMfrtrq-AbKawnv4nso-NAomQIhgOWgfhZ6o4TR3AdrLU9KPxP-G7FAmQQk4vh1r4IKdZqHt8OTie8AbKqG00nDRsMIKrPuRQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfjjFQZm22RaV_biO1gRCLR4JblTnzME_-oLzuUipVnX6A&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2-BEGTscRN015Xk0j2S7mvc0m_638p5LwB0hB_3PUN-28A1smWRIRipdn7YZUrpaQI7ODNrJV8E7b085JbHeur8gIO9JiCMmMgfphvqWtT-CNU0Z88yBWaoHhFUVZIDNmhly_zhvSJry5viFMx_g)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfhLK8bf7ZiOlZgoaeGev312NKK_-YJb11ZdzdlMnHX50g&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3lhBf08NBDdRYgConOGrEqO54OzIztZ7AElKbhk5YC-bBqTgdHQOPNJ3TsSEv-Dsed_SAH0uT5nyZ4mo5R1SLHtKhuumNBX-k7ZRgtGoCcZYjKJMQuxVYHU4LIHwjoc_nEiBW8ploBTwKNHPbETw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfgIwZutNr6zkHSwbMrM83g0dqaLYJwc6oJmXTBW109MGg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0gJaDgJuVsPO6_mkqHPJOQ1LZOHwgP2q-c0r-7i1EyoZvVYWrlfqTdu0RfNct1kXtMc958wn3lChHDtPu55bLaf40gB1T7K8AYrHOtdp51I1RlogJ3s-DgULEX7gxolQi_3SUSf37GcAs--lebAA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1a3PWk2n86m-SNA9C-NWL9pf7gBx0vjTdA484FHtUwJzb5_jyYDktbFXTAhRJ0syCfUS4fVPyTo5ElFJJPXeqVnrIWVwEsKYjCQOGMiMV3YAgCwRxAqsJN24hmY_2WgGNR9TIq0ePhNfeGOjn92LYrTFUJfHjDbVY)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3NWKlgyihTOeCSj13DGirhl1Jl94h5cSJEeC7gqWQtiq-drZOZg1oO5Pccep8jHUDeVCY3VQHrcR7nS81jAS0YG5bMjrdwX6A8eiFyolzp6zBsC-5YyEBKzJTLHquSphZXwwcFN6WrjnUI-50klw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfhIu9xYeXr9sKJ74ZcrSnXAMa9LRnkWCftnwYk7cpc9qA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfgtCs4xlWJkbgB7VWlWD4bvr-b2SpQ2oIlgDjf4w_vBPA&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT35ALHe_bbN1tqMrbUHajmPgYNFmDFO2Jx3mYNCWUuiDNIoxyQdLsIUm51W4JOABANw6xNmq9pbMnfjlsm8GiACuLOtchNEeUoBZt9p00T9yz4sVeh6aN1FOrStYpCUgxIzEb_jLRsYMVroeQ00Ig)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfhRrNo_F1F-a4_KUyssDpFZoVZ5gm__6EzHBTmjxeI7RA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3pt9iF1yWcHXK0qBzBXCAfqaHlj3QhF71O5GkmfqvFQ8Hup8s2bXZgYsxY1-4YcyGzfTUwVE7Z9ncvzVujQAUEEsKJzwkeJqaT-E0xYF_qCKa2m7IL-HtZG_G8Gy6Z-jus6_Zz99IA06LhGlRSOg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfjQEpwnflrrt7feau5d-SOHzo0R178iXHdp6LPODdHfVA&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0s4UV_4OfwvMLDqR4Aen7IxkLDV3656vR6o0i88fRhTNepGtlDwT_k2LcRh2uCdpuMC7abSDqtAl0DUd-x1X_SvhoY74b9F4SyY4TpYoN6VJcelxvg2FYLSBQIVQL6xyogaJLHWHFmP4s4QJLJDQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=tJrs49Kp_75VpbOOfn6OxA&oh=00_AfhDDYxclxvfEgWnCZZPLuFGjHXMOsOmPizaBlR7NDDx0Q&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT339BzWg4UvI_pDSO6fJVXuKZdvthrcT1NlPrnbMJ4xVwDTfKcwVWKCmu5ryX4iymaTUAlTN3m5oeBD4kHHfPQJwW3CERUYDFf4E_hCAEayZ7ae1azURkmf2HyACg4h1fY5dDqsf7af77mrdEv4ew)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0KWUN3MjICSwpt0rzLizQmvpvYV92rDSEDmfnRhek9LhY9vTjHHsowr3-VVvREf-pOhf9zGpiK_X2LU2Ivr-8t9NRXL6oW0jvoWvlx_FjElT0F6UECpepFKqVmzYgvsYC3K0hAluWU6-HQwj2r9Q)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)