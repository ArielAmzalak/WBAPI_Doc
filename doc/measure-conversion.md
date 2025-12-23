+++
id = "measure-conversion"
title = "Setting up conversion measurement"
summary = "Using Marketing Messages for WhatsApp, you can now integrate your marketing messages with events, allowing you to measure the rate and cost at which a Marketing message sent via Marketing Messages..."
source = "https://developers.facebook.com/docs/whatsapp/measure-conversion"
lang = "en"
tags = ["whatsapp-business-platform", "templates", "tools"]
+++
# Setting up conversion measurement

Using Marketing Messages for WhatsApp, you can now integrate your marketing messages with events, allowing you to measure the rate and cost at which a Marketing message sent via Marketing Messages for WhatsApp leads to a downfunnel event like "purchase" on your website or app.

Conversion measurement is built on the same events that you can send to Meta when using Ads, making it seamless for businesses who are already integrated with Events for Ads purposes (e.g. via Pixel or Conversions API for websites, or Meta SDK in their mobile app), to leverage the same reporting automatically with no setup.

If a business is using both marketing messages on Marketing Messages for WhatsApp and Ad Campaigns on the same business portfolio, conversion events reported will be automatically attributed to the last Meta touch (either Marketing Messages for WhatsApp click or Ad click) before the event, based on the attribution window settings of each. For example, if a business is running both an Instagram Ad campaign and a Marketing message campaign on MM API for WhatsApp, each with a URL pointing to the same website for a sale, a user who purchases after clicking on both the Instagram Ad and the Marketing message will be attributed to either the MM API for WhatsApp click or the Ad click, based on the attribution window settings of each. This helps businesses better understand the holistic picture of their Ad and Marketing message campaigns in driving outcomes.

## Understanding linked Ad entities

When a business registers for Marketing Messages for WhatsApp, read-only Ad accounts are created under their business portfolio, which are synced to each WhatsApp Business Account under the same portfolio. Note that marketing messages are separate and distinct from Ads - the use of "Ads" terminology below represents the use of Ads entities as technical constructs only.

No action is needed on the part of the business or partner - these linked read-only Ad accounts are kept in sync with any changes made to Marketing templates, so that any new or updated marketing templates are reflected by their linked ad entity.

Linking Marketing templates to Ad accounts provide several benefits:

**Common UI and API for marketing teams:** Businesses can view their Marketing Messages for WhatsApp marketing campaigns and campaign metrics as "Campaigns" in Ads Managers "Marketing Messages" tab, and via API using the Marketing API "[Insights API](/docs/marketing-api/insights/)". Using these interfaces helps a business marketing teams view their Ads and Marketing message campaigns using common interfaces and terminology, instead of viewing Ad campaigns in one place and marketing campaigns sent via WhatsApp in another.

* **New metrics:** The Ads Manager UI and Insights API report new Conversion metrics (e.g. Web, App) that Cloud API and the Business Management API do not support. When Marketing template messages sent via MM API for WhatsApp lead to Conversion events (e.g. add to cart, purchase) that a business reports from their website or app, these conversion events are attributed to the Marketing message and are shown in metrics, leading to a better understanding of Marketing message ROI. Reporting events is done via integration with Pixel or Conversions API for Web and App Events and the Meta SDK.

## Template-to-Ad-sync guidelines

* Marketing templates map to Ads only once during initial onboarding to Marketing Messages for WhatsApp.
* Syncs must be completed for templates to display correct app conversion metrics.
* Ads syncing can take up to 10 minutes.
* Avoid sending messages with new templates before syncing completes to prevent errors or loss of optimization and tracking.
* Existing templates prior to initial onboarding will not have conversion metrics enabled.
* To reactivate unused templates for over 7 days: Send one message using the template and wait 10 minutes for Ad sync to re-activate.

## Understanding automatic objective setting

In order to measure Conversion events, Marketing Messages for WhatsApp automatically syncs Marketing templates to corresponding Ads entities (Campaigns, Message sets, and Ads) with configurations that allow for Conversion reporting of an assumed objective.

This linking process happens automatically, to reduce the integration complexity of Marketing Messages for WhatsApp for businesses. For those familiar with Metas Ads ecosystem, note that these Campaign and Ad Set parameters will not change how messages are delivered via Marketing Messages for WhatsApp - they are only set so that reported events can be correctly attributed.

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
3. MM API for WhatsApp reformats this to `www.partnerURL.com/abc123?fbclid=yxz789` - the short URL service of your partner may break Metas ability to append the Click ID.

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

Note that if this conversion event is also being used to measure the efficacy of Ads on Facebook or Instagram, Meta will attribute the conversion to the last touch interaction of the user. For example, if a user arrives at your website via an ad on Facebook, and then closes their browser window and later that day returns to your website via clicking a link from a MM API for WhatsApp message and purchases an item, that purchase conversion event will be attributed to the MM API for WhatsApp campaign (and not the ad on Facebook) as the most recent interaction.

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
3. If your app is using Conversions API, learn more [here](/docs/marketing-api/conversions-api/parameters/app-data#campaign-ids) to send campaign\_ids parameters w/ app events. To get campaign\_ids, youll need to parse `campaign_ids` from `al_applink_data parameters` from the deep link that the user clicked from.

Example deep link:

```
exampleapp://applink/ad_landing_recommend?data={"goods_id":"39109246","page_type":"B"}&al_applink_data={"target_url":"https://www.exampleapp.com&fbclid=IwZXh0bgNhZW0BMAABHbKVD62Fa0uTdpAh6KZn16BmrnWgsTbZgiCEsKGLOcF9RDncEAsbJKWp0Q_aem_y0zBYthdxb0j9epvkZum7w","extras":{"fb_app_id":312563225523989},"referer_app_link":{"url":"fb:///?app_id=312563225523989","app_name":"Facebook"},"campaign_ids":"IwAR2rBBgtFjvI_IUUes4nZ6FcQ0dtqujIz1w9JIwrs1YKKn7tGIIqC4kKrXk_wapm_fVVosPGBQJWpvSW8Z8emXg_aem_pyDxR3ch5qDkVdd0Y138yg","ad_id":"1234567","adgroup_id":"1234567","campaign_id":"1234567","campaign_group_id":"1234567","account_id":"1234567"}
```

4. Make sure you have pixel/conversions set up for the fallback website URL as well.

### Via a 3rd party mobile measurement partner

Some mobile measurement platforms will automatically forward App conversion events to Meta on your behalf. No integration effort is needed on your part.
