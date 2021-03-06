---
title: Enviar e receber mensagens com um bot
description: Descreve como enviar e receber mensagens com bots no Microsoft Teams
ms.topic: overview
localization_priority: Normal
keywords: mensagens de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: efa7658aef87650e360c79523ac1c282dc4814fd
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630457"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Ter uma conversa com um Microsoft Teams bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre seu bot e um ou mais usuários. Há três tipos de conversas (também chamados de escopos) no Teams:

* `teams` Também chamadas de conversas de canal, visíveis para todos os membros do canal.
* `personal` Conversas entre bots e um único usuário.
* `groupChat` Chat entre um bot e dois ou mais usuários.

Um bot se comporta um pouco diferente dependendo do tipo de conversa em que ele está envolvido:

* [Bots em conversas de chat](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) de canal e grupo exigem que o usuário @mention o bot para invocá-lo em um canal.
* [Bots em conversas de usuário](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) único não exigem um @mention - o usuário pode apenas digitar.

Para que o bot funcione em um escopo específico, ele deve ser listado como suporte a esse escopo no manifesto. Os escopos são definidos e discutidos ainda mais na [Referência de Manifesto.](~/resources/schema/manifest-schema.md)

## <a name="proactive-messages"></a>Mensagens proativas

Os bots podem participar de uma conversa ou iniciar uma. A maioria das comunicações é em resposta a outra mensagem. Se um bot iniciar uma conversa, ele será chamado de mensagem *proativa*. Os exemplos incluem:

* Mensagem de boas-vindas
* Notificações de eventos
* Mensagens de sondagem

## <a name="conversation-basics"></a>Noções básicas sobre conversas

Cada mensagem é um `Activity` do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem em seu bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagens do seu bot. Seu bot examina a mensagem para determinar seu tipo e responde de acordo.

Os bots também suportam mensagens no estilo de evento. Para obter mais informações, consulte [Handle bot events in Microsoft Teams](~/resources/bot-v3/bots-notifications.md). No momento, não há suporte para fala.

As mensagens são, na maioria das vezes, as mesmas em todos os escopos, mas há diferenças em como o bot é acessado na interface do usuário e diferenças nos bastidores que você precisará saber.

A conversa básica é manipulada por meio do Bot Framework Connector, uma única API REST para permitir que o bot se comunique com Teams e outros canais. O SDK do Construtor de Bots fornece fácil acesso a essa API, funcionalidade adicional para gerenciar o fluxo e o estado da conversa e maneiras simples de incorporar serviços cognitivos, como processamento de linguagem natural (NLP).

## <a name="message-content"></a>Conteúdo da mensagem

Seu bot pode enviar rich text, pictures e cards. Os usuários podem enviar texto e imagens rich para seu bot. Você pode especificar o tipo de conteúdo que o bot pode manipular na página Microsoft Teams configurações do bot.

| Formatar | De usuário para bot  | De bot para usuário |  Observações |
| --- | :---: | :---: | --- |
| Rich text  | ✔ | ✔ |  |
| Imagens | ✔ | ✔ | Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não são suportados. |
| Cartões | ✖ | ✔ | Consulte a [referência Teams cartão para](~/task-modules-and-cards/cards/cards-reference.md) cartões com suporte. |
| Emojis | ✖ | ✔ | Teams atualmente dá suporte a emojis por meio do UTF-16, como U+1F600 para face de goslinha. |
|

Para obter mais informações sobre os tipos de interação com bots suportados pela Estrutura de [](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0&preserve-view=true) Bot, em que bots em equipes são baseados, consulte a documentação da Estrutura de Bot sobre o fluxo de conversas e os conceitos relacionados na documentação do [SDK](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0&preserve-view=true) do Construtor de Bots para .NET e do [SDK ](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0&preserve-view=true)do Construtor de Bots para Node.js.

## <a name="message-formatting"></a>Formatação de mensagem

Você pode definir a propriedade opcional de a para controlar como o conteúdo de texto da mensagem [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) `message` é renderizado. Consulte [Formatação de mensagem](~/resources/bot-v3/bots-message-format.md) para uma descrição detalhada da formatação com suporte em mensagens bot.
Você pode definir a propriedade opcional para controlar como o conteúdo de texto da mensagem [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) é renderizado.

Para obter informações detalhadas sobre como Teams suporte à formatação de texto nas equipes, consulte Formatação de texto [em mensagens bot.](~/resources/bot-v3/bots-text-formats.md)

Para obter mais informações sobre formatação de cartões em mensagens, consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Mensagens de imagem

As imagens são enviadas adicionando anexos a uma mensagem. Você pode encontrar mais informações sobre anexos na documentação [da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true)

As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é suportado.

Recomendamos que você especifique a altura e a largura de cada imagem usando XML. Se você usar Markdown, o tamanho da imagem será padrão para 256×256. Por exemplo:

