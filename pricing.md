![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Fpricing%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Pricing](/docs/whatsapp/cloud-api/groups/pricing)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Groups API Pricing](#groups-api-pricing)

[Per-message pricing on Groups API](#per-message-pricing-on-groups-api)

[How customer service windows work with Groups API](#how-customer-service-windows-work-with-groups-api)

[Pricing information in Message Status webhook](#pricing-information-in-message-status-webhook)

[How read and delivered message status webhooks are processed](#how-read-and-delivered-message-status-webhooks-are-processed)

[How pricing data is displayed in the Message Status webhook](#how-pricing-data-is-displayed-in-the-message-status-webhook)

[Sent message status webhook](#sent-message-status-webhook)

[Delivered / Read message status webhook](#delivered---read-message-status-webhook)

[Parameters](#parameters)

[Identifying billable messages](#identifying-billable-messages)

[Identifying free messages](#identifying-free-messages)

[Messaging analytics for Groups API](#messaging-analytics-for-groups-api)

[Filter parameters for messaging analytics](#filter-parameters-for-messaging-analytics)

[Changes to filter parameters for Groups API](#changes-to-filter-parameters-for-groups-api)

[Response value](#response-value)

[Pricing analytics for Groups API](#pricing-analytics-for-groups-api)

[Filter parameters for pricing analytics](#filter-parameters-for-pricing-analytics)

[Changes to filter parameters for Groups API](#changes-to-filter-parameters-for-groups-api-2)

[Rate cards](#rate-cards)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Groups API Pricing

## Per-message pricing on Groups API

Groups API uses Cloud API's [per-message pricing model](https://developers.facebook.com/docs/whatsapp/pricing/updates-to-pricing#per-message-pricing) to determine if a given message is billable. However, **you are charged each time a billable message is delivered to someone in the group.**

For example, if you send a (billable) marketing template message to a group with 5 WhatsApp users and it is delivered to all 5 users, you would be charged for 5 delivered messages at the going marketing message rate for each recipient's country calling code.

If the message was delivered to only 4 of the 5 users, you would only be charged for the 4 delivered messages.

## How customer service windows work with Groups API

Customer service windows work differently when using Groups API.

When any WhatsApp user in the group messages you, a [customer service window](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows) is opened between you and the entire group (or is refreshed, if one already exists). This allows you to send utility and marketing template messages, or free form messages, for free.

This is different from 1:1 messaging, where when a WhatsApp user messages you, a [customer service window](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows) is opened between you and that customer (or is refreshed, if one already exists).

Everything else about [customer service windows](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows) remains the same.

## Pricing information in Message Status webhook

Pricing information for messages sent using Groups API is included in [messages status webhooks](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/webhooks#pricing-information).

### How `read` and `delivered` message status webhooks are processed

In order for a message status to be considered `read`, it must have been at least `delivered`.

In some scenarios, such as when a user is present in the chat thread when a message arrives, the message is marked `delivered` and `read` nearly simultaneously. In this and other similar scenarios, the `delivered` webhook is not sent back. This is because it is implied that the message was delivered since it has been read.

### How pricing data is displayed in the Message Status webhook

Not all Message Status webhooks include pricing information.

With the introduction of [Per-message Pricing](https://developers.facebook.com/docs/whatsapp/pricing/updates-to-pricing#per-message-pricing), pricing data can be present in `sent`, `delivered` or `read` status webhook. If a message is **charged**, you can expect that at least one webhook (`delivered` or `read`) will contain the pricing information.

### Sent message status webhook

```
// All versions

"pricing": {
  "billable": "<IS_BILLABLE>",
  "pricing_model": "<PRICING_MODEL>",  // new value, see table below
  "type": "<PRICING_TYPE>",            // new property, see table below
  "category": "<CONVERSATION_CATEGORY>"
}
```

### Delivered / Read message status webhook

```
// Version 24.0 and higher

"pricing": {
  "billable": "<IS_BILLABLE?>",
  "pricing_model": "<PRICING_MODEL>",  // new value, see table below
  "type": "<PRICING_TYPE>",            // new property, see table below
  "category": "<CONVERSATION_CATEGORY>"
}
// Version 23.0 and lower
"conversation": {
  "id": "<CONVERSATION_ID>",           // new behavior, see table below
  "expiration_timestamp": "<CONVERSATION_EXPIRATION_TIMESTAMP>",
  "origin": {
    "type": "<CONVERSATION_CATEGORY>"
  }
},

"pricing": {
  "billable": "<IS_BILLABLE?>",
  "pricing_model": "PMP",              // Value is now "PMP" instead of "CBP"
  "type": "<PRICING_TYPE>",            // new property, see table below
  "category": "<PRICING_CATEGORY>"
}
```

### Parameters

| Placeholder | Description |
| --- | --- |
| `<CONVERSATION_ID>` | Version 24.0 and higher:   * The `conversation` object will be omitted entirely   Version 23.0 and lower:   * Value will now be set to a unique ID per-message, instead of per-conversation. |
| `<CONVERSATION_CATEGORY>` | Not changing. |
| `<CONVERSATION_EXPIRATION_TIMESTAMP>` | Not changing. |
| `<IS_BILLABLE?>` | Not changing.  However, the `billable` property will be deprecated in a future [versioned release](https://developers.facebook.com/docs/graph-api/guides/versioning#calling_older_versions), so we recommend that you start using `pricing.type` and `pricing.category` together to determine if a message is billable, and if so, its [billing rate](#identifying-billable-messages). |
| `<PRICING_TYPE>` | New property. Values can be:   * `regular` — indicates the message is billable. * `free_group_customer_service` — indicates the message is free because it was either a utility template message or non-template message sent within a [customer service window](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows). |
| `<PRICING_CATEGORY>` | Values are not changing, but can now be interpreted as follows:   * `group_marketing` — indicates a marketing template message. * `group_utility` — indicates a utility template message. * `group_service` — indicates a non-template message. |

### Identifying billable messages

Billable messages have `pricing.type` set to regular. The `pricing.category` value indicates the rate (`group_marketing` or `group_utility`).

### Identifying free messages

Free messages have `pricing.type` set to `free_group_customer_service`. The `pricing.category` value tells you why it was free:

* `group_utility` — the message was sent within an open group customer service window.
* `group_service` — all non-templates messages are free.

## Messaging analytics for Groups API

The `analytics` field provides the number and type of messages sent and delivered by the phone numbers associated with a specific WABA — for conversation metrics, see Conversation Analytics.

You can use the following endpoint to retrieve analytics for messages sent using Groups API:

```
/<WHATSAPP_BUSINESS_ACCOUNT_ID>?fields=analytics.<FILTER_PARAMETER>.<FILTER_PARAMETER>...
```

### Filter parameters for messaging analytics

For a full list of messaging analytics filter parameters, view the [Messaging Analytics reference](https://developers.facebook.com/docs/whatsapp/business-management-api/analytics#conversation-analytics).

### Changes to filter parameters for Groups API

| Name | Description |
| --- | --- |
| `product_types`  type: Array | *Optional.*  The types of messages (notification messages and/or customer support messages) for which you want to retrieve notifications.  Provide an array and include: \* `101` for group notification messages \* `102` for group customer support messages. \* `103` for inbound group messages  If the above values are not provided, the API call will be return analytics for all messages together.  Inbound product type cannot be queried together with other product types, or you will see an error similar to the one below:   ```  {  "error": {    "message": "Invalid parameter",    "type": "OAuthException",    "code": 100,    "error_subcode": 2388077,    "is_transient": false,    "error_user_title": "Insight Invalid Product Type Combination",    "error_user_msg": "Unable to query this combination of product types. Please query individually and try again.",  } } ``` |

### Response value

Successful responses to the analytics API when querying Groups API message data will return an object similar to the following:

**Note: The country code filter is not supported for group sent messages.**

```
With Country code filter
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
        "delivered": 179715,
        "groups_delivered": 4
      },
      {
        "start": 1543629600,
        "end": 1543716000,
        "sent": 147649,
        "delivered": 139032
      }
      # more data points
    ]
  },
  "id": "102290129340398"
}

Without Country code filter
{
  "analytics": {
    "phone_numbers": [
      "16505550111",
      "16505550112",
      "16505550113"
    ],
    "granularity": "DAY",
    "data_points": [
      {
        "start": 1543543200,
        "end": 1543629600,
        "sent": 196093,
        "delivered": 179715,
        "groups_sent": 2,
        "groups_delivered": 4
      },
      {
        "start": 1543629600,
        "end": 1543716000,
        "sent": 147649,
        "delivered": 139032
      }
      # more data points
    ]
  },
  "id": "102290129340398"
}
```

## Pricing analytics for Groups API

The `pricing_analytics` field allows you to get pricing breakdowns for any messages delivered within a specified date range.

```
GET /<WABA_ID>
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

### Filter parameters for pricing analytics

For a full list of messaging analytics filter parameters, view the [Messaging Analytics reference](https://developers.facebook.com/docs/whatsapp/business-management-api/analytics#pricing-analytics).

### Changes to filter parameters for Groups API

| Name | Description |
| --- | --- |
| `<PRICING_CATEGORIES>`  *Array of strings* | *Optional.*  Array of pricing categories. If you send an empty array, we return results for all pricing categories.  Values can be:   * `GROUP_MARKETING`: Group messages charged the marketing rate. * `GROUP_SERVICE`: Group messages that were not charged. Includes all non-template messages and utility messages sent inside of a customer service window. * `GROUP_UTILITY`: Group messages charged the utility rate. |
| `<PRICING_TYPES>`  *Array of strings* | *Optional.*  Array of pricing types. If you send an empty array, we return results for all pricing types.  Values can be:   * `FREE_GROUP_CUSTOMER_SERVICE`: Free group messages. These are non-template messages and utility messages sent within group customer service windows. * `REGULAR`: Billable messages. Includes all authentication and marketing template messages, and any utility template messages sent outside of a customer service window. |

## Rate cards

Group utility messages are not eligible for volume tiers.

Messaging rates for Groups API are the same as per-messaging pricing rates for 1 to 1 messaging.

[View per-message pricing rate cards](https://developers.facebook.com/docs/whatsapp/pricing/#rate-cards-and-volume-tiers)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Groups API Pricing](#groups-api-pricing)

[Per-message pricing on Groups API](#per-message-pricing-on-groups-api)

[How customer service windows work with Groups API](#how-customer-service-windows-work-with-groups-api)

[Pricing information in Message Status webhook](#pricing-information-in-message-status-webhook)

[How read and delivered message status webhooks are processed](#how-read-and-delivered-message-status-webhooks-are-processed)

[How pricing data is displayed in the Message Status webhook](#how-pricing-data-is-displayed-in-the-message-status-webhook)

[Sent message status webhook](#sent-message-status-webhook)

[Delivered / Read message status webhook](#delivered---read-message-status-webhook)

[Parameters](#parameters)

[Identifying billable messages](#identifying-billable-messages)

[Identifying free messages](#identifying-free-messages)

[Messaging analytics for Groups API](#messaging-analytics-for-groups-api)

[Filter parameters for messaging analytics](#filter-parameters-for-messaging-analytics)

[Changes to filter parameters for Groups API](#changes-to-filter-parameters-for-groups-api)

[Response value](#response-value)

[Pricing analytics for Groups API](#pricing-analytics-for-groups-api)

[Filter parameters for pricing analytics](#filter-parameters-for-pricing-analytics)

[Changes to filter parameters for Groups API](#changes-to-filter-parameters-for-groups-api-2)

[Rate cards](#rate-cards)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfiN3NPgFHIYBDOwlKgZ8B8PUdpIxU7Fom_H5greP3KSvg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfjtthHCSwpzeeMzBst4t8YZSFWoWGNweqUmmRYAJbtGyg&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_Afh5kPjpiXpmDxfwQdud1V7Qi34tBKIhCKYr1vAKydP2Gw&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0wvs3OdSFw4WiH9dRFXSQ8-ocytfda_r6AN8ejKQIz53HfuYbYAzxK3QQ5xVPTD3HEbxu4wN3aLWz6helmS1SnaeNUkrCE_4lmUEgSOKAH8P0U8ywyYodEZcfyh7Y5OPgYDPDGpbXAeAd1oI69tw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfhVuZECz9Qw5v8qN6oxW7OgMI4oze0GpWgxQAE8GlXfbg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2Kbv5UOdxkv5iBVB37VLNQuDwiRTMEYj3r6awZaAj1xqlj74Wq9X19mgPz_HknZCsltW9WKiJX5ldYqPmUrOc0Eo-DAIuJVRiIAUUF0UQuBuU2hDRsfyJW7LkU5wBh84g6ZWkUBf-iTVESIU5XQw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfhazkApy47tm-OQ7cGwcnPQXus5hGgvbNwwgnKjdVIywA&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3T7C-NTBtrxdegTnr18bosymBLH2quvt8Ei0CYQk8o-khREDNwbG03P3yG-59u2DTY_ItUbss_KtGmEjGaNUhWxNY7iHLe9Lt0uD0S6p5UuNrinv_Mt6vcV_f6UO1-cK-AM2Ljz4Qjd9DeLHKbMg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfgfeoEfRLiIYHLafJX3f6-zS6SIkoV4Jv91iqvAykxQDA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT23vhJcyRtdJF4NZIiUyvrFlwyRUAG364Cifxgi-7B-lN0GUSrdgR3itw-yl6KF1Now23KhH1uzEXZigH0tG2DOXkqQbKRm3VibQOGFyWooEYR__85y-cYBSgnqzzX-xvLomGSUibjtVk-W0ig0aA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT302ulpV9q4-sbGVE3Lirk-HSuuD7Cw6pNohclCLRgMeESuVsQJZ8giDXNWwpfAM8lxlZCyFCdgbA_1pvFgv62Zk1GuMql2jYr7IlU4rRPJVEry8OKZbTzL0ZFeRivgjvPSX3SDyD0nBnJbIh4ihWPmU995nkuHVwY)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2A2vNuta2-PP56Gym3iD5ND2Dm96TNZzPJn8quW0AJEiC86j6mHOm1wqqcT0QTRrRI126RJWBgdjFA-sbpTqneq4JUEaFm2jryGvNydThN-rdB1W6hfCSWXXhv0BLye8ZFXQSJqitKem35sN_0gQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfiOk7ZiWhIf7ULISkZvcWUElvLH41aDmOpR9lpgaZdF2Q&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_Afh9gIl4ja7Hd0SG1tvCGTamy7o-AQaXxOW5Ihwz_5j8wQ&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2wvrHFDCNVuDKNoWAiwwNxN6YzQIqU7a0-D85B7mF2Gc-c5bvsIopBOxEA-wOMsYM0mxltrZX2ezg8d7jiYRaKJY_n-BzVbQgtERnps7jzCF9LGq5aO-CHYh2_fcIIxFGP4VEQVryyUKL3vLS2JQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfiiXiEYoRuRZru-p7Q7bOMl8IxdveHqISv8ZyMDqiKGSA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3HUVqiwye3ciqzB-Sgu8awBXiriHlOFSYxqJcb6PMMSmeABDgCQKb3vYYCZaflwbZ8dAz-xhA_aD0veNLPdvidoVzEgpL4jcAZOcky6qDfwgQGfS_VFjVwVtjt-s_YfwLmEXAocq518CvV6uK31Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfhCo4XV4RAg-Wl6jTfTeS-C5lWwK-xlFYtqBVfcpdb4Yw&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1jgqVHWIqrXwXSSf1HklWilNg-ONrlSsjTBv6eE7QbUgEKwYHdv6PQafSAE9zA_5anqynsUMoZGxBn8zuIxhiqHKSAyTpi3hQ0u7TVP1Mkx21LnpWU8eClbzp3mvqGDqZakRXkv1q7RzE0K_-7fw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=mK1sE_6QVOctb80Gnp6n9Q&oh=00_AfhHwpB3iC40Zs_EFS1gGHCSJzcFaDu55UGQ-czV2Te44g&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3sPz3Sc-Uq3KEyL6IuN3DfYpIG4b8UJqbLRp3Z6HT4CSSsZGeaicfYmTCoLvUZB6OCADt9doZSTNsMML8kmgaTH5DX5Veb6ozBl_woH72JG_6i9vDA0JRO09JO_LKkou1rBo8Aseyjr_gj8UYDaw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2XZUK5dywMqjcmvjT5_W2GdcHhMeFWLpsAeA5rlmk4Rbgygk0glzFS8654ByFV9Rt-OOtlvmNIGLpXE3S3PmNhFkuwNvrGCieLFwdL_IVQt-SJrdPtrTjZx6xnEIxw4e1kKbgP3sU3YAMFP1hmUg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)