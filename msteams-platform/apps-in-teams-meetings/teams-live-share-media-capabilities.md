---
title: Recursos de mídia do Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre os recursos de mídia, suspensões e pontos de espera do Live Share, além da redução de volume de áudio e sincronização entre vídeo e áudio.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 0ab0bf436ce3ca27b55a68ea2c80f1451f4d967e
ms.sourcegitcommit: 134ce9381891e51e6327f1f611fdfd60c90cca18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2022
ms.locfileid: "67425579"
---
# <a name="live-share-media-capabilities"></a>Recursos de mídia do Live Share

:::image type="content" source="../assets/images/teams-live-share/live-share-media-capabilities-docs-feature-1.png" alt-text="Sincronização de mídia do Teams Live Share":::

Vídeo e áudio são partes fundamentais do local de trabalho e do mundo modernos. Ouvimos comentários abrangentes no sentido de que podemos fazer mais para aumentar a qualidade, acessibilidade e proteções de licenças quando se trata de assistir a vídeos durante as reuniões.

O SDK do Live Share permite **a sincronização** de mídia robusta para qualquer HTML `<video>` `<audio>` e elemento com apenas algumas linhas de código. Ao sincronizar a mídia na camada de controles de transporte e estado do player, você pode atribuir visualizações e licenças individualmente, fornecendo a mais alta qualidade possível disponível por meio do seu aplicativo.

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

| Aulas                                                                                        | Descrição                                                                                                                                       |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EphemeralMediaSession](/javascript/api/@microsoft/live-share-media/ephemeralmediasession)     | Objeto efêmero personalizado projetado para coordenar os controles de transporte de mídia e estado de reprodução em fluxos de mídia independentes.                          |
| [MediaPlayerSynchronizer](/javascript/api/@microsoft/live-share-media/mediaplayersynchronizer) | Sincroniza qualquer objeto que implementa a `IMediaPlayer` interface , incluindo HTML5 `<video>` e `<audio>` -- usando `EphemeralMediaSession`. |

Exemplo:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
</body>
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient, UserMeetingRole } from "@microsoft/live-share";
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
const allowedRoles = [UserMeetingRole.organizer, UserMeetingRole.presenter];
await mediaSession.initialize(allowedRoles);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient, UserMeetingRole } from "@microsoft/live-share";
import { EphemeralMediaSession, IMediaPlayer, MediaPlayerSynchronizer } from "@microsoft/live-share-media";
import { ContainerSchema } from "fluid-framework";

// Initialize the Teams Client SDK
await microsoftTeams.app.initialize();

// Join the Fluid container
const client = new TeamsFluidClient();
const schema: ContainerSchema = {
  initialObjects: { mediaSession: EphemeralMediaSession },
};
const { container } = await client.joinContainer(schema);
const mediaSession = container.initialObjects.mediaSession as EphemeralMediaSession;

// Get the player from your document and create synchronizer
const player: IMediaPlayer = document.getElementById("player") as HTMLVideoElement;
const synchronizer: MediaPlayerSynchronizer = mediaSession.synchronize(player);

