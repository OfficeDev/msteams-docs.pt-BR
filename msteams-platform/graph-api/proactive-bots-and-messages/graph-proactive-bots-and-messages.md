---
title: Use Microsoft Graph para autorizar a instalação proativa de bots e mensagens no Teams
description: Este artigo descreve as mensagens proativas no Teams e como implementá-lo. Saiba mais sobre como habilitar a instalação proativa de aplicativos e mensagens usando o exemplo de código.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
ms.openlocfilehash: b7893b425618372085e8ef118beff7c12bd2eb15
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503589"
---
# <a name="send-proactive-installation-messages"></a>Enviar mensagens de instalação proativa 

## <a name="proactive-messaging-in-teams"></a>Mensagens proativas no Teams

Mensagens proativas são iniciadas por bots para iniciar conversas com um usuário. Eles têm muitas finalidades, incluindo enviar mensagens de boas-vindas, realizar pesquisas ou votações e transmitir notificações em toda a organização. As mensagens proativas no Teams podem ser entregues como conversas **ad hoc** ou **baseadas em diálogo**:

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem proativa ad hoc| O bot interjecta uma mensagem sem interromper o fluxo de conversa.|
|Mensagem proativa baseada em diálogo | O bot cria um novo thread de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para o diálogo anterior.|

## <a name="proactive-app-installation-in-teams"></a>Instalação proativa de aplicativos no Teams

Antes que o bot possa enviar mensagens proativamente a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe na qual o usuário é membro. Às vezes, você precisa enviar mensagens proativas aos usuários que não instalaram ou interagiram anteriormente com seu aplicativo. Por exemplo, se você precisar enviar informações importantes para todos em sua organização, poderá usar o Microsoft API do Graph para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

