---
title: Visão geral das Ações Universais para Cartões Adaptáveis
description: Conheça as Ações Universais para Cartões Adaptáveis, como exibições específicas do usuário, suporte a fluxo de trabalho sequencial e muito mais para ambientes de área de trabalho e móveis
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: 82f2120164b745d021f2d2d8921ac8492015c6ed
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142084"
---
# <a name="universal-actions-for-adaptive-cards"></a>Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis evoluíram dos comentários do desenvolvedor de que, embora o layout e a renderização para Cartões Adaptáveis fosse universal, a manipulação de ações não era. Mesmo que um desenvolvedor queira enviar o mesmo cartão para locais diferentes, ele precisa lidar com ações de maneira diferente.

As Ações Universais para Cartões Adaptáveis trazem o bot como o back-end comum para lidar com ações e introduz um novo tipo de ação, `Action.Execute`que funciona em aplicativos, como Teams e Outlook.

Este documento ajuda você a entender como você pode usar o modelo de Ações Universais para aprimorar a experiência do usuário de interagir com Cartões Adaptáveis em plataformas e aplicativos.

> [!NOTE]
> O suporte para Ações Universais para Cartões Adaptáveis v1.4 só está disponível para cartões enviados pelo bot. O suporte para cartões enviados por meio da caixa de redação e do link de cartões desfraláveis estará disponível em breve.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Aprimorar as experiências do usuário com Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis aprimoram a experiência do usuário habilitando os seguintes cenários:

* [Ações Universais](#universal-actions)
* [Exibições Específicas do Usuário](#user-specific-views)
* [Suporte a fluxo de trabalho sequencial](#sequential-workflow-support)
* [Modos de exibição atualizados](#up-to-date-views)

### <a name="universal-actions"></a>Ações Universais

Antes das Ações Universais para Cartões Adaptáveis, hosts diferentes forneceram modelos de ação diferentes da seguinte maneira:

* Teams ou bots usados`Action.Submit`, uma abordagem que adia o modelo de comunicação real para o canal subjacente.
* Outlook para `Action.Http` se comunicar com o serviço de back-end especificado explicitamente no conteúdo do Cartão Adaptável.

A imagem a seguir mostra o modelo de ação inconsistente atual:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Modelo de ação inconsistente":::

Com as Ações Universais para Cartões Adaptáveis, você pode usar `Action.Execute` para o tratamento de ações em diferentes plataformas. `Action.Execute`funciona entre hubs, incluindo Teams e Outlook. Além disso, um Cartão Adaptável pode ser retornado como resposta para uma `Action.Execute` solicitação de invocação disparada.

A imagem a seguir mostra o novo modelo de Ação Universal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Novas ações universais para cartões adaptáveis":::

Agora você pode enviar o mesmo cartão para ambos, Teams e Outlook e mantê-los em sincronia entre si usando o bot subjacente. Qualquer ação executada em qualquer plataforma é refletida para a outra com esse build uma vez *, implante* em qualquer lugar (ações universais para cartões adaptáveis).

A imagem a seguir ilustra as Ações Universais para Cartões Adaptáveis para Teams e Outlook:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/mobile-universal-bots-teams-outlook.png" alt-text="Cartão mesmo móvel para Teams e Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Mesmo cartão para Teams e Outlook" lightbox="../../../assets/images/adaptive-cards/universal-bots-teams-outlook.png":::

* * *

### <a name="user-specific-views"></a>Exibições Específicas do Usuário

Hoje, todos os usuários Teams chat ou canal veem exatamente a mesma exibição e ações de botão no Cartão Adaptável. No entanto, em determinados cenários, há um requisito para que determinados usuários atuem de forma diferente e tenham acesso a informações diferentes dentro do mesmo chat ou canal.

Por exemplo, se você enviar um cartão de relatório de incidentes em um chat ou canal, somente o usuário atribuído ao incidente deverá ver um **botão** Resolver. Por outro lado, o criador do incidente deve ver um  botão Editar e todos os outros usuários só devem ser capazes de exibir detalhes do incidente. Isso é possível por exibições específicas do usuário que estão habilitadas pela `refresh` propriedade.

A imagem a seguir mostra um exemplo de uma me (extensão de mensagem de tíquete), em que diferentes usuários no chat são mostrados ações diferentes com base no requisito:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Exibições específicas do usuário móvel" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

* * *

Para obter mais informações, consulte [o exemplo de exibições específicas do usuário](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Suporte a fluxo de trabalho sequencial

Com o suporte ao Fluxo de Trabalho Sequencial, os usuários podem passar por uma série de fluxos de trabalho sem enviar cartões diferentes separadamente. Isso é possibilitado pela capacidade de retornar `Action.Execute` um Cartão Adaptável em resposta a uma ação. Além disso, qualquer usuário no chat ou canal pode progredir pelo fluxo de trabalho sem modificar o cartão para outros usuários no chat.

A imagem a seguir ilustra um exemplo de bot de pedidos de alimentos: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

A imagem a seguir mostra os vários estados para diferentes usuários no chat ou canal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados do bot de bufê" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

Para obter mais informações, consulte [o exemplo de Fluxo de Trabalho Sequencial](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Modos de exibição atualizados

Você pode criar Cartões Adaptáveis que são atualizados automaticamente. Por exemplo, pode ser uma solicitação de aprovação enviada por um usuário. Após a aprovação, o cartão deve exibir automaticamente os detalhes sobre o tempo de aprovação da solicitação e quem aprovou. O modelo de atualização permite que você forneça esses modos de exibição atualizados. A imagem a seguir mostra um fluxo de aprovação de várias etapas e como as exibições para diferentes usuários são mostradas.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Exibições específicas do usuário atualizadas" lightbox="../../../assets/images/adaptive-cards/universal-bots-up-to-date-views.png":::

Para obter mais informações, consulte [o exemplo de exibições atualizadas](Up-To-Date-Views.md).

Agora, você pode entender como os Cartões Adaptáveis podem ser transformados com o novo modelo de Ações Universais para fornecer uma experiência de usuário exclusiva e aprimorada.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Cartões Adaptáveis e o novo modelo de Ações Universais

Cartões Adaptáveis são uma combinação de conteúdo, como texto e elementos gráficos, e ações que podem ser executadas por um usuário. Para obter mais informações, [Cartões Adaptáveis](http://adaptivecards.io/). As novas Ações Universais para Cartões Adaptáveis permitem uma manipulação comum das ações de Cartão Adaptável em plataformas e aplicativos. Para obter mais informações, consulte [Modelo de Ação Universal](/adaptive-cards/authoring-cards/universal-action-model).

Você pode começar atualizando cenários usando o [guia de início rápido]. (Work-with-universal-actions-for-adaptive-cards.md) e aproveite as Ações Universais.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)

## <a name="see-also"></a>Confira também

* [O que são bots](~/bots/what-are-bots.md)
* [Visão geral dos Cartões Adaptáveis](~/task-modules-and-cards/what-are-cards.md)
* [Cartões Adaptáveis @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Cartões Adaptáveis @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460).
