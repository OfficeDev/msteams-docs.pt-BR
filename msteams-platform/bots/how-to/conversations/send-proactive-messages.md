---
title: enviar mensagens proativas
description: descreve como enviar mensagens proativas com seu bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
Keywords: enviar uma mensagem obter a ID de conversa do canal de ID do usuário
ms.openlocfilehash: 2d7ff10469a181bb06fda5029c8f6b2725b0402d
ms.sourcegitcommit: 7db6eabe3ef128ac7f14b32d07e9e86c995d187f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2021
ms.locfileid: "50103602"
---
# <a name="send-proactive-messages"></a>Enviar mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta direta a uma solicitação de um usuário. Isso pode incluir mensagens como:

* Mensagens de boas-vindas
* Notificações
* Mensagens agendadas

Para que seu bot envie uma mensagem proativa, ele deve ter acesso ao usuário, chat em grupo ou equipe para a quem você deseja enviar a mensagem. Para um chat ou uma equipe de grupo, isso significa que o aplicativo que contém seu bot deve ser instalado nesse local primeiro. Você pode [instalar proativamente](#proactively-install-your-app-using-graph) seu aplicativo usando o Graph [](/microsoftteams/teams-custom-app-policies-and-settings) em uma equipe, se necessário, ou usar uma política de aplicativo para por push de aplicativos para equipes e usuários em seu locatário. Para os usuários, seu aplicativo deve ser instalado para o usuário ou o usuário deve fazer parte de uma equipe em que seu aplicativo está instalado.

Enviar uma mensagem proativa é diferente de enviar uma mensagem normal. In that, there is no active `turnContext` to use for a reply. Talvez também seja necessário criar a conversa antes de enviar a mensagem. Por exemplo, um novo chat um-para-um ou um novo thread de conversa em um canal. Você não pode criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.

Em um nível alto, as etapas que você precisará concluir para enviar uma mensagem proativa são:

1. [Obter a ID de usuário ou a ID de equipe/canal](#get-the-user-id-or-teamchannel-id) (se necessário).
1. [Crie o thread de conversa ou conversa](#create-the-conversation) (se necessário).
1. [Obter a ID da conversa.](#get-the-conversation-id)
1. [Envie a mensagem.](#send-the-message)

Os trechos de código na seção [de exemplos](#examples) são para criar uma conversa um-para-um. Para links para concluir amostras de trabalho para conversas de um para um e grupo ou canais, consulte [exemplos de código.](#code-samples)

## <a name="get-the-user-id-or-teamchannel-id"></a>Obter a ID de usuário ou a ID de equipe/canal

Para criar um novo thread de conversa ou conversa em um canal, você precisa da ID correta. Você pode receber ou recuperar essa ID de várias maneiras:

1. Quando seu aplicativo for instalado em qualquer contexto específico, você receberá uma [ `onMembersAdded` Atividade.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
1. Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você receberá uma [ `onMembersAdded` Atividade.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
1. Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe em que seu aplicativo está instalado.
1. Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe em que seu aplicativo está instalado.
1. Todas as atividades que seu bot recebe devem conter as informações necessárias.

Independentemente de como você obtenha as informações, será necessário armazenar o ou criar `tenantId` `userId` uma nova `channelId` conversa. Você também pode usar o `teamId` para criar um novo thread de conversa no canal geral ou padrão de uma equipe.

Ela `userId` é exclusiva para sua ID de bot e um usuário específico, você não pode re usá-los entre bots. No entanto, é global, seu bot deve ser instalado na equipe antes que você possa enviar uma mensagem `channelId` proativa para um canal.

## <a name="create-the-conversation"></a>Criar a conversa

Depois de ter as informações do usuário ou do canal, você precisará criar a conversa se ela ainda não existir ou você não sabe o `conversationId` . Você só deve criar a conversa uma vez e certificar-se de armazenar o `conversationId` valor ou objeto a ser usado no `conversationReference` futuro.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Depois que a conversa for criada, use o `conversationReference` objeto ou e envie a `conversationId` `tenantId` mensagem. Você pode obter essa ID criando a conversa ou armazenar a partir de qualquer Atividade enviada a você a partir desse contexto. Certifique-se de armazenar essa ID.

## <a name="send-the-message"></a>Enviar a mensagem

Agora que você tem as informações de endereço corretas, pode enviar sua mensagem. Se você estiver usando o SDK, você fará isso usando o método e o e para `continueConversation` fazer uma chamada direta à `conversationId` `tenantId` API. Você deve definir o `conversationParameters` corretamente para enviar sua mensagem com êxito. Consulte a [seção de exemplos](#examples) ou use um dos exemplos listados na seção [de exemplos de](#code-samples) código.

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira muito eficaz de se comunicar com seus usuários. No entanto, de acordo com a perspectiva, essa mensagem pode parecer completamente nãompida e, no caso de mensagens de boas-vindas, é a primeira vez que elas interagem com seu aplicativo. Portanto, é muito importante usar essa funcionalidade com moderação, não enviar spam para os usuários e fornecer informações suficientes para permitir que os usuários entendam por que estão sendo mensagens.

### <a name="welcome-messages"></a>Mensagens de boas-vindas

Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas que recebem a mensagem, não há contexto para o motivo pelo qual elas a estão recebendo. Essa também é a primeira vez que eles interagem com seu aplicativo. É sua oportunidade de criar uma boa primeira impressão. As melhores mensagens de boas-vindas devem incluir:

* **Por que um usuário está recebendo a mensagem.** Deve ser muito claro para o usuário por que ele está recebendo a mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, avise em qual canal ele foi instalado e, potencialmente, quem o instalou.
* **O que você oferece.** O que eles podem fazer com seu aplicativo? Qual valor você pode trazer para eles?
* **O que eles devem fazer em seguida.** Convide-os para experimentar um comando ou interagir com seu aplicativo de alguma forma.

Lembre-se de que mensagens de boas-vindas ruins podem fazer com que os usuários bloqueem seu bot. Passe muito tempo preparando suas mensagens de boas-vindas e itere neles se elas não estão tendo o efeito desejado.

### <a name="notification-messages"></a>Mensagens de notificação

Ao usar mensagens proativas para enviar notificações, você deve garantir que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e um entendimento claro do motivo pelo qual a notificação ocorreu. As mensagens de notificação boas geralmente incluem:

* **O que aconteceu.** Uma indicação clara do que causou a notificação.
* **Qual foi o resultado.** Deve ser claro qual item ou coisa foi atualizado para causar a notificação.
* **Quem/o que a disparou.** Quem ou o que fez com que a notificação fosse enviada.
* **O que os usuários podem fazer em resposta.** Facilmente para os usuários tomarem ações com base em suas notificações.
* **Como os usuários podem optar por não fazer isso.** Você deve fornecer um caminho para que os usuários retivem notificações adicionais.

## <a name="proactively-install-your-app-using-graph"></a>Instalar seu aplicativo proativamente usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Microsoft Graph está atualmente na versão beta.

Ocasionalmente, pode ser necessário mensagens proativas de usuários que não tenham instalado ou interagido com seu aplicativo anteriormente. Por exemplo, você deseja usar o [comunicador da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a organização. Para esse cenário, você pode usar a API do Graph para instalar seu aplicativo proativamente para seus usuários e, em seguida, armazenar em cache os valores necessários do evento que seu aplicativo recebe `conversationUpdate` na instalação.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do Teams.

Consulte [Instalar aplicativos para usuários na](/graph/api/userteamwork-post-installedapps) documentação do Graph e instalação de bot proativo e mensagens no Teams com o Microsoft [Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) Há também um [exemplo do Microsoft .NET Framework](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.

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

Você deve fornecer a ID de usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará com o seguinte objeto de resposta.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a>Exemplos de código

Os exemplos oficiais de mensagens proativas são os seguinte:

| Nome do exemplo           | Descrição                                                                      | .NET    | JavaScript   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Noções básicas de conversa do Teams  | Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens proativas um-para-um.|[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|Iniciar novo thread em um canal     | Demonstra a criação de um novo thread em um canal. |[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a>Exibir exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Exemplos proativos de código de mensagens do Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
