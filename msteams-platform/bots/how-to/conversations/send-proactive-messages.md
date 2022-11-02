---
title: Enviar mensagens proativas
description: Saiba como enviar mensagens proativas com seu bot do Teams, instalar seu aplicativo usando o Microsoft Graph e verificar exemplos de código com base no SDK do Bot Framework v4.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 7e50719e9befd807127a1eae4022b4af67a9fc00
ms.sourcegitcommit: d58f670fed6ff217c52d2e00c0bee441fcb96920
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819680"
---
# <a name="proactive-messages"></a>Mensagens proativas

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Esta mensagem pode incluir conteúdo, como:

* Mensagem de boas-vindas
* Notificações
* Mensagens agendadas

> [!IMPORTANT]
>
> * Para enviar uma mensagem proativa, é recomendável começar com o [bot de notificação de criação com JavaScript](../../../sbs-gs-notificationbot.yml) ou [exemplo de notificação de webhook de entrada](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/incoming-webhook-notification). Para começar, baixe a exploração [do Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) . Para obter mais informações, consulte [Documentos do Teams Toolkit](../../../toolkit/teams-toolkit-fundamentals.md).
>
> * Atualmente, os bots estão disponíveis na Nuvem da Comunidade Governamental (GCC) e no GCC-High, mas não no Departamento de Defesa (DOD). Para mensagens proativas, os bots devem usar os seguintes pontos de extremidade para ambientes de nuvem governamentais: <br> -GCC: `https://smba.infra.gcc.teams.microsoft.com/gcc`<br> - GCCH: `https://smba.infra.gov.teams.microsoft.us/gcch`

Para enviar uma mensagem proativa para um usuário, um chat em grupo ou uma equipe, seu bot deve ter o acesso necessário para enviar a mensagem. O aplicativo que contém seu bot deve ser instalado primeiro onde houver um chat em grupo ou equipe.

