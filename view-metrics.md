![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fviewing-metrics%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Viewing metrics](/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics)

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

[Viewing metrics](#viewing-metrics)

[View metrics via UIs](#view-metrics-via-uis)

[Benchmarks and recommendations metrics](#benchmarks-and-recommendations-metrics)

[Calculating benchmarks](#calculating-benchmarks)

[Understanding your ranking and how to use benchmark metrics](#understanding-your-ranking-and-how-to-use-benchmark-metrics)

[Error metrics](#error-metrics)

[View metrics via APIs](#view-metrics-via-apis)

[Benchmark metrics](#benchmark-metrics)

[Measuring ROI with the Marketing API “Insights API” endpoint (richer analytics, recommended)](#measuring-roi-with-the-marketing-api--insights-api--endpoint--richer-analytics--recommended-)

[Example Request](#example-request)

[Example Response](#example-response)

[Measuring ROI with the WhatsApp Business Management API “Template Analytics” endpoint (basic analytics)](#measuring-roi-with-the-whatsapp-business-management-api--template-analytics--endpoint--basic-analytics-)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

Conversion metrics will be solely available in the WhatsApp Manager UI and WhatsApp Business Management API that businesses use with Cloud API in October 2025.

As a result, the following conversion metrics will be depreciated:

* Viewing conversion metrics via Ads Manager UI (**September 8th, 2025**).
* Viewing conversion metrics via Ads Insights API (**Q1 2026**).

# Viewing metrics

Businesses that use Marketing Messages API for WhatsApp can view metrics from 4 surfaces:

* Via WhatsApp Business Platform surfaces
* WhatsApp Manager UI
* [WhatsApp Business Management API](https://developers.facebook.com/docs/whatsapp/business-management-api)
* Via Ads surfaces (optional)
* Ads Manager UI “Marketing Messages" tab
* Marketing API “[Insights API](https://developers.facebook.com/docs/marketing-api/insights/)”

| ROI Reporting | WhatsApp Business Management surfaces | Ads surfaces |
| --- | --- | --- |
| Messages sent, delivered, read | Y | Y |
| Total amount spent | Y | Y |
| Cost per delivery | Y | Y |
| CTA URL link clicks | Y | Y |
| Cost per click | Y | Y |
| CTA URL link click rate | N | Y |
| Add to cart (Web + App) | Y | Y`*` |
| Checkout initiated (Web + App) | Y | Y`*` |
| Purchase, purchase value (Web + App) | Y | Y`*` |
| App Activations | Y | Y`*` |
| Quick Replies | N | N |

`*` Requires a business to report this conversion event via Meta Pixel or Conversions API for App Events [see Get started with the Meta Pixel and Conversions API](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.facebookblueprint.com%2Fstudent%2Factivity%2F212737&h=AT1b3FZtp5jpm_SEJidscXlNBcuHnvy0xzq-FP6LzqI4J-7ZwX8jeAcqOc2Z3R297K33JUWl8wXugHV3r3-ulYMV-HAQUY6A67PE87RrxFEieAOL4TFltqGdGxL1KDuf2wmlCitEzYdx4nLqWaOoPA).

## View metrics via UIs

After sending Marketing Messages via Marketing Messages API for WhatsApp, view read-only metrics on sends, clicks, and conversions from two UIs:

1. WhatsApp Manager (does not include conversions)
2. Ads Manager “Marketing Messages” tab (includes conversions)

Marketing Messages API for WhatsApp metrics (not including conversions), can be viewed in WhatsApp Manager on both Phone Number and Template screens:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/476092006_1150702876444748_6174975982108219980_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=6_JLqepfbg4Q7kNvwEDW7-G&_nc_oc=Adm7PijPKdXLTnmyLZaIaAkgwYDfjXIxlNSyrMjq8-uQGY1a2d9rg1hi_pAOyVpylk4&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=d2gHLky6_rON9n_zbDmoKA&oh=00_Afgr2E3FxIM1WiyKeLANdsKrx3JWxFUCAekWqBrkKQ0IhA&oe=694042EC)

### Benchmarks and recommendations metrics

Benchmark metrics provide insights into how your business is performing compared to similar businesses in your industry. These metrics are based on data from the past 30 days and take into account various factors that define similar businesses. Based on the benchmark metrics, we provide personalized recommendations to help you improve your template's performance. If your template's read rate or click rate falls below the benchmark, we provide suggestions to boost engagement.

### Calculating benchmarks

To calculate benchmark metrics, we consider the following characteristics:

* **Business Country or Region**: We use the business country as the default cohort, but if the cohort size is too small, we switch to the business region.
* **Business Industry**: We compare your business with others in the same industry or vertical to provide relevant benchmarks.
* **Template Categories**: We only compare templates within the same category (e.g., marketing templates with other marketing templates) to ensure accurate and relevant benchmarks.

We then calculate two key benchmark metrics:

* **Read Rate Benchmark**: We calculate this metric as the 75th percentile of read rates across similar businesses, representing the percentage of messages read out of total messages delivered.
* **Click Rate Benchmark**: We calculate this metric as the 75th percentile of click rates across similar businesses, representing the percentage of link clicks out of total messages delivered.

### Understanding your ranking and how to use benchmark metrics

When you view your benchmark metrics, you will see a ranking that indicates how your template performs compared to templates in the same category. This ranking is calculated by comparing your template's performance with the read rate or click rate performance of peer templates with high engagement over the past 30 days.

Use the benchmark metrics to compare your template's performance to templates from similar businesses over the past 30 days. Benchmarks are calculated daily, with a delay of up to 2 days. This ensures that you have access to updated and relevant data to inform your business decisions.

To access the benchmark and recommendations metrics:

1. Go to the WhatsApp Manager and select "Manage templates".
2. Choose the template you want to view.
3. Select the "Marketing Messages API for WhatsApp" option from the dropdown menu highlighted in red.
4. The benchmark metrics and recommendation cards will be displayed below the preview card in the left panel.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/489606125_1614641949479830_5793009593844219233_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=HO3bHgkfWp0Q7kNvwGIInwq&_nc_oc=AdlFHNOhb4ENqRP8YmUlN8vLCH7iV81x4Yr4CjbrSrj91H2oMu00VxziIr0RIc_QOxk&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=d2gHLky6_rON9n_zbDmoKA&oh=00_AfisA--Z4PemEPtaoXh6zjtcrKZZfRKnbSALVWxJi_qqOw&oe=694065CB)

### Error metrics

You can see a summary of error messages your template encountered within a given period of time by navigating to the [**WhatsApp Manager**](https://business.facebook.com/latest/whatsapp_manager/) > **Message templates** > **Manage templates** panel and clicking on the template. Errors are displayed in the **Error messages** section.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/494916197_1372780987177522_8462538949406730249_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=lCxB7hCoyrwQ7kNvwG0GRCv&_nc_oc=AdlTV93-whrghi93xz9PgQjXtM3SpEAYYVV9mhKJjWvpIHECggW3YqfU73UXNYACMps&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=d2gHLky6_rON9n_zbDmoKA&oh=00_Afhwn4bFREi2GLjFu0TXr4QGg0M1eygblRph8eEXtU-ixg&oe=69404963)

The period of time can be defined using the date selector dropdown at the top of the page. See [Cloud API error codes](/docs/whatsapp/cloud-api/support/error-codes/) for a list of error codes and their descriptions.

The most frequently encountered message delivery errors are displayed in the **Summary** tab:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/494939750_1018419840401159_1265335467156200602_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=kFy5P38vFyYQ7kNvwFPCIEA&_nc_oc=AdldnCHu2Izb9ytVPjMuhI5Z3TwcCuSNrX_2YQda3rSAwBZS1dEE7j7iDBZ_e9asiGo&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=d2gHLky6_rON9n_zbDmoKA&oh=00_AfgmrtSEN8fuHdxre7PVzA0SqHOHYaAbDkgNbe6-jB5zjg&oe=69405FD6)

This information is also displayed as trend lines in the **Trend** tab:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/495675967_1251270636408181_5159031297095990508_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=GUph-ku6udYQ7kNvwGRuiXB&_nc_oc=AdmFeeCOgV5aX0-GRt2F4gdYGY0L9F0yyJ9Qjn3IrqFP5cCG64x3EC7kv7u6ib2x1CI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=d2gHLky6_rON9n_zbDmoKA&oh=00_AfgXj5mDKtTdQeKDNpGoaiWC8ZotG1bZX-v_4C_KxsehSQ&oe=69405268)

## View metrics via APIs

After registering in Marketing Messages API for WhatsApp, analytics for a business's marketing message templates sent via the API are available from two APIs:

1. The WhatsApp Business Management API (does not include conversions)
2. The Marketing API “Insights API” (includes conversions)

### Benchmark metrics

You can get benchmark metrics via Insights API for read rates and click rates by requesting the following fields:

* `marketing_messages_read_rate_benchmark`
* `marketing_messages_click_rate_benchmark`

#### Syntax

```
curl
'https://graph.facebook.com/<API_VERSION>/<AD_GROUP_ID>/insights?fields=<METRICS>' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

#### Example query

This example query returns the number of messages read, their read rate, and the benchmark read rate for comparison, as well as the number of button link clicks, their click rate, and the benchmark click rate for comparison, with a default lookback of 30 days:

```
    curl 'https://graph.facebook.com/v17.0/120229306178900226/insights?fields=marketing_messages_read,marketing_messages_read_rate,marketing_messages_read_rate_benchmark,marketing_messages_link_btn_click,marketing_messages_link_btn_click_rate,marketing_messages_click_rate_benchmark' \
    -H 'Authorization: Bearer EAACE...'
```

#### Example response

```
    {
      "data": [
        {
          "date_start": "2025-05-11",
          "date_stop": "2025-06-09",
          "marketing_messages_read": "265",
          "marketing_messages_read_rate": "481.818182",
          "marketing_messages_read_rate_benchmark": "70.27",
          "marketing_messages_link_btn_click": "59",
          "marketing_messages_link_btn_click_rate": "107.272727",
          "marketing_messages_click_rate_benchmark": "18.74"
        }
      ],
      "paging": {
        "cursors": {
          "after": "MAZDZD",
          "before": "MAZDZD"
        }
      }
    }
```

### Measuring ROI with the Marketing API “Insights API” endpoint (richer analytics, recommended)

Businesses can use the [Meta Pixel](https://www.facebook.com/business/tools/meta-pixel) and [Conversions API for App Events](https://developers.facebook.com/docs/marketing-api/conversions-api/app-events) to send signals to Meta when customers take an action on their website or app, after clicking a URL in a marketing message. Note that in-thread conversion optimizations and reporting are not yet available for Marketing Messages API for WhatsApp.

The [Insights API](https://developers.facebook.com/docs/marketing-api/insights/) is an interface to retrieve ads statistics, allowing a business to view all of the metrics of the Template Analytics plus additional metrics on when marketing messages sent via Marketing Messages API for WhatsApp led to an event reported from their website via Meta Pixel or Conversions API, like a user adding to cart or checking out. **It is required that the business that owns the Pixel is the same business that owns the WABA.**

#### Step 1) Fetch Ad IDs for Templates, using the Templates endpoint

When a business has registered for Marketing Messages API for WhatsApp, a read-only Ad account will be created for each WABA under their BMID, and any marketing message templates under the WABA will be linked to an Ad object in that Ad account. Each marketing message template under the WABA will also be linked to an Ad set. These IDs are needed when calling the Insights API to retrieve metrics on marketing campaigns sent via Marketing Messages API for WhatsApp.

Once a business has registered for the Marketing Messages API for WhatsApp, the Business Management API’s Template endpoint will return an additional parameter reflecting their Ad IDs.

* `ad_id`
* `ad_account_id`
* `ad_campaign_id`
* `ad_adset_id`

These fields indicate the Ad id of linked Ads object for each marketing message template.

Call the Template endpoint to retrieve the Ad IDs for each ad entity linked to marketing message templates, for calling the Insights API later.

| Endpoint | Authentication |
| --- | --- |
| `/WHATSAPP_BUSINESS_ACCOUNT_ID/message_templates` | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.  Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_messaging` permission. |

Request Syntax

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates
  ?fields=category,ad_id,ad_adset_id,ad_campaign_id,ad_account_id
```

See docs: [GET Message Templates](https://developers.facebook.com/docs/whatsapp/business-management-api/message-templates/#retrieve-templates)

If you only want to fetch 1 Template at a time, you can fetch the Ad ID fields at a Template level.

| Endpoint | Authentication |
| --- | --- |
| `/<TEMPLATE_ID>/` | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.  Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_management` permission. |

Request Syntax

```
GET /<TEMPLATE_ID>
  ?fields=category,ad_id,ad_adset_id,ad_campaign_id,ad_account_id
```

See docs: [GET Templates](https://developers.intern.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/template-api#fields)

#### Step 2) Call the Insights API using the Ad IDs

Direct integrators or business messaging partners retrieve these read-only campaign objects through the existing Insights API endpoints:

| Endpoint | Authentication |
| --- | --- |
| `/AD_CAMPAIGN_ID/insights` | Partners must authenticate themselves with an access token with the `ads_read` permission. |

Get the specified metrics for at an ad object level (i.e., ad account, campaign, ad set, or ad id) given its ID:

### Example Request

```
curl --verbose -s -G -d "access_token=${ACCESS_TOKEN}" https://graph.facebook.com/v19.0/${AD_ACCOUNT_ID|CAMPAIGN_ID|AD_SET_ID|AD_ID}/insights?fields=marketing_messages_sent%2Cmarketing_messages_read"
```

### Example Response

```
{
  "data": [
    {
      "marketing_messages_sent": "2",
      "marketing_messages_read": "1",
      "date_start": "2023-09-24",
      "date_stop": "2023-10-23"
    }
  ],
  "paging": {
    "cursors": {
      "before": "MAZDZD",
      "after": "MAZDZD"
    }
  }
}
```

This is only an example. For all available params of the API see the full doc: [Insights API docs](https://developers.facebook.com/docs/marketing-api/insights/)

All available insights fields are listed below:

* Sent, Read, Delivered, Click
* marketing\_messages\_sent
* marketing\_messages\_read
* marketing\_messages\_delivered
* marketing\_messages\_link\_btn\_click
* Rates
* marketing\_messages\_delivery\_rate
* marketing\_messages\_read\_rate
* marketing\_messages\_link\_btn\_click\_rate
* Spend metrics
* marketing\_messages\_spend
* marketing\_messages\_cost\_per\_delivered
* marketing\_messages\_cost\_per\_link\_btn\_click
* Conversion events
* marketing\_messages\_website\_add\_to\_cart
* marketing\_messages\_website\_initiate\_checkout
* marketing\_messages\_website\_purchase
* marketing\_messages\_website\_purchase\_values
* marketing\_messages\_app\_add\_to\_cart
* marketing\_messages\_app\_initiate\_checkout
* marketing\_messages\_app\_purchase
* marketing\_messages\_app\_purchase\_values

### Measuring ROI with the WhatsApp Business Management API “Template Analytics” endpoint (basic analytics)

The [Template Analytics](https://developers.facebook.com/docs/whatsapp/business-management-api/analytics#template-analytics) endpoint of the WhatsApp Business Management API offers the ability to view metrics including: Sent, Delivered, Read, Clicked, and Cost.

In order to fetch metrics for messages sent via Marketing Messages API for WhatsApp, attach the new parameter “product\_type” with the value below. If omitted, only analytics for Cloud API will be returned.

| Endpoint | Authentication |
| --- | --- |
| `/WHATSAPP_BUSINESS_ACCOUNT_ID/conversation_analytics`  Use the query parameter `conversation_categories` = `MARKETING_MESSAGES` to include data from the Marketing Messages API for WhatsApp.  If omitted, the API will return results for all conversation categories. | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.  Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_management` permission. |

Request Syntax

```
GET /WHATSAPP_BUSINESS_ACCOUNT_ID/?fields=conversation_analytics.start(<START_TIMESTAMP>).end(<END_TIMESTAMP>).granularity(DAILY).conversation_categories(MARKETING_LITE).dimensions(["CONVERSATION_CATEGORY"])
```

See docs: [GET Conversation Analytics](https://developers.facebook.com/docs/whatsapp/business-management-api/analytics#conversation-analytics)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Viewing metrics](#viewing-metrics)

[View metrics via UIs](#view-metrics-via-uis)

[Benchmarks and recommendations metrics](#benchmarks-and-recommendations-metrics)

[Calculating benchmarks](#calculating-benchmarks)

[Understanding your ranking and how to use benchmark metrics](#understanding-your-ranking-and-how-to-use-benchmark-metrics)

[Error metrics](#error-metrics)

[View metrics via APIs](#view-metrics-via-apis)

[Benchmark metrics](#benchmark-metrics)

[Measuring ROI with the Marketing API “Insights API” endpoint (richer analytics, recommended)](#measuring-roi-with-the-marketing-api--insights-api--endpoint--richer-analytics--recommended-)

[Example Request](#example-request)

[Example Response](#example-response)

[Measuring ROI with the WhatsApp Business Management API “Template Analytics” endpoint (basic analytics)](#measuring-roi-with-the-whatsapp-business-management-api--template-analytics--endpoint--basic-analytics-)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4q0GMzgTHWF0gMis9soykA&oh=00_AfhV0ca4FTV7-VVwE3KDZZoX_qR89K5-tvmUuH2spdNkdQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4q0GMzgTHWF0gMis9soykA&oh=00_AfizRzrwd_oY_7_velIOj8i3it290PGgz282M_YA6BqQ_Q&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4q0GMzgTHWF0gMis9soykA&oh=00_AfiZxJROVqHbSbXa6dmHPBSHpR9wv-EykhUIpFPiad3AaQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4q0GMzgTHWF0gMis9soykA&oh=00_Afib_yJF6wGxQz6mCh2-lFu4w4Yo_TvzmUQ7pKDNJsTaQg&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=4q0GMzgTHWF0gMis9soykA&oh=00_AfgeorNVSKbS_z5MtLlzcoFC6_7Rz7evQ8gGt6ru8j2HAA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1H3267NroCEJQVJQu09uV30juBAMhokDZQrdGjrvx3JznAwvTiRBs50C3KX0afVNOEgOcTxZ9NZzKlrG28H0_imuWRBJeOjBuGrnoIq9MZq8ErRqkJM8ppQRukF2rvgbSKm6hm4NUoOZm-FBA_WA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)