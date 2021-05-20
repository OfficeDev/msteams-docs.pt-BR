---
title: Mensagens proativas
description: Descreve que bots podem iniciar uma conversa em Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: cenários de equipes proativo troca de mensagens bot
ms.openlocfilehash: baf148d0f4d0a669de582dfca70ed5d5bed0274c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566786"
---
# <a name="proactive-messaging-for-bots"></a>Mensagens proativas para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma mensagem proativa é uma mensagem enviada por um bot para iniciar uma conversa. Talvez você queira que seu bot inicie uma conversa por vários motivos, incluindo:

* Mensagens de boas-vindas para conversas pessoais de bots.
* Respostas nas pesquisas.
* Notificações externas de eventos.

Enviar uma mensagem para iniciar um novo segmento de conversação é diferente de enviar uma mensagem em resposta a uma conversa existente: quando seu bot inicia uma nova conversa, não há conversa pré-existente para postar a mensagem. Para enviar uma mensagem proativa, você precisa:

1. [Decida o que você vai dizer](#best-practices-for-proactive-messaging)
1. [Obtenha a identificação única do usuário e o ID do inquilino](#obtain-necessary-user-information)
1. [Enviar a mensagem](#examples)

Ao criar mensagens proativas, você **deve** ligar `MicrosoftAppCredentials.TrustServiceUrl` e passar na URL do serviço antes de criar a que você usará para enviar `ConnectorClient` a mensagem. Se você não fizer isso, seu aplicativo receberá uma `401: Unauthorized` resposta. Para obter mais informações, consulte [as amostras abaixo](#net-example-from-this-sample).

## <a name="best-practices-for-proactive-messaging"></a>Melhores práticas para mensagens proativas

Enviar mensagens proativas aos usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários. No entanto, do ponto de vista deles, essa mensagem pode parecer chegar a eles completamente sem ser provocada, e no caso de mensagens de boas-vindas será a primeira vez que eles interagiram com seu aplicativo. Como tal, é muito importante usar essa funcionalidade com moderação (não spam seus usuários), e fornecer-lhes informações suficientes para deixá-los entender por que eles estão sendo mensagens.

As mensagens proativas geralmente se enquadram em uma das duas categorias: mensagens de boas-vindas ou notificações.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que para a maioria das pessoas que recebem a mensagem eles não terão contexto para o porquê de eles estarem recebendo. Esta também é a primeira vez que eles terão interagido com o seu aplicativo; é sua oportunidade de criar uma boa primeira impressão. As melhores mensagens de boas-vindas incluirão:

* **Por que eles estão recebendo esta mensagem.** Deve ser muito claro para o usuário por que eles estão recebendo a mensagem. Se o seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, avise-os em que canal foi instalado e potencialmente quem o instalou.
* **O que você oferece.** O que eles podem fazer com o seu aplicativo? Que valor você pode trazer para eles?
* **O que eles devem fazer a seguir.** Convide-os a experimentar um comando ou interagir com seu aplicativo de alguma forma.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você precisa garantir que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara do porquê da notificação ter ocorrido. Boas mensagens de notificação geralmente incluem:

* **O que aconteceu.** Uma clara indicação do que aconteceu para causar a notificação.
* **O que aconteceu com.** Deve ficar claro qual item/coisa foi atualizado para causar a notificação.
* **Who fiz isso.** Who tomou a ação que fez com que a notificação fosse enviada.
* **O que eles podem fazer sobre isso.** Facilite a tomada de ações dos seus usuários com base em suas notificações.
* **Como eles podem optar por sair.** Você precisa fornecer um caminho para que os usuários optem por não receber notificações adicionais.

## <a name="obtain-necessary-user-information"></a>Obtenha informações necessárias do usuário

Os bots podem criar novas conversas com um usuário Microsoft Teams individual obtendo o *ID exclusivo* do usuário e o *ID do inquilino.* Você pode obter esses valores usando um dos seguintes métodos:

* [Ao buscar a lista](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) da equipe a partir de um canal em que seu aplicativo está instalado.
* Ao caching-los quando um usuário [interage com seu bot em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).
* Quando um usuário é @mentioned em uma conversa de [canal,](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) o bot faz parte.
* Ao caching-los quando você [recebe o `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) evento quando seu aplicativo é instalado em um escopo pessoal, ou novos membros são adicionados a um canal ou bate-papo em grupo que.

### <a name="proactively-install-your-app-using-graph"></a>Instale proativamente seu aplicativo usando Graph

> [!Note]
> A instalação proativa de aplicativos usando gráficos está atualmente em beta.

Ocasionalmente, pode ser necessário enviar mensagens proativas aos usuários que não instalaram ou interagiram com seu aplicativo anteriormente. Por exemplo, você deseja usar o [comunicador](~/samples/app-templates.md#company-communicator) da empresa para enviar mensagens para toda a sua organização. Para este cenário, você pode usar a API Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, em cache os valores necessários do evento que `conversationUpdate` seu aplicativo receberá no momento da instalação.

Você só pode instalar aplicativos que estão no seu catálogo de aplicativos organizacionais ou na loja de aplicativos Teams.

Consulte [Instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação Graph para obter detalhes completos. Há também uma [amostra em .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

## <a name="examples"></a>Exemplos

Certifique-se de autenticar e ter um token portador antes de criar uma nova conversa usando a API REST.

```json
POST /v3/conversations
{
  "bot": {
    "id": "28:10j12ou0d812-2o1098-c1mjojzldxcj-1098028n ",
    "name": "The Bot"
  },
  "members": [
    {
      "id": "29:012d20j1cjo20211"
    }
  ],
  "channelData": {
    "tenant": {
      "id": "197231joe-1209j01821-012kdjoj"
    }
  }
}
```

Você deve fornecer o ID do usuário e o ID do inquilino. Se a chamada for bem sucedida, a API retorna com o seguinte objeto de resposta.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

Esta ID é a id de conversa única do chat pessoal. Por favor, armazene esse valor e reutilize-o para futuras interações com o usuário.

### <a name="using-net"></a>Usando .NET

Este exemplo usa o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.

```csharp
// Create or get existing chat conversation with user
var response = client.Conversations.CreateOrGetDirectConversation(activity.Recipient, activity.From, activity.GetTenantId());

// Construct the message to post to conversation
Activity newActivity = new Activity()
{
    Text = "Hello",
    Type = ActivityTypes.Message,
    Conversation = new ConversationAccount
    {
        Id = response.Id
    },
};

// Post the message to chat conversation with user
await client.Conversations.SendToConversationAsync(newActivity, response.Id);
```

### <a name="using-nodejs"></a>Usando Node.js

```javascript
var address =
{
    channelId: 'msteams',
    user: { id: userId },
    channelData: {
        tenant: {
            id: tenantId
        }
    },
    bot:
    {
        id: appId,
        name: appName
    },
    serviceUrl: session.message.address.serviceUrl,
    useAuth: true
}

var msg = new builder.Message().address(address);
msg.text('Hello, this is a notification');
bot.send(msg);
```

## <a name="creating-a-channel-conversation"></a>Criar uma conversa de canal

Seu bot adicionado pela equipe pode postar em um canal para criar uma nova cadeia de respostas. Se você estiver usando o Node.js Teams SDK, use `startReplyChain()` o que lhe dá um endereço totalmente preenchido com o id de atividade correto e o id de conversação. Se você estiver usando C#, veja o exemplo abaixo.

Alternativamente, você pode usar a API REST e emitir uma solicitação POST para [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) o recurso.

### <a name="net-example-from-this-sample"></a>Exemplo .NET [(desta amostra](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))

```csharp
using Microsoft.Bot.Builder.Dialogs;
using Microsoft.Bot.Connector;
using Microsoft.Bot.Connector.Teams.Models;
using Microsoft.Teams.TemplateBotCSharp.Properties;
using System;
using System.Threading.Tasks;

namespace Microsoft.Teams.TemplateBotCSharp.Dialogs
{
    [Serializable]
    public class ProactiveMsgTo1to1Dialog : IDialog<object>
    {
        public async Task StartAsync(IDialogContext context)
        {
            if (context == null)
            {
                throw new ArgumentNullException(nameof(context));
            }

            var channelData = context.Activity.GetChannelData<TeamsChannelData>();
            var message = Activity.CreateMessageActivity();
            message.Text = "Hello World";

            var conversationParameters = new ConversationParameters
            {
                  IsGroup = true,
                  ChannelData = new TeamsChannelData
                  {
                      Channel = new ChannelInfo(channelData.Channel.Id),
                  },
                  Activity = (Activity) message
            };

            MicrosoftAppCredentials.TrustServiceUrl(serviceUrl, DateTime.MaxValue);
            var connectorClient = new ConnectorClient(new Uri(activity.ServiceUrl));
            var response = await connectorClient.Conversations.CreateConversationAsync(conversationParameters);

            context.Done<object>(null);
        }
    }
}
```

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)