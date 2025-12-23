![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fsmb_app_state_sync%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[smb\_app\_state\_sync](/docs/whatsapp/cloud-api/webhooks/reference/smb_app_state_sync)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)

  + [account\_alerts](/docs/whatsapp/cloud-api/webhooks/reference/account_alerts)
  + [account\_review\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_review_update)
  + [account\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_update)
  + [automatic\_events](/docs/whatsapp/cloud-api/webhooks/reference/automatic_events)
  + [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update)
  + [history](/docs/whatsapp/cloud-api/webhooks/reference/history)
  + [message\_template\_components\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_components_update)
  + [message\_template\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_quality_update)
  + [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update)
  + [messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)
  + [partner\_solutions](/docs/whatsapp/cloud-api/webhooks/reference/partner_solutions)
  + [payment\_configuration\_update](/docs/whatsapp/cloud-api/webhooks/reference/payment_configuration_update)
  + [phone\_number\_name\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_name_update)
  + [phone\_number\_quality\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_quality_update)
  + [security](/docs/whatsapp/cloud-api/webhooks/reference/security)
  + [smb\_app\_state\_sync](/docs/whatsapp/cloud-api/webhooks/reference/smb_app_state_sync)
  + [smb\_message\_echoes](/docs/whatsapp/cloud-api/webhooks/reference/smb_message_echoes)
  + [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update)
  + [user\_preferences](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[smb\_app\_state\_sync webhook reference](#smb-app-state-sync-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# `smb_app_state_sync` webhook reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **smb\_app\_state\_sync** webhook.

The **smb\_app\_state\_sync** webhook is used for synchronizing contacts of [WhatsApp Business app users who have been onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) via a solution provider.

## Triggers

* A solution provider [synchronizes the WhatsApp Business app contacts](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users#step-1--initiate-contacts-synchronization) of a business customer with a WhatsApp Business app phone number who the provider has [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider adds a contact to their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT3V4rMGusBQbxes_DTsWxZe0YWW_TCgdv6FkAvGej0Bdb_XRYOsjTm3FJEO81MrR1xq_DGu6TZGjFgIMMAFdQ-XyxQ_mjL9JDNQcjJrDImDXY2rkM5BzXoJGW_gleTDF8FY5p5xpPnpMRPUEqIFTg).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider removes a contact from their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT2rFhs80M2VXq48m0Ce5--UFCVklogzkh_U44jhJuoYgvvE-7sPj2zHsin9bkIYnCdtuabKhq1MEE1JCfFwi0NsbdEr52onnslgLxvjUGHCt2Z39jy1tj4IYg7-vRu5oc-g0jVFQrzhfA4QxkSyCg).
* A business customer with a WhatsApp Business app phone number who has been [onboarded](/docs/whatsapp/embedded-signup/custom-flows/onboarding-business-app-users) by a solution provider edits a contact in their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT0VfY8K1suOLK1fF-uMqqrGH4rzdqcM-jP-El4CeTrUcT3QebrLYaelO0gJ0-iiKVEVGIdJY9oDctqU0Q6PQrYgZiW-rrqdmdMZq8JMUtsOxN7IQ0dv379FeDGvI5swhZNiimD3EdkeQgVqk8UPnQ).

## Syntax

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
                  "phone_number": "<CONTACT_PHONE_NUMBER>"
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

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<ACTION>`  *String* | Indicates if the business customer added, edited, or deleted a contact from their WhatsApp Business app phone address book.  Values can be:  `add` — Indicates the WhatsApp Business app user added or edited a contact.  `remove` — Indicates the WhatsApp Business app user removed a contact. | `add` |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<CONTACT_FIRST_NAME>`  *String* | The contact's first name, as it appears in the business customer's WhatsApp Business app phone address book.  Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo` |
| `<CONTACT_FULL_NAME>`  *String* | The contact's full name, as it appears in the business customer's WhatsApp Business app phone address book.  Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo Morales` |
| `<CONTACT_PHONE_NUMBER>`  *String* | The contact's WhatsApp phone number. | `16505551234` |
| `<WEBHOOK_TRIGGER_TIMESTAMP>`  *Integer* | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `<WHATSAPP_BUSINESS_ACCOUNT_ID>`  *String* | WhatsApp Business Account ID. | `102290129340398` |

## Example

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
            "state_sync": [
              {
                "type": "contact",
                "contact": {
                  "full_name": "Pablo Morales",
                  "first_name": "Pablo",
                  "phone_number": "16505551234"
                },
                "action": "add",
                "metadata": {
                  "timestamp": "1739321024"
                }
              }
            ]
          },
          "field": "smb_app_state_sync"
        }
      ]
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[smb\_app\_state\_sync webhook reference](#smb-app-state-sync-webhook-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZBjQd2ydc2rff3mTXmHVjA&oh=00_AfiWLG7YsaBmvXh-RG6Nze2BkEugGXdvk9sRdEB6I8n3Ow&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZBjQd2ydc2rff3mTXmHVjA&oh=00_Afi1bytdpSpWMB65luutyT-ZrJrpkcO86itwY_2IG_Q5yQ&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZBjQd2ydc2rff3mTXmHVjA&oh=00_Afhc0fZQrQ4-QL3ep_g3QPwR-4j2DYq2GhmUwX_SoYOBcQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZBjQd2ydc2rff3mTXmHVjA&oh=00_AfjpMf1UMRAJiQl3UISncU5OEqrobInIti9jwuv_pN5cVQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZBjQd2ydc2rff3mTXmHVjA&oh=00_AfiOZ95TmH_yyGtnrmt8fMLlNy9UTIBC9nhnllgJEMsZvA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2cr6XNqMMRJZCFIYxpXxfIpl4E4phjTPpN02YTZ1I2bifWvpCJ6nUA1e3OoE70jwzGVTxqcLuXwQ7llyHs2HI-vbv7BAi5yHnxteOaB8Gh4raNxznlyDKePUJIY70sWqxLu3G9hhZgHLL_jJhO8w)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)