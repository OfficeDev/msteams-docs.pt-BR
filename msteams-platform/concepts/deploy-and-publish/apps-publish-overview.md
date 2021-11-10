---
title: Visão geral - Distribuir seu aplicativo
description: Descreve as opções para publicar seu aplicativo Microsoft Teams, carregar seu aplicativo e GCC.
ms.topic: conceptual
author: KirtiPereira
ms.author: surbhigupta
ms.localizationpriority: none
keywords: implantar publicar o carregamento de aplicativo gcc
ms.openlocfilehash: 0436388365c2d7fc355c3f8cb40a9f05283124b8
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889185"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir seu Microsoft Teams app

Você pode fornecer seu Microsoft Teams para uma pessoa, equipe, organização ou qualquer pessoa que queira usá-lo. A distribuição depende de vários fatores, incluindo as necessidades dos usuários, os negócios, os requisitos técnicos e suas metas para o aplicativo.

## <a name="upload-your-app-in-teams"></a>Upload seu aplicativo no Teams

Fazer sideload de um aplicativo para uso pessoal, colaborar com sua equipe ou testar e depurar. Esse tipo de distribuição não exige um processo de revisão formal.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e Departamento de Defesa (DOD).

Para obter mais informações, [consulte upload your app in Teams](apps-upload.md).

## <a name="publish-your-app-to-your-org"></a>Publicar seu aplicativo em sua organização

Disponibilizar seu aplicativo para as pessoas em sua organização. Esse tipo de distribuição requer Teams aprovação do administrador.

Para obter mais informações, [consulte manage your apps in the Teams admin center](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2FMicrosoftTeams%2Fbreadcrumb%2Ftoc.json).

### <a name="government-community-cloud-gcc-organizations"></a>Nuvem da Comunidade Governamental (GCC)

Em GCC Teams ambientes, os aplicativos Microsoft compatíveis são habilitados por padrão. No entanto, antes de publicar um aplicativo, certifique-se de que todos os pontos de extremidade do aplicativo estão em conformidade com os requisitos da sua GCC da sua organização.

> [!IMPORTANT]
>Se seu aplicativo incluir um bot ou extensão de mensagens, você deverá selecionar a opção **Microsoft Teams** para Governo ao configurar um canal entre seu bot e Teams no Azure. Para obter mais informações, [consulte conectar um bot aos canais](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0&preserve-view=true).

## <a name="publish-your-app-to-the-teams-store"></a>Publicar seu aplicativo no Teams store

Disponibilizar seu aplicativo para todos. Esse tipo de distribuição requer aprovação da Microsoft.

Para obter mais informações, [consulte publish to the Teams store](~/concepts/deploy-and-publish/appsource/publish.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar as opções de instalação padrão do aplicativo](~/concepts/deploy-and-publish/add-default-install-scope.md)

## <a name="see-also"></a>Confira também

* [Programa de Conformidade de Aplicativos do Microsoft 365](/microsoft-365-app-certification/overview)
