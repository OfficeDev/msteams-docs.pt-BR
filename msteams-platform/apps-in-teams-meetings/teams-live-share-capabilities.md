---
title: Introdução ao Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre as funcionalidades do SDK do Live Share, permissões RSC e estruturas de dados efêmeros.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 2c60ce362810fdaf4b98342d2250ea34d9fbfbeb
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841880"
---
# <a name="live-share-core-capabilities"></a>Principais recursos do Live Share 

O SDK do Live Share pode ser adicionado aos contextos `sidePanel` e `meetingStage` da extensão da sua reunião com o mínimo de esforço. Este artigo se concentra em como integrar o SDK do Live Share ao seu aplicativo e aos principais recursos do SDK.

> [!Note]
> Atualmente, há suporte apenas para reuniões agendadas e todos os participantes devem estar no calendário da reunião. No momento, não há suporte para reuniões do tipo Reunir Agora, chamadas individuais, chamadas em grupo.

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-dashboard.png" alt-text="Teams Live Share":::

## <a name="install-the-javascript-sdk"></a>Instalar o SDK do JavaScript

O [SDK do Live Share](https://github.com/microsoft/live-share-sdk) é um pacote JavaScript publicado em [npm](https://www.npmjs.com/package/@microsoft/live-share) e você pode baixar por meio do npm ou yarn.

**npm**

```bash
npm install @microsoft/live-share --save
```

**Yarn**

```bash
yarn add @microsoft/live-share
```

## <a name="register-rsc-permissions"></a>Registrar permissões de RSC

Para habilitar o SDK do Live Share para sua extensão de reunião, adicione primeiramente as seguintes permissões de RSC ao manifesto do seu aplicativo:

```json
{
  // ...rest of your manifest here
  "configurableTabs": [
    {
        "configurationUrl": "https://<<BASE_URI_ORIGIN>>/config",
        "canUpdateConfiguration": false,
        "scopes": [
            "groupchat"
        ],
        "context": [
            "meetingSidePanel",
            "meetingStage"
        ]
    }
  ],
  "validDomains": [
    "<<BASE_URI_ORIGIN>>"
  ],
  "authorization": {
    "permissions": {
      "resourceSpecific": [
        // ...other permissions here
        {
          "name": "LiveShareSession.ReadWrite.Chat",
          "type": "Delegated"
        },
        {
          "name": "LiveShareSession.ReadWrite.Group",
          "type": "Delegated"
        },
        {
          "name": "MeetingStage.Write.Chat",
          "type": "Delegated"
        },
        {
          "name": "ChannelMeetingStage.Write.Group",
          "type": "Delegated"
        }
      ]
    }
  }
}
```

## <a name="join-a-meeting-session"></a>Ingressar em uma sessão de reunião

Siga as etapas para ingressar em uma sessão associada à reunião de um usuário:

1. Inicializar o SDK do Cliente Teams.
2. Inicialize o [TeamsFluidClient](/javascript/api/@microsoft/live-share/teamsfluidclient).
3. Defina as estruturas de dados que você deseja sincronizar. Por exemplo, `SharedMap`.
4. Ingressar no contêiner.

Exemplo:

```javascript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";

// Initialize the Teams Client SDK
await microsoftTeams.app.initialize();

// Setup the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { exampleMap: SharedMap },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

Isso é tudo o que foi necessário para configurar seu contêiner e ingressar na sessão da reunião. Agora, vamos revisar os diferentes tipos de _estruturas de dados distribuídos_ que você pode usar com o SDK do Live Share.

## <a name="fluid-distributed-data-structures"></a>Estruturas de dados distribuídos do Fluid

O SDK do Live Share dá suporte a qualquer [estrutura de dados distribuída](https://fluidframework.com/docs/data-structures/overview/) incluída no Fluid Framework. Aqui está uma visão geral rápida de alguns dos diferentes tipos de objetos disponíveis:

| Objeto Compartilhado                                                                       | Descrição                                                                                                                                  |
| ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| [SharedMap](https://fluidframework.com/docs/data-structures/map/)                   | Um repositório de chave-valor distribuído. Defina qualquer objeto serializável JSON de uma determinada chave para sincronizar esse objeto para todos na sessão. |
| [SharedSegmentSequence](https://fluidframework.com/docs/data-structures/sequences/) | Uma estrutura de dados semelhante à lista para armazenar um conjunto de itens (chamados segmentos) em posições definidas.                                                    |
| [SharedString](https://fluidframework.com/docs/data-structures/string/)             | Sequência de cadeia de caracteres distribuída otimizada para edição de texto do documento.                                                                     |

Vamos ver como o `SharedMap` funciona. Neste exemplo, usamos `SharedMap` para criar um recurso de playlist.

```javascript
import { SharedMap } from "fluid-framework";
// ...
const schema = {
  initialObjects: { playlistMap: SharedMap },
};
const { container } = await client.joinContainer(schema);
const { playlistMap } = container.initialObjects;

// Listen for changes to values in the map
playlistMap.on("valueChanged", (changed, local) => {
  const video = playlistMap.get(changed.key);
  // Update UI with added video
});

function onClickAddToPlaylist(video) {
  // Add video to map
  playlistMap.set(video.id, video);
}
// ...
```

> [!Note]
> Os objetos DDS do Fluid Framework principal não dão suporte à verificação de função de reunião. Todos na reunião podem alterar os dados armazenados por meio desses objetos.

## <a name="live-share-ephemeral-data-structures"></a>Estruturas de dados efêmeros do Live Share

O SDK do Live Share inclui um conjunto de novas classes `SharedObject` efêmeras que fornecem objetos com estado e sem estado que não são armazenados no contêiner do Fluid. Por exemplo, se quiser criar um recurso de apontador laser em seu aplicativo, como a popular integração do PowerPoint Live, poderá usar nossos objetos `EphemeralEvent` ou `EphemeralState`.

| Objeto Efêmero                                                                                                       | Descrição                                                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| [EphemeralPresence](/javascript/api/@microsoft/live-share/ephemeralpresence) | Veja quais usuários estão online, defina propriedades personalizadas para cada usuário e transmita as alterações em sua presença.                       |
| [EphemeralEvent](/javascript/api/@microsoft/live-share/ephemeralevent)       | Transmita eventos individuais com quaisquer atributos de dados personalizados no conteúdo.                                                     |
| [EphemeralState](/javascript/api/@microsoft/live-share/ephemeralstate)       | Semelhante ao SharedMap, um repositório de chave-valor distribuído que permite alterações de estado restrito com base na função, por exemplo, o apresentador.|

### <a name="ephemeralpresence-example"></a>Exemplo de EphemeralPresence

A classe `EphemeralPresence` torna o controle de quem está participando de uma reunião mais fácil do que nunca. Ao chamar os métodos `.start()` ou `.updatePresence()`, você pode atribuir metadados personalizados para esse usuário, como um nome ou identificador exclusivo.

Exemplo:

```javascript
import { EphemeralPresence, PresenceState } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);
const { presence } = container.initialObjects;

