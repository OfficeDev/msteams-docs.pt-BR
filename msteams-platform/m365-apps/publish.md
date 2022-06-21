---
title: Publicar aplicativos do Teams para o Microsoft 365
description: Saiba como tornar seus aplicativos Microsoft 365 habilitados para Teams para usuários no Teams, Outlook e Office.
ms.date: 05/24/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: ff0391bb82bed022ec372094546e3a5236e030ea
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190190"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Publicar aplicativos do Teams para o Microsoft 365

Microsoft 365 aplicativos Teams habilitados para uso em Microsoft Teams. Você pode distribuir esses aplicativos para públicos-alvo que usam  as versões de Lançamento Direcionado do outlook.com e do office.com e a compilação do Canal *Beta* do Outlook para Windows área de trabalho. As opções de distribuição e os processos Microsoft 365 aplicativos Teams habilitados são os mesmos para aplicativos Teams tradicionais.

Depois que ele for publicado, seu aplicativo será detectável como um aplicativo inserível nas lojas Outlook e Aplicativo do Office, além da Teams store. Seu aplicativo usa as permissões definidas em Teams entre Outlook e Office. Teams administradores podem [gerenciar o acesso Teams aplicativos](/MicrosoftTeams/manage-third-party-teams-apps) em Microsoft 365 para usuários em sua organização.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="Outlook e Office.com para os aplicativos SurveyMonkey e MURAL Teams.com":::

## <a name="single-tenant-distribution"></a>Distribuição de locatário único

Outlook de mensagens habilitadas para Outlook podem ser distribuídas para locatários de teste e produção de várias maneiras:

### <a name="teams-client"></a>Cliente do Teams

No menu **Aplicativos** , selecione **Gerenciar seus aplicativos** > **Publicar um aplicativo** > **Enviar um aplicativo para sua organização**. Isso requer aprovação do administrador de TI.

### <a name="teams-developer-portal"></a>Teams Portal do Desenvolvedor

Use o [Teams Portal do Desenvolvedor](https://dev.teams.microsoft.com/) para carregar e publicar um aplicativo em sua organização. Isso requer aprovação do administrador de TI. Para obter mais informações, [consulte Gerenciar seus aplicativos com o Portal do Desenvolvedor para Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>Centro de Administração do Microsoft Teams

Como administrador Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização [Teams centro de administração](https://admin.teams.microsoft.com/). Para obter mais informações, [Upload seus aplicativos personalizados no Microsoft Teams de administração](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote do aplicativo do [administrador da Microsoft](https://admin.microsoft.com/). Para obter mais informações, [consulte Testar e implantar Microsoft 365 Apps por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Distribuição multilocatário

O [processo de envio do Microsoft AppSource](https://appsource.microsoft.com/) (marketplace comercial da Microsoft) para aplicativos Teams habilitados para Outlook e Office é o mesmo que os aplicativos Teams tradicionais. A única diferença é que você precisará usar o manifesto do aplicativo Teams versão [1.13](../tabs/how-to/using-teams-client-sdk.md) no pacote do aplicativo, que introduz suporte para aplicativos Teams executados em Microsoft 365.

> [!TIP]
> Use Teams Portal do Desenvolvedor para validar [](https://dev.teams.microsoft.com/validation) o pacote do aplicativo para resolver erros ou avisos antes de enviá-lo ao repositório Teams (por meio [do Microsoft Partner Network](https://partner.microsoft.com/)).

Para começar, consulte [Distribuir seu Microsoft Teams aplicativo](../concepts/deploy-and-publish/apps-publish-overview.md).