// Define roles you want to allow playback control and start sync
const allowedRoles: UserMeetingRole[] = [UserMeetingRole.organizer, UserMeetingRole.presenter];
await mediaSession.initialize(allowedRoles);
```

---

O `EphemeralMediaSession` usuário escuta automaticamente as alterações no estado de reprodução do grupo. `MediaPlayerSynchronizer` escuta as alterações de estado emitidas por `EphemeralMediaSession` e aplica-as ao objeto `IMediaPlayer` fornecido, como um HTML5 `<video>` ou `<audio>` elemento. Para evitar alterações de estado de reprodução que um usuário não iniciou intencionalmente, como um evento de buffering, devemos invocar os controles de transporte por meio do sincronizador, em vez de fazê-lo diretamente por meio do player.

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

> [!NOTE]
> Embora você possa usar o `EphemeralMediaSession` objeto para sincronizar a mídia manualmente, geralmente é recomendável usar o `MediaPlayerSynchronizer`. Dependendo do player usado em seu aplicativo, talvez seja necessário criar um shim delegado para fazer com que a interface do seu web player corresponda à interface [do IMediaPlayer](/javascript/api/@microsoft/live-share-media/imediaplayer) .

## <a name="suspensions-and-wait-points"></a>Suspensões e pontos de espera

:::image type="content" source="../assets/images/teams-live-share/live-share-media-out-of-sync.png" alt-text="Captura de tela que mostra uma sincronização de suspensão com o apresentador.":::

Se quiser suspender temporariamente a sincronização do objeto `EphemeralMediaSession`, você pode usar as suspensões. Um objeto [MediaSessionCoordinatorSuspension](/javascript/api/@microsoft/live-share-media/ephemeralmediasessioncoordinatorsuspension) é local por padrão, o que pode ser útil nos casos em que um usuário talvez queira se atualizar quanto a algo que deixou passar, dar uma parada e assim por diante. Se o usuário terminar a suspensão, a sincronização será retomada automaticamente.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
// Suspend the media session coordinator
const suspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { MediaSessionCoordinatorSuspension } from "@microsoft/live-share-media";

// Suspend the media session coordinator
const suspension: MediaSessionCoordinatorSuspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

---

Ao iniciar uma suspensão, você também pode incluir um parâmetro [CoordinationWaitPoint](/javascript/api/@microsoft/live-share-media/coordinationwaitpoint) opcional que permita que os usuários definam carimbos de data/hora nos quais uma suspensão deve ocorrer para todos os usuários. A sincronização não será retomada até que todos os usuários tenham terminado a suspensão para esse ponto de espera.

Aqui estão alguns cenários em que os pontos de espera são especialmente úteis:

- Adicionar um teste ou uma pesquisa em determinados pontos no vídeo.
- Aguardando que todos carreguem um vídeo adequadamente antes que ele seja iniciado ou durante o buffer.
- Permitir que um apresentador escolha pontos no vídeo para discussão em grupo.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
// Suspend the media session coordinator
const waitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension(waitPoint);
// End the suspension when the user readies up
document.getElementById("ready-up-button").onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { MediaSessionCoordinatorSuspension, CoordinationWaitPoint } from "@microsoft/live-share-media";

// Suspend the media session coordinator
const waitPoint: CoordinationWaitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension(waitPoint);

// End the suspension when the user readies up
document.getElementById("ready-up-button")!.onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

---

## <a name="audio-ducking"></a>Redução de volume do áudio

O SDK do Live Share é compatível com a redução inteligente do volume de áudio. Você pode usar o _recurso experimental_ em seu aplicativo adicionando o seguinte ao código:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import * as microsoftTeams from "@microsoft/teams-js";

// ... set up MediaPlayerSynchronizer

// Register speaking state change handler through Teams Client SDK
let volumeTimer;
microsoftTeams.meeting.registerSpeakingStateChangeHandler((speakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    // If someone in the meeting starts speaking, periodically
    // lower the volume using your MediaPlayerSynchronizer's
    // VolumeLimiter.
    synchronizer.volumeLimiter?.lowerVolume();
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    // If everyone in the meeting stops speaking and the
    // interval timer is active, clear the interval.
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";

// ... set up MediaPlayerSynchronizer

// Register speaking state change handler through Teams Client SDK
let volumeTimer: NodeJS.Timeout | undefined;
microsoftTeams.meeting.registerSpeakingStateChangeHandler((speakingState: microsoftTeams.meeting.ISpeakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    // If someone in the meeting starts speaking, periodically
    // lower the volume using your MediaPlayerSynchronizer's
    // VolumeLimiter.
    synchronizer.volumeLimiter?.lowerVolume();
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    // If everyone in the meeting stops speaking and the
    // interval timer is active, clear the interval.
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

---

Além disso, adicione as seguintes [permissões de RSC](/microsoftteams/platform/graph-api/rsc/resource-specific-consent) ao manifesto do aplicativo:

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

> [!NOTE]
> A API `registerSpeakingStateChangeHandler` usada atualmente para redução de volume do áudio funciona apenas para os usuários não locais que estão falando.

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo          | Descrição                                                                                                                               | JavaScript                                     |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| Vídeo de React          | Exemplo básico mostrando como o objeto EphemeralMediaSession funciona com o vídeo HTML5.                                                        | [Visualizar](https://aka.ms/liveshare-reactvideo)    |
| Modelo de mídia de React | Permita que todos os clientes conectados assistam a vídeos juntos, criem uma playlist compartilhada, transfiram quem está no controle e façam anotações no vídeo. | [Visualizar](https://aka.ms/liveshare-mediatemplate) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tutorial do Agile Poker](../sbs-teams-live-share.yml)

## <a name="see-also"></a>Confira também

- [Perguntas Frequentes do SDK do Live Share](teams-live-share-faq.md)
- [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
- [Documentos de referência do SDK de Mídia do Live Share](/javascript/api/@microsoft/live-share-media/)
- [Documentos de Referência](https://aka.ms/livesharedocs)
- [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
