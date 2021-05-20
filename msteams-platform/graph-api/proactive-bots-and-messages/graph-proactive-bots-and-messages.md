---
title: Use o Microsoft Graph para autorizar a instalação e a troca de mensagens proativas de bots em Teams
description: Descreve mensagens proativas em Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: equipes de instalação de chat de mensagens proativas Graph
ms.openlocfilehash: 06b50e5ab8594c257959430383bab5e355af4e06
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566149"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a>Instalação proativa de aplicativos usando a API do Graph e enviar mensagens

>[!IMPORTANT]
> As Graph da Microsoft e Microsoft Teams visualizações públicas estão disponíveis para acesso antecipado e feedback. Embora esta versão tenha sido submetida a testes extensivos, não se destina a ser usada na produção.

## <a name="proactive-messaging-in-teams"></a>Mensagens proativas em Teams

Mensagens proativas são iniciadas por bots para iniciar conversas com um usuário. Eles servem a muitos propósitos, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou pesquisas e a transmissão de notificações em toda a organização. Mensagens proativas em Teams podem ser entregues como conversas **baseadas em** **ad-hoc** ou dialogas:

|Tipo de mensagem | Descrição |
|----------------|-------------- |
|Mensagem proativa ad-hoc| O bot interjece uma mensagem sem interromper o fluxo de conversa.|
|Mensagem proativa baseada em diálogo | O bot cria um novo segmento de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle ao diálogo anterior.|

## <a name="proactive-app-installation-in-teams"></a>Instalação proativa de aplicativos em Teams

Antes que seu bot possa enviar uma mensagem proativa para um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe onde o usuário é um membro. Às vezes, você precisa enviar mensagens proativas aos usuários que não instalaram ou interagiram anteriormente com o seu aplicativo. Por exemplo, a necessidade de enviar informações vitais para todos em sua organização. Para tais cenários, você pode usar a API Graph Microsoft para instalar proativamente seu bot para seus usuários.

## <a name="permissions"></a>Permissões

As permissões de tipo de recurso do Microsoft [Graph AppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajudam você a gerenciar o ciclo de vida de instalação do seu aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) dentro da plataforma Microsoft Teams:

|Permissão de aplicativo | Descrição|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Permite que um aplicativo Teams leia, instale, atualize e desinstale para qualquer **usuário**, sem login ou uso prévio.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Permite que um aplicativo Teams leia, instale, atualize e desinstale em qualquer **equipe**, sem login ou uso prévio.|

Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao seu manifesto de aplicativo com os seguintes valores:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id** — seu ID do aplicativo Azure AD.
> * **recurso** — a URL de recurso para o aplicativo.
>
>[!NOTE]
>
> * Seu bot requer aplicação e não permissões delegadas pelo usuário porque a instalação é para outros.
>
> * Um administrador de inquilinos do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application). Após uma solicitação ser concedida permissões, todos os membros do inquilino Azure AD ganham as permissões concedidas.

## <a name="enable-proactive-app-installation-and-messaging"></a>Habilite a instalação e as mensagens proativas do aplicativo

> [!IMPORTANT]
>A Microsoft Graph só pode instalar aplicativos publicados na loja de aplicativos da sua organização ou na loja de Teams.

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Crie e publique seu bot de mensagens proativo para Teams

Para começar, você precisa de um [bot para Teams](../../bots/how-to/create-a-bot-for-teams.md) com recursos [proativos de mensagens](../../concepts/bots/bot-conversations/bots-conv-proactive.md) que estão na [loja de aplicativos da](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) sua organização ou na loja [de Teams](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).

>[!TIP]
> A empresa pronta para produção [**Communicator**](../..//samples/app-templates.md#company-communicator) modelo de aplicativo permite mensagens de transmissão e é uma boa base para a construção de seu aplicativo de bot proativo.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Obter o para o `teamsAppId` seu aplicativo

**1.** Você precisa dos `teamsAppId` próximos passos.

O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:

**Referência de página Graph da Microsoft:** [timesApp tipo de recurso](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**HTTP OBTER** solicitação:

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

O pedido deve retornar um `teamsApp` objeto. O objeto retornado `id` é o ID do aplicativo gerado pelo catálogo do aplicativo e é diferente do ID que você forneceu no manifesto do aplicativo Teams:

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

**2.**  Se o seu aplicativo já tiver sido carregado ou carregado lateralmente para um usuário no escopo pessoal, você pode recuperar o `teamsAppId` seguinte:

**Referência de página Graph da Microsoft:** [liste aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP OBTER** solicitação:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Se o seu aplicativo tiver sido carregado ou carregado lateralmente para um canal no escopo da equipe, você pode recuperar o `teamsAppId` seguinte:

**Referência de página Graph da Microsoft:** [liste aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP OBTER** solicitação:

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Para reduzir a lista de resultados, você pode filtrar em qualquer um dos campos do objeto [**TeamApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Determinar se o bot está instalado no momento para um destinatário de mensagens

**Referência de página Graph da Microsoft:** [liste aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP OBTER** solicitação:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Esta solicitação retorna uma matriz vazia se o aplicativo não estiver instalado e um array com um único objeto [de configuração do TimesAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.

### <a name="-install-your-app"></a>✔ Instale seu aplicativo

**Referência de página Graph da Microsoft:** [Instale aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**SOLICITAÇÃO HTTP POST:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Se o usuário tiver Microsoft Teams em execução, a instalação do aplicativo será vista imediatamente. Uma reinicialização pode ser necessária para visualizar o aplicativo instalado.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Recuperar o **chat de** conversa

Quando seu aplicativo é instalado para o usuário, o bot recebe uma `conversationUpdate` [notificação de evento](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) que contém as informações necessárias para enviar a mensagem proativa.

O `chatId` também pode ser recuperado da seguinte forma:

**Referência de página Graph da Microsoft:** [obtenha bate-papo](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Você deve precisar do seu aplicativo `{teamsAppInstallationId}` . Se você não tiver, use o seguinte:

**HTTP OBTER** solicitação:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

A propriedade de **id** da resposta é o `teamsAppInstallationId` .

**2.** Faça a seguinte solicitação para buscar `chatId` o:

**SOLICITAÇÃO HTTP GET** (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

A propriedade de **id** da resposta é o `chatId` .

Você também pode recuperar a `chatId` seguinte solicitação, mas requer a permissão mais `Chat.Read.All` ampla:

**SOLICITAÇÃO HTTP GET** (permissão `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Enviar mensagens proativas

Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot tiver sido adicionado para um usuário ou uma equipe e tenha recebido todas as informações do usuário.

## <a name="see-also"></a>Confira também

* [**Gerencie políticas de configuração de aplicativos em Microsoft Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Enviar notificações proativas aos usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="view-additional-code-samples"></a>Exibir amostras de código adicionais
>
> [!div class="nextstepaction"]
> [**Teams amostras de código de mensagens proativas**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)