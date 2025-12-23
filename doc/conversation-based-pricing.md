+++
id = "conversation-based-pricing"
title = "Conversation-based pricing (DEPRECATED)"
summary = "This document explains how conversation-based pricing works on the WhatsApp Business Platform."
source = "https://developers.facebook.com/docs/whatsapp/conversation-based-pricing"
lang = "en"
tags = ["whatsapp-business-platform", "marketing-messages-lite-api", "webhooks", "messaging", "authentication", "rate-limits", "pricing"]
+++
# Conversation-based pricing (DEPRECATED)

This document explains how conversation-based pricing works on the WhatsApp Business Platform.

Charges are applied per conversation, not per individual message sent or received.

Conversations are 24-hour message threads between you and your customers. They are opened and charged when messages you send to customers are delivered. The criteria that determines when a conversation is opened and how it is categorized is explained below.

Businesses are responsible for reviewing the category assigned to their approved templates. Whenever a template is used, a business accepts the charges associated with the category applied to the template at time of use.

## Conversation categories

Conversations are categorized with one of the following categories:

* **Marketing**  Enables you to achieve a wide range of goals, from generating awareness to driving sales and retargeting customers. Examples include new product, service, or feature announcements, targeted promotions/offers, and cart abandonment reminders.
* **Utility**  Enables you to follow-up on user actions or requests. Examples include opt-in confirmation, order/delivery management (e.g., delivery update); account updates or alerts (for example., payment reminder); or feedback surveys.
* **Authentication**  Enables you authenticate users with one-time pass codes, potentially at multiple steps in the login process (e.g., account verification, account recovery, integrity challenges).
* **Service**  Enables you to resolve customer inquiries.

Marketing, utility, and authentication conversations can only be opened with template messages. Service conversations can be opened with any type of message other than a template message.

