---
title: Conversas de chat de canal e grupo com bots
description: Neste módulo, aprenda o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: e93b6cc18e38da4f6307fda3d30968bfa709dbf1
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190183"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Canais e conversas de chat em grupo com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários tragam bots para seu canal ou conversas de chat em grupo. Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem aproveitar a funcionalidade do bot diretamente na conversa. Você também pode acessar a funcionalidade específica do Teams em seu bot, como consultar informações da equipe e @mencionar usuários.

O chat em canais e chats em grupo difere do chat pessoal, já que o usuário precisa @mention o bot. Se um bot for usado em vários escopos, como pessoal, chat em grupo ou canal, você precisará detectar de qual escopo as mensagens do bot vieram e processá-las adequadamente.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Projetando um ótimo bot para canais ou grupos

Os bots adicionados a uma equipe se tornam outro membro da equipe e podem ser @mencionados como parte da conversa. Na verdade, os bots só recebem mensagens quando @mentioned, portanto, outras conversas no canal não são enviadas para o bot.

Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros. Embora seu bot certamente possa fornecer qualquer informação relevante para a experiência, lembre-se de que as conversas com ele são visíveis para todos. Portanto, um ótimo bot em um grupo ou canal deve agregar valor a todos os usuários e, certamente, não compartilhar inadvertidamente informações mais apropriadas para uma conversa individual.

