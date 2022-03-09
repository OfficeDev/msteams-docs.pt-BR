---
title: Bots de chamadas e reuniões online
description: Saiba como seus aplicativos Microsoft Teams podem interagir com usuários usando voz e vídeo usando APIs do Microsoft Graph para chamadas e reuniões online e saiba mais sobre fluxos de mídia em tempo real
ms.topic: conceptual
ms.localizationpriority: medium
keywords: chamadas de chamadas de áudio vídeo IVR voz online reuniões em tempo real fluxos de mídia bot
ms.openlocfilehash: a0172bff6487da25ff7d482a24fa797f97b049b6
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398670"
---
# <a name="calls-and-online-meetings-bots"></a>Bots de chamadas e reuniões online

Os bots podem interagir com Teams e reuniões usando o compartilhamento de voz, vídeo e tela em tempo real. Com [as APIs Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true) microsoft para chamadas e reuniões online, Teams aplicativos agora podem interagir com os usuários usando voz e vídeo para aprimorar a experiência. Essas APIs permitem adicionar os seguintes novos recursos:

* Resposta de voz interativa (IVR).
* Controle de chamada.
* Acesso a fluxos de áudio e vídeo em tempo real, incluindo o compartilhamento de aplicativos e área de trabalho.

Para usar essas GRAPH APIs em um aplicativo Teams, crie um bot e especifique algumas informações e permissões adicionais.

Além disso, a Plataforma de Mídia em tempo real permite que os bots interajam com Teams chamadas e reuniões usando compartilhamento de voz, vídeo e tela em tempo real. Um bot que participa de chamadas de áudio ou vídeo e reuniões online é um bot Microsoft Teams com poucos recursos extras usados para registrar o bot.

O Teams `supportsCalling` `supportsVideo`de aplicativo com duas configurações adicionais e , Graph permissões para a ID do aplicativo Microsoft do bot e o consentimento do administrador do locatário permitem que você registre o bot. Ao registrar um bot de chamadas e reuniões para Teams, a URL do Webhook é mencionada, que é o ponto de extremidade de webhook para todas as chamadas de entrada para seu bot. Um bot de mídia hospedado por aplicativo requer a Microsoft. Graph. Biblioteca Communications.Calls.Media .NET para acessar os fluxos de mídia de áudio e vídeo, e o bot deve ser implantado em uma máquina do Windows Server ou no sistema operacional convidado do Windows Server no Azure. Os bots no Teams suportam apenas um conjunto específico de formatos de mídia para conteúdo de áudio e vídeo.

Agora, você deve entender alguns conceitos principais, terminologia e convenções.

## <a name="terminologies"></a>Terminologias

Os principais conceitos, terminologia e convenções a seguir orientam você pelo uso de chamadas e bots de reuniões online:

* Chamadas de áudio ou vídeo
* Tipos de chamadas
* Sinais
* Chamadas e reuniões online
* Mídia em tempo real

### <a name="audio-or-video-calls"></a>Chamadas de áudio ou vídeo

As chamadas Teams podem ser somente áudio ou áudio e vídeo. Em vez de chamada de áudio ou vídeo, a chamada de termo é usada.

### <a name="call-types"></a>Tipos de chamadas

As chamadas são ponto a ponto entre uma pessoa e seu bot ou várias partes entre seu bot e duas ou mais pessoas em uma chamada de grupo.

![Tipos de chamada](~/assets/images/calls-and-meetings/call-types.png)

A seguir estão os diferentes tipos de chamada e permissões necessárias para a chamada:

* Um usuário pode iniciar uma chamada ponto a ponto com seu bot ou convidar seu bot para uma chamada multipartidária existente. A chamada de várias partes ainda não está habilitada na interface Teams usuário.

    > [!NOTE]
    > Atualmente, as chamadas iniciadas pelo usuário para um bot não são suportadas Microsoft Teams plataforma móvel.

* Graph permissões não são necessárias para que um usuário inicie uma chamada ponto a ponto com seu bot. Permissões adicionais são necessárias para o bot participar de uma chamada de várias partes ou para que o bot inicie uma chamada ponto a ponto com um usuário.
* Uma chamada pode começar como ponto a ponto e, eventualmente, se tornar uma chamada de várias partes. Seu bot pode iniciar chamadas de várias partes convidando outras pessoas, desde que seu bot tenha as permissões adequadas. Se o bot não tiver permissões para participar de chamadas de grupo e se um participante adiciona outro participante à chamada, seu bot será descartado da chamada.

### <a name="signals"></a>Sinais

Há dois tipos de sinais, chamada de entrada e chamada. A seguir estão os diferentes recursos de sinais:

