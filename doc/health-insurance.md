+++
id = "health-insurance"
title = "Use Case Guide: Insurance Quote"
summary = "WhatsApp is making it easier than ever for your customers to understand the options available to them, offering a convenient and immediate solution for getting a quote."
source = "https://developers.facebook.com/docs/whatsapp/health-insurance"
lang = "en"
tags = ["whatsapp-business-platform", "overview", "templates", "security", "testing"]
+++
# Use Case Guide: Insurance Quote

## Intro and Overview

WhatsApp is making it easier than ever for your customers to understand the options available to them, offering a convenient and immediate solution for getting a quote. Creating an experience within a WhatsApp Flow is a quick and easy way for your customers to interact with your offering, without having to exchange multiple messages back and forth.

WhatsApp Flows enables your users to get a quote within the chat thread - providing an experience that is quick and easy for users to complete.

In this guide, we will walk through the entire process to build a Flow for a Get Insurance Quote use case. The templates here can be adapted to suit your use case.

Flows we will build will demonstrate how you can:

* Collect relevant information to help build a personalised quote
* Allow your users to customise their preferred excess amount
* Request appropriate personal information of the people who the insurance will cover
* Allow your users to select the payment frequency
* Review available insurance plans based on the selections and present a description for each
* Publish, Send, and Monitor your Flow

