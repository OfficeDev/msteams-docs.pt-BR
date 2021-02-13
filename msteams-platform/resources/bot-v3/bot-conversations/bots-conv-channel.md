---
title: Conversas de chat de canal e grupo com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: bot de conversa de canais de cenários de equipes
ms.date: 06/25/2019
ms.openlocfilehash: e556eb006257a83ddf93adb62f79857201d6a9ad
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231628"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Conversas de chat de canal e grupo com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários traga bots para suas conversas de chat em grupo ou canal. Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem tirar proveito da funcionalidade do bot na conversa. Você também pode acessar a funcionalidade específica do Teams no seu bot, como consultar informações da equipe e @mentioning usuários.

Os chats em canais e chats em grupo diferem do chat pessoal, já que o usuário precisa @mention o bot. Se um bot for usado em vários escopos (pessoal, chat em grupo ou canal), você precisará detectar de qual escopo as mensagens de bot vieram e processá-las de acordo.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Projetando um ótimo bot para canais ou grupos

Os bots adicionados a uma equipe se tornam outro membro da equipe e podem ser @mentioned como parte da conversa. Na verdade, os bots só recebem mensagens quando estão @mentioned, portanto, outras conversas no canal não são enviadas para o bot.

Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros. Embora seu bot certamente possa fornecer informações relevantes para a experiência, tenha em mente que as conversas com ele ficam visíveis para todos. Portanto, um ótimo bot em um grupo ou canal deve agregar valor a todos os usuários e, certamente, não compartilhar inadvertidamente informações mais apropriadas para uma conversa um-para-um.

Seu bot, assim como está, pode ser inteiramente relevante em todos os escopos sem exigir trabalho adicional. No Microsoft Teams, não há expectativas de que seu bot funcione em todos os escopos, mas você deve garantir que seu bot fornece valor ao usuário em qualquer escopo que você escolher suportar. Para obter mais informações sobre escopos, consulte [Aplicativos no Microsoft Teams.](~/concepts/build-and-test/app-studio-overview.md)

Desenvolver um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade que as conversas pessoais. Eventos e dados adicionais na carga fornecem informações de grupo e canal do Teams. Essas diferenças, bem como as principais diferenças na funcionalidade comum, são descritas nas seções a seguir.

### <a name="creating-messages"></a>Criando mensagens

For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Receber mensagens

Para um bot em um grupo ou canal, além do esquema de mensagens [regular,](https://docs.botframework.com/core-concepts/reference/#activity)seu bot também recebe as seguintes propriedades:

* `channelData`Confira os [dados do canal do Teams.](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data) Em um chat de grupo, contém informações específicas para esse chat.
* `conversation.id` A ID da cadeia de resposta, consistindo na ID do canal mais a ID da primeira mensagem na cadeia de resposta
* `conversation.isGroup` É `true` para mensagens de bot em canais ou chats de grupo
* `conversation.conversationType` Uma `groupChat` ou outra `channel`
* `entities`Pode conter uma ou mais menções (consulte [Menções)](#-mentions)

### <a name="replying-to-messages"></a>Respondendo a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) no .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) no Node.js. O SDK do Construtor de Bots lida com todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto de extremidade.

Em um canal, responder a uma mensagem é uma resposta à cadeia de resposta inicial. Contém `conversation.id` o canal e a ID da mensagem de nível superior. Embora o Bot Framework se encadee dos detalhes, você pode armazenar em cache isso para respostas futuras a `conversation.id` esse thread de conversa, conforme necessário.

### <a name="best-practice-welcome-messages-in-teams"></a>Práticas práticas: Mensagens de boas-vindas no Teams

Quando seu bot é adicionado pela primeira vez ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários. A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário. O ideal é que a mensagem também inclua comandos para que o usuário interaja com o aplicativo. Para fazer isso, certifique-se de que seu bot responda à `conversationUpdate` mensagem, com `teamsAddMembers` o eventType no `channelData` objeto. Certifique-se de que a ID seja a própria ID do aplicativo do bot, pois o mesmo evento é enviado quando um usuário `memberAdded` é adicionado a uma equipe. Consulte [o membro da equipe ou a adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, você pode [buscar a lista de participação da](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) equipe e enviar uma mensagem direta a cada [usuário.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)

Recomendamos que seu bot *não envie* uma mensagem de boas-vindas nas seguintes situações:

* A equipe é grande (obviamente inentente, mas, por exemplo, maior do que 100 membros). Seu bot pode ser visto como "spammy" e a pessoa que o adicionou poderá receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado pela primeira vez a uma equipe)
* Um grupo ou canal é renomeado
* Um membro da equipe é adicionado a um grupo ou canal

## <a name="-mentions"></a>@ Menções

Como os bots em um grupo ou canal respondem somente quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome, e você deve garantir que a análise de mensagens lida com isso. Além disso, os bots podem analisar outros usuários mencionados e mencionar usuários como parte de suas mensagens.

### <a name="retrieving-mentions"></a>Recuperar menções

As menções são retornadas no objeto na carga e contêm a ID exclusiva do usuário e, na maioria dos casos, o nome `entities` do usuário mencionado. Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de Bots para .NET, que retorna uma `GetMentions` matriz de `Mentioned` objetos.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo do .NET: verificar e retirar @bot menção

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
> Você também pode usar a função de extensão do Teams `GetTextWithoutMentions` , que retira todas as menções, incluindo o bot.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js exemplo de código: verificar e retirar @bot menção

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

Você também pode usar a função de extensão do Teams `getTextWithoutMentions` , que retira todas as menções, incluindo o bot.

### <a name="constructing-mentions"></a>Construir menções

Seu bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

* Incluir `<at>@username</at>` no texto da mensagem
* Incluir o `mention` objeto dentro da coleção de entidades

#### <a name="net-example"></a>Exemplo de .NET

Este exemplo usa o [pacote NuGet Microsoft.Bot.Connector.Teams.](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a>Node.js exemplo

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

#### <a name="example-outgoing-message-with-user-mentioned"></a>Exemplo: Mensagem de saída com o usuário mencionado

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

## <a name="accessing-groupchat-or-channel-scope"></a>Acessando o escopo de groupChat ou canal

Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes. Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais. Confira [Obter contexto para seu bot do Microsoft Teams](~/resources/bot-v3/bots-context.md) para saber mais.

*Consulte também exemplos* [de Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
