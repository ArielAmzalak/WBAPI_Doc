![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Fauthentication-best-practices%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Authenticating Users](/docs/whatsapp/business-management-api/authentication-templates/authentication-best-practices)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)

    - [Preenchimento automático com um toque](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates)
    - [Zero-Tap](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates)
    - [Copy Code](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates)
    - [Authenticating Users](/docs/whatsapp/business-management-api/authentication-templates/authentication-best-practices)
    - [Bulk management](/docs/whatsapp/business-management-api/authentication-templates/bulk-management)
    - [Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals)
    - [Template preview](/docs/whatsapp/business-management-api/authentication-templates/template-preview)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)
  + [Utility templates](/docs/whatsapp/business-management-api/message-templates/utility-templates)
  + [Componentes](/docs/whatsapp/business-management-api/message-templates/components)
  + [Management](/docs/whatsapp/business-management-api/message-templates/template-management)
  + [Quality](/docs/whatsapp/business-management-api/message-templates/template-quality)
  + [Per-user marketing limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits)
  + [Pacing](/docs/whatsapp/business-management-api/message-templates/template-pacing)
  + [Pausing](/docs/whatsapp/business-management-api/message-templates/template-pausing)
  + [Review](/docs/whatsapp/business-management-api/template-review)
  + [Languages](/docs/whatsapp/business-management-api/message-templates/supported-languages)
  + [Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library)
  + [Comparison](/docs/whatsapp/business-management-api/message-templates/template-comparison)
  + [Migração de modelo](/docs/whatsapp/business-management-api/message-templates/template-migration)
  + [Groups](/docs/whatsapp/business-management-api/message-templates/template-groups)
  + [Tap target title URL override](/docs/whatsapp/cloud-api/guides/send-message-templates/tap-target-url-title-override)
  + [Time-to-live](/docs/whatsapp/business-management-api/time-to-live)
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
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Best practices for authenticating users via WhatsApp](#best-practices-for-authenticating-users-via-whatsapp)

[Security](#security)

[UX](#ux)

[Collect opt-in](#collect-opt-in)

[Resolving message delivery issues](#resolving-message-delivery-issues)

[Support all apps](#support-all-apps)

[Be ready to receive the code from WhatsApp](#be-ready-to-receive-the-code-from-whatsapp)

[Business accounts and phone numbers](#business-accounts-and-phone-numbers)

[Checking if WhatsApp is installed on Android and iOS](#checking-if-whatsapp-is-installed-on-android-and-ios)

[Checking on Android](#checking-on-android)

[Checking on iOS](#checking-on-ios)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Best practices for authenticating users via WhatsApp

## Security

To register with WhatsApp, users must register using their phone number. During [this sign-up process](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Fcoronavirus%2Fget-started&h=AT0B77LeIle5CEvjSAGvL3hoIO-xeEP3IBAFl4XllkA3w7XXb0tBfp6spW602aTjdDRsmjEMZh8yROBVRmBQEya-xGXASeYZ5c5GFSVFd85y-D109BkFmXbppT6MEZkHrmvdF8AX-ogwmsWM9WFOnw), WhatsApp verifies the user has ownership of this phone number by sending a 6-digit registration code via SMS or phone call.

For many WhatsApp users, their phone number will continue to be the same as the number they have registered with WhatsApp. However, WhatsApp does not enforce ownership of the phone number past initial registration, so there is no guarantee that a phone number and the WhatsApp account tied to that phone number are owned by the same individual. In particular, since phone numbers are recycled by mobile providers, it is possible that if your user currently owns the phone number and does not use WhatsApp, [the previous owner of that phone number still has access to the WhatsApp account tied to that phone number](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F3347469605523961&h=AT028P2DfnqfVGV2E_vysMSY_WP3C9Dx76VQ1l7EUt-kNRKpWA9cV2FYaC0iFYBiHQDvwKFhrUiDN2X5SyO_IRxzI0B80DerGW2beHvp0Y4tgFyeJpPnu2QIfwMlbE38KlPZmOaC5BapDeWu5Nnn4mTefwD9ApXVL0Q).

As such, for sensitive authentication use cases such as account recovery (where a code sent via WhatsApp may be the only authentication factor), a phone number and the WhatsApp account tied to that phone number should not be treated interchangeably. In these cases, some best practices may apply:

1. Explicitly verifying that your user owns the WhatsApp account as you would any other new authentication channel, by sending e.g. an initial OTP and having the user enter it in your app during registration or while they are logged in.
2. Showing an additional challenge to verify the user, on top of the code sent via WhatsApp.

With the first method, you can take advantage of our identity change check systems on [Cloud API](/docs/whatsapp/cloud-api/reference/phone-numbers#identity-change-check) and [On-Premises API](/docs/whatsapp/on-premises/reference/contacts/users-whatsapp-id/identity) to "bind" the WhatsApp account to your user’s account, making sure that future messages only reach the WhatsApp user who received that initial OTP. For example, on Cloud API you should store the identity hash received after sending the initial OTP and (assuming the verification was successful) include it in all subsequent message send requests. This setup would improve security over SMS as message delivery would fail if the phone number is recycled and the new owner registers on WhatsApp (OTP codes will not be accidentally sent to an unintended recipient).

To combat phishing, WhatsApp disables [forwarding](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F887468535575482%2F&h=AT0PUhXF6BNSRerZbg3itynN-edTiEZYC7Nw6uTzZSOrAiBUH9OWmQSPAdFF9OQT3Ru36lTWcstyZfoWL4RK9HvHXlchJ9b_ULqyHBXrnFxk8kZY_Km19EqvfNLacabsqwIJmKhEeatgfQOxC7-AAg) of authentication messages. Messages travel end-to-end encrypted between [Cloud API and the user](/docs/whatsapp/cloud-api/overview/data-privacy-and-security/), or end-to-end encrypted between the manager of the WhatsApp Business API endpoint and the user for [On-Premises API](/docs/whatsapp/on-premises/faq/#faq_188619461766385).

WhatsApp does not support and cannot validate the security practices of [unofficial apps](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1217634902127718&h=AT0Y1s10JX-axX0_My6R_8yp_VQSlh1acq3GrSeL7qsnRWz2ioWKzYRtOpXrk9o3XP35pdmGPx4NLZ2WvH3taewJd7edABK9gP1pZYJbzb8K9v-lKgZwiPm-_8RtV2hEYqhYccRx4irDXxbpcBJY5Q). There is no guarantee that authentication via WhatsApp is secure for users who use these apps.

## UX

### Collect opt-in

Per the [WhatsApp Business Messaging Policy](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fbusiness-policy%2F&h=AT1vXPLWOSOeLWblEWiWnzPzqo10nwicF2XZ1bfc6sZ70PdfiK8TMO7HWqdng8E5YCFSd7pBXMg3urYfN45v9eIPreHh8Unf8DEEUh0xAeElYuPPvnamdXn0qPSwJTUZFXwCZoeMYWd99LC8TKdLrw), you must get opt-in before send you can send a message to a WhatsApp user. A common implementation is to offer users a choice of authentication channels (WhatsApp, e-mail, SMS, etc.), as shown in [our sample application](/docs/whatsapp/business-management-api/authentication-templates#sample-app).

### Resolving message delivery issues

If you are seeing issues where users are selecting WhatsApp but messages end up being undeliverable, it is possible users are accidentally selecting WhatsApp when they in fact are not registered on WhatsApp. To mitigate this, on Android, you can check if WhatsApp is installed and only show WhatsApp in this case.

```
fun isWhatsAppAvailable(context: Context){
   return isAppAvailable(context, "com.whatsapp") ||
          isAppAvailable(context, "com.whatsapp.w4b")
}

fun isAppAvailable(
   context: Context,
   packageName: String
): Boolean {
 val intent = Intent()
 intent.setPackage(packageName)
 intent.action = "com.whatsapp.otp.OTP_REQUESTED"
 val packageManager = context.packageManager
 val listActivities = packageManager.queryBroadcastReceivers(intent, 0)
 return listActivities.isNotEmpty()
}
```

If you are still seeing issues where users are selecting WhatsApp but messages end up being undeliverable, it is also possible that the WhatsApp phone number is not correct. This could be through a user typo error, or that an app is incorrectly assuming the initial registration phone number is the same as the WhatsApp phone number. Users may have a phone number used for SMS and a different phone number used for WhatsApp, in the case where they might have multiple SIM cards for traveling. You should ensure that if WhatsApp is chosen as the authentication channel that the user has a chance to confirm their WhatsApp phone number.

If messages are being delivered but you are seeing lower than expected conversion rates in your authentication flows, consider adopting [our more seamless "one-tap autofill" functionality](/docs/whatsapp/business-management-api/authentication-templates#example-request--one-tap-autofill-), available for Android.

### Support all apps

Your users may be ready to receive messages through WhatsApp or the WhatsApp Business App (or both). If following [our Android client implementation guide](/docs/whatsapp/business-management-api/authentication-templates#client-implementation), your “one-tap autofill” messages should work with any combination of installs, but we recommend testing one-tap across both the consumer app and the business app.

### Be ready to receive the code from WhatsApp

If integrating with "one-tap autofill" functionality, you should be able to handle the code arriving as soon as you have sent the [handshake](/docs/whatsapp/business-management-api/authentication-templates#handshake). WhatsApp will send the code when received regardless of what screen is currently shown on your app. For example, in situations with poor network connectivity, you may receive the code before you are able to load the code entry screen in your app. To handle these cases, one option is to store the received code such that the app can retrieve it when the next screen is fully loaded. This way, the code can be automatically filled by your app as soon as the code is received.

## Business accounts and phone numbers

Every business must have its own WhatsApp Business Account and be sending authentication templates through its own phone number, as opposed to sharing WABAs and phone numbers with separate business entities. Sharing a WABA across multiple businesses is against policy as it conflicts with the [WhatsApp Business Terms of Service](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fbusiness-terms&h=AT3lkV6GZFaKcT4wiv1IpWLm5xCnJUvswo6BSWZD9uIUQuVV2PXHTPR6c1BpNxk9LBwutZOxopCIzMqI6okSFyNP8wod4q2v2mz7EY9bJ9YP2xK_yZS0K8uBuOE-e5Td_nJhmqTcYpRL8WdaC8l_lw) and [WhatsApp Business Messaging Policy](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fbusiness-policy%2F&h=AT0ShSo7pcwCiybqZmhkVKY6xfGyq73mmf-dQ4NoEbICKj9R4lO4aTqw1dYIsID30ZVS7XB9s7e9ApxdRHvomIyNxSc1V78mff6QzFbBT2-so3Fm6pEM-BMqhlxjcve4VI23bBCPPFBpNFhPnPTVUQ), in addition to creating poor user and business experiences on WhatsApp.

## Checking if WhatsApp is installed on Android and iOS

### Checking on Android

You can check WhatsApp installation before offering WhatsApp as an option if you expect both WhatsApp and your app to be on the same device.

First, you need to add the following to your `AndroidManifest.xml` file:

```
<queries>
    <package android:name="com.whatsapp"/>
    <package android:name="com.whatsapp.w4b"/>
</queries>
```

#### Using the SDK (Preferred)

Instantiate the `WhatsAppOtpHandler` object:

```
WhatsAppOtpHandler whatsAppOtpHandler = new WhatsAppOtpHandler();
```

Check if the WhatsApp client is installed by passing the `isWhatsAppInstalled` method as the clause in an `If` statement:

```
If (whatsAppOtpHandler.isWhatsAppInstalled(context)) {
    // ... do something
}
```

#### Without the SDK

```
if (this.isWhatsAppInstalled(context)) {
    // ... do something
}

public boolean isWhatsAppInstalled(final @NonNull Context context){
    return isWhatsAppInstalled(context, "com.whatsapp") ||
           isWhatsAppInstalled(context, "com.whatsapp.w4b");
  }

  public boolean isWhatsAppInstalled(final @NonNull Context context,
      final @NonNull String type){
    final Intent intent = new Intent();
    intent.setPackage(type);
    intent.setAction("com.whatsapp.otp.OTP_REQUESTED");
    PackageManager packageManager = context.getPackageManager();
    List<ResolveInfo> receivers = packageManager.queryBroadcastReceivers(intent, 0);
    return !receivers.isEmpty();
  }
}
```

### Checking on iOS

Use the following code in your iOS application to check if WhatsApp is installed

```
let schemeURL = URL(string: "whatsapp://otp")!
let isWhatsAppInstalled = UIApplication.shared.canOpenURL(schemeURL)
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Best practices for authenticating users via WhatsApp](#best-practices-for-authenticating-users-via-whatsapp)

[Security](#security)

[UX](#ux)

[Collect opt-in](#collect-opt-in)

[Resolving message delivery issues](#resolving-message-delivery-issues)

[Support all apps](#support-all-apps)

[Be ready to receive the code from WhatsApp](#be-ready-to-receive-the-code-from-whatsapp)

[Business accounts and phone numbers](#business-accounts-and-phone-numbers)

[Checking if WhatsApp is installed on Android and iOS](#checking-if-whatsapp-is-installed-on-android-and-ios)

[Checking on Android](#checking-on-android)

[Checking on iOS](#checking-on-ios)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfgpOuxYcbUXlzR5jXR11hQ62lyT9I4tOpA0HfKoiY2zTg&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_Afhmw4M5rkHit3hJGIzunQesJPA5PLvFOv5CiicNStDKPQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfgVbAhHAStX8Oy_3K2Dbb3nTZER_Cv8zxVxJ499vLocBw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0zM8b3FP2vwCrZoYhYWDYUbCHV-S6eOZF6TTJJ_2_zEHORbKcI8QydmtXukNiUo3zoI0h03MBr1OqpncYgkt-Bml55FHnFkhvq9LH3ULFJE_M_wzlW8VyWv0g9k-Xab6q8ZipeLbvKH7srtmvJk9EdaygvMYOTnBo)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfgI7sLZqQ1PtrHKQ61ijquTwehU2-U_zJi5byppF4zOxg&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT03UULdstaIWxWsUt2msGEP6I4V95PaUusfw9YjHcJeqmWY-y0-YFjdWE5Aa5z7u_e4j0hDKd8X4cWYJmOLJmL5i6gs9Iy5gZWj76f6dIuiML9tPJr7j8GE-cZg7pXwDqNm5kei3BKFAe9O4VL-eg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfjqsXfVWUjzp_bZ_QEYLfbjo_HRt1DXo0_yQoYVnUb7wg&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0H7seY7CCPqbFlAZFWxFizSSrSLr4a4Zd3mgQmXcMD5PuDskMfv8YtNUCGi86q9zpVn9m0Ovt6vLtjKnyXZPMfwqd5Lv7Ao3Gh1_sM_km7sC1ZKeCPTeo8SPLJGxsLvYfz_ZUb0wp8e05dpUSuIw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfirhqymGEYVKdFZd5URElIr_Hqy3ac7dev5Ci5FJuIY4A&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2Gm_QVMJaN6QW7mMjC_VASZIhcKG32rtdSY5MLtbZ0CVk8qQgxIrhNAUTKRcgu_ie9xkiWNTx7N9chOSMqU3Z3O5PjQbWFzh6xAgkQ9i7tvCtNGACBn6hWgixA53PFRWadytDjSDsHtYeEtULqqg)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT2YAHMOT_eqtLxv-mmi2cEyN1MJfNP9meH7pFKhqcnelCeZ8CAaQIIj1k1jSeUSk8fgJ2dg3mZxKskKJ3TNlcJBxAI9-HyKmFpUqgcTElkYVYfpyZCmLTK0Axw8_-QMmEW38PzPmdhsvbYjVkaV1w)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT11YTK2ssJysLAMSxMEkfgd7FffNQHP5SQJk7_5kq-xwFJ4ZmAEL_0QRQPreQDo8dweoPgzoRFVl4zv0-iK-t_gH6wQy98Nkedi7YBxLxNV4YBwL1zTXujFBQvAgU3Qa1N-GWpZzVRrmgRcCcL9_g)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfgPWkEQBw4sJKzodkbwSd5VcOU_9sw9DHbAHN5DKTN-wg&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfhFymerDXdOlfHMgyHKAK2ULHqpJ4ksepw7Mbl0_dT2aw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3IJoAzt0Sj7ftmfIZvpqv5d2sn-G4lqj4I2XH-VNjx3DNbyTZHvL0Uk5_EFKArwrYyjjJnL9y7QrPmSg_IYon02ZU7DtYMLSUEnXYfoLzzmzvfqxZEr-d9LBiFIJ-M2OwNiPpu53DkJUClYXxyiQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_Afi228COWZmSGV0Hb3E8RpIaGgyURR1I9D6wfLSwjZV4qQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT35wfF1xDde4mpDfhWLqOxj0dBHxHir-iBQ3tDqu2b0JzKgRZRsdbexZloMmy-5cnMpej3ol4q7Mz7U6scGboFys3q7am48NtrExf7qkn9Qrlu-J9gcB8xS2bBUljOPAg7RGBrGITk64L3y1A6WbA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfjF-whthgd-F22QSp5xrsAh0oWId-iHZ3OWHc9bsoEKzQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3imWgHdu_RfJmbBONOoRU-mk-1TMX4HwAIjwFwpY8bILhAKHmPtlCLaBZZGTNOHxnZNIvhcqxqJLfgHueojazbUdrnhenjw0uV7fRjVhBEVEduTA1ko15MDGaLOSdfANa3_YQq_H2CvXXcfAz5nA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-Eim8lNHGSx7_PbDVU0SRQ&oh=00_AfhBPcUb97uOaGpWwG2ZQXrM9xkWvFau60Fv2qkq5W9sfA&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2Ti0RC9Kb4fZXuMuYY380kvElIGsHwOaaSgLe-gpQ-sO3dBWm0cjm12IWETJCDOEQq52uxzPg7MxkHbYJ9GM0PjAEfllLNvmjc74yy6JCpUXZX44_hMh6t1vYzgahAFXm-HyIC2zMckUysvG-_RQ)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1ZBqcplhCy7_nGC6Hbqa6vEolUWEkhE_av_1voUDZSBGxc3izCZrSVBuHG-Fv6xsL9jukcaBLcphSos7oXSuvYzs9UaqLDsBDEuZNuyrQzNqs7hHSwLw6nei465ivC_lvk0StnQs530deMZYeH8A)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)