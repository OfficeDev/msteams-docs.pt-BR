---
title: Visão geral das ações universais para cartões adaptáveis
description: Uma visão geral rápida das Ações Universais para Cartões Adaptáveis, como exibições específicas do usuário, suporte ao fluxo de trabalho sequencial e muito mais para ambientes desktop e móveis
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: c294e235074bd6a2c9ae148c20e355a9c86325c5
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889353"
---
# <a name="universal-actions-for-adaptive-cards"></a>Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis evoluíram dos comentários do desenvolvedor que, embora o layout e a renderização para Cartões Adaptáveis fosse universais, o tratamento de ações não era. Mesmo que um desenvolvedor quisesse enviar o mesmo cartão para locais diferentes, ele teria que lidar com ações de maneira diferente.

Ações universais para Cartões Adaptáveis traz o bot como o back-back comum para lidar com ações e introduz um novo tipo de ação, que funciona em aplicativos, como Teams e `Action.Execute` Outlook.

Este documento ajuda você a entender como você pode usar o modelo de Ações Universais para aprimorar a experiência do usuário de interagir com Cartões Adaptáveis em plataformas e aplicativos.

> [!NOTE]
> O suporte para Ações Universais para Cartões Adaptáveis v1.4 só está disponível para cartões enviados por bot. O suporte para cartões enviados por meio da caixa de redação e dos cartões de desfraldamento de link está chegando em breve.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Aprimorar as experiências do usuário com ações universais para cartões adaptáveis

Ações universais para cartões adaptáveis aprimora a experiência do usuário habilitando os seguintes cenários:

* [Ações universais](#universal-actions)
* [Exibições Específicas do Usuário](#user-specific-views)
* [Suporte ao Fluxo de Trabalho Sequencial](#sequential-workflow-support)
* [Exibições atualizadas](#up-to-date-views)

### <a name="universal-actions"></a>Ações universais

Antes das Ações Universais para Cartões Adaptáveis, hosts diferentes forneceam modelos de ação diferentes da seguinte maneira:

* Teams ou bots usados , uma abordagem que adia o modelo de comunicação `Action.Submit` real para o canal subjacente.
* Outlook usado `Action.Http` para se comunicar com o serviço back-end explicitamente especificado na carga cartão adaptável.

A imagem a seguir mostra o modelo de ação inconsistente atual:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Modelo de ação inconsistente":::

Com as Ações Universais para Cartões Adaptáveis, você pode usar para o tratamento `Action.Execute` de ações em diferentes plataformas. `Action.Execute`funciona entre hubs, incluindo Teams e Outlook. Além disso, um Cartão Adaptável pode ser retornado como resposta para uma `Action.Execute` solicitação de invocação disparada.

A imagem a seguir mostra o novo modelo de Ação Universal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Novas ações universais para cartões adaptáveis":::

Agora você pode enviar o mesmo cartão para ambos, Teams e Outlook e mantê-los em sincronia uns com os outros usando o bot subjacente. Qualquer ação realizada em qualquer plataforma é refletida na outra com essa com build uma *vez, implante* em qualquer lugar (Ações Universais para Cartões Adaptáveis).

A imagem a seguir mostra as Ações Universais para Cartões Adaptáveis para Teams e Outlook:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-teams-outlook.jpg" alt-text="Cartão do mesmo celular para Teams e Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Mesmo cartão para Teams e Outlook":::

* * *

### <a name="user-specific-views"></a>Exibições Específicas do Usuário

Hoje, todos os usuários no Teams chat ou canal veem exatamente as mesmas ações de modo de exibição e botão no Cartão Adaptável. No entanto, em determinados cenários, há um requisito para que determinados usuários atuem de forma diferente e tenham acesso a informações diferentes no mesmo chat ou canal.

Por exemplo, se você enviar um cartão de relatório de incidentes em um chat ou canal, somente o usuário atribuído ao incidente deverá ver um **botão Resolver.** Por outro lado, o criador de incidentes deve ver um botão **Editar** e todos os outros usuários só poderão exibir detalhes do incidente. Isso é possível por exibições específicas do usuário que estão habilitadas pela `refresh` propriedade.

A imagem a seguir mostra um exemplo de uma extensão de mensagens de tíquete (ME) onde diferentes usuários no chat são mostrados diferentes ações com base no requisito:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Exibições específicas do usuário móvel":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário":::

* * *

Para obter mais informações, consulte [sample for User Specific Views](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Suporte ao Fluxo de Trabalho Sequencial

Com o suporte ao Fluxo de Trabalho Sequencial, os usuários podem progredir através de uma série de fluxos de trabalho sem enviar cartões diferentes separadamente. Isso é possível pela capacidade de `Action.Execute` retornar um Cartão Adaptável em resposta a uma ação. Além disso, qualquer usuário no chat ou canal pode progredir por meio de seu fluxo de trabalho sem modificar o cartão para outros usuários no chat.

A imagem a seguir ilustra um exemplo de bot de ordenação de alimentos: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

A imagem a seguir mostra os vários estados para diferentes usuários no chat ou no canal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

Para obter mais informações, consulte [sample for Sequential Workflow](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Exibições atualizadas

Você pode criar Cartões Adaptáveis que são atualizados automaticamente. Por exemplo, pode ser uma solicitação de aprovação enviada por um usuário. Após a aprovação, o cartão deve exibir automaticamente detalhes sobre o tempo de aprovação da solicitação e quem aprovou a solicitação. O modelo de atualização permite que você forneça tais exibições atualizadas. A imagem a seguir mostra um fluxo de aprovação em várias etapas e como as exibições para diferentes usuários são mostradas.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Exibições específicas do usuário atualizadas":::

Para obter mais informações, consulte [exemplo de exibições atualizadas](Up-To-Date-Views.md).

Agora, você pode entender como os Cartões Adaptáveis podem ser transformados com o novo modelo de Ações Universais para oferecer uma experiência de usuário exclusiva e aprimorada.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Cartões adaptáveis e o novo modelo de Ações Universais

Cartões adaptáveis são uma combinação de conteúdo, como texto e elementos gráficos, e ações que podem ser executadas por um usuário. Para obter mais informações, consulte [Adaptive Cards](http://adaptivecards.io/). As novas Ações Universais para Cartões Adaptáveis permitem uma manipulação comum das ações do Cartão Adaptável em plataformas e aplicativos. Para obter mais informações, consulte [Modelo de Ação Universal](/adaptive-cards/authoring-cards/universal-action-model).

Você pode começar atualizando cenários usando o [guia](Work-with-universal-actions-for-adaptive-cards.md) de início rápido e aproveitar ações universais.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)

## <a name="see-also"></a>Confira também

* [O que são bots](~/bots/what-are-bots.md)
* [Visão geral dos Cartões Adaptáveis](~/task-modules-and-cards/what-are-cards.md)
* [Cartões adaptáveis @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Cartões adaptáveis @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)
