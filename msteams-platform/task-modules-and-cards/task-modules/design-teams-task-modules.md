---
title: Criar módulos de tarefa
author: heath-hamilton
description: Aprenda a projetar módulos de tarefas para os aplicativos do Teams e a obter o Kit de IU do Microsoft Teams.
ms.localizationpriority: high
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 1514ed8e3101065efd482ced45de98b8b0f58ab8
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104130"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Criando módulos de tarefa para o seu aplicativo do Microsoft Teams

Você pode criar experiências pop-up modais no seu aplicativo do Teams com módulos de tarefas. Use este recurso para exibir mídia e informações avançada ou concluir uma tarefa complexa.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="O exemplo apresenta um módulo de tarefas." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Você pode encontrar diretrizes de design do módulo de tarefas mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de IU do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Criar um módulo de tarefas

Os módulos de tarefas podem ser iniciados de praticamente qualquer lugar no seu aplicativo.

* **Guia**: um módulo de tarefas pode ser iniciado de qualquer link em uma guia. Use em cenários em que você quer que o usuário se concentre em uma interação.
* **Bot**: um módulo de tarefas pode ser iniciado de um link dentro de uma mensagem de bot.
* **Cartão Adaptável**: Um módulo de tarefas pode ser iniciado a partir de um Cartão Adaptável (enviado com uma extensão de mensagem ou por um bot) quando um usuário seleciona um botão.
* **Extensão de mensagem (comandos de ação)**: as extensões de mensagens permitem que você realize uma ação específica no conteúdo da mensagem. Selecionar uma ação abre um módulo de tarefas.
* **Extensão de mensagem (contexto da caixa de redação)**: na caixa de redação, você pode projetar uma extensão de mensagem para abrir um módulo de tarefas em vez do submenu típico. Reserve módulos de tarefas para as interações complexas, como a conclusão de um formulário.

## <a name="anatomy"></a>Anatomia

Os módulos de tarefas fornecem uma superfície flexível às experiências de aplicativos hospedados. Eles são construídos usando um iframe (desktop) ou Modo de Exibição da Web (dispositivo móvel) para que você possa projetar módulos de tarefas com nossos modelos de IU (recomendados) ou do zero.

Eles também podem ser construídos com a estrutura [Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md), que pode ser uma maneira mais simples e mais rápida para facilitar cenários comuns (como formulários).

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia da IU de um módulo de tarefas no celular." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Cabeçalho**: tornar os cabeçalhos claros e concisos. Descreva a tarefa que você quer que os usuários concluam.
|2|**Nome do aplicativo**: nome completo do seu aplicativo.|
|3|**Botão Fechar**: fecha o módulo de tarefas. Não aplica alterações não salvas no conteúdo do aplicativo.|
|4|**Modo de Exibição da Web**: espaço responsivo que hospeda o conteúdo do seu aplicativo.|
|5|**Ações (opcional)**: botões relacionados ao conteúdo do seu aplicativo.|

### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia da IU de um módulo de tarefas." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**ícone do aplicativo**|
|2|**Nome do aplicativo**: nome completo do seu aplicativo.|
|3|**Cabeçalho**: tornar os cabeçalhos claros e concisos. Descreva a tarefa que você quer que os usuários concluam.
|4|**Botão Fechar**: fecha o módulo de tarefas. Não aplica alterações não salvas no conteúdo do aplicativo.|
|5|**iframe**: espaço responsivo que hospeda o conteúdo do aplicativo.|
|6 |**Ações (opcional)**: botões relacionados ao conteúdo do seu aplicativo.|

## <a name="designing-with-ui-templates"></a>Projetando com modelos de IU

Considere usar modelos para layouts comuns dentro dos seus módulos de tarefas. Cada um é formado por componentes menores para criar um design elegante e responsivo que pode ser usado fora da caixa ou personalizado ao seu cenário ou com a aparência da sua marca.

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato que facilita a visualização e permite que os usuários executem ações em uma lista inteira ou itens individuais.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários servem para coletar, validar e submeter a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira execução, mensagens de erro, e muito mais.

## <a name="examples"></a>Exemplos

### <a name="list"></a>Lista

As listas funcionam bem em um módulo de tarefas porque são fáceis de examinar.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-list.png" alt-text="Lista de exemplos em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Lista de exemplos em um módulo de tarefas." border="false":::

