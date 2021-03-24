---
title: Bots de Chamadas e Reuniões Online
description: Saiba como seus aplicativos do Microsoft Teams podem interagir com usuários usando voz e vídeo usando APIs do Microsoft Graph para chamadas e reuniões online.
keywords: chamadas de chamadas de vídeo de áudio reuniões de voz IVR online
ms.openlocfilehash: 0fcf420ba8d698404d00bb2cab3d61cab2245f40
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034639"
---
# <a name="calls-and-online-meetings-bots"></a>Bots de chamadas e reuniões online

Com a adição de APIs do Microsoft Graph para chamadas e reuniões [online,](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)os aplicativos do Microsoft Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem adicionar novos recursos, como ivr (resposta de voz interativa), controle de chamada e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo o compartilhamento de área de trabalho e aplicativos.

Para usar essas APIs do Microsoft Graph em um aplicativo do Microsoft Teams, crie um bot e especifique algumas informações adicionais e permissões que descreveremos em outro lugar, mas primeiro, é importante compreender alguns conceitos, terminologia e convenções principais:

* **Chamadas de áudio/vídeo.** As chamadas no Teams podem ser puramente áudio ou áudio+vídeo. Por uma questão de brevidade, não dizemos "chamada de áudio/vídeo" em todos os lugares; apenas dizemos "chamada".
* **Tipos de chamada.** As chamadas são ponto a ponto (entre uma pessoa e seu bot) ou multiparte (seu bot e duas ou mais pessoas em uma chamada de grupo).
  ![CallingTypes ](~/assets/images/calls-and-meetings/call-types.png) :
  * Um usuário pode iniciar uma chamada ponto a ponto com seu bot ou convidar seu bot para uma chamada multipartidária existente (embora a última ainda não tenha habilitada na interface do usuário do Microsoft Teams).
  
  > [!NOTE]
  > No momento, as chamadas iniciadas pelo usuário para um bot não são suportadas na plataforma móvel do Microsoft Teams. 
  
  * As permissões do Microsoft Graph não são necessárias para que um usuário inicie uma chamada ponto a ponto com seu bot, mas são necessárias permissões adicionais para o bot participar de uma chamada de várias partes ou para que o bot inicie uma chamada ponto a ponto com um usuário.
  * Uma chamada pode começar como ponto a ponto e escalonar para várias partes. Seu bot pode iniciar essa escalada convidando outras pessoas, desde que o bot tenha as permissões adequadas. Se o bot não tiver permissões para participar de chamadas de grupo e um participante adiciona outra parte, seu bot será descartado da chamada.
* **Sinalização.** Há dois tipos de sinais : chamada de entrada e chamada:
  * Para receber uma chamada de entrada, especifique um ponto de extremidade nas configurações do bot; esse ponto de extremidade recebe uma notificação quando uma chamada de entrada chega. Você pode atender a chamada, rejeitá-la ou redirecioná-la para algum lugar ou outra pessoa.
  ![Tipos de chamada](~/assets/images/calls-and-meetings/call-handling.png)
  * Quando um bot está em uma chamada, há APIs para muting e unmuting si mesmo e para iniciar/parar o compartilhamento de conteúdo de vídeo/área de trabalho com os outros participantes.
  * O bot também pode acessar a lista de participantes, convidar novos participantes e silenciá-los.
* **Chamadas e reuniões online.** Na perspectiva de um usuário do Teams, há dois tipos de reuniões online — ad hoc e agendadas. No entanto, da perspectiva de um bot, ambos são os mesmos. Para um bot, uma reunião online é apenas uma chamada multipartidário (o conjunto de participantes) mais "coordenadas de reunião", que você pode pensar como os metadados da reunião: , associados à reunião, , e muito `botId` `chatId` `joinUrl` `startTime` / `endTime` mais.
* **Mídia em tempo real.** Quando um bot está participando de uma chamada ou reunião online, ele deve lidar com fluxos de áudio e vídeo. Quando os usuários conversam em uma chamada, mostram a si mesmos em uma webcam ou apresentam suas telas em uma reunião, um bot "vê" isso como fluxos de áudio e/ou vídeo. Se um bot quiser dizer algo ou apresentar conteúdo de tela, isso requer um fluxo de áudio ou vídeo. Mesmo algo tão simples quanto o bot dizendo, "pressione 0 para alcançar o operador" em um cenário ivr (resposta de voz interativa) significa a reprodução de um . Arquivo WAV. Coletivamente, nos referimos a isso como mídia ou mídia em tempo _real_ (quando se refere a cenários em que a mídia deve ser processada em tempo real, em vez da reprodução de áudio/vídeo gravado anteriormente).  Historicamente, lidar com fluxos de mídia, particularmente fluxos de mídia em tempo real, tem sido extremamente complexo para desenvolvedores. A Microsoft criou a Plataforma de Mídia em tempo _real_ para lidar com esses casos de uso e para descarregar o máximo possível da "elevação pesada" tradicional do processamento de mídia em tempo real.  Quando o bot responde a uma chamada recebida, ou se junta a uma chamada nova ou existente, ele precisa informar o RealTime Media Platform como a mídia será tratada. Se você estiver criando um aplicativo IVR, poderá descarregar o processamento de áudio caro para a Microsoft. Como alternativa, se o bot exigir acesso direto a fluxos de mídia, também podemos dar suporte a esse cenário. Há os dois tipos de processamento de mídia:
  * **Mídia hospedada pelo serviço.** Os bots se concentram no gerenciamento do fluxo de trabalho do aplicativo (por exemplo, chamadas de roteamento) e descarregam o processamento de áudio para a Plataforma de Mídia em tempo real da Microsoft. Com a mídia hospedada pelo serviço, você tem várias opções para implementar e hospedar seu bot. Um bot de mídia hospedado pelo serviço pode ser implementado como um serviço sem estado, pois ele não processa mídia localmente. Os bots de mídia hospedados pelo serviço podem usar APIs como para reprodução de um clipe de áudio, para gravar clipes de áudio ou para assinar tons `PlayPrompt` `Record` DTMF (por exemplo, saber quando um usuário pressionou 0 para alcançar o `SubscribeToTone` operador).
  * **Mídia hospedada pelo aplicativo.** Para que um bot tenha acesso direto à mídia, ele precisa de uma permissão específica do Graph, mas depois que o bot a tiver, a Biblioteca de Mídia em tempo [real](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) e o [SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) de Chamada de Gráfico ajudam você a criar mídia rica e em tempo real, chamando bots. Um bot hospedado pelo aplicativo deve ser hospedado em um ambiente do Windows, conforme descrito em mais detalhes [aqui](./requirements-considerations-application-hosted-media-bots.md).

## <a name="further-reading"></a>Leitura posterior

Veja mais informações sobre como criar e testar chamadas e bots de reuniões online:

* [Referência da API do Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrar um bot que oferece suporte a chamadas e reuniões online](./registering-calling-bot.md) e permissões do Microsoft Graph para [bots de](./registering-calling-bot.md#add-microsoft-graph-permissions) chamadas e reuniões online
* [Como desenvolver bots de reunião online e de chamada no computador local](./debugging-local-testing-calling-meeting-bots.md)
* [Mais informações sobre o processamento](./real-time-media-concepts.md)de mídia em tempo real e o que é necessário para dar suporte à [mídia hospedada pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md)
* [Informações técnicas sobre como lidar com notificações de chamadas de entrada](./call-notifications.md)
