---
title: Chamadas de mídia em tempo real e reuniões online com o Microsoft Teams
description: Conheça os principais conceitos na criação de bots que podem conduzir chamadas de áudio e vídeo em tempo real e reuniões online.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b1ff14a0229483312c0de6fdb33836ee205f1e14
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143785"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Chamadas de mídia em tempo real e reuniões com Microsoft Teams

A Plataforma de Mídia em Tempo Real permite que os bots interajam com as chamadas e reuniões do Microsoft Teams usando voz, vídeo e compartilhamento de tela em tempo real. A Plataforma de Mídia em Tempo Real é um recurso avançado que permite que o bot envie e receba conteúdos de voz e vídeo quadro a quadro. O bot tem acesso bruto aos fluxos de mídia de voz, vídeo e compartilhamento de tela. Existem bots mais simples de mídia hospedada pelo serviço que dependem da Plataforma de Mídia em Tempo Real para todo o processamento de mídia. Os bots que processam mídia são chamados de bots de mídia hospedada pelo aplicativo.

Por exemplo, em uma chamada individual com um bot, enquanto o usuário fala, o bot recebe 50 quadros de áudio por segundo. O bot recebe os quadros de áudio com cada quadro de 20 milissegundos (ms) de áudio. Um bot de mídia hospedada pelo aplicativo pode fazer o reconhecimento de fala em tempo real à medida que os quadros de áudio são recebidos. Não é necessário esperar por uma gravação depois que o usuário tiver parado de falar. O bot também pode enviar e receber vídeos de alta definição, incluindo conteúdos de compartilhamento de tela baseado em vídeo.

A plataforma fornece uma API simples semelhante a um soquete para que o bot envie e receba mídia. Ele lida com a codificação e decodificação em tempo real de pacotes de áudio ou vídeo. Ele utiliza codecs como SILK e G.722 para áudio e H.264 para vídeo. A plataforma também manipula toda a criptografia ou descriptografia de pacotes de mídia e da transmissão de rede de pacotes. O bot só está preocupado com o conteúdo real de áudio ou vídeo. Um bot de mídia em tempo real participa de chamadas individuais e reuniões com vários participantes.

## <a name="media-session"></a>Sessão de mídia

Um bot de mídia em tempo real deve declarar quais modalidades ele deve suportar. O bot de mídia em tempo real deve declarar suporte ao responder a uma chamada recebida ou ingressar em uma reunião do Teams. Para cada modalidade suportada, o bot declara se pode enviar e receber mídia, receber apenas ou enviar apenas. Por exemplo, um bot projetado para lidar com chamadas individuais do Teams exige o envio e recebimento de áudio. Mas o bot precisa apenas enviar o vídeo, pois ele não precisa receber o vídeo do chamador. O conjunto de modalidades de áudio e vídeo estabelecido entre o bot e o chamador ou reunião do Teams é chamado de sessão de mídia.

Dois tipos de modalidades de vídeo são suportados, vídeo principal e compartilhamento de tela baseado em vídeo. O vídeo principal é usado para transportar o vídeo a partir da webcam de um usuário. O compartilhamento de tela baseado em vídeo permite ao usuário compartilhar a tela. A plataforma permite que um bot envie e receba os dois tipos de vídeo.

Ao participar de uma reunião do Teams, um bot pode receber vários fluxos de vídeos principais simultaneamente até 10 por sessão de mídia. O bot pode ver mais de um participante na reunião.

A próxima seção fornece detalhes sobre o bot enviando e recebendo mídia como uma sequência de quadros.

## <a name="frames-and-frame-rate"></a>Quadros e taxa de quadros

Um bot de mídia em tempo real interage diretamente com as modalidades de áudio e vídeo de uma sessão de mídia. O bot está enviando e recebendo mídia como uma sequência de quadros e cada quadro é uma unidade de conteúdo. Um segundo de áudio é transmitido como uma sequência de 50 quadros. Cada quadro contém 20 ms que é 1/50 de um segundo de conteúdo de fala. Um segundo de vídeo é transmitido como uma sequência de 30 imagens estáticas. Cada imagem deve ser visualizada por apenas 33,3 ms, ou seja, 1/30 de segundo antes do próximo quadro de vídeo. O número de quadros transmitidos ou renderizados por segundo é chamado de taxa de quadros.

