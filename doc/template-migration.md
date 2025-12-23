+++
id = "template-migration"
title = "Template migration"
summary = "This document describes how to migrate templates from one WhatsApp Business Account (WABA) to another. Note that migration doesn't move templates, it recreates them in the destination WABA."
source = "https://developers.facebook.com/docs/whatsapp/template-migration"
lang = "en"
tags = ["whatsapp-business-platform", "templates", "rate-limits"]
+++
# Template migration

This document describes how to migrate templates from one WhatsApp Business Account (WABA) to another. Note that migration doesn't move templates, it recreates them in the destination WABA.

## Limitations

* Templates can only be migrated between WABAs owned by the same Meta business.
* Only templates with a status of `APPROVED` and a `quality_score` of either `GREEN` or `UNKNOWN` are eligible for migration.

## Request syntax

Use the [WhatsApp Business Account > Migrate Message Templates](/docs/graph-api/reference/whats-app-business-account/migrate_message_templates/) endpoint to migrate templates from one WABA to another.

```
curl -X POST "https://graph.facebook.com/<API_VERSION>/<DESTINATION_WABA_ID>/migrate_message_templates" \
-H "Authorization: Bearer <ACCESS_TOKEN>" \
-H "Content-Type: application/json" \
-d '
{
  "source_waba_id": "<SOURCE_WABA_ID>",
  "page_number": <PAGE_NUMBER>,
  "count": <COUNT>

  <!-- only if migrating specific templates that failed to migrate -->
  "template_ids": [<TEMPLATE_IDS>]
}'
```

### Parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<ACCESS_TOKEN>`  *String* | **Required.**  [System token](/docs/whatsapp/access-tokens#system-user-access-tokens) or [business token](/docs/whatsapp/access-tokens#business-integration-system-user-access-tokens). | `EAAAN6tcBzAUBOZC82CW7iR2LiaZBwUHS4Y7FDtQxRUPy1PHZClDGZBZCgWdrTisgMjpFKiZAi1FBBQNO2IqZBAzdZAA16lmUs0XgRcCf6z1LLxQCgLXDEpg80d41UZBt1FKJZCqJFcTYXJvSMeHLvOdZwFyZBrV9ZPHZASSqxDZBUZASyFdzjiy2A1sippEsF4DVV5W2IlkOSr2LrMLuYoNMYBy8xQczzOKDOMccqHEZD` |
| `<API_VERSION>`  *String* | **Optional.**  Graph API version. | `v24.0` |
| `<COUNT>`  *Integer* | **Optional.**  Overrides the default batch size with a maximum count of 500.  If the request takes longer than 30 seconds to execute and times out, reduce the count number. | `200` |
| `<DESTINATION_WABA_ID>`  *WhatsApp Business Account ID* | **Required.**  Destination WhatsApp Business Account ID. | `104996122399160` |
| `<PAGE_NUMBER>`  *Integer* | **Optional.**  Indicates amount of templates to migrate as sets of 500. Zero-indexed. For example, to migrate 1000 templates, send one request with this value set to `0` and another request with this value set to `1`, in parallel. | `0` |
| `<TEMPLATE_IDS>`  *Array of strings* | **Optional.**  Only use to migrate specific template IDs with a max array length of 500. For example, to migrate failed template IDs, add the specific template ID to the array. | `["35002248699842","351234565148","54382248699842"]` |
| `<SOURCE_WABA_ID>`  *WhatsApp Business Account ID* | **Required.**  Source WhatsApp Business Account ID. | `102290129340398` |

## Response

```
{
  "migrated_templates": [<MIGRATED_TEMPLATES>],
  "failed_templates": [<FAILED_TEMPLATES>]
}
```

### Response properties

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<MIGRATED_TEMPLATES>`  *List* | List of template IDs that were successfully duplicated in the destination WhatsApp Business Account. | `"1473688840035974","6162904357082268","6147830171896170"` |
| `<FAILED_TEMPLATES>`  *Map* | Map identifying templates that were not duplicated in the destination WhatsApp Business Account.   Keys are template IDs and values are failure reasons. | `"1019496902803242":"Incorrect category",` `"259672276895259":"Formatting error - dangling parameter",` `"572279198452421":"Incorrect category"` |

## Example request

```
curl -X POST 'https://graph.facebook.com/v24.0/104996122399160/migrate_message_templates?source_waba_id=102290129340398&page_number=0' \
-H 'Authorization: Bearer EAAJB...'
```

## Example response

```
{
  "migrated_templates": [
    "1473688840035974",
    "6162904357082268",
    "6147830171896170"
  ],
  "failed_templates": {
    "1019496902803242": "Incorrect category",
    "259672276895259": "Formatting error - dangling parameter",
    "572279198452421": "Incorrect category"
  }
}
```
