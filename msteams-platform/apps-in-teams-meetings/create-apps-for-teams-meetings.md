---
title: Pré-requisitos para aplicativos em reuniões do Teams
author: surbhigupta
description: Identificar pré-requisitos com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 9ac6e87a8f85d0e8d73c6bf58dd705a55f887f43
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720229"
---
# <a name="prerequisites-for-apps-in-teams-meetings"></a>Pré-requisitos para aplicativos em reuniões do Teams

Com aplicativos para Teams reuniões, você pode expandir os recursos de seus aplicativos no ciclo de vida da reunião. Antes de trabalhar com aplicativos para Teams reuniões, você deve cumprir os seguintes pré-requisitos:

* Saiba como desenvolver Teams aplicativos. Para obter mais informações sobre como desenvolver Teams aplicativo, [consulte Teams desenvolvimento de aplicativos.](../overview.md)

* Atualize o Teams de aplicativos para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Use seu aplicativo que oferece suporte a guias configuráveis no escopo de groupchat. Para obter mais informações, consulte [group chat scope and](../resources/schema/manifest-schema.md#configurabletabs) build a group [tab](../build-your-first-app/build-channel-tab.md).

* Acate as diretrizes Teams de design de guias gerais para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião. Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Suporte ao `groupchat` escopo para habilitar seu aplicativo em chats de pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar as tarefas de pré-reunião. Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou taxa
* Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` . Os parâmetros estão disponíveis como parte da atividade Teams SDK do cliente e bot. Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.

* A `Meeting Details` API deve ter um registro de bot e uma ID de bot. Requer o SDK de Bot para `TurnContext` obter .

* Para eventos de reunião em tempo real, você deve estar familiarizado com o objeto disponível por meio `TurnContext` do SDK bot. O objeto em contém a carga com o início e a `Activity` `TurnContext` hora de término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.

* Ter parâmetros `meetingId` , e na URL da API de `userId` `tenantId` reunião. Os parâmetros estão disponíveis como parte da atividade Teams SDK do cliente e bot. Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).

* Ter um registro de bot e ID na `GetParticipant` API para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Mantenha seu aplicativo atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, verifique o parâmetro de conclusão `bot Id` na `NotificationSignal` API.

* Tenha um registro de bot e uma ID de bot na `MeetingDetails` API. Requer o SDK de Bot para `TurnContext` obter .

* Familiarizar-se `TurnContext` com o objeto disponível por meio do SDK bot. O objeto em contém a carga com o início e a `Activity` `TurnContext` hora de término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.

Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião , , e que permitem acessar informações usando atributos e exibir conteúdo `GetUserContext` `GetParticipant` `NotificationSignal` `Meeting Details` relevante.

> [!NOTE]
> Teams SDK JavaScript (_Versão_: 1.10 e posterior) para que o SSO funcione no painel do lado da reunião.

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para Teams reuniões](teams-apps-in-meetings.md)

## <a name="next-step"></a>Próxima Etapa

> [!div class="nextstepaction"]
> [Referências à API de aplicativos de reunião](API-references.md)
