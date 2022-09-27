---
title: Visão geral – Distribuir seu aplicativo
description: Neste artigo, conheça as opções para publicar seu aplicativo Microsoft Teams, carregar e implantar seu aplicativo e GCC.
ms.topic: conceptual
author: v-rpatkur
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: b194e435ec6152993ce1269875d431ab4ef03aef
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044669"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir seu aplicativo Microsoft Teams

Você pode fornecer seu aplicativo Microsoft Teams para um indivíduo, equipe, organização ou qualquer pessoa que queira usá-lo. A maneira como você distribui depende de vários fatores, incluindo necessidades dos usuários, negócios, requisitos técnicos e suas metas para o aplicativo.

## <a name="configure-default-install-options"></a>Configurar opções de instalação padrão

Você pode configurar as opções de instalação padrão. Por exemplo, se a funcionalidade principal do aplicativo for um bot, você poderá tornar o bot a funcionalidade padrão quando um usuário instalar seu aplicativo em uma equipe.

## <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Para distribuir seu aplicativo Teams, você deve ter um pacote de aplicativo válido.  Um pacote de aplicativos é um arquivo zip que contém um **manifesto do aplicativo** e **ícones do aplicativo**.

## <a name="upload-your-app-in-teams"></a>Carregar seu aplicativo no Teams

Realizar o sideload de um aplicativo para uso pessoal, colaborar com sua equipe ou testar e depurar. Esse tipo de distribuição não requer um processo de revisão formal.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa).

Para obter mais informações, consulte [Carregue seu aplicativo no Teams](apps-upload.md).

## <a name="publish-your-app-to-your-org"></a>Publique seu aplicativo na sua organização

Disponibilize seu aplicativo para as pessoas na sua organização. Esse tipo de distribuição requer a aprovação do seu administrador do Teams.

Para obter mais informações, consulte [Gerencie seus aplicativos no Centro de administração do Teams](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json).

### <a name="government-community-cloud-gcc-organizations"></a>Organizações da Nuvem da Comunidade Governamental (GCC)

Em ambientes do GCC Teams, os aplicativos da Microsoft em conformidade são habilitados por padrão. No entanto, antes de publicar um aplicativo, verifique se todos os pontos de extremidade do aplicativo estão em conformidade com os requisitos da sua organização do GCC. Para obter mais informações, consulte [Nuvem da Comunidade Governamental](../app-fundamentals-overview.md#government-community-cloud).

> [!IMPORTANT]
>Se seu aplicativo incluir um bot ou uma extensão de mensagem, você deverá selecionar a opção **Microsoft Teams para o Governo** ao configurar um canal entre o bot e o Teams no Azure. Para obter mais informações, consulte [Conectar um bot a canais](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true).

## <a name="publish-your-app-to-the-teams-store"></a>Publique seu aplicativo na loja do Teams.

Disponibilize seu aplicativo para todos. Esse tipo de distribuição requer a aprovação da Microsoft.

Para obter mais informações, consulte as [Diretrizes de publicação da loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar as opções de instalação padrão](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Confira também

[Programa de Conformidade do Aplicativo do Microsoft 365](/microsoft-365-app-certification/overview)
