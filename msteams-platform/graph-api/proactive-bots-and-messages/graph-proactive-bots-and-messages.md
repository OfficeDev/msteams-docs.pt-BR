---
title: Usar o Microsoft Graph autorizar a instalação proativa de bots e mensagens no Teams
description: Descreve as mensagens proativas no Teams e como implementá-la. Saiba mais sobre a habilitação da instalação proativa de aplicativos e mensagens usando exemplo de código.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do teams Graph
ms.openlocfilehash: a3b7ffd24f7601c8247f1f11c6fe1a562d9cd847
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888003"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a>Instalação proativa de aplicativos usando Graph API para enviar mensagens

>[!IMPORTANT]
> O Microsoft Graph e Microsoft Teams visualizações públicas estão disponíveis para acesso antecipado e comentários. Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.

## <a name="proactive-messaging-in-teams"></a>Mensagens proativas em Teams

As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário. Eles servem a muitas finalidades, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou sondagens e a transmissão de notificações em toda a organização. As mensagens proativas Teams podem ser entregues como conversas **ad hoc** ou **baseadas em** diálogo:

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem proativa ad hoc| O bot interjectes uma mensagem sem interromper o fluxo de conversa.|
|Mensagem proativa baseada em caixa de diálogo | O bot cria um novo thread de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.|

## <a name="proactive-app-installation-in-teams"></a>Instalação proativa de aplicativos Teams

Antes que o bot possa enviar mensagens proativas a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe em que o usuário seja membro. Às vezes, você precisa enviar mensagens proativas aos usuários que não tenham instalado ou interagido anteriormente com seu aplicativo. Por exemplo, a necessidade de enviar informações importantes para todos na sua organização. Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

Permissões de tipo de recurso do Microsoft Graph [TeamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajudam você a gerenciar o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma Microsoft Teams:

|Permissão do aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um Teams aplicativo leia, instale, atualize e desinstale a si mesmo para qualquer usuário *,* sem entrar ou usar anteriormente.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que um Teams aplicativo leia, instale, atualize e desinstale-se em qualquer equipe *,* sem entrar ou usar anteriormente.|

Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

* **id**: Sua Azure Active Directory (AAD) ID do aplicativo.
* **resource**: A URL de recurso do aplicativo.

> [!NOTE]
>
> * Seu bot requer permissões de aplicativo e não delegadas pelo usuário, pois a instalação é para outras pessoas.
>
> * Um AAD administrador de locatário deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application). Depois que o aplicativo receber permissões, todos os membros do AAD locatário receberão as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilitar a instalação proativa de aplicativos e mensagens

> [!IMPORTANT]
> O Microsoft Graph pode instalar apenas aplicativos publicados na loja de aplicativos da sua organização ou no Teams store.

### <a name="create-and-publish-your-proactive-messaging-bot-for-teams"></a>Criar e publicar seu bot de mensagens proativo para Teams

Para começar, você precisa de um [bot](../../bots/how-to/create-a-bot-for-teams.md) para Teams com recursos [](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) de mensagens proativos que estão na loja de aplicativos da sua organização ou no Teams [store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store). [](../../concepts/bots/bot-conversations/bots-conv-proactive.md)

> [!TIP]
> O modelo de aplicativo [*company Communicator*](../..//samples/app-templates.md#company-communicator) de produção permite mensagens de transmissão e é um bom começo para criar seu aplicativo de bot proativo.

### <a name="get-the-teamsappid-for-your-app"></a>Obter o `teamsAppId` para seu aplicativo

Você pode recuperar o `teamsAppId` das seguintes maneiras:

* No catálogo de aplicativos da sua organização:

    **Referência Graph página da Microsoft: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

    **Solicitação GET HTTP:**

    ```http
    GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
    ```

    A solicitação deve retornar um objeto , que é a ID de aplicativo gerada pelo catálogo `teamsApp` `id` do aplicativo. Isso é diferente da ID fornecida no manifesto Teams aplicativo:

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

* Se seu aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal:

    **Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **Solicitação GET HTTP:**

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

* Se seu aplicativo já tiver sido carregado ou feito sideload para um canal no escopo da equipe:

    **Referência Graph página da Microsoft: Listar** [aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **Solicitação GET HTTP:**

    ```http
    GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

    > [!TIP]
    > Para restringir a lista de resultados, você pode filtrar qualquer um dos campos do [**objeto teamsApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

### <a name="determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>Determinar se o bot está instalado no momento para um destinatário de mensagem

Você pode determinar se o bot está instalado no momento para um destinatário de mensagem da seguinte maneira:

**Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação GET HTTP:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A solicitação retorna:

* Uma matriz vazia se o aplicativo não estiver instalado.
* Uma matriz com um único [objeto teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.

### <a name="install-your-app"></a>Instalar seu aplicativo

Você pode instalar seu aplicativo da seguinte forma:

**Referência Graph página da Microsoft:** [Instalar aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**Solicitação HTTP POST:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver Microsoft Teams em execução, a instalação do aplicativo ocorrerá imediatamente. Uma reinicialização pode ser necessária para exibir o aplicativo instalado.

### <a name="retrieve-the-conversation-chatid"></a>Recuperar a conversa `chatId`

Quando seu aplicativo é instalado para o usuário, o bot recebe uma notificação de evento que contém as informações necessárias `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para enviar a mensagem proativa.

**Referência Graph página da Microsoft:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

1. Você deve ter o `{teamsAppInstallationId}` seu aplicativo. Se você não o tiver, use o seguinte:

    **Solicitação GET HTTP:**

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
    ```

    A **propriedade id** da resposta é `teamsAppInstallationId` .

1. Faça a seguinte solicitação para buscar o `chatId` :

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

### <a name="send-proactive-messages"></a>Enviar mensagens proativas

Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot foi adicionado para um usuário ou uma equipe e recebeu todas as informações do usuário.

## <a name="code-sample"></a>Exemplo de código

| **Exemplo de nome** | **Descrição** | **.NET** | **Node.js** |
|---------------|--------------|--------|-------------|
| Instalação proativa do aplicativo e envio de notificações proativas | Este exemplo mostra como você pode usar a instalação proativa do aplicativo para usuários e enviar notificações proativas chamando as APIs Graph Microsoft. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) |

## <a name="additional-code-samples"></a>Exemplos de código adicionais
>
> [!div class="nextstepaction"]
> [**Teams exemplos proativos de código de mensagens**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="see-also"></a>Confira também

* [**Gerenciar políticas de configuração de aplicativos Microsoft Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Enviar notificações proativas para usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)
