![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Foverview%2Ftrack-waba-policy-violations%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)[Rastrear violações de política da WABA](/docs/whatsapp/overview/track-waba-policy-violations)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)
* [Preços](/docs/whatsapp/pricing)
* [Limites de mensagens](/docs/whatsapp/messaging-limits)
* [Webhooks](/docs/whatsapp/webhooks)
* [Parceiros de soluções](/docs/whatsapp/solution-providers)
* [Cadastro Incorporado](/docs/whatsapp/embedded-signup)
* [Prévias de links](/docs/whatsapp/link-previews)
* [Monitoramento da política](/docs/whatsapp/overview/policy-enforcement)

  + [Violações](/docs/whatsapp/overview/policy-enforcement/violations)
  + [Rastrear violações de política da WABA](/docs/whatsapp/overview/track-waba-policy-violations)
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[Use Webhooks to Track WABA Policy Violations](#use-webhooks-to-track-waba-policy-violations)

[Before You Start](#before-you-start)

[Step 1: Set up Endpoint and Configure Webhooks](#step-1--set-up-endpoint-and-configure-webhooks)

[Step 2: Subscribe Your App to your WABA](#step-2--subscribe-your-app-to-your-waba)

[Step 3: Signup for Account Updates](#step-3--signup-for-account-updates)

[Step 4: Track WABA Restrictions](#step-4--track-waba-restrictions)

[Voltar para Português (Brasil)](/docs/whatsapp/overview/track-waba-policy-violations/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 3 de nov
Atualização em Português (Brasil): 8 de mar de 2024

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[WhatsApp Business Platform](/docs/whatsapp)

# Use Webhooks to Track WABA Policy Violations

Businesses can integrate with webhooks to get real-time notifications about changes to a WhatsApp Business Account (WABA), including when a business has [violated a WhatsApp policy](/docs/whatsapp/overview/policy-enforcement). This guide teaches you how to set up your webhooks to receive those notifications so businesses can quickly adjust behavior to avoid additional warnings and/or enforcement actions.

## Before You Start

To complete this guide you need to [register as a Meta Developer](/docs/development/register/). Once you are registered, you need to set up a [Business Manager account](https://www.facebook.com/business/help/1710077379203657) and a [Meta for Developers](/docs/development/create-an-app) App.

When creating your Meta app, make sure you select the ["Business" type](/docs/development/create-an-app/app-dashboard/app-types#business) and [link your new app with the Business Manager](https://www.facebook.com/business/help/2199735813629697).

Once you have created the app, add WhatsApp as a product to your application. To do that:

* Go to [developers.facebook.com/apps](https://developers.facebook.com/apps) and click the app. After the click, you will be redirected to the app dashboard for your app.
* On the dashboard, find **Products** on the left side panel and click **Add Product**. After the click, you will see a list of products that can be added to an app.
* Find **WhatsApp** and click **Set Up**.

Additionally, make sure your app has completed [App Review](docs/app-review) and requested the `whatsapp_business_management` permission.

## Step 1: Set up Endpoint and Configure Webhooks

Follow our [Webhooks Getting Started](/docs/graph-api/webhooks/getting-started) guide to create your endpoint and configure your Webhooks.

## Step 2: Subscribe Your App to your WABA

You need to subscribe your app to Webhook notifications for the WhatsApp Business Account. You can subscribe in two different ways:

* [Using API Calls](/docs/graph-api/webhooks/getting-started/webhooks-for-whatsapp#create-a-subscription)
* [Using Graph API Explorer](/docs/graph-api/webhooks/getting-started/webhooks-for-whatsapp#explorer)

## Step 3: Signup for Account Updates

Now that your app has signed up to receive webhooks related to your WABA, you can refine which types of updates you want to receive. To track a WABA’s status, you need to select the account\_update option. This way, you will be notified when a WABA has violated WhatsApp policies.

To select this option, go to your App Dashboard and find the **Settings** option. You will see a Webhooks section with all the information you provided in the previous steps. Find **Webhook fields**, and click **Manage**. A dialog box will appear with all the fields you can subscribe to. Click Subscribe for account\_update.

Now, every time your WABA has violated a policy, you will get a notification looking like this:

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "1099927220743518",  //WhatsApp Business Account ID
      "time": 1604703058,
      "changes": [
        {
          "field": "account_update",
          "value": {
            "phone_number": "16505551111",
            "event": "ACCOUNT_VIOLATION",
            "violation_info": {
            	"violation_type": "ALCOHOL",
            }
          }
        }
      ]
    }
  ]
}

```

[Learn more about all policy violations.](/docs/whatsapp/overview/policy-enforcement/violations)

## Step 4: Track WABA Restrictions

You should keep an eye on your webhooks to check if your WABA has been restricted due to policy violations. If a restriction has been imposed, you get a webhook that includes the `restriction_info` field, inside the value object. The `restriction_info` field lists all restrictions imposed on your account and when those restrictions expire.

Your WABA may receive one or more restrictions due to policy violations. In the following example, the webhook reports that a WABA has been restricted from adding new phone numbers:

```
{
  "field": "account_update",
  "value": {
    "phone_number": "16505551111",
    "event": "ACCOUNT_RESTRICTION",
    "restriction_info": [
      {
        "restriction_type": "RESTRICTION_ON_ADD_PHONE_NUMBER_ACTION",
        "expiration": 1604703058
      },
    ]
  }
}
```

Here, you see a WABA that is no longer allowed to send [business-initiated messages](/docs/whatsapp/pricing#how-it-works):

```
{
  "field": "account_update",
  "value": {
    "phone_number": "16505551111",
    "event": "ACCOUNT_RESTRICTION",
    "restriction_info": [
      {
        "restriction_type": "RESTRICTED_BIZ_INITIATED_MESSAGING",
        "expiration": 1604703058
      },
    ]
  }
}
```

Finally, you see a WABA that is no longer allowed to respond to [user-initiated messages](/docs/whatsapp/pricing#how-it-works):

```
{
  "field": "account_update",
  "value": {
    "phone_number": "16505551111",
    "event": "ACCOUNT_RESTRICTION",
    "restriction_info": [{
        "restriction_type": "RESTRICTED_CUSTOMER_INITIATED_MESSAGING",
        "expiration": 1604703058
      }
    ]
  }
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Use Webhooks to Track WABA Policy Violations](#use-webhooks-to-track-waba-policy-violations)

[Before You Start](#before-you-start)

[Step 1: Set up Endpoint and Configure Webhooks](#step-1--set-up-endpoint-and-configure-webhooks)

[Step 2: Subscribe Your App to your WABA](#step-2--subscribe-your-app-to-your-waba)

[Step 3: Signup for Account Updates](#step-3--signup-for-account-updates)

[Step 4: Track WABA Restrictions](#step-4--track-waba-restrictions)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=HO_0HxentFzW0gApICh4rg&oh=00_AfjUm-aBY4-4BT1tLhloJBUcmWqmHQN6zJTJpLKHhkXoeg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=HO_0HxentFzW0gApICh4rg&oh=00_AfhaKOhAc0YHfvCpbkWXoCPtoBEpk_1Cy12poElNkqGI7A&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=HO_0HxentFzW0gApICh4rg&oh=00_AfgMF5Zglh8uSs6SI9VRIb8WztQ46Jo4NOLyNsglCwR73g&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=HO_0HxentFzW0gApICh4rg&oh=00_Afi5F1qIlkHmn-CeakLl1f_xTRa3hJukguzFHT6Bhcf6hw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=HO_0HxentFzW0gApICh4rg&oh=00_Afjq_xCGWdditRjxp4a9mz6mTrlc8flTqXafYIKe9nQIuQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1gvyTvgb6hXlXwTwABPc82VrNVId6TIQdX6tjpSTMt0UGbLnykG7Ykge5iehdlpwE-pWPuW0kFphNjWFpHu4qIebcPol_g1US7JSN8vZIxTxcqyoltLSha09qyDCQEoDhc9qy0tR8k5N-fsEW2Ow)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)