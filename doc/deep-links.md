![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fguides%2Fdeep-links%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Deep links](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides/deep-links)

[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)

* [Get started](/docs/whatsapp/marketing-messages-api-for-whatsapp/get-started)
* [Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)

  + [Onboarding](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding)
  + [Sending messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages)
  + [Measuring conversion](/docs/whatsapp/marketing-messages-api-for-whatsapp/measuring-conversion)
  + [Tracking click events](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides/tracking-click-events)
  + [Viewing metrics](/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics)
  + [Deep links](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides/deep-links)
* [Features](/docs/whatsapp/marketing-messages-api-for-whatsapp/features)
* [Onboard business customers](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers)
* [Pricing](/docs/whatsapp/marketing-messages-api-for-whatsapp/mm-api-pricing)
* [Support](/docs/whatsapp/marketing-messages-api-for-whatsapp/support)
* [Changelog](/docs/whatsapp/marketing-messages-api-for-whatsapp/changelog)

Nesta Página

[Deep links](#deep-links)

[Template creation via WhatsApp Manager](#template-creation-via-whatsapp-manager)

[Form fields](#form-fields)

[Template creation via API](#template-creation-via-api)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Viewing metrics](#viewing-metrics)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Deep links

You can map an [Android deep link](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.android.com%2Ftraining%2Fapp-links%2Fdeep-linking&h=AT2-3kR54stc8EOnzWTsBnCI4agCcskoVTzyA4Ig1QxrTEqnjl-5IUpf0_uqgEpBPsWz_J0VfGPjLYt6o71ga1Y3ptr-zHQBFIi4oj31rl0FzZrnT5I9lCyAW7rp88g9ITHXy15o9K2hArWBPWzbSg) to a marketing template URL button that, when tapped, loads a particular location or content within your app.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/499229465_1266088541526902_7472965918950036987_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=kBNJyvGpkDsQ7kNvwEZ3NAQ&_nc_oc=AdnIk7fyn8bs_JYo5MSiIKrBd4fq-SmmQGRW8SV-0z9lJ3yWOX6E93EWnxJv-KAglA8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfgMrtjcNjBXysQExFLwaZGeO-aydZX2AIYOvNiMtrileA&oe=694054C5)

If you have not onboarded to the Marketing Messages API for WhatsApp (MM API for WhatsApp), your marketing templates will not display any conversion metrics. Learn more about how to [measure conversion](/docs/whatsapp/marketing-messages-api-for-whatsapp/measuring-conversion).

## Template creation via WhatsApp Manager

To create a template with a button mapped to an Android deep link:

1. Access [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/).
2. Navigate to the **Message templates** > **Manage templates** panel and click the **Create template** button.
3. Select **Marketing** (tab) > **Custom** (radio button) and click the **Next** button.
4. In the **Buttons** section, click the **+ Add buttons** dropdown menu and select **Visit website**.
5. Check the **Track app conversions** checkbox to reveal the deep link fields (pictured below).
6. Complete each field using their tooltips or [form field](#form-fields) descriptions below as guidance.
7. Add any additional components you'd like your template to use, name your template, and submit it for approval.

Note that you can also use the **Manage templates** panel to edit an existing template and add a deep link-mapped button, but the template will have to undergo template review again.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/524030257_747636164413080_2609413167857336367_n.png?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=e7KPU8G6Ha0Q7kNvwEm-B1E&_nc_oc=AdmclsmwvavQSmraNu1iqAI-nS-ff8srgYO9QuAEp-5JguiZ2b554Nw1G92E-p5XPuY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfiEujASpE4G8gC2WL4CNPBVtI_WEsTS0kyWXwroWEEboQ&oe=694049D2)

### Form fields

| Field label | Description | Example value |
| --- | --- | --- |
| Android deep link | **Required.** Android deep link URI. | luckyshrub://deals/summer\_solstice |
| Android fallback URL | **Optional.** Fallback URL. If the WhatsApp client cannot load the deep link URI, the client will load this URL in the device's default web browser.  If omitted, the client will attempt to load the URL specified in the Website URL field instead. | https://www.luckyshrub.com/deals/summer\_solstice |
| Button Text | **Required.** Button label text. Maximum 25 characters. | View deal |
| Meta app ID | **Required.** This is a list of the Meta app(s) associated with your business portfolio. Select the app whose access token you will use to send the template. | Lucky Shrub (634974688087057) |
| Type of Action | Required.  Must be set to **Visit website**. | Visit website |
| URL Type | **Required.** Set to **Static** if your Android deep link or Android fallback URL has no dynamic values, otherwise set to **Dynamic**. | Static |
| Website URL | **Required.**  URL of a website to load if the WhatsApp user views the message on a non-Android device, or if the WhatsApp client cannot load your Android deep link URI and no Android fallback URL is specified. | https://www.luckyshrub.com/ |

## Template creation via API

Use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account/message_templates#Creating) endpoint to create the template and include a URL button component mapped to your Android deep link.

Note that you can also use the [POST /<TEMPLATE\_ID>](/docs/graph-api/reference/whats-app-business-hsm/#Updating) endpoint to edit an existing template and add a URL button component, but the template will have to undergo template review again.

### Request syntax

Template components can vary based on your needs. This example syntax creates a marketing template with the following components:

* **text header**, without parameters
* **body**, without parameters
* **URL button**, mapped to a deep link URI and fallback URL

```
'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE>",
  "category": "marketing",
  "components": [
    {
      "type": "header",
      "format": "text",
      "text": "<HEADER_TEXT>"
    },
    {
      "type": "body",
      "text": "<BODY_TEXT>"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "<BUTTON_LABEL_TEXT>",
          "url": "<BUTTON_URL>",
          "app_deep_link": {
            "meta_app_id": <META_APP_ID>,
            "android_deep_link": "<ANDROID_DEEP_LINK>",
            "android_fallback_playstore_url": "<FALLBACK_URL>"
          }
        }
      ]
    }
  ]
}'
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACCESS_TOKEN>` *String* | **Required.** [System token](/docs/whatsapp/business-management-api/get-started#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAJB...` |
| `<ANDROID_DEEP_LINK>` *String* | **Required if using a URL button component mapped to a deep link.** [Android deep link](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.android.com%2Ftraining%2Fapp-links%2Fdeep-linking&h=AT3SFe70C9WTVdBjrZaGgG-FilGYl_MVtHjSa3UkkqFjNfZI_g3K9atwlF7pM8dGmN_L9XtPq4lV4I1xLf_ZAUNKdUG8eezVHg7czob9q2hff7CKJZNxqfiMYVWKrq2BCo9UaUw3DzpNo4Yf0kyGtQ) URI. The WhatsApp client will attempt to load this URI if the WhatsApp user taps the button on an Android device. | `luckyshrub://deals/summer/` |
| `<API_VERSION>` *String* | **Optional** Graph API [version](/docs/graph-api/guides/versioning). | `v22.0` |
| `<BODY_TEXT>` *String* | **Required if using a body component.** Template body text. Variables are supported. Maximum 1024 characters. | `Beat the heat with our sizzling summer deals on succulents! At Lucky Shrub, we...` |
| `<BUTTON_LABEL_TEXT>` *String* | **Required if using a URL button component.** Button label text. Maximum 25 characters. | `View Deals` |
| `<BUTTON_URL>` *String* | **Required if using a URL button component.** URL of a website that the WhatsApp client will attempt to load in the device's default web browser when the button is tapped. For deep links, this URL only be used if the WhatsApp user taps the button on a non-Android device. | `https://www.luckyshrub.com/deals/summer/` |
| `<FALLBACK_URL>` *String* | **Required if using a URL button mapped to a deep link.** URL of a website that the WhatsApp client will attempt to load in the device's default web browser when the button is tapped but unable to load the Android deep link URI. | `https://www.luckyshrub.com/deals/summer/` |
| `<HEADER_TEXT>` *String* | **Required if using a text header component.** Template header text string. Supports up to 1 parameter. If this string contains a parameter, you must include an `example` property. Maximum 60 characters. | `Sizzling Summer Deals at Lucky Shrub` |
| `<META_APP_ID>` *Integer* | **Required if using a URL button mapped to a deep link.** Your Meta app ID. | `634974688087057` |
| `<TEMPLATE_LANGUAGE>` *String* | **Required.** Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>` *String* | **Required.** Template name. Maximum 512 characters. | `summer_deals_deep_link_v1` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>` *String* | **Required.** WhatsApp Business Account ID. | `102290129340398` |

## Example request

```
curl 'https://graph.facebook.com/v22.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "summer_deals_deep_link_v1",
  "language": "en_US",
  "category": "marketing",
  "components": [
    {
      "type": "header",
      "format": "text",
      "text": "Sizzling Summer Deals at Lucky Shrub"
    },
    {
      "type": "body",
      "text": "Beat the heat with our sizzling summer deals on succulents! At Lucky Shrub, we're passionate about bringing a touch of greenery to your life. Our succulents are not only low-maintenance and easy to care for, but they also add a pop of color and style to any room. Use the button below to see our Summer Steals!"
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "url",
          "text": "View Deals",
          "url": "https://www.luckyshrub.com/deals/summer/",
          "app_deep_link": {
            "meta_app_id": 634974688087057,
            "android_deep_link": "luckyshrub://deals/summer/",
            "android_fallback_playstore_url": "https://www.luckyshrub.com/deals/summer/"
          }
        }
      ]
    }
  ]
}'
```

## Viewing metrics

See our [Viewing metrics](/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics) document.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Deep links](#deep-links)

[Template creation via WhatsApp Manager](#template-creation-via-whatsapp-manager)

[Form fields](#form-fields)

[Template creation via API](#template-creation-via-api)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Viewing metrics](#viewing-metrics)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfiEcxt3pJNciaBNWtOQCEpuAzLUHQc6uB0XLuP2olw5jw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfgClIh_XxlgNWXvpbqGlP35cDe6yR97ezFj_OwP7ZpzZA&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfjF9VmOyqSSAK_aFsXdwtPSW4XPTgM4SQclYM9H5HtiqA&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0ORhIpZkqQ9-wtF15_SexE1Szp5PIfLZPxOB3hxaqQp-VT_e9set63JozfBM9xdaMS2aEuQUh1i-VSz0P1HAoCKVYHCwLJVLgWJDov5QZ_iCyN2JeWh-p3ulcOTl3y8UWHvBfwX2frBOFhNM2Hkw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfiUociFyCxd4iNnvvtGpIeq3UYgS56ek-DiMBjhLU00OQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3B-tvqFjyKuCzQb6V5EXHVlmqflmHVFArP04eZVOLKv9xRdM0e7tVnIyNwWcQdeWRWygtOHg8LnWQYp14mxq8ceWcrh0WN6qGqpctsd7qkGdUWDfS4qUFa5iat2UufPfHkVXkCipk-waXShFXJOQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfhT2RPL7rIzoxd-EF189fOBlpxnqT7MuthHy3fmOn_0Gg&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT24_HzGer7o9OVNr0DTLSmc4ulGkaieH-k-BqClb1vo1U4JhNG0HjUX1Ds8do4eU-6YFBTdYKDWm2MHZAuR1dGjxOX1Hk5tJUmf7x7tKn3hwvHCt2nRdAEYHCZJqhF5vN_KY9mbXV-8eqA0_PkIzA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfhRydICOGwdn6kGEa6X14Ph5qiKGZqxVUvH4FeJwGQZbQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT25QMaHX5k1Q3zkKUL_9w18doZJWf8oTnfpNmn2vAlEk8OYhThTRbMO2KpTrDcF40rcuSzOvt15Wzf6VAbW7wZvx5ngwPaj0GMWQOoWHbd_ftSWxiYyomG7OwFLQOBYbHRYim32fAynKHDVx2EVpQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3MncaIAii44MzYzq9WsmLydEthyDFsPmmrwp233eXXMuzIaDstchPnzYeW0yrHt80P765CfGMirCahcs0fKcZA23xaxL1G3KTGEqJKV9aluJ4A2sY_0Z7Nts28w_rkgSf6npM261CWsXRrFQOxVg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3KiIZj5uu1vHxH3a6aVELgcdVsTKb5KGHY6Majb-2t2d6Vw4fHi98iJBKU5lAEnAJ88VA1nwfCNthJoZ2zh6mnM05sRn977eorbKv6K7Ou62oEXt84YGMABCRqG9Bjr90aJzhhrfVujNy2Nnun-Q)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_Afh65n2iCqndsTHaXJY7P4wkqt-FPAuYOKsmgThzdd2oWA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_Afg_clJTuJK9yIVaUJ4ZCe8_e0O3VKV59-DtXlrhw3xW4A&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3yl_brbd5hWVvQBxmkHXRSS-u9ZYcsXzAV9Oq7sq1OsXuo7Jh-l67yJLijRMlEjKnw5J8o2DwA5cdEHIoOcm2l2ZoAGVZ8zlW_njk0GZBR2SUkeROhKmJVlLDxt71h6lzlVoZfICL_BjvbPZVHpQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_Afjoniwd6xIoCTKHJfme4Cij6ujZF4vNQ4s4y7J5UV9gRA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1O_6yCePTjKDvpI120MQD1fovPLbBhvxm5BkrJlKcj1LxwdgWqykZtG5-T5wCxjKxxSUqyQ3JUXgZV1bE7h0H7y994k5Cvc-HQQOcsZVdpbMGPzjmBN4RtAIXBiw1kHxzafh_Zmdruj-UCFw8zOQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfiAcLL3pstvFFPpii8AtRFVtQtCqs_fcdGW1vpSZESC1Q&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1NrvKDtspkSGsCeuv5yaZxf-pX_joMuUwLoND4Izn1_a6boy-jDVPgnJQPwBFroVFpP8C60vTYz5IX03yBwDU1KVXm5hkgkA8iB6n4okdaOuUJ5-V9fou24gn265eHOW5YwCOEQ4CvIQXo2wAfJw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=W4j9kZekYB3lpS_ZDVyL8g&oh=00_AfhCiYOpIVRTBqH4WA57vZ0pNNpVbK156b2x-kr5C7onNQ&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0PxLURPv-f59HxDdrlr-thBCg64tWYUWMDF6zLfcUx8_ZXWEe6S28IYKZNNo8RrwWWtl3se6BQVuxEyExqMM4lw4bV5ifTDd9-wLzpJ7S0rSLkGS9waM1UsFucaGENDaWM6fkEPKs-4YKiqdf-cw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3r4uxpTKSIOfutNbbgotlTATWGSjsIgzJRWp1M3wrK8s7MoT3mIRQ6cTHubzUPr0KNRQ9kYxUWSIoBX34wswpccq5-jh2yc9oZmGWxi7kZVtPshMIxbExA0IsTeGPAuGFHypljI88nkad5keL8tQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)