Você pode [instalar proativamente seu aplicativo usando o Microsoft Graph](#proactively-install-your-app-using-graph) em uma equipe, se necessário, ou usar uma [política de aplicativo personalizada](/microsoftteams/teams-custom-app-policies-and-settings) para instalar um aplicativo em suas equipes e para usuários da organização. Para determinados cenários, você deve [instalar proativamente seu aplicativo usando o Graph](#proactively-install-your-app-using-graph). Para que um usuário receba mensagens proativas, instale o aplicativo para o usuário ou faça do usuário uma parte de uma equipe na qual o aplicativo está instalado.

Enviar uma mensagem proativa é diferente de enviar uma mensagem normal. Não há nenhum ativo `turnContext` a ser usado como resposta. Você deve criar a conversa antes de enviar a mensagem. Por exemplo, um novo chat individual ou um novo tópico de conversa em um canal. Não é possível criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.

Para enviar uma mensagem proativa, siga estas etapas:

1. [Obtenha a ID do usuário, ID da equipe ou ID do canal ](#get-the-user-id-team-id-or-channel-id), se necessário.
1. [Crie a conversa](#create-the-conversation), se necessário.
1. [Obtenha a ID da conversa](#get-the-conversation-id).
1. [Envie a mensagem](#send-the-message).

Os snippets de código na seção [exemplos](#samples) são para criar uma conversa individual. Para obter links para exemplos para conversas um a um e mensagens de grupo ou canais, consulte [exemplo de código](#code-sample). Para usar mensagens proativas de forma eficaz, consulte [as melhores práticas para mensagens proativas](#best-practices-for-proactive-messaging).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Obter a ID de usuário, ID da equipe ou ID do canal

Você pode criar uma nova conversa com um usuário ou um thread de conversa em um canal e deve ter a ID correta. Você pode receber ou recuperar essa ID usando qualquer uma das seguintes maneiras:

* Quando seu aplicativo é instalado em um contexto específico, você recebe uma [`onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você recebe uma [atividade `onMembersAdded`](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Cada evento que o bot recebe contém as informações necessárias, que você pode obter do contexto do bot (objeto TurnContext).
* Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe onde seu aplicativo está instalado.
* Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe onde seu aplicativo está instalado.

Independentemente de como você obtém as informações, armazene o `tenantId` e ou `userId` `channelId` para criar uma nova conversa. Você também pode usar a `teamId` para criar um novo tópico de conversa no canal geral ou padrão de uma equipe.

A `userId` é exclusiva da ID do bot e de um usuário específico. Não é possível reutilizar a `userId` entre bots. O `channelId` é global. No entanto, instale o bot na equipe antes de enviar uma mensagem proativa para um canal.

Crie a conversa, depois de ter as informações do usuário ou do canal.

## <a name="create-the-conversation"></a>Criar a conversa

Você pode criar a conversa se ela não existir ou não conhecer o `conversationId`. Crie a conversa apenas uma vez e armazene o valor ou `conversationReference` o `conversationId` objeto.

Para criar a conversa, você precisa de um `userId`, `tenantId`e `serviceUrl`.

Para `serviceUrl`, use o valor de uma atividade de entrada disparando o fluxo ou uma das URLs de serviço globais. Se o `serviceUrl` não estiver disponível de uma atividade de entrada que dispara o cenário proativo, use os seguintes pontos de extremidade de URL globais:

* Público: `https://smba.trafficmanager.net/teams/`
* GCC: `https://smba.infra.gcc.teams.microsoft.com/gcc`
* GCCH: `https://smba.infra.gov.teams.microsoft.us/gcch`

Para obter um exemplo de código, consulte a chamada `CreateConversationAsync` no [**exemplo**](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/57.teams-conversation-bot/Bots/TeamsConversationBot.cs).

Você pode obter a conversa quando o aplicativo é instalado pela primeira vez. Depois que a conversa for criada, [obtenha a ID da conversa](#get-the-conversation-id). O `conversationId` está disponível nos eventos de atualização da conversa.

Se você não tiver o `conversationId`, poderá [instalar proativamente seu aplicativo usando o Graph](#proactively-install-your-app-using-graph) para obter o `conversationId`.

## <a name="get-the-conversation-id"></a>Obter a ID da conversa

Use o objeto `conversationReference` ou a `conversationId` e `tenantId` para enviar a mensagem. É possível obter essa ID criando a conversa ou armazenando-a de qualquer atividade enviada a você desse contexto. Armazene essa ID para referência.

Depois de obter as informações de endereço apropriadas, é possível enviar sua mensagem.

## <a name="send-the-message"></a>Enviar a mensagem

Agora que você tem as informações de endereço corretas, pode enviar sua mensagem. Se estiver usando o SDK, deverá usar o método `continueConversation` e a `conversationId` e `tenantId` para fazer uma chamada direta à API. Para enviar sua mensagem, defina o `conversationParameters`. Confira a seção [exemplos](#samples) ou use um dos exemplos listados na seção [exemplo de código](#code-sample).

> [!NOTE]
> O Teams não dá suporte ao envio de mensagens proativas usando o email ou o Nome da Entidade de Usuário (UPN).

Depois de enviada a mensagem proativa, você deverá seguir essas práticas recomendadas ao enviar mensagens proativas para obter uma melhor troca de informações entre os usuários e o bot.

Confira o vídeo a seguir para saber como enviar mensagens proativas de bots:

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHyk]
<br>

### <a name="understand-who-blocked-muted-or-uninstalled-a-bot"></a>Entender quem bloqueou, silenciou ou desinstalou um bot

Como desenvolvedor, você pode criar um relatório para entender quais usuários da sua organização bloquearam, silenciaram ou desinstalaram um bot. Essas informações podem ajudar os administradores da sua organização a transmitir mensagens em toda a organização ou impulsionar o uso do aplicativo.

Usando o Teams, você pode enviar uma mensagem proativa ao bot para verificar se um usuário bloqueou ou desinstalou um bot. Se o bot estiver bloqueado ou desinstalado, o Teams retornará um código de `403` resposta com um `subCode: MessageWritesBlocked`. Essa resposta indica que a mensagem enviada pelo bot não é entregue ao usuário.

O código de resposta é enviado por usuário e inclui a identidade do usuário. Você pode compilar os códigos de resposta para cada usuário ao lado de sua identidade para criar um relatório de todos os usuários que bloquearam o bot.

Um exemplo de um código de resposta 403 está abaixo.

```http

HTTP/1.1 403 Forbidden

Cache-Control: no-store, must-revalidate, no-cache

 Pragma: no-cache

 Content-Length: 196

 Content-Type: application/json; charset=utf-8

 Server: Microsoft-HTTPAPI/2.0

 Strict-Transport-Security: max-age=31536000; includeSubDomains

 MS-CV: NXZpLk030UGsuHjPdwyhLw.5.0

 ContextId: tcid=0,server=msgapi-canary-eus2-0,cv=NXZpLk030UGsuHjPdwyhLw.5.0

 Date: Tue, 29 Mar 2022 17:34:33 GMT

{"errorCode":209,"message":"{\r\n  \"subCode\": \"MessageWritesBlocked\",\r\n  \"details\": \"Thread is blocked from message writes.\",\r\n  \"errorCode\": null,\r\n  \"errorSubCode\": null\r\n}"}
```

## <a name="best-practices-for-proactive-messaging"></a>Práticas recomendadas para mensagens proativas

Enviar mensagens proativas aos usuários é uma maneira eficaz de se comunicar com seus usuários. No entanto, da perspectiva do usuário, a mensagem aparece espontaneamente. Se houver uma mensagem de boas-vindas, será a primeira vez que eles interagirão com seu aplicativo. É importante usar essa funcionalidade e fornecer as informações completas ao usuário para entender a finalidade dessa mensagem.

### <a name="welcome-messages"></a>Mensagem de boas-vindas

Quando as mensagens proativas são usadas para enviar uma mensagem de boas-vindas a um usuário, não há contexto para o motivo pelo qual o usuário recebe a mensagem. Além disso, essa é a primeira interação do usuário com seu aplicativo. É uma oportunidade para criar uma boa primeira impressão. Uma boa experiência do usuário garante uma melhor adoção do aplicativo. Mensagens de boas-vindas ruins podem levar os usuários a bloquear seu aplicativo. Escreva uma mensagem de boas-vindas clara e itere na mensagem de boas-vindas se ela não estiver tendo o efeito desejado.

Uma boa mensagem de boas-vindas pode incluir o seguinte:

* Motivo da mensagem – deve ficar claro para o usuário por que ele está recebendo a mensagem. Se seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas para todos os usuários, informe a eles em qual canal ele foi instalado e quem o instalou.

* Sua oferta – os usuários devem ser capazes de identificar o que podem fazer com seu aplicativo e qual valor você pode trazer para eles.

* Próximas etapas – os usuários devem entender as próximas etapas. Por exemplo, convide os usuários para experimentar um comando ou interagir com seu aplicativo.

### <a name="notification-messages"></a>Mensagens de notificação

Para enviar notificações usando mensagens proativas, verifique se os usuários têm um caminho claro para executar ações comuns com base em sua notificação. Verifique se os usuários têm uma compreensão clara do motivo pelo qual receberam uma notificação. As boas mensagens de notificação geralmente incluem os seguintes itens:

* O que está acontecendo? Uma indicação clara do que aconteceu para causar a notificação.

* Qual foi o resultado? Deve ser claro, qual item está atualizado para receber a notificação.

* Quem ou o que a disparou? Quem ou o que tomou medidas, o que fez com que a notificação fosse enviada.

* O que os usuários podem fazer em resposta? Facilite para que seus usuários realizem ações com base nas suas notificações.

* Como os usuários podem optar por sair? Você deve fornecer um caminho para que os usuários optem por não receber mais notificações.

Para enviar mensagens para um grande grupo de usuários, por exemplo, para sua organização, instale proativamente seu aplicativo usando o Graph.

### <a name="scheduled-messages"></a>Mensagens agendadas

Ao usar mensagens proativas para enviar mensagens agendadas aos usuários, verifique se o fuso horário está atualizado com o fuso horário deles. Isso garante que as mensagens sejam entregues aos usuários no momento relevante. As mensagens agendadas geralmente incluem:

* Por que o usuário está recebendo a mensagem? Facilite para que seus usuários entendam o motivo pelo qual estão recebendo a mensagem.

* O que o usuário pode fazer a seguir? Os usuários podem executar as ações necessárias com base no conteúdo da mensagem.

## <a name="proactively-install-your-app-using-graph"></a>Instalar proativamente seu aplicativo usando o Graph

Envie mensagens proativas a usuários que anteriormente não instalaram ou interagiram com seu aplicativo. Por exemplo, você deseja usar o [comunicador da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a organização. Nesse caso, você pode usar a API do Graph para instalar proativamente seu aplicativo aos usuários. Armazene em cache os valores necessários do evento `conversationUpdate` que seu aplicativo recebe após a instalação.

Você só pode instalar aplicativos que estão em no catálogo de aplicativos da sua organização ou na Loja de aplicativos do Teams.

Confira [instalar aplicativos para usuários](/graph/api/userteamwork-post-installedapps) na documentação do Graph e [instalação proativa de bot e mensagens no Teams com o Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Também há um [exemplo de framework do Microsoft .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.

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
        foreach (var conversationReference in _conversationReferences.Values) // Loop of all conversation references must be updated to get it from backend system.
        {
            var newReference = new ConversationReference()
        {
            Bot = new ChannelAccount()
            {
                Id = conversationReference.Bot.Id
            },
            Conversation = new ConversationAccount()
            {
                Id = conversationReference.Conversation.Id
            },
            ServiceUrl = conversationReference.ServiceUrl,
        };
            await ((BotAdapter)_adapter).ContinueConversationAsync(_appId, newReference, BotCallback, default(CancellationToken));
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

A tabela a seguir fornece um exemplo de código simples que incorpora o fluxo básico de conversação em um aplicativo do Teams e como criar um novo thread de conversa em um canal no Teams:

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Noções básicas de conversa do Teams  | Demonstra as noções básicas de conversas no Teams, incluindo o envio de mensagens individuais proativas.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Iniciar novo tópico em um canal | Demonstra a criação de um novo tópico em um canal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |
| Instalação proativa do aplicativo e envio de notificações proativas | Este exemplo mostra como você pode usar a instalação proativa do aplicativo para usuários e enviar notificações proativas chamando as APIs do Microsoft Graph. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) | NA |
| Mensagens proativas | Este é um exemplo que mostra como salvar as informações de referência de conversa do usuário para enviar mensagens de lembrete proativas usando Bots. | NA | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging-teamsfx) | NA |

> [!div class="nextstepaction"]
> [Mais exemplo de código de mensagens proativas](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Formatar suas mensagens de bot](~/bots/how-to/format-your-bot-messages.md)

## <a name="see-also"></a>Confira também

* [**Exemplos de código de mensagens proativas do Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
* [Canais e conversas de chat em grupo com um bot do Microsoft Teams](~/bots/how-to/conversations/channel-and-group-conversations.md)
* [Responder à ação de envio do módulo de tarefas](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
* [Enviar notificações proativas aos usuários](/azure/bot-service/bot-builder-howto-proactive-message)
* [Crie seu primeiro aplicativo de bot usando JavaScript](../../../sbs-gs-bot.yml)
* [Criar bot de notificação com JavaScript para enviar uma mensagem proativa](../../../sbs-gs-notificationbot.yml)
* [TurnContext](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest"&preserve-view=true")
