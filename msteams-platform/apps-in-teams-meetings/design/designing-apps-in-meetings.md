---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Aprenda a projetar aplicativos em reuniões Teams e obtenha o kit de interface do usuário Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 0a888c333305e9caafcd0bac0e5549bf08ead424
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566023"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Projetando sua extensão de reunião de Microsoft Teams

Você pode criar aplicativos para tornar as reuniões mais produtivas. Por exemplo, peça às pessoas para concluir uma pesquisa durante uma chamada ou enviar um lembrete rápido que não interrompa o fluxo da reunião.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode pegar e modificar conforme necessário, no Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Adicione uma extensão de reunião

Você pode adicionar uma extensão de reunião antes e durante as reuniões. Você também pode adicionar um aplicativo para uma reunião específica diretamente da loja Teams (AppSource).

### <a name="add-before-a-meeting"></a>Adicione antes de uma reunião

Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a>Adicione durante uma reunião

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a>Antes de uma reunião

Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de pesquisa que as pessoas responderão durante a chamada.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como app conteúdo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomia: Guia de reunião (antes e depois das reuniões)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: Etiqueta de navegação para sua guia.|
|2|**Estouro da** guia : Abre ações de guia, como renomear e remover.|
|3|**iframe**: Exibe o conteúdo do seu aplicativo.|

