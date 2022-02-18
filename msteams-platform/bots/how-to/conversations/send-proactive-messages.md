---
title: Enviar mensagens proativas
description: Descreve como enviar mensagens proativas com o bot do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: high
Keywords: Enviar mensagem, obter ID do usuário, obter ID do canal, obter ID da conversa
ms.openlocfilehash: 15d564af900e0b13024d051ef4711025c4b16060
ms.sourcegitcommit: fb10a8b14acdba5cc48d2b31dec6f8e6d4ad99ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62896324"
---
# <a name="proactive-messages"></a>Mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Isso inclui mensagens, como:

* Mensagem de boas-vindas
* Notificações
* Mensagens agendadas

Para que seu bot envie uma mensagem proativa a um usuário, chat em grupo ou equipe, ele precisa ter acesso para enviar a mensagem. O aplicativo que contém seu bot deve ser instalado primeiro onde houver um chat em grupo ou equipe. Você pode [instalar seu aplicativo de forma proativa usando o Microsoft Graph](#proactively-install-your-app-using-graph) em uma equipe, se necessário, ou usar uma [política de aplicativo](/microsoftteams/teams-custom-app-policies-and-settings) para enviar aplicativos para equipes e usuários em seu locatário. Se for um usuário, você deve ter o aplicativo instalado ou ser um membro da equipe na qual o aplicativo está instalado.

Enviar uma mensagem proativa é diferente de enviar uma mensagem normal. Não há nenhum ativo `turnContext` a ser usado como resposta. Você deve criar a conversa antes de enviar a mensagem. Por exemplo, um novo chat individual ou um novo tópico de conversa em um canal. Não é possível criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.

**Para enviar uma mensagem proativa**

1. [Obtenha a ID do usuário, ID da equipe ou ID do canal](#get-the-user-id-team-id-or-channel-id), se necessário.
1. [Crie a conversa](#create-the-conversation), se necessário.
1. [Obtenha a ID da conversa](#get-the-conversation-id).
1. [Envie a mensagem](#send-the-message).

Os trechos de código na seção [exemplos](#samples) são para criar uma conversa individual. Para obter links para concluir exemplos de trabalho de conversas individuais e grupos ou canais, confira o [exemplo de código](#code-sample).

Para usar mensagens proativas efetivamente, confira [práticas recomendadas para mensagens proativas](#best-practices-for-proactive-messaging). Para determinados cenários, você deve [instalar proativamente seu aplicativo usando o Graph](#proactively-install-your-app-using-graph). Os trechos de código na seção [exemplos](#samples) são para criar uma conversa individual. Para obter exemplos de trabalho completos de conversas individuais e grupos ou canais, confira o [exemplo de código](#code-sample).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Obter a ID de usuário, ID da equipe ou ID do canal

É necessário ter a ID correta para criar uma nova conversa ou tópico de conversa em um canal. Você pode receber ou recuperar essa ID das seguintes formas:

* Quando seu aplicativo é instalado em qualquer contexto específico, você recebe uma [atividade `onMembersAdded`](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você recebe uma [atividade `onMembersAdded`](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe onde seu aplicativo está instalado.
* Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe onde seu aplicativo está instalado.
* Todas as atividades que seu bot recebe devem conter as informações necessárias.

Independentemente de como você obter as informações, é necessário armazenar a `tenantId` e a `userId` ou a `channelId` para criar uma nova conversa. Você também pode usar a `teamId` para criar um novo tópico de conversa no canal geral ou padrão de uma equipe.

A `userId` é exclusiva da ID do bot e de um usuário específico. Não é possível reutilizar a `userId` entre bots. O `channelId` é global. No entanto, seu bot deve ser instalado na equipe antes de poder enviar uma mensagem proativa para um canal.

Depois de ter as informações do usuário ou do canal, você deve criar a conversa.

## <a name="create-the-conversation"></a>Criar a conversa

Você deve criar a conversa se ela não existir ou se não souber a `conversationId`. Você só deve criar a conversa uma vez e armazenar o valor `conversationId` ou o objeto `conversationReference`.

Após a criação da conversa, é necessário obter a ID da conversa.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Use o objeto `conversationReference` ou a `conversationId` e `tenantId` para enviar a mensagem. É possível obter essa ID criando a conversa ou armazenando-a de qualquer atividade enviada a você desse contexto. Armazene essa ID para referência.

Depois de obter as informações de endereço apropriadas, é possível enviar sua mensagem.

## <a name="send-the-message"></a>Enviar a mensagem

Agora que você tem as informações de endereço corretas, pode enviar sua mensagem. Se estiver usando o SDK, deverá usar o método `continueConversation` e a `conversationId` e `tenantId` para fazer uma chamada direta à API. Você deve definir os `conversationParameters` corretamente para enviar sua mensagem com êxito. Confira a seção [exemplos](#samples) ou use um dos exemplos listados na seção [exemplo de código](#code-sample).

Depois de enviada a mensagem proativa, você deverá seguir essas práticas recomendadas ao enviar mensagens proativas para obter uma melhor troca de informações entre os usuários e o bot.

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira eficaz de se comunicar com seus usuários. No entanto, da perspectiva do usuário, a mensagem aparece espontaneamente. Se houver uma mensagem de boas-vindas, será a primeira vez que eles interagirão com seu aplicativo. É importante usar essa funcionalidade e fornecer as informações completas ao usuário para entender a finalidade dessa mensagem.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Quando as mensagens proativas são usadas para enviar uma mensagem de boas-vindas a um usuário, não precisa haver contexto para os usuários receberem essa mensagem. Essa também é a primeira vez que os usuários interagem com seu aplicativo. É uma oportunidade de criar uma boa primeira impressão. As mensagens de boas-vindas ideais devem incluir:

* Por que um usuário recebe a mensagem: deve ser muito claro para o usuário o motivo pelo qual ele recebe a mensagem. Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e quem o instalou.
* O que você oferece: os usuários devem identificar o que podem fazer com seu aplicativo e qual valor você pode agregar a eles.
* O que eles devem fazer a seguir: convidar os usuários para tentar um comando ou interagir com seu aplicativo.
Mensagens de boas-vindas ruins podem levar os usuários a bloquear seu bot. Escreva até o ponto e limpe as mensagens de boas-vindas. Iterar nas mensagens de boas-vindas se elas não estão tendo o efeito desejado.

### <a name="notification-messages"></a>Mensagens de notificação

Para enviar notificações usando mensagens proativas, verifique se os usuários têm um caminho claro para executar ações comuns com base em sua notificação. Verifique se os usuários têm uma compreensão clara do motivo pelo qual receberam uma notificação. As mensagens de notificação consideradas boas geralmente incluem o seguinte:

* O que aconteceu: uma indicação clara do que aconteceu para gerar a notificação.
* Qual foi o resultado: ele deve estar claro, qual item é atualizado para receber a notificação.
* Quem ou o que a disparou: quem ou o que executou uma ação que fez com que a notificação fosse enviada.
* O que os usuários podem fazer em resposta: facilitar a ação dos usuários com base em suas notificações.
* Como os usuários podem recusar: você deve fornecer um caminho para os usuários recusarem notificações adicionais.

Para enviar mensagens para um grande grupo de usuários, por exemplo, para sua organização, instale proativamente seu aplicativo usando o Graph.

### <a name="scheduled-messages"></a>Mensagens agendadas

Ao usar mensagens proativas para enviar mensagens agendadas aos usuários, verifique se o fuso horário está atualizado com o fuso horário deles. Isso garante que as mensagens sejam entregues aos usuários no momento relevante. As mensagens agendadas geralmente incluem:

* Por que o usuário recebe a mensagem: facilitar aos usuários entenderem o motivo pelo qual eles recebem a mensagem.
* O que o usuário pode fazer a seguir: os usuários podem executar a ação necessária com base no conteúdo da mensagem.

## <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

Envie mensagens proativas a usuários que anteriormente não instalaram ou interagiram com seu aplicativo. Por exemplo, você deseja usar o [comunicador da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a organização. Nesse caso, você pode usar a API do Graph para instalar proativamente seu aplicativo aos usuários. Armazene em cache os valores necessários do evento `conversationUpdate` que seu aplicativo recebe após a instalação.

Você só pode instalar aplicativos que estão em no catálogo de aplicativos da sua organização ou na Loja de aplicativos do Teams.

Confira [instalar aplicativos para usuários](/graph/api/userteamwork-post-installedapps) na documentação do Graph e [instalação proativa de bot e mensagens no Teams com o Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Também há um [exemplo de estrutura do Microsoft .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.

## <a name="samples"></a>Exemplos

O código a seguir mostra como enviar mensagens proativas:

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

É preciso fornecer a ID do usuário e a ID do locatário. Se a chamada for bem-sucedida, a API retornará o seguinte objeto de resposta:

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-sample"></a>Exemplo de código

A tabela a seguir fornece um exemplo de código simples que incorpora o fluxo básico de conversa em um aplicativo do Teams e como criar um novo tópico de conversa em um canal do Teams:

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Noções básicas de conversa do Teams  | Demonstra as noções básicas de conversas no Teams, incluindo o envio de mensagens individuais proativas.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Iniciar novo tópico em um canal | Demonstra a criação de um novo tópico em um canal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |
| Instalação proativa do aplicativo e envio de notificações proativas | Este exemplo mostra como você pode usar a instalação proativa do aplicativo para usuários e enviar notificações proativas chamando as APIs do Microsoft Graph. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) | |

### <a name="additional-code-sample"></a>Exemplo de código adicional

> [!div class="nextstepaction"]
> [Exemplos de código de mensagens proativas do Teams](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../../sbs-send-proactive.yml), que ajuda você a enviar uma mensagem proativa de um bot.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Formatar suas mensagens de bot](~/bots/how-to/format-your-bot-messages.md)

## <a name="see-also"></a>Confira também

* [**Exemplos de código de mensagens proativas do Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
* [Canais e conversas de chat em grupo com um bot do Microsoft Teams](~/bots/how-to/conversations/channel-and-group-conversations.md)
* [Responder à ação de envio do módulo de tarefas](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
