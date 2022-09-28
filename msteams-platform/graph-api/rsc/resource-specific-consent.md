---
title: Habilitar o consentimento específico do recurso no Teams
description: Saiba mais sobre as permissões de RSC (consentimento específicos de recursos) granulares com suporte, que permitem que os proprietários da equipe e os proprietários de chat concedam consentimento para um aplicativo.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 558ddd3603c9545781a3ebe06b7878df48b1333c
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100886"
---
# <a name="resource-specific-consent"></a>Consentimento específico do recurso

> [!NOTE]
> O consentimento específico do recurso para o escopo do chat está disponível [Visualização do desenvolvedor público](../../resources/dev-preview/developer-preview-intro.md) somente.

O RSC (consentimento específico do recurso) é uma integração do Microsoft Teams e da API do Microsoft Graph que permite que seu aplicativo use pontos de extremidade de API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização. O modelo de permissões RSC permite que *proprietários de equipe* e *proprietários de chat* concedam consentimento para que um aplicativo acesse e modifique os dados de uma equipe e os dados de um chat, respectivamente.

**Observação:** Se um chat tiver uma reunião ou uma chamada associada a ele, as permissões RSC relevantes também se aplicarão a esses recursos.

## <a name="resource-specific-permissions"></a>Permissões específicas do recurso

As permissões granulares, específicas do Teams e da RSC definem o que um aplicativo pode fazer dentro de um recurso específico.

### <a name="resource-specific-permissions-for-a-team"></a>Permissões específicas de recursos para uma equipe

|Permissão do aplicativo| Action |
| ----- | ----- |
|TeamSettings.Read.Group | Obtenha as configurações desta equipe.|
|TeamSettings.ReadWrite.Group|Atualize as configurações desta equipe.|
|ChannelSettings.Read.Group|Obtenha os nomes de canal, as descrições de canal e as configurações de canal desta equipe.|
|ChannelSettings.ReadWrite.Group|Atualize os nomes de canal, as descrições de canal e as configurações de canal desta equipe.|
|Channel.Create.Group|Criar canais nesta equipe. |
|Channel.Delete.Group|Exclua canais desta equipe. |
|ChannelMessage.Read.Group |Obtenha as mensagens de canal desta equipe. |
|TeamsAppInstallation.Read.Group|Obtenha uma lista dos aplicativos instalados desta equipe.|
|TeamsTab.Read.Group|Obtenha uma lista das guias desta equipe.|
|TeamsTab.Create.Group|Criar guias nesta equipe. |
|TeamsTab.ReadWrite.Group|Atualize as guias desta equipe. |
|TeamsTab.Delete.Group|Excluir as guias dessa equipe. |
|TeamMember.Read.Group|Obtenha os membros desta equipe. |
|TeamsActivity.Send.Group|Crie novas notificações nos feeds de atividades dos usuários nesta equipe. |

