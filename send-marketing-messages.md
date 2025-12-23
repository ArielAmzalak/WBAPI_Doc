![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fsending-messages%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Sending messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages)

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

[Sending messages](#sending-messages)

[Create marketing templates](#create-marketing-templates)

[Automatic Creative Optimizations](#automatic-creative-optimizations)

[Image cropping](#image-cropping)

[Image filtering](#image-filtering)

[Text overlays](#text-overlays)

[Image animation](#image-animation)

[Image background generation](#image-background-generation)

[Headline extraction](#headline-extraction)

[Tap-target title extraction](#tap-target-title-extraction)

[Product extensions](#product-extensions)

[Text formatting](#text-formatting)

[Configure Automatic Creative Optimizations (Template-level)](#configure-automatic-creative-optimizations--template-level-)

[Configure Automatic Creative Optimizations (Whatsapp business account-level)](#configure-automatic-creative-optimizations--whatsapp-business-account-level-)

[Send marketing template messages](#send-marketing-template-messages)

[Request Syntax](#request-syntax)

[Receiving message status webhooks](#receiving-message-status-webhooks)

[Receiving incoming messages](#receiving-incoming-messages)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Sending messages

Marketing Messages for WhatsApp allows you to send Marketing template messages only. For sending other message types, and for receiving messages, you can use Cloud API in parallel with Marketing Messages for WhatsApp on the same business phone number.

If you use a partner’s UI portals or APIs to configure and send marketing messages, you can continue to do so, and do not need to use any of the below capabilities - your partner will take care of integrating with MM API for WhatsApp's message sending functions on your behalf.

## Create marketing templates

Marketing templates can be created in several ways:

1. Via WhatsApp Business Manager UI
2. Via the Business Management API “Message Templates” endpoint
3. If you work with a partner, your partner may offer their own API or UIs for template creation, which leverage the “Message Templates” endpoint

See documentation on how to [Create and Manage Templates here](/docs/whatsapp/business-management-api/message-templates).

When a new Marketing template is created, it will take up to 10 minutes to sync with corresponding Ad account, allowing messages to be optimized and click and downstream conversions to be measured. Templates which have been inactive for longer than 7 days will also require 10 minutes to sync after the first new use. Please wait 10 minutes after creating new Marketing Templates (or 10 minutes after sending the first marketing message on a dormant Template) before sending marketing traffic.

Marketing Messages for WhatsApp supports all Marketing templates. In addition, MM API for WhatsApp provides the following additional features that are not available to Marketing templates on Cloud API:

* **Time-To-Live (TTL) for Marketing template messages:** If we are unable to deliver a message to a WhatsApp user, we will retry the delivery for a period of time known as a time-to-live, TTL, or the message validity period. TTL is available for Authentication and Utility template messages on Cloud API, but TTL for Marketing template messages is exclusively available on MM API for WhatsApp. See documentation on how to [Create and Manage Templates via API](/docs/whatsapp/business-management-api/message-templates#time-to-live--ttl---customization--defaults--min-max-values--and-compatibility) or [How to set a custom message validity period via UI](https://www.facebook.com/business/help/1305007343713790) for details on how to set TTLs for Marketing template messages.

## Automatic Creative Optimizations

Automatic Creative Optimizations are currently only available to businesses participating in early access. It will be made available to all businesses on a future date.

Automatic Creative Optimizations enhance the visual appeal and engagement of Marketing template messages. This feature is not predictable, meaning the output may vary between messages even with the same input.

This capability tests minor variations of your existing image header with different crop orientations or color filters, and automatically selects the variant which is getting the highest click-through rate over time with no input needed from you. These creative enhancements are designed to help improve performance and visual appeal of marketing messages, while maintaining the fidelity of the message. These optimizations are similar to [Advantage+ creative](https://www.facebook.com/business/help/297506218282224?id=649869995454285).

### Image cropping

For some campaigns, we will automatically crop header images to an optimal dimension, ensuring your visuals are always perfectly framed without cutting off image text:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/490288529_1839136930195624_7868580583654703557_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=AWfHLtWgVU8Q7kNvwG0i2Oi&_nc_oc=AdkfEGv_WhDRz3pYNtXh7s-68d74Rf19xE8Y1z38O3T2b2-IbtQ6dKfdtbuOvJpbQSk&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfjWo4SyMovwtgZFZyFv7vICwVicgpxM76D6rBQHrrcpVg&oe=69406225)

### Image filtering

For some campaigns, we will automatically apply the most effective filters to header images in order to enhance the images’ quality and appeal:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/490148881_649567434578657_6531913133400572045_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=COiihxbOPWMQ7kNvwEpksD_&_nc_oc=AdmKQI62_opVgTTuknq5oZQsDkyMmwFS2bN2zw6kKem3qGDzo2WCA1Y0LHNWE1QXGFw&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afi5MWx9lghWmJg23NtLo27BSTlYdfBQ_7IN8W7TZiG0TA&oe=69404ADE)

Automatic Creative Optimizations run silently for all image headers sent via MM API for WhatsApp, working to select the header image with the most visual appeal and click-through. They can be disabled using the Message template API, providing businesses flexibility and control over how creative enhancements are applied. See API request call below for more details.

### Text overlays

For some campaigns, we will automatically add a text overlay onto your image using your message content:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/510250002_997759808891598_7747444436127893252_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=XVxmtQFeNr4Q7kNvwEEv31s&_nc_oc=AdnOvS3VeRJA14JSXxya0gu2BipQHn-gTT7XztuhSdOWgoy6Z-TqrNgUFPBgANXr7A0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfiR86hw0Cz0VnLFuUbB2G6wyIAwpesQkFyQajPBsYNwxA&oe=69404D25)

### Image animation

For some campaigns, we will automatically transform your header image into an animated GIF:

|  |  |  |  |
| --- | --- | --- | --- |
|  | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/499208944_582725901558956_3362739552469670606_n.png?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=0ozk7bLmlzMQ7kNvwFlrk6W&_nc_oc=Adk-jZuK4neLzA1TZlt0xpdMIbx8oJzCuVuHpbaj6q4KAYE3O72vG8YDPLPC9XQxcF0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afjiuth9E-fRFRfizj5lTJWJnbxk_urEQwgManzVWACsGQ&oe=6940743D) | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/512706297_1012568737452141_3654535789190862417_n.gif?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=21_aWjZpEzcQ7kNvwEjfP6t&_nc_oc=AdnMI8U7hu5Q_ZLfZJZoI_XYFGRS8KtjyxP0lhBsPH3m1yoF4VhWss9aYZLbp_xiGaY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhD87uPRwDiiy7GCAz2Q7nyrcft_dB0YvvbT3gr2LWU2A&oe=6940491C) |  |

### Image background generation

For some campaigns, we will automatically generate a new image background:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/529481192_1905147433612259_8373917617145368846_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=LZs0l5dvHq0Q7kNvwFKwLHQ&_nc_oc=AdmDkxEPmEXPTrdiSoiZz-PHHHg1mRhCAOtjgYK_tra3DiwJJih2ZhiEeBAI3_nbKU8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfgsZ6YBHnLjpRQ8DFBg4MFYWwUGRT_Zozd9rCh0BllbQw&oe=69404B87)

### Headline extraction

For some campaigns, we'll extract keywords or phrases from your message to create a headline for your body text to highlight key information.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/568356332_1741218023258733_764318396409509397_n.png?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=gSYVXID4ou0Q7kNvwHr8_N2&_nc_oc=AdlXL_PP99W3dF3B3YL7GG1mEUltLiMQ_1iIHQEbJ5JqbQnZhw5FZSd5xUiv-zEC1OM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfgkKHOyy-6HAOXpAMVKQMHvedypcKPC0Y25PRuNAbOczQ&oe=69407473)

### Tap-target title extraction

For some campaigns, we'll extract keywords or phrases from your message to create a title for the tap-target area to highlight key information.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/565927808_1275784957569302_5821755358925562973_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=-1LRv3Cc88YQ7kNvwF5LDoB&_nc_oc=AdmOA1-Ft5v8rr6sIdU1pPVlr0ijuyUmU3sOchK-LrLuDxMP3PSc3_D88khm2TaB3eA&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfiG_FZkIsYYRG2K6RZRHMI4eb71q4XBr9GjbTR0tVqXpw&oe=694066BF)

### Product extensions

We will enhance single-image creatives by appending a set of additional catalog products users are likely to engage or convert with, creating more personalized and relevant experiences.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/571739475_802429889249611_5730968219809248185_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=NOahw3hXUQQQ7kNvwGPnfLs&_nc_oc=AdnRtLUxCLTkYCFf1T9Us39AhTwCG8RiStzq6kImtdMPQycwDot7eZpjuDMdeWoFwJY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhZmH1vPFhchuAv-mu5MHgOneK5a89pbDKRd7oiC_y21g&oe=69403DE4)

### Text formatting

For some campaigns, we update the formatting of text (e.g. remove unnecessary spaces, bold phrases) to increase performance. No text content is changed - format only.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/571559956_1527237245143422_4708127400362964555_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=C6qZ5Yb_unUQ7kNvwFGF6zA&_nc_oc=AdneRAB5FP6g5U92GPCW7l5gocq5wRVlhjvfr5imajAC6lZVpJxoJ85-ateOpoe6NTc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhXnsvx-BubbW9GpCKEV9daSAtY9wW6vqMfYJBlcQ8U0A&oe=69406874)

### Configure Automatic Creative Optimizations (Template-level)

All optimization features are enabled by default, but you can use the `creative_features_spec` object to specify which optimizations you want to enable ("opt-in") or disable ("opt-out") on a given template. To do this, set each optimization's `enroll_status` property to either `OPT_IN` or `OPT_OUT` upon template creation, or when editing an existing template. For example:

```
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates
{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE_AND_LOCALE_CODE>",
  "components": [<TEMPLATE_COMPONENTS>],
  "degrees_of_freedom_spec": {
    "creative_features_spec": {
      "image_brightness_and_contrast": {
        "enroll_status": "OPT_OUT"
      },
      "image_touchups": {
        "enroll_status": "OPT_IN"
      },
      "add_text_overlay": {
        "enroll_status": "OPT_OUT"
      },
      "image_animation": {
        "enroll_status": "OPT_IN"
      },
      "image_background_gen": {
        "enroll_status": "OPT_IN"
      },
     "text_extraction_for_headline": {
       "enroll_status": "OPT_IN"
     },
     "text_extraction_for_tap_target": {
       "enroll_status": "OPT_IN"
     },
      "product_extensions": {
        "enroll_status": "OPT_OUT"
      },
      "text_formating_optimization": {
        "enroll_status": "OPT_OUT"
      }
    }
  }
}
```

### Configure Automatic Creative Optimizations (Whatsapp business account-level)

All optimization features are enabled by default, but you can use the creative\_features\_spec object to specify which optimizations you want to enable (“opt-in”) or disable (“opt-out”) for the entire Whatsapp business account. To do this, set each optimization’s enroll\_status property that you wish to modify to either OPT\_IN or OPT\_OUT. For example:

```
POST /<WHATSAPP_BUSINESS_ACCOUNT_ID>
{
  "degrees_of_freedom_spec": {
    "creative_features_spec": {
      "image_touchups": {
        "enroll_status": "OPT_IN"
      },
      "image_animation": {
        "enroll_status": "OPT_IN"
      },
      "image_brightness_and_contrast": {
        "enroll_status": "OPT_IN"
      },
      "add_text_overlay": {
        "enroll_status": "OPT_IN"
      },
      "image_background_gen": {
        "enroll_status": "OPT_IN"
      },
      "text_extraction_for_headline": {
        "enroll_status": "OPT_IN"
      },
      "product_extensions": {
        "enroll_status": "OPT_IN"
      },
      "text_extraction_for_tap_target": {
        "enroll_status": "OPT_IN"
      },
      "text_formating_optimization": {
        "enroll_status": "OPT_OUT"
      }
    }
  }
}
```

## Send marketing template messages

Marketing Messages for WhatsApp is not supported for MSC businesses. `/marketing_messages` requests will either be routed via Cloud API or rejected if the `product_policy` filed is set to strict.

Sending messages follows the same API payload syntax as Sending Messages on Cloud API, and requires the same permissions.

The `/marketing_messages` endpoint supports **only** marketing template messages for MM API for WhatsApp and Cloud API. All other message types (freeform, Authentication, Service, Utility) are not supported, and will produce an error.

Marketing messages will only be sent via MM API for WhatsApp when the business customer has met all [onboarding requirements](/docs/whatsapp/marketing-messages-lite-api/onboarding). If onboarding requirements are not met, the marketing messages will still be routed via Cloud API. You may disable the ability to route to Cloud API by setting the optional field `product_policy` to strict.

Note: You may still use the `/messages` endpoint to send marketing messages through the Cloud API.

| Endpoint | Authentication |
| --- | --- |
| `/PHONE_NUMBER_ID/marketing_messages` | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.  Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_messaging` permission. |

### Request Syntax

```
POST /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/marketing_messages
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<WHATSAPP_USER_PHONE_NUMBER>",
  "type": "<MESSAGE_TYPE>",
  "<MESSAGE_TYPE>": {
    <MESSAGE_CONTENTS>
  },
  <!-- Optional -->
  "product_policy": "<PRODUCT_POLICY>",
  "message_activity_sharing": <SHARE_MESSAGING_ACTIVITY?>
}
```

MM API for WhatsApp provides the following additional features that are not available to Marketing template messages on Cloud API:

* **Product fallback policy:** Set `product_policy` to `CLOUD_API_FALLBACK` to have the API send the outgoing message via Cloud API, if [onboarding requirements](/docs/whatsapp/marketing-messages-lite-api/onboarding) have not been met. Set to `STRICT` if you do not want the API to fallback to sending the message via Cloud API.
* **Message activity sharing:** `message_activity_sharing` is an optional parameter at the message level that toggles on / off sharing message activities (e.g. message read) for that specific marketing message to Meta to help optimize marketing messages. If this parameter is not provided, the default WABA-level setting will be applied. You can always edit your default setting in Business Settings (see Changelog for a screenshot of this).

For details on message types, reference the Cloud API [Message Types documentation](/docs/whatsapp/cloud-api/guides/send-messages#message-types), as MM API for WhatsApp uses the same message send formatting.

## Receiving message status webhooks

MM API for WhatsApp triggers status [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) webhooks (sent, delivered, read). In addition, status messages webhooks that describe a message sent via MM API for WhatsApp, and that include pricing information, will have `pricing.category` and `conversation.type` set to `marketing_lite`. If the message is routed via Cloud API, `pricing.category` will be set to `marketing`.

```
{
  "conversation": {
    "id": "<CONVERSATION_ID>",
    "origin": {
      "type": "marketing_lite"
    }
  },
  "pricing": {
    "billable": true,
    "pricing_model": "PMP",
    "category": "marketing_lite"
  }
}
```

It is recommended that you maintain logs of each outgoing message ID, and whether that ID was sent via Cloud API or MM API for WhatsApp, in order to use the unique message ID returned in message status webhooks to identify the origin of the sent message.

## Receiving incoming messages

MM API for WhatsApp is a send-only API. It does not receive incoming messages from consumers. To receive incoming messages on a business phone number, use Cloud API in parallel with MM API for WhatsApp on the same phone number.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Sending messages](#sending-messages)

[Create marketing templates](#create-marketing-templates)

[Automatic Creative Optimizations](#automatic-creative-optimizations)

[Image cropping](#image-cropping)

[Image filtering](#image-filtering)

[Text overlays](#text-overlays)

[Image animation](#image-animation)

[Image background generation](#image-background-generation)

[Headline extraction](#headline-extraction)

[Tap-target title extraction](#tap-target-title-extraction)

[Product extensions](#product-extensions)

[Text formatting](#text-formatting)

[Configure Automatic Creative Optimizations (Template-level)](#configure-automatic-creative-optimizations--template-level-)

[Configure Automatic Creative Optimizations (Whatsapp business account-level)](#configure-automatic-creative-optimizations--whatsapp-business-account-level-)

[Send marketing template messages](#send-marketing-template-messages)

[Request Syntax](#request-syntax)

[Receiving message status webhooks](#receiving-message-status-webhooks)

[Receiving incoming messages](#receiving-incoming-messages)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afg7fyUryLIyHgISi1lIAWBNZ79-2g3WP-I4mmLNeUZxlw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afjjz2d3-VXlkTs9LlivHq8LxM-YfBuk28elVTwkLqGReQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhSnQPayejL2cn34J55ctImraIasiAY638gvLZ3ycA-Xw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT09mpcXbdHN2Iaj5qK21_hrxiVwY0oFiVb-M5jegF1wjeLKGPMPv8GT9SxZfh1wzHCq2Nu4MNCBzuPK2qo2IaymGVycx0VJdpVnJYvvxuDxY_B8t7QeUyOVRrTL9dFEHa71yLT_cNrJk3Qtgm8M-Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afj3_iF0zn-3mSq5RfQGpospkG9cxVHktuqjsaE9QjxqsA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT26Yx5wqXKUf4rh2JmSAWGn2TjZ6cXOSIsRgC4783odhY6hofggrbe0YiFDYzQfxGeiYVaUxkhUfelER_wTmFS0Ub8REKIsGZyhJuTA5Nm2RmgZVMWlCu_zP-wduVfyquegXWgnHv4VaQ7clA81Nj7GY_w48G-aBqQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfjbAEmER_ONdj_buhdUCmEsw319Hkp1XIHFx2GXf_Z-Sg&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2BOblO57HtNnyi3745xiqca-Hn2udwdwVDeDnuTmYFmfo_UurF6VvNsy2RviWi9AY4X14Sr8Iaijolaexekg6PoF-oCN8v0mbFdqS2dniYKkHpSYWS1pSCPazGHdS93Ia4rjVnW8IdpOWXBqiRnA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfiBywxtpELifXmf5fHMpHosy2LrAw47HDwnx_kvqiXZhg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1EJRhBzhFVfKv_uvyWAKbv75nnHGA3sbYlsHqOjauqz3nrH3OH3YhI07wvrR7vrdrFe79kJ9dp9Aq54Dnf32SvoMKVUekVFq0viTMbxKfzRPx55gpv0xhWZ0Bft2EL6FocIt6nMMqOJRMBWcIakw)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT1X1RyslFBHC2JdUNQTE1iCBbk74iRWyKElOjglx07Z0yspfJ1R3zXs01vXjCd0qS6Q24ALmhZ_ZXnjM8ns2FObsVZMerIbybgI4qRz2Hk-pchajrhEPuBsti8FSx6bdpkH5R4uy_k0jq-sqDOGaA)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2WB_EJralQIQl5joG4I0L7TiO0NJNcOQcB926MAFI7TC_xCzSToSmKpX5pxMGWkJ4uZkiwDcOMEgxChlI8oobyvZx2ejiCwV5J8JWdA1XuwiMQTK0a742FTOMWDmcOVXeUgzxlfFPfpOjAul7sfw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhqwetYbRRy_WEvRLBANpJbdgemqdw00_kA-EWYduJx0g&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfhoJ7D60wL155tF2IWFpRU9YDkqb01q16pN0ZZyfM5ppQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2cfRSIZl0O63jGtNe5Ab57pDQDxaq3Yfk3MN_TCyTBMlGYj2t7Et4LA-IUuCEl24diq_WAOFZfwurVGReF3ddAf5_BP1gpNU_vuD7Wc6n3LelRiZ_bb5wTmC1dOazhF9fHvDEgOJ5dYdOeBwrgys0wOr8kZrt5lwM)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfjwCPkdwAYQXyJCI4xl0riSL8mnqbmHRmicuxqduEJXAg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1onFoqDV0WqhXZhcgHH6qeAuftkKrQUhaMo7LeN_iG3nb1YG6lSAW36pAm3ov0MZizEU6KND9fnd_lINLwy_fIc6Z7KKHs9gjEaiWvtnkR0NqAuTZ-oYpi1p4UaPCVOWKlBBGd29eLiccd96miJw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_AfgaDNW5cxugvvZQiRsqfDIulKT6djV0HExKamWfVTAR4Q&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0N6ty5T6rBOUnwbQlih5t0GgTPEMiVON4FYJGQZBNs669Ap-d5CkxjKP26c-5sHaMtzieMamQ3tI0rGwDi6oTjKXL9I30CU7dXYYixPE7zisRGhOpYSP-pVRgqphx2d4i2efIBkTTHlyjajXNL5Q)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=VHyuCDijDXX60c0kKHjH1g&oh=00_Afj25CQoDNbl6KezkUMetqdp5JHhdQdaDnispb0uknozyg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2Ln7hkC115rJaWv0muYHDzdYfJymwLrygvz_ExeQn0DU3-d9rSBUZYJaqUWvjzGD3T1qkANez2jwYaYzfbhjgXMZmoCWPX4P6aHSj_Zmgv_g4vJLJz1aAGTHfYdxOXzm1u1NEs4GGcmdZ_lM7uHg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2jI8-wuFen2iYGvboR5miS0S7Eocmy_9xLNq11lT1FlXy-1mmgKAiaBLn8ZPInoRTwt-0R5TpPiM_7V_kGMDmlp6OYPAfPLDmZ1yOWckFFq1ngcF-hZ5SXPRHOJUt7z4EMzXx9MtEz2Is_qp_JhQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)