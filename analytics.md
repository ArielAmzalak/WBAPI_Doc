![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fanalytics%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)[Guides](/docs/whatsapp/business-management-api/guides)[Análise](/docs/whatsapp/business-management-api/analytics)

[API de Gerenciamento do WhatsApp Business](/docs/whatsapp/business-management-api)

* [Começar](/docs/whatsapp/business-management-api/get-started)
* [Access tokens](/docs/whatsapp/access-tokens)
* [Permissions](/docs/whatsapp/permissions)
* [Configuração de webhooks](/docs/whatsapp/business-management-api/guides/set-up-webhooks)
* [Guides](/docs/whatsapp/business-management-api/guides)

  + [Análise](/docs/whatsapp/business-management-api/analytics)
  + [Templates](/docs/whatsapp/business-management-api/guides/templates-stub)
  + [Recuperar números de telefone](/docs/whatsapp/business-management-api/manage-phone-numbers)
  + [Migrate numbers via Embedded Signup](/docs/whatsapp/business-management-api/guides/migrate-numbers-via-es-redirect)
  + [Migrate Numbers Programmatically](/docs/whatsapp/business-management-api/guides/migrating-phone-numbers-between-wabas-programmatically)
  + [QR codes](/docs/whatsapp/business-management-api/qr-codes)
  + [Monitorar sinais de qualidade](/docs/whatsapp/guides/how-to-monitor-quality-signals)
  + [Welcome Message Sequences](/docs/whatsapp/business-management-api/ads/welcome-message-sequences)
* [Referência](/docs/whatsapp/business-management-api/reference)
* [Error Codes](/docs/whatsapp/business-management-api/error-codes)

Nesta Página

