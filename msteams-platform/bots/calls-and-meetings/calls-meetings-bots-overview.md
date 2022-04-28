---
title: Chamadas e bots de reuniões online
description: Saiba como seus aplicativos Microsoft Teams podem interagir com os usuários usando voz e vídeo usando APIs do Microsoft Graph para chamadas e reuniões online e saiba mais sobre fluxos de mídia em tempo real
ms.topic: conceptual
ms.localizationpriority: medium
keywords: chamadas de chamadas de áudio vídeo IVR voz online reuniões em tempo real fluxos de mídia bot
ms.openlocfilehash: a7b9dbe81304e2556b8b8b868f1f9e29f8bba284
ms.sourcegitcommit: e40383d9081bf117030f7e6270140e6b94214e8b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65102492"
---
# <a name="calls-and-online-meetings-bots"></a>Chamadas e bots de reuniões online

Os bots podem interagir com Teams e reuniões usando voz, vídeo e compartilhamento de tela em tempo real. Com [as APIs do Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true) para chamadas e reuniões online, Teams aplicativos agora podem interagir com os usuários usando voz e vídeo para aprimorar a experiência. Essas APIs permitem que você adicione os seguintes novos recursos:

* IVR (resposta de voz interativa).
* Controle de chamada.
* Acesso a fluxos de áudio e vídeo em tempo real, incluindo compartilhamento de aplicativos e área de trabalho.

Para usar essas APIs Graph em um aplicativo Teams, crie um bot e especifique algumas informações e permissões adicionais.

Além disso, a Plataforma de Mídia em tempo real permite que os bots interajam com Teams e reuniões usando voz, vídeo e compartilhamento de tela em tempo real. Um bot que participa de chamadas de áudio ou vídeo e reuniões online é um bot Microsoft Teams regular com alguns recursos extras usados para registrar o bot.

O Teams `supportsCalling` `supportsVideo`manifesto do aplicativo com duas configurações adicionais e, Graph permissões para a ID do Aplicativo microsoft do bot e o consentimento do administrador do locatário permitem que você registre o bot. Ao registrar um bot de chamadas e reuniões para Teams, a URL do Webhook é mencionada, que é o ponto de extremidade do webhook para todas as chamadas de entrada para o bot. Um bot de mídia hospedado pelo aplicativo requer a Microsoft. Graph. A biblioteca .NET Communications.Calls.Media para acessar os fluxos de mídia de áudio e vídeo, e o bot deve ser implantado em um computador do Windows Server ou no sistema operacional convidado do Windows Server no Azure. Os bots Teams suporte apenas a um conjunto específico de formatos de mídia para conteúdo de áudio e vídeo.

Agora, você deve entender alguns conceitos principais, terminologia e convenções.

## <a name="terminologies"></a>Terminologias

Os seguintes conceitos principais, terminologia e convenções orientam você pelo uso de chamadas e bots de reuniões online:

* Chamadas de áudio ou vídeo
* Tipos de chamadas
* Sinais
* Chamadas e reuniões online
* Mídia em tempo real

### <a name="audio-or-video-calls"></a>Chamadas de áudio ou vídeo

As chamadas Teams podem ser apenas áudio ou áudio e vídeo. Em vez de chamada de áudio ou vídeo, a chamada de termo é usada.

### <a name="call-types"></a>Tipos de chamadas

As chamadas são ponto a ponto entre uma pessoa e seu bot ou são multiparte entre o bot e duas ou mais pessoas em uma chamada em grupo.

:::image type="content" source="~/assets/images/calls-and-meetings/call-types.png" alt-text="Tipos de chamada"border="true":::

A seguir estão os diferentes tipos de chamada e permissões necessárias para a chamada:

* Um usuário pode iniciar uma chamada ponto a ponto com seu bot ou convidar seu bot para uma chamada multiparte existente. A chamada de várias partes ainda não está habilitada na Teams do usuário.

    > [!NOTE]
    > Atualmente, não há suporte para chamadas iniciadas pelo usuário para um bot Microsoft Teams plataforma móvel.

* Graph permissões não são necessárias para que um usuário inicie uma chamada ponto a ponto com seu bot. Permissões adicionais são necessárias para o bot participar de uma chamada de várias partes ou para que o bot inicie uma chamada ponto a ponto com um usuário.
* Uma chamada pode começar como ponto a ponto e, eventualmente, se tornar uma chamada de várias partes. Seu bot pode iniciar chamadas de vários participantes convidando outras pessoas, desde que o bot tenha as permissões adequadas. Se o bot não tiver permissões para participar de chamadas em grupo e se um participante adicionar outro participante à chamada, o bot será removido da chamada.

### <a name="signals"></a>Sinais

Há dois tipos de sinais, chamada de entrada e em chamada. A seguir estão os diferentes recursos de sinais:

