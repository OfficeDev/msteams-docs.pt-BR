---
title: Processo de design de aplicativo
author: heath-hamilton
description: Tenha uma ideia geral de como e quando você pode usar ferramentas e recursos da Microsoft para projetar um aplicativo Microsoft Teams eficaz.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: f4d406426cdadd946e3579cec85e8c5c8133c2b5206a00fc1e32a29a2442b7cd
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57704485"
---
# <a name="design-process-for-microsoft-teams-apps"></a>Processo de design para Microsoft Teams aplicativos

Há várias ferramentas e recursos para projetar seu Microsoft Teams app. As etapas a seguir descrevem quando e como você pode usá-los durante o processo de design. (Algumas das etapas podem estar tecnicamente fora do processo de design, mas estão incluídas para contexto adicional.)

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagrama mostrando um exemplo do processo de design Teams aplicativo." border="false":::

## <a name="plan-your-app"></a>Planejar seu aplicativo

Projetar um aplicativo de alta qualidade Teams requer a compreensão do que você deseja que o aplicativo faça e como você acha que as pessoas o usarão. Antes de começar a projetar, no entanto, responda às seguintes perguntas:

* Quem são os seus usuários?
* Qual é o problema deles?
* Como seu aplicativo pode resolver o problema?
* Com que frequência seu aplicativo será usado?
* Quantas pessoas usarão seu aplicativo?
* Que tipo de retorno sobre o investimento seu aplicativo pode fornecer?

