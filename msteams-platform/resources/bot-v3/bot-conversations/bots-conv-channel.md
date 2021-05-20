---
title: Conversas de bate-papo de canal e grupo com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal em Microsoft Teams
keywords: cenários equipes canais chat bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: e254302271cf101638c897e1a1952d302705d6a4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566793"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Canais e conversas de chat em grupo com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams permite que os usuários tragam bots para suas conversas de canal ou chat em grupo. Ao adicionar um bot a uma equipe ou bate-papo, todos os usuários da conversa podem aproveitar a funcionalidade do bot apenas na conversa. Você também pode acessar Teams funcionalidade específica dentro do seu bot, como consultar informações da equipe e @mentioning usuários.

Chat em canais e bate-papos em grupo diferem do bate-papo pessoal na forma de que o usuário precisa @mention o bot. Se um bot for usado em vários escopos, como pessoal, groupchat ou canal, você precisa detectar de que escopo as mensagens do bot vieram e processá-las de acordo.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Projetando um ótimo bot para canais ou grupos

Bots adicionados a uma equipe tornam-se outro membro da equipe e podem ser @mentioned como parte da conversa. Na verdade, os bots só recebem mensagens quando são @mentioned, de modo que outras conversas no canal não são enviadas para o bot.

Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros. Embora seu bot certamente possa fornecer qualquer informação relevante para a experiência, tenha em mente que as conversas com ele são visíveis para todos. Portanto, um grande bot em um grupo ou canal deve agregar valor a todos os usuários, e certamente não compartilhar inadvertidamente informações mais apropriadas para uma conversa um-para-um.

Seu bot, assim como é, pode ser inteiramente relevante em todos os escopos sem exigir trabalho adicional. Em Microsoft Teams não há expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que seu bot forneça valor ao usuário em qualquer escopo que você escolher para suportar. Para obter mais informações sobre escopos, consulte [Aplicativos em Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

Desenvolver um bot que funciona em grupos ou canais usa muito da mesma funcionalidade que conversas pessoais. Eventos adicionais e dados na carga fornecem informações Teams grupo e canal. Essas diferenças, bem como as principais diferenças na funcionalidade comum são descritas nas seguintes seções.

### <a name="creating-messages"></a>Criando mensagens

Para obter mais informações sobre bots criando mensagens em canais, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)e criando especificamente [uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Recebimento de mensagens

Para um bot em um grupo ou canal, além do [esquema de mensagem regular,](https://docs.botframework.com/core-concepts/reference/#activity)o bot também recebe as seguintes propriedades:

* `channelData`Veja [os dados do canal Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Em um bate-papo em grupo, contém informações específicas para esse bate-papo.
* `conversation.id` O ID da cadeia de resposta, que consiste no ID do canal mais o ID da primeira mensagem na cadeia de resposta.
* `conversation.isGroup` É `true` para mensagens de bot em canais ou chats em grupo.
* `conversation.conversationType` Ou você `groupChat` `channel` ou.
* `entities` Pode conter uma ou mais menções. Para obter mais informações, consulte [Mentions](#-mentions).

### <a name="replying-to-messages"></a>Respondendo às mensagens

Para responder a uma mensagem existente, ligue [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) para .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) em Node.js. O Bot Builder SDK lida com todos os detalhes.

Se você optar por usar a API REST, você também pode chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto final.

Em um canal, responder a uma mensagem mostra como resposta à cadeia de resposta inicial. O `conversation.id` contém o canal e o ID de mensagem de nível superior. Embora o Bot Framework cuide dos detalhes, você pode armazenar isso `conversation.id` para respostas futuras a esse segmento de conversa, conforme necessário.

### <a name="best-practice-welcome-messages-in-teams"></a>Melhores práticas: Mensagens de boas-vindas em Teams

Quando o seu bot é adicionado pela primeira vez ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot a todos os usuários. A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário. Idealmente, a mensagem também deve incluir comandos para o usuário interagir com o aplicativo. Para fazer isso, certifique-se de que seu bot responda à `conversationUpdate` mensagem, com o `teamsAddMembers` eventType no `channelData` objeto. Certifique-se de que o `memberAdded` ID é o próprio App ID do bot, pois o mesmo evento é enviado quando um usuário é adicionado a uma equipe. Consulte [a adição de membro da equipe ou bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, você pode [buscar a lista da equipe](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) e enviar uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)a cada usuário .

Recomendamos que seu bot *não* envie uma mensagem de boas-vindas nas seguintes situações:

* A equipe é grande (obviamente subjetiva, por exemplo, mais de 100 membros). Seu bot pode ser visto como 'spammy' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do seu bot para todos que virem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal, em vez de ser adicionado pela primeira vez a uma equipe.
* Um grupo ou canal é renomeado.
* Um membro da equipe é adicionado a um grupo ou canal.

## <a name="-mentions"></a>@ Menções

Como os bots em um grupo ou canal respondem apenas quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome, e você deve garantir que sua mensagem de análise seja manipulação disso. Além disso, os bots podem analisar outros usuários mencionados e mencionar os usuários como parte de suas mensagens.

### <a name="retrieving-mentions"></a>Recuperando menções

As menções são devolvidas no `entities` objeto em carga útil e contêm tanto o ID exclusivo do usuário quanto, na maioria dos casos, o nome do usuário mencionado. Você pode recuperar todas as menções na mensagem chamando a `GetMentions` função no Bot Builder SDK para .NET, que retorna uma matriz de `Mentioned` objetos.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo .NET: Verifique e despoja @bot menção

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
> Você também pode usar a função de extensão `GetTextWithoutMentions` Teams, que tira todas as menções, incluindo o bot.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>código de exemplo Node.js: Verifique e tire @bot menção

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

Você também pode usar a função de extensão `getTextWithoutMentions` Teams, que tira todas as menções, incluindo o bot.

### <a name="constructing-mentions"></a>Construindo menções

Seu bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

* Inclua `<at>@username</at>` no texto da mensagem.
* Inclua o `mention` objeto dentro da coleção de entidades.

#### <a name="net-example"></a>Exemplo .NET

Este exemplo usa o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.

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

#### <a name="example-outgoing-message-with-user-mentioned"></a>Exemplo: Mensagem de saída com usuário mencionado

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

## <a name="accessing-groupchat-or-channel-scope"></a>Acessando o grupoChat ou escopo do canal

Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes. Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais. Para obter mais informações, consulte [Obter contexto para o seu Microsoft Teams bot](~/resources/bot-v3/bots-context.md).

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
