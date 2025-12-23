![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Foverview%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)

  + [Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)
  + [Official Business Accounts](/docs/whatsapp/official-business-accounts)
  + [Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)
  + [Business profiles](/docs/whatsapp/business-profiles)
  + [Display names](/docs/whatsapp/display-names)
  + [Receber aceitação](/docs/whatsapp/overview/getting-opt-in)
  + [Identity Change](/docs/whatsapp/overview/identity-change)
  + [Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)
* [Preços](/docs/whatsapp/pricing)
* [Limites de mensagens](/docs/whatsapp/messaging-limits)
* [Webhooks](/docs/whatsapp/webhooks)
* [Parceiros de soluções](/docs/whatsapp/solution-providers)
* [Cadastro Incorporado](/docs/whatsapp/embedded-signup)
* [Prévias de links](/docs/whatsapp/link-previews)
* [Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[About the WhatsApp Business Platform](#about-the-whatsapp-business-platform)

[Core APIs and capabilities](#core-apis-and-capabilities)

[WhatsApp Cloud API](#whatsapp-cloud-api)

[Business Management API](#business-management-api)

[Marketing Messages Lite API](#marketing-messages-lite-api)

[Webhooks](#webhooks)

[Technical foundations](#technical-foundations)

[HTTP protocol and API requests](#http-protocol-and-api-requests)

[JSON responses](#json-responses)

[Authentication and authorization](#authentication-and-authorization)

[Key resources](#key-resources)

[Business portfolios](#business-portfolios)

[WhatsApp business accounts (WABA)](#whatsapp-business-accounts--waba-)

[Business phone numbers](#business-phone-numbers)

[Message templates](#message-templates)

[Test resources](#test-resources)

[Tools and integrations](#tools-and-integrations)

[WhatsApp Manager](#whatsapp-manager)

[Third-party SDKs](#third-party-sdks)

[Postman collection](#postman-collection)

[Security and performance](#security-and-performance)

[Throughput](#throughput)

[Encryption](#encryption)

[Scaling](#scaling)

[Rate limits](#rate-limits)

[Terms and policies](#terms-and-policies)

[User opt-in](#user-opt-in)

[Next steps](#next-steps)

[Voltar para Português (Brasil)](/docs/whatsapp/overview/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 21 de nov
Atualização em Português (Brasil): 5 de nov

# About the WhatsApp Business Platform

The WhatsApp Business Platform enables businesses to communicate with customers at scale.

This documentation is intended for developers using our APIs. If you are looking for information on other ways to use WhatsApp for your business see the [WhatsApp Business site](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2F&h=AT3vClA3shUyUARb9Z-0sxV0WR_3J_7ohk31BMgin8NbRNQEEdCs1F5ceNKkr2Bf1btxv5PJg-WnURWMZ-5WbKLZjdTa9Niebal8wCQDSsFgothlkg0q5EQuaBfr3JXMqs6X_uHV9RmxG3vLbCqjEw).

## Core APIs and capabilities

### WhatsApp Cloud API

WhatsApp Cloud API enables you to programmatically message and call on WhatsApp. You can use Cloud API to send users a variety of messages, from simple text messages to rich media and interactive messages.

WhatsApp Cloud API includes:

* **Messaging:** Send text messages, rich media, and interactive messages
* **Calling:** Make and receive calls to customers
* **Groups:** Create, manage, and message WhatsApp group conversations

WhatsApp messaging provides a powerful and private way to engage with customers. Use Cloud API to:

* Send order confirmations and shipping updates
* Share appointment availability and other reminders
* Drive upsell and cross-sell opportunities
* Facilitate end-to-end transactions, from product discovery to payment
* Enable multi-factor authentication or one-time passwords to verify accounts and users
* Deliver custom interactive conversational experiences

[Learn more about message types on WhatsApp Cloud API.](/docs/whatsapp/cloud-api/guides/send-messages)

### Business Management API

The WhatsApp Business Management API enables you to programmatically manage a WhatsApp Business Account and its associated assets.

Manage account assets with Business Management API like:

* **Business phone numbers:** Add and remove phone numbers associated with your business
* **Templates:** Create and modify message templates for scalable messaging.

Business Management API also gives you access to account analytics like:

* **Messaging analytics:** The number and type of messages sent and delivered.
* **Pricing analytics:** Granular pricing breakdowns for delivered messages.
* **Template analytics:** Sent/read/delivered template metrics, alongside template message button clicks.

* [Learn more about message templates.](/docs/whatsapp/business-management-api/message-templates)
* [Learn more about managing business phone numbers.](/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers)
* [Learn more about account analytics.](/documentation/business-messaging/whatsapp/analytics)

### Marketing Messages Lite API

MM Lite is an API for sending optimized marketing messages on WhatsApp.

When you send marketing messages through the MM Lite API, you can access new features not available on Cloud API and get automatic optimizations, so high engagement messages can reach more customers.

The MM Lite API includes:

* **Quality-based delivery:** Up to 9% higher marketing message deliveries over Cloud API for high engagement content.
* **Automated creative optimizations:** Automatic enhancements to marketing creative to increase message performance.
* **Performance benchmarks and recommendations:** Comparison of read and click rates versus similar templates from businesses in your region.
* **Conversion metrics:** Measure marketing messages that lead users to perform app events such as 'Add to Cart', 'Checkout Initiated', or 'Purchase'.

[Learn more about the Marketing Messages Lite API.](/docs/whatsapp/marketing-messages-lite-api/)

### Webhooks

Webhooks deliver JSON payloads to your server for message status updates, incoming messages, asynchronous error handling, and many other notification utilities.

The platform relies heavily on webhooks, as the contents of any message sent from a WhatsApp user to your business phone number is communicated via webhook, and all outgoing message delivery status updates are reported via webhook.

[Learn more about webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks).

## Technical foundations

### HTTP protocol and API requests

The WhatsApp Business Platform is built on [Graph API](/docs/graph-api/overview) and uses HTTP protocol. API requests include path, body, and header parameters.

#### Example: Sending a text message using cURL

```
curl 'https://graph.facebook.com/v17.0/106540352242922/messages' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer EAAJB...' \
  -d '{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "+16505555555",
    "type": "text",
    "text": {
      "preview_url": true,
      "body": "Here's the info you requested! https://www.meta.com/quest/quest-3/"
    }
  }'
```

[Learn more about the Graph API.](/docs/graph-api/)

### JSON responses

API responses are formatted in JSON.

#### Example: Requesting a business phone number's metadata

```
{
  "verified_name": "Lucky Shrub",
  "code_verification_status": "VERIFIED",
  "display_phone_number": "15550783881",
  "quality_rating": "GREEN",
  "platform_type": "CLOUD_API",
  "throughput": {
    "level": "STANDARD"
  },
  "webhook_configuration": {
    "application": "https://www.luckyshrub.com/webhooks"
  },
  "id": "106540352242922"
}
```

### Authentication and authorization

Authentication uses OAuth (not 2.0) access tokens, while permissions restrict access to specific resources.

* [Learn more about access tokens.](/docs/whatsapp/access-tokens)
* [Learn more about permissions.](/docs/whatsapp/permissions)

## Key resources

### Business portfolios

A business portfolio allows organizations to bring all their Meta business assets together so they can be managed in one place. On the WhatsApp Business Platform, a business portfolio mainly serves as a container for WhatsApp Business Accounts (WABA). You must have a business portfolio to use the platform.

Business portfolios can be verified, and verification status factors into improved functionality, such as higher throughput and [Official Business Account](/docs/whatsapp/official-business-accounts) status.

[Learn more about business portfolios.](https://www.facebook.com/business/help/486932075688253)

### WhatsApp business accounts (WABA)

A WhatsApp Business Account represents your business, storing metadata and linking to phone numbers, templates, and analytics.

[Learn more about WhatsApp Business Accounts.](/docs/whatsapp/overview/business-accounts)

### Business phone numbers

Business phone numbers, real or virtual, are used for sending and receiving WhatsApp messages. They can have display names and earn Official Business Account status.

[Learn more about business phone numbers.](/docs/whatsapp/cloud-api/phone-numbers)

### Message templates

Templates are customizable messages that you can construct in advance of sending them. Template messages generally require approval before you can send them.

Templates are useful for messaging at scale. They are also the only type of message that can be sent to WhatsApp users outside of a [customer service window](/docs/whatsapp/cloud-api/guides/send-messages/#customer-service-windows).

Templates have quality scores and are subject to various messaging limits.

[Learn more about message templates.](/docs/whatsapp/business-management-api/message-templates)

### Test resources

When you [get started with Cloud API](/docs/whatsapp/cloud-api/get-started), a test WABA and test business phone number are automatically created for you. Test WABAs and test phone numbers are useful for testing purposes, as they have relaxed messaging limits and don't require a payment method on file in order to send template messages.

You can delete your business portfolio and its test resources if:

* You are an admin on the business portfolio associated with the app
* No other apps are associated with the business portfolio
* The business portfolio is not associated with any other WABAs
* The WABA is not associated with any other business phone numbers.

To delete your business portfolio and its test resources:

1. Go to the **App Dashboard > WhatsApp > Configuration** panel.
2. Locate the **Test Account** section.
3. Click the **Delete** button.

We recommend using our API Playground when testing endpoints. You can find the playground in the "API Reference" section on the left sidebar of this page. In each reference, there is a "Try it" button which opens the playground.

Also helpful for testing is our [Postman collection](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.postman.com%2Fmeta%2Fwhatsapp-business-platform%2F&h=AT0Qff--AYyX0KU8W5qZBaSPR5vgbdFM8R4yH439ufDLc-ztRsa6HfebNCzHaOlrfvr234tcF-3Aterqtq7pZl9wHm4Mne7iVLcMhNXgCC8r729A9VWpkzeosPmzdlJCXqN_jahE9zEqXvoxGlj_wg).

## Tools and integrations

### WhatsApp Manager

WhatsApp Manager is a web app for managing WABAs, phone numbers, templates, and reviewing analytics.

[Access WhatsApp Manager](https://business.facebook.com/wa/manage/home/)

### Third-party SDKs

Some SDKs, like [PyWa](https://l.facebook.com/l.php?u=https%3A%2F%2Fpywa.readthedocs.io%2Fen%2F2.0.1%2F&h=AT1yz3mCF22Bqfk1XQKBCUKP4oFCs6iSqsg78HLvkK8bR2TBkO2MaKAh4BqS2SDIm5RMCUjwmiEtH2NO1vZv-9LGQpgG_rhTmJSrMVg9QPCwrt8cS0XpjhhEkgMiklgpTFExNtlvlbIrWMktj3-UJQ) (Python wrapper), are available but are not maintained or endorsed by Meta.

### Postman collection

The official Postman collection lets you execute common API queries.

[Access the WhatsApp Business Platform Postman collection](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.postman.com%2Fmeta%2Fwhatsapp-business-platform%2F&h=AT2oA2p7-CJrPz7zqx9OPcY8eVzyWGKuUwk6kCqZGNG07FLUDrrCvKWDN6T7V-b0ABrl4bb8dpkvUZlY94gJA0amPi_KhAtLXgVpV7RjVRtDCoEcRLmH99gNYQAoL7LT4gvLFb8VBld6svYohbZd8Q).

## Security and performance

### Throughput

Business phone numbers can send up to 80 messages per second by default, with capacity upgrades available.

[Learn more about throughput.](/docs/whatsapp/throughput)

### Encryption

With the Cloud API, every WhatsApp message continues to be protected by Signal protocol encryption that secures messages before they leave the device. This means messages with a WABA are securely delivered to the destination chosen by each business.

The Cloud API uses industry standard encryption techniques to protect data in transit and at rest. The API uses Graph API for sending messages and Webhooks for receiving events, and both operate over industry standard HTTPS, protected by TLS. See our Encryption Overview whitepaper for additional details.

See the [WhatsApp Encryption Overview whitepaper](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Fsecurity%2FWhatsApp-Security-Whitepaper.pdf&h=AT2zkdJVdSUrzJ9O7itbMO_5Wqs6ax-XUuGXVP_j7AgBigctz84cWSDeOT6zGPDQWD2SNgdPM32PkXIaYjO8vjDpnCoz1fLmLFL__VL_n_JGDECnB0gX3Zl3dKan2FiSfJ-8U3kxvOn3KIL-P6sr0g) for additional details.

### Scaling

The Cloud API automatically scales usage within your rate limits.

### Rate limits

Requests made by your app on your WhatsApp Business Account (WABA) are counted against your app's request count. An app's request count is the number of requests it can make during a rolling one hour.

For the following endpoints, your app can make 200 requests per hour, per app, per WABA, by default. For active WABAs with at least one registered phone number, your app can make 5000 requests per hour, per app, per active WABA.

| Type of request | Endpoint |
| --- | --- |
| `GET` | `/<WHATSAPP_BUSINESS_ACCOUNT_ID>` |
| `GET`, `POST`, and `DELETE` | `/<WHATSAPP_BUSINESS_ACCOUNT_ID>/assigned_users` |
| `GET` | `/<WHATSAPP_BUSINESS_ACCOUNT_ID>/phone_numbers` |
| `GET`, `POST`, and `DELETE` | `/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates` |
| `GET`, `POST`, and `DELETE` | `/<WHATSAPP_BUSINESS_ACCOUNT_ID>/subscribed_apps` |
| `GET` | `/<WHATSAPP_BUSINESS_ACCOUNT_TO_NUMBER_CURRENT_STATUS_ID>` |

For the following [Credit Line API](/docs/whatsapp/embedded-signup/manage-accounts/share-and-revoke-credit-lines) requests, your app can make 5000 requests per hour.

| Type of request | Endpoint |
| --- | --- |
| `GET` | `/<BUSINESS_ID>/extendedcredits` |
| `POST` | `/<EXTENDED_CREDIT_ID>/whatsapp_credit_sharing_and_attach` |
| `GET` and `DELETE` | `/<ALLOCATION_CONFIG_ID>` |
| `GET` | `/<EXTENDED_CREDIT_ID>/owning_credit_allocation_configs` |

For more information on how to get your current rate usage, see [Headers](/docs/graph-api/overview/rate-limiting/#headers).

In addition, the platform applies several message rate limits:

* Test message rate limit (for unverified WABAs)
* Quality rating and messaging limits (for verified WABAs)
* Capacity rate limit (for all accounts)
* Business phone rate limit (per phone number)

#### Pair rate limits

Business phone numbers can send 1 message every 6 seconds to the same WhatsApp user (0.17 messages/second), which equals about 10 messages per minute or 600 per hour. Exceeding this limit triggers [error code 131056](/docs/whatsapp/cloud-api/support/error-codes#throttling-errors) until you are back within the allowed rate.

You may send up to 45 messages in a 6-second burst, but this "borrows" from your future quota. After a burst, you must wait the equivalent time it would take to send those messages at the normal rate (e.g., a burst of 20 requires a ~2-minute wait before sending more to that user).

To manage post-burst throttling, if a send request fails, retry after 4^X seconds (starting with X=0 and increasing X by 1 after each failure) until successful.

## Terms and policies

### User opt-in

You must obtain user [opt-in](/docs/whatsapp/overview/getting-opt-in) before sending message templates. Opt-in must clarify your business name and intent.

[Learn more about the WhatsApp Business Messaging Policy.](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fbusiness-policy%2F&h=AT2JagFhiURqquiXNrsBS9YmeHvFc6dIwzEa7kJmBbmuoyVqki_nMM91QAf1rlm4gyW5MYvSPI1IEUHRJ9eJiQeF2gdGHeVMwNrPqhK0PYx75beWyl7pKXBtyZnxkDfuoA9J6WF-ekUJilrGYtk29g)

### Terms and policies

All platform use must comply with WhatsApp's terms and policies. Using unauthorized third-party tools is prohibited.

* [Learn more about terms and policies.](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fbusiness-terms%2F&h=AT34Lx7qR5rdu0bPYGuEa8UrPzScPnrMq5XkLUgN8icLAKATFeVH1kMrDxjg-87EzaIGy1EZ-mFUEUgLQkspC_PK8VIT5afW1zoUMGQFekd0HdY7Yq-YfRX2z-vtPLyt29-rKoAuKNbILe-oOLfUfA)

## Next steps

[Get started with the WhatsApp Business Platform.](/docs/whatsapp/cloud-api/get-started)

**Learn more**

* [Display names](/docs/whatsapp/display-names/)
* [Phone numbers](/docs/whatsapp/cloud-api/phone-numbers)
* [Pricing](/docs/whatsapp/pricing/)
* [Webhooks](/docs/whatsapp/webhooks/)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[About the WhatsApp Business Platform](#about-the-whatsapp-business-platform)

[Core APIs and capabilities](#core-apis-and-capabilities)

[WhatsApp Cloud API](#whatsapp-cloud-api)

[Business Management API](#business-management-api)

[Marketing Messages Lite API](#marketing-messages-lite-api)

[Webhooks](#webhooks)

[Technical foundations](#technical-foundations)

[HTTP protocol and API requests](#http-protocol-and-api-requests)

[JSON responses](#json-responses)

[Authentication and authorization](#authentication-and-authorization)

[Key resources](#key-resources)

[Business portfolios](#business-portfolios)

[WhatsApp business accounts (WABA)](#whatsapp-business-accounts--waba-)

[Business phone numbers](#business-phone-numbers)

[Message templates](#message-templates)

[Test resources](#test-resources)

[Tools and integrations](#tools-and-integrations)

[WhatsApp Manager](#whatsapp-manager)

[Third-party SDKs](#third-party-sdks)

[Postman collection](#postman-collection)

[Security and performance](#security-and-performance)

[Throughput](#throughput)

[Encryption](#encryption)

[Scaling](#scaling)

[Rate limits](#rate-limits)

[Terms and policies](#terms-and-policies)

[User opt-in](#user-opt-in)

[Next steps](#next-steps)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFxmMLX&_nc_oc=Adk0MDKdx0ok-BK_nCRu9o2VoLUsCvcSS3YTSGuiVeiTEp3CHEmUtFFDnPFFuJWwMjY&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=BdKmJXw231jF0yUjRxGvgQ&oh=00_AfhJHNj8m97I4f0sEQtViJahMynjBlwRA7eJ1bUOlzibDQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwEBwnQ4&_nc_oc=AdmOpkTsfGruoAAHVK1H9YfwyFzxRYaDBo2LGWyP4WkKibtFMrMa9lGoBZRy9wKpnHs&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=BdKmJXw231jF0yUjRxGvgQ&oh=00_AfgxWYk08X_1u1OVJjBR-cXbP086UqOTNIPq8Vunhn52VQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[![X](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwF8X-KD&_nc_oc=AdkYRc8mkS5m80V438qLHvaUkjy4uVxq1x1oAyNMFjMWETxcQ5YMI69734whtKeAIqA&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=BdKmJXw231jF0yUjRxGvgQ&oh=00_AfiKQheMLpKgB7eAxTCDJuNg5RD3dsAJXR2-mW3GYHdrBw&oe=692BC22A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[![LinkedIn](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwH4mhnt&_nc_oc=AdkVG_kGsVcK_P1OeUBWJEXcF5ZnM9WhzjPNv90HPNUe9FLv2eePCqyf85tpwLFFwnE&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=BdKmJXw231jF0yUjRxGvgQ&oh=00_Afi2G5Y-ngEY9eNH90k-0xyv4Dz5WstPkZ1Ml6iqqsoOTw&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[![YouTube](https://scontent.fcgh5-2.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwGh9vcp&_nc_oc=AdmkzaI0-6ppCV1-LcMpNbj3nGN-1u9RWnzAn2-KS4iu2FbGDhFCn5CMjp8d_MyvMqc&_nc_zt=14&_nc_ht=scontent.fcgh5-2.fna&_nc_gid=BdKmJXw231jF0yUjRxGvgQ&oh=00_Afhvgu-HMMZq6V2gKqItRG1BatrSsmsP4GhX3P0TgDDHhw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1LWnvvlzkgzqNdQ2dQ52ME-iMxzxHpxXzb2YpyVyqSKaVsIfD-IhuX07ZjKaUgiHTHrKUJ8JfuNve1gvz-qhcSb9R_t7aV9IVasv_Mwl2eEHlxfz32A5DQnG41YMZrrgWGfSfr9XgnWggPd4G_Wg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)