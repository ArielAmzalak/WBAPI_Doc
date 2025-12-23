![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fconversation-types%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Mensagens](/docs/whatsapp/conversation-types)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)
* [Descontinuação da API Local](/docs/whatsapp/on-premises/sunset)
* [Cloud vs On-Prem](/docs/whatsapp/cloud-vs-onprem)
* [Números de telefone](/docs/whatsapp/phone-numbers)
* [Mensagens](/docs/whatsapp/conversation-types)

  + [Diretrizes para modelo de mensagem](/docs/whatsapp/message-templates/guidelines)
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

[Mensagens](#mensagens)

[Confirmações de leitura](#confirma--es-de-leitura)

[Status de mensagens](#status-de-mensagens)

[Perguntas frequentes](#perguntas-frequentes)

# Mensagens

Este documento fornece uma visão geral sobre o funcionamento das mensagens na Plataforma do WhatsApp Business.

É possível enviar estes tipos de mensagem por meio da plataforma:

* **Mensagens de texto**
* **Mensagens de mídia** (mensagens com imagem, vídeo, áudio, documento e figurinha)
* **Mensagens com contato**
* **Mensagens de localização**
* **Mensagens interativas** (listas, botões Responder, bem como mensagens de produto único e multiproduto).
* **Modelos de mensagem**

Com os seguintes pontos de extremidade, é possível enviar uma mensagem de um número de telefone a um cliente:

* Ponto de extremidade [`/messages`](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) da API de Nuvem

## Confirmações de leitura

Você pode habilitar confirmações de leitura, e os clientes podem decidir se também querem enviá-las. Caso o cliente opte por não enviar confirmações de leitura, você verá somente se a mensagem foi entregue. Para saber mais, consulte estes recursos:

* API Local: [Marking Messages as Read](/docs/whatsapp/guides/mark-as-read#step-1--make-put-request-to--messages)
* API de Nuvem: [Marcar mensagens como lidas](/docs/whatsapp/cloud-api/guides/mark-message-as-read)

## Status de mensagens

Você receberá uma notificação sobre o status de cada mensagem que a sua empresa enviar. Na tabela abaixo, clique na seta na coluna da esquerda para ver o equivalente do app WhatsApp para cada status, se estiver disponível.

| Nome | Descrição |
| --- | --- |
| `deleted` | A mensagem enviada foi excluída pelo usuário. Depois de receber essa notificação, você precisa garantir que a mensagem seja excluída do seu sistema caso ela tenha sido baixada do servidor. |
| Equivalente do app WhatsApp | A mensagem é substituída no WhatsApp para dispositivos móveis por uma nota em que se lê "Esta mensagem foi excluída". |
| `delivered` | Uma mensagem enviada pela sua empresa foi entregue ao dispositivo do usuário. |
| Equivalente do app WhatsApp | Duas marcas de seleção |
| `failed` | O envio de uma mensagem da sua empresa falhou. O motivo da falha será incluído no retorno de chamada. Verifique a documentação sobre mensagens de erro para obter ajuda com a depuração:   * [Erros da API Local](/docs/whatsapp/api/errors) * [Códigos de erro](/docs/whatsapp/cloud-api/support/error-codes) e [solução de problemas](/docs/whatsapp/cloud-api/support/troubleshooting) da API de Nuvem |
| Equivalente do app WhatsApp | Triângulo de erro vermelho |
| `read` | Uma mensagem enviada pela sua empresa foi lida pelo usuário. As notificações de `read` estarão disponíveis somente para usuários que habilitaram os recibos de leitura. Para usuários que não tiverem essa opção habilitada, você receberá somente a notificação de `delivered` . |
| Equivalente do app WhatsApp | Duas marcas de seleção azuis |
| `sent` | Uma mensagem enviada pela empresa está em trânsito nos nossos sistemas.   Usuários da API Local: para receber notificações de mensagens `sent` defina `sent_status` como `true` nas [configurações do app](/docs/whatsapp/api/settings/app). A notificação de status `sent` é desabilitada por padrão. |
| Equivalente do app WhatsApp | Uma marca de seleção |
| `warning` | Uma mensagem enviada pela empresa contém um item de catálogo que não está disponível ou não existe. |

A ordem dessas notificações no seu app pode não refletir o momento real do status da mensagem. Se necessário, veja o registro de data e hora para determinar o momento.

## Perguntas frequentes

[É possível formatar mensagens?](#faq_1731118056945893)

Sim! O WhatsApp permite que você formate o texto selecionado na mensagem com negrito, itálico, tachado ou espaçamento uniforme.

[Link permanente](#faq_1731118056945893)

[Como devo proceder quando for necessário enviar mensagens de atendimento ao cliente após o período de 24h?](#faq_715120295540784)

Poderá haver casos em que você precisará de mais tempo para atender à solicitação de um cliente, e será necessário enviar uma resposta ao cliente após o período de 24h. Recomendamos criar modelos de mensagem para:

* enviar o resultado ao usuário ou
* solicitar uma resposta do usuário com o objetivo de ativar uma nova janela de atendimento ao cliente.

Em ambos os casos, adicione a maior quantidade possível de contexto ao modelo de mensagem. Por exemplo:

* “Olá, {{1}}! A respeito do problema que você relatou anteriormente, viemos informar que, infelizmente, {{2}}. Pedimos desculpas por qualquer inconveniência causada."
* Temos atualizações a respeito do seu ticket. Responda a esta mensagem se deseja continuar recebendo suporte.”

[Link permanente](#faq_715120295540784)

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Mensagens](#mensagens)

[Confirmações de leitura](#confirma--es-de-leitura)

[Status de mensagens](#status-de-mensagens)

[Perguntas frequentes](#perguntas-frequentes)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwELHXUv&_nc_oc=AdnQSB3tXDEx8Zr27rvr5QhJRbPbKlPwYPo_tbTKIkeX-Y0pKKpki9XMw22z-_siQGQ&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=_LrB_W5t-WRZ6IaH8oGw9A&oh=00_AfjXHb55Lv6f1znowWlsW08vjsXfJQ8njUIv6apS_FABEg&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwF1UM9E&_nc_oc=AdkIeTlaAdZP8jsEm7TarADX4yXJ2nMwI1valKegli_3z4L3HlL4VZ3RsrtpmkSUWVg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=_LrB_W5t-WRZ6IaH8oGw9A&oh=00_AfhFsUifdQniZJsvqnDr9rHPRtHWtVG6XAM6JCnnCdWzgg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[![X](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwGpCypP&_nc_oc=AdkflfsSSVx72lQ6-UyuXx6Qnr77-cDFaB0_m2zfILiP_og0p2VNmXuaX7Td9uggUsY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=_LrB_W5t-WRZ6IaH8oGw9A&oh=00_AfiWG2dlE0OWWH0mifB4kOJmE1IjTL026myy0D6joWrnRw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[![LinkedIn](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwEpc-zG&_nc_oc=AdmBZBgX0wX64r_0deWkrNm0sh9oMGn2h-E1bHAnRusY0nl5FN2qWlqDpq1gWJ2bmuI&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=_LrB_W5t-WRZ6IaH8oGw9A&oh=00_AfjVf24e4BzNCU4aq-MTJApB6fZwi-8X9AnQvjeUKcWUeA&oe=692BD1BE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[![YouTube](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwE4Ii11&_nc_oc=AdnaWdINQtK4QhGsGOwxbDkvd1TBd-VU9ErozOA3kMc6JnZdI5GmNG-_Pp7ra015wfc&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=_LrB_W5t-WRZ6IaH8oGw9A&oh=00_AfgIouM7jySx6lZ5VtIH1f4igs4Lk8BNo0asEWMk5SP_xw&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT1pVwrXhlnkvntwgoZ7dfWITEUPCko7XDFhqT-a2w3clVPM8wxplkzmOWN4QxythBvrMYT8tJqgrAUREBy9hW1MvzerYteRTXINkiRklzSnEi4TVapp4JraENraPxwvxbSH_AUd-xTw2ayTMeCgcw)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)