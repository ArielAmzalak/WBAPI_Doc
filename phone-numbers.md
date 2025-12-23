![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Fcloud-api%2Fphone-numbers%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)[Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)

[API de Nuvem do WhatsApp](/docs/whatsapp/cloud-api)

* [Visão geral](/docs/whatsapp/cloud-api/overview)
* [Começar](/docs/whatsapp/cloud-api/get-started)
* [Mensagem](/docs/whatsapp/cloud-api/guides/send-messages)
* [Modelos](/docs/whatsapp/business-management-api/message-templates)
* [Webhooks](/docs/whatsapp/cloud-api/guides/set-up-webhooks)
* [Calling](/docs/whatsapp/cloud-api/calling)
* [Grupos](/docs/whatsapp/cloud-api/groups)
* [Bloquear usuários](/docs/whatsapp/cloud-api/block-users)
* [Números de telefone](/docs/whatsapp/cloud-api/phone-numbers)

  + [Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components)
  + [Throughput](/docs/whatsapp/throughput)
* [Vender produtos e serviços](/docs/whatsapp/cloud-api/guides/sell-products-and-services)
* [Payments API - India](/docs/whatsapp/cloud-api/payments-api/payments-in)
* [API de Pagamentos – Brasil](/docs/whatsapp/cloud-api/payments-api/payments-br)
* [Referência da API](/docs/whatsapp/cloud-api/reference)
* [Webhooks reference](/docs/whatsapp/webhooks/reference)
* [Suporte](/docs/whatsapp/cloud-api/support)

Nesta Página

