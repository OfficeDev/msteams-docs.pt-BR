---
title: Usar o Microsoft Graph para habilitar a instalação proativa de bot e mensagens no Microsoft Teams
description: Descreve as mensagens pró-ativas no Microsoft Teams e como implementar o.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Gráfico de instalação do chat de mensagens pró-ativas do teams
ms.openlocfilehash: b601c5858e5141ce81985dca62968b1713e1d2ba
ms.sourcegitcommit: 9fd61042e8be513c2b2bd8a33ab5e9e6498d65c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46819158"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a>Habilitar instalação de bot proativo e mensagens pró-ativas no Teams com o Microsoft Graph (visualização pública)

>[!IMPORTANT]
> As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários. Embora este lançamento tenha transcorrido testes extensivos, ele não se destina ao uso em produção.

## <a name="proactive-messaging-in-teams"></a>Mensagens pró-ativas no Teams

As mensagens pró-ativas são iniciadas por bots para iniciar conversas com um usuário. Eles atendem a vários propósitos, incluindo o envio de mensagens de boas-vindas, condução de pesquisas ou sondas e transmissão de notificações em toda a organização.  As mensagens pró-ativas no Microsoft Teams podem ser fornecidas como conversas **ad-hoc** ou **baseadas em diálogo** :

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem pró-ativa ad-hoc| O bot interjects uma mensagem sem interromper o fluxo de conversa.|
|Mensagem proativa baseada em caixa de diálogo | O bot cria um novo encadeamento de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.|

*Ver*, [enviar notificações proativas para os usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)

## <a name="proactive-app-installation-in-teams"></a>Instalação de aplicativo proativo no Teams

Antes que o bot possa proativamente mensagens de um usuário, ele precisa ser instalado como um aplicativo pessoal ou em uma equipe onde o usuário é membro. Às vezes, talvez você precise proativamente usuários de mensagens que _não_ tenham sido instaladas ou previamente interagindo com o aplicativo. Por exemplo, a necessidade de mensagens vitais para todas as pessoas em sua organização. Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

As permissões de [tipo de recurso teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) do Microsoft Graph permitem que você gerencie o ciclo de vida de instalação de seu aplicativo para todos os escopos de usuário (pessoal) ou de equipe (canal) na plataforma Microsoft Teams:

|Permissão de aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um aplicativo do teams Leia, instale, atualize e desinstale a si mesmo para qualquer **usuário**, sem entrar ou usar o anterior.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que o aplicativo de equipes Leia, instale, atualize e desinstale em qualquer **equipe**, sem entrar ou usar o anterior.|

Para usar essas permissões, você deve adicionar uma chave de [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **ID**  — sua ID de aplicativo do Azure AD.
> * **recurso** — a URL do recurso para o aplicativo.
>

>[!NOTE]
>
> * Seu bot requer permissões _delegadas do usuário_ do _aplicativo_ , pois a instalação não é para você mesmo, mas para outros.
>
> * Um administrador de locatários do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application). Depois que um aplicativo recebe permissões, _todos_ os membros do locatário do Azure ad obterão as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilitar a instalação e mensagens proativas de aplicativos

 > [!IMPORTANT]
>O Microsoft Graph só instalará aplicativos publicados no catálogo de [aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource](https://appsource.microsoft.com/).

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Criar e publicar seu bot de mensagens pró-ativas para o Microsoft Teams

Para começar, você precisará de um [bot para o Microsoft Teams](../../bots/how-to/create-a-bot-for-teams.md) com recursos [proativos de mensagens](../../concepts/bots/bot-conversations/bots-conv-proactive.md) e  [publicado](../../concepts/deploy-and-publish/overview.md) no [Catálogo de aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource](https://appsource.microsoft.com/).

>[!TIP]
> O modelo de aplicativo do [**Communicator da empresa**](../..//samples/app-templates.md#company-communicator) pronto para produção permite transmissão de mensagens e é uma boa base para criar seu aplicativo de bot proativo.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Obter o `teamsAppId` para seu aplicativo

**1.** você precisará das `teamsAppId`  próximas etapas.

O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:

**Referência de página do Microsoft Graph:** [tipo de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0)

Solicitação **http Get** :

```http
GET https://graph.microsoft.com/beta/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

A solicitação retornará um `teamsApp`  objeto. O objeto retornado `id`  é a ID do aplicativo gerado pelo catálogo do aplicativo e é diferente do "ID:" que você forneceu no manifesto do aplicativo do Microsoft Teams:

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

**2.**  se seu aplicativo já foi carregado/suplementos foi feito para um usuário no escopo pessoal, você pode recuperar o da `teamsAppId` seguinte maneira:

**Referência de página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)

Solicitação **http Get** :

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** se seu aplicativo já tiver sido carregado/suplementos foi feito para um canal no escopo da equipe, você poderá recuperar o da `teamsAppId` seguinte maneira:

**Referência de página do Microsoft Graph:** [listar aplicativos no Team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)

Solicitação **http Get** :

```http
GET https://graph.microsoft.com/beta/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Você pode filtrar em qualquer um dos campos do objeto [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) para restringir a lista de resultados.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Determinar se o seu bot está instalado atualmente para um destinatário de mensagem

**Referência de página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)

Solicitação **http Get** :

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado, ou uma matriz com um único objeto [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) , se tiver sido instalado.

### <a name="-install-your-app"></a>✔ Instalar seu aplicativo

**Referência do Microsoft Graph: instalar o** [aplicativo para o usuário](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)

Solicitação **http post** :

```http
POST https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/beta/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver o Microsoft Teams em execução, ele poderá ver a instalação do aplicativo imediatamente. Como alternativa, pode ser necessário reinicializar para ver o aplicativo instalado.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Recuperar o **chat** de conversa

Quando seu aplicativo for instalado para o usuário, o bot receberá uma `conversationUpdate` [notificação de eventos](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) que conterá as informações necessárias para enviar a mensagem proativa.

O `chatId` também pode ser recuperado da seguinte maneira:

**Referência do Microsoft Graph:** [obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http)

**1.** você precisará do seu aplicativo `{teamsAppInstallationId}` . Se você não o tiver, use o seguinte:

Solicitação **http Get** :

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A propriedade **ID** da resposta é o `teamsAppInstallationId` .

**2.** faça a seguinte solicitação para buscar `chatId` :

Solicitação **http Get** (permissão – `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

A propriedade **ID** da resposta é o `chatId` .

Como alternativa, você pode recuperar o `chatId`  com a solicitação abaixo, mas ele exigirá a permissão mais ampla `Chat.Read.All` :

Solicitação **http Get** (permissão – `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Enviar mensagens pró-ativas

Depois que o bot for adicionado para um usuário ou uma equipe e tiver adquirido as informações necessárias do usuário, ele poderá começar a [enviar mensagens pró-ativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp).

# <a name="c--net"></a>[C#/.NET](#tab/csharp)

O trecho de código a seguir é do [Microsoft bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)

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

O trecho de código a seguir é proveniente dos [exemplos da Microsoft bot Framework para JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).

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

## <a name="related-topic-for-teams-administrators"></a>Tópico relacionado para administradores do teams
>
> [!div class="nextstepaction"]
> [**Gerenciar políticas de configuração de aplicativos no Microsoft Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Exibir exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Amostras de código de mensagens proativas do teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