This template can be further adapted to collect additional information from the customer. Weve created the Flow JSON Template for this experience, which you can access
[here](#flows-json-template).

## Getting Started

To follow this guide, ensure you have:

* Completed [prerequisites](/docs/whatsapp/flows/gettingstarted#prerequisites) for building Flows.
* A [Glitch](https://l.facebook.com/l.php?u=https%3A%2F%2Fglitch.com%2Fsignup&h=AT1018Q6r4RWs6YVq21IzULAx9ZidvxUKy54a49X16tmsoFA8DGQm006qRqV6sXyTaKH5eqH3e1Kz31QJcm_84f88YLjprZ5wnSg3q2qFc9ExzSV4sdeGIHCo-x_aiVniVOWTxJbjfbTFHtWKT1MMQ) account

## Flows JSON Template

Flow JSON

{

"version": "7.3",

"data\_api\_version": "3.0",

"routing\_model": {

"APPLICANTS": [

"COVER\_LEVEL"

],

"COVER\_LEVEL": [

"EXCESS"

],

"EXCESS": [

"DETAILS"

],

"DETAILS": [

"YOUR\_HEALTH",

"ADDITIONAL\_APPLICANT"

],

"YOUR\_HEALTH": [

"ADDITIONAL\_APPLICANT",

"POLICY\_SELECTION"

],

"ADDITIONAL\_APPLICANT": [

"POLICY\_SELECTION"

],

"POLICY\_SELECTION": [

"SELECTED\_POLICY"

],

"SELECTED\_POLICY": [

"YOUR\_QUOTE"

],

"YOUR\_QUOTE": [

"SUMMARY"

],

"SUMMARY": []

},

"screens": [

{

"id": "APPLICANTS",

"title": "Applicants",

"data": {

"cover": {

"type": "array",

"items": {

"type": "object",

Enter to Rename, Shift+Enter to Preview

Preview

Run

Configuracoes



Select screen

APPLICANTS



---

Preview Flow

# Applicants

Applicants

# Applicants

Applicants

# Tell us who you'd like to cover?

#

Who would you like to cover?

* #

  Just myself
* #

  Myself & another person
* #

  My family
* #

  Just my children (under 18)

---

# Additional applicant

Additional applicant

#

Number of people you want to add to this policy

#

Continue

#

Gerenciada pela empresa. Saiba maisSaiba mais

### Create new flow from a template

1. In the [Flows section of WhatsApp Manager](https://business.facebook.com/wa/manage/flows/) click on the **Create Flow** button in the top right corner.
2. In the Create page, fill in the details for the pre-approved loan Flow:
   * **Name** - Type *Insurance Quote*, or choose another name you like.
   * **Categories** - Select *Lead generation*.
   * **Template** - Choose *Provide Insurance Quote*. You can further customize the template to suit your use case.
3. Click **Create** to create Flow.

You can preview the Flow on the right of the Builder UI.

The Flow remains in the draft state as you edit it. You can share it with your team for testing purposes only. To share it with a large audience, youll need to publish it. However, you cant edit the Flow once you [publish](#publishing). Since you will still need to add the endpoint URL for this Flow, leave it as a draft for now and proceed to the next step, where youll configure the demo backend endpoint.

**See also**

* [Flow JSON Overview](/docs/whatsapp/flows/reference/flowjson)

## Configure Demo Backend on Glitch

WhatsApp Flows lets you connect to an external endpoint. This endpoint can provide dynamic data for your Flow and control routing. It also receives user-submitted responses from the Flow.

For testing purposes, this template uses Glitch to host the endpoint. Using Glitch is entirely optional, and not required to use Flows. You can [clone the endpoint code from GitHub](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-Flows-Tools%2Ftree%2Fmain%2Fexamples%2Fendpoint%2Fnodejs%2Finsurance-quote&h=AT09A08hVGFlpkaRwYoWBikNVuHgrMVTRSK2sfPQutoIfMIRT8vTbjTlZBsouBmDhV6X0eBQBgYskQID4PdHD5mJsG9oK_5knIPLCybHbFa1DaKSdHZdGzG59Vz5RmjQGRMzif3-6dCQEFttYRvsLQ) and run it in any environment you prefer.

### 1. Remix (fork) Glitch endpoint

Access the [endpoint code in Glitch](https://l.facebook.com/l.php?u=https%3A%2F%2Fglitch.com%2Fedit%2F%23%21%2Fwhatsapp-flows-insurance-quote&h=AT1rHwmx-TP-463zevGp8pGrdOgBlxKhPtjRVlz5gOkLLeQoF4PCbvjkr3yVqYHEbJbnAc_sPoMgDbyQaSqmaHZwNSk-ZH3qh2YBysOelpA9jVnwyUZ18l7N9hNBuUkQaH7WPXnDDGIWTvJGqZU-cg) and remix it to get your unique domain. To remix it, click **Remix** at the top of the page. A unique domain will appear as a placeholder in the input element on the right side of the Glitch page.

### 2. Setup encryption key

Private key helps decrypt the messages received. The passphrase will be used to verify the private key. Along with the private key, you also need its corresponding public key, which youll upload later. Never use the private keys for your production accounts here. Create a temporary private key for testing on Glitch, and then replace it with your production key in your own infrastructure.

1. Generate the public-private key pair by running the command below in the Glitch terminal. Replace `YOUR_PASSPHRASE` with your designated passphrase. Access the Glitch terminal by clicking the **TERMINAL** tab at the bottom of the page a run following command:
   `node src/keyGenerator.js YOUR_PASSPHRASE`
2. Copy the passphrase and private key and paste them to the .env file. Click on the file labeled **.env** on the left sidebar, then click on ** Plain text** on top. *Do not edit it directly from the UI, as it will break your key formatting.*
3. After you set the environment variables, copy the public key that you generated and [upload the public key](https://developers.facebook.com/docs/whatsapp/cloud-api/reference/whatsapp-business-encryption#set-business-public-key) via the Graph API.

### 3. Set endpoint URI

Once you set up encryption keys, you can proceed with setting Endpoint URI for your flow.

1. At the top right of the Glitch page, click on **Share** and copy the **Live Site** URL from the displayed modal.
2. Head to the [Flow Builder](https://business.facebook.com/wa/manage/flows/) and in the Flow Builder click on the **three dot** menu in top right corner of the screen. Select **Setup** under the **Endpoint** section.
3. A popup will appear, allowing you to configure the endpoint URI, business phone number, and app on Meta for Developers. Save the Live Site URL copied from the Glitch into the first step of modal.

After making the necessary configurations, perform a health check from the last step of the modal. You should be able to get a successful response (if you get an error please check the details and the provided resolution advice).

### 4. Set App Secret (optional)

App secret is used in signature verification. It helps you check whether a request is coming via WhatsApp and, therefore, is safe to process. Youll add it to the **.env** file.

To access your app secret, select your App from the [dashboard in the Meta for Developers](https://developers.facebook.com/apps/). In the left navigation pane under **App settings**, choose **Basic**. Click **Show** under **App secret** and copy the secret. Then, return to Glitch, open the .env file, and create a variable named APP\_SECRET with the value of the secret you copied.

Now you have completed all the required steps to be able to test flow with the provided endpoint.

**See also**

* [Detailed code walk through](#overview-of-demo-backend) for demo backend
* [Implementing endpoint for Flows](docs/whatsapp/flows/guides/implementingyourflowendpoint) for full details on how to build production endpoint

## Testing and Debugging

### Debug flow using the interactive preview

After you complete the configurations, toggle the interactive preview in the WhatsApp Builder UI to test the Flow.

1. Trigger the interactive preview by clicking on settings menu in the **Preview** section of the Flow Builder and enabling **Interactive mode** toggle.
2. In the modal that appears, select the phone number, enter any string as **Flow token** and choose the **Request data** option under **Request data on the first screen**. This sends a request to the endpoint to retrieve data for the first screen.

Now, click on **Actions** tab at the bottom of the code editor in Builder. Youll see an `init` action in the list. Click on it to see the details and you will see the decrypted request sent to the endpoint. There will also be decrypted response received from endpoint with the initial data payload.

Return back to **Preview** and proceed to select option from radio button selection. Back in **Actions** tab notice action has changed to `data_exchange` and selected option is visible when you click on the last entry in the action log under request tab.

Keep testing out the Flow and observe the data changes in the **Actions** tab. Similar logs will be generated when users interact with the Flow from their mobile devices.

You can also see decrypted request and responses logged in the Glitch LOGS tab at the bottom of the Glitch screen.

### Send draft flow to your device

Before you publish your flow you can also send it and test it on an actual device. To send draft flow to your device, follow [instructions here](/docs/whatsapp/flows/guides/testingdebugging#send-draft-flow-to-your-device).

**See also**

* [Flow Testing and debugging guide](/docs/whatsapp/flows/guides/testingdebugging)

## Publishing

When you first created your Flow, it entered the Draft state.
And as you edited and saved the modified Flow JSON content, it remained in the Draft state.
You are able to send the Flow while it's in the Draft state, but only for testing purposes. If you want to send the Flow to a larger audience, you'll need to Publish the Flow.

You can publish your Flow once you have ensured that:

* All validation errors and [publishing checks](/docs/whatsapp/flows/guides/healthmonitoring#publishing-checks) have been resolved.
* The Flow meets the [design principles](https://developers.facebook.com/docs/whatsapp/flows/guides/bestpractices) of WhatsApp Flows
* The Flow complies with [WhatsApp Terms of Service](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fterms-of-service%2F%3Flang%3Den&h=AT22OXcxOIIUnOOY_f0sE9-PZNbSIE1-WBHMnY0-S0xpJm6yZ1Q4BK7g4NfBWIL5Yb2_5U6h7fDdy6PFtRfg9tRYLBKnEpNtWy5oL0gszvmmrPzhjMW-Q-kSXPlDIf9Ytk00JIcZVkjya9PpRrI4nQ), the [WhatsApp Business Messaging Policy](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F933578044281252&h=AT0ru5mSAEqKORijihrNSAVedhTO1nkadxPNB5GBjsd7r49By4T-xZ5l4ten3gC0vQEap7uLIh-6gBqZynJvqwqjSOB8mEfaVu67DAd7FdKyd_SxBvxr5OQ16QF5xz9EwmjtaVYv_MDQ1ldWoI_U6g) and, if applicable, the [WhatsApp Commerce Policy](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.whatsapp.com%2Flegal%2Fcommerce-policy%2F%3Flang%3Den&h=AT1vocZpyvTMFqu6VnSjuFXqZ-Qmx39VhsnlKQGuP7VCWc-RTGFkZPnyrS3y-ZcNnGbh2MidmvnUmizPNmzLLyvQYLMlCPnsRsLhussuKqgPKGVZFKl3yK-bpA8PPbhAlFmaL57rMsx4G24ESGV38A)

Remember, once a Flow has been published it can no longer be modified.
See [Flow Status Lifecycle](/docs/whatsapp/flows/gettingstarted/flows-lifecycle) for more information on the different Flow states.

To publish your Flow, open the **three dot** menu to the right of the **Save** button and click **Publish**. Once published, the Flow can be sent to anyone!

## Sending

You can send your WhatsApp Flow as:

* **[Template messages](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted/sendingaflow#templatemessages)** - these do not require a 24-hour customer service window to be open between you and the message recipient before the message can be sent.
* **[Interactive Flow messages](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted/sendingaflow#userinitiated)** - these can only be sent to a user when a customer service window is open between you and the user.

[Learn more about sending your Flow](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted/sendingaflow)

## Receiving flow response

Upon flow completion a response message will be sent to the WhatsApp chat. You will receive it in the same way as you receive all other messages from the user - via message webhook.

[Learn more about how to setup messaging webhook](/docs/whatsapp/flows/gettingstarted/receiveflowresponse)

## Monitoring

Flow monitoring is only applicable to Flows with endpoint.

After your Flow is published and being sent to the customers, it is important to monitor your Flow's health and address any problems as they are discovered by WhatsApp.

There are multiple ways how you can monitor your flows:

* Metrics Dashboard in WhatsApp Account Manager
  + Navigate to [Flow section of Whatsapp Account Manager](https://business.facebook.com/wa/manage/flows/) and click on any published flow with the endpoint. You will be presented with a Details page with a Performance Metrics Dashboard.
* Metrics API
  + All the data presented in the Details page is also available to be queried through [Flows Metrics API](https://developers.facebook.com/docs/whatsapp/flows/reference/metrics_api).
* Quality Webhooks
  + You should also [subscribe to Flows Quality Webhooks](https://developers.facebook.com/docs/whatsapp/flows/reference/flowswebhooks#subscribe-to-webhooks) to be updated in real time about the statuses and performance of your business' Flows.

See [Flow Health and Monitoring](https://developers.facebook.com/docs/whatsapp/flows/guides/healthmonitoring) overview for more information.

## Next Steps

Now that you have successfully completed this guide, learn more about what you can do with this Flows in our [Guides](/docs/whatsapp/flows/guides) and [Reference](https://developers.facebook.com/docs/whatsapp/flows/reference) sections.

## Overview of demo backend

There are four JavaScript files in the [Glitch example src directory](https://l.facebook.com/l.php?u=https%3A%2F%2Fglitch.com%2Fedit%2F%23%21%2Fwhatsapp-flows-insurance-quote&h=AT0B1mtO4OQqDhJuN-f3hVAPgkFrX-vzYqDElLZtAjEAsQOGJT0ju_O2846fuBUabxshrS86S7zmIYuQENOwNlfE8C4gyZTYCfUZIy8PURExV84yNKktTXNM2Nc7XiDrltKZxi_yEuh2YP9ikw_QRQ): `encryption.js`, `flow.js`, `keyGenerator.js`, and `server.js`. The entry file is `server.js`, so lets look at it first.

### server.js

The `server.js` file starts by configuring the Express application to use the express.json middleware to parse incoming JSON requests. Then, it loads the environment variables needed for the endpoint.

```
const { APP_SECRET, PRIVATE_KEY, PASSPHRASE, PORT = "3000" } = process.env;
```

The `server.js` file also contains a POST endpoint that performs different steps:

Checks that the private key is present:

```

if (!PRIVATE_KEY) {
  throw new Error('Private key is empty. Please check your env variable "PRIVATE_KEY".');
}
```

Validates the request signature using the isRequestSignatureValid function found at the bottom of the file:

```
if(!isRequestSignatureValid(req)) {
// Return status code 432 if request signature does not match.
// To learn more about return error codes visit: https://developers.facebook.com/docs/whatsapp/flows/reference/error-codes#endpoint_error_codes
  return res.status(432).send();
}
```

Decrypts incoming messages using the decryptRequest function found in the encryption.js file:

```
let decryptedRequest = null;
try {
  decryptedRequest = decryptRequest(req.body, PRIVATE_KEY, PASSPHRASE);
} catch (err) {
  console.error(err);
  if (err instanceof FlowEndpointException) {
    return res.status(err.statusCode).send();
  }
  return res.status(500).send();
}

const { aesKeyBuffer, initialVectorBuffer, decryptedBody } = decryptedRequest;
console.log(" Decrypted Request:", decryptedBody);
```

Decides what Flow screen to display to the user. Youll look at the getNextScreen function in detail later.

```
const screenResponse = await getNextScreen(decryptedBody);
console.log(" Response to Encrypt:", screenResponse);
```

Encrypts the response to be sent to the user:

```
res.send(encryptResponse(screenResponse, aesKeyBuffer, initialVectorBuffer));
```

### encryption.js

This file contains the logic for encrypting and decrypting messages exchanged for security purposes. See [Code examples](https://developers.facebook.com/docs/whatsapp/flows/guides/implementingyourflowendpoint#code-examples) section of Endpoint implementation guide for encryption examples in other languages.

### keyGenerator.js

This file helps generate the private and public keys, as you saw earlier.

### flow.js

The logic for handling the Flow is housed in this file. It starts with an object assigned the name `SCREEN_RESPONSES`. The object contains screen IDs with their corresponding details, such as the preset data used in the data exchanges. This object is generated from Flow Builder under **"..." > Endpoint > Snippets > Responses**. In the same object, you also have another ID, `SUCCESS`, that is sent back to the client device when the Flow is successfully completed. This closes the Flow.

The `getNextScreen` function contains the logic that guides the endpoint on what Flow data to display to the user. It starts by extracting the necessary data from the decrypted message.

```

const { screen, data, version, action, flow_token } = decryptedBody;
```

WhatsApp Flows endpoints usually receive three types of requests:

* A [data\_exchange](https://developers.facebook.com/docs/whatsapp/flows/guides/implementingyourflowendpoint#data_exchange_request) request signified by a `data_exchange` action
* An [error notification](https://developers.facebook.com/docs/whatsapp/flows/guides/implementingyourflowendpoint/#error_notification_request) request signified by a `data.error` element
* A [health check](https://developers.facebook.com/docs/whatsapp/flows/guides/implementingyourflowendpoint/#health_check_request) request signified by a `ping` action

#### Health check and Error handler

The function handles the health check and error notifications using if statements and responds accordingly, as shown in the snippet below:

```

// handle health check request
if (action === "ping") {
    return {
        version,
        data: {
            status: "active",
        },
    };
}

// handle error notification
if (data?.error) {
    console.warn("Received client error:", data);
    return {
        version,
        data: {
            acknowledged: true,
        },
    };
}
```

#### INIT handler

When a user clicks the Flows call to action (CTA) button, a request with `INIT` action is sent to the endpoint. This action returns the initial data for the APPLICANTS screen.

```
 // handle initial request when opening the flow and display APPLICANTS screen
  if (action === "INIT") {
    return {
      ...SCREEN_RESPONSES.APPLICANTS,
      data: {
        ...SCREEN_RESPONSES.APPLICANTS.data,
        additional_applicants_count: undefined,
      },
    };
  }
```

#### data-exchange handlers

For `data_exchange` actions, a switch case structure is used to determine what data to send back based on the screen ID and other request data.

For the first screen with ID `APPLICANTS` we handle two requests. If the `cover_for_additional` field of the request is not null, it means that the user has selected to add additional applicant and therefore a new additional\_applicants\_count and add\_additional boolean are returned back to the client to keep track of additional applicants.

If the `cover_for_additional` field of request is null, it means that the user clicked on the Continue button on the Applicants screen. We return the next screen name in the response (`COVER_LEVEL`) and data received from the client.

For the next two screens, `COVER_LEVEL` and `EXCESS`, we set the initial data for next screen and attach data received from the Flow.

On the `DETAILS` screen, if user has selected they want to cover only their children we skip `YOUR_HEALTH` screen.

```

if (data.cover === "my_children") {
  return {
    ...SCREEN_RESPONSES.ADDTIONAL_APPLICANT,
    data: {
      ...data,
      additional_applicants: [],
      additional_applicant_title: "Additional Applicant 1",
      additional_applicant_index: 0,
    },
  };
}
```

Otherwise we navigate to next screen `YOUR_HEALTH` and we override specific fields in the initial screen data with data received from Flow.

For `YOUR_HEALTH` screen if `cover` is just just for `myself` we take user to `POLICY_SELECTION` screen next.

```

if (data.cover === "myself") {
  return {
    ...SCREEN_RESPONSES.POLICY_SELECTION,
    data: {
      // copy initial screen data then override specific fields
      ...SCREEN_RESPONSES.POLICY_SELECTION.data,
      ...data,
    },
  };
}
```

Otherwise we navigate to `ADDTIONAL_APPLICANT` screen.

For the `ADDTIONAL_APPLICANT` screen while `applicant_index < data.additional_applicants_count` we keep sending user to `ADDTIONAL_APPLICANT` screen until we have collected information for all additional applicants.

```

if (applicant_index < data.additional_applicants_count) {
  return {
    ...SCREEN_RESPONSES.ADDTIONAL_APPLICANT,
    data: {
      ...rest,
      additional_applicant_title: `Additional Applicant ${
        applicant_index + 1
      }`,
      additional_applicant_index: applicant_index,
      additional_applicants: updateApplicantsList,
   },
 };
}
```

After all the additional applicants information is collected we navigate to `POLICY_SELECTION` screen.

```

return {
  ...SCREEN_RESPONSES.POLICY_SELECTION,
  data: {
    // copy initial screen data then override specific fields
    ...SCREEN_RESPONSES.POLICY_SELECTION.data,
    ...rest,
    additional_applicants: updateApplicantsList,
    additional_applicants_count: undefined, // we do not need to send the count to the next screen
    additional_applicant_index: undefined, // we do not need to send the index to the next screen     },
};
```

For the `POLICY_SELECTION` screen we set policy details based on `selected_policy` and navigate to `SELECTED_POLICY` screen.

From `SELECTED_POLICY` we navigate to `YOUR_QUOTE` screen, where we set `payment_option` based on what user selected and then navigate to final `SUMMARY` screen.

After the `SUMMARY` screen is submitted from the client, a success response is sent to the client device to mark the Flow as complete.

Nesta Pagina

[Use Case Guide: Insurance Quote](#use-case-guide--insurance-quote)

[Intro and Overview](#intro-and-overview)

[Getting Started](#getting-started)

[Flows JSON Template](#flows-json-template)

[Create new flow from a template](#create-new-flow-from-a-template)

[Configure Demo Backend on Glitch](#configure-demo-backend-on-glitch)

[1. Remix (fork) Glitch endpoint](#1--remix--fork--glitch-endpoint)

[2. Setup encryption key](#2--setup-encryption-key)

[3. Set endpoint URI](#3--set-endpoint-uri)

[4. Set App Secret (optional)](#4---set-app-secret--optional-)

[Testing and Debugging](#testing-and-debugging)

[Debug flow using the interactive preview](#debug-flow-using-the-interactive-preview)

[Send draft flow to your device](#send-draft-flow-to-your-device)

[Publishing](#publishing)

[Sending](#sending)

[Receiving flow response](#receiving-flow-response)

[Monitoring](#monitoring)

[Next Steps](#next-steps)

[Overview of demo backend](#overview-of-demo-backend)

[server.js](#server-js)

[encryption.js](#encryption-js)

[keyGenerator.js](#keygenerator-js)

[flow.js](#flow-js)
