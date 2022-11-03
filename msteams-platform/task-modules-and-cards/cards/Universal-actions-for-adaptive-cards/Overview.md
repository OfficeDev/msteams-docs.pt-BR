---
title: Visão geral das Ações Universais para Cartões Adaptáveis
description: Saiba Ações Universais para Cartões Adaptáveis, como exibições específicas do usuário, suporte a fluxo de trabalho sequencial e muito mais para ambientes de área de trabalho e móveis
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: 4ee3210391f3a8aaba4b74d3d07ee6507789afed
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833055"
---
# <a name="universal-actions-for-adaptive-cards"></a>Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis evoluíram dos comentários do desenvolvedor de que, embora o layout e a renderização para Cartões Adaptáveis fosse universal, o tratamento de ações não era. Mesmo que um desenvolvedor quisesse enviar o mesmo cartão para lugares diferentes, ele teria que lidar com ações de forma diferente.

Ações Universais para Cartões Adaptáveis trazem o bot como o back-end comum para lidar com ações e apresenta um novo tipo de ação, `Action.Execute`, que funciona entre aplicativos, como Teams e Outlook.

Este documento ajuda você a entender como você pode usar o modelo de Ações Universais para aprimorar a experiência do usuário de interagir com cartões adaptáveis entre plataformas e aplicativos.

> [!NOTE]
> O suporte para Ações Universais para Cartões Adaptáveis v1.4 só está disponível para cartões enviados por bot. O suporte para cartões enviados por meio da caixa de composição e dos cartões de desenrolamento de link está chegando em breve.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Aprimorar experiências do usuário com Ações Universais para Cartões Adaptáveis

As Ações Universais para Cartões Adaptáveis aprimoram a experiência do usuário habilitando os seguintes cenários:

