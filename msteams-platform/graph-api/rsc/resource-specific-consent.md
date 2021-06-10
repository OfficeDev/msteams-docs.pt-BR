---
title: Consentimento específico do recurso em Teams
description: Descreve o consentimento específico do recurso em Teams e como tirar proveito dele.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: d751e5dba22b19edfe6ffda3eb6a73a37375f92b
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630674"
---
# <a name="resource-specific-consent-rsc"></a>Consentimento específico do recurso (RSC)

O RSC (consentimento específico de recurso) é uma integração Microsoft Teams api do Microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização. O modelo de permissões de consentimento específico do recurso (RSC) permite que os *proprietários* da equipe concedam consentimento para que um aplicativo acesse e/ou modifique os dados de uma equipe. As permissões RSC granulares, Teams específicas do RSC definem o que um aplicativo pode fazer em uma equipe específica:

## <a name="resource-specific-permissions"></a>Permissões específicas de recursos

|Permissão de aplicativo| Action |
| ----- | ----- |
|TeamSettings.Read.Group | Obter as configurações dessa equipe.|
|TeamSettings.ReadWrite.Group|Atualizar as configurações para esta equipe.|
|ChannelSettings.Read.Group|Obter os nomes de canal, descrições de canal e configurações de canal para essa equipe.|
|ChannelSettings.ReadWrite.Group|Atualize os nomes de canal, descrições de canal e configurações de canal para essa equipe.|
|Channel.Create.Group|Criar canais nesta equipe.|
|Channel.Delete.Group|Exclua canais nesta equipe.|
|ChannelMessage.Read.Group |Receba as mensagens de canal dessa equipe.|
|TeamsAppInstallation.Read.Group|Obter uma lista dos aplicativos instalados dessa equipe.|
|TeamsTab.Read.Group|Obter uma lista das guias dessa equipe.|
|TeamsTab.Create.Group|Criar guias nesta equipe.|
|TeamsTab.ReadWrite.Group|Atualize as guias desta equipe.|
|TeamsTab.Delete.Group|Excluir as guias dessa equipe.|
|TeamMember.Read.Group|Obter os membros dessa equipe.|

>[!NOTE]
>Permissões específicas de recursos estão disponíveis apenas para Teams aplicativos instalados no cliente Teams e atualmente não fazem parte do portal Azure Active Directory.

## <a name="enable-resource-specific-consent-in-your-application"></a>Habilitar o consentimento específico do recurso em seu aplicativo

As etapas para habilenciar o RSC em seu aplicativo são as seguintes:

