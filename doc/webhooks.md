![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Fwebhooks%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)

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

[Webhooks for Groups API](#webhooks-for-groups-api)

[group\_lifecycle\_update webhooks](#group-lifecycle-update-webhooks)

[Group create succeed](#group-create-succeed)

[Group create fail](#group-create-fail)

[Delete group succeed](#delete-group-succeed)

[Delete group fails](#delete-group-fails)

[group\_participants\_update webhooks](#group-participants-update-webhooks)

[User joined group using invite link succeed](#user-joined-group-using-invite-link-succeed)

[User accepts or cancels join request](#user-accepts-or-cancels-join-request)

[Join request approved](#join-request-approved)

[Group participant remove succeed](#group-participant-remove-succeed)

[Group participant remove with participants partially fails](#group-participant-remove-with-participants-partially-fails)

[Group participant remove fails](#group-participant-remove-fails)

[Group participant leaves webhook](#group-participant-leaves-webhook)

[group\_settings\_update webhooks](#group-settings-update-webhooks)

[Group settings update succeed](#group-settings-update-succeed)

[Group settings update partial fail](#group-settings-update-partial-fail)

[Group settings update total fail](#group-settings-update-total-fail)

[group\_status\_update webhooks](#group-status-update-webhooks)

[Group suspended](#group-suspended)

[Group suspension cleared](#group-suspension-cleared)

[Group Message Status Webhooks](#group-message-status-webhooks)

[Aggregated group sessage status](#aggregated-group-sessage-status)

[Group message delivered](#group-message-delivered)

[Pricing information](#pricing-information)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Webhooks for Groups API

In order to receive webhook notifications for metadata about your groups, please subscribe to the following webhook fields:

* `group_lifecycle_update`
* `group_participants_update`
* `group_settings_update`
* `group_status_update`

## `group_lifecycle_update` webhooks

A `group_lifecycle_update` webhook is triggered when a group is either created or deleted.

### Group create succeed

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "group_id": "GROUP_ID",
                "type": "group_create",
                "request_id": "REQUEST_ID",
                "subject": "test invite link",
                "invite_link": "https://chat.whatsapp.com/LINK_ID"
                "join_approval_mode": "JOIN_APPROVAL_MODE"
              }
            ]
          },
          "field": "group_lifecycle_update"
        }
      ]
    }
  ]
}
```

### Group create fail

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
		      {
                    "timestamp": "TIMESTAMP",
                    "type": "group_create",
                    "subject": "GROUP_SUBJECT",
                    "description": "GROUP_DESCRIPTION",
                    "request_id": "REQUEST_ID",
                    "group_id": "GROUP_ID",
                    "errors": [
                      {
                        "code": "ERROR_CODE",
                        "message": "ERROR_MESSAGE",
                        "title": "ERROR_TITLE",
                        "error_data": {
                          "details": "ERROR_DETAILS"
                        }
                      }
                    ]
		      }
               ]
            },
          "field": "group_lifecycle_update"
        }
      ]
    }
  ]
}
```

### Delete group succeed

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_delete"
                    "request_id": "REQUEST_ID",
                 }
               ]
          },
          "field": "group_lifecycle_update"
        }
      ]
    }
  ]
}
```

### Delete group fails

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_delete",
                    "request_id": "REQUEST_ID",
                    "errors": [
                      {
                        "code": "ERROR_CODE",
                        "message": "ERROR_MESSAGE",
                        "title": "ERROR_TITLE",
                        "error_data": {
                          "details": "ERROR_DETAILS"
                        }
                      }
                    ]
                 }
               ]
          },
          "field": "group_lifecycle_update"
        }
      ]
    }
  ]
}
```

## `group_participants_update` webhooks

A `group_participants_update` webhook is triggered when a WhatsApp user joins a group with an invite link, requests to join a group, cancels their request, or when one or more join requests are approved.

### User joined group using invite link succeed

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_participants_add",
                    "reason": "invite_link",
                    "added_participants": [
                        {
                          "wa_id": "WHATSAPP_ID",
                        },
                    ]
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

### User accepts or cancels join request

* **For join requests:** `GROUP_REQUEST_TYPE` is set to `group_join_request_created`.
* **For cancel requests:** `GROUP_REQUEST_TYPE` is set to `group_join_request_revoked`.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "group_id": "GROUP_ID",
                "type": "GROUP_REQUEST_TYPE",
                "reason": "REASON_FOR_REQUEST_OUTCOME"
                "join_request_id": "JOIN_REQUEST_ID",
                "wa_id": "WHATSAPP_USER_ID"
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

### Join request approved

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": WEBHOOK_TRIGGER_TIMESTAMP,
                "group_id": "GROUP_ID",
                "type": "group_participants_add",
                "reason": "invite_link",
                "added_participants": [
                  {
                    "input": "WHATSAPP_USER_PHONE_NUMBER",
                    "wa_id": "WHATSAPP_USER_ID"
                  },
                  //Additional added participants here, if approved in bulk.
                ]
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

### Group participant remove succeed

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_participants_remove",
                    "request_id": "REQUEST_ID",
                    "removed_participants": [
                        // User 1 removed successfully
                        {
                          "input": "PHONE_NUMBER or WHATSAPP_ID"
                        },
                        {
                          "input": "PHONE_NUMBER or WHATSAPP_ID"
                        },
                        ...
                    ]
                 }
                 "initiated_by": "business"
              ]
          },
          "field": "group_participants_update"
        }
      ]
    }
  ]
}
```

### Group participant remove with participants partially fails

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_participants_remove",
                    "request_id": "REQUEST_ID",
                    "initiated_by": business,
                    "removed_participants": [
                      // User 1 removed successfully
                      {
                        "input": "PHONE_NUMBER or WHATSAPP_ID"
                      },
                      // Additional users removed successfully
                      ...
                    ],
                    "failed_participants": [
                      // User 2 not removed due to errors
                      {
                        "input": "PHONE_NUMBER or WHATSAPP_ID"
                        "errors": [
                          {
                            "code": "ERROR_CODE",
                            "message": "ERROR_MESSAGE",
                            "title": "ERROR_TITLE",
                            "error_data": {
                              "details": "ERROR_DETAILS"
                            }
                          }
                        ]
                      }
                    ],
                    "errors": [
                      {
                        "code": "ERROR_CODE",
                        "message": "Failed to remove some participants from the group",
                        "title": "Not All Participants Remove Succeeded",
                        "error_data": {
                          "details": "ERROR_DETAILS"
                        }
                      }
                    ]
                 }
                 "initiated_by": "business"
              ]
          },
          "field": "group_participants_update"
        }
      ]
    }
  ]
}
```

### Group participant remove fails

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_participants_remove",
                    "request_id": "REQUEST_ID",
                    "failed_participants": [
                      {
                        "input": "PHONE_NUMBER or WHATSAPP_ID"
                      },
                      {
                        "input": "PHONE_NUMBER or WHATSAPP_ID"
                      },
                      // Additional users failed to be removed
                      ...
                    ],
                    "errors": [
                      {
                        "code": "ERROR_CODE",
                        "message": "ERROR_MESSAGE",
                        "title": "ERROR_TITLE",
                        "error_data": {
                          "details": "ERROR_DETAILS"
                        }
                      }
                    ]
                 }
                 "initiated_by": "business"
              ]
          },
          "field": "group_participants_update"
        }
      ]
    }
  ]
}
```

### Group participant leaves webhook

This webhook is sent when a group participant leaves the group. The `initiated_by` field and only the `wa_id` in the `removed_participants` list will point to the participant who left the group.

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_ACCOUNT_ID",
      "changes": [
        {
          "value": {
              "messaging_product": "whatsapp",
              "metadata": {
                   "display_phone_number": "DISPLAY_PHONE_NUMBER",
                   "phone_number_id": "PHONE_NUMBER_ID",
              },
               "groups": [
                  {
                    "timestamp": "TIMESTAMP",
                    "group_id": "GROUP_ID",
                    "type": "group_participants_remove",
                    "removed_participants": [
                      {
                        "wa_id": "WHATSAPP_ID",
                      }
                    ]
                 }
                 "initiated_by": "participant"
               ]
          },
          "field": "group_participants_update"
        }
      ]
    }
  ]
}
```