// Listen for changes to presence
presence.on("presenceChanged", (userPresence, local) => {
  // Update UI with presence
});

// Start tracking presence
presence.start("YOUR_CUSTOM_USER_ID", {
  name: "Anonymous",
  picture: "DEFAULT_PROFILE_PICTURE_URL",
});

function onUserDidLogIn(userName, profilePicture) {
  presence.updatePresence(PresenceState.online, {
    name: userName,
    picture: profilePicture,
  });
}
```

### <a name="ephemeralevent-example"></a>Exemplo de EphemeralEvent

`EphemeralEvent` é uma ótima maneira de enviar eventos simples para outros clientes em uma reunião. É útil para cenários como o envio de notificações de sessão.

```javascript
import { EphemeralEvent } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { notifications: EphemeralEvent },
};
const { container } = await client.joinContainer(schema);
const { notifications } = container.initialObjects;

// Listen for incoming notifications
notifications.on("received", (event, local) => {
  let notificationToDisplay;
  if (local) {
    notificationToDisplay = `You ${event.text}`;
  } else {
    notificationToDisplay = `${event.senderName} ${event.text}`;
  }
  // Display notification in your UI
});

// Start tracking notifications
await notifications.start();

notifications.sendEvent({
  senderName: "LOCAL_USER_NAME",
  text: "joined the session",
});
```

## <a name="role-verification-for-ephemeral-data-structures"></a>Verificação de função das estruturas de dados efêmeros

As reuniões no Teams podem variar de chamadas individuais a reuniões gerais e podem incluir membros de todas as organizações. Os objetos efêmeros são projetados para dar suporte à verificação de função, permitindo definir as funções que têm permissão para enviar mensagens para cada objeto efêmero individual. Por exemplo, você pode optar por permitir que apenas os apresentadores e organizadores da reunião controlem a reprodução de vídeo, mas, ainda assim, permitir que convidados e participantes solicitem vídeos para assistir em seguida.

Exemplo:

```javascript
import { EphemeralState, UserMeetingRole } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { appState: EphemeralState },
};
const { container } = await client.joinContainer(schema);
const { appState } = container.initialObjects;

// Listen for changes to values in the map
appState.on("stateChanged", (state, value, local) => {
  // Update local app state
});

// Set roles who can change state and start
const allowedRoles = [UserMeetingRole.organizer, UserMeetingRole.presenter];
appState.start(allowedRoles);

function onSelectEditMode(documentId) {
  appState.changeState("editing", {
    documentId,
  });
}

function onSelectPresentMode(documentId) {
  appState.changeState("presenting", {
    documentId,
    presentingUserId: "LOCAL_USER_ID",
  });
}
```

Ouça seus clientes para entender seus cenários antes de implementar a verificação de função em seu aplicativo, principalmente para a função de **Organizador**. Não há nenhuma garantia de que um organizador esteja presente na reunião. Como regra geral, todos os usuários serão **Organizadores** ou **Apresentadores** ao colaborar em uma organização. Se um usuário for um **Participante**, geralmente é uma decisão intencional do organizador.

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo | Descrição  | JavaScript  |
| ----------- | ---------------------------------------------- | -------------- |
| Dice Roller | Habilite todos os clientes conectados para rolar um dado e exibir o resultado. | [Exibir](https://aka.ms/liveshare-diceroller) |
| Agile Poker | Permita que todos os clientes conectados joguem o Agile Poker.| [Exibir](https://aka.ms/liveshare-agilepoker) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Funcionalidades de mídia do Live Share](teams-live-share-media-capabilities.md)

## <a name="see-also"></a>Confira também

* [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK de Mídia do Live Share](/javascript/api/@microsoft/live-share-media/)
* [Perguntas frequentes do Live Share](teams-live-share-faq.md)
* [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
