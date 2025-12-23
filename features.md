![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fmarketing-messages-api-for-whatsapp%2Ffeatures%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)[Features](/docs/whatsapp/marketing-messages-api-for-whatsapp/features)

[Marketing Messages API for WhatsApp](/docs/whatsapp/marketing-messages-api-for-whatsapp)

* [Get started](/docs/whatsapp/marketing-messages-api-for-whatsapp/get-started)
* [Guides](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides)
* [Features](/docs/whatsapp/marketing-messages-api-for-whatsapp/features)
* [Onboard business customers](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers)
* [Pricing](/docs/whatsapp/marketing-messages-api-for-whatsapp/mm-api-pricing)
* [Support](/docs/whatsapp/marketing-messages-api-for-whatsapp/support)
* [Changelog](/docs/whatsapp/marketing-messages-api-for-whatsapp/changelog)

Nesta Página

[Features](#features)

[Optimization features](#optimization-features)

[Marketing message formats](#marketing-message-formats)

[Guidance](#guidance)

[Metrics](#metrics)

[Enterprise, Security 5 & Compliance Features](#enterprise--security-5---compliance-features)

[Onboarding](#onboarding)

[Footnotes](#footnotes)

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

# Features

Marketing Messages API for WhatsApp offers added features that are not available on Cloud API, such as performance benchmarks and recommendations, time-to-live, and automated creative optimizations (in testing).

For more detail, see the comparison tables below.

## Optimization features

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Quality-based delivery:** Improving deliveries of high engagement messages. | **Yes:** Marketing Messages API for WhatsApp factors if a message is high engagement into delivery decisions, offering up to 9% higher deliveries vs. Cloud API\*. High engagement marketing messages refers to messages that are expected by users, relevant, and timely, and therefore more likely to be read and clicked. | **No:** Message quality does not factor into per-user marketing message limits. No ability to increase delivery for high engagement messages. |
| **Automated creative optimizations:** Automatic enhancements to creative to increase message performance. | **Yes (pilot):** Automatically enhance the visual appeal and engagement of marketing template messages. See full list of capabilities [here](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages#automatic-creative-optimizations). | **No** |

## Marketing message formats

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Animated Image (GIF) Header:** Marketing message templates support a GIF [media type in the header.](/docs/whatsapp/business-management-api/message-templates/components#media-headers) | **Yes** | **No** |
| **Android App Deep Links:** [Links](/docs/whatsapp/marketing-messages-api-for-whatsapp/guides/deep-links) that directly open up the app on a customer's phone. | **Yes** | **No** |
| **Customizable Message Validity Periods:** Set a [time-to-live for messages](/docs/whatsapp/marketing-messages-api-for-whatsapp/sending-messages#create-marketing-templates) that should expire if they cannot be delivered soon enough. | **Yes:** TTL can range from 12 hours to 30 days. | **Limited:** Only supports Authentication and Utility messages. |
| **Basic marketing message formats:** [Media, carousel, product catalog, flow, interactive list, interactive reply, etc.](/docs/whatsapp/business-management-api/message-templates/marketing-templates) | **Yes** | **Yes** |

## Guidance

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Benchmarks:** Comparison of read and click rates versus similar templates from businesses in your region. | **Yes** | **No** |
| **Recommendations:** Evidence-based recommendations to improve the performance of your template. | **Yes** | **No** |

## Metrics

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Conversion metrics:** Conversions on Web and App. | **Yes:** [Measure marketing messages](https://developers.facebook.com/docs/whatsapp/marketing-messages-api-for-whatsapp/measuring-conversion#measure-app-conversions-with-meta-sdk-or-app-events-api) leading users to perform app events, such as 'Add to Cart', 'Checkout Initiated', 'Purchase'. | **No** |
| **Cost metrics:** [Spend per Template, Cost per click, Cost per delivery.](https://developers.facebook.com/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics) | **Yes** | **Yes** |
| **Basic metrics:** [Sent, delivered, read, clicked, errors.](https://developers.facebook.com/docs/whatsapp/marketing-messages-api-for-whatsapp/viewing-metrics) | **Yes** | **Yes** |

## Enterprise, Security 5 & Compliance Features

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Local Storage Support:** Phone numbers with [Local Storage enabled.](/docs/whatsapp/cloud-api/overview/local-storage/) | **Yes** | **Yes** |
| **Compliance certification:** Compliance resources available on the [Business Messaging Compliance Center](https://www.facebook.com/business/business-messaging/compliance). | **Yes:** Certification for LGPD, GDPR, System Audit Report, SOC, ISO27001. | **Yes:** Certification for LGPD, GDPR, System Audit Report, SOC, ISO27001. |
| **Automatic throughput upgrades:** Automatic upgrades (and webhook notifications) to a phone number’s [messaging throughput](/docs/whatsapp/cloud-api/overview/#higher-throughput). | **Yes** | **Yes** |
| **Real-time service status updates:** [Uptime and availability metrics](/docs/whatsapp/support-api-status-page) are live on [metastatus.com](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2Fwhatsapp-business-api%3Ffbclid%3DIwY2xjawM2uLNleHRuA2FlbQIxMQBicmlkETFPWE5PUldSeE95a2tuMnA1AR4r-Af63nidsmVRDdEJ4WtriGpxdlenOA60_uzhuqXHr06lE0-d2S9pnJm_Ww_aem_WtrDEZEwN2EZflsD4vmusQ&h=AT3IcWvYPAa2WH5pTfdcK0Z3od0XvnkQs2CEq9OmNHJYlo32ekZd39FeuczKjWp_9c_5TkZhFrTp7Nmut5VzL3j9ujuwYtFJdXqmgQ1YcUNq4TkCJ665lEb80tUcCzN_BU8MiP1dbSPLU_2zaCHhyw). | **Yes** | **Yes** |

## Onboarding

| Description | Marketing Messages API for WhatsApp (Supports Marketing) | Cloud API (Supports Auth, Utility, Service, Marketing) |
| --- | --- | --- |
| **Streamlined Onboarding:** [Onboard via Embedded Signup, Intent API, and Intent UI](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding). | **Yes** | **Limited:** Embedded signup only. |
| **Error Codes:** Graph API [error codes](/docs/whatsapp/cloud-api/support/error-codes/#marketing-messages-api-for-whatsapp-error-codes). | **Yes:** [Specific Marketing Messages API for WhatsApp error codes](/docs/whatsapp/cloud-api/support/error-codes/#marketing-messages-api-for-whatsapp-error-codes). | **Yes** |
| **Onboarding Status via API:** Granular [eligibility status data and error codes](/docs/whatsapp/marketing-messages-api-for-whatsapp/changelog#july-15--2025). | **Yes:** A [new eligibility status field](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboarding#eligibility-requirements) has been introduced to better report on the API onboarding status. | **Limited** |
| **Coexistence:** [Onboarding WhatsApp business app users.](/docs/whatsapp/marketing-messages-api-for-whatsapp/onboard-business-customers#onboard-whatsapp-business-app-users--aka--coexistence--) | **Yes** | **Yes** |

## Footnotes

1. \*AB test conducted with ~12 million delivered marketing messages sent by advertisers in India between 1st Jan 2025 to 31st Jan 2025. It compared Marketing Messages API for WhatsApp optimized delivery to standard CloudAPI delivery for high engagement messages only (i.e. more reads, clicks, etc.) and the analysis consisted of a t-test at 95% confidence.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Features](#features)

[Optimization features](#optimization-features)

[Marketing message formats](#marketing-message-formats)

[Guidance](#guidance)

[Metrics](#metrics)

[Enterprise, Security 5 & Compliance Features](#enterprise--security-5---compliance-features)

[Onboarding](#onboarding)

[Footnotes](#footnotes)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_Afjrj5TZ0-LoNO9Ttk0hKe_8UEhbhCTrJJEQ0oUDtz33Sg&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfjyjR0KnWODMnIAZ14gjq0BmRAUZI9hEmoho35AZPRb8g&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfgRDV_gRuKMsgH-AwnLKjDR3RE6Bg4AVZ6vUOhsgm-BBQ&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0lcAfUnAEk_1WdFsEqnqQs0R8UP9fl1nfupgIdBYkIAJN4iELzrwmFTej8LwMlK0LroHdAbMH2-LbZ-wUI9jBvk9M5l9dQsmBQ8-9Dde7jGCej0vBsl-dq78dYvJvZlGchIJLDQV9EtRPFAFdAJg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfjtzxEWMj52NRMuNwMhY12xGSJ83nWMKxuffGJ64kF0Ew&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0qZqIgtMJ2shmBL2SP6R60o97tebcAZJdy4UIuUTSeu2wUHLdUiby4QqfxIKw2-bXVzXoXFn7OSCV1B-kWsg0W2LfPxP_H93kugynkr1spmeiakY06b7N7kfHFuKQi-zShqGex9MqluJptfinF6w)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_Afg1jMc3OVp3SY7L5f8laSDeMLla750YFwWjWibWnZrAJw&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2wqcegeg-9WTCsrhzD_8jSjlXXlKd5yBx1jCbvfkXYackTDos1gyLIOSPeZRGjLvnYTO3CnZADJqIkTH1uYBpyU-UbNmVZV0xnxLXNgY0BBjlJCWniZahfHYxa5RCo3dg_w89qELGdN6EqXfk_7Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfhEX1Pzr1p0LOOd-XTKyFqxTe_i0OGzAKtH6okaod_KdQ&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT34d7IN-6ZpsagGRSsltMzGqdTEygh9BSFRUgP36k6HwWuDWlUFIef_ANKFoGyC7E2XZf6D2Kfyjb6KochTgPMgGOGxkF-UTTcYL2RVBPdFek2E2JbGENHpYxmS-5d1QGWPQnChZZ7DFazv9qZ82g)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3F9l7PJhglBW_qpT87lWoRAwUk1XB4y1NL9dmUU2knaOfDhRi_kMbmqh_vvy2gc5AvfNzV3EFnoqQd9vUzm78IG1t2WHgsF3CeNskkfE0ONU8qIueo_ps8dqkfKfDAHntvWgM8y9EmRVaOxiPjjA)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1GKciuVGxPHCP98m3iUJaJ8MqNnGMWiI56DuTTkMHh2_cav6ogKLRH29Rj2BQhqUT-wABI8mWXr74vhk-mU9evQbLCLByBxyXsf5R0UL9tyCUsn0b-lHHadR-8vHYC6tnVwB1vT6OsXM-8ITkENw)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfgYBjPnSznZHTS25DRRCFyii55mR5pcmHZ8mrafaSrwfQ&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfjhgMNcpVfDnUwFt4YgMxGaPdTvUGctu5g0-VbKbVb_xQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3qHGSpoTxZWvHGKIxUSJ64--L-LwqI9dc3gkO6Au_9B0sC5qCzftNH9kzgeioAivjstN54g8h9eHMnf7qVhHhE0KrNETZu33xSLin3ur7EGJC0jQ7Hwp7E-7qRKWSodNPoF3juUDHPwkOiNgHtN3TPdYqJmG204Wk)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfhYR3aLu2NikaK2l_OgDrW4nJ0c7FJ_jOqbPVAPl43VHQ&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1H65THCIayHXf390IWw5gXexG64XTL1qAf_5ODE3Ge69XHbPB3tK0F3mrYbYb8rRRYyOANqtRhbWizonl8fMdQL-KbUMPcfd_NtBsor4XsfPGAWboEroxFjbuAxgY8atrX3V1Ar_K0gO8M42JvlQ)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_Afjnx1JRVbEqBlAWF0UuHu8XqvrRBinmOqu3XdtHZjekvg&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1FH0QUVO8exu68mw9sVXcnMUpexosx-sGwPQrb2fmAYBaladAtJlrZ7F7qBWTdAceu75BmK8LKntwg9oOsz02zPmMIqbkh9SsL9eoNREPFJIQrhuDFQeh4uwkAwjkAvc7Nr8YAytdIVhfAcufQiw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=RrcZ2ryX-_9x6aGQNZDaEw&oh=00_AfgsA2rn_p-_LPhlF1dmulZPTi3SNbv5au4piKsJXvsADQ&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT33WZKtIkuH6c6R88Sz_gkGpMSYblq90Q1g2r_5XkRdG6tDIYWE7-BVOzVPaXsfddY02gwWS46b8cWMgyxWgBzd413L04a4QTvCD58zLDC3T4XOPFXp4pdtqXbi3KcYvPtGYPaJsiiNt4h0EuPbGA)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2tRj_wBuRYGGJTJWC-DbflA6-WUCWATxfL4zhXeaSH5yXBvJvjUY6qual90aW25lxvfa91Rn78SlV1NcUFdJsvyqsYnJrlSdCrMcpfKHMfK1gbPz2VtPmT-sgjFXHSI9fgGmMZjDSwJepIr2ic7g)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)