![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fgroups%2Fgetting-started%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Grupos](/docs/whatsapp/cloud-api/groups)[Get Started](/docs/whatsapp/cloud-api/groups/getting-started)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)

  + [Get Started](/docs/whatsapp/cloud-api/groups/getting-started)
  + [Group Management](/docs/whatsapp/cloud-api/groups/reference)
  + [Group Messaging](/docs/whatsapp/cloud-api/groups/groups-messaging)
  + [Webhooks](/docs/whatsapp/cloud-api/groups/webhooks)
  + [Error Codes](/docs/whatsapp/cloud-api/groups/error-codes)
  + [Pricing](/docs/whatsapp/cloud-api/groups/pricing)
  + [FAQ](/docs/whatsapp/cloud-api/groups/faq)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Get started with Groups API](#get-started-with-groups-api)

[Overview](#overview)

[How to start using groups](#how-to-start-using-groups)

[Prerequisites](#prerequisites)

[Step 2: Create a group](#step-2--create-a-group)

[Step 3: Invite WhatsApp users to the group](#step-3--invite-whatsapp-users-to-the-group)

[Step 4: Send and receive messages](#step-4--send-and-receive-messages)

[Features](#features)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Get started with Groups API

**Eligibility for Groups API**

To qualify for groups features, your business must meet the following requirement:

* Have a messaging limit of at least 100,000 business-initiated conversations in a rolling 24-hour period
* Be an [Official Business Account (OBA)](https://developers.facebook.com/docs/whatsapp/official-business-accounts)

[Learn more about Quality Ratings and Messaging Limits](https://developers.facebook.com/docs/whatsapp/messaging-limits/)

## Overview

Groups on are invite-only, meaning that potential group participants are ultimately in control of wether they want to join the group or not.

When you create a group, a unique invite link that is generated which you can share to potential group participants. This link includes information about the group, enabling users to make an informed decision about wether or not they want to join the group.

Once a user joins the group, a webhook is triggered, signaling that you are now eligible to send messages to the group.

For a complete overview of available features, see the [Groups API Features](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/getting-started#features) below.

## How to start using groups

### Prerequisites

Before you get started with the Groups API, ensure that:

1. Your business number is in use with Cloud API (not the WhatsApp Business app).
2. Your webhook server is set up for use with Cloud API.
3. Your app is subscribed to the following groups webhook fields:
   * `group_lifecycle_update`
   * `group_participants_update`
   * `group_settings_update`
   * `group_status_update`
4. Your app is subscribed to the WhatsApp Business Account of your business phone number.
5. Your app has the `whatsapp_business_messaging` permission for the business number.

### Step 2: Create a group

Use the [Create Group endpoint](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/reference#create-group) to create a group, providing a subject and an optional description. Once a group has been successfully created, a [`group_lifecycle_update` webhook for successful group creation](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/webhooks#group-create-succeed) will be returned. This webhook will include a `invite_link` field with the invite link that you can now share with potential group participants.

### Step 3: Invite WhatsApp users to the group

#### 3.1 Add a group invite link template in [Template Library](https://business.facebook.com/wa/manage/template-library) to your account templates:

1. Navigate to [Template Library](https://business.facebook.com/wa/manage/template-library)
2. On the left, click the **Group invite link** dropdown, then click the **Group invite upon request** checkbox.
3. Select the template you want to use, give it a name, and click **Submit**

#### 3.2 Send the invite link to potential group participants

Once the template has been approved, use the template to invite members to the group using the invite link provided in the webhook from Step 2.

You can follow the instructions in the [Send Group Invite Link Template Message reference](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/reference#send-group-invite-link-template-message) to send the invite link with the template you just added to your account.

#### 3.3 Notification of when participants join the group

When a participant joins, a [`group_participants_update` webhook for a group participant joining webhook](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/webhooks#group-participants-update-webhook) will be triggered.

### Step 4: Send and receive messages

You can now use the [Cloud API send message endpoint](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/groups-messaging#send-group-message) to send messages to the group.

[Sent, delivered, and read status webhooks](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/webhooks#group-message-status-webhooks) will be triggered when there are updates in the group. Replies from participants will also trigger webhooks.

[Learn more about how to send and receive group messages](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/groups-messaging)

## Features

To learn more about all the features available in groups:

* Visit the [Group Management reference](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/reference/) to learn more about features available for managing groups.
* Visit the [Group Messaging reference](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/groups-messaging) to understand sending, receiving, and other messaging functions in groups.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Get started with Groups API](#get-started-with-groups-api)

[Overview](#overview)

[How to start using groups](#how-to-start-using-groups)

[Prerequisites](#prerequisites)

[Step 2: Create a group](#step-2--create-a-group)

[Step 3: Invite WhatsApp users to the group](#step-3--invite-whatsapp-users-to-the-group)

[Step 4: Send and receive messages](#step-4--send-and-receive-messages)

[Features](#features)

---

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHTryHJ&_nc_oc=Admy7GpnqwRB2yrV0K26R1ruyRzbFEMRIIBbpRk3E9Zarv1fHentEg_yHWtQS2xgIBg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfiQdmpkOZli1q5tN7I1yPuIxDOB5VPykdoif4kyA-Nrdw&oe=6940632C)

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwH57swG&_nc_oc=AdmAqBAGvpcpumYIfT0h6rR9U77Nz_vmeCCTFGNh9aLARTf2sdGzPrcUJq_WrE7YRK4&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfjDxa5cV4iu-mURUOtAOpLoTJyOe_XE4mcBTSjkM4vg2w&oe=69407F22)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwElAVdy&_nc_oc=Adl4CfQs2tjJaJxxfKSdK1GytHHQDxZiA0SzUTnMpu0RCc5ZzXbl-owuYi0BHtN3HwM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AficRRL4N3f1TVhdmBUKVZ6Ska30w17QRUFDXRxLhr00Jw&oe=69407B8E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1IezXVujnkCsMiiwX3fMV_mZtz1vsyOWieMiUIWD03j7C-dsqZFzyqXTt4buMw1SrXSkXHnGWVfklqTNS_ZXgrfD9ba7nZB5_VMArdt33dRa7mr5Sed2XNTrH24cM426SX-lPtQhU2f3r6mjPO9Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwFyVchK&_nc_oc=Adn24jR9avCJri9rb4xV6WHOmSE2xAabhA5SPU9df_1bQBXH841bb0qD0tklwIM7Ta0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfhaYhvXz8rJyuUdFLD6rbLuKm--2yjCL4Io2sIR7vvpsQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT16W4KO9H8JLEQ9dwxh_cn5Jii2WUPt6CPfZvzxZYNxBQPFz7SAAL7g9fePIWhvZQSUtKv64CLJpq5yquqIeYDvgBdPM2b4be7LFuwF5DfnnsO_X7iV4dPur1A-FluwzlzuWOpyksRpMrKO5AO3WC1RTkIGfIvNK1Q)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwG2RjRe&_nc_oc=Adlnyq_S62cXawdO_hSxzSAlCrv3ynvKQZDhvtZQFNaWhW_nD48_6gV_GK1r1LDCpsk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfiXaEdZXOgDBrk98XULTsdp5BL7SMHf-L5puCfAxLJ-8g&oe=694080EC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3OoTql24vFFZQcx__ZA_xKdgtNe6VQfKn1Ka9MS9i_jA_D3iapLsyznj5Xv9DXfw__blMmOaKOIz1oP4EBxJmByEMPa4zdLf79ZsF9XgTG--dzVfOy0YoQFT2wXAyMemzv1HP-UZBuyeS3Hx8Mtg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwEguXQl&_nc_oc=AdmDmwQKNjLIRoko1ZMTYMX6KY4m5nEXZFxVWUblwV08Zse4xdDoyq9pQ4nrrw6KzYM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_Afjx9DL4MjgEYlqGrZTadqPO7206Wls2Qv1aisWF1w7XNA&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT3lbAZxuo7mlzsmqxpgD8nftbskl2p8bgc-g67Esr_fFvsLcFFyjRr5Tgc4vdfP14wcF7qx4lStYvW8CyxjY6s52JeFmQmqiwCQoUK51QG8jgzvAhZudes_8Zga5Ag61xZoJVXXMz25SZbI5P_9gw)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT19C7Lb6MaY_0ae3a3gCt7IaGOsBlqz5TeQMHm0X-stXSREkD_aC2z2eAXAnJfw_KNupLKhPT1A9SYWCW8aIMEsG76ueeRyVERSL338u86OrcPfpwwIxrq2fvZ3sdC7Zq1bYFtZKrKVc3jTo5_88g)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2ik-YObhjPD_AaqL78Zmcc6_J7zseH9IaRWqS4a34XwScGChFeENGWpM-XnFfP031j59y0N4GUdAjzixhdprtBRDpR2mK_lHpsjupl0fvpTGoCSY7SnZCEhJ-cuydUBP05GIZLU8fXpY6ecjSypg)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwGUWsXR&_nc_oc=AdnkdIwdyYL2p27S4pcMUluaDHncOtxukTwj8FqfTZknw4_XgIgh5cPl-QzSzp7OMCU&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfjUe89RtffUcCiUFqqpJzTr_22qtH1R-1fORuamwSF8Eg&oe=69407B2F)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGsDBGI&_nc_oc=AdlWVflpA2urZdS4m87QYejj6r6uaqiXFWCIwPFWxzloM-2y0q6m688lRdiYSkdwh1A&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfgEpAJEYyEmFgP0Th5G_Ey3osktATLIZLhGjLQpHLujvw&oe=694086B5)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0zoMyHZ6S4JNMzWsk-uJl5HbRgyrd-L37xcq9lS_uX91OhxhXfPSICdxKFQWOmFyFNJkx_V2K32gK8sKuDECMJBQ6de9G58uXoRRD1iCYWrzHycSMSJuHfa0vYyvRpe2C0pW64uJfqZZRXa1X1sg)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwHRipk7&_nc_oc=Adli-wVDrkDQa22mpmVUODQn1mXIqV_zQB6dKGNYV6RBgcwlDqcyn7qOYPrYym0QVGA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfiXEuHFP7m0o0Cj1hVK2BNget4k6HTwxfNg1luP91NTXw&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT3JSJAtT5K1kB7fKvKB47CQSxVkhDPFdWn1R1y1XAxToIh3pSM1fGJXT4-nGX16kJgnzF54_BjW3BPHZeTPSAJRKuuAdAHEyRnQ9C2yJmeGLyMh8R_rHUEJvQi49GXOiQU93JXInAPnPxQyBtPEDw)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFhV88c&_nc_oc=Adnm-v0eNCQgUTK7hMvDLYzhR3P3rpgTrg1sZ0rUtSnxNTsGDsCGP0_GKhQS1oTO-RQ&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfjBlD-toI-95SUlgtzJsgsayMkK8oVdScDGOkbySY7WUA&oe=69408A06)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2vHhW6eL9Eh3ZnFSpzJ8cABdxYae4Z27V1bHfUHwL-mhPE_RxrQhzC_X1zKS5-7KVWL64kM99lPy8k-uGB3f67I59t-cetKF8tfxNK67Sxe71krT-4W5vSWd7k12OVmZ0ZZQVQyvts2x3qpGwlpA)[![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwFs0vVn&_nc_oc=AdnlQJBeilJ3nDjXi0hSw3jetsPF4W8H4GBJfUXEEu0uulgD2OpFpaRd65VlX_SOGeg&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=G0fSyzI6OqLQMdLbNhQ8TQ&oh=00_AfjQCpJoPef5hmTVLZEtrbTkORfOB6wd-Pxpoh4Ov6tBCg&oe=694071D4)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2lldlo-SjzZJinM0UoQZOt8MELlZ8xKE6Bh3igJa2HyhHCNoxsuRIxg4neC9r6SOOkqu31YdsCa30dCkisFbCTX_rqXTgRK1MnydRkldEawEKBolafCaHgsKxRSMcfctNJcU36PyKfyEhfXiwKpw)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0MbWWFXlwdKFHg3XhNq9zFl3fWK4Qi6pmvAd6lnFRWvud02WdFlCWjgHIth3hdIE1zuRhQuqRJuc7gusSfV5ZBhdCkPhigeaNaoVvEbK1MqYmSjls9qZLP5Tr3ahQAyfUYAoph-62v9J_PZwS3qA)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)