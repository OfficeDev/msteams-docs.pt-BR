---
title: Criar uma guia na reunião do Microsoft Teams
author: heath-hamilton
description: Orientações e práticas recomendadas para projetar a guia na reunião do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 91981ab79c8e50483568dd0dc750b4e9b3fdef24
ms.sourcegitcommit: b01986739a05c65094618fbe76aeb53d038b1c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48178320"
---
# <a name="design-an-in-meeting-tab"></a>Criar uma guia na reunião

A guia na reunião é uma tela para aumentar a colaboração durante as reuniões. Com base na capacidade de guia do Teams, os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio da reunião por meio de exibições compartilhadas ou baseadas em função.

## <a name="use-cases"></a>Casos de uso

As pessoas podem usar a guia na reunião para:

* Fornecer feedback detalhado (por exemplo, avaliar um candidato a trabalho)
* Criar rapidamente um item de pesquisa, pesquisa ou tarefa para os participantes da reunião
* Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)

## <a name="example"></a>Exemplo

O exemplo a seguir mostra a guia na reunião que exibe o conteúdo do aplicativo de pesquisa.

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="O exemplo mostra como a guia na reunião da reunião pode parecer da perspectiva de um organizador da reunião.":::

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Consulte o cenário completo (figma)</a>

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver outros exemplos de exemplos de uso (figma)</a>

## <a name="anatomy"></a>Anatomia

A guia na reunião exibe o conteúdo do aplicativo usando as seguintes dimensões:

* **Largura**: 280 pixels para a área de WebView. Há 20 pixels de enchimento nos lados esquerdo e direito do WebView.
* **Altura**: sangramento completo para a parte inferior da guia. Há 20 pixels de preenchimento entre a área da WebView e o cabeçalho da guia.

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface de usuário de uma guia na reunião da extensão de reunião." border="false":::

1. **Ícone do aplicativo**: o ponto de entrada para a guia na reunião.
1. **Cabeçalho**: inclui o nome da guia.
1. **Nome**: o nome da instância de tabulação.
1. **Dispensar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.
1. **WebView**: exibe todo o conteúdo de aplicativo de terceiros.

## <a name="behavior"></a>Comportamento

### <a name="scale"></a>Escala

No momento, a largura da guia na reunião é corrigida.

### <a name="scrolling"></a>Rolagem

Veja o que saber sobre rolagem na guia na reunião:

* Você só deve rolar verticalmente.
* Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo).
* O ScrollBar é parte do conteúdo da WebView.

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Ilustração que mostra como a rolagem do conteúdo da WebView na guia na reunião funciona." border="false":::

### <a name="navigation"></a>Navegação

Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem para uma camada secundária. Os usuários devem ser capazes de voltar para a camada anterior.

:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Ilustração mostrando como funciona a navegação para uma camada secundária na guia na reunião." border="false":::

## <a name="components"></a>Componentes

As guias na reunião são criadas principalmente com os seguintes <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">componentes de interface do usuário (figma)</a>, que se baseiam no <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">sistema de design fluente</a>.

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

### <a name="responsiveness"></a>Responsividade

Os layouts de guia na reunião devem poder ser dimensionados para vários tamanhos. Considere como a guia será dimensionada e assumir forma antes, durante e depois da reunião.

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Ilustração mostrando que o conteúdo da guia na reunião parece com uma guia de tela inteira antes e depois de uma reunião." border="false":::

#### <a name="before-the-meeting"></a>Antes da reunião

Certifique-se de que o layout de Tabulação pode se adaptar a um layout à direita ou à esquerda para idiomas diferentes e que os controles se movem para os locais corretos. (Os layouts antes da reunião também podem ser aplicados aos layouts pós-reunião.)

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Ilustração que mostra como o conteúdo da guia de pré-reunião é condensado para a guia na reunião durante uma reunião." border="false":::

#### <a name="during-the-meeting"></a>Durante a reunião

O conteúdo da guia ajusta o layout e o local da guia na reunião.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Ilustração mostrando como você deve projetar a guia na reunião para o tema escuro usado em reuniões do teams." border="false":::

#### <a name="do-design-for-a-dark-theme"></a>Fazer: design para um tema escuro

As reuniões do teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitiva, para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Ilustração que mostra que você não deve usar cores que não conduzam ao tema escuro da equipe." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a>Não: usar cores desconhecidas

As cores que em conflito com o ambiente de reunião podem ser discadas e parecer menos nativas para o Microsoft Teams.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Rolagem

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Ilustração mostrando você só deve permitir rolagem vertical na guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a>Fazer: rolar verticalmente

Os usuários antecipam a rolagem vertical no Teams (e em outros lugares).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Ilustração mostrando como mostrar você não deve permitir rolagem horizontal na guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a>Não: rolar horizontalmente

A rolagem horizontal não é um comportamento esperado no Microsoft Teams. Outras telas no ambiente de reunião rolam verticalmente.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Ilustração mostrando o layout recomendado de uma única coluna na guia na reunião." border="false":::

#### <a name="do-single-columns"></a>Fazer: colunas únicas

Dada a natureza estreita da guia na reunião, é altamente recomendável exibir o conteúdo em uma única coluna.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Ilustração que mostra como um layout de duas colunas na guia na reunião não é ideal." border="false":::

#### <a name="dont-multiple-columns"></a>Não: várias colunas

Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Ilustração mostrar você sempre deve fornecer um botão voltar se seu aplicativo de guia na reunião tiver mais de uma camada de navegação." border="false":::

#### <a name="do-have-a-back-button"></a>Fazer: ter um botão voltar

Se você tiver mais de uma camada de navegação, os usuários devem ser capazes de retornar ao modo de exibição anterior.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Ilustração mostrando que adicionar outro botão fechar na guia na reunião para navegação é redundante e pode causar problemas." border="false":::

#### <a name="dont-include-another-close-button"></a>Não: incluir outro botão fechar

O fornecimento de uma opção para fechar o conteúdo da guia na reunião pode causar problemas, já que já existe um botão fechar no cabeçalho para ignorar a guia na reunião em si.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Ilustração mostrando que você precisa ter cuidado ao usar as modalidades (ou seja, módulos de tarefas) na guia na reunião, de acordo com o espaço limitado." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a>Cuidado: usar caixas de diálogo em um espaço estreito

Caixas de diálogo, como módulos de tarefas, na guia já restrita na reunião podem quebrar e obscurecer o conteúdo.

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a>Acessibilidade

Para obter informações sobre acessibilidade, consulte <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.

## <a name="resources"></a>Recursos

* <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Arquivo de extensões de reunião do Microsoft Teams figma</a>
* [Diretrizes de design de guias](../tabs/design/tabs.md)
* [Diretrizes de design de guias para dispositivos móveis](../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