* Usar o `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Não use `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages&quot;></a>Recebimento de mensagens

Dependendo de quais escopos são declarados, seu bot pode receber mensagens nos seguintes contextos:

* **chat pessoal** Os usuários podem interagir em uma conversa privada com um bot simplesmente selecionando o bot adicionado no histórico do chat ou digitando seu nome ou ID do aplicativo na caixa Para: em um novo chat.
* **Canais** Um bot pode ser mencionado (&quot;@_botname_") em um canal se tiver sido adicionado à equipe. Observe que respostas adicionais a um bot em um canal exigem a menção ao bot. Ele não responderá às respostas onde não é mencionada.

Para mensagens de entrada, seu bot recebe um [objeto Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) do tipo `messageType: message` . Embora o objeto possa conter outros tipos de informações, como atualizações de canal enviadas ao bot, o tipo representa a comunicação `Activity` entre bot e [](~/resources/bot-v3/bots-notifications.md#channel-updates) `message` usuário.

Seu bot recebe uma carga que contém a mensagem do usuário, bem como outras informações sobre o usuário, a origem da mensagem e Teams `Text` informações. Observação:

* `timestamp` A data e a hora da mensagem em Tempo Universal Coordenado (UTC).
* `localTimestamp` A data e a hora da mensagem no fuso horário do remetente.
* `channelId` Sempre "msteams". Isso se refere a um canal de estrutura de bots, não a um canal de equipes.
* `from.id` Uma ID exclusiva e criptografada para esse usuário para seu bot; adequado como uma chave se seu aplicativo precisar armazenar dados do usuário. Ele é exclusivo para o bot e não pode ser usado diretamente fora da instância do bot de qualquer maneira significativa para identificar esse usuário.
* `channelData.tenant.id` A ID do locatário para o usuário.

> [!NOTE]
> `from.id` é exclusivo para o bot e não pode ser usado diretamente fora da instância do bot de qualquer maneira significativa para identificar esse usuário.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Combinando canal e interações privadas com seu bot

Ao interagir em um canal, seu bot deve ser inteligente sobre como fazer determinadas conversas offline com um usuário. Por exemplo, suponha que um usuário está tentando coordenar uma tarefa complexa, como o agendamento com um conjunto de membros da equipe. Em vez de ter toda a sequência de interações visíveis para o canal, considere enviar uma mensagem de chat pessoal para o usuário. Seu bot deve ser capaz de fazer a transição fácil do usuário entre conversas pessoais e de canal sem perder o estado.

> [!NOTE]
>Não se esqueça de atualizar o canal quando a interação for concluída para notificar os outros membros da equipe.

## <a name="full-inbound-schema-example"></a>Exemplo de esquema de entrada completa

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot",
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

> [!NOTE]
> O campo de texto para mensagens de entrada às vezes contém menções. Certifique-se de verificar e desmá-los corretamente. Para obter mais informações, consulte [Menções](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams de canal

O objeto contém Teams informações específicas e é a fonte `channelData` definitiva para IDs de equipe e canal. Você deve armazenar em cache e usar essas IDs como chaves para armazenamento local.

O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de qualquer canal.

Um objeto channelData típico em uma atividade enviada ao bot contém as seguintes informações:

* `eventType`Teams tipo de evento; passada somente em casos de eventos [de modificação de canal](~/resources/bot-v3/bots-notifications.md#channel-updates).
* `tenant.id`Azure Active Directory ID do locatário; passado em todos os contextos.
* `team` Passado somente em contextos de canal, não em chat pessoal.
  * `id` GUID para o canal.
  * `name`Nome da equipe; passada somente em casos de [eventos de renomear equipe.](~/resources/bot-v3/bots-notifications.md#team-name-updates)
* `channel` Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.
  * `id` GUID para o canal.
  * `name` Nome do canal; passada somente em casos de eventos [de modificação de canal](~/resources/bot-v3/bots-notifications.md#channel-updates).
* `channelData.teamsTeamId` Preterido. Essa propriedade é incluída apenas para compatibilidade com compatibilidade com compatibilidade.
* `channelData.teamsChannelId` Preterido. Essa propriedade é incluída apenas para compatibilidade com compatibilidade com compatibilidade.

### <a name="example-channeldata-object-channelcreated-event"></a>Objeto channelData de exemplo (evento channelCreated)

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

### <a name="net-example"></a>Exemplo do .NET

O [pacote Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet fornece um objeto especializado, que expõe propriedades para acessar informações `TeamsChannelData` Teams específicas.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Enviando respostas a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_&preserve-view=true) o .NET ou [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities&preserve-view=true) Node.js. O SDK do Construtor de Bots lida com todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0&preserve-view=true) ponto de extremidade.

O conteúdo da mensagem em si pode conter texto simples ou algumas das ações de cartão e [cartões](~/task-modules-and-cards/cards/cards-actions.md)fornecidas pela Estrutura de Bot.

Observe que, no esquema de saída, você sempre deve usar o mesmo que `serviceUrl` o recebido. Esteja ciente de que o valor de `serviceUrl` tende a ser estável, mas pode mudar. Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl` .

## <a name="updating-messages"></a>Atualizando mensagens

Em vez de suas mensagens serem instantâneos estáticos de dados, o bot pode atualizar dinamicamente as mensagens em linha após enviá-las. Você pode usar atualizações dinâmicas de mensagens para cenários como atualizações de sondagem, modificação de ações disponíveis depois de pressionar um botão ou qualquer outra alteração de estado assíncrona.

A nova mensagem não precisa corresponder ao tipo original. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

> [!NOTE]
> Você só pode atualizar o conteúdo enviado em mensagens de anexo único e layouts de carrossel. Não há suporte para postagem de atualizações em mensagens com vários anexos no layout da lista.

### <a name="rest-api"></a>API REST

Para emitir uma atualização de mensagem, basta executar uma solicitação PUT no ponto de extremidade `/v3/conversations/<conversationId>/activities/<activityId>/` usando uma determinada ID de atividade. Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada POST original.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>Exemplo do .NET

Você pode usar o `UpdateActivityAsync` método no SDK do Construtor de Bots para atualizar uma mensagem existente.

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
  if (activity.Type == ActivityTypes.Message)
  {
    ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
    Activity reply = activity.CreateReply($"You sent {activity.Text} which was {activity.Text.Length} characters");
    var msgToUpdate = await connector.Conversations.ReplyToActivityAsync(reply);
    Activity updatedReply = activity.CreateReply($"This is an updated message");
    await connector.Conversations.UpdateActivityAsync(reply.Conversation.Id, msgToUpdate.Id, updatedReply);
  }
}
```

### <a name="nodejs-example"></a>Node.js exemplo

Você pode usar o `session.connector.update` método no SDK do Construtor de Bots para atualizar uma mensagem existente.

```javascript
function sendCardUpdate(bot, session, originalMessage, address) {

  var origAttachment = originalMessage.data.attachments[0];
  origAttachment.content.subtitle = 'Assigned to Larry Jin';

  var updatedMsg = new builder.Message()
    .address(address)
    .textFormat(builder.TextFormat.markdown)
    .addAttachment(origAttachment)
    .toMessage();

  session.connector.update(updatedMsg, function(err, addresses) {
    if (err) {
      console.log(`Could not update the message`);
    }
  });
}
```

## <a name="starting-a-conversation-proactive-messaging"></a>Iniciar uma conversa (mensagens proativas)

Você pode criar uma conversa pessoal com um usuário ou iniciar uma nova cadeia de respostas em um canal para seu bot de equipe. Isso permite que você mensagem seu usuário ou usuários sem que eles iniciem primeiro contato com seu bot. Para mais informações, confira os seguintes tópicos:

Consulte [Mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter informações mais gerais sobre conversas iniciadas por bots.

## <a name="deleting-messages"></a>Excluir mensagens

As mensagens podem ser excluídas usando o método [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) connectors no [SDK BotBuilder.](/bot-framework/bot-builder-overview-getstarted)

```typescript
bot.dialog('BotDeleteMessage', function (session: builder.Session) {
  var msg = new teams.TeamsMessage(session).text("Bot will delete this message in 5 sec.")
  bot.send(msg, function (err, response) {
    if (err) {
      console.log(err);
      session.endDialog();
    }

    console.log('Proactive message response:');
    console.log(response);
    console.log('---------------------------------------------------')
    setTimeout(function () {
      var activityId: string = null;
      var messageAddress: builder.IChatConnectorAddress = null;
      if (response[0]){
        messageAddress = response[0];
        activityId = messageAddress.id;
      }

      if (activityId == null)
      {
        console.log('Message failed to send.');
        session.endDialog();
        return;
      }

      // Bot delete message
      let address: builder.IChatConnectorAddress  = {
        channelId: 'msteams',
        user: messageAddress.user,
        bot: messageAddress.bot,
        id : activityId,
        serviceUrl : (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
        conversation: {
          id: session.message.address.conversation.id
        }
      };

      connector.delete(address, function (err) {
        if (err)
        {
          console.log(err);
        }
        else
        {
          console.log("Message: " + activityId + " deleted successfully.");
        }

        // Try editing deleted message would fail
        var newMsg = new builder.Message().address(address).text("To edit message.");
        connector.update(newMsg.toMessage(), function (err, address) {
          if (err)
          {
            console.log(err);
            console.log('Deleted message can not be edited.');
          }
          else
          {
            console.log("There is something wrong. Message: " + activityId + " edited successfully.");
            console.log(address);
          }

          session.endDialog();
        });
      });
    }, 5000);
  });
})
```
