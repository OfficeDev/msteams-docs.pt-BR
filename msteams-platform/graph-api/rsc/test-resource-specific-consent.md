---
title: Testar permissões de consentimento específicas do recurso Teams
description: Detalhes do teste de consentimento específico do recurso em Teams postman com exemplos de código
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: autorização do teams OAuth SSO Azure AD rsc Postman Graph
ms.openlocfilehash: 8bde324791199d1369c5accf454774cdc1c9a828
ms.sourcegitcommit: 54f6690b559beedc330b971618e574d33d69e8a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62362925"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testar permissões de consentimento específicas do recurso Teams

> [!NOTE]
> O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.

O RSC (consentimento específico de recursos) é uma integração de API Microsoft Teams e Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. Para obter mais informações, consulte [Consentimento específico do recurso (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).

## <a name="prerequisites"></a>Pré-requisitos

Verifique as seguintes alterações de manifesto do aplicativo para consentimento específico do recurso antes do teste:

<br>

<details>

<summary><b>Permissões RSC para manifesto do aplicativo versão 1.12</b></summary>

Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua ID do aplicativo do Azure AD. Para obter mais informações, [consulte register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Cadeia de caracteres| Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.|

Especifique as permissões necessárias pelo aplicativo.

|Nome| Tipo | Descrição|
|---|---|---|
|`authorization`|Objeto|Lista de permissões que o aplicativo precisa para funcionar. Para obter mais informações, consulte [authorization](../../resources/schema/manifest-schema.md#authorization).|

Exemplo de RSC em uma equipe

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp"
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "TeamSettings.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamSettings.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "ChannelSettings.Read.Group",
                "type": "Application"
            },
            {
                "name": "ChannelSettings.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "Channel.Create.Group",
                "type": "Application"
            },
            {
                "name": "Channel.Delete.Group",
                "type": "Application"
            },
            {
                "name": "ChannelMessage.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsAppInstallation.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Create.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Delete.Group",
                "type": "Application"
            },
            {
                "name": "TeamMember.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsActivity.Send.Group",
                "type": "Application"
            }
        ]    
    }
}
```

Exemplo de RSC em um chat

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp"
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "ChatSettings.Read.Chat",
                "type": "Application"
            },
            {
                "name": "ChatSettings.ReadWrite.Chat",
                "type": "Application"
            },
            {
                "name": "ChatMessage.Read.Chat",
                "type": "Application"
            },
            {
                "name": "ChatMember.Read.Chat",
                "type": "Application"
            },
            {
                "name": "Chat.Manage.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Read.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Create.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Delete.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.ReadWrite.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsAppInstallation.Read.Chat",
                "type": "Application"
            },
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            },
            {
                "name": "Calls.AccessMedia.Chat",
                "type": "Application"
            },
            {
                "name": "Calls.JoinGroupCalls.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsActivity.Send.Chat",
                "type": "Application"
            }
        ]    
    }
}
```
    
> [!NOTE]
> Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `authorization`.

</details>

<br>

<details>

<summary><b>Permissões RSC para manifesto do aplicativo versão 1.11 ou anterior</b></summary>

Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua ID do aplicativo do Azure AD. Para obter mais informações, [consulte register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Cadeia de caracteres| Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.|
|`applicationPermissions`|Matriz de cadeias de caracteres|Permissões RSC para seu aplicativo. Para obter mais informações, consulte [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).|

Exemplo de RSC em uma equipe

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
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

Exemplo de RSC em um chat

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
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

<br>

> [!NOTE]
> Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions`.
    
</details>

> [!IMPORTANT]
> No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.

> [!NOTE]
> Se o aplicativo tiver como objetivo acessar APIs de chamada/mídia, `webApplicationInfo.Id` a ID do aplicativo do Azure AD deve ser de um [Serviço de Bot do Azure](/graph/cloud-communications-get-started#register-a-bot).

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a>Test added RSC permissions to a team using the Postman app

Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-team-rsc-json-file.md) para a equipe em seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.
* `azureADAppSecret`: Sua senha do aplicativo do Azure AD.
* `token_scope`: O escopo é necessário para obter um token. definir o valor como https://graph.microsoft.com/.default.
* `teamGroupId`: Você pode obter a ID do grupo de equipe do cliente Teams da seguinte forma:

    1. No cliente Teams, selecione **Teams** na barra de navegação à esquerda.
    2. Selecione a equipe onde o aplicativo está instalado no menu suspenso.
    3. Selecione o **ícone Mais opções** (&#8943;).
    4. Selecione **Obter link para a equipe**. 
    5. Copie e salve o **valor groupId** da cadeia de caracteres.

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a>Test added RSC permissions to a chat using the Postman app

Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC para chats](test-chat-rsc-json-file.md) em seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.
* `azureADAppSecret`: Sua senha do aplicativo do Azure AD.
* `token_scope`: O escopo é necessário para obter um token. definir o valor como https://graph.microsoft.com/.default.
* `tenantId`: O nome ou a ID do objeto do Azure AD do locatário.
* `chatId`: Você pode obter a ID do thread de chat do cliente *Teams Web* da seguinte forma:

    1. No cliente Teams Web, selecione **Chat** na barra de navegação à esquerda.
    2. Selecione o chat em que o aplicativo está instalado no menu suspenso.
    3. Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.
![ID do thread de chat da URL da Web.](../../assets/images/chat-thread-id.png)

### <a name="use-postman"></a>Usar o Postman

1. Abra o [aplicativo Postman](https://www.postman.com) .
2. Selecione **Arquivo** **FileImportImport** >  >  **para** carregar o arquivo JSON atualizado do seu ambiente.  
3. Selecione a **guia Coleções** . 
4. Selecione a divisa **>** ao lado do **RSC de teste** para expandir o exibição de detalhes e consulte as solicitações de API.

Execute toda a coleção de permissões para cada chamada de API. As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403. Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atendem às expectativas.

> [!NOTE]
> Para testar chamadas de API DELETE e READ específicas, adicione esses cenários de instância ao arquivo JSON.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testar permissões RSC revogadas usando [Postman](https://www.postman.com/)

1. Desinstale o aplicativo do recurso específico.
2. Siga as etapas para chat ou equipe: 
    1. [Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).
    2. [Test added RSC permissions to a chat using Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).
3. Verifique todos os códigos de status de resposta para confirmar se as chamadas de API **específicas falharam com um código de status HTTP 403**.

## <a name="see-also"></a>Confira também

* [API Graph Microsoft e Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)
* [Consentimento específico do recurso](~/graph-api/rsc/resource-specific-consent.md)
