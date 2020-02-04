---
title: Enviar e receber mensagens com um bot
description: Descreve como enviar e receber mensagens com bots no Microsoft Teams
keywords: mensagens de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: 864473c7f502d96987a48e5837840236c45f59c7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672941"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Ter uma conversa com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre o bot e um ou mais usuários. Há três tipos de conversas (também chamadas de escopos) no Teams:

* `teams`Também chamado de conversações de canal, visíveis para todos os membros do canal.
* `personal`Conversas entre bots e um único usuário.
* `groupChat`Converse entre um bot e dois ou mais usuários.

Um bot se comporta de forma ligeiramente diferente dependendo do tipo de conversa envolvido em:

* Os [bots nas conversas de chat de canal e de grupo](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) exigem que o usuário @ mencione o bot para chamá-lo em um canal.
* Os [bots em conversas de usuário único](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) não exigem um @ menção-o usuário pode simplesmente digitar.

Para que o bot funcione em um escopo específico, ele deve ser listado como suporte a esse escopo no manifesto. Os escopos são definidos e abordados mais detalhadamente na [referência do manifesto](~/resources/schema/manifest-schema.md).

## <a name="proactive-messages"></a>Mensagens proativas

Os bots podem participar de uma conversa ou iniciar um. A maior parte da comunicação é de resposta a outra mensagem. Se um bot iniciar uma conversa, ele será chamado de uma *mensagem proativa*. Exemplos incluem:

* Mensagens de boas-vindas
* Notificações de eventos
* Mensagens de sondagem

## <a name="conversation-basics"></a>Noções básicas da conversa

Cada mensagem é um `Activity` objeto do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagem de seu bot. O bot examina a mensagem para determinar seu tipo e responde de acordo.

Os bots também suportam mensagens no estilo de eventos. Consulte [manipular eventos de bot no Microsoft Teams](~/resources/bot-v3/bots-notifications.md) para obter mais detalhes. A fala não é suportada no momento.

As mensagens são para a maior parte do mesmo em todos os escopos, mas há diferenças em como o bot é acessado na interface do usuário e as diferenças por trás dos bastidores que você precisa saber.

A conversa básica é manipulada por meio do conector da estrutura de bot, uma única API REST para permitir que seu bot se comunique com o Teams e outros canais. O SDK do bot Builder fornece acesso fácil a essa API, funcionalidade adicional para gerenciar o fluxo e o estado da conversa e maneiras simples de incorporar serviços cognitivas, como o processamento de idioma natural (NLP).

## <a name="message-content"></a>Conteúdo da mensagem

Seu bot pode enviar Rich Text, imagens e cartões. Os usuários podem enviar Rich Text e imagens para o bot. Você pode especificar o tipo de conteúdo que seu bot pode lidar na página de configurações do Microsoft Teams para seu bot.

| Formatar | De usuário para bot  | De bot para usuário |  Observações |
| --- | :---: | :---: | --- |
| Rich text  | ✔ | ✔ |  |
| Imagens | ✔ | ✔ | Máximo de 1024 × 1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é suportado |
| Placa | ✖ | ✔ | Consulte a [referência de cartões de equipe](~/task-modules-and-cards/cards/cards-reference.md) para cartões suportados |
| Emojis | ✖ | ✔ | No momento, o Microsoft Teams oferece suporte a emojis via UTF-16 (como U + 1F600 para Grinning face) |
|

Para obter mais informações sobre os tipos de interação de bot suportados pela estrutura de bot (em que bots no Teams são baseados em), consulte a documentação da estrutura de bot sobre o [fluxo de conversa](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) e conceitos relacionados na documentação do [SDK do bot Builder para .net](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) e [o SDK do bot Builder para o Node. js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).

## <a name="message-formatting"></a>Formatação de mensagens

