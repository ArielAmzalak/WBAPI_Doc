![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fdisplay-names%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Display names](/docs/whatsapp/display-names)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)

  + [Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)
  + [Official Business Accounts](/docs/whatsapp/official-business-accounts)
  + [Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)
  + [Business profiles](/docs/whatsapp/business-profiles)
  + [Display names](/docs/whatsapp/display-names)
  + [Receber aceitação](/docs/whatsapp/overview/getting-opt-in)
  + [Identity Change](/docs/whatsapp/overview/identity-change)
  + [Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)
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
* [Registro de alterações](/docs/whatsapp/business-platform/changelog)
* [Suporte](/docs/whatsapp/support)

Nesta Página

[Display names](#display-names)

[Display name guidelines](#display-name-guidelines)

[Display name verification](#display-name-verification)

[Viewing display name in WhatsApp Manager](#viewing-display-name-in-whatsapp-manager)

[Getting display name and display name status via API](#getting-display-name-and-display-name-status-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Updating display name via WhatsApp Manager](#updating-display-name-via-whatsapp-manager)

[Updating display name via API](#updating-display-name-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Learn more](#learn-more)

# Display names

You must provide a display name when [registering](#registering-business-phone-numbers) a business phone number. The display name appears in your business phone number's WhatsApp profile:

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/507127951_698062976515521_2852142619234157074_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=-AMx-e8Xpc0Q7kNvwHB7QVx&_nc_oc=AdnObMjsf2ux4jbU_OGErB_CuM-PHw8zbpPp_NfKrGlAFOZi2aWms8wJpLaVy9JAfzk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfjtOotwWRgGh4tHZOBj7Y7X83V_SoVpwITf8O0rSZPimw&oe=69404C29)

It can also appear at the top of **individual chat** threads and the **chat list** if your business phone number is approved via [display name verification](#display-name-verification). Note that if a WhatsApp user edits your profile name in the WhatsApp client, the name they set will appear instead.

## Display name guidelines

See our [Display name guidelines for the WhatsApp Business Platform](https://www.facebook.com/business/help/757569725593362) Help Center article for naming guidelines.

## Display name verification

When you reach a [higher messaging limit](/docs/whatsapp/messaging-limits), your business phone number's display name will automatically undergo verification based on our [display name guidelines](https://www.facebook.com/business/help/757569725593362). When we complete the process, a [phone\_number\_name\_update](/docs/whatsapp/cloud-api/webhooks/reference/phone_number_name_update) webhook and Meta Business Suite notification will be triggered.

If your display name is approved, the webhook will have `decision` set to `APPROVED`, and we will set the `name_status` field on your business phone number to `APPROVED`.

If your display name is rejected, the webhook will have `decision` set to `REJECTED`, and we will set the `name_status` field on your business phone number to `DECLINED`. If your name is rejected, we recommend that you re-review our [display name guidelines](https://www.facebook.com/business/help/757569725593362) and [edit your display name](https://www.facebook.com/business/help/378834799515077) accordingly, or file an appeal via [Developer Support](/docs/whatsapp/support#developer-support) or [Enterprise Developer Support](/docs/whatsapp/support#enterprise-developer-support).

## Viewing display name in WhatsApp Manager

Your business phone number's display name appears in the **Name** column in the [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/) > **Account tools** > **Phone numbers** panel.

## Getting display name and display name status via API

Request the `verified_name` and `name_status` field on your WhatsApp Business Phone Number ID to get its display name and display name status. See the [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) reference for a list of returnable values and their meanings.

Note that the `verified_name` value does not indicate if the display name is approved or not, it just represents the display name string that will undergo verification when eligible. The `name_status` field indicates its approval status.

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922?fields=verified_name%2Cname_status' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```
{
  "verified_name": "Lucky Shrub",
  "name_status": "APPROVED",
  "id": "106540352242922"
}
```

## Updating display name via WhatsApp Manager

To update your display name via WhatsApp Manager:

1. Navigate to [WhatsApp Manager](https://business.facebook.com/latest/whatsapp_manager/) > **Account tools** > **Phone numbers**.
2. Select your business phone number.
3. Click the **Profile** tab.
4. In the **Display name** section, click the **Edit** button and complete the flow.

Once you complete the flow, your display name will undergo [display name verification](#display-name-verification) again.

This information is also available in our [How to change your WhatsApp Business display name](https://www.facebook.com/business/help/378834799515077) Help Center article.

## Updating display name via API

Use the [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Updating) endpoint's `new_display_name` field to update your display name via API.

### Example request

```
curl -X POST 'https://graph.facebook.com/v24.0/106540352242922?new_display_name=Lucky%20Shrub' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```
{
  "success": true
}
```

Upon success, your display name will undergo [display name verification](#display-name-verification). If you want to check the verification status, request the `new_display_name` and `new_name_status` fields on your business phone number ID:

### Example request

```
curl 'https://graph.facebook.com/v23.0/106540352242922?fields=new_display_name,new_name_status' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

Upon success:

```
{
  "new_display_name": "New Lucky Shrub",
  "new_name_status": "PENDING_REVIEW",
  "id": "106540352242922"
}
```

If your newly updated display name is approved, your business phone number's `verified_name` and `name_status` fields will be updated to reflect your new display name and name status, and **phone\_number\_name\_update** webhooks will be triggered.

## Learn more

The following Help Center articles provide additional information about display names.

* [About WhatsApp Business display name](https://www.facebook.com/business/help/338047025165344)
* [How to change your WhatsApp Business display name](https://www.facebook.com/business/help/378834799515077)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Display names](#display-names)

[Display name guidelines](#display-name-guidelines)

[Display name verification](#display-name-verification)

[Viewing display name in WhatsApp Manager](#viewing-display-name-in-whatsapp-manager)

[Getting display name and display name status via API](#getting-display-name-and-display-name-status-via-api)

[Example request](#example-request)

[Example response](#example-response)

[Updating display name via WhatsApp Manager](#updating-display-name-via-whatsapp-manager)

[Updating display name via API](#updating-display-name-via-api)

[Example request](#example-request-2)

[Example response](#example-response-2)

[Learn more](#learn-more)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_Afi4K2q47LjzLzjmeQogT38fql_GyFEDUywDbgrnoBEV9w&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfiZOXLvyxC_u4XGv-5KwXGyvYepFQMIMvvb8jMVmyMVeQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_Afh_PxQ3vxxOPwrZD4Vr6H4dGx9vSbv6QjIsWp_uhNElrw&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1pZp6utVFeXFACb3XyPjWJCFkZkNMLNu4pO-HpMXPEV69AmVR5EJwiY-DwGMPCinMUo5ricOeqk28doAEwJoHPazAseaAanGnZRYB9yqBkaPmRflGQfy9lI9tCjsFW6fh9XdAf9FNSE750bLRZ0g)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_Afh8noy6q4Wo2aljOH7_EL49587vvdCRariol57-5Ml8HA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0yggYCFlUYxfOFSVvGXLpF3KEvi8wpzAAwAnQ_G_ogg48z0zuoCE3hwy7p0d-eRaRf7GWlpx_Napy9PjNtTDhXKniq0CQP2nQVIE2LdY8sDXmTnXlz5Pzcqr7g1rmA--_fUjWhYZkKHVnJSBgH5ZHqxJ4pyZMdx6o)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfhPZwZmr6IumZVTrAQ1Ny_Of7CI_cVLnY7E_mpasqmZIA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT00sjgfahOOi-x6Xk0tBBy4fTxk1a74RQyeMfyHifWlSOCCTt4T0Fl8sY9rw4gqiHaDTqZFaqr0HXsij8a7MqRbDo7uHeekOYOSM2JRqEZbs6aQlkg9cw9Mo5wxgo2FUqJ6GeWTZIiODY0mQg7mGg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfhoP7jPea9TnD_yrfgk1kkLOPw0juCL9FVUBa9Jk6oyvQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0KDMPVy3D3-M74fl8JKziQU09mdIeU0_Qpw1_BOeui-QBNoi9vCAFFgTZ2H9RtbJEmT5tMUfmyMAzzdl1hLovnXLY6gscZIqTh6oAa-GYN6lW1dYnIoX8Q9H_UA9XzC5aIFsdk5dTNCg8zd66ZEg)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT0j0_fTNCY0JZGDQjbAekEBMbWJZ3i-HJYAXoW1p78q7bRgcP_XLqoPwt_QgI0H39O4o70a3AA0-rZ5-YQQAoGiUiWhGVNzRwD_7Iz1w7Eu2fkMKHCR-S5l76RfA9tMhz6Y--kxQxerXiKAdO-g2Q)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1pP898jAClAYdgvKJ22dPGtrqZj9ns_Clnu8arn8LaJ2hGqAxJ9UpoPFC9sHMzGHQ3cMw_EtfceHQZclnmdBKb5iV1bIUyDNTfCLuJTwwrVh8gJy7cxV0oLjlSSxtP9W-I3bbtJg5_e-cITGtxIA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfjQTFZ5ykCcJ3lKI9lIefc3aFYMrOxhdrakBaKpeW7bDw&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfhOEqBByQft4mfHSAJ2eS61Fy8T4nqJvZfcCIdI7uzOMw&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1POOs5Nbuk-3F8fLg7zvBCbxsMzBUItI_MHl-ubSPZu64mqJGcJVOLGs7t3FaXHyKrLxeZiypVfVXIPFOQxgSAnDUiILaR7-teJ6Bm9txaMjE3RXGjfcwb619eZsTSN9YLzoXXNy9ZFkQQhMyvow)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_Afj7IGmrWRCdRiAp9fwP2FqQprOaobq_u2Qqfj2vkarroA&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1O44_3Nga7M2HSJdfsR33bxFZIlIHAvIB1t-KuJCapPb2ApiUHEFi7YlNnu64VRZo5Zfypwimu3DpkbDGAEn6vaoZrzyJIBynHZKsnSJavSDvvGqJTa41rQv28jC0eniP7Qa8obmrEFpES_GtdXw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfgBwwB2ssMx3daSIpm8w4TQJPV3JmnK3H_fUFOHm3mXsw&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT11FyFhDkDoEtwGW5yE_bk5ITseo7C6wjPtmX3cifFBN7U9O53j5VV0eFGdqguoalLTg-8C0nCAZbJL42hAP8b3KK0om4LXLAPpGklPCnZPwsSLUauvkTuE998oYVgo1j49zmScsrvOJpEHb4YsJQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=BBwHNcy_NT2v8d4TIA39ZA&oh=00_AfjTa1vT4_XyxLGIYKKgt7di_qTjfWds07wH314n7kuqdw&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1caeCTH2qXBJPagAsZe4DiHPRqH2Mt_y-P-7JUHReRtuIJXb1I42g7FnLzQsICvp3bOrQWQq9tfN6NB8QePR7dEDBWkReP2_jgwJo14iBz6jLIt3xcVcJZQjEIBCt3n4nD5qaKYNDMVf8AfDHtew)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2FAuQ6JNzkPiv05fMXAYq2AYzQpjExyQn9gQrdqSWHrkkQYAU04tSYZZI6udy6WwfAYpUPZ3V6UGQwtuL-zm_T6fPHFMDIsZzbgrpFV39KV_bD9_400hDYGDoTrk1zXpI9qJ-GVNJYXpzh29qmbg)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)