---
title: Consentimento específico de recursos em Teams
description: Descreve o consentimento específico de recursos em Teams e como fazer proveito disso.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: equipes autorização OAuth SSO AAD rsc Graph
ms.openlocfilehash: dabe0c33013fbb398eee7bf00ac2881cd86e6bc5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566121"
---
# <a name="resource-specific-consent-rsc"></a>Consentimento específico para recursos (RSC)

O RSC (Resource-Specific Consent, consentimento específico para recursos) é uma integração de API Microsoft Teams e microsoft Graph que permite que seu aplicativo use pontos finais de API para gerenciar equipes específicas dentro de uma organização. O modelo de permissões de consentimento específico para recursos (RSC) permite que *os proprietários de equipe* concedam consentimento para um aplicativo acessar e/ou modificar os dados de uma equipe. As permissões RSC granulares, Teams específicas, definem o que um aplicativo pode fazer dentro de uma equipe específica:

## <a name="resource-specific-permissions"></a>Permissões específicas de recursos

|Permissão de aplicativo| Action |
| ----- | ----- |
|TeamSettings.Read.Group | Pegue as configurações para esta equipe.|
|TeamSettings.ReadWrite.Group|Atualizar as configurações para esta equipe.|
|ChannelSettings.Read.Group|Obtenha os nomes do canal, as descrições do canal e as configurações do canal para esta equipe.|
|ChannelSettings.ReadWrite.Group|Atualize os nomes dos canais, as descrições dos canais e as configurações do canal para esta equipe.|
|Channel.Create.Group|Criar canais nesta equipe.|
|Channel.Delete.Group|Exclua canais nesta equipe.|
|ChannelMessage.Read.Group |Pegue as mensagens do canal desta equipe.|
|TeamsAppInstallation.Read.Group|Obtenha uma lista dos aplicativos instalados desta equipe.|
|TeamsTab.Read.Group|Pegue uma lista das guias deste time.|
|TeamsTab.Create.Group|Criar guias nesta equipe.|
|TeamsTab.ReadWrite.Group|Atualize as guias desta equipe.|
|TeamsTab.Delete.Group|Excluir as guias dessa equipe.|
|TeamMember.Read.Group|Pegue os membros da equipe.|

>[!NOTE]
>Permissões específicas de recursos só estão disponíveis para Teams aplicativos instalados no Teams cliente e atualmente não fazem parte do portal Azure Active Directory.

## <a name="enable-resource-specific-consent-in-your-application"></a>Habilite o consentimento específico de recursos em seu aplicativo

As etapas para habilitar o RSC em seu aplicativo são as seguintes:

