![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fbusiness-management-api%2Fmessage-templates%2Fmarketing-templates%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Modelos](/docs/whatsapp/business-management-api/message-templates)[Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)

  + [Modelos de autenticação](/docs/whatsapp/business-management-api/authentication-templates)
  + [Marketing templates](/docs/whatsapp/business-management-api/message-templates/marketing-templates)

    - [Custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates)
    - [Modelos de catálogo](/docs/whatsapp/business-management-api/message-templates/catalog-templates)
    - [Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template)
    - [Modelos de cupom](/docs/whatsapp/business-management-api/message-templates/coupon-templates)
    - [Modelos de oferta por tempo limitado](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates)
    - [Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates)
    - [Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates)
    - [Product Card Carousel Templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates)
    - [Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates)
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

[Marketing templates](#marketing-templates)

[Custom templates](#custom-templates)

[Specialty templates](#specialty-templates)

[Catalog templates](#catalog-templates)

[Coupon code templates](#coupon-code-templates)

[Media card carousel templates](#media-card-carousel-templates)

[Call permission request templates](#call-permission-request-templates)

[Limited-time offer templates](#limited-time-offer-templates)

[Multi-product message templates](#multi-product-message-templates)

[Product card carousel templates](#product-card-carousel-templates)

[Single-product message templates](#single-product-message-templates)

[Per-user marketing template message limits](#per-user-marketing-template-message-limits)

[User preferences for marketing messages](#user-preferences-for-marketing-messages)

[Interested/Not Interested feedback](#interested-not-interested-feedback)

[Stop/Resume controls](#stop-resume-controls)

[For accounts linked with WhatsApp Business app (aka "Coexistence")](#for-accounts-linked-with-whatsapp-business-app--aka--coexistence--)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785&transcode_extension=webp)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Marketing templates

Marketing templates are typically used to drive engagement, brand awareness, and driving sales.
They are the only type of template that can be used with both Cloud API and Marketing Messages Lite API.

## Custom templates

You can use the [POST /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>/message\_templates](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/#Creating) endpoint to create custom marketing templates that suit your business needs from any supported components.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/555677225_1191798406305539_8221742988743767334_n.png?stp=dst-webp&_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=dOEliZVhLZkQ7kNvwHtl7qV&_nc_oc=AdlN14muPlO3FHt_EPaoDvcB4l4Ducnf5vadkISQr9Np0o23fE-M-RWc4IIiAfij3us&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfiATuAu_LmHl1h1UqXebehYEeDv5dtYAeNxZcktIIcgww&oe=694072A3)

See our [custom marketing templates](/docs/whatsapp/business-management-api/message-templates/custom-marketing-templates) document for example of how to create and send a custom template, and which components are supported.

## Specialty templates

Some templates use a special component that requires or excludes additional components, or require additional configuration. These are described below.

|  |  |
| --- | --- |
| Catalog templates [Catalog templates](/docs/whatsapp/business-management-api/message-templates/catalog-templates) are marketing templates that allow you to showcase your product catalog entirely within WhatsApp. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/354047426_125269187252102_7173148343631613735_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=b5R6jfDxH9EQ7kNvwEF_Mdy&_nc_oc=AdkV8PmjGGpdTsrhMDfI-JvVMYga1OC1vIRqjXrZlM7GWRrcwGuRxOUgoixk5DC5sSk&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfglmKuwljx0aH50o3M3mTeiKd_vdVbA3B6sjUOy1kpZtA&oe=69405A26) |
| Coupon code templates [Coupon code templates](/docs/whatsapp/business-management-api/message-templates/coupon-templates) are marketing templates that display a single copy code button. When tapped, the code is copied to the customer's clipboard. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/365756533_1756280054770140_7287687181799037425_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=WNAi-9JViF8Q7kNvwEHEhny&_nc_oc=AdnSNHABjc5VdZEVxl1iGGFMFOgbOrN6-bLhwrziS-yrf8uO4XJxjIHzAo9gE93AQas&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfgP1k4fKrLQ_Bsg-85R9h5HgST_rFK8InP0UfMT1Kh8QA&oe=69407A25) |
| Media card carousel templates [Media card carousel templates](/docs/whatsapp/business-management-api/message-templates/media-card-carousel-templates) allow you to send a single text message accompanied by a set of up to 10 media cards in a horizontally scrollable view. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/461961248_1048610163180196_3907313698557856900_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=vdPyjxZ_Hf4Q7kNvwFc491T&_nc_oc=Adkb1HaKttZJHWyBSISfY3SkODMhkTO5r7eKx2-MKkx1W_2O1kckKvqxsnS_82QtJWM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfiR9RFm2l_yxSYieEItEkcBlyPtUZstbxntH8Tawv4tcw&oe=69407B3C) |
| Call permission request templates [Call permission request templates](/docs/whatsapp/business-management-api/message-templates/call-permission-request-message-template) allow your business to call your customers outside of the customer service window. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/556555685_1517571612922347_1402127790412272783_n.webp?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=8eQPZFgMV-MQ7kNvwEVQ1Vm&_nc_oc=Adly-KWJI8r0loJvAuZVCOdL-AE5klWq8ZQzUgwT0Xr2FpLO5DUkdbS11RDUXbuFon8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_Afhxg3MP7D_eehYQtyKzEkKPJO6y4kX0sanB7PrBwf6zSw&oe=6940785A) |
| Limited-time offer templates [Limited-time offer templates](/docs/whatsapp/business-management-api/message-templates/limited-time-offer-templates) allow you to display expiration dates and running countdown timers for offer codes in template messages, making it easy for you to communicate time-bound offers and drive customer engagement. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/385485492_1044097420371007_6435130166952753459_n.png?stp=dst-webp&_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=brr9Mr1oS58Q7kNvwHwLSvz&_nc_oc=Adl0Ts95CC33OvIoM4ZZrc0i6YvoXgqeC7hN-yxiroYJq6tOfJOIoajJFfoClTZstDo&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfjqSUCavkCMGnZoUasrjnua2a75CtG2CIM9Nd7CLIfWUA&oe=6940543F) |
| Multi-product message templates [Multi-product message templates](/docs/whatsapp/business-management-api/message-templates/mpm-templates) allow you to showcase up to 30 products from your ecommerce catalog, organized in up to 10 sections, in a single message. | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/345336924_1476472873159435_9050004394387774321_n.png?stp=dst-webp&_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=Bo6oPwvRcMkQ7kNvwFLBFAZ&_nc_oc=AdkQpIg3ri3h0pVQ7hqFGgU9U7i85Grx4KI74Exz3Za-QrQqRlawbHZR2UNYB6fAZTM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_Afg8d51ReEMPFll2l6L5DqwAeGODxqkOIOXpGRuHTqKnOw&oe=69407DDC) |
| Product card carousel templates [Product card carousel templates](/docs/whatsapp/business-management-api/message-templates/product-card-carousel-templates) allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view: | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456451243_832660229062364_6760679807399209749_n.png?stp=dst-webp&_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=GkdwnchPbQAQ7kNvwHBZYI1&_nc_oc=AdmshxeXTyeai1hJ-4SusQbZW95EgTRBmK46Lzid8xdcxE43Xxs_cwBE7ltABsPe7Os&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfjzOG0OGARtpXlepOI2fIlm8uPdPAp_woWnRB3jQetQ6Q&oe=69406223) |
| Single-product message templates [Single-product message templates](/docs/whatsapp/business-management-api/message-templates/spm-templates) allow you to send a single text message accompanied by a set of up to 10 product cards in a horizontally scrollable view: | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456611074_369667709517740_8197750041061962345_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=PeO2wueboKsQ7kNvwEwPNnM&_nc_oc=AdlruGS2r-Hd3Slb7HKmiVOrzVEw_p1GYKHgWgFa3995Cf--MuNsOj7q-dDFcWzEg3U&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfgoHL1ix4d6z1eGWCBEkBiu_MZEEk7RFGgCXVB3Vb870Q&oe=6940538A) |

## Per-user marketing template message limits

WhatsApp may limit the number of marketing template messages a person receives from any business in a given period of time, starting with delivering fewer marketing conversations to those users who are less likely to engage with them. In most WhatsApp markets, this is determined based on a number of factors, including a dynamic view of an individual’s marketing message read rate.

Refer to [per-user marketing template message limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits) document for more information.

## User preferences for marketing messages

WhatsApp provides a setting, **Offers and announcements**, that allows WhatsApp users to indicate their interest level in marketing messages sent from your business, and to stop or resume delivery of marketing messages from your business entirely.

|  |  |  |  |
| --- | --- | --- | --- |
|  | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/499661558_686750450817076_8407823728923343264_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=_KzDfibeA2oQ7kNvwEqr4th&_nc_oc=Adk0pN9iVR2I-SymtXubtGn5KwSm45z_XArxe6LAiD7nl8sv0BK76ObgUUW_L77jR08&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_Afibb5XIsG8E6Ay-zhCjPlD3FzHIiw1mFgd6BhG3g_zgWg&oe=69407438) | ![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/497928479_674388312073388_4498328545588580050_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=R_gquoKe0x8Q7kNvwHqbwN-&_nc_oc=AdlF8lqGnKSvSXubf7gLhd9yz46_yqinX_Dw2kRVK9UW_YWYvqbhFp54U04RvlKEo20&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=mYTX6b65u9extRa6jpTwtA&oh=00_AfhcmW0lgHroTRta3stV9-aV3oEv_1kQyTONh2eMBmEs8g&oe=6940698D) |  |

### Interested/Not Interested feedback

WhatsApp users can use the **Offers and announcements** setting to indicate how interested they are in receiving marketing template messages from your business.

If a user chooses **Not interested**, it can affect [per-user marketing template messaging limits](/docs/whatsapp/business-management-api/message-templates/template-messaging-limits) between you and the user. Choosing this option also displays the second modal, which gives the user the option to stop delivery of marketing messages from your business.

### Stop/Resume controls

WhatsApp users can use the **Offers and announcements** setting to stop or resume delivery of marketing template messages from your business.

If you attempt to send a marketing template to a WhatsApp user who has stopped marketing template messages from your business, the API will process the request but not send the message. Instead, the API will trigger a [status messages webhook](/docs/whatsapp/cloud-api/webhooks/reference/messages/status) with:

* `status` set to `failed`,
* `code` set to `131050`,
* `title` set to `Unable to deliver the message. This recipient has chosen to stop receiving marketing messages on WhatsApp from your business`

To be notified whenever a WhatsApp user stops or resumes delivery of marketing template messages from your business, subscribe to the [user\_preferences webhook](/docs/whatsapp/cloud-api/webhooks/reference/user_preferences) webhook.

## For accounts linked with WhatsApp Business app (aka "Coexistence")

To improve the experience for WhatsApp Business Users, marketing messages sent to business customers will not bump chat threads to the top of the inbox. These messages will still be delivered and visible to business customers, but the thread will only move to the top if the customer responds.

Note: This feature is currently limited and not generally available (GA) to all users.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Marketing templates](#marketing-templates)

[Custom templates](#custom-templates)

[Specialty templates](#specialty-templates)

[Catalog templates](#catalog-templates)

[Coupon code templates](#coupon-code-templates)

[Media card carousel templates](#media-card-carousel-templates)

[Call permission request templates](#call-permission-request-templates)

[Limited-time offer templates](#limited-time-offer-templates)

[Multi-product message templates](#multi-product-message-templates)

[Product card carousel templates](#product-card-carousel-templates)

[Single-product message templates](#single-product-message-templates)

[Per-user marketing template message limits](#per-user-marketing-template-message-limits)

[User preferences for marketing messages](#user-preferences-for-marketing-messages)

[Interested/Not Interested feedback](#interested-not-interested-feedback)

[Stop/Resume controls](#stop-resume-controls)

[For accounts linked with WhatsApp Business app (aka "Coexistence")](#for-accounts-linked-with-whatsapp-business-app--aka--coexistence--)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=U3F0njTuim12Z8HlDgfjeg&oh=00_Afgq6V-EzFfYdLAkDguVHlbYtSZU_SIQJUAL1IeFAnab0g&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=U3F0njTuim12Z8HlDgfjeg&oh=00_AfjPpt7lHxzpsJQ5SfaEHON2uYvN1RwTt_Ez4qmm7Hq8Hw&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=U3F0njTuim12Z8HlDgfjeg&oh=00_AfjCh2S6AnOMsB7_pApkXL2x4v_JfLuAc9lQVx8WAbEQ9Q&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=U3F0njTuim12Z8HlDgfjeg&oh=00_Afis2pEJsbmhjSgR8t5G_Cj5GzGVHT0be3OUwnzv6kGcKw&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=U3F0njTuim12Z8HlDgfjeg&oh=00_Afi6PR8l9NrD4E1aQjx_mNiZhnXRIl19alq2_j_ABA16-w&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT39RREHmarexpIfKW8F2L7ZpCNyKxXtSxztZKXdp4qqrc2hlV7wXN2uHiTgUjXMzIOA_zLSklXTTmYxIJyayOnpukFEJZBNv0d8DlAzlcQlug2JdeOHOWybYhj9Bdwdk5uflqJ8aoS-5nJMWhey8Q)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)