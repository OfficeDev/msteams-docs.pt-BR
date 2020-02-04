---
title: Chamadas de mídia em tempo real e reuniões online com o Microsoft Teams
description: Compreender os principais conceitos de criação de bot que podem conduzir chamadas de áudio e vídeo em tempo real e reuniões online.
keywords: áudio fluxo vídeo fluxo de áudio/vídeo chamada da reunião chamadas de mídia em tempo real do serviço de mídia hospedado por aplicativo de mídia hospedado
ms.openlocfilehash: 0ec99d1caa8810d292170c7c70a1518de7301873
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672615"
---
# <a name="real-time-media-calls-and-meetings-with-microsoft-teams"></a>Chamadas de mídia em tempo real e reuniões com o Microsoft Teams

A plataforma de mídia em tempo real permite que os bots interajam com chamadas e reuniões do Microsoft Teams usando voz, vídeo e compartilhamento de tela em tempo real. Essa é uma capacidade avançada que permite ao bot enviar e receber quadro de conteúdo de voz e vídeo *por quadro*. O bot tem acesso "bruto" aos fluxos de mídia de voz, vídeo e compartilhamento de tela. (Os bots que processam mídias são chamados de bots de _mídia hospedados por aplicativos_ , em oposição aos bots de _mídia hospedados pelo serviço_ mais simples que dependem da plataforma de mídia em tempo real para todo o processamento de mídia.)

Por exemplo, em uma chamada 1:1 com um bot, conforme o usuário fala, o bot receberá 50 quadros de áudio por segundo, com cada quadro contendo 20 milissegundos (MS) de áudio. Um bot de mídia hospedado por aplicativo pode executar o reconhecimento de fala em tempo real à medida que os quadros de áudio são recebidos, em vez de esperar por uma gravação depois que o usuário parou de falar. O bot também pode enviar e receber vídeo de resolução de alta definição, incluindo o conteúdo de compartilhamento de tela baseado em vídeo.

A plataforma fornece uma API simples, semelhante a Soquete, para o bot enviar e receber mídias e manipula a codificação em tempo real e decodificação de pacotes de áudio/vídeo usando codecs como SILK e G. 722 para áudio e H. 264 para vídeo. A plataforma também lida com toda a criptografia de pacotes de mídia/descriptografia e transmissão de rede de pacotes automaticamente, de modo que o bot só precisa se preocupar com o conteúdo de áudio/vídeo real. Um bot de mídia em tempo real pode participar de chamadas 1:1, bem como reuniões com vários participantes.

Este artigo apresenta os principais conceitos relacionados à criação de um bot que pode realizar chamadas de áudio/vídeo em tempo real com o Microsoft Teams.

## <a name="media-session"></a>Sessão de mídia

Quando um bot de mídia em tempo real responde a uma chamada de entrada ou participa de uma reunião do Microsoft Teams, ele deve declarar quais modalidades ela pretende suportar. Para cada modalidade suportada, o bot declara se pode enviar e receber mídia, somente receber ou somente enviar. Por exemplo, um bot projetado para lidar com as chamadas do Team 1:1 pode querer enviar e receber áudio, mas apenas *Enviar* vídeo (já que ele não precisa receber o vídeo do chamador). O conjunto de modalidades de áudio e vídeo estabelecidos entre o bot e o chamador ou a reunião do teams é chamado de **sessão de mídia**.

Dois tipos de modalidades de vídeo têm suporte: **vídeo principal** e **compartilhamento de tela baseado em vídeo**. O vídeo principal é usado para transportar o vídeo da webcam de um usuário. O compartilhamento de tela baseado em vídeo permite que um usuário Compartilhe sua tela como um fluxo de vídeo. A plataforma permite que um bot envie e/ou receba *ambos os* tipos de vídeo.

Quando ingressou em uma reunião do Teams, um bot pode receber vários fluxos de vídeo principais simultaneamente, até 10 por sessão de mídia. Isso permite que o bot "Veja" mais de um participante da reunião.

## <a name="frames-and-frame-rate"></a>Quadros e taxa de quadros