Microsoft Graph [tipo de recurso teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajuda você a gerenciar o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma Microsoft Teams:

|Permissão do aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um aplicativo do Teams leia, instale, atualize e desinstale a si mesmo para qualquer *usuário*, sem antes entrar ou usar.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que um aplicativo Teams leia, instale, atualize e desinstale a si mesmo em qualquer *equipe*, sem antes entrar ou usar.|

Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

* **id**: sua ID Azure Active Directory aplicativo.
* **recurso**: a URL de recurso do aplicativo.

> [!NOTE]
>
> * Seu bot requer permissões delegadas pelo aplicativo e não pelo usuário porque a instalação é para outras pessoas.
>
> * Um administrador de locatários do Azure AD deve [explicamente conceder permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application). Depois que o aplicativo recebe permissões, todos os membros do locatário do Azure AD obtêm as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilitar a instalação proativa de aplicativos e mensagens

> [!IMPORTANT]
> Microsoft Graph só pode instalar aplicativos publicados na loja de aplicativos da sua organização ou na loja do Teams.

### <a name="create-and-publish-your-proactive-messaging-bot-for-teams"></a>Criar e publicar seu bot de mensagens proativo para o Teams

Para começar, você precisa de um [bot para o Teams](../../bots/how-to/create-a-bot-for-teams.md) com recursos de [mensagens proativas](../../concepts/bots/bot-conversations/bots-conv-proactive.md) que esteja na [loja de aplicativos da sua organização](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) ou na [loja do Teams](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).

> [!TIP]
> O modelo de aplicativo [*Communicator da empresa*](../..//samples/app-templates.md#company-communicator) permite mensagens de difusão e é um bom começo para criar seu aplicativo de bot proativo.

### <a name="get-the-teamsappid-for-your-app"></a>Obtenha o `teamsAppId` para seu aplicativo

Você pode recuperar o `teamsAppId` das seguintes maneiras:

* No catálogo de aplicativos da sua organização:

    **Página de referência do Microsoft Graph:** [tipo de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

    Solicitação **HTTP GET**:

    ```http
    GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
    ```

    A solicitação deve retornar um `teamsApp` objeto `id`, que é a ID do aplicativo gerado pelo catálogo do aplicativo. Isso é diferente da ID que você forneceu no manifesto do aplicativo Teams:

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

* Se seu aplicativo já tiver sido carregado ou carregado em sideload para um usuário no escopo pessoal:

    **Página de referência do Microsoft Graph:** [Aplicativos de lista instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    Solicitação **HTTP GET**:

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

* Se seu aplicativo já tiver sido carregado ou carregado em sideload para um canal no escopo da equipe:

    **Página de referência do Microsoft Graph:** [Aplicativos de lista no equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    Solicitação **HTTP GET**:

    ```http
    GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

    > [!TIP]
    > Para restringir a lista de resultados, você pode filtrar qualquer um dos campos do objeto [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true).

### <a name="determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>Determinar se o bot está instalado no momento para um destinatário da mensagem

Você pode determinar se o bot está instalado no momento para um destinatário da mensagem da seguinte maneira:

**Página de referência do Microsoft Graph:** [Aplicativos de lista instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

Solicitação **HTTP GET**:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A solicitação retorna:

* Uma matriz vazia se o aplicativo não estiver instalado.
* Uma matriz com um único objeto [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.

### <a name="install-your-app"></a>Instalar seu aplicativo

Você pode instalar seu aplicativo da seguinte maneira:

**Página de referência do Microsoft Graph:** [Aplicativos instalados para o usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

Solicitação **HTTP POST**:

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver o Microsoft Teams em execução, a instalação do aplicativo ocorrerá imediatamente. Uma reinicialização pode ser necessária para exibir o aplicativo instalado.

### <a name="retrieve-the-conversation-chatid"></a>Recuperar a conversa `chatId`

Quando seu aplicativo é instalado para o usuário, o bot recebe uma `conversationUpdate` [notificação de evento](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) que contém as informações necessárias para enviar a mensagem proativa.

**Página de referência do Microsoft Graph:** [Obter chat](/graph/api/chat-get?view=graph-rest-v1.0&tabs=http&preserve-view=true)

1. Você deve ter o `{teamsAppInstallationId}`. Se você não o tiver, use o seguinte:

    Solicitação **HTTP GET**:

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
    ```

    A propriedade **id** da resposta é `teamsAppInstallationId`.

1. Faça a seguinte solicitação para buscar o `chatId`:

    **Solicitação HTTP GET** (permissão):`TeamsAppInstallation.ReadWriteSelfForUser.All`  

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
    ```

    A propriedade **id** da resposta é `chatId`.

    Você também pode recuperar o `chatId` com a seguinte solicitação, mas requer a permissão `Chat.Read.All` mais ampla:

    **Solicitação HTTP GET** (permissão):`Chat.Read.All`

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
    ```

### <a name="send-proactive-messages"></a>Enviar mensagens proativas

Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot foi adicionado para um usuário ou uma equipe e recebeu todas as informações do usuário.

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de envio de mensagens proativas:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public async Task<int> SendNotificationToAllUsersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
   int msgSentCount = 0;

   // Send notification to all the members
   foreach (var conversationReference in _conversationReferences.Values)
   {
       await turnContext.Adapter.ContinueConversationAsync(_configuration["MicrosoftAppId"], conversationReference, BotCallback, cancellationToken);
       msgSentCount++;
   }

   return msgSentCount;
}

private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
{
   await turnContext.SendActivityAsync("Proactive hello.");
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
server.get('/api/notify', async (req, res) => {
    for (const conversationReference of Object.values(conversationReferences)) {
        await adapter.continueConversationAsync(process.env.MicrosoftAppId, conversationReference, async context => {
            await context.sendActivity('proactive hello');
        });
    }

    res.setHeader('Content-Type', 'text/html');
    res.writeHead(200);
    res.write('<html><body><h1>Proactive messages have been sent.</h1></body></html>');
    res.end();
});
```

---

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** |
|---------------|--------------|--------|-------------|
| Instalação proativa do aplicativo e envio de notificações proativas | Este exemplo mostra como você pode usar a instalação proativa do aplicativo para usuários e enviar notificações proativas chamando as APIs do Microsoft Graph. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) |

## <a name="additional-code-samples"></a>Exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Exemplos de código de mensagens proativas do Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="see-also"></a>Confira também

* [Gerenciar políticas de configuração de aplicativo no Teams](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Enviar notificações proativas aos usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)
* [Enviar notificações do feed de atividades aos usuários no Microsoft Teams](/graph/teams-send-activityfeednotifications)
