---
title: Consentimento específico do recurso no Teams
description: Descreve o consentimento específico do recurso no Microsoft Teams e como aproveitar isso.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: Gráfico de autorização do AAD SSO do Microsoft Teams
ms.openlocfilehash: 3cafbb090c4e4bc44a814c840a7a297357341bba
ms.sourcegitcommit: 43e1be9d9e3651ce73a8d2139e44d75550a0ca60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "49366858"
---
# <a name="resource-specific-consent-rsc"></a>Consentimento específico de recurso (RSC)

>[!IMPORTANT]
> Essas APIs estão acessíveis no https://graph.microsoft.com/beta ponto de extremidade.  O ponto de extremidade da [versão beta](/graph/versioning-and-support#beta-version) inclui APIs que estão atualmente em versão prévia e ainda não estão disponíveis. As APIs no ponto de extremidade beta estão sujeitas a alterações e não recomendamos que você as use em seus aplicativos de produção. 

O RSC (consentimento específico de recurso) é uma integração de Microsoft Teams e API do Microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização. O modelo de permissões de consentimento específico de recurso (RSC) permite que os *proprietários de equipe* concedam a permissão para um aplicativo acessar e/ou modificar os dados de uma equipe. As permissões do tipo granular, específicas de equipes, de RSC definem o que um aplicativo pode fazer dentro de uma equipe específica:

## <a name="resource-specific-permissions"></a>Permissões específicas do recurso

|Permissão de aplicativo| Action |
| ----- | ----- |
|TeamSettings.Read.Group | Obter as configurações da equipe.|
|TeamSettings.ReadWrite.Group|Atualizar as configurações para esta equipe.|
|ChannelSettings.Read.Group|Obtenha os nomes de canal, as descrições de canal e as configurações de canal para esta equipe.|
|ChannelSettings.ReadWrite.Group|Atualize os nomes de canal, as descrições de canal e as configurações de canal para essa equipe.|
|Channel.Create.Group|Criar canais nesta equipe.|
|Channel.Delete.Group|Excluir canais nesta equipe.|
|ChannelMessage.Read.Group |Obtenha as mensagens do canal da equipe.|
|TeamsAppInstallation.Read.Group|Obtenha uma lista dos aplicativos instalados pela equipe.|
|TeamsTab.Read.Group|Obtenha uma lista das guias da equipe.|
|TeamsTab.Create.Group|Criar guias nesta equipe.|
|TeamsTab.ReadWrite.Group|Atualize as guias desta equipe.|
|TeamsTab.Delete.Group|Excluir as guias dessa equipe.|
|TeamMember.Read.Group|Obter membros da equipe.|

>[!NOTE]
>As permissões específicas do recurso estão disponíveis apenas para aplicativos do teams instalados no cliente do Teams e atualmente não fazem parte do portal do Azure Active Directory.

## <a name="enable-resource-specific-consent-in-your-application"></a>Habilitar o consentimento específico do recurso em seu aplicativo

As etapas para habilitar o RSC no aplicativo são as seguintes:

