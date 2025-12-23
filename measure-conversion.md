![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fmeasuring-conversion%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Measuring conversion](/docs/whatsapp/marketing-messages-api-for-whatsapp/measuring-conversion)

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

[Setting up conversion measurement](#setting-up-conversion-measurement)

[Understanding automatic objective setting](#understanding-automatic-objective-setting)

[Ensure your URL is compatible with conversion measurement](#ensure-your-url-is-compatible-with-conversion-measurement)

[Measure Website conversions with Meta Pixel or Conversions API](#measure-website-conversions-with-meta-pixel-or-conversions-api)

[Measure App Conversions with Meta SDK or Conversions API](#measure-app-conversions-with-meta-sdk-or-conversions-api)

[Using the Meta SDK](#using-the-meta-sdk)

[Via a 3rd party mobile measurement partner](#via-a-3rd-party-mobile-measurement-partner)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Setting up conversion measurement

Using Marketing Messages for WhatsApp, you can now integrate your marketing messages with events, allowing you to measure the rate and cost at which a Marketing message sent via Marketing Messages for WhatsApp leads to a downfunnel event like "purchase" on your website or app.

Conversion measurement is built on the same events that you can send to Meta when using Ads, making it seamless for businesses who are already integrated with Events for Ads purposes (e.g. via Pixel or Conversions API for websites, or Meta SDK in their mobile app), to leverage the same reporting automatically with no setup.

If a business is using both marketing messages on Marketing Messages for WhatsApp and Ad Campaigns on the same business portfolio, conversion events reported will be automatically attributed to the last Meta touch (either Marketing Messages for WhatsApp click or Ad click) before the event, based on the attribution window settings of each. For example, if a business is running both an Instagram Ad campaign and a Marketing message campaign on MM API for WhatsApp, each with a URL pointing to the same website for a sale, a user who purchases after clicking on both the Instagram Ad and the Marketing message will be attributed to either the MM API for WhatsApp click or the Ad click, based on the attribution window settings of each. This helps businesses better understand the holistic picture of their Ad and Marketing message campaigns in driving outcomes.

## Understanding linked Ad entities

When a business registers for Marketing Messages for WhatsApp, read-only Ad accounts are created under their business portfolio, which are synced to each WhatsApp Business Account under the same portfolio. Note that marketing messages are separate and distinct from Ads - the use of "Ads" terminology below represents the use of Ads entities as technical constructs only.

No action is needed on the part of the business or partner - these linked read-only Ad accounts are kept in sync with any changes made to Marketing templates, so that any new or updated marketing templates are reflected by their linked ad entity.

Linking Marketing templates to Ad accounts provide several benefits:

**Common UI and API for marketing teams:** Businesses can view their Marketing Messages for WhatsApp marketing campaigns and campaign metrics as "Campaigns" in Ads Manager’s "Marketing Messages" tab, and via API using the Marketing API "[Insights API](/docs/marketing-api/insights/)". Using these interfaces helps a business’ marketing teams view their Ads and Marketing message campaigns using common interfaces and terminology, instead of viewing Ad campaigns in one place and marketing campaigns sent via WhatsApp in another.

* **New metrics:** The Ads Manager UI and Insights API report new Conversion metrics (e.g. Web, App) that Cloud API and the Business Management API do not support. When Marketing template messages sent via MM API for WhatsApp lead to Conversion events (e.g. add to cart, purchase) that a business reports from their website or app, these conversion events are attributed to the Marketing message and are shown in metrics, leading to a better understanding of Marketing message ROI. Reporting events is done via integration with Pixel or Conversions API for Web and App Events and the Meta SDK.

## Template-to-Ad-sync guidelines

* Marketing templates map to Ads only once during initial onboarding to Marketing Messages for WhatsApp.
* Syncs must be completed for templates to display correct app conversion metrics.
* Ads syncing can take up to 10 minutes.
* Avoid sending messages with new templates before syncing completes to prevent errors or loss of optimization and tracking.
* Existing templates prior to initial onboarding will not have conversion metrics enabled.
* To reactivate unused templates for over 7 days: Send one message using the template and wait 10 minutes for Ad sync to re-activate.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/476235279_4018761408406419_4409302645887282875_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=uSCc7hmew_QQ7kNvwH8V1Q1&_nc_oc=Adl4WCmAs13MG5GquLg9iBLj5VEc2sEqaQdhiU30hD5iPatnJltBjxc94HbwfmZ84NA&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=conJf2kawHEYKYT849jXZw&oh=00_AfhdRIfvn4GCeXAu7b65a92WGXMWcS-dfos2ShlmC2Wlxw&oe=69403C4B)

## Understanding automatic objective setting

In order to measure Conversion events, Marketing Messages for WhatsApp automatically syncs Marketing templates to corresponding Ads entities (Campaigns, Message sets, and Ads) with configurations that allow for Conversion reporting of an assumed objective.

This linking process happens automatically, to reduce the integration complexity of Marketing Messages for WhatsApp for businesses. For those familiar with Meta’s Ads ecosystem, note that these Campaign and Ad Set parameters will not change how messages are delivered via Marketing Messages for WhatsApp - they are only set so that reported events can be correctly attributed.

See the table below for how Marketing templates are mapped to Ads entities.

|  | Campaign parameters | Message Set parameters |
| --- | --- | --- |
| Marketing templates with no CTA URL button | Objective:OUTCOME\_SALES | OptimizationGoal: Impression |
| Marketing templates with a CTA URL button that points to a website or app without event reporting enabled. | Objective:LINK\_CLICKS | OptimizationGoal: LinkClicks |
| Marketing templates with a CTA URL button that points to a website or app with event reporting enabled. | Objective:LINK\_CLICKS | OptimizationGoal: OffsiteConversion |

* Event reporting is detected by whether the URL points to a website or app which the same business portfolio has enabled for event reporting via Pixel, Conversions API, or Meta SDK.

While most changes to Templates will be automatically synced with Ads (e.g. text content), Campaign and Message set parameters are synced only once when a business first onboards to Marketing Messages for WhatsApp or creates a new Template, in order to maintain a consistent campaign and message set structure when reporting on clicks and conversions from messages sent using that Template. This means that if you wish to add, edit, or remove a URL from a CTA button on a Template, you must create a new Template in order to correctly capture click and conversion metrics for the updated URL.

## Ensure your URL is compatible with conversion measurement

In order to attribute events you report via Meta Pixel, Conversions API for web or app events, or Meta SDK, Meta will append URLs you send in CTA buttons on Marketing Template messages with a Meta click ID, prior to sending.

This may produce an error if you or a partner you work with uses a shortlink service that also attempts to reformat URLs.

For example:

1. You send the URL `www.mybusiness.com`
2. your partner reformats this to `www.partnerURL.com/abc123` prior to sending to Marketing Messages for WhatsApp
3. MM API for WhatsApp reformats this to `www.partnerURL.com/abc123?fbclid=yxz789` - the short URL service of your partner may break Meta’s ability to append the Click ID.

Please test to ensure your URLs are being correctly passed through, and you can see correct counts of conversion events via Ads Manager or Insights API, prior to running production workloads. If you experience any issues arising from this behavior, work with your partner or reach out to Meta directly with details.

## Measure Website conversions with Meta Pixel or Conversions API

Businesses who are reporting events from their website using Meta Pixel or Conversions API for web, can now measure when a clicking on a URL in a marketing message sent via Marketing Messages for WhatsApp leads to one of 3 conversion events.

If a business is not yet reporting Offsite Conversion events from their website, see documentation below to set up Event reporting:

**Tutorial**: [Get started with the Meta Pixel and Conversions API](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.facebookblueprint.com%2Fstudent%2Factivity%2F212737&h=AT3b9U_O3xbDgd6tyXep3x0MQTK-lDdlWliEsRVzcDFsXjVLKDeOZEl4cvhDRhHWLX5UGgdv1_0u79pTNGinBr1k_UulucYqgRuS0ghY_FvLvK63L0T87DjVb23RY9uWv3FB7_gmduUbLixkG53j9w)

Once a business is reporting events via Pixel or Conversions API, the following 3 standard events are automatically associated with website visitors who arrived at the site via a CTA URL from a marketing message sent via MM API for WhatsApp:

* Add to cart
* Initiate checkout
* Purchase
* Purchase value

When a user clicks a CTA URL in a Marketing Messages for WhatsApp message and performs any of the above 3 events, Meta will automatically attribute the conversion event to the MM API for WhatsApp Campaign, and make those analytics available to you or your Partner via the Insights API, which your Partner may surface on their own reporting surfaces that you are accustomed to using.

Note that if this conversion event is also being used to measure the efficacy of Ads on Facebook or Instagram, Meta will attribute the conversion to the ‘last touch’ interaction of the user. For example, if a user arrives at your website via an ad on Facebook, and then closes their browser window and later that day returns to your website via clicking a link from a MM API for WhatsApp message and purchases an item, that purchase conversion event will be attributed to the MM API for WhatsApp campaign (and not the ad on Facebook) as the most recent interaction.

## Measure App Conversions with Meta SDK or Conversions API

Businesses can use Marketing Messages for WhatsApp to measure when marketing messages lead users to perform app events, such as purchases and app activations. See [Conversions API for App Events](/docs/marketing-api/conversions-api/app-events) for an introduction to app events.

The following app conversion events are available for MM API for WhatsApp:

* App Purchase
* App Purchase value
* App Add to cart
* App Initiate checkout
* App Activations

Businesses can capture App conversion events in 3 ways. See [Conversions API for App Events](/docs/marketing-api/conversions-api/app-events) for more information.

1. Via the Meta SDK
2. Via the Conversions API
3. Via a 3rd party mobile measurement partner, who sends events to Meta on your behalf

### Using the Meta SDK

1. If your app is using Meta SDK, please [upgrade](/docs/android/upgrading-4x) your SDK version to Meta Android SDK v17.0.2 or above. Note iOS app measurement is currently not supported.
2. If your app is using a supported Mobile Measurement Partner (MMP), check with your MMP to get your app ready.
3. If your app is using Conversions API, learn more [here](/docs/marketing-api/conversions-api/parameters/app-data#campaign-ids) to send campaign\_ids parameters w/ app events. To get campaign\_ids, you’ll need to parse `campaign_ids` from `al_applink_data parameters` from the deep link that the user clicked from.

Example deep link:

```
exampleapp://applink/ad_landing_recommend?data={"goods_id":"39109246","page_type":"B"}&al_applink_data={"target_url":"https://www.exampleapp.com&fbclid=IwZXh0bgNhZW0BMAABHbKVD62Fa0uTdpAh6KZn16BmrnWgsTbZgiCEsKGLOcF9RDncEAsbJKWp0Q_aem_y0zBYthdxb0j9epvkZum7w","extras":{"fb_app_id":312563225523989},"referer_app_link":{"url":"fb:///?app_id=312563225523989","app_name":"Facebook"},"campaign_ids":"IwAR2rBBgtFjvI_IUUes4nZ6FcQ0dtqujIz1w9JIwrs1YKKn7tGIIqC4kKrXk_wapm_fVVosPGBQJWpvSW8Z8emXg_aem_pyDxR3ch5qDkVdd0Y138yg","ad_id":"1234567","adgroup_id":"1234567","campaign_id":"1234567","campaign_group_id":"1234567","account_id":"1234567"}
```

4. Make sure you have pixel/conversions set up for the fallback website URL as well.

### Via a 3rd party mobile measurement partner

Some mobile measurement platforms will automatically forward App conversion events to Meta on your behalf. No integration effort is needed on your part.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Setting up conversion measurement](#setting-up-conversion-measurement)

[Understanding automatic objective setting](#understanding-automatic-objective-setting)

[Ensure your URL is compatible with conversion measurement](#ensure-your-url-is-compatible-with-conversion-measurement)

[Measure Website conversions with Meta Pixel or Conversions API](#measure-website-conversions-with-meta-pixel-or-conversions-api)

[Measure App Conversions with Meta SDK or Conversions API](#measure-app-conversions-with-meta-sdk-or-conversions-api)

[Using the Meta SDK](#using-the-meta-sdk)

[Via a 3rd party mobile measurement partner](#via-a-3rd-party-mobile-measurement-partner)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mOeiZ4djezYVY1VJepM_8Q&oh=00_Afhby811GMSa_BA6FF5efDDUq7R7ELEy-EaV3MsPGPW0uA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mOeiZ4djezYVY1VJepM_8Q&oh=00_AfiySwTkJN1FnWXbn_DNttVczXLKb5IuUJeS9AoxZBFkqA&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mOeiZ4djezYVY1VJepM_8Q&oh=00_AfioIUK9Ty81GK8aAANk4KASLyMTr6UAN7Drblgyy3l9rQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mOeiZ4djezYVY1VJepM_8Q&oh=00_AfhJgfrBdOL9z9fsmKWvVOcUDuq4Yty9ejp9Cmhux3y6IQ&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mOeiZ4djezYVY1VJepM_8Q&oh=00_Afi7XUkRXuXHHNkTB2s8M8P3NqRRQ3ez_XE-WuXYM2Eekw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0WyqdaWW4IHJdDj3w_0LZcK5zq6rMvCeETiBxsq-9fqFgQtPcZ90iwoAMLMNKAVbq2OZjaJ2fUlOYhH0jYzfaaETURIpxFdCoTFoMg8yGkHKflYVroLR9YIeP3X6cTiw8GIiIspfSGBA_-gctcPQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)