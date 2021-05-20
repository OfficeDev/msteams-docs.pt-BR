---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Aprenda a projetar Microsoft Teams aplicativos. Os recursos incluem o kit de interface do usuário Microsoft Teams, práticas recomendadas, exemplos e muito mais.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 2f21872bd8c37026528ff6fde282e8c433d5e052
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565113"
---
# <a name="designing-your-microsoft-teams-app"></a>Projetando seu aplicativo de Microsoft Teams

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual introduzindo as diretrizes de design Microsoft Teams.":::

Se você é um designer, gerente de produto, desenvolvedor ou fabricante usando ferramentas de baixo código, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design certas para o seu aplicativo Microsoft Teams.

## <a name="teams-app-design-principles"></a>Teams princípios de design de aplicativos

Teams aplicativos ajudam as pessoas a alcançar mais juntos. Use esses princípios para orientar seu design.

:::row:::
   :::column span="":::

### <a name="collaborative"></a>colaborativo

Teams aplicativos ajudam as pessoas a alcançar mais juntos. Use esses princípios para orientar seu design.

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a>confiável

O aplicativo é seguro e compatível. Os usuários podem facilmente encontrar informações sobre privacidade.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a>Globalmente inclusivo

Pessoas de todas as origens, habilidades e disciplinas podem usar o aplicativo. É cultural, racial e socialmente consciente.

   :::column-end:::
   :::column span="":::

### <a name="light"></a>Leve

O aplicativo se concentra em cenários centrais que se misturam com fluxos de trabalho Teams.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a>Nativo ou distinto

O aplicativo usa componentes nativos de design Teams ou seus próprios. Não há mistura de esquemas de cores, controles, e assim por diante.

   :::column-end:::
   :::column span="":::

### <a name="useful"></a>útil

O aplicativo é baseado em um cenário que as pessoas precisam fazer em Teams.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a>Fácil de usar

A interface do usuário é fácil de entender, agradável no visual e no tom, e torna as pessoas mais produtivas.

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a>Dinâmico

O aplicativo é dispositivo e tela agnóstica.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a>Acessíveis

O aplicativo atende Teams requisitos de acessibilidade em termos de contraste de cores, alternativas de navegação e muito mais.

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a>Bem descrito

Texto, ícones e imagens deixam claro para que é o aplicativo e como usá-lo.

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a>Criando uma experiência coesa

Projetar um aplicativo Teams é como projetar um aplicativo web convencional — mas também um pouco diferente. Um design eficaz destaca os atributos exclusivos do seu aplicativo, ao mesmo tempo em que se encaixa naturalmente com Teams recursos e contextos.

Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio. Você saberá o que fazer e o que evitar ao projetar seu aplicativo Teams (como navegação multiníníveis em uma guia).

## <a name="planning-your-app"></a>Planejando seu aplicativo

Para projetar um aplicativo de Teams de alta qualidade, você deve primeiro entender o que você quer que seu aplicativo faça e como você acha que as pessoas vão usá-lo. Se você ainda não tem, tire um tempo para planejar corretamente [seu aplicativo](../../concepts/extensibility-points.md).

## <a name="design-fundamentals"></a>Conceitos básicos de design

Conheça os [fundamentos do design de aplicativos Teams](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.

## <a name="basic-fluent-ui-components-for-teams"></a>Componentes básicos da interface do usuário fluente para Teams

Com base na Interface Fluent, estes são os [elementos centrais para criar interfaces Teams familiares](design-teams-app-basic-ui-components.md).

## <a name="ui-templates"></a>Modelos de Interface de Usuário 

Crie rapidamente designs complexos e de alta fidelidade com [modelos para casos de uso de Teams comum e fluxos de trabalho](design-teams-app-ui-templates.md).

## <a name="app-capabilities"></a>Recursos do aplicativo

Entenda como as pessoas adicionam, usam e gerenciam aplicativos Teams para aproveitar ao máximo cada capacidade em seu design.

* [Aplicativos pessoais](../../concepts/design/personal-apps.md)
* [Guias](../../tabs/design/tabs.md)
* [Extensões de Mensagens](../../messaging-extensions/design/messaging-extension-design.md)
* [Bots](../../bots/design/bots.md)
* [Extensões de reunião](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Módulos de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a>Personalização de aplicativos

Entenda como o administrador Teams pode personalizar ou renomear o aplicativo com base na necessidade da organização. Esta personalização é habilitada se você definir o `configurableProperties` esquema manifesto. Para obter mais informações, consulte [Personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> A personalização de aplicativos permite que os administradores alterem a aparência dos aplicativos carregados através de bots, extensões de mensagens, guias e conectores. Por exemplo, se o administrador Teams personalizar o nome de um aplicativo de *Contoso* para *Agente Contoso,* então o aplicativo aparecerá com o novo nome *Agente Contoso* para os usuários. No entanto, ao adicionar um conector a um chat, na lista os conectores ainda mostrarão o nome do aplicativo como *Contoso*.
> 
> Como uma prática recomendada, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes seguirem ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

## <a name="tools-and-samples"></a>Tools and samples

As seguintes ferramentas podem ajudar designers e desenvolvedores a começar:

### <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Projete um aplicativo Teams com componentes de interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário. O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem parecer e se comportar em diferentes cenários Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams Biblioteca de Interface do Usuário

Exibir e testar modelos de interface do usuário individuais Teams e componentes relacionados no seu navegador.

> [!div class="nextstepaction"]
> [Experimente a biblioteca de interface do usuário (playground)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importe esses modelos e componentes relacionados diretamente no seu projeto de aplicativo Teams.

> [!div class="nextstepaction"]
> [Obtenha a biblioteca de interface do usuário (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Aplicativo de amostra

Instale um aplicativo de exemplo para ver como os modelos de interface do usuário parecem e se comportam dentro de Teams contextos.

> [!div class="nextstepaction"]
> [Obtenha o aplicativo de amostra (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a>Outros recursos

Para saber mais, experimente um dos seguintes recursos:

### <a name="fluent-ui-documentation"></a>Documentação de interface do usuário fluente

Obtenha amostras de código e detalhes de implementação para os componentes baseados em Interface do Usuário Fluentes usados para construir experiências Teams.

> [!div class="nextstepaction"]
> [Experimente Teams componentes de interface do usuário (Fluent UI)](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a>Designer de Cartões Adaptativos

Design Adaptive Cards em nossa ferramenta baseada na Web.

> [!div class="nextstepaction"]
> [Experimente o designer de Cartões Adaptativos](https://adaptivecards.io/designer/)
