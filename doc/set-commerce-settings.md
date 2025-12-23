+++
id = "set-commerce-settings"
title = "Set Commerce Settings"
summary = "You can enable or disable the shopping cart and the product catalog on a per-business phone number basis."
source = "https://developers.facebook.com/docs/whatsapp/set-commerce-settings"
lang = "en"
tags = ["whatsapp-business-platform", "phone-numbers"]
+++
# Set Commerce Settings

You can enable or disable the shopping cart and the product catalog on a per-business phone number basis. By default, the shopping cart is enabled and the storefront icon is hidden for all business phone numbers associated with a WhatsApp Business Account.

## Requirements

* A [system token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [user token](/docs/whatsapp/access-tokens#user-access-tokens).
* The [whatsapp\_business\_management](/docs/permissions/reference/whatsapp_business_management) permission.
* If using a [system token](/docs/whatsapp/access-tokens#system-user-access-tokens), the system user must be granted full controll over the WhatsApp Business Account.
* Businesses based in India must [comply with all online selling laws](https://www.facebook.com/help/1104628230079278).

## Get Business Phone Numbers

Use the [WhatsApp Business Account > Phone Numbers](/docs/whatsapp/business-management-api/manage-phone-numbers#get-all-phone-numbers) endpoint to get a list of all business phone numbers associated with a WhatsApp Business Account.

## Enable/Disable Cart

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to enable or disable the shopping cart for a specific business phone number.

When enabled, cart-related buttons appear in the chat, catalog, and product details views:

When the cart is disabled, customers can see products and their details, but all cart related buttons will not appear in any view.

### Request Syntax

```
POST /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
  ?is_cart_enabled=<IS_CART_ENABLED>
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |
| `<IS_CART_ENABLED>` | `true` | Boolean. Set to `true` to enable cart or `false` to disable it. Default value is `true`. |

### Sample Request

```
curl -X POST 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings?is_cart_enabled=true' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "success": true
}
```

## Enable/Disable Catalog

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to enable or disable the product catalog for a specific business phone number.

When enabled, the catalog storefront icon and catalog-related buttons appear in chat views and business profile views:

When the catalog is disabled, the storefront icon and catalog-related buttons will not appear in any views and the catalog preview with thumbnails will not appear in the business profile view.

If you disable the catalog, wa.me links to your catalog, as well as the **View catalog** button that appears when you send your catalog link in a message will display an **Invalid catalog link** warning when tapped.

### Request Syntax

```
POST /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
  ?is_catalog_visible=<IS_CATALOG_VISIBLE>
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |
| `<IS_CATALOG_VISIBLE>` | `true` | Boolean. Set to `true` to show catalog storefront icon or `false` to hide it. Default value is `false`. |

### Sample Request

```
curl -X POST 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings?is_catalog_visible=true' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "success": true
}
```

## Get Commerce Settings

Use the [Business Phone Number > WhatsApp Commerce Settings](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/whatsapp_commerce_settings) endpoint to get an individual business phone number's commerce settings.

### Request Syntax

```
GET /<BUSINESS_PHONE_NUMBER_ID>/whatsapp_commerce_settings
```

### Parameters

| Placeholder | Sample Value | Description |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>` | `106850078877666` | Business phone number ID. |

### Sample Request

```
curl -X GET 'https://graph.facebook.com/v24.0/106850078877666/whatsapp_commerce_settings' \
-H 'Authorization: Bearer EAAJB...'
```

### Sample Response

```
{
  "data": [
    {
      "is_cart_enabled": true,
      "is_catalog_visible": true,
      "id": "727705352028726"
    }
  ]
}
```
