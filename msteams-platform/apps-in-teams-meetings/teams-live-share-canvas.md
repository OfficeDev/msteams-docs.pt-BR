---
title: Visão geral da tela do Live Share
author: surbhigupta
description: Neste módulo, saiba mais sobre a tela do Live Share, uma extensão que permite inking, ponteiros a laser e cursores para aplicativos de reunião.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 10/04/2022
ms.openlocfilehash: 11f465072d496f466df28c37b8eee7289bae4180
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791444"
---
# <a name="live-share-canvas-overview"></a>Visão geral da tela do Live Share

:::image type="content" source="../assets/images/teams-live-share/live-share-canvas-docs-feature-1.png" alt-text="A captura de tela mostra um exemplo de uma tela em sincronia com outros participantes da reunião em uma reunião do Teams.":::

Em salas de conferência e salas de aula em todo o mundo, os quadros de brancos são uma parte fundamental da colaboração. Nos tempos modernos, no entanto, o quadro de brancos não é mais suficiente. Com inúmeras ferramentas digitais como o PowerPoint sendo o ponto focal da colaboração na era moderna, é essencial habilitar o mesmo potencial criativo.

Para habilitar uma colaboração mais perfeita, a Microsoft criou PowerPoint Live, que se tornou fundamental para a forma como as pessoas trabalham no Microsoft Teams. Os apresentadores podem anotar em slides para que todos vejam, usando canetas, marcadores e ponteiros laser para chamar a atenção para os principais conceitos. Usando a tela Do Live Share, seu aplicativo pode trazer o poder de PowerPoint Live ferramentas de incrustação com o mínimo de esforço.

## <a name="install"></a>Instalar

Para adicionar a versão mais recente do SDK ao seu aplicativo usando npm:

```bash
npm install @microsoft/live-share@next --save
npm install @microsoft/live-share-canvas@next --save
```

OU

