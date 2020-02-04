---
title: Pontos extensíveis no cliente do teams
author: clearab
description: Compreenda os pontos de extensibilidade disponíveis para seu aplicativo no cliente do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f65a5111bf59b08347291caa15c557dc0a48e886
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672522"
---
# <a name="extensible-points-in-the-teams-client"></a>Pontos extensíveis no cliente do teams

Um aplicativo criado na plataforma do Microsoft Teams estende o cliente do Microsoft Teams (Web, Mobile e desktop) com os serviços Web que você hospeda. A plataforma do Microsoft Teams fornece um conjunto avançado e flexível de pontos de extensibilidade, construções de interface do usuário e APIs para que você tire proveito da criação do aplicativo. Seu aplicativo pode ser tão simples quanto a incorporação de seu site existente dentro de uma guia para sua equipe ou um aplicativo multifacetado totalmente repleto que envolve seus usuários em toda a abrangência do cliente Teams. Você pode optar por integrar um aplicativo existente ou criar uma nova experiência criada inteiramente para o Microsoft Teams.

Há vários lugares em que o cliente do Microsoft Teams pode ser estendido para permitir que os usuários interajam com seu aplicativo. Dependendo do seu cenário, você pode optar por se concentrar em um único ponto de extensão (como um bot de conversa pessoal) ou combinar vários pontos de extensão.

## <a name="teams-channels-and-group-chats"></a>Equipes, canais e bate-papos de grupo

Equipes, canais e bate-papos de grupo permitem que várias pessoas colaborem. Os aplicativos desse contexto estão disponíveis para todos os membros do grupo ou da conversa, geralmente concentrando-se em Habilitar fluxos de trabalho colaborativos adicionais ou desbloquear novas interações sociais. Seu aplicativo terá acesso às APIs, permitindo que ele obtenha informações sobre os membros da conversa, os canais de uma equipe e metadados sobre a equipe ou conversa.

Eles podem ser estendidos com:

* **[Bots de conversa](~/bots/what-are-bots.md)** interagindo com membros da conversa através de chat e respondendo a eventos (como um novo membro que está sendo adicionado ou um canal que está sendo renomeado). Todas as conversas com um bot neste contexto são visíveis para todos os membros do canal ou grupo, portanto, você precisará garantir que a conversa seja relevante para todos.

* **[Guias configuráveis](~/tabs/what-are-tabs.md)** que fornecem uma experiência Web incorporada de tela inteira configurada para o canal ou o chat de grupo em que está instalada. Todos os membros irão interagir no mesmo aplicativo Web compartilhado, de forma que uma experiência de aplicativo de página única sem estado seja típica.

* **[WebHooks e conectores](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)** permitindo que os serviços externos publiquem mensagens na conversa e seus usuários enviem mensagens para o serviço. Você pode tirar proveito de cartões e ações de cartões para criar mensagens ricas e acionáveis.

### <a name="personal-apps"></a>Aplicativos pessoais

Os [aplicativos pessoais](~/concepts/design/personal-apps.md) são a parte do aplicativo do Microsoft Teams que se concentra em interações com um único usuário. A experiência é exclusiva para cada usuário individual. Esta parte do seu aplicativo pode ser fixada para o trilho de navegação à esquerda, habilitando o acesso de um clique para seus usuários.

Eles podem conter:

* **[Bots de conversas](~/bots/what-are-bots.md)** com uma conversa de um-para-um com o usuário. Como esta é uma conversa privada, se seu aplicativo precisa ter uma conversa de múltipla volta ou fornecer uma notificação relevante apenas para um único usuário, normalmente é melhor ter essa interação em um aplicativo pessoal.

* **[Guias pessoais](~/tabs/what-are-tabs.md)** que fornecem uma experiência da Web incorporada em tela inteira.

## <a name="messages"></a>Mensagens

As mensagens são o coração de colaboração no Microsoft Teams. Com um **[comando de ação de extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)**, seu aplicativo pode permitir que os usuários invoquem a API do aplicativo de uma mensagem, enviando o conteúdo da mensagem para o seu aplicativo para processamento ou ação. Seu aplicativo pode responder ao apresentar um formulário (um módulo de tarefa) ao usuário para coletar mais informações, enviar uma resposta para a mensagem original ou enviar uma mensagem diretamente ao usuário.

## <a name="writing-messages"></a>Gravando mensagens