See [Message Types](/docs/whatsapp/cloud-api/guides/send-messages#message-types) to learn more about the various types of messages you can send to customers.

## Opening conversations

Conversations are opened when you send a message to a customer under the following conditions.

### Marketing, Utility, and Authentication Conversations

When you send an approved marketing, utility, or authentication template to a customer, we check if an open conversation matching the template's **category** already exists between you and the customer. If one exists, no new conversation is opened. If one does not exist, a new **conversation of that category** is opened, lasting 24 hours.

For example:

* **Hour 0:** You send a targeted promotion (marketing [template message](/docs/whatsapp/cloud-api/guides/send-message-templates)) to a customer. No open marketing conversation exists between you and the customer, so a marketing conversation lasting 24 hours is opened.
* **Hour 4:** The customer completes an order on your site, so you send them an order confirmation (utility template message). No open utility conversation exists between you and the customer, so a utility conversation lasting 24 hours is opened.
* **Hour 10:** You send a shipment confirmation (utility template message) to the customer. An open utility conversation already exists between you and the customer, so a new utility conversation is not opened.

To learn more about template categories and how to choose an appropriate category when creating templates, see [Template Categorization](/docs/whatsapp/updates-to-pricing/new-template-guidelines).

For additional examples, see our

[pricing explainer PDF](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/350685135_631521772182777_716278591301876804_n.pdf?_nc_cat=111&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=EXZMVPNGCkoQ7kNvwHBND-p&_nc_oc=AdluhKJ6ItH2QaJObcnDpUxRFj-rblU2XKkyV0LZRSo5Jph4xcdeJMu3C2oZOFzvxrs&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_Afhg4XaDpy7CxcCgS1h_i7ChphQc60CuaiHceXdkbXqyow&oe=692BF310)

.

### Service conversations

Service conversations are now free. This change does not affect how service conversations are opened.

A service conversation is opened when any message other than a template message is delivered to your customer and no open conversation of **any category** exists between you and the customer.

Note that a [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows) must exist between you and the customer before you can send them a non-template message.

For example:

* **Hour 0:** You send a targeted promotion (marketing template) to a customer. No open marketing conversation exists between you and the customer, so a marketing conversation lasting 24 hours is opened.
* **Hour 4:** The customer messages you. This opens a customer service window between you and the customer, allowing you to send them any type of message for the next 24 hours.
* **Hour 5:** You send an interactive list message to the customer. An open conversation already exists between you and the customer (a marketing conversation in this case), so a service conversation is not opened.
* **Hour 24:** The marketing conversation expires.
* **Hour 25:** The 24-hour customer service window is still open, so you send a second text message to the customer. No open conversation exists between you and the customer anymore, so a service conversation is opened, lasting 24 hours.
* **Hour 26:** The 24-hour customer service window is still open, so you send a third text message to the customer. An open service conversation already exists between you and the customer, so a new service conversation is not opened.

For additional examples, see our

[pricing explainer PDF](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/350685135_631521772182777_716278591301876804_n.pdf?_nc_cat=111&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=EXZMVPNGCkoQ7kNvwHBND-p&_nc_oc=AdluhKJ6ItH2QaJObcnDpUxRFj-rblU2XKkyV0LZRSo5Jph4xcdeJMu3C2oZOFzvxrs&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_Afhg4XaDpy7CxcCgS1h_i7ChphQc60CuaiHceXdkbXqyow&oe=692BF310)

.

## Customer Service Windows

See [Customer Service Windows](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows).

## Conversation duration

Marketing, utility, authentication, and service conversations last 24 hours unless closed by a newly opened [free-entry point conversation](#free-entry-point-conversations).

Free-entry point conversations last 72 hours.

## Multiple conversations

It is possible to have multiple open conversations between you and a customer. This can happen in the following situations:

* An open marketing, utility, or authentication conversation exists between you and a customer and you send them a template message of a different category within 24 hours.
* An open service conversation exists between you and a customer and you send them a template message within 24 hours.

## Free Tier conversations

As of November 1, 2024, you can open an unlimited number of service conversations at no charge. See [Free Service Conversations](/docs/whatsapp/pricing/conversation-based-pricing) to learn more.

## Free Entry Point conversations

A free entry point conversation is opened if (1) a customer using a device running Android or iOS (the desktop and web clients are not supported) messages you via a [Click to WhatsApp Ad](https://www.facebook.com/business/help/447934475640650/) or [Facebook Page Call-to-Action](https://www.facebook.com/help/977869848936797) button and (2) you respond within 24 hours. If you do not respond within 24 hours, a free entry point conversation is not opened and you must use a template to message the customer, which opens a marketing, utility, or authentication conversation, per the category of the template.

The free entry point conversation is opened as soon as your message is delivered and lasts 72 hours. When a free entry point conversation is opened, it automatically closes all other open conversations between you and the customer, and no new conversations will be opened until the free entry point conversation expires.

Once the free entry point conversation is opened, you can send any type of message to the customer without incurring additional charges. However, you can only send non-templates messages if there is an open customer service window between you and the customer.

For example, if the customer messages you via a Click to WhatsApp Ad at 10am and you respond via a template message at 10pm the same day:

* The free entry point conversation starts at 10pm and lasts 72 hours.
* You can send template messages at no charge in those 72 hours.
* You can send non-template messages until 10am the next day, at which point the [customer service window](/docs/whatsapp/cloud-api/guides/send-messages#customer-service-windows) closes, as it is independent of the free entry point conversation (if the customer messages you again, however, it opens another 24-hour customer service window in which you can send any type of message).

## Rates

Rates vary based on conversation category and country/region rate. You can download the rate card below that corresponds to your WhatsApp Business Account's currency to see our rates by country/region for each conversation category.

These rates apply for any conversation opened on or after June 1, 2023 at 12:00 AM, based on WhatsApp Business Account time zone.

### Rate Cards

These rate cards represent the current rates on our platform.

* [Rates in USD](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/488548499_1171612161004324_55612467351100312_n.csv?_nc_cat=111&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=98TEIgTu6EwQ7kNvwF6SgfJ&_nc_oc=AdkWYdgqoVNdImew0NQshwA3FK2ZtHSZhWjN83GXbNWa2W-e-cobIkZwui3lngRcpXg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_AfjOsc4lc5_vTP125Zl3ccMqFweFqrOpPJAgGJMchFcRWQ&oe=692BD00F)
* [Rates in INR](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/487824680_1091145839722631_1669566641969332666_n.csv?_nc_cat=110&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=nZxThRy54rkQ7kNvwEFAAbp&_nc_oc=Adm81ujWVrZIYIOoLn-q-Q7Cj75_EwonzS0TSUn5EE32C8wsf4GEp_QxAiaV2m8C4W0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_AfgMTIfFPUUpmb58YV4Ny4affG8t5rKn4Gu0T1mm4nQ1pA&oe=692BE674)
* [Rates in IDR](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/487922265_2064407927393143_2707471833597803937_n.csv?_nc_cat=102&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=SwX4b1mpphAQ7kNvwF3Rwya&_nc_oc=Adn6nj75GAC6QUzae9uBdEjUiXWGtvxn2Ao3zVMJJrgkRkyIi8yVF2M3H4iugk-8eZ0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_AfiVaOW2ehBKWxm1ZSnzifC_S3BBujdTbwgDlBt-RSOzqQ&oe=692BD12A)
* [Rates in EUR](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/487823906_2411534455881440_2846910812011875203_n.csv?_nc_cat=110&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=bZJExjmsMWIQ7kNvwEGMOJy&_nc_oc=Adk63xZY1LF28ewRDGq_FlQ4-X0Uiw6VIdx_RK_qRdTV5WM0I1PcW3DgsK8oBQc3Pbs&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_Afg6yIcpxgK1e1XPSYGa54fC6wdzK9r8cKgJhXlIDbSiJw&oe=692BD2D2)
* [Rates in GBP](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/487967306_962284482744376_932505914283994051_n.csv?_nc_cat=106&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=7fRKH0qYyRcQ7kNvwEBL7GV&_nc_oc=AdkA0m_ZRttRHeD-EkHU58eJaexXB_UDlq5A_Jj2Fmn0boF6mm77XG7hC5RePn8c95U&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_AfhBZ0TAqDAVh_3GeBnaW6nimGvkFZTbNlo80YguZIYlSw&oe=692BD72B)
* [Rates in AUD](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/487931440_1489088359143806_5504887697981709499_n.csv?_nc_cat=106&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=jwSt4D0BJbsQ7kNvwHV-lUm&_nc_oc=AdkkA2X5iQRpfXjAUbWDhHQJPrbb0Dqz7aeSvW7UmOL15EVGnJuWj_pMryDuZ2c84Mo&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_Afgjh1wDToChRdoOH6wBS5v2n1OR0iGEzsh78en4m3N1hA&oe=692BE78D)

### Authentication-International rates

Starting June 1, 2024, we are introducing authentication-international rates. See [Authentication-International Rates](/docs/whatsapp/pricing/authentication-international-rates) to learn about these rates and if they apply to you.

A partir de 1o de abril de 2025, reduziremos as taxas internacionais de autenticacao no Egito, na Nigeria, no Paquistao e na Africa do Sul para manter precos competitivos com canais alternativos.

### Marketing Messages Lite API pricing

Per-message pricing is coming to MM Lite API. Starting July 1, 2025, Cloud API marketing rates will apply to messages sent via MM Lite API.

Marketing Messages Lite API ("MM Lite API") has different pricing. View the [MM Lite API pricing document](/docs/whatsapp/pricing) for details.

### WhatsApp Business Calling API pricing

The WhatsApp Business Calling API has different pricing. View the [Calling API pricing document](/docs/whatsapp/cloud-api/calling/pricing) for details.

### Updates to rate cards

As announced in June 2024, we may update rates up-to-quarterly. For marketing, updates are to reflect demand and the value these messages deliver. For utility and authentication, our objective is to price on-par with alternate channels.

To support these efforts, we have made the following updates:

* **Effective April 1, 2025**
  + Lowered [authentication-international pricing rates](/docs/whatsapp/pricing/authentication-international-rates) for Egypt, Nigeria, Pakistan, and South Africa.
* **Effective February 1, 2025**

  + Lowered [authentication pricing rates](/docs/whatsapp/pricing#rates) for Egypt, Malaysia, Nigeria, Pakistan, Saudi Arabia, South Africa, and the United Arab Emirates.
  + Added [authentication-international pricing rates](/docs/whatsapp/pricing/authentication-international-rates) for Egypt, Malaysia, Nigeria, Pakistan, Saudi Arabia, South Africa, and the United Arab Emirates.
* **Effective November 1, 2024**
  + [Service conversations](/docs/whatsapp/pricing#service-conversations) are now free for all businesses, including via AI-enabled conversational experiences.
* **Effective October 1, 2024**
  + Updated [pricing rates](/docs/whatsapp/pricing#rates) in India, Saudi Arabia, the United Arab Emirates, and the United Kingdom.
* **Effective August 1, 2024**
  + Lowered utility conversation [pricing rates](/docs/whatsapp/pricing#rates).

### Country calling codes

Charges for conversations are based on the country of the users phone number. We rely on your customer's country calling code and network prefix (area code) to determine their country. The table below shows how we map country codes to countries or regions. If a country is not listed below, it maps to Other.

| Markets | Calling Code   (and network prefix if applicable) |
| --- | --- |
| Countries |  |
| Argentina | 54 |
| Brazil | 55 |
| Chile | 56 |
| Colombia | 57 |
| Egypt | 20 |
| France | 33 |
| Germany | 49 |
| India | 91 |
| Indonesia | 62 |
| Israel | 972 |
| Italy | 39 |
| Malaysia | 60 |
| Mexico | 52 |
| Netherlands | 31 |
| Nigeria | 234 |
| Pakistan | 92 |
| Peru | 51 |
| Russia | 7 |
| Saudi Arabia | 966 |
| South Africa | 27 |
| Spain | 34 |
| Turkey | 90 |
| United Arab Emirates | 971 |
| United Kingdom | 44 |
| North America |  |
| Canada | 1 |
| United States | 1 |
| Rest of Africa |  |
| Algeria | 213 |
| Angola | 244 |
| Benin | 229 |
| Botswana | 267 |
| Burkina Faso | 226 |
| Burundi | 257 |
| Cameroon | 237 |
| Chad | 235 |
| Republic of the Congo (Brazzaville) | 242 |
| Eritrea | 291 |
| Ethiopia | 251 |
| Gabon | 241 |
| Gambia | 220 |
| Ghana | 233 |
| Guinea-Bissau | 245 |
| Ivory Coast | 225 |
| Kenya | 254 |
| Lesotho | 266 |
| Liberia | 231 |
| Libya | 218 |
| Madagascar | 261 |
| Malawi | 265 |
| Mali | 223 |
| Mauritania | 222 |
| Morocco | 212 |
| Mozambique | 258 |
| Namibia | 264 |
| Niger | 227 |
| Rwanda | 250 |
| Senegal | 221 |
| Sierra Leone | 232 |
| Somalia | 252 |
| South Sudan | 211 |
| Sudan | 249 |
| Swaziland | 268 |
| Tanzania | 255 |
| Togo | 228 |
| Tunisia | 216 |
| Uganda | 256 |
| Zambia | 260 |
| Rest of Asia Pacific |  |
| Afghanistan | 93 |
| Australia | 61 |
| Bangladesh | 880 |
| Cambodia | 855 |
| China | 86 |
| Hong Kong | 852 |
| Japan | 81 |
| Laos | 856 |
| Mongolia | 976 |
| Nepal | 977 |
| New Zealand | 64 |
| Papua New Guinea | 675 |
| Philippines | 63 |
| Singapore | 65 |
| Sri Lanka | 94 |
| Taiwan | 886 |
| Tajikistan | 992 |
| Thailand | 66 |
| Turkmenistan | 993 |
| Uzbekistan | 998 |
| Vietnam | 84 |
| Rest of Central & Eastern Europe |  |
| Albania | 355 |
| Armenia | 374 |
| Azerbaijan | 994 |
| Belarus | 375 |
| Bulgaria | 359 |
| Croatia | 385 |
| Czech Republic | 420 |
| Georgia | 995 |
| Greece | 30 |
| Hungary | 36 |
| Latvia | 371 |
| Lithuania | 370 |
| Moldova | 373 |
| North Macedonia | 389 |
| Poland | 48 |
| Romania | 40 |
| Serbia | 381 |
| Slovakia | 421 |
| Slovenia | 386 |
| Ukraine | 380 |
| Rest of Western Europe |  |
| Austria | 43 |
| Belgium | 32 |
| Denmark | 45 |
| Finland | 358 |
| Ireland | 353 |
| Norway | 47 |
| Portugal | 351 |
| Sweden | 46 |
| Switzerland | 41 |
| Rest of Latin America |  |
| Bolivia | 591 |
| Costa Rica | 506 |
| Dominican Republic | 1 (809, 829, 849) |
| Ecuador | 593 |
| El Salvador | 503 |
| Guatemala | 502 |
| Haiti | 509 |
| Honduras | 504 |
| Jamaica | 1 (658, 876) |
| Nicaragua | 505 |
| Panama | 507 |
| Paraguay | 595 |
| Puerto Rico | 1 (787, 939) |
| Uruguay | 598 |
| Venezuela | 58 |
| Rest of Middle East |  |
| Bahrain | 973 |
| Iraq | 964 |
| Jordan | 962 |
| Kuwait | 965 |
| Lebanon | 961 |
| Oman | 968 |
| Qatar | 974 |
| Yemen | 967 |
| Other |  |
| All other countries | Varies by country |

The information in the table above is also available in a CSV file:

* [Country Calling Codes and Regional Rate Mapping CSV](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.8562-6/559604326_1510649803514615_3972087685039081235_n.csv?_nc_cat=111&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=EGYbyVnqksEQ7kNvwEpLMFm&_nc_oc=AdnpK1P8odfHsDyQ2NLoQUc6nHfDQ_iTm7s6jYFw_1ePXH7oLmjUpZltLRl4uZk7azU&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=hArOSVZBHFH5g8WQClf_Pg&oh=00_Afjh7v6oN5Ai_8pLwUnwqXXlUrcIDuDaJAxTicuaf3eNFQ&oe=692BE2D3)

## Webhooks

Pricing information is included in all message webhooks. See:

* Cloud API: [Message Status Updates](/docs/whatsapp/cloud-api/webhooks/payload-examples#message-status-updates)
* On-Premises API: [Message Status Updates](/docs/whatsapp/on-premises/webhooks/components#statuses-object)

## Billing

Billing and billing-related actions are handled through the Meta Business Suite. See [About Billing For Your WhatsApp Business Account](https://www.facebook.com/business/help/2225184664363779) for more information.

## Marketing Messages Lite API

If you are using the Marketing Messages Lite API ("MM Lite API"), such usage is subject to MM Lite API pricing. See the [MM Lite API pricing](/docs/whatsapp/pricing) document for MM Lite API pricing information and rate cards.

## See also

* [Conversations](/docs/whatsapp/conversation-types)
* [About Billing For Your WhatsApp Business Account](https://www.facebook.com/business/help/2225184664363779)
* [Pricing](/docs/whatsapp/pricing)
* [Template Categorization](/docs/whatsapp/updates-to-pricing/new-template-guidelines)
* [Sending messages with Cloud API](/docs/whatsapp/cloud-api/guides/send-messages)
* [Sending messages with On-Premises API](/docs/whatsapp/on-premises/guides/messages)