Você pode definir a propriedade [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) opcional de um `message` para controlar como o conteúdo de texto da mensagem é renderizado. Veja [formatação da mensagem](~/resources/bot-v3/bots-message-format.md) para obter uma descrição detalhada da formatação suportada nas mensagens de bot.
Você pode definir a propriedade [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) opcional para controlar como o conteúdo de texto da mensagem é renderizado.

Para obter informações detalhadas sobre como o Microsoft Teams dá suporte à formatação de texto no Teams, consulte [Text Formatting in bot messages](~/resources/bot-v3/bots-text-formats.md).

Para obter informações sobre como formatar cartões em mensagens, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Mensagens de imagem

As imagens são enviadas adicionando anexos a uma mensagem. Você pode encontrar mais informações sobre anexos na [documentação da estrutura do bot](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).

As imagens podem ser no máximo 1024 × 1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é suportado.

Recomendamos que você especifique a altura e a largura de cada imagem usando XML. Se você usar redução, o tamanho da imagem padrão será 256 × 256. Por exemplo:

* Use`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Não use `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages"></a>Receber mensagens

Dependendo de quais escopos são declarados, seu bot pode receber mensagens nos seguintes contextos:

* **chat pessoal** Os usuários podem interagir em uma conversa privada com um bot simplesmente selecionando o bot adicionado no histórico do chat, ou digitando seu nome ou ID de aplicativo na caixa para: em um novo chat.
* **Canais** Um bot pode ser mencionado ("@_botname_") em um canal se ele tiver sido adicionado à equipe. Observe que as respostas adicionais para um bot em um canal exigem que o bot seja mencionado. Ele não responderá às respostas onde não for mencionado.