Um bot de mídia em tempo real interage diretamente com as modalidades de áudio e vídeo de uma sessão de mídia. Isso significa que o bot está enviando e/ou recebendo mídia como uma sequência de **quadros**, onde cada quadro representa uma unidade de conteúdo. Um segundo de áudio pode ser transmitido como uma sequência de 50 quadros, com cada quadro contendo 20 milissegundos (MS), 1/50 º de um segundo – conteúdo de fala. Um segundo de vídeo pode ser dividido em fatias como uma sequência de 30 imagens estáticas, cada uma delas se destina a ser vista apenas 33.3 ms, 1/30 de um segundo, antes da exibição do próximo quadro de vídeo. O número de quadros transmitidos ou renderizados por segundo é chamado de **taxa de quadros**. "30fps" indica 30 quadros por segundo.

## <a name="audio-format"></a>Formato de áudio

Cada segundo de áudio é representado como **amostras**16.000, com cada amostra contendo 16 bits de dados. Um quadro de áudio do 20 ms contém 320 amostras (640 bytes de dados).

## <a name="video-format"></a>Formato de vídeo

Há vários formatos com suporte para o vídeo. Duas propriedades de chave de um formato de vídeo são seu **tamanho de quadro** e **formato de cor**. Os tamanhos de quadro suportados incluem 640x360 ("360p"), 1280 x 720 ("720p") e 1920 x 1080 ("1080p"). Os formatos de cores suportados incluem NV12 (12 bits por pixel) e RGB24 (24 bits por pixel).

Um quadro de vídeo "720p" contém 921.600 pixels (1280 vezes 720). No formato de cor RGB24, cada pixel é representado como 3 bytes (24 bits) composto por um byte cada um dos componentes de cor vermelho, verde e azul. Portanto, um único quadro de vídeo 720p RGB24 requer 2.764.800 bytes de dados (921.600 pixels vezes de 3 bytes/pixel). Em uma taxa de quadros de 30fps, o envio de quadros de vídeo 720p RGB24 significa processamento de aproximadamente 80 MB/s de conteúdo (que é amplamente compactado pelo codec de vídeo H. 264 antes da transmissão de rede).

Uma capacidade avançada da plataforma permite que um bot envie/receba vídeo como quadros **codificados** H. 264. Isso oferece suporte a bots que oferecem seu próprio codificador/decodificador H. 264 ou não precisam do fluxo de vídeo decodificado em bitmaps RGB24 ou NV12 brutos.

## <a name="active-and-dominant-speakers"></a>Alto-falantes ativos e dominantes

Quando fizer parte de uma reunião do teams que consiste em vários participantes, um bot poderá identificar quais participantes da reunião estão falando no momento. Os **oradores ativos** identificam quais participantes estão sendo ouvidos em cada quadro de áudio recebido. Os **alto-falantes dominantes** identificam quais participantes estão atualmente mais ativos (ou "dominantemente") na conversa de grupo, mesmo que sua voz não seja ouvida em todos os quadros de áudio. O conjunto de alto-falantes dominantes pode mudar à medida que os diferentes participantes se acendem.

## <a name="video-subscription"></a>Assinatura de vídeo

Em uma chamada 1:1, o bot receberá automaticamente o vídeo do chamador se o bot estiver habilitado para receber vídeo. Em uma reunião do Teams, o bot deve indicar à plataforma quais participantes ele deseja ver. Uma **assinatura de vídeo** é uma solicitação pelo bot para receber o vídeo principal de um participante ou o conteúdo de compartilhamento de tela. À medida que os participantes da reunião realizam a conversa, o bot pode modificar as assinaturas de vídeo desejadas com base nas atualizações do conjunto de alto-falantes dominante ou nas notificações que indicam qual participante está compartilhando tela no momento.

## <a name="developer-resources"></a>Recursos de desenvolvedor

Para desenvolver um bot de mídia hospedado por aplicativo, você deve instalar o pacote NuGet a seguir em seu projeto do Visual Studio:

- [Biblioteca Microsoft. Graph. calls. Media .NET](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)

Os bots de mídia hospedados por aplicativos exigem o .NET/C# e o Windows Server, conforme descrito em detalhes em [requisitos e considerações para bots de mídia hospedados por aplicativos](requirements-considerations-application-hosted-media-bots.md#application-hosted-media-bot-development-requires-cnet-and-windows-server).
