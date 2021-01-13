---
title: O que são bots de conversa?
author: clearab
description: Uma visão geral dos bots de conversa no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 0304ae436b54db0d111eaed507beb350f1ca4632
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797866"
---
# <a name="what-are-conversational-bots-in-microsoft-teams"></a>O que são bots de conversa no Microsoft Teams?

Os bots de conversa permitem que os usuários interajam com seu serviço Web por meio de texto, cartões interativos e módulos de tarefas. Eles são incrivelmente flexíveis — os bots de conversa podem ter como escopo lidar com alguns comandos simples ou assistentes virtuais complexos, alimentados por inteligência artificial e processamento de linguagem natural. Eles podem ser um aspecto de um aplicativo maior ou completamente autônomo.

O GIF abaixo mostra um usuário conversão com um bot em um chat um-para-um usando cartões de texto e interativos. Encontrar a combinação correta de cartões, texto e módulos de tarefas é fundamental para criar um bot útil. Não se esqueça de que os bots são muito mais do que apenas texto!

![Gif de Perguntas Frequentes Plus](~/assets/images/FAQPlusEndUser.gif)

## <a name="build--a-bot-for-teams-with-the-microsoft-bot-framework"></a>Criar um bot para o Teams com o Microsoft Bot Framework

O [Microsoft Bot Framework é](https://dev.botframework.com/) um SDK rico para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado na Estrutura de Bot, poderá adaptá-lo facilmente ao trabalho no Microsoft Teams. Recomendamos que você use C# ou Node.js para tirar proveito de [nossos SDKs.](/microsoftteams/platform/#pivot=sdk-tools) Esses pacotes estendem as classes e métodos básicos do SDK do Bot Builder da seguinte forma:

* Use tipos de cartão especializados, como o cartão do Conector do Office 365.
* Consumir e definir dados de canal específicos do Teams em atividades.
* Processar solicitações de extensão de mensagens.

O bot do Teams consiste em três elementos:

* Um serviço Web publicamente acessível que você hospeda.
* Seu registro de bot com a Estrutura de Bot.
* Seu pacote de aplicativos do Teams com o manifesto do aplicativo. Isso é o que os usuários instalarão e conectarão o cliente teams ao seu serviço Web, roteado pelo Serviço de Bot.

> [!IMPORTANT]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação na Web e chamar as [APIs REST](/bot-framework/rest-api/bot-framework-rest-overview) do Bot Framework diretamente, mas deve executar todo o tratamento de token por conta própria.

> [!TIP]
> O Teams App Studio* ajuda você a criar e configurar o manifesto do aplicativo e pode registrar seu serviço Web como um bot no Bot Framework. Ele também contém uma biblioteca de controle react e um construtor de cartão interativo. *Confira* [Como começar a trabalhar com o Teams App Studio.](~/concepts/build-and-test/app-studio-overview.md)

## <a name="create-a-chatbot-for-teams-with-microsoft-power-virtual-agents"></a>Criar um chatbot para o Teams com o Microsoft Power Virtual Agents

[O Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é um serviço chatbot, criado na plataforma Microsoft Power e na Estrutura de Bot.  O processo de desenvolvimento do Power Virtual Agent usa uma abordagem interativa de interface gráfica sem código para capacitar todos os membros da sua equipe a criar e manter facilmente um agente virtual inteligente.  Depois de concluir a criação de seu chatbot no portal do [Power Virtual Agents,](https://powervirtualagents.microsoft.com)você poderá integrar facilmente seu chatbot de Agentes Virtuais Do Power com [o Teams.](how-to/add-power-virtual-agents-bot-to-teams.md) Para começar a criar seu chatbot do Power Virtual Agents, *consulte a* documentação do [Power Virtual Agents.](https://docs.microsoft.com/power-virtual-agents/)

## <a name="webhooks-and-connectors"></a>Webhooks e conectores

Webhooks e conectores permitem que você crie um bot simples para interação básica, como sair de um fluxo de trabalho ou outros comandos simples. Eles só estão na equipe na qual você os cria e são destinados a processos simples específicos do fluxo de trabalho da sua empresa. *Veja* [o que são webhooks e conectores?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) para obter mais informações.

## <a name="where-bots-work-best"></a>Onde os bots funcionam melhor

Os bots no Microsoft Teams podem fazer parte de uma conversa um-para-um, um chat em grupo ou um canal em uma equipe. Cada escopo fornecerá oportunidades exclusivas e desafios para seu bot de conversa.

### <a name="in-a-channel"></a>Em um canal

Os canais contêm conversas encadeadas entre várias pessoas — potencialmente muitas pessoas (atualmente, até duas mil). Isso potencialmente dá ao seu bot grande alcance, mas as interações individuais precisam ser concisas. Interações multi-turn tradicionais provavelmente não funcionarão bem. Em vez disso, procure usar cartões interativos ou módulos de tarefas, ou potencialmente mova a conversa para uma conversa um-para-um se você precisar coletar muitas informações. Seu bot também só terá acesso às mensagens em que ele está diretamente, embora você possa recuperar mensagens adicionais da conversa usando o Microsoft Graph e permissões elevadas no `@mentioned` nível da organização.

Alguns cenários em que os bots se destacam em um canal incluem:

* **Notificações,** particularmente se você fornecer um cartão interativo para que os usuários forneçam informações adicionais.
* **Cenários de comentários** como pesquisas e pesquisas.
* Interações que podem ser resolvidas em um único ciclo **de solicitação/resposta,** onde os resultados são úteis para vários membros da conversa.
* **Bots sociais/divertidos** — obter uma imagem de gato incrível, escolher aleatoriamente um prêmio, etc.

### <a name="in-a-group-chat"></a>Em um chat de grupo

Chats em grupo são conversas não encadeadas entre três ou mais pessoas. Eles tendem a ter menos membros do que um canal e são mais transitórios. Semelhante a um canal, seu bot só terá acesso às mensagens em que ele está `@mentioned` diretamente.

Cenários que funcionam bem em um canal normalmente funcionarão da mesma forma em um chat em grupo.

### <a name="in-a-one-to-one-chat"></a>Em um chat um-para-um

Essa é a maneira tradicional para um bot de conversa interagir com um usuário. Eles podem habilitar cargas de trabalho incrivelmente diversas. P&Um bots, bots que iniciam fluxos de trabalho em outros sistemas, bots que informam coisas e bots que fazem anotações são apenas alguns exemplos. Lembre-se apenas de considerar se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="bot-fails"></a>O bot falha

### <a name="having-multi-turn-experiences-in-chat"></a>Ter experiências multi-turn no chat

Uma caixa de diálogo extensa entre seu bot e o usuário é uma maneira lenta e muito complexa de concluir uma tarefa e também exige que o desenvolvedor mantenha o estado. Para sair desse estado, um usuário deve ter tempo de vida ou digitar "*Cancelar".* Acima de tudo, o processo é desnecessariamente tedioso:

USUÁRIO: Agende uma reunião com Megan.

BOT: i've found 200 results, please include a first and last name.

USER: Agendar uma reunião com Megan Bowen.

BOT: OK, que horas você gostaria de se encontrar com Megan Bowen?

USUÁRIO: 13:00.

BOT: Em qual dia?

### <a name="supporting-too-many-commands"></a>Suporte a muitos comandos

Um bot que oferece suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não será bem-sucedido ou visualizado positivamente pelos usuários. Como há apenas seis comandos visíveis no menu de bot atual, nada mais é improvável de ser usado com qualquer frequência. Os bots que se profundidade em uma área específica em vez de tentar ser um assistente amplo funcionarão e funcionarão melhor.

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a>Mantendo uma grande base de conhecimento de recuperação com respostas não ranked

Os bots são mais adequados para interações curtas e rápidas, não para fazer a interseção em listas longas em busca de uma resposta.

## <a name="get-started"></a>Introdução

* [Bot de conversa do Teams em C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Bot de conversa do Teams em JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Saiba mais

> [!div class="nextstepaction"]
> [Noções básicas de bots no Teams](~/bots/bot-basics.md)

> [!div class="nextstepaction"]
> [Criar um bot para o Teams](~/bots/how-to/create-a-bot-for-teams.md)