### <a name="form"></a>Formulário

Os módulos de tarefas são um ótimo lugar para criar formulários com entradas sequenciais do usuário e validação em linha. Você pode aproveitar Cartões Adaptáveis como uma maneira de incorporar elementos de formulários.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-form.png" alt-text="Formulário de exemplo em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/form.png" alt-text="Formulário de exemplo em um módulo de tarefas." border="false":::

### <a name="sign-in"></a>Entrar

Crie um fluxo de entrada ou de assinatura focado com uma série de módulos de tarefas, permitindo que os usuários se movam facilmente pelas etapas sequenciais.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-sign-in.png" alt-text="Experiência de entrada de exemplo em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Experiência de entrada de exemplo em um módulo de tarefas." border="false":::

### <a name="media"></a>Mídia

Incorpore conteúdo de mídia em um módulo de tarefas que permita uma experiência de visualização focada.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefas." border="false":::

### <a name="empty-state"></a>Estado vazio

Use para mensagens de boas-vindas, erros e sucesso.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefas." border="false":::

### <a name="image-gallery"></a>Galeria de imagens

Incorpore um carrossel de galeria em um iframe (área de trabalho) ou modo de exibição da Web (móvel).

##### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-image-gallery.png" alt-text="Galeria de imagens de exemplo em um módulo de tarefas no celular." border="false":::

##### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Galeria de imagens de exemplo em um módulo de tarefas." border="false":::

### <a name="poll"></a>Enquete

Esse exemplo apresenta os resultados da enquete iniciados de um Cartão Adaptável. A enquete também pode ser colocada dentro de um módulo de tarefas.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/task-module/mobile-poll.png" alt-text="Enquete de exemplo em um módulo de tarefas no celular." border="false":::

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Enquete de exemplo em um módulo de tarefas." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="usability"></a>Usabilidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (um módulo de tarefas por vez)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Fazer: usar um módulo de tarefas por vez

Afinal, o objetivo é focar o usuário na conclusão de uma tarefa!

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (abrir uma caixa de diálogo sobre um módulo de tarefas)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Não fazer: abrir uma caixa de diálogo sobre um módulo de tarefas

Isso cria uma experiência de usuário confusa e sem foco.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Dinâmico

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (certifique-se de que o conteúdo seja responsivo)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Fazer: certifique-se de que o conteúdo seja responsivo

Embora os Cartões Adaptáveis hospedados em um módulo de tarefa renderizem bem nos dispositivos móveis, se você optar por usar um iframe para hospedar o conteúdo do aplicativo, certifique-se de que a IU seja responsiva e funcione bem em todos os dispositivos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (não use barras de rolagem horizontal)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a>Não fazer: use barras de rolagem horizontal

É uma prática recomendada manter o conteúdo focado e não muito extenso. Se um rolagem for necessária, role verticalmente e não horizontalmente.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Simplicidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (seja breve)." border="false":::

#### <a name="do-keep-it-short"></a>Fazer: seja breve

Você pode criar facilmente um assistente de várias etapas, mas isso não significa necessariamente que você deve! Um módulo de tarefas de várias telas pode ser problemático pois as mensagens de entrada estão distraindo e tentando que os usuários saiam. Se sua tarefa estiver realmente envolvida, saia para uma página da Web completa em vez de um módulo de tarefas.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (não há interações longas)." border="false":::

#### <a name="dont-have-long-interactions"></a>Não fazer: ter interações longas

Tente manter suas interações curtas e diretas.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Mensagens de erro

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Exemplo mostrando a prática recomendada do módulo de tarefas (use mensagens de erro em linha)." border="false":::

#### <a name="do-use-inline-error-messages"></a>Fazer: usar mensagens de erro em linha

Consulte o modelo de IU de formulários para obter orientações sobre o tratamento de erros em linha.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Exemplo mostrando uma prática recomendada do módulo de tarefas (colocar mensagens de erro em caixas de diálogo)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Não fazer: colocar mensagens de erro em caixas de diálogo

Não abrir uma mensagem de erro em uma caixa de diálogo sobre um módulo de tarefas. Isso cria uma experiência de usuário confusa.

   :::column-end:::
:::row-end:::
