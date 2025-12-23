![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Faccess-tokens%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)[Access tokens](/docs/whatsapp/access-tokens)

[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)

* [Começar](/docs/whatsapp/business-management-api/get-started)
* [Access tokens](/docs/whatsapp/access-tokens)
* [Permissions](/docs/whatsapp/permissions)
* [Configuração de webhooks](/docs/whatsapp/business-management-api/guides/set-up-webhooks)
* [Guides](/docs/whatsapp/business-management-api/guides)
* [Referência](/docs/whatsapp/business-management-api/reference)
* [Error Codes](/docs/whatsapp/business-management-api/error-codes)

Nesta Página

[Access tokens](#access-tokens)

[System user access tokens](#system-user-access-tokens)

[Admin system users](#admin-system-users)

[Employee system users](#employee-system-users)

[Generating System User Access Tokens](#generating-system-user-access-tokens)

[Business Integration system user access tokens](#business-integration-system-user-access-tokens)

[User access tokens](#user-access-tokens)

[Using tokens in requests](#using-tokens-in-requests)

[Business asset access](#business-asset-access)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Access tokens

The platform supports the following access token types. The type you use depends on who will be using your application, and whether or not you are a [solution provider](/docs/whatsapp/solution-providers).

* If you are a **direct developer**, meaning only you or your business will be accessing your own data, use a [System User access token](#system-user-access-tokens).
* If you are a **Tech Provider**, use a [Business Integration System User access token](#business-integration-system-user-access-tokens).
* If you are a **Solution Partner**, use [System User access tokens](#system-user-access-tokens) to share your line of credit with newly onboarded customers, and [Business Integration System User access tokens](#business-integration-system-user-access-tokens) for everything else.

## System user access tokens

System user access tokens ("system tokens") represent you, your business or organization, or people within your business or organization. The main advantage of these tokens is that they are long-lived and can represent automated services within your business that don't require any user input.

System tokens rely on system users. Most endpoints check if the user identified by the token has access to the queried resource. If the user does not have access to the resource, the request will be rejected with error code `200`.

System users can be [admins](#admin-system-users) or [employees](#employee-system-users).

### Admin system users

By default, admin system users have full access to all WABAs and their assets owned by or shared with you or your business portfolio.

Admin system users are useful if your app needs access to all of the business portfolio's assets, without having to manually grant business asset access to each asset whenever it is created, or shared with your business portfolio.

Note that you can override an admin system user's default business asset access by granting partial access on a per-WABA basis. See [Business Asset Access](#business-asset-access) to learn how to set and override access.

### Employee system users

Employee system users must be granted access to individual WABAs that are owned by, or shared with, your business portfolio. If your app will only need access to a few WABAs that you own, an employee system user should be sufficient.

Once created, you must grant **Partial** or **Full** [business asset access](#business-asset-access) to each WABA that the system user needs to access.

### Generating System User Access Tokens

To generate a system token, access the [**Business settings**](https://business.facebook.com/settings/) panel and then click **System Users**:

![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/465045103_469826065488878_468932947489962332_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=78b7_n4YIjoQ7kNvwFq7Cqe&_nc_oc=AdmEeCo8QooE-Mi0x2aMWXg5nt8QxWe2n0AENjDN4vgO8WSVH6_hwo6yvGKdSUKmzW4&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_AfgCxzAEqiTs8ip5E7lkNaL3z8czggas8qYWRC_uTVETDw&oe=694049FE)

Click the **+Add** button, and in the **Create system user** window that appears, enter a system user name and assign it an **Admin** or **Employee** role:

![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/465150702_510049308508353_7881035250572985544_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=aeuIjE2DMJQQ7kNvwHn26M9&_nc_oc=AdmfPRbG7Q4jAkGpz9Q8lhRF5sTWituFwzliGPnsH-o3SAVad-MufDqFrWXDG2WA_wY&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_Afjpze7Yt20oFgtrybYbR0kOx-QK9MUy_L0KEdJ4S6aiuA&oe=6940508E)

Once the admin system user has been created, it will appear in the list of system users. Click the system user's name to display the asset assignment overlay:

![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/465056956_862633796067178_7287331611550335065_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=aPAdnIKfGY0Q7kNvwE0Gfoa&_nc_oc=AdnCGjTevH9hWDpHC3ayK69mZZrNowwuoNN84pCGSEWmAoDF1hp5BGtD68q2N7_xJGw&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_AfhhFJGkGOcRM-3T_bii7dVaSnbzhVTaDxwhheVcIDtnIg&oe=69405916)

Click the **Assign assets** button to display the **Select assets and assign permissions** window:

![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/465238023_523683013888319_4402098107854849013_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=5tU_1wXje1QQ7kNvwESi29Q&_nc_oc=Adlusg_sCoO4S4JUyJJ9e57yR3VK1x9Et6qs_qrZmmGqGlyz7fF8JLD2Oib4ZX709Dc&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_Afgy7kvoVO5MPCoM2bvDOKdtCgzGJcpSLzXCP_XqpzFCig&oe=694031FF)

Select your app and grant your system user the **Manage app** permission, then click the **Assign assets** button to confirm and dismiss the window.

Back in the **System Users** panel, reload the page to confirm that your system user has been granted **Full control** of your app. It may take a few minutes for the permissions to be granted, so reload the page after a few minutes if your app doesn't appear as an assigned asset. Once the asset has been assigned, it should look like this:

![](https://scontent.fcgh5-1.fna.fbcdn.net/v/t39.2365-6/465048557_1084025226566535_5772232306997286547_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=zYktSmgbrJMQ7kNvwFzI2Jb&_nc_oc=Adks4x2TjsO3QwVkLwyMDhmVH_SmUuOaoT0QM0ur0qXTHDoHMVg2EsAOh4_wb41PbF8&_nc_zt=14&_nc_ht=scontent.fcgh5-1.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_AfgfbF4xYBEOkyjp9f_loPusk93-XWLC1Ydd0keGXbKkrg&oe=69405F98)

Once you see that your system user has been granted full control of your app, in the asset assignment overlay, click the **Generate token** button. In the window that appears, select your app, choose a token expiration preference, and assign your app these three Graph API permissions:

* `business_management`
* `whatsapp_business_management`
* `whatsapp_business_messaging`

You can search for "business" to find these permissions quickly:

![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/465115001_533379429601225_2797461055613545929_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=0g_Dlszr_2EQ7kNvwHYMsz9&_nc_oc=AdlYMCySBQPNy5DoBZXNEQR3IAf54bEr-cvWo1tcaWd2CU6HVZlyDq7GmqSiSypstdk&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_AfiuZBdwsbM676st7z8RA3sNDVspXY3XQyaP_S4Wkcfm3w&oe=69403E19)

Click the **Generate token** button and copy the token when it appears.

## Business Integration system user access tokens

Business Integration system user access tokens ("business tokens") are scoped to individual onboarded customers and should be used by Tech Providers and Solution Partners when accessing onboarded customer data.

These tokens are useful for apps that perform programmatic, automated actions on customer WABAs, without having to rely on input from an app user, or requiring future re-authentication.

To generate a Business Integration System User access tokens, you must implement Embedded Signup (configured with Facebook Login for Businesses) and exchange the code returned to you when a customer completes the flow.

See the [Embedded Signup](/docs/whatsapp/embedded-signup) document and the [Business Integration System User access tokens](/docs/facebook-login/facebook-login-for-business#business-integration-system-user-access-tokens) document to learn more about these tokens and how they are generated.

## User access tokens

Although User access tokens are supported and can be used by all app developers, you likely will only use them when you first use the App Dashboard to [send your first test message](/docs/whatsapp/cloud-api/get-started). As you develop your app, however, you most likely will switch to a System User access token (and eventually a Business System User access token, if you are Tech Provider or Solution Provider). This is because user access tokens expire quickly, so you will have to keep generating a new one every few hours.

There are several ways to generate a User access token:

* Access the **App Dashboard** > **WhatsApp** > **API setup** panel. This panel always generates a new User access token whenever you visit it. The token is automatically scoped to your user, since you are signed into your developer account when you access the panel.
* Use [Graph API Explorer](/tools/explorer).
* Implement [Facebook Login](/docs/facebook-login).

## Using tokens in requests

When making API requests, include your token in an authorization request header, preceded by `Bearer`. For example:

```
curl 'https://graph.facebook.com/v18.0/102290129340398/message_templates' \
-H 'Authorization: Bearer EAAJB...' \
```

## Business asset access

After creating a system user, you must set business asset access levels. Many endpoints require the system user whose token is included in API requests to have either **Partial** or **Full** business asset access to the WABA being queried (or its assets). If the system user does not have this access, these endpoints will return error code `200`.

Note that if you set a system user's business asset access on a WABA to **Partial** access, you can further restrict access to certain assets or actions on the WABA. For example, if you have a large business and want a certain department to only have read access to a WABA's template and business phone number data, you could create a system user for that department and set granular access to view only for that data.

To set business asset access on a WABA:

1. Sign into [Meta Business Suite](https://business.facebook.com/).
2. Locate your business portfolio in the top-left dropdown menu and click its **Settings** (gear) icon.
3. Navigate to **Accounts** > **WhatsApp Accounts**.
4. Select the appropriate WABA.
5. Select the **WhatsApp Account Access** tab.
6. Click the **+Add people** button.
7. Select the appropriate system user and assign appropriate access levels on the WABA.

![](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/458274092_845026414442989_6944264004016403962_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=a0leIpDY3jUQ7kNvwH7uw8A&_nc_oc=AdmKiczVPIJBmFjJSB4o_a78-QccbQ5ByQs8L-UF1n9ueTOWgL59YjbX1eovBnQnDvQ&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=r7v4H85tmnfqnszeRaWLcw&oh=00_Afhq0qYZoT-I3Ii4nugoqZUhTGVEvAZXLIG5xYwRS8RxsA&oe=69405C6E)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Access tokens](#access-tokens)

[System user access tokens](#system-user-access-tokens)

[Admin system users](#admin-system-users)

[Employee system users](#employee-system-users)

[Generating System User Access Tokens](#generating-system-user-access-tokens)

[Business Integration system user access tokens](#business-integration-system-user-access-tokens)

[User access tokens](#user-access-tokens)

[Using tokens in requests](#using-tokens-in-requests)

[Business asset access](#business-asset-access)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFxmMLX&_nc_oc=Adk0MDKdx0ok-BK_nCRu9o2VoLUsCvcSS3YTSGuiVeiTEp3CHEmUtFFDnPFFuJWwMjY&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=bLvR4HwqE4twOsmLVl3Ejw&oh=00_AfiZaLCXkUNmXO7p34qR3a-UHJXm7NCQvBndGbAZf95Vsg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwEBwnQ4&_nc_oc=AdmOpkTsfGruoAAHVK1H9YfwyFzxRYaDBo2LGWyP4WkKibtFMrMa9lGoBZRy9wKpnHs&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=bLvR4HwqE4twOsmLVl3Ejw&oh=00_AfjemJLgFngUUb4UNPsQczWVI8p8kUYC5bNIam0qngamsg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[![X](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwF8X-KD&_nc_oc=AdkYRc8mkS5m80V438qLHvaUkjy4uVxq1x1oAyNMFjMWETxcQ5YMI69734whtKeAIqA&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=bLvR4HwqE4twOsmLVl3Ejw&oh=00_Afi_B9PfghURiglO-4RH6U2kHmSlgTLVOpqA9xru8GnDzg&oe=692BC22A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[![LinkedIn](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwH4mhnt&_nc_oc=AdkVG_kGsVcK_P1OeUBWJEXcF5ZnM9WhzjPNv90HPNUe9FLv2eePCqyf85tpwLFFwnE&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=bLvR4HwqE4twOsmLVl3Ejw&oh=00_AfgB3JoyKjtpoK6xQ3vfNYF2rAKB41lzFmlpdYbLKtg98A&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[![YouTube](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwGh9vcp&_nc_oc=AdmkzaI0-6ppCV1-LcMpNbj3nGN-1u9RWnzAn2-KS4iu2FbGDhFCn5CMjp8d_MyvMqc&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=bLvR4HwqE4twOsmLVl3Ejw&oh=00_AfhGCJE1odhXpgXyaWA8m-FVU-Une5yO9AHfAIxx6EyeFg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2xccvgMcN-kaEUQ9vIv0gFijZw1XYYLbNlIOfNedIP2D3fgOqMcpQ402Z8PIEK6s6j6vAwV1hDs3yB4zHqzqLGvEXUwuaWdC19MMLraDPnnfjCxDkReEJ-WcD8Ij8ItQfWEm5HXkEXW8BwipRAxg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)