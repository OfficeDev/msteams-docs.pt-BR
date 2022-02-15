---
title: Cartões
description: Descreve cartões e como eles são usados em bots, conectores e extensões de mensagens
ms.localizationpriority: high
keywords: conectores de mensagens de cartões de bots
ms.topic: overview
ms.openlocfilehash: 7ab05607e7c5abf897c790bb777e5c697edc9e08
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821581"
---
# <a name="cards"></a>Cartões

Um cartão é um contêiner de interface do usuário (UI) para obter informações curtas ou relacionadas. Os cartões podem ter várias propriedades e anexos e podem incluir botões que disparam [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md). Ao usar os cartões, você pode organizar informações em grupos e dar aos usuários a oportunidade de interagirem com partes específicas das informações.

Os bots do Teams suportam os seguintes tipos de cartões:
 
- Cartão Adaptável
- Cartão Hero
- Cartão de listagem
- Cartão do Conector do Office 365
- Cartão de recebimento
- Cartão de entrada
- Cartão de miniatura
- Coleções de cartões

Você pode adicionar a formatação Rich Text aos cartões usando Markdown ou HTML, dependendo do tipo de cartão. Cartões usados por bots e extensões de mensagens no Microsoft Teams, adicione e responda a essas ações de cartão, `openUrl`, `messageBack`, `imBack`, `invoke` e `signin`.

O Teams usa cartões em três locais diferentes:

* Conectores
* Bots
* Extensões de mensagens

## <a name="cards-in-connectors"></a>Cartões em conectores

Os cartões foram definidos pela primeira vez como parte do Outlook e Office 365 e já são usados como parte dos Conectores do Office 365. Como muitos aplicativos do Office 365, o Teams dá suporte aos conectores. Para obter mais informações, consulte [Conectores do Office 365 do Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md). Você pode encontrar a especificação para cartões nos conectores em [referência de cartão de mensagens acionáveis](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Cartões em bots

O Microsoft Bot Framework estende a especificação de cartões adicionando um conjunto de cartões predefinidos que os bots podem usar como parte das mensagens do bot. O Teams oferece suporte aos bots usando o Bot Framework, mas oferece suporte a um conjunto diferente dessas cartas. Informações gerais sobre cartões no Bot Framework podem ser encontradas em [adicionar anexos de cartões avançados para mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards). Esses cartões são chamados de cartões simples no Teams.

Os bots no Teams podem usar cartões simples, cartões de conector ou Cartões Adaptáveis. Os [Tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md) fornecem informações sobre cartões, com suporte dos bots no Teams.

## <a name="cards-in-messaging-extensions"></a>Cartões nas extensões de mensagens

As [Extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) também podem retornar um cartão. As extensões de mensagens podem usar cartões simples, cartões de conector ou Cartões Adaptáveis. Esses cartões são encontrados em [tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="types-of-cards"></a>Tipos de cartões

Todos os cartões usados pelo Teams estão listados em [tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md). Essa referência também descreve as diferenças entre cartões do Bot Framework e cartões no Teams.

## <a name="adaptive-cards"></a>Cartões Adaptáveis

Os [Cartões Adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) são uma nova especificação de produto cruzado de cartões nos produtos da Microsoft, incluindo bots, Cortana, Outlook e Windows. Eles são o tipo de cartão recomendado do novo desenvolvimento do Teams. Para obter informações gerais da equipe dos Cartões Adaptáveis, consulte [Visão geral dos Cartões Adaptáveis](/adaptive-cards). Você pode usar os Cartões Adaptáveis em qualquer lugar que você usar os cartões hero, cartões do Office 365 e cartões em miniatura existentes.

Além dos Cartões Adaptáveis, o Teams oferece suporte a dois outros tipos de cartões:

* Cartões conectores: usados como parte dos conectores do Office 365.
* Cartões simples: usados do Bot Framework, como os carões em miniatura e os cartões hero.

### <a name="people-picker-in-adaptive-cards"></a>Seletor de Pessoas nos Cartões Adaptáveis

O [Seletor de Pessoas](cards/people-picker.md#people-picker-in-adaptive-cards) adicionado como um controle de entrada nos Cartões Adaptáveis permite a pesquisa e seleção de pessoas. Você pode usá-lo em chats, canais, módulos de tarefas e guias. Os clientes móveis e de área de trabalho suportam o Seletor de Pessoas que fornece uma experiência de digitação em linha. 

### <a name="type-ahead-search-in-adaptive-cards"></a>Pesquisa de preenchimento automático nos Cartões Adaptáveis  

Pesquisa de preenchimento automático adicionado como um controle de entrada nos Cartões Adaptáveis habilitam a experiência de [pesquisa dinâmica](~/task-modules-and-cards/cards/dynamic-search.md) de um conjunto de dados carregado dinamicamente. Ele também permite que os usuários façam uma pesquisa de preenchimento automático em uma lista com limite de opções. Os clientes móveis e de área de trabalho suportam a experiência de pesquisa de preenchimento automático. 

### <a name="adaptive-cards-and-incoming-webhooks"></a>Cartões adaptáveis e Webhooks de entrada

> [!NOTE]
> * Todos os elementos de esquema dos Cartões Adaptáveis nativos, exceto `Action.Submit`, são totalmente suportados.
> * As ações com suporte são [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)e [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Os Cartões Adaptáveis com Webhooks de entrada permitem que você use os recursos avançados e flexíveis dos Cartões Adaptáveis. Ele envia dados usando os Webhooks de entrada no Teams do seu serviço Web.

## <a name="support-for-azure-ad-object-id-and-upn-in-user-mention"></a>Suporte para ID de Objeto do Azure Active Directory e UPN na menção do usuário 

Bots com Cartões Adaptáveis dão suporte a IDs de menção de usuário, como ID de objeto do Microsoft Azure Active Directory (Azure AD) e Nome de Princípio do Usuário (UPN), além das IDs existentes. Os webhooks de entrada começam a dar suporte à menção do usuário no Cartão Adaptável com a ID de Objeto do Azure Active Directory e o UPN.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tipos de cartões](~/task-modules-and-cards/cards/cards-reference.md)

## <a name="see-also"></a>Confira também

* [Formatar cartões no Teams](~/task-modules-and-cards/cards/cards-format.md)
* [Projetar os Cartões Adaptáveis](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Cartões adaptáveis nos bots](../bots/how-to/conversations/conversation-messages.md#adaptive-cards)