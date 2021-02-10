---
title: Usar o Microsoft Graph para habilitar a instalação proativa de bots e mensagens no Teams
description: Descreve as mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do Teams Graph
ms.openlocfilehash: 4f26b4d2f4e82fcf50b7a35c46bcd07e5afecf19
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162891"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a>Habilitar a instalação proativa de bots e mensagens proativas no Teams com o Microsoft Graph (Visualização Pública)

>[!IMPORTANT]
> As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários. Embora esta versão tenha passado por testes extensos, ela não foi destinada ao uso na produção.

## <a name="proactive-messaging-in-teams"></a>Mensagens proativas no Teams

As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário. Eles atendem a muitos propósitos, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou votações e a transmissão de notificações em toda a organização.  As mensagens proativas no Teams podem ser entregues como conversas **ad hoc** ou **baseadas em diálogo:**

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem proativa ad hoc| O bot intercala uma mensagem sem interromper o fluxo da conversa.|
|Mensagem proativa baseada em caixa de diálogo | O bot cria um novo thread de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.|

*Ver*, [Enviar notificações proativas para os usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="proactive-app-installation-in-teams"></a>Instalação proativa de aplicativos no Teams

Para que seu bot possa enviar mensagens proativamente a um usuário, ele precisa ser instalado como um aplicativo pessoal ou em uma equipe na qual o usuário é membro. Às vezes, talvez seja necessário enviar mensagens proativas aos usuários que não _tenham_ instalado ou interagido anteriormente com seu aplicativo. Por exemplo, a necessidade de enviar informações vitais para todos em sua organização. Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

As permissões de tipo de recurso [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) do Microsoft Graph permitem que você gerencie o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma do Microsoft Teams:

|Permissão de aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um aplicativo do Teams leia, instale, atualize e se desinstale para qualquer **usuário,** sem antes entrar ou usar.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que um aplicativo do Teams leia, instale, atualize e se desinstale em qualquer **equipe,** sem antes entrar ou usar.|

Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id**  — sua ID de aplicativo do Azure AD.
> * **resource** — a URL do recurso para o aplicativo.
>

>[!NOTE]
>
> * Seu bot requer _permissões delegadas_ _pelo usuário e não_ pelo aplicativo porque a instalação não é para você, mas para outras pessoas.
>
> * Um administrador de locatários do Azure AD [deve conceder permissões explicitamente a um aplicativo.](/graph/security-authorization#grant-permissions-to-an-application) Depois que um aplicativo recebe _permissões,_ todos os membros do locatário do Azure AD receberão as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilitar a instalação proativa de aplicativos e mensagens

 > [!IMPORTANT]
>O Microsoft Graph só instalará aplicativos publicados no catálogo de [aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource.](https://appsource.microsoft.com/)

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ criar e publicar seu bot de mensagens proativo para o Teams

Para começar, você precisará de um [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) bot para [](../../concepts/deploy-and-publish/overview.md) o [Teams](../../bots/how-to/create-a-bot-for-teams.md) com [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) recursos proativos de mensagens e publicado no catálogo de aplicativos da sua organização ou no [AppSource.](https://appsource.microsoft.com/)

>[!TIP]
> O modelo de aplicativo [**Communicator da empresa pronto**](../..//samples/app-templates.md#company-communicator) para produção permite a transmissão de mensagens e é uma boa base para criar seu aplicativo de bot proativo.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ obter o `teamsAppId` para seu aplicativo

**1.** Você precisará das `teamsAppId`  próximas etapas.

Ele `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:

**Referência de página do Microsoft Graph: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**Solicitação HTTP GET:**

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

A solicitação retornará um `teamsApp`  objeto. O objeto retornado é a ID de aplicativo gerada pelo catálogo do aplicativo e é diferente da "id:" que você forneceu no manifesto do `id`  aplicativo do Teams:

```json
{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "name": "Test App",
      "version": "1.0.1",
      "distributionMethod": "Organization"
    }
  ]
}
```

**2.**  Se o aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal, você poderá recuperar `teamsAppId` o seguinte:

**Referência da página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP GET:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Se seu aplicativo já tiver sido carregado/sideload para um canal no escopo da equipe, você poderá recuperar `teamsAppId` o seguinte:

**Referência da página do Microsoft Graph: Listar** [aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP GET:**

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Você pode filtrar qualquer um dos campos do objeto [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) para restringir a lista de resultados.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Determinar se o bot está instalado no momento para um destinatário da mensagem

**Referência da página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP GET:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado ou uma matriz com um único objeto [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se ele tiver sido instalado.

### <a name="-install-your-app"></a>✔ instalar seu aplicativo

**Referência da página do Microsoft Graph:** [Instalar aplicativo para o usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP POST:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver o Microsoft Teams em execução, ele poderá ver o aplicativo ser instalado imediatamente. Como alternativa, uma reinicialização pode ser necessária para ver o aplicativo instalado.

### <a name="-retrieve-the-conversation-chatid"></a>✔ recuperar o **chatId de conversa**

Quando seu aplicativo for instalado para o usuário, o bot receberá uma notificação de evento que conterá as informações necessárias para enviar a `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) mensagem proativa.

O `chatId` também pode ser recuperado da seguinte forma:

**Referência da página do Microsoft Graph:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Você precisará do seu `{teamsAppInstallationId}` aplicativo. Se você não o tiver, use o seguinte:

**Solicitação HTTP GET:**

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A **propriedade de id** da resposta é o `teamsAppInstallationId` .

**2.** Faça a solicitação a seguir para buscar `chatId` o:

**Solicitação HTTP GET** (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

A **propriedade de id** da resposta é o `chatId` .

Como alternativa, você pode recuperar o `chatId`  com a solicitação abaixo, mas ela exigirá a permissão `Chat.Read.All` mais ampla:

**Solicitação HTTP GET** (permissão `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ enviar mensagens proativas

Depois que seu bot tiver sido adicionado a um usuário ou equipe e tiver adquirido as informações de usuário necessárias, ele poderá começar a [enviar mensagens proativas.](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

# <a name="c--net"></a>[C# / .NET](#tab/csharp)

O trecho de código a seguir é dos [Exemplos do Microsoft Bot Framework para C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)

```csharp
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.Bot.Builder;
using Microsoft.Bot.Schema;

namespace Microsoft.BotBuilderSamples
{
    public class ProactiveBot : ActivityHandler
    {
        // Message to send to users when the bot receives a Conversation Update event
        private const string WelcomeMessage = "Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.";

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

        public ProactiveBot(ConcurrentDictionary<string, ConversationReference> conversationReferences)
        {
            _conversationReferences = conversationReferences;
        }

        private void AddConversationReference(Activity activity)
        {
            var conversationReference = activity.GetConversationReference();
            _conversationReferences.AddOrUpdate(conversationReference.User.Id, conversationReference, (key, newValue) => conversationReference);
        }

        protected override Task OnConversationUpdateActivityAsync(ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            return base.OnConversationUpdateActivityAsync(turnContext, cancellationToken);
        }

        protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            foreach (var member in membersAdded)
            {
                // Greet anyone that was not the target (recipient) of this message.
                if (member.Id != turnContext.Activity.Recipient.Id)
                {
                    await turnContext.SendActivityAsync(MessageFactory.Text(WelcomeMessage), cancellationToken);
                }
            }
        }

        protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            // Echo back what the user said
            await turnContext.SendActivityAsync(MessageFactory.Text($"You sent '{turnContext.Activity.Text}'"), cancellationToken);
        }
    }
}
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

O trecho de código a seguir é dos Exemplos da [Estrutura de Bot da Microsoft para JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).

```javascript
const { ActivityHandler, TurnContext } = require('botbuilder');

class ProactiveBot extends ActivityHandler {
    constructor(conversationReferences) {
        super();

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        this.conversationReferences = conversationReferences;

        this.onConversationUpdate(async (context, next) => {
            this.addConversationReference(context.activity);

            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (let cnt = 0; cnt < membersAdded.length; cnt++) {
                if (membersAdded[cnt].id !== context.activity.recipient.id) {
                    const welcomeMessage = 'Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.';
                    await context.sendActivity(welcomeMessage);
                }
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });

        this.onMessage(async (context, next) => {
            this.addConversationReference(context.activity);

            // Echo back what the user said
            await context.sendActivity(`You sent '${ context.activity.text }'`);
            await next();
        });
    }

    addConversationReference(activity) {
        const conversationReference = TurnContext.getConversationReference(activity);
        this.conversationReferences[conversationReference.conversation.id] = conversationReference;
    }
}

module.exports.ProactiveBot = ProactiveBot;

```
---

## <a name="related-topic-for-teams-administrators"></a>Tópico relacionado para administradores do Teams
>
> [!div class="nextstepaction"]
> [**Gerenciar políticas de configuração de aplicativo no Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Exibir exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Exemplos proativos de código de mensagens do Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
