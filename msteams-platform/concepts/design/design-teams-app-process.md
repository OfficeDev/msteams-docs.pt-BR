---
title: Processo de criação do aplicativo
author: heath-hamilton
description: Tenha uma ideia geral de como e quando você pode usar as ferramentas e os recursos da Microsoft para criar um aplicativo eficaz do Microsoft Teams.
ms.localizationpriority: mediums
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 40d223180e0f8bcbfcd5aad27a9a3eb4ee571328
ms.sourcegitcommit: 430bf416bb8d1b74f926c8b5d5ffd3dbb0782286
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65297216"
---
# <a name="design-process-for-microsoft-teams-apps"></a>Processo de criação para aplicativos do Microsoft Teams

Há várias ferramentas e recursos para criar seu aplicativo Microsoft Teams. As etapas a seguir descrevem quando e como você pode usá-lo durante o processo de design. (Algumas das etapas podem estar tecnicamente fora do processo de criação, mas estão incluídas para contexto adicional.)

:::image type="content" source="~/assets/images/design-guidelines/teams-app-design-process.png" alt-text="Diagrama mostrando um exemplo do processo de design do aplicativo Teams." border="false":::

## <a name="plan-your-app"></a>Planeje seu aplicativo

A criação de um aplicativo do Teams de alta qualidade exige a compreensão do que você deseja que o aplicativo faça e como você acha que as pessoas o usarão. Antes de começar a projetar, no entanto, responda às seguintes perguntas:

* Quem são os seus usuários?
* Qual é o problema deles?
* Como seu aplicativo pode resolver o problema?
* Com que frequência seu aplicativo será usado?
* Quantas pessoas usarão seu aplicativo?
* Que tipo de retorno sobre o investimento seu aplicativo pode fornecer?

Para obter mais informações, consulte [Entender’ os casos de uso dos aplicativos](~/concepts/design/understand-use-cases.md) e [Mapear casos de uso para o Teams](~/concepts/design/map-use-cases.md).

## <a name="get-teams-design-tools"></a>Obter ferramentas de criação do Teams

A Microsoft fornece ferramentas para facilitar a criação do aplicativo Teams. No mínimo, é altamente recomendável usar o Kit de Interface do Usuário do Microsoft Teams.

### <a name="get-the-microsoft-teams-ui-kit"></a>Obter o Kit de IU do Microsoft Teams

O Kit de Interface do Usuário do Microsoft Teams pode ajudá-lo a desenvolver um aplicativo do Teams eficaz no menor período de tempo. O kit de IU tem tudo o que você vê nesses documentos relacionados à criação de aplicativos do Teams e muito mais, incluindo exemplos e variações abrangentes.

O kit de IU também tem modelos e componentes pré-criados que você pode copiar e modificar conforme necessário, para que você possa gastar mais tempo projetando a melhor experiência do usuário em vez de se preocupar com a aparência de um botão.

> [!TIP]
> **O kit de IU é para mim?** Se você tiver alguma participação na criação de um aplicativo do Teams, sim. Entender como criar um aplicativo do Teams não é útil apenas para designers, mas gerentes de produtos, desenvolvedores que usam IDEs e criadores que criam com ferramentas de pouco código (como o Microsoft Power Platform).

1. Vá para [Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159).
1. Selecione **Duplicar** para abrir o kit de IU. (Talvez seja necessário criar uma conta do Figma primeiro.)

### <a name="try-the-sample-app"></a>Experimente o aplicativo de exemplo

Você pode carregar um aplicativo de exemplo para ver a aparência e o comportamento dos aplicativos no cliente do Teams.

