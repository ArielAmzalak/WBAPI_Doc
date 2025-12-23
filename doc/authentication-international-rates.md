+++
id = "authentication-international-rates"
title = "Authentication-international rates"
summary = "Specific countries have an authentication-international rate in our rate cards."
source = "https://developers.facebook.com/docs/whatsapp/authentication-international-rates"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "messaging", "authentication", "rate-limits", "pricing"]
+++
# Authentication-international rates

Specific countries have an **authentication-international** rate in our [rate cards](/docs/whatsapp/pricing#rate-cards). If you send an authentication template message to a WhatsApp user whose country calling code is for a country that has an authentication-international rate, the delivered message will be billed the country's authenticationinternational rate if:

* your business is [eligible](#eligibility) for authentication-international rates
* your business is based in another country (see [Primary Business Location](#primary-business-location))
* the message was delivered on or after your [start time](#start-times) for that country

For example, if your business is based in Indonesia and you send an authentication template message to a WhatsApp user who has a +62 (Indonesia) country calling code, and the message is delivered, you will not be billed the authentication-international rate since you are based in the same country as the user. If your business is based in India, however, you will be billed the authentication-international rate, if you meet all of the criteria above.

See [Examples](#examples) for additional example scenarios.

Status [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks that include pricing details and [pricing analytics](/docs/whatsapp/business-management-api/analytics#pricing-analytics) will indicate if a message or set of messages were billed the authentication-international rate.

## Eligibility

If your business sends more than 750K messages outside of customer service windows in a moving 30-day period, across all of your WhatsApp Business Accounts, with unique WhatsApp users whose country calling codes are for a country that has an authentication-international rate, it will be deemed eligible for authentication-international rates.

Once deemed eligible, we will set your [start times](#start-times) 30 days out for each country that has an authentication-international rate. In addition, we will attempt to determine your [primary business location](#primary-business-location) using publicly-available information.

We will then send you an [eligibility email](#eligibility-email) that includes these start times and the country that we set as your primary business location (if we were able to determine the country). This provides you with 30 days notice before authentication-international rates apply. [Webhooks](#webhooks) will also be triggered that include your start times and your primary business location (if we set it).

Note that eligibility is permanent. Once your business is deemed eligible, all authentication template messages sent on or after your start time will be charged the authentication-international rate in markets where authorization-international rates apply.

## Countries with authentication-international rates

The following countries have authentication-international rates:

* Egypt
* India
* Indonesia
* Malaysia
* Nigeria
* Pakistan
* Saudi Arabia
* South Africa
* United Arab Emirates

Please see [Rate cards](/docs/whatsapp/pricing#rate-cards) for more details about the rates.

## Start times

Start times are business- and country-specific timestamps. They indicate when newly-delivered authentication template messages are subject to authentication-international rates. Authentication template messages sent by your business and delivered to WhatsApp users in these countries **on or after these dates** only will be charged authentication-international rates.

Start times are set when your business is first deemed eligible for authentication-international rates, and are 30 days from your eligibility date, so you will always have 30-days notice before the authentication-international rate applies.

Start times are included in your [eligibility email](#eligibility-email) and [webhooks](#webhooks). You can also get these times by requesting the `auth_international_rate_eligibility` field on any of your business's WhatsApp Business Accounts:

### Request

```
curl 'https://graph.facebook.com/<API_VERSION>/<WABA_ID>?fields=auth_international_rate_eligibility' \
-H 'Authorization: <ACCESS_TOKEN>'
```

### Request parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<WABA_ID>`  *String* | **Required.**  WhatsApp Business Account ID. | `102290129340398` |

### Response

Upon success:

```
{
  "id": "<WABA_ID>",
  "auth_international_rate_eligibility": {
    "start_time": <START_TIME>,
    "exception_countries": [
      <EXCEPTION_COUNTRY>,
      <EXCEPTION_COUNTRY>,
      ...
    ]
  }
}
```

### Response parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<WABA_ID>` | WhatsApp Business Account (WABA) ID. | `102290129340398` |
| `<START_TIME>` | Unix timestamp indicating start time for all countries with authentication-international pricing for which you do not have an [exception](#exception-countries). | `1732057507` |
| `<EXCEPTION_COUNTRY>` | A unique object describing a country that has an exception start time. See [exception country](#exception-countries).  For most WhatsApp Business Accounts, the `exception_countries` array will be empty. | ``` {
   "country_code": "ID",
   "start_time": 1742450707
 }
 ``` |

## Primary business location

Your primary business location is the country where your business is based. It will appear in the Business Manager under the **Primary Business Location** field starting May 1, 2024, if we are able to determine where your business is based using publicly-available information.

The following publicly-available information is used to determine where your business is based:

* Where your business may be publicly-traded and listed
* Your business's corporate structure (where a parent or may be based or publicly-traded)

We will attempt to determine where your business is based when:

* It is deemed [eligible](#eligibility) for authentication-international rates
* You [edit your primary business location](#editing-your-primary-business-location) using the Business Manager.

This process can take up to 3 business days. The outcome of this determination can be:

* **Verified**  We determined where your business is based and set your primary business location to this country (which also triggers a webhook).
* **Need more information**  We require more information in order to make a determination.
* **Rejected**  We disagreed with the country you designated in the Business Manager (if you used it to edit the **Primary Business Location** field)

You will be notified of the outcome in your initial [eligibility email](#eligibility-email), or in a separate email if you used the Business Manager to edit your location.

If rejected or if we need more information, or if you disagree with the country we determined to be the primary business location, you can use the Business Manager to edit your location.

Note that if your primary business location status is not verified but you are past your start time for a given country, any authentication messages that you send to a WhatsApp user in that country will be billed the authentication-international rate.

### Set or edit your primary business location

To set or edit your primary business location:

1. [Navigate to Business Settings by clicking here](https://business.facebook.com/settings/info?edit_pbl=true)
2. Select the country of the businesss primary location of operation from the dropdown, or enter it in the text field. Note that this is the location where your business has its headquarters and maintains its bookkeeping records.
3. Click **Next**
4. Answer the questions on the screen. These answers will help Meta verify your primary business location.
5. Click **Next**
6. Click **Submit for review**

*Note: You wont be able to make any changes while your verification is under review.*

### Primary business location status

The **Primary Business Location** field in the Business Manager will also display a status:

* **Verified**  We have verified your business's primary location.
* **Pending verification**  We are in the process of determining your business's primary location.
* **Rejected**  We disagreed with the country you designated, based on publicly available information and what you included when you edited your location. You can manually edit your location again and include different information as part of your submission.

### Get your location via API

You can use the API to see if your business's primary business location is set by requesting the `primary_business_location` field on your WhatsApp Business Account (WABA):

#### Request

```
curl 'https://graph.facebook.com/<API_VERSION>/<WABA_ID>?fields=primary_business_location' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Response:

Upon success:

```
{
  "id": "<WABA_ID>",
  "primary_business_location": "<COUNTRY_CODE>"
}
```

* `<WABA_ID>`  WhatsApp Business Account ID.
* `<COUNTRY_CODE>`  Two-character country code indicating the country where we have determined the business to be based.

## Eligibility email

By sending authentication messages over WhatsApp, you acknowledge and agree that when your business is deemed eligible for authentication-international rates, an email will be sent to all of the email addresses associated with the admins of your accounts, and all third parties that your WhatsApp Business Accounts have been shared with (e.g. admins of Solution Partners that have access to your WhatsApp Business Accounts), to alert them that the threshold of eligibility has been reached.

The email will include:

* Your exact [start times](#start-times) for each country that has an authentication-international rate.
* The country that we set as your [primary business location](#primary-business-location).

## Exception countries

Authentication-international rates for applicable countries will begin on the same date, unless otherwise specified in your eligibility email, the `exception_countries` array in [eligibility webhooks](#eligibility-webhook), or the `exception_countries` array returned when [requesting](https://developers.facebook.com/docs/whatsapp/pricing/authentication-international-rates#request) the `auth_international_rate_eligibility` field on your WhatsApp Business Account (WABA).

You will always be charged the domestic rate for your primary business location, even if it appears in the either `exception_countries` array.

### Example Scenario

In the following examples, assume this scenario:

* there are three countries, identified by three fictitious country codes: A, B, and C
* countries A and B have authentication-international rates
* country C does not have an authentication-international rate
* the business portfolio has a WABA with ID 12345

Requesting the `auth_international_rate_eligibility` field on WABA 12345 returns:

```
{
  "id": "12345",
  "auth_international_rate_eligibility": {
    "start_time": 1717225200, // Indicates country A start time: June 1, 2024
    "exception_countries": [
      {
        "country_code": "B",
        "start_time": 1719817200 // Indicates country B start time: July 1, 2024
      }
    ]
  }
}
```

Country C is not represented in the response because it does not have an authentication-international rate.

### Scenario 1

The business's primary business location is country C.

* The authentication-international rate applies for country A on June 1, 2024.
* The authentication-international rate applies for country B on July 1, 2024.

### Scenario 2

The business's primary business location is country B.

* The authentication-international rate applies for country A on June 1, 2024.

The authentication-international rate for country B does not apply because the business's primary business location is also country B.

## Webhooks

### Eligibility webhook

An `account_update` webhook will be triggered if your business is deemed eligible for international rates. The webhook will include start times for each country that has an authentication-international rate.

Please see [Rate cards](/docs/whatsapp/pricing#rate-cards) for the list of countries with authentication-international rates.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WABA_ID>",
      "time": <WEBHOOK_SENT_TIMESTAMP>,
      "changes": [
        {
          "field": "account_update",
          "value": {
            "auth_international_rate_eligibility": {
              "exception_countries": [
                {
                  "country_code": "<EXCEPTION_COUNTRY_CODE>",
                  "start_time": <EXCEPTION_START_TIME>
                }
              ],
              "start_time": <START_TIME>
            },
            "event": "AUTH_INTL_PRICE_ELIGIBILITY_UPDATE"
          }
        }
      ]
    }
  ]
}
```

* `<WABA_ID>`  WhatsApp Business Account ID.
* `<WEBHOOK_SENT_TIMESTAMP>`  Unix timestamp indicating when the webhook was sent.
* `<EXCEPTION_COUNTRY_CODE>`  Two-letter country code (e.g. `ID` for Indonesia) of the country with a start time exception.
* `<EXCEPTION_START_TIME>`  Unix timestamp indicating authentication-international rate start time for the exception country.
* `<START_TIME_INDIA>`  Unix timestamp indicating start time for all countries with authentication-international pricing **for which you do not have an exception**.

### Primary business location update webhook

Subscribe to the `account_update` webhook to be notified when the business's [primary business location](#primary-business-location) is set. If we are able to determine the country where your business is based, we will set your location to that country and trigger an `account_update` webhook with the country's two-character country code assigned to the `BUSINESS_PRIMARY_LOCATION_COUNTRY_UPDATE` property.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WABA_ID>",
      "time": <TIMESTAMP>,
      "changes": [
        {
          "field": "account_update",
          "value": {
            "country": "<COUNTRY_CODE>",
            "event": "BUSINESS_PRIMARY_LOCATION_COUNTRY_UPDATE"
          }
        }
      ]
    }
  ]
}
```

* `<WABA_ID>`  WhatsApp Business Account ID.
* `<TIMESTAMP>`  Unix timestamp indicating when the webhook was sent.
* `<COUNTRY_CODE>`  ISO 3166-1 alpha-2 country code, indicating the country where we have determined the business to be based.

### Pricing in messages webhook

If an authentication template message is billed the authentication-international rate, the `pricing` object in status [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks will have `category` set to `authentication_international`.

```
"pricing": {
"billable": true,
"pricing_model": "PMP",
"type": "regular",
"category": "authentication_international"
}
```

## Examples

A business with an **Indonesia** [primary business location](#primary-business-location) send an authentication template message to a WhatsApp user:

| User location | Is business eligible? | Is on/after start time? | Rate billed |
| --- | --- | --- | --- |
| Indonesia | - | - | Authentication |
| India | No | - | Authentication |
| India | Yes | No | Authentication |
| India | Yes | Yes | Authentication-International |

A business with an India primary business location sends an authentication template message to a WhatsApp user:

| User location | Is business eligible? | Is on/after start time? | Rate billed |
| --- | --- | --- | --- |
| India | - | - | Authentication |
| Indonesia | No | - | Authentication |
| Indonesia | Yes | No | Authentication |
| Indonesia | Yes | Yes | Authentication-International |

A business with a primary business location that does not have an authentication-international rate sends an authentication template message to a WhatsApp user:

| User location | Is business eligible? | Is on/after start time? | Rate billed |
| --- | --- | --- | --- |
| Indonesia | No | - | Authentication |
| Indonesia | Yes | No | Authentication |
| Indonesia | Yes | Yes | Authentication-International |
| India | No | - | Authentication |
| India | Yes | No | Authentication |
| India | Yes | Yes | Authentication-International |

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Pagina

[Authentication-international rates](#authentication-international-rates)

[Eligibility](#eligibility)

[Countries with authentication-international rates](#countries-with-authentication-international-rates)

[Start times](#start-times)

[Request](#request)

[Request parameters](#request-parameters)

[Response](#response)

[Response parameters](#response-parameters)

[Primary business location](#primary-business-location)

[Set or edit your primary business location](#set-or-edit-your-primary-business-location)

[Primary business location status](#primary-business-location-status)

[Get your location via API](#get-your-location-via-api)

[Response:](#response-)

[Eligibility email](#eligibility-email)

[Exception countries](#exception-countries)

[Example Scenario](#example-scenario)

[Scenario 1](#scenario-1)

[Scenario 2](#scenario-2)

[Webhooks](#webhooks)

[Eligibility webhook](#eligibility-webhook)

[Primary business location update webhook](#primary-business-location-update-webhook)

[Pricing in messages webhook](#pricing-in-messages-webhook)

[Examples](#examples)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFxmMLX&_nc_oc=Adk0MDKdx0ok-BK_nCRu9o2VoLUsCvcSS3YTSGuiVeiTEp3CHEmUtFFDnPFFuJWwMjY&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=q7qKD-wPJaYdC0MV9ZsBRg&oh=00_Afja2up561o0JTEJmgFY1sn077vOc84guSNO31j3JZqOvA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwEBwnQ4&_nc_oc=AdmOpkTsfGruoAAHVK1H9YfwyFzxRYaDBo2LGWyP4WkKibtFMrMa9lGoBZRy9wKpnHs&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=q7qKD-wPJaYdC0MV9ZsBRg&oh=00_AfjBHyCTQ1AzthfLlMlna5tgOToJqJvtNdhNvnNEeuhirg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[![X](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwF8X-KD&_nc_oc=AdkYRc8mkS5m80V438qLHvaUkjy4uVxq1x1oAyNMFjMWETxcQ5YMI69734whtKeAIqA&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=q7qKD-wPJaYdC0MV9ZsBRg&oh=00_AfhBkz0XviRDgzfB8M_nW7tfEvrAkmLRZ5WvK1ESBCLKmw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[![LinkedIn](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwH4mhnt&_nc_oc=AdkVG_kGsVcK_P1OeUBWJEXcF5ZnM9WhzjPNv90HPNUe9FLv2eePCqyf85tpwLFFwnE&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=q7qKD-wPJaYdC0MV9ZsBRg&oh=00_AfiSdE44fyi8z5xpNqUomxwDoD6ac2iFgMabp5gTdEUOag&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[![YouTube](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwGh9vcp&_nc_oc=AdmkzaI0-6ppCV1-LcMpNbj3nGN-1u9RWnzAn2-KS4iu2FbGDhFCn5CMjp8d_MyvMqc&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=q7qKD-wPJaYdC0MV9ZsBRg&oh=00_Afh_EO9s15iPHJdpR7B0uJIbl8Oskj1zi8AaE-WQ6M9ycg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw) [Tecnologias sociais](/social-technologies/)

---

Noticias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[Forum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e politicas

[Iniciativas de plataforma responsavel](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Politicas do Desenvolvedor](/devpolicy/)[Politica de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Tecnologias sociais](/social-technologies/)

Noticias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Forum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Carreiras](https://www.facebook.com/careers)

Termos e politicas

[Iniciativas de plataforma responsavel](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Politicas do Desenvolvedor](/devpolicy/)

[Politica de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Tecnologias sociais](/social-technologies/)

Noticias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Forum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Carreiras](https://www.facebook.com/careers)

Termos e politicas

[Iniciativas de plataforma responsavel](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Politicas do Desenvolvedor](/devpolicy/)

[Politica de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Tecnologias sociais](/social-technologies/)

Noticias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Forum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1obpaLUX4_zeswiN4yHpq50E7jJ9gCLug0rnnKK0f-wERYiztQbL7cL61_jJLA2P4-Mr16zBiyQwJwd0g70gNd147YVoF9tmgj7PrVlTVDfcnyoHsQEjYvqREyy6VQIOy4NcPbBiYlLxUJhOWhuw)

[Carreiras](https://www.facebook.com/careers)

Termos e politicas

[Iniciativas de plataforma responsavel](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Politicas do Desenvolvedor](/devpolicy/)

[Politica de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Portugues (Brasil)
