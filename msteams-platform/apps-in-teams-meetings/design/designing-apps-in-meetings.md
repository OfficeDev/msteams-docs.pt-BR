---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões do Teams e obter o Microsoft Teams UI Kit.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 022ffdd7341f60a9c6732948a0914383ddb248a8
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018471"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Projetando sua extensão de reunião do Microsoft Teams

Você pode criar aplicativos para tornar as reuniões mais produtivas. Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Adicionar uma extensão de reunião

Você pode adicionar uma extensão de reunião antes e durante as reuniões. Você também pode adicionar um aplicativo para uma reunião específica diretamente da loja do Teams (AppSource).

### <a name="add-before-a-meeting"></a>Adicionar antes de uma reunião

Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a>Adicionar durante uma reunião

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que você deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a>Antes de uma reunião

Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho de pesquisa que as pessoas responderão durante a chamada.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como o conteúdo do aplicativo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomia: guia Reunião (antes e depois das reuniões)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: Rótulo de navegação para sua guia.|
|2|**Estouro da** guia : abre ações de guia, como renomear e remover.|
|3|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Teams para ajudar a projetar sua guia de reunião:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.
* [Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia exigir alguma navegação. Em geral, você deve manter a navegação de tabulação no mínimo.

## <a name="use-an-in-meeting-tab"></a>Usar uma guia em reunião

A guia na reunião é uma tela para aumentar a colaboração durante as reuniões. Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio de reunião por meio de exibições compartilhadas ou baseadas em função.

### <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia na reunião para:

* Fornecer comentários detalhados (por exemplo, avaliar um candidato a trabalho)
* Criar rapidamente uma sondagem, uma pesquisa ou um item de tarefa para os participantes da reunião
* Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar o conteúdo da sondagem em uma guia na reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomia: guia In-meeting

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.|
|2|**Nome do aplicativo**|
|3|**Header**: Inclui o nome do aplicativo.|
|4 |**Botão Fechar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.|
|5 |**Barra de** notificações : Os alertas de erro são exibidos diretamente abaixo do header e pressionam o conteúdo do iframe para baixo em 20 pixels.|
|6 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="spacing"></a>Espaçamento

Otimize sua guia na reunião para caber de ponta a ponta dentro da área de iframe de 280 pixels. Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header de tabulação. O iframe é sangramento total na parte inferior da guia.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento da guia na reunião." border="false":::

### <a name="scrolling"></a>Rolagem

O conteúdo do Iframe deve rolar verticalmente. Você só pode ver o conteúdo que você roleu para (nada acima ou abaixo). A barra de rolagem faz parte do conteúdo do iframe.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária. Os usuários devem poder voltar para a camada anterior.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Usar uma caixa de diálogo na reunião

As caixas de diálogo na reunião são exibidas no estágio de reunião do Teams. Eles exigem a atenção, confirmação ou interação de um usuário, mas são sutis e não interrompem a reunião. Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.

### <a name="use-cases"></a>Casos de uso

As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Fornecer comentários breves
* Fazer uma pesquisa curta ou sondagem
* Enviar aprovações
* Receber lembretes

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomia: caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma caixa de diálogo na reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Header**: Inclui ícone de aplicativo, nome, cadeia de caracteres de ação e ícone de fechamento.|
|2|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomia: header de caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de um header de caixa de diálogo na reunião." border="false":::

Há duas variantes de header. Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: Pessoa que inicia a caixa de diálogo na reunião.|
|2|**ícone de aplicativo**|
|3|**Nome do aplicativo**|
|4 |**Botão Fechar**: descarta a caixa de diálogo.|
|5 |**Cadeia de caracteres** de ação : normalmente descreve quem iniciou a caixa de diálogo.|

### <a name="responsive-behavior"></a>Comportamento dinâmico

As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes. Certifique-se de manter tamanhos de preenchimento e componentes.

* **Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.
* **Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado. Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.

Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (248 pixels iframe). Max--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a>Após uma reunião

Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo. Neste exemplo, o organizador da reunião pode ver os resultados da sondagem na guia **Contoso.** (Observação: Do ponto de vista de design, não há diferença entre uma experiência de guia pré e pós-reunião.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração de exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Fazer: Limitar o número de interações

Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: introduzir elementos desnecessários

Uma única caixa de diálogo na reunião com várias interações pode distrair a chamada.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Fazer: usar um layout de caixa de diálogo de coluna única

Como as caixas de diálogo estão no centro do estágio de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve atrapalhar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a>Não: desorganmente o espaço

Conteúdo densa ou estruturada em excesso pode distrair e ser avassalador, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Fazer: usar um layout de guia de coluna única

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

#### <a name="do-right-align-the-primary-action"></a>Fazer: alinhar com a direita a ação principal

Recomendamos posicionar a ação mais pesada visualmente para o local mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Não: ações de alinhamento à esquerda ou central

Isso se desvia do padrão do Teams para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Rolar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a>Do: role verticalmente

Os usuários esperam rolagem vertical no Teams (e em outros lugares).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a>Não: role horizontalmente

A rolagem horizontal não é um comportamento esperado no Teams. Outras telas no ambiente de reunião rolam verticalmente.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Fluxos de trabalho

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia em reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Cenários complexos do Surface na guia em reunião

Se seu aplicativo incluir várias tarefas, é recomendável usar uma guia na reunião com um layout de coluna única.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Não: tornar as caixas de diálogo na reunião complexas

As caixas de diálogo na reunião destinam-se a interações breves.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Fazer: usar tokens de cores do Teams

As reuniões do Teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado. Saiba mais sobre como <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">usar tokens de cores (UI fluente)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (claro)." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Não: Valores de hexaxa de código rígido

Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão voltar." border="false":::

#### <a name="do-have-a-back-button"></a>Fazer: ter um botão voltar

Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem poder voltar para suas exibições anteriores.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Não: inclua outro botão de demissão

Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, já que já há um botão no header para descartar a própria guia de reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Cuidado: evite modais na guia em reunião

Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem envolver e obscurecer o conteúdo.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Valide o seu design

Se você planeja publicar seu aplicativo no AppSource, deve compreender os problemas de design que normalmente causam falha dos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verifique as diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
