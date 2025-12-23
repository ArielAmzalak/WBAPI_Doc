![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Freference%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Group Management](/docs/whatsapp/cloud-api/groups/reference)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Group management](#group-management)

[Overview](#overview)

[Group management features](#group-management-features)

[Subscribe to groups metadata webhooks](#subscribe-to-groups-metadata-webhooks)

[Create group](#create-group)

[Request syntax](#request-syntax)

[Request body](#request-body)

[Request parameters](#request-parameters)

[Webhooks](#webhooks)

[Groups with join requests](#groups-with-join-requests)

[Get join requests](#get-join-requests)

[Approve join requests](#approve-join-requests)

[Reject join requests](#reject-join-requests)

[Webhook](#webhook)

[Get and reset group invite link](#get-and-reset-group-invite-link)

[Get group invite link](#get-group-invite-link)

[Reset group invite link](#reset-group-invite-link)

[Send group invite link template message](#send-group-invite-link-template-message)

[Request syntax](#request-syntax-2)

[Endpoint parameters](#endpoint-parameters)

[Request body](#request-body-2)

[Webhooks](#webhooks-2)

[Delete group](#delete-group)

[Request Syntax](#request-syntax-3)

[Request properties](#request-properties)

[Webhooks](#webhooks-3)

[Remove group participants](#remove-group-participants)

[Request syntax](#request-syntax-4)

[Request body](#request-body-3)

[Request properties](#request-properties-2)

[Webhooks](#webhooks-4)

[Get group info](#get-group-info)

[Request syntax](#request-syntax-5)

[Endpoint parameters](#endpoint-parameters-2)

[Available fields](#available-fields)

[Sample response](#sample-response)

[Get active groups](#get-active-groups)

[Request syntax](#request-syntax-6)

[Query Parameters](#query-parameters)

[Response Object](#response-object)

[Response parameters](#response-parameters)

[Update group settings](#update-group-settings)

[Request syntax](#request-syntax-7)

[Request body](#request-body-4)

[Request properties](#request-properties-3)

[Webhooks](#webhooks-5)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Group management

## Overview

The Groups API gives you simple functions to control groups through their lifecycle.

When you create a new group, an invite link is created for inviting participants to the group.

Since you cannot manually add participants to the group, simply send a message with your invite link to WhatsApp users who you would like to join the group.

## Group management features

* [Create and delete group](#create-group)
* [Groups with join requests enabled](#groups-with-join-requests)
* [Get and reset group invite link](#get-and-reset-group-invite-link)
* [Send group invite link template message](#send-group-invite-link-template-message)
* [Remove group participants](#remove-group-participants)
* [Get group info](#get-group-info)
* [Get active groups](#get-active-groups)
* [Update group settings](#update-group-settings)

To learn how to message groups, view the [Group Messaging reference](/docs/whatsapp/cloud-api/groups/groups-messaging).

## Subscribe to groups metadata webhooks

In order to receive webhook notifications for metadata about your groups, please subscribe to the following webhook fields:

* `group_lifecycle_update`
* `group_participants_update`
* `group_settings_update`
* `group_status_update`

For a full reference of webhooks for the Groups API, please visit our [Webhooks for Groups API reference](/docs/whatsapp/cloud-api/groups/webhooks).

## Create group

Use this endpoint to create a new group and generate a group invite link.

Once the group is created, you will receive a webhook with an `invite_link` parameter that contains an invite link for the group. You can send this invite link to WhatsApp users interested in joining the group.

Optionally, you can create a group that requires join approval. This means that if a WhatsApp user wants to join your group, you can approve or reject their request.

[Learn more about groups with join requests enabled](#groups-with-join-requests).

### Request syntax

Create a group with an initial group invite link:

`POST /<BUSINESS_PHONE_NUMBER_ID>/groups`

### Request body

```
{
  "messaging_product": "whatsapp",
  "subject": "<GROUP_SUBJECT>",
  "description": "<GROUP_DESCRIPTION>",
  "join_approval_mode": "<JOIN_APPROVAL_MODE>"
}
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | **Required**  Business phone number ID. | `12784358810` |
| `<GROUP_SUBJECT>`  *String* | **Required**  Group subject.  Maximum 128 characters. Whitespace is trimmed. | `New Purchase Inquiry` |
| `<GROUP_DESCRIPTION>`  *String* | **Optional**  Group description.  Maximum 2048 characters. | `Jim, an existing client, would like to learn about new car purchase options for current year models.` |
| `<JOIN_APPROVAL_MODE>`  *String* | **Optional**  Indicates if WhatsApp users who click the invitation link can join the group with or without being approved first.  Values can be:   * `approval_required` — Indicates WhatsApp users must be approved via [join request](#groups-with-join-requests) before they can access the group. * `auto_approve` — Indicates WhatsApp users can join the group without approval.   If omitted, `join_approval_mode` is set to `auto_approve` by default. | `auto_approve` |

### Webhooks

A `group_lifecycle_update` webhook is triggered.

#### Group create succeed

[View the "Group create succeed" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-create-succeed)

#### Group create fail

[View the "Group create fail" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-create-fail)

#### User joins group using invite link

[View the "User joins group using invite link" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#user-joined-group-using-invite-link-succeed)

## Groups with join requests

You can create groups that require join request approval. Once enabled, WhatsApp users who click the group invitation link can submit a request to join the group, or cancel a prior request:

When a WhatsApp user joins the group using a join request, a [`group_participants_update` webhook for a user accepting the join request] (/docs/whatsapp/cloud-api/groups/webhooks#user-accepts-or-cancels-join-request) is triggered. You can also [get a list of open join requests via API](#get-join-requests). Use the contents of the webhook or API response to approve or reject requests.

### Get join requests

#### Request syntax

`GET /<GROUP_ID>/join_requests`

#### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required.**  Group ID. | `Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD` |

#### Response syntax

Upon success:

```
{
  "data": [
    {
      "join_request_id": "<JOIN_REQUEST_ID>",
      "wa_id": "<WHATSAPP_USER_ID>",
      "creation_timestamp": "<JOIN_REQUEST_CREATION_TIMESTAMP">
    },
    //Additional join request objects would follow, if any
  ],
  "paging": {
    "cursors": {
      "before": "<BEFORE_CURSOR>",
      "after": "<AFTER_CURSOR>"
    }
  }
}
```

#### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<JOIN_REQUEST_ID>`  *String* | Join request ID. | `MTY0NjcwNDM1OTU6MTIwMzYzNDA0Njk0MjMzODIw` |
| `<WHATSAPP_USER_ID>`  *String* | WhatsApp user ID. | `16505551234` |
| `<JOIN_REQUEST_CREATION_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the join request was created. | `1755548877` |
| `<BEFORE_CURSOR>`  *String* | Before cursor. See [Paginated Results](/docs/graph-api/results). | `eyJvZAmZAzZAXQiOjAsInZAlcnNpb25JZACI6IjE3NTU1NTM3MDUxNzUwNTQ1MTAifQZDZD` |
| `<AFTER_CURSOR>`  *String* | After cursor. See [Paginated Results](/docs/graph-api/results). | `eyJvZAmZAzZAXQiOjAsInZAlcnNpb25JZACI6IjE3NTU1NTM3MDUxNzUwNTQ1MTAifQZDZD` |

### Approve join requests

#### Request syntax

`POST /<GROUP_ID>/join_requests`

#### Request body

```
{
  "messaging_product": "whatsapp",
  "join_requests": [
    "<JOIN_REQUEST_ID>",
    // Additional join request IDs would go here, if approving in bulk
  ]
}
```

#### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required.**  Group ID. | `Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD` |

#### Response syntax

Upon success, the API will respond with the following JSON payload, and WhatsApp users whose join requests were approved will be able to access the group when tapping the invite link.

```
{
  "messaging_product": "whatsapp",
  "approved_join_requests": [
    "<JOIN_REQUEST_ID>",
    // Additional join request IDs would go here, it approved in bulk
  ],

  //Only included if unable to approve one or more join requests

  "failed_join_requests": [
    {
      "join_request_id": "<JOIN_REQUEST_ID>",
      "errors": [
        {
          "code": "<ERROR_CODE>",
          "message": "<ERROR_MESSAGE>",
          "title": "<ERROR_TITLE>",
          "error_data": {
            "details": "<ERROR_DETAILS>"
          }
        }
      ]
    }
  ],
  "errors": [
    {
      "code": "<ERROR_CODE>",
      "message": "<ERROR_MESSAGE>",
      "title": "<ERROR_TITLE>",
      "error_data": {
        "details": "<ERROR_DETAILS>"
      }
    }
  ]
}
```

#### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<JOIN_REQUEST_ID>`  *String* | ID of approved join request, or ID of failed join request, if we were unable to approve. | `MTY0NjcwNDM1OTU6MTIwMzYzNDA0Njk0MjMzODIw` |
| `<ERROR_CODE>`  *Integer* | Error code, if unable to approve. | `131203` |
| `<ERROR_MESSAGE>`  *String* | Error message, if unable to approve. | `(#131203) Recipient has not accepted our new Terms of Service and Privacy Policy.` |
| `<ERROR_TITLE>`  *String* | Error title, if unable to approve. | `Unable to add participant to group` |
| `<ERROR_DETAILS>`  *String* | Error details, if unable to approve. | `Recipient has not accepted our new Terms of Service and Privacy Policy.` |

#### Webhook

A `group_participants_update` webhook is triggered.

[View the "User accepts join request" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#user-accepts-or-cancels-join-request)

### Reject join requests

#### Request syntax

`DELETE /<GROUP_ID>/join_requests`

#### Request body

```
{
  "messaging_product": "whatsapp",
  "join_requests": [
    "<JOIN_REQUEST_ID>",
    //Additional join request IDs would go here, it rejecting in bulk
  ]
}
```

#### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required.**  Group ID. | `Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD` |
| `<JOIN_REQUEST_ID>`  *String* | **Required.**  ID of join request to reject. | `MTY0NjcwNDM1OTU6MTIwMzYzNDA0Njk0MjMzODIw` |

#### Response syntax

Upon success, the API will respond with the following JSON payload, and the WhatsApp user will see the **Request to join** button again when accessing the group invite link.

```
{
  "messaging_product": "whatsapp",
  "rejected_join_requests": [
    "<JOIN_REQUEST_ID>",
    //Additional join request IDs would go here, it rejecting in bulk
  ],

  //Only included if unable to reject one or more join requests
  "failed_join_requests": [
    {
      "join_request_id": "<JOIN_REQUEST_ID>",
      "errors": [
        {
          "code": "<ERROR_CODE>",
          "message": "<ERROR_MESSAGE>",
          "title": "<ERROR_TITLE>",
          "error_data": {
            "details": "<ERROR_DETAILS>"
          }
        }
      ]
    }
  ],
  "errors": [
    {
      "code": "<ERROR_CODE>",
      "message": "<ERROR_MESSAGE>",
      "title": "<ERROR_TITLE>",
      "error_data": {
        "details": "<ERROR_DETAILS>"
      }
    }
  ]
}
```

#### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<JOIN_REQUEST_ID>`  *String* | ID of rejected join request, or ID of failed join request, if we were unable to reject. | `MTY0NjcwNDM1OTU6MTIwMzYzNDA0Njk0MjMzODIw` |
| `<ERROR_CODE>`  *Integer* | Error code, if unable to reject. | `131203` |
| `<ERROR_MESSAGE>`  *String* | Error message, if unable to reject. | `(#131203) Recipient has not accepted our new Terms of Service and Privacy Policy.` |
| `<ERROR_TITLE>`  *String* | Error title, if unable to reject. | `Unable to add participant to group` |
| `<ERROR_DETAILS>`  *String* | Error details, if unable to reject. | `Recipient has not accepted our new Terms of Service and Privacy Policy.` |

### Webhook

None.

## Get and reset group invite link

Once an invite link is reset, all previous invite links will become invalid.

An invite link for the group is generated when the group is created. Use these endpoints to get and reset group invite links.

For each endpoint, you will need your group ID in order to get or reset a link for the correct group as follows:

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required**  The ID of the group you want to get or reset an invite link for. | `Y2FwaV9ncm91cDoxOTUwNTU1MDA3OToxMjAzNjMzOTQzMjAdOTY0MTUZD` |

### Get group invite link

#### Request syntax

`GET /<GROUP_ID>/invite_link`

#### Response body

```
{
  "messaging_product": "whatsapp",
  "invite_link": "https://chat.whatsapp.com/<LINK_ID>"
}
```

Note that `invite_link` always begins with the prefix `https://chat.whatsapp.com/`. The only variable portion is `<LINK_ID>`.

### Reset group invite link

#### Request syntax

`POST /<GROUP_ID>/invite_link`

#### Request body

```
{
  "messaging_product": "whatsapp",
}
```

#### Response body

```
{
  "messaging_product": "whatsapp",
  "invite_link": "https://chat.whatsapp.com/<LINK_ID>"
}
```

## Send group invite link template message

[Template Library](https://business.facebook.com/wa/manage/template-library) contains a utility message template for sending group invite links to WhatsApp users. Use these pre-defined templates to send group invitations as utility messages.

**In order to keep the template priced as `utility`, you cannot modify it when you copy it from template library to your WABA.**

To send the template message:

#### Step 1. Add a group invite link template in Template Library to your account templates:

*In WhatsApp Manager*

1. Navigate to [Template Library](https://business.facebook.com/wa/manage/template-library)
2. On the left, click the **Group invite link** dropdown, then click the **Group invite upon request** checkbox.
3. Select the template you want to use, give it a name, and click **Submit**.

*Via the API*

You can query template libraries applicable to group invite links using the request below:

`GET /message_template_library?category=utility&topic=group_invite_link&language=en`

[Read more about finding and adding the template to your WABA via the api](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library/#using-the-api)

Template approval may require up to 24 hours. You’ll be able to send messages with this template after its approval.

#### Step 2. Send the template message

1. Send the template using the request syntax and body below, substituting your group id, the name you gave your template, and other applicable values.

When you provide the group id in the api request, it will be automatically translated into the corresponding group invite link upon message delivery.

### Request syntax

`POST /<BUSINESS_PHONE_NUMBER_ID>/messages`

### Endpoint parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<BUSINESS_PHONE_NUMBER_ID>`  *Integer* | **Required**  Business phone number ID. | `13057863445` |

### Request body

```
curl --location 'https://graph.facebook.com/<API_VERSION>/<BUSINESS_PHONE_NUMBER_ID>/messages?access_token=' \
      --header 'Content-Type: application/json' \
      --data '{
        "messaging_product": "whatsapp",
        "to": "<WHATSAPP_USER_PHONE_NUMBER>",
        "type": "template",
        "template": {
          "name": "<TEMPLATE_NAME>",
          "language": {
            "code": "<TEMPLATE_LANGUAGE>"
          },
          "components": [
            {
              "type": "body",
              "parameters": [
                {
                  "type": "group_id",
                  "group_id": "<GROUP_ID>"
                },
                {
                  ...additional parameters
                }
              ]
            }
          ]
        }
      }'
```

[Learn more about Template Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)

### Webhooks

#### User joins group using invite link

[View the "User joins group using invite link" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#user-joined-group-using-invite-link-succeed)

## Delete group

This endpoint deletes the group and removes all participants, including the business. No request body is required.

### Request Syntax

`DELETE /<GROUP_ID>`

### Request properties

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required**   The ID of the group you want to delete. | `Y2FwaV9ncm91cDoxOTUwNTU1MDA3OToxMjAzNjMzOTQzMjAdOTY0MTUZD` |

### Webhooks

A `group_lifecycle_update` webhook is triggered.

#### Delete group succeed

[View the "Delete group succeed" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#delete-group-succeed)

#### Delete group fails

[View the "Delete group fails" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#delete-group-fails)

## Remove group participants

Use this endpoint to remove participants from the group.

**Note: If a participant is removed from a group, they can no longer join the group via an invite link.**

### Request syntax

`DELETE /<GROUP_ID>/participants`

### Request body

```
{
  "messaging_product": "whatsapp",
  "participants": [
    { "user": "<WHATSAPP_USER_PHONE_NUMBER> or <WHATSAPP_USER_ID>" },
    { "user": "<WHATSAPP_USER_PHONE_NUMBER> or <WHATSAPP_USER_ID>"" },
    ...
  ]
}
```

### Request properties

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `"participants": []`  *Array* | **Optional**  Specifies an array of phone numbers or WhatsApp IDs of WhatsApp accounts. The business phone number used to create the group is always added to the group as the creator and admin.   * Maximum 8 participants. * The array cannot be empty. | ``` { "user": "+17865347866" },  { "user": "+7669992245" }, ... ``` |

### Webhooks

A `group_participants_update` webhook is triggered.

#### Group participant leaves

[View the "Group participant leaves" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#delete-group-succeed)

## Get group info

Use this endpoint to retrieve metadata about a single group.

**Note:** Specifying no fields in the query parameters will just return the group ID and messaging product.

### Request syntax

`GET /<GROUP_ID>?fields=<FIELDS>`

### Endpoint parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<GROUP_ID>`  *String* | **Required**   The ID of the group you are querying info from. | `Y2FwaV9ncm91cDoxOTUwNTU1MDA3OToxMjAzNjMzOTQzMjAdOTY0MTUZD` |
| `<FIELDS>`  *String* | **Optional**   A comma-separated list of fields to return. If no fields are passed in, only the group id is returned. | `"subject,description,participants,join_approval_mode"`  [Learn more about Graph API fields here](/docs/graph-api/overview/#fields) |

### Available fields

| Field | Description | Sample Return Value |
| --- | --- | --- |
| `join_approval_mode`  *String* | Indicates if WhatsApp users who click the invitation link can join the group with or without being approved first.  Values can be:   * `approval_required` — Indicates WhatsApp users must be approved via [join request](#groups-with-join-requests) before they can access the group. * `auto_approve` — Indicates WhatsApp users can join the group without approval. | `auto_approve` |
| `subject`  *String* | The subject for the group. | `"Artificial Intelligence Insights"` |
| `description`  *String* | The group description, if set during creation time. | `"Explore AI developments, share knowledge, and discuss the future of artificial intelligence with fellow enthusiasts and experts."` |
| `suspended`  *Boolean* | Returns `true` if the group has been suspended by whatsapp. | `false` |
| `creation_timestamp`  *Integer* | UNIX timestamp in seconds at which the group was created. | `683731200` |
| `participants`  *List* | A list of objects `{"wa_id": "<WA_ID>"}`, where `<WA_ID>` is a participant in the group being queried. | `[{"wa_id": "2228675309"}, {"wa_id": "7693349922"}]` |
| `total_participant_count`  *Integer* | The total number of participants in the group, excluding your business. | `6` |

### Sample response

```
{
  "messaging_product": "whatsapp",
  "id": "<GROUP_ID>",
  "subject": "<SUBJECT>",
  "creation_timestamp": "<TIMESTAMP>",
  "suspended": "<SUSPENDED>",
  "description": "<DESCRIPTION>",
  "total_participant_count": "<TOTAL_PARTICIPANT_COUNT>",
  "participants": [
    {
      "wa_id": "<WA_ID>"
    },
    {
      "wa_id": "<WA_ID>"
    }
  ],
  "join_approval_mode": "<JOIN_APPROVAL_MODE>"
}
```

## Get active groups

Use this endpoint to retrieve a list of active groups for a given business phone number.

### Request syntax

`GET /<BUSINESS_PHONE_NUMBER_ID>/groups`

### Query Parameters

```
  ?limit=<LIMIT>, // Optional
  &after=<AFTER_CURSOR>, // Optional
  &before=<BEFORE_CURSOR> // Optional
```

| Parameter | Description |
| --- | --- |
| `<LIMIT>`  *Optional* | Number of groups to fetch in the request.  Min: 1 | Default: 25 | Max: 1024 |
| `<BEFORE_CURSOR>`  *Optional* | Cursor that points to the beginning of a page of data. Learn more about [Paginated Results in Graph API here](/docs/graph-api/results/) |
| `<AFTER_CURSOR>`  *Optional* | Cursor that points to the end of a page of data. Learn more about [Paginated Results in Graph API here](/docs/graph-api/results/) |

### Response Object

```
{
  "data": {
    "groups": [
      {"id": "GROUP_ID", "subject": SUBJECT, "created_at": "TIMESTAMP"},
      {"id": "GROUP_ID", "subject": SUBJECT, "created_at": "TIMESTAMP"}
      …
    ]
  },
  "paging": {
    "cursors": {
      "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
      "before": "NDMyNzQyODI3OTQw"
    },
    "previous": "https://graph.facebook.com/VERSION/PHONE_NUMBER_ID/groups?limit=10&before=NDMyNzQyODI3OTQw",
    "next": "https://graph.facebook.com/VERSION/PHONE_NUMBER_ID/groups?limit=25&after=MTAxNTExOTQ1MjAwNzI5NDE="
  }
}
```

### Response parameters

| Parameter | Description |
| --- | --- |
| `data[groups]`  *List* | A list of groups, each containing the group id, group subject, and UNIX timestamp for group creation. |
| `paging`  *Object* | A pagination object.  Learn more about [Paginated Results in Graph API here](/docs/graph-api/results/) |

## Update group settings

Use this webhook to update your group's subject, description, and photo.

### Request syntax

`POST /<GROUP_ID>`

### Request body

```
{
  "messaging_product": "whatsapp",
  "subject": "<GROUP_SUBJECT>",
  "profile_picture_file": "<FILE_PATH>",
  "description": "<GROUP_DESCRIPTION>",
}
```

### Request properties

**Note**

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<FILE_PATH>`  *String* | **Optional**  A path to an image file stored in your local directory.  **To upload a file**: Follow the same request structure as the [Upload Media](/docs/whatsapp/cloud-api/reference/media#upload-media) endpoint.  Sample file upload cURL:   ``` curl 'https://graph.facebook.com/v23.0/<GROUP_ID> \ -X POST \ -H 'Authorization: Bearer ...' \ -F 'messaging_product=whatsapp' \ -F 'file=@/media/pictures/square_pic.png' ```   Group profile picture requirement:   * Only support mime type image/jpeg * Maximum size: 5MB * Image should be in square, that is, height = width. * Minimum size: 192 x 192 | `/local/path/file.jpg` |
| `<GROUP_SUBJECT>`  *String* | **Optional**  The new subject for the group.   * Maximum length: 128 characters. * Must not be empty if provided. | `"Watch Enthusiasts"` |
| `<GROUP_DESCRIPTION>`  *String* | **Optional**  The new description for the group.   * Max length: 2048 characters | `"Join our community to discuss the latest timepieces, share watch reviews, and connect with fellow horology enthusiasts."` |

### Webhooks

A `group_settings_update` webhook is triggered.

#### Group settings update succeed

[View the "Group settings update succeed" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-settings-update-succeed).

#### Group settings update partial fail

[View the "Group settings update partial fail" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-settings-update-partial-fail).

#### Group settings update total fail

[View the "Group settings update total fail" sample webhook](/docs/whatsapp/cloud-api/groups/webhooks#group-settings-update-total-fail).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Group management](#group-management)

[Overview](#overview)

[Group management features](#group-management-features)

[Subscribe to groups metadata webhooks](#subscribe-to-groups-metadata-webhooks)

[Create group](#create-group)

[Request syntax](#request-syntax)

[Request body](#request-body)

[Request parameters](#request-parameters)

[Webhooks](#webhooks)

[Groups with join requests](#groups-with-join-requests)

[Get join requests](#get-join-requests)

[Approve join requests](#approve-join-requests)

[Reject join requests](#reject-join-requests)

[Webhook](#webhook)

[Get and reset group invite link](#get-and-reset-group-invite-link)

[Get group invite link](#get-group-invite-link)

[Reset group invite link](#reset-group-invite-link)

[Send group invite link template message](#send-group-invite-link-template-message)

[Request syntax](#request-syntax-2)

[Endpoint parameters](#endpoint-parameters)

[Request body](#request-body-2)

[Webhooks](#webhooks-2)

[Delete group](#delete-group)

[Request Syntax](#request-syntax-3)

[Request properties](#request-properties)

[Webhooks](#webhooks-3)

[Remove group participants](#remove-group-participants)

[Request syntax](#request-syntax-4)

[Request body](#request-body-3)

[Request properties](#request-properties-2)

[Webhooks](#webhooks-4)

[Get group info](#get-group-info)

[Request syntax](#request-syntax-5)

[Endpoint parameters](#endpoint-parameters-2)

[Available fields](#available-fields)

[Sample response](#sample-response)

[Get active groups](#get-active-groups)

[Request syntax](#request-syntax-6)

[Query Parameters](#query-parameters)

[Response Object](#response-object)

[Response parameters](#response-parameters)

[Update group settings](#update-group-settings)

[Request syntax](#request-syntax-7)

[Request body](#request-body-4)

[Request properties](#request-properties-3)

[Webhooks](#webhooks-5)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afj-QEoyVWQRGKdK-bf2eDshDVWtwFxF7Jk-Wl1SWWE8Cg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afin7bLLg_wbZhxru9SIOykEGe9u2M8M4w9fWBchiuAV-g&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afh89l5gzBGEanXtJzs53ttKHxBOzp_SC22BaRQ4Uqy4xg&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2uHyKzvy2HliTWtwIJ2dsv7OdZXDwaHI1ePzGEnHGAJcGbnWGY2kUMuZlj7jnpn60_k0bPmRhf6ySXpQ330_rmjhRDwwoIUNLCg-sMuSAwWl-kpJFc0Az-JAU-VGkd4qvUzsJoW7DyvR4Oyv3q_w)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_AfjEuOb7wy_bGRQJOvt48O0TygTVkJ-K4TWpb_NZhmPqFA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT311QKDDeSX0VshvoiRP4zOirWzgNnfWv99EWcLw06EpgE3Phz8UasHslsNh8kQ3xVV51j2bmDfeEzD5T4JEsofLonYUcSh7fjbyS6E36HCLmlUZdmdIYP9-UXYKVNuNN80sChiOe2JKVNsrY4soQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afj9B2DCivwWptZHHajxNGrrw-hy3ZjykFR3Z-EEkumwRQ&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1vSgD_QB3ivpnt2oyGPfAQKeRIEtwCVmYZWAq0UYF-12x194eP3nNEGpP6tCoBOTmbCwdMoj8E8WQaq-iws3EXuiDWALAOezm3FQvsq0S6iDUBVilAPc6QjWL6rtphouxSaq--kV3G05NVo2iACQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afhi7lCd2ZdklIbMyZGwMmdDvk4bzqZm4XgGtwnV9fWKyw&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3sRLAqD68Gul347VWmh7p_WidIOxrkNqj2Sz8tOjIS8a2poKJY7TMmXx0JSzy-y6UtLUKYg7i4XLWx1o9QYU4RzSNhVi1zYUVJsZmF96dFUBU0fKobu5kUX4h0iy6mMFYNfIPEkL1JTTw1PSXYaQ)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0yIPJEFNuxkB98aH9QWbNMk5VEHBiuTfMuqB1i_c7KqC-TaKGJvORdPZqi74JsAAKvAcOlFk0oT5slCTrMBmgTzZBKC9KA7V4LA7U3VOfsSzhH_Q4HBbL5cO2AC_1wx-V8xIr1nUEiaihWW3Jgpg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1e5I5HDwkn-aP56JUuknPmxzwwV4nZc6rjdWLS7npDKTVFU0xDVxortl-rEkP1jys7HAtNHP155UW1qfzsz0lL23dsqzTKai6xMNWhIFF82-jhoqu-GVMlX30hC80g-wdtjo7cAQPM3jCS5t_Irw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_AfjPzMy2lrCS1cyBJpAm8nxej5Csy9uBqlQ5peqJ1qR4nA&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afix1xPb14eD_BSBDVX-rNDiH2fEAdP-bkIaWrtIItpTMw&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2y7c29BcJamEIXOCGr8lahR5lPJFZoQ2D-YS6c-WvNcvx40HrPrS0SfSnBsfltFFw0esRvcIuN8EFXh1JUGxg_hjWbe5dYIjaQyj-jtsxnaFBq18Icwb_1oUIntrLCyIAo1jwNGGNuIcToDIx3QQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_AfgO346Za_YtH-tdzcP4iGsi_t1Nmpp5e_VzABovs7LUTA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2NB1kOCqLLP_VlPvuCAnmilUvMouAh7V4QyjlR1HLdLz6t7coSYqG-z5MUKf2qUBvvRIcB5XHr3xh79vO9VEzp9Yjuw8OhMO00aSIzMxu225d7jkgUmjyZCwglYovEFhsSB_e-ZGmJaEZ594CZJQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_AfhI0Jpt1SlW9RKDtWTyG0f9tWFNvZFecQ9eRclNWGAOVQ&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2mDHPwuQC8GzPrV5AdU64do3mEbZSs8cyKEQYSfnNGWf8XbkvdCHpDFwgqnG0G9aCo6oCIHjpB7Lc9xFGfMFpH2xQBRUm-ZDtmNu5am_iQm1x0hq1Y0GKihVzQ3X3_A_3k6vdJ8ZcZ9RID4Pe6xU3whit9nvj8A-M)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=NMW2qezRr6puT64loc-UvA&oh=00_Afgt6Z-yktV_dj5ZT49ELAt4LclTPl2QODG6S0lB5wxXRA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1k6AYAMNEFaQdNcOWkj0e7KDlzyLatfu9mZqZoN0JKRvMK2h0wduenw65EZW3lQ1Ji11-7dNueGUki6oy1IscD0PYM2qOgNADQi36H8kG1JnD86SZFg-UhMOffhxq9r6ri5GMVquhYHMRiciCapg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1dH7irVt4LuL8-AQfNASuHLZYN6WHuIze8OOjXP5stv2DulGJ9nwdN6Be1pyBnJwRoquwKBGCm3e6scOYHeRaR1ctmbY5c0BK_6N2KJSp9zQwF4u_CcGKGD-LnoXUpKmhNGc_3mtWXAN6uPfavqg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)