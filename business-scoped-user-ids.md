![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-scoped-user-ids%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)

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

[Business-scoped user IDs](#business-scoped-user-ids)

[User usernames](#user-usernames)

[Business-scoped user ID](#business-scoped-user-id)

[Phone numbers](#phone-numbers)

[Country codes](#country-codes)

[Business usernames](#business-usernames)

[Reserved usernames](#reserved-usernames)

[Chat window display priority](#chat-window-display-priority)

[Support](#support)

[Adopt or change a business username](#adopt-or-change-a-business-username)

[Get current username](#get-current-username)

[Get reserved usernames](#get-reserved-usernames)

[Delete a username](#delete-a-username)

[Response syntax:](#response-syntax-)

[Cancel pending username request](#cancel-pending-username-request)

[phone\_number\_username\_update webhook](#phone-number-username-update-webhook)

[Messages](#messages)

[Send message requests](#send-message-requests)

[Send message response](#send-message-response)

[Error codes](#error-codes)

[Marketing Messages API for WhatsApp](#marketing-messages-api-for-whatsapp)

[Send marketing message requests](#send-marketing-message-requests)

[Send marketing message response](#send-marketing-message-response)

[Messages webhooks](#messages-webhooks)

[Status messages webhooks](#status-messages-webhooks)

[Incoming messages webhooks](#incoming-messages-webhooks)

[System status messages webhooks](#system-status-messages-webhooks)

[User\_preferences webhooks](#user-preferences-webhooks)

[Groups API](#groups-api)

[Get group info](#get-group-info)

[Get group join requests](#get-group-join-requests)

[Remove group participants](#remove-group-participants)

[Groups API webhooks](#groups-api-webhooks)

[group\_participants\_update webhooks](#group-participants-update-webhooks)

[Blosk Users API](#blosk-users-api)

[Block or unblock user requests](#block-or-unblock-user-requests)

[Calling API](#calling-api)

[Businesses-initiated call requests](#businesses-initiated-call-requests)

[Get call permissions](#get-call-permissions)

[Send call permission request](#send-call-permission-request)

[Call permission request webhooks](#call-permission-request-webhooks)

[Business-initiated connected calls webhooks](#business-initiated-connected-calls-webhooks)

[User-initiated connected calls webhooks](#user-initiated-connected-calls-webhooks)

[Business-initiated terminated calls webhooks](#business-initiated-terminated-calls-webhooks)

[User-initiated terminated calls webhooks](#user-initiated-terminated-calls-webhooks)

[Business-initiated calls status webhooks](#business-initiated-calls-status-webhooks)

[SIP invites for business-initiated calls](#sip-invites-for-business-initiated-calls)

[SIP invites for user-initiated calls](#sip-invites-for-user-initiated-calls)

[SIP OK responses for business-initiated calls](#sip-ok-responses-for-business-initiated-calls)

[SIP BYE responses for business- and user-initiated calls](#sip-bye-responses-for-business--and-user-initiated-calls)

[Coexistence](#coexistence)

[History webhooks](#history-webhooks)

[smb\_message\_echoes webhooks](#smb-message-echoes-webhooks)

[smb\_app\_state\_sync webhooks](#smb-app-state-sync-webhooks)

[Analytics](#analytics)

[Billing and invoicing](#billing-and-invoicing)

[FAQs](#faqs)

# Business-scoped user IDs

WhatsApp is launching usernames later in 2026.

Usernames are an optional feature for users and businesses. If a username is adopted by a WhatsApp user, their username will be displayed instead of their phone number in the app. Business usernames are not intended for privacy, however. If you adopt a business username, it will not cause your business phone number to be hidden in the app.

To support usernames, we will share a new backend user identifier called business-scoped user ID, or BSUID. BSUID uniquely identifies a WA user and is tied to a specific business.

This document describes how the addition of usernames will impact API requests, API responses, and webhook payloads. Additional changes to support usernames before the feature is made available will be recorded here.

**Any changes described in this document are subject to change.**

## User usernames

A user username is a unique, optional name that WhatsApp users can set in order to display their username instead of their phone number in the app. Usernames can be used in lieu of profile names when personalizing message content for individual users.

WhatsApp users are limited to 1 username, but are able to change them periodically. Changing a username does not affect the user's phone number or business-scoped user ID, and does not affect the user's ability to communicate with other WhatsApp users or businesses on the WhatsApp Business Platform.

Usernames are assigned to the `username` property in API responses and webhooks payloads. Once enabled, a WhatsApp user's username will appear in all incoming [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages#incoming-messages) webhooks, and all **delivered** and **read** [status messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks.

## Business-scoped user ID

A business-scoped user ID ("BSUID") is a unique user identifier that can be used to message a WhatsApp user when you don't know their phone number. BSUID will be assigned to the `user_id` parameter and appear in all [messages webhooks](#messages-webhooks), regardless of whether or not the user has enabled the username feature.

BSUIDs will be:

* generated automatically
* composed of up to 256 alphanumeric characters
* unique to each business portfolio-user pair ([business portfolios](https://www.facebook.com/business/help/486932075688253) were formerly known as Business Managers)
* regenerated if a user changes their phone number (which trigger a [system status messages webhook](#system-status-messages-webhooks))

BSUIDs can be used to send any type of message except for one-tap, zero-tap, and copy code [authentication templates](/docs/whatsapp/business-management-api/authentication-templates), which require user phone numbers.

Note that since BSUIDs are unique to each business portfolio-user pair, if you have multiple portfolios, your API requests will fail if you are attempting to message a BSUID that is scoped to a different portfolio. However, there may be legitimate use cases for some businesses to share the BSUID between business portfolios. We are scoping a solution to simplify this process. Please note to your Meta POC if you would like to discuss.

## Phone numbers

When a user adopts a username, their phone number will not be included in [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages) webhooks in some cases. Instead, their BSUID will be sent in a new `user_id` field, and their phone number may be sent as an empty string in the `wa_id` field, on both existing and new API versions. Although phone numbers will still be shared in a few cases, primarily for existing customer interactions, it is essential for you to begin ingesting BSUIDs as soon as possible, to minimize losing any conversation context.

* If you message/call a WhatsApp user's phone number, or receive a message/call from their phone number, we will include their phone number in API responses and messages webhooks for 30 days from the time of sending or receiving, regardless of whether or not the user has adopted a username. **Sending/calling or receiving a message/call to or from the user's phone number within this window will reset the 30 day window.**
* There may be situations where you receive messages from existing customers outside of the 30 day window that look like a message from a new user, because their phone number is not in the messages webhook (wa\_id is an empty string). To ensure you can identify username adopters and maintain conversation context beyond 30 days, we are building a feature that will allow you to continue to receive a user's phone number even after they have adopted a username, provided you have messaged the user's phone number in the past. Communication history will be recorded starting from feature opt-in. We will provide details on the opt-in process and timing as they become available.
* If a user has not adopted a username, messages webhooks will include both their phone number and their BSUID.

You can message users using either their BSUID or phone number as soon as BSUIDs begin appearing in API responses and webhook payloads.

## Country codes

When a WhatsApp user enables the username feature, their phone number may not appear in webhooks. If you don't know their phone number but still need to communicate with them, you can send a message to their BSUID.

Country code will be included in all [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages) webhooks (subject to change).

## Business usernames

Businesses will also be able to adopt a business username. If you adopt a business username, however, it will not cause your business phone number to be hidden in the WhatsApp or WhatsApp Business client.

A business username is mapped to a single business phone number across all of WhatsApp, i.e. a phone number can have only one username at a given time, and no two WhatsApp phone numbers (consumer or business) can have the same username.

Business usernames must adhere to the following format:

* may only contain english letters (a-z), digits (0-9), period (.) and underscore (\_) characters
* must be between 3-35 characters in length
* must contain at least one English letter (a-z, A-Z)
* must not start or end with a period or have 2 consecutive periods
* must not start with www
* must not end with a domain (e.g., .com, .org, .net, .int, .edu, .gov, .mil, .us, .in, .html, etc.)
* case is ignored when comparing usernames, but period and underscore characters are not; for example, myID and myid are the same \*username but myid, my.id and my\_id are all distinct

### Reserved usernames

Before the username feature is made available, you will have the option to claim a username that WhatsApp has reserved for you. Alternatively, you can adopt a different username that aligns with your branding requirements. A reserved username can be claimed through WhatsApp Manager, Meta Business Suite, or [via API](#get-reserved-usernames). Claimed usernames that are approved will become active once the username feature is made available.

If your reserved username is already in use with your Facebook Page or Instagram account, you must [link](https://www.facebook.com/business/help/4631406400243963) your business phone number to your Facebook Page or Instagram account before you will be able to claim the username. To link your page or account, you must have full control of the page or account, or basic partial access with the manage\_phone permission.

See [About business portfolio and business asset permissions](https://www.facebook.com/business/help/442345745885606) for information about control/access and permissions.

### Chat window display priority

The following priority will be followed (in decreasing order of priority) for displaying business profile information in chat windows in the app. Your business phone numbers will always appear in your business profile.

* Saved contact name
* Verified business name or [Official Business Account](/docs/whatsapp/official-business-accounts) name
* Username
* Phone number

### Support

* You can contact your Partner Manager with any concerns.
* You can reach out to any of the [standard support channels](/docs/whatsapp/support); for API integrations, please raise a Direct support ticket with question type, **WA Usernames API Integration**.
* Use the **Report Abuse** channel via [Direct Support](https://business.facebook.com/direct-support/) to report impersonation.
* Use our [WhatsApp Intellectual Property Contact Form](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Fcontact%2Fforms%2F5071674689613749&h=AT1rLYFCfSalMNNU69bE6zv2_HzSgfSh06cy3wNUUczY2VCFfCGM20CdYhJk3PpyvO48qnBbrCjlgwkeowBnpiN5lX2b1psNdKQ44syNBqSF8Q-CWXJ1aC7tatn7gdKW1RVm4ooXSTfYxplbCY27WA) form to report infringement.

### Adopt or change a business username

You will be able to adopt or change a business username using Meta Business Suite, WhatsApp Manager, WhatsApp Business app, or the API.

Request syntax:

```
curl -X POST 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/username' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "username": "<DESIRED_USERNAME>"
}'
```

Response syntax, upon success:

```
{
  "status": "<STATUS>",

  <!-- Only included for REJECTED status -->
  "rejection_reasons": [
    "<REJECTION_REASON>",
    <!--Additional rejection reasons would follow, if any -->
  ]
}
```

* `status` — The status of the latest requested username. Values can be:
  + `APPROVED` — The requested username has been approved and will be active once the usernames feature is made available.
  + `REJECTED` — The requested username has been rejected. The business phone number's existing approved username, if any, will remain in place. Check `rejection_reasons` for details.
  + `PENDING` — The username is undergoing review. When a decision is made, a phone\_number\_username\_update webhook will be triggered, indicating the new status.
* `rejection_reasons` — An array of strings indicated the reason(s) for the rejection. Only included if the requested username has been rejected. Values can be:
  + `REQUIRE_FB_ACCOUNT_LINKING` — The requested username may be available if you [link](https://www.facebook.com/business/help/4631406400243963) your WhatsApp business phone number to the Facebook Page.
  + `REQUIRE_IG_ACCOUNT_LINKING` — The requested username may be available if you link your WhatsApp business phone number to the Instagram account.
  + `EXISTING_PENDING_REQUEST` — A previously requested username is still undergoing review.
  + `NOT_AVAILABLE` — The username is not available because it is associated with another account or it doesn’t pass our internal checks.
  + `ACCOUNT_INELIGIBLE` — The account is not eligible to request a username. The business phone number's [display name](/docs/whatsapp/display-names) must be approved, and the owning business must be [verified](https://www.facebook.com/business/help/2058515294227817).
  + `UNKNOWN` — Rejected for an unknown reason. Please contact support.

### Get current username

You can use the **GET /<BUSINESS\_PHONE\_NUMBER\_ID>/username** endpoint to get the status of the business username associated with the business phone number, or information about the username.

Request syntax:

```
curl 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/username' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

Response syntax:

```
{
  "username": "<USERNAME>",
  "status": "<STATUS>",

  <!-- Only included for phone number's with a pending username request -->
  "requested_username": "<REQUESTED_USERNAME>"
}
```

* `username` — Current username. Will be an empty string if the business phone number has no username.
* `status` — Username status. Values can be:
  + `ACTIVE` — The username is approved and will become active once the usernames feature is made available.
  + `RESERVED` — The username is reserved for the business phone number but is not active.
* `requested_username` — Requested username. This property will only be included if a new username has been requested on the business phone number, but the requested username is still undergoing review.

### Get reserved usernames

Adding a new **GET /<BUSINESS\_PHONE\_NUMBER\_ID>/username\_suggestions** endpoint that returns a list of usernames that have been reserved for your business portfolio.

Call the [**POST /<BUSINESS\_PHONE\_NUMBER\_ID>/username**](#adopt-or-change-a-business-username) endpoint to claim the desired username from the list, which will then need to be approved. Once approved and usernames become available in your country, it will move to to an "active" status, meaning the business username will start appearing on your business profile, and users will be able to search for it using exact match search.

Request syntax:

```
curl 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/username_suggestions' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

Response syntax:

```
{
  "data": [
   {
     "username_suggestions": [
       "<RESERVED_USERNAME>",
       <!-- Additional usernames would follow, if any -->
     ]
   }
 ],
}
```

* `username_suggestions` — An array of reserved usernames, if any. These usernames have a higher chance of approval.

### Delete a username

You can use the **DELETE /<BUSINESS\_PHONE\_NUMBER\_ID>/username** endpoint to delete the business username associated with the business phone number.

Request syntax:

```
curl -X DELETE 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/username' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Response syntax:

```
{
  "success": <SUCCESS?>
}
```

* `success` — Boolean. Will be set to `true` if the username is deleted successfully, otherwise it will be set to `false`.

### Cancel pending username request

You can use the **DELETE /<BUSINESS\_PHONE\_NUMBER\_ID>/requested\_username** endpoint to cancel a pending business username request.

Request syntax:

```
curl -X DELETE 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/requested_username' \
-H 'Authorization: Bearer <ACCESS_TOKEN>'
```

### Response syntax:

```
{
  "success": <SUCCESS?>
}
```

* `success` — Boolean. Will be set to `true` if the username is deleted successfully, otherwise it will be set to `false`.

### phone\_number\_username\_update webhook

A new **phone\_number\_username\_update** webhook will be added. This webhook will be triggered when the status of a business phone number's username changes. Please make sure to subscribe each of your apps to this webhook field to be notified of username changes.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "time": <WEBHOOK_TRIGGER_TIMESTAMP>,
      "changes": [
        {
          "field": "phone_number_username_update",
          "value": {
            "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
            "decision": "<DECISION>",
            "requested_username": "<REQUESTED_USERNAME>",
            "rejection_reasons": [
              "<REJECTION_REASON>",
              <!-- Additional rejection reasons would follow, if any -->
            ]
          }
        }
      ]
    }
  ]
}
```

* `id` — WhatsApp Business Account ID.
* `time` — Unix timestamp indicated when the webhook was triggered
* `display_phone_number` — The business phone number's display number (the number displayed on your profile in the app.
* `decision` — Indicates the outcome of the business username review process. Values can be:
  + `APPROVED` — Indicates the username has been approved and will become active once the usernames feature is made available.
  + `REJECTED` — Indicates the username has been rejected. You can edit the name using WhatsApp Manager. Review the rejection reason before editing.
* `requested_username` — The requested username.
* `rejection_reasons` — Indicates the reason why the business username was rejected, if it was rejected. Values can be:
  + `REQUIRE_FB_ACCOUNT_LINKING` — The requested username is associated with an existing Facebook page. To claim the username, you must first [add your business phone number to the Page](https://www.facebook.com/business/help/4631406400243963).
  + `REQUIRE_IG_ACCOUNT_LINKING` — The requested username is associated with an existing Instagram handle. To claim the username, you must first add your business phone number to the Instagram account.
  + `NOT_AVAILABLE` — The username is not available because it is associated with another account or it doesn’t pass our internal checks.
  + `ACCOUNT_INELIGIBLE` — The account is not eligible to request a username. The business phone number's [display name](/docs/whatsapp/display-names) must be approved, and the owning business must be [verified](https://www.facebook.com/business/help/2058515294227817).
  + `UNKNOWN` — Rejected for an unknown reason. Please contact support.

## Messages

### Send message requests

These changes apply to [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/#Creating) endpoint requests.

This example syntax is sending a text message, but the changes apply to all message types.

```
'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<USER_PHONE_NUMBER>",      <!-- CHANGED -->
  "type": "text",
  "text": {
    "body": "<BODY_TEXT>"
  }
}'
```

* `to` — Supports both WhatsApp user phone numbers and user BSUIDs.

### Send message response

These changes apply to [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/#Creating) endpoint responses.

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<USER_PHONE_NUMBER_OR_ID>",    <!-- CHANGED -->
      "wa_id": "<USER_PHONE_NUMBER>",          <!-- CHANGED -->
      "user_id": "<BSUID>"                     <!-- ADDED -->
    }
  ],
  "messages": [
    {
      "id": "<WHATSAPP_MESSAGE_ID>"
    }
  ]
}
```

* `input` — Will return the user's BSUID if you send the message to the user's BSUID. Otherwise, it will return the user's phone number, or group ID (if sent the message to a group).
* `wa_id` — Will be set to empty if you sent the message to the user's BSUID.
* `user_id` — New property. Will be set to the user's BSUID if you sent the message to the user's BSUID. Otherwise, the property will be omitted.

Example response to a send message request sent to a user's phone number:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "+16505551234"
      "wa_id": "16505551234"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA"
    }
  ]
}
```

Example response to a send message request sent to a user's BSUID:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
      "wa_id": "",
      "user_id": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA"
    }
  ]
}
```

### Error codes

Adding new error code response to the [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/#Creating) endpoint.

* Error code — `131062`
* Details — `You can only send authentication messages to recipients' phone numbers, not their business-scoped user IDs.`

## Marketing Messages API for WhatsApp

### Send marketing message requests

Marketing Messages API for WhatsApp will support both phone numbers and BSUIDs. If you have both, we recommend sending messages to phone numbers, primarily so you can continue to receive phone numbers in webhooks. If you only have a user's BSUID, use their BSUID.

These changes will apply to [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/marketing\_messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages#send-marketing-template-messages) endpoint requests.

```
'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/marketing_messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<USER_PHONE_NUMBER>",      <!-- CHANGED -->
  "type": "template",
  "template": {
    <EXPECTED_TEMPLATE_PARAMETERS>
  }
}'
```

* `to` — Supports both WhatsApp user phone numbers and user BSUIDs.

### Send marketing message response

These changes apply to [POST /<BUSINESS\_PHONE\_NUMBER\_ID>/marketing\_messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages#send-marketing-template-messages) endpoint responses.

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<USER_PHONE_NUMBER_OR_ID>",    <!-- CHANGED -->
      "wa_id": "<USER_PHONE_NUMBER>",          <!-- CHANGED -->
      "user_id": "<BSUID>"                     <!-- ADDED -->
    }
  ],
  "messages": [
    {
      "id": "<WHATSAPP_MESSAGE_ID>",
      "message_status": "<PACING_STATUS>"
    }
  ]
}
```

* `input` — Will return the user's BSUID if you send the message to the user's BSUID. Otherwise, it will return the user's phone number, or group ID (if sent the message to a group).
* `wa_id` — Will be set to empty if you sent the message to the user's BSUID.
* `user_id` — New property. Will be set to the user's BSUID if you sent the message to the user's BSUID. Otherwise, the property will be omitted.

Example response to a send a template message to a user's phone number:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "+16505551234"
      "wa_id": "16505551234"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA",
      "message_status": "accepted"
    }
  ]
}
```

Example response to a send a template message to a user's BSUID:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
      "wa_id": "",
      "user_id": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY0NjcwNDM1OTUVAgARGBI1RjQyNUE3NEYxMzAzMzQ5MkEA",
      "message_status": "accepted"
    }
  ]
}
```

## Messages webhooks

### Status messages webhooks

These changes will apply to sent, delivered, read, and failed [status messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks.

Exception: Groups API sent or failed status messages webhooks are unaffected.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },

            <!-- Contacts will be included for sent, delivered, and read status -->
            "contacts": [
              {
                "profile": {
                  "name": "<USER_DISPLAY_NAME>",             <!-- ADDED -->
                  "username": "<USERNAME>",                  <!-- ADDED -->
                  "country_code": "<USER_COUNTRY_CODE>"      <!-- ADDED -->
                },
                "wa_id": "<USER_PHONE_NUMBER>",              <!-- ADDED -->
                "user_id": "<BSUID>"                         <!-- ADDED -->
              }
            ],

            "statuses": [
              {
                "id": "<WHATSAPP_MESSAGE_ID>",
                "status": "<STATUS>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "recipient_id": "<USER_PHONE_NUMBER>",       <!-- CHANGED -->
                "recipient_user_id": "<BSUID>",              <!-- ADDED -->

                <!-- Only for status failed messages -->
                "errors": [
                  {
                    "code": <ERROR_CODE>,
                    "title": "<ERROR_TITLE>",
                    "message": "<ERROR_MESSAGE>",
                    "error_data": {
                      "details": "<ERROR_DETAILS>"
                    },
                    "href": "<ERROR_CODES_URL>"
                  }
                ]
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

* `contacts` — New array. Only included for sent, delivered, and read status messages. Will be omitted entirely for failed status messages webhooks.
  + `name` — New property. Value will be set to the WhatsApp user's display name.
  + `username` — New property. Will be set to the WhatsApp user's username if the user has adopted a username. Will be omitted entirely for sent status messages webhooks.
  + `country_code` — New property. Will be set to the WhatsApp user's country code (*subject to change*).
  + `wa_id` — New property. Will be set to empty if the user has adopted a username and (1) you sent the message to the user's BSUID, (2) you haven't messaged the user's phone number within the last 30 days, or (3) the user has not added your number to their WhatsApp contacts list. If you sent the message to the user's phone number, it will be set to the user's phone number.
  + `user_id` — New property. Will be set to the WhatsApp user's BSUID.
* `recipient_id` — New empty value. Will be set to:
  + the WhatsApp user's phone number, if you sent the message to the user's phone number.
  + the group ID, if you sent the message to a group.
  + empty, if you sent the message to the user's BSUID and (1) you haven't messaged the user's phone number within the last 30 days, and (2) the user has not added your number to their WhatsApp contacts list.
* `recipient_user_id` — New property. Will be set to the user's BSUID if you sent the message to the user's BSUID. Otherwise, the property will be omitted entirely.

Example delivered status messages webhook describing a message sent to the phone number of a WhatsApp user who has enabled the usernames feature:

```
{
 "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "contacts": [
              {
                "profile": {
                  "name": "Pablo M.",
                  "username": "@pablomorales",
                  "country_code": "US"
                },
                "wa_id": "16505551234",
                "user_id": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
              }
            ],
            "statuses": [
              {
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=",
                "status": "delivered",
                "timestamp": "1750030073",
                "recipient_id": "16505551234",
                "pricing": {
                  "billable": true,
                  "pricing_model": "PMP",
                  "type": "regular",
                  "category": "marketing"
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

Example delivered status messages webhook describing a message sent to the BSUID of a WhatsApp user who has enabled the username feature. Note that `wa_id`, which would normally be set to the user's phone number, is empty:

```
{
 "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "contacts": [
              {
                "profile": {
                  "name": "Pablo M.",
                  "username": "@pablomorales",
                  "country_code": "US"
                },
                "wa_id": "",
                "user_id": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6"
              }
            ],
            "statuses": [
              {
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=",
                "status": "delivered",
                "timestamp": "1750030073",
                "recipient_id": "",
                "recipient_user_id": "user.9373795779eb6441c8adb2eaee5b848e7dd174ddd302d7db62142f4722d574b6",
                "pricing": {
                  "billable": true,
                  "pricing_model": "PMP",
                  "type": "regular",
                  "category": "marketing"
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

### Incoming messages webhooks

These changes apply to incoming messages webhooks ([text](/docs/whatsapp/cloud-api/webhooks/reference/messages/text), [image](/docs/whatsapp/cloud-api/webhooks/reference/messages/image), [interactive](/docs/whatsapp/cloud-api/webhooks/reference/messages/interactive), etc.), including incoming messages sent by users in a Group chat.

The example syntax below is for an incoming **text** message, but the changes are the same for all incoming message types.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<WHATSAPP_USER_PROFILE_NAME>",
                  "username": "<USERNAME>",                <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"         <!-- ADDED -->
                },
                "wa_id": "<WHATSAPP_USER_ID>",             <!-- CHANGED -->
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER>",    <!-- CHANGED -->
                "from_user_id": "<BSUID>",                 <!-- ADDED -->
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "text",
                "text": {
                  "body": "<MESSAGE_TEXT_BODY>"
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Set to the user's country code (*subject to change*).
* `wa_id` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list, otherwise set to the user's phone number.
* `user_id` — New property, set to the user's BSUID.
* `from` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `from_user_id` — New property, set to the user's BSUID.

Example incoming text message from a user who has enabled the username feature. In this scenario, the business has not messaged the user's phone number in the last 30 days, and the user has not added the business's phone number to their WhatsApp contacts list. Note that `wa_id`, which would normally be set to the user's phone number, is empty:

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "102290129340398",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "15550783881",
              "phone_number_id": "106540352242922"
            },
            "contacts": [
              {
                "profile": {
                  "name": "Sheena Nelson",
                  "username": "@realsheenanelson",
                  "country_code": "US"
                },
                "wa_id": "",
                "user_id": "user.93737..."
              }
            ],
            "messages": [
              {
                "from": "",
                "from_user_id": "user.93737...",
                "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTRBNjU5OUFFRTAzODEwMTQ0RgA=",
                "timestamp": "1749416383",
                "type": "text",
                "text": {
                  "body": "Does it come in another color?"
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

### System status messages webhooks

These changes apply to [system status](/docs/whatsapp/cloud-api/webhooks/reference/messages/system) messages webhooks.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "system",
                "system": {
                  "body": "User...",                       <!-- CHANGED -->
                  "wa_id": "<NEW_WHATSAPP_USER_ID>",       <!-- CHANGED -->
                  "user_id": "<NEW_BSUID>",                <!-- ADDED -->
                  "type": "<SYSTEM_CHANGE_TYPE>"           <!-- CHANGED -->
                }
              }
            ]
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

* `body` — New string. Will be set to `User <WHATSAPP_USER_PROFILE_NAME> changed from <OLD_BSUID> to NEW_BSUID` if the user changed their business phone number.
* `wa_id` — New (empty) value. Will be set to empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's new BSUID.
* `type` — New (`user_changed_user_id`) value. Will be set to `user_changed_user_id` if the user changed their business phone number.

### User\_preferences webhooks

These changes will apply to [user\_preferences](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences) webhooks.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [
              {
                "profile": {
                  "name": "<WHATSAPP_USER_NAME>",
                  "username": "<USERNAME>",                <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"         <!-- ADDED -->
                },
                "wa_id": "<WHATSAPP_USER_ID>",             <!-- CHANGED -->
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "user_preferences": [
              {
                "wa_id": "<WHATSAPP_USER_ID>",             <!-- CHANGED -->
                "user_id": "<BSUID>",                      <!-- ADDED -->
                "detail": "<PREFERENCE_DESCRIPTION>",
                "category": "marketing_messages",
                "value": "<PREFERENCE>",
                "timestamp": <WEBHOOK_SENT_TIMESTAMP>
              }
            ]
          },
          "field": "user_preferences"
        }
      ]
    }
  ]
}
```

* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Set to the user's country code (*subject to change*).
* `wa_id` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list, otherwise set to the user's phone number.
* `user_id` — New property, set to the user's BSUID.

## Groups API

### Get group info

These changes apply to [GET /<GROUP\_ID>](/docs/whatsapp/cloud-api/groups/reference#get-group-info) endpoint responses.

```
{
  "participants": [
    {
      "wa_id": "<USER_PHONE_NUMBER>"  <!-- CHANGED -->
      "user_id": "<BSUID>",           <!-- ADDED -->
      "username": "<USERNAME>",       <!-- ADDED -->
      "country_code": "COUNTRY_CODE"  <!-- ADDED -->
    }
  ],
  "subject": "<GROUP_SUBJECT>",
  "id": "<GROUP_ID>",
  "messaging_product": "whatsapp"
}
```

* `wa_id` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list. Otherwise, will be set to the user's phone number.
  `user_id` — New property, set to the user's BSUID.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Set to the user's country code (*subject to change*).

### Get group join requests

These changes apply to [GET /<GROUP\_ID>/join\_requests](/docs/whatsapp/cloud-api/groups/reference#groups-with-join-requests) endpoint responses.

```
{
  "data": [
    {
      "join_request_id": "<JOIN_REQUEST_ID>",
      "creation_timestamp": "<JOIN_REQUEST_TIMESTAMP>",
      "wa_id": "<USER_PHONE_NUMBER>",                    <!-- CHANGED -->
      "user_id": "<BSUID>",                              <!-- ADDED -->
      "username": "<USERNAME>",                          <!-- ADDED -->
      "country_code": "<COUNTRY_CODE>"                   <!-- ADDED -->
    }
  ],
  "paging": {
    "cursors": {
      "before": "<BEFORE_CURSOR>",
      "after": "<AFTER_CURSOR>"
    }
  }
}
```

* `wa_id` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list. Otherwise, will be set to the user's phone number.
* `user_id` — New property, set to the user's BSUID.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Set to the user's country code (*subject to change*).

### Remove group participants

These changes apply to [DELETE /<GROUP\_ID>/participants](/docs/whatsapp/cloud-api/groups/reference#remove-group-participants) endpoint requests.

```
curl -g -X DELETE 'https://graph.facebook.com/<API_VERSION>/<GROUP_ID>/participants' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "participants": [
    {
      "user": "<USER_PHONE_NUMBER>"    <!-- CHANGED -->
    }
  ]
}'
```

* `user` — Will accept a user's phone number or BSUID.

## Groups API webhooks

### group\_participants\_update webhooks

These changes apply to the [group\_participants\_update](/docs/whatsapp/cloud-api/groups/webhooks#group-participants-update-webhooks) webhook.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "groups": [
              {
                "timestamp": <WEBHOOK_TRIGGER_TIMESTAMP>,
                "group_id": "<GROUP_ID>",

                <!-- Only if business removes participant from group -->
                "type": "group_participants_remove",
                "request_id": "REQUEST_ID",
                "removed_participants": [
                  {
                    "input": "<USER_PHONE_NUMBER>",      <!-- CHANGED -->
                  }
                ],
                "initiated_by": "business"

                <!-- Only if user removes themself from group -->
                "type": "group_participants_remove",
                "request_id": "REQUEST_ID",
                "removed_participants": [
                  {
                    "wa_id": "<USER_PHONE_NUMBER>"       <!-- CHANGED -->
                    "user_id": "<BSUID>",
                    "username": "<USERNAME>",
                    "country_code": "<COUNTRY_CODE>"
                  }
                ],
                "initiated_by": "participant"

                <!-- Only if user joins group via invite link -->
                "type": "group_participants_add",
                "reason": "invite_link",
                "added_participants": [
                  {
                    "wa_id": "<USER_PHONE_NUMBER>"       <!-- CHANGED -->
                    "user_id": "<BSUID>",                <!-- ADDED -->
                    "username": "<USERNAME>",            <!-- ADDED -->
                    "country_code": "<COUNTRY_CODE>"     <!-- ADDED -->
                  }
                ]

                <!-- Only if join request created -->
                "type": "group_join_request_created",
                "join_request_id": "<JOIN_REQUEST_ID>",
                "wa_id": "<USER_PHONE_NUMBER>",          <!-- CHANGED -->
                "user_id": "<BSUID>",                    <!-- ADDED -->
                "username": "<USERNAME>",                <!-- ADDED -->
                "country_code": "<COUNTRY_CODE>"         <!-- ADDED -->

                <!-- Only if join request revoked -->
                "type": "group_join_request_revoked",
                "join_request_id": "<JOIN_REQUEST_ID>",
                "wa_id": "<USER_PHONE_NUMBER>"           <!-- CHANGED -->
                "user_id": "<BSUID>",                    <!-- ADDED -->
                "username": "<USERNAME>",                <!-- ADDED -->
                "country_code": "<COUNTRY_CODE>"         <!-- ADDED -->

              }
            ]
          },
          "field": "group_participants_update"
        }
      ]
    }
  ]
}
```

* `wa_id` — New value (empty). Will be empty if the user has enabled the username feature and you have not messaged the user's phone number in the last 30 days, or your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's BSUID.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Will be set to the user's country code (*subject to change*).

## Blosk Users API

### Block or unblock user requests

These changes apply to the POST and DELETE [Block Users](/docs/whatsapp/cloud-api/block-users/) requests. This example is for a block user request syntax, but the changes also apply to unblock requests.

```
{
  "messaging_product": "whatsapp",
  "block_users": {
    "added_users": [
      {
        "input": "<USER_PHONE_NUMBER>",  <!-- CHANGED -->
        "wa_id": "<USER_PHONE_NUMBER>",  <!-- CHANGED -->
        "user_id": "<BSUID>"             <!-- ADDED -->
      }
    ]
  }
}
```

* `input` — Will be set to the user's BSUID if you used their BSUID when blocking or unblocking the user. Will be set to the user's phone number if you used their phone number when blocking or unblocking the user.
* `wa_id` — New empty value. Will be set to empty if you used the user's BSUID when blocking or unblocking the user. Will be set to the user's phone number if you used their phone number when blocking or unblocking the user.
* `user_id` — New property. Will be set to the user's BSUID if you used the user's BSUID when blocking or unblocking the user. If you used their phone number, the property will be omitted.

## Calling API

### Businesses-initiated call requests

The changes apply to business-initiated Calling API requests.

```
'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/calls' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-d '
{
  "messaging_product": "whatsapp",
  "to": "<USER_PHONE_NUMBER>",    <!-- CHANGED -->
  "action": "connect",
  "session": {
    "sdp_type": "offer",
    "sdp": "<RFC_4566_SDP>"
  }
}'
```

* `to` — Supports both WhatsApp user phone numbers and user BSUIDs.

### Get call permissions

The changes apply to [get call permissions](/docs/whatsapp/cloud-api/calling/user-call-permissions#call-permission-request-basics) requests. There are no changes to responses.

```
curl 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/call_permissions?user_wa_id=<BSUID>' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
```

* `user_wa_id` — Accepts both WhatsApp user phone numbers and user BSUIDs.

### Send call permission request

See [send message requests](#send-message-requests).

### Call permission request webhooks

See [incoming messages webhooks](#incoming-messages-webhooks).

### Business-initiated connected calls webhooks

These changes apply to business-initiated [connected calls](/docs/whatsapp/cloud-api/calling/reference#call-connect-webhook) webhooks.

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "calls",
          "value": {
            "contacts": [                                  <!-- ADDED -->
              {
                "profile": {
                  "name": "<USER_DISPLAY_NAME>",           <!-- ADDED -->
                  "country_code": "<USER_COUNTRY_CODE>"    <!-- ADDED -->
                },
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "calls": [
              {
                "biz_opaque_callback_data": "<data>",
                "session": {
                  "sdp_type": "answer",
                  "sdp": "<SDP>"
                },
                "from": "<BUSINESS_PHONE_NUMBER>",
                "id": "<WHATSAPP_CALL_ID>",
                "to": "<USER_PHONE_NUMBER>",               <!-- CHANGED -->
                "to_user_id": "<BSUID>",                   <!-- ADDED -->
                "event": "connect",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "direction": "BUSINESS_INITIATED"
              }
            ],
            "metadata": {
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              "display_phone_number": "<BUSINESS_PHONE_NUMBER>"
            },
            "messaging_product": "whatsapp"
          }
        }
      ],
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>"
    }
  ],
  "object": "whatsapp_business_account"
}
```

* `contacts` — A new contacts object will be included.
* `name` — New property. This will be set to the user's profile name.
* `country_code` — New property. This will be set to the user's country code (*subject to change*).
* `user_id` — New property. This will be set to the user's BSUID.
* `to` — New empty value. This will be set to the WhatsApp user's phone number if the user has adopted a username and (1) the message was sent to their phone number, (2) your business phone number is already in the user's WhatsApp contacts list, or (3) you have messaged or called their phone number within the last 30 days. Otherwise, it will be set to an empty string.
* `to_user_id` — New property. This will be set to the user's BSUID.

### User-initiated connected calls webhooks

These changes will apply to user-initiated [connected calls](/docs/whatsapp/cloud-api/calling/reference#call-connect-webhook) webhooks.

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "calls",
          "value": {
            "metadata": {
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              "display_phone_number": "<BUSINESS_PHONE_NUMBER>"
            },
            "calls": [
              {
                "session": {
                  "sdp_type": "offer",
                  "sdp": "<SDP>"
                },
                "from": "<USER_PHONE_NUMBER>",             <!-- CHANGED -->
                "from_user_id": "<BSUID>",                 <!-- ADDED -->
                "id": "<WHATSAPP_CALL_ID>",
                "to": "<BUSINESS_PHONE_NUMBER>",
                "event": "connect",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "direction": "USER_INITIATED"
              }
            ],
            "contacts": [
              {
                "wa_id": "<USER_PHONE_NUMBER>",            <!-- CHANGED -->
                "profile": {
                  "name": "<USER_DISPLAY_NAME>",           <!-- ADDED -->
                  "username": "<USERNAME>",                <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"         <!-- ADDED -->
                },
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "messaging_product": "whatsapp"
          }
        }
      ],
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>"
    }
  ],
  "object": "whatsapp_business_account"
}
```

* `from` — New empty value. If the user has adopted a username, it will be set to an empty string if (1) you haven't messaged or called the user's phone number in the last 30 days or (2) your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `from_user_id` — New property. Will be set to the user's BSUID.
* `wa_id` — New empty value. If the user has adopted a username, it will be set to an empty string if (1) you haven't messaged or called the user's phone number in the last 30 days or (2) your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `name` — New property. Will be set to the user's profile name.
* `username` — New property. If the user has adopted a username, it will be set to the user's username. Otherwise, the property will be omitted.
* `country_code` — New property. Will be set to the user's country code (*subject to change*).
* `user_id` — New property. Will be set to the user's BSUID.

### Business-initiated terminated calls webhooks

These changes apply to business-initiated [terminated calls](/docs/whatsapp/cloud-api/calling/reference#call-terminate-webhook) webhooks.

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "calls",
          "value": {
            "calls": [
              {
                "biz_opaque_callback_data": "<BUSINESS_OPAQUE_DATA>",
                "from": "<BUSINESS_PHONE_NUMBER>",
                "id": "<WHATSAPP_CALL_ID>",
                "to": "<USER_PHONE_NUMBER>",              <!-- CHANGED -->
                "to_user_id": "<BSUID>",                  <!-- ADDED -->
                "event": "terminate",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "direction": "BUSINESS_INITIATED",
                "status": "COMPLETED"
              }
            ],
            "metadata": {
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              "display_phone_number": "<BUSINESS_PHONE_NUMBER>"
            },
            "contacts": [                                  <!-- ADDED -->
              {
                "profile": {
                  "name": "<USER_PROFILE_NAME>",           <!-- ADDED -->
                  "country_code": "<USER_COUNTRY_CODE>"    <!-- ADDED -->

                },
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "messaging_product": "whatsapp"
          }
        }
      ],
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>"
    }
  ],
  "object": "whatsapp_business_account"
}
```

* `to` — New empty value. This will be set to the WhatsApp user's phone number if the user has adopted a username and (1) the call was made to their phone number, (2) your business phone number is already in the user's WhatsApp contacts list, or (3) you have messaged or called their phone number within the last 30 days. Otherwise, it will be set to an empty string.
* `to_user_id` — New property. This will be set to the user's BSUID.
* `contacts` — A new contacts object will be included.
* `name` — New property. This will be set to the user's profile name.
* `country_code` — New property. This will be set to the user's country code (*subject to change*).
* `user_id` — New property. This will be set to the user's BSUID.

### User-initiated terminated calls webhooks

These changes will apply to user-initiated [terminated calls](/docs/whatsapp/cloud-api/calling/reference#call-terminate-webhook) webhooks.

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "calls",
          "value": {
            "metadata": {
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              "display_phone_number": "<BUSINESS_PHONE_NUMBER>"
            },
            "calls": [
              {
                "duration": <CALL_DURATION>,
                "start_time": "<CALL_START_TIMESTAMP>",
                "biz_opaque_callback_data": "<BUSINESS_OPAQUE_DATA>",
                "end_time": "<CALL_END_TIMESTAMP>",
                "from": "<USER_PHONE_NUMBER>",             <!-- CHANGED -->
                "from_user_id": "<BSUID>",                 <!-- ADDED -->
                "id": "<WHATSAPP_CALL_ID>",
                "to": "<BUSINESS_PHONE_NUMBER>",
                "event": "terminate",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "direction": "USER_INITIATED",
                "status": "COMPLETED"
              }
            ],
            "contacts": [
              {
                "wa_id": "<USER_PHONE_NUMBER>",            <!-- CHANGED -->
                "profile": {
                  "name": "<USER_PROFILE_NAME>",           <!-- ADDED -->
                  "country_code": "<USER_COUNTRY_CODE>"    <!-- ADDED -->
                },
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "messaging_product": "whatsapp"
          }
        }
      ],
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>"
    }
  ],
  "object": "whatsapp_business_account"
}
```

* `from` — New empty value. This will be empty if the user has adopted a username and (1) your business phone number is not in the user's WhatsApp contacts list and (2) you have not messaged or called their phone number within the last 30 days. Otherwise, it will be set to the user's phone number.
* `from_user_id` — New property. This will be set to the user's BSUID.
* `wa_id` — New empty value. This will be empty if the user has adopted a username and (1) your business phone number is not in the user's WhatsApp contacts list and (2) you have not messaged or called their phone number within the last 30 days. Otherwise, it will be set to the user's phone number.
* `name` — New property. This will be set to the user's profile name.
* `country_code` — New property. This will be set to the user's country code (*subject to change*).
* `user_id` — New property. This will be set to the user's BSUID.

### Business-initiated calls status webhooks

These changes will apply to business-initiated [calls status](/docs/whatsapp/cloud-api/calling/reference#call-status-webhook) webhooks.

```
{
  "entry": [
    {
      "changes": [
        {
          "field": "calls",
          "value": {
            "statuses": [
              {
                "biz_opaque_callback_data": "<BUSINESS_OPAQUE_DATA>",
                "id": "<WHATSAPP_CALL_ID>",
                "type": "call",
                "status": "<STATUS>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "recipient_id": "<USER_PHONE_NUMBER>",     <!-- CHANGED -->
                "recipient_user_id": "<BSUID>"             <!-- ADDED -->
              }
            ],
            "metadata": {
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>",
              "display_phone_number": "<BUSINESS_PHONE_NUMBER>"
            },
            "contacts": [                                  <!-- ADDED -->
              {
                "profile": {
                  "name": "<USER_PROFILE_NAME>",           <!-- ADDED -->
                  "country_code": "<USER_COUNTRY_CODE>"    <!-- ADDED -->
                },
                "user_id": "<BSUID>"                       <!-- ADDED -->
              }
            ],
            "messaging_product": "whatsapp"
          }
        }
      ],
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>"
    }
  ],
  "object": "whatsapp_business_account"
}
```

* `recipient_id` — New empty value. This will be set to an empty string if the WhatsApp user has adopted a username and (1) the call was made to their BSUID, (2) your business phone number is not in the user's WhatsApp contacts list, and (3) you have not messaged or called their phone number within the last 30 days. Otherwise, it will be set to the user's phone number.
* `recipient_user_id` — New property. This will be set to the user's BSUID.
* `contacts` — A new contacts array will be included.
* `name` — New property. This will be set to the user's profile name.
* `country_code` — New property. This will be set to the user's country code (*subject to change*).
* `user_id` — New property. This will be set to the user's BSUID.

### SIP invites for business-initiated calls

These changes apply to business-initiated calls made using [SIP](/docs/whatsapp/cloud-api/calling/sip).

```
<!-- BEGIN CHANGE -->
INVITE sip:<BSUID>@wa.meta.vc;transport=tls SIP/2.0
<!-- END CHANGE -->

Record-Route: <sip:+159.65.244.171:5061;transport=tls;lr;ftag=Kc9QZg4496maQ;nat=yes>
Via: SIP/2.0/TLS 159.65.244.171:5061;received=2803:6081:798c:93f8:5f9b:bfe8:300:0;branch=z9hG4bK0da2.36614b8977461b486ceabc004c723476.0;i=617261
Via: SIP/2.0/TLS 137.184.87.1:35181;rport=56533;received=137.184.87.1;branch=z9hG4bKQNa6meey5Dj2g
Max-Forwards: 69
From: <sip:+17125550259@meta-voip.example.com>;tag=Kc9QZg4496maQ

<!-- BEGIN CHANGE -->
To: <sip:<BSUID>@wa.meta.vc>
<!-- END CHANGE -->

Call-ID: dc2c5b33-1b81-43ee-9213-afb56f4e56ba
CSeq: 96743476 INVITE
Contact: <sip:mod_sofia@137.184.87.1:35181;transport=tls;swrad=137.184.87.1~56533~3>
User-Agent: SignalWire
Allow: INVITE, ACK, BYE, CANCEL, OPTIONS, MESSAGE, INFO, UPDATE, REGISTER, REFER, NOTIFY
Supported: timer, path, replaces
Allow-Events: talk, hold, conference, refer
Session-Expires: 600;refresher=uac
Min-SE: 90
Content-Type: application/sdp
Content-Disposition: session
Content-Length: 2427
X-Relay-Call-ID: dc2c5b33-1b81-43ee-9213-afb56f4e56ba
Remote-Party-ID: <sip:+17125550259@meta-voip.example.com>;party=calling;screen=yes;privacy=off
Content-Type: application/sdp
Content-Length:  2427

<!-- SDP omitted for brevity -->
```

* `BSUID` — Will be the user's BSUID if the call was made to the user's BSUID, or the user's phone number if sent to their phone number.

### SIP invites for user-initiated calls

These changes apply to user-initiated calls made using [SIP](/docs/whatsapp/cloud-api/calling/sip).

```
INVITE sip:+17015558857@meta-voip.example.com;transport=tls SIP/2.0
Via: SIP/2.0/TLS [2803:6080:e888:51aa:d4a4:c5e0:300:0]:33819;rport=33819;received=2803:6080:e888:51aa:d4a4:c5e0:300:0;branch=z9hG4bKPjNvs.IZBnUa1W4l8oHPpk3SUMmcx3MMcE;alias
Max-Forwards: 70

<!-- BEGIN CHANGE -->
From: "<BSUID>" <sip:<BSUID>@wa.meta.vc>;tag=bbf1ad6e-79bb-4d9c-8a2c-094168a10bea
<!-- END CHANGE -->

To: <sip:+17015558857@meta-voip.example.com>

<!-- BEGIN CHANGE -->
Contact: <sip:<BSUID>@wa.meta.vc;transport=tls;ob>;isfocus
<!-- END CHANGE -->

Call-ID: outgoing:wacid.HBgLMTIxOTU1NTA3MTQVAgASGCAzODg1NTE5NEU1NTBEMTc1RTFFQUY5NjNCQ0FCRkEzRhwYCzE3MDE1NTU4ODU3FQIAAA==
CSeq: 2824 INVITE
Route: <sip:onevc-sip-proxy-dev.fbinfra.net:8191;transport=tls;lr>
X-FB-External-Domain: wa.meta.vc

<!-- BEGIN ADDITION -->
x-wa-meta-user-id: <BSUID>
x-wa-meta-user-name: <USERNAME>
x-wa-meta-user-country-code: <USER_COUNTRY_CODE>
<!-- END ADDITION -->

Allow: INVITE, ACK, BYE, CANCEL, NOTIFY, OPTIONS
User-Agent: Facebook SipGateway
Content-Type: application/sdp
Content-Length: 1028

<!-- SDP omitted for brevity -->
```

* `BSUID` — Will be the user's BSUID if the call was made to the user's BSUID, or if the user has adopted a username and (1) you haven't messaged or called the user's phone number in the last 30 days, or (2) your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be the user's phone number.
* `USERNAME` — Will be the user's username.
* `USER_COUNTRY_CODE` — Will be the user's country code (*subject to change*).

### SIP OK responses for business-initiated calls

```
SIP/2.0 200 OK
Via: SIP/2.0/TLS 54.172.60.1:5061;received=2803:6080:f934:8894:7eb5:24f9:300:0;branch=z9hG4bK1e5a.0da2ace9cc912d9e5f2595ca4acb9847.0
Via: SIP/2.0/UDP 172.25.10.217:5060;rport=5060;branch=z9hG4bK5cdada8c-cbf0-4369-b02d-cc97d3c36f2b_c3356d0b_54-457463274351249162
Record-Route: <sip:onevc-sip-proxy.fbinfra.net:8191;transport=tls;lr>
Record-Route: <sip:wa.meta.vc;transport=tls;lr>
Record-Route: <sip:54.172.60.1:5061;transport=tls;lr;r2=on>
Record-Route: <sip:54.172.60.1;lr;r2=on>
Call-ID: f304a1d2cafb8139c1f9ff93a7733586@0.0.0.0

<!-- BEGIN CHANGE -->
From: "<BSUID>" <sip:<BSUID>@meta-voip.example.com>;tag=28460006_c3356d0b_5cdada8c-cbf0-4369-b02d-cc97d3c36f2b
<!-- END CHANGE -->

To: <sip:12195550714@wa.meta.vc>;tag=0d185053-2615-46c7-8ff2-250bda494cf1
CSeq: 2 INVITE
Allow: INVITE, ACK, BYE, CANCEL, NOTIFY, OPTIONS
Supported: timer
X-FB-External-Domain: wa.meta.vc

<!-- BEGIN CHANGE -->
Contact: <sip:<BSUID>@wa.meta.vc;transport=tls;ob;X-FB-Sip-Smc-Tier=collaboration.sip_gateway.sip.prod>;isfocus
<!-- END CHANGE -->

<!-- BEGIN ADDITION -->
x-wa-meta-user-id: <BSUID>
x-wa-meta-user-name: <USERNAME>
x-wa-meta-user-country-code: <COUNTRY_CODE>
<!-- END ADDITION -->

Content-Type: application/sdp
Content-Length:   645

<!-- SDP omitted for brevity -->
```

* `BSUID` — Will be the user's BSUID if the call was made to the user's BSUID, or if the user has adopted a username and (1) you haven't messaged or called the user's phone number in the last 30 days, or (2) your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be the user's phone number.
* `USERNAME` — Will be the user's username.
* `USER_COUNTRY_CODE` — Will be the user's country code (*subject to change*).

### SIP BYE responses for business- and user-initiated calls

```
BYE sip:+12195550714@103.30.244.182:5061;transport=tls SIP/2.0
Via: SIP/2.0/TLS [2803:6080:e800:6746::]:56843;rport;branch=z9hG4bKPj65946b3e6f68128d52b6a498a8fd00a5;alias
Record-Route: <sip:wa.meta.vc;transport=tls;lr>
Record-Route: <sip:onevc-sip-proxy.fbinfra.net:8191;transport=tls;lr>
Via: SIP/2.0/TLS [2803:6080:e800:6746:3347:2251:14a4:a00]:5061;branch=z9hG4bKPj65946b3e6f68128d52b6a498a8fd00a5
Via: SIP/2.0/TLS [2803:6080:e934:3f82:b543:8a4d:1414:a00]:52767;rport=52767;received=2803:6080:e934:3f82:b543:8a4d:1414:a00;branch=z9hG4bKPj-D8BXdIVMqAUT9MIJIp78LxKUZNnjYKF;alias
Max-Forwards: 69

<!-- BEGIN CHANGE -->
From: <sip:<BSUID>@wa.meta.vc>;tag=0fb8b5f1-2703-49f4-a454-46b1bcb9bfac
<!-- END CHANGE -->

To: <sip:+12195550714@dev.moxcal.com>;tag=2c21fad0-c581-4e54-a707-3bd52abfcc3f
Call-ID: 21e38222-6fcb-4631-8e7d-5b94cf849c90
CSeq: 31641 BYE

<!-- BEGIN ADDITION -->
x-wa-meta-user-id: <BSUID>
x-wa-meta-user-name: <USERNAME>
x-wa-meta-user-country-code: <USER_COUNTRY_CODE>
<!-- END ADDITION -->

X-FB-External-Domain: wa.meta.vc
Allow: INVITE, ACK, BYE, CANCEL, NOTIFY, OPTIONS
User-Agent: Facebook SipGateway
Content-Length:  0
```

* `BSUID` — Will be the user's BSUID if the call was made to the user's BSUID, or if the user has adopted a username and (1) you haven't messaged or called the user's phone number in the last 30 days, or (2) your business phone number is not in the user's WhatsApp contacts list. Otherwise, it will be the user's phone number.
* `USERNAME` — Will be the user's username.
* `USER_COUNTRY_CODE` — Will be the user's country code (*subject to change*).

## Coexistence

### History webhooks

These changes will apply to [history](/docs/whatsapp/cloud-api/webhooks/reference/history) webhooks that describe an onboarded business customer's WhatsApp Business app chat history.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<CUSTOMER_WABA_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<CUSTOMER_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<CUSTOMER_PHONE_NUMBER_ID>"
            },
            "history": [
              {
                "metadata": {
                  "phase": <PHASE>,
                  "chunk_order": <CHUNK_ORDER>,
                  "progress": <PROGRESS>
                },
                "threads": [
                  <!-- First chat history thread object -->
                  {
                    "id": "<WHATSAPP_USER_PHONE_NUMBER>",                    <!-- CHANGED -->
                    "context": {                                             <!-- ADDED -->
                      "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>",               <!-- ADDED -->
                      "user_id": "<BSUID>",                                  <!-- ADDED -->
                      "username": "<USERNAME>",                              <!-- ADDED -->
                      "country_code": "US"                                   <!-- ADDED -->
                    },
                    "messages": [
                      <!-- First message object in thread -->
                      {
                        "from": "<BUSINESS_OR_WHATSAPP_USER_PHONE_NUMBER>",  <!-- CHANGED -->
                        "from_user_id" : "<BSUID>",                          <!-- ADDED -->
                        "to": "<WHATSAPP_USER_PHONE_NUMBER>",
                        "id": "<WHATSAPP_MESSAGE_ID>",
                        "timestamp": "<DEVICE_TIMESTAMP>,
                        "type": "<MESSAGE_TYPE>",
                        "<MESSAGE_TYPE>": {
                          <MESSAGE_CONTENTS>
                        },
                        "history_context": {
                          "status": "<MESSAGE_STATUS>"
                        }
                      },
                      <!-- Additional message objects in thread would follow, if any -->
                    ]
                  },
                  <!-- Additional chat history thread objects would follow, if any -->
                ]
              }
            ]
          },
          "field": "history"
        }
      ]
    }
  ]
}
```

* `id` — New empty value. Will be an empty string if, at the time when the user sent the message to the business customer, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `context` — A new context object will be included.
* `wa_id` — New property. Will be an empty string if, at the time when the user sent the message to the business customer, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's BSUID.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Will be set to the user's country code (\_subject to change).
* `from` — New empty value. Will be an empty string if, at the time when the user sent the message to the business customer, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `from_user_id` — New property. Will be set to the user's BSUID.

These changes will apply to [history](/docs/whatsapp/cloud-api/webhooks/reference/history) webhooks that describe a media asset sent from a WhatsApp user to a business customer, or vice-versa.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<CUSTOMER_WABA_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<CUSTOMER_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<CUSTOMER_PHONE_NUMBER_ID>"
            },
            "contacts": [                                              <!-- ADDED -->
              {
                "profile": {
                  "username": "<USERNAME>",                            <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"                     <!-- ADDED -->
                },
                "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>",               <!-- ADDED -->
                "user_id": "<BSUID>"                                   <!-- ADDED -->
              },
            ],

            <!-- Only for messages sent from a user to a business -->
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER>",
                "from_user_id": "<BSUID>",                             <!-- ADDED -->
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<ORIGINAL_WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "<MEDIA_TYPE>",
                "<MEDIA_TYPE>": {
                  <MEDIA_METADATA>
                }
              }
            ],

            <!-- Only for messages sent from a business to a user -->
            "message_echoes": [
              {
                "from": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
                "to": "<WHATSAPP_USER_PHONE_NUMBER>",                  <!-- CHANGED -->
                "to_user_id": "<BSUID>",                               <!-- ADDED -->
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "<MESSAGE_TYPE>",
                "<MESSAGE_TYPE>": {
                  <MESSAGE_CONTENTS>
                }
              }
            ]

          },
          "field": "history"
        }
      ]
    }
  ]
}
```

* `contacts` — A new contacts object will be included.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Will be set to the user's country code (*subject to change*).
* `wa_id` — New property. Will be an empty string if, at the time when the user sent the message to the business customer, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's BSUID.
* `from_user_id` — New property. Will be set to the user's BSUID.
* `to` — New empty value. Will be an empty string if, at the time when the business sent the message to the user, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `to_user_id` — New property. Will be set to the user's BSUID.

### smb\_message\_echoes webhooks

These changes will apply to [smb\_message\_echoes](/docs/whatsapp/cloud-api/webhooks/reference/smb_message_echoes) webhooks.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "contacts": [                                     <!-- ADDED -->
              {
                "profile": {
                  "username": "<USERNAME>",                   <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"            <!-- ADDED -->
                },
                "wa_id": "<WHATSAPP_USER_PHONE_NUMBER>",      <!-- ADDED -->
                "user_id": "<BSUID>"                          <!-- ADDED -->
              }
            ],
            "message_echoes": [
              {
                "from": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
                "to": "<WHATSAPP_USER_PHONE_NUMBER>",         <!-- CHANGED -->
                "to_user_id": "<BSUID>",                      <!-- ADDED -->
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>",
                "type": "<MESSAGE_TYPE>",
                "<MESSAGE_TYPE>": {
                  <MESSAGE_CONTENTS>
                }
              }
            ]
          },
          "field": "smb_message_echoes"
        }
      ]
    }
  ]
}
```

* `contacts` — A new contacts object will be included.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Will be set to the user's country code (*subject to change*).
* `wa_id` — New property. Will be an empty string if, at the time when the user sent the message to the business customer, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's BSUID.
* `to` — New empty value. Will be an empty string if, at the time when the business sent the message to the user, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of when the message was sent, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `to_user_id` — New property. Will be set to the user's BSUID.

### smb\_app\_state\_sync webhooks

These changes will apply to [smb\_app\_state\_sync](/docs/whatsapp/cloud-api/webhooks/reference/smb_app_state_sync) webhooks.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<WHATSAPP_BUSINESS_ACCOUNT_ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "<BUSINESS_DISPLAY_PHONE_NUMBER>",
              "phone_number_id": "<BUSINESS_PHONE_NUMBER_ID>"
            },
            "state_sync": [
              {
                "type": "contact",
                "contact": {
                  "full_name": "<CONTACT_FULL_NAME>",
                  "first_name": "<CONTACT_FIRST_NAME>",
                  "phone_number": "<CONTACT_PHONE_NUMBER>",    <!-- CHANGED -->
                  "user_id": "<BSUID>",                        <!-- ADDED -->
                  "username": "<USERNAME>",                    <!-- ADDED -->
                  "country_code": "<COUNTRY_CODE>"             <!-- ADDED -->
                },
                "action": "<ACTION>",
                "metadata": {
                  "timestamp": "<WEBHOOK_TRIGGER_TIMESTAMP>"
                }
              },
              <!-- Additional contacts would follow, if any -->
            ]
          },
          "field": "smb_app_state_sync"
        }
      ]
    }
  ]
}
```

* `phone_number` — New empty value. Will be an empty string if, at the time of the synchronization request, (1) the user had already enabled usernames, (2) the business customer had not messaged the user's phone number within 30 days of the synchronization request, and (3) the business customer's business phone number was not in the user's WhatsApp contacts list. Otherwise, it will be set to the user's phone number.
* `user_id` — New property. Will be set to the user's BSUID.
* `username` — New property. Will be set to the user's username, if the user has enabled the username feature. Property omitted if the user has disabled the username feature.
* `country_code` — New property. Will be set to the user's country code (*subject to change*).

## Analytics

No changes.

## Billing and invoicing

No changes

## FAQs

**What do I need to do to support usernames?**

BSUIDs and country code (subject to change) will begin appearing in webhooks payloads before usernames are made available to WhatsApp users. You will need to adopt BSUIDs in order to process user-initiated messages from users who have adopted a username. To do this, you must:

* Update your webhook integrations to support BSUIDs, which will be assigned to a new `user_id` property in existing webhooks.
* Build logic to support handling multiple identifiers (phone numbers from non-username adopters; BSUIDs from username adopters if phone number is not present in webhooks), and map relevant fields back to your CRM/database.
* Update internal and external systems related to these integrations to be able to handle BSUIDs and join with previous identifiers; primarily CRM (either 3P or internal database) and any tools or workflows triggered off of CRM (e.g., triggered campaign messages, campaign management, measurement, billing, etc.).
* If you still require customer phone numbers, update your messaging bots/journeys (if used) to request phone numbers, handle scenarios where users do not share phone numbers, and iterate on these new conversation journeys.
* If you have multiple business portfolios with Meta, you may want to implement a solution to enable central CRM access across multiple portfolios, to minimize the operational overhead that comes with using and storing BSUIDs.

**When will I receive a BSUID vs. a phone number?**

When a user adopts a username, they will have phone number privacy meaning their phone number will not be displayed in the app, and their phone number will not be included in webhooks. If the user's phone number is not present (the `wa_id` property is set to an empty string), you can use their BSUID, which will be included and assigned to a new `user_id` property.

If a user has not adopted usernames, you will receive both their phone number and their BSUID.

We will continue to share the phone number in a few cases, primarily for existing customer interactions. We’ll automatically include or return the user’s phone number on a rolling 30 days after any interaction between you and the user’s phone number, or if your business phone number is in the user's WhatsApp contacts list.

Per our Cloud API Terms of Service, however, phone numbers and related data are retained for a maximum of 30 days to support features like message redelivery. There may be situations where you receive messages from existing users outside of this 30 day window, which may look like a new user thread to you. Therefore, it is essential that you begin supporting BSUIDs as soon as possible, to minimize losing any conversation context.

**Why do partners and directly-integrated businesses using the Cloud API, including directly integrated ads that click to WhatsApp advertisers, have to adopt BSUID?**

Partners and businesses must adopt BSUID to continue processing incoming messages from WhatsApp username adopters. Once BSUID is adopted and user messages from username adopters are processed, message webhooks will no longer include phone numbers in some cases as part of the webhook such as wa\_id, so partners and businesses must ensure all connected systems can handle BSUID. They will also be able to ask for a user’s phone number in-thread.

**If a business has not yet adopted BSUID and starts to receive messages from username adopters which they cannot process, will there be any recourse or corrective action?**

If a business has not yet adopted BSUID and is not able to process messages from username adopters, there will not be any recourse or corrective action.

* For messages from new customers of the business: Meta will continue to send the webhook of an incoming message. Depending on the specifics of the implementation, this may impact systems that are not equipped to handle an empty string being sent in the wa\_id field when phone number is not present, and BSUID being sent through a new field.
* For messages from existing customers of the business: we will continue to share the phone number in a few cases, primarily for existing customer interactions.

**How do business usernames differ from display names? When will a user see a business username vs a display name?**

Business usernames will provide an ability for the users to reach the business by the business’ username, meaning an end user can search for a business username using their exact username and reach out to the businesses. Since end users cannot search by display names, business usernames offer a clear advantage as a searchable and unique identifier for users to reliably find the correct business.

Business usernames must follow specific formatting rules on length and allowed characters, while display names have some more leeway in terms of formatting.

Business usernames are unique and are tied 1-1 to phone numbers, meaning @JaspersMarket would be tied to one phone number while @JaspersMarketCustomerSupport would be tied to another phone number. Display names are not tied 1-1 to phone numbers, meaning the display name Jasper’s Market can have 10 phone numbers under this display name.

When a business has both a username and display name, display name will be shown first (e.g., in Profile, Chat list, Messages, etc), for the businesses to build trust with the users and for users to recognize the business when business reaches out to the user.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Business-scoped user IDs](#business-scoped-user-ids)

[User usernames](#user-usernames)

[Business-scoped user ID](#business-scoped-user-id)

[Phone numbers](#phone-numbers)

[Country codes](#country-codes)

[Business usernames](#business-usernames)

[Reserved usernames](#reserved-usernames)

[Chat window display priority](#chat-window-display-priority)

[Support](#support)

[Adopt or change a business username](#adopt-or-change-a-business-username)

[Get current username](#get-current-username)

[Get reserved usernames](#get-reserved-usernames)

[Delete a username](#delete-a-username)

[Response syntax:](#response-syntax-)

[Cancel pending username request](#cancel-pending-username-request)

[phone\_number\_username\_update webhook](#phone-number-username-update-webhook)

[Messages](#messages)

[Send message requests](#send-message-requests)

[Send message response](#send-message-response)

[Error codes](#error-codes)

[Marketing Messages API for WhatsApp](#marketing-messages-api-for-whatsapp)

[Send marketing message requests](#send-marketing-message-requests)

[Send marketing message response](#send-marketing-message-response)

[Messages webhooks](#messages-webhooks)

[Status messages webhooks](#status-messages-webhooks)

[Incoming messages webhooks](#incoming-messages-webhooks)

[System status messages webhooks](#system-status-messages-webhooks)

[User\_preferences webhooks](#user-preferences-webhooks)

[Groups API](#groups-api)

[Get group info](#get-group-info)

[Get group join requests](#get-group-join-requests)

[Remove group participants](#remove-group-participants)

[Groups API webhooks](#groups-api-webhooks)

[group\_participants\_update webhooks](#group-participants-update-webhooks)

[Blosk Users API](#blosk-users-api)

[Block or unblock user requests](#block-or-unblock-user-requests)

[Calling API](#calling-api)

[Businesses-initiated call requests](#businesses-initiated-call-requests)

[Get call permissions](#get-call-permissions)

[Send call permission request](#send-call-permission-request)

[Call permission request webhooks](#call-permission-request-webhooks)

[Business-initiated connected calls webhooks](#business-initiated-connected-calls-webhooks)

[User-initiated connected calls webhooks](#user-initiated-connected-calls-webhooks)

[Business-initiated terminated calls webhooks](#business-initiated-terminated-calls-webhooks)

[User-initiated terminated calls webhooks](#user-initiated-terminated-calls-webhooks)

[Business-initiated calls status webhooks](#business-initiated-calls-status-webhooks)

[SIP invites for business-initiated calls](#sip-invites-for-business-initiated-calls)

[SIP invites for user-initiated calls](#sip-invites-for-user-initiated-calls)

[SIP OK responses for business-initiated calls](#sip-ok-responses-for-business-initiated-calls)

[SIP BYE responses for business- and user-initiated calls](#sip-bye-responses-for-business--and-user-initiated-calls)

[Coexistence](#coexistence)

[History webhooks](#history-webhooks)

[smb\_message\_echoes webhooks](#smb-message-echoes-webhooks)

[smb\_app\_state\_sync webhooks](#smb-app-state-sync-webhooks)

[Analytics](#analytics)

[Billing and invoicing](#billing-and-invoicing)

[FAQs](#faqs)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfhY3tsdNHy2QZhjc33OjXVPTW3lEpx7aAs12ogQTZuRbA&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_Afht6wnCaDB7YeHuvmqs9YPQUFW8gwm1_qYpkG25TWhzPA&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_Afj3bBlUnWBX41aVEqe-VXxGng6P5wV79P9a9zqT-SghRg&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3DhuG4KTXS3OaIUpXyFJ3bcaSIfbYNIsYj6i8_EztaoZ3yrgq1i0aDawjEqa03iQdcw8RIA3g-BlQyMB86rjw1TMcxkp5sAILg0hlxZ1dUa5PoNTO-cu8Dd8IN9Yq0gUA585JY8aFCpfOSB5uhQg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfjCtSUlJ1A06V3otwkFoPZRsLv0nlKgfSc0IaKeU0qBRw&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3i_GyX5BcVg8j_6WoTc7gjf5alkKDnYZBPMXnr-6JwbvVxh5z3pgvVlNiRPdVJU-20wZeGjBjePg_p7vA9UXIYQVwuPPpoBFEwRmdBZhCt28FKDn21UaBYApEd6_uPi3ottNw6GdU4Tk20Lgdk8Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfiR7OzpPA0DBSpd0_Qmyk4oDfYb8F4_AG01RdosfwmEPQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0ZTboGJ52WVnhX736N_aTRkcKt2jUjYXy5Kou8fRGIOGjxwrHaeMNQbh-FFeQQEtm4nRMUmmHv-PmDkQ5BB8GhgvzU1bOqxHmtXbHQuxVNvPvLzHyDOqZyHuV7xGuTS0dIA31ygrmJh8cvASLzTw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_Afh6srsyKI36No8uyixCKvwB2SdWzsu9KyR6heMCtU5DdA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3DmQO6tdY9ZbSpCFnlpaQFqs0uvmF9JfdMwb4cQa4SkOUm6XoIoJlO6jdqFfg1Em7iL-NIPIczxX8gEnrU8VsFgrhoGoY4BqwY7VNCJTDKp3gKx2gc-DmALZQ3WE5pH7KBiTBKgwGjzkreBzFjew)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0vbghVsBdu2Z8ZJt8BcZmNVhD2Nd64TgCj5lgd-GI82oe-wwxPL8ajV3S_RxNVpnhM6-ePUrc60k8W9enR8mcayn64VzZOHIG34GA_PXxO-u0I1dw6r5d1ma4fvJQvLjX-_zJ7FWdWUQrznNhzqg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3h7HvOcr0WlCrcPBbiInXw-iGdWV-ctNy30ZLxCFaSGbRrycIKKFVFlvAmkNKzdzoP9OafoeHzlD4A4DxMASTp_ySbPC0gOsKq-PVcNsCRcJWgZdJurb_cFy71RtINGEQSmbN8c-nthtLcn-ZIlQ)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfimBdyPj5d5pPiGHuNScfG1wxA-4tXbORxiPvugCBZ5dg&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfjBprvbpRs_E3Mu8juLga0AxdGECdW0aKIF92ZhOgOHWg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0hJ_79pPvUQjU9FjZRCUfVbYlKId3o9OEoqKx3yRSDkbyOijS-IlAN3uKleOOFca0g-ulcI3bUBE9LigwiXGGQUoDJFHou3BHFgjhOZVuMw6JcksQ6RbJwAYdD2Nv_FswnbIfnJ_QZodkuzsOK1Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfgoNmF5dRFSfmSWYNuCt35E8dNnqJ2USB9jZHYpSZ4VKw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT38eRZk1H6atU9SjIFTfYiOCz1Sjd4s32D2PfoA_dEK-QW1W-wqIy8MIbcvgUUYwaRVxhlV203rlEK-l6rtQW-Jf4TMiRWrH52DYWcSREudJqfKrn2mNTCtOYqv7DHUPSEzVFfc3j1pdGvQ5SRGLw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_Afi4LOUQO9tU-vvxKkLCCStpuuK62hydCnZLrNtEQ51C_A&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3YCknW1OyvjdWIUGeGV-epi0Y4l_x5ShWgEftIm6_ol7zvusozzKxFebGNqGByvxnyOKwD1uHVKUhNkrBDM6tDvCG6W9RM8fA32WqorZ3akf2G_VzpTNEnA-F4IipH8MOJ62Fjs_jvLAoVGHK99A)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=WIGLIE-_NExMJWFBTwdZqw&oh=00_AfgKPTh6GuXwnyKR4inbTCYlU-H61fY12lwlO7YrsQUyRQ&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3h-wDC74rvoxjNG9UJMi6NHY5Ipj74-ta93vgH0jT-2ks470BmWD1h1MGjowm7pAAR4e0SLMyMSldoRWUexZ1pYfs8yqxJ3jKm_KqvSexoGbOWXVjAYH0OSLNMlvlzCvDl1bw7HiQiESStuKlxdw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT39raBvhMng8fV4uC2jMO_yO6gSuQhOnhK9-9XtfoZDts82V9P2okbwgDe21GbDtgyoovP8ViANuPhPqKYfOXlQs1ZX4Q7PWjC-49ypov9AIjM4I5dDvjmfpE1BvbB1xNyVFcVrCbqtXnB2eF4KDQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)