* Para receber uma chamada de entrada, insira um ponto de extremidade nas configurações do bot. Esse ponto de extremidade recebe uma notificação quando uma chamada de entrada é iniciada. Você pode atender a chamada, rejeitá-la ou redirecioná-la para outra pessoa.

    ![Tratamento de chamada](~/assets/images/calls-and-meetings/call-handling.png)

* Quando um bot está em uma chamada, há APIs para muting e desmuting do bot e para iniciar ou parar de compartilhar conteúdo de vídeo ou área de trabalho com outros participantes.
* O bot também pode acessar a lista de participantes, convidar novos participantes e silenciá-los.

### <a name="calls-and-online-meetings"></a>Chamadas e reuniões online

Na perspectiva Teams do usuário, há dois tipos de reuniões online, ad hoc e agendadas. Na perspectiva de um bot, ambas as reuniões online são as mesmas. Para um bot, uma reunião online é uma chamada de várias partes entre um conjunto de participantes e inclui coordenadas de reunião. As coordenadas de reunião são os metadados `botId`da reunião, incluindo , `chatId` associados à reunião, `joinUrl`ou `startTime` `endTime`, e assim por diante.

### <a name="real-time-media"></a>Mídia em tempo real

Quando um bot está participando de uma chamada ou reunião online, ele deve lidar com fluxos de áudio e vídeo. Quando os usuários falam em uma chamada, mostram a si mesmos em uma webcam ou apresentam suas telas em uma reunião para um bot que é mostrado como fluxos de áudio e vídeo. Se um bot quiser dizer algo tão simples quanto, pressione **0** para alcançar o operador em um cenário de resposta de voz interativa (IVR), ele requer a reprodução de um . Arquivo WAV. Coletivamente, isso é conhecido como mídia ou mídia em tempo real.

A mídia em tempo real refere-se a cenários em que a mídia deve ser processada em tempo real, em vez da reprodução de áudio ou vídeo gravado anteriormente. Lidar com fluxos de mídia, particularmente fluxos de mídia em tempo real, é extremamente complexo. A Microsoft criou a Plataforma de Mídia em tempo real para lidar com esses cenários e para descarregar o máximo possível da tradicional elevação pesada do processamento de mídia em tempo real. Quando o bot atende uma chamada de entrada ou instala uma chamada nova ou existente, ele precisa dizer à Plataforma de Mídia em tempo real como a mídia é manipulada. Se você estiver criando um aplicativo IVR, poderá descarregar o processamento de áudio caro para a Microsoft. Como alternativa, se o bot exigir acesso direto a fluxos de mídia, esse cenário também será suportado. Há dois tipos de processamento de mídia:

* **Mídia hospedada** pelo serviço: os bots se concentram no gerenciamento do fluxo de trabalho do aplicativo, como roteamento de chamadas e descarregamento de processamento de áudio para a Plataforma de Mídia em tempo real da Microsoft. Com a mídia hospedada pelo serviço, você tem várias opções para implementar e hospedar seu bot. Um bot mídia hospedada pelo serviço pode ser implementado como um serviço sem estado já que não processa mídia localmente. Os bots de mídia hospedados pelo serviço podem usar as seguintes APIs:

  * `PlayPrompt` para reprodução de um clipe de áudio.
  * `Record` para gravar clipes de áudio.
  * `SubscribeToTone` para assinar tons DTMF (dual tone multiple frequency).

    Por exemplo, saber quando um usuário pressionou **0** para alcançar o operador.

* **Mídia hospedada por aplicativo**: para que um bot tenha acesso direto à mídia, ele precisa de uma permissão Graph específica. Depois que o bot tiver a permissão, a Biblioteca de Mídia em tempo [real](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) e o [SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) de Graph de chamada ajudam você a criar mídia rica e em tempo real e chamar bots. Um bot hospedado pelo aplicativo deve estar hospedado em um ambiente Windows. Para obter mais informações, consulte [bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Graph** |
|---------------|----------|--------|
| Graph comunicação | Graph comunicações para interagir com a plataforma de comunicações da Microsoft. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |
| Bot de chamada e reunião | O exemplo de app demonesco começa como o Bot pode criar chamada, ingressar em reunião e transferir chamada. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-calling-meeting/csharp) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Chamadas de mídia e reuniões em tempo real](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Confira também

* [Graph api](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrar um bot que oferece suporte a chamadas e reuniões online](./registering-calling-bot.md)
* [Graph permissões para chamadas e bots de reuniões online](./registering-calling-bot.md#add-graph-permissions)
* [Como desenvolver bots de reunião online e de chamada em seu computador](./debugging-local-testing-calling-meeting-bots.md)
* [Requisitos e considerações para bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md)
* [Informações técnicas sobre como lidar com notificações de chamadas de entrada](./call-notifications.md)
