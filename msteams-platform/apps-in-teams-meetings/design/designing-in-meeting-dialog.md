---
title: Desenvolva uma conversa na reunião
author: heath-hamilton
description: Saiba como projetar com eficiência uma caixa de diálogo de reunião do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: f2ac0df3ce28293d9e3f61f45dd2d460dc01f2e9
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452670"
---
# <a name="design-an-in-meeting-dialog"></a>Desenvolva uma conversa na reunião

Caixas de diálogo na reunião exibidas no estágio de reunião do teams. Eles exigem a atenção, a confirmação ou a interação de um usuário, mas são sutis e não interrompem a reunião.

## <a name="use-cases"></a>Casos de uso

As caixas de diálogo na reunião são acionadas por um usuário (como o organizador da reunião) que pode querer que os participantes:

* Fornecer breve feedback
* Faça uma rápida pesquisa ou sondagem
* Enviar aprovações
* Receber lembretes

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o que a caixa de diálogo de reunião pode parecer da perspectiva de um participante da reunião. Como você pode ver, o conteúdo e a tarefa são leves.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-participant-view.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião.":::

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Consulte o cenário completo (figma)</a>

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver outros exemplos de exemplos de uso (figma)</a>

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

1. **ícone de aplicativo**
1. **Nome do aplicativo**
1. **Cadeia de caracteres de ação**
1. **Fechar ícone:** Fecha uma única caixa de diálogo. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.
1. **WebView**: exibe todos os botões e o conteúdo do aplicativo de terceiros (botões Standard Teams recomendado).

### <a name="sizing"></a>Size

As caixas de diálogo de reunião podem variar de tamanho para conta para diferentes casos de uso, mas você deve sempre manter os tamanhos de preenchimento e de componente.

* **Altura**: a altura da caixa de diálogo é determinada pelo conteúdo do WebView. A rolagem vertical assume o conteúdo que excede a altura máxima especificada.
* **Largura**: a largura do WebView é um valor absoluto dentro do intervalo especificado.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-sizing.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

## <a name="behavior"></a>Comportamento

Consulte comportamento geral da caixa de diálogo de reunião, como REST, carregando e mais, no <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.

### <a name="position"></a>Position

As caixas de diálogo de reunião são alinhadas no centro do estágio da reunião. Eles não podem ser arrastados e funcionam dentro da estrutura de notificações de nível de sistema do teams.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-position.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

### <a name="aggregation"></a>Agregação

Apenas uma caixa de diálogo é exibida por vez, pilha de classificação da última para a mais recente enviada para a parte inferior. Depois que uma caixa de diálogo for resolvida ou ignorada, a próxima assumirá seu lugar.

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver um exemplo (figma)</a>

### <a name="scrolling"></a>Rolagem

A rolagem ocorre na parte do WebView de uma caixa de diálogo de reunião. Lembre-se do seguinte sobre a rolagem:

* Você só deve rolar verticalmente.
* Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo).

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-scroll.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

### <a name="buttons"></a>Botões

Os botões de diálogo na reunião fazem parte do WebView ([Veja alguns exemplos](#best-practices)).

Ao contrário de componentes semelhantes, as caixas de diálogo de reunião são ignoradas quando um usuário seleciona um botão.

## <a name="components"></a>Componentes

As caixas de diálogo na reunião são criadas principalmente com os seguintes <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">componentes de interface do usuário (figma)</a>, que se baseiam no <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">sistema de design fluente</a>.

Componente | Diretrizes | Exemplo
 - | - | -
Botão | Os botões principal e secundário podem ser médios ou pequenos | Enviar uma resposta
Input | Campo para Brief entradas do usuário. O texto do rótulo pode incluir um ícone  | Inserir comentários
Lista suspensa | Selecione uma ou mais opções de uma lista. Pode incluir recursos de pesquisa e seleção múltipla | Escolha um idioma
Controles de seleção | Use caixas de seleção para várias opções ou botões de opção e alterna para opções individuais. Para seleções mais detalhadas, use um controle deslizante | Votar em uma votação
Alertas | Independentemente de exibir uma mensagem urgente, estado de erro ou aviso, a mensagem deve ser curta e não interromperá a tarefa atual do usuário | Exibir problema ao enviar uma resposta

## <a name="theming"></a>Temas

### <a name="colors"></a>Cores

Use o <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">esquema de cores recomendado (figma)</a> para planos de fundo, primeiro plano e transmitir Estados.

### <a name="typography"></a>Tipografia

Use os <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">tamanhos de fonte e pesos (figma) recomendados</a> para títulos, corpo de texto e texto de metadados.

## <a name="best-practices"></a>Práticas recomendadas

Enquanto as caixas de diálogo em reunião podem fazer chamadas mais eficazes, elas também podem derail chamadas se forem muito discretas. Em geral, use as caixas de diálogo com moderação e siga estas práticas recomendadas.

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-keep-it-contained"></a>Fazer: manter continha

Limite o conteúdo da caixa de diálogo de reunião para uma tela única, para que os usuários possam se concentrar na reunião.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-include-multiple-steps"></a>Não: incluir várias etapas

As caixas de diálogo de reunião não precisam exigir que os usuários naveguem pelo conteúdo.

   :::column-end:::
:::row-end:::

### <a name="interactions"></a>Interações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-limit-number-of-interactions"></a>Fazer: limitar o número de interações

Remover conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente. Se você precisar de interações complexas, é altamente recomendável exibir seu conteúdo usando uma única coluna na guia na reunião.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Não: apresentar elementos desnecessários

Você pode ser capaz de criar uma única caixa de diálogo de reunião com várias interações, mas muitas podem distrair da reunião.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-use-single-column-layouts"></a>Fazer: usar layouts de uma única coluna

Como as caixas de diálogo estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar frustração do usuário.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-clutter-the-space"></a>Não: desobstruir o espaço

O conteúdo denso ou muito estruturado pode ser confuso e impressionante, especialmente durante uma reunião.

   :::column-end:::
:::row-end:::

### <a name="size"></a>Size

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-keep-it-consistent"></a>Fazer: manter consistente

Isso é importante porque as caixas de diálogo na reunião sempre são exibidas no mesmo local.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-always-fit-to-the-content"></a>Não: sempre se ajusta ao conteúdo

Você pode estar tentando evitar a rolagem horizontal, mas vários tamanhos de diálogo na reunião no mesmo aplicativo são uma experiência inconsistente.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Controles

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Fazer: alinhar à direita a ação principal

É recomendável posicionar a ação mais visualmente pesada para a localização mais à direita.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Não: alinhar ações à esquerda ou ao centro

Isso se desvia do padrão da equipe padrão para o posicionamento de controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a>Acessibilidade

Para obter informações sobre acessibilidade, consulte <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.

## <a name="resources"></a>Recursos

* <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Arquivo de extensões de reunião do Microsoft Teams figma</a>

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
