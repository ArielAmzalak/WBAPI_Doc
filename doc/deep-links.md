+++
id = "deep-links"
title = "Deep links"
summary = "You can map an Android deep link to a marketing template URL button that, when tapped, loads a particular location or content within your app."
source = "https://developers.facebook.com/docs/whatsapp/deep-links"
lang = "en"
tags = ["whatsapp-business-platform", "templates", "analytics"]
+++
# Deep links

You can map an [Android deep link](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.android.com%2Ftraining%2Fapp-links%2Fdeep-linking&h=AT2-3kR54stc8EOnzWTsBnCI4agCcskoVTzyA4Ig1QxrTEqnjl-5IUpf0_uqgEpBPsWz_J0VfGPjLYt6o71ga1Y3ptr-zHQBFIi4oj31rl0FzZrnT5I9lCyAW7rp88g9ITHXy15o9K2hArWBPWzbSg) to a marketing template URL button that, when tapped, loads a particular location or content within your app.

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
