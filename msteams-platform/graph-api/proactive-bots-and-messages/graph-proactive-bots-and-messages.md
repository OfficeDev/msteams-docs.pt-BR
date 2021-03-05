---
title: Usar o Microsoft Graph para autorizar a instalação proativa de bots e mensagens no Teams
description: Descreve mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do teams Graph
ms.openlocfilehash: ac59f3408096993379cae490cd555d3b913cc827
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449399"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a>Instalação proativa de aplicativos usando a API do Graph e enviar mensagens

>[!IMPORTANT]
> As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários. Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.

## <a name="proactive-messaging-in-teams"></a>Mensagens proativas no Teams

As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário. Eles servem a muitas finalidades, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou sondagens e a transmissão de notificações em toda a organização. As mensagens proativas no Teams podem ser entregues como conversas **ad hoc** ou **baseadas em** diálogo:

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem proativa ad hoc| O bot interjectes uma mensagem sem interromper o fluxo de conversa.|
|Mensagem proativa baseada em caixa de diálogo | O bot cria um novo thread de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.|

Consulte Enviar [notificações proativas para usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).

## <a name="proactive-app-installation-in-teams"></a>Instalação proativa de aplicativos no Teams

Antes que o bot possa enviar mensagens proativas a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe em que o usuário seja membro. Às vezes, você precisa enviar mensagens proativas aos usuários que não tenham instalado ou interagido anteriormente com seu aplicativo. Por exemplo, a necessidade de enviar informações vitais para todos em sua organização. Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

Microsoft Graph [teamsAppInstallation Resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:

|Permissão de aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um aplicativo do Teams leia, instale, atualize e desinstale a si mesmo para qualquer usuário **,** sem entrar ou usar previamente.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que um aplicativo do Teams leia, instale, atualize e desinstale a si mesmo em qualquer equipe **,** sem entrar ou usar previamente.|

Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id** — sua ID do aplicativo do Azure AD.
> * **resource** — a URL de recurso do aplicativo.
>
>[!NOTE]
>
> * Seu bot requer permissões de aplicativo e não delegadas pelo usuário, pois a instalação é para outras pessoas.
>
> * Um administrador de locatário do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application). Depois que um aplicativo recebe permissões, todos os membros do locatário do Azure AD ganham as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilitar a instalação proativa de aplicativos e mensagens

 > [!IMPORTANT]
>O Microsoft Graph só pode instalar [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) aplicativos publicados no catálogo de aplicativos da sua organização ou [no AppSource](https://appsource.microsoft.com/).

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ criar e publicar seu bot de mensagens proativa para o Teams

Para começar, você precisa de [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) um bot para [](../../concepts/deploy-and-publish/overview.md) o [Teams](../../bots/how-to/create-a-bot-for-teams.md) com [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) recursos de mensagens proativos publicados no catálogo de aplicativos da sua organização ou no [AppSource](https://appsource.microsoft.com/).

>[!TIP]
> O modelo de aplicativo company pronto para [**Communicator**](../..//samples/app-templates.md#company-communicator) de produção permite mensagens de transmissão e é uma boa base para criar seu aplicativo de bot proativo.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Obter o `teamsAppId` para seu aplicativo

**1.** Você precisa do `teamsAppId` para as próximas etapas.

O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:

**Referência de página do Microsoft Graph: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

A solicitação deve retornar um `teamsApp` objeto. O objeto retornado é a ID de aplicativo gerada pelo catálogo do aplicativo e é diferente da ID fornecida no manifesto do `id` aplicativo do Teams:

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

**2.**  Se seu aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal, você poderá recuperar o `teamsAppId` seguinte:

**Referência de página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Se seu aplicativo tiver sido carregado ou feito sideload para um canal no escopo da equipe, você poderá recuperar `teamsAppId` o seguinte:

**Referência de página do Microsoft Graph:** [Listar aplicativos na equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Para restringir a lista de resultados, você pode filtrar em qualquer um dos campos do [**objeto teamsApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Determinar se o bot está instalado no momento para um destinatário de mensagem

**Referência de página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado e uma matriz com um único [objeto teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.

### <a name="-install-your-app"></a>✔ instalar seu aplicativo

**Referência de página do Microsoft Graph:** [Instalar aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP POST:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver o Microsoft Teams em execução, a instalação do aplicativo será vista imediatamente. Uma reinicialização pode ser necessária para exibir o aplicativo instalado.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Recuperar o **chatId da conversa**

Quando seu aplicativo é instalado para o usuário, o bot recebe uma notificação de evento que contém as informações necessárias `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para enviar a mensagem proativa.

O `chatId` também pode ser recuperado da seguinte forma:

**Referência de página do Microsoft Graph:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Você deve precisar do `{teamsAppInstallationId}` seu aplicativo. Se você não tiver, use o seguinte:

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A **propriedade id** da resposta é `teamsAppInstallationId` .

**2.** Faça a seguinte solicitação para buscar `chatId` o :

**Solicitação GET** HTTP (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` — ):  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

A **propriedade id** da resposta é `chatId` .

Você também pode recuperar `chatId` o com a seguinte solicitação, mas ela exige a permissão mais `Chat.Read.All` ampla:

**Solicitação GET** HTTP (permissão `Chat.Read.All` — ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Enviar mensagens proativas

Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot for adicionado para um usuário ou uma equipe e tiver recebido todas as informações do usuário.

## <a name="related-topic-for-teams-administrators"></a>Tópico relacionado para administradores do Teams
>
> [!div class="nextstepaction"]
> [**Gerenciar políticas de configuração de aplicativo no Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Exibir exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Exemplos de código de mensagens proativas do Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