## `group_settings_update` webhooks

### Group settings update succeed

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "group_id": "GROUP_ID",
                "type": "group_settings_update",
                "request_id": "REQUEST_ID",
                "profile_picture": {
                  "mime_type": "image/jpeg",
                  "update_successful": true,
                  "sha256": "PHOTO_HASH",
                },
                "group_subject": {
                  "text": "Test Subject",
                  "update_successful": true,
                },
                "group_description": {
                  "text": "Test Description",
                  "update_successful": true,
                }
              }
            ]
          },
          "field": "group_settings_update"
        }
      ]
    }
  ]
}
```

### Group settings update partial fail

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "group_id": "GROUP_ID",
                "type": "group_settings_update",
                "request_id": "REQUEST_ID",
                "profile_picture": {
                  "mime_type": "image/jpeg",
                  "update_successful": true
                  "sha256": "PHOTO_HASH",
                },
                "group_subject": {
                  "text": "Test Subject",
                  "update_successful": false,
                  "errors": [
                    {
                      "code": "ERROR_CODE",
                      "message": "ERROR_MESSAGE",
                      "title": "ERROR_TITLE",
                      "error_data": {
                        "details": "ERROR_DETAILS"
                      }
                    }
                  ]
                },
                "group_description": {
                  "text": "Test Description",
                  "update_successful": false,
                  "errors": [
                    {
                      "code": "ERROR_CODE",
                      "message": "ERROR_MESSAGE",
                      "title": "ERROR_TITLE",
                      "error_data": {
                        "details": "ERROR_DETAILS"
                      }
                    }
                  ]
                },
                "errors": [
                  {
                    "code": "ERROR_CODE",
                    "message": "ERROR_MESSAGE",
                    "title": "ERROR_TITLE",
                    "error_data": {
                      "details": "ERROR_DETAILS"
                    }
                  }
                ]
              }
            ]
          },
          "field": "group_settings_update"
        }
      ]
    }
  ]
}
```

