---
title: Publicar aplicativos do Teams para o Microsoft 365
description: Saiba como tornar seus aplicativos do Teams habilitados para Microsoft 365 detectáveis para usuários no Teams, Outlook e Office por meio de distribuição multilocatário e multilocatário.
ms.date: 10/10/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: b225624970a380679b2b1a508bf3b4d2882de72e
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537518"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Publicar aplicativos do Teams para o Microsoft 365

O Microsoft Teams dá suporte a aplicativos do Teams habilitados para Microsoft 365 para produção.  Você pode distribuir esses aplicativos para o público que usa as versões de Lançamento *Direcionado (versão* prévia de desenvolvimento) do Outlook.com e Office.com, o build do Canal *Beta* do Outlook para área de trabalho do Windows e o build do Canal Atual do Office (versão prévia de desenvolvimento) do aplicativo do Office para Android. Opções de distribuição e processos para aplicativos do Teams habilitados para Microsoft 365 são os mesmos para aplicativos tradicionais do Teams.

Depois que ele for publicado, seu aplicativo será detectável como um aplicativo inserível nas lojas de aplicativos do Outlook e do Office, além da loja do Teams. Seu aplicativo usa as permissões definidas no Teams no Outlook e no Office. Os administradores do Teams [podem gerenciar o acesso aos aplicativos do Teams no Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) para usuários em sua organização.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="A captura de tela é um exemplo que mostra o Outlook e Office.com telas de instalação para os aplicativos SurveyMonkey e MURAL Teams.":::

## <a name="single-tenant-distribution"></a>Distribuição de locatário único

As extensões de mensagem habilitadas para o Outlook podem ser distribuídas para locatários de teste e produção de várias maneiras:

### <a name="teams-client"></a>Cliente do Teams

No menu **Aplicativos** , selecione **Gerenciar seus aplicativos** > **Publicar um aplicativo** > **Enviar um aplicativo para sua organização**. Isso requer aprovação do administrador de TI.

### <a name="teams-developer-portal"></a>Portal do Desenvolvedor do Teams

Use o [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/) para carregar e publicar um aplicativo em sua organização. Isso requer aprovação do administrador de TI. Para obter mais informações, consulte [Gerenciar seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>Centro de Administração do Microsoft Teams

Como administrador do Teams, você pode carregar e pré-instalar o pacote do aplicativo para o locatário da sua organização no [Centro de administração do Teams](https://admin.teams.microsoft.com/). Para obter mais informações, [consulte Carregar seus aplicativos personalizados no Centro de administração do Microsoft Teams](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote do aplicativo do [administrador da Microsoft](https://admin.microsoft.com/). Para obter mais informações, [consulte Testar e implantar Microsoft 365 Apps por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Distribuição multilocatário

O [processo de envio do Microsoft](https://appsource.microsoft.com/) AppSource (Marketplace comercial da Microsoft) para aplicativos do Teams habilitados para Outlook e Office é o mesmo que os aplicativos tradicionais do Teams. A única diferença é que você precisará usar o manifesto do aplicativo Teams versão [1.13](../tabs/how-to/using-teams-client-sdk.md) no pacote do aplicativo, que apresenta suporte para aplicativos do Teams executados no Microsoft 365.

> [!TIP]
> Use o Portal do Desenvolvedor do Teams para [validar](https://dev.teams.microsoft.com/validation) o pacote do aplicativo para resolver erros ou avisos antes de enviar para o repositório do Teams (por meio [do Microsoft Partner Network](https://partner.microsoft.com/)).

Para começar, confira [Distribuir seu aplicativo Microsoft Teams](../concepts/deploy-and-publish/apps-publish-overview.md).
