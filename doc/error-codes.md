![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Ferror-codes%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Groups API Error Codes and Troubleshooting](#groups-api-error-codes-and-troubleshooting)

[Error Codes](#error-codes)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Groups API Error Codes and Troubleshooting

## Error Codes

| Code | Description | HTTP Status Code |
| --- | --- | --- |
| `131020`  Bad Group | Cannot send messages to single member groups. | `400`  Bad Request |
| `131041`  Group unknown | The group was not found, either because it doesn't exist or you are not a member. | `400`  Bad Request |
| `131059`  Invalid cursor | The cursor has either expired or become corrupted. Start pagination from the beginning again. | `400`  Bad Request |
| `131201`  Request partially succeeded | Not all participant-level operations in the request succeeded. | `206`  Partial Content Success |
| `131202`  Duplicate participant | Duplicate participants in the participant array input. | `400`  Bad Request |
| `131204`  Participant overlimit | Group participant size exceeds limit. | `400`  Bad Request |
| `131207`  Group suspended | The group violates platform policies. | `403`  Forbidden |
| `131208`  Group Rate Limit Hit | Group operation failed because there were too many group operations from this phone number in a short period. | `429`  Too many requests |
| `131209`  Invalid Group Profile Picture Aspect Ratio | Width and height of the image must be equal. | `400`  Bad Request |
| `131210`  Image is Too Small to Process | Image width and height must be greater than 192px. | `400`  Bad Request |
| `131211`  Group create limit reached | Reached the limit for the maximum number of groups that can be created for this number. | `400`  Bad Request |
| `131212`  Participant is not a part of the group. | Participant is not a part of the group. | `400`  Bad Request |
| `131213`  Group join request does not exist. | Group join request does not exist. | `400`  Bad Request |
| `131214`  Group creation is temporarily disabled | Group creation is temporarily disabled due to excessive marketing messages sent by the WABA in customer service window over the past 7 days. | `400`  Bad Request |
| `131215`  This phone number is not eligible to access Groups APIs | Groups APIs are only available for eligible phone numbers. Please check eligibility for Groups APIs in our documentation - https://developers.facebook.com/docs/whatsapp/cloud-api/groups/getting-started | `400`  Bad Request |

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Groups API Error Codes and Troubleshooting](#groups-api-error-codes-and-troubleshooting)

[Error Codes](#error-codes)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfiHDShi4S8liHtfEyiNjLq7MQG8OWnthP99mpPd4Hyojw&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfglbY9si_zHoVsx2Duixsrph_zh6rmTrZU9hcZeRWSyzQ&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfifadK9LB_PuNd8fhGiy2u0DlVYdJyW93P8GMPPQEdG_Q&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT322yryPbgvUb9j9T_ynCD999cXcDd6ZcmFISUjrwNY2yYugY9BVTEnwy9DHCYMMG-zV16VDje0fpM1_4_RvmUHY41p0VLGhz_9XMuZFxsVU-YxNS1tKDRcieUDbIU4Kx7kqAnM3Ll0GfJALzix2A)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfhBLLHwZouJljHLd733IhBrikFDtdF8YjCbdgp3g7uqOw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0heI9YQkvERnCuIv6z32B-QWY6RQH6apFylDo8qomlz-1TsUeRTyBUwb8xo6939-7KSScZANQmWHPE6p3N2fSLFvpxe4_Tt2kSls8pHsWXMH91VFbd7WwV38vA5_aho09BtF-039WSHO-M-JplcA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_Afh8pRXyBKbFwE5YNlfXG47iCz-dWOgmDRo7nbgxYFIH6w&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0holFoZh573WVZlZWR8XeZklPPNF3kZh1qM0bMhgZh3TmwcZAHitmqBlK5E5QQ6Qxn9WTM5sj7B0N780LGsqZsv4HPOzI4KTha-3ljfXuFUEAPymIX19XJ69muh4JSKSfs8MzzXw4vigKW_h95Lw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfhUendB75zVDQ5hNNdmKQy5m25setIm3Pcteq5sFlbmFw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1dZvGOn_E1LIqxWznVp3mnYGiGNpC7dgof_JZyD-kBwrgYWwfWKrlWpDYTGnCm4cNmXUxEOI24P2KPy4wgNckDnLzQ-a9C8TXhN1N3IIbv7lQ-EdrXydcCNPOqjAsxPqAheoB6q3EYyqIHLlhVfw)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1JGZlf8dn2pHDPZ7IhxozZL_6tilMpdg4LXb3HdzxoM_tpzZLh-ERIhkPOBYd1AYwcvANEzunJ0Cx2BuhEx2Q7YTXa5qrMBMAXilwQIE3lcCUO9VV6wXur_u9dziAcs7cvVDButhM5aaPsE8sv_Q)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3DENT79JYZYgYCBE8xAd4U8BmEIX2RVKyYYu_YPPOSx6gTwEEVrzrwm1L2EpNrBv9HRc5YW6pmtj8b1YergsKmrNUF__SW2z472ZqKTY_VtOGTfzYTGOaR6At5N2-lIhaaICGcE7pk340juGzh_g)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_Afhm8BnN5TUeZHXHhSuAI0hl_eYPBDdNjVBw086MkL-1rQ&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_Afixy35RzeX1k6t0rBBOwPdeyc2i_0JofZcQrEbAmGuTog&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT07Mgf8aXPlhIdwWAkyA4DiTLnCv1x2g1xbh4BOwb4WzQd_739NUmm3kYR4fSO9TEq1xdXEGuer-pY56lGZCbgi93pnC8qDciQQSZOzJWKfOhiZ3glQer4NDGcdox-_AZVI6lGn_iQEpd9uj9cw_A)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_AfiAu0MPgfD4KU3IjDrCQBcjheIRgU3LdspYUrXFG0n5Kw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT27fYsobH23GeQwFcyONUQxvs_SewmQ38NwRqdnEa2HnIQAqq4uFRyMcHTnK3nwxrc_CoMN46c_ouch073pLZ0nqAVgJ_GGxguOLKTyoIBwHcLlp-pJ_xkMX3KCATD5k1yVbHX2C90PoKsrEFsjPg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_Afhqlvghb_mVCfj_Ye8HAToxH6fIe5tYViphBXxx73k6ZQ&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1nlLM2ygJEwmdDpC34qsTNO0e3lVYg93tEO72cqsZ9i38BzWGbJOKO7kzDb2LlQQg5__ezaoZFRQrFYhsmVguoybs4-Mlx5vtPJXwebDR8thaR-6_-URba80msn7dyK36cYb3N9c4AIwAM2Cu7yA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=xPjHmcmE3GYuTycO_krwkQ&oh=00_Afiqkq9VK67zS69Vlbqu137nkNQuimai9uGPfqX-yDjfiw&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0KSlyjDL1H7w159dqRwoIO9hLnC2QS_AF56ZcIse5wuYWGfh8thIB3zZeSmCwUR5v1Rj8pKfTJHfhT50OsS7ZacpN5s_61m1rDnZQvtnGkV3_zRfuEkVpvLo8cMyoPycJLXaDxg3XjIXtnVHBJjQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3O2WsqOZC67wuHtmQ2eBpRxoy9IulmuikSpIUtzV4DROpjhDkrv3F91it_2JIkuGbqeUR0JWRwiE-sgKZbV0Z8gyfJIuTt1yM2Mv9PYgVsggw-Be3KFBmyC2MkJTKl3mG9ZFDaP-hK6qZvwT19VA)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)