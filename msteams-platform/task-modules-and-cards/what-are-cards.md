---
title: Cartões
description: Descreve cartões e como eles são usados em bots, conectores e extensões de mensagens
localization_priority: Normal
keywords: conectores de mensagens de cartões de bots
ms.topic: overview
ms.openlocfilehash: f895423e5755dd85a7618b8907c4c3b0acbc3cf4
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140541"
---
# <a name="cards"></a>Cartões

Um cartão é um contêiner de interface do usuário (UI) para informações curtas ou relacionadas. Os cartões podem ter várias propriedades e anexos e podem incluir botões, que disparam ações [de cartão.](~/task-modules-and-cards/cards/cards-actions.md) Usando cartões, você pode organizar informações em grupos e dar aos usuários a oportunidade de interagir com partes específicas das informações.

Os bots para Teams suportam os seguintes tipos de cartões: Cartão Adaptável, cartão de herói, cartão de lista, cartão de Office 365 Conector, cartão de recebimento, cartão de entrada, cartão de miniatura e coleções de cartões. Você pode adicionar formatação de rich text aos cartões usando Markdown ou HTML, dependendo do tipo de cartão. Cartões usados por bots e extensões de mensagens em Microsoft Teams, adicione e responda a essas ações de cartão, `openUrl` , , , e `messageBack` `imBack` `invoke` `signin` .

Teams usa cartões em três locais diferentes:

* Conectores
* Bots
* Extensões de mensagens

## <a name="cards-in-connectors"></a>Cartões em conectores

Os cartões foram definidos pela primeira vez como parte do Outlook e Office 365 e agora são usados como parte de Office 365 Conectores. Como muitos Office 365, o Teams dá suporte a conectores. Para obter mais informações, [consulte Office 365 Conectores para Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md). Você pode encontrar a especificação para cartões em conectores em referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference)

## <a name="cards-in-bots"></a>Cartões em bots

O Microsoft Bot Framework estende a especificação de cartões adicionando um conjunto de cartões predefinidos que os bots podem usar como parte das mensagens bot. Teams oferece suporte a bots usando a Estrutura de Bot, mas oferece suporte a um conjunto diferente dessas cartas. Informações gerais sobre cartões no Bot Framework podem ser encontradas em [adicionar anexos de cartão rich card a mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards). Esses cartões são chamados de cartões simples Teams.

Os bots no Teams podem usar cartões simples, cartões de conector ou Cartões Adaptáveis. [Tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md) fornece informações sobre cartões, com suporte de bots em Teams.

## <a name="cards-in-messaging-extensions"></a>Cartões em extensões de mensagens

[Extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) também podem retornar um cartão. As extensões de mensagens podem usar cartões simples, cartões de conector ou Cartões Adaptáveis. Esses cartões são encontrados [em tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="types-of-cards"></a>Tipos de cartões

Todos os cartões usados por Teams estão listados em [tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md). Essa referência também descreve as diferenças entre cartões e cartões da Estrutura de Bot no Teams.

## <a name="adaptive-cards"></a>Cartões Adaptáveis

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

[Cartões adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) são uma nova especificação de produto cruzado para cartões em produtos Microsoft, incluindo bots, Cortana, Outlook e Windows. Eles são o tipo de cartão recomendado para novos Teams desenvolvimento. Para obter informações gerais da equipe cartões adaptáveis, consulte [Adaptive Cards overview](/adaptive-cards). Você pode usar Cartões Adaptáveis em qualquer lugar que você use cartões de herói existentes, Office 365 cartões de Office 365 e cartões de miniatura.

Além dos Cartões Adaptáveis, o Teams oferece suporte a dois outros tipos de cartões:

* Cartões conectores: usados como parte de conectores Office 365 conectores.
* Cartões simples: usados a partir da Estrutura de Bot, como a miniatura e os cartões de herói.

### <a name="adaptive-cards-and-incoming-webhooks"></a>Cartões adaptáveis e Webhooks de entrada

> [!VIDEO https://www.youtube-nocookie.com/embed/y5pbJI43Zvg]

> [!NOTE]
> * Todos os elementos de esquema de Cartão Adaptável nativos, exceto `Action.Submit` , são totalmente suportados.
> * As ações suportadas são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard,**](https://adaptivecards.io/explorer/Action.ShowCard.html) [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)e [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Cartões adaptáveis com Webhooks de entrada permite que você use os recursos avançados e flexíveis de Cartões Adaptáveis. Ele envia dados usando Webhooks de entrada Teams de seu serviço Web.

## <a name="see-also"></a>Também consulte

* [Formatar cartões em Teams](~/task-modules-and-cards/cards/cards-format.md)
* [Projetar cartões adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md)