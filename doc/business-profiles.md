+++
id = "business-profiles"
title = "Business profiles"
summary = "Your business phone number's business profile provides additional information about your business, such as its address, website, description, etc."
source = "https://developers.facebook.com/docs/whatsapp/business-profiles"
lang = "en"
tags = ["whatsapp-business-platform"]
+++
# Business profiles

Your business phone number's business profile provides additional information about your business, such as its address, website, description, etc. You can supply this information when registering your business phone number, or later, via WhatsApp Manager or API.

## Viewing or updating your profile via WhatsApp Manager

To view or update your business profile via WhatsApp Manager:

1. Navigate to [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/) > **Account tools** > **Phone numbers**.
2. Select your business phone number.
3. Click the **Profile** tab to view your current profile.
4. Use the form to set new profile values.

## Getting your profile via API

Use the [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/whatsapp\_business\_profile](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_business_profile/#Reading) endpoint to request specific business profile fields:

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/whatsapp_business_profile?fields=about,address,description,email,profile_picture_url,websites,vertical' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```
{
  "data": [
    {
      "about": "Succulent specialists!",
      "address": "1 Hacker Way, Menlo Park, CA 94025",
      "description": "At Lucky Shrub, we specialize in providing a...",
      "email": "lucky@luckyshrub.com",
      "profile_picture_url": "https://pps.whatsapp.net/v/t61.24...",
      "websites": [
        "https://www.luckyshrub.com/"
      ],
      "vertical": "RETAIL",
      "messaging_product": "whatsapp"
    }
  ]
}
```

## Updating your profile via API

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>/whatsapp\_business\_profile](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_business_profile/#Updating) endpoint to update specific business profile fields:

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/whatsapp_business_profile' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
--data-raw '
{
  "about": "Succulent specialists!",
  "address": "1 Hacker Way, Menlo Park, CA 94025",
  "description": "At Lucky Shrub, we specialize in providing a diverse range of high-quality succulents to suit your needs. From rare and exotic varieties to timeless classics, our collection has something for everyone.",
  "email": "lucky@luckyshrub.com",
  "messaging_product": "whatsapp",
  "profile_picture_handle": "4::aW...",
  "vertical": "RETAIL",
  "websites": "[\n  \"https://www.luckyshrub.com\"\n]"
}'
```

### Example response

Upon success:

```
{
  "success": true
}
```
