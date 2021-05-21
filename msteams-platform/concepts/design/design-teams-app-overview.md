---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar Microsoft Teams aplicativos. Os recursos incluem Microsoft Teams kit de interface do usuário, práticas recomendadas, exemplos e muito mais.
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
# <a name="designing-your-microsoft-teams-app"></a>Projetando seu Microsoft Teams aplicativo

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual introduzindo as Microsoft Teams de design.":::

Se você é um designer, gerente de produto, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design corretas para seu Microsoft Teams app.

## <a name="teams-app-design-principles"></a>Teams de design de aplicativo

Teams aplicativos ajudam as pessoas a alcançarem mais juntos. Use esses princípios para orientar seu design.

:::row:::
   :::column span="":::

### <a name="collaborative"></a>Colaborativo

Teams aplicativos ajudam as pessoas a alcançarem mais juntos. Use esses princípios para orientar seu design.

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a>Confiável

O aplicativo é seguro e compatível. Os usuários podem encontrar facilmente informações sobre privacidade.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a>Globalmente inclusiva

Pessoas de todos os backgrounds, skillsets e disciplinas podem usar o aplicativo. É cultural, racial e socialmente ciente.

   :::column-end:::
   :::column span="":::

### <a name="light"></a>Leve

O aplicativo se concentra em cenários principais que se misturam com Teams fluxos de trabalho.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a>Nativo ou distinto

O aplicativo usa componentes Teams design nativos ou seus próprios. Não há combinação de esquemas de cores, controles e assim por diante.

   :::column-end:::
   :::column span="":::

### <a name="useful"></a>Útil

O aplicativo se baseia em um cenário que as pessoas precisam fazer Teams.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a>Fácil de usar

A interface do usuário é fácil de entender, agradável na aparência e no tom e torna as pessoas mais produtivas.

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a>Dinâmico

O aplicativo é agnóstico de dispositivo e tela.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a>Acessíveis

O aplicativo atende Teams requisitos de acessibilidade em termos de contraste de cores, alternativas de navegação e muito mais.

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a>Bem descrito

Texto, ícones e imagens fazem com que ele seja claro para o que o aplicativo é e como usá-lo.

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a>Criando uma experiência coesiva

Projetar um aplicativo Teams é como projetar um aplicativo Web convencional, mas também um pouco diferente. Um design eficaz realça os atributos exclusivos do seu aplicativo ao se ajustar naturalmente aos Teams e contextos.

Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio. Você vai saber o que fazer e o que evitar ao projetar seu aplicativo Teams (como navegação de vários níveis em uma guia).

## <a name="planning-your-app"></a>Planejando seu aplicativo

Para projetar um aplicativo de Teams de alta qualidade, você deve primeiro entender o que deseja que seu aplicativo faça e como você acha que as pessoas o usarão. Se você ainda não tiver feito isso, desem algum tempo para planejar [corretamente seu aplicativo.](../../concepts/extensibility-points.md)

## <a name="design-fundamentals"></a>Conceitos básicos de design

Saiba os [fundamentos do Teams de aplicativos](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.

## <a name="basic-fluent-ui-components-for-teams"></a>Componentes básicos da interface do usuário do Fluent para Teams

Com base na interface do usuário fluente, esses são os elementos fundamentais para a criação [de interfaces Teams familiares.](design-teams-app-basic-ui-components.md)

## <a name="ui-templates"></a>Modelos de Interface de Usuário 

Crie rapidamente designs complexos e de alta fidelidade com modelos para Teams casos de uso e [fluxos de trabalho](design-teams-app-ui-templates.md)comuns.

## <a name="app-capabilities"></a>Recursos do aplicativo

Entenda como as pessoas adicionam, usam e gerenciam Teams aplicativos para aproveitar ao máximo cada recurso em seu design.

* [Aplicativos pessoais](../../concepts/design/personal-apps.md)
* [Guias](../../tabs/design/tabs.md)
* [Extensões de Mensagens](../../messaging-extensions/design/messaging-extension-design.md)
* [Bots](../../bots/design/bots.md)
* [Extensões de reunião](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Módulos de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a>Personalização de aplicativos

Entenda como o Teams administrador pode personalizar ou renomear o aplicativo com base na necessidade da organização. Essa personalização será habilitada se você definir `configurableProperties` o esquema de manifesto. Para obter mais informações, consulte [Personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> A personalização do aplicativo permite que os administradores alterem a aparência dos aplicativos carregados por meio de bots, extensões de mensagens, guias e conectores. Por exemplo, se o administrador Teams personalizar o nome de um aplicativo da *Contoso* para o Agente *contoso,* o aplicativo aparecerá com o novo nome Agente *contoso* para usuários. No entanto, ao adicionar um conector a um chat, na lista os conectores ainda mostrarão o nome do aplicativo como *Contoso*.
> 
> Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

## <a name="tools-and-samples"></a>Tools and samples

As ferramentas a seguir podem ajudar designers e desenvolvedores a começar:

### <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Projete um Teams com componentes da interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário. O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem ter aparência e comportamento em diferentes Teams cenários.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams Biblioteca da interface do usuário

Exibir e testar modelos Teams de interface do usuário individuais e componentes relacionados no navegador.

> [!div class="nextstepaction"]
> [Experimente a biblioteca da interface do usuário (playground)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Import these templates and related components directly into your Teams app project.

> [!div class="nextstepaction"]
> [Obter a biblioteca da interface do usuário (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Exemplo de aplicativo

Instale um aplicativo de exemplo para ver como os modelos de interface do usuário são e se comportam Teams contextos.

> [!div class="nextstepaction"]
> [Obter o aplicativo de exemplo (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a>Outros recursos

Para saber mais, experimente um dos seguintes recursos:

### <a name="fluent-ui-documentation"></a>Documentação da interface do usuário do Fluent

Obter exemplos de código e detalhes de implementação para os componentes baseados na interface do usuário fluent usados para criar Teams experiências.

> [!div class="nextstepaction"]
> [Experimente Teams da interface do usuário (interface do usuário fluente)](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a>Designer de Cartões Adaptáveis

Projete Cartões Adaptáveis em nossa ferramenta baseada na Web.

> [!div class="nextstepaction"]
> [Experimente o designer de Cartões Adaptáveis](https://adaptivecards.io/designer/)
