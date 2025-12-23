+++
id = "send-messages"
title = "Mensagens"
summary = "Este documento fornece uma visao geral sobre o funcionamento das mensagens na Plataforma do WhatsApp Business."
source = "https://developers.facebook.com/docs/whatsapp/send-messages"
lang = "en"
tags = ["whatsapp-business-platform", "messaging"]
+++
# Mensagens

Este documento fornece uma visao geral sobre o funcionamento das mensagens na Plataforma do WhatsApp Business.

E possivel enviar estes tipos de mensagem por meio da plataforma:

* **Mensagens de texto**
* **Mensagens de midia** (mensagens com imagem, video, audio, documento e figurinha)
* **Mensagens com contato**
* **Mensagens de localizacao**
* **Mensagens interativas** (listas, botoes Responder, bem como mensagens de produto unico e multiproduto).
* **Modelos de mensagem**

Com os seguintes pontos de extremidade, e possivel enviar uma mensagem de um numero de telefone a um cliente:

* Ponto de extremidade [`/messages`](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/messages/) da API de Nuvem

## Confirmacoes de leitura

Voce pode habilitar confirmacoes de leitura, e os clientes podem decidir se tambem querem envia-las. Caso o cliente opte por nao enviar confirmacoes de leitura, voce vera somente se a mensagem foi entregue. Para saber mais, consulte estes recursos:

* API Local: [Marking Messages as Read](/docs/whatsapp/guides/mark-as-read#step-1--make-put-request-to--messages)
* API de Nuvem: [Marcar mensagens como lidas](/docs/whatsapp/cloud-api/guides/mark-message-as-read)

## Status de mensagens

Voce recebera uma notificacao sobre o status de cada mensagem que a sua empresa enviar. Na tabela abaixo, clique na seta na coluna da esquerda para ver o equivalente do app WhatsApp para cada status, se estiver disponivel.

| Nome | Descricao |
| --- | --- |
| `deleted` | A mensagem enviada foi excluida pelo usuario. Depois de receber essa notificacao, voce precisa garantir que a mensagem seja excluida do seu sistema caso ela tenha sido baixada do servidor. |
| Equivalente do app WhatsApp | A mensagem e substituida no WhatsApp para dispositivos moveis por uma nota em que se le "Esta mensagem foi excluida". |
| `delivered` | Uma mensagem enviada pela sua empresa foi entregue ao dispositivo do usuario. |
| Equivalente do app WhatsApp | Duas marcas de selecao |
| `failed` | O envio de uma mensagem da sua empresa falhou. O motivo da falha sera incluido no retorno de chamada. Verifique a documentacao sobre mensagens de erro para obter ajuda com a depuracao:   * [Erros da API Local](/docs/whatsapp/api/errors) * [Codigos de erro](/docs/whatsapp/cloud-api/support/error-codes) e [solucao de problemas](/docs/whatsapp/cloud-api/support/troubleshooting) da API de Nuvem |
| Equivalente do app WhatsApp | Triangulo de erro vermelho |
| `read` | Uma mensagem enviada pela sua empresa foi lida pelo usuario. As notificacoes de `read` estarao disponiveis somente para usuarios que habilitaram os recibos de leitura. Para usuarios que nao tiverem essa opcao habilitada, voce recebera somente a notificacao de `delivered` . |
| Equivalente do app WhatsApp | Duas marcas de selecao azuis |
| `sent` | Uma mensagem enviada pela empresa esta em transito nos nossos sistemas.   Usuarios da API Local: para receber notificacoes de mensagens `sent` defina `sent_status` como `true` nas [configuracoes do app](/docs/whatsapp/api/settings/app). A notificacao de status `sent` e desabilitada por padrao. |
| Equivalente do app WhatsApp | Uma marca de selecao |
| `warning` | Uma mensagem enviada pela empresa contem um item de catalogo que nao esta disponivel ou nao existe. |

A ordem dessas notificacoes no seu app pode nao refletir o momento real do status da mensagem. Se necessario, veja o registro de data e hora para determinar o momento.

## Perguntas frequentes

[E possivel formatar mensagens?](#faq_1731118056945893)

Sim! O WhatsApp permite que voce formate o texto selecionado na mensagem com negrito, italico, tachado ou espacamento uniforme.

[Link permanente](#faq_1731118056945893)

[Como devo proceder quando for necessario enviar mensagens de atendimento ao cliente apos o periodo de 24h?](#faq_715120295540784)

Podera haver casos em que voce precisara de mais tempo para atender a solicitacao de um cliente, e sera necessario enviar uma resposta ao cliente apos o periodo de 24h. Recomendamos criar modelos de mensagem para:

* enviar o resultado ao usuario ou
* solicitar uma resposta do usuario com o objetivo de ativar uma nova janela de atendimento ao cliente.

Em ambos os casos, adicione a maior quantidade possivel de contexto ao modelo de mensagem. Por exemplo:

* Ola, {{1}}! A respeito do problema que voce relatou anteriormente, viemos informar que, infelizmente, {{2}}. Pedimos desculpas por qualquer inconveniencia causada."
* Temos atualizacoes a respeito do seu ticket. Responda a esta mensagem se deseja continuar recebendo suporte.

[Link permanente](#faq_715120295540784)
