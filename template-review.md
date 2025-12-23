![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Ftemplate-review%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Review](/docs/whatsapp/business-management-api/template-review)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
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

[Template review](#template-review)

[Approval process](#approval-process)

[Samples](#samples)

[Common rejection reasons](#common-rejection-reasons)

[Parameter formatting](#parameter-formatting)

[Content and Policy Violations](#content-and-policy-violations)

[Character limits and text format](#character-limits-and-text-format)

[Duplication](#duplication)

[Rejection Notifications](#rejection-notifications)

[Appeals](#appeals)

[In the WhatsApp Manager:](#in-the-whatsapp-manager-)

[Template review webhooks](#template-review-webhooks)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Template review

Cloud API reviews templates and variable parameters using machine learning to protect the security and integrity of Cloud API services. When Cloud API reviews templates and variable text, no information is shared with WhatsApp.

When you submit a template creation request, the content undergoes validation through a combination of automated systems and manual reviews. This process ensures that the template complies with WhatsApp’s policies and quality standards. Templates that contain spam, scam-like content, or violate WhatsApp policies are rejected during this review process.

## Approval process

Once you have created your template you can submit it for approval. It can take up to 24 hours for an approval decision to be made. Once a decision has been made, a notification will appear in your WhatsApp Manager and we will send an email to your Business Manager admins. In addition, we will send a [message\_template\_status\_change](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update) webhook.

If your message template is approved, its status will be set to **Active - Quality pending** (`APPROVED` in the API) and you can begin sending it to customers. If it is rejected, you can edit it and resubmit for approval, or appeal the decision.

### Samples

If your template uses variables you must include sample variable values (media assets, text strings, etc.) with your submission. This makes it easier for us to visualize how your template will appear to customers.

To include a sample with your submission in the WhatsApp Manager, first create your template, adding any variables that it requires, then click the Add Sample button. The preview pane will render any sample media assets or sample text values you provide.

## Common rejection reasons

Submissions are commonly rejected for the following reasons, so make sure you avoid these mistakes.

### Parameter formatting

* Variable parameters are missing or have mismatched curly braces. The correct format is `{{1}}` for positional parameters .
* Variable parameters contain special characters such as a `#`, `$`, or `%`.
* Variable parameters are not sequential. For example, `{{1}}`, `{{2}}`, `{{5}}`, `{{4}}`.
* The template contains too many variable parameters relative to the message length. You need to decrease the number of variable parameters or increase the message length.
* The message template cannot start or end with a parameter i.e. dangling parameters are not allowed.

### Content and Policy Violations

* The message template contains content that violates WhatsApp’s Commerce Policy: When you offer goods or services for sale, we consider all messages and media related to your goods or services, including any descriptions, prices, fees, taxes and/or any required legal disclosures, to constitute transactions. Transactions must comply with the WhatsApp Commerce Policy.
* The message template contains content that violates the WhatsApps Business Policy: Do not request sensitive identifiers from users. For example, do not ask people to share full length individual payment card numbers, financial account numbers, National Identification numbers, or other sensitive identifiers. This also includes not requesting documents from users that might contain sensitive identifiers. Requesting partial identifiers (ex: last 4 digits of their Social Security number) is OK.
* The content contains potentially abusive or threatening content, such as threatening a customer with legal action or threatening to publicly shame them.

### Character limits and text format

The body component will have different character limits depending on the format and tag of the template. The number of emojis allowed in the body component may also be limited.

### Duplication

The message template is a duplicate of an existing template. If a template is submitted with the same wording in the body and footer of an existing template, the duplicate template will be rejected.

### Rejection Notifications

A rejection notification that includes the rejection reason will appear in Business Support Home. You can view rejections in the Business Support Home by navigating to **Account Overview** > **View my accounts** (button) > (your Meta Business Account) > (your WABA) > **Rejected message templates**.

Rejection info will also be sent via email.

You can refer to the Business Support Home notification to see the name and language of the existing template with the same content as the rejected duplicate template. You may also choose to edit the template and resubmit.

Note: This check does not apply to templates categorized as `AUTHENTICATION`.

## Appeals

If your submission is rejected you may file an appeal. Note that appeals must include a sample. If an approved template has become disabled, you may also edit it and resubmit it for approval.

### In the WhatsApp Manager:

1. Mouseover the suitcase icon (Account tools) and click Message templates. If you have multiple WhatsApp Business Accounts, use the dropdown menu in the top-right corner to select the account whose templates you want to manage.
2. Find the message template that you would like to edit and click it.
3. Edit the template's contents.
4. Click the **Add Sample** button and add sample variable values and images.
5. Click **Submit**.

The appeal will be reviewed and a decision made within 24 hours.

## Template review webhooks

You can receive updates via the [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update) webhook, which notifies whether a template is approved, pending, or rejected.

If your template is rejected and you disagree with the decision, you have the option to submit an appeal for reconsideration.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Template review](#template-review)

[Approval process](#approval-process)

[Samples](#samples)

[Common rejection reasons](#common-rejection-reasons)

[Parameter formatting](#parameter-formatting)

[Content and Policy Violations](#content-and-policy-violations)

[Character limits and text format](#character-limits-and-text-format)

[Duplication](#duplication)

[Rejection Notifications](#rejection-notifications)

[Appeals](#appeals)

[In the WhatsApp Manager:](#in-the-whatsapp-manager-)

[Template review webhooks](#template-review-webhooks)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qqMCxOLBC-2uahAay7C1tg&oh=00_AfhPEBH1CvecFaVkn4wllr2xN6zoZcTsyhljfdSCI1W4Xw&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qqMCxOLBC-2uahAay7C1tg&oh=00_AfgbLH-QDchuHn8we_Mt77oNNYhAZ3cDXQH1GYjmTPeHSg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qqMCxOLBC-2uahAay7C1tg&oh=00_AfiubJjnEoVWTRAmVtaw7hmEiBTYiyiD7s7ZgPIwCS3yBw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qqMCxOLBC-2uahAay7C1tg&oh=00_AfjjeSLKnzNqfCTs7fuln4sLsKCLln4Uh65DgtPgUjM4Ng&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=qqMCxOLBC-2uahAay7C1tg&oh=00_AfgVi_05dqmkbkzvrBTfE7zOFPkuNRtxaQbVf3tiJdaVNQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3oMSBAW2Z8_wu59hvspzHB63RZU9rI5YTK2eePgg1bBYha5PbSnPRFv-ZC7RyXzOvgYuoVDDZKm5o_MkWsHJT4kikJHHVFuABiDKKwe2s5x2rFLUujOx3N_aWrDFDUwhxXEeconfv5Q7nHX-eIpQ)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)