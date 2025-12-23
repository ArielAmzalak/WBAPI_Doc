+++
id = "link-previews"
title = "Previas de links"
summary = "O WhatsApp e compativel com previas de links enviados em conversas ou compartilhados no status."
source = "https://developers.facebook.com/docs/whatsapp/link-previews"
lang = "en"
tags = ["whatsapp-business-platform"]
+++
# Previas de links

O WhatsApp e compativel com previas de links enviados em conversas ou compartilhados no status. Sempre que possivel, o WhatsApp tentara gerar uma previa do link para melhorar a experiencia do usuario. Para habilitar essa experiencia, o WhatsApp precisa que os proprietarios de links definam propriedades otimizadas especificamente para ele. Se esses requisitos nao forem atendidos, nao sera possivel ver uma previa do link.

## Comecar

Para comecar a usar as previas de links, e preciso adicionar marcacoes HTML a secao HEAD da pagina.

```
<head> <meta property="og:title" content=WhatsApp"/> <meta property="og:description" content="Simple. Secure. Reliable messaging."/><meta property="og:url" content="https://whatsapp.com"/> <meta property="og:image"content="https://static.whatsapp.net/rsrc.php/ym/r/36B424nhiL4.svg"/> </head>
```

O `<head>` que contem as marcacoes HTML deve aparecer dentro dos primeiros 300 KB do HTML. O HTML completo nao precisa se encaixar em 300 KB.

As marcacoes `<og:title>`, `<og:description>` e `<og:url>` devem ficar dentro da tag `<head>`. Elas nao podem estar vazias.

A marcacao `<og:title>` representa o titulo do conteudo sem nenhuma indicacao de marca. O WhatsApp exibira esse texto na cor principal, em negrito e no maximo em duas linhas.

A marcacao `<og:description>` representa a descricao do conteudo. O WhatsApp exibira o texto em um tamanho menor que o titulo e com a cor de texto secundaria. O limite e de ate duas linhas e ate 80 caracteres.

A marcacao `<og:url>` representa a URL canonica da pagina. A URL deve ser a nao decorada, sem variaveis de sessao, parametros de identificacao do usuario nem contadores.

A marcacao `<og:image>` e uma URL absoluta para uma imagem usada como miniatura da previa do link. A imagem deve ter menos de 600 KB. A imagem deve ter 300 px ou mais de largura com taxa de proporcao de 4:1 largura/altura ou menos.

O WhatsApp fara o possivel para mostrar previas de links, por exemplo, flexibilizando requisitos, procurando outras marcacoes HTML e revertendo para pequenas previas de links. Porem, nao conte com isso. Nao ha garantia de que funcionara (e continuara funcionando).

O WhatsApp faz o crawl da pagina da web por meio de uma solicitacao HTTP GET.

A solicitacao tera o cabecalho `User-Agent` definido como `WhatsApp/2.x.x.x A|I|N`, em que `x` sao as versoes numericas principais/secundarias do WhatsApp, e `A|I|N` e para Android, iOS e web, respectivamente. Alguns exemplos de valores de cabecalho `User-Agent` validos: `WhatsApp/2.22.20.72 A`, `WhatsApp/2.22.19.78 I`, `WhatsApp/2.2236.3 N`. Os proprietarios de sites podem identificar essas solicitacoes recebidas e personalizar o conteudo (marcacoes e imagens) de maneira adequada.

A solicitacao tambem tera o cabecalho `Accept-Language` definido como o idioma selecionado pelo remetente, se houver. Alguns exemplos de valores de cabecalho `Accept-Language` validos sao: `en`, `fr` e `de`. Do mesmo modo, os proprietarios de sites podem personalizar o idioma do conteudo. O idioma definido pelo destinatario tambem sera visto por ele.

## Como fazer a verificacao?

Comece escrevendo uma mensagem com o link para testar (nao toque para enviar). Em nome do remetente, o WhatsApp rastreara essa URL e tentara gerar uma previa do link.

Se a previa nao aparecer acima da caixa do editor apos dez segundos, verifique se todos os requisitos mencionados foram atendidos. Caso contrario, prossiga com o envio da mensagem tocando no botao "enviar".

Se a previa nao aparecer no tamanho grande esperado, verifique se os requisitos de imagem mencionados acima foram atendidos. Caso contrario, as previas de links estao funcionando conforme o esperado. Pronto!
