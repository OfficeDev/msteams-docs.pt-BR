---
title: Enviar e receber mensagens com um bot
description: Descreve como enviar e receber mensagens com bots em Microsoft Teams
ms.topic: overview
localization_priority: Normal
keywords: equipes bots mensagens
ms.date: 05/20/2019
ms.openlocfilehash: e1926afe42bca45eda5f39be1be8342452b3aa24
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566492"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Converse com um robô Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre seu bot e um ou mais usuários. Há três tipos de conversas (também chamados de escopos) no Teams:

* `teams` Também chamadas de conversas de canal, visíveis para todos os membros do canal.
* `personal` Conversas entre bots e um único usuário.
* `groupChat` Converse entre um bot e dois ou mais usuários.

Um bot se comporta ligeiramente diferente dependendo do tipo de conversa em que está envolvido:

* [Bots em conversas de bate-papo de canal e grupo](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) exigem que o usuário @mention o bot para invocá-lo em um canal.
* [Bots em conversas de usuário único](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) não exigem uma @mention - o usuário pode simplesmente digitar.

Para que o bot funcione em um escopo específico, ele deve ser listado como suporte a esse escopo no manifesto. Os escopos são definidos e discutidos ainda mais no [Manifesto Referencial](~/resources/schema/manifest-schema.md).

## <a name="proactive-messages"></a>Mensagens proativas

Bots podem participar de uma conversa ou iniciar uma. A maior parte da comunicação é em resposta a outra mensagem. Se um bot iniciar uma conversa, ele é chamado de *mensagem proativa*. Os exemplos incluem:

* Mensagem de boas-vindas
* Notificações de eventos
* Mensagens de votação

## <a name="conversation-basics"></a>Noções básicas sobre conversas

Cada mensagem é um `Activity` do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem em seu bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagens do seu bot. Seu bot examina a mensagem para determinar seu tipo e responde de acordo.

Os bots também suportam mensagens no estilo evento. Para obter mais informações, consulte [os eventos do Handle bot em Microsoft Teams](~/resources/bot-v3/bots-notifications.md). No momento, a fala não é apoiada.

As mensagens são, na maioria das vezes, as mesmas em todos os escopos, mas há diferenças na forma como o bot é acessado na interface do usuário e diferenças nos bastidores que você precisará saber.

A conversa básica é tratada através do Bot Framework Connector, uma única API REST para permitir que seu bot se comunique com Teams e outros canais. O Bot Builder SDK fornece fácil acesso a esta API, funcionalidade adicional para gerenciar o fluxo e o estado de conversação e maneiras simples de incorporar serviços cognitivos, como processamento de linguagem natural (NLP).

## <a name="message-content"></a>Conteúdo da mensagem

Seu robô pode enviar textos, fotos e cartões ricos. Os usuários podem enviar textos e fotos ricos para o seu bot. Você pode especificar o tipo de conteúdo que seu bot pode lidar na página de configurações Microsoft Teams para o seu bot.

| Formatar | De usuário para bot  | Do bot ao usuário |  Notas |
| --- | :---: | :---: | --- |
| Rich text  | ✔ | ✔ |  |
| Imagens | ✔ | ✔ | Máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não são suportados. |
| Cartões | ✖ | ✔ | Consulte a [referência de cartão Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões suportados. |
| Emojis | ✖ | ✔ | Teams atualmente suporta emojis via UTF-16, como, U+1F600 para rosto sorridente. |
|

Para obter mais informações sobre os tipos de interação de bot suportada pelo Bot Framework, no qual os bots em equipes são baseados, consulte a documentação do Bot Framework sobre [fluxo de conversa](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0&preserve-view=true) e conceitos relacionados na documentação do Bot Builder [SDK para .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0&preserve-view=true) e [do Bot Builder SDK for Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0&preserve-view=true).

## <a name="message-formatting"></a>Formatação de mensagem

Você pode definir a propriedade opcional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) de um para controlar como o conteúdo de texto da sua `message` mensagem é renderizado. Consulte [a formatação da mensagem](~/resources/bot-v3/bots-message-format.md) para obter uma descrição detalhada da formatação suportada em mensagens de bot.
Você pode definir a propriedade opcional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) para controlar como o conteúdo de texto da sua mensagem é renderizado.

