---
title: Aplicativos para reuniões do Teams
author: surbhigupta
description: Neste artigo, saiba como os aplicativos funcionam em reuniões do Microsoft Teams com base na extensibilidade de aplicativos e funções de usuário e participantes.
ms.topic: overview
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: b62c2312524c1844b9b40b32d2d21ecdd2db43dc
ms.sourcegitcommit: 08bd7f1b9c654b95d3639ca88052c9ca9a8c3f67
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67833652"
---
# <a name="apps-for-teams-meetings-and-calls"></a>Aplicativos para reuniões e chamadas do Teams

As reuniões permitem colaboração, parceria, comunicação informada e comentários compartilhados. O aplicativo de reunião pode fornecer uma experiência do usuário em cada estágio do ciclo de vida da reunião. O ciclo de vida da reunião inclui a experiência de aplicativo de pré-reunião, em reunião e pós-reunião, dependendo do status do participante.

> [!Note]
>
> No momento, os aplicativos para reuniões instantâneas, reuniões de canal público agendadas, um para um e chamadas de grupo estão disponíveis apenas na versão prévia [do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md).

O Teams dá suporte ao acesso a aplicativos durante a reunião para os seguintes tipos de reunião:

* [**Reuniões agendadas**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): reuniões agendadas por meio do calendário do Teams.
* [**Reuniões de canal agendadas**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): reuniões agendadas por meio de canais públicos do Teams.
* [**Chamadas um-a-um**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): chamadas iniciadas em chat um-a-um.
* [**Chamadas em grupo**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): chamadas iniciadas no chat em grupo.
* [**Reuniões instantâneas**](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5): reuniões iniciadas **por meio do botão Reunir agora** no calendário do Teams.

Os usuários podem adicionar aplicativos à reunião usando a **+** opção na janela de reunião do Teams.

:::image type="content" source="../assets/images/apps-in-meetings/add-app.png" alt-text="Adicionar um aplicativo na reunião" border="true":::

Visite a [loja do Teams e](https://go.microsoft.com/fwlink/p/?LinkID=2183121) explore os aplicativos projetados especificamente para reuniões.

> [!Note]
>
> * Atualmente, não há suporte para a adição de um aplicativo em dispositivos móveis. No entanto, um usuário pode exibir o aplicativo e compartilhar o aplicativo para preparar a partir do celular.
>
> * Atualmente, quando uma terceira pessoa é adicionada a uma chamada um-a-um, a chamada é elevada a uma chamada de grupo que significa que uma nova sessão é iniciada. Os aplicativos adicionados à chamada um-a-um não estão disponíveis na chamada de grupo. No entanto, eles podem ser adicionados novamente.
>
> * Atualmente, não há suporte para experiências de aplicativo em reuniões de canal instantâneo do Teams.

A ilustração a seguir fornece a você uma ideia dos recursos de extensibilidade do aplicativo de reuniões:

![Extensibilidade do aplicativo de reunião](../assets/images/apps-in-meetings/meetingappextensibility.png)

Este artigo fornece uma visão geral da extensibilidade do aplicativo de reuniões, referências de API, habilitar e configurar aplicativos para reuniões e cenas personalizadas do Modo Conferência no Teams.

* **Estender o aplicativo de reunião**: aprimora sua experiência de reunião usando o recurso de extensibilidade de reunião. Esse recurso permite que você integre seus aplicativos nas reuniões. Ele também inclui diferentes estágios do ciclo de vida de uma reunião, em que você pode integrar guias, bots e extensões de mensagens. Você pode identificar várias funções de participantes e tipos de usuário, obter eventos de reunião e gerar diálogos de reunião.
* **Configurar aplicativos para reuniões**: para personalizar o Teams com aplicativos para reuniões, habilite seus aplicativos para reuniões do Teams atualizando o manifesto do aplicativo e também configure os aplicativos para cenários de reunião.
* **Personalizar com cenas do Modo Juntos**: o novo recurso personalizado cenas modo juntos permite que os usuários colaborem em uma reunião com sua equipe em um só lugar.
* **Personalizar a permissão do aplicativo no canal compartilhado**: se seu aplicativo compartilhar informações importantes no canal compartilhado, você poderá personalizar a permissão do aplicativo para membros externos. As permissões de aplicativo em [canais compartilhados](../concepts/build-and-test/Shared-channels.md) seguem a lista de aplicativos da equipe host e a política de aplicativo do locatário do host.
* **Recuperar transcrições de** reunião: você pode acessar e recuperar transcrições de reunião em um cenário pós-reunião. Configure seu aplicativo para obter transcrições automaticamente para uma reunião agendada e use-as para insights, análise inteligente e muito mais.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Aplicativos de reuniões unificadas](meeting-app-extensibility.md)

## <a name="see-also"></a>Confira também

* [Projetando sua extensão de reunião do Microsoft Teams](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Referências da API de aplicativos de reunião - Microsoft Teams](~/apps-in-teams-meetings/api-references.md)
* [Cenas personalizadas do Modo Conferência](~/apps-in-teams-meetings/teams-together-mode.md)
* [Ative e configure seus aplicativos para reuniões do Teams](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
* [Ciclo de vida da reunião](meeting-app-extensibility.md#meeting-lifecycle)
* [Colaboração aprimorada com o SDK do Live Share](teams-live-share-overview.md)
