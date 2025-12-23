+++
id = "messaging-limits"
title = "Messaging Limits"
summary = "This document describes messaging limits for the WhatsApp Business Platform."
source = "https://developers.facebook.com/docs/whatsapp/messaging-limits"
lang = "en"
tags = ["whatsapp-business-platform", "messaging", "rate-limits"]
+++
# Messaging Limits

This document describes messaging limits for the WhatsApp Business Platform.

Messaging limits are the maximum number of unique WhatsApp user phone numbers your business can deliver messages to, outside of a [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows), within a moving 24-hour period.

Messaging limits are calculated and set at the business portfolio level and are shared by all business phone numbers within a portfolio. This means that if a business portfolio has multiple business phone numbers, it's possible for one number to consume all of the portfolio's messaging capability within a given period.

Newly created business portfolios have a messaging limit of 250, but this limit can be increased to:

* 2,000 (by completing a [scaling path](#scaling-paths))
* 10,000 (via [automatic scaling](#automatic-scaling))
* 100,000 (via automatic scaling)
* Unlimited (via automatic scaling)

## Increasing your limit

You can increase your messaging limit to 2,000 by completing one of the [scaling paths](#scaling-paths) below. After that, we will automatically increase your limit to the next higher limit if you meet our [automatic scaling criteria](#automatic-scaling).

### Scaling paths

* [Verify your business](https://www.facebook.com/business/help/2058515294227817)
* Have your [solution provider verify your business](/docs/whatsapp/solution-providers/partner-led-business-verification) (if you were onboarded by one)
* Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality).

Once you complete one of these paths, we will analyze your [message quality](/docs/whatsapp/cloud-api/guides/send-messages#message-quality). Based on this analysis, your number's eligibility for automatic scaling will either be approved or denied.

### Approvals

If your request is approved, we will immediately increase your business phone number's messaging limit to 2,000 and notify you by email and developer alert. In addition, a [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update) webhook will be triggered with `max_daily_conversations_per_business` (for webhooks v24.0 and newer) and `max_daily_conversation_per_phone` (for v23.0 and older, until February, 2026) set to the new limit.

Additional messaging limit increases for your number can now happen automatically, via [automatic scaling](#automatic-scaling).

### Denials

If your request is denied, we will maintain your business phone number's messaging limit at its current level and notify you via email and developer alert. In addition, an [account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts) webhook will be triggered, with the `alert_type` and `alert_description` properties indicating alternate methods you can pursue to increase your limit.

| `alert_type` Value | Action you can take |
| --- | --- |
| `INCREASED_CAPABILITIES_ELIGIBILITY_DEFERRED` | Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers in a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |
| `INCREASED_CAPABILITIES_ELIGIBILITY_FAILED` | Send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |
| `INCREASED_CAPABILITIES_ELIGIBILITY_NEED_MORE_INFO` | [Verify your identity](https://www.facebook.com/business/help/587323819101032), or send 2,000 delivered messages outside of customer service windows to unique WhatsApp user phone numbers within a 30-day moving period, using templates with a high [quality rating](/docs/whatsapp/business-management-api/message-templates/template-quality). |

## Automatic scaling

Once your business portfolio's messaging limit has been increased to 2,000, we will determine if it should be increased further according to the following criteria:

* You are sending [high-quality messages](/docs/whatsapp/cloud-api/guides/send-messages#message-quality) across all of your business phone numbers and templates
* In the last 7 days, your business has utilized at least half of your current messaging limit

If these criteria are met, we will increase your portfolio's limit by one level within 6 hours.

## Checking your limit

### Via Meta Business Suite

Your business phone number's current messaging limit is displayed in the [WhatsApp Manager](https://business.facebook.com/wa/manage/home/) > **Account tools** > **Messaging limits** panel:

### Via API

Use the [GET /<BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) endpoint and request the `whatsapp_business_manager_messaging_limit` field (for v24.0 and newer) or `messaging_limit_tier` field (for 23.0 and older) to get a business phone number's current messaging limit.

#### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922?fields=whatsapp_business_manager_messaging_limit' \
-H 'Authorization: Bearer EAAJB...'
```

#### Example response

```
{
  "whatsapp_business_manager_messaging_limit": "TIER_250",
  "id": "106540352242922"
}
```
