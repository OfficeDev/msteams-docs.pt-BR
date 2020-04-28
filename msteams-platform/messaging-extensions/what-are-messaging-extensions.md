---
title: O que são extensões de mensagens?
author: clearab
description: Uma visão geral das extensões de mensagens na plataforma do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2a9fcdbcdda6bb85b6f5edc21253d05327ca5157
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "43914599"
---
# <a name="what-are-messaging-extensions"></a>O que são extensões de mensagens?

As extensões de mensagens permitem que os usuários interajam com o serviço Web por meio de botões e formulários no cliente do Microsoft Teams. Eles podem pesquisar ou iniciar ações em um sistema externo a partir da área de mensagem de redação, da caixa de comando ou diretamente de uma mensagem. Em seguida, você pode enviar os resultados dessa interação de volta para o cliente do Microsoft Teams, geralmente na forma de um cartão com formato avançado.

A captura de tela a seguir mostra os locais onde as extensões de mensagens podem ser chamadas.

![locais de chamadas de extensões de mensagens](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="what-kinds-of-tasks-are-they-good-for"></a>De que tipos de tarefas eles são bons?

**Cenário:** Preciso de algum sistema externo para fazer algo e desejo que o resultado da ação seja enviado de volta para minha conversa. \
**Exemplo:** Reservar um recurso e permitir que o canal saiba que dia/hora você o reservou.

**Cenário:** Preciso localizar algo em um sistema externo e quero compartilhar os resultados com minha conversa. \
**Exemplo:**  Procure um item de trabalho no DevOps do Azure e compartilhe-o com o grupo como um cartão adaptável.

**Cenário:** Preciso concluir uma tarefa complexa que envolve várias etapas (ou muitas informações) em um sistema externo, e os resultados devem ser compartilhados com uma conversa. \
**Exemplo:** Crie um bug no sistema de controle com base em uma mensagem do Teams, atribua esse bug a Bob e, em seguida, envie um cartão para o thread de conversa com os detalhes do bug.

## <a name="how-do-messaging-extensions-work"></a>Como funcionam as extensões de mensagens?

Uma extensão de mensagens consiste em um serviço Web que você hospeda e seu manifesto de aplicativo, que define onde seu serviço Web pode ser chamado no cliente Microsoft Teams. Eles aproveitam o esquema de mensagens e o protocolo de comunicação segura da estrutura de bot, portanto, você também precisará registrar seu serviço Web como um bot na estrutura do bot. Embora você possa criar seu serviço Web completamente à mão, recomendamos que você aproveite o [SDK da estrutura de bot](https://github.com/microsoft/botframework) para tornar o trabalho com o protocolo mais simples.

No manifesto do aplicativo para seu aplicativo do Microsoft Teams, você definirá uma única extensão de mensagens com até dez comandos diferentes. Cada comando define um tipo (ação ou pesquisa), e os locais no cliente podem ser invocados de (área de mensagem de composição, barra de comandos e/ou mensagem). Depois de invocado, seu serviço Web receberá uma mensagem HTTPS com uma carga JSON, incluindo todas as informações relevantes. Você responderá com uma carga JSON, permitindo que o cliente do teams saiba qual interação habilitará a seguir.

## <a name="types-of-messaging-extension-commands"></a>Tipos de comandos de extensão de mensagens

O tipo de comando de extensão de mensagens define os elementos da interface do usuário e os fluxos de interação disponíveis para o serviço Web. Algumas interações, como autenticação e configuração, estão disponíveis para ambos os tipos de comandos.

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação permitem que você apresente aos usuários um pop-up modal para coletar ou exibir informações. Ao enviar o formulário, seu serviço Web pode responder inserindo uma mensagem na conversa diretamente ou inserindo uma mensagem na área de mensagem de redação e permitindo que o usuário envie a mensagem. Você pode até encadear vários formulários juntos para fluxos de trabalho mais complexos.

Eles podem ser disparados da área de mensagem de redação, da caixa de comando ou de uma mensagem. Quando invocado de uma mensagem, a carga JSON inicial enviada ao bot inclui a mensagem inteira de onde foi invocado.

![módulo de tarefa de comando de ação de extensão de mensagens](~/assets/images/task-module.png)

### <a name="search-commands"></a>Comandos de pesquisa

Os comandos de pesquisa permitem que os usuários pesquisem em um sistema externo informações (manualmente por meio de uma caixa de pesquisa ou colando um link para um domínio monitorado na área de mensagem de composição) e, em seguida, insiram os resultados da pesquisa em uma mensagem. No fluxo de comando de pesquisa mais básico, a mensagem de chamada inicial incluirá a cadeia de caracteres de pesquisa que o usuário enviou. Você responderá com uma lista de cartões e visualizações de cartões. O cliente Teams processará as visualizações de cartões em uma lista para que o usuário final selecione. Quando o usuário seleciona um cartão, o cartão de tamanho completo será inserido na área de mensagem de composição.

Eles podem ser disparados da área de mensagem de redação ou da caixa de comando. Diferentemente dos comandos de ação, eles não podem ser disparados a partir de uma mensagem.

![comando de pesquisa de extensão de mensagens](~/assets/images/search-extension.png)

### <a name="link-unfurling"></a>Desenrolamento de link

Você também tem a opção de chamar o serviço quando uma URL é colada na área de mensagem de composição. Essa funcionalidade, conhecida como **link Unfurling**, permite inscrever-se para receber uma chamada quando as URLs que contêm um determinado domínio são coladas na área de mensagem de composição. O serviço Web pode "unfurl" a URL em um cartão detalhado, fornecendo mais informações do que o cartão de visualização de site padrão. Você pode até mesmo adicionar botões para permitir que os usuários executem ações imediatamente sem sair do cliente do Microsoft Teams.

## <a name="get-started"></a>Introdução

Pronto para começar a criar? Experimente um dos nossos QuickStartES:

* **C#**
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* **JavaScript**
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

## <a name="learn-more"></a>Saiba mais

Criar uma extensão de mensagens:

* [Criar uma extensão de mensagens](~/messaging-extensions/how-to/create-messaging-extension.md)
* [Comando definir extensão de mensagens de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Comando definir extensão de mensagens de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
