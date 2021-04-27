---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar aplicativos do Microsoft Teams. Os recursos incluem o Kit de interface do usuário do Microsoft Teams, práticas recomendadas, exemplos e muito mais.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: d7f3e89ce5ad51fb1a8cecddf0b22d59544ecc09
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019878"
---
# <a name="designing-your-microsoft-teams-app"></a>Projetando seu aplicativo do Microsoft Teams

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual apresentando as diretrizes de design do Microsoft Teams.":::

Se você é um designer, gerente de produto, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design corretas para seu aplicativo do Microsoft Teams.

## <a name="teams-app-design-principles"></a>Princípios de design de aplicativos do Teams

Os aplicativos do Teams ajudam as pessoas a alcançarem mais juntos. Use esses princípios para orientar seu design.

:::row:::
   :::column span="":::

### <a name="collaborative"></a>Colaborativo

Os aplicativos do Teams ajudam as pessoas a alcançarem mais juntos. Use esses princípios para orientar seu design.

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

O aplicativo se concentra em cenários principais que se misturam com fluxos de trabalho do Teams.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a>Nativo ou distinto

O aplicativo usa componentes nativos de design do Teams ou seus próprios. Não há combinação de esquemas de cores, controles etc.

   :::column-end:::
   :::column span="":::

### <a name="useful"></a>Útil

O aplicativo se baseia em um cenário que as pessoas precisam fazer no Teams.

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

O aplicativo atende aos requisitos de acessibilidade do Teams em termos de contraste de cores, alternativas de navegação e muito mais.

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a>Bem descrito

Texto, ícones e imagens fazem com que ele seja claro para o que o aplicativo é e como usá-lo.

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a>Criando uma experiência coesiva

Projetar um aplicativo do Teams é como projetar um aplicativo Web convencional, mas também um pouco diferente. Um design efetivo realça os atributos exclusivos do seu aplicativo ao se ajustar naturalmente aos recursos e contextos do Teams.

Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio. Você vai saber o que fazer e o que evitar ao projetar seu aplicativo do Teams (como navegação de vários níveis em uma guia).

## <a name="planning-your-app"></a>Planejando seu aplicativo

Para projetar um aplicativo do Teams de alta qualidade, você deve primeiro entender o que deseja que seu aplicativo faça e como você acha que as pessoas o usarão. Se você ainda não tiver feito isso, desem algum tempo para planejar [corretamente seu aplicativo.](../../concepts/extensibility-points.md)

## <a name="design-fundamentals"></a>Conceitos básicos de design

Saiba os [fundamentos do design de aplicativo do Teams,](design-teams-app-fundamentals.md)incluindo layout, esquemas de cores e muito mais.

## <a name="basic-fluent-ui-components-for-teams"></a>Componentes básicos da interface do usuário do Fluent para o Teams

Com base na interface do usuário fluente, esses são os [elementos fundamentais para a criação de interfaces familiares do Teams.](design-teams-app-basic-ui-components.md)

## <a name="ui-templates"></a>Modelos de Interface de Usuário 

Crie rapidamente designs complexos e de alta fidelidade com modelos para [o Teams comum usar casos e fluxos de trabalho.](design-teams-app-ui-templates.md)

## <a name="app-capabilities"></a>Recursos do aplicativo

Entenda como as pessoas adicionam, usam e gerenciam aplicativos do Teams para aproveitar ao máximo cada recurso em seu design.

* [Aplicativos pessoais](../../concepts/design/personal-apps.md)
* [Guias](../../tabs/design/tabs.md)
* [Extensões de Mensagens](../../messaging-extensions/design/messaging-extension-design.md)
* [Bots](../../bots/design/bots.md)
* [Extensões de reunião](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Módulos de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a>Personalização de aplicativos

Entenda como o administrador do Teams pode personalizar ou renomear o aplicativo com base na necessidade da organização. Essa personalização será habilitada se você definir `configurableProperties` o esquema de manifesto. Para obter mais informações, consulte [Personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> Esse recurso está disponível apenas na visualização do desenvolvedor.
> 
> A personalização do aplicativo permite que os administradores alterem a aparência dos aplicativos carregados por meio de bots, extensões de mensagens, guias e conectores. Por exemplo, se o administrador do Teams personalizar o nome de um aplicativo da *Contoso* para o Agente *contoso,* o aplicativo aparecerá com o novo nome Agente *contoso* para usuários. No entanto, ao adicionar um conector a um chat, na lista os conectores ainda mostrarão o nome do aplicativo como *Contoso*.
> 
> Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).

## <a name="tools-and-samples"></a>Tools and samples

As ferramentas a seguir podem ajudar designers e desenvolvedores a começar:

### <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Projete um aplicativo do Teams com componentes da interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário. O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem ter aparência e comportamento em diferentes cenários do Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Biblioteca de interface do usuário do Microsoft Teams

Exibir e testar modelos individuais de interface do usuário do Teams e componentes relacionados em seu navegador.

> [!div class="nextstepaction"]
> [Experimente a biblioteca da interface do usuário (playground)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importe esses modelos e componentes relacionados diretamente ao seu projeto de aplicativo do Teams.

> [!div class="nextstepaction"]
> [Obter a biblioteca da interface do usuário (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Exemplo de aplicativo

Instale um aplicativo de exemplo para ver como os modelos de interface do usuário são e se comportam em contextos do Teams.

> [!div class="nextstepaction"]
> [Obter o aplicativo de exemplo (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a>Outros recursos

Para saber mais, experimente um dos seguintes recursos.

### <a name="fluent-ui-documentation"></a>Documentação da interface do usuário do Fluent

Obter exemplos de código e detalhes de implementação para os componentes baseados na interface do usuário fluent usados para criar experiências do Teams.

> [!div class="nextstepaction"]
> [Experimente componentes da interface do usuário do Teams (Fluent UI)](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a>Designer de Cartões Adaptáveis

Projete Cartões Adaptáveis em nossa ferramenta baseada na Web.

> [!div class="nextstepaction"]
> [Experimente o designer de Cartões Adaptáveis](https://adaptivecards.io/designer/)
