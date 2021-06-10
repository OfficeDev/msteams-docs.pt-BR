---
title: Chamadas de mídia em tempo real e reuniões online com Microsoft Teams
description: Entenda os principais conceitos na criação de bot que podem conduzir chamadas de áudio e vídeo em tempo real e reuniões online.
ms.topic: conceptual
localization_priority: Normal
keywords: áudio stream vídeo stream audio/video calling meeting real-time media application-hosted media service-hosted media hosted media
ms.openlocfilehash: deedc47f67fe6848cf7f84457247d2271257e3f0
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020152"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Chamadas de mídia em tempo real e reuniões com Microsoft Teams

A Plataforma de Mídia em tempo real permite que os bots interajam com Microsoft Teams chamadas e reuniões usando compartilhamento de voz, vídeo e tela em tempo real. Esse é um recurso avançado que permite que o bot envie e receba conteúdo de voz e vídeo quadro a quadro. O bot tem acesso bruto aos fluxos de mídia de compartilhamento de voz, vídeo e tela. Há bots de mídia hospedados por serviço mais simples que dependem da Plataforma de Mídia em tempo real para todo o processamento de mídia. Os bots que processam a mídia por conta própria são chamados de bots de mídia hospedados pelo aplicativo.

Por exemplo, em uma chamada 1:1 com um bot, como o usuário fala, o bot recebe 50 quadros de áudio por segundo, com cada quadro contendo 20 milissegundos (ms) de áudio. Um bot de mídia hospedado por aplicativo pode executar o reconhecimento de fala em tempo real à medida que os quadros de áudio são recebidos, em vez de ter que esperar por uma gravação depois que o usuário parou de falar. O bot também pode enviar e receber vídeo de alta resolução, incluindo conteúdo de compartilhamento de tela baseado em vídeo.

A plataforma fornece uma API simples como soquete para o bot enviar e receber mídia. Ele lida com a codificação em tempo real e a decodificação de pacotes de áudio ou vídeo usando codecs como SILK e G.722 para áudio e H.264 para vídeo. A plataforma também lida com toda a criptografia de pacotes de mídia ou descriptografia e transmissão de rede de pacotes automaticamente. O bot só está preocupado com o conteúdo real de áudio ou vídeo. Um bot de mídia em tempo real participa de chamadas 1:1, bem como reuniões com vários participantes.

## <a name="media-session"></a>Sessão de mídia

Quando um bot de mídia em tempo real responde a uma chamada de entrada ou inscreves em uma reunião Teams, ele deve declarar quais modalidades ele deve dar suporte. Para cada modalidade suportada, o bot declara se pode enviar e receber mídia, receber somente ou enviar somente. Por exemplo, um bot projetado para lidar com chamadas de 1:1 Teams, exige enviar e receber áudio, mas apenas enviar vídeo, pois não é necessário receber o vídeo do chamador. O conjunto de modalidades de áudio e vídeo estabelecidas entre o bot e o Teams chamador ou reunião é chamado de sessão de mídia.

Há suporte para dois tipos de modalidades de vídeo, vídeo principal e compartilhamento de tela baseado em vídeo. O vídeo principal é usado para transportar o vídeo da webcam de um usuário. O compartilhamento de tela baseado em vídeo permite que um usuário compartilhe sua tela como um fluxo de vídeo. A plataforma permite que um bot envie e receba ambos os tipos de vídeo.

Quando ingressado em uma reunião Teams, um bot pode receber vários fluxos de vídeo principais simultaneamente até dez por sessão de mídia. Isso permite que o bot veja mais de um participante na reunião.

A próxima seção fornece detalhes sobre o bot enviando e recebendo mídia como uma sequência de quadros.

## <a name="frames-and-frame-rate"></a>Quadros e taxa de quadros

Um bot de mídia em tempo real interage diretamente com as modalidades de áudio e vídeo de uma sessão de mídia. Isso significa que o bot está enviando e recebendo mídia como uma sequência de quadros, onde cada quadro representa uma unidade de conteúdo. Um segundo de áudio é transmitido como uma sequência de 50 quadros, com cada quadro contendo 20 ms que seja 1/50 de um segundo de conteúdo de fala. Um segundo do vídeo é transmitido como uma sequência de 30 imagens ainda, cada uma delas destinada a ser exibida por apenas 33,3 ms que é 1/30 de segundo antes que o próximo quadro de vídeo seja exibido. O número de quadros transmitidos ou renderizados por segundo é chamado de taxa de quadros.