### <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua guia de reunião:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Um painel de instrumentos é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.
* [Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia precisar de alguma navegação. Em geral, você deve manter a navegação de controle ao mínimo.

## <a name="use-an-in-meeting-tab"></a>Use uma guia de reunião

A guia de reunião é uma tela para aumentar a colaboração durante as reuniões. Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do palco de reuniões através de visualizações compartilhadas ou baseadas em papéis.

### <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia de reunião para:

* Forneça feedback detalhado. Por exemplo, avalie um candidato a emprego.
* Crie uma enquete, pesquisa ou item de tarefa para os participantes da reunião.
* Notas de exibição relevantes para a reunião. Por exemplo, informações sobre um lead de vendas.

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar o conteúdo da enquete em uma guia de reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomia: Guia de encontros

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de encontro." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.|
|2|**Nome do aplicativo**|
|3|**Cabeçalho**: Inclui o nome do seu aplicativo.|
|4 |**Botão de fechamento**: Dispensa a guia. Use sempre o ícone de fechamento superior direito em vez de uma ação no rodapé.|
|5 |**Barra de notificação**: Os alertas de erro são exibidos diretamente abaixo do cabeçalho e empurram o conteúdo do iframe para baixo em 20 pixels.|
|6 |**iframe**: Exibe o conteúdo do seu aplicativo.|

### <a name="spacing"></a>Espaçamento

Otimize sua guia de reunião para caber borda a ponta dentro da área de iframe de 280 pixels de largura. Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o cabeçalho da guia. O iframe está sangrando até a parte inferior da guia.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento de guias em reunião." border="false":::

### <a name="scrolling"></a>Rolagem

O conteúdo de iframe deve rolar verticalmente. Você só pode ver o conteúdo para o qual rolou (nada acima ou abaixo). A barra de rolagem faz parte do conteúdo do iframe.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia de reunião rola." border="false":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária. Os usuários devem ser capazes de voltar à camada anterior.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra navegação em reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Use um diálogo de reunião

Diálogos em reunião são exibidos na Teams fase de reunião. Eles exigem a atenção, confirmação ou interação do usuário, mas são sutis e não interrompem a reunião. Você deve usá-los com moderação e para cenários que sejam leves e orientados para tarefas.

### <a name="use-cases"></a>Casos de uso

Diálogos de reunião são acionados por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Fornecer um breve feedback
* Faça uma pequena pesquisa ou enquete
* Enviar aprovações
* Receber lembretes

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar um diálogo de reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomia: Diálogo de encontro

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um diálogo em reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Cabeçalho**: Inclui ícone de aplicativo, nome, string de ação e ícone de fechamento.|
|2|**iframe**: Exibe o conteúdo do seu aplicativo.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomia: Cabeçalho de diálogo de reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um cabeçalho de diálogo em reunião." border="false":::

Há duas variantes de cabeçalho. Quando possível, use a variante com o avatar para reforçar que o diálogo vem de uma pessoa.

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: Pessoa que inicia o diálogo de reunião.|
|2|**ícone de aplicativo**|
|3|**Nome do aplicativo**|
|4 |**Botão de fechamento**: Dispensa o diálogo.|
|5 |**Cadeia de** ação : Normalmente descreve quem iniciou o diálogo.|

### <a name="responsive-behavior"></a>Comportamento dinâmico

Diálogos de encontro podem variar de tamanho para explicar diferentes cenários. Certifique-se de manter o preenchimento e os tamanhos dos componentes.

* **Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro da faixa de tamanho suportada.
* **Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro da faixa de tamanho suportada. Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.

Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra o diálogo de reunião. Largura: Min-280 pixels (248 pixels iframe). Max-460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a>Após uma reunião

Você pode voltar a uma reunião depois que terminar e visualizar o conteúdo do aplicativo. Neste exemplo, o organizador da reunião pode analisar os resultados das pesquisas na guia **Contoso.** (Nota: Do ponto de vista do design, não há diferença entre a experiência de guia pré e pós-reunião.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração do exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Faça: Limite o número de interações

Para diálogos de encontro, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: Introduza elementos desnecessários

Um único diálogo de encontro com múltiplas interações pode distrair a chamada.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de diálogo de uma única coluna." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Faça: Use um layout de diálogo de uma única coluna

Como os diálogos estão no centro da fase de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve bagunçar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a>Não: Desordene o espaço

Conteúdo denso ou excessivamente estruturado pode ser perturbador e avassalador, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de uma única coluna." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Faça: Use um layout de guia de uma única coluna

Dada a natureza estreita da guia de reunião, recomendamos fortemente exibir o conteúdo em uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a>Não: Use várias colunas

Devido ao espaço limitado da guia de reunião, não são recomendados layouts com mais de uma coluna.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Controles

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar os controles primários de direita." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Faça: Alinhar direito a ação primária

Recomendamos posicionar a ação mais visualmente pesada para o local mais certo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Não: Ações de alinhamento de esquerda ou centro

Isso se desvia do padrão Teams padrão para colocação de controle em um diálogo e pode entrar em conflito com um diálogo atrás do topo.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Rolar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando rolagem vertical em uma guia de reunião." border="false":::

#### <a name="do-scroll-vertically"></a>Faça: Role verticalmente

Os usuários esperam rolagem vertical em Teams (e em outros lugares).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando rolagem horizontal em uma guia de reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a>Não: Role horizontalmente

A rolagem horizontal não é um comportamento esperado em Teams. Outras telas no ambiente de reunião rolam verticalmente.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Fluxos de trabalho

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia de reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Faça: Cenários complexos de superfície na guia de reunião

Se o seu aplicativo incluir várias tarefas, recomendamos fortemente o uso de uma guia de reunião com um layout de uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em um diálogo presencial." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Não: Torne os diálogos em reunião complexos

Diálogos de reunião destinam-se a interações breves.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Faça: Use tokens de cor Teams

Teams reuniões são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado. Saiba mais sobre o uso <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">de tokens de cores (Fluent UI)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (leve)." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Não: Valores hexax de código rígido

Se você não usar Teams tokens de cor, seus designs serão menos escaláveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão traseiro." border="false":::

#### <a name="do-have-a-back-button"></a>Faça: Tenha um botão traseiro

Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem ser capazes de voltar às suas visualizações anteriores.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Não: Inclua outro botão de descarte

Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, uma vez que já há um botão no cabeçalho para descartar a própria guia de reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) dentro de uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Atenção: Evite modais dentro da guia de reunião

Modais (também conhecidos como módulos de tarefa) na já estreita guia de reunião podem embrulhar e obscurecer o conteúdo.

   :::column-end:::
:::row-end:::
