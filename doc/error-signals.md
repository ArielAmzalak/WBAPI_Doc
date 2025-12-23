![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Ferror-signals%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals)

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

[Error Signals](#error-signals)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Error Signals

The OTP Android SDK is in beta and features a simplified workflow for implementing one-tap and zero-tap authentication templates. You can learn how to use it below.

This document describes Android-only error signals that can help you debug [one-tap autofill authentication templates](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates) and [zero-tap authentication templates](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates).

If your message fails the eligibility check, the one-tap autofill button will be replaced with a copy code button. In addition, there may be device or WhatsApp client settings that prevent message notifications. To help with debugging, our apps surface some error information via the `com.whatsapp.OTP_ERROR` intent. In these situations you will receive an error key and message instead of the user's one-time passwords or verification code.

Note that some of these error signals will only surface if you are running WhatsApp in the Android emulator.

| Key | Description |
| --- | --- |
| `ambiguous_delivery_destination`  *Emulator only* | **Ambiguous delivery destination**  There are multiple active OTP requests for the packages specified by this template, and we could not determine which package to deliver the code to.  This can happen when multiple applications specified in the template’s `supported_apps` array have initiated the handshake (sent the `com.whatsapp.otp.OTP_REQUESTED` intent) within the past 10 minutes. |
| `incompatible_os_version` | **Incompatible Android version**   This can happen when you initiate the handshake (send the `com.whatsapp.otp.OTP_REQUESTED` intent) but the device is running a version of Android older than v19. |
| `incorrect_signature_hash`  *Emulator only* | **Incorrect signature hash**   This can happen when you initiate the handshake (send the `com.whatsapp.otp.OTP_REQUESTED` intent) and our app receives an authentication template message that uses a one-tap autofill button, but the package name in the message does not produce the message's signature hash. |
| `missing_handshake_or_disorder` | **Missing handshake / Order of operations**   This can happen when our app receives an authentication template message with a one-tap autofill button but the handshake was not initiated. |
| `otp_request_expired` | **OTP request expired**   This can happen when an authentication template that uses a one-tap autofill button is delivered to the user but more than 10 minutes (or the number of minutes indicated in the template's `code_expiration_minutes` property, if present) have passed since you initiated the handshake. In this situation, we display the copy code button instead. |
| `whatsapp_message_notification_disabled`  *Emulator only* | **Message notification disabled in WA settings**   This can happen when you initiate the handshake (send the `com.whatsapp.otp.OTP_REQUESTED` intent) but the user has disabled notifications in the WhatsApp app or WhatsApp Business app (within our app settings). |
| `whatsapp_notification_disabled`  *Emulator only* | **WA notification disabled in device level**   This can happen when you initiate the handshake (send the `com.whatsapp.otp.OTP_REQUESTED` intent) but the user has disabled app notifications for our apps (device level settings). |

### Integration

The error signals are delivered via broadcasted intent so you must implement [`BroadcastReceiver`](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.android.com%2Freference%2Fandroid%2Fcontent%2FBroadcastReceiver&h=AT1Brz9i_snLWo84fj9fWvg1LqDXfSkNn4maZhTki8GvJSCgUyPlsxgOQmDPboEp5NRzPqupDiWYMuAXN6MdF0Jit0D5m6fN8Gtr8bm62zA2JifyXutmqBPp0Nslw65BWhFKI_uY5NPrnXxPgYRb0g) to listen for error signals.

#### In manifest.xml

```
<receiver
 android:name=".app.otp.OtpErrorReceiver"
 android:enabled="true"
 android:exported="true" >
   <intent-filter>
       <action android:name="com.whatsapp.otp.OTP_ERROR"/>
   </intent-filter>
</receiver>
```

#### Receiver class - Using the SDK (Preferred)

Implement `onReceive` and use a `WhatsAppOtpIncomingIntentHandler` object to process the debug signals.

```
public class OtpErrorReceiver extends BroadcastReceiver {

 @Override
 public void onReceive(Context context, Intent intent) {
     WhatsAppOtpIncomingIntentHandler whatsAppOtpIncomingIntentHandler = new WhatsAppOtpIncomingIntentHandler();
     whatsAppOtpIncomingIntentHandler.processOtpDebugSignals(
                          whatsAppIntent,
                          // your function to handle the signal
                          (debugSignal) -> handleSignal(debugSignal),
                          // your function to handle any error
                          (error, exception) -> handleError(error, exception));
 }
}
```

#### Receiver class - Without the SDK

```
public class OtpErrorReceiver extends BroadcastReceiver {
 public static final String OTP_ERROR_KEY = "error";
 public static final String OTP_ERROR_MESSAGE_KEY = "error_message";

 @Override
 public void onReceive(Context context, Intent intent) {
   try {
     PendingIntent pendingIntent = intent.getParcelableExtra("_ci_");
     if (pendingIntent != null) {
       String packageName = pendingIntent.getCreatorPackage();
       if (packageName.equalsIgnoreCase("com.whatsapp")
           || packageName.equalsIgnoreCase("com.whatsapp.w4b")) {
         String otpErrorKey = intent.getStringExtra(OTP_ERROR_KEY);
         String otpErrorMessage = intent.getStringExtra(OTP_ERROR_MESSAGE_KEY);
         // Handle errors
       }
     }
   } catch (BadParcelableException e) {
     Log.e("OtpErrorReceiver", e.getLocalizedMessage());
   }
 }
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Error Signals](#error-signals)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-nHME2zQruKwbJlMjMLd0Q&oh=00_Afhe2KPCesldIHUy2GwwPOoejgtNmntqVyudsqmicn8Mdg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-nHME2zQruKwbJlMjMLd0Q&oh=00_AfigQzunS2LPV034HxHO-_Cx1Lj0Q3AaZFTrgsT6YoyCeQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-nHME2zQruKwbJlMjMLd0Q&oh=00_Afi8HiuoEKRqT09rva21BBZCxAzG0RAz8Gjnk13ciV3W9A&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-nHME2zQruKwbJlMjMLd0Q&oh=00_Afie7tA5xyCTvZvfG-9t-kT_4sOKls1D5ZTe8r95eBQp3A&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=-nHME2zQruKwbJlMjMLd0Q&oh=00_Afga8GsiiOl6AuXr3jGlH5WydD4RKEKMF3PXwmwwWB90ng&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3Yk4MNI6tl9wfcZ_SsGLqyIXpF7mZbaqb_GvZjk-QZgYExUT6_drNJpkwtvOx4x79uGcawmEILkdZfQ13awUjEZz5O8Azpqs7xzOA9UMm5wDXeV4vIYJmm5acrQ4Ve9DBugOpacqj1TFqFJOMhbQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)