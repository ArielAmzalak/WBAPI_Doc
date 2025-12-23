![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Flink-previews%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Prévias de links](/docs/whatsapp/link-previews)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)
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

[Prévias de links](#pr-vias-de-links)

[Começar](#come-ar)

[Como fazer a verificação?](#como-fazer-a-verifica--o-)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Prévias de links

O WhatsApp é compatível com prévias de links enviados em conversas ou compartilhados no status. Sempre que possível, o WhatsApp tentará gerar uma prévia do link para melhorar a experiência do usuário. Para habilitar essa experiência, o WhatsApp precisa que os proprietários de links definam propriedades otimizadas especificamente para ele. Se esses requisitos não forem atendidos, não será possível ver uma prévia do link.

![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/316961531_1509723012881470_8719776711697314858_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=2dBwRS9N6jwQ7kNvwEwo2vy&_nc_oc=Adm7wlo763U60asMgEuxDL1-IJAwMobXDtlhXx2flGgV9snXsX3nxllj7mrEdG3wVFA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=9vDIrAk4YfvgqxwdwH9kdg&oh=00_Afi0vKpMRx4SAGgatjl6LwSn5gAlvzJjTPs7LG-9B4bJWA&oe=694074E4)![](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/316956074_903853424360664_8885274580316527555_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=WJS_3j7nB2oQ7kNvwFBE0G8&_nc_oc=AdkGA17pi1KWQtIRSX0Z8GxThrmTJxPJyJ-OJB3cTEVru4moRuGm1hM65541FiB-pQ8&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=9vDIrAk4YfvgqxwdwH9kdg&oh=00_AfjnlPpxiA4qyO6BnPDvrk2uU1Xi0qbszr0_RXxCrpG_Gg&oe=694058AF)

## Começar

Para começar a usar as prévias de links, é preciso adicionar marcações HTML à seção HEAD da página.

```
<head> <meta property="og:title" content=”WhatsApp"/> <meta property="og:description" content="Simple. Secure. Reliable messaging."/><meta property="og:url" content="https://whatsapp.com"/> <meta property="og:image"content="https://static.whatsapp.net/rsrc.php/ym/r/36B424nhiL4.svg"/> </head>
```

O `<head>` que contém as marcações HTML deve aparecer dentro dos primeiros 300 KB do HTML. O HTML completo não precisa se encaixar em 300 KB.

As marcações `<og:title>`, `<og:description>` e `<og:url>` devem ficar dentro da tag `<head>`. Elas não podem estar vazias.

A marcação `<og:title>` representa o título do conteúdo sem nenhuma indicação de marca. O WhatsApp exibirá esse texto na cor principal, em negrito e no máximo em duas linhas.

A marcação `<og:description>` representa a descrição do conteúdo. O WhatsApp exibirá o texto em um tamanho menor que o título e com a cor de texto secundária. O limite é de até duas linhas e até 80 caracteres.

A marcação `<og:url>` representa a URL canônica da página. A URL deve ser a não decorada, sem variáveis de sessão, parâmetros de identificação do usuário nem contadores.

A marcação `<og:image>` é uma URL absoluta para uma imagem usada como miniatura da prévia do link. A imagem deve ter menos de 600 KB. A imagem deve ter 300 px ou mais de largura com taxa de proporção de 4:1 largura/altura ou menos.

O WhatsApp fará o possível para mostrar prévias de links, por exemplo, flexibilizando requisitos, procurando outras marcações HTML e revertendo para pequenas prévias de links. Porém, não conte com isso. Não há garantia de que funcionará (e continuará funcionando).

O WhatsApp faz o crawl da página da web por meio de uma solicitação HTTP GET.

A solicitação terá o cabeçalho `User-Agent` definido como `WhatsApp/2.x.x.x A|I|N`, em que `x` são as versões numéricas principais/secundárias do WhatsApp, e `A|I|N` é para Android, iOS e web, respectivamente. Alguns exemplos de valores de cabeçalho `User-Agent` válidos: `WhatsApp/2.22.20.72 A`, `WhatsApp/2.22.19.78 I`, `WhatsApp/2.2236.3 N`. Os proprietários de sites podem identificar essas solicitações recebidas e personalizar o conteúdo (marcações e imagens) de maneira adequada.

A solicitação também terá o cabeçalho `Accept-Language` definido como o idioma selecionado pelo remetente, se houver. Alguns exemplos de valores de cabeçalho `Accept-Language` válidos são: `en`, `fr` e `de`. Do mesmo modo, os proprietários de sites podem personalizar o idioma do conteúdo. O idioma definido pelo destinatário também será visto por ele.

## Como fazer a verificação?

Comece escrevendo uma mensagem com o link para testar (não toque para enviar). Em nome do remetente, o WhatsApp rastreará essa URL e tentará gerar uma prévia do link.

Se a prévia não aparecer acima da caixa do editor após dez segundos, verifique se todos os requisitos mencionados foram atendidos. Caso contrário, prossiga com o envio da mensagem tocando no botão "enviar".

Se a prévia não aparecer no tamanho grande esperado, verifique se os requisitos de imagem mencionados acima foram atendidos. Caso contrário, as prévias de links estão funcionando conforme o esperado. Pronto!

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Prévias de links](#pr-vias-de-links)

[Começar](#come-ar)

[Como fazer a verificação?](#como-fazer-a-verifica--o-)

---

![Meta](https://static.xx.fbcdn.net/rsrc.php/y9/r/tL_v571NdZ0.svg)

[![Facebook](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425860105_925920989121941_6933048753023841367_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=TlXg3Yp0zhcQ7kNvwFlHuzj&_nc_oc=Adlth0zZy4oztItVbjww3S27F1gAAHaCOth97fGPhPKdhDYKwlVT8tmCq8SSN8prXs0&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Na4ohrKY1utT6UkP8k3Pdw&oh=00_AfgSF_tAFx9fYt3KBE5jV9PJiiOHDoQPjVauNJtX4i3PoQ&oe=692BF1E2)](https://www.facebook.com/MetaforDevelopers)[![Instagram](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425804778_757649995874129_6917476492193301523_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=9toEBb-pE2cQ7kNvwFNJCB6&_nc_oc=AdlHaJJqU9SjSKjxpIT908b6J1OETLKHPmwa6pzYH463NCg13I4b2rCvxBAcolz_Vhk&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Na4ohrKY1utT6UkP8k3Pdw&oh=00_AfhTMzN4jQ9dgG0MYyGFm0SP0phWJ-URpPDhvAFhM3LUOg&oe=692BDBF8)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[![X](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/426747931_385023204117867_5811151062540225287_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=LrCKBfrXotkQ7kNvwHXJ9-R&_nc_oc=AdmWcwXydGH4fE6_ze9n1TULXTqneYU3K5ygGtaVzyBRBnyw7qb8Og3cZksVt5ToizM&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Na4ohrKY1utT6UkP8k3Pdw&oh=00_Afh6SfUHveWOfNx6EMtcw1TVIwunyl0Csx65ayYO7cXPyw&oe=692BFA6A)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[![LinkedIn](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/467689750_1684384502343829_7561568713040200172_n.svg?_nc_cat=103&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=rvzDMDq8OpYQ7kNvwFpZJjN&_nc_oc=AdlO0K6valAr8yBXuSJtO6iJS0r0g9RzlDBTkzXUhIADbGXGnHLCUefEiPT_tUXMtrY&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Na4ohrKY1utT6UkP8k3Pdw&oh=00_AfgJXwE0dDe6v0GEFWbez2Pn6rfOykTsVuQriiC3SQegIA&oe=692C09FE)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[![YouTube](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.2365-6/425519002_724756916408357_7491658959807896355_n.svg?_nc_cat=1&ccb=1-7&_nc_sid=aa6a2f&_nc_ohc=cSxQkBtFWXEQ7kNvwHMlhmF&_nc_oc=Adnl0siywGpWBIefbDUneekkB0PXKN416o7GLrNM6CqMMpaf5WBi3HQd8koViWw8GpI&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=Na4ohrKY1utT6UkP8k3Pdw&oh=00_Afj506CGSgMYTgpOroWQUZY6WoZIlyiMnXvItywU62KlaQ&oe=692BF51F)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA) [Tecnologias sociais](/social-technologies/)

---

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[Blog](/blog/)[Casos de sucesso](/success-stories/)

---

Suporte

[Suporte ao desenvolvedor](/support/)[Ferramenta de bug](/support/bugs/)[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)[Relatar um incidente](/incident/report/)

---

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)[Termos da plataforma](/terms/dfc_platform_terms/)[Políticas do Desenvolvedor](/devpolicy/)[Política de Privacidade](https://www.facebook.com/about/privacy)[Cookies](https://www.facebook.com/help/cookies)

---

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)[Carreiras](https://www.facebook.com/careers)

---

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Desenvolva com a Meta

[IA](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fai%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Meta Horizon](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fhorizon%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Tecnologias sociais](/social-technologies/)

Notícias

[Meta for Developers](https://l.facebook.com/l.php?u=https%3A%2F%2Fdevelopers.meta.com%2Fblog%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Blog](/blog/)

[Casos de sucesso](/success-stories/)

Suporte

[Suporte ao desenvolvedor](/support/)

[Ferramenta de bug](/support/bugs/)

[Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Fórum da Comunidade de Desenvolvedores](https://www.facebook.com/groups/fbdevelopers/)

[Relatar um incidente](/incident/report/)

Quem somos

[Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT0H3YOPDBQU90U2n4XQuXkjaOqbivRgVjzC7-dTtzUJwiO3Wcsl6ywh2txm0zgEpmnR-a4rilWVqQkGMyk_P7OuDmcSSakN6_kllM4PuzzV7EnfJ6yyBhf7mB4aCUSCioL3TBbjGXBF4BN1hkmKLA)

[Carreiras](https://www.facebook.com/careers)

Termos e políticas

[Iniciativas de plataforma responsável](/products/responsible-platform-initiatives/)

[Termos da plataforma](/terms/dfc_platform_terms/)

[Políticas do Desenvolvedor](/devpolicy/)

[Política de Privacidade](https://www.facebook.com/about/privacy)

[Cookies](https://www.facebook.com/help/cookies)

Português (Brasil)