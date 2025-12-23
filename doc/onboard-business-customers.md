![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fonboard-business-customers%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Onboard business customers](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers)

[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)

* [Get started](/docs/whatsapp/marketing-messages-api-for-whatsapp/get-started)
* [Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)
* [Features](/docs/whatsapp/marketing-messages-api-for-whatsapp/features)
* [Onboard business customers](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers)
* [Pricing](/docs/whatsapp/marketing-messages-api-for-whatsapp/mm-api-pricing)
* [Support](/docs/whatsapp/marketing-messages-api-for-whatsapp/support)
* [Changelog](/docs/whatsapp/marketing-messages-api-for-whatsapp/changelog)

Nesta Página

[Onboard business customers](#onboard-business-customers)

[Before you begin](#before-you-begin)

[Solution partner integration overview](#solution-partner-integration-overview)

[Onboarding yourself](#onboarding-yourself)

[Register yourself for MM API for WhatsApp](#register-yourself-for-mm-api-for-whatsapp)

[Submit for app review for Advanced App permissions](#submit-for-app-review-for-advanced-app-permissions)

[Onboard a business to Marketing Messages for WhatsApp using the Intent API](#onboard-a-business-to-marketing-messages-for-whatsapp-using-the-intent-api)

[Help the business set up Conversion measurement](#help-the-business-set-up-conversion-measurement)

[Sending messages](#sending-messages)

[Viewing metrics](#viewing-metrics)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Onboard business customers

The MM API for WhatsApp onboarding process is designed to be simple for you as a partner to adopt, making it quick and easy for [solution providers](/docs/whatsapp/solution-providers) (including Solution Partners, Tech Providers, and Tech Partners) to onboard current customers from Cloud API onto the MM API for WhatsApp. If your business directly integrates with Cloud API without a partner, follow the instructions below to accept the Terms of Service and onboard to the MM API for WhatsApp via WhatsApp Manager.

## Before you begin

Your app must have advanced access for the following permissions:

* **`whatsapp_business_messaging`**: This permission allows the app to call the MM API for WhatsApp to send messages.
* **`whatsapp_business_management`**: This permission enables the app to manage WABAs, Phone Numbers, and Templates via [WhatsApp Business Management API](/docs/whatsapp/business-management-api/analytics).
* **`ads_read`** (optional): This permission grants the app access to the [Insights API](/docs/marketing-api/insights), allowing partners to retrieve metrics on conversions.

If your app does not already have advanced access for these permissions, request advanced access via [App Review](/docs/whatsapp/solution-providers/app-review).

## Solution partner integration overview

To assist your customers in using the MM API for WhatsApp, several steps are required:

| Step | Notes |
| --- | --- |
| 1: Onboard yourself | Enroll via [App Dashboard](https://developers.facebook.com/apps) and follow instructions under the [Onboarding yourself](#onboarding-yourself). |
| 2: Send messages | Same Template endpoint and message send payload as Cloud API - only the ‘send message’ endpoint changes. |
| 3: View metrics | **New!** Integrate with the Insights API to view the metrics as Cloud API (sent/read/delivered), plus new metrics like Website and App conversions. |

## Onboarding yourself

### Register yourself for MM API for WhatsApp

To enroll, a solution provider must:

1. Navigate to the **[App Dashboard](/apps)** > **WhatsApp** > **Quickstart** panel
2. On the **Quickstart** page, locate the "Improve ROI with Marketing Messages API for WhatsApp" card and click the "Get started" button
3. Request any missing app review permissions by clicking the “Request permission” button. See “[Submit for app review](/docs/whatsapp/solution-providers/app-review)” for more information
4. Click on “Continue to integration guide” to accept the Terms of Service

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/475969838_666164382411179_8539011248692952115_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=JCKBNRmxjw0Q7kNvwHeiooq&_nc_oc=AdmS-gMhKTp3bKGvVCFureSd_MLq83zTnWEAtrFsia1AUeYirZglwBx4-OIqC5DHFLw&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfhLFmjlT_k4RmBWJQktJlxga50xqW0p5JBO8O8LahynCA&oe=69404440)![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/540765034_1761649757794419_9069938397320792839_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=vVLX3r4biZoQ7kNvwGhRck3&_nc_oc=AdntFxhUTcFz_TA__H2KL-jjodMWTAv71f1yQyJy3WZK0JoqweI8Go9-cuwmeqLRW-c&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_Afh0PPdx3JtbZqczuwizsI_RjByONYgC9CEjroGjzCdpkA&oe=69406A99)

### Submit for app review for Advanced App permissions

Solution Providers must use an App with the following Advanced App permissions, when using the MM API for WhatsApp.

If you do not already have an App with the following Advanced App Permissions, it is necessary for your App to go through [App review](/docs/whatsapp/solution-providers/app-review):

| Advanced App Permission | Required in order to do the following on behalf of your customer |
| --- | --- |
| `whatsapp_business_messaging` | Call the MM API for WhatsApp ‘send messages’ endpoint, to send messages via Marketing Messages API for WhatsApp |
| `whatsapp_business_management` | Call WABA, Phone Number, and Template endpoints, for managing WABAs, Phone Numbers, and Templates; and retrieve basic metrics via [WhatsApp Business Management API](/docs/whatsapp/business-management-api/analytics) |
| `ads_read` (optional) | This permission is optional, and is only required to call the [Insights API](/docs/marketing-api/insights), allowing a partner to fetch advanced metrics on conversions (e.g. Web conversions, App conversions) |

For the app review submission, prepare a screen recording of how each permission is used. It is recommended to show a sample of each action in the “Required in order to do …” column above, to demonstrate each permission in use.

## Onboarding end businesses

There are multiple ways that a partner can onboard a business they work with to the MM API for WhatsApp, and fetch the required access tokens needed to send messages and fetch metrics on their behalf:

* **via Whatsapp Manager** (recommended)
* **via Embedded Signup**

### Self-onboard to MM API for WhatsApp via WhatsApp Manager (recommended)

If your business integrates with Cloud API with a solution provider, they can [onboard directly via WhatsApp Manager](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding).

### Onboard a business to MM API for WhatsApp using Embedded Signup

MM API for WhatsApp has its own embedded signup flow for Solution Providers to use, which:

* allows your clients to register for Cloud API and MM API for WhatsApp
* allows you to request an access token with the necessary permissions to send messages via MM API for WhatsApp and retrieve metrics from the Insights API on behalf of your customers.

#### Step 1: Integrate with the Facebook Login SDK

If you have not already done so for Cloud API, set up the Facebook JavaScript SDK and Facebook Login to embed the signup flow into your website or client portal. You may embed the flow in multiple webpages or portals that you own.

#### Step 2: Set up a new permission configuration

Follow the instructions in [Step 2 of the Embedded Signup docs](/docs/whatsapp/embedded-signup/implementation#step-2--create-a-facebook-login-for-business-configuration) to create a new Facebook Login for Business configuration. Select the following in your configuration:

Assets:
- WhatsApp accounts
- (Do not select the other options of Ad accounts, Pages, Catalogues, Pixels, Instagram accounts)

Permissions:
- `ads_read` (optional)
- `whatsapp_business_management`
- `whatsapp_business_messaging`

#### Step 3: Launch Embedded Signup

Refer to the [Embedded Sign up implementation](/docs/whatsapp/embedded-signup/implementation) document and add `marketing_messages_lite` to the list of features before onboarding WhatsApp SMB users.

```
{
  "config_id": "<config_id>",
  "response_type": "code",
  "override_default_response_type": true,
  "extras": {
    "featureType": "whatsapp_business_app_onboarding",
    "sessionInfoVersion": "3",
    "features": [
      {
        "name": "marketing_messages_lite"
      }
    ],
    "version": "v3"
  }
}
```

#### Step 4: Wait for the onboarding confirmation webhook

Once a business admin completes the MM API for WhatsApp onboarding flow, and any backend onboarding processes complete successfully, an `account_update` webhook will be sent for each WABA under the BMID, to indicate that onboarding has successfully completed.

See the [Onboarding](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding) for details on the `account_update` webhook.

After a business goes through the Embedded Signup flow for MM API for WhatsApp, the returned system user app token will have permission to send messages via MM API for WhatsApp, and fetch metrics via the Insights API.

## Onboard a business to Marketing Messages for WhatsApp using the Intent API

Partners can use the Intent API to onboard a business to Marketing Messages for WhatsApp (MM API for WhatsApp) while automatically marking all On-behalf-of (OBO) WABAs to be transferred to your customer, and receive an async (webhook) notification when the onboarding is complete to fetch the necessary access tokens.

If an end business has any OBO WABAs that do not currently have an OBO migration intent set, this intent will automatically be set for all OBO WABAs between the partner and end business through this API call.

1) Call the intent API

Calling the intent API to onboard a BMID to MM API for WhatsApp will trigger an email to all admins of that BMID, directing them to an onboarding flow in Business Manager. Meta will contact admins of the BMID until they either onboard or reject the invitation to onboard.

Partners must use a System User Access Token for the App with advanced permissions to call the intent API for each of their eligible end businesses.

An eligible end business is one that:

* Has not yet signed the MM API for WhatsApp ToS
* Is currently a partner business as dictated by 1+ shared or OBO WABAs with the BSP
* Has 1+ WABAs in an MM API for WhatsApp eligible tax country

Request:

```
curl -i -X POST \
"https://graph.facebook.com/<API_VERSION>/<END_BUSINESS_ID>/onboard_partners_to_mm_lite?access_token=<SYSTEM_USER_ACCESS_TOKEN>"
```

Optional Body:

If a partner wants to migrate OBO WABAs to a WhatsApp Business Solution as opposed to being shared solely with the partner, an optional solution\_id can be passed into the API call.

```
{
  "solution_id": "<MULTI-PARTNER_SOLUTION_ID>"
}
```

Response:

```
{
  "request_id": "893436979557695"
}
```

* Error: Invalid recipient type
  + Reason: The end business is not eligible to onboard onto MM API for WhatsApp because
    - They have either accepted the ToS already
    - The end business is not in an allowlisted country
    - There are no country eligible WABAs shared with the BSP
* Error: Your business has already sent this request. To follow up on the request, contact the business you're requesting access from.
  + Reason: There is already a request to this end business to onboard onto MM API for WhatsApp using this flow.
* Error: The app does not have sufficient permissions to call this API.
  + Reason: The app SUAT used to call the API must have advanced access on at least whatsapp\_business\_messaging and whatsapp\_business\_management.
* What is the expected behavior for OBO WABAs and the migration intent that gets set?
  + 1 shared, 4 OBO with intent
    - Call succeeds, creating an MM API for WhatsApp intent, does not set new OBO intent
  + 0 shared, 5 OBO with intent
    - Call succeeds, creating an MM API for WhatsApp intent, does not set new OBO intent
  + 1 shared, 4 OBO without intent
    - Call succeeds, creating an MM API for WhatsApp intent, sets new OBO intent
  + 0 shared, 5 OBO without intent
    - Call succeeds, creating an MM API for WhatsApp intent, contingent on setting OBO intent
  + 0 shared, 0 OBO
    - Call fails, no MM API for WhatsAppor OBO intent is set

2) Wait for the onboarding confirmation webhook

Once a business admin completes the MM API for WhatsApp onboarding flow, and any backend onboarding processes complete successfully, a new account\_update webhook will be sent for each WABA under the BMID, to indicate that onboarding has successfully completed.

3) Fetch an updated Business Integration System User Access Token (BISUAT)
In order to call the Insights API, you will need a Business Integration System User Access Token scoped to the Ad account that is linked to the WABA you are managing.
Follow the guide in the “Business Integration System User Access Token Management API” section to fetch your existing token for managing ad account IDs received in the webhook.

Request syntax:

```
curl -i -X POST "https://graph.facebook.com/<API_VERSION>/<CLIENT_BUSINESS_ID>/system_user_access_tokens
    ?appsecret_proof="<APPSECRET_PROOF_HASH>"
    &access_token="<SYSTEM_USER_ACCESS_TOKEN>"
    &fetch_only=true
```

| Object | Description | Example Value |
| --- | --- | --- |
| `<API_VERSION>` | Graph API version. | v23.0 |
| `<APPSECRET_PROOF_HASH>` | Required. The appsecret\_proof is a sha256 hash of your access token ensuring API calls are from a server are more secure. [Learn more](/docs/graph-api/guides/secure-requests/#generate-the-proof). | e3b0c... |
| `<CLIENT_BUSINESS_ID>` | Required. Client business ID. | 2780023991704 |
| `<SYSTEM_USER_ACCESS_TOKEN>` | Required. This access token requires the business\_management permission. | EAAJZC... |

Response syntax

```
{
  "access_token": "<NEW_ACCESS_TOKEN>"
}
```

### Onboard WhatsApp Business app users (aka "Coexistence")

You can configure Embedded Signup to [allow business customers to onboard using their existing WhatsApp Business app account and phone number:](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users)

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/477341352_1809983926468415_3794578338113490554_n.png?stp=dst-webp&_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=bD3U3dQdqRgQ7kNvwHKPJv-&_nc_oc=AdnjMfe2-KkgzRhXaXtUjN4aP-cPjF6cnK76rRPfKU8umfcwL2wVnEL1B8CqhN9VLpU&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfhIj7o_Dl4sAGGjPJGgKMzoaL-CLzmzcTHAJF0q1arZ3w&oe=694070DB)

Businesses who are successfully onboarded after choosing this option will then be able to use your app to message their customers at scale, but still have the ability to send messages on a one-to-one basis using the WhatsApp Business app.

Note: To ensure accurate metrics tracking, we recommend that business customers avoid clicking links in their own marketing messages. Clicking these links may affect tracking data and could lead to skewed results.

### Offboard Whatsapp Business app users

When you offboard Coexistence, you will automatically be offboarded from MM API for WhatsApp. The ad account will be disabled and unlinked which will prevent conversion metrics tracking.

## Help the business set up Conversion measurement

See [Setting up conversion measurement](/docs/whatsapp/marketing-messages-api-for-whatsapp/measuring-conversion) for details on how businesses can measure when a marketing message from MM API for WhatsApp leads to a conversion (e.g. add to cart, purchase).

Partners are **strongly recommended** to work with their clients to set up Conversion reporting, so that they can take advantage of measuring the improved metrics and optimizations MM API for WhatsApp provides.

## Sending messages

See [Sending messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages) for documentation on how to send messages and receive webhooks on behalf of your customers via MM API for WhatsApp.

## Viewing metrics

See the Guide to [Viewing metrics](/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics) for documentation on how to:

* Fetch the IDs of the Ad entities mapped to a business’ WABAs and Templates, in order to call Insights APIs.
* Fetch metrics for messages sent via MM API for WhatsApp.

Partners are **strongly recommended** to fetch metrics using the Ads Insights APIs (not Business Management APIs), as these APIs provide richer metrics reporting, including conversion reporting from sources such as Web and App conversion events.

After integrating with reporting APIs (Insights API recommended), surface these metrics in your dashboards and APIs for your customers to use.

Reach out to your Partner Manager for suggestions on metrics best practices, including a copy of Meta’s “**Business Messaging Reporting Dashboards Playbook**” for partners.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Onboard business customers](#onboard-business-customers)

[Before you begin](#before-you-begin)

[Solution partner integration overview](#solution-partner-integration-overview)

[Onboarding yourself](#onboarding-yourself)

[Register yourself for MM API for WhatsApp](#register-yourself-for-mm-api-for-whatsapp)

[Submit for app review for Advanced App permissions](#submit-for-app-review-for-advanced-app-permissions)

[Onboard a business to Marketing Messages for WhatsApp using the Intent API](#onboard-a-business-to-marketing-messages-for-whatsapp-using-the-intent-api)

[Help the business set up Conversion measurement](#help-the-business-set-up-conversion-measurement)

[Sending messages](#sending-messages)

[Viewing metrics](#viewing-metrics)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfhQEF3TE8L7CN2vZ1gOVEjuGAa5e9nKO-MW-uL0iaREiA&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_Afh8ahGetXzJ6NfHFHWSWVCz-sGMaDHrvgUFIQa5lZMQbw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfgnteXqXJO0OY1prxle7ueP_do6v_8ZFgGNv28fK3IfPQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1X8XJUA_1xsOIsDfYwJCbu3Kqzs8nkfGyseWd83ESu_Q3KGi2uV92Xn1rhUKxZrqrnj0LKIgMJL0zI_5aHhhXCkkx-XwW55NL6gYDlH5nPu5FL8f4M6v65K9Q1yscEhWz6hnTNGzGV2ujj7n9wPA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfjtG-H_yIOf301btXTIY-d9bHrahuPOqHk2-5GJiQnFMQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3m5BnXD-KBjz1uuc3trJGeMlRV3r2kS1-NcKsIkpH0ai58f5y3xPgnnSArgUJVvIP_UscdSozI7wq4cf3PmXyt2wN32bdc_bdmdGlmKkEFa0URWcv3ksYlb4UJPpJMgvSu93Mn0spXaZJacYzlJA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfhMuohgkRmU8EnMfHGB8ryVvzcPHc5Z9OXvylwMXK2N7w&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT207hSy_2XEvq4vvi-yRaZ1RGHJ9RwWSr7AWr2o5lBZVMBCU9Q0bA_z2hmiIbHx98eKYrEayH0ewaBmMhE5wFgG1313ZFAT2Gr41SFULrGswhkwzaym-zEnmRjpsUnHP6nPomYVQGxu6cFKSLjjmw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfiGWZeW7Fth9Iq3Roj9uVaPO-ofz5Jd_ApJ7-Loy09O2w&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1_q4GDJidyLGeTKFCg3by7ED8yhajdx78IVSJcjA0GYVuhVn8dcRSJAFAvnFZLGAEfjyhk_lH4R5P8B-FBA2QJg-CoH5IA946ctFlxXNi7kIyU41T64W9TQPewpcsuEP39jFVw6DNRitj7j_uF0Q)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3TWTesEAgxO_5ZQSSj35EFdTsdDkku_u67uW0QqALBEGS6mpRNE6jLrfny_6bua9QfC8qbreG9VsMHG4NLKb5S3Tgd6lJboGgqMwGhpjjS2arm-J23ehGYMcP63L8NRsW9I6n0kfIoy-Jpz6wmzg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2N-WF9bS56ycIT1MXgEkzFYmw_wGqPXALoTZ4-W9EvPAomp6VQyaz3heRXX4fWLnhMF5yumUrlji7NG_Eny-suXwds4YW4LIkPKsDUlmoiFRRUl8RazRvcZd0kCSkh0TYWHcLy2MVsXIIoZStQ9Q)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfjvSOqim6WbpWv8XlkA3Dbt59yGEkyXu19JNGMBa_JREw&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_Afiiane1apeFG7zv6fafZ8cwQJu7BhNaOWbNSyu-NKrk0w&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0RYI5tY3Zabt9ZaYeZ1ca3065LAOwRBgCEzUxIgUBUNp_7RAcN5PJMeUxq7yo9EzW5NXdlUJ9oTU4xwJBa5k53x72DvcGT9ppc6oJi1ENQndUtxEuX9mufuBTxRlr_1tsFAfEStRDLO2ruKGGEjw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfjN-rB-7QZH7tUBcpFaXurXvuH4LyTVHPon7uA9Z-yvKg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT37bIeKiT5ILDGGL3OCEmNMFwLuEq2lIjGsL2itWHLJJc340U_j2Gzj3NJofEwr4ouGpvhQ87iI6z5HAh2wNgSq6MHa54BWhgbnoekNjgiEoJrHxq14G-Gc3mJcXcXHzVLLnAPNgB5K6-V_aJOspw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_AfhxxOhokK3tZQ1oPZKCvd70wJ-L8VVqLNS7WpuGj5eBZw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3AmibyEUIUW0_Fopjrz_enlqN45JDm_LMLvKeNrnAtDgElDZ26V6lO2mLCaVD0CQU3B53cJJcN-lz859gP7Pmpl6b6uSUktiSLB4-ozgUnLHfFKv8nSSayZAZ7DkuJRRfWVegSy8puBDU91gufEw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=IgORcecPCFPtBNUr67NCOg&oh=00_Afg24t05HDyBONYg4m6Slb3p0HOByemfk9c1ZMfbvGkeUg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1qnLdRExjMIwArltiN7qvZCc8FRz7NLVMk8NlfQtNiSKph3a3HOPRdSStSHhQTfqkiBqO7j2svhzlxPbGRgASnNh9iSEbzLkiTI5S_-zom9SYbvs19Dx_TEASWVgVUChwLT8V5HDPKD8VsUwQKAg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT24yOFjF-xtCmqSP2ONPSP5-dCUnhf6x8x6bQpsxL1ZEO8yaZYrBXexfQv2lLCejGrKwnn9G_1HbexY6YMoIxiZYNeOKQE74ehbI86Bw-TsLsN-acwIWx3Q1Mngleix0oqpTiPb0TX_Ipa9YBIsrg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)