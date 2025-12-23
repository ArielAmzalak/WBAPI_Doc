![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fphone-numbers%2Fconversational-components%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)[Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components)

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

  + [Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components)
  + [Throughput](/docs/whatsapp/throughput)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Conversational Components](#conversational-components)

[Limitations](#limitations)

[Configure using WhatsApp Manager (WAM)](#configure-using-whatsapp-manager--wam-)

[Welcome messages](#welcome-messages)

[Webhook payload](#webhook-payload)

[Ice breakers](#ice-breakers)

[Webhook payload](#webhook-payload-2)

[Commands](#commands)

[Webhook payload](#webhook-payload-3)

[Configuring using The API](#configuring-using-the-api)

[Configure Conversational Components Via The API](#configure-conversational-components-via-the-api)

[View the current configuration using the API](#view-the-current-configuration-using-the-api)

[Testing](#testing)

[Voltar para Português (Brasil)](/docs/whatsapp/cloud-api/phone-numbers/conversational-components/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 31 de out
Atualização em Português (Brasil): 6 de out

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Conversational Components

Conversational components are in-chat features that you can enable on business phone numbers. They make it easier for WhatsApp users to interact with your business. You can configure easy-to-use commands, provide pre-written ice breakers that users can tap, and greet first time users with a welcome message.

## Limitations

If a WhatsApp user taps a [universal link](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F425247423114725&h=AT3tqICIfSUaNvt26fTn1fe4NMUjo7AHRnJHHCsiNqRCySLqM_3fl_8D39hIxnp7hT4aDKR8FT-kZqyuWEHNvqHwXRHfBNpP42GIUdXBVdjgU0CzQV8G1Hm8vm7dcyUE4_92cQtTJCNTkYX5JOVyLw) (i.e. **wa.me** link) configured with pre-filled text, the user interfaces for **ice breakers** are automatically dismissed.

## Configure using WhatsApp Manager (WAM)

You can configure all of these features in WhatsApp Manager on the specific numbers you choose:

1. Navigate to the [My Apps dashboard in the Meta for Developers site.](https://developers.facebook.com/apps/)
2. Select your app, then on the left panel select **Configuration** under **WhatsApp**.
3. Under **Phone Numbers** select **Manage Phone Numbers**.
4. On the far right of the phone number you want to configure, select the **Gear Icon** under **Settings**.
5. Select **Automations**.
6. Access and configure Conversational Components.

Solution Partners can configure these features for their customers as well if they have access to their customer's WhatsApp Business Account in WhatsApp Manager.

## Welcome messages

**Welcome messages are currently not functioning as intended.**

Unfortunately, we do not have a timeline for when this feature is expected to be implemented in the future.

All freeform, interactive, and template message types can be sent as welcome messages. Categorized message pricing will apply.

You can be notified by webhook whenever a WhatsApp user opens a chat with you for the first time. This can be useful if you want to reply to these users with a special welcome message of your own design.

Welcome Messages are great for service interactions, such as customer support or account servicing. For example, you can embed a WhatsApp button on your app or website. When users tap the button, they will be redirected to WhatsApp where they will receive a welcome message that provides context on how they can interact with you.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=896659762089885&version=1763312171)

If you enable this feature and a user messages you, the WhatsApp client checks for an existing message thread between the user and your business phone number. If there is none, the client triggers a `messages` webhook with `type` set to `request_welcome`. You can then respond to the user with your own welcome message.

The `request_welcome` webhook triggers a customer service window which allows your business to send free-form messages when responding to customers.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1395533771028563&version=1763312171)

*Carousel template message as a Welcome Message*

### Webhook payload

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
                  "name": "<WHATSAPP_USER_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>"
              }
            ],
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER_ID>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<TIMESTAMP>",
                "type": "request_welcome"  // Indicates first time message from WhatsApp user
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

## Ice breakers

Ice breakers are customizable, tappable text strings that appear in a message thread the first time you chat with a user. For example, "Plan a trip" or "Create a workout plan".

Ice Breakers are great for service interactions, such as customer support or account servicing. For example, you can embed a WhatsApp button on your app or website. When users tap the button, they will be redirected to WhatsApp where they can choose from a set of customizable prompts, showing them how to interact with your services.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=1814698275644248&version=1763312171)

You can configure up to 4 ice breakers on a business phone number. Each ice breaker can have a maximum of 80 characters. Emojis are not supported.

When a user taps an ice breaker, it triggers a standard received message webhook with the ice breaker string assigned to the `body` property in the payload. If the user attempts to message you instead of tapping an ice breaker, the keyboard will appear as an overlay, but it can be dismissed to see the ice breaker menu again.

If a WhatsApp user taps a [universal link](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F425247423114725&h=AT0FTTjYoT-dfY8SWhvu7Nyg9HsmB1QOtcDRLFacMMvsxCdQXHFDOGO2mX78ZaRkJyGhg816Zm66NlazzlnbOu9pMVlS7i7Qxo_iVZQ5oBwGSudh9yqpx2qGHQ08yiZ-ZjL-ODpszjckfecPtKvCnXhKG7EwmvL4BKY) (**wa.me** or **api.whatsapp.com** links) configured with pre-filled text, the user interfaces for **ice breakers** are automatically dismissed.

### Webhook payload

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
                  "name": "<WHATSAPP_USER_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>"
              }
            ],
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER_ID>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<TIMESTAMP>",
                "text": {
                  "body": "Plan a trip"
                },
                "type": "text"
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

## Commands

Commands are text strings that WhatsApp users can see by typing a forward slash in a message thread with your business.

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=910814593784768&version=1763312171)

Commands are composed of the command itself and a hint, which gives the user an idea of what can happen when they use the command. For example, you could define the command:

`/imagine - Create images using a text prompt`

When a WhatsApp user types, */imagine cars racing on Mars*, it would trigger a received message webhook with that exact text string assigned to the `body` property. You could then generate and return an image of cars racing on the planet Mars.

You can define up to 30 commands. Each command has a maximum of 32 characters, and each hint has a maximum of 256 characters. Emojis are not supported.

### Webhook payload

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
                  "name": "<WHATSAPP_USER_NAME>"
                },
                "wa_id": "<WHATSAPP_USER_ID>"
              }
            ],
            "messages": [
              {
                "from": "<WHATSAPP_USER_PHONE_NUMBER_ID>",
                "id": "<WHATSAPP_MESSAGE_ID>",
                "timestamp": "<TIMESTAMP>",
                "text": {
                  "body": "/imagine cars racing on Mars"
                },
                "type": "text"
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

## Configuring using The API

Using the API, you can also configure conversational components and view any configured values.

The Conversational Components API has two endpoints:

`POST </PHONE_NUMBER_ID>/conversational_automation` which is used to configure conversational components on a given phone number.

`GET /<PHONE_NUMBER_ID>/conversational_automation` which returns the current values for the enable\_welcome\_message, commands, and prompts fields on a given phone number.

### Configure Conversational Components Via The API

You can configure Conversational Components on a given phone number by calling the POST endpoint.

#### Request syntax

```
// Enable or disable the Welcome Message for the given phone number ID
POST /<PHONE_NUMBER_ID>/conversational_automation?enable_welcome_message=<ENABLE_DISABLE>

// Configure Commands with names and descriptions
POST /<PHONE_NUMBER_ID>/conversational_automation?commands=<COMMAND_LIST>

// Configure Prompts
POST /<PHONE_NUMBER_ID>/conversational_automation?prompts=<PROMPT>
```

#### Body properties

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<PHONE_NUMBER_ID>`  *Integer* | **Required.**   A phone number ID on a WhatsApp Business account. | `+12784358810` |
| `<ENABLE_DISABLE>`  *Boolean* | **Optional.**   A boolean for enabling or disabling a welcome message on the phone number. | `true` |
| `<COMMAND_LIST>`  *JSON* | **Optional.**   A list of commands to be configured. | ``` "commands": {      "command_name": "generate"      "command_description": "Create a new image",      “command_name”: “rethink”      “command_description”: “Generate new images from existing images”, } ``` |
| `<PROMPTS>`  *List of String* | **Optional.**   The prompt(s) to be configured. | `"prompts": ["Book a flight","plan a vacation"]` |

#### Sample request

```
   curl -X POST \
 'https://graph.facebook.com/v19.0/PHONE_NUMBER_ID/conversational_automation' \
 -H 'Authorization: Bearer ACCESS_TOKEN' \
 -H 'Content-Type: application/json' \
 -d '{
   "enable_welcome_message": true/false,
   "commands": [
     {
       "command_name": "tickets",
       "command_description": "Book flight tickets",
     },
     {
       "command_name": "hotel",
       "command_description": "Book hotel",
     }
   ],
 "prompts": ["Book a flight","plan a vacation"]
}'
```

#### Sample response

```
{
  "success": true
}
```

### View the current configuration using the API

You can view the current configuration of Conversational Components on a given phone number by calling the GET endpoint.

#### Request Syntax

```
GET  /<PHONE_NUMBER_ID>?fields=conversational_automation
```

#### Sample response

```
{
  "conversational_automation": {
    "enable_welcome_message": true
    "prompts": [
      "Find the best hotels in the area",
      "Find deals on rental cars"
    ],
    "commands": [
      {
        "command_name": "tickets",
        "command_description": "Book flight tickets",
      },
      {
        "command_name": "hotel",
        "command_description": "Book hotel",
      }
    ],
  }
  "id": "123456"
}
```

## Testing

To test conversational components once they have been configured, open the WhatsApp client and open a chat with your business phone number.

For welcome messages and ice breakers, if you already have a chat thread going with the business phone number, you must first delete the chat thread:

1. Open the thread in the WhatsApp client.
2. Tap the business phone number's profile
3. Tap **Clear Chat** > **Clear All Messages**.
4. **Delete Chat**.
5. Start a new chat thread with this business.

You can then send a message to the business phone number, which should trigger the `request_welcome` webhook.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Conversational Components](#conversational-components)

[Limitations](#limitations)

[Configure using WhatsApp Manager (WAM)](#configure-using-whatsapp-manager--wam-)

[Welcome messages](#welcome-messages)

[Webhook payload](#webhook-payload)

[Ice breakers](#ice-breakers)

[Webhook payload](#webhook-payload-2)

[Commands](#commands)

[Webhook payload](#webhook-payload-3)

[Configuring using The API](#configuring-using-the-api)

[Configure Conversational Components Via The API](#configure-conversational-components-via-the-api)

[View the current configuration using the API](#view-the-current-configuration-using-the-api)

[Testing](#testing)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfjHVqioWTcSNtCYuHzSpOQ-Y0KLVtQhinSD3oW4SbJucg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfiLLFMOB8SYBEowbLM0AVvUyUVh8zZwwzm6rAyhfIPhUQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfjWU18uMlX1YdYByKEdmWPhMTeNT510MHC-1oQCNjU2tQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Ok3LNJI8h0KXeigoJrjVO5Ibs-8GkHHxqBdZiPeBK9qJmcEW4tzoGmpZJsj6cOxOSPe0y8uAr2_OxUNzvDzGQrMRF1aTUHm-fDrYoe9zY24zYYF-YaazzwTd5at70y2ijScZ3EBSh0DIHJWfgZw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_Afha5sKK5uZx2Lo807AA5C-_DJwvTY_dLCfAPtYXUsqtXA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0aQrcTQzc-X5Qxyb3T8nDwXn3fjhTkasnZL0GOU4WCcn1bebMF_HrkVS1eMDYNiqJ6LMIo66EuVPUSeoyYS6yK6L43sV7_tsMbyklQGyFJGDbX3AFpZ-8Fvagd4KIoQmsUoNxBw831z7cFYD-Tng)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfhPIGDII5CJ4Zs0fMLx_YqMCgOpC6wXwugBv4OMHoj0OQ&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1t5H03eWQD4nsyXWkkUBwQx6BzHMY-C-35Qlu8f3MU9TE0F54SlMZ2w03Tow8ydJusK8sxIrqqPjV40rHIbyZcFz3oYaUPC0QkMVG7VcQ07ygEADJ8Ip91HRVhDUuL2WEbMrBJQlmwOatbiOXJuw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_Afh8n0scKAK6SSLIyUkzHL2MuPHu8sJlW5N-eAe5t0_D8Q&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT27KCUjzAuCKvINqR8FKhvnSKPhPqQ2Mt1hlWxCxIZciGuk0TylopiExduGtf1D9GxSHXvws6H0W0UmKPTNupNihuvVGGTtH6g2v1qriCu4OXuMM881w9fPAqBEhsOFZL7qzs-oaROsvPHP6aqT9w)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT14MrR8bwBmoLM3KIrvDzSae6JsI8ZizBbpwET1U4EhX-fa_7hZ-I8n6OmpZX8cDYXXCJBueKDHwKHF_FOXIMMUp-qzQetvACykefuJ3wMw_7UC1nfZxpy-jygHNL4hz8SGSu-oGuDskApA6TidRg)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT08JPNDWUbu63I_Jpc6izy3_EPqGvgoyzLjr9cO4PfEJ0rpjw1Q785PBtiwVZIjF96bM3eiOt3iP_EO8EX8Uv0rKNgfXIiulDA8ltuUxOGNbT45L_um55kJSPdmjT79JR-n3tIhsXO0aaHL6x-bMg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfjhP5eowCA7vfQUG6vt4tSQKIG0g6LVkAzMCAK9wj6vXA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfgUo9zlIYGRMKlyGkeWfCP14M5a8LecHmQLeQO6Dn_9Ew&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2q0l8m_LkBp5J31CsoTb-7l5L-Zr6jRM9DcfzURGG0oi0rE5ynxkpKwBqZfiOQ5hXANDcjnT9xw9NFjczsB2L4ywplMk6CyM_wXSsyP3KhR6gGwMgGDqwpfbFhT24gPLJkd1Sq2LmO519eRG9VUQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_Afh6JOWJP9TjmfzK6Fs_hyc5_cI5hLXb-vZclu2Y4Y02LQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1kZQ7ZaVUyYfx11wiHuJvgc7FcF66sm_4_R9LKar-uZ4QkA34xJvTE7JQ5miZu3WlJPUPKCaVQvH_UhXGSaqA0t_k4E35JZwpZPId9JjXcI5XTj9pjhYuqMVQR530nfa1xKFS7G4bYNAUrcEniyA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_AfjzSfaYpxwSK1Vu8UEb7ky7C8PdLMY1jb5LfpHlDE6XEw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT29grenUjc-F9wl5VObCC4oG1CXDRxP8-8CZjBFqX03e6qBBHEMUCozr9cQdXi_lsPJu0tC-qebTlK18BOIcAemEf8OPHiyqxi0dF_hKMk5VmHNG8ZDIU-rKa1SdYk3tQgtyS2UiY-eJz7HmQBUug)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=X6C4s90lWpjlmWmopOTTzw&oh=00_Afjffyxa610SsBp3L88vZvaBfitXE3FK21S2Rge9g6n08w&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2frTiz8Vm1hE8cQishD3GqBBQBPIfYyGTVulPl6N2UD73sTI_0Bc0pGby6IfV9Bo_mXjz0D7fNng4J43qc5qup5NcTuhFs6Ugg942OyxGYoIE2l2JCZ3SlcoxAPs4XLDPnazsZSffozR7kq3PawQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2uYYlFnTSGUUR6RVcb1q0qV-JT1xIP5-FWxtUlma3m1uIHc3feYKDiIJhfxD43tAXdIzAmPeKZZlUFr2ZmxNYp9mweCNoz0TwLPLyQuhv1aHtK1-r6y1V4_SyzRiQmP4gDVBNdxA_5sNOQmJlEkQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)