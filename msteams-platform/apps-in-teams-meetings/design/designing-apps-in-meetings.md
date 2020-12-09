---
title: Criar sua extensão de reunião
author: heath-hamilton
description: Saiba como criar aplicativos em reuniões do Teams e obter o kit de interface do usuário do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 3d18895626d5f2846d10e7145a622834d82b2e98
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605813"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Projetando sua extensão de reunião do Microsoft Teams

Você pode criar aplicativos para tornar as reuniões mais produtivas. Por exemplo, peça às pessoas para concluir uma pesquisa durante uma chamada ou enviar um lembrete rápido que não interrompa o fluxo da reunião.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Adicionar uma extensão de reunião

Você pode adicionar uma extensão de reunião antes e durante as reuniões. Também é possível um aplicativo para uma reunião específica diretamente do repositório do Teams (AppSource).

### <a name="add-before-a-meeting"></a>Adicionar antes de uma reunião

Antes de uma reunião, os detalhes da reunião selecionam **Adicionar uma guia +** para abrir o submenu do aplicativo e localizar aplicativos otimizados para reuniões.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a>Adicionar durante uma reunião

Em uma reunião, selecione **mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo desejado.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a>Antes de uma reunião

Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de pesquisa de rascunho que as pessoas responderão durante a chamada.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="O exemplo mostra como o conteúdo do aplicativo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomia: guia reunião (antes e depois de reuniões)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: rótulo de navegação para sua guia.|
|2 |**Estouro de tabulação**: abre ações de tabulação, como renomear e remover.|
|3 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua guia de reunião:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.
* [Quadro de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um quadro de tarefas, às vezes chamado de um quadro Kanban ou uma pista de baixo, é uma coleção de cartões usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela contendo vários cartões que oferecem uma visão geral de dados ou conteúdo.
* [Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.
* [NAV à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): o modelo de navegação à esquerda pode ajudar se sua guia requer alguma navegação. Em geral, você deve manter a navegação de guia no mínimo.

## <a name="use-an-in-meeting-tab"></a>Usar uma guia na reunião

A guia na reunião é uma tela para aumentar a colaboração durante as reuniões. Os participantes podem ver e interagir com o conteúdo de aplicativo em um espaço dedicado fora da fase de reunião por meio de exibições compartilhadas ou baseadas em função.

### <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia na reunião para:

* Fornecer feedback detalhado (por exemplo, avaliar um candidato a trabalho)
* Criar rapidamente um item de pesquisa, pesquisa ou tarefa para os participantes da reunião
* Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar conteúdo de pesquisa em uma guia na reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomia: guia na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia na reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone de aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.|
|2 |**Nome do aplicativo**|
|3 |**Header**: inclui o nome do aplicativo.|
|4 |**Botão fechar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.|
|5 |**Barra de notificações**: alertas de erro são exibidos diretamente abaixo do cabeçalho e empurre o conteúdo do iframe para baixo em 20 pixels.|
|6 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="spacing"></a>Espaçamento

Otimize sua guia na reunião para ajustar a borda à borda dentro da área de iframe de 280 pixels de largura. Há 20 pixels de enchimento nos lados esquerdo e direito do iframe e entre o cabeçalho da guia. O iframe é uma sangria completa até a parte inferior da guia.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="O exemplo mostra as dimensões de espaçamento de tabulação na reunião." border="false":::

### <a name="scrolling"></a>Rolagem

O conteúdo do iframe deve rolar verticalmente. Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo). O ScrollBar é parte do conteúdo de iframe.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem para uma camada secundária. Os usuários devem ser capazes de voltar para a camada anterior.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="O exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Usar uma caixa de diálogo na reunião

Caixas de diálogo na reunião exibidas no estágio de reunião do teams. Eles exigem a atenção, a confirmação ou a interação de um usuário, mas são sutis e não interrompem a reunião. Você deve usá-las com moderação e para cenários que são leves e orientados a tarefas.

### <a name="use-cases"></a>Casos de uso

As caixas de diálogo na reunião são acionadas por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Fornecer breve feedback
* Faça uma rápida pesquisa ou sondagem
* Enviar aprovações
* Receber lembretes

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomia: caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma caixa de diálogo de reunião." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Header**: inclui ícone de aplicativo, nome, Cadeia de caracteres de ação e ícone fechar.|
|2 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomia: cabeçalho da caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um cabeçalho de diálogo na reunião." border="false":::

Há duas variantes de cabeçalho. Quando possível, use a VARIANT com o avatar para reforçar que a caixa de diálogo é proveniente de uma pessoa.

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: pessoa que inicia a caixa de diálogo de reunião.|
|2 |**ícone de aplicativo**|
|3 |**Nome do aplicativo**|
|4 |**Botão fechar**: descarta a caixa de diálogo.|
|5 |**Cadeia de caracteres de ação**: normalmente descreve quem iniciou a caixa de diálogo.|

### <a name="responsive-behavior"></a>Comportamento dinâmico

As caixas de diálogo de reunião podem variar de tamanho para conta para diferentes cenários. Certifique-se de manter os tamanhos de enchimento e de componente.

* **Largura**: a largura do iframe é um valor absoluto dentro do intervalo especificado.
* **Altura**: a altura da caixa de diálogo é determinada pelo conteúdo do iframe. A rolagem vertical assume o conteúdo que excede a altura máxima.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra a caixa de diálogo em reunião. Largura: mín--280 pixels (248 pixels iframe). Máx--460 pixels (428 pixels de iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a>Após uma reunião

Você pode voltar para uma reunião depois de terminar e exibir o conteúdo do aplicativo. Neste exemplo, o organizador da reunião pode examinar os resultados da pesquisa na guia **contoso** . (Observação: a partir de um ponto de vista de design, não há diferença entre a experiência de guia pré e pós reunião).

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="O exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Fazer: limitar o número de interações

Para caixas de diálogo de reunião, remova o conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: apresentar elementos desnecessários

Uma caixa de diálogo de reunião única com várias interações pode atrapalhar a chamada.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-use-single-column-layouts"></a>Fazer: usar layouts de uma única coluna

Como as caixas de diálogo estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a>Não: desobstruir o espaço

O conteúdo denso ou muito estruturado pode ser confuso e impressionante, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-use-single-columns"></a>Fazer: usar colunas únicas

Dada a natureza estreita da guia na reunião, é altamente recomendável exibir o conteúdo em uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-use-multiple-columns"></a>Não: usar várias colunas

Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Controles

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Fazer: alinhar à direita a ação principal

Recomendamos que positioining a ação mais visualmente pesada para a localização mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Não: alinhar ações à esquerda ou ao centro

Isso se desvia do padrão da equipe padrão para o posicionamento de controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Rolar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-scroll-vertically"></a>Fazer: rolar verticalmente

É recomendável posicionar a ação mais visualmente pesada para a localização mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a>Não: rolar horizontalmente

A rolagem horizontal não é um comportamento esperado no Microsoft Teams. Outras telas no ambiente de reunião rolam verticalmente.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Fluxos de trabalho

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Fazer: cenários complexos de superfície na guia na reunião

Se seu aplicativo incluir várias tarefas, recomendamos enfaticamente um layout de coluna única em uma guia na reunião.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-package-complex-scenarios-in-the-in-meeting-dialog"></a>Não: empacotar cenários complexos na caixa de diálogo em reunião

As caixas de diálogo de reunião são destinadas para interações rápidas.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Fazer: usar tokens de cores do teams

As reuniões do teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitiva, para que os usuários possam se concentrar na discussão e no conteúdo compartilhado. Saiba mais sobre como usar <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (IU fluente)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Não: incluir outro botão descartar

O fornecimento de uma opção para fechar o conteúdo da guia na reunião pode causar problemas, já que já existe um botão no cabeçalho para ignorar a guia na reunião em si.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="do-have-a-back-button"></a>Fazer: ter um botão voltar

Se você tiver mais de uma camada de navegação em uma guia na reunião, os usuários devem ser capazes de retornar aos modos de exibição anteriores.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Não: incluir outro botão descartar

O fornecimento de uma opção para fechar o conteúdo da guia na reunião pode causar problemas, já que já existe um botão no cabeçalho para ignorar a guia na reunião em si.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Cuidado: Evite janelas restritas dentro da guia na reunião

As modalidades (também conhecidas como módulos de tarefa) na guia já restrita na reunião podem quebrar e obscurecer o conteúdo.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
