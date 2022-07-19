---
title: Recursos de mídia do Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre os recursos de mídia, suspensões e pontos de espera do Live Share, além da redução de volume de áudio e sincronização entre vídeo e áudio.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: bf9d7c071a337a56373a9c58879d23a8d2638af7
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841868"
---
# <a name="live-share-media-capabilities"></a>Recursos de mídia do Live Share

Vídeo e áudio são partes fundamentais do local de trabalho e do mundo modernos. Ouvimos comentários abrangentes no sentido de que podemos fazer mais para aumentar a qualidade, acessibilidade e proteções de licenças quando se trata de assistir a vídeos durante as reuniões.

O SDK do Live Share habilita a **sincronização de mídia** em qualquer elemento HTML `<video>` e `<audio>` com a maior simplicidade já vista. Ao sincronizar a mídia na camada de controles de transporte e estado do player, você pode atribuir visualizações e licenças individualmente, fornecendo a mais alta qualidade possível disponível por meio do seu aplicativo.

## <a name="install"></a>Instalar

Para adicionar a versão mais recente do SDK ao seu aplicativo usando npm:

```bash
npm install @microsoft/live-share --save
npm install @microsoft/live-share-media --save
```

OU

Para adicionar a versão mais recente do SDK ao seu aplicativo usando [Yarn](https://yarnpkg.com/):

```bash
yarn add @microsoft/live-share
yarn add @microsoft/live-share-media
```

## <a name="media-sync-overview"></a>Visão geral da sincronização de mídia

O SDK do Live Share tem duas classes principais relacionadas à sincronização de mídia:

| Aulas                                                                                                                  | Descrição                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| [EphemeralMediaSession](/javascript/api/@microsoft/live-share-media/ephemeralmediasession)     | Objeto efêmero personalizado projetado para coordenar os controles de transporte de mídia e estado de reprodução em fluxos de mídia independentes. |
| [MediaPlayerSynchronizer](/javascript/api/@microsoft/live-share-media/mediaplayersynchronizer) | Sincroniza um Elemento de Mídia HTML local com um grupo de Elementos de Mídia HTML remotos para um `EphemeralMediaSession`.|

Exemplo:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
</body>
```

```javascript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient } from "@microsoft/live-share";
import { EphemeralMediaSession } from "@microsoft/live-share-media";

// Initialize the Teams Client SDK
await microsoftTeams.app.initialize();

// Setup the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { mediaSession: EphemeralMediaSession },
};
const { container } = await client.joinContainer(schema);
const { mediaSession } = container.initialObjects;

// Get the player from your document and create synchronizer
const player = document.getElementById("player");
const synchronizer = mediaSession.synchronize(player);

// Define roles you want to allow playback control and start sync
const allowedRoles = ["Organizer", "Presenter"];
await mediaSession.start(allowedRoles);
```

O `EphemeralMediaSession` escuta automaticamente as alterações no estado de reprodução do grupo e aplica as alterações por meio do `MediaPlayerSynchronizer`. Para evitar alterações de estado de reprodução que um usuário não iniciou intencionalmente, como um evento de buffering, devemos invocar os controles de transporte por meio do sincronizador, em vez de fazê-lo diretamente por meio do player.

Exemplo:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
  <div class="player-controls">
    <button id="play-button">Play</button>
    <button id="pause-button">Pause</button>
    <button id="restart-button">Restart</button>
    <button id="change-track-button">Change track</button>
  </div>
</body>
```

```javascript
// ...

document.getElementById("play-button").onclick = () => {
  synchronizer.play();
};

document.getElementById("pause-button").onclick = () => {
  synchronizer.pause();
};

document.getElementById("restart-button").onclick = () => {
  synchronizer.seekTo(0);
};

document.getElementById("change-track-button").onclick = () => {
  synchronizer.setTrack({
    trackIdentifier: "SOME_OTHER_VIDEO_SRC",
  });
};
```

 > [!Note]
 > Embora você possa usar o objeto `EphemeralMediaSession` para sincronizar a mídia diretamente, use o `MediaPlayerSynchronizer`, a menos que você queira um controle mais afinado da lógica de sincronização. Dependendo do player usado no seu aplicativo, talvez você queira criar um shim delegado para fazer com que a interface do seu web player corresponda à interface de mídia em HTML.

## <a name="suspensions-and-wait-points"></a>Suspensões e pontos de espera

Se quiser suspender temporariamente a sincronização do objeto `EphemeralMediaSession`, você pode usar as suspensões. Um objeto [MediaSessionCoordinatorSuspension](/javascript/api/@microsoft/live-share-media/ephemeralmediasessioncoordinatorsuspension) é local por padrão, o que pode ser útil nos casos em que um usuário talvez queira se atualizar quanto a algo que deixou passar, dar uma parada e assim por diante. Se o usuário terminar a suspensão, a sincronização será retomada automaticamente.

```javascript
// Suspend the media session coordinator
const suspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

Ao iniciar uma suspensão, você também pode incluir um parâmetro [CoordinationWaitPoint](/javascript/api/@microsoft/live-share-media/coordinationwaitpoint) opcional que permita que os usuários definam carimbos de data/hora nos quais uma suspensão deve ocorrer para todos os usuários. A sincronização não será retomada até que todos os usuários tenham terminado a suspensão para esse ponto de espera. Isso pode ser útil para, por exemplo, adicionar um teste ou pesquisa em determinados pontos do vídeo.

```javascript
// Suspend the media session coordinator
const waitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension();
// End the suspension when the user readies up
document.getElementById("ready-up-button").onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

## <a name="audio-ducking"></a>Redução de volume do áudio

O SDK do Live Share é compatível com a redução inteligente do volume de áudio. Você pode usar o recurso _experimental_ no seu aplicativo adicionando o seguinte ao seu código:

```javascript
import * as microsoftTeams from "@microsoft/teams-js";

// ...

let volumeTimer;
microsoftTeams.meeting.registerSpeakingStateChangeHandler((speakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

Para habilitar a redução de volume do áudio, adicione as seguintes permissões [RSC](/microsoftteams/platform/graph-api/rsc/resource-specific-consent) ao manifesto do seu aplicativo:

```json
{
  // ...rest of your manifest here
  "authorization": {
    "permissions": {
      "resourceSpecific": [
        // ...other permissions here
        {
          "name": "OnlineMeetingIncomingAudio.Detect.Chat",
          "type": "Delegated"
        },
        {
          "name": "OnlineMeetingIncomingAudio.Detect.Group",
          "type": "Delegated"
        }
      ]
    }
  }
}
```

> [!Note]
> A API `registerSpeakingStateChangeHandler` usada atualmente para redução de volume do áudio funciona apenas para os usuários não locais que estão falando.

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo   | Descrição | JavaScript |
| -------------------- | ----------------------------| -----------------|
| Vídeo de React          | Exemplo básico mostrando como o objeto EphemeralMediaSession funciona com o vídeo HTML5.                                                        | [Visualizar](https://aka.ms/liveshare-reactvideo)    |
| Modelo de mídia de React | Permita que todos os clientes conectados assistam a vídeos juntos, criem uma playlist compartilhada, transfiram quem está no controle e façam anotações no vídeo. | [Visualizar](https://aka.ms/liveshare-mediatemplate) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tutorial do Agile Poker](../sbs-teams-live-share.yml)

## <a name="see-also"></a>Confira também

* [Perguntas Frequentes do SDK do Live Share](teams-live-share-faq.md)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK de Mídia do Live Share](/javascript/api/@microsoft/live-share-media/)
* [Documentos de Referência](https://aka.ms/livesharedocs)
* [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
