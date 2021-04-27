---
title: Mensagens proativas
description: Descreve que os bots podem iniciar uma conversa no Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: teams scenarios proactive messaging conversation bot
ms.openlocfilehash: a13c565c8abe8c78fe6402d76796381b6a837393
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019787"
---
# <a name="proactive-messaging-for-bots"></a>Mensagens proativas para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma mensagem proativa é uma mensagem enviada por um bot para iniciar uma conversa. Talvez você queira que seu bot inicie uma conversa por vários motivos, incluindo:

* Mensagens de boas-vindas para conversas pessoais do bot
* Respostas a votações
* Notificações de eventos externos

Enviar uma mensagem para iniciar um novo thread de conversa é diferente de enviar uma mensagem em resposta a uma conversa existente: quando o bot inicia uma nova conversa, não há nenhuma conversa pré-existente para a postagem da mensagem. Para enviar uma mensagem proativa, você precisa:

1. [Decida o que você vai dizer](#best-practices-for-proactive-messaging)
1. [Obter a ID exclusiva do usuário e a ID do locatário](#obtain-necessary-user-information)
1. [Enviar a mensagem](#examples)

Ao criar mensagens  proativas, você deve chamar e passar a URL do serviço antes de criar o que você `MicrosoftAppCredentials.TrustServiceUrl` usará para enviar a `ConnectorClient` mensagem. Se você não fizer isso, seu aplicativo receberá uma `401: Unauthorized` resposta. Consulte [os exemplos abaixo](#net-example-from-this-sample).

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários. No entanto, do ponto de vista deles, essa mensagem pode parecer chegar a eles completamente não prompted e, no caso de mensagens de boas-vindas, será a primeira vez que elas interagirão com seu aplicativo. Dessa forma, é muito importante usar essa funcionalidade com moderação (não spam seus usuários) e fornecer informações suficientes para que eles entendam por que estão sendo mensagens.

As mensagens proativas geralmente se enquadram em uma das duas categorias: mensagens de boas-vindas ou notificações.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas que recebem a mensagem, elas não terão contexto para o motivo pelo qual a estão recebendo. Essa também é a primeira vez que eles interagem com seu aplicativo; é sua oportunidade de criar uma boa primeira impressão. As melhores mensagens de boas-vindas incluirão:

* **Por que eles estão recebendo essa mensagem.** Deve ser muito claro para o usuário por que ele está recebendo a mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e, potencialmente, quem o instalou.
* **O que você oferece.** O que eles podem fazer com seu aplicativo? Qual valor você pode trazer para eles?
* **O que eles devem fazer em seguida.** Convide-os para experimentar um comando ou interagir com seu aplicativo de alguma forma.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você precisa garantir que os usuários tenham um caminho claro para tomar ações comuns com base na notificação e entender claramente por que a notificação ocorreu. As boas mensagens de notificação geralmente incluirão:

* **O que aconteceu.** Uma indicação clara do que aconteceu para causar a notificação.
* **O que aconteceu com.** Deve ser claro qual item/coisa foi atualizado para causar a notificação.
* **Quem fez isso.** Quem tomou a ação que fez com que a notificação fosse enviada.
* **O que eles podem fazer sobre isso.** Facilita a ação dos usuários com base em suas notificações.
* **Como eles podem optar.** Você precisa fornecer um caminho para os usuários não receberem notificações adicionais.

## <a name="obtain-necessary-user-information"></a>Obter informações de usuário necessárias

Os bots podem criar novas conversas com um usuário individual do Microsoft Teams obtendo a *ID* exclusiva do usuário e a ID do *locatário.* Você pode obter esses valores usando um dos seguintes métodos:

* Ao [buscar a lista de equipe](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) de um canal em que seu aplicativo está instalado.
* Armazenando-os em cache quando um usuário [interage com seu bot em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).
* Quando um usuário é [@mentioned em uma conversa de canal,](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) o bot faz parte.
* Armazenando-os em cache quando [você `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) recebe o evento quando seu aplicativo é instalado em um escopo pessoal, ou novos membros são adicionados a um canal ou chat de grupo que

### <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o graph está atualmente na versão beta.

Ocasionalmente, pode ser necessário enviar mensagens proativas aos usuários que não tenham instalado ou interagido com seu aplicativo anteriormente. Por exemplo, você deseja usar o [comunicador da](~/samples/app-templates.md#company-communicator) empresa para enviar mensagens para toda a sua organização. Para esse cenário, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar em cache os valores necessários do evento que seu aplicativo receberá `conversationUpdate` ao instalar.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do Teams.

Consulte [Instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação do Graph para obter detalhes completos. Também há um [exemplo em .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

## <a name="examples"></a>Exemplos

Certifique-se de autenticar e ter um token de portador antes de criar uma nova conversa usando a API REST.

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

Você deve fornecer a ID do usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará com o objeto de resposta a seguir.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

Essa ID é a ID de conversa exclusiva do chat pessoal. Armazene esse valor e reutilize-o para futuras interações com o usuário.

### <a name="using-net"></a>Usando o .NET

Este exemplo usa o [pacote NuGet Microsoft.Bot.Connector.Teams.](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)

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

*Consulte também Exemplos* [da Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

## <a name="creating-a-channel-conversation"></a>Criar uma conversa de canal

Seu bot adicionado pela equipe pode postar em um canal para criar uma nova cadeia de respostas. Se você estiver usando o Node.js SDK do Teams, use o que fornece um endereço totalmente preenchido com a ID de atividade correta e a `startReplyChain()` ID da conversa. Se você estiver usando C#, consulte o exemplo abaixo.

Como alternativa, você pode usar a API REST e emitir uma solicitação POST para [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) o recurso.

### <a name="net-example-from-this-sample"></a>Exemplo do .NET [(a partir deste exemplo](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))

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
