---
title: Testar permissões de consentimento específicas do recurso Teams
description: Detalhes do teste de consentimento específico do recurso em Teams postman com exemplos de código
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: autorização do teams OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: fc926e307c2e3ee5d1336c09e264930abe20d9d0
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887717"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testar permissões de consentimento específicas do recurso Teams

> [!NOTE]
> O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.

O RSC (consentimento específico de recursos) é uma integração de API Microsoft Teams e Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. Para obter mais informações, consulte [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).

> [!NOTE]
> Para testar as permissões RSC, seu arquivo de manifesto do aplicativo Teams deve incluir uma chave **webApplicationInfo** preenchida com os seguintes campos:
>
> - **id**: Sua ID do aplicativo do Azure AD, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).
> - **resource**: Qualquer cadeia de caracteres, consulte a nota em [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).
> - **permissões de aplicativo**: permissões RSC para seu aplicativo, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).

## <a name="example-for-a-team"></a>Exemplo para uma equipe
```json
"webApplicationInfo":{
    "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource":"https://AnyString",
    "applicationPermissions":[
        "TeamSettings.Read.Group",
        "TeamSettings.ReadWrite.Group",
        "ChannelSettings.Read.Group",
        "ChannelSettings.ReadWrite.Group",
        "Channel.Create.Group",
        "Channel.Delete.Group",
        "ChannelMessage.Read.Group",
        "TeamsAppInstallation.Read.Group",
        "TeamsTab.Read.Group",
        "TeamsTab.Create.Group",
        "TeamsTab.ReadWrite.Group",
        "TeamsTab.Delete.Group",
        "TeamMember.Read.Group",
        "TeamsActivity.Send.Group"
    ]
   }
```

## <a name="example-for-a-chat"></a>Exemplo para um chat
```json
"webApplicationInfo":{
    "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource":"https://AnyString",
    "applicationPermissions":[
        "ChatSettings.Read.Chat",
        "ChatSettings.ReadWrite.Chat",
        "ChatMessage.Read.Chat",
        "ChatMember.Read.Chat",
        "Chat.Manage.Chat",
        "TeamsTab.Read.Chat",
        "TeamsTab.Create.Chat",
        "TeamsTab.Delete.Chat",
        "TeamsTab.ReadWrite.Chat",
        "TeamsAppInstallation.Read.Chat",
        "OnlineMeeting.ReadBasic.Chat",
        "Calls.AccessMedia.Chat",
        "Calls.JoinGroupCalls.Chat",
        "TeamsActivity.Send.Chat"
    ]
   }
```

> [!IMPORTANT]
> No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.

>[!NOTE]
>Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions` .

>Se o aplicativo tiver como objetivo acessar as APIs de chamada/mídia, a ID do aplicativo AAD de um Serviço bot do `webApplicationInfo.Id` [Azure.](/graph/cloud-communications-get-started#register-a-bot)

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a>Test added RSC permissions to a team using the Postman app

Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-team-rsc-json-file.md) para a equipe em seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.
* `azureADAppSecret`: Sua senha do aplicativo do Azure AD.
* `token_scope`: O escopo é necessário para obter um token. definir o valor como https://graph.microsoft.com/.default .
* `teamGroupId`: Você pode obter a ID do grupo de equipe do cliente Teams da seguinte forma:

    1. No cliente Teams, selecione **Teams** na barra de navegação à esquerda.
    2. Selecione a equipe onde o aplicativo está instalado no menu suspenso.
    3. Selecione o **ícone Mais opções** (&#8943;).
    4. Selecione **Obter link para a equipe**. 
    5. Copie e salve o **valor groupId** da cadeia de caracteres.

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a>Test added RSC permissions to a chat using the Postman app

Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-chat-rsc-json-file.md) para chats em seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.
* `azureADAppSecret`: Sua senha do aplicativo do Azure AD.
* `token_scope`: O escopo é necessário para obter um token. definir o valor como https://graph.microsoft.com/.default .
* `tenantId`: O nome ou a AAD ID do objeto do locatário.
* `chatId`: Você pode obter a ID do thread de chat do cliente *Teams Web* da seguinte forma:

    1. No cliente Teams Web, selecione **Chat** na barra de navegação à extrema esquerda.
    2. Selecione o chat em que o aplicativo está instalado no menu suspenso.
    3. Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.
![ID do thread de chat da URL da Web.](../../assets/images/chat-thread-id.png)

### <a name="use-postman"></a>Usar o Postman

1. Abra o [aplicativo Postman.](https://www.postman.com)
2. Selecione **Importar arquivo**  >    >  **de importação de arquivo** para carregar o arquivo JSON atualizado do seu ambiente.  
3. Selecione a **guia Coleções.** 
4. Selecione a divisa **>** ao lado do **RSC de teste** para expandir o exibição de detalhes e consulte as solicitações de API.

Execute toda a coleção de permissões para cada chamada de API. As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403. Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atendem às expectativas.

> [!NOTE]
> Para testar chamadas de API DELETE e READ específicas, adicione esses cenários de instância ao arquivo JSON.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testar permissões RSC revogadas usando [Postman](https://www.postman.com/)

1. Desinstale o aplicativo do recurso específico.
2. Siga as etapas para chat ou equipe: 
    1. [Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).
    2. [Test added RSC permissions to a chat using Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).
3. Verifique todos os códigos de status de resposta para confirmar se as chamadas de API **específicas falharam com um código de status HTTP 403.**

## <a name="see-also"></a>Confira também

* [API Graph Microsoft e Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)
* [Consentimento específico do recurso](~/graph-api/rsc/resource-specific-consent.md)