1. [Defina as configurações de consentimento do proprietário do grupo no portal do Azure Active Directory](#configure-group-owner-consent-settings-in-the-azure-ad-portal).
1. [Registre seu aplicativo com a plataforma de identidade da Microsoft por meio do portal do Azure ad](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
1. [Revise suas permissões de aplicativo no portal do Azure ad](#review-your-application-permissions-in-the-azure-ad-portal).
1. [Obter um token de acesso da plataforma de identidade da Microsoft](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Atualize o manifesto do aplicativo do Microsoft Teams](#update-your-teams-app-manifest).
1. [Instale seu aplicativo diretamente no Teams](#install-your-app-directly-in-teams).
1. [Verifique seu aplicativo para obter permissões de RSC adicionadas](#check-your-app-for-added-rsc-permissions).

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a>Definir configurações de consentimento do proprietário do grupo no portal do Azure AD

Você pode habilitar ou desabilitar o [consentimento do proprietário do grupo](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) diretamente no portal do Azure:

> [!div class="checklist"]
>
>- Entre no [portal do Azure](https://portal.azure.com) como um administrador [global/administrador da empresa](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).  
 > - [Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise applications**  =>  configurações de consentimento do usuário **de consentimento e permissões de** aplicativos corporativos do Azure Active Directory  =>  **User consent settings**.
> - Habilitar, desabilitar ou limitar o consentimento do usuário com o controle chamado de **proprietário de grupo com consentimento para aplicativos acessando dados** (o padrão é **permitir o consentimento do proprietário do grupo para todos os proprietários do grupo**). Para que um proprietário de equipe instale um aplicativo usando RSC, o consentimento do proprietário do grupo deve estar habilitado para esse usuário.

![configuração do Azure RSC](../../assets/images/azure-rsc-configuration.png)

Para habilitar ou desabilitar o consentimento de proprietário de grupo no portal do Azure usando o PowerShell, siga as etapas descritas em [Configurar consentimento de proprietário de grupo usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell).

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a>Registrar seu aplicativo com a plataforma de identidade da Microsoft via portal do Azure AD

O portal do Azure Active Directory fornece uma plataforma central para que você registre e configure seus aplicativos. Seu aplicativo deve ser registrado no portal do Azure AD para integração com a plataforma de identidade da Microsoft e chamar as APIs do Microsoft Graph. *Confira* [registrar um aplicativo com a plataforma de identidade da Microsoft](/graph/auth-register-app-v2).

>[!WARNING]
>Não registre vários aplicativos do teams na mesma ID de aplicativo do Azure AD. A ID do aplicativo deve ser exclusiva para cada aplicativo. As tentativas de instalar vários aplicativos para a mesma ID de aplicativos falharão.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Revisar as permissões do aplicativo no portal do Azure AD

Navegue até a página registros de aplicativos **residenciais**  =>  **App registrations** e selecione seu aplicativo RSC. Escolha **permissões de API** da barra de navegação à esquerda e examine a lista de permissões configuradas para seu aplicativo. Se seu aplicativo fizer apenas chamadas de API de gráfico RSC, exclua todas as permissões nessa página. Se seu aplicativo também fizer chamadas não-RSC, mantenha essas permissões conforme necessário.

>[!IMPORTANT]
>O portal do Azure AD não pode ser usado para solicitar permissões de RSC. Atualmente, as permissões de RSC são exclusivas para aplicativos do teams instalados no cliente do Teams e são declaradas no arquivo de manifesto de aplicativo (JSON).

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Obter um token de acesso da plataforma de identidade da Microsoft

Para fazer chamadas à API do Graph, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade. Antes que o aplicativo possa obter um token da plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD. O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.

Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:

- A **ID do aplicativo** atribuída pelo portal de registro do aplicativo. Se seu aplicativo oferecer suporte a logon único (SSO), você deverá usar a mesma ID de aplicativo para o seu aplicativo e SSO.
- O  **segredo do cliente/senha** ou um par de chaves pública/privada (**certificado**). Isso não é necessário para aplicativos nativos.
- Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.

 *Confira* [obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) e [obter acesso sem um usuário](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Atualizar o manifesto do aplicativo do Microsoft Teams

As permissões de RSC são declaradas no seu arquivo de manifesto de aplicativo (JSON).  Adicione uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

> [!div class="checklist"]
>
> - **ID**  — sua ID de aplicativo do Azure AD. *Confira* [registrar seu aplicativo no portal do Azure ad](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **recurso**  — qualquer cadeia de caracteres. Este campo não tem nenhuma operação em RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.
> - **permissões de aplicativo** – permissões de RSC para seu aplicativo. *Consulte* [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).

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

## <a name="install-your-app-directly-in-teams"></a>Instalar seu aplicativo diretamente no Teams

Depois de criar seu aplicativo, você pode [carregar seu pacote de aplicativos](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) diretamente para uma equipe específica.  Para fazer isso, a configuração de política **carregar aplicativos personalizados** deve ser habilitada como parte das políticas de configuração de aplicativos personalizados. *Consulte* [configurações de política de aplicativos personalizadas](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

## <a name="check-your-app-for-added-rsc-permissions"></a>Verifique seu aplicativo para permissões de RSC adicionadas

>[!IMPORTANT]
>As permissões de RSC não são atribuídas a um usuário. As chamadas são feitas com permissões de aplicativo, não permissões delegadas de usuário. Portanto, o aplicativo pode ter permissão para executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve analisar a intenção do proprietário da equipe para seu caso de uso antes de realizar chamadas à API RSC. *Confira* [visão geral da API do Microsoft Teams](/graph/teams-concept-overview).

Depois que o aplicativo tiver sido instalado em uma equipe, você poderá usar o [Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer)  para exibir as permissões que foram concedidas ao aplicativo em uma equipe:

> [!div class="checklist"]
>
>- Obtenha o **GroupId** da equipe do cliente do teams.
> - No cliente do Microsoft Teams, selecione **equipes** na barra de navegação da extrema esquerda.
> - Selecione a equipe onde o aplicativo está instalado no menu suspenso.
> - Selecione o ícone **mais opções** (&#8943;).
> - Selecione **obter link para a equipe**.
> - Copie e salve o valor de **GroupId** da cadeia de caracteres.
> - Faça logon no **Explorador do Graph**.
> - Faça uma chamada **Get** para o ponto de extremidade a seguir: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` . O campo clientAppId na resposta será mapeado para a appId especificada no manifesto do aplicativo Teams.
  ![Resposta do explorador do Graph para obter uma chamada.](../../assets/images/graph-permissions.png)
 
## <a name="test-resource-specific-consent"></a>Teste o consentimento específico do recurso
 
> [!div class="nextstepaction"]
> [**Testar permissões de consentimento específicas do recurso no Teams**](test-resource-specific-consent.md)
 
## <a name="related-topic-for-teams-administrators"></a>Tópico relacionado para administradores do teams

> [!div class="nextstepaction"]
> [**Consentimento específico do recurso no Microsoft Teams para administradores**](/MicrosoftTeams/resource-specific-consent)
> 
