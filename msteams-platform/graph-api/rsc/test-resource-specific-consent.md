---
title: Testando o consentimento específico do recurso no Teams
description: Detalhes de teste de consentimento específico do recurso no Teams usando o postmaster
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: How-to
keywords: Gráfico de postagem do AAD RSC do Microsoft Teams Authorization SSO
ms.openlocfilehash: 882e2d1e7b85bd90cf9e3b7f6771a29eb8505314
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44801032"
---
# <a name="test-resource-specific-consent-permissions--in-teams"></a>Testar permissões de consentimento específicas do recurso no Teams

O consentimento específico de recurso (RSC) é uma integração da API do Microsoft Teams e do Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização. *Confira*[o consentimento específico de recurso (RSC) — API do Microsoft Teams Graph](resource-specific-consent.md).  

> [!NOTE]
>Para testar as permissões de RSC, seu arquivo de manifesto de aplicativo do Microsoft Teams deve incluir uma chave de **webApplicationInfo** preenchida com os seguintes campos:
>
> - **ID** — sua ID de aplicativo do Azure AD, *consulte* [registrar seu aplicativo no portal do Azure ad](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **recurso** — qualquer cadeia de caracteres, *consulte* a observação em [atualizar seu manifesto de aplicativo do Microsoft Teams](resource-specific-consent.md#update-your-teams-app-manifest)
> - **permissões de aplicativo** – permissões de RSC para seu aplicativo, *consulte* [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).

```json
"webApplicationInfo": {

        "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX", 

"resource": "https://AnyString",

        "applicationPermissions": [

    "TeamSettings.Read.Group",

   "ChannelMessage.Read.Group",

  "TeamSettings.Edit.Group",

  "ChannelSettings.Edit.Group",

  "Channel.Create.Group",

  "Channel.Delete.Group",

  "TeamsApp.Read.Group",

  "TeamsTab.Read.Group",

  "TeamsTab.Create.Group",

  "TeamsTab.Edit.Group",

  "TeamsTab.Delete.Group",

  "Member.Read.Group",

  "Owner.Read.Group",

        ]

    }
```

>[!IMPORTANT]
>No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.

## <a name="test-added-rsc-permissions-using-the-postman-app"></a>Teste adicionado permissões de RSC usando o aplicativo postmaster

Para verificar se as permissões de RSC estão sendo atendidas pela carga da solicitação de API, você precisará copiar o [código de teste JSON do RSC](test-rsc-json-file.md) para o seu ambiente local e atualizar os seguintes valores:

1. `azureADAppId`— ID de aplicativo do Azure AD do seu aplicativo.
1. `azureADAppSecret`— seu segredo de aplicativo do Azure AD (senha)
1. `teamGroupId`— Você pode obter a ID do grupo de equipe do cliente do teams da seguinte maneira:

> [!div class="checklist"]
>
> * No cliente do Microsoft Teams, selecione **equipes** na barra de navegação da extrema esquerda.
> * Selecione a equipe onde o aplicativo é instalado no menu suspenso.
> * Selecionar o ícone **mais opções** (&#8943;)
> * Selecione **obter link para a equipe** 
> * Copie e salve o valor de **GroupId** da cadeia de caracteres.

### <a name="using-postman"></a>Usando o postmaster

> [!div class="checklist"]
>
> * Abra o aplicativo [postmaster](https://www.postman.com) .
> * Selecione **arquivo**  =>  **importar**  =>  **Importar arquivo** para carregar o arquivo JSON atualizado de seu ambiente.  
> * Selecione a guia **coleções** . 
> * Selecione a divisa (>) ao lado do **teste RSC** para expandir o modo de exibição de detalhes e ver as solicitações da API.

Execute toda a coleção Permissions para cada chamada de API. As permissões que você especificou em seu manifesto de aplicativo devem ser bem-sucedidas, enquanto aquelas não especificadas devem falhar com um código de status HTTP 403. Verifique todos os códigos de status de resposta para confirmar que o comportamento das permissões de RSC em seu aplicativo atende às expectativas.

>[!NOTE]
>Para testar chamadas específicas de API de exclusão e leitura, adicione esses cenários de instância ao arquivo JSON.

## <a name="test--revoked-rsc-permissions-using-postman"></a>Testar permissões RSC revogadas usando [postmaster](https://www.postman.com/)

> [!div class="checklist"]
>
> * Desinstale o aplicativo da equipe específica.
> * Siga as etapas acima para [testar permissões de RSC adicionadas usando o postmaster](#test-added-rsc-permissions-using-the-postman-app).
> * Verifique todos os códigos de status de resposta para confirmar que as chamadas de API específicas que tiveram êxito falharam com um código de status HTTP 403.

> [!div class="nextstepaction"]
>
> [Saiba mais sobre a API do Graph e o Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0)