Seu aplicativo pode ajudar os usuários a criar mensagens mais eficazes, permitindo que eles pesquisem ou executem ações em um sistema externo e insiram os resultados em um formato avançado e estruturado completo com botões acionáveis.

Há três maneiras em que o aplicativo pode ajudar os usuários a criar melhores mensagens:

* **[Messaging Extension-Search Commands](~/messaging-extensions/what-are-messaging-extensions.md)** permitindo a pesquisa rápida de um sistema externo, visualize os resultados dessa pesquisa e insira o resultado no bate-papo como um cartão rico.

* **[Messaging Extension-link Unfurling](~/messaging-extensions/what-are-messaging-extensions.md)** permite que seu aplicativo monitore domínios da Web nos quais você está interessado. Quando uma URL que contém esse domínio é colada na caixa de mensagem de redação, a API do aplicativo será invocada, permitindo que você adicione um cartão avançado à mensagem com informações adicionais sobre o item vinculado.

* **[Messaging Extension-os comandos de ação](~/messaging-extensions/what-are-messaging-extensions.md)** apresentam ao usuário um formulário de janela restrita (um módulo de tarefa), enviam os resultados do formulário para seu aplicativo e, em seguida, inserem uma mensagem na conversa diretamente ou criam parte de uma mensagem que o usuário pode editar antes de enviar à conversa.

## <a name="user-interface-ui-elements"></a>Elementos da interface do usuário (UI)

Além de pontos de extensibilidade, a plataforma Microsoft Teams fornece elementos de interface do usuário flexíveis para que os aplicativos aproveitem o. Esses elementos permitem que você crie experiências ricas que se sentem nativas ao cliente do teams.

### <a name="cards--card-actions"></a>Cartões & ações do cartão

Os [cartões](~/task-modules-and-cards/what-are-cards.md) são contêineres de interface do usuário definidos por esquematizado JSON, que podem conter várias propriedades e anexos. Eles podem conter texto formatado, mídia, controles (como caixas suspensas e botões de opção) e botões que disparam ações de cartão. As ações do cartão podem enviar cargas para a API do seu aplicativo, abrir um link, iniciar fluxos de autenticação ou enviar mensagens para conversas. A plataforma do Microsoft Teams dá suporte a vários tipos de cartões, incluindo cartões adaptáveis, cartões herói, cartões de miniaturas e muito mais. Eles podem ser combinados em coleções de cartões e exibidos em uma lista ou carrossel.

### <a name="task-modules"></a>Módulos de tarefa

Os [módulos de tarefas](~/task-modules-and-cards/what-are-task-modules.md) permitem que você crie experiências pop-up restritas em seu aplicativo do Microsoft Teams. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado `<iframe>` , mostrar um widget, como YouTube ou Microsoft Stream Video, ou exibir um cartão adaptável. Eles são especialmente úteis para iniciar e concluir tarefas ou exibir informações ricas, como vídeos ou painéis do Power BI. Uma experiência de pop-up geralmente é mais natural para usuários que iniciam e concluem tarefas comparadas a uma guia ou uma experiência de bot baseada em conversas.

### <a name="deep-links"></a>Deep links

Seu aplicativo pode criar [links de URL profundas](~/concepts/build-and-test/deep-links.md) para ajudar a navegar pelo seu usuário por meio do seu aplicativo e do cliente do teams. Você pode criar um deeplink para a maioria das entidades no Teams e alguns (como uma nova solicitação de reunião) permitem preencher previamente as informações usando cadeias de caracteres de consulta na URL. Por exemplo, seu bot de conversa pode enviar uma mensagem para um canal com um deeplink para um módulo de tarefa que resulte em um cartão ser enviado como uma mensagem de um para um usuário, que por sua vez contém um deeplink para criar uma nova reunião com um usuário específico em uma determinada data/hora. Use links de profunda para se conectar aos vários pontos de extensão disponíveis para seu aplicativo, mantendo sempre o usuário no contexto correto.

### <a name="web-content-pages"></a>Páginas de conteúdo da Web

Uma [página de conteúdo da Web](~/tabs/how-to/create-tab-pages/content-page.md) é uma página da Web que você hospeda, que pode ser incorporada em uma guia ou em um módulo de tarefa. Para permitir que sua página da Web seja incorporada a um cliente do Microsoft Teams, ela deve:

* Ser hospedado em um HTTPS.
* Ser capaz de ser incorporado a `<iframe>` pelo cliente Teams.
* Incluir o SDK do cliente JavaScript do Microsoft Teams e invocar `initialize()` o método do SDK na carga da página.