Para obter mais detalhes, consulte [permissões de consentimento específicas do recurso da equipe](/graph/permissions-reference#team-resource-specific-consent-permissions).

### <a name="resource-specific-permissions-for-a-chat"></a>Permissões específicas de recursos para um chat

A tabela a seguir fornece permissões específicas de recursos para um chat:

|Permissão do aplicativo| Action |
| ----- | ----- |
| ChatSettings.Read.Chat         | Obtenha as configurações deste chat.                                    |
| ChatSettings.ReadWrite.Chat    | Atualize as configurações deste chat.                          |
| ChatMessage.Read.Chat          | Obtenha as mensagens deste chat.                                    |
| ChatMember.Read.Chat           | Obtenha os membros deste chat.                                     |
| Chat.Manage.Chat               | Gerenciar este chat                                             |
| TeamsTab.Read.Chat             | Obtenha as guias deste chat.                                        |
| TeamsTab.Create.Chat           | Criar as guias neste chat.                                     |
| TeamsTab.Delete.Chat           | Exclua as guias deste chat.                                      |
| TeamsTab.ReadWrite.Chat        | Gerenciar as guias deste chat.                                      |
| TeamsAppInstallation.Read.Chat | Obtenha quais aplicativos estão instalados neste chat.                   |
| OnlineMeeting.ReadBasic.Chat   | Leia as propriedades básicas, como nome, agenda, organizador, link de ingresso e notificações de início/término de uma reunião associada a este chat. |
| Calls.AccessMedia.Chat         | Acesse fluxos de mídia em chamadas associadas a esse chat ou reunião.                                    |
| Calls.JoinGroupCalls.Chat         | Participe de chamadas associadas a esse chat ou reunião.                                    |
| TeamsActivity.Send.Chat         | Crie novas notificações nos feeds de atividades dos usuários neste chat. |
| OnlineMeetingTranscript.Read.Chat | Leia as transcrições da reunião associadas a este chat. |

Para obter mais detalhes, consulte [permissões de consentimento específicas do recurso de chat](/graph/permissions-reference#chat-resource-specific-consent-permissions).

> [!NOTE]
> As permissões específicas de recursos só estão disponíveis para aplicativos do Teams instalados no cliente do Teams e atualmente não fazem parte do portal Azure Active Directory (AAD).

## <a name="enable-rsc-in-your-application"></a>Habilitar o RSC em seu aplicativo

1. [Defina as configurações de consentimento](#configure-consent-settings).
    1. [Defina as configurações de consentimento do proprietário do grupo para a RSC em uma equipe usando o Azure AD portal](#configure-group-owner-consent-settings-for-rsc-in-a-team-using-the-azure-ad-portal).
    1. [Defina as configurações de consentimento do proprietário do chat para rsc em um chat usando as APIs do Microsoft Graph](#configure-chat-owner-consent-settings-for-rsc-in-a-chat-using-the-microsoft-graph-apis).
1. [Register seu aplicativo com a plataforma de identidade da Microsoft usando o portal do Azure AD](#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).
1. [Exibir suas permissões de aplicativo no portal do Azure AD](#review-your-application-permissions-in-the-azure-ad-portal).
1. [Obter um token de acesso da plataforma de identidade](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Atualize o manifesto do aplicativo Teams](#update-your-teams-app-manifest).
1. [Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).
1. [Verifique seu aplicativo para obter permissões de RSC adicionadas](#check-your-app-for-added-rsc-permissions).
    1. [Verifique seu aplicativo para obter permissões de RSC adicionadas em uma equipe](#check-your-app-for-added-rsc-permissions-in-a-team).
    1. [Verifique seu aplicativo para obter permissões de RSC adicionadas em um chat](#check-your-app-for-added-rsc-permissions-in-a-chat).

## <a name="configure-consent-settings"></a>Definir configurações de consentimento

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team-using-the-azure-ad-portal"></a>Definir configurações de consentimento do proprietário do grupo para rsc em uma equipe usando o portal Azure AD grupo

Você pode habilitar ou desabilitar o [consentimento do proprietário do grupo](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) diretamente no portal do Microsoft Azure:

1. Entre no [portal do Azure](https://portal.azure.com) como [Administrador Global ou Administrador da Empresa](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).
1. Selecione **Azure Active Directory** > **Aplicações Enterprise** > **Consentimento e permissões** > [**Configurações de consentimento do usuário**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings).
1. Habilite, desabilite ou limite o consentimento do usuário com o controle rotulado **Consentimento do proprietário do grupo para aplicativos que acessam dados**. O padrão é **Permitir o consentimento do proprietário do grupo para todos os proprietários do grupo**. Para que um proprietário de equipe instale um aplicativo usando RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.

    ![Configuração da equipe do RSC do Azure](../../assets/images/azure-rsc-team-configuration.png)

Além disso, você pode habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em [configurar o consentimento do proprietário do grupo usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).

### <a name="configure-chat-owner-consent-settings-for-rsc-in-a-chat-using-the-microsoft-graph-apis"></a>Definir configurações de consentimento do proprietário do chat para RSC em um chat usando as APIs do Microsoft Graph

Você pode habilitar ou desabilitar o RSC para chats usando API do Graph. A propriedade `isChatResourceSpecificConsentEnabled` em [**teamsAppSettings**](/graph/api/teamsappsettings-update#example-1-enable-installation-of-apps-that-require-resource-specific-consent-in-chats-meetings) determina se a RSC de chat está habilitada no locatário.

   ![Configuração da equipe RSC do Graph](../../assets/images/rsc/graph-rsc-chat-configuration.png)

> O valor padrão da propriedade **éChatResourceSpecificConsentEnabled** se baseia em se as configurações de consentimento do usuário são [ativadas ou desativadas](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) no locatário quando a RSC para chats é usada pela primeira vez. Essa pode ser a primeira vez que a) recupera o [**teamsAppSettings**](/graph/api/teamsappsettings-get) ou b) instala um aplicativo teams com permissões específicas de recursos em um chat/reunião.

## <a name="register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal"></a>Registrar seu aplicativo na plataforma de identidade da Microsoft usando o portal do Azure AD

O portal do Azure AD fornece uma plataforma central para você registrar e configurar seus aplicativos. Seu aplicativo deve ser registrado no portal do Azure AD para integrar-se à plataforma de identidade e chamar Microsoft Graph APIs. Para obter mais informações, consulte [registrar um aplicativo com a plataforma de identidade](/graph/auth-register-app-v2).

> [!WARNING]
> Uma ID de aplicativo do Azure AD não deve ser compartilhada entre vários aplicativos do Teams. Deve haver um mapeamento 1:1 entre um aplicativo do Teams e um aplicativo do Azure AD. As tentativas de instalar vários aplicativos do Teams associados à mesma ID de aplicativo do Azure AD causarão falhas de instalação ou de runtime.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Examinar suas permissões de aplicativo no portal do Azure AD

1. Vá para a página **Inicial** > **Registros de aplicativo** e selecione seu aplicativo RSC.
1. Escolha **permissões API** no painel esquerdo e percorra a lista de **Permissões configuradas** para seu aplicativo. Se seu aplicativo fizer apenas chamadas API do Graph RSC, exclua todas as permissões nessa página. Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.

> [!IMPORTANT]
> O portal do Azure AD não pode ser usado para solicitar permissões de RSC. No momento, as permissões RSC são exclusivas para aplicativos do Teams instalados no cliente do Teams e são declaradas no arquivo JSON (manifesto do aplicativo Teams).

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Obter um token de acesso da plataforma de identidade da Microsoft

Para fazer API do Graph chamadas, você deve obter um token de acesso para seu aplicativo da plataforma de identidade. Antes que seu aplicativo possa obter um token da plataforma de identidade, ele deve ser registrado no portal do Azure AD. O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.

Você deve ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:

* O **ID de Aplicativo** atribuída pelo portal de registro do aplicativo. Se seu aplicativo der suporte ao SSO (logon único), você deverá usar a mesma ID do Aplicativo para seu aplicativo e SSO.
* O **segredo/senha do cliente** ou um par de chaves pública ou privada que é **Certificado**. Isso não é necessário para aplicativos nativos.
* Um **URI de redirecionamento** ou URL de resposta para seu aplicativo receber respostas do Azure AD.

Para obter mais informações, consulte [Obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) e [Obtenha acesso sem um usuário](/graph/auth-v2-service).

## <a name="update-your-teams-app-manifest"></a>Atualizar o manifesto do aplicativo Teams

As permissões RSC são declaradas no arquivo JSON do manifesto do aplicativo.

> [!IMPORTANT]
> As permissões não RSC são armazenadas no portal do Azure. Não os adicione ao manifesto do aplicativo.

### <a name="manifest-changes-for-resource-specific-consent"></a>Alterações de manifesto para consentimento específico do recurso

<br>

<details>

<summary><b>Permissões RSC para o manifesto do aplicativo versão 1.12</b></summary>

Adicione uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:

|Nome| Tipo | Descrição|
|---|---|---|
|`id` |Cadeia de caracteres |Sua ID de aplicativo do Azure AD. Para obter mais informações, consulte[registrar seu aplicativo no portal do Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Cadeia de caracteres| Este campo não tem nenhuma operação na RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará isso.|

Especifique as permissões necessárias para o aplicativo.

|Nome| Tipo | Descrição|
|---|---|---|
|`authorization`|Objeto|Lista de permissões que o aplicativo precisa para funcionar. Para obter mais informações, consulte [espaço reservado para autorização de link no manifesto]

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
> Se o aplicativo tiver o objetivo de dar suporte à instalação nos escopos de equipe e chat, as permissões de equipe e chat poderão ser especificadas no mesmo manifesto em `authorization`.

<br>

</details>

<br>

<details>

<summary><b>Permissões RSC para o manifesto do aplicativo versão 1.11 ou anterior</b></summary>

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

> [!NOTE]
> Se o aplicativo tiver o objetivo de dar suporte à instalação nos escopos de equipe e chat, as permissões de equipe e chat poderão ser especificadas no mesmo manifesto em `applicationPermissions`.

<br>

</details>

## <a name="sideload-your-app-in-teams"></a>Faça o sideload do seu aplicativo do Teams

Se o administrador do Teams permitir uploads de aplicativos personalizados, você poderá fazer o [sideload do aplicativo](~/concepts/deploy-and-publish/apps-upload.md) diretamente para uma equipe ou chat específico.

## <a name="check-your-app-for-added-rsc-permissions"></a>Verifique seu aplicativo para obter permissões de RSC adicionadas

> [!IMPORTANT]
> As permissões RSC não são atribuídos a um usuário. As chamadas são feitas com permissões de aplicativo, não com permissões delegadas pelo usuário. O aplicativo pode ter permissão para executar ações que o usuário não pode, como excluir uma guia. Você deve examinar a intenção do proprietário da equipe ou do proprietário do chat para seu uso antes de fazer chamadas à API RSC. Para obter mais informações, consulte [Visão geral da API do Microsoft Teams](/graph/teams-concept-overview).

Depois que o aplicativo for instalado em um recurso, você poderá usar o [Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo no recurso.

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a>Verifique seu aplicativo para obter permissões de RSC adicionadas em uma equipe

1. Obtenha o **groupId** do Teams.
1. No Teams, selecione **Microsoft Teams** no painel mais à esquerda.
1. Selecione a equipe em que o aplicativo deve ser instalado.
1. Selecione as reticências ●●● para essa equipe.
1. Selecione **Obter link para a equipe** no menu suspenso da equipe.
1. Copie e salve o valor **groupId** da caixa de diálogo pop-up **Obter link para a equipe**.
1. Entre no **Explorador do Graph**.
1. Faça uma chamada **GET** para este ponto de extremidade: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants`. O campo `clientAppId` na resposta será mapeado para o `webApplicationInfo.id` especificado no manifesto do aplicativo Teams.

    ![Explorador do Graph resposta à chamada GET para permissões RSC da equipe](../../assets/images/team-graph-permissions.png)

Para obter mais informações sobre como obter detalhes dos aplicativos instalados em uma equipe específica, consulte [obter os nomes e outros detalhes dos aplicativos instalados na equipe especificada](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a>Verifique seu aplicativo para obter permissões de RSC adicionadas em um chat

1. Obtenha a ID do encadeamento de bate-papo do cliente *Web* do Teams.
1. No cliente Web do Teams, selecione **Chat** no painel mais à esquerda.
1. Selecione o chat em que o aplicativo está instalado no menu suspenso.
1. Copie o URL da web e salve o ID do tópico de chat da string.

    ![ID da conversa de chat da URL da Web](../../assets/images/chat-thread-id.png)

1. Entre no **Explorador do Graph**.
1. Faça uma chamada **GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants`. O campo `clientAppId` na resposta será mapeado para o `webApplicationInfo.id` especificado no manifesto do aplicativo Teams.

    ![Explorador do Graph resposta à chamada GET para permissões RSC de chat](../../assets/images/chat-graph-permissions.png)

Para obter mais informações sobre como obter detalhes de aplicativos instalados em um chat específico, consulte [obter os nomes e outros detalhes dos aplicativos instalados no chat especificado](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat).

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| RSC (Consentimento Específico do Recurso) | Use o RSC para chamar APIs do Graph. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|

## <a name="see-also"></a>Confira também

* [Teste permissões de consentimento específicas do recurso no Teams](test-resource-specific-consent.md)
* [Consentimento específico do recurso no Microsoft Teams para administradores](/MicrosoftTeams/resource-specific-consent)
