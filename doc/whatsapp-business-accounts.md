+++
id = "whatsapp-business-accounts"
title = "Contas do WhatsApp Business"
summary = "As contas do WhatsApp Business (\"WABAs\") representam uma empresa na Plataforma do WhatsApp Business."
source = "https://developers.facebook.com/docs/whatsapp/whatsapp-business-accounts"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "rate-limits"]
+++
# Contas do WhatsApp Business

As contas do WhatsApp Business ("WABAs") representam uma empresa na Plataforma do WhatsApp Business. E preciso ter uma WABA para enviar e receber mensagens de usuarios do WhatsApp, bem como criar e gerenciar modelos.

Veja diferentes maneiras de criar uma WABA descritas abaixo. Depois de criar a conta, recomendamos [conectar um numero de telefone](https://www.facebook.com/business/help/456220311516626) e [configurar uma forma de pagamento](https://www.facebook.com/business/help/2225184664363779).

## Limitacoes

* Uma conta do WhatsApp Business (WABA) pode ter ate 250 modelos de mensagem.
* Inicialmente, as contas comerciais da Meta podem ter dois numeros de telefone comerciais registrados. Entretanto, e possivel aumentar esse limite para ate 20. Consulte [Registered Number Limits](/docs/whatsapp/cloud-api/phone-numbers#registered-number-limits).
* Ha um limite inicial de 20 WABAs para contas comerciais da Meta.
* A WABA precisa pertencer a apenas um Gerenciador de Negocios. Nao e possivel ter dois ou mais Gerenciadores de Negocios como proprietarios de uma WABA.
* Nao e possivel editar o fuso horario e a moeda da WABA depois que uma linha de credito e anexada. Nao e possivel migrar uma WABA de uma empresa para outra.

## Criar uma WABA via Painel de Apps

Caso voce queira usar a API de Nuvem para enviar e receber mensagens, siga as etapas na documentacao [Introducao](/docs/whatsapp/cloud-api/get-started). Depois de concluir as etapas mencionadas, voce tera uma WABA e um numero comercial de teste. Alem disso, tera acesso a interface **Painel de Apps** > **WhatsApp** > **Configuracao da API**.

A opcao **Configuracao da API** permite adicionar um numero de telefone comercial de producao, o que gera uma nova WABA que e entao associada ao numero.

## Criar uma WABA via provedor de solucoes

Se estiver trabalhando com uma empresa que oferece servicos de mensagens do WhatsApp para voce por meio da API, esse provedor de solucoes fornecera as instrucoes. Normalmente, isso envolve a conclusao do fluxo de cadastro incorporado, que reune informacoes sobre sua empresa e gera uma WABA para voce. Depois, basta usar o app do provedor para acessar a WABA criada e os ativos relacionados.

Para saber mais, consulte o artigo da Central de Ajuda [Como criar uma conta do WhatsApp Business com provedores de solucoes do WhatsApp Business](https://www.facebook.com/business/help/524220081677109).

## Criar uma WABA via Meta Business Suite

Esse recurso sera lancado de forma gradual nas proximas semanas e pode nao estar disponivel para voce imediatamente. No momento, nao ha disponibilidade para portfolios empresariais com endereco no Brasil ou na India.

Voce pode criar uma WABA usando o [Meta Business Suite](https://business.facebook.com/). Use esse metodo se estiver trabalhando com um provedor de solucoes que fornece servicos relacionados a mensagens do WhatsApp por meio do Meta Business Suite em vez da API de Nuvem.

Para criar uma WABA usando o Meta Business Suite:

1. Acesse <https://business.facebook.com/> e crie um portfolio empresarial ou entre na sua conta e selecione o portfolio existente, caso ja tenha um.
2. Va para o painel **Configuracoes** (icone de engrenagem) > **Contas** > **Contas do WhatsApp**.
3. Clique no botao azul **+Adicionar** e, no menu suspenso, selecione **Crie uma nova conta do WhatsApp Business**.
4. Depois, complete o fluxo na janela **Criar uma conta do WhatsApp Business** (imagem abaixo).

## Como compartilhar a WABA com um provedor de solucoes

Voce pode compartilhar a WABA (ou qualquer um dos seus ativos de negocios) com um provedor de solucoes verificado pela empresa (tambem conhecido como "parceiro") usando o Meta Business Suite. Apos o compartilhamento, o parceiro podera usar o Meta Business Suite para acessar sua WABA e fornecer servicos.

### Notas

* Se estiver compartilhando a WABA com um provedor de solucoes (um tipo de parceiro que tem uma linha de credito), receba primeiro a linha de credito dele para que voce possa usar o app fornecido por ele para enviar mensagens.
* E possivel compartilhar uma WABA com ate dois parceiros.

### Se voce ainda nao tiver compartilhado um ativo com o parceiro

1. Peca ao parceiro que informe a identificacao do portfolio empresarial dele. Voce precisara dessa informacao para concluir as etapas restantes.
2. Entre no [Meta Business Suite](https://business.facebook.com/). Caso voce tenha varios portfolios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opcao.
3. Va para o painel **Configuracoes** (icone de engrenagem) > **Contas** > **Contas do WhatsApp**.
4. Na lista de WABAs, selecione sua conta ou clique no link **Detalhes**.
5. Na sobreposicao de detalhes que aparece a direita (imagem abaixo), clique no botao **Atribuir parceiro**.
6. Na sobreposicao **Compartilhar essa conta do WhatsApp com um parceiro**, insira a identificacao do portfolio empresarial do parceiro e use os botoes de alternancia para definir quais permissoes conceder. Depois, clique no botao **Atribuir**.
7. Se a WABA for compartilhada com o parceiro, voce vera a mensagem **Parceiro adicionado**. Clique no botao **Concluir** para ignora-la.
8. De volta a sobreposicao de detalhes, clique na aba **Parceiros**.
9. Na aba **Parceiros**, confirme se o nome do parceiro aparece com as permissoes apropriadas.
10. Informe ao parceiro que voce compartilhou a WABA. Se apropriado, peca para ele compartilhar a linha de credito, conforme explicado acima.

### Se voce ja tiver compartilhado um ativo com o parceiro

1. Entre no [Meta Business Suite](https://business.facebook.com/). Caso voce tenha varios portfolios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opcao.
2. Va para o painel **Configuracoes** (icone de engrenagem) > **Usuarios** > **Parceiros**.
3. Na lista de parceiros, clique em um nome ou no link **Detalhes**.
4. Na sobreposicao de detalhes que aparece a direita (imagem abaixo), clique no botao **Atribuir ativos**.
5. Na janela **Atribuir ativos e permissoes**, clique no tipo de ativo **Contas do WhatsApp**.
6. Marque a caixa de selecao ao lado da sua WABA, use os botoes de alternancia para definir quais permissoes conceder ao parceiro e clique no botao **Atribuir**.
7. Em caso de sucesso, voce vera a mensagem **Ativos atribuidos**. Clique no botao **Concluir** para ignorar a janela.
8. Confirme que a WABA exibida na aba **Ativos que voce atribuiu** tem as permissoes adequadas.
9. Informe ao parceiro que voce compartilhou a WABA. Se apropriado, peca para ele compartilhar a linha de credito, conforme explicado acima.

## Obter dados da WABA por meio da API

Use o ponto de extremidade [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#Reading) para obter dados de uma WABA. Use o parametro `fields` para solicitar campos especificos em uma WABA ou omita-o para obter campos padrao retornados pelo ponto de extremidade.

### Exemplo de solicitacao

```
curl 'https://graph.facebook.com/v24.0/102290129340398?fields=name,status,currency,country,business_verification_status' \
-H 'Authorization: Bearer EAAJB...'
```

### Exemplo de resposta

```
{
  "name": "Lucky Shrub",
  "status": "ACTIVE",
  "currency": "USD",
  "country": "US",
  "business_verification_status": "verified",
  "id": "102290129340398"
}
```

## Acessar a WABA com o Gerenciador do WhatsApp

Voce pode acessar sua WABA no Gerenciador do WhatsApp para ver informacoes basicas, como status do numero de telefone comercial e metricas de mensagens. Tambem e possivel executar tarefas simples, como criacao e edicao de modelos.

Para acessar sua WABA no Gerenciador do WhatsApp:

1. Entre no [Meta Business Suite](https://business.facebook.com/). Caso voce tenha varios portfolios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opcao.
2. Va para o painel **Configuracoes** (icone de engrenagem) > **Contas** > **Contas do WhatsApp**.
3. Na lista de WABAs, selecione sua conta ou clique no link **Detalhes**.
4. Na aba **Resumo**, clique no botao **Gerenciador do WhatsApp**.

## Webhooks

Assine o webhook [account\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_update) para receber notificacoes sobre alteracoes no status de uma conta do WhatsApp Business, incluindo mudancas devido a violacoes de politicas e termos.

Sempre que sua WABA violar uma politica, voce recebera uma notificacao semelhante a esta:

```
{
  "object": "whatsapp_business_account",
  "entry": [
    {
      "id": "whatsapp-business-account-id",
      "time": 1604703058,
      "changes": [
        {
          "field": "account_update",
          "value": {
            "phone_number": "16505551111",
            "event": "ACCOUNT_VIOLATION",
            "violation_info": {
            	"violation_type": "ALCOHOL",
            }
          }
        }
      ]
    }
  ]
}
```

Para ver uma lista de violacoes de politica, consulte o nosso documento [Violacoes da Politica da Plataforma do WhatsApp Business](/docs/whatsapp/overview/policy-enforcement/violations). Se uma restricao tiver sido imposta, um webhook **account\_update** sera disparado, descrevendo a violacao.

## Enviar mensagens em nome do cliente

O modelo de propriedade da WABA "Em nome de" esta obsoleto e nao e mais possivel. Consulte a [suspensao do modelo Em nome de (OBO)](/docs/whatsapp/solution-providers/on-behalf-of/legacy-model-deprecation/) para saber mais.
