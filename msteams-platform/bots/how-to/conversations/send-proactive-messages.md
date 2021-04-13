---
title: enviar mensagens proativas
description: descreve como enviar mensagens proativas com seu bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
Keywords: enviar uma mensagem obter iD de conversa de canal de ID do usuário
ms.openlocfilehash: 7da470eaba6ae9ecb82c9a7ba04d69b2f196a9d7
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654290"
---
# <a name="send-proactive-messages"></a>Enviar mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta direta a uma solicitação de um usuário. Isso pode incluir mensagens como:

* Mensagem de boas-vindas
* Notificações
* Mensagens agendadas

Para que o bot envie uma mensagem proativa, ele deve ter acesso ao usuário, chat de grupo ou equipe para o que você deseja enviar a mensagem. Para um chat em grupo ou equipe, isso significa que o aplicativo que contém seu bot deve ser instalado nesse local primeiro. Você pode [instalar proativamente](#proactively-install-your-app-using-graph) seu aplicativo usando o Graph [](/microsoftteams/teams-custom-app-policies-and-settings) em uma equipe, se necessário ou usar uma política de aplicativo para empurrar aplicativos para equipes e usuários em seu locatário. Para os usuários, seu aplicativo deve ser instalado para o usuário ou seu usuário deve fazer parte de uma equipe em que seu aplicativo está instalado.

Enviar uma mensagem proativa é diferente de enviar uma mensagem regular. Nisso, não há nenhum ativo a `turnContext` ser usado para uma resposta. Você também pode precisar criar a conversa antes de enviar a mensagem. Por exemplo, um novo chat um para um ou um novo thread de conversa em um canal. Não é possível criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.

Em alto nível, as etapas que você precisará concluir para enviar uma mensagem proativa são:

1. [Obter a ID do usuário ou a ID de equipe/canal](#get-the-user-id-or-teamchannel-id) (se necessário).
1. [Crie o thread de conversa ou conversa](#create-the-conversation) (se necessário).
1. [Obter a ID da conversa](#get-the-conversation-id).
1. [Envie a mensagem](#send-the-message).

Os trechos de código na seção [exemplos](#examples) são para criar uma conversa um para um. Para links para concluir exemplos de trabalho para conversas um-para-um e grupos ou canais , consulte [exemplos de código](#code-samples).

## <a name="get-the-user-id-or-teamchannel-id"></a>Obter a ID do usuário ou a ID de equipe/canal

Para criar um novo thread de conversa ou conversa em um canal, você precisa da ID correta. Você pode receber ou recuperar essa ID de várias maneiras:

1. Quando seu aplicativo estiver instalado em qualquer contexto específico, você receberá um [ `onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você receberá um [ `onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Você pode recuperar a [lista de canais em](~/bots/how-to/get-teams-context.md) uma equipe que seu aplicativo está instalado.
1. Você pode recuperar a [lista de membros de](~/bots/how-to/get-teams-context.md) uma equipe que seu aplicativo está instalado.
1. Todas as atividades que seu bot recebe devem conter as informações necessárias.

Independentemente de como você obter as informações, você precisará armazenar e ou `tenantId` `userId` criar uma nova `channelId` conversa. Você também pode usar o para criar um novo thread de conversa no canal geral ou `teamId` padrão de uma equipe.

O é exclusivo da ID do bot e de um usuário específico, não é possível `userId` rea usá-los entre bots. O é global, no entanto, seu bot deve ser instalado na equipe antes de você poder enviar uma mensagem `channelId` proativa para um canal.

## <a name="create-the-conversation"></a>Criar a conversa

Depois de ter as informações do usuário ou do canal, você precisará criar a conversa se ela ainda não existir ou se você não sabe o `conversationId` . Você só deve criar a conversa uma vez e certificar-se de armazenar o `conversationId` valor ou objeto a ser usado no `conversationReference` futuro.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Depois que a conversa for criada, use o `conversationReference` objeto ou e envie a `conversationId` `tenantId` mensagem. Você pode obter essa ID criando a conversa ou o armazenamento de qualquer Atividade enviada a você a partir desse contexto. Certifique-se de armazenar essa ID.

## <a name="send-the-message"></a>Enviar a mensagem

Agora que você tem as informações de endereço corretas, você pode enviar sua mensagem. Se você estiver usando o SDK, fará isso usando o método e e para `continueConversation` fazer uma chamada de API `conversationId` `tenantId` direta. Você deve definir `conversationParameters` corretamente para enviar sua mensagem com êxito. Consulte a [seção exemplos](#examples) ou use um dos exemplos listados na seção [de exemplos de](#code-samples) código.

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira muito eficaz de se comunicar com seus usuários. No entanto, da perspectiva deles, essa mensagem pode parecer completamente não prompada e, no caso de mensagens de boas-vindas, é a primeira vez que elas interagem com seu aplicativo. Portanto, é muito importante usar essa funcionalidade com moderação, não spam de seus usuários e fornecer informações suficientes para permitir que os usuários entendam por que estão sendo mensagens.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas que recebem a mensagem, não há contexto para o motivo pelo qual ela está recebendo. Essa também é a primeira vez que eles interagem com seu aplicativo. É a oportunidade de criar uma boa primeira impressão. As melhores mensagens de boas-vindas devem incluir:

* **Por que um usuário está recebendo a mensagem.** Deve ser muito claro para o usuário por que ele está recebendo a mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e, potencialmente, quem o instalou.
* **O que você oferece.** O que eles podem fazer com seu aplicativo? Qual valor você pode trazer para eles?
* **O que eles devem fazer em seguida.** Convide-os para experimentar um comando ou interagir com seu aplicativo de alguma forma.

Lembre-se de que mensagens de boas-vindas ruins podem levar os usuários a bloquear seu bot. Passe muito tempo preparando suas mensagens de boas-vindas e itere-as se elas não estão tendo o efeito desejado.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você deve garantir que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara do motivo pelo qual a notificação ocorreu. As boas mensagens de notificação geralmente incluem:

* **O que aconteceu.** Uma indicação clara do que aconteceu para causar a notificação.
* **Qual foi o resultado.** Deve ser claro qual item ou coisa foi atualizado para causar a notificação.
* **Quem/o que a disparou.** Quem ou o que fez com que a notificação fosse enviada.
* **O que os usuários podem fazer em resposta.** Facilita a ação dos usuários com base em suas notificações.
* **Como os usuários podem optar por não fazer isso.** Você deve fornecer um caminho para os usuários não receberem notificações adicionais.

### <a name="scheduled-messages"></a>Mensagens agendadas

Ao usar mensagens proativas para enviar mensagens agendadas aos usuários, verifique se o fuso horário está atualizado para o fuso horário. Isso garante que as mensagens sejam entregues aos usuários no momento relevante. As mensagens de agenda geralmente incluem:

* **Por que o usuário está recebendo a** mensagem : facilitar para os usuários entenderem o motivo pelo qual estão recebendo a mensagem.
* **O que o usuário pode fazer em seguida:** os usuários podem tomar a ação necessária com base no conteúdo da mensagem.

## <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Microsoft Graph está atualmente em beta.

Ocasionalmente, pode ser necessário enviar mensagens proativas aos usuários que não tenham instalado ou interagido com seu aplicativo anteriormente. Por exemplo, você deseja usar o [comunicador da](~/samples/app-templates.md#company-communicator) empresa para enviar mensagens para toda a sua organização. Para esse cenário, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar em cache os valores necessários do evento que seu aplicativo recebe `conversationUpdate` após a instalação.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do Teams.

Consulte [Instalar aplicativos para usuários na](/graph/api/userteamwork-post-installedapps) documentação do Graph e instalação de bot proativo e mensagens no Teams com o Microsoft [Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) Também há um exemplo [de estrutura do Microsoft .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.

## <a name="examples"></a>Exemplos

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
[Route("api/notify")]
[ApiController]
public class NotifyController : ControllerBase
{
    private readonly IBotFrameworkHttpAdapter _adapter;
    private readonly string _appId;
    private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

    public NotifyController(IBotFrameworkHttpAdapter adapter, IConfiguration configuration, ConcurrentDictionary<string, ConversationReference> conversationReferences)
    {
        _adapter = adapter;
        _conversationReferences = conversationReferences;
        _appId = configuration["MicrosoftAppId"] ?? string.Empty;
    }

    public async Task<IActionResult> Get()
    {
        foreach (var conversationReference in _conversationReferences.Values)
        {
            await ((BotAdapter)_adapter).ContinueConversationAsync(_appId, conversationReference, BotCallback, default(CancellationToken));
        }
        
        // Let the caller know proactive messages have been sent
        return new ContentResult()
        {
            Content = "<html><body><h1>Proactive messages have been sent.</h1></body></html>",
            ContentType = "text/html",
            StatusCode = (int)HttpStatusCode.OK,
        };
    }

    private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
    {
        // If you encounter permission-related errors when sending this message, see
        // https://aka.ms/BotTrustServiceUrl
        await turnContext.SendActivityAsync("proactive hello");
    }
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

Você deve fornecer a ID do usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará com o objeto de resposta a seguir.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a>Exemplos de código

Os exemplos oficiais de mensagens proativas são:

| Exemplo de nome           | Descrição                                                                      | .NET    | JavaScript   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Noções básicas de conversa do Teams  | Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens proativas um para um.|[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|Iniciar novo thread em um canal     | Demonstra a criação de um novo thread em um canal. |[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a>Exibir exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Exemplos de código de mensagens proativas do Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
