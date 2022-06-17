---
title: Bots de chamadas e reuniões online
description: Neste módulo, saiba como seus aplicativos Microsoft Teams podem interagir com usuários usando voz e vídeo usando APIs do Microsoft Graph para chamadas e reuniões online e saiba mais sobre fluxos de mídia em tempo real
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: bbeca082a561386d6c64d08e1d303975f9746f0a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143848"
---
# <a name="calls-and-online-meetings-bots"></a>Bots de chamadas e reuniões online

Os bots podem interagir com chamadas e reuniões do Teams usando voz, vídeo e compartilhamento de tela em tempo real. Com as [APIs do Microsoft Graph para chamadas e reuniões online](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true), os aplicativos do Teams agora podem interagir com os usuários usando voz e vídeo para aprimorar a experiência. Essas APIs permitem que você adicione os seguintes novos recursos:

* Resposta interativa de voz (IVR).
* Controle de chamadas.
* Acesso a fluxos de áudio e vídeo em tempo real, incluindo compartilhamento de desktop e aplicativo.

Para usar essas APIs do Graph em um aplicativo do Teams, crie um bot e especifique algumas informações e permissões adicionais.

Além disso, a plataforma de mídia em tempo real permite que os bots interajam com chamadas e reuniões do Teams usando voz, vídeo e compartilhamento de tela em tempo real. Um bot que participa de chamadas de áudio ou vídeo e reuniões online é um bot regular do Microsoft Teams com alguns recursos extras usados ​​para registrar o bot.

O manifesto do aplicativo Teams com duas configurações adicionais `supportsCalling` e `supportsVideo`, permissões do Graph para a ID do aplicativo Microsoft do bot e consentimento do administrador de locatários permitem que você registre o bot. Ao registrar um bot de chamadas e reuniões para o Teams, a URL do Webhook é mencionada, que é o ponto de extremidade do webhook para todas as chamadas de entrada para seu bot. Um bot de mídia hospedado pelo aplicativo requer a biblioteca .NET Microsoft.Graph.Communications.Calls.Media para acessar os fluxos de mídia de áudio e vídeo, e o bot deve ser implantado em um computador Windows Server ou sistema operacional convidado (SO) do Windows Server no Azure. Os bots no Teams dão suporte apenas a um conjunto específico de formatos de mídia para conteúdo de áudio e vídeo.

Agora, você deve entender alguns conceitos principais, terminologia e convenções.

## <a name="terminologies"></a>Terminologias

Os conceitos principais, a terminologia e as convenções a seguir orientam você pelo uso de chamadas e bots de reuniões online:

* Chamadas de áudio ou vídeo
* Tipos de chamadas
* Sinais
* Chamadas e reuniões online
* Mídia em tempo real

### <a name="audio-or-video-calls"></a>Chamadas de áudio ou vídeo

As chamadas no Teams podem ser puramente áudio ou áudio e vídeo. Em vez de chamada de áudio ou vídeo, a chamada de termo é usada.

### <a name="call-types"></a>Tipos de chamadas

As chamadas são ponto a ponto entre uma pessoa e seu bot ou várias partes entre o bot e duas ou mais pessoas em uma chamada em grupo.

:::image type="content" source="~/assets/images/calls-and-meetings/call-types.png" alt-text="Tipos de chamada"border="true":::

A seguir estão os diferentes tipos de chamada e permissões necessárias para a chamada:

* Um usuário pode iniciar uma chamada ponto a ponto com seu bot ou convidar seu bot para uma chamada multiparte existente. A chamada com várias partes ainda não está habilitada na interface do usuário do Teams.

    > [!NOTE]
    > Atualmente, não há suporte para chamadas iniciadas pelo usuário para um bot na plataforma móvel do Microsoft Teams.

* As permissões de grafo não são necessárias para que um usuário inicie uma chamada ponto a ponto com seu bot. Permissões adicionais são necessárias para o bot participar de uma chamada com várias partes ou para que o bot inicie uma chamada ponto a ponto com um usuário.
* Uma chamada pode começar como ponto a ponto e, eventualmente, se tornar uma chamada com várias partes. Seu bot pode iniciar chamadas com várias partes convidando outras pessoas, desde que seu bot tenha as permissões adequadas. Se o bot não tiver permissões para participar de chamadas em grupo e se um participante adicionar outro participante à chamada, o bot será removido da chamada.

### <a name="signals"></a>Sinais

Há dois tipos de sinais, chamada de entrada e em chamada. A seguir estão os diferentes recursos de sinais:

* Para receber uma chamada de entrada, insira um ponto de extremidade nas configurações do bot. Esse ponto de extremidade recebe uma notificação quando uma chamada de entrada é iniciada. Você pode atender à chamada, rejeitá-la ou redirecioná-la para outra pessoa.

     :::image type="content" source="~/assets/images/calls-and-meetings/call-handling.png" alt-text="Tratamento de chamadas"border="true":::

