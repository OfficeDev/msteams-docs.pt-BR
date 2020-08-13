---
title: Apresentando cartões
description: Descreve os cartões e como eles são usados em bots, conectores e extensões de mensagens
keywords: conectores de mensagens dos cartões de bots
ms.openlocfilehash: 6d850f83183f12fa0c228a7a89b23e58f523e15b
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651653"
---
# <a name="cards"></a>Cartões

Um *cartão* é um contêiner de interface do usuário (IU) para informações curtas ou relacionadas. Os cartões podem ter várias propriedades e anexos. Os cartões podem incluir botões que podem acionar [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

## <a name="adaptive-cards"></a>Cartões adaptáveis

Os [cartões adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) são uma nova especificação de produto cruzado para cartões em produtos da Microsoft, incluindo bots, Cortana, Outlook e Windows. Eles são o tipo de cartão recomendado para o desenvolvimento do novo Teams. Para obter informações gerais da equipe de cartões adaptáveis, consulte [visão geral de cartões adaptáveis](/adaptive-cards). Você pode usar cartões adaptáveis em qualquer lugar onde você pode usar cartões herói existentes, cartões do Office365 e cartões de miniaturas.

Além de cartões adaptáveis, o Teams oferece suporte a dois outros tipos de cartões:

* Cartões de conexão, usados como parte dos conectores do Office 365.
* Cartões simples da estrutura de bot, como os cartões de miniatura e herói.

Esses tipos de cartão são descritos com mais detalhes na [referência de cartão de equipes](~/task-modules-and-cards/cards/cards-reference.md).

O Microsoft Teams usa cartões em três locais diferentes:

* Conectores
* Bots
* Extensões de mensagens

## <a name="adaptive-cards-and-incoming-webhooks"></a>Cartões adaptáveis e WebHooks de entrada

> [!NOTE]
> Os cartões adaptáveis são suportados em WebHooks de entrada como parte do [programa Public Developer Preview](../resources/dev-preview/developer-preview-intro.md). As visualizações públicas estão disponíveis para acesso antecipado e comentários. Embora o lançamento seja estável e tenha passou por testes extensivos, ele não se destina ao uso em produção.
>
> ✔ Dentro da visualização do desenvolvedor, todos os elementos nativos do esquema de cartão adaptável, exceto `Action.Submit` , são totalmente suportados.
>
> ✔ As ações com suporte são [**Action. OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action. iscard**](https://adaptivecards.io/explorer/Action.ShowCard.html)e [**Action. ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

## <a name="cards-in-connectors"></a>Cartões em conectores

Os cartões foram definidos pela primeira vez como parte do Outlook e do Office 365 e são usados como parte dos conectores do Office 365. Como muitos aplicativos do Office 365, o Teams suporta conectores. Você pode saber mais sobre conectores nos [conectores do Office 365 para o Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)e encontrar a especificação de cartões em conectores na [referência do cartão de mensagens acionáveis](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Cartões em bots

A estrutura do Microsoft bot ampliou a especificação de cartões adicionando um conjunto de cartões predefinidos que os bots podiam usar como parte das mensagens de bot. O Microsoft Teams suporta bots usando a estrutura de bot, mas dá suporte a um conjunto de cartões levemente diferente. As informações gerais sobre cartões na estrutura de bot podem ser encontradas em [Adicionar anexos de cartão avançado a mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards). Esses cartões são chamados de *cartões simples* no Microsoft Teams.

Os bots no Teams podem usar qualquer tipo de cartão: simples, conector ou adaptável. Os cartões suportados por bots no Teams são detalhados na [referência de cartões de equipes](~/task-modules-and-cards/cards/cards-reference.md).  

## <a name="cards-in-messaging-extensions"></a>Cartões em extensões de mensagens

[As extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) também podem retornar um cartão. As extensões de mensagens podem usar qualquer tipo de cartão: simples, conector ou adaptável. Esses cartões são encontrados na [referência do cartão do teams](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="card-reference"></a>Referência de cartão

Todos os cartões usados pelo Teams estão listados na [referência do cartão de equipe](~/task-modules-and-cards/cards/cards-reference.md). Esta referência também descreve as diferenças entre placas e cartões da estrutura de bot no Microsoft Teams.
