+++
id = "phone-numbers"
title = "Numeros de telefone comerciais"
summary = "Este documento descreve os numeros de telefone comerciais do WhatsApp, bem como os requisitos, as informacoes de gerenciamento e os recursos unicos relacionados."
source = "https://developers.facebook.com/docs/whatsapp/phone-numbers"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks", "phone-numbers", "rate-limits"]
+++
# Numeros de telefone comerciais

Este documento descreve os numeros de telefone comerciais do WhatsApp, bem como os requisitos, as informacoes de gerenciamento e os recursos unicos relacionados.

## Como registrar numeros de telefone comerciais

E preciso registrar um numero de telefone comercial valido para enviar e receber mensagens via API de Nuvem. Os numeros registrados ainda funcionam para fins cotidianos, como ligacoes e mensagens de texto, mas nao podem ser usados com o WhatsApp Messenger ("WhatsApp").

Os numeros que ja estiverem em uso no WhatsApp nao poderao ser registrados, a menos que sejam [excluidos](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F2138577903196467%2F%3Fhelpref%3Duf_share&h=AT0bHkgcHVWAcl3r99RD3PcoxaJrDbFqF_yMFJGCDC9s6DvRioQCFqlrd6PPLLOvaXXQfR-rDeAVC_8ySuClZ-erhXUUSnBo47qLuQ5H2Evdm-4ev0fxO2ZKcIm8NxSSKjIffiLdOjtIDKxb97GxNA) primeiro. Para registrar um numero que foi banido do WhatsApp, reative-o primeiro por meio do [processo de apelacao](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F465883178708358&h=AT0y9eOxEDEw4FEqfHo01lFHfShJXiTOBK32WBVjoiWOjRoPRJqE2qb9JGufejphyCsw88qGuPfcfQ7-t0HRktH0ahv8r8gx7YqpoS1N7mB0dZhIqCeA2yMx4pWc_RbML82VVQtDnU1ouTEqRh_VDA).

Apos a conclusao das etapas descritas no nosso documento [Introducao](/docs/whatsapp/cloud-api/get-started), um numero de telefone comercial de **teste** sera gerado e registrado para voce automaticamente.

### Requisitos de qualificacao

Os numeros de telefone qualificados devem:

