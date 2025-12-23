![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fguides%2Fset-up-whatsapp-echo-bot%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)[Create a test webhook endpoint](/docs/whatsapp/cloud-api/guides/set-up-whatsapp-echo-bot)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)

  + [Create a webhook endpoint](/docs/whatsapp/webhooks/create-webhook-endpoint)
  + [Create a test webhook endpoint](/docs/whatsapp/cloud-api/guides/set-up-whatsapp-echo-bot)
  + [Substituições de webhook](/docs/whatsapp/cloud-api/webhooks/override)
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

[Create a test webhook endpoint](#create-a-test-webhook-endpoint)

[Requirements](#requirements)

[Step 1: Create a Github repository](#step-1--create-a-github-repository)

[Step 2: Deploy a Node Express app on Render](#step-2--deploy-a-node-express-app-on-render)

[Step 3: Add your test webhook app URL to your Meta app](#step-3--add-your-test-webhook-app-url-to-your-meta-app)

[Step 4: Send a test message](#step-4--send-a-test-message)

[Troubleshooting](#troubleshooting)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Create a test webhook endpoint

If you aren't ready to create your own webhook endpoint yet, you can deploy a test webhook app on [Render.com](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.render.com%2F&h=AT0NPWp6TOWGz9FREH0RHkb6WcDRWFzFNvoYEeknru9ZWmGT_eR6GyZl8jdZBggYj1kz9qEHhmuPJuifqwbCer9bn77LPS_cCGfKfpBxj_DUXNV2DQ4GC9mbI3iGuet4_OgPkUYAU1nIhJ2aHXPeNA) that accepts webhook requests and dumps their contents to Render's console.

*Only use this app for testing purposes.*

## Requirements

* A [Render](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.render.com%2F&h=AT2ceqSJdkNPm4edBdwFMFhmp6sOuJbZPxzFSxa1jThAj0CUjHwIeYChCJ9yyDQLn-daF0hbtVd6d7ABNupMNhrrxy66DN8lptNQF_4x5W3j6LSJwPK-qbo6d0xrDh3YEwWYvaB5fTijsCUjWYIfbg) account.
* A [Github](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.github.com%2F&h=AT3Z0HZVxnptN8es1steqqrUd5RE5Iv3stBk60mp5Iie-cYjc7UQjbZEyoGFcHrMoVOsIbKSUHMBxnVS-WpgDMs0JUlLLhIcliT5_ObN8elsBuh3rhKLwokfGQPj3xbxWxZ5TQBanf7TeSx5YkFjlQ) account.

## Step 1: Create a Github repository

Sign into your Github account and create a new repo (public or private) with a name of your choice. Within the repo, create an `app.js` file and paste this code into it:

```
// Import Express.js
const express = require('express');

// Create an Express app
const app = express();

// Middleware to parse JSON bodies
app.use(express.json());

// Set port and verify_token
const port = process.env.PORT || 3000;
const verifyToken = process.env.VERIFY_TOKEN;

// Route for GET requests
app.get('/', (req, res) => {
  const { 'hub.mode': mode, 'hub.challenge': challenge, 'hub.verify_token': token } = req.query;

  if (mode === 'subscribe' && token === verifyToken) {
    console.log('WEBHOOK VERIFIED');
    res.status(200).send(challenge);
  } else {
    res.status(403).end();
  }
});

// Route for POST requests
app.post('/', (req, res) => {
  const timestamp = new Date().toISOString().replace('T', ' ').slice(0, 19);
  console.log(`\n\nWebhook received ${timestamp}\n`);
  console.log(JSON.stringify(req.body, null, 2));
  res.status(200).end();
});

// Start the server
app.listen(port, () => {
  console.log(`\nListening on port ${port}\n`);
});
```

## Step 2: Deploy a Node Express app on Render

Follow Render's instructions for [deploying a Node Express app](https://l.facebook.com/l.php?u=https%3A%2F%2Frender.com%2Fdocs%2Fdeploy-node-express-app&h=AT05P3HRv-W-nGlcM2b1MzBAsrqDd2C0kypq7kjbPvzGW6DVcfXOpGK0p1vgwxZVwTalLg6KNJA3QCSBfpSGiloXp0-bfusp3kQMJRtuLVfDQKkpLTS0RHwn-w46OcgNm7BFASSkuAUbEgCWvz1nuw), with these differences:

* Skip step 1
* Use these settings for step 3:
  + Build command: `npm install express`
  + Start command: `node app.js`
  + In the **Environment Variables** section, add the variable `VERIFY_TOKEN` and set it to a string of your choice (e.g. `vibecode`).

When you're done, click the **Deploy your web service** button. This will take you to the app log where you will see your app being built, which can take a few minutes. You'll know it's done when you see "Your service is live" in the log.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/518314752_779138407775567_4233589617658404934_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=fdtL28JWVnIQ7kNvwHumkOf&_nc_oc=Adn79MY4LfKmXhhOF-YMLY64HmgrHV1RM004TOsolGuQtGzOOO_ObU03BFVj9iw4zQw&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=BcHw_eh0E2hCmLwMPI9kdg&oh=00_AfjsHWwse5eusjxOgweyfVyoTUdoLgPQHtbcJ---F-2aEg&oe=694064C5)

Copy your deployed test webhook app URL, which is displayed at the top of the page under your Github repo name. (If you view the URL, you'll get a 403 error, which is expected).

## Step 3: Add your test webhook app URL to your Meta app

Open a new window/tab, and navigate to the (Meta) [App Dashboard](/apps) > **WhatsApp** > **Webhooks** > **Configuration** panel.

Paste your test webhook app URL in the **Callback URL** field, and add the `VERIFY_TOKEN` environment variable string you set earlier to the **Verify token** field, then click **Verify and save**.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/518348561_1679202599393717_3427225193188619311_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=ERZHbUR8GmIQ7kNvwEn7RPL&_nc_oc=Adk6Q1rAmQH3Y6ji5QLKiCgiTQ9rRnd-RCfcGi1K1-Cx0gRO7dWQudNTcke9pFFSrMY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=BcHw_eh0E2hCmLwMPI9kdg&oh=00_AfjZn4fOGSpBegG9pLmZ5ognRIqg3Q4D-Eu8AfKGI6jyKQ&oe=69405C70)

If verification is successful, the Meta app dashboard should refresh and you should see a list of webhook fields you can subscribe to.

*Subscribe to the **messages** webhook field if you haven't already.*

Also, in Render's app log, if you see "WEBHOOK VERIFIED", your test webhook app URL has been successfully verified.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/516871315_2146397049169598_3394446764023076795_n.png?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=I0pAmrQ3340Q7kNvwE6r7Qa&_nc_oc=AdmsKlVFRng9c67Kj8ms_vVxlpKgbjJ8tRYLMGlke_-z7dUVwD35xu_BbAagwDHaodE&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=BcHw_eh0E2hCmLwMPI9kdg&oh=00_AfjRuLDn-iGexGBpntqwVPcESGgmtRZQWfQXdcp854R3BA&oe=69404CD0)

## Step 4: Send a test message

Back in the Meta app dashboard **Configuration** panel, scroll down to the **messages** webhook field, subscribe to the field if you haven't already, then click the **Test** link.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/518357131_2083466912058941_6508814785021877118_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=G0UTIhnyQ_EQ7kNvwElLvAN&_nc_oc=AdmJ3b3148zlFPCbnrhcYmfGOuYVVJ-a-x6E3LqKHlTR6RwBqvz6lPstuVTB1Uqfgp4&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=BcHw_eh0E2hCmLwMPI9kdg&oh=00_AfhzW2F9xz-arwKqDH0YqkfULdG25xx_OAH-u-3DceF7tw&oe=69405A8B)

This will send a test message to your test webhook app. Confirm that it appears in Render app log with "Webhook received" followed by a test JSON payload:

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/516488905_709538035232698_4800340255912767794_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=FIATQu_AISAQ7kNvwHraQ6h&_nc_oc=Adls3x3ffz4pXnWMR-WMxvm7zUJZn9UvZARybmLEXkl8yEQtBFNPT7K09vI441XU5eA&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=BcHw_eh0E2hCmLwMPI9kdg&oh=00_Afihe7gyQMmU_87feswlAfk8r0Ycnv9YM4MfXGQTQjCF0g&oe=69407DC1)

## Troubleshooting

If the test **messages** webhook doesn't appear in the Render app dashboard log:

* Confirm that you successfully added your test webhook app URL to your Meta app (Step 3).
* Confirm that your app is subscribed to the **messages** webhook field.
* Make sure you are sending a **messages** test webhook; some test webhooks only work when your app is in Live mode, while others only work in Development mode (**messages** test webhooks work in both modes).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Create a test webhook endpoint](#create-a-test-webhook-endpoint)

[Requirements](#requirements)

[Step 1: Create a Github repository](#step-1--create-a-github-repository)

[Step 2: Deploy a Node Express app on Render](#step-2--deploy-a-node-express-app-on-render)

[Step 3: Add your test webhook app URL to your Meta app](#step-3--add-your-test-webhook-app-url-to-your-meta-app)

[Step 4: Send a test message](#step-4--send-a-test-message)

[Troubleshooting](#troubleshooting)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=KklK6hO5YVyYHnvXZnEbeg&oh=00_AfhPfwm91PKuvcd5-8dv6ohoLCGlpkEQLGGFeldShcNGvA&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=KklK6hO5YVyYHnvXZnEbeg&oh=00_AfjaeBC4cobLrVBzjjHCt5jInbt0JCGVQLcsI15Lu2aWBQ&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=KklK6hO5YVyYHnvXZnEbeg&oh=00_AfgE24XLx1Z0YMcQOE29mok7siSSGMy5INOQw-oAobtV-w&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=KklK6hO5YVyYHnvXZnEbeg&oh=00_AfjSUd6MHv8OFwjImuxYgN_yPRB-F1Avtk2-15_UMvCuKQ&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=KklK6hO5YVyYHnvXZnEbeg&oh=00_Afg6-vuDZf5T_nIfZceZahrHRTIBlAZ9Yy9-YtLOG8SCpA&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3vYZJ66svDd0bWPgB3zkI0LDIXs0U1evH11pZASWhbL7yZWMFTDT8PQbb63Jh5wRpPq9DB5ek0lRVFjuZZjQBZutkj7v4Ll-YjO10riWWE4nTYyoJ0kRmPZNgHWYbQsTNaLvXc8EpuDJ6ZWPZ2Ug)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)