* [Ações Universais](#universal-actions)
* [Exibições Específicas do Usuário](#user-specific-views)
* [Suporte ao fluxo de trabalho sequencial](#sequential-workflow-support)
* [Exibições atualizadas](#up-to-date-views)

### <a name="universal-actions"></a>Ações Universais

Antes das Ações Universais para Cartões Adaptáveis, diferentes hosts forneceram modelos de ação diferentes da seguinte maneira:

* Equipes ou bots usados `Action.Submit`, uma abordagem que adia o modelo de comunicação real para o canal subjacente.
* O Outlook costumava `Action.Http` se comunicar com o serviço de back-end explicitamente especificado no conteúdo do Cartão Adaptável.

A imagem a seguir mostra o modelo de ação inconsistente atual:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Modelo de ação inconsistente":::

Com as Ações Universais para Cartões Adaptáveis, você pode usar `Action.Execute` para o tratamento de ações em diferentes plataformas.

`Action.Execute` funciona em todos os hubs, incluindo Teams e Outlook e não é uma substituição de `Action.Submit`. Por exemplo, se você quiser que um sistema externo faça uma ação e o resultado da ação deve ser enviado de volta para sua conversa usando [a Extensão de Mensagens](../../../messaging-extensions/what-are-messaging-extensions.md), `Action.Execute` não há suporte.

Para cartões [de desenrolamento de link](../../../messaging-extensions/how-to/link-unfurling.md) , como cartões de herói e miniatura, você deve chamar `Action.Submit`.

Além disso, um Cartão Adaptável pode ser retornado como uma resposta para uma solicitação de invocação `Action.Execute` disparada.

A imagem a seguir mostra o novo modelo da Ação Universal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Novas ações universais para cartões adaptáveis":::

Agora você pode enviar o mesmo cartão para o Teams e o Outlook e mantê-los em sincronização entre si usando o bot subjacente. Qualquer ação tomada em qualquer plataforma é refletida para a outra com esse *build uma vez, implantar qualquer* modelo (Ações Universais para Cartões Adaptáveis).

A imagem a seguir mostra as Ações Universais para Cartões Adaptáveis para o Teams e o Outlook:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/mobile-universal-bots-teams-outlook.png" alt-text="Mesmo cartão móvel para o Teams e o Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Mesma carta para o Teams e o Outlook" lightbox="../../../assets/images/adaptive-cards/universal-bots-teams-outlook.png":::

* * *

### <a name="user-specific-views"></a>Exibições Específicas do Usuário

Hoje, cada usuário no chat ou canal do Teams vê exatamente a mesma exibição e ações de botão no Cartão Adaptável. No entanto, em determinados cenários, há um requisito para que determinados usuários atuem de forma diferente e tenham acesso a informações diferentes no mesmo chat ou canal.

Por exemplo, se você enviar um cartão de relatório de incidentes em um chat ou canal, somente o usuário atribuído ao incidente deverá ver um botão **Resolver** . Por outro lado, o criador de incidentes deve ver um botão **Editar** e todos os outros usuários só devem ser capazes de exibir detalhes do incidente. Isso é possível por exibições específicas do usuário habilitadas pela `refresh` propriedade.

A imagem a seguir mostra um exemplo de uma extensão de mensagem de tíquete (ME) em que diferentes usuários no chat são mostrados ações diferentes com base no requisito:

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Exibições específicas do usuário móvel" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

* * *

Para obter mais informações, consulte [exemplo para exibições específicas do usuário](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Suporte ao fluxo de trabalho sequencial

Com suporte ao Fluxo de Trabalho Sequencial, os usuários podem progredir por meio de uma série de fluxos de trabalho sem enviar cartões diferentes separadamente. Isso é possível pela capacidade de `Action.Execute` retornar um Cartão Adaptável em resposta a uma ação. Além disso, qualquer usuário no chat ou canal pode progredir por meio de seu fluxo de trabalho sem modificar o cartão para outros usuários no chat.

A imagem a seguir ilustra um exemplo de bot de ordenação de alimentos: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

A imagem a seguir mostra os vários estados para usuários diferentes no chat ou canal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de catering" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

Para obter mais informações, consulte [exemplo para Fluxo de Trabalho Sequencial](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Exibições atualizadas

Você pode criar cartões adaptáveis que são atualizados automaticamente. Por exemplo, pode ser uma solicitação de aprovação enviada por um usuário. Após a aprovação, o cartão deve exibir automaticamente detalhes sobre o tempo de aprovação da solicitação e quem aprovou a solicitação. O modelo de atualização permite que você forneça exibições atualizadas. A imagem a seguir mostra um fluxo de aprovação de várias etapas e como as exibições para diferentes usuários são mostradas.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Exibições específicas do usuário atualizadas" lightbox="../../../assets/images/adaptive-cards/universal-bots-up-to-date-views.png":::

Para obter mais informações, consulte [exemplo para exibições atualizadas](Up-To-Date-Views.md).

Agora, você pode entender como os Cartões Adaptáveis podem ser transformados com o novo modelo de Ações Universais para fornecer uma experiência de usuário única e aprimorada.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Cartões Adaptáveis e o novo modelo de Ações Universais

Cartões Adaptáveis são uma combinação de conteúdo, como texto e gráficos, e ações que podem ser executadas por um usuário. Para obter mais informações, [Cartões Adaptáveis](http://adaptivecards.io/). As novas Ações Universais para Cartões Adaptáveis permitem um tratamento comum das ações do Cartão Adaptável entre plataformas e aplicativos. Para obter mais informações, consulte [Modelo de Ação Universal](/adaptive-cards/authoring-cards/universal-action-model).

Você pode começar atualizando cenários usando o [guia de início rápido]. (Work-with-universal-actions-for-adaptive-cards.md) e aproveitar ações universais.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)

## <a name="see-also"></a>Confira também

* [O que são bots](~/bots/what-are-bots.md)
* [Visão geral dos Cartões Adaptáveis](~/task-modules-and-cards/what-are-cards.md)
* [Cartões Adaptáveis @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Cartões Adaptáveis @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460).
* [Ações Universais para extensões de mensagens baseadas em pesquisa](../../../messaging-extensions/how-to/search-commands/universal-actions-for-search-based-message-extensions.md)