Para obter informações detalhadas sobre como Teams suporta formatação de texto em equipes, consulte [formatação de texto em mensagens de bot](~/resources/bot-v3/bots-text-formats.md).

Para obter mais informações sobre cartões de formatação em mensagens, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Mensagens de imagem

As imagens são enviadas adicionando anexos a uma mensagem. Você pode encontrar mais informações sobre anexos na [documentação do Bot Framework](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true).

As imagens podem ser no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é suportado.

Recomendamos que você especifique a altura e largura de cada imagem usando XML. Se você usar o Markdown, o tamanho da imagem padrão para 256×256. Por exemplo:

* Usar o `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Não use. `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages&quot;></a>Recebimento de mensagens

Dependendo de quais escopos são declarados, seu bot pode receber mensagens nos seguintes contextos:

* **bate-papo pessoal** Os usuários podem interagir em uma conversa privada com um bot simplesmente selecionando o bot adicionado no histórico do chat ou digitando seu nome ou ID do aplicativo na caixa Para: em um novo chat.
* **Canais** Um bot pode ser mencionado (&quot;@_botname_") em um canal se tiver sido adicionado à equipe. Observe que respostas adicionais a um bot em um canal exigem mencionar o bot. Ele não responderá às respostas onde não for mencionado.

Para mensagens recebidas, o bot recebe um [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0&preserve-view=true) objeto do tipo `messageType: message` . Embora o `Activity` objeto possa conter outros tipos de informações, como [atualizações](~/resources/bot-v3/bots-notifications.md#channel-updates) de canal enviadas ao seu bot, o `message` tipo representa comunicação entre bot e usuário.

Seu bot recebe uma carga que contém a mensagem do `Text` usuário, bem como outras informações sobre o usuário, a fonte da mensagem e Teams informações. Nota:

* `timestamp` A data e a hora da mensagem em Tempo Universal Coordenado (UTC).
* `localTimestamp` A data e a hora da mensagem no fuso horário do remetente.
* `channelId` Sempre "msteams". Isso se refere a um canal de estrutura de bot, não a um canal de equipes.
* `from.id` Uma ID única e criptografada para esse usuário para o seu bot; adequado como uma chave se o seu aplicativo precisa armazenar dados do usuário. É único para o seu bot e não pode ser usado diretamente fora da sua instância de bot de qualquer maneira significativa para identificar esse usuário.
* `channelData.tenant.id` O ID do inquilino para o usuário.

> [!NOTE]
> `from.id` é único para o seu bot e não pode ser usado diretamente fora da sua instância de bot de qualquer maneira significativa para identificar esse usuário.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Combinando canais e interações privadas com seu bot

Ao interagir em um canal, seu bot deve ser inteligente em tirar certas conversas offline com um usuário. Por exemplo, suponha que um usuário esteja tentando coordenar uma tarefa complexa, como agendar com um conjunto de membros da equipe. Em vez de ter toda a sequência de interações visível para o canal, considere enviar uma mensagem de chat pessoal para o usuário. Seu bot deve ser capaz de fazer a transição facilmente entre conversas pessoais e de canal sem perder o estado.

> [!NOTE]
>Não se esqueça de atualizar o canal quando a interação estiver completa para notificar os outros membros da equipe.

## <a name="full-inbound-schema-example"></a>Exemplo completo de esquema de entrada

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
> O campo de texto para mensagens de entrada às vezes contém menções. Certifique-se de verificar corretamente e despojá-los. Para obter mais informações, consulte [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>dados do canal Teams

O `channelData` objeto contém informações específicas Teams e é a fonte definitiva para iDs de equipe e canal. Você deve armazenar e usar esses ids como chaves para armazenamento local.

O `channelData` objeto não está incluído em mensagens em conversas pessoais, uma vez que elas ocorrem fora de qualquer canal.

Um objeto típico do CanalData em uma atividade enviada ao seu bot contém as seguintes informações:

* `eventType`Teams tipo de evento; passado apenas em casos de eventos de [modificação](~/resources/bot-v3/bots-notifications.md#channel-updates)de canal .
* `tenant.id`Azure Active Directory iD do inquilino; passou em todos os contextos.
* `team` Passou apenas em contextos de canal, não em bate-papo pessoal.
  * `id` GUID para o canal.
  * `name` Nome da equipe; passado apenas em casos de eventos de [renome da equipe](~/resources/bot-v3/bots-notifications.md#team-name-updates).
* `channel` Passou apenas em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.
  * `id` GUID para o canal.
  * `name` Nome do canal; passado apenas em casos de eventos de [modificação](~/resources/bot-v3/bots-notifications.md#channel-updates)de canal .
* `channelData.teamsTeamId` deprecado. Esta propriedade está incluída apenas para compatibilidade invertida.
* `channelData.teamsChannelId` deprecado. Esta propriedade está incluída apenas para compatibilidade invertida.

### <a name="example-channeldata-object-channelcreated-event"></a>Exemplo canalDe objetoData (evento channelCreated)

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

### <a name="net-example"></a>Exemplo .NET

O pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet fornece um `TeamsChannelData` objeto especializado, que expõe propriedades para acessar informações específicas Teams.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Enviando respostas para mensagens

Para responder a uma mensagem existente, ligue [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_&preserve-view=true) para .NET ou [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities&preserve-view=true) em Node.js. O Bot Builder SDK lida com todos os detalhes.

Se você optar por usar a API REST, você também pode chamar o [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0&preserve-view=true) ponto final.

O conteúdo da mensagem em si pode conter texto simples ou alguns dos cartões e ações de [cartão fornecidos](~/task-modules-and-cards/cards/cards-actions.md)pelo Bot Framework .

Por favor, note que no seu esquema de saída você deve sempre usar o mesmo `serviceUrl` que você recebeu. Esteja ciente de que o valor de `serviceUrl` tende a ser estável, mas pode mudar. Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl` .

## <a name="updating-messages"></a>Atualizando mensagens

Em vez de ter suas mensagens como instantâneos estáticos de dados, seu bot pode atualizar dinamicamente as mensagens inline após enviá-las. Você pode usar atualizações dinâmicas de mensagens para cenários como atualizações de enquetes, modificando ações disponíveis após uma pressão de botão ou qualquer outra alteração de estado assíncroníncro.

A nova mensagem não precisa coincidir com o tipo original. Por exemplo, se a mensagem original contivesse um anexo, a nova mensagem pode ser uma simples mensagem de texto.

> [!NOTE]
> Você pode atualizar apenas o conteúdo enviado em mensagens de anexo único e layouts de carrossel. A publicação de atualizações de mensagens com vários anexos no layout da lista não é suportada.

### <a name="rest-api"></a>API REST

Para emitir uma atualização de mensagem, basta executar uma solicitação PUT contra o `/v3/conversations/<conversationId>/activities/<activityId>/` ponto final usando um determinado ID de atividade. Para completar este cenário, você deve armazenar o ID de atividade retornado pela chamada POST original.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>Exemplo .NET

Você pode usar o `UpdateActivityAsync` método no Bot Builder SDK para atualizar uma mensagem existente.

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

Você pode usar o `session.connector.update` método no Bot Builder SDK para atualizar uma mensagem existente.

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

Você pode criar uma conversa pessoal com um usuário ou iniciar uma nova cadeia de respostas em um canal para o bot da sua equipe. Isso permite que você envie uma mensagem ao seu usuário ou usuários sem que eles iniciem primeiro o contato com o seu bot. Para mais informações, confira os seguintes tópicos:

Consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter informações mais gerais sobre conversas iniciadas por bots.

## <a name="deleting-messages"></a>Excluindo mensagens

As mensagens podem ser excluídas usando o método de conectores [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) no [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted).

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
