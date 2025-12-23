+++
id = "groups"
title = "Groups API"
summary = "The Groups API enables you to programmatically create groups for messaging and collaboration."
source = "https://developers.facebook.com/docs/whatsapp/groups"
lang = "en"
tags = ["whatsapp-business-platform", "messaging", "rate-limits", "pricing", "analytics"]
+++
# Groups API

The Groups API enables you to programmatically create groups for messaging and collaboration.

## How it works

Groups are an invite-only experience where participants join using a group invite link you send them. This invite link provides context about the group, helping the user decide whether they want to join.

## Get Started

When you are ready to start using the Groups API, head on over to our "Get Started" guide for more information:

## Quick Facts

* **Max group participants:** 8
* **Supported message types:** Text, media, text-based templates, and media-based templates
* **Max groups you can create:** 10,000 per business number
* **Max Cloud API businesses per group:** 1

## Analytics

**Performance metrics are not available for message templates used in Groups.**

Please create new templates specifically for Groups use instead of repurposing templates used for one-to-one messaging.

## Limits

**Eligibility for Groups API**

To qualify for groups features, your business must meet the following requirements:

* Have a messaging limit of at least 100,000 business-initiated conversations in a rolling 24-hour period
* Be an [Official Business Account (OBA)](/docs/whatsapp/official-business-accounts)

*Groups are **not available** for [Coexistence users](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users/) and phone numbers onboarded to [Multi-solution Conversations](/docs/whatsapp/multi-solution-conversations)*.

*The [Calling API](/docs/whatsapp/cloud-api/calling) is not supported in groups.*

* **Non-supported message types:**
  + Calling
  + Disappearing messages
  + View-once
  + Auth
  + Commerce messages
  + Interactive messages

* **Non-supported actions:**
  + Admin hide group participant list
  + Edit message
  + Delete message
  + Marking message as read

## Pricing

The Groups API uses [per-message pricing](/docs/whatsapp/pricing).

## Features and reference

### Group management features

* [Create and delete group](/docs/whatsapp/cloud-api/groups/reference/#create-group)
* [Groups with join requests enabled](/docs/whatsapp/cloud-api/groups/reference#groups-with-join-requests)
* [Get and reset group invite link](/docs/whatsapp/cloud-api/groups/reference/#get-and-reset-group-invite-link)
* [Send group invite link template message](/docs/whatsapp/cloud-api/groups/reference#send-group-invite-link-template-message)
* [Remove group participants](/docs/whatsapp/cloud-api/groups/reference/#remove-group-participants-endpoint)
* [Get group info](/docs/whatsapp/cloud-api/groups/reference/#get-group-info)
* [Get active groups](/docs/whatsapp/cloud-api/groups/reference/#get-active-groups)
* [Update group settings](/docs/whatsapp/cloud-api/groups/reference/#update-group-settings)

### Group messaging features

* [Send group messages](/docs/whatsapp/cloud-api/groups/groups-messaging#send-group-message)
* [Receive group messages](/docs/whatsapp/cloud-api/groups/groups-messaging#receive-group-messages)
* [Pin and unpin group message](/docs/whatsapp/cloud-api/groups/groups-messaging#pin-and-unpin-group-message)
