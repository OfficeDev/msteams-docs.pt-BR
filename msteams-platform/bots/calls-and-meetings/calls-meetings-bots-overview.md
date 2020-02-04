---
title: Chamadas e bots de reuniões online
description: Saiba como os aplicativos do Microsoft Teams podem interagir com usuários usando voz e vídeo usando as APIs do Microsoft Graph para chamadas e reuniões online.
keywords: chamadas de chamada para o vídeo de áudio IVR de voz online
ms.openlocfilehash: 03bd7e085908a49f070fe84aba87138ecabafb83
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672620"
---
# <a name="calls-and-online-meetings-bots"></a>Chamadas e bots de reuniões online

Com a adição das [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta), os aplicativos do Microsoft Teams agora podem interagir com usuários de maneiras ricas usando voz e vídeo. Essas APIs permitem que você adicione novos recursos, como resposta de voz interativa (IVR), controle de chamadas e acesso a fluxos de áudio e/ou vídeo em tempo real para chamadas e reuniões, incluindo área de trabalho e compartilhamento de aplicativos.

Para usar essas APIs do Microsoft Graph em um aplicativo do Microsoft Teams, você cria um bot e especifica algumas informações adicionais e permissões que descreveremos em outros lugares, mas primeiro, é importante entender alguns conceitos principais, terminologia e convenções:

* **Chamadas de áudio/vídeo.** As chamadas no Teams podem ser puramente áudio ou áudio + vídeo. Para fins de brevidade, não dizem "chamada de áudio/vídeo" em qualquer lugar; apenas dizemos "Call".
* **Tipos de chamada.** As chamadas são ponto a ponto (entre uma pessoa e seu bot) ou multiparty (seu bot e duas ou mais pessoas em uma chamada de grupo).
  ![Tipos](~/assets/images/calls-and-meetings/call-types.png)de chamada:
  * Um usuário pode iniciar uma chamada ponto a ponto com seu bot ou convidar seu bot para uma chamada de vários participantes existente (embora o último ainda não esteja habilitado na interface do usuário do Microsoft Teams).
  * As permissões do Microsoft Graph não são necessárias para um usuário iniciar uma chamada ponto a ponto com seu bot, mas as permissões adicionais são necessárias para que seu bot participe de uma chamada de vários participantes ou para que o bot inicie uma chamada ponto a ponto com um usuário.
  * Uma chamada pode começar como ponto-a-ponto e escalar para vários participantes. Seu bot pode iniciar esse escalonamento convidando outros, contanto que seu bot tenha as permissões adequadas. Se o seu bot não tiver permissões para participar de chamadas de grupo e um participante adicionar outra parte, seu bot será descartado da chamada.
* **Sinalização.** Há dois tipos de sinais: chamada de entrada e em chamada:
  * Para receber uma chamada de entrada, especifique um ponto de extremidade nas suas configurações de bot; Este ponto de extremidade recebe uma notificação quando chega uma chamada de entrada. Você pode responder à chamada, rejeitá-la ou redirecioná-la para qualquer lugar ou outra pessoa.
  ![Tipos de chamada](~/assets/images/calls-and-meetings/call-handling.png)
  * Quando um bot está em uma chamada, há APIs para ativar mudo e desativação e para iniciar/parar o compartilhamento do conteúdo de vídeo/área de trabalho com outros participantes.
  * O bot também pode acessar a lista de participantes, convidar novos participantes e mudo para eles.
* **Chamadas e reuniões online.** Da perspectiva de um usuário do Team, há dois tipos de reuniões online: ad hoc e agendado. No entanto, da perspectiva de um bot, é diferente. Para um bot, uma reunião online é apenas uma chamada de várias partes (o conjunto de participantes) mais "coordenadas da reunião", que você pode considerar como os `botId`metadados da reunião:, `chatId` associado à reunião, `joinUrl` `startTime` / `endTime`e mais.
* **Mídia em tempo real.** Quando um bot está participando em uma chamada ou reunião online, ele deve lidar com fluxos de áudio e vídeo. Quando os usuários falam em uma chamada, aparecem em uma webcam ou apresentam suas telas em uma reunião, um bot "vê" isso como áudio e/ou fluxos de vídeo. Se um bot quiser dizer algo ou apresentar conteúdo de tela, que requer um fluxo de áudio ou vídeo. Até mesmo algo tão simples quanto o bot dizendo, "Pressione 0 para chegar ao operador" em um cenário IVR (resposta de voz interativa) significa reproduzir um. Arquivo WAV. Coletivamente, vamos nos referir a _isso como mídia_ ou _mídia em tempo real_ (ao fazer referência a cenários em que a mídia deve ser processada em tempo real, em vez de reproduzir o áudio/vídeo gravado anteriormente). Historicamente, lidar com fluxos de mídia, especialmente fluxos de mídia em tempo real, é extremamente complexo para os desenvolvedores. A Microsoft criou a _plataforma de mídia em tempo real_ para lidar com esses casos de uso e para descarregar o máximo possível de "trabalho pesado" do processamento de mídia em tempo real.  Quando o bot responde a uma chamada recebida, ou se junta a uma chamada nova ou existente, ele precisa informar o RealTime Media Platform como a mídia será tratada. Se você estiver criando um aplicativo de IVR, poderá transferir o alto processamento de áudio para a Microsoft. Como alternativa, se o seu bot requer acesso direto a fluxos de mídia, oferecemos suporte a esse cenário também. Há dois tipos de processamento de mídia:
  * **Mídia hospedada pelo serviço.** O foco dos bots no gerenciamento do fluxo de trabalho do aplicativo (por exemplo, chamadas de roteamento) e o processamento de áudio para a plataforma de mídia em tempo real da Microsoft. Com a mídia hospedada em serviço, você tem várias opções para implementar e hospedar o bot. Um bot de mídia hospedado pelo serviço pode ser implementado como um serviço sem monitoração de estado, pois ele não processa mídias localmente. Os `PlayPrompt` bots de mídia hospedados pelo serviço podem usar APIs como reproduzir um clipe de `Record` áudio, para gravar clipes `SubscribeToTone` de áudio ou inscrever-se em tons DTMF (por exemplo, saber quando um usuário pressionou 0 para chegar ao operador).
  * **Mídia hospedada por aplicativo.** Para que um bot obtenha acesso direto à mídia, ela precisa de uma permissão de gráfico específica, mas depois que seu bot o tiver, a [biblioteca de mídia em tempo real](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) e o [SDK de chamada de gráfico](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) ajudam a criar mídias ricas e em tempo real, ligando para bots. Um bot hospedado por aplicativo deve ser hospedado em um ambiente do Windows, conforme descrito em mais detalhes [aqui](./requirements-considerations-application-hosted-media-bots.md).

## <a name="further-reading"></a>Leitura adicional

Veja mais informações sobre como criar e testar chamadas e bots de reuniões online:

* [Referência da API do Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta)
* [Exemplos de aplicativos](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrar um bot que oferece suporte a chamadas e reuniões online](./registering-calling-bot.md) e [permissões do Microsoft Graph para chamadas e bots de reuniões online](/registering-calling-bot.md#add-microsoft-graph-permissions)
* [Como desenvolver as chamadas e bots de reunião online no computador local](./debugging-local-testing-calling-meeting-bots.md)
* [Obter mais informações sobre processamento de mídia em tempo real](./real-time-media-concepts.md)e [o que é necessário para dar suporte a mídia hospedada por aplicativos](./requirements-considerations-application-hosted-media-bots.md)
* [Informações técnicas sobre como lidar com notificações de chamada de entrada](./call-notifications.md)
