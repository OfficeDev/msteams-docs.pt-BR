---
title: Mensagens proativas
description: Descreve os bots podem iniciar uma conversa no Microsoft Teams
keywords: cenários do teams-bot de conversa de mensagens pró-ativas
ms.openlocfilehash: 2f644820da33acc885a7972b13a1f61c167d6d8f
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228063"
---
# <a name="proactive-messaging-for-bots"></a>Mensagens proativas para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma mensagem pró-ativa é uma mensagem enviada por um bot para iniciar uma conversa. Talvez você queira que o bot inicie uma conversa por vários motivos, incluindo:

* Mensagens de boas-vindas para conversas de bot pessoais
* Respostas de pesquisa
* Notificações de eventos externos

Enviar uma mensagem para iniciar um novo thread de conversa é diferente de enviar uma mensagem em resposta a uma conversa existente: quando seu bot inicia uma nova conversa, não há uma conversa pré-existente para postar a mensagem. Para enviar uma mensagem pró-ativa, você precisa:

1. [Decidir o que você pretende dizer](#best-practices-for-proactive-messaging)
1. [Obter a ID exclusiva do usuário e a ID do locatário](#obtain-necessary-user-information)
1. [Enviar a mensagem](#examples)

Ao criar mensagens proativas **** , você `MicrosoftAppCredentials.TrustServiceUrl`deve chamar e passar a URL do serviço antes de `ConnectorClient` criar o que você usará para enviar a mensagem. Se você não fizer isso, seu aplicativo receberá `401: Unauthorized` uma resposta. Confira [os exemplos abaixo](#net-example-from-this-sample).

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens pró-ativas para os usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários. No entanto, a partir de sua perspectiva, essa mensagem pode parecer ser exibida completamente sem confirmação e, no caso de mensagens de boas-vindas, será a primeira vez que interagiu com seu aplicativo. Assim, é muito importante usar essa funcionalidade com moderação (não enviar spam aos usuários) e fornecer informações suficientes para que eles entendam por que estão recebendo mensagens.

As mensagens pró-ativas geralmente se enquadram em uma de duas categorias, mensagens de boas-vindas ou notificações.

### <a name="welcome-messages"></a>Mensagens de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas receber a mensagem, eles não terão nenhum contexto para o recebimento. Essa é também a primeira vez que terá interagindo com o aplicativo; é sua oportunidade de criar uma boa impressão em bom lugar. As melhores mensagens de boas-vindas incluirão:

* **Por que eles estão recebendo esta mensagem.** Deve estar muito claro para o usuário por que eles estão recebendo a mensagem. Se o seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas para todos os usuários, informe-o sobre o canal em que ele foi instalado e possivelmente quem o instalou.
* **O que você oferece.** O que eles podem fazer com o seu aplicativo? Que valor você pode trazer para eles?
* **O que deve ser feito em seguida.** Convide-os a experimentar um comando ou interagir com o aplicativo de alguma forma.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você precisa certificar-se de que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara de por que a notificação ocorreu. Geralmente, as boas mensagens de notificação incluirão:

* **O que aconteceu.** Uma indicação clara do que aconteceu com a notificação.
* **O que aconteceu.** Deve estar claro qual item/coisa foi atualizado para causar a notificação.
* **Quem fazia isso.** Quem executou a ação que provocou a envio da notificação.
* **O que eles podem fazer sobre ele.** Facilite que os usuários executem ações com base em suas notificações.
* **Como eles podem recusar.** Você precisa fornecer um caminho para que os usuários recusem notificações adicionais.

## <a name="obtain-necessary-user-information"></a>Obter informações necessárias do usuário

Os bots podem criar novas conversas com um usuário individual do Microsoft Teams obtendo a *ID exclusiva* do usuário e a *ID do locatário.* Você pode obter esses valores usando um dos seguintes métodos:

* Ao [buscar a lista de equipes](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) em um canal em que seu aplicativo está instalado.
* Por meio de armazenamento em cache quando um usuário [interage com seu bot em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).
* Quando um usuário é [@mentioned em uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) , o bot é parte de.
* Ao [receber o `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) evento em cache quando o aplicativo é instalado em um escopo pessoal, ou novos membros são adicionados a um chat de canal ou de grupo que

### <a name="proactively-install-your-app-using-graph"></a>Instalar o aplicativo proativamente usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Graph está atualmente em versão beta.

Ocasionalmente, pode ser necessário que usuários de mensagens de forma proativa não tenham sido instalados ou interagindo com o aplicativo anteriormente. Por exemplo, você deseja usar o [Communicator da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a sua organização. Para este cenário, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar `conversationUpdate` em cache os valores necessários do evento que seu aplicativo receberá na instalação.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do teams.

Consulte [instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação do gráfico para obter detalhes completos. Há também um [exemplo no .net](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

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

Você deve fornecer a ID de usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará com o seguinte objeto Response.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

Esta ID é a ID de conversa exclusiva do chat pessoal. Armazene esse valor e reutilize-o para futuras interações com o usuário.

### <a name="using-net"></a>Usando o .NET

Este exemplo usa o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .

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

### <a name="using-nodejs"></a>Usando node. js

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

*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

## <a name="creating-a-channel-conversation"></a>Criando uma conversa de canal

O bot adicionado pela equipe pode ser publicado em um canal para criar uma nova cadeia de resposta. Se você estiver usando o SDK de equipes do node. js `startReplyChain()` , use o que fornece um endereço totalmente preenchido com a ID de atividade e ID de conversa corretas. Se você estiver usando C#, confira o exemplo a seguir.

Como alternativa, você pode usar a API REST e emitir uma solicitação POST para [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) o recurso.

### <a name="net-example-from-this-sample"></a>Exemplo .NET ( [neste exemplo](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))

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
