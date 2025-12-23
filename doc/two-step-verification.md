![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Freference%2Ftwo-step-verification%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Referência da API](/docs/whatsapp/cloud-api/reference)[Two-Step Verification](/docs/whatsapp/cloud-api/reference/two-step-verification)

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

[Two-Step Verification](#two-step-verification)

[Resetting your PIN](#resetting-your-pin)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Two-Step Verification

You are required to set up two-step verification for your phone number, as this provides an extra layer of security to the business accounts. To set it up, make a `POST` call to `/PHONE_NUMBER_ID` and attach the parameters below. There is no endpoint to disable two-step verification.

| Endpoint | Authentication |
| --- | --- |
| `/PHONE_NUMBER_ID`  (consulte [Get Phone Number ID](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers)) | Solution Partners must authenticate themselves with an access token with the `whatsapp_business_management` and `whatsapp_business_messaging` permissions. |

### Parameters

| Name | Description |
| --- | --- |
| `pin` | **Required.**  A 6-digit PIN you wish to use for two-step verification. |

### Example

Sample request:

```
curl -X  POST \
 'https://graph.facebook.com/v24.0/FROM_PHONE_NUMBER_ID' \
 -H 'Authorization: Bearer ACCESS_TOKEN' \
 -H 'Content-Type: application/json' \
 -d '{"pin" : "6_DIGIT_PIN"}'
```

Sample response:

```
{
  "success": true
}
```

All API calls require authentication with access tokens.

Developers can authenticate their API calls with the access token generated in the **App Dashboard** > **WhatsApp** > **API Setup**.

Solution Partners must authenticate themselves with an access token with the `whatsapp_business_messaging` and `whatsapp_business_management` permissions. See [System User Access Tokens](/docs/whatsapp/business-management-api/get-started#system-user-access-tokens) for information.

## Resetting your PIN

If you forget or misplace your PIN, you can update it by following these steps in WhatsApp Manager:

1. Go to [settings](https://business.facebook.com/settings/), log into your Facebook Business, and click the business you are using to manage your WABA (WhatsApp Business Account).
2. In the settings screen, click **WhatsApp Accounts** and find the WABA you want to update the PIN for. Click on the WABA and a panel with its respective info will come up on the right-side of the page.
3. In the WABA info panel, click **Settings**.
4. In the new tab, click **WhatsApp Manager**.
5. In WhatsApp Manager, find your phone number and click **Settings**.
6. Click **Two-step verification**.
7. In the Two-step verification tab, click **Change PIN**.
8. You will be prompted to enter a new PIN and confirm it. You have now successfully updated your PIN.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Two-Step Verification](#two-step-verification)

[Resetting your PIN](#resetting-your-pin)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_Afjp8-RfeaigEawHbXWTGslNioG78L9VIXIkuKhoIGw8jA&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfjgZH7f-A3Zd2MDUR7j49cQEYlDmCQd-nLFma0mBqu1iw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_Afg_RMlWtr2vro8DNXDj-Jj4uY5UYn_odg4SbjuUBxzRLQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT04fmRokqI8oxy3UYcFe8AanZ1R-edp1e5zcWBZyLOl1qbFaMmWdQXuH5Y-c_ZnIcKlcvfhUk4wHQqMF0UUl2f5QhZyiC05oLlzHBekjV6sZ9OgR6Kt4VWqfak0DLPqM1RVdTzCEX23TMGgHHiQ4Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfjzEPWhTW88iFiwCCM5sLGCYgA6QDADzshdp0g8jU_Ekg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2crsPsJqr9Dbv3KUw3bkVs__y-ZshS4rqw_OhaKnMkhgVVmvm2yIktYmScruWg_uuq1CvBZgUMA5ENpNkQmqf9lQzAKF2fvEK0gkjmcLDx6z4NV7CefN7_q6qi44I6M7UiZ19npHD-rc4_R16D8g)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfgYABqd9WbTVz7GTJzCdjTMKsb7dmYeEFW1XwH2-OH6XQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3sFDnYlduOvlWc5Omux5vgqMm0Y5zG7TjelCZeI5Eyxy_u4cJvkLrkaqP7k4nJ6F_msbwLTcX4c1deC9GM_FZg_PD2i2Y3Hv4GMdNDOpGKsWhmLx-ybtREymvnEQq1KIlUpIQ3DPc5juo7Zxjbsw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfgcNKqvWSvKTXncu-dRaGbuIGOuwJ5_FZ6knwcwyHjbTQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0tJFhE_4eGKHLCmqMliQDY8F1ZVji7iuC3R7fSLQxsd3dLbQEGNu2356YhBqDIipJz2TeLSfn_ftyu6xBQlbbYFSHVY7mPRDy3VvZysKs2fvUHBSQPN4JaWVbBhd6FLdpdO7m1vmsj54phkVvzew)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT29CFztR-4YdYgivCUmkdT_w5aMfoffV1mAqeOh5W2ZXyx8_kWDOlF8E8wVWLCXjaD1p6G2rgMOfKvTdEN4Zf516G20DAnGKvVT2BuXMsyL-bHFrZYpyscJ0pOuryKmvZiBMYQvzJPa2qcFIzzOfg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2QypYBMaVbXOOL2N5PWei7JzJliqpZvXkJohs17XfS-hxYjcN1uUkDsDdww0ONCZTv8v1-pcx_NyApw64R24ZfPEigzpGxe2z1GoSEhUy6FCrjy_hqf9nuSa6GbIJ8Jwc7L2DvCtglRWD_-EhKNg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfjHGalJ44wGfaxDobwcWdi2spxKPPoDkY57z8sFJuoAgQ&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_Afg-JuIYM5-Afep9-5ndJnhrfW2rQEK2O-Kh78B6YTHhUw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3PgyiNnN8xUYGPxwmKLySpdY9eNSeQ04kUpbGKIZvBbroBlmnp3viKcnvo_cSsrLlaDWils-yVsdTnjrOWV54r-0uUq0hLT74XPSTzbxxqpXXS_du-0slP8EwCZzn0mOMQ_wa59HUn0Pob3XYE1A)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_Afg4BL_aDRYxzHhbEAk18D234lgUcgx1DTtJoNxbTIwtyg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1plhLrgcjKlBBrP6z47fsv0gM5Ngp93PbJAu2E5GjGkXyLV0V4TxDvnBaR6h9UTdU3FBiQHwu2wY9gEmY1-qNxEOKrp35m1NXMN3MAda6gSc-wpqENRaS0pnmO9Ff_N92_rMHlGvPf_gIt6M1oBQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfiUcEmaF3l8Ma0cqOEAeHIPRk4A1JM8feYGD2AMOYLjfQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT256xgmuNgJfTe008NNDlEnznpNJrH_eWnZKPbQGQRI_XnzODzdI7hlMSJLFjBeJOkcAXrePLYpHa4TpBgFTfgBaHut-PB_ynhLE_Q1iyspxG97wy-8itGy0njSvpbmZY6_hSFfyXg3-BPS52n0hg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=A8qr2yT10WUsrviLfM4mtA&oh=00_AfhNraa0tUH_beU9MYm4BcmxLNhadD7iVOIjoLAMFsuCVQ&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3puwFF12jU7rkgUuH-7jNmwL-bot_ru33Et9COLbwN-lFG-eFA0iPUiiW4ObI92pTNrCtP04-aQamwWmXwjvGMbkM_l1RIv0cEfXUK8TEZF_kk6ML1_lepbGHxLDKTW95O2tcpn7RlLtQlJEkL6Q)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3s6Rnf-5_lBqqZXRcE0-F3lEgBmF0x2izQaLOdpSYzgchV8M3UHfg1crNx-ChMn7jFNz-oHGdNuSeL80R9xoMi5GjHpt8e8oA0r-lN1cwt8NGB7oxuQrdI9inD43JhmH3bbKGFFTq8XCk1Yzs3RQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)