A próxima seção fornece detalhes sobre o formato de áudio e vídeo usado em chamadas de mídia e reuniões em tempo real.

## <a name="audio-and-video-format"></a>Formato de áudio e vídeo

No formato de áudio, cada segundo de áudio é representado por 16.000 amostras, com cada amostra contendo 16 bits de dados. Um quadro de áudio de 20 ms contém 320 amostras que são 640 bytes de dados.

No formato de vídeo, vários formatos são suportados. Duas propriedades chave de um formato de vídeo são seu tamanho de quadro e formato de cor. Os tamanhos de quadro suportados incluem 640x360 ou seja, 360 pixels, 1280x720 ou seja, 720 pixels e 1920x1080 ou seja, 1080 pixels. Os formatos de cor suportados incluem NV12 que é de 12 bits por pixel e RGB24 que é de 24 bits por pixel.

Um quadro de vídeo de 720-p contém 921.600 pixels, ou seja, 1280 vezes 720. No formato de cor RGB24, cada pixel é representado por 3 bytes que são 24 bits, incluindo 1 byte de cada um dos componentes de cores vermelho, verde e azul. Um único quadro de vídeo RGB24 de 720p requer 2.764.800 bytes de dados, ou seja, 921.600 pixels vezes 3 bytes por pixel. Em uma taxa de quadros variável, o envio de quadros de vídeo RGB24 de 720p significa processar aproximadamente 80 megabytes por segundo de conteúdo. Os 80 megabytes são substancialmente compactados pelo codec de vídeo H.264 antes da transmissão de rede.

Uma funcionalidade avançada da plataforma permite que um bot envie ou receba vídeos como quadros H.264 codificados. Bots que fornecem seu próprio codificador ou decodificador H.264 são suportados, ou o fluxo de vídeo decodificado em mapas de bits RGB24 ou NV12 brutos não é necessário.

A próxima seção fornece detalhes sobre quais participantes da reunião estão falando, ou seja, quais são o palestrantes ativos e dominantes.

## <a name="active-and-dominant-speakers"></a>Palestrantes ativos e dominantes

Ao participar de uma reunião do Teams composta por vários participantes, um bot pode identificar quais participantes da reunião estão falando no momento. Os palestrantes ativos identificam quais participantes estão sendo ouvidos em cada quadro do áudio recebido. Os palestrantes dominantes identificam quais participantes são atualmente mais ativos ou dominantes na conversa em grupo, embora sua voz não seja ouvida em todos os quadros de áudio. O conjunto de palestrantes dominantes pode ser alterado à medida que diferentes participantes se revezam para falar.

A próxima seção fornece detalhes sobre as solicitações de assinatura de vídeo feitas por um bot.

## <a name="video-subscription"></a>Assinatura de vídeos

Em uma chamada individual, o bot recebe automaticamente o vídeo do chamador se o bot estiver habilitado para receber o vídeo. Em uma reunião do Teams, o bot deve indicar à plataforma quais participantes ele deseja ver. Uma assinatura de vídeo é uma solicitação feita pelo bot para receber o conteúdo principal de vídeo ou compartilhamento de tela de um participante. À medida que os participantes da reunião conduzem a conversa, o bot modifica as assinaturas de vídeo necessárias. O bot modifica as assinaturas de vídeo com base nas atualizações do conjunto dominante de palestrantes ou notificações que indicam qual participante está compartilhando a tela no momento.

A próxima seção fornece detalhes sobre o que você deve instalar e os requisitos para desenvolver um bot de mídia hospedada pelo aplicativo.

## <a name="developer-resources"></a>Recursos de desenvolvedor

Para desenvolver um bot de mídia hospedada pelo aplicativo, você deve instalar a [biblioteca Microsoft.Graph.Calls.Media .NET](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) do pacote NuGet no seu projeto do Visual Studio.

Os bots de mídia hospedada pelo aplicativo exigem .NET ou C# e o Windows Server. Para obter mais informações, consulte os [requisitos e considerações para bots de mídia hospedada pelo aplicativo](requirements-considerations-application-hosted-media-bots.md#c-or-net-and-windows-server-for-development).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Registrar um bot de chamada](~/bots/calls-and-meetings/registering-calling-bot.md)

## <a name="see-also"></a>Confira também

[Formatos de mídia com suporte para bots](~/resources/media-formats.md)
