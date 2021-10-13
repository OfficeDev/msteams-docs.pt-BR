---
title: Habilitar o consentimento específico do recurso Teams
description: Descreve o consentimento específico do recurso em Teams e como tirar proveito dele.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: abd56787c89fde44f7cc4c72f0f59e66b05af9aa
ms.sourcegitcommit: 37b1724bb0d2f1b087c356e0fd0ff80145671e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60291629"
---
# <a name="resource-specific-consent"></a>Consentimento específico do recurso

> [!NOTE]
> O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.

O RSC (consentimento específico de recursos) é uma integração de API Microsoft Teams e microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. O modelo de permissões RSC permite que *proprietários* de equipe e proprietários de *chat* concedam consentimento para que um aplicativo acesse e modifique os dados de uma equipe e os dados de um chat, respectivamente. 

**Observação:** Se um chat tiver uma reunião ou uma chamada associada a ela, as permissões de RSC relevantes também se aplicam a esses recursos.

## <a name="resource-specific-permissions"></a>Permissões específicas de recursos

As permissões granulares, Teams RSC específicas definem o que um aplicativo pode fazer em um recurso específico.

### <a name="resource-specific-permissions-for-a-team"></a>Permissões específicas de recursos para uma equipe

|Permissão do aplicativo| Action |
| ----- | ----- |
|TeamSettings.Read.Group | Obter as configurações dessa equipe.|
|TeamSettings.ReadWrite.Group|Atualize as configurações dessa equipe.|
|ChannelSettings.Read.Group|Obter nomes de canal dessa equipe, descrições de canal e configurações de canal.|
|ChannelSettings.ReadWrite.Group|Atualize os nomes de canal dessa equipe, descrições de canal e configurações de canal.|
|Channel.Create.Group|Criar canais nesta equipe. |
|Channel.Delete.Group|Exclua canais nesta equipe. |
|ChannelMessage.Read.Group |Receba as mensagens de canal dessa equipe. |
|TeamsAppInstallation.Read.Group|Obter uma lista dos aplicativos instalados dessa equipe.|
|TeamsTab.Read.Group|Obter uma lista das guias dessa equipe.|
|TeamsTab.Create.Group|Criar guias nesta equipe. |
|TeamsTab.ReadWrite.Group|Atualize as guias desta equipe. |
|TeamsTab.Delete.Group|Excluir as guias dessa equipe. |
|TeamMember.Read.Group|Obter os membros dessa equipe. |
|TeamsActivity.Send.Group|Crie novas notificações nos feeds de atividade dos usuários nesta equipe. |

