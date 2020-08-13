---
title: Determinando os contextos de aplicativos do Microsoft Teams
author: heath-hamilton
description: Ao planejar seu aplicativo do Microsoft Teams, você deve decidir se o aplicativo será usado em espaços colaborativos, espaços pessoais ou ambos.
ms.openlocfilehash: 05c92aa8b199cbdb58e477fb4a64467c150edbfd
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651831"
---
# <a name="getting-to-know-teams-ui-conventions"></a>Conhecendo as convenções de interface do usuário do Microsoft Teams

Os aplicativos normalmente exibem uma ou mais convenções de interface do usuário de equipes padrão. A criação de recursos do seu aplicativo usando essas convenções leva a experiências ricas que se sentem nativas para os usuários do Microsoft Teams.

## <a name="cards"></a>Cartões

Os [cartões](~/task-modules-and-cards/what-are-cards.md) são contêineres de interface do usuário definidos por esquematizado JSON que podem conter várias propriedades e anexos. Eles podem conter texto formatado, mídia, controles (como caixas suspensas e botões de opção) e botões que disparam ações de cartão.

As ações do cartão podem enviar cargas para a API do seu aplicativo, abrir um link, iniciar fluxos de autenticação ou enviar mensagens para conversas. A plataforma do Microsoft Teams suporta vários tipos de cartões, incluindo cartões adaptáveis, cartões herói, cartões de miniaturas e muito mais. Você pode combinar conjuntos de cartões e exibi-los em uma lista ou carrossel.

## <a name="task-modules"></a>Módulos de tarefas

Os [módulos de tarefas](~/task-modules-and-cards/what-are-task-modules.md) oferecem experiências pop-up restritas no Microsoft Teams. Eles são especialmente úteis para iniciar fluxos de trabalho, coletar entradas do usuário ou exibir informações ricas, como vídeos ou painéis do Power BI. Em módulos de tarefa, você pode executar código de front-end personalizado, exibir um `<iframe>` widget ou mostrar um cartão adaptável.

Ao considerar como você deseja criar seu aplicativo, lembre-se de que as modalidades são naturais para que os usuários insiram informações ou concluam tarefas comparadas a uma guia ou uma experiência de bot baseada em conversas.

## <a name="deep-links"></a>Deep links

Seu aplicativo pode criar [links de URL profundas](~/concepts/build-and-test/deep-links.md) para ajudar a navegar pelo seu usuário por meio do seu aplicativo e do cliente do teams. Você pode criar um deeplink para a maioria das entidades no Teams e alguns (como uma nova solicitação de reunião) permitem preencher previamente as informações usando cadeias de caracteres de consulta na URL. 

Por exemplo, seu bot de conversa pode enviar uma mensagem para um canal com um deeplink para um módulo de tarefa que resulte em um cartão ser enviado como uma mensagem de um para um usuário, que por sua vez contém um deeplink para criar uma nova reunião com um usuário específico em uma determinada data/hora. Use links de profunda para se conectar aos vários pontos de extensão disponíveis para seu aplicativo, mantendo sempre o usuário no contexto correto.

## <a name="web-based-content"></a>Conteúdo baseado na Web

[Conteúdo baseado na Web](~/tabs/how-to/create-tab-pages/content-page.md) é uma página da Web que você hospeda, que pode ser incorporada em um módulo de tarefa ou guia. Para inserir sua página da Web no cliente do Teams, ela deve:

* Incluir `HTTPS` na URL.
* Ser incorporado em um `<iframe>` .
* Incluir o SDK do cliente JavaScript do Microsoft Teams e chamar o método do SDK `initialize()` na carga da página.

## <a name="next-steps"></a>Próximas etapas

* [Criar seu aplicativo](../../tabs/design/tabs.md)
