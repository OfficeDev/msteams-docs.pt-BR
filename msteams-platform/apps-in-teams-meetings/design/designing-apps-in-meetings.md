---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como criar extensões de reunião para seus aplicativos em reuniões do Teams. Use os modelos de interface do usuário no Kit de Interface do Usuário do Microsoft Teams para ajudá-lo a criar sua guia de reunião.
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 7df89357f5c052fec5ff2a82cd721b9b7c06da94
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558083"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Projetando sua extensão de reunião do Microsoft Teams

Você pode criar aplicativos para tornar as reuniões mais produtivas. Por exemplo, peça que as pessoas concluam uma pesquisa durante uma reunião ou enviem um lembrete rápido que não interrompa o fluxo da reunião.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que podem ser pegos e modificados conforme necessário, no Kit de Interface do Usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Adicionar uma extensão de reunião

Os usuários podem adicionar uma extensão de reunião antes e durante as reuniões. Eles também podem adicionar um aplicativo para uma reunião específica diretamente da loja do Teams.

### <a name="add-before-a-meeting"></a>Adicionar antes de uma reunião

Nos detalhes da reunião, os usuários podem selecionar Adicionar **uma guia +** para abrir o submenu do aplicativo e localizar aplicativos otimizados para reuniões.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião antes de uma reunião.":::

### <a name="add-during-a-meeting"></a>Adicionar durante uma reunião

#### <a name="mobile"></a>Celular

Depois que o aplicativo é adicionado (por exemplo, na área de trabalho), os usuários podem acessar o aplicativo em uma reunião selecionando **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião durante uma reunião no celular.":::

#### <a name="desktop"></a>Desktop

Em uma reunião, os usuários podem selecionar **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: > **Adicionar um aplicativo** e selecionar o aplicativo desejado.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião durante uma reunião.":::

## <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, seu aplicativo está disponível para os usuários em uma guia. O exemplo a seguir mostra uma pergunta de rascunho de pesquisa que as pessoas responderão durante a reunião.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="O exemplo mostra como aplicativo conteúdo nos detalhes da reunião antes de uma chamada.":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomia: guia Reunião (antes e depois das reuniões)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião.":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: rótulo de navegação para sua guia.|
|2|**Excedente da guia**: abre as ações de guia, como renomear e remover.|
|3|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="design-with-ui-templates"></a>Criação com modelos de IU

