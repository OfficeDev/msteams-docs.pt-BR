---
title: Apresentando cartões
description: Descreve cartões e como eles são usados em bots, conectores e extensões de mensagens
keywords: mensagens de cartões de bots de conectores
ms.openlocfilehash: 00c649a1339f05b782e03a2c0db5cba2445f66bc
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777921"
---
# <a name="cards"></a>Cartões

Um *cartão* é um contêiner de interface do usuário (UI) para informações curtas ou relacionadas. Os cartões podem ter várias propriedades e anexos. Cartões podem incluir botões que podem disparar ações [de cartão](~/task-modules-and-cards/cards/cards-actions.md).

## <a name="adaptive-cards"></a>Cartões adaptáveis

[Cartões adaptáveis são](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) uma nova especificação cruzada de produtos para cartões em produtos da Microsoft, incluindo Bots, Cortana, Outlook e Windows. Eles são o tipo de cartão recomendado para o desenvolvimento do novo Teams. Para obter informações gerais da equipe de cartões adaptáveis, consulte [Visão geral dos cartões adaptáveis.](/adaptive-cards) Você pode usar cartões adaptáveis em qualquer lugar que possa usar cartões Hero, cartões do Office365 e cartões em miniatura existentes.

Além dos Cartões Adaptáveis, o Teams dá suporte a dois outros tipos de cartões:

* Cartões de conector, usados como parte dos conectores do Office 365.
* Cartões simples da estrutura de bot, como cartões de miniatura e herói.

Esses tipos de cartão são descritos com mais detalhes na Referência [de Cartão do Teams.](~/task-modules-and-cards/cards/cards-reference.md)

O Teams usa cartões em três lugares diferentes:

* Conectores
* Bots
* Extensões de mensagens

## <a name="adaptive-cards-and-incoming-webhooks"></a>Cartões adaptáveis e webhooks de entrada

> [!NOTE]
>
> ✔ Todos os elementos nativos do esquema de placa adaptável, exceto `Action.Submit`, são totalmente suportados.
>
> ✔ As ações com suporte são [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)e [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

## <a name="cards-in-connectors"></a>Cartões em Conectores

Os cartões foram definidos pela primeira vez como parte do Outlook e do Office 365 e são usados como parte dos Conectores do Office 365. Como muitos aplicativos do Office 365, o Teams dá suporte a Conectores. Você pode saber mais sobre conectores nos Conectores do [Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)para o Microsoft Teams e encontrar a especificação para cartões em conectores na referência de cartão de mensagem a [actionable.](/outlook/actionable-messages/card-reference)

## <a name="cards-in-bots"></a>Cartões em bots

O Microsoft Bot Framework estendeu a especificação dos cartões adicionando um conjunto de cartões predefinidos que os bots podem usar como parte das mensagens de bot. O Teams dá suporte a bots usando a Estrutura de Bot, mas dá suporte a um conjunto ligeiramente diferente desses cartões. Informações gerais sobre cartões no Bot Framework podem ser encontradas em [Adicionar anexos de cartão ricos às mensagens.](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards) Esses cartões são chamados *de cartões simples* no Teams.

Os bots no Teams podem usar qualquer tipo de cartão: simples, conector ou adaptável. Cartões que são suportados por bots no Teams são detalhados na Referência [de cartão do Teams.](~/task-modules-and-cards/cards/cards-reference.md)  

## <a name="cards-in-messaging-extensions"></a>Cartões em Extensões de Mensagens

[As Extensões de Mensagens](~/messaging-extensions/what-are-messaging-extensions.md) também podem retornar um cartão. Extensões de mensagens podem usar qualquer tipo de cartão: simples, conector ou adaptável. Esses cartões são encontrados na Referência [de Cartão do Teams.](~/task-modules-and-cards/cards/cards-reference.md)

## <a name="card-reference"></a>Referência de cartão

Todos os cartões usados pelo Teams estão listados na Referência [de Cartão do Teams.](~/task-modules-and-cards/cards/cards-reference.md) Essa referência também descreve as diferenças entre cartões e cartões do Bot Framework no Teams.