Para obter mais informações, consulte [understand your app's use cases and](~/concepts/design/understand-use-cases.md) [mape use cases to Teams](~/concepts/design/map-use-cases.md).

## <a name="get-teams-design-tools"></a>Obter Teams de design

A Microsoft fornece ferramentas para facilitar o design do Teams app. No mínimo, é recomendável usar o kit Microsoft Teams interface do usuário.

### <a name="get-the-microsoft-teams-ui-kit"></a>Obter o Microsoft Teams de interface do usuário

O Microsoft Teams kit de interface do usuário pode ajudá-lo a desenvolver um aplicativo Teams no menor período de tempo. O kit de interface do usuário tem tudo o que você vê nesses documentos relacionados Teams design do aplicativo e muito mais, incluindo exemplos e variações abrangentes.

O kit de interface do usuário também tem modelos e componentes pré-construídos que você pode copiar e modificar conforme necessário, para que você possa gastar mais tempo projetando a melhor experiência do usuário em vez de se preocupar com a aparência de um botão.

> [!TIP]
> **O kit de interface do usuário é para mim?** Se você tiver alguma parte na criação de um aplicativo Teams, sim. Entender como criar um aplicativo Teams não é útil apenas para designers, mas gerentes de produto, desenvolvedores usando IDEs e criadores criando com ferramentas de baixo código (como a Plataforma do Microsoft Power).

1. Vá para a [página Microsoft Teams kit de interface](https://www.figma.com/community/file/916836509871353159)do usuário .
1. Selecione **Duplicar** para abrir o kit de interface do usuário. (Você pode ter que primeiro criar uma conta do Figma.)

### <a name="try-the-sample-app"></a>Experimente o aplicativo de exemplo

Você pode carregar um aplicativo de exemplo para ver como os aplicativos devem parecer e se comportar no Teams cliente.

> [!div class="nextstepaction"]
> [Obter o aplicativo de exemplo (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a>Aprender Teams design do sistema

Leia detalhadamente ou, pelo menos, familiarize-se com os [fundamentos](design-teams-app-fundamentals.md)do design do aplicativo Teams , incluindo layout, esquemas de cores e muito mais.

## <a name="choose-app-capabilities"></a>Escolher recursos do aplicativo

Após a fase de planejamento, você pode determinar quais Teams recursos se encaixam nos casos de uso do aplicativo. Por exemplo, se você quiser notificar proativamente as pessoas, um bot pode ser o recurso certo.

O kit de interface do usuário tem designs pré-construídos que mostram como as pessoas normalmente adicionam, configuram, usam e gerenciam cada recurso. Para referência rápida, essas informações também estão nesses documentos, mas com o kit de interface do usuário você pode copiar e colar qualquer um desses designs no design do aplicativo.

1. Na interface do usuário do kit de interface do usuário à esquerda, acesse Recursos **do** aplicativo e selecione o recurso que você deseja para seu aplicativo.
1. Copie o que você precisa dessa página para projetar seu aplicativo.<br />
   Por exemplo, se seu aplicativo dá suporte à autenticação com um único login, copie e colar o design para lidar com esse cenário exato.

## <a name="design-your-ux-flow"></a>Projetar seu fluxo deux

Depois de ter um design de aplicativo básico Teams, você pode modificá-lo e refiná-lo o quanto quiser, copiando modelos de interface do usuário e componentes básicos do kit de interface do usuário.

### <a name="design-with-ui-templates"></a>Projetar com modelos de interface do usuário

Os modelos de interface do usuário são designs complexos e de alta fidelidade para Teams casos de uso e fluxos de trabalho comuns. Em vez de começar de baixo para cima com componentes básicos, recomendamos que você use esses modelos para simplificar e acelerar o processo de design.

1. Na interface do usuário do kit de interface do usuário à esquerda, vá para modelos **de interface do usuário**.
1. Copie modelos que fazem sentido para o design do aplicativo.<br />
   Por exemplo, se você estiver projetando um aplicativo pessoal, talvez queira usar um modelo de Painel.

### <a name="design-with-basic-ui-components"></a>Projetar com componentes básicos da interface do usuário

Com base Fluent interface do usuário, esses são os elementos principais para criar interfaces Teams familiares. Use esses componentes se um modelo de interface do usuário estiver faltando algo que você precisa ou você só deseja projetar seu aplicativo do zero.

1. Na interface do usuário do kit de interface do usuário à esquerda, vá para **Componentes básicos da interface do usuário**.
1. Copie os componentes necessários para o design do aplicativo (por exemplo, um botão ou alternância).

## <a name="implement-your-design"></a>Implementar seu design

O design foi feito e você está pronto para começar a construir. As ferramentas a seguir podem ajudar a simplificar o desenvolvimento front-end do seu aplicativo.

### <a name="build-with-ui-templates"></a>Criar com modelos de interface do usuário

Se você usou modelos de interface do usuário em seu design, poderá implementar esses modelos com a biblioteca de interface do usuário Microsoft Teams (uma biblioteca de componentes React com base em Fluent interface do usuário).

Atualmente, nem todos os modelos listados no kit de interface do usuário estão disponíveis na biblioteca.

> [!div class="nextstepaction"]
> [Obter a biblioteca (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a>Criar com componentes básicos da interface do usuário

Diferentemente da fase de design, você pode usar esses Fluent de interface do usuário em seu projeto de aplicativo se um modelo de interface do usuário estiver faltando algo que você precisa ou você só deseja criar o aplicativo do zero. 

(Observação: se você notar algo faltando ou tiver uma ideia para um modelo, considere contribuir para o Teams de biblioteca de interface do usuário.)

> [!div class="nextstepaction"]
> [Obter a biblioteca (Fluent interface do usuário)](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a>Revisar recursos de design

Se você está apenas começando em seu aplicativo ou perto de um aplicativo pronto para produção, recomendamos que você revise periodicamente os seguintes recursos:

* Microsoft Teams diretrizes de validação da loja : fornece padrões que todos os Teams aplicativos devem se esforçar e não apenas os **aplicativos** listados na loja. Para obter mais informações, consulte as [diretrizes](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).
* **Práticas recomendadas de** design: esses documentos e o kit de interface do usuário fornecem práticas recomendadas para projetar aplicativos de alta qualidade. Por exemplo, consulte as [práticas recomendadas para projetar bots](~/bots/design/bots.md#best-practices).

