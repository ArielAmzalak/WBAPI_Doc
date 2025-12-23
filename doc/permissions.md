![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fpermissions%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)[Permissions](/docs/whatsapp/permissions)

[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)

* [Começar](/docs/whatsapp/business-management-api/get-started)
* [Access tokens](/docs/whatsapp/access-tokens)
* [Permissions](/docs/whatsapp/permissions)
* [Configuração de webhooks](/docs/whatsapp/business-management-api/guides/set-up-webhooks)
* [Guides](/docs/whatsapp/business-management-api/guides)
* [Referência](/docs/whatsapp/business-management-api/reference)
* [Error Codes](/docs/whatsapp/business-management-api/error-codes)

Nesta Página

[Permissions](#permissions)

[App Review](#app-review)

[How to get permissions](#how-to-get-permissions)

[Checking for granted permissions](#checking-for-granted-permissions)

[Request syntax](#request-syntax)

[Response syntax](#response-syntax)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Permissions

Platform endpoints are gated by permissions. References for each endpoint indicated which permissions it requires, but in general, you will need the following:

* [whatsapp\_business\_management](/docs/permissions/#whatsapp_business_management) — needed to access metadata on your WhatsApp Business Account, template management, getting business phone numbers associated with your WABA, all analytics, and to receive webhooks notifying you of changes to your Whatsapp Business Account
* [whatsapp\_business\_messaging](/docs/permissions/#whatsapp_business_messaging) — needed to send any type of message to a WhatsApp users, and to receive incoming message and message status webhooks

Depending on your business needs, you may also need these permission:

* [business\_management](/docs/permissions/#business_management) — only needed if you need to programmatically access your business portfolio (this is rarely needed, since you can access your portfolio using [Meta Business Suite](https://business.facebook.com/).
* [whatsapp\_business\_manage\_events](/docs/permissions/#whatsapp_business_manage_events) — only needed if you are sending marketing templates with [Marketing Message Lite API](/docs/whatsapp/marketing-messages-lite-api/), in conjunction with the [Conversions API](/docs/marketing-api/conversions-api), for event tracking.
* [ads\_read](/docs/permissions/#ads_read) — only needed if you are using [Marketing Message Lite API](/docs/whatsapp/marketing-messages-lite-api/) in conjunction with the [Insights API](/docs/marketing-api/insights/) to get conversion metrics

## App Review

If you are a [solution provider](/docs/whatsapp/solution-providers/) and other businesses will be using your app to access their data, your app must undergo [App Review](/docs/whatsapp/solution-providers/app-review), and you must be approved for **advanced access** for any permissions your app needs. If you aren't approved for advanced access for a given permission, your app users will be unable to grant your app that permission.

If you are a direct developer and will only be accessing your own business data, you do not need to under App Review and do not need advanced access for any permissions.

## How to get permissions

App users must grant your app individual permissions. If you are a direct developer and are using a system token, when you create a [system token](/docs/whatsapp/access-tokens#system-user-access-tokens), you must create a system user and use it to grant your app individual permissions as part of the system token creation process:

![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/465115001_533379429601225_2797461055613545929_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=0g_Dlszr_2EQ7kNvwHYMsz9&_nc_oc=AdlYMCySBQPNy5DoBZXNEQR3IAf54bEr-cvWo1tcaWd2CU6HVZlyDq7GmqSiSypstdk&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfigEP0mvNc1NjKIgVdnZG8XLaozjx0P7nOt4umn2KLjag&oe=69403E19)

If you are a [solution provider](/docs/whatsapp/solution-providers/) using [business tokens](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens), the Embedded Signup [authorization screen](/docs/whatsapp/embedded-signup/default-flow#authorization-screen) allows the user to grant your app permissions for which you have advanced access approval:

![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/464191580_1337884324044562_8279151817864174578_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=tGDGLdhHwosQ7kNvwHh-JXP&_nc_oc=AdknNJQ21vpfRBIa6qG7_Mu0mNctsQ1OzIE6abH-KDpbI2UIy8Ore14HfbxXV38knXs&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfgqGJnlmU_9Fed1KbLHyI-OLWPs8izpAhjTL3odS2X7-w&oe=69403357)

## Checking for granted permissions

Use the **debug\_token** endpoint to see which permissions the token granter has granted to your app. Alternatively, you can use the [access token debugger](/tools/debug/accesstoken/) tool, which returns the same information.

### Request syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/debug_token?input_token=<ACCESS_TOKEN_TO_CHECK>' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Response syntax

Granted permissions are assigned to the `scopes` property.

```
{
    "data": {
        "app_id": "634974688087057",
        "type": "SYSTEM_USER",
        "application": "Lucky Shrub",
        "data_access_expires_at": 0,
        "expires_at": 0,
        "is_valid": true,
        "issued_at": 1712099387,
        "scopes": [
            "whatsapp_business_management",
            "whatsapp_business_messaging"
        ],
        "granular_scopes": [
            {
                "scope": "whatsapp_business_management"
            },
            {
                "scope": "whatsapp_business_messaging"
            }
        ],
        "user_id": "104169029247128"
    }
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Permissions](#permissions)

[App Review](#app-review)

[How to get permissions](#how-to-get-permissions)

[Checking for granted permissions](#checking-for-granted-permissions)

[Request syntax](#request-syntax)

[Response syntax](#response-syntax)

---

![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwGNT9yz&_nc_oc=AdkK1fnuk4xGhFeHAn4XdiyXjPrVvBcFpPLLj-ofY9JirBmaYrzYNRWwTXvsH73XuD0&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfhrSPhUmhw-de2uj4SHP1qZh1cqNLB5MZ_tbEJiMPII4w&oe=6940632C)

* [![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHEsv4Y&_nc_oc=Adm6jtccY3OnrUzILdLpOWk_xqNHFc6pMFaMCpAlWm3GoNleDRg3k7HULDT7_sm563g&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfjedatCSAZgJt2e4APRy8dneg47gYsNmvA7jrc8HbG-Cw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwHDLY8q&_nc_oc=AdnDqpiAOYfTgn2Lm3GKnsDZVZepJY5OPe5E482PwVFgqMxcX5vVk1dgBBfrDS4OcSU&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_Afi2IDk9apNDX4NjW0w4BiVKEjT5iCuyU4E0fE7lfqZFxw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0rvErJtZ30DmSXlLlvyAI7cKaHlOCvCMh5GcC9lsk3y5Wa7pEvYR5aLTTk7FH8wMGHYmr9euhiGZFSloQMICBa-szM4TNjIzhHoksdN-ONSPpvWX2VPWEOXt-X04AFiZfgdIKAc2oSvz7ac6tQcQ)[![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwGuFGXZ&_nc_oc=Adn1Hqsrm5F4GJr-kA_yfnyjb1ybD4JVh4u85RtRZ0DBcemLq0AXi-c0MddQsjeRTmA&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_Afg40qbosCD31-9vjn-WD9WUxCG3oamSNAGSzR3hCb8umQ&oe=69403258)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT21nUgnOU_01m_HGTDbnNHGbKertC1kapaVAkcX2AvX4ctr9XhYIIG1H20bY_yar8b9FxV0xSRQxfxGpjviEUj1BEfUWlGSfaqQw1VF7UpzICVdS4tsd5s7dojPO7fQfcWTyOHbMDK6zaHoSR2tWA)[![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwGlp7mk&_nc_oc=AdlIpkGG_WzkgIyBHpm4TKLrlmBjkTl70_ffNGLGeVX6jqxTTTzLaryquGc4Gsb8xrw&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_Afj8J4-PFmkmiNLErBTVCWDjrj_kxb5xcBMlOdQFEz9aMg&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3Z7GQ-rnZdH51Rec2pQKcaIMtPPC8HRDRrqLhuQFk3qzBUvAArZBSmgyRm2sfQLRX3jNkNG6p5NRtla5893a2QiP-wdf6RHfTFRxfntdDdNpryxl_wsl2GpZOuL12ybgbdAJo0p8WlP1_EbyzeNA)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwGEs1i8&_nc_oc=AdlTkvh3TJikc1GEG5fKtaiCgyGpjPjM0Fj8RJZ26UZaET5iL8Kjznw8FiIRLhj-IkU&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfhV57Ue-gZtE5wWOukm-FGPNW_KBjC6KMYmJbdwl-iLLw&oe=694035F0)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3AyKuKrtl2gG4Tk3pSLrf05ikJ553NrJdpPD_aTYF29ftuI99uYE5O2X1VpMP20-thzxjk5t4bSmC7jyirkMLBcWjULbJJhbT_rAwZ8mBRTuNH8dnBglAKk0ICoYqEHF9xXdFw5h5jWSgnbjKPXQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1KSbCCmHv74L6SOmiCeFLTt1wlvDLHiVGeJfwskP9P52vWlnPQD1tPo1_reOyRqjmMhIL67vpSRZ_zDHjg40oseMh8_rFL3wPncdgn_lulhHe4amJpR-mQCGuK61cS6IldoVXrfvmB_cCNfIrQyQ)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3I-_id7YBHk35EnZWobJDF6CZk289oC7uxjho-u7WgoI_utatw2HQwZeaJNpwmrvVoSz50Jylf_T1l15cs9ahRYdo2igLM0t3FYbchbQ9OnfphrT5hwY3VpVkjwlGt1KaR0brPZivcvqMGRmWWWQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEq5oI7&_nc_oc=AdlAglBh-X3ENGGH5XMx6G2B7UpUoFlWYnrZkk4JnWCmUz6B3QHWFRjz47yIReQByvs&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfiZLhOYITv8nsOBD4djhe1qTvPOGR1HFBVDR4BIlKLnoQ&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwEnaVF3&_nc_oc=AdnT_LnzqDUtD4IwpxbE7omAC50cx6JjoLej8_XjPvmc1So3UmE1atNIu6WylG-b-Yk&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfivigGbm4k_WdCQzWMN8c5sOAaNAVA86gDReRgIIXyP_A&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2gTc4yZSTAqulOqrgDGhn6tZ8OaV1K2IsIDmtdom6JsqpsGyCx0WU-YJOBdBNK_7YS6ppjDnKDOeofWpcsxK4mlvoqI8WHChNhzONw9McL-sZs8K1pcCPIgQm5byZuEqiCEvF-XxAmUxIoeQPWXA)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHLB21u&_nc_oc=Adk0TzexrcdcZdx3geqNBUTeaDuXVZ_e8nwP_7hcuRp6pylTeTC-0q1umBEfE1jbdyM&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfiXUAoU8dnz96IT-k1UYaQ2ffzSMJrVLZBgLiY6l-JgXQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0fkeK_q6ucspUru76K-JQXoqc9FIAIUQrTqNyTUhR0tbmArD_j31x0VXgDk9yGKM_NUV6oZnTzrydkOrxuuSbQmuQzLVm--kgRI6mnXIq7Jb_zf0NmRX07d0i3vQ8An9stZzoykFnXoyL67tIHPFuuLdOzwti4ajw)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwGF0pej&_nc_oc=Adkuk_xo8Ox-YMnoe5pI0mI1Uix6qXJQpnn7YKwVKCB7MfC3pnpClLWnBqDhltGeNdo&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfjEwDk7HNjkFYDqpitwJ5zsUS7mwatBQIJAWB31e2iXgw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0in8fU2mAxhR53UvqB4TGU4V6qn3dd-VHUhOaPAV6dHCG-tXD5RD5u3APAAaxb-gBGO9iguRw46WKof15bHwW8KY3eqUd6_dnjmhl4Fh1LRZpkKTluB2rCtNjRu6qw-2ubBg6DEQILLS0ZXj0-0A)[![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwEeVlzc&_nc_oc=AdntLfF6sXVrIzbZfKfiVZONQFbfG5vXrTVIGb_eYk5FCz-sk3uw19SffkOAZidiQIs&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=LatLej1MLKpwvBb1mnqhBg&oh=00_AfgyjwudhxGEoG31efmZ86rNEVAse8j8bhdXyqGBe2BKLA&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0tlN5440l9LiWTD1efh3Umb0YImj7ulcdj1h-nP82IsyjEXQEM4X1Ofjt57kutkZTjDGFYJi7pT34F-cBfI4bbJ9RjTuUARJTRGIcHuhi5COx1KBwwD45EwCAX2Ue7NB984bG_iNyzcrAZ8Omp_l1rFG3z_3gQGJY)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3NaT72xIEZY_Mmwkg3nLLqEw4qOA7YYkWhYCymzx73SxkJBt3xc8VbFDX7cwMae2CcqMqonGiLpZAIDtByCfrlK7-bXfAMwHIW9ByVz4Hl6aowILT8BfvnTRsNZtu92nhHE7FwE7KiR1jnJv-0oQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)