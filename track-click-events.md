![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Fguides%2Ftracking-click-events%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)[Tracking click events](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides/tracking-click-events)

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

[Tracking click events](#tracking-click-events)

[Limitations](#limitations)

[Webhooks](#webhooks)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Tracking click events

*Available using Marketing Messages API for WhatsApp (MM API for WhatsApp) and Ads Manager only*

We deliver a webhook payload when users click on the body or call-to-action of your marketing message. You can subscribe to this webhook to capture this data and use it to inform your campaign decisions.

## Limitations

* At the moment, this feature is not available for all users
* Click events are only available for messages sent in the last 7 days

## Webhooks

To receive this webhook, subscribe to the `whatsapp_business_account` webhook topic. The webhook payload is on the `messages` field and is delivered as below:

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
            "user_actions": [
              {
                "action_type": "marketing_messages_link_click",
                "timestamp": "<time_of_click>",
                "marketing_messages_link_click_data": {
                  "click_component": "cta" | "body",
                  "product_id": "sku_id",
                  "click_id": "click_id",
                  "tracking_token": "example_token"
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

| Field Name | Field Type | Field Description |
| --- | --- | --- |
| `action_type` | **Required** String | Name of the action |
| `timestamp` | **Required** Unix timestamp | Timestamp of when the event happened |
| `click_component` | **Optional** Enum | The click action Can either be `cta` or `body` |
| `click_id` | **Optional** String | The unique identifier for the click. Is also appended to the original url when the user visits the url. |
| `tracking_token` | **Optional** String | Internal Meta token for processing and tracking |
| `product_id` | **Optional** String | ID of the product, if it was assigned in Ads Manager or Marketing API. |

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Tracking click events](#tracking-click-events)

[Limitations](#limitations)

[Webhooks](#webhooks)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Hbwl88f-2JR9sagWyQCZpQ&oh=00_AfgcFJALYgRpyVvraueu8sxTkfuBQeVsP0SdOsyjULqn2Q&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Hbwl88f-2JR9sagWyQCZpQ&oh=00_AfgmSKnPbgdUrhBPv29AyeC768VkZwPV-jJUAZXAaSyVjQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Hbwl88f-2JR9sagWyQCZpQ&oh=00_AfjoGCczW0rbNiz04-TdK4ujSoqnU9B4yjKsmHKWxbc0zA&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Hbwl88f-2JR9sagWyQCZpQ&oh=00_AfhHyCnKvdhTkU2xoHy3cF1chO-I6dwlVuFf5fe0sUg8SA&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=Hbwl88f-2JR9sagWyQCZpQ&oh=00_AfikkyVklqY2wJrtqoIYjzq7gx_uhxyoMcfAC2UHIJ-DoA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0_blvgr0R-XjrWRF_iF7fIyAl2bc_3shVCg7gXH68TAfa6nryU-J3WIBaKLOiuDk7ArMfAcZOaqtyIjxpyBgeNP4DxZ6tWzvZdNhNvEsQa6_kV0ldydEZMGDByJLB_nO0-4i40rZhZIAVZ5mPr5g)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)