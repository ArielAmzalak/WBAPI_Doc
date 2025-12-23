+++
id = "changelog"
title = "Changelog"
summary = "Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available."
source = "https://developers.facebook.com/docs/whatsapp/changelog"
lang = "en"
tags = ["whatsapp-business-platform"]
+++
# Changelog

## November 19, 2025

*Marketing Messages API for WhatsApp*

[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp) (formerly known as Marketing Messages Lite API) is now generally available.

## October 31, 2025

*MM Lite API*

* Added two new [Automatic Creative Optimization types](/docs/whatsapp/marketing-messages-lite-api/sending-messages#product-extensions): product extensions and text formatting optimization.
* Launched a new endpoint to support [WABA-level opt-out](/docs/whatsapp/marketing-messages-lite-api/sending-messages#configure-automatic-creative-optimizations--whatsapp-business-account-level-) for automatic creative optimizations.

## October 20, 2025

*MM Lite API*

* [Offsite conversion metrics](/docs/whatsapp/marketing-messages-lite-api/viewing-metrics) is now available in WhatsApp Business Manager and in the [Template Analytics API](/docs/whatsapp/business-management-api/analytics#template-analytics).
* Added two new Automatic Creative Optimization features: [Headline extraction](/docs/whatsapp/marketing-messages-lite-api/sending-messages#headline-extraction) and [Tap-target title extraction](/docs/whatsapp/marketing-messages-lite-api/sending-messages#tap-target-title-extraction).

## October 17, 2025

*MM Lite API*

Added [`marketing_messages_onboarding_status`](/docs/whatsapp/marketing-messages-lite-api/onboarding#if-you-want-to-check-tos-and-intent-request-status-for-the-business-manager) and [`owner_business_info`](docs/whatsapp/marketing-messages-lite-api/onboarding#if-you-want-to-check-tos-and-intent-request-status-for-the-business-manager) fields to check Terms of Service and Intent request status for business manager.

## October 14, 2025

*MM Lite API*

The [`product_policy`](/docs/whatsapp/marketing-messages-lite-api/sending-messages#send-marketing-template-messages) field is now 100% rolled out for businesses customers.

## October 8, 2025

*Embedded Signup*

Embedded Signup version 4 is now available. Version 4 provides a simplified onboarding experience and allows you to onboard business customers to multiple products (WhatsApp Cloud API, Marketing Messages Lite API, Ads that click-to-WhatsApp and the Conversions API). For more information, see the [versions](/docs/whatsapp/embedded-signup/versions) and [v4](/docs/whatsapp/embedded-signup/versions/version-4) page.

*MM Lite*

Updated the [onboarding page](/docs/whatsapp/marketing-messages-lite-api/onboarding#onboarding-business-customers) with an onboarding video tutorial.

## October 1, 2025

*MM Lite API*

Updated the [support page](/docs/whatsapp/marketing-messages-lite-api/support) with new troubleshooting guides.

## September 29, 2025

*MM Lite API*

Added a [Coexistence onboarding guide to MM Lite](/docs/whatsapp/marketing-messages-lite-api/for-solution-providers#onboard-whatsapp-business-app-users--aka--coexistence--). Whatsapp Business users can now onboard with their existing WhatsApp Business app account and phone number.

## September 3, 2025

*MM Lite API*

* On September 8th, 2025, we're launching a new [MM Lite ToS signed webhook](/docs/whatsapp/marketing-messages-lite-api/onboarding#receive-mm-lite-terms-of-service-signed-webhook--preferred-), which will be sent whenever a business signs the MM Lite ToS via any method (e.g. Embedded Signup, or in WhatsApp Manager). The webhook will have a more descriptive name than the existing `AD_ACCOUNT_LINKED` webhook. The older webhook will be deprecated by Jan 1, 2026.
* [Conversion metrics](/docs/whatsapp/marketing-messages-lite-api/viewing-metrics) will now also be available in WhatsApp Manager UI and via the WhatsApp Business Management API. This means that we're removing the ability to view MM Lite metrics for read-only Ad Accounts in Ads Manager.
* The `/marketing_messages` endpoint will [accept marketing messages for both MM Lite API and Cloud API](/docs/whatsapp/marketing-messages-lite-api/sending-messages#send-marketing-template-messages).

## August 22, 2025

*MM Lite API*

Added a [features page](/docs/whatsapp/marketing-messages-lite-api/features) comparing MM Lite and Cloud API features.

MM Lite API [uptime and availability metrics](/docs/whatsapp/support-api-status-page) are now live on [metastatus.com](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2Fwhatsapp-business-api%3Ffbclid%3DIwY2xjawM2tbNleHRuA2FlbQIxMQBicmlkETFPWE5PUldSeE95a2tuMnA1AR66setbfmUOYwOMQ3HtM7k277dWGE5sNlomsS6qAp8WTv_DlOf4Y10k6Dhf2w_aem_ieXDJ6jqZJA6QbtWWAA2Dw&h=AT3n3r2UMYgHR_ORzNE3aLMLqF4bYOwSqrFUv5iZi1n5fjlm_KFQO6mSVxzZqQSBZnPV4qMzTdAZQyZl98SXeCQoiaDoWTz0w_YLAl0d576l5FUWCT9hcbb8D0dZRXI6Vb_xAAVDw4aHIRZm0d_vAA), providing visibility into service status.

## August 06, 2025

*MM Lite API*

Added a [image background generation](/docs/whatsapp/marketing-messages-lite-api/sending-messages) field for automatic creative optimization.

## July 25, 2025

*MM Lite API*

* Updated [references](/docs/whatsapp/marketing-messages-lite-api/guides/deep-links#form-fields) to "Mobile App ID" to "Meta App ID" when creating a template to avoid confusion.
* Added a [Template-to-ad-syncing guideline](/docs/whatsapp/marketing-messages-lite-api/measuring-conversion) for clients to follow to ensure all templates be set up for conversion metrics.

## July 22, 2025

*MM Lite API*

Local Storage is now available for MM Lite. If you have already enabled [Local Storage](/docs/whatsapp/cloud-api/overview/local-storage) for the Cloud API, your existing settings are automatically applied to the MM Lite API.

## July 16, 2025

*MM Lite API*

Added a troubleshooting guide on how to identify admins of a business portfolio using Meta Business Suite or the API. Both methods return the same results.

* [Meta Business Suite](https://business.facebook.com/): Navigate to the Business Settings to view users with **Full Control** access.
* API: [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account) and [GET /<BUSINESS\_PORTFOLIO\_ID>/business\_users](/docs/marketing-api/reference/business/business_users/) endpoints to get a list of business portfolio admins.

## July 15, 2025

*MM Lite API*

* Added [`marketing_messages_onboarding_status` field](/docs/whatsapp/marketing-messages-lite-api/onboarding#checking-eligibility-status) which provides more granular eligibility status data. The field will be a replacement for [`marketing_messages_api_status` field](/docs/whatsapp/marketing-messages-lite-api/onboarding#checking-eligibility-status--alternative-) which will be deprecated in version 24.0.
* Fixed the `marketing_messages_lite_api_status` field to correct a bug which was erroneously returning `ELIGIBLE` when it should have returned `ONBOARDED`. This field will be deprecated in version 24.0, so we recommend using the new `marketing_onboarding_status` field instead.
* Changed the `marketing_messages_api_status` field to no longer require one or more registered phone numbers, or one or more MM Lite API-ready templates, in order for `ONBOARDED` to be returned.

## July 1, 2025

*MM Lite API*

Per-message pricing now applies to MM Lite API! See [Pricing on the WhatsApp Business Platform](/docs/whatsapp/pricing) to learn more.

## June 24, 2025

*MM Lite API*

*Permissions*

The [ads\_read](/docs/permissions#a) permission is now optional for partners. This change impacts the [Intent API](/docs/whatsapp/marketing-messages-lite-api/for-solution-providers#-recommended--onboard-a-business-to-mm-lite-api-using-the-intent-api) and the [Embedded Signup](/docs/whatsapp/marketing-messages-lite-api/for-solution-providers#onboard-a-business-to-mm-lite-api-using-embedded-signup) onboarding flows. Prior to this change, partners had to apply for App Review to get advanced access for this new permission, regardless of whether or not their app intended to call the [Insights API](/docs/marketing-api/insights/) for conversion metrics. Now, partners only need to request advanced access for this permission via App Review if their app intends to use the Insights API.

*Automatic Creative Optimizations*

Added [text overlays](/docs/whatsapp/marketing-messages-lite-api/sending-messages#text-overlays) and [image animation](/docs/whatsapp/marketing-messages-lite-api/sending-messages#image-animation) Automatic Creative Optimizations. Like other optimizations, these are enabled by default on all templates, but can be disabled upon template creation, or when editing a template.

## June 20, 2025

*MM Lite API*

Businesses in Russia who were previously unable to send messages via MM Lite API can now do so. Note that these businesses will not have access to some advanced features, but can still take advantage of all other benefits, such as exclusive [marketing features](/docs/whatsapp/marketing-messages-lite-api). For more details, see [Geographic availability of features](/docs/whatsapp/marketing-messages-lite-api/get-started#russia).

## June 10, 2025

*MM Lite API*

Added two new Insights API fields so you can [get read rate and click rate benchmarks via API](/docs/whatsapp/marketing-messages-lite-api/viewing-metrics/#benchmark-metrics) instead of only via WhatsApp Manager:

* `marketing_messages_read_rate_benchmark`
* `marketing_messages_click_rate_benchmark`

## May 23, 2025

*MM Lite API*

Added [Android deep link](/docs/whatsapp/marketing-messages-lite-api/guides/deep-links) support.

## May 21, 2025

*MM Lite API*

Added an [Error messages](/docs/whatsapp/marketing-messages-lite-api/viewing-metrics#error-metrics) section to WhatsApp Manager that shows a summary of errors encountered by your templates within a given period of time.

## May 20, 2025

*MM Lite API*

Added [new error codes](/docs/whatsapp/marketing-messages-lite-api/support#error-codes) to help diagnose messaging errors. These will be available with Graph API version 23.0.

* `134100`
* `134101`
* `134102`
* `134103`

## April 16, 2025

*MM Lite API*

*Limited access available for [tracking click events](https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/guides/tracking-click-events/).*

We are offering a limited roll-out of webhook access to click events on marketing messages sent using MM Lite. [Read the "Tracking click events" page for more information](https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/guides/tracking-click-events/)

### April 11, 2025

*MM Lite API*

*Early access to Automated Creative Optimizations*

We are piloting a new optimization capability exclusive to MM Lite API (not available on Cloud API), which automatically enhances the visual appeal and engagement of marketing messages. Similarly to Advantage+ creative, this capability tests minor variations of your existing image header with different crop orientations or color filters, and automatically selects the variant which is getting the highest click-through rate over time with no input needed from you.

A small group of businesses will be getting early access to this feature starting May 5, with the ability to opt Templates out via the message template API. For more details, see [Automated Creative Optimizations](/docs/whatsapp/marketing-messages-lite-api/sending-messages#automatic-creative-optimizations).

Please reach out to your partner, if you would like to be included in early access to this feature.

## April 1, 2025

*MM Lite API*

*MM lite is now in Open Beta*

With this update, MM lite has:

* **Self-signup for all partners and businesses**. All businesses and solution providers (including Solution Partners, Tech Providers and Tech Partners) can now use self-serve onboarding flows to onboard to MM Lite API. See documentation on [Onboarding](/docs/whatsapp/marketing-messages-lite-api/onboarding) for more details.
* **Global availability**. MM Lite API is now available in all regions where Cloud API is also available. Note that while the API is available, some geographic variation of features may apply, [see details here](/docs/whatsapp/marketing-messages-lite-api/get-started#geographic-availability-of-features).

## March 27, 2025

*MM Lite API*

*Updates to character and emoji limits in Templates*

This update applies across all Templates on the Business Messaging API, and is not specific to MM Lite API (also applies on Cloud API).

As part of our ongoing efforts to improve the performance and user experience of our messaging platform, we are introducing changes to the body component of marketing templates via Cloud API and MM Lite API. These changes will impact the character limits and emoji usage in the body component, depending on the format and tag of the template.

**Key Updates**:

* Character limits for the body component will vary based on the template format and tag
* The number of emojis allowed in the body component may also be limited.

These updates are designed to enhance the performance and user experience of our messaging platform. While these changes may require some adjustments to your template creation process, they can ultimately lead to better performance and engagement with your customers.

## Dec 1, 2024

*MM Lite API*

*USA availability, and checking MM Lite eligibility via API*

Businesses in the USA are now eligible to use the MM Lite API.

In addition, a new MM Lite enrolment parameter allows businesses and partners to programmatically check MM Lite eligibility. See API docs for details.

## November 18, 2024

*MM Lite API*

*Reduced sync and async latency*

MM Lite team has quickly responded to feedback on async or delivery latency. This is defined as the time between an API call being received by MM Lite API, and MM Lite API dispatching a delivered webhook, assuming a user is online when the message is sent.

MM Lite previously had a p99 async delivery time of 12s, vs. p99 of 5s on Cloud API. This time has now been reduced to 9s. No action is required on a business or partners part.

## November 15, 2024

*MM Lite API*

*New easier onboarding flow, for partner-managed businesses*

MM Lite is rolling out a new way for partners to guide a business through signing the MM Lite Terms of Service and moving to MM Lite.

In parallel with the Embedded Signup flow already available, a partner will also alternatively be able to initiate the following flow:

1. Call an Intent API endpoint to indicate a BMID the partner wishes to assist in migrating to MM Lite. (If a BMID contains any OBO WABAs, these must be migrated to shared prior to this event).
2. Admins of that BMID will receive a notification that they have been invited to start sending marketing messages with optimizations via MM Lite. This notification is in Business Manager and via email.
3. Once accepted, and MM Lite setup and Ad account syncing is complete, a webhook will be triggered to the partner and all subscribers indicating that MM Lite onboarding is complete, and including the linked Ad IDs.
4. The partner may now call the send endpoint of MM Lite on this business behalf, and call an API to fetch an updated token with permission to access the business Ad account metrics.

See API docs for details on this new onboarding flow.

## November 8, 2024

*MM Lite API*

*App Conversion reporting now supported*

Businesses can now use MM Lite API to measure when marketing messages lead users to perform app events, such as purchases, searches, or achieving levels in games. See Integrate with App Conversions for details.

## November 1, 2024

*MM Lite API*

*Metrics in WhatsApp Manager*

To represent this new conversation type, MM Lite API conversations are available in every surface where reporting is offered:

1. Ads Manager UI [recommended]
2. Marketing API Insights API [recommended]
3. WhatsApp Manager UI WABA Insights page and Template Insights page
4. Business Management API
5. Pricing webhooks

For full details on how to see MM Lite API metrics via API and in pricing webhooks, consult the MM Lite API docs.

* In the Marketing API Insights API response, MM Lite events can be return using fields named `marketing_messages_[event]`
* In the Business Management API Template Analytics endpoint, MM Lite events can be returned using the query parameter `MARKETING_MESSAGES_LITE_API`
* In the Business Management API Conversation Analytics endpoints, MM Lite events can be returned using the `product_type` query parameter `MARKETING\_LITE
* In message status webhooks, the `conversation:origin:type` and `pricing:category` fields will show as `marketing_lite`

Businesses can now see MM Lite metrics as Marketing - lite in the WhatsApp Manager UI:

We recommend you integrate with the Marketing API Insights API for MM Lite Metrics, and encourage end businesses to log into Ads Manager UI to see their metrics, instead of using the WhatsApp business surface. Ads Mgr UI and Insights API show conversion metrics that are not available on WhatsApp surfaces, and will continue to support new metrics and features as the primary surface for MM Lite API reporting as the API grows.

API docs for partners have been updated to reflect how to fetch MM Lite metrics via API.

API docs have been updated to reflect how to fetch MM Lite metrics via API, see [Viewing metrics](/docs/whatsapp/marketing-messages-lite-api/viewing-metrics).

## October 30, 2024

*MM Lite API*

*Exclusive feature: TTLs for Marketing messages*

We continue to invest to improve consumer experiences and business outcomes. We are introducing customizable message validity periods (time-to-live or TTL) for marketing messages on MM Lite API, to ensure marketing messages are always timely and relevant for users thus performant for businesses. We are also updating our customizable range for TTL for utility and authentication templates, to provide businesses more control and flexibility.

* Marketing: From 12 hours to 30 days, for businesses on MM Lite API
* Utility: From 30 seconds to 12 hours, for businesses on Cloud API
* Authentication: From 30 seconds to 15 minutes, for businesses on Cloud API or On-Premises API

Businesses can customize the TTL of marketing, utility and authentication templates during template creation via WhatsApp Manager (via pre-set increments) and via API (in 1-second increments). This is reflected in our [dev docs](/docs/whatsapp/business-management-api/message-templates#time-to-live--customization-and-defaults) and [Business Help Center](https://www.facebook.com/business/help/1305007343713790).

## October 15, 2024

*MM Lite API*

*New rate cards and pricing category for MM Lite*

Marketing message conversations initiated via MM Lite API are counted and billed separately from Marketing message conversations initiated via Cloud API. This includes updates to pricing webhooks. For details, please see [Pricing](/docs/whatsapp/marketing-messages-lite-api/mm-lite-api-pricing).

## June 25, 2024

*MM Lite API*

*Show MM Lite metrics on the Template Analytics API*

MM Lite metrics are now available from the Template Analytics API endpoint. See documentation for details.