Para adicionar a versão mais recente do SDK ao seu aplicativo usando [Yarn](https://yarnpkg.com/):

```bash
yarn add @microsoft/live-share@next
yarn add @microsoft/live-share-canvas@next
```

## <a name="setting-up-the-package"></a>Configurando o pacote

A tela Live Share tem duas classes primárias que permitem a colaboração de chave de turno: `InkingManager` e `LiveCanvas`. `InkingManager` é responsável por anexar um elemento totalmente em `<canvas>` destaque ao seu aplicativo, enquanto `LiveCanvas` gerencia a sincronização remota com outros participantes da reunião. Usado em conjunto, seu aplicativo pode ter uma funcionalidade completa em forma de quadro em apenas algumas linhas de código.

| Aulas                                                                     | Descrição                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [InkingManager](/javascript/api/@microsoft/live-share-canvas/inkingmanager) | Classe que anexa um `<canvas>` elemento a um determinado `<div>` para gerenciar automaticamente traços de caneta ou marcador, ponteiro laser, linhas e setas e apagadores. Expõe um conjunto de APIs (para controlar qual ferramenta está ativa) e configurações básicas. |
| [LiveCanvas](/javascript/api/@microsoft/live-share-canvas/livecanvas)      | Uma `SharedObject` classe que sincroniza traços e posições de cursor de `InkingManager` para todos em uma sessão do Live Share.                                                                                                                   |

Exemplo:

```html
<body>
  <div id="canvas-host"></div>
</body>
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient } from "@microsoft/live-share";
import { InkingManager, LiveCanvas } from "@microsoft/live-share-canvas";

// Setup the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { liveCanvas: LiveCanvas },
};
const { container } = await liveShare.joinContainer(schema);
const { liveCanvas } = container.initialObjects;

// Get the canvas host element
const canvasHostElement = document.getElementById("canvas-host");
const inkingManager = new InkingManager(canvasHostElement);

// Begin synchronization for LiveCanvas
await liveCanvas.initialize(inkingManager);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient } from "@microsoft/live-share";
import { InkingManager, LiveCanvas } from "@microsoft/live-share-canvas";
import { ContainerSchema } from "fluid-framework";

// Setup the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { liveCanvas: LiveCanvas },
};
const { container } = await liveShare.joinContainer(schema);
const liveCanvas = container.initialObjects.liveCanvas as LiveCanvas;

// Get the canvas host element
const canvasHostElement = document.getElementById("canvas-host");
const inkingManager = new InkingManager(canvasHostElement);

// Begin synchronization for LiveCanvas
await liveCanvas.initialize(inkingManager);
```

---

## <a name="canvas-tools-and-cursors"></a>Ferramentas de tela e cursores

Agora que a tela do Live Share está configurada e sincronizada, você pode configurar a tela para interação do usuário, como botões para selecionar uma ferramenta de caneta. Nesta seção, discutiremos quais ferramentas estão disponíveis e como usá-las.

### <a name="inking-tools"></a>Ferramentas de incrustação

Cada ferramenta de incrustação na tela do Live Share renderiza traços à medida que os usuários desenham. Se usar uma tela sensível ao toque ou caneta, as ferramentas também dão suporte à dinâmica de pressão, afetando a largura do traço. As configurações incluem cor do pincel, espessura, forma e uma seta final opcional.

#### <a name="pen-tool"></a>Ferramenta de caneta

:::image type="content" source="../assets/images/teams-live-share/canvas-pen-tool.gif" alt-text="O GIF mostra um exemplo de traços de desenho na tela usando a ferramenta de caneta.":::

A ferramenta de caneta desenha traços sólidos que são armazenados na tela. A forma de dica padrão é um círculo.

```html
<div>
  <button id="pen">Enable Pen</button>
  <label for="pen-color">Select a color:</label>
  <input type="color" id="color" name="color" value="#000000" />
  <button id="pen-tip-size">Increase pen size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to pen
document.getElementById("pen").onclick = () => {
  inkingManager.tool = InkingTool.pen;
};
// Change the selected color for pen
document.getElementById("pen-color").onchange = () => {
  const colorPicker = document.getElementById("color");
  inkingManager.penBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for pen
document.getElementById("pen-tip-size").onclick = () => {
  inkingManager.penBrush.tipSize = inkingManager.penBrush.tipSize + 1;
};
```

#### <a name="highlighter-tool"></a>Ferramenta realçador

:::image type="content" source="../assets/images/teams-live-share/canvas-highlighter-tool.gif" alt-text="O GIF mostra um exemplo de traços translúcidos de desenho na tela usando a ferramenta de realce.":::

A ferramenta de realce desenha traços translúcidos armazenados na tela. A forma de dica padrão é um quadrado.

```html
<div>
  <button id="highlighter">Enable Highlighter</button><br />
  <label for="highlighter-color">Select a color:</label>
  <input type="color" id="highlighter-color" name="highlighter-color" value="#FFFC00" />
  <button id="highlighter-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to highlighter
document.getElementById("highlighter").onclick = () => {
  inkingManager.tool = InkingTool.highlighter;
};
// Change the selected color for highlighter
document.getElementById("highlighter-color").onchange = () => {
  const colorPicker = document.getElementById("highlighter-color");
  inkingManager.highlighterBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for highlighter
document.getElementById("highlighter-tip-size").onclick = () => {
  inkingManager.highlighterBrush.tipSize = inkingManager.penBrush.tipSize + 1;
};
```

#### <a name="eraser-tool"></a>Ferramenta borracha

:::image type="content" source="../assets/images/teams-live-share/canvas-eraser-tool.gif" alt-text="O GIF mostra um exemplo de apagamento de traços na tela usando a ferramenta borracha.":::

A ferramenta borracha apaga traços inteiros que cruzam seu caminho.

```html
<div>
  <button id="eraser">Enable Eraser</button><br />
  <button id="eraser-size">Increase eraser size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to eraser
document.getElementById("eraser").onclick = () => {
  inkingManager.tool = InkingTool.eraser;
};
// Increase the tip size for eraser
document.getElementById("eraser-size").onclick = () => {
  inkingManager.eraserSize = inkingManager.eraserSize + 1;
};
```

#### <a name="point-eraser-tool"></a>Ferramenta de borracha de ponto

:::image type="content" source="../assets/images/teams-live-share/canvas-point-eraser-tool.gif" alt-text="O GIF mostra um exemplo de remoção de pontos individuais dentro de traços na tela usando a ferramenta de borracha de ponto.":::

A ferramenta borracha de ponto apaga pontos individuais dentro de traços que cruzam seu caminho dividindo traços existentes pela metade. Essa ferramenta é computacionalmente cara e pode resultar em taxas de quadro mais lentas para seus usuários.

> [!NOTE]
> A borracha de ponto compartilha o mesmo tamanho de ponto de borracha que a ferramenta de borracha regular.

```html
<div>
  <button id="point-eraser">Enable Point Eraser</button><br />
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to eraser
document.getElementById("point-eraser").onclick = () => {
  inkingManager.tool = InkingTool.pointEraser;
};
```

#### <a name="laser-pointer"></a>Ponteiro laser

:::image type="content" source="../assets/images/teams-live-share/canvas-laser-tool.gif" alt-text="GIF mostra um exemplo de traços de desenho na tela usando a ferramenta ponteiro laser.":::

O ponteiro laser é exclusivo, pois a ponta do laser tem um efeito à medida que você move o mouse. Quando você desenha traços, o efeito à direita renderiza por um curto período antes que ele desapareça completamente. Essa ferramenta é perfeita para apontar informações na tela durante uma reunião, pois o apresentador não precisa alternar entre ferramentas para apagar traços.

```html
<div>
  <button id="laser">Enable Laser Pointer</button><br />
  <label for="laser-color">Select a color:</label>
  <input type="color" id="laser-color" name="laser-color" value="#000000" />
  <button id="laser-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to laser pointer
document.getElementById("laser").onclick = () => {
  inkingManager.tool = InkingTool.highlighter;
};
// Change the selected color for laser pointer
document.getElementById("laser-color").onchange = () => {
  const colorPicker = document.getElementById("laser-color");
  inkingManager.laserPointerBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for laser pointer
document.getElementById("laser-tip-size").onclick = () => {
  inkingManager.laserPointerBrush.tipSize = inkingManager.laserPointerBrush.tipSize + 1;
};
```

#### <a name="line-and-arrow-tools"></a>Ferramentas de linha e seta

:::image type="content" source="../assets/images/teams-live-share/canvas-line-tool.gif" alt-text="GIF mostra um exemplo de desenho de linhas retas em uma tela usando a ferramenta de linha e seta .":::

A ferramenta de linha permite que os usuários desenhe linhas retas de um ponto para outro, com uma seta opcional que pode ser aplicada ao final.

```html
<div>
  <button id="line">Enable Line</button><br />
  <button id="line-arrow">Enable Arrow</button><br />
  <input type="color" id="line-color" name="line-color" value="#000000" />
  <button id="line-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to line
document.getElementById("line").onclick = () => {
  inkingManager.tool = InkingTool.line;
  inkingManager.lineBrush.endArrow = "none";
};
// Change the selected tool to line
document.getElementById("line-arrow").onclick = () => {
  inkingManager.tool = InkingTool.line;
  inkingManager.lineBrush.endArrow = "open";
};
// Change the selected color for lineBrush
document.getElementById("line-color").onchange = () => {
  const colorPicker = document.getElementById("line-color");
  inkingManager.lineBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for lineBrush
document.getElementById("line-tip-size").onclick = () => {
  inkingManager.lineBrush.tipSize = inkingManager.lineBrush.tipSize + 1;
};
```

#### <a name="clear-all-strokes"></a>Limpar todos os traços

Você pode limpar todos os traços na tela chamando `inkingManager.clear()`. Isso exclui todos os traços da tela.

### <a name="cursors"></a>Cursores

:::image type="content" source="../assets/images/teams-live-share/canvas-cursors.gif" alt-text="GIF mostra um exemplo de usuários compartilhando um cursor em uma tela.":::

Você pode habilitar cursores ao vivo em seu aplicativo para que os usuários acompanhem as posições do cursor uns dos outros na tela. Ao contrário das ferramentas de incrustação, os cursores operam inteiramente por meio da `LiveCanvas` classe. Opcionalmente, você pode fornecer um nome e uma imagem para identificar cada usuário. Você pode habilitar cursores separadamente ou com as ferramentas de incrustação.

```javascript
// Optional. Set user display info
liveCanvas.onGetLocalUserInfo = () => {
  return {
    displayName: "YOUR USER NAME",
    pictureUri: "YOUR USER PICTURE URI",
  };
};
// Toggle Live Canvas cursor enabled state
liveCanvas.isCursorShared = !isCursorShared;
```

## <a name="optimizing-across-devices"></a>Otimização entre dispositivos

Para a maioria dos aplicativos na Web, o conteúdo é renderizado de forma diferente, dependendo do tamanho da tela ou do estado variável do aplicativo. Se `InkingManager` não for otimizado corretamente para seu aplicativo, isso poderá fazer com que traços e cursores apareçam de forma diferente para cada usuário. A tela Live Share dá suporte a um conjunto simples de APIs, que permite ajustar posições `<canvas>` de traço para se alinhar corretamente com seu conteúdo.

Por padrão, a tela do Live Share funciona muito como um aplicativo de quadro de dados, com o conteúdo sendo alinhado ao modo de exibição com um nível de zoom de 1x. Somente parte do conteúdo está sendo renderizada dentro dos limites visíveis do `<canvas>`. Conceitualmente, é como gravar um vídeo do modo de vista do pássaro. Enquanto o visor da câmera está gravando uma parte do mundo abaixo dela, o mundo real se estende quase infinitamente em todas as direções.

Aqui está um diagrama simples para ajudar a visualizar este conceito:

:::image type="content" source="../assets/images/teams-live-share/live-share-canvas-capabilities-docs-diagram-1.png" alt-text="A captura de tela mostra o layout da tela inteira para usuários da área de trabalho e móveis juntos.":::

Você pode personalizar esse comportamento das seguintes maneiras:

- Alterando o ponto de referência inicial para o canto superior esquerdo da tela.
- Altere as posições de deslocamento de pixel x e y do modo de exibição.
- Altere o nível de escala do modo de exibição.

> [!NOTE]
> Os pontos de referência, deslocamentos e níveis de escala são locais para o cliente e não são sincronizados entre os participantes da reunião.

Exemplo:

```html
<body>
  <button id="pan-left">Pan left</button>
  <button id="pan-up">Pan up</button>
  <button id="pan-right">Pan right</button>
  <button id="pan-down">Pan down</button>
  <button id="zoom-out">Zoom out</button>
  <button id="zoom-in">Zoom in</button>
  <button id="change-reference">Change reference</button>
</body>
```

```javascript
// ...

// Pan left
document.getElementById("pan-left").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x - 10,
    y: inkingManager.offset.y,
  };
};
// Pan up
document.getElementById("pan-up").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x,
    y: inkingManager.offset.y - 10,
  };
};
// Pan right
document.getElementById("pan-right").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x + 10,
    y: inkingManager.offset.y,
  };
};
// Pan down
document.getElementById("pan-down").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x,
    y: inkingManager.offset.y + 10,
  };
};
// Zoom out
document.getElementById("zoom-out").onclick = () => {
  if (inkingManager.scale > 0.1) {
    inkingManager.scale -= 0.1;
  }
};
// Zoom in
document.getElementById("zoom-in").onclick = () => {
  inkingManager.scale += 0.1;
};
// Change reference
document.getElementById("change-reference").onclick = () => {
  if (inkingManager.referencePoint === "center") {
    inkingManager.referencePoint = "topLeft";
  } else {
    inkingManager.referencePoint = "center";
  }
};
```

## <a name="ideal-scenarios"></a>Cenários ideais

Com páginas da Web chegando em todas as formas e tamanhos, não é possível fazer a tela do Live Share para dar suporte a todos os cenários. O pacote é ideal para cenários em que todos os usuários estão olhando para o mesmo conteúdo ao mesmo tempo. Embora nem todo o conteúdo precise estar visível na tela, ele deve ser o conteúdo que é dimensionado entre dispositivos linearmente.

Aqui estão alguns exemplos de cenários em que a tela do Live Share é uma ótima opção para seu aplicativo:

- Sobreponha imagens e vídeos que renderizam com a mesma proporção em todos os clientes.
- Exibindo um mapa, um modelo 3D ou um quadro de dados do mesmo ângulo de rotação.

Ambos os cenários funcionam bem porque o conteúdo pode ser exibido o mesmo em todos os dispositivos, mesmo que os usuários estejam olhando para ele com diferentes níveis de zoom e deslocamentos. Se o layout ou o conteúdo do seu aplicativo mudar dependendo do tamanho da tela e não for possível gerar uma exibição comum para todos os participantes, a tela do Live Share pode não ser uma boa opção para o seu cenário.

## <a name="code-samples"></a>Exemplos de código

| Nome do exemplo          | Descrição                            | JavaScript                                                                                |
| -------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------- |
| Demonstração do Live Canvas     | Aplicativo de quadro de dados simples.         | [Visualizar](https://github.com/microsoft/live-share-sdk/tree/main/samples/03.live-canvas-demo) |
| Modelo de mídia de React | Desenhe um player de vídeo sincronizado. | [View](https://aka.ms/liveshare-mediatemplate)                                            |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tutorial do Agile Poker](../sbs-teams-live-share.yml)

## <a name="see-also"></a>Confira também

- [Perguntas Frequentes do SDK do Live Share](teams-live-share-faq.md)
- [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
- [Documentos de referência do SDK do Live Share Canvas](/javascript/api/@microsoft/live-share-canvas/)
- [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