[Números de telefone comerciais](#n-meros-de-telefone-comerciais)

[Como registrar números de telefone comerciais](#como-registrar-n-meros-de-telefone-comerciais)

[Requisitos de qualificação](#requisitos-de-qualifica--o)

[Métodos de registro](#m-todos-de-registro)

[Status](#status)

[Como ver o status via Gerenciador do WhatsApp](#como-ver-o-status-via-gerenciador-do-whatsapp)

[Como receber o status via API](#como-receber-o-status-via-api)

[Nomes de exibição](#nomes-de-exibi--o)

[Perfis empresariais](#perfis-empresariais)

[Status de conta comercial oficial](#status-de-conta-comercial-oficial)

[Confirmação em duas etapas](#confirma--o-em-duas-etapas)

[Como alterar seu PIN via Gerenciador do WhatsApp](#como-alterar-seu-pin-via-gerenciador-do-whatsapp)

[Como alterar seu PIN via API](#como-alterar-seu-pin-via-api)

[Como desabilitar a confirmação em duas etapas](#como-desabilitar-a-confirma--o-em-duas-etapas)

[0800 e números gratuitos](#0800-e-n-meros-gratuitos)

[Limite de números registrados](#limite-de-n-meros-registrados)

[Verificar números de telefone](#verificar-n-meros-de-telefone)

[Parâmetros](#par-metros)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo](#exemplo)

[WhatsApp user phone number formats](#whatsapp-user-phone-number-formats)

[Verificação de alteração de identidade](#verifica--o-de-altera--o-de-identidade)

[Sintaxe da solicitação](#sintaxe-da-solicita--o)

[Corpo do post](#corpo-do-post)

[Exemplo de solicitação para habilitar a configuração](#exemplo-de-solicita--o-para-habilitar-a-configura--o)

[Exemplo de resposta a essa solicitação](#exemplo-de-resposta-a-essa-solicita--o)

[Exemplo de envio de mensagem com verificação](#exemplo-de-envio-de-mensagem-com-verifica--o)

[Webhooks](#webhooks)

[Como consultar o nível da taxa de transferência de dados](#como-consultar-o-n-vel-da-taxa-de-transfer-ncia-de-dados)

[Recuperar todos os números de telefone](#recuperar-todos-os-n-meros-de-telefone)

[Sintaxe da solicitação](#sintaxe-da-solicita--o-2)

[Exemplo de resposta](#exemplo-de-resposta)

[Filtrar números de telefone](#filtrar-n-meros-de-telefone)

[Recuperar um número de telefone único](#recuperar-um-n-mero-de-telefone--nico)

[Sintaxe da solicitação](#sintaxe-da-solicita--o-3)

[Exemplo de solicitação](#exemplo-de-solicita--o-2)

[Consultar status do nome de exibição (beta)](#consultar-status-do-nome-de-exibi--o--beta-)

[Exemplo de solicitação](#exemplo-de-solicita--o-3)

[Exemplo de resposta](#exemplo-de-resposta-2)

[Como excluir números de telefone comerciais](#como-excluir-n-meros-de-telefone-comerciais)

[Como excluir números de telefone comerciais via Gerenciador do WhatsApp](#como-excluir-n-meros-de-telefone-comerciais-via-gerenciador-do-whatsapp)

[Como excluir números de telefone comerciais via API](#como-excluir-n-meros-de-telefone-comerciais-via-api)

[Como migrar números de telefone comerciais](#como-migrar-n-meros-de-telefone-comerciais)

[Componentes de conversa](#componentes-de-conversa)

![](https://lookaside.fbsbx.com/elementpath/media/?media_id=595945097590761&version=1760739785)[Plataforma do WhatsApp Business](https://developers.facebook.com/docs/whatsapp)

# Números de telefone comerciais

Este documento descreve os números de telefone comerciais do WhatsApp, bem como os requisitos, as informações de gerenciamento e os recursos únicos relacionados.

## Como registrar números de telefone comerciais

É preciso registrar um número de telefone comercial válido para enviar e receber mensagens via API de Nuvem. Os números registrados ainda funcionam ​para fins cotidianos, como ligações e mensagens de texto, mas não podem ser usados ​​com o WhatsApp Messenger ("WhatsApp").

Os números que já estiverem em uso no WhatsApp não poderão ser registrados, a menos que sejam [excluídos](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F2138577903196467%2F%3Fhelpref%3Duf_share&h=AT0bHkgcHVWAcl3r99RD3PcoxaJrDbFqF_yMFJGCDC9s6DvRioQCFqlrd6PPLLOvaXXQfR-rDeAVC_8ySuClZ-erhXUUSnBo47qLuQ5H2Evdm-4ev0fxO2ZKcIm8NxSSKjIffiLdOjtIDKxb97GxNA) primeiro. Para registrar um número que foi banido do WhatsApp, reative-o primeiro por meio do [processo de apelação](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F465883178708358&h=AT0y9eOxEDEw4FEqfHo01lFHfShJXiTOBK32WBVjoiWOjRoPRJqE2qb9JGufejphyCsw88qGuPfcfQ7-t0HRktH0ahv8r8gx7YqpoS1N7mB0dZhIqCeA2yMx4pWc_RbML82VVQtDnU1ouTEqRh_VDA).

Após a conclusão das etapas descritas no nosso documento [Introdução](/docs/whatsapp/cloud-api/get-started), um número de telefone comercial de **teste** será gerado e registrado para você automaticamente.

### Requisitos de qualificação

Os números de telefone qualificados devem:

* pertencer a você;
* ter código do país e código de área (códigos curtos não são compatíveis);
* poder receber chamadas de voz ou SMS.
* o número deve ter [recursos dimensionados](https://www.facebook.com/business/help/595597942906808)

Para registrar um número 0800, consulte [Registrar 0800 e números gratuitos](#registering-1-800-and-toll-free-numbers).

### Métodos de registro

* **Painel de Apps**: conclua as etapas descritas no nosso documento [Introdução](/docs/whatsapp/cloud-api/get-started). Depois, acesse o painel [Painel de Apps](https://developers.facebook.com/apps) > **WhatsApp** > **Configuração da API** para adicionar um número de telefone.
* **Meta Business Suite**: você pode registrar um número de telefone comercial ao [usar o Meta Business Suite para criar uma conta comercial do WhatsApp](/docs/whatsapp/overview/business-accounts#create-a-waba-via-meta-business-suite).
* **Gerenciador do WhatsApp**: consulte o artigo [Como conectar seu número de telefone à sua conta do WhatsApp Business](https://www.facebook.com/business/help/456220311516626) na Central de Ajuda.
* **Cadastro incorporado**: se você estiver trabalhando com um parceiro de soluções, ele fornecerá um link para o cadastro incorporado, que poderá ser usado para registrar um número.

## Status

Os números de telefone comerciais têm um status, que reflete a classificação de qualidade e o [limite de troca de mensagens](/docs/whatsapp/messaging-limits). Esses números devem ter o status "conectado" para enviar e receber mensagens usando a API.

### Como ver o status via Gerenciador do WhatsApp

O status atual do seu número de telefone comercial é exibido na coluna **Status** no painel [Gerenciador do WhatsApp](https://business.facebook.com/latest/whatsapp_manager/) > **Ferramentas da conta** > **Números de telefone**.

Consulte o artigo [Sobre a classificação por qualidade do seu número de telefone do WhatsApp Business](https://www.facebook.com/business/help/896873687365001) para saber mais sobre as classificações de qualidade e o status que aparecem no Gerenciador do WhatsApp.

### Como receber o status via API

Solicite o campo `status` na sua identificação de número de telefone comercial do WhatsApp. Consulte a referência [GET /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) para conferir uma lista de valores de status retornáveis ​​e os respectivos significados.

#### Exemplo de solicitação

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

## Nomes de exibição

Para registrar um número de telefone comercial, é preciso fornecer informações de nome de exibição. O nome de exibição aparece no perfil do WhatsApp do seu número de telefone comercial e também pode ser mostrado na parte superior de **conversas individuais** e na **lista de conversas** se determinadas condições forem atendidas. Consulte o documento [Nomes de exibição](/docs/whatsapp/display-names) para saber como funcionam os nomes de exibição.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/507127951_698062976515521_2852142619234157074_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=-AMx-e8Xpc0Q7kNvwEpY9TP&_nc_oc=AdmquytE61Q79Sjy049ONGTGZmnhJLdJor3SbJba4jnDyndy-j8TXfYxJJwUjvgTL94&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfhpIZ9vITbkQ39b5fvI0Ay_4DIu6TBXtwYLtyZusgOzRQ&oe=69404C29)

## Perfis empresariais

O perfil empresarial fornece informações adicionais sobre sua empresa, como endereço, site, descrição, entre outras. Você pode fornecer essas informações ao registrar o número de telefone comercial. Consulte o documento [Perfis comerciais](/docs/whatsapp/business-profiles) para saber como os perfis comerciais funcionam.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/507476070_1379105613180336_7510619276605653298_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=JCeQUJtp_HwQ7kNvwEQ7vM1&_nc_oc=AdkE6K1hrBYDiIQOIjkDeUrS0Uxny5QFF2W4wnW9RER_SQjGXGFLjkwfik8iEjjsOl4&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfjdgatuJz0trskHLxVkQQZlKORabSvBs8nCsEkaWYHLfQ&oe=6940531D)

## Status de conta comercial oficial

Os números de telefone comerciais podem receber o status de Conta Comercial Oficial ("OBA"). Os números de OBA têm uma marca de seleção azul ao lado do nome na visualização de contatos.

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/456954377_453386597161620_5745766558871976538_n.png?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=RVUKnZvUKHwQ7kNvwGm9rK2&_nc_oc=AdkZqodK9sCoxtEofKO_BcKGgFCQJ0s3Vf-xX9eaRH97dway-nW__lH2ybiUUNAhQM0&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfhjBJUPgKBgDlgaFphf_qe08IKP8Now0Ut6t3G0DhN1Pw&oe=69404273)

Consulte nosso documento sobre [contas comerciais oficiais](/docs/whatsapp/official-business-accounts) para saber como solicitar o status de OBA para um número de telefone comercial.

## Confirmação em duas etapas

É preciso definir um PIN de confirmação em duas etapas ao registrar um número de telefone comercial. Você precisará desse código de identificação pessoal para alterar seu PIN ou excluir seu número de telefone da plataforma.

### Como alterar seu PIN via Gerenciador do WhatsApp

Você precisará do código de identificação pessoal atual para alterar seu PIN via Gerenciador do WhatsApp. Para alterar seu PIN:

1. Acesse [Gerenciador do WhatsApp](https://business.facebook.com/latest/whatsapp_manager/) > **Ferramentas da conta** > **Números de telefone**.
2. Selecione seu número de telefone comercial.
3. Clique na aba **Confirmação em duas etapas**.
4. Clique no botão **Alterar PIN** e complete o fluxo.

Caso você não tenha seu PIN, será possível alterá-lo usando a API.

### Como alterar seu PIN via API

Use o ponto de extremidade [POST /<WHATSAPP\_BUSINESS\_PHONE\_NUMBER\_ID>](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Updating) para definir um novo PIN.

#### Exemplo de solicitação

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

Caso a solicitação seja bem-sucedida:

```
{
  "success": true
}
```

### Como desabilitar a confirmação em duas etapas

Para desabilitar a confirmação em duas etapas usando o Gerenciador do WhatsApp, siga os passos para alterar seu PIN, mas clique no botão **Desativar a confirmação em duas etapas** ao final do processo. Um email com um link será enviado ao endereço de email associado ao portfólio empresarial. Use o link para desabilitar a confirmação em duas etapas. Depois disso, é possível reabilitar a configuração ao definir um novo PIN.

Não é possível desabilitar a confirmação em duas etapas usando a API.

## 0800 e números gratuitos

Talvez você queira registrar um 0800 ou outro número gratuito na plataforma. Porém, esses números normalmente têm um sistema de resposta interativa de voz (IVR, pelas iniciais em inglês) que não pode ser navegado por uma chamada de registro do WhatsApp. Esse tipo de número de telefone pode ser registrado, mas é necessário que ele aceite chamadas de números internacionais e redirecione o SMS ou a chamada de voz para um agente humano.

Veja as etapas para registrar números de telefone com sistema IVR:

1. O WhatsApp consegue compartilhar com você um ou dois números de telefone dos quais a ligação de registro será feita.
2. Crie uma lista de permissão para esses números. Caso você não consiga criar uma lista de permissão para esses números, adicione o número de telefone à sua WABA. Além disso, abra um tíquete no Suporte Direto para pedir os números da chamada de registro e inclua o número de telefone que você deseja registrar.
3. Redirecione a chamada de registro para um funcionário ou uma caixa de correio. Depois, acesse o código de registro.

Não há compatibilidade com números de telefone com sistema de resposta interativa de voz (IVR) que não podem receber chamadas de registro.

## Limite de números registrados

Novos portfólios empresariais são limitados inicialmente a dois números de telefone comercial registrados.

Se a empresa for [verificada](https://www.facebook.com/business/help/1095661473946872) ou você atingir o [limite de mensagens](/docs/whatsapp/messaging-limits) de 2.000, aumentaremos automaticamente o limite para 20. Após o aumento, você receberá uma notificação do Meta Business Suite informando o novo limite e um webhook [business\_capability\_update](/docs/whatsapp/cloud-api/webhooks/reference/business_capability_update) será disparado com `max_phone_numbers_per_business` definido como o novo limite.

## Verificar números de telefone

É preciso verificar o número de telefone que você quer usar para enviar mensagens aos clientes. Os números de telefone devem ser verificados por meio de um código enviado por SMS ou ligação de voz. O processo de verificação pode ser feito a partir das chamadas da Graph API especificadas a seguir.

Para verificar um número de telefone usando a Graph API, faça uma solicitação `POST` a `PHONE_NUMBER_ID/request_code`. Na chamada, inclua o idioma e o método de verificação escolhido.

| Ponto de extremidade | Autenticação |
| --- | --- |
| `/PHONE_NUMBER_ID/request_code` | Faça sua autenticação com um token de acesso de usuário do sistema.  Se você estiver solicitando o código em nome de outra empresa, o token de acesso precisa ter acesso avançado para a permissão `whatsapp_business_management`. |

### Parâmetros

| Nome | Descrição |
| --- | --- |
| `code_method`  *string* | **Obrigatório.**  O método de verificação escolhido. Opções compatíveis:   * `SMS` * `VOICE` |
| `language`  *string* | **Obrigatório.**  O código de dois caracteres [do idioma](/docs/whatsapp/business-management-api/message-templates/supported-languages). Por exemplo: `"en"`. |

### Exemplo de solicitação

```
curl -X POST 'https://graph.facebook.com/v24.0/106540352242922/request_code?code_method=SMS&language=en_US' \
-H 'Authorization: Bearer EAAJB...'
```

Depois da chamada de API, você receberá o código de verificação por meio do método selecionado. Para concluir o processo de verificação, inclua o código em uma solicitação `POST` a `PHONE_NUMBER_ID/verify_code`.

| Ponto de extremidade | Autenticação |
| --- | --- |
| `/PHONE_NUMBER_ID/verify_code` | Faça sua autenticação com um token de acesso de usuário do sistema.  Se você estiver solicitando o código em nome de outra empresa, o token de acesso precisa ter acesso avançado para a permissão `whatsapp_business_management`. |

### Parâmetros

| Nome | Descrição |
| --- | --- |
| `code`  *string numérica* | **Obrigatório.**  O código recebido depois de fazer a chamada a `FROM_PHONE_NUMBER_ID/request_code`. |

### Exemplo

Exemplo de solicitação:

```
curl -X POST \
  'https://graph.facebook.com/v13.0/FROM_PHONE_NUMBER_ID/verify_code' \
  -H 'Authorization: Bearer ACCESS_TOKEN' \
  -F 'code=000000'
```

Copiar código

A resposta bem-sucedida é semelhante a esta:

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

## Verificação de alteração de identidade

Podemos verificar a identidade de um cliente antes de enviarmos sua mensagem para ele. Para isso, habilite a verificação de alteração de identidade no seu número de telefone comercial.

Se o cliente realizar uma ação no WhatsApp que considerarmos uma alteração de identidade, geraremos um novo hash de identidade para ele. Com essa configuração habilitada, você poderá recuperar esse hash sempre que enviar uma mensagem ao cliente. Nesse caso, sempre que você receber ou enviar uma mensagem para um cliente sem um hash de identidade, incluiremos o hash dele nos [webhooks de mensagem recebida](/docs/whatsapp/cloud-api/webhooks/reference/messages#incoming-messages) ou [status da mensagem](/docs/whatsapp/cloud-api/webhooks/reference/messages/status). Assim, você pode capturar e armazenar esse hash para uso futuro.

Quando quiser usar o hash, inclua-o na solicitação de envio de mensagem. Compararemos o hash da solicitação com o atual do cliente. Se eles forem iguais, a mensagem será entregue. Caso haja incompatibilidade, isso significa que a identidade do cliente foi alterada depois do seu último contato com ele. Por isso, não entregaremos a mensagem. Nesse caso, enviaremos um webhook de status de mensagem com o código de erro `137000`, notificando sobre a falha e a discrepância dos hashes.

Ao receber esse tipo de webhook, considere que o número de telefone do cliente deixou de ser confiável. Para reestabelecer a confiança, verifique a identidade do cliente por meio de outro canal que não seja o WhatsApp. Depois, reenvie a mensagem com falha para a nova identidade (se houver), sem um hash. Armazene, então, o novo hash do cliente incluído no webhook de status de entrega.

### Sintaxe da solicitação

Envie uma solicitação POST ao ponto de extremidade **WhatsApp Business Phone Number > Settings** para habilitar ou desabilitar a verificação de alteração de identidade.

`POST /<WHATSAPP_BUSINESS_PHONE_NUMBER>/settings`

### Corpo do post

```
{
  "user_identity_change" : {
    "enable_identity_key_check": <ENABLE_IDENTITY_KEY_CHECK>
}
```

Defina `<ENABLE_IDENTITY_KEY_CHECK>` como `true` para habilitar a verificação de identidade ou como `false` para desabilitá-la.

### Exemplo de solicitação para habilitar a configuração

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

### Exemplo de resposta a essa solicitação

```
{
  "success": true
}
```

### Exemplo de envio de mensagem com verificação

Esta mensagem só seria entregue se o valor `recipient_identity_key_hash` correspondesse ao hash atual do cliente.

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

Em webhooks de mensagens recebidas com o objeto `contacts` (como [webhook de mensagens de texto](/docs/whatsapp/cloud-api/webhooks/reference/messages/text)), o hash do cliente é atribuído à propriedade `identity_key_hash`.

Em webhooks de mensagens enviadas ([webhooks de mensagens de status](/docs/whatsapp/cloud-api/webhooks/reference/messages/status)), o hash do cliente é atribuído à propriedade `recipient_identity_key_hash` no objeto `statuses`.

## Como consultar o nível da taxa de transferência de dados

Use o ponto de extremidade [Número de telefone do WhatsApp Business](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/#Reading) para consultar o [nível da taxa de transferência](/docs/whatsapp/throughput) atual de um número de telefone:

`GET /<WHATSAPP_BUSINESS_PHONE_NUMBER_ID>?fields=throughput`

## Recuperar todos os números de telefone

Para receber uma lista de todos os números de telefone associados a uma conta do WhatsApp Business, envie uma solicitação GET para o ponto de extremidade de [conta do WhatsApp Business > números de telefone](/docs/graph-api/reference/whats-app-business-account/phone_numbers/).

Além disso, os números de telefone podem ser classificados em ordem crescente ou decrescente de acordo com o `last_onboarded_time`, que é baseado em quando o usuário concluiu a integração do [cadastro incorporado](/docs/whatsapp/embedded-signup). Se não for especificada, a ordem padrão será decrescente.

### Sintaxe da solicitação

```
curl -X GET "https://graph.facebook.com/<API_VERSION>/<WABA_ID>/phone_numbers?access_token=<ACCESS_TOKEN>"
```

Em caso de sucesso, um objeto JSON será retornado com uma lista de nomes, telefones, classificações de qualidade e IDs de telefones associados a uma empresa. Os resultados são exibidos por data de conclusão do cadastro incorporado em ordem decrescente, com a integração mais recente listada primeiro.

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

### Sintaxe da solicitação

```
curl -X GET "https://graph.facebook.com/<API_VERSION>/<WABA_ID>/phone_numbers?access_token=&lt;SYSTEM_USER_ACCESS_TOKEN>]&amp;sort=['last_onboarded_time_ascending']"
```

### Exemplo de resposta

Em caso de sucesso, um objeto JSON será retornado com uma lista de nomes, telefones, classificações de qualidade e IDs de telefones associados a uma empresa. Os resultados são exibidos em ordem crescente com base em quando o usuário concluiu o cadastro incorporado, com a integração mais recente listada por último.

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

### Filtrar números de telefone

Consulte e filtre números de telefone com base em `account_mode`. No momento, essa opção de filtragem está sendo testada no modo beta. Nem todos os desenvolvedores têm acesso ao recurso.

#### Parâmetros

| Nome | Descrição |
| --- | --- |
| `field` | **Valor**: `account_mode` |
| `operator` | **Valor**: `EQUAL` |
| `value` | **Valores:**`SANDBOX`, `LIVE` |

#### Sintaxe da solicitação

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
      "verified_name": "John’s Cake Shop",
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

## Recuperar um número de telefone único

Para consultar informações sobre um número de telefone, envie uma solicitação GET ao ponto de extremidade de [número de telefone do WhatsApp Business](/docs/graph-api/reference/whats-app-business-account-to-number-current-status/):

### Sintaxe da solicitação

```
GET https://graph.facebook.com/<API_VERSION>/<PHONE_NUMBER_ID>
```

### Exemplo de solicitação

```
curl \
'https://graph.facebook.com/v15.0/105954558954427/' \
-H 'Authorization: Bearer EAAFl...'
```

Em caso de sucesso, um objeto JSON é retornado com o nome, o número de telefone, o ID do telefone e as classificações de qualidade do número de telefone consultado.

```
{
  "code_verification_status" : "VERIFIED",
  "display_phone_number" : "15555555555",
  "id" : "105954558954427",
  "quality_rating" : "GREEN",
  "verified_name" : "Support Number"
}
```

## Consultar status do nome de exibição (beta)

Inclua `fields=name_status` como um parâmetro da string de consulta para consultar o status do nome de exibição associado a um número de telefone específico. No momento, esse campo está na versão beta e não está disponível para todos os desenvolvedores.

### Exemplo de solicitação

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

* `APPROVED` – o nome foi aprovado. Você já pode baixar o certificado.
* `AVAILABLE_WITHOUT_REVIEW` – o certificado do telefone está disponível, e o nome de exibição está pronto para ser usado sem análise.
* `DECLINED` – o nome não foi aprovado. Não é possível baixar o certificado.
* `EXPIRED` – o certificado expirou e não é mais possível baixá-lo.
* `PENDING_REVIEW` – a solicitação de nome está em análise. Não é possível baixar o certificado.
* `NONE` – não há certificados disponíveis.

Os certificados têm validade de sete dias.

## Como excluir números de telefone comerciais

Apenas os administradores do portfólio empresarial podem excluir números de telefone comerciais. Além disso, os números não poderão ser excluídos se tiverem sido usados para enviar mensagens pagas nos últimos 30 dias.

### Como excluir números de telefone comerciais via Gerenciador do WhatsApp

Caso o número de telefone comercial tenha o status "Conectado", você precisará do seu PIN de confirmação em duas etapas para excluir o número.

1. Carregue seu portfólio empresarial no [Gerenciador do WhatsApp](https://business.facebook.com/wa/manage/home/).
2. Se o painel Números de telefone não carregar automaticamente, navegue até **Ferramentas da conta** (ícone de caixa de ferramentas) > **Telefones**.
3. Clique no ícone da lixeira do número de telefone e conclua o fluxo.

Caso o número tenha sido usado para enviar mensagens pagas nos últimos 30 dias, redirecionaremos você para o painel **Insights**, que mostra a data da última mensagem paga. A exclusão do número de telefone poderá ser feita 30 dias após a data listada.

### Como excluir números de telefone comerciais via API

Não é possível excluir um número de telefone comercial via API.

## Como migrar números de telefone comerciais

É possível [migrar números de telefone de uma WABA para outra](/docs/whatsapp/solution-providers/support/migrating-phone-numbers-among-solution-partners-via-embedded-signup), bem como [migrar um número da API Local para a API de Nuvem](/docs/whatsapp/cloud-api/guides/migrating-from-onprem-to-cloud).

## Componentes de conversa

Você pode habilitar componentes de interface do usuário para que os usuários do WhatsApp interajam por mensagem com sua empresa mais facilmente. Consulte [Componentes de conversa](/docs/whatsapp/cloud-api/phone-numbers/conversational-components).

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Números de telefone comerciais](#n-meros-de-telefone-comerciais)

[Como registrar números de telefone comerciais](#como-registrar-n-meros-de-telefone-comerciais)

[Requisitos de qualificação](#requisitos-de-qualifica--o)

[Métodos de registro](#m-todos-de-registro)

[Status](#status)

[Como ver o status via Gerenciador do WhatsApp](#como-ver-o-status-via-gerenciador-do-whatsapp)

[Como receber o status via API](#como-receber-o-status-via-api)

[Nomes de exibição](#nomes-de-exibi--o)

[Perfis empresariais](#perfis-empresariais)

[Status de conta comercial oficial](#status-de-conta-comercial-oficial)

[Confirmação em duas etapas](#confirma--o-em-duas-etapas)

[Como alterar seu PIN via Gerenciador do WhatsApp](#como-alterar-seu-pin-via-gerenciador-do-whatsapp)

[Como alterar seu PIN via API](#como-alterar-seu-pin-via-api)

[Como desabilitar a confirmação em duas etapas](#como-desabilitar-a-confirma--o-em-duas-etapas)

[0800 e números gratuitos](#0800-e-n-meros-gratuitos)

[Limite de números registrados](#limite-de-n-meros-registrados)

[Verificar números de telefone](#verificar-n-meros-de-telefone)

[Parâmetros](#par-metros)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo](#exemplo)

[WhatsApp user phone number formats](#whatsapp-user-phone-number-formats)

[Verificação de alteração de identidade](#verifica--o-de-altera--o-de-identidade)

[Sintaxe da solicitação](#sintaxe-da-solicita--o)

[Corpo do post](#corpo-do-post)

[Exemplo de solicitação para habilitar a configuração](#exemplo-de-solicita--o-para-habilitar-a-configura--o)

[Exemplo de resposta a essa solicitação](#exemplo-de-resposta-a-essa-solicita--o)

[Exemplo de envio de mensagem com verificação](#exemplo-de-envio-de-mensagem-com-verifica--o)

[Webhooks](#webhooks)

[Como consultar o nível da taxa de transferência de dados](#como-consultar-o-n-vel-da-taxa-de-transfer-ncia-de-dados)

[Recuperar todos os números de telefone](#recuperar-todos-os-n-meros-de-telefone)

[Sintaxe da solicitação](#sintaxe-da-solicita--o-2)

[Exemplo de resposta](#exemplo-de-resposta)

[Filtrar números de telefone](#filtrar-n-meros-de-telefone)

[Recuperar um número de telefone único](#recuperar-um-n-mero-de-telefone--nico)

[Sintaxe da solicitação](#sintaxe-da-solicita--o-3)

[Exemplo de solicitação](#exemplo-de-solicita--o-2)

[Consultar status do nome de exibição (beta)](#consultar-status-do-nome-de-exibi--o--beta-)

[Exemplo de solicitação](#exemplo-de-solicita--o-3)

[Exemplo de resposta](#exemplo-de-resposta-2)

[Como excluir números de telefone comerciais](#como-excluir-n-meros-de-telefone-comerciais)

[Como excluir números de telefone comerciais via Gerenciador do WhatsApp](#como-excluir-n-meros-de-telefone-comerciais-via-gerenciador-do-whatsapp)

[Como excluir números de telefone comerciais via API](#como-excluir-n-meros-de-telefone-comerciais-via-api)

[Como migrar números de telefone comerciais](#como-migrar-n-meros-de-telefone-comerciais)

[Componentes de conversa](#componentes-de-conversa)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_Afjqll4Mhg0CCpKuBDZGVfun35tEjnPiFsAdpXBQXniqXw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfgQsTBc6UJJGKqMSgpvbJPaHwVwmGyjF4bNGBRFtH_NZQ&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_Afi-WW9f1bb_4Cfug8HS92bsmKzlIWqhVwCg3fKgzzjywA&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT00eRcq3RcILKhHxONt7Db4IoZupwN2zhMNtRznX9QEWtGAhPk6OtlcolUfpOAbegYd1zYgpjYUgxk36QBw0-WXuiWdcCaMiaUAAHFVZVnl4WUrWjRES3jjGRKEY1XJclZ0kVgKDX6ycYLwwuWuDQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_Afga918zvybUkfG6IhyEtmVr19eJ-IufyJKWqZmC0EcLOQ&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT22KoDjle2KA-APf6VbA_gZjW0Qnl50C_GGFFLTr6QJcYeT3X9ja5izwBscO1Ixs2YvmUU2nbJuwGyuSSAvPNQWJ9m2TQ2yxd4vbyCk2ukhcUZDRxoskFu9uJ6CpnTMsHIoTeQGxhPjlDiSF7K1dQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfgSSsV7yAKJjK1AQCf6TBJS9pF20V7dQVh8pe2Zl_8zxA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2Zw4_T2bQgIrgoLv1jZhH3H5e2qGF1SavTQpGdOGPDrIfS7RZcI6ueQ-9jirAG9k3i4CXpXpQNh6mUJIHZoMWvnjCnmNhCtXhBHzGPjwVzUH0En5oHhmKfXhrBzQdBrbfVZiYGAXSyj6foX5CLHw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_Afi0wQV54xo2M5NZpax9VgqKaUCWUos2fxFQCrMEDNKFJQ&oe=694035F0)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1jDaTV3YXRmr6GAb0eiZsT29GKD8Gsv06Vz3CHKo_2xPrhb-iNCHNO-seTy7q5-_Y0C_EQ9G-32bNIIDWhn1BEwXzhkpj2q8Qb83aD44N_0OjDuLLQ48S27XEcwABzdAML3bkduPI61qBsuL9ImA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT2AbszQCjF0HIRfqHPG4Iuv5659Lob7OgF8btrwMQTdOGrZVB5QExt-gtB3HkaI0s4TKPBkai9D6HWkFPaCY87bNbr70Ze1sMQmVpbvDlGd0rlA6GB9BRqnNOTnhaDlD1PUPjV5DqHbMLpdS48in3gV31HDFQA6E9Y)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT04jNgH5S_ngmOdlFaVKfLoaiMJ33IYiyGUXY0hEtvDgjFwSQxJe8aR-sTqQuqQYfNi2k6uUMpkmFNwbfbeZFTMQQoI2_3oK7S48KhYtNYBXzS0XSQ8rEBnQjacXH0YRIqLj-FdiqEBcecFwh5wUA)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_Afit9M2o_JgB6XXmma-WBFj50nx0U2NxMaTAjB5yInuAbA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfjNiqOwFKXl8E28zWGp17LCQFwwk54l2ywZGzpqAeJGFQ&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT3P_yb-nrrKeJy9xJlbmbTmC6Mtn6VfxSSU2NYQm6xaVRMu0kdu6J2nbIhX_GWYy7xWguTIJw5k0-aibBoWfuQQXja-IpoSiLuphXP7GXI-xIPN8da-tio9kGMXYtHs0dMcakDnINgXKsddE2DJLQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfhRVaHupSImN8nO3BBTAYiYcDhByNJ3BFSU0VFhukRN9w&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1vq3ZoyV9X5tC545_LmPAu_5eun56U7D_EAJLD3bFzHd1uGh9FkXu_wf-1V1Lu-zl1UwMtvD7-fYsH7AyoOiIJw9XugKWEY9F6bQgDz4IuR3Y1LINPay3Fq_R-9cQc2CvtcZ4iYqkER9J58hLpPQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfhY0KAGho_JOz1uSosep2Hr8wnDTJ1kwdx9hOV0J_euhg&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2sJryXLAY9icKswdBocBVE-0OHou7htgmQyCS6u5lmaGTeRnKhpsB4VGZRUlBkZLJeZjMkeLdMkTxmDOFlOnQAMzegH7Zrk1DvZrvxKA3Bry1fPaXnJmxbY38BTviw8yklqWokQzrnLSuBR1p9hQ)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=YchNqSAR0ZKnVwaTVTacBw&oh=00_AfjKszwSvq4QFebkcFlZwEHfH1uLSkIp96n9ltIIm87j6w&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT2FpgIwPVNUfWFRRB_GHkqzhSh7InrfuJNFsZX75rH-r3reccua-dht75vWgZ3rD6GyvmVShK83lxFJ-tCbtt3kiY6DSo2sRa_Cdt6KLNH9oeb3pszaKs1gaM1x2YiqdwXWNeHx5XT-ls4ivDXfUceaVf9OThef5mI)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT3QXXaZfUioOlFnG1WDx6fezkeXMgfxfJhpBPP9IvhFeUPsw3yRLPASYEU0h4cKCOfeVfjFapPChvb3qDXXSA6uVh0u9YH2eWjPHHC3ZzbrY54U8rYCGBiTLvQ-WTfGlbgA9JWxiyQvidbIV15kBQ)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)