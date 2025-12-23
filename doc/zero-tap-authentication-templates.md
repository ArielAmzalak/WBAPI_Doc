![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Fzero-tap-authentication-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Zero-Tap](/docs/whatsapp/business-management-api/authentication-templates/zero-tap-authentication-templates)

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

[Zero-tap authentication templates](#zero-tap-authentication-templates)

[Limitations](#limitations)

[Best practices](#best-practices)

[Creating authentication templates](#creating-authentication-templates)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[App signing key hash](#app-signing-key-hash)

[Supported apps](#supported-apps)

[Handshake](#handshake)

[Eligibility Check](#eligibility-check)

[Android notifications](#android-notifications)

[Using the SDK (Beta)](#using-the-sdk--beta-)

[Zero-tap broadcast receiver](#zero-tap-broadcast-receiver)

[Zero-tap receiver class](#zero-tap-receiver-class)

[One-tap autofill button activity (optional)](#one-tap-autofill-button-activity--optional-)

[One-tap autofill button activity class (optional)](#one-tap-autofill-button-activity-class--optional-)

[Initiating the handshake](#initiating-the-handshake)

[Checking if WhatsApp is installed](#checking-if-whatsapp-is-installed)

[Error signals](#error-signals)

[Sending authentication templates](#sending-authentication-templates)

[Request](#request)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response Parameters](#response-parameters)

[Example Request](#example-request-2)

[Example Response](#example-response-2)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Zero-tap authentication templates

Zero-tap authentication templates allow your users to receive one-time passwords or codes via WhatsApp without having to leave your app.

When a user in your app requests a password or code and you deliver it using a zero-tap authentication template, the WhatsApp client simply broadcasts the included password or code and your app can capture it immediately with a broadcast receiver.

From your user's perspective, they request a password or code in your app and it appears in your app automatically. If your app user happens to check the message in the WhatsApp client, they will only see a message displaying the default fixed text: *< code > is your verification code.*

Like one-tap autofill button authentication templates, when the WhatsApp client receives the template message containing the user's password or code, we perform a series of eligibility checks. If the message fails this check and we are unable to broadcast the password or code, the message will display either a one-tap autofill button or a copy code button. For this reason, when you create a zero-tap authentication template, you must include a one-tap autofill and copy code button in your post body payload, even if the user may never see one of these buttons.

Note: The OTP Android SDK is in beta and features a simplified workflow for implementing one-tap and zero-tap authentication templates. You can learn how to use it below.

## Limitations

Zero-tap is only supported on Android. If you send a zero-tap authentication template to a WhatsApp user who is using a non-Android device, the WhatsApp client will display a copy code button instead.

URLs, media, and emojis are not supported.

## Best practices

* Do not make WhatsApp your default password/code delivery method.
* Make it clear to your app users that the password or code will be automatically delivered to your app when they select WhatsApp for delivery.
* Link to our [About security codes that automatically fill on WhatsApp](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F659113242716268%2F&h=AT3Vn7is2URZgBi6yZRe2SUbhd3xMH3H9-kh8zwYjR1EIUunzCZuX47mltBZiqkbgX9moOsNWNhAO4OQ7YAQLzROmidz3gXVGKo1RtFnMXEsFAUTfSAWgT-uP3q4Ht8K6GUWjW7_xstRPZoe931SHw) help center article if your users are worried about auto-delivery of the password or code.
* After the password/code is used in your app, make it clear to your app user that it was received successfully.

Here are some examples that make it clear to an app user that their code will automatically appear in the app.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/391694662_849209140220804_774216131431245181_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=wGhGE4XaUnEQ7kNvwFe0EFP&_nc_oc=AdmNWXX6NBPXsXAWdLU7J94gUHdEAn7r_PcWJIbxVnnfk1Q5AJEFN0jidiIOnlScSFQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfjTN4V-giof6KwJjYzMCmBIYaVICKyrIW-3CXC69VBS7A&oe=6940686A)

## Creating authentication templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates) endpoint to create a zero-tap authentication template.

### Request Syntax

```
curl -X POST "https://graph.facebook.com/v19.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
  {
    "name": "<TEMPLATE_NAME>",
    "language": "<TEMPLATE_LANGUAGE>",
    "category": "authentication",
    "message_send_ttl_seconds": <TIME_TO_LIVE>,
    "components": [
      {
        "type": "body",
        "add_security_recommendation": <SECURITY_RECOMMENDATION>
      },
      {
        "type": "footer",
        "code_expiration_minutes": <CODE_EXPIRATION>
      },
      {
        "type": "buttons",
        "buttons": [
          {
            "type": "otp",
            "otp_type": "zero_tap",
            "text": "<CODY_CODE_BUTTON_TEXT>",
            "autofill_text": "<AUTOFILL_BUTTON_TEXT>",
            "zero_tap_terms_accepted": <TERMS_ACCEPTED>,
            "supported_apps": [
              {
                "package_name": "<PACKAGE_NAME>",
                "signature_hash": "<SIGNATURE_HASH>"
              }
            ]
          }
        ]
      }
    ]
  }'
```

Note that in your template creation request the button type is designated as `otp`, but upon creation the button type will be set to `url`. You can confirm this by performing a GET request on a newly created authentication template and analyzing its components.

### Request parameters

| Placeholder | Description | Example Value |
| --- | --- | --- |
| `<AUTOFILL_BUTTON_TEXT>`  *String* | **Optional.**  One-tap autofill button label text.  If omitted, the autofill text will default to a pre-set value, localized to the template's language. For example, Autofill for English (US).  Maximum 25 characters. | `Autofill` |
| `<COPY_CODE_BUTTON_TEXT>`  *String* | **Optional.**  Copy code button label text.  If the message fails the [eligibility check](#eligibility-check) and displays a copy code button, the button will use this text label.  If omitted, and the message fails the eligibility check and displays a copy code button, the text will default to a pre-set value localized to the template's language. For example, `Copy Code` for English (US).  Maximum 25 characters. | `Copy Code` |
| `<CODE_EXPIRATION>`  *Integer* | **Optional.**  Indicates the number of minutes the password or code is valid.  If included, the code expiration warning and this value will be displayed in the delivered message. If the message fails the [eligibility check](#eligibility-check) and displays a one-tap autofill button, the button will be disabled in the delivered message the indicated number of minutes from when the message was sent.  If omitted, the code expiration warning will not be displayed in the delivered message. If the message fails the eligibility check and displays a one-tap autofill button, the button will be disabled 10 minutes from when the message was sent.  Minimum 1, maximum 90. | `5` |
| `<PACKAGE_NAME>`  *String* | **Required.**  Your Android app's package name.  The string must have at least two segments (one or more dots), and each segment must start with a letter.  All characters must be alphanumeric or an underscore (`a-zA-Z0-9_`).  If using Graph API version 20.0 or older, you can define your app's package name outside of the `supported_apps` array, but this is not recommended. See [Supported Apps](#supported-apps) below.  Maximum 224 characters. | `com.example.luckyshrub` |
| `<SECURITY_RECOMMENDATION>`  *Boolean* | **Optional.**  Set to `true` if you want the template to include the fixed string, For your security, do not share this code. Set to `false` to exclude the string. | `true` |
| `<SIGNATURE_HASH>`  *String* | **Required.**  Your app signing key hash. See [App Signing Key Hash](#app-signing-key-hash) below.  All characters must be either alphanumeric, `+`, `/`, or `=` (`a-zA-Z0-9+/=`).  If using Graph API version 20.0 or older, you can define your app's signature hash outside of the `supported_apps` array, but this is not recommended. See [Supported Apps](#supported-apps) below.  Must be exactly 11 characters. | `K8a/AINcGX7` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.   Maximum 512 characters. | `zero_tap_auth_template` |
| `<TERMS_ACCEPTED>`  *Boolean* | **Required.**  Set to `true` to indicate that you understand that your use of zero-tap authentication is subject to the WhatsApp Business Terms of Service, and that it's your responsibility to ensure your customers expect that the code will be automatically filled in on their behalf when they choose to receive the zero-tap code through WhatsApp.  If set to `false`, the template will **not** be created as you need to accept zero-tap terms before creating zero-tap enabled message templates. | `true` |
| `<TIME_TO_LIVE>`  *Integer* | **Optional.**  Authentication message time-to-live value, in seconds. See [Time-To-Live](/docs/whatsapp/business-management-api/authentication-templates#time-to-live). | `60` |

### Example request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "zero_tap_auth_template",
  "language": "en_US",
  "category": "authentication",
  "message_send_ttl_seconds": 60,
  "components": [
    {
      "type": "body",
      "add_security_recommendation": true
    },
    {
      "type": "footer",
      "code_expiration_minutes": 5
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "otp",
          "otp_type": "zero_tap",
          "text": "Copy Code",
          "autofill_text": "Autofill",
          "zero_tap_terms_accepted": true,
          "supported_apps": [
            {
              "package_name": "com.example.luckyshrub",
              "signature_hash": "K8a/AINcGX7"
            }
          ]
        }
      ]
    }
  ]
}'
```

### Example response

```
{
  "id": "594425479261596",
  "status": "PENDING",
  "category": "AUTHENTICATION"
}
```

## App signing key hash

You must include your app signing key hash in your post body.

To calculate your hash, follow Google's instructions for [computing your app's hash string](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.google.com%2Fidentity%2Fsms-retriever%2Fverify%23computing_your_apps_hash_string&h=AT2Ifcesq9sKWXtN3yu3tB5tW7mqrFgq2KIFmPj3sGzLKlR7P6ne41zDQwggghRd1dUXDD9L2euHY5Nulw8hbFG7Oau9fWb6DMxGLnbIbQY1JVEpSUlSYG9aZEljSlLfqKIdZvmzsilVtiiSDJYLEA).

Alternatively, if you follow Google's instructions and download your app signing key certificate (step 1), you can use your certificate with the [sms\_retriever\_hash\_v9.sh](https://l.facebook.com/l.php?u=https%3A%2F%2Ftinyurl.com%2F43bkdrdt&h=AT03RMkTiJJjtcYYJxjRtra_fUNqV6EYMKS2j6ok0q8zwnOYkyZbXNrkbfQXlUDIhizoMUKFO76O_FKX_thL3qVAEFq500nUJEqAuuEtAQPr-4WHSba3kFLItnPQrVwPJHJthVMfDSxXVEhHK3rBtg) shell script to compute the hash. For example:

```
./sms_retriever_hash_v9.sh --package "com.example.myapplication" --keystore ~/.android/debug.keystore
```

## Supported apps

The `supported_apps` array allows you define pairs of app package names and signing key hashes for up to 5 apps. This can be useful if you have different app builds and want each of them to be able to initiate the handshake:

```
"buttons": [
  {
    "type": "otp",
    ...
    "supported_apps": [
      {
        "package_name": "<PACKAGE_NAME_1>",
        "signature_hash": "<SIGNATURE_HASH_1>"
      },
      {
        "package_name": "<PACKAGE_NAME_2>",
        "signature_hash": "<SIGNATURE_HASH_2>"
      },
      ...
    ]
  }
]
```

Alternatively, if you are using Graph API version 20.0 or older and have only a single app, you can define the app's package name and signing key hash as `buttons` object properties, but this is not recommended as we will stop supporting this method starting with version 21.0:

```
"buttons": [
  {
    "type": "otp",
    ...
    "package_name": "<PACKAGE_NAME>",
    "signature_hash": "<SIGNATURE_HASH>"
  }
]
```

## Handshake

You must signal to the WhatsApp client to expect imminent delivery of a password or code. You can do this by initiating a "handshake".

A handshake is an Android intent and public class that you implement but that the WhatsApp client can start.

When a user in your app requests a password or code to be delivered to their WhatsApp number, first [initiate the handshake](#initiating-the-handshake), then call our API to send the authentication template message. When the WhatsApp client receives the message, it will perform an [eligibility check](#eligibility-check), and if there are no errors, start a broadcast.

If you do not initiate the handshake before sending the message, or the message fails an eligibility check, the broadcast will not be started. Instead, the delivered message will display a one-tap autofill button, if able to do so. If unable to do so, it will display a copy code button.

### Eligibility Check

The WhatsApp client performs the following checks when it receives an authentication template message. If any check fails, it will attempt to display the one-tap autofill button in the message. If unable to do so, it will fall back to a copy code button.

* The handshake was initiated no more than 10 minutes ago (or no more than the number of minutes indicated by the template's `code_expiration_minutes` property, if present).
* The package name in the message (defined in the `package_name` property in the `components` array upon template creation) matches the package name set on the intent. The match is determined through the `getCreatorPackage` method called in the `PendingIntent` object provided by your application. See [One-Tap Autofill Button Class](#one-tap-autofill-button-class--optional-).
* The app signing key hash in the message (defined in the `signature_hash` property in the components array upon template creation) matches your installed app's signing key hash.
* Your app has defined a one-tap autofill button activity and class to receive the password or code.
* Your app has defined a zero-tap broadcast receiver and class to receive the password or code.

### Android notifications

Android notifications indicating receipt of a WhatsApp authentication template message will only appear on the user's Android device if:

* The user is logged into the WhatsApp app or WhatsApp Business app with the phone number (account) that the message was sent to.
* The user is logged into your app.
* Android OS is KitKat (4.4, API 19) or above.
* **Show notifications** is enabled (**Settings** > **Notifications**) in the WhatsApp app or WhatsApp Business app.
* Device level notification is enabled for the WhatsApp app or WhatsApp Business app.
* Prior message threads in the WhatsApp app or WhatsApp Business app between the user and your business are not muted.

### Using the SDK (Beta)

The OTP Android SDK is available in beta. It can be used to perform handshakes, as well as other functions in both one-tap and zero-tap authentication templates.

To access SDK functionality, add the following configuration to your Gradle file:

```
dependencies {
    …
    implementation 'com.whatsapp.otp:whatsapp-otp-android-sdk:0.1.0'
    …
}
```

To your repositories, add `mavenCentral()`:

```
repositories {
    …
    mavenCentral()
    …
}
```

### Zero-tap broadcast receiver

Declare a Receiver and intent filter that can receive the one-time password or code. The intent filter must have the action name com.whatsapp.otp.OTP\_RETRIEVED.

```
<receiver
   android:name=".app.receiver.OtpCodeReceiver"
   android:enabled="true"
   android:exported="true">
   <intent-filter>
       <action android:name="com.whatsapp.otp.OTP_RETRIEVED" />
   </intent-filter>
</receiver>
```

This is the receiver that the WhatsApp app or WhatsApp Business app will start once the authentication template message is received and it passes all [eligibility checks](/docs/whatsapp/business-management-api/authentication-templates#eligibility-checks).

### Zero-tap receiver class

Using the SDK (Preferred)

Define a class that extends `BroadcastReceiver`, then define the `onReceive` method, passing in your context and intent. Instantiate a `WhatsAppOtpIncomingIntentHandler` object, then run the `.processOtpCode()` method which will receive the intent, validate the OTP code, and handle errors.

```
public class OtpCodeReceiver extends BroadcastReceiver {

  @Override
  public void onReceive(Context context, Intent intent) {
    WhatsAppOtpIncomingIntentHandler whatsAppOtpIncomingIntentHandler = new WhatsAppOtpIncomingIntentHandler();
    whatsAppOtpIncomingIntentHandler.processOtpCode(intent,
      // call your function to validate
      (code) -> validateCode(code),
      // call your function to handle errors
      (error, exception) -> handleError(error, exception));
    }
}
```

#### Without the SDK

The broadcast receiver class should look something like this:

```
public class OtpCodeReceiver extends BroadcastReceiver

    @Override
    public void onReceive(Context context, Intent intent) {
       PendingIntent pendingIntent =     intent.getParcelableExtra("_ci_");
       // verify source of the pendingIntent
       String pendingIntentCreatorPackage = pendingIntent.getCreatorPackage();

       String creatorPackage = pendingIntent.getCreatorPackage();
       if ("com.whatsapp".equals(creatorPackage) ||
           "com.whatsapp.w4b".equals(creatorPackage)) {
          // use OTP code
          String otpCode = intent.getStringExtra("code");
          // ...
       }
    }
}
```

### One-tap autofill button activity (optional)

If you want the delivered message to be able to fall back to a one-tap autofill button if the message fails the eligibility check, implement this activity and intent filter in your app to receive the one-time password or code.

The intent filter must have the action name `com.whatsapp.otp.OTP_RETRIEVED`.

```
<activity
   android:name=".ReceiveCodeActivity"
   android:enabled="true"
   android:exported="true"
   android:launchMode="standard">
   <intent-filter>
       <action android:name="com.whatsapp.otp.OTP_RETRIEVED" />
   </intent-filter>
</activity>
```

This is the activity that the WhatsApp client will start if the message fails the eligibility check but is still eligible to display a one-tap autofill button.

### One-tap autofill button activity class (optional)

If you want the message to be able to display a one-tap autofill button if the if fails an eligibility check, define the activity public class that can accept the code once the user taps the button.

```
public class ReceiveCodeActivity extends AppCompatActivity {

   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       Intent intent = getIntent();
       // retrieve PendingIntent from extras bundle
       PendingIntent pendingIntent = intent.getParcelableExtra("_ci_");
       // verify source of the pendingIntent
       String pendingIntentCreatorPackage = pendingIntent.getCreatorPackage();
       // check if creatorPackage is "com.whatsapp" -> WA consumer app Or
       // "com.whatsapp.w4b" -> WA business app
       if ("com.whatsapp".equals(creatorPackage) || "com.whatsapp.w4b".equals(creatorPackage)) {
         // use OTP code
         String otpCode = intent.getStringExtra("code");
       }
   }
}
```

### Initiating the handshake

#### Using the SDK (Preferred)

Performing a handshake can be done by instantiating a `WhatsAppOtpHandler` object and passing in your context to the `.sendOtpIntentToWhatsApp()` method:

```
WhatsAppOtpHandler whatsAppOtpHandler = new WhatsAppOtpHandler();
whatsAppOtpHandler.sendOtpIntentToWhatsApp(context);
```

#### Without the SDK

This example demonstrates one way to initiate a handshake with the WhatsApp app or WhatsApp Business app.

```
public void sendOtpIntentToWhatsApp() {
   // Send OTP_REQUESTED intent to both WA and WA Business App
   sendOtpIntentToWhatsApp("com.whatsapp");
   sendOtpIntentToWhatsApp("com.whatsapp.w4b");
}

private void sendOtpIntentToWhatsApp(String packageName) {

  /**
  * Starting with Build.VERSION_CODES.S, it will be required to explicitly
  * specify the mutability of  PendingIntents on creation with either
  * (@link #FLAG_IMMUTABLE} or FLAG_MUTABLE
  */
  int flags = Build.VERSION.SDK_INT >= Build.VERSION_CODES.S ? FLAG_IMMUTABLE : 0;
  PendingIntent pi = PendingIntent.getActivity(
      getApplicationContext(),
      0,
      new Intent(),
      flags);

  // Send OTP_REQUESTED intent to WhatsApp
  Intent intentToWhatsApp = new Intent();
  intentToWhatsApp.setPackage(packageName);
  intentToWhatsApp.setAction("com.whatsapp.otp.OTP_REQUESTED");
  // WA will use this to verify the identity of the caller app.
  Bundle extras = intentToWhatsApp.getExtras();
  if (extras == null) {
     extras = new Bundle();
  }
  extras.putParcelable("_ci_", pi);
  intentToWhatsApp.putExtras(extras);
  getApplicationContext().sendBroadcast(intentToWhatsApp);
}
```

### Checking if WhatsApp is installed

You can check WhatsApp installation before offering WhatsApp as an option if you expect both WhatsApp and your app to be on the same device.

First, you need to add the following to your `AndroidManifest.xml` file:

```
<queries>
    <package android:name="com.whatsapp"/>
    <package android:name="com.whatsapp.w4b"/>
</queries>
```

Instantiate the `WhatsAppOtpHandler` object:

```
WhatsAppOtpHandler whatsAppOtpHandler = new WhatsAppOtpHandler();
```

Check if the WhatsApp client is installed by passing the `.isWhatsAppInstalled()` method as the clause in an `If` statement:

```
If (whatsAppOtpHandler.isWhatsAppInstalled(context)) {
    // ... do something
}
```

## Error signals

See [Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals) that can help with debugging.

## Sending authentication templates

Note that **you must first initiate a handshake** between your app and the WhatsApp client. See [Handshake](#handshake) above.

### Request

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages) endpoint to send an [authentication template message with a one-time password button](/docs/whatsapp/business-management-api/authentication-templates).

### Request syntax

```
curl -X POST "https://graph.facebook.com/<API_VERSION>/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '
{
    "messaging_product": "whatsapp",
    "recipient_type": "individual",
    "to": "<CUSTOMER_PHONE_NUMBER>",
    "type": "template",
    "template": {
      "name": "<TEMPLATE_NAME>",
      "language": {
        "code": "<TEMPLATE_LANGUAGE_CODE>"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "<ONE-TIME PASSWORD>"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": "0",
          "parameters": [
            {
              "type": "text",
              "text": "<ONE-TIME PASSWORD>"
            }
          ]
        }
      ]
    }
  }'
```

### Request parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<CUSTOMER_PHONE_NUMBER>` | The customer's WhatsApp phone number. | `12015553931` |
| `<ONE-TIME PASSWORD>` | The one-time password or verification code to be delivered to the customer.   Note that this value must appear twice in the payload.   Maximum 15 characters. | `J$FpnYnP` |
| `<TEMPLATE_LANGUAGE_CODE>` | The template's [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>` | The template's name. | `verification_code` |

### Response

Upon success, the API will respond with:

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "<INPUT>",
      "wa_id": "<WA_ID>"
    }
  ],
  "messages": [
    {
      "id": "<ID>"
    }
  ]
}
```

### Response Parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<INPUT>`  *String* | The customer phone number that the message was sent to. This may not match `wa_id`. | `+16315551234` |
| `<WA_ID>`  *String* | WhatsApp ID of the customer who the message was sent to. This may not match `input`. | `+16315551234` |
| `<ID>`  *String* | WhatsApp message ID. You can use the ID listed after "wamid." to track your message status. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI3N0EyQUJDMjFEQzZCQUMzODMA` |

### Example Request

```
curl -L 'https://graph.facebook.com/v24.0/105954558954427/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '{
      "messaging_product": "whatsapp",
      "recipient_type": "individual",
      "to": "12015553931",
      "type": "template",
      "template": {
        "name": "verification_code",
        "language": {
          "code": "en_US"
      },
      "components": [
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "J$FpnYnP"
            }
          ]
        },
        {
          "type": "button",
          "sub_type": "url",
          "index": "0",
          "parameters": [
            {
              "type": "text",
              "text": "J$FpnYnP"
            }
          ]
        }
      ]
    }
  }'
```

### Example Response

```
{
  "messaging_product": "whatsapp",
  "contacts": [
    {
      "input": "12015553931",
      "wa_id": "12015553931"
    }
  ],
  "messages": [
    {
      "id": "wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI4Qzc5QkNGNTc5NTMyMDU5QzEA"
    }
  ]
}
```

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Zero-tap authentication templates](#zero-tap-authentication-templates)

[Limitations](#limitations)

[Best practices](#best-practices)

[Creating authentication templates](#creating-authentication-templates)

[Request Syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[App signing key hash](#app-signing-key-hash)

[Supported apps](#supported-apps)

[Handshake](#handshake)

[Eligibility Check](#eligibility-check)

[Android notifications](#android-notifications)

[Using the SDK (Beta)](#using-the-sdk--beta-)

[Zero-tap broadcast receiver](#zero-tap-broadcast-receiver)

[Zero-tap receiver class](#zero-tap-receiver-class)

[One-tap autofill button activity (optional)](#one-tap-autofill-button-activity--optional-)

[One-tap autofill button activity class (optional)](#one-tap-autofill-button-activity-class--optional-)

[Initiating the handshake](#initiating-the-handshake)

[Checking if WhatsApp is installed](#checking-if-whatsapp-is-installed)

[Error signals](#error-signals)

[Sending authentication templates](#sending-authentication-templates)

[Request](#request)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response Parameters](#response-parameters)

[Example Request](#example-request-2)

[Example Response](#example-response-2)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfhZm6nj0W53QXqJj7PdF5IlNvDAh2jQuedcX7xctokrKg&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfiqrNheWoql4iHiq_8Ue5LrKZG3SUL4Ea0n6TRMw5TaFw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_Afh3n2K98l-M7QEsCPmSOcTYoi7KE1JknK2W_thNXpTuEw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT2Kd89i4e5n5vVpTJ3SbUfOrfoOxOokRqfQwjb0_xwRsaKp38t9A7T6pfNFQfaYhvbaQWpsg-DZbj2G08htXKF3eD4xNPR39-ROHltHpqmAaL55UqKvEvqWm6MRoRFnI6aYRv6LGLhhaB-rX9zLmQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfhIya2xeXLej95Fp1P22Jw6spv1SyWCVHQ3XSJ3SEngJQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2Rm3amI4ggt0rfwcCtuXz6hjFsIWTsvjO55m4ctnPYbqGF2v0Pt20XpS2jEj4hODM0bPudsPTZovAyTFx3_Fqn1yO7cyr3KMbHLZQpZuCWgM2oJFxr4HAHIOiCKHNN8FjgDhmRmWnnHRxOUXh4mw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfgP6jxQeWgslumlqTAXVBfwHCJPMBCPW0GbjoEm0vfLVA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2IByr1wjn-5S8nT9_-n0EGbUT_ozgkZyagKAjCdP_tJSzighedA2BrevqIhT1lPyhHCkc0IfIxT6aCOATQphUwI1pKCbhk-YVDsFGuuwdxQ1cEAw4Rrno5Ow4UuUO6Gb0SFi5D8JQCmVAabZp1Dg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_Afhzo6MU4hHD0p-0JwaOwuhK--POpMDZiMjufPVLa89iew&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2298pJlDk81wMwWCe7nR6i7pFx9zcHJNpD3i40xatSB9GUVjHJ1_30yhJK4rdCDkt-eIHByHjTEgGQG2QfDDTld7q-yd72oPRFF5AC6h7Yimh2GWy7Bn-rao0SpTzq-J3VR9wnIq-hlTm74XI5QA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0h4PBDF_IaDVUuiVznfjRAIX9Iw8zsebqd8A_xUR8OR7wcDCyoBma_G4xSckEILhiQ5KtSorGmB2GwH7VEeqRyEI8h1hxy_oaaOnKAT0I0DITKg0hXAh5T--dRRcrIJNX2V-ErHoCWW4bTwGrp3Q)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2PMDdTUVfhL9aob23UG2O4jzXZnAE228mu7wKWLyhaRYBm3NJPsafkJYVimcIthP0fde8ZQ2qhp1DvHFs58XAPbYrabZpoykCC8NYbVsGCzuANbGpX6HOugyvvRhoqwtLhsUMJcWiHRlqldc2r3w)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfhZcKSy-2Bs9beBfPQ6sGnFyT9cDxikH7LgKtDvkhGttA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfjtqUHxaro0O8m9bUxlKVn_CHHTFs9hdHwIljyK3mOT1Q&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3_tSQinDmi1cL6uXeHlOdizc5BVf9cAdVTcCDOGZLGwDQwIV16HWWG8-OYaBsH4-Eqypznv3WQUOcBWMTaXh51tElOZ-UFh7Wq7W6JqPtZqEcwkhzvfcI0fhhF0is7pSsy7zOtZPh9D7a5jR84gA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfgDUeo71xwt5jvGeO5PJQKD2_r_5GC-zhuvI6s5h-tUYA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2XNs6oj3SFf7sRG6nq0kpx__5Bx9Rxlp61YMWjMhnvwFrgT2UkTVayInKYoFDabw4PgMxa1O58yuRo2fg_MpUNSziH-onXh6J23EgQvTodLT2sW1HNsg5II7yt3S2r9CeQMaOctEa7RN5-JNQ9dA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_Afg8L__DPzr4K9JL5KU3K130M7u_P3pZZvbqpJcRWsUBrQ&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0g0x5qnhyZSsj8aLLSCArllJafB0el7ghDVRb5eg_RUlGrkk29zjUIX5UejfG15ekrCfd0Ne-U9gt5Tiiw3c4Y6vWtd8cw72lmep4jyQ5bY8EtSoBmjZwWs5UIlr8mRW_7y4qARfRIRrbmWTHIEg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=TxFm8-305-tPZfUdlxvL-A&oh=00_AfgRY1dEYnzK8eKqeIC__Zb-ZO8d6KJfia_FInnDuaJq5w&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0VVNL-jCoQe1nPAc7vbOXkE9JsqILPyo-UqSqrq666NSRpXCnAkuQpKCJaOYbZMQ_nDcfyZkBKZ-W1pg6vjTrY6UutmIyM49a_JMqQ0tupOzAgGlwPVRd5KcTO5u0t5P0XGlPzCA5aVRakIiprwg)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1-dxiS_Sl1NLOXk0m92Vtj3wLZXSIbR2MVSfGW_2bp1kQymur4hvoqCGdrDaqSShOEbbowR_5EI04NjyClO0d41pdJ2VL2JpRrrt1A-Vzhmt_2tdLc6NmzF4eiAdvKVAXU5-XA6OD8x_o0F8kxhw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)