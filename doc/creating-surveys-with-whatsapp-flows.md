+++
id = "creating-surveys-with-whatsapp-flows"
title = "Creating Surveys with WhatsApp Flows"
summary = "O WhatsApp Flows otimiza e simplifica como as empresas coletam dados do cliente."
source = "https://developers.facebook.com/docs/whatsapp/creating-surveys-with-whatsapp-flows"
lang = "en"
tags = ["whatsapp-business-platform", "webhooks"]
+++
# Creating Surveys with WhatsApp Flows

#### De Gafi G & Iryna Wagner

O WhatsApp Flows otimiza e simplifica como as empresas coletam dados do cliente. Sua organizacao pode facilmente absorver informacoes estruturadas provenientes das interacoes com os clientes, que, por sua vez, desfrutam de uma experiencia positiva do usuario. O WhatsApp Flows funciona bem para a coleta de dados de geracao de cadastros, realizando pesquisas, ajudando clientes a agendar horarios, enviando perguntas e preocupacoes do cliente e muito mais.

O melhor de tudo e que voce pode oferecer aos seus clientes essas opcoes sem precisar desenvolver um app e back-end complexos. Para isso, basta usar o WhatsApp como front-end e empregar um webhook para capturar as respostas como mensagens JSON, processar as informacoes e recuperar os dados de que voce precisa.

Usando uma empresa ficticia como exemplo, este tutorial explica como configurar uma pesquisa do cliente no WhatsApp usando webhooks. A pesquisa coletara feedbacks para saber como o cliente descobriu a empresa e quais sao seus tipos preferidos de passeios. Dessa forma, a empresa podera atender melhor aos clientes futuros e atuais.

## Realizando uma pesquisa com o WhatsApp Flows

### Pre-requisitos

Para conseguir acompanhar o tutorial, voce deve ter:

