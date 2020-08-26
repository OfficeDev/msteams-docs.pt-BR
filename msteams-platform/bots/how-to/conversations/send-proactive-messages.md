---
title: Enviar mensagens proativas
author: clearab
description: Como enviar mensagens pró-ativas com o bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2dfb8e18243079ca38d505f4b80deb7abf2de32f
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874846"
---
# <a name="send-proactive-messages"></a>Enviar mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta direta a uma solicitação de um usuário. Isso pode incluir mensagens como:

* Mensagens de boas-vindas
* Notificações
* Mensagens agendadas

Para que o bot envie uma mensagem pró-ativa, ele deve ter acesso ao usuário, ao chat de grupo ou à equipe para a qual você deseja enviar a mensagem. Para um chat de grupo ou equipe, isso significa que o aplicativo que contém o bot deve primeiro ser instalado nesse local. Você pode [instalar proativamente seu aplicativo usando o Graph](#proactively-install-your-app-using-graph) em uma equipe, se necessário, ou usar uma [política de aplicativo](/microsoftteams/teams-custom-app-policies-and-settings) para enviar aplicativos para o Microsoft Teams e usuários em seu locatário. Para os usuários, seu aplicativo precisa ser instalado para esse usuário, ou o usuário precisa fazer parte de uma equipe onde seu aplicativo está instalado.

O envio de uma mensagem pró-ativa é diferente do envio de uma mensagem regular, pois você não terá um ativo `turnContext` para ser usado para uma resposta. Você também pode precisar criar a conversa (por exemplo, um novo chat de um-para-um ou um novo thread de conversa em um canal) antes de enviar a mensagem. Você não pode criar um novo chat de grupo ou um novo canal em uma equipe com mensagens proativas.

Em um nível alto, as etapas que você precisa concluir para enviar uma mensagem pró-ativa são:

1. [Obtenha a ID de usuário ou ID de canal/equipe](#get-the-user-id-or-teamchannel-id) (se necessário).
1. [Crie a conversa ou thread de conversa](#create-the-conversation) (se necessário).
1. [Obtenha a ID da conversa](#get-the-conversation-id).
1. [Envie a mensagem](#send-the-message).

Os trechos de código na seção de [exemplos](#examples) abaixo são para a criação de uma conversa de um-para-um, consulte a seção de [referências](#references) para obter links de exemplos de trabalho completos para conversas de uma única vez e grupo/canais.

## <a name="get-the-user-id-or-teamchannel-id"></a>Obter a ID do usuário ou a ID do canal/equipe

Se você precisar criar uma nova conversa ou thread de conversa em um canal, precisará primeiro da ID correta para criar a conversa. Você pode receber/recuperar essa ID de várias maneiras:

1. Quando seu aplicativo for instalado em qualquer contexto específico, você receberá uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você receberá uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe que seu aplicativo está instalado.
1. Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe que seu aplicativo está instalado.
1. Toda atividade que seu bot recebe conterá as informações necessárias.

Independentemente de como você obtém as informações, você precisará armazenar o `tenantId` e o `userId` ou `channelId` para criar uma nova conversa. Você também pode usar o `teamId` para criar um novo thread de conversa no canal geral/padrão de uma equipe.

O `userId` é exclusivo do seu ID de bot e de um usuário específico, não é possível usá-los novamente entre bots. O `channelId` é global, mas seu bot _deve_ ser instalado na equipe antes que você possa enviar uma mensagem proativa para um canal.

## <a name="create-the-conversation"></a>Criar a conversa

Depois de ter as informações de usuário/canal, você precisará criar a conversa se ela ainda não existir (ou se você não souber o `conversationId` ). Você só deve criar a conversa uma vez; Certifique-se de armazenar o `conversationId` valor ou o `conversationReference` objeto a ser usado no futuro.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Após a criação da conversa, você usará o `conversationReference` objeto ou o `conversationId` e o `tenantId` para enviar a mensagem. Você pode obter essa ID criando a conversa ou armazenando-a de qualquer atividade enviada por esse contexto. Certifique-se de que armazenou essa ID.

## <a name="send-the-message"></a>Enviar a mensagem

Agora que você tem as informações de endereço corretas, você pode enviar a mensagem. Se você estiver usando o SDK, fará isso usando o método e `continueConversation` o `conversationId` e `tenantId` para fazer uma chamada de API direta.  Você precisará definir `conversationParameters` corretamente para enviar sua mensagem com êxito, consulte os [exemplos](#examples) abaixo ou use um dos exemplos listados na seção [referências](#references) .

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens pró-ativas para os usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários. No entanto, de sua perspectiva esta mensagem pode aparecer completamente sem confirmação e, no caso de mensagens de boas-vindas, será a primeira vez que interagem com seu aplicativo. Assim, é muito importante usar essa funcionalidade com moderação (não enviar spam aos usuários) e fornecer informações suficientes para permitir que os usuários entendam por que estão sendo messaged.

### <a name="welcome-messages"></a>Mensagens de boas-vindas

Ao usar o sistema de mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas receber a mensagem, não haverá nenhum contexto para o recebimento. Essa é também a primeira vez que terá interagindo com o aplicativo; é sua oportunidade de criar uma boa impressão em bom lugar. As melhores mensagens de boas-vindas incluirão:

* **Por que um usuário recebe a mensagem.** Deve estar muito claro para o usuário por que eles estão recebendo a mensagem. Se o seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas para todos os usuários, informe-o sobre o canal em que ele foi instalado e possivelmente quem o instalou.
* **O que você oferece.** O que eles podem fazer com o seu aplicativo? Que valor você pode trazer para eles?
* **O que deve ser feito em seguida.** Convide-os a experimentar um comando ou interagir com o aplicativo de alguma forma.

Lembre-se: as mensagens de boas-vindas podem levar a usuários que estão bloqueando o bot Você deve gastar bastante tempo para criar suas mensagens de boas-vindas e iterar neles se elas não estiverem tendo o efeito desejado.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você precisa certificar-se de que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara de por que a notificação ocorreu. Geralmente, as boas mensagens de notificação incluirão:

* **O que aconteceu.** Uma indicação clara do que aconteceu com a notificação.
* **Qual era o resultado.** Deve estar claro qual item/coisa foi atualizado para causar a notificação.
* **Quem/o disparou.** Quem ou o que executou a ação que provocou a envio da notificação.
* **O que os usuários podem fazer em resposta.** Facilite que os usuários executem ações com base em suas notificações.
* **Como os usuários podem recusar.** Você precisa fornecer um caminho para que os usuários recusem notificações adicionais.

## <a name="proactively-install-your-app-using-graph"></a>Instalar o aplicativo proativamente usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Microsoft Graph está atualmente em versão beta.

Ocasionalmente, pode ser necessário que usuários de mensagens de forma proativa não tenham sido instalados ou interagindo com o aplicativo anteriormente. Por exemplo, você deseja usar o [Communicator da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a sua organização. Para este cenário, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar em cache os valores necessários do `conversationUpdate` evento que seu aplicativo receberá na instalação.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do teams.

Confira [instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação de gráfico e [instalação e mensagens de bot proativas no Teams com o Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Há também um [exemplo do Microsoft .NET Framework](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  na plataforma github.

## <a name="examples"></a>Exemplos

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
private async Task MessageAllMembersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var teamsChannelId = turnContext.Activity.TeamsGetChannelId();
    var serviceUrl = turnContext.Activity.ServiceUrl;
    var credentials = new MicrosoftAppCredentials(_appId, _appPassword);
    ConversationReference conversationReference = null;

    //Get the set of member IDs to send the message to
    var members = await GetPagedMembers(turnContext, cancellationToken);

    foreach (var teamMember in members)
    {
        var proactiveMessage = MessageFactory.Text($"Hello {teamMember.GivenName} {teamMember.Surname}. I'm a Teams conversation bot.");

        var conversationParameters = new ConversationParameters
        {
            IsGroup = false,
            Bot = turnContext.Activity.Recipient,
            Members = new ChannelAccount[] { teamMember },
            TenantId = turnContext.Activity.Conversation.TenantId,
        };
        //create the new one-to-one conversations
        await ((BotFrameworkAdapter)turnContext.Adapter).CreateConversationAsync(
            teamsChannelId,
            serviceUrl,
            credentials,
            conversationParameters,
            async (t1, c1) =>
            {
                //Get the conversationReference
                conversationReference = t1.Activity.GetConversationReference();
                //Send the proactive message
                await ((BotFrameworkAdapter)turnContext.Adapter).ContinueConversationAsync(
                    _appId,
                    conversationReference,
                    async (t2, c2) =>
                    {
                        await t2.SendActivityAsync(proactiveMessage, c2);
                    },
                    cancellationToken);
            },
            cancellationToken);
    }

    await turnContext.SendActivityAsync(MessageFactory.Text("All messages have been sent."), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```javascript

async messageAllMembersAsync(context) {
    const members = await this.getPagedMembers(context);

    members.forEach(async (teamMember) => {
        const message = MessageFactory.text('Hello ${ teamMember.givenName } ${ teamMember.surname }. I\'m a Teams conversation bot.');

        var ref = TurnContext.getConversationReference(context.activity);
        ref.user = teamMember;

        await context.adapter.createConversation(ref,
            async (t1) => {
                const ref2 = TurnContext.getConversationReference(t1.activity);
                await t1.adapter.continueConversation(ref2, async (t2) => {
                    await t2.sendActivity(message);
                });
            });
    });

    await context.sendActivity(MessageFactory.text('All messages have been sent.'));
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _message_all_members(self, turn_context: TurnContext):
    team_members = await self._get_paged_members(turn_context)

    for member in team_members:
        conversation_reference = TurnContext.get_conversation_reference(
            turn_context.activity
        )

        conversation_parameters = ConversationParameters(
            is_group=False,
            bot=turn_context.activity.recipient,
            members=[member],
            tenant_id=turn_context.activity.conversation.tenant_id,
        )

        async def get_ref(tc1):
            conversation_reference_inner = TurnContext.get_conversation_reference(
                tc1.activity
            )
            return await tc1.adapter.continue_conversation(
                conversation_reference_inner, send_message, self._app_id
            )

        async def send_message(tc2: TurnContext):
            return await tc2.send_activity(
                f"Hello {member.name}. I'm a Teams conversation bot."
            )

        await turn_context.adapter.create_conversation(
            conversation_reference, get_ref, conversation_parameters
        )

    await turn_context.send_activity(
        MessageFactory.text("All messages have been sent")
    )

```

# <a name="json"></a>[JSON](#tab/json)

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

---

## <a name="references"></a>Referências

As amostras de mensagens pró-ativas oficiais estão listadas abaixo.

|  Não.  | Nome da amostra           | Descrição                                                                      | .NET    | JavaScript   | Python  |
|:--:|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|57|Noções básicas da conversa do teams  | Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens pró-ativas de um para um.|[&nbsp;Núcleo .net](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|58|Iniciar novo thread em um canal     | Demonstra como criar um novo thread em um canal. |[&nbsp;Núcleo .net](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

O exemplo a seguir demonstra a quantidade mínima de informações necessárias para enviar uma mensagem proativa (sem usar um `conversationReference` objeto). Este exemplo pode ser útil se você estiver usando chamadas de API REST diretamente ou não armazenou `conversationReference` objetos completos.

* [Mensagens proativas do teams](https://github.com/clearab/teamsProactiveMessaging)

## <a name="view-additional-code"></a>Exibir código adicional
>
> [!div class="nextstepaction"]
> [**Amostras de código de mensagens proativas do teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>