### Group settings update total fail

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "<ID>",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "group_id": "GROUP_ID",
                "request_id": "REQUEST_ID",
                "type": "group_settings_update",
                "profile_picture": {
                  "mime_type": "image/jpeg",
                    "sha256": "PHOTO_HASH",
                  "update_successful": false,
                  "errors": [
                    {
                      "code": "ERROR_CODE",
                      "message": "ERROR_MESSAGE",
                      "title": "ERROR_TITLE",
                      "error_data": {
                        "details": "ERROR_DETAILS"
                      }
                    }
                  ]
                },
                "group_subject": {
                  "text": "Test Subject",
                  "update_successful": false,
                  "errors": [
                    {
                      "code": "ERROR_CODE",
                      "message": "ERROR_MESSAGE",
                      "title": "ERROR_TITLE",
                      "error_data": {
                        "details": "ERROR_DETAILS"
                      }
                    }
                  ]
                },
                "group_description": {
                  "text": "Test Description",
                  "update_successful": false,
                  "errors": [
                    {
                      "code": "ERROR_CODE",
                      "message": "ERROR_MESSAGE",
                      "title": "ERROR_TITLE",
                      "error_data": {
                        "details": "ERROR_DETAILS"
                      }
                    }
                  ]
                },
                "errors": [
                  {
                    "code": "ERROR_CODE",
                    "message": "ERROR_MESSAGE",
                    "title": "ERROR_TITLE",
                    "error_data": {
                      "details": "ERROR_DETAILS"
                    }
                  }
                ]
              }
            ]
          },
          "field": "group_settings_update"
        }
      ]
    }
  ]
}
```

## `group_status_update` webhooks

WhatsApp uses advanced machine learning technology to evaluate group information including group subjects, profile photos, and group descriptions. We also provide simple options for users to make reports to us from any chat.

We may prevent further activity in chat groups to comply with our legal obligations. We may also prevent further chat activity when a group admin is in violation of our [Terms of Service](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fterms-of-service&h=AT3fIdqtpSpz4D7HnnPrn1a_ZoC9NMTiSLDQfrxJjAb01ZwSd_1e5OOcEuzDulEP-R7ga1YfhficDCnAXGqPYadcZFZzMll5C3dSdFqhPV6H-pYfreIqz8DsIfpeQrjjMNqKCp9VYaq5j9r4poeEXg).

You may receive a webhook if a group you manage is suspended. You may also receive a webhook if a suspended group you manage becomes clear of suspensions.

### Group suspended

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "type": "group_suspend",
                "group_id": "GROUP_ID"
              }
            ]
          },
          "field": "group_status_update"
        }
      ]
    }
  ]
}
```

