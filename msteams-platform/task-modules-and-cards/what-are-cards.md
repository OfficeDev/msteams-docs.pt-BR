---
title: Apresentando cartões
description: Descreve cartões e como eles são usados em bots, conectores e extensões de mensagens
localization_priority: Normal
ms.topic: conceptual
keywords: conectores de mensagens de cartões de bots
ms.openlocfilehash: 77dcbb7d0472b584623e878df956a6165296f4cf
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088749"
---
# <a name="cards"></a>Cartões

Um *cartão* é um contêiner de interface do usuário (UI) para informações curtas ou relacionadas. Os cartões podem ter várias propriedades e anexos. Os cartões podem incluir botões que podem disparar [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

## <a name="adaptive-cards"></a>Cartões adaptáveis

[Cartões adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) são uma nova especificação de produto cruzado para cartões em produtos Microsoft, incluindo Bots, Cortana, Outlook e Windows. Eles são o tipo de cartão recomendado para novos Teams desenvolvimento. Para obter informações gerais da equipe de cartões adaptáveis, consulte [Visão geral dos cartões adaptáveis.](/adaptive-cards) Você pode usar cartões adaptáveis em qualquer lugar que você possa usar cartões Hero existentes, cartões do Office365 e cartões thumbnail.

Além dos Cartões Adaptáveis, o Teams oferece suporte a dois outros tipos de cartões:

* Cartões conectores, usados como parte de Office 365 conectores.
* Cartões simples da estrutura de bot, como a miniatura e cartões de herói.

Esses tipos de cartão são descritos de forma mais completa [na Teams Referência de Cartão.](~/task-modules-and-cards/cards/cards-reference.md)

Teams usa cartões em três locais diferentes:

* Conectores
* Bots
* Extensões de mensagens

## <a name="adaptive-cards-and-incoming-webhooks"></a>Cartões adaptáveis e webhooks de entrada

> [!NOTE]
>
> ✔ Todos os elementos nativos do esquema de placa adaptável, exceto `Action.Submit`, são totalmente suportados.
>
> ✔ As ações suportadas são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard,**](https://adaptivecards.io/explorer/Action.ShowCard.html) [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html) [**eAction.Execute**](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

## <a name="cards-in-connectors"></a>Cartões em Conectores

Os cartões foram definidos pela primeira vez como parte Outlook e Office 365, e são usados como parte de Office 365 Conectores. Como muitos Office 365, o Teams dá suporte a Conectores. Você pode saber mais sobre conectores em Office 365 [conectores](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)para Microsoft Teams , e encontrar a especificação para cartões em conectores em Referência de cartão de mensagem a [actionable](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Cartões em Bots

O Microsoft Bot Framework estendeu a especificação de cartões adicionando um conjunto de cartões predefinidos que os bots poderiam usar como parte das mensagens bot. Teams oferece suporte a bots usando a Estrutura de Bot, mas oferece suporte a um conjunto ligeiramente diferente dessas cartas. Informações gerais sobre cartões no Bot Framework podem ser encontradas em [Adicionar anexos de cartão rich card a mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards). Esses cartões são chamados *de cartões simples* Teams.

Os bots Teams podem usar qualquer tipo de cartão: simples, conector ou adaptável. Os cartões que são suportados por bots Teams são detalhados [em Teams Referência de Cartão.](~/task-modules-and-cards/cards/cards-reference.md)  

## <a name="cards-in-messaging-extensions"></a>Cartões em Extensões de Mensagens

[Extensões de Mensagens](~/messaging-extensions/what-are-messaging-extensions.md) também podem retornar um cartão. Extensões de mensagens podem usar qualquer tipo de cartão: simples, conector ou adaptável. Esses cartões são encontrados na referência [Teams cartão](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="card-reference"></a>Referência de cartão

Todos os cartões usados por Teams estão listados [na referência Teams cartão](~/task-modules-and-cards/cards/cards-reference.md). Essa referência também descreve as diferenças entre cartões e cartões da Estrutura de Bot no Teams.
