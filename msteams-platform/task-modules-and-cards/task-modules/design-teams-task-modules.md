---
title: Criando módulos de tarefas
author: heath-hamilton
description: Saiba como projetar módulos de tarefa para aplicativos do Teams e obter o kit de interface do usuário do Microsoft Teams.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 41584ecf58ca7718290e58e5845549e4579dac64
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605836"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Criando módulos de tarefas para seu aplicativo do Microsoft Teams

Você pode criar experiências de pop-up modais no seu aplicativo do teams com módulos de tarefa. Use este recurso para exibir mídia avançada e informações ou concluir uma tarefa complexa.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="O exemplo mostra um módulo de tarefa." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar mais abrangentes diretrizes de design de módulo de tarefa, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Abrir um módulo de tarefa

Os módulos de tarefa podem ser iniciados de quase qualquer lugar em seu aplicativo.

* **Guia**: um módulo de tarefa pode ser iniciado em qualquer link dentro de uma Tabulação ou iframe. Use em cenários em que você deseja que o usuário se concentre em uma interação.
* **Bot**: um módulo de tarefa pode ser iniciado em um link dentro de uma mensagem de bot.
* **Cartão adaptável**: um módulo de tarefa pode ser iniciado a partir de um cartão adaptável (enviado com uma extensão de mensagens ou por um bot) quando um usuário seleciona um botão.
* **Extensão de mensagens (comandos de ação)**: as extensões de mensagens permitem executar uma ação específica no conteúdo da mensagem. Selecionar uma ação abre um módulo de tarefa.
* **Extensão de mensagens (contexto da caixa de composição)**: na caixa compor, você pode criar uma extensão de mensagens para abrir um módulo de tarefa em vez do submenu típico. Reserve módulos de tarefas para interações complexas, como preencher um formulário.

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia de interface do usuário de um módulo de tarefa." border="false":::

Os módulos de tarefa são superfícies muito flexíveis. Eles podem ser criados com IFrames, puxando outros modelos de interface do usuário para hospedar experiências criadas pelo parceiro. Isso é preferível para a experiência mais elegante.

Eles também podem ser criados com a estrutura de [cartão adaptável](../../task-modules-and-cards/cards/design-effective-cards.md) , que pode ser uma maneira mais simples e rápida de executar cenários comuns (como formulários).

|Contador|Descrição|
|----------|-----------|
|1|**ícone de aplicativo**|
|2 |**Nome do aplicativo**: nome completo do seu aplicativo.|
|3 |**Cabeçalho**: torne os cabeçalhos claros e concisos. Descreva a tarefa que você deseja que os usuários concluam.
|4 |**Botão fechar**: permite que os usuários encontrem o conteúdo de aplicativo que desejam inserir.|
|5 |**iframe**: espaço responsivo que hospeda o conteúdo do aplicativo.|
|6 |**Ações (opcional)**: botões relacionados ao conteúdo do aplicativo.|

## <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Considere usar modelos para layouts comuns dentro de seus módulos de tarefas. Cada uma é composta por componentes menores para criar um design elegante e responsivo que pode ser usado fora da caixa ou personalizado para o seu cenário ou com a aparência da marca.

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.
* [Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.

## <a name="examples"></a>Exemplos

### <a name="list"></a>Listar

As listas funcionam bem em um módulo de tarefa, pois elas são fáceis de examinar.

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Exemplo de lista em um módulo de tarefa." border="false":::

### <a name="form"></a>Formulário

Os módulos de tarefa são um ótimo local para a superfície de formulários com entradas de usuário sequenciais e validação embutida. Você pode aproveitar cartões adaptáveis como uma maneira de incorporar elementos de formulário.

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Formulário de exemplo em um módulo de tarefa." border="false":::

### <a name="sign-in"></a>Entrar

Criar um fluxo de entrada ou de inscrição focalizado com uma série de módulos de tarefa, permitindo que os usuários se movimentem facilmente por meio de etapas sequenciais.

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Experiência de entrada de exemplo em um módulo de tarefa." border="false":::

### <a name="media"></a>Mídia

Incorpore conteúdo de mídia em um módulo de tarefa para uma experiência de exibição focalizada.

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefa." border="false":::

### <a name="empty-state"></a>Estado vazio

Use para mensagens de boas-vindas, erros e sucesso.

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefa." border="false":::

### <a name="image-gallery"></a>Galeria de imagens

Insira um carrossel de galeria dentro de um iframe.

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Exemplo de galeria de imagens em um módulo de tarefa." border="false":::

### <a name="poll"></a>Quanto

Este exemplo mostra os resultados da pesquisa iniciados a partir de um cartão adaptável.

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Pesquisa de exemplo em um módulo de tarefa." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

### <a name="usability"></a>Praticidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Fazer: usar um módulo de tarefa por vez

O objetivo é concentrar o usuário na conclusão de uma tarefa após tudo!

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Não: pop uma caixa de diálogo na parte superior de um módulo de tarefa

Isso cria uma experiência de usuário desfocada e confusa.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Dinâmico

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Fazer: Certifique-se de que o conteúdo é responsivo

Enquanto os cartões adaptáveis hospedados em um módulo de tarefa são renderizados em dispositivos móveis, se você optar por usar um iframe para hospedar o conteúdo do aplicativo, certifique-se de que a interface do usuário seja responsiva e funcione bem entre os dispositivos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-use-horizontal-scrollbars"></a>Não: usar barras de rolagem horizontais

É uma prática recomendada manter o conteúdo focado e muito longo. Se uma rolagem for necessária, role verticalmente e não horizontalmente.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Devido

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-keep-it-short"></a>Fazer: Mantenha-o curto

Você pode criar facilmente um assistente de várias etapas, mas isso não significa necessariamente que você deve! Um módulo de tarefa de várias telas pode ser problemático porque as mensagens de entrada estão distraindo e tentam sair. Se a tarefa estiver realmente envolvida, desapareça para uma página da Web completa em vez de um módulo de tarefa.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-do-long-interactions"></a>Não: fazer interações longas

Tente manter suas interações curtas e ao ponto.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Mensagens de erro

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-use-inline-error-messages"></a>Fazer: usar mensagens de erro embutidas

Consulte o modelo de interface do usuário de formulários para obter diretrizes sobre o tratamento de erros embutido.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Não: colocar mensagens de erro em caixas de diálogo

Não é exibida uma mensagem de erro em uma caixa de diálogo na parte superior de um módulo de tarefa. Ele cria uma experiência de usuário confusa.

   :::column-end:::
:::row-end:::