A próxima seção fornece detalhes sobre o formato de áudio e vídeo usado em chamadas e reuniões de mídia em tempo real.

## <a name="audio-and-video-format"></a>Formato de áudio e vídeo

No formato de áudio, cada segundo de áudio é representado como 16.000 amostras, com cada amostra contendo 16 bits de dados. Um quadro de áudio de 20 ms contém 320 amostras que são 640 bytes de dados.

No formato de vídeo, há suporte para vários formatos. Duas propriedades principais de um formato de vídeo são o tamanho do quadro e o formato de cor. Os tamanhos de quadros com suporte incluem 640x360 que é 360 pixels, 1280x720 que é 720 pixels e 1920x1080 que é 1080 pixels. Os formatos de cores com suporte incluem NV12 que é 12 bits por pixel e RGB24 que é 24 bits por pixel.

Um quadro de vídeo de 720p contém 921.600 pixels que é 1280 vezes 720. No formato de cor RGB24, cada pixel é representado como 3 bytes que são 24 bits compostos por um byte cada um dos componentes de cor vermelho, verde e azul. Portanto, um único quadro de vídeo RGB24 de 720p requer 2.764.800 bytes de dados que são 921.600 pixels vezes 3 bytes por pixel. A uma taxa de quadros de 30 fps, enviar quadros de vídeo RGB24 de 720p significa processar aproximadamente 80 megabytes por segundo de conteúdo, que é substancialmente compactado pelo codec de vídeo H.264 antes da transmissão da rede.

Um recurso avançado da plataforma permite que um bot envie ou receba vídeo como quadros H.264 codificados. Isso dá suporte a bots que fornecem seu próprio codificador ou decodificador H.264 ou não exigem o fluxo de vídeo decodificado em bitmaps RGB24 ou NV12 brutos.

A próxima seção fornece detalhes sobre quais participantes da reunião estão falando que são falantes ativos e dominantes.

## <a name="active-and-dominant-speakers"></a>Alto-falantes ativos e dominantes

Quando ingressado em uma reunião Teams que consiste em vários participantes, um bot pode identificar quais participantes da reunião estão atualmente falando. Os alto-falantes ativos identificam quais participantes estão sendo ouvidos em cada quadro de áudio recebido. Os alto-falantes dominantes identificam quais participantes estão mais ativos ou dominantes na conversa de grupo, mesmo que sua voz não seja ouvida em todos os quadros de áudio. O conjunto de alto-falantes dominantes pode mudar à medida que diferentes participantes se revezam falando.

A próxima seção fornece detalhes sobre solicitações de assinatura de vídeo feitas por um bot.

## <a name="video-subscription"></a>Assinatura de vídeo

Em uma chamada 1:1, o bot recebe automaticamente o vídeo do chamador se o bot estiver habilitado para receber o vídeo. Em uma Teams, o bot deve indicar para a plataforma quais participantes ele deseja ver. Uma assinatura de vídeo é uma solicitação do bot para receber o conteúdo principal de vídeo ou compartilhamento de tela de um participante. À medida que os participantes da reunião conduzem suas conversas, o bot modifica suas assinaturas de vídeo desejadas com base nas atualizações do conjunto de alto-falantes dominante ou nas notificações indicando qual participante está compartilhamento de tela no momento.

A próxima seção fornece detalhes sobre o que você deve instalar e os requisitos para desenvolver um bot de mídia hospedado pelo aplicativo.

## <a name="developer-resources"></a>Recursos de desenvolvedor

Para desenvolver um bot de mídia hospedado por aplicativo, você deve instalar o [Microsoft.Graph. Biblioteca Calls.Media .NET NuGet](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) pacote em seu Visual Studio projeto.

Os bots de mídia hospedados pelo aplicativo exigem .NET ou C# e Windows Server. Para obter mais informações, consulte [requisitos e considerações para bots de mídia hospedados pelo aplicativo.](requirements-considerations-application-hosted-media-bots.md#c-or-net-and-windows-server-for-development)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Registrar um bot de chamada](~/bots/calls-and-meetings/registering-calling-bot.md)