* pertencer a voce;
* ter codigo do pais e codigo de area (codigos curtos nao sao compativeis);
* poder receber chamadas de voz ou SMS.
* o numero deve ter [recursos dimensionados](https://www.facebook.com/business/help/595597942906808)

Para registrar um numero 0800, consulte [Registrar 0800 e numeros gratuitos](#registering-1-800-and-toll-free-numbers).

### Metodos de registro

* **Painel de Apps**: conclua as etapas descritas no nosso documento [Introducao](/docs/whatsapp/cloud-api/get-started). Depois, acesse o painel [Painel de Apps](https://developers.facebook.com/apps) > **WhatsApp** > **Configuracao da API** para adicionar um numero de telefone.
* **Meta Business Suite**: voce pode registrar um numero de telefone comercial ao [usar o Meta Business Suite para criar uma conta comercial do WhatsApp](/docs/whatsapp/overview/business-accounts#create-a-waba-via-meta-business-suite).
* **Gerenciador do WhatsApp**: consulte o artigo [Como conectar seu numero de telefone a sua conta do WhatsApp Business](https://www.facebook.com/business/help/456220311516626) na Central de Ajuda.
* **Cadastro incorporado**: se voce estiver trabalhando com um parceiro de solucoes, ele fornecera um link para o cadastro incorporado, que podera ser usado para registrar um numero.

## Status

Os numeros de telefone comerciais tem um status, que reflete a classificacao de qualidade e o [limite de troca de mensagens](/docs/whatsapp/messaging-limits). Esses numeros devem ter o status "conectado" para enviar e receber mensagens usando a API.

### Como ver o status via Gerenciador do WhatsApp

O status atual do seu numero de telefone comercial e exibido na coluna **Status** no painel [Gerenciador do WhatsApp](https://business.facebook.com/latest/whatsapp_manager/) > **Ferramentas da conta** > **Numeros de telefone**.

Consulte o artigo [Sobre a classificacao por qualidade do seu numero de telefone do WhatsApp Business](https://www.facebook.com/business/help/896873687365001) para saber mais sobre as classificacoes de qualidade e o status que aparecem no Gerenciador do WhatsApp.

### Como receber o status via API

Solicite o campo `status` na sua identificacao de numero de telefone comercial do WhatsApp. Consulte a referencia [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) para conferir uma lista de valores de status retornaveis e os respectivos significados.

#### Exemplo de solicitacao

```
curl 'https://graph.facebook.com/v24.0/106540352242922?fields=status' \
-H 'Authorization: Bearer EAAJB...'
```

#### Exemplo de resposta

```
{
  "status": "CONNECTED",
  "id": "106540352242922"
}
```

## Nomes de exibicao

Para registrar um numero de telefone comercial, e preciso fornecer informacoes de nome de exibicao. O nome de exibicao aparece no perfil do WhatsApp do seu numero de telefone comercial e tambem pode ser mostrado na parte superior de **conversas individuais** e na **lista de conversas** se determinadas condicoes forem atendidas. Consulte o documento [Nomes de exibicao](/docs/whatsapp/display-names) para saber como funcionam os nomes de exibicao.

## Perfis empresariais

O perfil empresarial fornece informacoes adicionais sobre sua empresa, como endereco, site, descricao, entre outras. Voce pode fornecer essas informacoes ao registrar o numero de telefone comercial. Consulte o documento [Perfis comerciais](/docs/whatsapp/business-profiles) para saber como os perfis comerciais funcionam.

## Status de conta comercial oficial

Os numeros de telefone comerciais podem receber o status de Conta Comercial Oficial ("OBA"). Os numeros de OBA tem uma marca de selecao azul ao lado do nome na visualizacao de contatos.

Consulte nosso documento sobre [contas comerciais oficiais](/docs/whatsapp/official-business-accounts) para saber como solicitar o status de OBA para um numero de telefone comercial.

## Confirmacao em duas etapas

E preciso definir um PIN de confirmacao em duas etapas ao registrar um numero de telefone comercial. Voce precisara desse codigo de identificacao pessoal para alterar seu PIN ou excluir seu numero de telefone da plataforma.

### Como alterar seu PIN via Gerenciador do WhatsApp

Voce precisara do codigo de identificacao pessoal atual para alterar seu PIN via Gerenciador do WhatsApp. Para alterar seu PIN:

1. Acesse [Gerenciador do WhatsApp](https://business.facebook.com/latest/whatsapp_manager/) > **Ferramentas da conta** > **Numeros de telefone**.
2. Selecione seu numero de telefone comercial.
3. Clique na aba **Confirmacao em duas etapas**.
4. Clique no botao **Alterar PIN** e complete o fluxo.

Caso voce nao tenha seu PIN, sera possivel altera-lo usando a API.

### Como alterar seu PIN via API

Use o ponto de extremidade [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Updating) para definir um novo PIN.

#### Exemplo de solicitacao

```
curl 'https://graph.facebook.com/v24.0/106540352242922/' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "pin": "150954"
}'
```

#### Exemplo de resposta

Caso a solicitacao seja bem-sucedida:

```
{
  "success": true
}
```

### Como desabilitar a confirmacao em duas etapas

Para desabilitar a confirmacao em duas etapas usando o Gerenciador do WhatsApp, siga os passos para alterar seu PIN, mas clique no botao **Desativar a confirmacao em duas etapas** ao final do processo. Um email com um link sera enviado ao endereco de email associado ao portfolio empresarial. Use o link para desabilitar a confirmacao em duas etapas. Depois disso, e possivel reabilitar a configuracao ao definir um novo PIN.

Nao e possivel desabilitar a confirmacao em duas etapas usando a API.

## 0800 e numeros gratuitos

Talvez voce queira registrar um 0800 ou outro numero gratuito na plataforma. Porem, esses numeros normalmente tem um sistema de resposta interativa de voz (IVR, pelas iniciais em ingles) que nao pode ser navegado por uma chamada de registro do WhatsApp. Esse tipo de numero de telefone pode ser registrado, mas e necessario que ele aceite chamadas de numeros internacionais e redirecione o SMS ou a chamada de voz para um agente humano.

Veja as etapas para registrar numeros de telefone com sistema IVR:

1. O WhatsApp consegue compartilhar com voce um ou dois numeros de telefone dos quais a ligacao de registro sera feita.
2. Crie uma lista de permissao para esses numeros. Caso voce nao consiga criar uma lista de permissao para esses numeros, adicione o numero de telefone a sua WABA. Alem disso, abra um tiquete no Suporte Direto para pedir os numeros da chamada de registro e inclua o numero de telefone que voce deseja registrar.
3. Redirecione a chamada de registro para um funcionario ou uma caixa de correio. Depois, acesse o codigo de registro.

Nao ha compatibilidade com numeros de telefone com sistema de resposta interativa de voz (IVR) que nao podem receber chamadas de registro.

## Limite de numeros registrados

Novos portfolios empresariais sao limitados inicialmente a dois numeros de telefone comercial registrados.

Se a empresa for [verificada](https://www.facebook.com/business/help/1095661473946872) ou voce atingir o [limite de mensagens](/docs/whatsapp/messaging-limits) de 2.000, aumentaremos automaticamente o limite para 20. Apos o aumento, voce recebera uma notificacao do Meta Business Suite informando o novo limite e um webhook [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update) sera disparado com `max_phone_numbers_per_business` definido como o novo limite.

## Verificar numeros de telefone

E preciso verificar o numero de telefone que voce quer usar para enviar mensagens aos clientes. Os numeros de telefone devem ser verificados por meio de um codigo enviado por SMS ou ligacao de voz. O processo de verificacao pode ser feito a partir das chamadas da Graph API especificadas a seguir.

Para verificar um numero de telefone usando a Graph API, faca uma solicitacao `POST` a `PHONE_NUMBER_ID/request_code`. Na chamada, inclua o idioma e o metodo de verificacao escolhido.

| Ponto de extremidade | Autenticacao |
| --- | --- |
| `/PHONE_NUMBER_ID/request_code` | Faca sua autenticacao com um token de acesso de usuario do sistema.  Se voce estiver solicitando o codigo em nome de outra empresa, o token de acesso precisa ter acesso avancado para a permissao `whatsapp_business_management`. |

### Parametros

| Nome | Descricao |
| --- | --- |
| `code_method`  *string* | **Obrigatorio.**  O metodo de verificacao escolhido. Opcoes compativeis:   * `SMS` * `VOICE` |
| `language`  *string* | **Obrigatorio.**  O codigo de dois caracteres [do idioma](/docs/whatsapp/business-management-api/message-templates/supported-languages). Por exemplo: `"en"`. |

### Exemplo de solicitacao

```
curl -X POST 'https://graph.facebook.com/v24.0/106540352242922/request_code?code_method=SMS&language=en_US' \
-H 'Authorization: Bearer EAAJB...'
```

Depois da chamada de API, voce recebera o codigo de verificacao por meio do metodo selecionado. Para concluir o processo de verificacao, inclua o codigo em uma solicitacao `POST` a `PHONE_NUMBER_ID/verify_code`.

| Ponto de extremidade | Autenticacao |
| --- | --- |
| `/PHONE_NUMBER_ID/verify_code` | Faca sua autenticacao com um token de acesso de usuario do sistema.  Se voce estiver solicitando o codigo em nome de outra empresa, o token de acesso precisa ter acesso avancado para a permissao `whatsapp_business_management`. |

### Parametros

| Nome | Descricao |
| --- | --- |
| `code`  *string numerica* | **Obrigatorio.**  O codigo recebido depois de fazer a chamada a `FROM_PHONE_NUMBER_ID/request_code`. |

### Exemplo

Exemplo de solicitacao:

```
curl -X POST \
  'https://graph.facebook.com/v13.0/FROM_PHONE_NUMBER_ID/verify_code' \
  -H 'Authorization: Bearer ACCESS_TOKEN' \
  -F 'code=000000'
```

Copiar codigo

A resposta bem-sucedida e semelhante a esta:

```
{
  "success": true
}
```

## WhatsApp user phone number formats

Plus signs (`+`), hyphens (`-`), parenthesis (`(`,`)`), and spaces are supported in send message requests.

We highly recommend that you include both the plus sign and country calling code when sending a message to a customer. If the plus sign is omitted, your business phone number's country calling code is prepended to the customer's phone number. This can result in undelivered or misdelivered messages.

For example, if your business is in India (country calling code `91`) and you send a message to the following customer phone number in various formats:

| Number In Send Message Request | Number Message Delivered To | Outcome |
| --- | --- | --- |
| `+16315551234` | `+16315551234` | Correct number |
| `+1 (631) 555-1234` | `+16315551234` | Correct number |
| `(631) 555-1234` | `+916315551234` | Potentially wrong number |
| `1 (631) 555-1234` | `+9116315551234` | Potentially wrong number |

Note: For Brazil and Mexico, the extra added prefix of the phone number may be modified by the Cloud API. This is a standard behavior of the system and is not considered a bug.

## Verificacao de alteracao de identidade

Podemos verificar a identidade de um cliente antes de enviarmos sua mensagem para ele. Para isso, habilite a verificacao de alteracao de identidade no seu numero de telefone comercial.

Se o cliente realizar uma acao no WhatsApp que considerarmos uma alteracao de identidade, geraremos um novo hash de identidade para ele. Com essa configuracao habilitada, voce podera recuperar esse hash sempre que enviar uma mensagem ao cliente. Nesse caso, sempre que voce receber ou enviar uma mensagem para um cliente sem um hash de identidade, incluiremos o hash dele nos [webhooks de mensagem recebida](/docs/whatsapp/cloud-api/webhooks/reference/messages#incoming-messages) ou [status da mensagem](/docs/whatsapp/cloud-api/webhooks/reference/messages/status). Assim, voce pode capturar e armazenar esse hash para uso futuro.

Quando quiser usar o hash, inclua-o na solicitacao de envio de mensagem. Compararemos o hash da solicitacao com o atual do cliente. Se eles forem iguais, a mensagem sera entregue. Caso haja incompatibilidade, isso significa que a identidade do cliente foi alterada depois do seu ultimo contato com ele. Por isso, nao entregaremos a mensagem. Nesse caso, enviaremos um webhook de status de mensagem com o codigo de erro `137000`, notificando sobre a falha e a discrepancia dos hashes.

Ao receber esse tipo de webhook, considere que o numero de telefone do cliente deixou de ser confiavel. Para reestabelecer a confianca, verifique a identidade do cliente por meio de outro canal que nao seja o WhatsApp. Depois, reenvie a mensagem com falha para a nova identidade (se houver), sem um hash. Armazene, entao, o novo hash do cliente incluido no webhook de status de entrega.

### Sintaxe da solicitacao

Envie uma solicitacao POST ao ponto de extremidade **WhatsApp Business Phone Number > Settings** para habilitar ou desabilitar a verificacao de alteracao de identidade.

`POST /<WHATSAPP_BUSINESS_PHONE_NUMBER>/settings`

### Corpo do post

```
{
  "user_identity_change" : {
    "enable_identity_key_check": <ENABLE_IDENTITY_KEY_CHECK>
}
```

Defina `<ENABLE_IDENTITY_KEY_CHECK>` como `true` para habilitar a verificacao de identidade ou como `false` para desabilita-la.

### Exemplo de solicitacao para habilitar a configuracao

```
curl 'https://graph.facebook.com/v24.0/106850078877666/settings' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "user_identity_change": {
    "enable_identity_key_check": true
  }
}'
```

### Exemplo de resposta a essa solicitacao

```
{
  "success": true
}
```

### Exemplo de envio de mensagem com verificacao

Esta mensagem so seria entregue se o valor `recipient_identity_key_hash` correspondesse ao hash atual do cliente.

```
curl 'https://graph.facebook.com/v24.0/106850078877666/messages' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "+16505551234",
  "recipient_identity_key_hash": "DF2lS5v2W6x=",
  "type": "text",
  "text": {
    "preview_url": false,
    "body": "Your latest statement is attached. See... "
  }
}'
```

### Webhooks

Em webhooks de mensagens recebidas com o objeto `contacts` (como [webhook de mensagens de texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)), o hash do cliente e atribuido a propriedade `identity_key_hash`.

Em webhooks de mensagens enviadas ([webhooks de mensagens de status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)), o hash do cliente e atribuido a propriedade `recipient_identity_key_hash` no objeto `statuses`.

## Como consultar o nivel da taxa de transferencia de dados

Use o ponto de extremidade [Numero de telefone do WhatsApp Business](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) para consultar o [nivel da taxa de transferencia](/docs/whatsapp/throughput) atual de um numero de telefone:

`GET /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>?fields=throughput`

## Recuperar todos os numeros de telefone

Para receber uma lista de todos os numeros de telefone associados a uma conta do WhatsApp Business, envie uma solicitacao GET para o ponto de extremidade de [conta do WhatsApp Business > numeros de telefone](/docs/graph-api/reference/whats-app-business-account/phone_numbers/).

Alem disso, os numeros de telefone podem ser classificados em ordem crescente ou decrescente de acordo com o `last_onboarded_time`, que e baseado em quando o usuario concluiu a integracao do [cadastro incorporado](/docs/whatsapp/embedded-signup). Se nao for especificada, a ordem padrao sera decrescente.

### Sintaxe da solicitacao

```
curl -X GET "https://graph.facebook.com/<API_VERSION>/<WABA_ID>/phone_numbers?access_token=<ACCESS_TOKEN>"
```

Em caso de sucesso, um objeto JSON sera retornado com uma lista de nomes, telefones, classificacoes de qualidade e IDs de telefones associados a uma empresa. Os resultados sao exibidos por data de conclusao do cadastro incorporado em ordem decrescente, com a integracao mais recente listada primeiro.

### Exemplo de resposta

```
{
  "data": [
    {
      "verified_name": "Jasper's Market",
      "display_phone_number": "+1 631-555-5555",
      "id": "1906385232743451",
      "quality_rating": "GREEN"

    },
    {
      "verified_name": "Jasper's Ice Cream",
      "display_phone_number": "+1 631-555-5556",
      "id": "1913623884432103",
      "quality_rating": "NA"
    }
  ]
}
```

### Sintaxe da solicitacao

```
curl -X GET "https://graph.facebook.com/<API_VERSION>/<WABA_ID>/phone_numbers?access_token=&lt;SYSTEM_USER_ACCESS_TOKEN>]&amp;sort=['last_onboarded_time_ascending']"
```

### Exemplo de resposta

Em caso de sucesso, um objeto JSON sera retornado com uma lista de nomes, telefones, classificacoes de qualidade e IDs de telefones associados a uma empresa. Os resultados sao exibidos em ordem crescente com base em quando o usuario concluiu o cadastro incorporado, com a integracao mais recente listada por ultimo.

```
{
  "data": [
   {
      "verified_name": "Jasper's Ice Cream",
      "display_phone_number": "+1 631-555-5556",
      "id": "1913623884432103",
      "quality_rating": "NA"
    },
    {
      "verified_name": "Jasper's Market",
      "display_phone_number": "+1 631-555-5555",
      "id": "1906385232743451",
      "quality_rating": "GREEN"
    }
  ]
}
```

### Filtrar numeros de telefone

Consulte e filtre numeros de telefone com base em `account_mode`. No momento, essa opcao de filtragem esta sendo testada no modo beta. Nem todos os desenvolvedores tem acesso ao recurso.

#### Parametros

| Nome | Descricao |
| --- | --- |
| `field` | **Valor**: `account_mode` |
| `operator` | **Valor**: `EQUAL` |
| `value` | **Valores:**`SANDBOX`, `LIVE` |

#### Sintaxe da solicitacao

```
curl -i -X GET "https://graph.facebook.com/<API_VERSION>/<WABA_ID>/phone_numbers?filtering=[{"field":"account_mode","operator":"EQUAL","value":"SANDBOX"}]&access_token=<ACCESS_TOKEN>
```

### Exemplo de resposta

```
{
  "data": [
    {
      "id": "1972385232742141",
      "display_phone_number": "+1 631-555-1111",
      "verified_name": "Johns Cake Shop",
      "quality_rating": "UNKNOWN",
    }
  ],
  "paging": {
	"cursors": {
		"before": "abcdefghij",
		"after": "klmnopqr"
	}
   }
}
```

## Recuperar um numero de telefone unico

Para consultar informacoes sobre um numero de telefone, envie uma solicitacao GET ao ponto de extremidade de [numero de telefone do WhatsApp Business](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/):

### Sintaxe da solicitacao

```
GET https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>
```

### Exemplo de solicitacao

```
curl \
'https://graph.facebook.com/v15.0/105954558954427/' \
-H 'Authorization: Bearer EAAFl...'
```

Em caso de sucesso, um objeto JSON e retornado com o nome, o numero de telefone, o ID do telefone e as classificacoes de qualidade do numero de telefone consultado.

```
{
  "code_verification_status" : "VERIFIED",
  "display_phone_number" : "15555555555",
  "id" : "105954558954427",
  "quality_rating" : "GREEN",
  "verified_name" : "Support Number"
}
```

## Consultar status do nome de exibicao (beta)

Inclua `fields=name_status` como um parametro da string de consulta para consultar o status do nome de exibicao associado a um numero de telefone especifico. No momento, esse campo esta na versao beta e nao esta disponivel para todos os desenvolvedores.

### Exemplo de solicitacao

```
curl \
'https://graph.facebook.com/v15.0/105954558954427?fields=name_status' \
-H 'Authorization: Bearer EAAFl...'
```

### Exemplo de resposta

```
{
  "id" : "105954558954427",
  "name_status" : "AVAILABLE_WITHOUT_REVIEW"
}
```

O valor `name_status` pode ser um dos seguintes:

* `APPROVED`  o nome foi aprovado. Voce ja pode baixar o certificado.
* `AVAILABLE_WITHOUT_REVIEW`  o certificado do telefone esta disponivel, e o nome de exibicao esta pronto para ser usado sem analise.
* `DECLINED`  o nome nao foi aprovado. Nao e possivel baixar o certificado.
* `EXPIRED`  o certificado expirou e nao e mais possivel baixa-lo.
* `PENDING_REVIEW`  a solicitacao de nome esta em analise. Nao e possivel baixar o certificado.
* `NONE`  nao ha certificados disponiveis.

Os certificados tem validade de sete dias.

## Como excluir numeros de telefone comerciais

Apenas os administradores do portfolio empresarial podem excluir numeros de telefone comerciais. Alem disso, os numeros nao poderao ser excluidos se tiverem sido usados para enviar mensagens pagas nos ultimos 30 dias.

### Como excluir numeros de telefone comerciais via Gerenciador do WhatsApp

Caso o numero de telefone comercial tenha o status "Conectado", voce precisara do seu PIN de confirmacao em duas etapas para excluir o numero.

1. Carregue seu portfolio empresarial no [Gerenciador do WhatsApp](https://business.facebook.com/wa/manage/home/).
2. Se o painel Numeros de telefone nao carregar automaticamente, navegue ate **Ferramentas da conta** (icone de caixa de ferramentas) > **Telefones**.
3. Clique no icone da lixeira do numero de telefone e conclua o fluxo.

Caso o numero tenha sido usado para enviar mensagens pagas nos ultimos 30 dias, redirecionaremos voce para o painel **Insights**, que mostra a data da ultima mensagem paga. A exclusao do numero de telefone podera ser feita 30 dias apos a data listada.

### Como excluir numeros de telefone comerciais via API

Nao e possivel excluir um numero de telefone comercial via API.

## Como migrar numeros de telefone comerciais

E possivel [migrar numeros de telefone de uma WABA para outra](/docs/whatsapp/solution-providers/support/migrating-phone-numbers-among-solution-partners-via-embedded-signup), bem como [migrar um numero da API Local para a API de Nuvem](/docs/whatsapp/cloud-api/guides/migrating-from-onprem-to-cloud).

## Componentes de conversa

Voce pode habilitar componentes de interface do usuario para que os usuarios do WhatsApp interajam por mensagem com sua empresa mais facilmente. Consulte [Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components).
