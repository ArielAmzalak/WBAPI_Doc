![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-profiles%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Business profiles](/docs/whatsapp/business-profiles)

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

[Business profiles](#business-profiles)

[Viewing or updating your profile via WhatsApp Manager](#viewing-or-updating-your-profile-via-whatsapp-manager)

[Getting your profile via API](#getting-your-profile-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Updating your profile via API](#updating-your-profile-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

# Business profiles

Your business phone number's business profile provides additional information about your business, such as its address, website, description, etc. You can supply this information when registering your business phone number, or later, via WhatsApp Manager or API.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/507476070_1379105613180336_7510619276605653298_n.png?stp=dst-webp&_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=JCeQUJtp_HwQ7kNvwHU2Ue5&_nc_oc=AdmOsqtfEfjMU9VFEJiTmkIxxT_HINPimBuK1YnNlEQqC_Fzi4pTnDnDODE_hU2eD2c&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfjwxYGDASFt-LH3xR9BUpBgG6dg0QGpYO145wzkXcksew&oe=6940531D)

## Viewing or updating your profile via WhatsApp Manager

To view or update your business profile via WhatsApp Manager:

1. Navigate to [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/) > **Account tools** > **Phone numbers**.
2. Select your business phone number.
3. Click the **Profile** tab to view your current profile.
4. Use the form to set new profile values.

## Getting your profile via API

Use the [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/whatsapp\_business\_profile](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_business_profile/#Reading) endpoint to request specific business profile fields:

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/whatsapp_business_profile?fields=about,address,description,email,profile_picture_url,websites,vertical' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```
{
  "data": [
    {
      "about": "Succulent specialists!",
      "address": "1 Hacker Way, Menlo Park, CA 94025",
      "description": "At Lucky Shrub, we specialize in providing a...",
      "email": "lucky@luckyshrub.com",
      "profile_picture_url": "https://pps.whatsapp.net/v/t61.24...",
      "websites": [
        "https://www.luckyshrub.com/"
      ],
      "vertical": "RETAIL",
      "messaging_product": "whatsapp"
    }
  ]
}
```

## Updating your profile via API

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/whatsapp\_business\_profile](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_business_profile/#Updating) endpoint to update specific business profile fields:

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/whatsapp_business_profile' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
--data-raw '
{
  "about": "Succulent specialists!",
  "address": "1 Hacker Way, Menlo Park, CA 94025",
  "description": "At Lucky Shrub, we specialize in providing a diverse range of high-quality succulents to suit your needs. From rare and exotic varieties to timeless classics, our collection has something for everyone.",
  "email": "lucky@luckyshrub.com",
  "messaging_product": "whatsapp",
  "profile_picture_handle": "4::aW...",
  "vertical": "RETAIL",
  "websites": "[\n  \"https://www.luckyshrub.com\"\n]"
}'
```

### Example response

Upon success:

```
{
  "success": true
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Business profiles](#business-profiles)

[Viewing or updating your profile via WhatsApp Manager](#viewing-or-updating-your-profile-via-whatsapp-manager)

[Getting your profile via API](#getting-your-profile-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Updating your profile via API](#updating-your-profile-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfjXQcLJ6UnasIs5XTcyQcwqCBcDh9ac4Ygz--AVxkBayA&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_Afh74AL64kQgpocYGxZb5JqTUGsYB145W62ktIDypDw60Q&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfgVxnllkHF_fypmYbSiJUxzt_Bz1kArXJnD6-H9dJO0_g&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3g-J4T0kjUlWdUX31xuBegkaZAZblCXILXLroBGVKVnbubJ2c4PaiejJUN7IghjDxE4niybwlEuAXqML7lZ379GgHOQcVJDWuGNImBVKYmBEG0jwMnsOdhXAUczhnMoX-URb4Vn7JAvU0FH51xMA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfhrfBfjSRsTpbBKW8WbfIcSy6WfyRcYusc3d8xah5zw0Q&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2UXMrwuB-y1bM5GqmqyPVNEjzPI8Kql6tpJOIHM3cyIVEWV57Yz94Zse2LbayxC17IcQwBQmhxkGbkFnVbDXRS3CtVWSw5ng3VWKot7lVwpSSgS4jQYBxYFYNCQo7WiQI5jREap0m--fKLsPakTQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfgUkWfTM8lomTUbW1jQjoHoyCfWFjLvmMfTIjZvrIKw-w&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3ghV2iCy5pjkMfeiOSElThpyZMoP79ygn8GH0vdZbixBe5B6OOA4wPLH1YuE9o2eNBvUuzbkgLXjXOTT7hUeNtU6_mZ5wFatARTTbqpDwoiDUiEYHxnICftmXxak7v2-Ze8RWMfZDxcpUDRs5jwA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfhltXYQ700nkjMIc3mS_FoZvwkDMf2-Yo18dhb5ftvMkQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2rIYk1SDqE5h7zL281FUMJUNG_DddtExluLM6FzjxKjP-yhlP3oGUXEqN_1coVC9P6BmRuUZSsZ_xNTYoGAN3pEhSchLPTLUbi2OjjjP2QCi3dZ_5biTetR35IM8-yW4kvYPbRxHdTnMpObu9yKg)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT29VaKgAiT6ys6Uv7pAISu6y7BVEPgp876pPwtZFOqJKyE3Bzyz756jPASf2bgCE3bBggwW0z9MQrk15cGs9prOmj9Qv2lMxSgNgAJj3KiDeFQn3_dvA70PyeEBeC6iGrQAskQFWqXv5jNTNyzu2Q)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3vnkICI1Mb3rE3-tlMZFWURWMd1IBrl28POAtHbPgJczbi6OZrIJDcT5FEdx42j7TonM8mNAjee3bmPYdHL8-3XwXr-HJLPKjUX5oEwnWZM0VWTP9AAC03y_ML4yfWj9c2g3REIZzRRq3pA4XjLw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfihW0MiMupfZif_FVNBcKeH9URu-jppU8hZXhUUcAthEQ&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfjoXnfMDxC_ZTvisR1umAUjOj55aCQU7OX4IAUY5o1uCg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT263tPG7rgvELs71GFfGOgfcVPI3rV2omukfX4Nt1U2_x6x066OsYJip0x3QhZfpeThQxL8z-4zy4I7Li3ohkgnZx2Ojx9CeO69CmnAE9dNz5NEobbpuPu2yr8cn8bDAZAbl5XTePKgJTY-2I7eug)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfjUt6Rzt1Qmtp5Ut4_eInie0hzHun7I-IeuU2DxTiv4vA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0doKRyZe76QG0r2gA4_32u7EBCg9Pv1eYuOkyTrOTERzxxfY1cA1bWcq_FCOu6YDDCUnce8tlUYIN-YD3goVOIYpPaVcq9VV-hNnLNzFFJPGUtbZOP0PsgF5jbYPOCihjHtK0JT4-MMtp56vyyTw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfjUxy_QyzR1OvYGsBNzDzawIkhPre1NlZQYNpyyhqlY_w&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3WxTqWvqthiJCwUMAtdmOClHdQTejI4NivuHevZqfQCU9L7RFHdKxECJBSSr7QIjzt0VhTLkQL7cYY2fMzeHpdeMtIHt859jPKexSSa8oMp-nKsxQMkltYieCgUfG0Sn_3QGpidXkCNPuvMVQigg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=hwaJ2w1Jk_rcMk0Uxx5eWw&oh=00_AfgN9tB2bC81I1QG7vU4S8TR23gUIeBoMRmijXWKLwJnSQ&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0nSBYk2kMKbxSg5xdlBrv5cio_KhcWa6wTv0NN-K3ZPFScWqm6gyUZ9tZFYf5XVXG4_GUtkcbq3dyvOCQiD7Zppqzp-r1QTvTbG04LDeu_xqa3BR4ioiif0FkaiIbP_D0IuPQHmu9ccIJDjW38jQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3-50DzloKZXN8LT7e25tITrZBos7iB6a6bWnlwyyvpb0MThCpXJz-UAB5tT9nEaer09D2gz4Gav5Pq8CDIJ7hnbzVv15Saa7DKyCRIB3yca-tAouX822vcN3lN_9S2Cm-568jwz08Qiye-m25QUQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)