Use um dos seguintes modelos de interface do usuário do Teams para ajudar a criar sua guia de reunião:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato que facilita a visualização e permite que os usuários executem ações em uma lista inteira ou itens individuais.
* [Painel de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um painel de tarefas, às vezes chamado de quadro Kanban ou raias, é uma coleção de cartões frequentemente usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou do conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo logon, experiências de primeira execução, mensagens de erro e muito mais.
* [Navegação esquerda](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): o componente de navegação à esquerda pode ajudar se a guia requer alguma navegação. Em geral, você deve manter a navegação no mínimo.

## <a name="use-an-in-meeting-tab"></a>Usar uma guia na reunião

A guia na reunião é uma tela para aumentar a colaboração durante as reuniões. Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio da reunião por meio de exibições compartilhadas ou baseadas em função.

### <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia na reunião para:

* Forneça comentários detalhados. Por exemplo, avalie um candidato a trabalho.
* Crie uma pesquisa, uma pesquisa ou um item de tarefa para os participantes da reunião.
* Exibir anotações relevantes para a reunião. Por exemplo, informações sobre um cliente potencial de vendas.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar conteúdo de votação em uma guia na reunião no celular.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar conteúdo de votação em uma guia na reunião.":::

### <a name="anatomy-in-meeting-tab"></a>Anatomia: guia Na reunião

:::image type="content" source="../../assets/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia na reunião.":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do aplicativo (selecionado)**: logotipo do aplicativo transparente de 16 pixels.|
|2|**Nome do aplicativo**|
|3|**Cabeçalho**: inclui o nome do aplicativo.|
|4|**Botão Fechar**: ignora a guia. Sempre use o ícone fechar no canto superior direito em vez de uma ação no rodapé.|
|5|**Barra de notificação**: os alertas de erro são exibidos diretamente abaixo do cabeçalho e enviam o restante do conteúdo do iframe para baixo 20 pixels.|
|6 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="spacing"></a>Espaçamento

Otimize sua guia na reunião para ajustar de ponta a ponta dentro da área de iframe de 280 pixels de largura. Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o cabeçalho da guia. O iframe está sangrando até a parte inferior da guia.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="O exemplo mostra as dimensões de espaçamento da guia na reunião.":::

### <a name="scrolling"></a>Rolagem

Lembre-se do seguinte se você permitir a rolagem:

* O conteúdo no conteúdo do iframe só deve rolar verticalmente.
* Os usuários só devem ver o conteúdo para o qual rolaram (nada acima ou abaixo).
* A barra de rolagem faz parte do conteúdo do iframe.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia na reunião rola.":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo pesado, é recomendável permitir que os usuários naveguem para uma camada secundária. Os usuários devem poder voltar para a camada anterior.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="O exemplo mostra a navegação na reunião.":::

## <a name="use-an-in-meeting-dialog"></a>Usar uma caixa de diálogo na reunião

As caixas de diálogo na reunião são exibidas no estágio de reunião do Teams. Eles exigem a atenção, a confirmação ou a interação do usuário, mas são sutis e não interrompem a reunião. Você deve usá-lo com moderação e para cenários que são leves e orientados a tarefas.

### <a name="use-cases"></a>Casos de uso

As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Forneça comentários breves.
* Faça uma breve pesquisa ou sondagem.
* Enviar aprovações.
* Obter lembretes.

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião no celular.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião.":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomia: caixa de diálogo na reunião

:::image type="content" source="../../assets/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um diálogo em reunião.":::

|Contador|Descrição|
|----------|-----------|
|1|**Cabeçalho**: inclui ícone do aplicativo, nome, cadeia de caracteres de ação e ícone fechar.|
|2|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomia: cabeçalho da caixa de diálogo na reunião

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um cabeçalho de diálogo na reunião.":::

Há duas variantes de cabeçalho. Quando possível, use a variante com o avatar para reforçar que o diálogo é proveniente de uma pessoa.

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: pessoa que inicia a caixa de diálogo na reunião.|
|2|**ícone do aplicativo**|
|3|**Nome do aplicativo**|
|4|**Botão Fechar**: ignora a caixa de diálogo.|
|5|**Cadeia de caracteres** de ação: normalmente descreve quem iniciou a caixa de diálogo.|

### <a name="responsive-behavior-in-meeting-dialogs"></a>Comportamento responsivo: caixas de diálogo na reunião

As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes. Certifique-se de manter o preenchimento e o tamanho dos componentes.

* **Largura**: você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanho com suporte.
* **Altura**: você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanho com suporte. Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (248 pixels iframe). Máximo – 460 pixels (428 pixels de iframe). Altura: 300 pixels (iframe).":::

## <a name="use-the-shared-meeting-stage"></a>Usar o estágio de reunião compartilhada

Você pode permitir que os usuários compartilhem e interajam com algum ou todo o conteúdo do aplicativo no estágio da reunião. Aqui estão exemplos de como as pessoas podem usar esse recurso durante uma reunião:

* Editando um documento.
* Quadro de comunicações
* Revisando um painel.
* Assistindo a um vídeo.
* Jogando um jogo.

Os aplicativos compartilhados com o estágio de reunião ocupam o mesmo espaço que uma tela compartilhada. A fase também é reorientada para todos os participantes da reunião.

> [!NOTE]
> Atualmente, os usuários móveis não podem compartilhar o conteúdo do aplicativo para o estágio da reunião. No entanto, eles podem ver o conteúdo compartilhado da área de trabalho.

### <a name="use-cases"></a>Casos de uso

O estágio de reunião compartilhada tem tudo a ver com colaboração e participação. Aqui estão alguns cenários de exemplo para ajudá-lo a começar.

:::row:::
   :::column span="1":::

**Editar e revisar**: aprofunde-se em painéis e planejamento com todos na reunião.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review.png" alt-text="O exemplo mostra um painel sendo revisado no estágio de reunião compartilhado.":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review-component.png" alt-text="O exemplo mostra um componente de painel sendo revisado no estágio de reunião compartilhado.":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Quadro de** comunicações: desenhe e desenhe em uma tela compartilhada.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-whiteboard.png" alt-text="O exemplo mostra um quadro de comunicações no estágio de reunião compartilhado.":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Teste**: Testar o conhecimento e obter insights com materiais interativos.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-quiz.png" alt-text="O exemplo mostra um teste no estágio de reunião compartilhado.":::

   :::column-end:::
:::row-end:::

### <a name="anatomy-share-all-app-content-to-a-meeting"></a>Anatomia: compartilhar todo o conteúdo do aplicativo em uma reunião

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy.png" alt-text="A imagem mostra a anatomia de design do estágio de reunião compartilhado quando todo o conteúdo do aplicativo é compartilhado.":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do** aplicativo: o ícone realçado indica que a guia na reunião do aplicativo está aberta.|
|2|**Botão Compartilhar para reunião**: o ponto de entrada para compartilhar o aplicativo com a reunião. Será exibido se você configurar seu aplicativo para usar o estágio de reunião compartilhado.|
|3|**Atribuição do apresentador**: exibe o nome do participante que compartilhou o aplicativo.|
|4|**iframe**: exibe o conteúdo do aplicativo.|
|5|**Botão Parar de compartilhar**: interrompe o compartilhamento do aplicativo para o estágio da reunião. Exibe somente para o participante que iniciou o compartilhamento.|

### <a name="anatomy-share-specific-app-content-to-a-meeting"></a>Anatomia: Compartilhar conteúdo específico do aplicativo para uma reunião

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy-component.png" alt-text="A imagem mostra a anatomia de design do estágio de reunião compartilhado quando apenas o conteúdo específico do aplicativo é compartilhado.":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone do** aplicativo: o ícone realçado indica que a guia na reunião do aplicativo está aberta.|
|2|**Botão Compartilhar para reunião**: o ponto de entrada para compartilhar o aplicativo com a reunião. Para uma experiência consistente, sempre use o ícone de compartilhamento padrão do Teams. **Compartilhar com reunião é** o texto padrão recomendado, mas você também pode personalizá-lo para seus casos de uso. Por exemplo, **jogue em conjunto** para um aplicativo de jogos ou **assista juntos** para um aplicativo de vídeo. De qualquer forma, torne claro que a ação criará uma experiência compartilhada e interativa com todos na reunião.|
|3|**Atribuição do apresentador**: exibe o nome do participante que compartilhou o aplicativo.|
|4|**iframe**: exibe o conteúdo do aplicativo.|
|5|**Botão Parar de compartilhar**: interrompe o compartilhamento do aplicativo para o estágio da reunião. Exibe somente para o participante que iniciou o compartilhamento.|

### <a name="responsive-behavior-shared-meeting-stage"></a>Comportamento responsivo: estágio de reunião compartilhado

Os aplicativos compartilhados com o estágio da reunião variam de acordo com o estado da reunião e como o usuário redimensiona a janela. Mantenha o preenchimento e o layout responsivo de navegação e controles da mesma forma que você faria em um navegador.

* **Painel lateral**: um usuário pode ter o painel lateral aberto a qualquer momento durante uma reunião para conversar, exibir a lista de participantes ou usar um aplicativo (ou seja, a guia na reunião). O estágio é reorganizado dinamicamente quando o painel está aberto.
* **Grade de áudio e vídeo**: a grade de áudio e vídeo está sempre visível para mostrar os participantes da reunião. Quando um usuário destaca ou fixa alguém na reunião, isso aumenta a altura ou a largura da grade do participante, dependendo da orientação.

#### <a name="meeting-stage-without-side-panel"></a>Estágio de reunião (sem painel lateral)

Quando o painel lateral não está aberto, o estágio de reunião é de 994 x 678 pixels por padrão e pode ter um mínimo de 792 x 382 pixels.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-no-side-panel.png" alt-text="Imagem mostrando a capacidade de resposta do estágio de reunião compartilhado com o painel lateral fechado.":::

#### <a name="meeting-stage-with-side-panel"></a>Estágio de reunião (com painel lateral)

Quando o painel lateral está aberto, o estágio de reunião é de 918 x 540 pixels por padrão e pode ter um mínimo de 472 x 382 pixels.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-with-side-panel.png" alt-text="Imagem mostrando a capacidade de resposta do estágio de reunião compartilhado com o painel lateral aberto.":::

## <a name="after-a-meeting"></a>Após uma reunião

Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo. Neste exemplo, o organizador da reunião pode examinar os resultados da votação na guia **Contoso** . (Observação: do ponto de vista do design, não há nenhuma diferença entre a experiência da guia pré e pós-reunião.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração de exemplo mostra uma guia pós-reunião.":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações.":::

#### <a name="do-limit-the-number-of-interactions"></a>Fazer: limitar o número de interações

Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários.":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: introduzir elementos desnecessários

Uma única caixa de diálogo na reunião com várias interações pode distrair a reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-do.png" alt-text="Exemplo mostrando como criar um ambiente focado.":::

#### <a name="do-create-a-focused-environment"></a>Fazer: criar um ambiente focado

É recomendável manter a experiência do aplicativo no escopo apenas para o estágio da reunião. Você pode usar uma guia na reunião no painel lateral como uma exibição secundária privada para determinados cenários.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-dont.png" alt-text="Exemplo mostrando como não incluir superfícies concorrentes durante as reuniões.":::

#### <a name="dont-include-competing-surfaces"></a>Não: incluir superfícies concorrentes

Seu aplicativo só deve solicitar que os usuários se concentrem em uma única superfície por vez, seja colaborando no palco ou respondendo a uma caixa de diálogo na reunião. (Observação: você não pode manter as caixas de diálogo sendo disparadas por outros aplicativos enquanto seu aplicativo está no palco.)

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única.":::

#### <a name="do-use-a-one-column-dialog"></a>Fazer: usar uma caixa de diálogo de uma coluna

Como os diálogos estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve desorganize o espaço de uma extensão de reunião.":::

#### <a name="dont-clutter-the-space"></a>Não: desorganize o espaço

O conteúdo denso ou excessivamente estruturado pode ser uma distração e uma grande distração, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única.":::

#### <a name="do-use-a-one-column-tab"></a>Fazer: usar uma guia de uma coluna

Dada a natureza estreita da guia na reunião, é altamente recomendável exibir o conteúdo em uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas.":::

#### <a name="dont-use-multiple-columns"></a>Não: usar várias colunas

Devido ao espaço limitado da guia na reunião, não são recomendados layouts com mais de uma coluna.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Controles

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários.":::

#### <a name="do-right-align-the-primary-action"></a>Faça: alinhar à direita a ação primária

Recomendamos posicionar a ação mais intensa visualmente no local mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve alinhar os controles primários à esquerda.":::

#### <a name="dont-left-or-center-align-actions"></a>Não: ações de alinhamento à esquerda ou centralizar

Isso se desvia do padrão do Teams para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo por trás da parte superior.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Rolagem

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical no estágio de reunião compartilhado.":::

#### <a name="do-scroll-vertically"></a>Fazer: rolar verticalmente

Os usuários esperam rolagem vertical no Teams (e em outro lugar). Isso pode não se aplicar se você tiver uma tela criativa, como um quadro de comunicações, que os usuários podem aplicar panorââ sobre os eixos x e y.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal no estágio de reunião compartilhado.":::

#### <a name="dont-scroll-horizontally"></a>Não: rolar horizontalmente

A rolagem horizontal não é um comportamento esperado no Teams (incluindo o ambiente de reunião).

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Fluxos de trabalho

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando um cenário complexo em uma guia na reunião.":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Fazer: exibir cenários complexos na guia na reunião

Se seu aplicativo incluir várias tarefas, é altamente recomendável usar uma guia na reunião com um layout de coluna única.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião.":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Não faça isso: tornar os diálogos na reunião complexos

Os diálogos na reunião destinam-se a interações breves.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-do.png" alt-text="Outro exemplo mostrando a extensão de reunião com o tema escuro.":::

#### <a name="do-focus-on-dark-theme"></a>Do: Foco no tema escuro

As reuniões do Teams são otimizadas para o tema escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado. Lembre-se de que determinados tipos de aplicativos (como quadro de comunicações e edição de documentos) não precisam de uma tela escura.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com cores que não correspondem ao tema da reunião.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-dont.png" alt-text="Outro exemplo mostrando uma extensão de reunião com cores que não correspondem ao tema da reunião.":::

#### <a name="dont-use-unfamiliar-colors"></a>Não use cores desconhecidas

Cores que se colidem com o ambiente de reunião podem ser distração e parecem menos nativas do Teams. Saiba mais sobre a rampa de [cores do](https://developer.microsoft.com/fluentui#/styles/web/colors/products) Teams, incluindo os neutros do tema de chamada.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão Voltar.":::

#### <a name="do-have-a-back-button"></a>Fazer: ter um botão Voltar

Se você tiver mais de uma camada de navegação em uma guia na reunião, os usuários deverão ser capazes de voltar para seus modos de exibição anteriores.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de ignorar.":::

#### <a name="dont-include-another-dismiss-button"></a>Não fazer: incluir outro botão ignorar

Fornecer uma opção para fechar o conteúdo da guia na reunião pode causar problemas, pois já há um botão no cabeçalho para ignorar a própria guia na reunião.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia na reunião.":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Cuidado: evite modais na guia na reunião

Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem encapsular e obscurecer o conteúdo.

   :::column-end:::
:::row-end:::

### <a name="responsive-behavior"></a>Comportamento dinâmico

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-do.png" alt-text="Exemplo mostrando como redimensionar corretamente uma extensão de reunião.":::

#### <a name="do-resize-and-scale-your-app-responsively"></a>Faça: redimensione e dimensione seu aplicativo de maneira responsiva

O conteúdo do aplicativo deve redimensionar e condensar dinamicamente em janelas menores. Mantenha a navegação principal do aplicativo e os controles flutuantes visíveis.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-dont.png" alt-text="Exemplo mostrando como não redimensionar corretamente uma extensão de reunião.":::

#### <a name="dont-crop-or-clip-primary-ui-components"></a>Não: cortar ou recortar componentes primários da interface do usuário

A navegação flutuante e os controles fora da tela e a necessidade de uma rolagem para localizar podem ser confusos para os usuários. O conteúdo do aplicativo não deve rolar horizontalmente quando ele não pode caber no iframe.

   :::column-end:::
:::row-end:::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar seu aplicativo para reuniões](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
