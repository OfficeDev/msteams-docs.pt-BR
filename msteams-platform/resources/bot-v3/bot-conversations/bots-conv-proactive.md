---
title: Mensagens proativas para bots
description: Saiba como usar mensagens proativas para bots no Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: high
keywords: bot de conversa proativa de mensagens de cenários de equipes
ms.openlocfilehash: 12c6f9ad79d7e28f31e3985930557339e75ccbbf
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111483"
---
# <a name="proactive-messaging-for-bots"></a>Mensagens proativas para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma mensagem proativa é uma mensagem enviada por um bot para iniciar uma conversa. Talvez você queira que seu bot inicie uma conversa por vários motivos, incluindo:

* Mensagens de boas-vindas para conversas pessoais do bot
* Respostas a votações
* Notificações de eventos externos

Enviar uma mensagem para iniciar um novo thread de conversa é diferente de enviar uma mensagem em resposta a uma conversa existente: quando o bot inicia uma nova conversa, não há nenhuma conversa pré-existente para postar a mensagem. Para enviar uma mensagem proativa, você precisa:

1. [Decidir o que você vai dizer](#best-practices-for-proactive-messaging)
1. [Obter a ID exclusiva do usuário e a ID do locatário](#obtain-necessary-user-information)
1. [Enviar a mensagem](#examples)

Ao criar mensagens proativas você **deve** chamar `MicrosoftAppCredentials.TrustServiceUrl`e passar a URL do serviço antes de criar o `ConnectorClient` usado para enviar a mensagem. Caso contrário, uma resposta `401: Unauthorized` será recebida pelo aplicativo. Para obter mais informações, consulte os [exemplos abaixo](#net-example-from-this-sample).

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira eficaz de se comunicar com seus usuários. No entanto, da perspectiva do usuário, a mensagem aparece espontaneamente. Se houver uma mensagem de boas-vindas, será a primeira vez que eles interagirão com seu aplicativo. É importante usar essa funcionalidade e fornecer as informações completas ao usuário para entender a finalidade dessa mensagem.

As mensagens proativas geralmente se enquadram em uma das duas categorias: mensagens de boas-vindas ou notificações.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, verifique se, da perspectiva do usuário, a mensagem parece não ser proativa. Se houver uma mensagem de boas-vindas, será a primeira vez que eles interagirão com seu aplicativo. As mensagens de boas-vindas ideais devem incluir:

* **por quê eles estão recebendo esta mensagem**: deve ser claro para o usuário por quê ele está recebendo esta mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e quem o instalou.
* **o que você oferece**: o que eles podem fazer com seu aplicativo? Qual valor você pode trazer para eles?
* **o que eles devem fazer em seguida**: convidar os usuários para tentar um comando ou interagir com seu aplicativo.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você precisa garantir que os usuários tenham um caminho claro para executar ações comuns com base em sua notificação e uma compreensão clara do motivo pelo qual a notificação ocorreu. Boas mensagens de notificação geralmente incluirão:

* **o que aconteceu**: uma indicação clara do que aconteceu para gerar a notificação.
* **Com o que aconteceu**: deve estar claro qual item/coisa foi atualizado para causar a notificação.
* **quem fez isso**: quem executou a ação que fez com que a notificação seja enviada?
* **O que eles podem fazer a respeito**: torne fácil para os usuários tomarem ações com base em suas notificações.
* **Como eles podem recusar**: forneça um caminho para os usuários recusarem notificações adicionais.

## <a name="obtain-necessary-user-information"></a>Obter as informações necessárias do usuário

Os bots podem criar novas conversas com um usuário individual do Microsoft Teams obtendo a *ID exclusiva* e a *ID de locatário* do usuário. Você pode obter esses valores usando um dos seguintes métodos:

* Ao [buscar a lista de participantes ](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) de um canal em que seu aplicativo está instalado.
* Armazenando-os em cache quando um usuário [interage com seu bot em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).
* Quando um usuário é [@mencionado em uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) da qual o bot faz parte.
* Armazenando-os em cache quando você [recebe o`conversationUpdate`](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) evento quando seu aplicativo é instalado em um escopo pessoal ou novos membros são adicionados a um canal ou chat em grupo que.

### <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Graph está atualmente em versão beta.

Ocasionalmente, pode ser necessário enviar mensagens proativas aos usuários que não instalaram ou interagiram com seu aplicativo anteriormente. Por exemplo, você deseja usar o [comunicador da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a organização. Para esse cenário, você pode usar o API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar em cache os valores necessários do evento `conversationUpdate` que seu aplicativo receberá após a instalação.

Você só pode instalar aplicativos que estão em no catálogo de aplicativos da sua organização ou na Loja de aplicativos do Teams.

Consulte [Instalar aplicativos para usuários](/graph/api/userteamwork-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true) na documentação do Graph para obter detalhes completos. Também há um [exemplo em .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

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

É preciso fornecer a ID do usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará o seguinte objeto de resposta.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

Essa ID é a ID de conversa exclusiva do chat pessoal. Armazene esse valor e reutilize-o para interações futuras com o usuário.

### <a name="using-net"></a>Usando o .NET

Este exemplo usa o pacote NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .

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

Seu bot adicionado pela equipe pode postar em um canal para criar uma nova cadeia de respostas. Se você estiver usando o SDK do Teams do Node.js, use`startReplyChain()`, que fornece um endereço totalmente preenchido com a ID de atividade e a ID de conversa corretas. Se você estiver usando C#, consulte o exemplo abaixo.

Como alternativa, você pode usar a API REST e emitir uma solicitação POST para o recurso [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation).

### <a name="net-example-from-this-sample"></a>Exemplo de.NET ([deste exemplo](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))

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

[Exemplos do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
