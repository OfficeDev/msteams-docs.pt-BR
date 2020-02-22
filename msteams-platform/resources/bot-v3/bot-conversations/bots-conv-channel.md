---
title: Conversas de chat de grupo e canal com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: bot de conversa de canais de cenários de equipe
ms.date: 06/25/2019
ms.openlocfilehash: d2d72bdba43de6ebb10c7504dd309459cb09d56c
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42227994"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Conversas de chat de grupo e canal com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários tragam bots para suas conversas de chat de grupo ou canal. Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem aproveitar o direito de funcionalidade de bot na conversa. Você também pode acessar a funcionalidade específica do teams no seu bot, como consultar informações da equipe de consulta e usuários do @mentioning.

O chat em canais e chats de grupo diferem do bate-papo pessoal, pois o usuário precisa @mention o bot. Se um bot for usado em vários escopos (pessoal, Groupchat ou canal), você precisará detectar de qual escopo as mensagens de bot vieram e processá-las de acordo.

## <a name="designing-a-great-bot-for-channels-or-groups"></a>Criando um ótimo bot para canais ou grupos

Os bots adicionados a uma equipe se tornarão outro membro da equipe, que pode ser @mentioned como parte da conversa. Na verdade, os bots só recebem mensagens quando estão @mentioned, portanto, outras conversas no canal não são enviadas para o bot.

> [!NOTE]
> Para conveniência ao responder a mensagens de bot em um canal, o nome do bot é anexado automaticamente na caixa de mensagem de composição.

Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros. Embora seu bot possa, certamente, fornecer qualquer informação relevante para a experiência, lembre-se de que as conversas com ela são visíveis para todos. Portanto, um grande bot em um grupo ou canal deve adicionar valor a todos os usuários e certamente não compartilha inadvertidamente as informações mais apropriadas em uma conversa de um para um.

Seu bot pode ser totalmente relevante em todos os escopos como está, e não é necessário nenhum trabalho extra significativo para permitir que o bot funcione entre eles. No Microsoft Teams, não há nenhuma expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que seu bot forneça o valor do usuário em qualquer escopo para o qual você opte por oferecer suporte. Para obter mais informações sobre escopos, consulte [aplicativos no Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).

O desenvolvimento de um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade de conversas pessoais. Eventos e dados adicionais na carga fornecem informações de grupo e canal do teams. Essas diferenças, bem como as principais diferenças em funcionalidades comuns, são descritas nas seções a seguir.

### <a name="creating-messages"></a>Criar mensagens

Para obter mais informações sobre bots Criando mensagens em canais, consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), e especificamente [criando uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).

### <a name="receiving-messages"></a>Receber mensagens

Para um bot em um grupo ou canal, além do esquema de [mensagem regular](https://docs.botframework.com/core-concepts/reference/#activity), seu bot também recebe as seguintes propriedades:

* `channelData`Consulte [dados do canal do teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data). Em um chat de grupo, contém informações específicas desse chat.
* `conversation.id`A ID da cadeia de resposta, consistindo na ID do canal mais a ID da primeira mensagem na cadeia de resposta
* `conversation.isGroup`É `true` para mensagens de bot em canais ou chats de grupo
* `conversation.conversationType`Um `groupChat` ou`channel`
* `entities`Podem conter uma ou mais mencionas (consulte [mencionas](#-mentions))

### <a name="replying-to-messages"></a>Respondendo a mensagens

Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) no .net ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) no node. js. O SDK do bot Builder trata de todos os detalhes.

Se você optar por usar a API REST, também poderá chamar o ponto [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) de extremidade.

Em um canal, responder a uma mensagem é exibido como uma resposta para a cadeia de resposta inicial. O `conversation.id` contém o canal e a ID da mensagem de nível superior. Embora a estrutura de bot se encarrega dos detalhes, você pode armazenar em `conversation.id` cache as respostas futuras para esse segmento de conversa, conforme necessário.

### <a name="best-practice-welcome-messages-in-teams"></a>Práticas recomendadas: mensagens de boas-vindas no Teams

Quando seu bot é adicionado ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários. A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário. O ideal é que a mensagem também inclua comandos para o usuário interagir com o aplicativo. Para fazer isso, certifique-se de que seu bot `conversationUpdate` responda à mensagem com `teamsAddMembers` o EventType no `channelData` objeto. Certifique-se de `memberAdded` que a ID é a própria ID de aplicativo do bot, porque o mesmo evento é enviado quando um usuário é adicionado a uma equipe. Confira o [membro da equipe ou a adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot é adicionado. Para fazer isso, você poderia [buscar a lista de equipes](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) e enviar uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)a cada usuário.

Recomendamos que o bot *não* envie uma mensagem de boas-vindas nas seguintes situações:

* A equipe é grande (obviamente subjetiva, mas por exemplo, mais de 100 membros). Seu bot pode ser visto como ' spam ' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos os usuários que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado a uma equipe)
* Um grupo ou canal é renomeado
* Um membro da equipe é adicionado a um grupo ou canal

## <a name="-mentions"></a>@ Menciona

Como os bots em um grupo ou canal respondem apenas quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que as alças de análise da mensagem. Além disso, os bots podem analisar outros usuários mencionados e mencionar os usuários como parte de suas mensagens.

### <a name="retrieving-mentions"></a>Como recuperar menção

As menção são retornadas no `entities` objeto no Payload e contêm a identificação exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado. Você pode recuperar todas as menção na mensagem chamando a `GetMentions` função no SDK do bot Builder para .net, que retorna uma matriz de `Mentioned` objetos.

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo .NET: verificar e remover @bot mencionar

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
> Você também pode usar a função `GetTextWithoutMentions`de extensão do Teams, que retira todas as menção, incluindo o bot.

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a>Código de exemplo do node. js: verificar e remover @bot mencionar

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

Você também pode usar a função `getTextWithoutMentions`de extensão do Teams, que retira todas as menção, incluindo o bot.

### <a name="constructing-mentions"></a>Como criar menção

O bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

* Incluir `<at>@username</at>` no texto da mensagem
* Incluir o `mention` objeto dentro da coleção Entities

#### <a name="net-example"></a>Exemplo .NET

Este exemplo usa o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a>Exemplo do node. js

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

Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes. Por exemplo, também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais. Consulte [obter contexto para o bot do Microsoft Teams](~/resources/bot-v3/bots-context.md) para saber mais.

*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
