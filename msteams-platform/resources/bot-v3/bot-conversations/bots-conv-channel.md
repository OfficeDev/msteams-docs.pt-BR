---
title: Conversas de chat de canal e grupo com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: teams scenarios channels conversation bot
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: 8e4336e8b0db7c6c720b8fb7adcb281685b6a6ba
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155187"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Canais e conversas de chat em grupo com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams permite que os usuários tragam bots para seus canais ou conversas de chat em grupo. Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem tirar proveito da funcionalidade do bot logo na conversa. Você também pode acessar Teams funcionalidade específica do bot, como consultar informações da equipe e @mentioning usuários.

O chat em canais e chats de grupo difere do chat pessoal, já que o usuário precisa @mention o bot. Se um bot for usado em vários escopos, como pessoal, groupchat ou canal, você precisará detectar de que escopo as mensagens bot vieram e processá-las de acordo.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Criar um ótimo bot para canais ou grupos

Os bots adicionados a uma equipe se tornam outro membro da equipe e podem ser @mentioned como parte da conversa. Na verdade, os bots só recebem mensagens quando @mentioned, portanto, outras conversas no canal não são enviadas para o bot.

Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros. Embora o bot certamente possa fornecer informações relevantes para a experiência, tenha em mente que as conversas com ele são visíveis para todos. Portanto, um ótimo bot em um grupo ou canal deve adicionar valor a todos os usuários e, certamente, não compartilhar inadvertidamente informações mais apropriadas a uma conversa um para um.

Seu bot, assim como está, pode ser totalmente relevante em todos os escopos sem exigir trabalho adicional. No Microsoft Teams não há expectativa de que sua função bot funcione em todos os escopos, mas você deve garantir que o bot fornece valor ao usuário em qualquer escopo que você optar por dar suporte. Para obter mais informações sobre escopos, consulte [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

O desenvolvimento de um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade que conversas pessoais. Eventos e dados adicionais na carga fornecem informações Teams grupo e canal. Essas diferenças, bem como as principais diferenças na funcionalidade comum são descritas nas seções a seguir.

### <a name="creating-messages"></a>Criando mensagens

Para obter mais informações sobre bots que criam mensagens em canais, consulte [Mensagens proativas](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)para bots e, [especificamente, Criando uma conversa de canal.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation)

### <a name="receiving-messages"></a>Recebimento de mensagens

Para um bot em um grupo ou canal, além do esquema de mensagens [regular,](https://docs.botframework.com/core-concepts/reference/#activity)o bot também recebe as seguintes propriedades:

* `channelData`Consulte [Teams dados do canal](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Em um chat em grupo, contém informações específicas para esse chat.
* `conversation.id` A ID da cadeia de resposta, que consiste na ID do canal mais a ID da primeira mensagem na cadeia de resposta.
* `conversation.isGroup` É `true` para mensagens bot em canais ou chats de grupo.
* `conversation.conversationType` Ou `groupChat` `channel` .
* `entities` Pode conter uma ou mais menções. Para obter mais informações, consulte [Menções](#-mentions).

### <a name="replying-to-messages"></a>Responder a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) o .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js. O SDK do Construtor de Bots lida com todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto de extremidade.

Em um canal, responder a uma mensagem mostra como uma resposta à cadeia de resposta de inicialização. O `conversation.id` contém o canal e a ID da mensagem de nível superior. Embora a Estrutura de Bots cuide dos detalhes, você pode armazenar em cache isso para respostas futuras a `conversation.id` esse thread de conversa, conforme necessário.

### <a name="best-practice-welcome-messages-in-teams"></a>Prática prática: mensagens de boas-vindas no Teams

Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários. A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade e dos benefícios do usuário do bot. O ideal é que a mensagem também inclua comandos para o usuário interagir com o aplicativo. Para fazer isso, verifique se o bot responde à `conversationUpdate` mensagem, com `teamsAddMembers` o eventType no `channelData` objeto. Certifique-se de que a ID seja a própria ID do aplicativo do bot, pois o mesmo evento é enviado quando um usuário é `memberAdded` adicionado a uma equipe. Consulte [Membro da equipe ou adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, você pode [buscar a lista de](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) equipe e enviar a cada usuário uma mensagem [direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

Recomendamos que seu bot *não* envie uma mensagem de boas-vindas nas seguintes situações:

* A equipe é grande (obviamente subjetivo, por exemplo, mais de 100 membros). Seu bot pode ser visto como "spammy" e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal, em vez de ser adicionado pela primeira vez a uma equipe.
* Um grupo ou canal é renomeado.
* Um membro da equipe é adicionado a um grupo ou canal.

## <a name="-mentions"></a>@ Menções

Como os bots em um grupo ou canal respondem somente quando eles são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que a análise da mensagem lida com isso. Além disso, os bots podem analisar outros usuários mencionados e mencionar usuários como parte de suas mensagens.

### <a name="retrieving-mentions"></a>Recuperando menções

As menções são retornadas no objeto em carga e contêm a ID exclusiva do usuário e, na maioria dos casos, o `entities` nome do usuário mencionado. Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de Bots para .NET, que retorna uma `GetMentions` matriz de `Mentioned` objetos.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo do .NET: verifique e @bot menção

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
> Você também pode usar a função Teams de extensão , que retira todas as `GetTextWithoutMentions` menções, incluindo o bot.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Node.js código de exemplo: verifique e @bot menção

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

Você também pode usar a função Teams de extensão , que retira todas as `getTextWithoutMentions` menções, incluindo o bot.

### <a name="constructing-mentions"></a>Criar menções

Seu bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

* Inclua `<at>@username</at>` no texto da mensagem.
* Inclua o `mention` objeto dentro da coleção de entidades.

#### <a name="net-example"></a>Exemplo do .NET

Este exemplo usa o [pacote Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.

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

#### <a name="example-outgoing-message-with-user-mentioned"></a>Exemplo: mensagem de saída com o usuário mencionado

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

## <a name="accessing-groupchat-or-channel-scope"></a>Acessando groupChat ou escopo de canal

Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes. Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais. Para obter mais informações, [consulte Obter contexto para seu Microsoft Teams bot](~/resources/bot-v3/bots-context.md).

## <a name="see-also"></a>Confira também

[Exemplos de Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
