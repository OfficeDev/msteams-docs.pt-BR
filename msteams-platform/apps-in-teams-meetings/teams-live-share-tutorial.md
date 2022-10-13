---
title: Tutorial de código do Live Share
author: surbhigupta
description: Neste módulo, saiba como começar a usar o SDK do Live Share e como criar um exemplo de Dice Roller usando o SDK do Live Share
ms.topic: conceptual
ms.localizationpriority: high
ms.author: stevenic
ms.date: 04/07/2022
ms.openlocfilehash: 66ff0cfed7fcd34d741a35ff4aa30e507adf8717
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560537"
---
# <a name="dice-roller-code-tutorial"></a>Tutorial de código do Dice Roller

No aplicativo de exemplo Dice Roller, os usuários são mostrados um dado com um botão para rolá-lo. Quando os dados são rolados, o SDK do Live Share usa o Fluid Framework para sincronizar os dados entre clientes, para que todos vejam o mesmo resultado. Para sincronizar dados, execute as seguintes etapas no arquivo [app.js](https://github.com/microsoft/live-share-sdk/blob/main/samples/01.dice-roller/src/app.js):

1. [Configurar o aplicativo](#set-up-the-application)
2. [Ingressar em um contêiner do Fluid](#join-a-fluid-container)
3. [Gravar o modo de exibição de estágio](#write-the-stage-view)
4. [Conectar o modo de exibição de estágio aos dados do Fluid](#connect-stage-view-to-fluid-data)
5. [Gravar o modo de exibição do painel lateral](#write-the-side-panel-view)
6. [Gravar o modo de exibição de configurações](#write-the-settings-view)

:::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="Exemplo do DiceRoller":::

## <a name="set-up-the-application"></a>Configurar o aplicativo.

Você pode começar importando os módulos necessários. O exemplo usa [o DDS SharedMap](https://fluidframework.com/docs/data-structures/map/) do Fluid Framework e [o TeamsFluidClient](/javascript/api/@microsoft/live-share/teamsfluidclient) do SDK do Live Share. O exemplo dá suporte à Extensibilidade de Reunião do Teams, portanto, você deve incluir o [SDK do Cliente do Teams](https://github.com/OfficeDev/microsoft-teams-library-js). Por fim, o exemplo foi projetado para ser executado localmente e em uma reunião do Teams, portanto, você precisa incluir mais partes do Fluid Framework para [testar o exemplo localmente](https://fluidframework.com/docs/testing/testing/#azure-fluid-relay-as-an-abstraction-for-tinylicious).

Os aplicativos criam contêineres Fluid usando um esquema que define um conjunto de objetos _iniciais_ que estão disponíveis para o contêiner. O exemplo usa um SharedMap para armazenar o valor de dados atual que foi rolado. Para obter mais informações, consulte [Modelagem de dados](https://fluidframework.com/docs/build/data-modeling/).

Os aplicativos de reunião do Teams exigem várias exibições, como conteúdo, configuração e estágio. Você pode criar uma função `start()` para ajudar a identificar a exibição. Isso ajuda a renderizar e executar qualquer inicialização necessária. O aplicativo dá suporte à execução local em um navegador da Web e de dentro de uma reunião do Teams. A `start()` função procura um parâmetro `inTeams=true` de consulta para determinar se ela está em execução no Teams.

> [!NOTE]
> Ao executar no Teams, seu aplicativo precisa chamar `app.initialize()` antes de chamar qualquer outro método teams-js.

Além do parâmetro de `inTeams=true` consulta, você pode usar um parâmetro de consulta para determinar a `view=content|config|stage` exibição que precisa ser renderizada.

```js
import { SharedMap } from "fluid-framework";
import { app, pages } from "@microsoft/teams-js";
import { LiveShareClient, testLiveShare } from "@microsoft/live-share";
import { InsecureTokenProvider } from "@fluidframework/test-client-utils";

const searchParams = new URL(window.location).searchParams;
const root = document.getElementById("content");

// Define container schema

const diceValueKey = "dice-value-key";

const containerSchema = {
  initialObjects: { diceMap: SharedMap },
};

function onContainerFirstCreated(container) {
  // Set initial state of the rolled dice to 1.
  container.initialObjects.diceMap.set(diceValueKey, 1);
}

// STARTUP LOGIC

async function start() {
  // Check for page to display
  let view = searchParams.get("view") || "stage";

  // Check if we are running on stage.
  if (!!searchParams.get("inTeams")) {
    // Initialize teams app
    await app.initialize();

    // Get our frameContext from context of our app in Teams
    const context = await app.getContext();
    if (context.page.frameContext == "meetingStage") {
      view = "stage";
    }
  }

  // Load the requested view
  switch (view) {
    case "content":
      renderSidePanel(root);
      break;
    case "config":
      renderSettings(root);
      break;
    case "stage":
    default:
      const { container } = await joinContainer();
      renderStage(container.initialObjects.diceMap, root);
      break;
  }
}

start().catch((error) => console.error(error));
```

## <a name="join-a-fluid-container"></a>Ingressar em um contêiner do Fluid

Nem todas as exibições do seu aplicativo precisam ser colaborativas. O modo de exibição `stage` _sempre_ precisa de recursos colaborativos, o modo de exibição `content` _pode_ precisar de recursos colaborativos e o modo de exibição `config` _nunca_ deve precisar de recursos colaborativos. Para os modos de exibição que precisam de recursos colaborativos, você precisará ingressar em um contêiner do Fluid associado à reunião atual.

Ingressar no contêiner para a reunião é tão simples quanto inicializar o [LiveShareClient](/javascript/api/@microsoft/live-share/liveshareclient) e chamar seu [método joinContainer](/javascript/api/@microsoft/live-share/liveshareclient#@microsoft-live-share-liveshareclient-joincontainer) ().

Ao executar localmente, você pode importar [testLiveShare e](/javascript/api/@microsoft/live-share/testliveshare) chamar seu [método initialize](/javascript/api/@microsoft/live-share.testliveshare#@microsoft-live-share-testliveshare-initialize) (). Em seguida, use [o método joinContainer()](/javascript/api/@microsoft/live-share.testliveshare#@microsoft-live-share-testliveshare-joincontainer) para se conectar a uma sessão.

```js
async function joinContainer() {
  // Are we running in teams?
  if (!!searchParams.get("inTeams")) {
    // Create client
    const liveShare = new LiveShareClient();
    // Join container
    return await liveShare.joinContainer(containerSchema, onContainerFirstCreated);
  }
  // Create client and configure for testing
  testLiveShare.initialize();
  return await testLiveShare.joinContainer(containerSchema, onContainerFirstCreated);
}
```

Ao testar localmente, `testLiveShare` atualiza a URL do navegador para conter a ID do contêiner de teste que foi criado. Copiar esse link para outras guias do navegador faz com que ele `testLiveShare` ingresse no contêiner de teste que foi criado. Se a modificação da URL de aplicativos interferir na operação do aplicativo, a estratégia usada para armazenar a ID de contêineres de teste poderá ser personalizada usando as opções [setLocalTestContainerId](/javascript/api/@microsoft/live-share.iliveshareclientoptions#@microsoft-live-share-iliveshareclientoptions-setlocaltestcontainerid) e [getLocalTestContainerId](/javascript/api/@microsoft/live-share.iliveshareclientoptions#@microsoft-live-share-iliveshareclientoptions-getlocaltestcontainerid) `LiveShareClient`passadas para .

## <a name="write-the-stage-view"></a>Gravar o modo de exibição de estágio

Muitos aplicativos de Extensibilidade de Reunião do Teams foram projetados para React para sua estrutura de modo de exibição, mas isso não é necessário. Por exemplo, este exemplo usa métodos HTML/DOM padrão para renderizar um modo de exibição.

### <a name="start-with-a-static-view"></a>Iniciar com um modo de exibição estático

É fácil criar o modo de exibição usando dados locais sem nenhuma funcionalidade do Fluid e, em seguida, adicionar o Fluid alterando algumas partes principais do aplicativo.

A `renderStage` função acrescenta o `stageTemplate` elemento HTML passado e cria um rolo de dados de trabalho com um valor de dado aleatório sempre que o **botão Rolar** é selecionado. O `diceMap` será usado nas próximas etapas.

```js
const stageTemplate = document.createElement("template");

stageTemplate["innerHTML"] = `
  <div class="wrapper">
    <div class="dice"></div>
    <button class="roll"> Roll </button>
  </div>
`;
function renderStage(diceMap, elem) {
  elem.appendChild(stageTemplate.content.cloneNode(true));
  const rollButton = elem.querySelector(".roll");
  const dice = elem.querySelector(".dice");

  rollButton.onclick = () => updateDice(Math.floor(Math.random() * 6) + 1);

  const updateDice = (value) => {
    // Unicode 0x2680-0x2685 are the sides of a die (⚀⚁⚂⚃⚄⚅).
    dice.textContent = String.fromCodePoint(0x267f + value);
  };
  updateDice(1);
}
```

## <a name="connect-stage-view-to-fluid-data"></a>Conectar o modo de exibição de estágio aos dados do Fluid

### <a name="modify-fluid-data"></a>Modificar dados do Fluid

Para começar a usar o Fluid no aplicativo, a primeira coisa a ser alterada é o que acontece quando o usuário seleciona o `rollButton`. Em vez de atualizar o estado local diretamente, o botão atualiza o número armazenado na chave `value` do passado em `diceMap`. Como `diceMap` é um `SharedMap` do Fluid, as alterações são distribuídas para todos os clientes. Qualquer alteração no evento `diceMap` pode fazer com que `valueChanged` um evento seja emitido e um manipulador de eventos pode disparar uma atualização da exibição.

Esse padrão é comum no Fluid porque permite que o modo de exibição se comporte da mesma maneira para alterações locais e remotas.

```js
rollButton.onclick = () =>
  diceMap.set("dice-value-key", Math.floor(Math.random() * 6) + 1);
```

### <a name="rely-on-fluid-data"></a>Depender dos dados do Fluid

A próxima alteração que precisa ser feita é alterar `updateDice` a função, pois ela não aceita mais um valor arbitrário. Isso significa que o aplicativo não pode mais modificar diretamente o valor do dado local. Em vez disso, o valor é recuperado de `SharedMap` cada vez que `updateDice` é chamado.

```js
const updateDice = () => {
  const diceValue = diceMap.get("dice-value-key");
  dice.textContent = String.fromCodePoint(0x267f + diceValue);
};
updateDice();
```

### <a name="handle-remote-changes"></a>Manipular alterações remotas

Os valores retornados de `diceMap` são apenas um instantâneo do momento. Para manter os dados atualizados à medida que eles são alterados, um manipulador de eventos deve ser definido no `diceMap` para chamar `updateDice` cada vez que o evento `valueChanged` for enviado. Para obter uma lista de eventos disparados e os valores passados para esses eventos, consulte [SharedMap](https://fluidframework.com/docs/data-structures/map/).

```js
diceMap.on("valueChanged", updateDice);
```

## <a name="write-the-side-panel-view"></a>Gravar o modo de exibição do painel lateral

O modo de exibição do painel lateral, carregado por meio da guia `contentUrl` com o contexto de quadro `sidePanel`, é exibido para o usuário em um painel lateral quando ele abre seu aplicativo em uma reunião. O objetivo da exibição do painel lateral é permitir que um usuário selecione o conteúdo do aplicativo antes de compartilhar o aplicativo no estágio da reunião. Para os aplicativos de SDK do Live Share, o modo de exibição do painel lateral também pode ser usado como uma experiência complementar para o aplicativo. Chamar [joinContainer()](/javascript/api/@microsoft/live-share/liveshareclient#@microsoft-live-share-liveshareclient-joincontainer) do modo de exibição do painel lateral conecta ao mesmo contêiner do Fluid ao qual o modo de exibição de estágio está conectado. Esse contêiner pode ser usado para se comunicar com o modo de exibição de estágio. Verifique se você está se comunicando com o modo de exibição de estágio _e o modo de exibição do painel lateral_ de todos.

O modo de exibição do painel lateral do exemplo solicita que o usuário selecione o botão Compartilhar na janela de conteúdo compartilhado.

```js
const sidePanelTemplate = document.createElement("template");

sidePanelTemplate["innerHTML"] = `
  <style>
    .wrapper { text-align: center }
    .title { font-size: large; font-weight: bolder; }
    .text { font-size: medium; }
  </style>
  <div class="wrapper">
    <p class="title">Lets get started</p>
    <p class="text">Press the share to stage button to share Dice Roller to the meeting stage.</p>
  </div>
`;

function renderSidePanel(elem) {
  elem.appendChild(sidePanelTemplate.content.cloneNode(true));
}
```

## <a name="write-the-settings-view"></a>Gravar o modo de exibição de configurações

A exibição de configurações, `configurationUrl` carregada no manifesto do aplicativo, é mostrada a um usuário quando ele adiciona seu aplicativo pela primeira vez a uma reunião do Teams. Esse modo de exibição permite que o desenvolvedor configure o `contentUrl` para a guia fixada à reunião com base na entrada do usuário. Esta página é necessária no momento, mesmo que nenhuma entrada do usuário seja necessária para definir o `contentUrl`.

> [!NOTE]
> Não há suporte para [joinContainer() do Live](/javascript/api/@microsoft/live-share/liveshareclient#@microsoft-live-share-liveshareclient-joincontainer) Share no contexto da `settings` guia.

O modo de exibição de configurações do exemplo solicita que o usuário selecione o botão Salvar.

```js
const settingsTemplate = document.createElement("template");

settingsTemplate["innerHTML"] = `
  <style>
    .wrapper { text-align: center }
    .title { font-size: large; font-weight: bolder; }
    .text { font-size: medium; }
  </style>
  <div class="wrapper">
    <p class="title">Welcome to Dice Roller!</p>
    <p class="text">Press the save button to continue.</p>
  </div>
`;

function renderSettings(elem) {
  elem.appendChild(settingsTemplate.content.cloneNode(true));

  // Save the configurable tab
  pages.config.registerOnSaveHandler((saveEvent) => {
    pages.config.setConfig({
      websiteUrl: window.location.origin,
      contentUrl: window.location.origin + "?inTeams=1&view=content",
      entityId: "DiceRollerFluidLiveShare",
      suggestedDisplayName: "DiceRollerFluidLiveShare",
    });
    saveEvent.notifySuccess();
  });

  // Enable the Save button in config dialog
  pages.config.setValidityState(true);
}
```

## <a name="test-locally"></a>Testar localmente

Você pode testar seu aplicativo localmente, usando `npm run start`. Para obter mais informações, consulte o [Guia de Início Rápido](./teams-live-share-quick-start.md).

## <a name="test-in-teams"></a>Testar no Teams

Depois de começar a executar seu aplicativo localmente com `npm run start`, você poderá testar seu aplicativo em Teams. Se você quiser testar seu aplicativo sem implantação, baixe e use o [`ngrok`](https://ngrok.com/) serviço de túnel.

### <a name="create-a-ngrok-tunnel-to-allow-teams-to-reach-your-app"></a>Criar um túnel ngrok para permitir que o Teams acesse seu aplicativo

1. [Baixar ngrok](https://ngrok.com/download).

1. Use o ngrok para criar um túnel com a porta 8080. Execute o seguinte comando:

   ```bash
    ngrok http 8080 --host-header=localhost
   ```

   Um novo terminal ngrok é aberto com uma nova URL, por exemplo `https:...ngrok.io`. A nova URL é o túnel que aponta para seu aplicativo, que precisa ser atualizado em seu aplicativo `manifest.json`.

### <a name="create-the-app-package-to-sideload-into-teams"></a>Criar o pacote do aplicativo para realizar o sideload no Teams

1. Ir para a pasta de exemplo `\live-share-sdk\samples\01.dice-roller` do Dice Roller no computador. Você também pode verificar o [`.\manifest\manifest.json`](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller/manifest) do exemplo do Dice Roller no GitHub.

1. Abra manifest.json e atualize a URL de configuração.

   Substitua `https://<<BASE_URI_DOMAIN>>` pelo ponto de extremidade http do ngrok.

1. Você pode atualizar essas propriedades nas seguintes situações:

   - Defina `developer.name` como seu nome.
   - Atualize `developer.websiteUrl` com seu site.
   - Atualize `developer.privacyUrl` com sua política de privacidade.
   - Atualize `developer.termsOfUseUrl` com seus termos de uso.

1. Compacte o conteúdo da pasta de manifesto para criar `manifest.zip`. Verifique se `manifest.zip` contém apenas o arquivo de origem `manifest.json`, o ícone `color` e o ícone `outline`.

   1. No Windows, selecione todos os arquivos no diretório `.\manifest` e compacte-os.

   > [!NOTE]
   >
   > - Não compacte a pasta que o contém.
   > - Dê um nome descritivo ao arquivo ZIP. Por exemplo, `DiceRollerLiveShare`.

   Para obter mais informações sobre o manifesto, visite a [documentação do manifesto do Teams](../resources/schema/manifest-schema.md)

### <a name="sideload-your-app-into-a-meeting"></a>Fazer sideload do aplicativo em uma reunião

1. Abra o Teams.

1. Agende uma reunião no calendário do Teams. Certifique-se de convidar pelo menos um participante para a reunião.

1. Ingresse na reunião.

1. Na janela de reunião na parte superior, selecione **+ Aplicativos** > **Gerenciar aplicativos**.

1. No painel **Gerenciar aplicativos**, selecione **Carregar um aplicativo personalizado**.

   1. Se você não vir a opção para **Carregar aplicativo personalizado**, siga as [instruções](/microsoftteams/teams-custom-app-policies-and-settings) para habilitar aplicativos personalizados em seu locatário.

1. Selecione e carregue o arquivo `manifest.zip` do computador.

1. Selecione **Adicionar** para adicionar seu aplicativo de exemplo à reunião.

1. Selecione **+ Aplicativos**, digite Dice Roller na caixa de pesquisa de **Localizar um aplicativo**.

1. Selecione o aplicativo para ativá-lo na reunião.

1. Selecione **Salvar**.

   O aplicativo Dice Roller é adicionado ao painel de reunião do Teams.

1. No painel lateral, selecione o ícone Compartilhar na janela de conteúdo compartilhado. O Teams inicia uma sincronização ao vivo com os usuários no estágio de reunião na reunião.

   :::image type="content" source="../assets/images/teams-live-share/teams-live-share-to-stage.png" alt-text="ícone compartilhar na janela de conteúdo compartilhado":::

   Agora você deve ver o rolador de dados no estágio de reunião.

   :::image type="content" source="../assets/images/teams-live-share/teams-live-share-meeting-stage.png" alt-text="imagem do estágio de reunião":::

Os usuários convidados para a reunião podem ver seu aplicativo na janela de conteúdo compartilhado quando ingressam na reunião.

## <a name="deployment"></a>Implantação

Depois de se preparar para implantar seu código, você pode usar o [Kit de Ferramentas do Teams](../toolkit/provision.md#provision-using-teams-toolkit-in-visual-studio-code) ou o [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/apps) para provisionar e carregar o arquivo ZIP do aplicativo.

> [!NOTE]
> Você precisa adicionar seu appId provisionado ao `manifest.json` antes de carregar ou distribuir o aplicativo.

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo | Descrição                                                     | JavaScript                                                                           |
| :---------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Dice Roller | Habilite todos os clientes conectados para rolar um dado e exibir o resultado. | [Exibir](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Principais recursos](teams-live-share-capabilities.md)

## <a name="see-also"></a>Confira também

- [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
- [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
- [Documentos de referência do SDK de Mídia do Live Share](/javascript/api/@microsoft/live-share-media/)
- [Perguntas frequentes do Live Share](teams-live-share-faq.md)
- [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