1. [Configure as configurações de consentimento do proprietário do grupo no portal Azure Active Directory .](#configure-group-owner-consent-settings-in-the-azure-ad-portal)
1. [Registre seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD.](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal)
1. [Revise suas permissões de aplicativo no portal do Azure AD.](#review-your-application-permissions-in-the-azure-ad-portal)
1. [Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Atualize seu Teams de aplicativo .](#update-your-teams-app-manifest)
1. [Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).
1. [Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a>Configurar configurações de consentimento do proprietário do grupo no portal do Azure AD

Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:

> [!div class="checklist"]
>
>- Entre no [portal do Azure](https://portal.azure.com) como administrador [global/administrador da empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)  
 > - [Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise**  =>  **aplicativos Consentimento e permissões** Configurações de consentimento  =>  **do usuário.**
> - Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo para aplicativos que acessam dados **(O** padrão é Permitir o consentimento do proprietário do grupo para todos os proprietários **do grupo**). Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.

![Configuração rsc do azure](../../assets/images/azure-rsc-configuration.png)

Para habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a>Registrar seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD

O Azure Active Directory portal fornece uma plataforma central para você registrar e configurar seus aplicativos. Seu aplicativo deve ser registrado no portal do Azure AD para se integrar ao plataforma de identidade da Microsoft e chamar as APIs Graph Microsoft. Para obter mais informações, [consulte Register an application with the plataforma de identidade da Microsoft](/graph/auth-register-app-v2).

>[!WARNING]
>Não registre vários Teams aplicativos na mesma ID do aplicativo do Azure AD. A id do aplicativo deve ser exclusiva para cada aplicativo. As tentativas de instalar vários aplicativos na mesma ID do aplicativo falharão.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Revise suas permissões de aplicativo no portal do Azure AD

Navegue até **a página Registros** do Aplicativo Inicial e selecione seu aplicativo  =>   RSC. Escolha **permissões de API** na barra de nav esquerda e examine a lista de permissões configuradas para seu aplicativo. Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua toda a permissão nessa página. Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.

>[!IMPORTANT]
>O portal do Azure AD não pode ser usado para solicitar permissões RSC. As permissões RSC atualmente são exclusivas Teams aplicativos instalados no cliente Teams e são declaradas no arquivo JSON (manifesto do aplicativo).

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Obtenha um token de acesso do plataforma de identidade da Microsoft

Para fazer Graph de API, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade. Para que seu aplicativo possa obter um token do plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD. O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.

Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:

- A **ID do aplicativo** atribuída pelo portal de registro do aplicativo. Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.
- O  **segredo/senha do cliente** ou um par de chaves públicas/privadas (**Certificado**). Isso não é necessário para aplicativos nativos.
- Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.

 *Consulte* [Obter acesso em nome de um usuário e](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) Obter acesso sem um [usuário](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Atualizar seu manifesto Teams aplicativo

As permissões RSC são declaradas no arquivo JSON (manifesto do aplicativo).  Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

> [!div class="checklist"]
>
> - **id**  — sua id de aplicativo do Azure AD. Para obter mais informações, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **resource**  — qualquer cadeia de caracteres. Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.
> - **permissões de aplicativo** — permissões RSC para seu aplicativo. Para obter mais informações, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).

>
>[!IMPORTANT]
> As permissões não RSC são armazenadas no portal do Azure. Não os adicione ao manifesto do aplicativo.
>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.Edit.Group",
      "ChannelSettings.ReadWrite.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.ReadWrite.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group"
    ]
  }
```

## <a name="sideload-your-app-in-teams"></a>Fazer sideload do aplicativo Teams

Se o administrador Teams permite carregamentos de aplicativos personalizados, você pode [fazer sideload](~/concepts/deploy-and-publish/apps-upload.md) do aplicativo diretamente em uma equipe específica.

## <a name="check-your-app-for-added-rsc-permissions"></a>Verifique se o aplicativo tem permissões RSC adicionadas

>[!IMPORTANT]
>As permissões RSC não são atribuídas a um usuário. As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário. Assim, o aplicativo pode ter permissão para executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve analisar a intenção do proprietário da equipe para seu caso de uso antes de fazer chamadas de API RSC. Para obter mais informações, [consulte Microsoft Teams visão geral da API](/graph/teams-concept-overview).

Depois que o aplicativo for instalado em uma equipe, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo em uma equipe:

> [!div class="checklist"]
>
>- Obter **groupId** da equipe do cliente Teams.
> - No cliente Teams, selecione **Teams** na barra de nav da extrema esquerda.
> - Selecione a equipe onde o aplicativo está instalado no menu suspenso.
> - Selecione o **ícone Mais opções** (&#8943;).
> - Selecione **Obter link para a equipe**.
> - Copie e salve o **valor groupId** da cadeia de caracteres.
> - Faça **logoff Graph Explorer**.
> - Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` . O campo clientAppId na resposta será mapeado para o appId especificado no manifesto Teams aplicativo.
  ![Graph resposta do explorer à chamada GET.](../../assets/images/graph-permissions.png)

## <a name="code-sample"></a>Exemplo de código
| **Exemplo de nome** | **Descrição** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Consentimento Específico do Recurso (RSC) | Use RSC para chamar Graph APIs. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a>Confira também
 
* [Testar permissões de consentimento específicas do recurso Teams](test-resource-specific-consent.md)
* [Consentimento específico do recurso no Microsoft Teams para administradores](/MicrosoftTeams/resource-specific-consent)


