![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fauthentication-templates%2Fautofill-button-authentication-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)[Preenchimento automático com um toque](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates)

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

[One-tap autofill authentication templates](#one-tap-autofill-authentication-templates)

[Limitations](#limitations)

[Creating authentication templates](#creating-authentication-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

[Example webhook](#example-webhook)

[App signing key hash](#app-signing-key-hash)

[Supported apps](#supported-apps)

[Handshake](#handshake)

[Eligibility check](#eligibility-check)

[Android notifications](#android-notifications)

[Using the SDK (Beta)](#using-the-sdk--beta-)

[Activity](#activity)

[Activity class](#activity-class)

[Initiating the handshake](#initiating-the-handshake)

[Checking if WhatsApp is installed on Android](#checking-if-whatsapp-is-installed-on-android)

[Checking if WhatsApp is installed on iOS](#checking-if-whatsapp-is-installed-on-ios)

[Sending authentication template](#sending-authentication-template)

[Request](#request)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Voltar para Português (Brasil)](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates/?translation)

Este documento foi atualizado.
A tradução para Português (Brasil) não foi concluída ainda.

Atualização em inglês: 4 de nov
Atualização em Português (Brasil): 9 de jan

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[WhatsApp Business Platform](/docs/whatsapp)

# One-tap autofill authentication templates

One-tap autofill authentication templates allow you to send a one-time password or code along with an one-tap autofill button to your users. When a WhatsApp user taps the autofill button, the WhatsApp client triggers an activity which opens your app and delivers it the password or code.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/544891318_1193716362844107_2249981522588832509_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=1-r1qM2St5sQ7kNvwHMtqQw&_nc_oc=Adkqr_J9N4TgJv5LGDmVbqXU9ecJM0Phep91K1j7siMvDheDXWwScrgDvBKl-cXSovQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfiRlz6bBvYWQN8oPLru7b8EcbNDuahjDDMc7PEuzlFjwg&oe=694052C1)

One-tap autofill button authentication templates consist of:

* Preset text: *<VERIFICATION\_CODE> is your verification code.*
* An optional security disclaimer: *For your security, do not share this code.*
* An optional expiration warning (optional): *This code expires in <NUM\_MINUTES> minutes.*
* A one-tap autofill button.

Notes:

* The "I didn't request a code" button is currently in beta and is being rolled out incrementally to business customers.
* The OTP Android SDK is in beta and features a simplified workflow for implementing one-tap and zero-tap authentication templates. You can learn how to use it below.

## Limitations

One-tap autofill buttons are only supported on Android. If you send an authentication template to a WhatsApp user who is using a non-Android device, the WhatsApp client will display a copy code button instead.

URLs, media, and emojis are not supported.

## Creating authentication templates

Use the [WhatsApp Business Account > Message Templates](/docs/graph-api/reference/whats-app-business-account/message_templates) endpoint to create authentication templates.

### Request syntax

```
curl 'https://graph.facebook.com/v24.0/<WHATSAPP_BUSINESS_ACCOUNT_ID>/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d
'{
  "name": "<TEMPLATE_NAME>",
  "language": "<TEMPLATE_LANGUAGE>",
  "category": "authentication",
  "message_send_ttl_seconds": <TIME_T0_LIVE>, // Optional
  "components": [
    {
      "type": "body",
      "add_security_recommendation": <SECURITY_RECOMMENDATION> // Optional
    },
    {
      "type": "footer",
      "code_expiration_minutes": <CODE_EXPIRATION> // Optional
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "otp",
          "otp_type": "one_tap",
          "text": "<COPY_CODE_BUTTON_TEXT>",  // Optional
          "autofill_text": "<AUTOFILL_BUTTON_TEXT>", // Optional
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
| `<AUTOFILL_BUTTON_TEXT>`  *String* | **Optional.**  One-tap autofill button label text.  If omitted, the autofill text will default to a pre-set value, localized to the template's language. For example, `Autofill` for English (US).  Maximum 25 characters. | `Autofill` |
| `<CODE_EXPIRATION>`  *Integer* | **Optional.**  Indicates the number of minutes the password or code is valid.  If included, the code expiration warning and this value will be displayed in the delivered message. The button will be disabled in the delivered message the indicated number of minutes from when the message was sent.  If omitted, the code expiration warning will not be displayed in the delivered message. In addition, the button will be disabled 10 minutes from when the message was sent.  Minimum 1, maximum 90. | `5` |
| `<COPY_CODE_BUTTON_TEXT>`  *String* | **Optional.**  Copy code button label text.  If omitted, the text will default to a pre-set value localized to the template's language. For example, `Copy Code` for English (US).  If included, the authentication template message will display a copy code button with this text if the message fails the [eligibility check](#eligibility-check).  Maximum 25 characters. | `Copy Code` |
| `<PACKAGE_NAME>`  *String* | **Required.**  Your Android app's package name.  The string must have at least two segments (one or more dots), and each segment must start with a letter.  All characters must be alphanumeric or an underscore [`a-zA-Z0-9_`].  If using Graph API version 20.0 or older, you can define your app's package name outside of the `supported_apps` array, but this is not recommended. See [Supported Apps](#supported-apps) below.  Maximum 224 characters. | `com.example.luckyshrub` |
| `<SECURITY_RECOMMENDATION>`  *Boolean* | **Optional.**  Set to `true` if you want the template to include the string, *For your security, do not share this code.* Set to `false` to exclude the string. | `true` |
| `<SIGNATURE_HASH>`  *String* | **Required.**  Your app signing key hash. See [App Signing Key Hash](#app-signing-key-hash) below.  All characters must be either alphanumeric, `+`, `/`, or `=` (`a-zA-Z0-9+/=`).  If using Graph API version 20.0 or older, you can define your app's signature hash outside of the `supported_apps` array, but this is not recommended. See [Supported Apps](#supported-apps) below.  Must be exactly 11 characters. | `K8a/AINcGX7` |
| `<TEMPLATE_LANGUAGE>`  *String* | **Required.**  Template [language and locale code](/docs/whatsapp/business-management-api/message-templates/supported-languages). | `en_US` |
| `<TEMPLATE_NAME>`  *String* | **Required.**  Template name.  Maximum 512 characters. | `verification_code` |
| `<TIME_TO_LIVE>`  *Integer* | **Optional.**  Authentication message time-to-live value, in seconds. See [Customizing Time-To-Live](/docs/whatsapp/business-management-api/message-templates#customizing-time-to-live). | `60` |

### Example request

This example creates a template named "authentication\_code\_autofill\_button" categorized as `authentication` with all optional text strings enabled and a one-tap autofill button.

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "name": "authentication_code_autofill_button",
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
      "code_expiration_minutes": 10
    },
    {
      "type": "buttons",
      "buttons": [
        {
          "type": "otp",
          "otp_type": "one_tap",
          "text": "Copy Code",
          "autofill_text": "Autofill",
          "package_name": "com.example.luckyshrub",
          "signature_hash": "K8a/AINcGX7"
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

## Webhooks

The [button messages webhook](/docs/whatsapp/cloud-api/webhooks/reference/messages/button) is triggered whenever a user taps the "I didn't request a code" button within the message.

### Example webhook

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "320580347795883",
      "changes": [
        {
          "value": {
            "messaging_product": "whatsapp",
            "metadata": {
              "display_phone_number": "12345678",
              "phone_number_id": "1234567890"
            },
            "contacts": [
              {
                "profile": {
                  "name": "John"
                },
                "wa_id": "12345678"
              }
            ],
            "messages": [
              {
                "context": {
                  "from": "12345678",
                  "id": "wamid.HBgLMTIxMTU1NTE0NTYVAgARGBJDMDEyMTFDNTE5NkFCOUU3QTEA"
                },
                "from": "12345678",
                "id": "wamid.HBgLMTIxMTU1NTE0NTYVAgASGCBBQ0I3MjdCNUUzMTE0QjhFQkM4RkQ4MEU3QkE0MUNEMgA=",
                "timestamp": "1753919111",
                "from_logical_id": "131063108133020",
                "type": "button",
                "button": {
                  "payload": "DID_NOT_REQUEST_CODE",
                  "text": "I didn't request a code"
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

## App signing key hash

You must include your app signing key hash in your post body.

To calculate your hash, follow Google's instructions for [computing your app's hash string](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.google.com%2Fidentity%2Fsms-retriever%2Fverify%23computing_your_apps_hash_string&h=AT2qbwtoIPO-cdO9c_H5mEGWIj5aL5k1GfW96u4J6da02OFyqKmTbOWiVuOwMji17L1zQ_y3I1gGbSPloWHOvoP1MkIDehaZNsXJERPtoPeOx6JfOd2rMVQpOz3qEXYMLfBbC78e4FrSZq--G5oFxw).

Alternatively, if you follow Google's instructions and download your app signing key certificate (step 1), you can use your certificate with the [sms\_retriever\_hash\_v9.sh](https://l.facebook.com/l.php?u=https%3A%2F%2Ftinyurl.com%2F43bkdrdt&h=AT0uAofLwZcndsetQ_olI2EsW1ixhyju1fjKagldZQJtLdhKIFLwCqSMnTIM4obtBAkN87QC-joMmRhU-7FcIEPmy6258jf_71QpjmL5JUOjeAmlBkIPK2q2hpdNub63wOL4ukYVJCNLd_iVZ8RrDZJk89J08KgDkxk) shell script to compute the hash. For example:

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

When a user in your app requests a one-time password or verification code and chooses for it to be delivered to their WhatsApp number, first perform the handshake, then call our API to send the authentication template message. When the WhatsApp client receives the message, it will perform an eligibility check, and if there are no errors, start the intent and display the message to the user. Finally, when the user taps the message's one-tap autofill button, we automatically load your app and pass it the password or code.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/335941006_3334832200114460_5878835743521475587_n.png?stp=dst-webp&_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=T6y6WMkv__sQ7kNvwFnoWst&_nc_oc=AdmtnrAbyupsKWTUT7fF8jTuZt3c4r3Pkbj-d0224WbTmSxIIjge8UfIRWY2kBqV7BA&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfhZxstGh9xiMJqK-UZwFpsBUynOpBcqPhMIwOek4nwf5g&oe=6940716C)

If you do not perform a handshake before sending the message, or the message fails an eligibility check, the delivered message will display a copy code button instead of a one-tap button.

### Eligibility check

The WhatsApp client performs the following checks when it receives an authentication template message. If any check fails, the one-tap autofill button will be replaced with a copy code button.

* The handshake was initiated no more than 10 minutes ago (or no more than the number of minutes indicated by the template's `code_expiration_minutes` property, if present).
* The package name in the message (defined in the `package_name` property in the `components` array upon template creation) matches the package name set on the intent. The match is determined through the `getCreatorPackage` method called in the `PendingIntent` object provided by your application.
* None of the other apps that you included in the template’s list of `supported_apps` initiated a handshake in the last 10 minutes (or the number of minutes indicated by the template's `code_expiration_minutes` property, if present).
* The app signing key hash in the message (defined in the `signature_hash` property in the components array upon template creation) matches your installed app's signing key hash.
* The message includes the one-tap autofill button text.
* Your app has defined an activity to receive the password or code.

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

### Activity

Declare an activity and intent filter that can receive the one-time password or code. The intent filter must have the action name `com.whatsapp.otp.OTP_RETRIEVED`.

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

This is the activity that the WhatsApp app or WhatsApp Business app will start once the authentication template message is received and it passes all [eligibility checks](#eligibility-checks).

### Activity class

#### Using the SDK (Preferred)

Define the activity public class and instantiate a `WhatsAppOtpIncomingIntentHandler` object to handle the intent, validate the OTP code, and handle errors.

```
public class ReceiveCodeActivity extends AppCompatActivity {

      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          WhatsAppOtpIncomingIntentHandler incomingIntentHandler = new WhatsAppOtpIncomingIntentHandler();
          incomingIntentHandler.processOtpCode(
                                 intent,
                                 // call your function to validate
                                 (code) -> validateCode(code),
                                 // call your function to handle errors
                                 (error, exception) -> handleError(error, exception));
    }
```

#### Without the SDK

Define the activity public class that can accept the code once it has been passed to your app.

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

Performing a handshake can be done by instantiating the `WhatsAppOtpHandler` object and passing in your context to the `.sendOtpIntentToWhatsApp()` method:

```
WhatsAppOtpHandler whatsAppOtpHandler = new WhatsAppOtpHandler();
whatsAppOtpHandler.sendOtpIntentToWhatsApp(context);
```

#### Without the SDK

This example demonstrates one way to initiate a handshake with the WhatsApp client.

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

### Checking if WhatsApp is installed on Android

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

### Checking if WhatsApp is installed on iOS

Use the following code in your iOS application to check if WhatsApp is installed

```
let schemeURL = URL(string: "whatsapp://otp")!
let isWhatsAppInstalled = UIApplication.shared.canOpenURL(schemeURL)
```

### Error signals

See [Error Signals](/docs/whatsapp/business-management-api/authentication-templates/error-signals) that can help with debugging.

### Sample app

See our [WhatsApp One-Time Password (OTP) Sample App](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-OTP-Sample-App&h=AT0y-0zOFghU_uMLgVNhhhEW2CZJkXRclvJGXkT7GS1slx6N7zblKa81KnDkMUGbi0oah3MNyx6XXT9TgjsqV8WYUqAw6GkfJ2HrCidc9B8b5ZSFeklUgRmiqDxNvbYpSJxO63d1CYLyI97R9_Ml1A) for Android on Github. The sample app demonstrates how to send and receive OTP passwords and codes via the API, how to integrate the one-tap autofill and copy code buttons, how to create a template, and how to spin up a sample server.

## Sending authentication template

This document explains how to send approved [authentication templates with one-time password buttons](/docs/whatsapp/business-management-api/authentication-templates).

Note that **you must first initiate a handshake** between your app and the WhatsApp client. See [Handshake](#handshake) above.

### Request

Use the [WhatsApp Business Phone Number > Messages](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) endpoint to send an [authentication template message with a one-time password button](/docs/whatsapp/business-management-api/authentication-templates).

### Request syntax

```
curl -X POST "https://graph.facebook.com/v23.0/<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>/messages" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
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
          "index": 0,
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

### Response parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `<INPUT>`  *String* | The customer phone number that the message was sent to. This may not match `wa_id`. | `+16315551234` |
| `<WA_ID>`  *String* | WhatsApp ID of the customer who the message was sent to. This may not match `input`. | `+16315551234` |
| `<ID>`  *String* | WhatsApp message ID. You can use the ID listed after "wamid." to track your message status. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgARGBI3N0EyQUJDMjFEQzZCQUMzODMA` |

### Example request

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

### Example response

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

[One-tap autofill authentication templates](#one-tap-autofill-authentication-templates)

[Limitations](#limitations)

[Creating authentication templates](#creating-authentication-templates)

[Request syntax](#request-syntax)

[Request parameters](#request-parameters)

[Example request](#example-request)

[Example response](#example-response)

[Webhooks](#webhooks)

[Example webhook](#example-webhook)

[App signing key hash](#app-signing-key-hash)

[Supported apps](#supported-apps)

[Handshake](#handshake)

[Eligibility check](#eligibility-check)

[Android notifications](#android-notifications)

[Using the SDK (Beta)](#using-the-sdk--beta-)

[Activity](#activity)

[Activity class](#activity-class)

[Initiating the handshake](#initiating-the-handshake)

[Checking if WhatsApp is installed on Android](#checking-if-whatsapp-is-installed-on-android)

[Checking if WhatsApp is installed on iOS](#checking-if-whatsapp-is-installed-on-ios)

[Sending authentication template](#sending-authentication-template)

[Request](#request)

[Request syntax](#request-syntax-2)

[Request parameters](#request-parameters-2)

[Response](#response)

[Response parameters](#response-parameters)

[Example request](#example-request-2)

[Example response](#example-response-2)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AficG9ysewKbVC549_ta0JNJibWO6c2CXk0E9f8F8PyQQg&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfiTssFl9g0YDgN6L3zIAKQ2hkA9sgJMHJPOJbYlLpKrUQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfhZlsbKcQBfqGlO9FxTcXBtzHTBmij6uoyTdlbuzWj8jg&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0SCO-F-kAG0dDG7upE0THbHOkotlR7FIoDkK4BAu7yo6z3JqDSqaO218IE6DLax52mT5xK8xdY_KGtE_kAvTtmgXHKNDPUjd78icLlPCROrPmlfk8lHHUSUnfUrvmS84GEoo6ojYvclCFDjY2ohg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfhrXZ1aOx5r35geB6pKXGDkMcMnykDIQ5Fvi8g_ThvM3w&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2kaIjUkWFQdwKJuvODZqExcwP1lwyxUQmvtx0rys3HmNa5zfBQP23AZXYp_HXPAsBj622EyMsPbwqni6fzXISNFB-IVftabc29zvTfSyPmTIm0eBnNhsAOHPYyjnSOGkiH19ZEH9V3ZGM6Xpgdlp2tT4GJcFs8VOI)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_Afhx75DwTdVQ8c5WL8o2HDAKXAzyprPLU347EbgtFXKQoA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0MXaLfrThSIEmDvj7Soag9_3YWHWWzHOkPuwgPjVrEEckfw3cTk5WE3wn6qgj48qvBkQOn57PMxvHDQV8e4Khog2f79cyF-FfwNAo5aB9P6jhpBl031wINFiJVrpu5oS3ECWZmLMtX1d6zuNgNEw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfiIW-8SkcbVVndb4XIfuRdOZxBZNrtFN_iT0mqnkP_y_w&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT13e1kbzwR7XJe6KAklrWc2x9PfGGh7WzBMUKSbH1erynbOp17FZWJMTvMOmTX9CBdi11ja7TiIhjelm3uloEJ287iEJafKorbZSCIOPUuPEDDETE5HjqbZMNsZum-2sKjgMJJfXhX2lap7nQNOaA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0_6YHOFi06zvWES9eG3tLMfnM8D8IoPHkZrW5iiLTp6veinmG_3ipdT6CVh1Q9zoQm4eNux5Xnf-79u_9TGiJHEtYObyn2gIVUfUHFzzXCG0Orni-hoBJXYs23Fr4XteP1CAxiqxQtPfch5H6xUw)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3fEBIY3aIXWZvXDe6Aa01doZkrnSB-ul7KKYsBCci5hwAsYNTyXXKM4FFO4NlK90eDvD64j03lfbiqJOgULvu3RVJyTtcLsT3gsRzfDRIwpSw7Zo4zKvrhZ9cDZuzeW_QQeLb8S83-_vi6voledA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfiBw03nFjGOjFtowlo26O00KY88PzMu3deKecJ1U-AB2w&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfhvXcdWKEQ_0FMmDxnXobGLrhJ8ocVWXFZ1zC0OZRaPoQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3sIUHD4grC8Ctl51SYODZH8VAjlTWHB9x_xuux4bKsWiOiz9_ffTEXJAyvbwLOmWJgS7NcW2WoFdrsHBLi_kI0XNsE_hH1_q-vQi9YZ0IUuSBx2SV7V5VQ4xX0SOdeNUSpRdeANf1cMbSR-OT0cQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfgnmzxM9TszkybQa4PjgItrSeSttoQVtPHk40lXAGbo2A&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0kZcqaMgN6NgJJABT2Kcj24bcHQ7LxpbAOR55uXQcaipPpIiOrcF9DexP_Fb_80l0ORsyGDeZcARHTHvwfVKRXooTc_yaqssSMxAkQTgVy7JTx8NpNHffoMZyPVpKVMy-_lEhmOozzGrLUX3yKug)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_Afj4d0_x0X6QeE12lojsMcRsKLheAQiHLuq74LalO72NdA&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2XWOf2EO6KM7Indsc99snaWK96SBVBAZYGzwqR60oTHNedJ0ylO5LLkmzZFEXWEWmYDMRNGFFTpmOUkQ7EQpi-aThKxFGsj8sO3Faq3-bfXh6wxyUPL7euaBq2Pd8o4mrlcWtkkTwc675TjffmYg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=t6qaMXUU8Wk72a8uz5qgpw&oh=00_AfiPCqV0JVN0MVlm-V9NxM8x9tyWo67xhVnUIpmXRLT1Jg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT00AxzBSxmcyN4Ngfwu2_xv12SUHVDDbCnBs7rwSf9BlTWDpNVsRW39GeLbE8k7u_YH0AB-7daNVdZp-8sZoMfGvCeazQ6jEw1d10W-zDTR5ycuZZLGKurnFvytc5dJBZyzVRz1WAi2L-WbYel-vA)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3eDzVA3uteqs3vhlpYNUQCdbr29n58lF0yln6bhMj3aJdPLdVB2L6tPsxwhbnQYDoUaMbvNQvy-plfrgh1kwBxigigI8_jbvwp5NieWJdGZu2X-JTmka9fHGky1AWZK3ySlG0E0vD83QswSQBKNA)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)