> [!div class="nextstepaction"]
> [Obter o aplicativo de exemplo (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="learn-teams-design-system"></a>Aprenda sobre o sistema de criação do Teams

Leia detalhadamente ou, pelo menos, familiarize-se com os[Conceitos básicos da criação de aplicativos do Teams](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.

## <a name="choose-app-capabilities"></a>Escolher recursos do aplicativo

Após a fase de planejamento, você pode determinar quais recursos do Teams se ajustam aos casos de uso do seu aplicativo. Por exemplo, se você quiser notificar as pessoas proativamente, um bot pode ser a funcionalidade certa.

O kit de IU tem designs pré-criados que mostram como as pessoas normalmente adicionam, configuram, usam e gerenciam cada funcionalidade. Para referência rápida, essas informações também estão nesses documentos, mas com o kit de interface do usuário, você pode copiar e colar qualquer um desses designs no design do aplicativo.

1. Na navegação esquerda do kit de IU, acesse **Funcionalidades do aplicativo** e selecione a funcionalidade desejada para seu aplicativo.
1. Copie o que você precisa dessa página para criar seu aplicativo.<br />
   Por exemplo, se seu aplicativo der suporte à autenticação com logon único, copie e cole o design para lidar com esse cenário exato.

## <a name="design-your-ux-flow"></a>Projetar seu fluxo de experiência do usuário

Depois de ter um design de aplicativo básico, você pode modificá-lo e refiná-lo o quanto quiser copiando modelos de interface do usuário do Teams e componentes básicos do kit de IU.

### <a name="design-with-ui-templates"></a>Criação com modelos de IU

Os modelos de IU são designs complexos e de alta fidelidade para fluxos de trabalho e casos de uso comuns do Teams. Em vez de começar de baixo para cima com componentes básicos, recomendamos que você use esses modelos para simplificar e acelerar o processo de design.

1. Na navegação esquerda do kit de interface do usuário, vá para **modelos de UI**.
1. Copie modelos que fazem sentido para o design do aplicativo.<br />
   Por exemplo, se você estiver criando um aplicativo pessoal, convém usar um modelo de Painel.

### <a name="design-with-basic-ui-components"></a>Design com componentes básicos da IU

Com base na Fluent UI, esses são os principais elementos para criar interfaces conhecidas do Teams. Use esses componentes se um modelo de interface do usuário não tiver algo de que você precisa ou se você quiser apenas projetar seu aplicativo do zero.

1. Na navegação esquerda do kit de IU, vá para **Componentes básicos de UI**.
1. Copie os componentes necessários para o design do aplicativo (por exemplo, um botão ou um botão de alternância).

## <a name="implement-your-design"></a>Implemente seu design

O design foi concluído e você está pronto para começar a criar. As ferramentas a seguir podem ajudar a simplificar o desenvolvimento de front-end do seu aplicativo.

### <a name="build-with-ui-templates"></a>Crie com modelos de IU

Se você usou modelos de interface do usuário em seu design, poderá implementar esses modelos com a Biblioteca de IU do Microsoft Teams (uma biblioteca de componentes do React com base na Fluent UI).

Atualmente, nem todos os modelos listados no kit de IU estão disponíveis na biblioteca.

> [!div class="nextstepaction"]
> [Obter a biblioteca (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="build-with-basic-ui-components"></a>Crie com componentes básicos da IU

Diferentemente da fase de criação, você pode usar esses componentes da Fluent UI em seu projeto de aplicativo se um modelo de IU não tiver algo de que você precisa ou se quiser apenas compilar o aplicativo do zero. 

(Observação: se você observar algo ausente ou tiver uma ideia para um modelo, considere contribuir para o repositório da Biblioteca de IU do Teams.)

> [!div class="nextstepaction"]
> [Obter a biblioteca (Fluent UI)](https://fluentsite.z22.web.core.windows.net/)

## <a name="review-design-resources"></a>Examinar recursos de design

Se você está apenas começando em seu aplicativo ou perto de um aplicativo pronto para produção, recomendamos que você examine periodicamente os seguintes recursos:

* **Diretrizes de validação da loja do Microsoft Teams**: Fornece padrões pelos quais todos os aplicativos do Teams devem se esforçar, e não apenas os aplicativos listados na loja. Para obter mais informações, consulte as [diretrizes](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).
* **Práticas recomendadas de design**: esses documentos e o kit de IU fornecem práticas recomendadas para a criação de aplicativos de alta qualidade. Por exemplo, consulte as [práticas recomendadas para criar bots](~/bots/design/bots.md#best-practices).

## <a name="see-also"></a>Confira também

[Criando notificações de feed de atividades](~/concepts/design/activity-feed-notifications.md)
