![](https://facebook.com/security/hsts-pixel.gif)

[![](/images/developer/m4d_logo_july_2024.svg)](/?no_redirect=1)

[Documentos](/docs/)[Ferramentas](/tools/)[Suporte](/support/)[Entrar](https://business.facebook.com/business/loginpage/?next=https%3A%2F%2Fdevelopers.facebook.com%2Fdocs%2Fwhatsapp%2Foverview%2Fbusiness-accounts%3Fnav_ref%3Dbiz_unified_f3_login_page_to_dfc&login_options%5B0%5D=FB&login_options%5B1%5D=SSO&app=436761779744620&is_work_accounts=1&config_ref=biz_login_tool_flavor_dfc)

[Documentos](/docs/)[Plataforma do WhatsApp Business](/docs/whatsapp)[Sobre a plataforma](/docs/whatsapp/overview)[Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)

[Plataforma do WhatsApp Business](/docs/whatsapp)

* [Sobre a plataforma](/docs/whatsapp/overview)

  + [Contas do WhatsApp Business](/docs/whatsapp/overview/business-accounts)
  + [Official Business Accounts](/docs/whatsapp/official-business-accounts)
  + [Business-scoped user IDs](/docs/whatsapp/business-scoped-user-ids)
  + [Business profiles](/docs/whatsapp/business-profiles)
  + [Display names](/docs/whatsapp/display-names)
  + [Receber aceitação](/docs/whatsapp/overview/getting-opt-in)
  + [Identity Change](/docs/whatsapp/overview/identity-change)
  + [Códigos QR e links curtos](/docs/whatsapp/overview/qr-codes)
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

[Contas do WhatsApp Business](#contas-do-whatsapp-business)

[Limitações](#limita--es)

[Criar uma WABA via Painel de Apps](#criar-uma-waba-via-painel-de-apps)

[Criar uma WABA via provedor de soluções](#criar-uma-waba-via-provedor-de-solu--es)

[Criar uma WABA via Meta Business Suite](#criar-uma-waba-via-meta-business-suite)

[Como compartilhar a WABA com um provedor de soluções](#como-compartilhar-a-waba-com-um-provedor-de-solu--es)

[Notas](#notas)

[Se você ainda não tiver compartilhado um ativo com o parceiro](#se-voc--ainda-n-o-tiver-compartilhado-um-ativo-com-o-parceiro)

[Se você já tiver compartilhado um ativo com o parceiro](#se-voc--j--tiver-compartilhado-um-ativo-com-o-parceiro)

[Obter dados da WABA por meio da API](#obter-dados-da-waba-por-meio-da-api)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo de resposta](#exemplo-de-resposta)

[Acessar a WABA com o Gerenciador do WhatsApp](#acessar-a-waba-com-o-gerenciador-do-whatsapp)

[Webhooks](#webhooks)

[Enviar mensagens em nome do cliente](#enviar-mensagens-em-nome-do-cliente)

# Contas do WhatsApp Business

As contas do WhatsApp Business ("WABAs") representam uma empresa na Plataforma do WhatsApp Business. É preciso ter uma WABA para enviar e receber mensagens de usuários do WhatsApp, bem como criar e gerenciar modelos.

Veja diferentes maneiras de criar uma WABA descritas abaixo. Depois de criar a conta, recomendamos [conectar um número de telefone](https://www.facebook.com/business/help/456220311516626) e [configurar uma forma de pagamento](https://www.facebook.com/business/help/2225184664363779).

## Limitações

* Uma conta do WhatsApp Business (WABA) pode ter até 250 modelos de mensagem.
* Inicialmente, as contas comerciais da Meta podem ter dois números de telefone comerciais registrados. Entretanto, é possível aumentar esse limite para até 20. Consulte [Registered Number Limits](/docs/whatsapp/cloud-api/phone-numbers#registered-number-limits).
* Há um limite inicial de 20 WABAs para contas comerciais da Meta.
* A WABA precisa pertencer a apenas um Gerenciador de Negócios. Não é possível ter dois ou mais Gerenciadores de Negócios como proprietários de uma WABA.
* Não é possível editar o fuso horário e a moeda da WABA depois que uma linha de crédito é anexada. Não é possível migrar uma WABA de uma empresa para outra.

## Criar uma WABA via Painel de Apps

Caso você queira usar a API de Nuvem para enviar e receber mensagens, siga as etapas na documentação [Introdução](/docs/whatsapp/cloud-api/get-started). Depois de concluir as etapas mencionadas, você terá uma WABA e um número comercial de teste. Além disso, terá acesso à interface **Painel de Apps** > **WhatsApp** > **Configuração da API**.

A opção **Configuração da API** permite adicionar um número de telefone comercial de produção, o que gera uma nova WABA que é então associada ao número.

## Criar uma WABA via provedor de soluções

Se estiver trabalhando com uma empresa que oferece serviços de mensagens do WhatsApp para você por meio da API, esse provedor de soluções fornecerá as instruções. Normalmente, isso envolve a conclusão do fluxo de cadastro incorporado, que reúne informações sobre sua empresa e gera uma WABA para você. Depois, basta usar o app do provedor para acessar a WABA criada e os ativos relacionados.

Para saber mais, consulte o artigo da Central de Ajuda [Como criar uma conta do WhatsApp Business com provedores de soluções do WhatsApp Business](https://www.facebook.com/business/help/524220081677109).

## Criar uma WABA via Meta Business Suite

Esse recurso será lançado de forma gradual nas próximas semanas e pode não estar disponível para você imediatamente. No momento, não há disponibilidade para portfólios empresariais com endereço no Brasil ou na Índia.

Você pode criar uma WABA usando o [Meta Business Suite](https://business.facebook.com/). Use esse método se estiver trabalhando com um provedor de soluções que fornece serviços relacionados a mensagens do WhatsApp por meio do Meta Business Suite em vez da API de Nuvem.

Para criar uma WABA usando o Meta Business Suite:

1. Acesse <https://business.facebook.com/> e crie um portfólio empresarial ou entre na sua conta e selecione o portfólio existente, caso já tenha um.
2. Vá para o painel **Configurações** (ícone de engrenagem) > **Contas** > **Contas do WhatsApp**.
3. Clique no botão azul **+Adicionar** e, no menu suspenso, selecione **Crie uma nova conta do WhatsApp Business**.
4. Depois, complete o fluxo na janela **Criar uma conta do WhatsApp Business** (imagem abaixo).

## Como compartilhar a WABA com um provedor de soluções

Você pode compartilhar a WABA (ou qualquer um dos seus ativos de negócios) com um provedor de soluções verificado pela empresa (também conhecido como "parceiro") usando o Meta Business Suite. Após o compartilhamento, o parceiro poderá usar o Meta Business Suite para acessar sua WABA e fornecer serviços.

### Notas

* Se estiver compartilhando a WABA com um provedor de soluções (um tipo de parceiro que tem uma linha de crédito), receba primeiro a linha de crédito dele para que você possa usar o app fornecido por ele para enviar mensagens.
* É possível compartilhar uma WABA com até dois parceiros.

### Se você ainda não tiver compartilhado um ativo com o parceiro

1. Peça ao parceiro que informe a identificação do portfólio empresarial dele. Você precisará dessa informação para concluir as etapas restantes.
2. Entre no [Meta Business Suite](https://business.facebook.com/). Caso você tenha vários portfólios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opção.
3. Vá para o painel **Configurações** (ícone de engrenagem) > **Contas** > **Contas do WhatsApp**.
4. Na lista de WABAs, selecione sua conta ou clique no link **Detalhes**.
5. Na sobreposição de detalhes que aparece à direita (imagem abaixo), clique no botão **Atribuir parceiro**.
6. Na sobreposição **Compartilhar essa conta do WhatsApp com um parceiro**, insira a identificação do portfólio empresarial do parceiro e use os botões de alternância para definir quais permissões conceder. Depois, clique no botão **Atribuir**.
7. Se a WABA for compartilhada com o parceiro, você verá a mensagem **Parceiro adicionado**. Clique no botão **Concluir** para ignorá-la.
8. De volta à sobreposição de detalhes, clique na aba **Parceiros**.
9. Na aba **Parceiros**, confirme se o nome do parceiro aparece com as permissões apropriadas.
10. Informe ao parceiro que você compartilhou a WABA. Se apropriado, peça para ele compartilhar a linha de crédito, conforme explicado acima.

### Se você já tiver compartilhado um ativo com o parceiro

1. Entre no [Meta Business Suite](https://business.facebook.com/). Caso você tenha vários portfólios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opção.
2. Vá para o painel **Configurações** (ícone de engrenagem) > **Usuários** > **Parceiros**.
3. Na lista de parceiros, clique em um nome ou no link **Detalhes**.
4. Na sobreposição de detalhes que aparece à direita (imagem abaixo), clique no botão **Atribuir ativos**.
5. Na janela **Atribuir ativos e permissões**, clique no tipo de ativo **Contas do WhatsApp**.
6. Marque a caixa de seleção ao lado da sua WABA, use os botões de alternância para definir quais permissões conceder ao parceiro e clique no botão **Atribuir**.
7. Em caso de sucesso, você verá a mensagem **Ativos atribuídos**. Clique no botão **Concluir** para ignorar a janela.
8. Confirme que a WABA exibida na aba **Ativos que você atribuiu** tem as permissões adequadas.
9. Informe ao parceiro que você compartilhou a WABA. Se apropriado, peça para ele compartilhar a linha de crédito, conforme explicado acima.

## Obter dados da WABA por meio da API

Use o ponto de extremidade [GET /<WHATSAPP\_BUSINESS\_ACCOUNT\_ID>](/docs/graph-api/reference/whats-app-business-account#Reading) para obter dados de uma WABA. Use o parâmetro `fields` para solicitar campos específicos em uma WABA ou omita-o para obter campos padrão retornados pelo ponto de extremidade.

### Exemplo de solicitação

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

Você pode acessar sua WABA no Gerenciador do WhatsApp para ver informações básicas, como status do número de telefone comercial e métricas de mensagens. Também é possível executar tarefas simples, como criação e edição de modelos.

Para acessar sua WABA no Gerenciador do WhatsApp:

1. Entre no [Meta Business Suite](https://business.facebook.com/). Caso você tenha vários portfólios empresariais, use o menu suspenso no canto superior esquerdo para selecionar uma opção.
2. Vá para o painel **Configurações** (ícone de engrenagem) > **Contas** > **Contas do WhatsApp**.
3. Na lista de WABAs, selecione sua conta ou clique no link **Detalhes**.
4. Na aba **Resumo**, clique no botão **Gerenciador do WhatsApp**.

## Webhooks

Assine o webhook [account\_update](/docs/whatsapp/cloud-api/webhooks/reference/account_update) para receber notificações sobre alterações no status de uma conta do WhatsApp Business, incluindo mudanças devido a violações de políticas e termos.

Sempre que sua WABA violar uma política, você receberá uma notificação semelhante a esta:

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

Para ver uma lista de violações de política, consulte o nosso documento [Violações da Política da Plataforma do WhatsApp Business](/docs/whatsapp/overview/policy-enforcement/violations). Se uma restrição tiver sido imposta, um webhook **account\_update** será disparado, descrevendo a violação.

## Enviar mensagens em nome do cliente

O modelo de propriedade da WABA "Em nome de" está obsoleto e não é mais possível. Consulte a [suspensão do modelo Em nome de (OBO)](/docs/whatsapp/solution-providers/on-behalf-of/legacy-model-deprecation/) para saber mais.

![](https://www.facebook.com/tr?id=675141479195042&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=574561515946252&ev=PageView&noscript=1)![](https://www.facebook.com/tr?id=1754628768090156&ev=PageView&noscript=1)

Nesta Página

[Contas do WhatsApp Business](#contas-do-whatsapp-business)

[Limitações](#limita--es)

[Criar uma WABA via Painel de Apps](#criar-uma-waba-via-painel-de-apps)

[Criar uma WABA via provedor de soluções](#criar-uma-waba-via-provedor-de-solu--es)

[Criar uma WABA via Meta Business Suite](#criar-uma-waba-via-meta-business-suite)

[Como compartilhar a WABA com um provedor de soluções](#como-compartilhar-a-waba-com-um-provedor-de-solu--es)

[Notas](#notas)

[Se você ainda não tiver compartilhado um ativo com o parceiro](#se-voc--ainda-n-o-tiver-compartilhado-um-ativo-com-o-parceiro)

[Se você já tiver compartilhado um ativo com o parceiro](#se-voc--j--tiver-compartilhado-um-ativo-com-o-parceiro)

[Obter dados da WABA por meio da API](#obter-dados-da-waba-por-meio-da-api)

[Exemplo de solicitação](#exemplo-de-solicita--o)

[Exemplo de resposta](#exemplo-de-resposta)

[Acessar a WABA com o Gerenciador do WhatsApp](#acessar-a-waba-com-o-gerenciador-do-whatsapp)

[Webhooks](#webhooks)

[Enviar mensagens em nome do cliente](#enviar-mensagens-em-nome-do-cliente)

---

![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459257729_1010347667767763_3581566724399163588_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=8mhMcpIjeBkQ7kNvwHkP4-q&_nc_oc=AdlO3ZH_Jvl4nkiSl_NzPx_bZU9wlyyiBqGM7BftG4BZ-zyDTiz3IYeP9jzwyRa3MBM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_Afjcyq5S9IIDhxr9EWR15bWGI6La6AhBQ83KWXR-DHlrvw&oe=6940632C)

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459306853_1501629487899251_7449019458089488547_n.png?stp=dst-webp&_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=G9HoN6clJj0Q7kNvwHW8YOK&_nc_oc=Adl4qqjs2GQ_KCtPcQK5nkyFNKGk2VG_MDKDqJajF6afEsyVXYrgEfPJ8sL7u2Owi3A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfjcPCtFScuJLzTTEZEF3B9AjXkcGcDiw-LHftmx0ibffw&oe=694046E2)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458971466_433154499741175_6962021715663093697_n.png?stp=dst-webp&_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=Da_uV3THaUoQ7kNvwF1AAec&_nc_oc=Adms3y4JCEspj3ygUkhiNGbJFZR-oETEUXNTHEA9PBzDGOQ3eeaqgNfhJGrdKa1ekJ8&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfhwLyVn1scQp9PjqzkDCFj8IJQqoZqT5ad5uvs_jpzJdA&oe=6940434E)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT02TywaiE5WjyW2hcAqaOZWtUrI6hUM9veM-T_UfDewuqbwTJCRpuN2ev0xEBISZ5fiVhSyGKrSQMJG8bYqQcq2psUF1FqRBvATV-I558ZwVtBCX1wFKNzhp1MG2dwSojNkZXJBIId34zUI1zjxew)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459160202_540178488525397_747089945616031028_n.png?stp=dst-webp&_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=xMk3wRUIgeUQ7kNvwHqMDKx&_nc_oc=Adl6-yLpj-oA8nZLGCMRbDVjAOlD1TSf8Z_sncBFZKdi6sBbLBmhs0PA0e_ZoKfMA6g&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfjLIc71ASwBgLV9gEh4Qka2yu4WMvcV3Upmt2maRwchcA&oe=69406A98)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT1BngHI2Dm-pBuoMvZwx_jcG2Or9xficrJpQ5QRwo9naw4wmDTnbaafMCbjlet6CvZ20aP4XjpVy_WIGTS2QWga0Btb90EFtDFsTs2L1yOPiO7KqLxrh1nkw9wbasC7aA62NYvzXdUFssd672TIkg)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/458754681_1046279956748647_3773356972584952025_n.png?stp=dst-webp&_nc_cat=103&ccb=1-7&_nc_sid=e280be&_nc_ohc=g67ScHV0LcEQ7kNvwFE9SaD&_nc_oc=Adnm_fQarb-P9HecEp4ZJiFoXCpivyxrjjzjL9w5N3VW0FuM2Xg2me3lqs_ug_ob2Ns&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfiguwnxTfRWssgU_WBCGaFyPBHJLQKua4z141nviQ3uiA&oe=694048AC)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT2XoscI-IRU98tof8g3GKWJJ3hKgUBkI8L2lUGL4NENYkxnP7z85785QpHaM1mNX9ac3OKwKDZaPV3zSpjFCnYA7BW5axr0hKVC-wXuH5ZUDevCcHCzvjvRqX50ORK-hSmmhigxZ5CZJGUz44WrGw)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/459342489_501198322668453_7712071717227028092_n.png?stp=dst-webp&_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=PKQzoyB_GWYQ7kNvwHuQ3Qo&_nc_oc=AdlZ6PusCJjK-MqVyMbegbP9cF2-JParHbS_7SO6tVR_zRZ9As7h2c-aarjHrSmHSyM&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_Afh_HcM15eBmXYMTcZp7E_qP4u6LxzqFuIbPboLfV6NT_Q&oe=69406E30)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1w_c7YEmLoNjVUjXbSV0zRaebaSYmtWpmkc2k1Q-Wb49aDEQ4evO79Nq4DQs5uhLNgeM-cO7EtKqU3Qg9rOzhxaRb9FBMFbe_P9RqyIu71kI25yOXKHf2VVsSJcOMqSmpqDgpf9P9CvSP_JGqoMA)

#### Desenvolva com a Meta

* [IA](https://developers.meta.com/ai/)
* [Meta Horizon OS](https://developers.meta.com/horizon/)
* [Tecnologias sociais](/social-technologies/)
* [Dispositivos vestíveis](https://l.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.meta.com%2Fwearables%2F&h=AT3vgP81IdgLWk5ZtF94xjQBYMunXKHgARvaby9b0ZpgAeHjoR7H4X5jjy9ZUdPU9DJiYgA2-tIUIxj_-zUTicQ1FNzuEZB9u7zTF0h5nQUNZsIaT25XnQSjMyZtr1tDBMTPalOzg8RIFNgaKAYr7A)

#### Notícias

* [Meta for Developers](https://developers.meta.com/blog/)
* [Blog](/blog/)
* [Casos de sucesso](/success-stories/)

#### Suporte

* [Suporte ao desenvolvedor](/support/)
* [Ferramenta de bug](/support/bugs/)
* [Status da plataforma](https://l.facebook.com/l.php?u=https%3A%2F%2Fmetastatus.com%2F&h=AT2X3Yv4kBr5heGgj5218jg56nOHLNH4pptb8uu0Sx4fuyKHKnMALO34LkH4aYDdarcoECMAzIE3opyQJ4zZ9gHE2AgKgeTkoglSJdJ__N3yiMfkqQ9LMFd7ds7GGuNk6s7nC3MHikJRjtbUgzMn4Q)
* [Fórum da comunidade de desenvolvedores![](https://static.xx.fbcdn.net/rsrc.php/v4/yE/r/3AaI47RuuWt.png)](https://www.facebook.com/groups/fbdevelopers/)
* [Relatar um incidente](/incident/report/)

#### Termos e políticas

* [Iniciativas da plataforma responsável](/products/responsible-platform-initiatives/)
* [Termos da plataforma](/terms/)
* [Políticas do Desenvolvedor](/devpolicy/)

Siga-nos

* [![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89126182_222315695571651_4936319991919149056_n.svg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=jVaAdZR-cusQ7kNvwEcegmJ&_nc_oc=AdmiBraDOmtoE9jJ7N1ARcKhu2zRcVQhE-puYTPRNJUsLeThg-dmKW4EvjEgnWRXg-I&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfhiVDAof5IB9mV37FcXiKoHu4OBQ2UdQi6DbcyPmr91WA&oe=694042EF)](https://www.facebook.com/MetaforDevelopers)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89319900_506382610280628_2520212398984396800_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=866JCMN-YaAQ7kNvwGu2k-u&_nc_oc=AdnMSFXUTR6BKYOcgLBvfLhyyP4wTHaIBI7IncOuiCIKefiCT_DMS4-PSL-g0qU_7mg&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_Afhg1HoeSJjWxkkmKz8Ycn-DurALpBOVaitgt1vxFBRBlg&oe=69404E75)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.instagram.com%2Fmetafordevelopers%2F&h=AT1PtbCoP5iQZIc5df-toTr2RBzaUE26o2BlLSJi8M-KojnIFkh9t2S9QxSmvXPVjxr4HKPA-HiqLNOwqSIIj42EsF9kez8hP1zr4pEkODMND-kGrB4lGy3tSx37UNxOKgDmrNM4TomfJuEqj80U6A)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89154638_493934268150363_1123534170136510464_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=lAaTViSW3NMQ7kNvwFiDJyV&_nc_oc=AdkLWyM25HuFV6d_EdW-d15rekQ2Q0oWryVvfbpvP23K-D9qm0gIk6PzRhQiM9M49zY&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfiRrB4yHKqa6c6xBsC12I2IcGsiKW04W60gpFCWtxkZ3Q&oe=69406085)](https://l.facebook.com/l.php?u=https%3A%2F%2Ftwitter.com%2Fmetafordevs&h=AT2fMHNrroVXinoBAC2WqmLaJl8MUi3bT7GYS7W08mfM4lngqlT27FpHOnK8LCgPhbi2oSKqHqUX69T1Ti9Fq_JlQ6t_R281GaCkjzlIuvsnNXCUOPuqsaOJgFnFW-fvFW6xb_NcMegaMs3S7PhLVA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89354779_640044533453459_7031092369583767552_n.svg?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=YUHZv44W0BEQ7kNvwFsVK8a&_nc_oc=Admq0MiSpCD5BDCCMx7O3kdwvKMKzt4EaBIwfdVwAz6xt3mzqaiSvec83zvkwiZtn-k&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfgjzegNrAQ6tT3mQknSa78PA7boZVUpPJxe28__iGKaGA&oe=694051C6)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.linkedin.com%2Fshowcase%2Fmeta-for-developers%2F&h=AT3l2oeikmiavMR_HaCyVF5z5mQuA36XeIxHDEiAdEu9ZQ35tpm8TOErJX0dY5iVRa2H27hkCIxtW5NRFVYSRq2bKMdQ_ubebO9PY6TVxRAlPa5Imk71Z4MNRFmX_vi7Vtj68Jk0mlyjkGCGGh2cZA)[![](https://scontent.fpll10-1.fna.fbcdn.net/v/t39.2365-6/89127358_532616317687233_292625476315250688_n.svg?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=4eJmFx9fWJ0Q7kNvwET74gM&_nc_oc=Adn0VQn8zlM0qhkzEPsvh53FbUilR4Q1JZVrngx32iPmDOad4dTZI7h1ycnyqRss36A&_nc_zt=14&_nc_ht=scontent.fpll10-1.fna&_nc_gid=c0hW1Ji9v0mLflkB5z6eCw&oh=00_AfhikMlTAuZjxECtrTe2mPDzi_Wh1ZyW0asmBb5kBzNcqg&oe=69403994)](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.youtube.com%2FMetaDevelopers%2F&h=AT1B5kUKFVO_IHy_susL0cVrXN1ccUB0FYKyLbYt3LPdQpQ_A6EcINcDOWiarUuYHeQAWvwve-doT609NGdaP01jXJJV_QTxT3qKjallhqDf4_ZTfaE6cxrFruGFSil2ohxTxj4BSboZAzfb3ZYr3A)

© 2025 Meta

* [Sobre](https://l.facebook.com/l.php?u=https%3A%2F%2Fabout.fb.com%2F&h=AT2XMtWiK5Lca4l2I4_qiocxwImXU9G4ilGBhIg24XHie9rvSl4bcPAZ2aQgiR0Rzjof_wsj7Jb2SuuxOhuRPSh-F2GYZXjLFHTZlO8QgXBnSVg-7jWGWIjfoDzfbquJOJBTSimueHdF68_qgd9fnw)
* [Carreiras](https://www.facebook.com/careers)
* [Política de Privacidade](https://www.facebook.com/about/privacy)
* [Cookies](https://www.facebook.com/help/cookies)
* [Termos](https://www.facebook.com/policies)

Português (Brasil)Bahasa IndonesiaDeutschEnglish (US)EspañolEspañol (España)Français (France)ItalianoTiếng ViệtРусскийالعربيةภาษาไทย한국어中文(香港)中文(台灣)中文(简体)日本語

Português (Brasil)