* Para receber uma chamada de entrada, insira um ponto de extremidade nas configurações do bot. Esse ponto de extremidade recebe uma notificação quando uma chamada de entrada é iniciada. Você pode atender a chamada, rejeitá-la ou redirecioná-la para outra pessoa.

     :::image type="content" source="~/assets/images/calls-and-meetings/call-handling.png" alt-text="Tratamento de chamadas"border="true":::

* Quando um bot está em uma chamada, há APIs para desativar e desativar o bot e iniciar ou parar de compartilhar conteúdo de vídeo ou área de trabalho com outros participantes.
* O bot também pode acessar a lista de participantes, convidar novos participantes e silenciá-los.

### <a name="calls-and-online-meetings"></a>Chamadas e reuniões online

Da perspectiva Teams usuário, há dois tipos de reuniões online, ad hoc e agendadas. Da perspectiva de um bot, ambas as reuniões online são as mesmas. Para um bot, uma reunião online é uma chamada de várias partes entre um conjunto de participantes e inclui coordenadas de reunião. As coordenadas de reunião são `botId`os metadados da reunião, incluindo, `chatId` associados à reunião, `joinUrl``startTime` ou`endTime`, e assim por diante.

### <a name="real-time-media"></a>Mídia em tempo real

Quando um bot está participando de uma chamada ou reunião online, ele deve lidar com fluxos de áudio e vídeo. Quando os usuários falam em uma chamada, se mostram em uma webcam ou apresentam suas telas em uma reunião para um bot, ele é mostrado como fluxos de áudio e vídeo. Se um bot quiser dizer algo tão simples quanto, pressione **0** para alcançar o operador em um cenário de IVR (resposta de voz interativa), ele exigirá a reprodução de um . Arquivo WAV. Coletivamente, isso é chamado de mídia ou mídia em tempo real.

A mídia em tempo real refere-se a cenários em que a mídia deve ser processada em tempo real, em vez da reprodução de áudio ou vídeo gravado anteriormente. Lidar com fluxos de mídia, especialmente fluxos de mídia em tempo real, é extremamente complexo. A Microsoft criou a Plataforma de Mídia em tempo real para lidar com esses cenários e descarregar o máximo possível do trabalho pesado tradicional do processamento de mídia em tempo real. Quando o bot responde a uma chamada de entrada ou ingressa em uma chamada nova ou existente, ele precisa informar à Plataforma de Mídia em tempo real como a mídia é tratada. Se você estiver criando um aplicativo IVR, poderá descarregar o processamento de áudio caro para a Microsoft. Como alternativa, se o bot exigir acesso direto a fluxos de mídia, esse cenário também será compatível. Há dois tipos de processamento de mídia:

* **Mídia hospedada pelo** serviço: os bots se concentram no gerenciamento do fluxo de trabalho do aplicativo, como roteamento de chamadas e descarregamento de processamento de áudio para a Plataforma de Mídia em Tempo Real da Microsoft. Com a mídia hospedada pelo serviço, você tem várias opções para implementar e hospedar seu bot. Um bot mídia hospedada pelo serviço pode ser implementado como um serviço sem estado já que não processa mídia localmente. Os bots de mídia hospedados pelo serviço podem usar as seguintes APIs:

  * `PlayPrompt` para reproduzir um clipe de áudio.
  * `Record` para gravar clipes de áudio.
  * `SubscribeToTone` para assinar tons DTMF (dual tone multiple frequency).

    Por exemplo, saber quando um usuário pressionou **0** para alcançar o operador.

* **Mídia hospedada pelo aplicativo**: para que um bot obtenha acesso direto à mídia, ele precisa de uma permissão Graph específica. Depois que o bot tiver a permissão, a Biblioteca de Mídia em tempo [real](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) e o [SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) de Graph chamada ajudarão você a criar mídia avançada em tempo real e chamar bots. Um bot hospedado pelo aplicativo deve estar hospedado em um ambiente Windows. Para obter mais informações, consulte [bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Graph** |
|---------------|----------|--------|
| Graph comunicação | Graph comunicações para interagir com a plataforma de comunicações da Microsoft. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Chamadas de mídia e reuniões em tempo real](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Confira também

* [API do Graph referência](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrar um bot que dá suporte a chamadas e reuniões online](./registering-calling-bot.md)
* [Graph permissões para chamadas e bots de reuniões online](./registering-calling-bot.md#add-graph-permissions)
* [Como desenvolver bots de chamadas e reuniões online em seu computador](./debugging-local-testing-calling-meeting-bots.md)
* [Requisitos e considerações para bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md)
* [Informações técnicas sobre como lidar com notificações de chamada de entrada](./call-notifications.md)
* [Configurar um atendedor automático](/microsoftteams/create-a-phone-system-auto-attendant)
* [Configurar a resposta automática para Salas do Microsoft Teams em dispositivos de Teams Android e vídeo](/microsoftteams/set-up-auto-answer-on-teams-android)
* [Teams de gravação](/MicrosoftTeams/teams-recording-policy)