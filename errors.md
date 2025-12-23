![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fwebhooks%2Freference%2Fmessages%2Ferrors%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks reference](/docs/whatsapp/webhooks/reference)[messages](/docs/whatsapp/cloud-api/webhooks/reference/messages)[errors](/docs/whatsapp/cloud-api/webhooks/reference/messages/errors)

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

    - [audio](/docs/whatsapp/cloud-api/webhooks/reference/messages/audio)
    - [button](/docs/whatsapp/cloud-api/webhooks/reference/messages/button)
    - [contacts](/docs/whatsapp/cloud-api/webhooks/reference/messages/contacts)
    - [document](/docs/whatsapp/cloud-api/webhooks/reference/messages/document)
    - [errors](/docs/whatsapp/cloud-api/webhooks/reference/messages/errors)
    - [group](/docs/whatsapp/cloud-api/webhooks/reference/messages/group)
    - [image](/docs/whatsapp/cloud-api/webhooks/reference/messages/image)
    - [interactive](/docs/whatsapp/cloud-api/webhooks/reference/messages/interactive)
    - [location](/docs/whatsapp/cloud-api/webhooks/reference/messages/location)
    - [order](/docs/whatsapp/cloud-api/webhooks/reference/messages/order)
    - [reaction](/docs/whatsapp/cloud-api/webhooks/reference/messages/reaction)
    - [status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)
    - [sticker](/docs/whatsapp/cloud-api/webhooks/reference/messages/sticker)
    - [system](/docs/whatsapp/cloud-api/webhooks/reference/messages/system)
    - [texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)
    - [unsupported](/docs/whatsapp/cloud-api/webhooks/reference/messages/unsupported)
    - [video](/docs/whatsapp/cloud-api/webhooks/reference/messages/video)
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

[Errors messages webhooks reference](#errors-messages-webhooks-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Errors `messages` webhooks reference

This reference describes trigger events and payload contents for the WhatsApp Business Account **messages** webhook for errors messages.

## Triggers

* We are unable to process a request due to a system level problem.
* We are unable to process a request due to an app or account level problem.

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
          },
          "field": "messages"
        }
      ]
    }
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `<BUSINESS_DISPLAY_PHONE_NUMBER>`  *String* | Business display phone number. | `15550783881` |
| `<BUSINESS_PHONE_NUMBER_ID>`  *String* | Business phone number ID. | `106540352242922` |
| `<ERROR_CODE>`  *Integer* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/). | `130429` |
| `<ERROR_CODES_URL>`  *String* | Link to [error code documentation](/docs/whatsapp/cloud-api/support/error-codes/). | `https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/` |
| `<ERROR_DETAILS>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) details. | `Message failed to send because there were too many messages sent from this phone number in a short period of time` |
| `<ERROR_MESSAGE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) message. This value is the same as the `title` property value. | `Rate limit hit` |
| `<ERROR_TITLE>`  *String* | [Error code](/docs/whatsapp/cloud-api/support/error-codes/) title. This value is the same as the `message` property value. | `Rate limit hit` |
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
            "errors": [
              {
                "code": 130429,
                "title": "Rate limit hit",
                "message": "Rate limit hit",
                "error_data": {
                  "details": "Message failed to send because there were too many messages sent from this phone number in a short period of time"
                },
                "href": "https://developers.facebook.com/docs/whatsapp/cloud-api/support/error-codes/"
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

[Errors messages webhooks reference](#errors-messages-webhooks-reference)

[Triggers](#triggers)

[Syntax](#syntax)

[Parameters](#parameters)

[Example](#example)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZaSWheJag9XVYJQ8gdY1bg&oh=00_AfinvugmDQZ0eg6rzBATz95wa6ZfSVqV31sQyNQrneCVSw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZaSWheJag9XVYJQ8gdY1bg&oh=00_Afga-QZyofaghY9driHjAiWQhe0xWB-I_tPiJsgYHFRtkw&oe=692C1438)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZaSWheJag9XVYJQ8gdY1bg&oh=00_Afj429cVspNt_EkCQBflIScgwHhE6a5A0OV4egx668FgSQ&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZaSWheJag9XVYJQ8gdY1bg&oh=00_AfiD5Ywudbm-3itImTGs_Gn5Ha8csTdqU-oFvfRQcpDHOQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=ZaSWheJag9XVYJQ8gdY1bg&oh=00_AfgnCdl8lZJhxKVP_UMEE2tUlXl5ZpHP_exbpja_4_5bqg&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1Z143MeS7P1oQ5XI8ZrbwcmaeHgtJ2s6CXC-1HXaj3wHqPeEs7fN4LtTXay5c3UALSIryNFx0_LSTa_bFi58hS22DeDCOXBHirE2uQIobdfObkeCJgqMugdDPkpL-0FMSojiG1JI5nD-tJboB6BA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)