* Conhecimento basico em Python
* [Python](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.python.org%2Fdownloads%2F&h=AT19eSpcRHZxKwaj-QtAtI53QgJChXqVh5HNiMKd83hDoApEsehLfUygQbeVqYOLBBowV9gaqQfsvlptfSE-uUZ0eYF6A69m_Uy6zBAMtMVySibYU95q1G6tMpjAnjat56eLmkVsJKtjA_WlAA-8hQ) instalado no seu ambiente de trabalho
* [ngrok](https://l.facebook.com/l.php?u=https%3A%2F%2Fngrok.com%2Fdownload&h=AT0Y2q7AWyDkDVrkSOl9GgivVQBz0L4HpPtaDjleDeNGyGXNvEe21WzfvEJjd7GjAQN_dOewYc6gdrsdQAcOGkOTXuvtSfbasl4wnqsfvC7gJVR8Hu459rBM_tZ0aiGyd-s2LXZB0bjDkjTkRDa3_A) instalado no seu ambiente de trabalho
* Conta de desenvolvedor no [Meta for Developers](https://developers.facebook.com/)
  + Familiaridade com a integracao da [API de Nuvem](https://developers.facebook.com/docs/whatsapp/cloud-api/)
  + [Feito a conclusao das etapas para usar o Flows](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted) na sua conta, incluindo [verificar a conta](https://developers.facebook.com/docs/development/release/business-verification/)
  + Token de acesso da conta e identificacao do numero de telefone
  + Numero de telefone do destinatario
* Um editor de codigo, como o [Visual Studio Code](https://l.facebook.com/l.php?u=https%3A%2F%2Fcode.visualstudio.com%2FDownload&h=AT0MihPjuhfhF4tkfH38n_XMLuSw31527QSWb2fZGpu6W4ea-QCBQnR7ogZJr23HTfC1NOqmly_s2beRzxkAQ6B3bpsMhStvWhf4ax9DbKFE_EvivChQQK0tnx3lx-6pob87Cy5rJ0BnEvM3UQ_EPg)

### O processo

1. Crie um app [Flask](https://l.facebook.com/l.php?u=https%3A%2F%2Fflask.palletsprojects.com%2F&h=AT2lWclM5iD1KNulKIIilp3iQP9-2R3SAzFQjTOK7B312r7EYebm3igooQvc0rNaYHX-NOPPFZxsRglWr6E0447NW7Q1RhS2x58VFfqDp-f4vbqk7c2XEhj4K75rBT-MLNQ4LmdY6JCNM27cD5kveg).
2. Escreva o codigo Python para criar e publicar o fluxo usando a [WhatsApp Flows API](https://developers.facebook.com/docs/whatsapp/flows/reference/flowsapi). O codigo Python tambem enviara o fluxo publicado usando a API de Nuvem.
3. Crie um webhook para ouvir a mensagens de bate-papo.
4. Execute o app.

Se quiser ver uma previa do projeto, visualize o [codigo completo](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-Flows-Tools%2Fblob%2Fmain%2Farticles%2Fcreating-surveys%2Fmain.py&h=AT1CQNESnFOymN-MbgBnwub3_-ddMjWRHhFW2QpDPISPipSjmGR3ClX46p5pB8la9I7vYCRbbER_5a2EUJs-m4EJvlUxGheO8v-PteKTU45y-44eaWedbzTa2MH_aWC2s72CCPtLMFw9EaJxPuM-dg).

## Criando uma pesquisa com a API do WhatsApp Flows

Ha duas formas de criar um fluxo: usando o [Flow Builder UI](https://developers.facebook.com/docs/whatsapp/flows/introduction/flowbuilderui/) ou a Flows API. Este tutorial usa a Flows API para configurar a pesquisa programaticamente.

Para criar um fluxo que usa dados dinamicos do seu servidor, voce pode [criar um ponto de extremidade](https://developers.facebook.com/docs/whatsapp/flows/introduction/regularflowsandaddingendpointstoyourflows) conectando a pesquisa ao seu proprio servidor. Com um ponto de extremidade, voce pode controlar a logica de navegacao entre as telas de fluxo, preencher os dados de fluxo do seu servidor, ou mostrar/ocultar componentes na tela com base na interacao com o usuario.

O exemplo de fluxo de pesquisa que sera discutido nao usa nenhum ponto de extremidade, pois nao ha troca de dados dinamicos entre ele e um servidor. Voce usara o webhook do bate-papo para coletar as informacoes da pesquisa. Alem disso, pode [anexar fluxos a um modelo de mensagem](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted/sendingaflow#templatemessages) no Gerenciador do WhatsApp.

### Crie um app Flask

Primeiro, crie um app Flask para interagir com a Flows API. Execute o comando a seguir no seu terminal para criar um ambiente virtual.

```
python -m venv venv
```

Depois, use o comando abaixo para ativar o ambiente.

```
source venv/bin/activate
```

Em seguida, use o comando a seguir para instalar os pacotes necessarios.

```
pip install requests flask python-dotenv
```

Voce usara o Flask para criar rotas e interagir com a Flows API, para enviar solicitacoes HTTP e python-dotenv para carregar variaveis de ambientes.

Agora, crie um arquivo de ambiente chamado .env e cole-o nas seguintes informacoes.

```
VERIFY_TOKEN =
ACCESS_TOKEN =
WHATSAPP_BUSINESS_ACCOUNT_ID =
PHONE_NUMBER_ID =
```

Atribua os valores com base nas informacoes da conta de desenvolvedor. Voce pode usar qualquer cadeia de caracteres para `VERIFY_TOKEN`. As variaveis `WHATSAPP_BUSINESS_ACCOUNT_ID` e `PHONE_NUMBER_ID` sao os identificadores unicos da sua conta e sao gerados automaticamente pela Meta. `The ACCESS_TOKEN` e para autenticar e autorizar as solucoes da API.

Para acessar essas informacoes no painel do app da Meta, clique em **WhatsApp > Configuracao da API** no painel de navegacao esquerdo, como na captura de tela abaixo.

Por fim, no mesmo diretorio, crie um arquivo chamado main.py para conter a logica Python para a criacao dos fluxos e webhooks.

### Criando o fluxo

Para criar o fluxo, primeiro adicione os seguintes pacotes a `main.py`.

```
import os
import uuid
import requests
from dotenv import load_dotenv
from flask import Flask, request, make_response, json
```

Depois, adicione o seguinte trecho de codigo a `main.py` para inicializar as variaveis. O trecho tambem inicia o Flask e chama o metodo `load_dotenv()` para ajudar a carregar as variaveis.

```
app = Flask(__name__)

load_dotenv()
PHONE_NUMBER_ID = os.getenv('PHONE_NUMBER_ID')
VERIFY_TOKEN = os.getenv('VERIFY_TOKEN')
ACCESS_TOKEN = os.getenv('ACCESS_TOKEN')
WHATSAPP_BUSINESS_ACCOUNT_ID = os.getenv('WHATSAPP_BUSINESS_ACCOUNT_ID')
created_flow_id = ""
messaging_url = f"https://graph.facebook.com/v18.0/{PHONE_NUMBER_ID}/messages"

auth_header = {"Authorization": f"Bearer {ACCESS_TOKEN}"}

messaging_headers = {
    "Content-Type": "application/json",
    "Authorization": f"Bearer {ACCESS_TOKEN}",
}
```

Em seguida, adicione a seguinte rota para criar um fluxo.

```
@app.route("/create-flow", methods=["POST"])
def create_flow():
    flow_base_url = (
        f"https://graph.facebook.com/v18.0/{WHATSAPP_BUSINESS_ACCOUNT_ID}/flows"
    )
    flow_creation_payload = {"name": "<FLOW-NAME>", "categories": '["SURVEY"]'}
    flow_create_response = requests.request(
        "POST", flow_base_url, headers=auth_header, data=flow_creation_payload
    )

    try:
        global created_flow_id
        created_flow_id = flow_create_response.json()["id"]
        graph_assets_url = f"https://graph.facebook.com/v18.0/{created_flow_id}/assets"

        upload_flow_json(graph_assets_url)
        publish_flow(created_flow_id)

        print("FLOW CREATED!")
        return make_response("FLOW CREATED", 200)
    except:
        return make_response("ERROR", 500)
```

A funcao chama o ponto de extremidade dos fluxos `(flow_base_url)` enquanto transmite a carga `(flow_creation_payload)` contendo o nome e a categoria do fluxo. Os possiveis valores da categoria sao: `SIGN_UP`, `SIGN_IN`, `APPOINTMENT_BOOKING`, `LEAD_GENERATION`, `CONTACT_US`, `CUSTOMER_SUPPORT`, `SURVEY` ou `OTHER`.

Substitua `<FLOW-NAME>` pelo nome desejado, por exemplo, survey\_flow.

Depois que o codigo criar o fluxo, ele extraira o `created_flow_id` para carregar o corpo JSON.

### Carregando os componentes JSON do fluxo

Crie um arquivo `survey.json` com [estes conteudos](https://l.facebook.com/l.php?u=https%3A%2F%2Fgithub.com%2FWhatsApp%2FWhatsApp-Flows-Tools%2Fblob%2Fmain%2Farticles%2Fcreating-surveys%2Fsurvey.json&h=AT0-I-bQr9FwkMLpKVefRy_VEErgIU0vYyqz3sqjesA-SyGjjwGjKf_u48XX43kpgqDAhgB7WOsbpdUzWkr9XoO_LALPzA7gsugPwvOT7CbLL01BVwe0SetzREL5YmdkHXt6MpPyv7vwz7eNWHA-FfAHaQpIIcqxZZc). O JSON contem a estrutura do fluxo.

Em seguida, cole o seguinte codigo no arquivo `main.py`.

```
def upload_flow_json(graph_assets_url):
    flow_asset_payload = {"name": "flow.json", "asset_type": "FLOW_JSON"}
    files = [("file", ("survey.json", open("survey.json", "rb"), "application/json"))]

    res = requests.request(
        "POST",
        graph_assets_url,
        headers=auth_header,
        data=flow_asset_payload,
        files=files,
    )
    print(res.json())
```

Essa funcao carrega os dados JSON de `survey.json` para o ponto de extremidade dos ativos do fluxo.

No trecho de codigo abaixo, quando o usuario aciona a acao do clique, ela inicia o `on-click-action`, coletando dados na carga. O campo `"name": "complete"` indica que o fluxo esta completo. Ele sera fechado e a carga sera enviada para o servidor do webhook.

```
...
"on-click-action": {
    "name": "complete",
    "payload": {
        "source": "${form.source}",
        "tour_type": "${form.tour_type}",
        "tour_quality": "${form.tour_quality}",
        "decision_influencer": "${form.decision_influencer}",
        "tour_guides": "${form.tour_guides}",
        "aspects_enjoyed": "${form.aspects_enjoyed}",
        "improvements": "${form.improvements}",
        "recommend": "${form.recommend}",
        "return_booking": "${form.return_booking}"
    }
}

...
```

Os valores dentro dos objetos de carga podem corresponder aos componentes do fluxo (que lembra [nomes de elementos nos formularios de HTML](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.w3schools.com%2Ftags%2Fatt_name.asp&h=AT2ClHGdr8xh4tTAkgJrqph-tcJoIB7M_dG8rUhetN6S4Yw84thmIlJFIOUenlAXxgtRlXOjFu1mqk1-VGoRQ2A7pCRFctV44JUmLzFQ61hqg2NyJzgxT2MjcOfI7HnWB4KoM7PbVYzVF9LCw_j7gA)) ou aos objetos de dados. As chaves associadas a esses valores de carga sao chamadas de nomes, semelhante a como voce atribui variaveis em linguagens de programacao.

Os elementos `data-source` tambem contem identificacoes que agem como chaves para os valores. O codigo envia essas identificacoes para as opcoes. Por exemplo, se o usuario selecionar `Likely` para `data-source` abaixo, o codigo enviara `1`. Quando tiver recebido os dados, voce podera corresponde-los com as fontes de dados.

```
...
{
    "type": "RadioButtonsGroup",
    "required": true,
    "name": "return_booking",
    "data-source": [
        {
            "id": "0",
            "title": "Very likely"
        },
        {
            "id": "1",
            "title": "Likely"
        },
        {
            "id": "2",
            "title": "Undecided"
        },
        {
            "id": "3",
            "title": "Unlikely"
        },
        {
            "id": "4",
            "title": "Very likely"
        }
    ]
}
...
```

O fluxo tem uma tela contendo nove perguntas com opcoes de multipla escolha, como abaixo.

Voce pode explorar os detalhes dos elementos JSON na [documentacao do desenvolvedor](https://developers.facebook.com/docs/whatsapp/flows/introduction/introflowjson#introduction).

### Publicando o fluxo

Depois, cole a funcao abaixo no arquivo `main.py` para adicionar a logica para publicar o fluxo. Um fluxo publicado esta pronto para producao e voce nao podera fazer mais mudancas.

```
def publish_flow(flow_id):
    flow_publish_url = f"https://graph.facebook.com/v18.0/{flow_id}/publish"
    requests.request("POST", flow_publish_url, headers=auth_header)
```

A funcao invoca o ponto de extremidade de publicacao enquanto transmite a identificacao do fluxo.

### Enviando o fluxo

Cole a seguinte funcao no arquivo `main.py` para enviar o fluxo a um usuario do WhatsApp. A funcao chama o ponto de extremidade das mensagens da API de Nuvem enquanto transmite a carga do fluxo.

```
def send_flow(flow_id, recipient_phone_number):
    # Generate a random UUID for the flow token
    flow_token = str(uuid.uuid4())

    flow_payload = json.dumps(
        {
            "type": "flow",
            "header": {"type": "text", "text": "Survey"},
            "body": {
                "text": "Your insights are invaluable to us  please take a moment to share your feedback in our survey."
            },
            "footer": {"text": "Click the button below to proceed"},
            "action": {
                "name": "flow",
                "parameters": {
                    "flow_message_version": "3",
                    "flow_token": flow_token,
                    "flow_id": flow_id,
                    "flow_cta": "Proceed",
                    "flow_action": "navigate",
                    "flow_action_payload": {"screen": "SURVEY_SCREEN"},
                },
            },
        }
    )

    payload = json.dumps(
        {
            "messaging_product": "whatsapp",
            "recipient_type": "individual",
            "to": str(recipient_phone_number),
            "type": "interactive",
            "interactive": json.loads(flow_payload),
        }
    )

    requests.request("POST", messaging_url, headers=messaging_headers, data=payload)
    print("MESSAGE SENT")
```

A carga do fluxo contem os [detalhes do fluxo](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted/sendingaflow). O campo `action.parameters.flow_token` permite que voce transmita um identificador unico para a mensagem do fluxo que sera enviada do cliente para seu webhook quando o fluxo estiver concluido. Para este tutorial, voce usara uma identificacao aleatoria (uuid). O codigo define o `action.parameters.flow_action_payload.screen` como `SURVEY_SCREEN`, que e a identificacao da tela que voce quer exibir quando o usuario clica em `action.parameters.flow_cta`.

### Definindo o webhook

A logica do webhook e bastante objetiva. Ela tem duas funcoes, `webhook_get` e `webhook_post`, que lida com solucoes `GET` e `POST` respectivamente. O codigo usa solicitacoes `GET` quando adiciona o webhook ao seu app da Meta. Ele retorna o `hub.challenge` da solicitacao quando bem-sucedido. A solicitacao `POST` imprime a carga da mensagem no terminal.

```
@app.route("/webhook", methods=["GET"])
def webhook_get():
    if (
        request.args.get("hub.mode") == "subscribe"
        and request.args.get("hub.verify_token") == VERIFY_TOKEN
    ):
        return make_response(request.args.get("hub.challenge"), 200)
    else:
        return make_response("Success", 403)
```

A solicitacao `POST` extrai e processa a carga da mensagem. Como o codigo so atende a carga da mensagem, ele gera erros ao capturar qualquer outra carga. Por esse motivo, voce usa uma instrucao `if` para verificar se ha um corpo `messages`. Apos verificar se o corpo JSON das `messages` esta presente, outra verificacao e realizada para extrair apenas o numero de telefone do remetente se houver um corpo `text` na carga das `messages`.

```
@app.route("/webhook", methods=["POST"])
def webhook_post():
    # checking if there is a messages body in the payload
    if (
        json.loads(request.get_data())["entry"][0]["changes"][0]["value"].get(
            "messages"
        )
    ) is not None:
        """
        checking if there is a text body in the messages payload so that the sender's phone number can be extracted from the message
        """
        if (
            json.loads(request.get_data())["entry"][0]["changes"][0]["value"][
                "messages"
            ][0].get("text")
        ) is not None:
            user_phone_number = json.loads(request.get_data())["entry"][0]["changes"][
                0
            ]["value"]["contacts"][0]["wa_id"]
            send_flow(created_flow_id, user_phone_number)
        else:
            flow_reply_processor(request)

    return make_response("PROCESSED", 200)
```

Alem disso, voce deve usar a seguinte funcao auxiliar chamada `flow_reply_processor` para extrair uma resposta do fluxo e envia-la para o usuario. Como a resposta do fluxo contem a identificacao da opcao selecionada ao coletar dados do `RadioButtonsGroups`, a funcao corresponde as identificacoes com valores de cadeia de caracteres correspondentes.

```
def flow_reply_processor(request):
    flow_response = json.loads(request.get_data())["entry"][0]["changes"][0]["value"][
        "messages"
    ][0]["interactive"]["nfm_reply"]["response_json"]

    flow_data = json.loads(flow_response)
    source_id = flow_data["source"]
    tour_type_id = flow_data["tour_type"]
    tour_quality_id = flow_data["tour_quality"]
    decision_influencer_id = flow_data["decision_influencer"]
    tour_guides_id = flow_data["tour_guides"]
    aspects_enjoyed_id = flow_data["aspects_enjoyed"]
    improvements_id = flow_data["improvements"]
    recommend_id = flow_data["recommend"]
    return_booking_id = flow_data["return_booking"]

    match source_id:
        case "0":
            source = "Online search"
        case "1":
            source = "Social media"
        case "2":
            source = "Referral from a friend/family"
        case "3":
            source = "Advertisement"
        case "4":
            source = "Others"

    match tour_type_id:
        case "0":
            tour_type = "Cultural tour"
        case "1":
            tour_type = "Adventure tour"
        case "2":
            tour_type = "Historical tour"
        case "3":
            tour_type = "Wildlife tour"

    match tour_quality_id:
        case "0":
            tour_quality = "1 - Poor"
        case "1":
            tour_quality = "2 - Below Average"
        case "2":
            tour_quality = "3 - Average"
        case "3":
            tour_quality = "4 - Good"
        case "4":
            tour_quality = "5 - Excellent"

    match decision_influencer_id:
        case "0":
            decision_influencer = "Positive reviews"
        case "1":
            decision_influencer = "Pricing"
        case "2":
            decision_influencer = "Tour destinations offered"
        case "3":
            decision_influencer = "Reputation"

    match tour_guides_id:
        case "0":
            tour_guides = "Knowledgeable and friendly"
        case "1":
            tour_guides = "Knowledgeable but not friendly"
        case "2":
            tour_guides = "Friendly but not knowledgeable"
        case "3":
            tour_guides = "Neither of the two"
        case "4":
            tour_guides = "I didnt interact with them"

    match aspects_enjoyed_id:
        case "0":
            aspects_enjoyed = "Tourist attractions visited"
        case "1":
            aspects_enjoyed = "Tour guide's commentary"
        case "2":
            aspects_enjoyed = "Group dynamics/interaction"
        case "3":
            aspects_enjoyed = "Activities offered"

    match improvements_id:
        case "0":
            improvements = "Tour itinerary"
        case "1":
            improvements = "Communication before the tour"
        case "2":
            improvements = "Transportation arrangements"
        case "3":
            improvements = "Advertisement"
        case "4":
            improvements = "Accommodation quality"

    match recommend_id:
        case "0":
            recommend = "Yes, definitely"
        case "1":
            recommend = "Yes, but with reservations"
        case "2":
            recommend = "No, I would not"

    match return_booking_id:
        case "0":
            return_booking = "Very likely"
        case "1":
            return_booking = "Likely"
        case "2":
            return_booking = "Undecided"
        case "3":
            return_booking = "Unlikely"

    reply = (
        f"Thanks for taking the survey! Your response has been recorded. This is what we received:\n\n"
        f"*How did you hear about our tour company?*\n{source}\n\n"
        f"*Which type of tour did you recently experience with us?*\n{tour_type}\n\n"
        f"*On a scale of 1 to 5, how would you rate the overall quality of the tour?*\n{tour_quality}\n\n"
        f"*What influenced your decision to choose our tour company?*\n{decision_influencer}\n\n"
        f"*How knowledgeable and friendly were our tour guides?*\n{tour_guides}\n\n"
        f"*What aspects of the tour did you find most enjoyable?*\n{aspects_enjoyed}\n\n"
        f"*Were there any aspects of the tour that could be improved?*\n{improvements}\n\n"
        f"*Would you recommend our tour company to a friend or family member?*\n{recommend}\n\n"
        f"*How likely are you to book another tour with us in the future?*\n{return_booking}"
    )

    user_phone_number = json.loads(request.get_data())["entry"][0]["changes"][0][
        "value"
    ]["contacts"][0]["wa_id"]
    send_message(reply, user_phone_number)

After the extraction, the following send_message function sends the responses to the sender.

def send_message(message, phone_number):
    payload = json.dumps(
        {
            "messaging_product": "whatsapp",
            "to": str(phone_number),
            "type": "text",
            "text": {"preview_url": False, "body": message},
        }
    )

    requests.request("POST", messaging_url, headers=messaging_headers, data=payload)
    print("MESSAGE SENT")
```

A funcao envia a resposta usando o ponto de extremidade de [mensagem de texto da API de Nuvem](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-messages/#text-messages).

O app precisa estar sendo executado antes de voce configurar o webhook no console do Meta for Developers. Portanto, use o comando `flask --app main run --port 5000` no seu terminal para executar o codigo. Voce vera a mensagem **`* Running on http://127.0.0.1:5000`** no terminal se tudo estiver configurado corretamente.

Em seguida, execute o comando `ngrok``http 5000` no terminal para obter um URL que mapeia seu app. Copie o link.

No console do Meta for Developers, em **WhatsApp** no painel de navegacao esquerdo, clique em **Configuracao**.

No cartao **Webhook**, clique em **Editar**. Depois, na caixa de dialogo no campo **URL de retorno**, adicione o URL copiado e o `/webhook`. No campo **Verificar token**, adicione o token da variavel `TOKEN` do arquivo `.env`.

Quando tiver concluido, clique em **Verificar e salvar**. A caixa de dialogo sera fechada. Clique em **Gerenciar** e consulte o campo **Mensagens**. As informacoes devem ser semelhantes a imagem abaixo, com o **URL de retorno**, informacoes ocultas sob **Verificar token**, e **Mensagens** listadas em **Campos de webhook**.

Agora, o webhook esta pronto.

## Executando o app

Em uma nova instancia terminal, execute o comando cURL abaixo para criar um fluxo.

```
curl --location --request POST 'http://127.0.0.1:5000/create-flow'
```

Na instancia terminal que exibe a saida do seu webhook, voce vera uma mensagem semelhante a mostrada abaixo.

Quando um usuario enviar uma mensagem ao seu numero do WhatsApp, ele recebera o fluxo como resposta, conforme mostrado na captura de tela abaixo.

Depois de concluir a pesquisa, ele recebera uma copia com as respostas fornecidas.

Qualquer mensagem que um usuario enviar para seu numero aciona o fluxo. Para seu caso de uso, personalize o codigo para enviar o fluxo da pesquisa apenas em situacoes especificas, por exemplo, depois que um usuario tiver conversado com sua empresa.

## Conclusao

O WhatsApp Flows melhora a experiencia do usuario por meio de interfaces interativas para coletar dados estruturados, como respostas a pesquisas para uma empresa de turismo hipotetica. A empresa cria um app Flask, implementa um codigo Python para gerar e implementa os fluxos via a WhatsApp Flows API, configura um webhook para ouvir mensagens recebidas e executa o app para habilitar a coleta de respostas a pesquisa.

Com o WhatsApp Flows, sua empresa pode coletar dados de forma simples e rapida, o que pode ajudar a melhorar as taxas de conclusao para as interacoes com clientes. Use um processo semelhante para configurar suas proprias pesquisas, oferecer suporte ao cliente, ajuda-los a agendar horarios e muito mais.

Continue explorando o potencial do WhatsApp Flows. [Experimente agora mesmo.](https://developers.facebook.com/docs/whatsapp/flows/gettingstarted)

TAGS

[Plataformas](https://developers.facebook.com/blog/platforms/)[WhatsApp](https://developers.facebook.com/blog/whats_app/)

### Explorar mais

[

20 de agosto de 2025

#### Grow Your Business and Stand Out: Why the New WhatsApp for Business Certification Matters for Developers](https://developers.facebook.com/blog/post/2025/08/20/grow-your-business-and-stand-out/)[

1 de julho de 2025

#### Create true end-to-end journeys with the WhatsApp Business Calling API](https://developers.facebook.com/blog/post/2025/07/01/whatsapp-business-calling-api-end-to-end-journey/)[

20 de marco de 2024

#### Adicionando o WhatsApp Flows a experiencia do seu chatbot](https://developers.facebook.com/blog/post/2024/03/20/adding-whatsapp-flows-to-your-chatbot-experience/)

### Receba nosso boletim informativo

Cadastre-se para receber atualizacoes mensais da Meta for Developers.

[Cadastre-se](/m/signup/)
