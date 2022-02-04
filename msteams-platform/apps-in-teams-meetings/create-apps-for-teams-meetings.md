---
title: Pré-requisitos para aplicativos em reuniões do Teams
author: surbhigupta
description: Identificar pré-requisitos com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 4c42a66f7891691b8c53d61d1ce637d57048eae8
ms.sourcegitcommit: 54f6690b559beedc330b971618e574d33d69e8a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62362735"
---
# <a name="prerequisites-for-apps-in-teams-meetings"></a>Pré-requisitos para aplicativos em reuniões do Teams

Com aplicativos para Teams reuniões, você pode expandir os recursos de seus aplicativos no ciclo de vida da reunião. Antes de trabalhar com aplicativos para Teams reuniões, você deve cumprir os seguintes pré-requisitos:

* Saiba como desenvolver Teams aplicativos. Para obter mais informações sobre como desenvolver Teams aplicativo, [consulte Teams desenvolvimento de aplicativos](../overview.md).

* Atualize o Teams de aplicativos para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Use seu aplicativo que oferece suporte a guias configuráveis no escopo de groupchat. Para obter mais informações, consulte [group chat scope and](../resources/schema/manifest-schema.md#configurabletabs) [build a group tab](../build-your-first-app/build-channel-tab.md).

* Acate as diretrizes Teams de design de guias gerais para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião. Para obter mais informações, [consulte Teams](../tabs/design/tabs.md) diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) de guia na reunião e [diretrizes de design de caixa de diálogo na reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Suporte ao `groupchat` escopo para habilitar seu aplicativo em chats de pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar as tarefas de pré-reunião. Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou taxa
* Os parâmetros de URL da API de reunião devem ter `meetingId`, `userId`e `tenantId`. Os parâmetros estão disponíveis como parte da atividade Teams SDK do cliente e bot. Além disso, você pode recuperar informações confiáveis para iD de usuário e ID de locatário usando [autenticação SSO de tabulação](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.

* A `Meeting Details` API deve ter um registro de bot e uma ID de bot. Requer o SDK de Bot para obter `TurnContext`. Para usar a API de Detalhes da Reunião, você deve obter uma permissão RSC diferente com base no escopo de qualquer reunião, como reunião privada ou reunião de canal.

* Para eventos de reunião em tempo real, você deve estar familiarizado `TurnContext` com o objeto disponível por meio do SDK bot. O `Activity` objeto em `TurnContext` contém a carga com o início e a hora de término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams. O bot pode receber automaticamente o evento inicial ou final da reunião adicionando `ChannelMeeting.ReadBasic.Group` no manifesto.

* Ter parâmetros `meetingId`, `userId`e na URL da `tenantId` API de reunião. Os parâmetros estão disponíveis como parte da atividade Teams SDK do cliente e bot. Além disso, você pode recuperar informações confiáveis para iD de usuário e ID de locatário usando [autenticação SSO de tabulação](../tabs/how-to/authentication/auth-aad-sso.md).

* Ter um registro de bot e ID na `GetParticipant` API para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Mantenha seu aplicativo atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, verifique o parâmetro de conclusão `bot Id` na `NotificationSignal` API.

* Tenha um registro de bot e uma ID de bot na `MeetingDetails` API. Requer o SDK de Bot para obter `TurnContext`.

* Familiarizar-se com `TurnContext` o objeto disponível por meio do SDK bot. O `Activity` objeto em `TurnContext` contém a carga com o início e a hora de término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.

Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos `GetUserContext`de reunião , `GetParticipant`, e `NotificationSignal``Meeting Details` que permitem acessar informações usando atributos e exibir conteúdo relevante.

> [!NOTE]
> Teams SDK JavaScript (_versão_: 1.10 e posterior) para que o SSO funcione no painel do lado da reunião.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para reuniões do Teams](teams-apps-in-meetings.md)
* [Teams da API de bot para buscar membros de equipe ou chat](~/resources/team-chat-member-api-changes.md)
