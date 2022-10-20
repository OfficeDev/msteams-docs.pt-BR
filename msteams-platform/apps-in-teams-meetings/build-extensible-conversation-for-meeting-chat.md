---
title: Criar conversa extensível para chat de reunião
author: v-sdhakshina
description: Neste artigo, saiba como criar conversas extensíveis para o chat de reunião do Microsoft Teams com bots, cartões e extensões de mensagem.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: 65fc91d51cd4c740f28d5f33a2ad578f214c20a8
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615370"
---
# <a name="build-extensible-conversation-for-meeting-chat"></a>Criar conversa extensível para chat de reunião

Você pode tornar as conversas extensíveis em reuniões do Microsoft Teams. Bots, extensões de mensagem, cartões e módulos de tarefa podem ser combinados para proporcionar uma experiência intuitiva.

## <a name="bots"></a>Bots

Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. O uso diário de bots inclui bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem. As interações com bots podem ser perguntas e respostas rápidas ou conversas complexas. Um bot precisa ser habilitado no escopo de `team` uma `groupchat` reunião de canal e no escopo de todos os outros tipos de reunião. Para implementar bots, comece com [Criar um bot](/microsoftteams/platform//sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode).

### <a name="bot-apis"></a>APIs de bot

O [Bot Framework](https://dev.botframework.com/) é um SDK avançado usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado no Bot Framework, poderá modificá-lo facilmente para funcionar no Teams. Use C# ou Node.js para aproveitar nossos [SDKs](/microsoftteams/platform/).

### <a name="code-samples---bots"></a>Exemplos de código – Bots

|Nome do exemplo | Descrição | .NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|
| Bot de conversas do Teams | Manipulação de eventos de mensagens e conversas | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |
|Exemplos de bot | Conjunto de exemplos de bot  | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python) |

## <a name="message-extensions"></a>Extensões de mensagens

As extensões de mensagem permitem que os usuários interajam com seu serviço Web por meio de botões e formulários no cliente do Teams. Os usuários podem pesquisar ou iniciar ações em um sistema externo na área de mensagem de composição, na caixa de comando ou diretamente de uma mensagem. Você pode enviar de volta os resultados dessa interação para o cliente do Teams na forma de um cartão bem formatado. Implementar extensões de mensagem para chats de reunião não é diferente de chats regulares. Para implementar a extensão de mensagem, comece com [extensões de mensagem](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions?tabs=dotnet).

## <a name="cards-and-task-modules"></a>Cartões e módulos de tarefa

Os cartões fornecem aos usuários várias mensagens visuais, de áudio e selecionáveis e ajudam no fluxo da conversa. Com os módulos de tarefa, você pode criar experiências pop-up modais no Teams. Eles são úteis para iniciar e concluir as tarefas ou exibir informações avançadas, como vídeos ou painéis do Power Business Intelligence (BI). Para obter mais informações, consulte [cartões de construção e módulos de tarefa](/microsoftteams/platform/task-modules-and-cards/cards-and-task-modules).

## <a name="feature-compatibility-by-user-types"></a>Compatibilidade de recursos por tipos de usuário

A tabela a seguir fornece os tipos de usuário e lista os recursos que cada usuário pode acessar em reuniões:

| Tipo de usuário | Bots | Extensões de mensagens | Cartões Adaptáveis | Módulos de tarefas |
| :-- | :-- | :-- | :-- | :-- |
| Usuário no locatário | Disponível | Disponível | Disponível | Disponível |
| Convidado, parte do locatário Azure AD | Não disponível | Não disponível | Interações no chat da reunião são permitidas. | Interações no chat de reunião do Cartão Adaptável são permitidas. |
| Usuários federados, para obter mais informações, consulte [usuários não padrão](/microsoftteams/non-standard-users). | A interação é permitida. A aquisição, a atualização e a exclusão não são permitidas. | Não disponível | Interações no chat da reunião são permitidas. | Interações no chat de reunião do Cartão Adaptável são permitidas. |
| Usuário anônimo | Não disponível | Não disponível | Interações no chat da reunião são permitidas. | Não disponível |

## <a name="see-also"></a>Confira também

* [Como criar sua extensão de mensagens do Microsoft Teams](../messaging-extensions/design/messaging-extension-design.md)
* [Criando módulos de tarefa para o seu aplicativo do Microsoft Teams](../task-modules-and-cards/task-modules/design-teams-task-modules.md)
