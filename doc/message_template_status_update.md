+++
id = "message_template_status_update"
title = "Monitor Quality Signals"
summary = "It is important to build and maintain a high quality customer experience on WhatsApp, so that customers can keep using this channel to communicate with your business."
source = "https://developers.facebook.com/docs/whatsapp/message_template_status_update"
lang = "en"
tags = ["whatsapp-business-platform", "business-management-api", "webhooks", "messaging", "templates", "phone-numbers"]
+++
# Monitor Quality Signals

It is important to build and maintain a high quality customer experience on WhatsApp, so that customers can keep using this channel to communicate with your business.
To protect our users, WhatsApp has a reporting and blocking mechanism. If a user doesn't like the experience they get, they might block or report your business number.

A block or report action against your business keeps you from contacting those users and impacts your phone number reach and the template availability. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs and [Message Template Guidelines](/docs/whatsapp/message-templates/guidelines) docs.

To help you keep a high quality experience for your customers, we recommend that you **monitor the quality signals** (via WhatsApp Business Management API and WhatsApp Manager UI) to assess how your messages are being received by users and act on relevant updates as quickly as possible.

## Monitor Quality Signals Programmatically

We recommend using [webhooks](/docs/whatsapp/business-management-api/webhooks) to monitor phone number and message template quality. Then, you can act whenever there is a need, like when quality is Low or status is Flagged.

If the information you need is still not available via webhooks, you can alternatively call the [WhatsApp Business Management API](/docs/whatsapp/business-management-api).

The following webhooks and APIs provide real-time information and updates. For now, they don't provide historical data check the next section of this document to learn how to use the WhatsApp Manager UI to get the last 30 days quality ratings.

### Phone Numbers

#### [Webhooks](/docs/whatsapp/business-management-api/webhooks)

To get notified when a phone number quality status changes, subscribe to the `phone_number_quality_update` webhook. You must subscribe to each WhatsApp Business Account you'd like to get the updates.

**What to watch for:** the **Flagged** status in WhatsApp Manager, or a `phone_number_quality_update` webhook with `EVENT` set to `FLAGGED`. Flagged status occurs when the quality rating reaches a low state. If the message quality improves to a high or medium state and maintains this for 7 days, your business phone number status will return to **Connected** in WhatsApp Manager, and its [`status` field](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#fields) will be set to `CONNECTED`. If the quality rating doesn't improve within 7 days, however, it will still return to a connected status, but its messaging limit will be downgraded. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs.

#### [API](/docs/whatsapp/business-management-api/phone-numbers)

Make [this call](https://developers.facebook.com/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers) once in a while to follow your phone numbers quality rating:

```
curl -X GET \
'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>/phone_numbers?access_token=<ACCESS_TOKEN>'
```

Be mindful these calls will count against the [API limits](/docs/whatsapp/business-management-api/using-the-api#api-limits), while the webhooks will not.

**What to watch for:** Any quality ratings different than **High**. They indicate negative feedback from users and may impact the phone number reach. Learn more on [Phone Number Quality](https://www.facebook.com/business/help/896873687365001) docs.

### Message Templates

#### [Webhooks](/docs/whatsapp/business-management-api/webhooks)

Subscribe to the `message_template_status_update` webhook to get notified when the message template status changes, by being approved or rejected, or if it has been disabled. You must subscribe to each WhatsApp Business Account you'd like to get the updates.

## Check Quality Signals on the UI

On **Business Manager**, go to the **WhatsApp Manager** and look for the following tabs:

### Phone Numbers Tab

* Check the current phone number quality rating column. Mouse over to see the reason users gave for their negative feedback, if available.

* Go to Insights and check the quality for the last 30 days.

### Message Templates tab

* Check the current message template quality rating column:

## Implement Internal Trackers

We also recommend you to implement your own internal trackers on the chat thread. This way, once you receive a signal on webhooks that indicates negative feedback from users or low read-rates (quality rating = medium or low, status = Flagged), you can investigate your own trackers to try to understand where you can improve the chat experience.

As an example, these are a two places you can add internal trackers to:

#### Response time

Monitor how much time it takes for you to answer client messages. Ideally this should be instant, so watch out for increases and peaks. Important metrics: first message response time and average response time.

#### Customer messaging journey steps

Check if users are getting through the entire messaging journey you planned.

A few questions to help you analyze metrics:

* Are users dropping on an unexpected step?
* Is there a specific message that is causing confusion?
* Are users getting looped in a sequence of steps?
* Are users completing the final action you want them to perform?

With this measurement in place you can run A/B testing and see if changes in the experience improves user feedback. Some things you could try to test if it improves the experience:

* Change the phrasing
* Split the question into more questions,
* Aggregating multiple questions into one

After the test, analyze the new metrics and compare them to the old ones.