### Group suspension cleared

```

{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "DISPLAY_PHONE_NUMBER",
              "phone_number_id": "PHONE_NUMBER_ID"
            },
            "groups": [
              {
                "timestamp": "TIMESTAMP",
                "type": "group_suspend_cleared",
                "group_id": "GROUP_ID"
              }
            ]
          },
          "field": "group_status_update"
        }
      ]
    }
  ]
}
```

## Group Message Status Webhooks

When you send messages to a group, you will receive a status webhook when the message is sent, delivered, and read.

Instead of sending multiple webhooks for each status update, we will send an aggregated webhook.

This means that if you send a message and are set to receive several `read` or `delivered` statuses, we will send you a single, aggregated webhook that contains multiple `status` objects.

Each webhook you receive is only ever in reference to a single message sent to a single group and a single status type.

### Aggregated group sessage status

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "statuses": [
              {
                "id": "WHATSAPP_MESSAGE_ID",
                "status": "delivered",
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "recipient_id": "GROUP_ID",
                "recipient_type": "group",
                "recipient_participant_id": "GROUP_PARTICIPANT_PHONE_NUMBER",
                "conversation": {
                  "id": "CONVERSATION_ID",
                  "origin": {
                    "type": "CONVERSATION_CATEGORY"
                  },
                  "pricing": {
                    "billable": "IS_BILLABLE",
                    "pricing_model": "PRICING_MODEL",
                    "category": "CONVERSATION_CATEGORY"
                  }
                }
              },
              {
                "id": "WHATSAPP_MESSAGE_ID",
                "status": "delivered",
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "recipient_id": "GROUP_ID",
                "recipient_type": "group",
                "recipient_participant_id": "GROUP_PARTICIPANT_PHONE_NUMBER",
                "conversation": {
                  "id": "CONVERSATION_ID",
                  "origin": {
                    "type": "CONVERSATION_CATEGORY"
                  },
                  "pricing": {
                    "billable": IS_BILLABLE,
                    "pricing_model": "PRICING_MODEL",
                    "category": "CONVERSATION_CATEGORY"
                  }
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

### Group message delivered

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "statuses": [
              {
                "id": "WHATSAPP_MESSAGE_ID",
                "status": "delivered",
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "recipient_id": "GROUP_ID",
                "recipient_type": "group",
                "participant_recipient_id": "GROUP_PARTICIPANT_PHONE_NUMBER",
                "conversation": {
                "id": "CONVERSATION_ID",
                "origin": {
                  "type": "CONVERSATION_CATEGORY"
                }
              },
                "pricing": {
                  "billable": IS_BILLABLE,
                  "pricing_model": "PRICING_MODEL",
                  "category": "CONVERSATION_CATEGORY"
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

### Pricing information

Status messages webhooks that contain pricing information will have:

* `CONVERSATION_CATEGORY` set to one of:
  + `group_marketing` — Indicates a marketing conversation.
  + `group_utility` — Indicates a utility conversation.
  + `group_service` — Indicates a service conversation.
* `IS_BILLABLE` set to one of:
  + `true` — Indicates a billable conversation.
  + `false` — Indicates a non-billable conversation.
* `PRICING_MODEL` set to `PMP`.

[Learn more about Groups API pricing](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing)

#### Group message read (*With pricing*)

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "statuses": [
              {
                "id": "WHATSAPP_MESSAGE_ID",
                "status": "read",
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "recipient_id": "GROUP_ID",
                "recipient_type": "group",
                "participant_recipient_id": "GROUP_PARTICIPANT_PHONE_NUMBER",
                "conversation": {
                "id": "CONVERSATION_ID",
                "origin": {
                  "type": "CONVERSATION_CATEGORY"
                }
              },
                "pricing": {
                  "billable": IS_BILLABLE,
                  "pricing_model": "PRICING_MODEL",
                  "category": "CONVERSATION_CATEGORY"
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

#### Group message read (*Without pricing*)

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "WHATSAPP_BUSINESS_ACCOUNT_ID",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "BUSINESS_DISPLAY_PHONE_NUMBER",
              "phone_number_id": "BUSINESS_PHONE_NUMBER_ID"
            },
            "statuses": [
              {
                "id": "WHATSAPP_MESSAGE_ID",
                "status": "read",
                "timestamp": "WEBHOOK_TRIGGER_TIMESTAMP",
                "recipient_id": "GROUP_ID",
                "recipient_type": "group"
                "participant_recipient_id": "GROUP_PARTICIPANT_PHONE_NUMBER"
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

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Webhooks for Groups API](#webhooks-for-groups-api)

[group\_lifecycle\_update webhooks](#group-lifecycle-update-webhooks)

[Group create succeed](#group-create-succeed)

[Group create fail](#group-create-fail)

[Delete group succeed](#delete-group-succeed)

[Delete group fails](#delete-group-fails)

[group\_participants\_update webhooks](#group-participants-update-webhooks)

[User joined group using invite link succeed](#user-joined-group-using-invite-link-succeed)

[User accepts or cancels join request](#user-accepts-or-cancels-join-request)

[Join request approved](#join-request-approved)

[Group participant remove succeed](#group-participant-remove-succeed)

[Group participant remove with participants partially fails](#group-participant-remove-with-participants-partially-fails)

[Group participant remove fails](#group-participant-remove-fails)

[Group participant leaves webhook](#group-participant-leaves-webhook)

[group\_settings\_update webhooks](#group-settings-update-webhooks)

[Group settings update succeed](#group-settings-update-succeed)

[Group settings update partial fail](#group-settings-update-partial-fail)

[Group settings update total fail](#group-settings-update-total-fail)

[group\_status\_update webhooks](#group-status-update-webhooks)

[Group suspended](#group-suspended)

[Group suspension cleared](#group-suspension-cleared)

[Group Message Status Webhooks](#group-message-status-webhooks)

[Aggregated group sessage status](#aggregated-group-sessage-status)

[Group message delivered](#group-message-delivered)

[Pricing information](#pricing-information)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_Afg3sLfNXCTU1Ox9qOXZnJs_6PdxAwv7DemreGaQVCqFFA&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_Afjxq-FQAx-MFywIGJPSCHfllPmjGmkCZH3jXO85uWUiIA&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfhAuiUF3-J0gbNcsnVlcXvEkuJb7SWX0aZGFmHIVvtUbA&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3Mp6SibYctwHZAJSeBFdAkVrhRthS5XB-xQ0mtLVutHH_kIUiZguZJo_QU_8jvgPpnVYRmZNtAbc95olNmchxlhpeu4DfS-FQ2sL029EfSCj9ugJYW84kJU3o8nLfzh7AVj2pi1Zv3kJV6iHbQFw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfheJB9IwNurCzXqAU349rNT0za5fAzvHyT-xFhRS5evWA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2SW8TiBgzvWvu8EnBYpD4l4EE26sjaVNb4Rgx3KCBVwMSWwRmUQtZw1-2dJQli7z3C6kgVZCFaddihH1gCAHG79Nw17lPazGWALLDJpRqyxAMTd8WZpOOmwhPzasaiIdwZucF7VYXQc7WT-yZXXQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfiDpepa_2WSzgnESj2Hz-S4Uwqjj55tEwqletZgwiNlAA&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1MyeHBFgBttQ2ey0u7G1SHLuiF5H-SDwS1kPlbgcDeUMRsMFuZiiiLb8FFV96yfCWLxaXys-h59rwNb7jVfG4tRqv0lOfV6pngZW3QlYMukg8UmuqKzB31M1FiYW3EP1D-cCw8UAyWPrNZ2xfVYQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfjABNVd0mRElmF0uufhNWQn3SaIOp3-OvK6EJulmo9CYg&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1jE5yKXj6Vb07opEZbPy53Dh1kPnzzYmqQ8IYt6P2RtFR0eW92Mg8I5DgRaJQqzVYUqKeLlEs09ydq-pp04SMGNQgzKdcvdXAU6HR0q-poomoJFPVPmHz0O8refwrVNEqHEyb4FqAKwsO7p1Cyig)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3OBHY7YFYAUZNwpq2kY0PCqzLt9XJ1YQAw2dLmaPP9WPS72uDchUD3grMJ1O9A2aJ2FxqV6TLBTnFdrIz5y6vmbdQ7tDic6nlgORsyYOEw2m4PlXQQrXo0HEzTZh9SD73dJhVT75HrMAPqVjlR8g)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT20t015fjp6q44KoLZ7riyFDtnSETbFM-k31Ehelo0gifP-GfKURPu2AeW2xDUUrAhNShoeqW_jLoG2eTMlnhwZm8RtkNLdv8BJR2-UrY5-NM5EEfnTmjwSfiCifZ3HYsbuPnsk4-OWpehuw57-Jg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfghCkqksDTk2k0hI7VSSWQflLZRjsyaYPiyZ0P0nDGEbg&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_Afh3seEn6ob3rlKjwTh5MG4Oc7SuRSFBaw1vltz1XYSa5w&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT10Xa4k96AjdgC_2DKO7HDEB7KzQRz0i0Hc_fwEpHzsziTOEG21NMxKBPAWWRYOWAmU4rip0nRHJ8jjE3QaBw4tg5J0kYD_Ygc_ONVxjpMqNVXfUauNTaJkZiOJOcgKrUGiI3qs36m6nSs8eSgpmw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfiaJ27sv9rame2BodqlNt4JM-750QPe4wf36H4ULP9XZg&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3cwhLrxZqbG5Q-1Kg6To9RCmt4dUQoC5UILVxrVFdY7JpgRoa8ODI9_EhQiVRBB0Q_WIPp7xO1jPnmS41NN6nJ6vWskvY7Xg4MzDBuXB9v9cZ937NLwDgLccuSXzFVL36xKwa4p8w5WIYpGpnLZQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_Afh7uZu702OlW-a0kxBJ177OcFH7cupSqEMDE_UILbngsw&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2SUII5gK3hy9SrJu-5XmXImRYiBDcfFpiKmrTA5uqHq6BeHrYo37NeH1nzWawVKNzCigIZxqeT7u-Ccux2HH5E4oxPXagg6t5zAGwDyVdQvz-2XwgQHZMonRx_QGyoexmSsBz4mCb_kgfVAEdXeA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=f4cL35AMA4jtVfX3uUOgnA&oh=00_AfhVJ7Gv5KBsflakdIoRokdc2u7bnxayEc1ECQ873yTHkA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0hrTYp5lGreL8qbDwIVylf2qA_mmeelMxiDDB9k5DliNgLeDRKv9d2s_hXm9lXQKf3Ye7_3_o07kBaW1x7rtzMb39IeNVeSGNKHLm2N6t47MP31GCG0XFkDJ8Klqv3zxDQXG3z6CdHRiQNq14mAg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1J00sEZMebm8oh3Zkiu4yWnzhQv2n3ZG_bISoesL1vDYjzpNca3F7-JGdQLHNC6SOjBiIW2CwD956jA0Dvr_x2V-qfmjgtZ2hQCaeQS1Na-A-CpnOuVdyAJb1OF11nnQrpNIrjCXu9OHh6ue5K3w)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)