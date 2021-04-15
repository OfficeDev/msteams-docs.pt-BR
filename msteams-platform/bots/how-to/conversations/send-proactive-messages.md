---
title: Enviar mensagens proativas
description: Descreve como enviar mensagens proativas com seu bot do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
Keywords: enviar uma mensagem obter iD de conversa de canal de ID do usuário
ms.openlocfilehash: 25d5c6a1b51240c87ff0d8610a965d30f6b01095
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697050"
---
# <a name="send-proactive-messages"></a>Enviar mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Isso pode incluir mensagens, como:

* Mensagem de boas-vindas
* Notificações
* Mensagens agendadas

Para que o bot envie uma mensagem proativa para um usuário, chat em grupo ou equipe, ele deve ter acesso para enviar a mensagem. Para um chat em grupo ou equipe, o aplicativo que contém seu bot deve ser instalado primeiro nesse local. Você pode [instalar proativamente](#proactively-install-your-app-using-graph) seu aplicativo usando o Microsoft Graph [](/microsoftteams/teams-custom-app-policies-and-settings) em uma equipe, se necessário, ou usar uma política de aplicativo para empurrar aplicativos para equipes e usuários em seu locatário. Para os usuários, seu aplicativo deve ser instalado para o usuário ou seu usuário deve fazer parte de uma equipe em que seu aplicativo está instalado.

Enviar uma mensagem proativa é diferente de enviar uma mensagem regular. Não há nenhum ativo `turnContext` a ser usado para uma resposta. Você deve criar a conversa antes de enviar a mensagem. Por exemplo, um novo chat um para um ou um novo thread de conversa em um canal. Não é possível criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.

**Para enviar uma mensagem proativa**

1. [Obter a ID do usuário, a ID da equipe ou a ID do](#get-the-user-id-team-id-or-channel-id)canal, se necessário.
1. [Crie a conversa](#create-the-conversation), se necessário.
1. [Obter a ID da conversa](#get-the-conversation-id).
1. [Envie a mensagem](#send-the-message).

Para usar mensagens proativas efetivamente, consulte [práticas recomendadas para mensagens proativas.](#best-practices-for-proactive-messaging) Para determinados cenários, você deve [instalar proativamente seu aplicativo usando Graph](#proactively-install-your-app-using-graph). Os trechos de código na seção [exemplos](#samples) são para criar uma conversa um para um. Para amostras completas de trabalho para conversas e grupos ou canais de um para um, consulte [amostra de código](#code-sample).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Obter a ID do usuário, a ID da equipe ou a ID do canal

Para criar um novo thread de conversa ou conversa em um canal, você deve ter a ID correta. Você pode receber ou recuperar essa ID usando qualquer um dos seguintes:

* Quando seu aplicativo é instalado em qualquer contexto específico, você recebe uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você recebe uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe onde seu aplicativo está instalado.
* Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe onde seu aplicativo está instalado.
* Todas as atividades que seu bot recebe devem conter as informações necessárias.

Independentemente de como você obter as informações, você deve armazenar e `tenantId` ou criar uma nova `userId` `channelId` conversa. Você também pode usar o para criar um novo thread de conversa no canal geral ou `teamId` padrão de uma equipe.

O `userId` é exclusivo da ID do bot e de um usuário específico. Não é possível reutilizar os `userId` bots entre. O `channelId` é global. No entanto, seu bot deve ser instalado na equipe antes de poder enviar uma mensagem proativa para um canal.

Depois de ter as informações do usuário ou do canal, você deve criar a conversa.

## <a name="create-the-conversation"></a>Criar a conversa

Você deve criar a conversa se ela não existir ou não conhecer `conversationId` o . Você só deve criar a conversa uma vez e armazenar `conversationId` o valor ou `conversationReference` objeto.

Após a criação da conversa, você deve obter a ID da conversa.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Use o `conversationReference` objeto ou e envie a `conversationId` `tenantId` mensagem. Você pode obter essa ID criando a conversa ou o armazenamento de qualquer atividade enviada a você a partir desse contexto. Armazene essa ID para referência.

Depois de obter as informações de endereço apropriadas, você pode enviar sua mensagem.

## <a name="send-the-message"></a>Enviar a mensagem

Se você estiver usando o SDK, deverá usar o método e e fazer uma chamada `continueConversation` de API direta para enviar a `conversationId` `tenantId` mensagem. Você deve definir `conversationParameters` corretamente para enviar sua mensagem com êxito.

Agora que você enviou a mensagem proativa, você deve seguir essas práticas recomendadas ao enviar mensagens proativas para melhor troca de informações entre usuários e o bot.

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira muito eficaz de se comunicar com seus usuários. No entanto, da perspectiva deles, essa mensagem pode parecer completamente não prompada e, no caso de mensagens de boas-vindas, é a primeira vez que elas interagem com seu aplicativo. Portanto, é muito importante usar mensagens proativas com moderação, não spam de seus usuários e fornecer informações suficientes para permitir que os usuários entendam por que estão recebendo as mensagens.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Quando as mensagens proativas são usadas para enviar uma mensagem de boas-vindas a um usuário, não há contexto para o motivo pelo qual os usuários recebem a mensagem. Essa também é a primeira vez que os usuários interagem com seu aplicativo. É uma oportunidade de criar uma boa primeira impressão. As melhores mensagens de boas-vindas devem incluir:

* Por que um usuário está recebendo a mensagem: deve ser muito claro para o usuário o motivo pelo qual ele está recebendo a mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e quem o instalou.
* O que você oferece: os usuários devem ser capazes de identificar o que podem fazer com seu aplicativo e qual valor você pode trazer para eles.
* O que eles devem fazer a seguir: convidar os usuários para experimentar um comando ou interagir com seu aplicativo.

Mensagens de boas-vindas ruins podem levar os usuários a bloquear seu bot. Escreva até o ponto e limpe as mensagens de boas-vindas. Iterar nas mensagens de boas-vindas se elas não estão tendo o efeito desejado.

### <a name="notification-messages"></a>Mensagens de notificação

Para enviar notificações usando mensagens proativas, certifique-se de que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação. Verifique se os usuários têm uma compreensão clara do motivo pelo qual receberam uma notificação. As boas mensagens de notificação geralmente incluem o seguinte:

* O que aconteceu: uma indicação clara do que aconteceu para causar a notificação.
* Qual foi o resultado: deve ser claro qual item foi atualizado para causar a notificação.
* Quem ou o que a acionou: Quem ou o que fez com que a notificação fosse enviada.
* O que os usuários podem fazer em resposta: facilitar a ação dos usuários com base em suas notificações.
* Como os usuários podem optar por não fazer isso: você deve fornecer um caminho para que os usuários optem por não receber notificações adicionais.

Para enviar mensagens para um grande grupo de usuários, por exemplo, para sua organização, instale proativamente seu aplicativo usando o Graph.

### <a name="scheduled-messages"></a>Mensagens agendadas

Ao usar mensagens proativas para enviar mensagens agendadas aos usuários, verifique se o fuso horário está atualizado para o fuso horário. Isso garante que as mensagens sejam entregues aos usuários no momento relevante. As mensagens de agenda geralmente incluem:

* **Por que o usuário está recebendo a** mensagem : facilitar para os usuários entenderem o motivo pelo qual estão recebendo a mensagem.
* **O que o usuário pode fazer em seguida:** os usuários podem tomar a ação necessária com base no conteúdo da mensagem.

## <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

> [!Note]
> A instalação proativa de aplicativos usando o Graph está atualmente na versão beta.

Mensagens proativas de usuários que anteriormente não instalaram ou interagiram com seu aplicativo. Por exemplo, você deseja usar o [comunicador da](~/samples/app-templates.md#company-communicator) empresa para enviar mensagens para toda a sua organização. Nesse caso, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários. Armazenar em cache os valores necessários `conversationUpdate` do evento que seu aplicativo recebe durante a instalação.

Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na Loja de Aplicativos do Teams.

Consulte [instalar aplicativos para usuários na](/graph/api/userteamwork-post-installedapps) documentação do Graph e instalação proativa de bots e mensagens no Teams com [Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Também há um exemplo [de estrutura do Microsoft .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.

## <a name="samples"></a>Exemplos

O código a seguir mostra um exemplo de código simples que instala proativamente seu aplicativo usando o Graph:

# <a name="c"></a>[C#](#tab/dotnet)

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

Você deve fornecer a ID do usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará o seguinte objeto de resposta:

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-sample"></a>Exemplo de código

A tabela a seguir fornece um exemplo de código simples que incorpora o fluxo básico de conversa em um aplicativo do Teams e como criar um novo thread de conversa em um canal no Teams:

| Exemplo de nome           | Descrição                                                                      | .NET    | Node.js   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Noções básicas de conversa do Teams  | Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens proativas um para um.|[View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|Iniciar novo thread em um canal     | Demonstra a criação de um novo thread em um canal. |[View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

### <a name="additional-code-sample"></a>Exemplo de código adicional

> [!div class="nextstepaction"]
> [Exemplos de código de mensagens proativas do Teams](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Formatar suas mensagens bot](~/bots/how-to/format-your-bot-messages.md)
