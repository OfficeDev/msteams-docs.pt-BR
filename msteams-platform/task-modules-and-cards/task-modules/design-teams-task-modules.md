---
title: Criar módulos de tarefa
author: heath-hamilton
description: Saiba como projetar módulos de tarefa para Teams aplicativos e obter o kit Microsoft Teams interface do usuário.
localization_priority: Normal
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 347ce42c41706f698e2f8897a0518aae0850a275
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101727"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Projetando módulos de tarefas para seu Microsoft Teams app

Você pode criar experiências pop-up modais em seu aplicativo Teams com módulos de tarefa. Use esse recurso para exibir mídia e informações ricas ou concluir uma tarefa complexa.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Exemplo mostra um módulo de tarefa." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes de design de módulo de tarefa mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Abrir um módulo de tarefa

Os módulos de tarefa podem ser lançados de praticamente qualquer lugar em seu aplicativo.

* **Guia**: Um módulo de tarefa pode ser lançado a partir de qualquer link em uma guia. Use em cenários em que você deseja que o usuário se concentre em uma interação.
* **Bot**: um módulo de tarefa pode ser lançado a partir de um link dentro de uma mensagem bot.
* **Cartão Adaptável**: um módulo de tarefa pode ser lançado a partir de um Cartão Adaptável (enviado com uma extensão de mensagens ou por um bot) quando um usuário seleciona um botão.
* **Extensão de mensagens (comandos de ação)**: As extensões de mensagens permitem que você tome uma ação específica no conteúdo da mensagem. Selecionar uma ação abre um módulo de tarefa.
* **Extensão de mensagens (contexto** da caixa de redação) : Na caixa de redação, você pode projetar uma extensão de mensagens para abrir um módulo de tarefa em vez do flyout típico. Reserve módulos de tarefa para interações complexas, como a conclusão de um formulário.

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um módulo de tarefa." border="false":::

Os módulos de tarefa são superfícies muito flexíveis. Eles podem ser construídos com iframes, a partir de outros modelos de interface do usuário, para hospedar experiências criadas por parceiros. Isso é preferencial para a experiência mais polida.

Eles também podem ser construídos com a estrutura [cartão](../../task-modules-and-cards/cards/design-effective-cards.md) adaptável, que pode ser uma maneira mais simples e mais rápida de executar cenários comuns (como formulários).

|Contador|Descrição|
|----------|-----------|
|1|**ícone de aplicativo**|
|2|**Nome do** aplicativo : Nome completo do seu aplicativo.|
|3|**Header**: Tornar os headers claros e concisos. Descreva a tarefa que você deseja que os usuários concluam.
|4 |**Botão Fechar**: Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.|
|5 |**iframe**: espaço responsivo que hospeda o conteúdo do aplicativo.|
|6 |**Ações (opcional)**: Botões relacionados ao conteúdo do aplicativo.|

## <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Considere usar modelos para layouts comuns dentro de seus módulos de tarefas. Cada um deles é feito de componentes menores para criar um design elegante e responsivo que pode ser usado fora da caixa ou personalizado para seu cenário ou com a aparência da sua marca.

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.

## <a name="examples"></a>Exemplos

### <a name="list"></a>List

As listas funcionam bem em um módulo de tarefa porque são fáceis de examinar.

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Lista de exemplos em um módulo de tarefa." border="false":::

### <a name="form"></a>Formulário

Os módulos de tarefa são um ótimo local para superfície de formulários com entradas de usuário sequenciais e validação em linha. Você pode aproveitar cartões adaptáveis como uma maneira de incorporar elementos de formulário.

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Formulário de exemplo em um módulo de tarefa." border="false":::

### <a name="sign-in"></a>Entrar

Crie um fluxo de login ou de assinatura focado com uma série de módulos de tarefas, deixando que os usuários se movam facilmente através de etapas sequenciais.

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Experiência de login de exemplo em um módulo de tarefa." border="false":::

### <a name="media"></a>Mídia

Incorporar conteúdo de mídia em um módulo de tarefa para uma experiência de exibição focada.

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefa." border="false":::

### <a name="empty-state"></a>Estado vazio

Use para mensagens de boas-vindas, erros e sucesso.

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefa." border="false":::

### <a name="image-gallery"></a>Galeria de imagens

Incorporar um carrossel de galeria em um iframe.

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Galeria de imagens de exemplo em um módulo de tarefa." border="false":::

### <a name="poll"></a>Sondagem

Este exemplo mostra os resultados da sondagem lançados de um Cartão Adaptável. A sondagem também pode ser colocada dentro de um módulo de tarefas.

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Sondagem de exemplo em um módulo de tarefa." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="usability"></a>Usabilidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (um módulo de tarefa por vez)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Fazer: usar um módulo de tarefa por vez

O objetivo é concentrar o usuário na conclusão de uma tarefa, afinal!

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (pop a dialog on top of a task module)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Não: pop uma caixa de diálogo em cima de um módulo de tarefa

Isso cria uma experiência de usuário confusa e sem foco.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Dinâmico

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (certifique-se de que o conteúdo seja responsivo)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Fazer: certifique-se de que o conteúdo seja responsivo

Embora os Cartões Adaptáveis hospedados em um módulo de tarefa renderizarão bem em dispositivos móveis, se você optar por usar um iframe para hospedar conteúdo do aplicativo, certifique-se de que a interface do usuário seja responsiva e funcione bem entre dispositivos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (não use barras de rolagem horizontal)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a>Não: use barras de rolagem horizontal

É uma prática melhor manter o conteúdo focado e não muito longo. Se um rolagem for necessário, role verticalmente e não horizontalmente.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Simplicidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (mantenha-o curto)." border="false":::

#### <a name="do-keep-it-short"></a>Do: mantenha-o curto

Você pode criar facilmente um assistente de várias etapas, mas isso não significa necessariamente que você deve! Um módulo de tarefa de várias telas pode ser problemático porque as mensagens de entrada estão distraindo e tentando que os usuários saiam. Se sua tarefa estiver realmente envolvida, saia para uma página da Web completa em vez de um módulo de tarefa.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (não há interações longas)." border="false":::

#### <a name="dont-have-long-interactions"></a>Não: ter interações longas

Tente manter suas interações curtas e diretas.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Mensagens de erro

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Exemplo mostrando a prática prática de um módulo de tarefa (use mensagens de erro em linha)." border="false":::

#### <a name="do-use-inline-error-messages"></a>Fazer: usar mensagens de erro em linha

Consulte o modelo de interface do usuário de formulários para ver diretrizes sobre o tratamento de erros em linha.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa (colocar mensagens de erro em caixas de diálogo)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Não: colocar mensagens de erro em caixas de diálogo

Não pop uma mensagem de erro em uma caixa de diálogo em cima de um módulo de tarefa. Ele cria uma experiência de usuário confusa.

   :::column-end:::
:::row-end:::
