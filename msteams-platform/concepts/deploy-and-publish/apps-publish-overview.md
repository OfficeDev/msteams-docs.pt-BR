---
title: Visão geral – Distribuir seu aplicativo
description: Descreve as opções para publicar seu aplicativo Microsoft Teams, carregar seu aplicativo e GCC.
ms.topic: conceptual
author: v-rpatkur
ms.author: surbhigupta
ms.localizationpriority: none
keywords: deploy publish app upload gcc
ms.openlocfilehash: 5db182f9276865fc98d277f642f7e58fd4a52df5
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104431"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir seu Microsoft Teams aplicativo

Você pode fornecer seu aplicativo Microsoft Teams para um indivíduo, equipe, organização ou qualquer pessoa que queira usá-lo. A maneira como você distribui depende de vários fatores, incluindo necessidades dos usuários, negócios, requisitos técnicos e suas metas para o aplicativo.

## <a name="configure-default-install-options"></a>Configurar opções de instalação padrão

Configure as opções de instalação padrão. Por exemplo, se a funcionalidade principal do aplicativo for um bot, você também poderá tornar o bot a funcionalidade padrão quando um usuário instalar seu aplicativo em uma equipe.

## <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Para distribuir seu Microsoft Teams, você deve ter um pacote de aplicativo válido.  Um pacote de aplicativos é um arquivo zip que contém um manifesto **do aplicativo e** **ícones de aplicativo**.

## <a name="upload-your-app-in-teams"></a>Upload seu aplicativo no Teams

Realizar sideload de um aplicativo para uso pessoal, colaborar com sua equipe ou testar e depurar. Esse tipo de distribuição não requer um processo de revisão formal.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa).

Para obter mais informações, [consulte carregar seu aplicativo Teams](apps-upload.md).

## <a name="publish-your-app-to-your-org"></a>Publique seu aplicativo na sua organização

Dispobilize seu aplicativo para as pessoas em sua organização. Esse tipo de distribuição requer a aprovação Teams seu administrador.

Para obter mais informações, [consulte gerenciar seus aplicativos no Teams de administração](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json).

### <a name="government-community-cloud-gcc-organizations"></a>Nuvem da Comunidade Governamental (GCC)

Em GCC Teams ambientes, os aplicativos da Microsoft em conformidade são habilitados por padrão. No entanto, antes de publicar um aplicativo, verifique se todos os pontos de extremidade do aplicativo estão em conformidade com GCC requisitos da sua organização. Para obter mais informações, [consulte Nuvem da Comunidade Governamental](../app-fundamentals-overview.md#government-community-cloud).

> [!IMPORTANT]
>Se seu aplicativo incluir um bot ou uma extensão de mensagem, você deverá selecionar a opção **Microsoft Teams for Government** ao configurar um canal entre o bot e o Teams no Azure. Para obter mais informações, [consulte conectar um bot aos canais](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true).

## <a name="publish-your-app-to-the-teams-store"></a>Publicar seu aplicativo na Teams armazenamento

Dispobilize seu aplicativo para todos. Esse tipo de distribuição requer aprovação da Microsoft.

Para obter mais informações, [consulte publicar no Teams store](~/concepts/deploy-and-publish/appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar as opções de instalação padrão do aplicativo](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Confira também

[Programa de Conformidade do Aplicativo do Microsoft 365](/microsoft-365-app-certification/overview)