Para mensagens de entrada, seu bot recebe [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) um objeto do `messageType: message`tipo. Embora o `Activity` objeto possa conter outros tipos de informações, como [as atualizações de canal](~/resources/bot-v3/bots-notifications.md#channel-updates) enviadas ao bot, `message` o tipo representa a comunicação entre o bot e o usuário.

O bot recebe uma carga que contém a mensagem `Text` do usuário, bem como outras informações sobre o usuário, a fonte da mensagem e as informações sobre o Teams. Observação:

* `timestamp`A data e a hora da mensagem no UTC (tempo Universal Coordenado)
* `localTimestamp`A data e a hora da mensagem no fuso horário do remetente
* `channelId`Sempre "msteams". Isso se refere a um canal de estrutura de bot, não a um canal de equipe.
* `from.id`Uma ID exclusiva e criptografada para o usuário para o bot; adequado como uma chave se seu aplicativo precisa armazenar dados do usuário. É exclusivo para o bot e não pode ser usado diretamente fora da instância de bot de forma significativa para identificar esse usuário
* `channelData.tenant.id`A ID do locatário do usuário.

> [!NOTE]
> `from.id`é exclusivo para o bot e não pode ser usado diretamente fora da instância de bot de forma significativa para identificar o usuário.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Combinar interações privadas e de canal com seu bot

Ao interagir em um canal, seu bot deve ser inteligente sobre como fazer determinadas conversas offline com um usuário. Por exemplo, suponha que um usuário esteja tentando coordenar uma tarefa complexa, como o agendamento com um conjunto de membros da equipe. Em vez de ter toda a sequência de interações visíveis para o canal, considere enviar uma mensagem de chat pessoal para o usuário. O bot deve ser capaz de fazer a transição fácil do usuário entre conversas pessoais e de canal sem perder o estado.

> [!NOTE]
>Não se esqueça de atualizar o canal quando a interação estiver concluída para notificar os outros membros da equipe.

## <a name="full-inbound-schema-example"></a>Exemplo de esquema de entrada completo

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
> O campo de texto para mensagens de entrada às vezes contém menção. Certifique-se de verificar corretamente e stripá-las. Para obter mais informações, consulte [menciona](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Dados de canal do teams

O `channelData` objeto contém informações específicas de equipes e é a fonte definitiva para IDs de canal e equipe. Você deve armazenar em cache e usar essas IDs como chaves para armazenamento local.

O `channelData` objeto não está incluído nas mensagens em conversas pessoais, pois elas ocorrem fora de qualquer canal.

Um objeto channelData típico em uma atividade enviada ao seu bot contém as seguintes informações:

* `eventType`Tipo de evento Teams; aprovado apenas em casos de [eventos de modificação de canal](~/resources/bot-v3/bots-notifications.md#channel-updates)
* `tenant.id`ID de locatário do Azure Active Directory; aprovado em todos os contextos
* `team`Aprovado apenas em contextos de canal, não no chat pessoal.
  * `id`GUID do canal
  * `name`Nome da equipe; passado apenas em casos de [eventos de renomeação de equipe](~/resources/bot-v3/bots-notifications.md#team-name-updates)
* `channel`É passado apenas em contextos de canal quando o bot é mencionado ou para eventos em canais no Teams onde o bot foi adicionado
  * `id`GUID do canal
  * `name`Nome do canal; passou apenas em casos de [eventos de modificação de canal](~/resources/bot-v3/bots-notifications.md#channel-updates).
* `channelData.teamsTeamId`Preterido. Essa propriedade é incluída apenas para compatibilidade com versões anteriores.
* `channelData.teamsChannelId`Preterido. Essa propriedade é incluída apenas para compatibilidade com versões anteriores.

### <a name="example-channeldata-object-channelcreated-event"></a>Exemplo do objeto channelData (evento channelCreated)

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

O pacote [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet fornece um `TeamsChannelData` objeto especializado, que expõe as propriedades para acessar informações específicas do teams.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Enviando respostas a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) no .net ou [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) no node. js. O SDK do bot Builder trata de todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o ponto [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) de extremidade.

O próprio conteúdo da mensagem pode conter texto simples ou alguns [cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md)fornecidos pela estrutura de bot.

Observe que, no seu esquema de saída, você sempre deve usar `serviceUrl` o mesmo que o recebido. Lembre-se de que o `serviceUrl` valor de tende a ser estável, mas pode ser alterado. Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl`.

## <a name="updating-messages"></a>Atualizando mensagens

Em vez de as mensagens serem instantâneos de dados estáticos, seu bot pode atualizar dinamicamente as mensagens embutidas após enviá-las. Você pode usar atualizações de mensagens dinâmicas para cenários como atualizações de pesquisa, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrono.

A nova mensagem não precisa coincidir com o original no tipo. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

> [!NOTE]
> Você pode atualizar somente o conteúdo enviado em mensagens de anexo único e layouts de carrossel. Não há suporte para o lançamento de atualizações em mensagens com vários anexos no layout de lista.

### <a name="rest-api"></a>API REST

Para emitir uma atualização de mensagem, basta executar uma solicitação PUT no `/v3/conversations/<conversationId>/activities/<activityId>/` ponto de extremidade usando uma determinada ID de atividade. Para concluir esse cenário, você deve armazenar em cache a ID da atividade retornada pela chamada POST original.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>Exemplo .NET

Você pode usar o `UpdateActivityAsync` método no SDK do bot Builder para atualizar uma mensagem existente.

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

### <a name="nodejs-example"></a>Exemplo do node. js

Você pode usar o `session.connector.update` método no SDK do bot Builder para atualizar uma mensagem existente.

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

## <a name="starting-a-conversation-proactive-messaging"></a>Iniciar uma conversa (mensagens pró-ativas)

Você pode criar uma conversa pessoal com um usuário ou iniciar uma nova cadeia de resposta em um canal para o bot da equipe. Isso permite que você envie mensagens para o usuário ou usuários sem que eles iniciem o contato pela primeira vez com o bot. Para obter mais informações, consulte os seguintes tópicos:

Consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter informações mais gerais sobre conversas iniciadas por bots.

## <a name="deleting-messages"></a>Excluir mensagens

As mensagens podem ser excluídas usando [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) o método Connectors no [SDK do BotBuilder](/bot-framework/bot-builder-overview-getstarted).

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
