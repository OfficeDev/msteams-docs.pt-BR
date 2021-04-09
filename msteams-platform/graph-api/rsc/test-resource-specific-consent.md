---
title: Testar permissões de consentimento específicas do recurso no Teams
description: Detalhes do teste de consentimento específico do recurso no Teams usando Postman
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: tutorial
keywords: Autorização do teams OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 0d3d1c895c77bb417a9fdd84e319103485aa8944
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634703"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testar permissões de consentimento específicas do recurso no Teams

O RSC (consentimento específico de recursos) é uma integração da API do Microsoft Teams e do Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização. Para obter mais informações, consulte Consentimento específico do recurso [(RSC) — API do Microsoft Teams Graph](resource-specific-consent.md).

> [!NOTE]
> Para testar as permissões RSC, o arquivo de manifesto do aplicativo teams deve incluir uma chave **webApplicationInfo** preenchida com os seguintes campos:
>
> - **id**: Sua ID do aplicativo do Azure AD, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest)
> - **permissões de aplicativo**: permissões RSC para seu aplicativo, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).

```json
"webApplicationInfo":{
      "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
      "resource":"https://AnyString",
      "applicationPermissions":[
         "Channel.Create.Group",
         "Channel.Delete.Group",
         "ChannelMessage.Read.Group",
         "ChannelSettings.Read.Group",
         "ChannelSettings.Edit.Group",
         "Member.Read.Group",
         "Owner.Read.Group",
         "TeamsApp.Read.Group",
         "TeamsTab.Read.Group",
         "TeamsTab.Create.Group",
         "TeamsTab.Edit.Group",
         "TeamsTab.Delete.Group",
         "TeamSettings.Read.Group",
         "TeamSettings.Edit.Group"
      ]
   }
```

> [!IMPORTANT]
> No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.

## <a name="test-added-rsc-permissions-using-the-postman-app"></a>Test added RSC permissions using the Postman app

Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-rsc-json-file.md) para seu ambiente local e atualizar os seguintes valores:

* `azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo
* `azureADAppSecret`: Seu segredo do aplicativo do Azure AD (senha)
* `token_scope`: o escopo é necessário para obter um token - definir o valor como https://graph.microsoft.com/.default
* `teamGroupId`: Você pode obter a ID do grupo de equipe do cliente do Teams da seguinte forma:

  > [!div class="checklist"]
  >
  > * No cliente do Teams, selecione **Teams** na barra de navegação à extrema esquerda.
  > * Selecione a equipe onde o aplicativo está instalado no menu suspenso.
  > * Selecione o **ícone Mais opções** (&#8943;)
  > * Selecione **Obter link para a equipe** 
  > * Copie e salve o **valor groupId** da cadeia de caracteres.

### <a name="use-postman"></a>Usar o Postman

1. Abra o [aplicativo Postman.](https://www.postman.com)
2. Selecione **Importar arquivo**  >    >  **de importação de arquivo** para carregar o arquivo JSON atualizado do seu ambiente.  
3. Selecione a **guia Coleções.** 
4. Selecione a divisa **>** ao lado do **RSC de teste** para expandir o exibição de detalhes e consulte as solicitações de API.

Execute toda a coleção de permissões para cada chamada de API. As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403. Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atendem às expectativas.

> [!NOTE]
> Para testar chamadas de API DELETE e READ específicas, adicione esses cenários de instância ao arquivo JSON.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testar permissões RSC revogadas usando [Postman](https://www.postman.com/)

1. Desinstale o aplicativo da equipe específica.
2. Siga as etapas para [Testar as permissões RSC adicionadas usando Postman](#test-added-rsc-permissions-using-the-postman-app).
3. Verifique todos os códigos de status de resposta para confirmar se as chamadas de API específicas, bem-sucedidas, falharam com um **código de status HTTP 403**.

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [API e Teams do Microsoft Graph](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