[Analytics](#analytics)

[Get data](#get-data)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Messaging analytics](#messaging-analytics)

[Messaging analytics parameters](#messaging-analytics-parameters)

[Example](#example)

[Conversation analytics](#conversation-analytics)

[Conversation analytics parameters](#conversation-analytics-parameters)

[Examples](#examples)

[Pricing analytics](#pricing-analytics)

[Request syntax](#request-syntax-2)

[Pricing analytics parameters](#pricing-analytics-parameters)

[Volume tier information](#volume-tier-information)

[Example request](#example-request)

[Example response](#example-response)

[Template analytics](#template-analytics)

[Limitations](#limitations)

[Confirming template analytics](#confirming-template-analytics)

[Template analytics parameters](#template-analytics-parameters)

[Examples](#examples-2)

[Cost and click metrics](#cost-and-click-metrics)

[Disabling button click analytics](#disabling-button-click-analytics)

[Template group analytics](#template-group-analytics)

[Limitations](#limitations-2)

[Enabling template analytics](#enabling-template-analytics)

[Request syntax](#request-syntax-3)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Cost and click metrics](#cost-and-click-metrics-2)

[Reference](#reference)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/analytics/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 19 de nov
Atualização em Português (Brasil): 19 de nov

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

Starting December 1, 2025, the maximum lookback window for messaging, conversation, and pricing analytics is changing from 10 years to 1 year. The lookback window for template and template group analytics will be unaffected and will continue to be 90 days.

# Analytics

This document describes how to get messaging, conversation, and template analytics, such as the number of messages sent from a business phone number, the number of conversations and their costs for a WhatsApp Business Account (WABA), or the number of times a given template has been read.

Only metrics for business phone numbers and templates associated with your WABA at the time of the request will be included in responses.

## Get data

Use the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#Reading) endpoint to get analytics.

### Request syntax

```
curl -g 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_ACCOUNT_ID>?fields=<FIELD>.<FILTERS>' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<FIELD>` | **Required.**  Metric. Value can be one of:   * [`analytics`](#analytics-2) * [`conversation_analytics`](#conversation-analytics) * [`pricing_analytics`](#pricing-analytics) * [`template_analytics`](#template-analytics) * [`template_group_analytics`](#template-group-analytics) | `analytics` |
| `<FILTERS>` | **Required.**  Metric filtering parameter. Append additional filtering parameters using dots.  For possible values, see:   * [Messaging analytics parameters](#messaging-analytics-parameters) * [Conversation analytics parameters](#conversation-analytics-parameters) * [Template analytics parameters](#template-analytics-parameters) * [Template group analytics parameters](#template-group-analytics-parameters) | `.start(1543543200).end(1544148000).granularity(DAY)` |

## Messaging analytics

The `analytics` field provides the number and type of messages sent and delivered by the phone numbers associated with a specific WABA — for conversation metrics, see [Conversation Analytics](#conversation-analytics). When calling `/<WHATSAPP_BUSINESS_ACCOUNT_ID>?fields=analytics.{filtering-parameters}`, you can attach the following parameters.

### Messaging analytics parameters

| Name | Description |
| --- | --- |
| `start`  type: UNIX Timestamp | **Required.**  The start date for the date range for which you are retrieving analytics. |
| `end`  type: UNIX Timestamp | **Required.**  The end date for the date range for which you are retrieving analytics. |
| `granularity`  type: String | **Required.**  The granularity at which you would like to retrieve the analytics. Supported Options:   * `HALF_HOUR` * `DAY` * `MONTH` |
| `phone_numbers`  type: Array | **Optional.**  An array of phone numbers for which you would like to retrieve analytics. If not provided, all phone numbers added to your WABA are included. |
| `product_types`  type: Array | **Optional.**  The types of messages (notification messages and/or customer support messages) for which you want to retrieve notifications. Provide an array and include `0` for notification messages, and `2` for customer support messages. If not provided, analytics will be returned for all messages together. |
| `country_codes`  type: Array | **Optional.**  The countries for which you would like to retrieve analytics. Provide an array with 2 letter country codes for the countries you would like to include. If not provided, analytics will be returned for all countries you have communicated with. |

### Example

**Scenario:** You need to get the number of messages sent and delivered by all phone numbers associated with your WABA.

**Suggested Solution:** [Assemble the URL you want to call](#getting-the-data) and include the following filtering parameters: `start`, `end`, `granularity`. Then, make a `GET` request to that URL:

```
curl -i -X GET "https://graph.facebook.com/v24.0/102290129340398
      ?fields=analytics
      .start(1543543200)
      .end(1544148000)
      .granularity(DAY)
      &access_token=BLI8lkj..."
```

A successful response returns an `analytics` object with the data you have requested:

```
{
  "analytics": {
    "phone_numbers": [
      "16505550111",
      "16505550112",
      "16505550113"
    ],
    "country_codes": [
      "US",
      "BR"
    ],
    "granularity": "DAY",
    "data_points": [
      {
        "start": 1543543200,
        "end": 1543629600,
        "sent": 196093,
        "delivered": 179715
      },
      {
        "start": 1543629600,
        "end": 1543716000,
        "sent": 147649,
        "delivered": 139032
      },
      {
        "start": 1543716000,
        "end": 1543802400,
        "sent": 61988,
        "delivered": 58830
      },
      {
        "start": 1543802400,
        "end": 1543888800,
        "sent": 132465,
        "delivered": 124392
      }
      # more data points
    ]
  },
  "id": "102290129340398"
}
```

## Conversation analytics

The `conversation_analytics` field provides cost and [conversation](/docs/whatsapp/pricing#conversations) information for a specific WABA. When calling `/<WHATSAPP_BUSINESS_ACCOUNT_ID>?fields=conversation_analytics.{filtering-parameters}`, you can attach the following parameters.

### Conversation analytics parameters

| Name | Description *(Click the arrow in the left column for supported options.)* |
| --- | --- |
| `start`  type: UNIX Timestamp | **Required.**  The start date for the date range for which you are retrieving analytics. |
| `end`  type: UNIX Timestamp | **Required.**  The end date for the date range for which you are retrieving analytics. |
| `granularity`  type: String | **Required.**  The granularity at which you would like to retrieve the analytics. Supported Options:   * `HALF_HOUR` * `DAILY` * `MONTHLY` |
| `phone_numbers`  type: Array | **Optional.**  An array of phone numbers for which you would like to retrieve analytics. If not provided, all phone numbers added to your WABA are included. |
| `metric_types` | **Optional.**  List of metrics you would like to receive. If you send an empty list, we return results for all metric types. Supported Options: {#supported}   * `COST`: Includes approximate charges for that time range, in the WABA’s currency. * `CONVERSATION`: Includes the count of conversations for that time range.   **As of July 1, 2023, `COST` is no longer shown for businesses who bill through a Solution Partner.** To understand your charges, please reach out to your partner. If you bill through a partner, this is the behavior to expect:   1. If no `metric_types` are specified in your request, only `CONVERSATION` is returned 2. If only `CONVERSATION` is specified, only `CONVERSATION` is returned 3. If only COST is specified, the following exception is returned:    * Title: “Cost not available”    * Message: “Cost is no longer shown for businesses who bill through a partner (i.e., BSP). To understand your charges, please reach out to your partner.”   If you query a time period that includes dates on or after July 1, 2023, (for example, May 1, 2023 through August 1, 2023), the response will include the above exception.  ***There is no change for partners when querying the `conversation_analytics` endpoint.*** |
| `conversation_categories` | **Optional.**  List of [conversation categories](/docs/whatsapp/pricing#conversation-categories). If you send an empty list, we return results for all conversation categories. Supported Options:   * `AUTHENTICATION` * `MARKETING` * `SERVICE` * `UTILITY` |
| `conversation_types` | **Optional.**  List of conversation types. If you send an empty list, we return results for all conversation types. Supported Options:   * `FREE_ENTRY`: Conversations originating from a [free entry point](/docs/whatsapp/pricing#free-entry-point-windows). * `FREE_TIER`: Conversations within the monthly [free tier](/docs/whatsapp/pricing#free-entry-point-windows). * `REGULAR`: Any conversations that did not originate from a [free entry point](/docs/whatsapp/pricing#free-entry-point-windows) or are above the monthly free tier allotment. |
| `conversation_directions` | **Optional.**  List of conversation directions. If you send an empty list, we return results for all conversation directions. Supported Options:   * `BUSINESS_INITIATED`: Conversations initiated by the business. * `USER_INITIATED`: Conversations initiated by an end user/customer. * `UNKNOWN`: System cannot determine direction. |
| `dimensions` | **Optional.**  List of breakdowns you would like to apply to your metrics. If you send an empty list, we return results without any breakdowns. Supported Options:   * `CONVERSATION_CATEGORY` * `CONVERSATION_DIRECTION` * `CONVERSATION_TYPE` * `COUNTRY` * `PHONE` |

Analytics data is approximate and may differ from what’s shown on invoices due to small variations in data processing.

### Examples

Given a time range, you can get conversation and cost information associated with your WABA. If you want, you can filter and break down your results. See the code samples below for examples.

#### Get monthly data, using all breakdowns

**Scenario:** Given a month, you want to retrieve all conversation and cost information for all phone numbers associated with a WABA.

**Suggested Solution:** [Assemble the URL you want to call](#getting-the-data) and include the following filtering parameters:

* `start`: Start of your time range. In this case, the beginning of the month you want metrics for.
* `end`: End of your time range. In this case, the end of the month you want metrics for.
* `granularity`: How granular you want your data points to be. In the example below, we use `MONTHLY`, so each datapoint will represent a month’s worth of data.
* `phone_numbers`: Send an empty array and we return information for all phone numbers associated with the WABA.
* `dimensions`: Set it to all available breakdowns: `"CONVERSATION_CATEGORY"`, `"CONVERSATION_TYPE"`, `"COUNTRY"`, and `"PHONE"`.

In this case, you do not need to specify `country_codes`, `metric_types`, `conversation_types` and `conversation_categories`. If you don't send us anything for those fields, we return all available options. Once you set up the URL, make a GET request:

```
curl -i -X GET
"https://graph.facebook.com/v24.0/102290129340398
  ?fields=conversation_analytics
  .start(1685602800).end(1688194800)
  .granularity(MONTHLY)
  .phone_numbers([])
  .dimensions(["CONVERSATION_CATEGORY","CONVERSATION_TYPE","COUNTRY","PHONE"])
  &access_token=BLI8lkj..."
```

A successful response returns a `conversation_analytics` object with the data you have requested. In the following example, the WABA contains only one phone number.

```
{
  "conversation_analytics": {
    "data": [
      {
        "data_points": [
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 1558,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_direction": "UNKNOWN",
            "conversation_category": "AUTHENTICATION",
            "cost": 15.58
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 2636,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_category": "MARKETING",
            "cost": 26.36
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 2238,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_category": "SERVICE",
            "cost": 22.38
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 1782,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_category": "UTILITY",
            "cost": 17.82
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 1568,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "FREE_TIER",
            "conversation_category": "AUTHENTICATION",
            "cost": 15.68
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 2716,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "FREE_TIER",
            "conversation_category": "MARKETING",
            "cost": 27.16
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 2180,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "FREE_TIER",
            "conversation_category": "SERVICE",
            "cost": 21.8
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 1465,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "FREE_TIER",
            "conversation_category": "UTILITY",
            "cost": 14.65
          },
          {
            "start": 1685602800,
            "end": 1688194800,
            "conversation": 1433,
            "phone_number": "15550458206",
            "country": "US",
            "conversation_type": "FREE_ENTRY_POINT",
            "conversation_category": "SERVICE",
            "cost": 14.33
          }
        ]
      }
    ]
  },
  "id": "102290129340398",
}
```

#### Get data for a specific phone number, using all breakdowns and half hour granularity

**Scenario**: Given a time range, you want to retrieve all conversation and cost information for a specific phone number associated with a WABA. In the results, you want to use all possible breakdowns. You need each data point to represent half an hour’s worth of data.

**Suggested Solution**: [Assemble the URL you want to call](#getting-the-data) and include the following filtering parameters:

* `start`: Start of your time range.
* `end`: End of your time range.
* `granularity`: How granular you want your data points to be. In the example below, we use `HALF_HOUR`, so each datapoint represents half an hour’s worth of data.
* `phone_numbers`: The phone number you need information for.
* `dimensions`: Set it to all available breakdowns: `CONVERSATION_CATEGORY`, `CONVERSATION_TYPE`, `COUNTRY`, and `PHONE`.

In this case, you do not need to specify `country_codes`, `metric_types`, `conversation_types`, or `conversation_categories`. If you don’t send us anything for those fields, we return all available options. Once you set up the URL, make a GET request:

```
curl -i -X GET \
"https://graph.facebook.com/v24.0/102290129340398
  ?fields=conversation_analytics
  .start(1685602800)
  .end(1685689200)
  .granularity(HALF_HOUR)
  .phone_numbers(["19195552584"])
  .dimensions(["CONVERSATION_CATEGORY","CONVERSATION_TYPE","COUNTRY,PHONE"])
  &access_token=BLI8lkj..."
```

A successful response returns a `conversation_analytics` object with the data you have requested:

```
{
  "conversation_analytics": {
    "data": [
      {
        "data_points": [
          {
            "start": 1685602800,
            "end": 1685604600,
            "conversation": 4,
            "phone_number": "19195552584",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_direction": "UNKNOWN",
            "conversation_category": "SERVICE",
            "cost": 0.0232
          },
          {
            "start": 1685602800,
            "end": 1685604600,
            "conversation": 4,
            "phone_number": "19195552584",
            "country": "US",
            "conversation_type": "REGULAR",
            "conversation_direction": "UNKNOWN",
            "conversation_category": "MARKETING",
            "cost": 0.0232
          },
         # ... more data points
        ]
      }
    ]
  },
  "id": "102290129340398"
}
```

#### Get monthly data, using conversation type breakdowns

**Scenario**: Given a time range, you want to retrieve all conversation and cost information for all phone numbers associated with a WABA. In the results, you want to break down by conversation type.

**Suggested Solution**: [Assemble the URL you want to call](#getting-the-data) and include the following filtering parameters:

* `start`: Start of your time range.
* `end`: End of your time range.
* `granularity`: How granular you want your data points to be. In the example below, we use `MONTHLY`, so each datapoint represents half a month’s worth of data.
* `phone_numbers`: Send an empty array and we’ll return information for all phone numbers associated with the WABA.
* `dimensions`: Set it to `CONVERSATION_TYPE`.

In this case, you do not need to specify `country_codes`, `metric_types`, `conversation_types`, `conversation_directions`, or `conversation_categories`. If you don't send us anything for those fields, we return all available options. Once you set up the URL, make a GET request:

```
curl -i -X GET "https://graph.facebook.com/v24.0/102290129340398
      ?fields=conversation_analytics
      .start(1643702400).end(1646121600)
      .granularity(MONTHLY)
      .phone_numbers([])
      .dimensions([CONVERSATION_TYPE])
      &access_token=BLI8lkj..."
```

A successful response returns a `conversation_analytics` object with the data you have requested:

```
{
  "data": [
    {
      "data_points": [
        {
          "start": 1643702400,
          "end": 1646121600,
          "conversation": 8500,
          "conversation_type": "REGULAR",
          "cost": 88.1010
        },
        {
          "start": 1643702400,
          "end": 1646121600,
          "conversation”: 1000,
          "conversation_type": "FREE_TIER",
          "cost": 0.0000
        }
        {
          "start": 1643702400,
          "end": 1646121600,
          "conversation”: 250,
          "conversation_type": "FREE_ENTRY_POINT",
          "cost": 0.0000
        }
      ]
    }
  ]
}
```

#### Get half-hour data broken down by conversation category

Request:

```
curl -i -X GET "https://graph.facebook.com/v24.0/102290129340398
  ?fields=conversation_analytics
  .start(1685527200)
  .end(1685613600)
  .granularity(HALF_HOUR)
  .conversation_categories(["MARKETING","AUTHENTICATION"])
  .dimensions(["CONVERSATION_CATEGORY"])
  &access_token=BLI8lkj..."
```

Response:

```
{
  "conversation_analytics": {
    "data": [
      {
        "data_points": [
          {
            "start": 1685529000,
            "end": 1685530800,
            "conversation": 2,
            "conversation_category": "AUTHENTICATION",
            "cost": 0.0128
          },
          {
            "start": 1685527200,
            "end": 1685529000,
            "conversation": 3,
            "conversation_category": "MARKETING",
            "cost": 0.0432
          }
        ]
      }
    ]
  },
  "id": "102290129340398"
}
```

#### Get half-hour data broken down by conversation category and conversation type

Request:

```
curl -i -X GET \
 "https://graph.facebook.com/v24.0/102290129340398
  ?fields=conversation_analytics
  .start(1685527200)
  .end(1685613600)
  .granularity(HALF_HOUR)
  .conversation_categories(["MARKETING","AUTHENTICATION"])
  .dimensions(["CONVERSATION_CATEGORY","CONVERSATION_TYPE"])
  &access_token=BLI8lkj..."
```

Response:

```
{
  "conversation_analytics": {
    "data": [
      {
        "data_points": [
          {
            "start": 1685527200,
            "end": 1685529000,
            "conversation": 3,
            "conversation_type": "REGULAR",
            "conversation_category": "MARKETING",
            "cost": 0.0432
          },
          {
            "start": 1685529000,
            "end": 1685530800,
            "conversation": 2,
            "conversation_type": "REGULAR",
            "conversation_category": "AUTHENTICATION",
            "cost": 0.0128
          }
        ]
      }
    ]
  },
  "id": "102290129340398"
}
```

## Pricing analytics

The `pricing_analytics` field allows you to get pricing breakdowns for any messages delivered within a specified date range.

### Request syntax

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>
  ?fields=pricing_analytics
  .start(<START>)
  .end(<END>)
  .granularity(<GRANULARITY>)
  .phone_numbers(<PHONE_NUMBERS>)
  .country_codes(<COUNTRY_CODES>)
  .metric_types(<METRIC_TYPES>)
  .pricing_types(<PRICING_TYPES>)
  .pricing_categories(<PRICING_CATEGORIES>)
  .dimensions(<DIMENSIONS>)
```

### Pricing analytics parameters

| Filter | Description | Example Value |
| --- | --- | --- |
| `<COUNTRY_CODES>`  *Array of strings* | **Optional.**  The countries for which you would like to retrieve analytics. Provide an array with 2 letter country codes for the countries you would like to include. If not provided, analytics will be returned for all countries you have communicated with. | `[ US, BR ]` |
| `<DIMENSIONS>`  *Array of strings* | **Optional.**  List of breakdowns you would like to apply to your metrics. If you send an empty list, we return results without any breakdowns.  Values can be:   * `COUNTRY` * `PHONE` * `PRICING_CATEGORY` * `PRICING_TYPE` * `TIER` | `[ PRICING_CATEGORY, PRICING_TYPE, COUNTRY ]` |
| `<END>`  *UNIX timestamp* | **Required.**  UNIX timestamp indicating the end date for the date range you are retrieving analytics for. | `1728581152` |
| `<GRANULARITY>`  *String* | **Required.**  The granularity at which you would like to retrieve the analytics. Value can be one of:   * `DAILY` * `HALF_HOUR` * `MONTHLY` | `DAILY` |
| `<METRIC_TYPES>`  *Array of strings* | **Optional.**  Array of metrics you would like to receive. If you send an empty array, we return results for all metric types.  Values can be:   * `COST`: Approximate charges for messages delivered in that time range, in your WABA's currency. * `VOLUME`: Includes the number of messages delivered for that time range. | `[COST, VOLUME]` |
| `<PHONE_NUMBERS>`  *Array of strings* | **Optional.**  An array of phone numbers for which you would like to retrieve analytics. If not provided, data for all business phone numbers associated with your WABA are included. | `[ 15550783881, 15550783882, 15550783883 ]` |
| `<PRICING_CATEGORIES>`  *Array of strings* | **Optional.**  Array of pricing categories. If you send an empty array, we return results for all pricing categories.  Values can be:   * `AUTHENTICATION`: Messages charged the authentication rate. * `AUTHENTICATION_INTERNATIONAL`: Messages charged the authentication-international rate. * `MARKETING`: Messages charged the marketing rate. * `SERVICE`: Messages that were not charged. Includes all non-template messages and utility messages sent inside of a customer service window. * `UTILITY`: Messages charged the utility rate. * `REFERRAL_CONVERSION`: Messages that have been received through a [free entry point](https://developers.facebook.com/docs/whatsapp/pricing#free-entry-point-windows) | `[ AUTHENTICATION, MARKETING, UTILITY ]` |
| `<PRICING_TYPES>`  *Array of strings* | **Optional.**  Array of pricing types. If you send an empty array, we return results for all pricing types.  Values can be:   * `FREE_CUSTOMER_SERVICE`: Free messages. These are non-template messages and utility messages sent within customer service windows. * `FREE_ENTRY_POINT`: All messages sent within free entry point customer service windows. * `REGULAR`: Billable messages. Includes all authentication and marketing template messages, and any utility template messages sent outside of a customer service window. Excludes all messages sent within free entry point customer service windows. | `[ REGULAR, FREE_CUSTOMER_SERVICE ]` |
| `<START>`  *UNIX timestamp* | **Required.**  UNIX timestamp indicating the start date for the date range you are retrieving analytics for. | `1726014453` |
| `<WABA_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `102290129340398` |

### Volume tier information

Include the `TIER`, `PRICING_CATEGORY`, and `COUNTRY` parameters in the `dimensions` array to get volume tier information. Data points representing messages affected by volume tier pricing will have a `tier` property in the response.

#### Example response syntax with tier information

```
{
  "start": <START_TIMESTAMP>,
  "end": <END_TIMESTAMP>,
  "phone_number": "<BUSINESS_PHONE_NUMBER>",
  "country": "<COUNTRY_CODE>",
  "tier": "<LOWER>:<UPPER>",
  "pricing_type": "<PRICING_TYPE>",
  "pricing_category": "<PRICING_CATEGORY>",
  "volume": <VOLUME>,
  "cost": <COST>
}
```

The `tier` property value represents a concatenation of the lower and upper bounds for the tier specific to the market–category pair (`country` and `pricing_category`) that that data point represents.

* `<LOWER>` – An integer representing the lower bound of the tier (inclusive).
* `<UPPER>` – An integer representing the upper bound of the tier (inclusive), or the string `MAX`.

**Notes**

* To determine your current volume tier, read the `tier`, `country`, and `pricing_category` values. The `tier` value's `<UPPER>` integer (the integer after the colon) tells you your current tier for the `country` and `pricing_category` (for example, (India and utility, respectively).
* To determine how many messages you need to send to reach the next tier for a given `country` and `pricing_category`, subtract the `volume` integer from the tier value's `<UPPER>` integer.
* Volume tiers will only be available for utility and authentication template messages. For marketing template messages (where volume tiers will not apply), tier will be set to `0:MAX`.
* The `tier` property will be omitted for data points that represent free messages, since free messages don't contribute to tiering counts.
* Volume tiers will be determined solely by Meta. All insights data is approximate due to small variations in data processing. Undue reliance should not be placed on insights data.

### Example request

```
curl 'https://graph.facebook.com/v24.0/161311403722088?fields=pricing_analytics.start(1748761200).end(1749687703).granularity(DAILY).dimensions(PRICING_CATEGORY,PRICING_TYPE,TIER,COUNTRY).country_codes(US,IN)' \
-H 'Authorization: Bearer EAAJB'
```

### Example response

```
{
  "pricing_analytics": {
    "data": [
      {
        "data_points": [
          {
            "start": 1749193200,
            "end": 1749279600,
            "country": "IN",
            "pricing_type": "FREE_CUSTOMER_SERVICE",
            "pricing_category": "SERVICE",
            "volume": 2,
            "cost": 0
          },
          {
            "start": 1749106800,
            "end": 1749193200,
            "country": "IN",
            "tier": "0:750000",
            "pricing_type": "REGULAR",
            "pricing_category": "AUTHENTICATION_INTERNATIONAL",
            "volume": 2,
            "cost": 4.6
          },
          {
            "start": 1749106800,
            "end": 1749193200,
            "country": "IN",
            "pricing_type": "FREE_CUSTOMER_SERVICE",
            "pricing_category": "SERVICE",
            "volume": 2,
            "cost": 0
          },
          {
            "start": 1748934000,
            "end": 1749020400,
            "country": "US",
            "tier": "0:MAX",
            "pricing_type": "REGULAR",
            "pricing_category": "MARKETING",
            "volume": 1,
            "cost": 10
          },
          {
            "start": 1748847600,
            "end": 1748934000,
            "country": "US",
            "pricing_type": "FREE_CUSTOMER_SERVICE",
            "pricing_category": "SERVICE",
            "volume": 1,
            "cost": 0
          },
          {
            "start": 1748847600,
            "end": 1748934000,
            "country": "US",
            "pricing_type": "FREE_ENTRY_POINT",
            "pricing_category": "SERVICE",
            "volume": 6,
            "cost": 0
          },
          {
            "start": 1748847600,
            "end": 1748934000,
            "country": "US",
            "tier": "0:2",
            "pricing_type": "REGULAR",
            "pricing_category": "AUTHENTICATION",
            "volume": 1,
            "cost": 10
          },
          {
            "start": 1748847600,
            "end": 1748934000,
            "country": "IN",
            "tier": "0:750000",
            "pricing_type": "REGULAR",
            "pricing_category": "AUTHENTICATION_INTERNATIONAL",
            "volume": 1,
            "cost": 2.3
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "pricing_type": "FREE_CUSTOMER_SERVICE",
            "pricing_category": "SERVICE",
            "volume": 2,
            "cost": 0
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "tier": "0:2",
            "pricing_type": "REGULAR",
            "pricing_category": "AUTHENTICATION",
            "volume": 1,
            "cost": 10
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "pricing_type": "FREE_CUSTOMER_SERVICE",
            "pricing_category": "UTILITY",
            "volume": 1,
            "cost": 0
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "tier": "0:2",
            "pricing_type": "REGULAR",
            "pricing_category": "UTILITY",
            "volume": 1,
            "cost": 10
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "tier": "0:MAX",
            "pricing_type": "REGULAR",
            "pricing_category": "MARKETING",
            "volume": 4,
            "cost": 40
          },
          {
            "start": 1748761200,
            "end": 1748847600,
            "country": "US",
            "tier": "0:MAX",
            "pricing_type": "REGULAR",
            "pricing_category": "MARKETING_LITE",
            "volume": 1,
            "cost": 10
          }
        ]
      }
    ]
  }
}
```

## Template analytics

Template analytics describe the number of times a template has been sent, delivered, and read, and the number of times [URL buttons](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) or [Quick Reply buttons](/docs/whatsapp/business-management-api/message-templates/components#quick-reply-buttons) in the template have been clicked. Additionally, onboarded [MM API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp) businesses can track offsite conversion metrics.

Data is returned with a daily granularity in the default timezone of UTC and WABA's timezone, with a lookback window of up to 90 days. To show data in the WABA’s configured timezone, pass in the use\_waba\_timezone param with a value of true.

Display data in the WABA’s configured timezone by passing in the `use_waba_timezone` param with a value of `true`.

```
{
 "data": [
   {
     "waba_timezone": "America/Los_Angeles",
     "granularity": "DAILY",
     "product_type": "cloud_api",
     "data_points": [
         ...
     ]
   }
}
```

### Limitations

* Template Analytics are only available for On-Premises API if the account has not opted into Cloud API template analytics.
* Button click analytics are only available for templates categorized as `MARKETING` or `UTILITY`.
* WABAs owned by or shared with Meta Business Accounts in the European Union, United Kingdom, or Japan, or that have a business phone number with a country calling code from any of those countries or regions, are not supported.
* Offsite conversion metrics are available exclusively for businesses onboarded to MM API for WhatsApp.
* Read and click event data for WhatsApp template messages is only available for up to 7 days from the date the message is sent. After this 7-day window, the corresponding read/click counts reset to zero and no further updates are recorded for those messages.

### Confirming template analytics

You must confirm template analytics on your WhatsApp Business Account before you can get template analytics. You can confirm template analytics using the WhatsApp Manager or the API.

By confirming access via the API, you direct Meta to add insights to your WhatsApp Business Account. These insights include link tracking to report website clicks. You can turn off link tracking on each message template. You also direct Meta to collect and anonymize data from your chats with customers. Meta will anonymize this data to improve services it provides you and other businesses.

To confirm via API, send the following request:

```
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>?is_enabled_for_insights=true
```

Once confirmed, we will begin capturing template analytics for the WhatsApp Business Account. Once confirmed, template analytics cannot be disabled.

Upon success, the API will respond with your WhatsApp Business Account ID. For example:

```
{
  "id": 102290129340398
}
```

### Template analytics parameters

| Name | Description | Example Value |
| --- | --- | --- |
| `start`  *UNIX Timestamp or date string* | **Required.**  The start time for the date range you are retrieving analytics for. Can be represented as either a unix timestamp integer or a date string in the format YYYY-MM-DD. As template analytics are being provided with a daily granularity in the UTC timezone, a start unix timestamp that does not correspond to 0:00 UTC will be adjusted back to the current day’s 00:00 UTC.  If `use_waba_timezone` param has a value of true, this value must be a date string in the format YYYY-MM-DD. | `1543536000` |
| `end`  *UNIX Timestamp or date string* | **Required.**  The end time for the date range you are retrieving analytics for. Can be represented as either a unix timestamp integer or a date string in the format YYYY-MM-DD. As template analytics are being provided with a daily granularity in the UTC timezone, an end unix timestamp that does not correspond to 0:00 UTC will be adjusted back to the current day’s 00:00 UTC.  If `use_waba_timezone` param has a value of true, this value must be a date string in the format YYYY-MM-DD. | `1543708800` |
| `granularity`  *Enum* | **Required.**  The granularity at which you would like to retrieve the analytics. Value must be `DAILY`. | `DAILY` |
| `template_ids`  *Array of IDs* | **Required.**  An array of template IDs for which you would like to retrieve analytics for.  Maximum 10. | `[1924084211297547,954638012257287,969725530748535]` |
| `metric_types`  *Array of enums* | **Optional.**  `COST` node is NOT accessible to businesses who bill through a Solution Partner. To understand your charges, please reach out to your partner.  The types of metrics which you want to retrieve. If omitted or an empty array, analytics for all metric types will be returned.  Possible values:   * `COST` * `CLICKED` * `DELIVERED` * `READ` * `SENT` * `APP_ACTIVATIONS (MM API for WhatsApp only)` * `APP_ADD_TO_CART (MM API for WhatsApp only)` * `APP_CHECKOUTS_INITIATED (MM API for WhatsApp only)` * `APP_PURCHASES (MM API for WhatsApp only)` * `APP_PURCHASES_CONVERSION_VALUE (MM API for WhatsApp only)` * `WEBSITE_ADD_TO_CART (MM API for WhatsApp only)` * `WEBSITE_CHECKOUTS_INITIATED (MM API for WhatsApp only)` * `WEBSITE_PURCHASES (MM API for WhatsApp only)` * `WEBSITE_PURCHASES_CONVERSION_VALUE (MM API for WhatsApp only)`   You can [learn more about cost and click metrics here.](/docs/whatsapp/business-management-api/analytics/#cost-and-click-metrics). | `[SENT,DELIVERED,READ]` |
| `product_type`  *Enum* | **Optional.**  The product type of the metrics you want to retrieve. If omitted, only analytics for Cloud API will be returned.  Possible values:   * `CLOUD_API`: Use this product type to filter for template metrics sent via Cloud API * `MARKETING_MESSAGES_API_FOR_WHATSAPP`: Use this product type to filter for template metrics sent via Marketing Messages API for WhatsApp | `MARKETING_MESSAGES_API_FOR_WHATSAPP` |
| `<USE_WABA_TIMEZONE>`  *Boolean* | **Optional.**  Whether to show metrics in the WABA’s configured timezone. If false or omitted, metrics will be shown in UTC.  If true, params start and end must be in the format YYYY-MM-DD. | `true` |

### Examples

#### Getting all template analytics

**Scenario:** Given a 1-day timeframe, get all template analytics metric types for an authentication template and a marketing template with a URL button.

Example Request:

```
curl -g 'https://graph.facebook.com/v24.0/109259195336416/template_analytics?start=1718064000&end=1718122745&granularity=daily&metric_types=cost%2Cclicked%2Cdelivered%2Cread%2Csent&template_ids=[1421988012088524%2C2632273056924580]' \
-H 'Authorization: Bearer EAAJB...'
```

Example response:

```
{
  "data": [
    {
      "granularity": "DAILY",
      "product_type": "cloud_api", // Only available to businesses in the Marketing Messages API for WhatsApp alpha
      "data_points": [
        {
          "template_id": "1421988012088524",
          "start": 1718064000,
          "end": 1718150400,
          "sent": 1,
          "delivered": 1,
          "read": 1,
          "cost": [
            {
              "type": "amount_spent",
              "value": 0.01
            },
            {
              "type": "cost_per_delivered",
              "value": 0.01
            }
          ]
        },
        {
          "template_id": "2632273056924580",
          "start": 1718064000,
          "end": 1718150400,
          "sent": 1,
          "delivered": 1,
          "read": 1,
          "clicked": [
            {
              "type": "quick_reply_button",
              "button_content": "Contact Support",
              "count": 108
            },
            {
              "type": "unique_url_button",
              "button_content": "Tell me more",
              "count": 16
            }
          ],
          "cost": [
            {
              "type": "amount_spent",
              "value": 0.03
            },
            {
              "type": "cost_per_delivered",
              "value": 0.03
            },
            {
              "type": "cost_per_url_button_click",
              "value": 0.03
            }
          ]
        }
      ]
    }
  ],
  "paging": {
    "cursors": {
      "before": "MAZDZD",
      "after": "MjQZD"
    }
  }
}
```

### Cost and click metrics

**Cost metrics** are returned as an array of cost objects, each with a type and value. Types can be:

* `amount_spent` — Total amount spent on conversations opened within the `start` and `end` timeframe as a result of sending the template. See [Opening Conversations](/docs/whatsapp/pricing#opening-conversations).
* `cost_per_delivered` — The `amount_spent` value divided by the number of times the template was delivered within the `start` and `end` timeframe.
* `cost_per_url_button_click` — The `amount_spent` value divided by the number of times the template's URL button was clicked, within the `start` and `end` timeframe. Quick reply button clicks are not included. Object omitted if the template does not have a URL button.

**Click metrics** are returned as an array of JSON objects each with a type and value. Clicks are only returned for URL buttons and quick-reply buttons in templates categorized as `MARKETING` or `UTILITY`.

Types can be:

* `url_button` — The total number of clicks on the url button.
* `unique_url_button` — Unique clicks track the number of distinct WhatsApp accounts that have clicked on a button. This metric helps you understand how many individual users are engaging with your CTAs, while eliminating duplicate clicks from the same recipient and providing an accurate measurement of engagement.

### Disabling button click analytics

You can disable button click tracking on an individual template by setting its `cta_url_link_tracking_opted_out` field to `true`. Once disabled, the API will no longer return the clicked property in template analytics or display button engagement/clicks in the WhatsApp Manager when viewing the template's insights.

#### Request syntax

```
POST /<TEMPLATE_ID>
  ?cta_url_link_tracking_opted_out=<OPT_OUT>
  &category=<TEMPLATE_CATEGORY>
```

#### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<WHATSAPP_TEMPLATE_ID>`  *Template ID* | **Required.**  Template ID. | `245435364965041` |
| `<OPT_OUT>`  *Boolean* | **Required.**  Indicates if template button click tracking is disabled. Set to `true` to disable button click tracking on the template, or `false` to enable.  This value is set to `false` upon template creation. | `true` |
| `<TEMPLATE_CATEGORY>`  *String* | **Required.**  Template's current category.  If you set the template category to a value other than its current category, the template status will be set to `PENDING` and the template must undergo template review to be approved. | `marketing` |

#### Example request

```
curl -X POST 'https://graph.facebook.com/v24.0/245435364965041?cta_url_link_tracking_opted_out=true&category=marketing' \
-H 'Authorization: Bearer EAAJB...'
```

#### Example response

Upon success, the API will respond with:

```
{
    "success": true
}
```

## Template group analytics

The `template_group_analytics` field allows you to get the number of times templates within a [template group](/docs/whatsapp/business-management-api/message-templates/template-groups) have been sent, delivered, and read, and the number of times their [URL buttons](/docs/whatsapp/business-management-api/message-templates/components#url-buttons) or [Quick Reply buttons](/docs/whatsapp/business-management-api/message-templates/components#quick-reply-buttons) have been clicked.

Data is returned with a daily granularity in the default timezone of UTC and WABA's timezone, with a lookback window of up to 90 days. To show data in the WABA’s configured timezone, pass in the use\_waba\_timezone param with a value of true.

```
{
 "data": [
   {
     "waba_timezone": "America/Los_Angeles",
     "granularity": "DAILY",
     "product_type": "cloud_api",
     "data_points": [
         ...
     ]
   }
}
```

### Limitations

Button click analytics are only available for templates categorized as `marketing` or `utility`.
WABAs owned by or shared with Meta Business Accounts in the European Union, United Kingdom, or Japan, or that have a business phone number with a country calling code from any of those countries or regions, are not supported.

### Enabling template analytics

You must enable template analytics on your WhatsApp Business Account before you can get template group analytics. You can confirm template analytics enablement using the WhatsApp Manager or the API.

By confirming access via the API, you direct Meta to add insights to your WhatsApp Business Account. These insights include link tracking to report website clicks. You can turn off link tracking on each message template. You also direct Meta to collect and anonymize data from your chats with customers. Meta will anonymize this data to improve services it provides you and other businesses.

To confirm enablement via API, send the following request:

`POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>?is_enabled_for_insights=true`

Upon success, the API will respond with your WhatsApp Business Account ID and we will begin capturing template group analytics for the WhatsApp Business Account.

Once enabled, template analytics cannot be disabled.

### Request syntax

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>/template_group_analytics
  ?granularity=daily
  &start=<START_TIME>
  &end=<END_TIME>
  &metric_types=<METRIC_TYPES>
  &template_group_ids=[<TEMPLATE_GROUP_IDS>]
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<WABA_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `102290129340398` |
| `<START_TIME>`  *UNIX Timestamp or date string* | **Required.**  The start time for the date range you are retrieving analytics for. Can be represented as either a unix timestamp integer or a date string in the format YYYY-MM-DD.  As template group analytics are being provided with a daily granularity in the UTC timezone, a start unix timestamp that does not correspond to 0:00 UTC will be adjusted back to the current day’s 00:00 UTC.  If `use_waba_timezone` param has a value of true, this value must be a date string in the format YYYY-MM-DD. | `1738465116` |
| `<END_TIME>`  *UNIX Timestamp or date string* | **Required.**  The end time for the date range you are retrieving analytics for. Can be represented as either a unix timestamp integer or a date string in the format YYYY-MM-DD.  As template group analytics are being provided with a daily granularity in the UTC timezone, an end unix timestamp that does not correspond to 0:00 UTC will be adjusted back to the current day’s 00:00 UTC.  If `use_waba_timezone param` has a value of true, this value must be a date string in the format YYYY-MM-DD. | `1739559516` |
| `<METRIC_TYPES>`  *Array of strings* | **Optional.**  Array of metrics you would like to receive. If you send an empty array, the API returns results for all metric types.  Values can be:   * `cost` * `clicked` * `delivered` * `read` * `sent`   Note that `COST` is not accessible to business customers who are billed through a Solution Partner.  See [Cost and click metrics](#cost-and-click-metrics-2) to learn more about cost and click metrics. | ``` [ sent, delivered, read ] ``` |
| `<TEMPLATE_GROUP_IDS>` | **Required.**  An array of template group IDs for which you wish to get template group metrics.  Maximum 10 IDs. | `102290129340398` |
| `<USE_WABA_TIMEZONE`>`  *Boolean* | **Optional.**  Whether to show metrics in the WABA’s configured timezone. If false or omitted, metrics will be shown in UTC.  If true, params start and end must be in the format YYYY-MM-DD. | `true` |

### Example request

```
curl -g 'https://graph.facebook.com/v24.0/102290129340398/template_group_analytics?granularity=daily&start=1738465116&end=1739559516&metric_types=sent,delivered,read&template_group_ids=[1044106240855852]' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Note that the example below has been truncated with an ellipsis (`...`) for brevity.

```
{
  "data": [
    {
      "granularity": "DAILY",
      "data_points": [
        {
          "template_group_id": "1044106240855852",
          "start": 1739491200,
          "end": 1739577600,
          "sent": 1460,
          "delivered": 1460,
          "read": 1399
        },
        {
          "template_group_id": "1044106240855852",
          "start": 1739404800,
          "end": 1739491200,
          "sent": 673,
          "delivered": 673,
          "read": 645
        },
        ...
      ]
    }
  ],
  "paging": {
    "cursors": {
      "before": "MAZDZD",
      "after": "MjQZD"
    }
  }
}
```

### Cost and click metrics

**Cost metrics** are returned as an array of cost objects, each with a type and value. Types can be:

* `amount_spent` — Total amount spent on conversations opened within the `start` and `end` timeframe as a result of sending the template. See [Opening Conversations](/docs/whatsapp/pricing#opening-conversations).
* `cost_per_delivered` — The `amount_spent` value divided by the number of times the template was delivered within the `start` and `end` timeframe.
* `cost_per_url_button_click` — The `amount_spent` value divided by the number of times the template's URL button was clicked, within the `start` and `end` timeframe. Quick reply button clicks are not included. Object omitted if the template does not have a URL button.

**Click metrics** are returned as an array of JSON objects each with a type and value. Clicks are only returned for URL buttons and quick-reply buttons in templates categorized as `marketing` or `utility`.

Types can be:

* `url_button` — The total number of clicks on the url button.
* `unique_url_button` — Unique clicks track the number of distinct WhatsApp accounts that have clicked on a button. This metric helps you understand how many individual users are engaging with your CTAs, while eliminating duplicate clicks from the same recipient and providing an accurate measurement of engagement.

## Reference

For a list of all possible values for each field, see the Graph API reference of the [WhatsApp Business Account Analytics field](/docs/graph-api/reference/waba-analytics/).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Analytics](#analytics)

[Get data](#get-data)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Messaging analytics](#messaging-analytics)

[Messaging analytics parameters](#messaging-analytics-parameters)

[Example](#example)

[Conversation analytics](#conversation-analytics)

[Conversation analytics parameters](#conversation-analytics-parameters)

[Examples](#examples)

[Pricing analytics](#pricing-analytics)

[Request syntax](#request-syntax-2)

[Pricing analytics parameters](#pricing-analytics-parameters)

[Volume tier information](#volume-tier-information)

[Example request](#example-request)

[Example response](#example-response)

[Template analytics](#template-analytics)

[Limitations](#limitations)

[Confirming template analytics](#confirming-template-analytics)

[Template analytics parameters](#template-analytics-parameters)

[Examples](#examples-2)

[Cost and click metrics](#cost-and-click-metrics)

[Disabling button click analytics](#disabling-button-click-analytics)

[Template group analytics](#template-group-analytics)

[Limitations](#limitations-2)

[Enabling template analytics](#enabling-template-analytics)

[Request syntax](#request-syntax-3)

[Request parameters](#request-parameters-2)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Cost and click metrics](#cost-and-click-metrics-2)

[Reference](#reference)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfiJKi_nYjgCYH01DZBpLDv116TAQI3DPfNnFcNSGt-PSQ&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_Afg9bhlu_kdIjZO7l-fZ8WejBBek2CacRL_5uIvqZs1SYw&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfgpKYj0vQRZ8AKqgASacpthHVnEYiihLCtsaOwZ-MLFEQ&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2K2ALb5-BycJqFwc6BkedJaMUVPEe4_En2NNX8PUa-p7VIa7DzeMvpsOdA2J0VVWzE73XtuMIVDUC7_ieFLeCnZk9IThQ_zzMawowoJdr-nUix7vqzYWYd2D1JsM2nzNlZoFvj3BhN4eufwn4uWA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfhUcJduj5tn1t4lG-PslTH3GKPH2py7HrkddSn-cHJR-A&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3ToM4VgJCMMvt4ExPDCg6xjniRKSDBHzuZw-b4OVGC-OXtdRqHg84oFxfY8IdUnsoJeRGVEFbKMKS8XkvGvKbsh48nqQpYaY-7tfr9CLgzHniKQNSTA084eagjHwOxzlB_jnBhnb1tHHYIuZNEjw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfhitNRVyFT35SUXrCWVMV_3U4Wlbn9TeHG45J8_ybyqwQ&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3eUORTKf7YpS_wZIe_ZreVuoFQomU70Q9NbTGCywH1_IJVPV9rfrtfsi1gtQfquMCgxMGPz33heQn7GLepz1cr-mGVGMR_giR6-ggcn3ZQUeZSqdRePAtsg-kfqaFcagkDKF50Vq4o2DvOEkXglg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfhvbCQf8P1qj2jlPMr-boO0mJz6czrE8FL-wcuzIOIzLw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1fxSO_KAofTTxgw1AKIi0838cAhi2mebJdWuG8_E-cruV_ocRfBB9FfXuniwKQvJvnfQQm6A7oU6viISXO3WNKeTki7Ji94cz37dyM9sPKvUtwmMtk-XckwhqFEc-zAKyxiDANehc_68pYw1trwA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1yYIZSgFP_SdwkPIGVRGfXuMl-g1utV-4QvVQqFFR9WFp3conyl6-SUN7mSDZdHeEXjDNIhbPL8p6sCVUKvllu2TwpY5wFs681RiWYRC9BDasBvXQACXVBquTqdgDnRmxpQQIAl6Wz8j09DvgA2w)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Q0--4F1KsgJrffubbc0OUvFhNUTv5lMxmaVetN51Irac4FyXitRrypAg-p8DFp4YEau3ez3jIWuVRujmGIjU7IU5lyyq1a8SSQi8TlWLl9abv-ELuzCPIBUgl8gkhj8RzhSwPAS8LK5NMANz_Vg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_Afg3PzTBdp-XzFoBjual-4pBTq4XdYfVQq_DgGCMy4ILKQ&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfiOLO8rG3sayrVkcEApelwNOaeIZrSLzclIQAlz0C3hHg&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1OMneiIaHM8iSD5WCQhsHEi-qN9Cqtrcm8H3NYB_vAMyR_vlKaZfX_LHhj9DHPdtOo7zqEzzpajCUhguCpGW5m2eYew1LTzPkqG--58gKG102sKmm4_j48Og6J-WnZHq3UlWIBZwA3d4R_Q-fyTA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfiF2QUX3beqDWqo2UOEcKdrRGQcXj_uUSNkW7hFo7QVxw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0lEExAbRUoVIBRASxJmMf-kHAVfO8iFqa4X1zkwVWc_PnKTO9vOxcLJR0lb3APblZTf4cpWfNnSjnwz5MTMUOvxllY5AsMzE4V9BymTLrFEKuP4_iGnGiB0IkvIguShKR2wbnVmlQdNxzyxHY08w)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_AfgTYEhPLV_SKtLHQrONSdCGW8zzI5uoA_OLXv7pwC2wKA&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2RfPeeaHvi2ztBksS-AM9pT4A9uq5c4dHY0TVuKFpDPJ_ciCizZ02873NJ8Cd4DJL84zy_xsdNhlgZ8jw93IEcROdAmmHPiH-WVkPXWwj03KQLDP2peRaULvt8tSzhNVhoVPzc6taFpoZicdLQdg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YvYlAgjiDrVia9853IggHA&oh=00_Afh8cJmS95gXvTmJu5AbZpI_uAsvC_4iAfeygCe3CzVKxg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0Uk8gsygL-au--tsEKrGKYGv9pqK82o0WXkQpejhK9CjUCql1xnYN0YHCTKexyFXBBP-_g8ee2ptRFXSyj9gtr21csrUtNDPtndxTN8jun6Jcu8y63mt5KixjrhxL73IhHL_ejQJ-r8uLGAAFqLQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT15O8OymtpAdRyA_h292d_AF5btDPoAPfU7LBZK0sqyve7lQbPGaPGqDU5hCjlI8cy0bdlRqE4JrMyInAA6Z09rF0b6AW-1Qd642ZLRliugFXW6x5IIyZQq9-UEudbVHChnojOe1ciq49M5nPeJzg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)