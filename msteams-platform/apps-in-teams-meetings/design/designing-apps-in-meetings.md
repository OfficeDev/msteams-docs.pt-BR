---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões do Teams e obter o Kit de interface do usuário do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: c6e76356b698da4e32e279b0842ab2cc35254e99
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886755"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Projetando sua extensão de reunião do Microsoft Teams

Você pode criar aplicativos para tornar as reuniões mais produtivas. Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obter o Kit de Interface do Usuário do Microsoft Teams (Kit de Interface do Usuário do Microsoft Teams)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Adicionar uma extensão de reunião

Você pode adicionar uma extensão de reunião antes e durante as reuniões. Você também pode adicionar um aplicativo para uma reunião específica diretamente da loja do Teams (AppSource).

### <a name="add-before-a-meeting"></a>Adicionar antes de uma reunião

Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a>Adicionar durante uma reunião

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que você deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a>Antes de uma reunião

Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho da pesquisa que as pessoas responderão durante a chamada.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como aplicativo conteúdo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomia: guia Reunião (antes e depois das reuniões)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da** guia: rótulo de navegação da guia.|
|2 |**Estouro de** guia: abre ações da guia, como renomear e remover.|
|3|**iframe:** exibe o conteúdo do aplicativo.|

### <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Teams para ajudar a projetar sua guia de reunião:

* [Lista:](../../concepts/design/design-teams-app-ui-templates.md#list)as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas: um quadro de tarefas, às vezes chamado de quadro kanban ou trilhos de mesa, é uma coleção de cartões frequentemente usada para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)um painel é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar entradas do usuário de maneira estruturada.
* [Estado vazio:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.
* [Navegação à esquerda:](../../concepts/design/design-teams-app-ui-templates.md#left-nav)o modelo de navegação à esquerda pode ajudar se a guia exigir alguma navegação. Em geral, você deve manter a navegação por tabulação no mínimo.

## <a name="use-an-in-meeting-tab"></a>Usar uma guia na reunião

A guia na reunião é uma tela para aumentar a colaboração durante as reuniões. Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio da reunião por meio de exibições compartilhadas ou baseadas em função.

### <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia na reunião para:

* Fornecer comentários detalhados (por exemplo, avaliar um candidato a trabalho)
* Criar rapidamente um poll, uma pesquisa ou um item de tarefa para os participantes da reunião
* Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar conteúdo de sondagem em uma guia na reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomia: guia Na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do aplicativo (selecionado)**: logotipo do aplicativo transparente de 16 pixels.|
|2 |**Nome do aplicativo**|
|3|**Header**: inclui o nome do aplicativo.|
|4 |**Botão Fechar:** descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.|
|5 |**Barra de notificação:** os alertas de erro são exibidos diretamente abaixo do título e baixam o conteúdo do iframe em 20 pixels.|
|6 |**iframe:** exibe o conteúdo do aplicativo.|

### <a name="spacing"></a>Espaçamento

Otimize a guia na reunião para ajustar de ponta a ponta dentro da área de iframe de 280 pixels. Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header da guia. O iframe está com sangramento completo na parte inferior da guia.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="O exemplo mostra as dimensões de espaçamento de tabulação na reunião." border="false":::

### <a name="scrolling"></a>Rolagem

O conteúdo do Iframe deve rolar verticalmente. Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo). A barra de rolagem faz parte do conteúdo do iframe.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo intenso, recomendamos permitir que os usuários naveguem até uma camada secundária. Os usuários devem poder voltar à camada anterior.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="O exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Usar uma caixa de diálogo na reunião

As caixas de diálogo na reunião são exibidas no estágio de reunião do Teams. Eles exigem a atenção, a confirmação ou a interação do usuário, mas são sutis e não interrompem a reunião. Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.

### <a name="use-cases"></a>Casos de uso

As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Fornecer comentários breves
* Fazer uma pequena pesquisa ou sondagem
* Enviar aprovações
* Receber lembretes

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomia: Caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma caixa de diálogo em reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Header:** inclui ícone do aplicativo, nome, cadeia de caracteres de ação e ícone fechar.|
|2 |**iframe:** exibe o conteúdo do aplicativo.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomia: No-meeting dialog header

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um header de caixa de diálogo em reunião." border="false":::

Há duas variantes de header. Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: pessoa que inicia a caixa de diálogo na reunião.|
|2 |**ícone de aplicativo**|
|3|**Nome do aplicativo**|
|4 |**Botão Fechar:** descarta a caixa de diálogo.|
|5 |**Cadeia de caracteres** de ação: normalmente descreve quem iniciou a caixa de diálogo.|

### <a name="responsive-behavior"></a>Comportamento dinâmico

As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes. Certifique-se de manter os tamanhos de preenchimento e componente.

* **Largura**: a largura do iframe é um valor absoluto dentro do intervalo especificado.
* **Altura**: a altura da caixa de diálogo é determinada pelo conteúdo no iframe. A rolagem vertical assume o controle do conteúdo que excede a altura máxima.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (iframe de 248 pixels). Máx--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a>Após uma reunião

Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo. Neste exemplo, o organizador da reunião pode ver os resultados da votação na guia **Contoso.** (Observação: do ponto de vista do design, não há nenhuma diferença entre a experiência de guia pré e pós-reunião.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="O exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Fazer: limitar o número de interações

Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: introduzir elementos desnecessários

Uma única caixa de diálogo de reunião com várias interações pode distrair a chamada.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Fazer: Usar um layout de caixa de diálogo de coluna única

Como as caixas de diálogo estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve desorganar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a>Não: desorganmente o espaço

Conteúdo densa ou muito estruturada pode distrair e sobrecarregar, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Fazer: Usar um layout de guia de coluna única

Dada a natureza estreita da guia na reunião, é recomendável exibir o conteúdo em uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a>Não: use várias colunas

Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Controles

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Fazer: Alinhar à direita a ação principal

Recomendamos posicionar a ação mais intensa visualmente no local mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve alinhar à esquerda os controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Não: ações de alinhamento à esquerda ou ao centro

Isso se desvia do padrão do Teams para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da superior.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Rolar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a>Fazer: rolar verticalmente

Os usuários esperam rolagem vertical no Teams (e em outro lugar).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a>Não: rolar horizontalmente

A rolagem horizontal não é um comportamento esperado no Teams. Outras telas no ambiente de reunião rolam verticalmente.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Fluxos de trabalho

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia na reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Surface complex scenarios in the in-meeting tab

Se seu aplicativo incluir várias tarefas, recomendamos o uso de uma guia na reunião com um layout de coluna única.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Não: tornar as caixas de diálogo na reunião complexas

As caixas de diálogo na reunião destinam-se a breves interações.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Use tokens de cor do Teams

As reuniões do Teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitiva para que os usuários possam se concentrar na discussão e no conteúdo compartilhado. Saiba como usar <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário do Fluent).</a>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (claro)." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Não: codificar valores hexaxa

Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão Voltar." border="false":::

#### <a name="do-have-a-back-button"></a>Fazer: ter um botão Voltar

Se você tiver mais de uma camada de navegação em uma guia na reunião, os usuários deverão poder voltar para suas exibições anteriores.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de dismiss." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Não: incluir outro botão de descartar

Fornecer uma opção para fechar o conteúdo da guia na reunião pode causar problemas, pois já existe um botão no título para descartar a própria guia de reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia na reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Cuidado: evite modais na guia na reunião

Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem quebrar e ocultar o conteúdo.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Validar seu design

Se você planeja publicar seu aplicativo no AppSource, deve entender os problemas de design que normalmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