1. [Configure as configurações de consentimento do proprietário do grupo no portal Azure Active Directory](#configure-group-owner-consent-settings-in-the-azure-ad-portal).
1. [Cadastre seu aplicativo com plataforma de identidade da Microsoft através do portal Azure AD](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
1. [Revise suas permissões de solicitação no portal Azure AD](#review-your-application-permissions-in-the-azure-ad-portal).
1. [Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Atualize seu manifesto de aplicativo Teams](#update-your-teams-app-manifest).
1. [Instale seu aplicativo diretamente em Teams](#sideload-your-app-in-teams).
1. [Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a>Configure as configurações de consentimento do proprietário do grupo no portal Azure AD

Você pode ativar ou desativar o [consentimento do proprietário do grupo](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) diretamente dentro do portal do Azure:

> [!div class="checklist"]
>
>- Faça login no [portal Azure](https://portal.azure.com) como [administrador global/administrador da empresa.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)  
 > - [Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise aplicativos**  =>  **Consentir e permissões**  =>  **Configurações de consentimento do usuário**.
> - Habilite, desabilitar ou limite o consentimento do usuário com o consentimento do proprietário do grupo de controle rotulado **para aplicativos que acessam dados** (O padrão é permitir o consentimento do proprietário do grupo para todos os **proprietários do grupo**). Para que um proprietário de equipe instale um aplicativo usando O RSC, o consentimento do proprietário do grupo deve ser ativado para esse usuário.

![configuração azure rsc](../../assets/images/azure-rsc-configuration.png)

Para ativar ou desativar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas no [consentimento do proprietário do grupo Configurar usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a>Cadastre seu aplicativo com plataforma de identidade da Microsoft através do portal Azure AD

O portal Azure Active Directory fornece uma plataforma central para você se cadastrar e configurar seus aplicativos. Seu aplicativo deve ser cadastrado no portal Azure AD para se integrar com o plataforma de identidade da Microsoft e ligar para a Microsoft Graph APIs. Para obter mais informações, consulte [Registrar um aplicativo no plataforma de identidade da Microsoft](/graph/auth-register-app-v2).

>[!WARNING]
>Não registre vários aplicativos Teams no mesmo id do aplicativo Azure AD. O id do aplicativo deve ser exclusivo para cada aplicativo. As tentativas de instalar vários aplicativos para o mesmo id do aplicativo falharão.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Revise suas permissões de aplicativo no portal Azure AD

Navegue até a página de registros do **Aplicativo Inicial** e selecione seu aplicativo  =>   RSC. Escolha permissões de **API** na barra de navegação esquerda e examine a lista de permissões configuradas para o seu aplicativo. Se o seu aplicativo fizer apenas chamadas de API Graph RSC, exclua toda a permissão nessa página. Se o seu aplicativo também fizer chamadas não-RSC, mantenha essas permissões conforme necessário.

>[!IMPORTANT]
>O portal Azure AD não pode ser usado para solicitar permissões RSC. As permissões RSC são atualmente exclusivas para Teams aplicativos instalados no Teams cliente e são declaradas no arquivo manifesto do aplicativo (JSON).

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Obtenha um token de acesso do plataforma de identidade da Microsoft

Para fazer Graph chamadas de API, você deve obter um token de acesso para o seu aplicativo a partir da plataforma de identidade. Antes que seu aplicativo possa obter um token do plataforma de identidade da Microsoft, ele deve ser registrado no portal Azure AD. O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.

Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:

- O **ID do aplicativo** atribuído pelo portal de registro do aplicativo. Se o aplicativo suportar um único login (SSO) você deve usar o mesmo ID do aplicativo para o seu aplicativo e SSO.
- O **cliente secreto/senha** ou um par de chaves públicas/privadas **(Certificado).** Isso não é necessário para aplicativos nativos.
- Um **URI redirecionar** (ou responder URL) para que seu aplicativo receba respostas do Azure AD.

 *Ver* [Obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) e obter acesso sem um [usuário](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Atualize seu manifesto de aplicativo de Teams

As permissões RSC são declaradas no arquivo manifesto do aplicativo (JSON).  Adicione uma tecla [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao seu manifesto de aplicativo com os seguintes valores:

> [!div class="checklist"]
>
> - **id**  — seu id de aplicativo Azure AD. Para obter mais informações, consulte [Cadastrar seu aplicativo no portal Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **recurso**  - qualquer string. Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer corda vai fazer.
> - **permissões de aplicativos** — Permissões RSC para o seu aplicativo. Para obter mais informações, consulte [Permissões específicas de recursos](resource-specific-consent.md#resource-specific-permissions).

>
>[!IMPORTANT]
> As permissões não-RSC são armazenadas no portal Azure. Não adicione ao manifesto do aplicativo.
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

## <a name="sideload-your-app-in-teams"></a>Carregar lateralmente seu aplicativo em Teams

Se o administrador de Teams permitir uploads personalizados de aplicativos, você pode [carregar seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md) diretamente para uma equipe específica.

## <a name="check-your-app-for-added-rsc-permissions"></a>Verifique se o seu aplicativo tem permissões RSC adicionadas

>[!IMPORTANT]
>As permissões RSC não são atribuídas a um usuário. As chamadas são feitas com permissões de aplicativos, não com permissões delegadas pelo usuário. Assim, o aplicativo pode ser autorizado a executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve revisar a intenção do proprietário da equipe para o seu caso de uso antes de fazer chamadas de API RSC. Para obter mais informações, consulte [Microsoft Teams visão geral da API](/graph/teams-concept-overview).

Uma vez que o aplicativo tenha sido instalado em uma equipe, você pode usar [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para visualizar as permissões que foram concedidas ao aplicativo em uma equipe:

> [!div class="checklist"]
>
>- Pegue o **groupId** da equipe do cliente Teams.
> - No Teams cliente, selecione **Teams** da barra de navegação de extrema esquerda.
> - Selecione a equipe onde o aplicativo está instalado no menu suspenso.
> - Selecione o ícone **Mais opções** (&#8943;).
> - Selecione **Obter link para equipe**.
> - Copie e salve o valor **do groupId** da string.
> - Faça login **no Graph Explorer**.
> - Faça uma chamada **GET** para o seguinte ponto final: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` . O campo clienteAppId na resposta irá mapear o appId especificado no manifesto do aplicativo Teams.
  ![Graph resposta do explorador para receber chamada.](../../assets/images/graph-permissions.png)

## <a name="code-sample"></a>Exemplo de código
| **Nome da amostra** | **Descrição** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Consentimento específico do recurso (RSC) | Use o RSC para chamar Graph APIs. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a>Confira também
 
* [Teste permissões de consentimento específicas para recursos em Teams](test-resource-specific-consent.md)
* [Consentimento específico de recursos em Microsoft Teams para administradores](/MicrosoftTeams/resource-specific-consent)