Seu bot, assim como está, pode ser totalmente relevante em todos os escopos sem exigir mais trabalho. No Teams, não há nenhuma expectativa de que o bot funcione em todos os escopos, mas você deve garantir que seu bot forneça valor de usuário em qualquer escopo que você optar por dar suporte. Para obter mais informações sobre escopos, consulte [Aplicativos no Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

O desenvolvimento de um bot que funciona em grupos ou canais usa muito da mesma funcionalidade das conversas pessoais. Eventos e dados adicionais na carga útil fornecem informações de grupo e canal do Teams. Essas diferenças, bem como as principais diferenças na funcionalidade comum, são descritas nas seções a seguir.

### <a name="creating-messages"></a>Criando mensagens

Para obter mais informações sobre bots que criam mensagens em canais, consulte Mensagens [proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) e, especificamente, [Criando uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Recebendo mensagens

Para um bot em um grupo ou canal, além do [esquema de mensagem normal](https://docs.botframework.com/core-concepts/reference/#activity), seu bot também recebe as seguintes propriedades:

* `channelData` Consulte [Dados do canal do Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Em um chat em grupo, contém informações específicas desse chat.
* `conversation.id` O ID da cadeia de resposta, consistindo no ID do canal mais o ID da primeira mensagem na cadeia de resposta.
* `conversation.isGroup` É `true` para mensagens de bot em canais ou chats em grupo.
* `conversation.conversationType` Ou `groupChat` ou `channel`.
* `entities` Pode conter uma ou mais menções. Para obter mais informações, consulte [Menções](#-mentions).

### <a name="replying-to-messages"></a>Respondendo a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) em .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) em Node.js. O SDK do Bot Builder lida com todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o ponto de extremidade [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply).

Em um canal, responder a uma mensagem é exibido como uma resposta à cadeia de resposta inicial. O `conversation.id` contém o canal e o ID da mensagem de nível superior. Embora o Bot Framework cuide dos detalhes, você pode armazenar em cache esse `conversation.id` para futuras respostas a esse tópico de conversa, conforme necessário.

### <a name="best-practice-welcome-messages-in-teams"></a>Prática recomendada: mensagens de boas-vindas no Teams

Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, é útil enviar uma mensagem de boas-vindas apresentando o bot a todos os usuários. A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário. Idealmente, a mensagem também deve incluir comandos para o usuário interagir com o aplicativo. Para fazer isso, certifique-se de que seu bot responda à mensagem `conversationUpdate`, com o eventType `teamsAddMembers` no objeto `channelData`. Certifique-se de que o ID `memberAdded` seja o próprio ID do aplicativo do bot, pois o mesmo evento é enviado quando um usuário é adicionado a uma equipe. Para obter mais informações, consulte [o membro da equipe ou adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.

Você também pode enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, você pode [buscar a lista da equipe](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) e enviar a cada usuário uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

Recomendamos que seu bot *não* envie uma mensagem de boas-vindas nas seguintes situações:

* A equipe é grande (obviamente subjetiva, por exemplo, mais de 100 membros). Seu bot pode ser visto como 'spam' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do seu bot a todos que virem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal, em vez de ser adicionado pela primeira vez a uma equipe.
* Um grupo ou canal é renomeado.
* Um membro da equipe é adicionado a um grupo ou canal.

## <a name="-mentions"></a>@ Menções

Como os bots em um grupo ou canal respondem somente quando são mencionados ("@*botname*") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que a análise de mensagens lide com isso. Além disso, os bots podem analisar outros usuários mencionados e mencionar usuários como parte de suas mensagens.

### <a name="retrieving-mentions"></a>Recuperando menções

As menções são retornadas no objeto `entities` conteúdo e contêm a ID exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado. Você pode recuperar todas as menções na mensagem chamando a função `GetMentions` no SDK do Bot Builder para .NET, que retorna uma matriz de `Mentioned` objetos.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo .NET: verifique e retire a menção @bot

```csharp
Mention[] m = sourceMessage.GetMentions();
var messageText = sourceMessage.Text;

for (int i = 0;i < m.Length;i++)
{
    if (m[i].Mentioned.Id == sourceMessage.Recipient.Id)
    {
        //Bot is in the @mention list.
        //The below example will strip the bot name out of the message, so you can parse it as if it wasn't included. Note that the Text object will contain the full bot name, if applicable.
        if (m[i].Text != null)
            messageText = messageText.Replace(m[i].Text, "");
    }
}
```

> [!NOTE]
> Você também pode usar a função de extensão do Teams `GetTextWithoutMentions`, que remove todas as menções, incluindo o bot.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo do Node.js: verifique e retire a menção @bot

```javascript
var text = message.text;
if (message.entities) {
    message.entities
        .filter(entity => ((entity.type === "mention") && (entity.mentioned.id.toLowerCase() === botId)))
        .forEach(entity => {
            text = text.replace(entity.text, "");
        });
    text = text.trim();
}
```

Você também pode usar a função de extensão do Teams `getTextWithoutMentions`, que remove todas as menções, incluindo o bot.

### <a name="constructing-mentions"></a>Construindo menções

Seu bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

* Inclua `<at>@username</at>` no texto da mensagem.
* Inclua o objeto `mention` dentro da coleção de entidades.

#### <a name="net-example"></a>Exemplo .NET

Este exemplo usa o pacote NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a>Exemplo de Node.js

```javascript
// User to mention
var toMention: builder.IIdentity = {
    name: 'John Doe',
    id: userId
};

// Create a message and add mention to it
var msg = new teams.TeamsMessage(session).text(teams.TeamsMessage.getTenantId(session.message));
var mentionedMsg = msg.addMentionToText(toMention);

// Post the message
var generalMessage = mentionedMsg.routeReplyToGeneralChannel();
session.send(generalMessage);
```

#### <a name="example-outgoing-message-with-user-mentioned"></a>Exemplo: mensagem de saída com usuário mencionado

```json
{
    "type": "message", 
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "28:9e52142b-5e5e-4d7b-bb3e- e82dcf620000",
        "name": "SchemaTestBot"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

## <a name="accessing-groupchat-or-channel-scope"></a>Acessando o groupChat ou o escopo do canal

Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes. Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais. Para obter mais informações, consulte [Obter contexto para seu bot do Microsoft Teams](~/resources/bot-v3/bots-context.md).

## <a name="see-also"></a>Confira também

[Amostras de estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
