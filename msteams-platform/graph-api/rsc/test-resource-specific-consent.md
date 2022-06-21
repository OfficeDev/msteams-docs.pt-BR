---
title: Testar permissões de consentimento específicas do recurso no Teams
description: Detalhes do teste de consentimento específico do recurso no Teams usando o Postman com Exemplos de código
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: microsoft teams authorization OAuth SSO Microsoft Azure Active Directory (Azure AD) rsc Postman Graph
ms.openlocfilehash: d0eba34c8477c00e400e89adee7b9f09604918b7
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189882"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testar permissões de consentimento específicas do recurso no Teams

> [!NOTE]
> O consentimento específico do recurso para o escopo do chat está disponível apenas na [pré-visualização pública de desenvolvedor](../../resources/dev-preview/developer-preview-intro.md).

O RSC (consentimento específico do recurso) é uma integração do Microsoft Teams e da API do Microsoft Graph que permite que seu aplicativo use pontos de extremidade de API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. Para obter mais informações, consulte [RSC (Consentimento específico do recurso) do Microsoft Teams API do Graph](resource-specific-consent.md).

## <a name="prerequisites"></a>Pré-requisitos

Verifique se as seguintes alterações de manifesto do aplicativo para consentimento específico do recurso antes de testar:

<br>

<details>

<summary><b>Permissões de RSC para o manifesto do aplicativo versão 1.12 e posterior</b></summary>

Adicione uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua ID de aplicativo do Azure AD. Para obter mais informações, consulte[registrar seu aplicativo no portal do Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Cadeia de caracteres| Este campo não tem nenhuma operação na RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará isso.|

Especifique as permissões necessárias para o aplicativo.

|Nome| Tipo | Descrição|
|---|---|---|
|`authorization`|Objeto|Lista de permissões que o aplicativo precisa para funcionar. Para obter mais informações, consulte [autorização](../../resources/schema/manifest-schema.md#authorization).|

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
> Se o aplicativo tiver o objetivo de dar suporte à instalação nos escopos de equipe e chat, as permissões de equipe e chat poderão ser especificadas no mesmo manifesto em `authorization`

</details>

<br>

<details>

<summary><b>Permissões de RSC para o manifesto do aplicativo versão 1.11 e anteriores</b></summary>

Adicione uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua ID de aplicativo do Azure AD. Para obter mais informações, consulte[registrar seu aplicativo no portal do Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Cadeia de caracteres| Este campo não tem nenhuma operação na RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará isso.|
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
> Se o aplicativo tiver o objetivo de dar suporte à instalação nos escopos de equipe e chat, as permissões de equipe e chat poderão ser especificadas no mesmo manifesto em `applicationPermissions`

</details>

> [!IMPORTANT]
> No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.

> [!NOTE]
> Se o aplicativo for destinado a acessar APIs de chamada/mídia, o `webApplicationInfo.Id` deverá ser a ID do aplicativo do Azure AD de um [Serviço de Bot do Azure](/graph/cloud-communications-get-started#register-a-bot).

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a>O teste adicionou permissões de RSC a uma equipe usando o aplicativo Postman

Para verificar se as permissões RSC estão sendo respeitadas pelo conteúdo da solicitação de API, você precisa copiar o [código do teste JSON do RSC para a equipe](test-team-rsc-json-file.md) em seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: a ID do aplicativo do Azure AD do aplicativo.
* `azureADAppSecret`: sua senha de aplicativo do Azure AD.
* `token_scope`: o escopo é necessário para obter um token. defina o valor como https://graph.microsoft.com/.default.
* `teamGroupId`: você pode obter a ID do grupo de equipes do cliente do Teams da seguinte maneira:

    1. No cliente do Teams, selecione **Teams** na barra de navegação à esquerda.
    2. Selecione o chat em que o aplicativo está instalado no menu suspenso.
    3. Selecione o ícone **Mais opções**(&#8943;).
    4. Selecione **Obter um link para a equipe**.
    5. Copie e salve o valor **groupId** da cadeia de caracteres.

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a>O teste adicionou permissões RSC a um chat usando o aplicativo Postman

Para verificar se as permissões RSC estão sendo respeitadas pelo conteúdo da solicitação de API, você precisa copiar o [código de teste JSON do RSC para chats](test-chat-rsc-json-file.md) para seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: a ID do aplicativo do Azure AD do aplicativo.
* `azureADAppSecret`: sua senha de aplicativo do Azure AD.
* `token_scope`: o escopo é necessário para obter um token. defina o valor como https://graph.microsoft.com/.default.
* `tenantId`: o nome ou a ID de Objeto do Azure AD do seu locatário.
* `chatId`: você pode obter a ID do thread de chat do *cliente web* do Teams da seguinte maneira:

    1. No cliente do Teams, selecione **Chat** na barra de navegação à esquerda.
    2. Selecione o chat em que o aplicativo está instalado no menu suspenso.
    3. Copie o URL da web e salve o ID do tópico de chat da cadeia de caracteres.
![ID da conversa de chat da URL da Web.](../../assets/images/chat-thread-id.png)

### <a name="use-postman"></a>Usar o Postman

1. Abra o aplicativo [Postman](https://www.postman.com).
2. Selecione **Arquivo** > **Importar** > **Importar arquivo** para carregar o arquivo JSON atualizado do seu ambiente.  
3. Escolha a guia **Conjuntos**.
4. Selecione a divisa **>** ao lado do **Testar RSC** para expandir a exibição de detalhes e ver as solicitações de API.

Execute toda a coleção de permissões para cada chamada à API. As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403. Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atende às expectativas.

> [!NOTE]
> Para testar chamadas específicas à API DELETE e READ, adicione esses cenários de instância ao arquivo JSON.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testar permissões RSC revogadas usando o [Postman](https://www.postman.com/)

1. Desinstale o aplicativo do recurso específico.
2. Siga as etapas para chat ou equipe:
    1. [O teste adicionou permissões RSC a uma equipe usando o Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).
    2. [O teste adicionou permissões RSC a um chat usando o Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).
3. Verifique todos os códigos de status de resposta para confirmar se as chamadas à API específicas **falharam com um código de status HTTP 403**.

## <a name="see-also"></a>Confira também

* [API do Microsoft Graph e Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)
* [Consentimento específico do recurso](~/graph-api/rsc/resource-specific-consent.md)
