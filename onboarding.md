![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fonboarding%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Onboarding](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding)

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

[Onboarding](#onboarding)

[Eligibility requirements](#eligibility-requirements)

[Check WABA onboarding status and eligibility](#check-waba-onboarding-status-and-eligibility)

[Checking eligibility status (alternative)](#checking-eligibility-status--alternative-)

[If you want to check ToS and intent request status for the business manager](#if-you-want-to-check-tos-and-intent-request-status-for-the-business-manager)

[Register a phone number on Cloud API](#register-a-phone-number-on-cloud-api)

[For solution providers](#for-solution-providers)

[Onboarding business customers](#onboarding-business-customers)

[For business customers without a partner](#for-business-customers-without-a-partner)

[Sharing event activity](#sharing-event-activity)

[Manage via WhatsApp Account settings](#manage-via-whatsapp-account-settings)

[Configure via API](#configure-via-api)

[Request syntax](#request-syntax)

[Receive MM API for WhatsApp Terms of Service signed webhook (Preferred)](#receive-mm-api-for-whatsapp-terms-of-service-signed-webhook--preferred-)

[Receive onboarding completion webhook (Legacy)](#receive-onboarding-completion-webhook--legacy-)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Onboarding

Onboarding to the Marketing Messages API for WhatsApp (MM API for WhatsApp) is a low-effort upgrade to sending marketing messages with optimizations on Cloud API. See the directions below to onboard your business, whether you integrate with the API directly or work with a partner.

When a business registers for the MM API for WhatsApp, read-only Ad accounts are created that are linked to each of the marketing templates that exist under their business portfolio.

These linked accounts allow a business to:

* fetch their MM API for WhatsApp insights from the Marketing API “Insights API” to view the same

These read-only ad accounts are kept in sync with any changes to marketing templates, so that any changes to marketing templates are reflected in the linked ad entity.

Follow the steps below to Onboard to MM API for WhatsApp.

## Eligibility requirements

In order to use the Marketing Messages API for WhatsApp (MM API for WhatsApp), a business must comply with applicable legal, vertical and content restrictions (country dependent) outlined in [WhatsApp Business Messaging Policies](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2Fpolicy&h=AT0QxChcfC2jDiifYcMN06MLpYzSpFCfP4blAcUlD99C_uHGdzLg3aI3Czzl1Q7wZkPjUwUaF1Lf-LqgvUYEyhze_K5LG73Egh-8JHZQlK92fcZRkPqg8l-0-6CcIWvFzmzoFgz7-AzOfF-m6xYNYw).

In addition, the following requirements must be met:
- WABA is active and not restricted from messaging due to any violations
- WABA is not a WhatsApp Business app account WABA (a.k.a. "Coexistence WABA")
- WABA tax country is not in sanctioned regions
- Owner Business country is not in sanctioned regions

MM API for WhatsApp will continuously update vertical eligibility and policies to comply with various policies and regulations internationally, so these requirements may change.

### Check WABA onboarding status and eligibility

Use the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#fields) endpoint and request the `marketing_messages_onboarding_status` field to check the MM API for WhatsApp eligibility status of a WABA.

Eligible WABAs have this field set to `ELIGIBLE`. If this value is set to `ONBOARDED`, it means the business customer WABA has already been onboarded. See the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#fields) reference for all possible values and their meanings.

**Example request**

```
    curl 'https://graph.facebook.com/v24.0/25002526842541/?fields=marketing_messages_onboarding_status' \
    -H 'Authorization: Bearer EAAAl...'
```

**Example response**

```
    {
      "marketing_messages_onboarding_status": "ELIGIBLE",
      "id": "25002526842541"
    }
```

You can also use the [GET /<BUSINESS\_PORTFOLIO\_ID>/client\_whatsapp\_business\_accounts](/docs/marketing-api/reference/business) endpoint with the following filtering to get a list of all eligible WABAs that have been shared with you.

**Request syntax**

```
GET /<BUSINESS_PORTFOLIO_ID>/client_whatsapp_business_accounts
  ?filtering=[
    {
      'field':'marketing_messages_onboarding_status',
      'operator':'IN',
      'value':['ELIGIBLE']
    }
  ]
```

**Example request**

```
    curl -g 'https://graph.facebook.com/v24.0/19502398688333/client_whatsapp_business_accounts?filtering=[{'field':'marketing_messages_onboarding_status','operator':'IN','value':['ELIGIBLE']}]' \
    -H 'Authorization: Bearer EAAAj...'
```

**Example response**

```
    {
      "data": [
        {
          "id": "46302397361990",
          "name": "San Andreas Roofing",
          "timezone_id": "1",
          "message_template_namespace": "93d3e793_8a4f_49c4_b903_fd72aac80f71"
        }
      ]
    }
```

### Checking eligibility status (alternative)

This field will be deprecated in version 24.0. We recommend using the [`marketing_messages_onboarding_status` field](#checking-eligibility-status) instead.

You can use the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](https://developers.facebook.com/docs/graph-api/reference/whats-app-business-account) endpoint and request the [`marketing_messages_lite_api_status`](#checking-eligibility-status) field to get eligibility status, but this field will be deprecated at a future date, so we recommend using the [method above](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding#eligibility-requirements) instead.

```
GET /<WHATSAPP_BUSINESS_ACCOUNT_ID>?fields=marketing_messages_lite_api_status
```

For partner-managed WABAs, businesses can find eligible WABAs using the following endpoint:

```
GET /<BUSINESS_ID>/client_whatsapp_business_accounts?fields=marketing_messages_lite_api_status
```

See the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#fields) reference for a list of returnable values and their meanings.

### If you want to check ToS and intent request status for the business manager

Use the [GET /<BUSINESS\_PORTFOLIO\_ID>/](/docs/marketing-api/reference/business) endpoint and request the `marketing_messages_onboarding_status` field to check the MM API for WhatsApp eligibility status.

**Permission**
\* `business_management`

#### Example request

```
curl "https://graph.facebook.com/v24.0/52002526842524351/?fields=marketing_messages_onboarding_status" \
-H 'Authorization: Bearer EAAAl...'
```

#### Example response

```
{
  "marketing_messages_onboarding_status":
   {
      "status": "TERM_OF_SERVICE_SIGNED"
      "time": "2025-10-07"
   }
}
```

Use the [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#fields) endpoint and request the `owner_business_info` field to check the onboarding status of the WABA.

**Permissions**
\* `whatsapp_business_management`
\* `whatsapp_business_messaging`

#### Example request

```
curl GET "https://graph.facebook.com/v24.0/69843579834234?fields=owner_business_info" \
-H 'Authorization: Bearer EAAAl...'
```

#### Example response

```
{
  "owner_business_info": {
    "name": "WhatsApp PaidSend Testing",
    "id": "<BM_ID>",
    "marketing_messages_onboarding_status": {
     "status": "TERM_OF_SERVICE_SIGNED" | "REQUEST_SENT" | "NOT_STARTED"
     "time": "2025-08-13"
    }
  },
}
```

## Register a phone number on Cloud API

In order to send a message via MM API for WhatsApp, a business phone number must also be registered on Cloud API. MM API for WhatsApp and Cloud API are used together on the same phone number:

* Cloud API allows a business to send Authentication, Service, Utility, and non-Optimized Marketing template messages and freeform messages, and receive inbound messages from consumers on a business phone number.
* MM API for WhatsApp allows a business to send marketing messages with optimizations, over the same phone number as is registered on Cloud API.

WhatsApp Business phone numbers that are not registered on Cloud API cannot be used with MM API for WhatsApp.

If a business phone number is already registered on Cloud API, phone number verification is not required when registering for MM API for WhatsApp, as no new phone numbers are registered during the MM API for WhatsApp registration process. Existing Phone Numbers remain registered on Cloud API, and will now be eligible to use MM API for WhatsApp in addition to and simultaneously with Cloud API for sending marketing messages.

## For solution providers

If you are a solution provider onboarding your end businesses, refer to [onboard business customers](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers).

## Onboarding business customers

You can instruct your business customers to have someone with full control to the business portfolio to accept the Terms of Service and onboard MM API for WhatsApp via WhatsApp Manager.

[](blob:https://developers.facebook.com/a5ada5f3-8250-4167-9ce1-561684a04c5e)

Reproduzir

-0:16

Silenciar

Configurações visuais adicionais

Entrar em modo de tela cheia

Opções de compartilhamento e relatórios

![](https://static.xx.fbcdn.net/rsrc.php/v4/y4/r/-PAXP-deijE.gif)

Ocorreu um erro

Estamos tendo problemas ao reproduzir este vídeo.

[Saiba mais](https://www.facebook.com/help/396404120401278/list)

1. Open WhatsApp Manager > Overview.
2. In the Alerts section, click Accept terms to get started for Marketing Messages API for WhatsApp.
3. Follow the steps to finish signing MM API for WhatsApp Terms of Service.

Your business customers should be able to start sending messages via MM API for WhatsApp.

If you are unable to access your WhatsApp Manager, [find your business portfolio admin here](/docs/whatsapp/marketing-messages-api-for-whatsapp/support#i-can-t-find-an-admin-user-at-my-company-to-onboard-to-mm-api-for-whatsapp).

## For business customers without a partner

If your business directly integrates with Cloud API without a partner, follow the instructions below to accept the Terms of Service and onboard to MM API for WhatsApp.

* Navigate to the **[App Dashboard](/apps)** > **WhatsApp** > **Quickstart** panel.
* On the **Quickstart** page, locate the "Improve ROI with Marketing Messages API for WhatsApp" card and click the "Get started" button.
* Click on “Continue to integration guide” to accept the Terms of Service

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/476020445_3647418092312679_4465719704295641193_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=3FAGqB7x4r0Q7kNvwF6WRMt&_nc_oc=AdlZi4-zSsSsty2fo9CDm1W76T6JIVSCh_Y3iENaH6WWjA4shIQFp1fCBaOacTnEppk&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=74A0r9hhBXVzh850pjiwoQ&oh=00_Afgly4sKQ3OTBE2s2LYEPWqJSV6coP3pbK4mVcpk4wizlw&oe=6940454B)![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/476114538_1636490170408141_5744881403199109308_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=w1dUOQwVxNEQ7kNvwGZ3J6l&_nc_oc=Adkyq0syAp3hXo6DuRd3nTyhYS_q-ZX1t6d5spsxFVgEdNWqXSNYd4D3H6MH8z_4L8U&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=74A0r9hhBXVzh850pjiwoQ&oh=00_Afjcn59nBI2b39A38q52u1wI3Vk63dH2XVYuDUyGIZ0GXQ&oe=69406CD1)

## Sharing event activity

Once your business is onboarded, message status events (delivery status, read, clicked) will automatically be shared with Meta as part of event activity. Meta does not sell your or your subscribers’ data; this data is used solely to optimize the performance of marketing campaigns.

### Manage via WhatsApp Account settings

If you wish to disable sharing event activity, toggle it off via [WhatsApp Business account setting](https://business.facebook.com/latest/settings/whatsapp_account).

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/532666735_24223328414028742_8881901315029283677_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=q7OaQkTwg5sQ7kNvwGQLIoU&_nc_oc=AdlJ8PPzDfB1AZIt3CU0GX0R57eTmlsEluXG1GRUmkg9_0IEUeGSNSzUCMBygGoxUDI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=74A0r9hhBXVzh850pjiwoQ&oh=00_Afhs-8YqRRcD9uvQfOAxsLvee84dfRkDvXkyD-IaSe0ICQ&oe=694047DC)

### Configure via API

You can also customize sharing event activity on a per-message basis by including the `<message_activity_sharing>` parameter and setting it to a boolean (True/False) in the `marketing_messages` API call payload. The API call overrides the default account configuration for your WhatsApp Business account.

Use the `POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/marketing_messages` endpoint to send a message to a WhatsApp user.

### Request syntax

```
curl 'https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/marketing_messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "message_activity_sharing": "<BOOLEAN>",
  "type": "<MESSAGE_TYPE",
  "<MESSAGE_TYPE":"<MESSAGE_CONTENTS>"
}
```

## Receive MM API for WhatsApp Terms of Service signed webhook (Preferred)

Note: The ToS event value will be available from September 8th, 2025. Refer to the legacy webhook below.

When the MM API for WhatsApp Terms of Service (ToS) is signed for a business, a new [`account_update`](/docs/whatsapp/cloud-api/webhooks/reference/account_update) webhook will be sent for each WhatsApp Business Account (WABA) under your business portfolio. The webhook indicates that the WABA's business has successfully accepted the MM API for WhatsApp ToS. When the webhook is triggered, your WABA will be allowed to send messages through MM API for WhatsApp.

You can use the included business portfolio ID and WABA ID to verify compliance and begin sending messages, or trigger subsequent onboarding actions as needed. This webhook is the preferred webhook to track MM API for WhatsApp onboarding and eligibility status.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<SOLUTION_PROVIDER_BUSINESS_ID>",
      "time": "<WEBHOOK_TIMESTAMP>",
      "changes": [
        {
          "field": "account_update",
          "value": {
            "event": "MM_LITE_TERMS_SIGNED",
            "waba_info": {
              "owner_business_id": "<BUSINESS_PORTFOLIO_ID>",
              "waba_id": "<WABA_ID>"
            }
          }
        }
      ]
    }
  ]
}
```

## Receive onboarding completion webhook (Legacy)

Once you have completed onboarding and linked Ad accounts have been set up, an [`account_update`](/docs/whatsapp/cloud-api/webhooks/reference/account_update) webhook will be sent for each WABA under your business portfolio to indicate that onboarding has successfully completed. This webhook contains the ID of the read-only Ad account that each WABA is linked to, for use when calling Insights APIs.

Note: This webhook is considered legacy for MM API for WhatsApp onboarding. Please use the MM API for WhatsApp Terms of Service signed webhook.

Important: The `ad_account_linked` webhook event will no longer be fired since partners will not receive access to ad accounts.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WABA_ID>",
      "time": "<WEBHOOK_TIMESTAMP>",
      "changes": [
        {
          "field": "account_update",
          "value": {
            "event": "AD_ACCOUNT_LINKED",
            "waba_info": {
              "waba_id": "<WABA_ID>",
              "ad_account_id": "<AD_ACCOUNT_ID>",
              "owner_business_id": "<BUSINESS_PORTFOLIO_ID>"
            }
          }
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Onboarding](#onboarding)

[Eligibility requirements](#eligibility-requirements)

[Check WABA onboarding status and eligibility](#check-waba-onboarding-status-and-eligibility)

[Checking eligibility status (alternative)](#checking-eligibility-status--alternative-)

[If you want to check ToS and intent request status for the business manager](#if-you-want-to-check-tos-and-intent-request-status-for-the-business-manager)

[Register a phone number on Cloud API](#register-a-phone-number-on-cloud-api)

[For solution providers](#for-solution-providers)

[Onboarding business customers](#onboarding-business-customers)

[For business customers without a partner](#for-business-customers-without-a-partner)

[Sharing event activity](#sharing-event-activity)

[Manage via WhatsApp Account settings](#manage-via-whatsapp-account-settings)

[Configure via API](#configure-via-api)

[Request syntax](#request-syntax)

[Receive MM API for WhatsApp Terms of Service signed webhook (Preferred)](#receive-mm-api-for-whatsapp-terms-of-service-signed-webhook--preferred-)

[Receive onboarding completion webhook (Legacy)](#receive-onboarding-completion-webhook--legacy-)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=enzVyas0qSOEIGkkq4snOg&oh=00_AfhfBLPdPFlkuhzdfBHQydVM17QoI41NjMutmMz6kff1_g&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=enzVyas0qSOEIGkkq4snOg&oh=00_Afgy-zNASNHwAPO0u611_bLmNB1Qifo0h4kLzl8EWZrvqQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=enzVyas0qSOEIGkkq4snOg&oh=00_Afi_4gYMHIlI0cdqyBDIING8UHyv2PPAF5zRVBk-QZCwlw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=enzVyas0qSOEIGkkq4snOg&oh=00_AfhXLisaui8-32EqfX45QJJmrvNZH-H9pKKBlM11RLTDDA&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=enzVyas0qSOEIGkkq4snOg&oh=00_Afjg3rjeiWpDSLkw8lHLvQIJzj4fY-h3a1dTK9uuHBEtQA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2586sv9ep-_I1_v1HoQHUfoMXK7aJ6whoC2NY9wxLVKdHAOYD8ystwarCJ-8THfZPBfFl3grTbdUY8EBpA6rZLfn33v3ovpxUrQ6KG49CERsIt8-9KU62SyDw_MLBnhGVLHiTvvTWjT-D9OJNwJg)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)