Para obter mais detalhes, consulte permissões de consentimento [específicas do](/graph/permissions-reference#teams-resource-specific-consent-permissions)recurso de equipe .

### <a name="resource-specific-permissions-for-a-chat"></a>Permissões específicas de recursos para um chat

A tabela a seguir fornece permissões específicas de recursos para um chat:

|Permissão do aplicativo| Action |
| ----- | ----- |
| ChatSettings.Read.Chat         | Obter as configurações desse chat.                                    |
| ChatSettings.ReadWrite.Chat    | Atualize as configurações desse chat.                          |
| ChatMessage.Read.Chat          | Receba as mensagens desse chat.                                    |
| ChatMember.Read.Chat           | Obter membros desse chat.                                     |
| Chat.Manage.Chat               | Gerenciar este chat                                             |
| TeamsTab.Read.Chat             | Obter as guias desse chat.                                        |
| TeamsTab.Create.Chat           | Criar as guias neste chat.                                     |
| TeamsTab.Delete.Chat           | Exclua as guias deste chat.                                      |
| TeamsTab.ReadWrite.Chat        | Gerenciar as guias deste chat.                                      |
| TeamsAppInstallation.Read.Chat | Obter quais aplicativos estão instalados neste chat.                   |
| OnlineMeeting.ReadBasic.Chat   | Leia as propriedades básicas, como nome, agendamento, organizador, link de associação e notificações de início/término de uma reunião associada a esse chat. |
| Calls.AccessMedia.Chat         | Acesse fluxos de mídia em chamadas associadas a esse chat ou reunião.                                    |
| Calls.JoinGroupCalls.Chat         | Participe de chamadas associadas a esse chat ou reunião.                                    |
| TeamsActivity.Send.Chat         | Crie novas notificações nos feeds de atividade dos usuários neste chat. |

Para obter mais detalhes, consulte [chat resource-specific consent permissions](/graph/permissions-reference#chat-resource-specific-consent-permissions).

> [!NOTE]
> Permissões específicas de recursos estão disponíveis apenas para Teams aplicativos instalados no cliente Teams e atualmente não fazem parte do portal Azure Active Directory (AAD).

## <a name="enable-rsc-in-your-application"></a>Habilitar o RSC em seu aplicativo

1. [Configure as configurações de consentimento no portal AAD .](#configure-consent-settings-in-the-aad-portal)
    1. [Configure as configurações de consentimento do proprietário do grupo para o RSC em uma equipe.](#configure-group-owner-consent-settings-for-rsc-in-a-team)
    1. [Configurar configurações de consentimento do usuário para RSC em um chat](#configure-user-consent-settings-for-rsc-in-a-chat).
1. [Registre seu aplicativo com plataforma de identidade da Microsoft usando o portal AAD .](#register-your-app-with-microsoft-identity-platform-using-the-aad-portal)
1. [Revise suas permissões de aplicativo no portal AAD .](#review-your-application-permissions-in-the-aad-portal)
1. [Obtenha um token de acesso da plataforma de identidade](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Atualize seu Teams de aplicativo .](#update-your-teams-app-manifest)
1. [Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).
1. [Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)
    1. [Verifique se o aplicativo adicionou permissões RSC em uma equipe](#check-your-app-for-added-rsc-permissions-in-a-team).
    1. [Verifique se o aplicativo adicionou permissões RSC em um chat](#check-your-app-for-added-rsc-permissions-in-a-chat).

## <a name="configure-consent-settings-in-the-aad-portal"></a>Configurar configurações de consentimento no portal AAD

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team"></a>Configurar configurações de consentimento do proprietário do grupo para RSC em uma equipe

Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:

1. Entre no [portal do Azure](https://portal.azure.com) como Administrador [Global ou Administrador de Empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)
1. Selecione **Azure Active Directory**  >  **Enterprise**  >  **aplicativos Consentimento e permissões**  >  [**Configurações de consentimento do usuário.**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)
1. Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo **para aplicativos que acessam dados.** O padrão é **Permitir consentimento do proprietário do grupo para todos os proprietários do grupo.** Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.

    ![Configuração da equipe RSC do Azure](../../assets/images/azure-rsc-team-configuration.png)

Além disso, você pode habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em configurar o consentimento do proprietário do grupo [usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).

### <a name="configure-user-consent-settings-for-rsc-in-a-chat"></a>Configurar configurações de consentimento do usuário para RSC em um chat

Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) usuário diretamente no portal do Azure:

1. Entre no [portal do Azure](https://portal.azure.com) como Administrador [Global ou Administrador de Empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)
1. Selecione **Azure Active Directory**  >  **Enterprise**  >  **aplicativos Consentimento e permissões**  >  [**Configurações de consentimento do usuário.**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)
1. Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado **Consentimento do usuário para aplicativos**. O padrão é **Permitir consentimento do usuário para aplicativos**. Para um membro do chat instalar um aplicativo usando o RSC, o consentimento do usuário deve ser habilitado para esse usuário.

    ![Configuração de chat RSC do Azure](../../assets/images/azure-rsc-chat-configuration.png)

Além disso, você pode habilitar ou desabilitar o consentimento do usuário usando o PowerShell, siga as etapas descritas em configurar o consentimento do usuário [usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell).

## <a name="register-your-app-with-microsoft-identity-platform-using-the-aad-portal"></a>Registre seu aplicativo com plataforma de identidade da Microsoft usando o portal AAD usuário

O AAD portal fornece uma plataforma central para você registrar e configurar seus aplicativos. Seu aplicativo deve ser registrado no portal de AAD para integrar-se à plataforma de identidade e chamar as APIs Graph Microsoft. Para obter mais informações, [consulte register an application with the identity platform](/graph/auth-register-app-v2).

> [!WARNING]
> Uma AAD ID do aplicativo não deve ser compartilhada em vários Teams aplicativos. Deve haver um mapeamento 1:1 entre um aplicativo Teams e um AAD. As tentativas de instalar vários aplicativos Teams que estão associados à mesma ID AAD aplicativo causarão falhas de instalação ou tempo de execução.

## <a name="review-your-application-permissions-in-the-aad-portal"></a>Revise as permissões do aplicativo no portal AAD

1. Vá até a página **Registros** do Aplicativo Inicial e selecione seu aplicativo  >   RSC.
1. Escolha **permissões de API** no painel esquerdo e vá até a lista de permissões **configuradas** para seu aplicativo. Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua todas as permissões nessa página. Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.

> [!IMPORTANT]
> O AAD portal não pode ser usado para solicitar permissões RSC. As permissões RSC atualmente são exclusivas Teams aplicativos instalados no cliente Teams e são declaradas no arquivo JSON (manifesto do aplicativo Teams).

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Obtenha um token de acesso do plataforma de identidade da Microsoft

Para fazer Graph de API, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade. Antes que seu aplicativo possa obter um token da plataforma de identidade, ele deve ser registrado no portal AAD. O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.

Você deve ter os seguintes valores do processo de registro AAD para recuperar um token de acesso da plataforma de identidade:

- A **ID do aplicativo** atribuída pelo portal de registro do aplicativo. Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.
- O **segredo/senha do cliente** ou um par de chaves públicas ou privadas que é **Certificate**. Isso não é necessário para aplicativos nativos.
- Um **URI de redirecionamento** ou URL de resposta para seu aplicativo receber respostas de AAD.

Para obter mais informações, [consulte obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) e obter acesso sem um [usuário](/graph/auth-v2-service).

## <a name="update-your-teams-app-manifest"></a>Atualizar seu manifesto Teams aplicativo

As permissões RSC são declaradas no arquivo JSON do manifesto do aplicativo. Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua AAD ID do aplicativo. Para obter mais informações, [consulte register your app in the AAD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).|
|`resource`|Cadeia de Caracteres| Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.|
|`applicationPermissions`|Matriz de cadeias de caracteres|Permissões RSC para seu aplicativo. Para obter mais informações, consulte [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).|

>
> [!IMPORTANT]
> As permissões não RSC são armazenadas no portal do Azure. Não os adicione ao manifesto do aplicativo.
>

### <a name="example-for-rsc-in-a-team"></a>Exemplo de RSC em uma equipe

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

### <a name="example-for-rsc-in-a-chat"></a>Exemplo de RSC em um chat

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

> [!NOTE]
> Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions` .

## <a name="sideload-your-app-in-teams"></a>Fazer sideload do aplicativo Teams

Se o administrador Teams permite carregamentos de aplicativos personalizados, você pode [fazer sideload](~/concepts/deploy-and-publish/apps-upload.md) do aplicativo diretamente em uma equipe ou chat específico.

## <a name="check-your-app-for-added-rsc-permissions"></a>Verifique se o aplicativo tem permissões RSC adicionadas

> [!IMPORTANT]
> As permissões RSC não são atribuídas a um usuário. As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário. O aplicativo pode ter permissão para executar ações que o usuário não pode, como excluir uma guia. Você deve revisar a intenção do proprietário da equipe ou do proprietário do chat para seu uso antes de fazer chamadas de API RSC. Para obter mais informações, [consulte Microsoft Teams visão geral da API](/graph/teams-concept-overview).

Depois que o aplicativo for instalado em um recurso, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo no recurso.

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a>Verifique se o aplicativo adicionou permissões RSC em uma equipe

1. Obter groupId da **equipe Teams.**
1. Em Teams, selecione **Teams** no painel mais à esquerda.
1. Selecione a equipe onde o aplicativo deve ser instalado.
1. Selecione as releições &#x25CF;&#x25CF;&#x25CF; para essa equipe.
1. Selecione **Obter link para a equipe** no menu suspenso da equipe.
1. Copie e salve o **valor groupId** da caixa de diálogo **Obter um link** para a caixa de diálogo pop-up da equipe.
1. Entre no **Graph Explorer**.
1. Faça uma **chamada GET** para este ponto de extremidade: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants` . O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.

    ![Graph resposta do explorer a get call for team RSC permissions](../../assets/images/team-graph-permissions.png)

Para obter mais informações sobre como obter detalhes dos aplicativos instalados em uma equipe específica, consulte obter os nomes e outros detalhes dos aplicativos instalados na [equipe especificada](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a>Verifique se o aplicativo tem permissões RSC adicionadas em um chat

1. Obter a ID do thread de chat do cliente Teams *Web.*
1. No cliente Teams Web, selecione **Chat** no painel mais à esquerda.
1. Selecione o chat em que o aplicativo está instalado no menu suspenso.
1. Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.

    ![ID do thread de chat da URL da Web](../../assets/images/chat-thread-id.png)

1. Entre no **Graph Explorer**.
1. Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants` . O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.

    ![Graph de explorer para obter chamada para permissões RSC de chat](../../assets/images/chat-graph-permissions.png)

Para obter mais informações sobre como obter detalhes dos aplicativos instalados em um chat específico, consulte obter os nomes e outros detalhes dos aplicativos instalados no [chat especificado.](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat)

## <a name="code-sample"></a>Exemplo de código

| **Nome do exemplo** | **Descrição** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Resource-Specific Consentimento (RSC) | Use RSC para chamar Graph APIs. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|

## <a name="see-also"></a>Confira também
 
* [Testar permissões de consentimento específicas do recurso Teams](test-resource-specific-consent.md)
* [Consentimento específico do recurso no Microsoft Teams para administradores](/MicrosoftTeams/resource-specific-consent)
