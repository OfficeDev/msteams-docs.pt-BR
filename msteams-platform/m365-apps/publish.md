---
title: Publicar aplicativos do Teams para o Microsoft 365
description: Saiba como tornar seus aplicativos do Teams habilitados para Microsoft 365 detectáveis para usuários no Teams, Outlook e Office por meio de um único locatário e distribuição multilocatário.
ms.date: 10/10/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: cfe650e676252a16c1665f078938adbff0d4c7d7
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789881"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Publicar aplicativos do Teams para o Microsoft 365

O Microsoft Teams dá suporte a aplicativos do Teams habilitados para Microsoft 365 para produção. Você pode distribuir esses aplicativos para usuários que usam as versões *de versão*  direcionada(visualização de desenvolvimento) de Outlook.com e Office.com, o build do *Canal* Beta do Outlook para a área de trabalho do Windows e o build do Office Current Channel (versão prévia do desenvolvimento) do aplicativo Office para Android. As opções de distribuição e os processos para aplicativos do Teams habilitados para Microsoft 365 são os mesmos dos aplicativos tradicionais do Teams.

Depois de publicado, seu aplicativo será detectável como um aplicativo instalável nas lojas de aplicativos do Outlook e do Office, além da loja do Teams. Seu aplicativo usa as permissões definidas no Teams no Outlook e no Office. Os administradores do Teams podem [gerenciar o acesso a aplicativos do Teams no Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) para usuários em sua organização.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="A captura de tela é um exemplo que mostra o Outlook e Office.com instalar telas para os aplicativos SurveyMonkey e MURAL Teams.":::

## <a name="single-tenant-distribution"></a>Distribuição de locatário único

Extensões de mensagem habilitadas para Outlook podem ser distribuídas para locatários de teste e produção de várias maneiras:

### <a name="teams-client"></a>Cliente do Teams

No menu **Aplicativos** , **selecione Gerenciar seus aplicativos** > **Publicar um aplicativo** > **Enviar um aplicativo para sua organização**. Para enviar um aplicativo, é necessário a aprovação do administrador de TI.

### <a name="teams-developer-portal"></a>Portal do Desenvolvedor do Teams

Use o [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/) para carregar e publicar um aplicativo para sua organização. Carregar e publicar um aplicativo requer a aprovação do administrador de TI. Para obter mais informações, confira [Gerenciar seus aplicativos com o Portal do Desenvolvedor para Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>Centro de Administração do Microsoft Teams

Como administrador do Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização no [centro de administração do Teams](https://admin.teams.microsoft.com/). Para obter mais informações, consulte [Carregar seus aplicativos personalizados no centro de administração do Microsoft Teams](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote de aplicativos do administrador da [Microsoft](https://admin.microsoft.com/). Para obter mais informações, consulte [Testar e implantar Microsoft 365 Apps por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Distribuição multilocatário

O processo de envio do [Microsoft AppSource](https://appsource.microsoft.com/) (microsoft commercial marketplace) para aplicativos do Teams habilitados para Outlook e Office é igual ao dos aplicativos tradicionais do Teams. A única diferença é que você precisa usar o manifesto de aplicativo do Teams [versão 1.13](../tabs/how-to/using-teams-client-sdk.md) em seu pacote de aplicativos, o que apresenta suporte para aplicativos do Teams executados no Microsoft 365.

> [!TIP]
> Use o Portal de Desenvolvedores do Teams para [validar seu pacote de aplicativos](https://dev.teams.microsoft.com/validation) para resolver quaisquer erros ou avisos antes de enviá-lo à loja do Teams (via [Microsoft Partner Network](https://partner.microsoft.com/)).

Para começar, confira [Distribuir seu aplicativo do Microsoft Teams](../concepts/deploy-and-publish/apps-publish-overview.md).