* Quando um bot está em uma chamada, há APIs para desativar e desativar o mudo do bot e para iniciar ou parar de compartilhar conteúdo de vídeo ou área de trabalho com outros participantes.
* O bot também pode acessar a lista de participantes, convidar novos participantes e silenciá-los.

### <a name="calls-and-online-meetings"></a>Chamadas e reuniões online

Da perspectiva de um usuário do Teams, há dois tipos de reuniões online, ad hoc e agendadas. Da perspectiva de um bot, ambas as reuniões online são as mesmas. Para um bot, uma reunião online é uma chamada com vários participantes entre um conjunto de participantes e inclui coordenadas de reunião. Coordenadas de reunião são os metadados da reunião, incluindo `botId`, `chatId` associados à reunião, `joinUrl`, `startTime` ou `endTime`e assim por diante.

### <a name="real-time-media"></a>Mídia em tempo real

Quando um bot está participando de uma chamada ou reunião online, ele deve lidar com fluxos de áudio e vídeo. Quando os usuários falam em uma chamada, se mostram em uma webcam ou apresentam suas telas em uma reunião, para um bot, isso é mostrado como fluxos de áudio e vídeo. Se um bot quiser dizer algo tão simples como **pressionar 0 para alcançar o operador** em um cenário de resposta de voz interativa (IVR), é necessário reproduzir um arquivo .WAV. Coletivamente, isso é conhecido como mídia ou mídia em tempo real.

A mídia em tempo real refere-se a cenários em que a mídia deve ser processada em tempo real, em vez da reprodução de áudio ou vídeo gravado anteriormente. Lidar com fluxos de mídia, especialmente fluxos de mídia em tempo real, é extremamente complexo. A Microsoft criou a Plataforma de Mídia em Tempo Real para lidar com esses cenários e descarregar o máximo possível do trabalho pesado tradicional de processamento de mídia em tempo real. Quando o bot responde a uma chamada de entrada ou ingressa em uma chamada nova ou existente, ele precisa informar à Plataforma de Mídia em tempo real como a mídia é tratada. Se você estiver criando um aplicativo IVR, poderá descarregar o processamento de áudio caro para a Microsoft. Como alternativa, se o bot exigir acesso direto a fluxos de mídia, esse cenário também será compatível. Há dois tipos de processamento de mídia:

* **Mídia hospedada pelo serviço**: os bots se concentram no gerenciamento do fluxo de trabalho do aplicativo, como roteamento de chamadas e descarregamento de processamento de áudio para a Plataforma de Mídia em Tempo Real da Microsoft. Com a mídia hospedada pelo serviço, você tem várias opções para implementar e hospedar seu bot. Um bot mídia hospedada pelo serviço pode ser implementado como um serviço sem estado já que não processa mídia localmente. Os bots de mídia hospedados pelo serviço podem usar as seguintes APIs:

  * `PlayPrompt` para reproduzir um clipe de áudio.
  * `Record` para gravar clipes de áudio.
  * `SubscribeToTone` para assinar tons de frequência múltipla de tom duplo (DTMF).

    Por exemplo, saber quando um usuário pressionou **0** para alcançar o operador.

* **Mídia hospedada pelo aplicativo**: para que um bot obtenha acesso direto à mídia, ele precisa de uma permissão específica do Graph. Depois que seu bot tiver a permissão, a [Biblioteca de Mídia em Tempo Real](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) e o [SDK de chamada do Graph](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/index.html#graph-calling-sdk-and-stateful-client-builder) ajudam você a criar mídia avançada em tempo real e bots de chamada. Um bot hospedado pelo aplicativo deve estar hospedado em um ambiente Windows. Para obter mais informações, [bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md).

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Graph** |
|---------------|----------|--------|
| Comunicação do Graph | Comunicações do Graph para interagir com a plataforma de comunicações da Microsoft. | [Exibir](https://github.com/microsoftgraph/microsoft-graph-comms-samples) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Chamadas de mídia e reuniões em tempo real](~/bots/calls-and-meetings/real-time-media-concepts.md)

## <a name="see-also"></a>Confira também

* [Referência da API do Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
* [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
* [Registrar um bot que dá suporte a chamadas e reuniões online](./registering-calling-bot.md)
* [Permissões do Graph para chamadas e bots de reuniões online](./registering-calling-bot.md#add-graph-permissions)
* [Como desenvolver bots de chamadas e reuniões online em seu computador](./debugging-local-testing-calling-meeting-bots.md)
* [Requisitos e considerações para bots de mídia hospedados pelo aplicativo](./requirements-considerations-application-hosted-media-bots.md)
* [Informações técnicas sobre como lidar com notificações de chamadas de entrada](./call-notifications.md)
* [Configurar um atendedor automático](/microsoftteams/create-a-phone-system-auto-attendant)
* [Configurar a resposta automática para Salas do Microsoft Teams em dispositivos de telefone com vídeo Android e Teams](/microsoftteams/set-up-auto-answer-on-teams-android)
* [Política de gravação do Teams](/MicrosoftTeams/teams-recording-policy)
* [Trabalhar com a API de comunicações no Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)
