---
title: O que são bots?
author: clearab
description: Uma visão geral dos bots no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 1e07d56769cbb303f9af98f84c8ae6064325c1a7
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651819"
---
# <a name="what-are-bots"></a>O que são bots?

Os bots permitem que os usuários interajam com o serviço Web por meio de texto, cartões interativos e módulos de tarefa. Eles são incrivelmente flexíveis, você pode fazer o escopo dos bots para lidar com alguns comandos simples ou assistentes virtuais alimentados por inteligência artificial e processamento de linguagem natural. Eles podem ser um aspecto de um aplicativo maior ou completamente autônomo.

Encontrar a combinação certa de cartões, texto e módulos de tarefas é fundamental para criar um bot útil. Não se esqueça, os bots são muito mais do que apenas texto!

![Perguntas frequentes mais sobre gif](~/assets/images/FAQPlusEndUser.gif)

## <a name="user-scenarios"></a>Cenários de usuário

Os bots no Microsoft Teams podem fazer parte de um canal, chat de grupo ou chat um-em-um. Cada escopo fornecerá oportunidades e desafios exclusivos para o bot da conversa.

### <a name="in-a-channel"></a>Em um canal

Os canais contêm conversas encadeadas entre várias pessoas, potencialmente muitas pessoas (atualmente, até 2000). Isso pode causar o alcance maciço de bot, mas as interações individuais precisam ser concisas. Interações de múltipla volta tradicional provavelmente não funcionarão bem. Em vez disso, procure usar cartões interativos ou módulos de tarefas ou mova a conversa para uma conversa de um para um se precisar coletar muitas informações. O bot também terá acesso apenas às mensagens em que for `@mentioned` diretamente, embora você possa recuperar mensagens adicionais da conversa usando o Microsoft Graph e permissões elevadas de nível de organização.

Alguns cenários em que os bots Excel em um canal incluem:

* **Notificações**, especialmente se você fornecer um cartão interativo para que os usuários tenham mais informações.
* **Cenários de comentários** como pesquisas e pesquisas.
* Interações que podem ser resolvidas em um **único ciclo de solicitação/resposta**, onde os resultados são úteis para vários membros da conversa.
* **Bots sociais/divertidos** — obtenha uma imagem de gato incrível, escolha aleatoriamente um vencedor, etc.

### <a name="in-a-group-chat"></a>Em um chat de grupo

Os chats de grupo são conversas não encadeadas entre três ou mais pessoas. Eles tendem a ter menos membros do que um canal e são mais transitórios. Semelhante a um canal, seu bot só terá acesso a mensagens em que for `@mentioned` diretamente.

Cenários que funcionam bem em um canal normalmente funcionarão tão bem em um chat de grupo.

### <a name="in-a-one-on-one-chat"></a>Em um chat de um em um

Essa é a maneira tradicional de um bot de conversação interagir com um usuário. Eles podem habilitar cargas de trabalho incrivelmente diversificadas. P&um bots, bots que iniciam fluxos de trabalho em outros sistemas, bots que dizem piadas e bots que fazem anotações são apenas alguns exemplos. Lembre-se apenas de considerar se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="building-a-teams-bot-with-the-microsoft-bot-framework"></a>Criando um bot do teams com o Microsoft bot Framework

O [Microsoft bot Framework](https://dev.botframework.com/) é um SDK avançado para a criação de bots usando C#, Java, Python ou JavaScript. Se você já tiver um bot baseado na estrutura de bot, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams. Recomendamos que você use C# ou Node.js para aproveitar os benefícios de nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e os métodos do SDK do gerador de bot básico da seguinte maneira:

* Use tipos de cartões especializados como o cartão de conexão do Office 365.
* Consumir e definir dados de canal específicos de equipes em atividades.
* Processar solicitações de extensão de mensagens.

> [!IMPORTANT]
> Você pode desenvolver aplicativos do teams em qualquer tecnologia de programação Web e chamar as [APIs REST da estrutura de bot](/bot-framework/rest-api/bot-framework-rest-overview) diretamente, mas você deve executar todo o tratamento de tokens por conta própria.

O bot da equipe consiste em três elementos:

* Um serviço Web publicamente acessível que você hospeda.
* O registro do bot com a estrutura do bot.
* Seu pacote de aplicativos do Microsoft Teams com o manifesto do aplicativo. Isso é o que os usuários instalarão e conectarão o cliente do teams ao seu serviço Web, roteado através do serviço bot.

> [!TIP]
> O Teams app Studio * ajuda você a criar e configurar seu manifesto de aplicativo e pode registrar seu serviço Web como um bot na estrutura de bot. Ele também contém uma biblioteca de controle de reagir e um construtor de cartões interativos. *Confira* [introdução ao Teams app Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="building-a-teams-bot-with-microsoft-power-virtual-agents"></a>Criando um bot do Microsoft Teams com agentes virtuais de alimentação da Microsoft

[Os agentes virtuais de alimentação](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) são um serviço baseado na Microsoft Power Platform e bot Framework. O processo de desenvolvimento do agente virtual de energia usa uma abordagem de interface gráfica orientada e sem código para permitir que todos os membros da sua equipe criem e mantenham facilmente um agente virtual inteligente. Após concluir a criação do seu chatbot no [portal de agentes virtuais de energia](https://powervirtualagents.microsoft.com), você poderá [integrar facilmente seus agentes virtuais de alimentação chatbot com o Teams](../../bots/how-to/add-power-virtual-agents-bot-to-teams.md). Para começar a criar seus agentes virtuais de chatbot, *consulte* a [documentação de agentes virtuais de energia](https://docs.microsoft.com/power-virtual-agents/).

## <a name="connectors-and-bots"></a>Conectores e bots

Os conectores permitem que você crie um bot simples para interação básica, como o Iniciando de um fluxo de trabalho ou outros comandos simples. Eles residem apenas na equipe em que você os cria e se destinam a processos simples específicos do fluxo de trabalho de sua empresa. *Confira* [o que são WebHooks e conectores?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) para obter mais informações.

## <a name="bot-fails"></a>Falha no bot

### <a name="having-multi-turn-experiences-in-chat"></a>Ter experiências de vários voltagens no chat

Uma caixa de diálogo abrangente entre o bot e o usuário é uma maneira lenta e muito complexa de obter uma tarefa concluída e também exige que o desenvolvedor Mantenha o estado. Para sair desse Estado, um usuário deve se esgotar ou digitar "*Cancelar*". Acima de tudo, o processo é desnecessariamente entediante:

USUÁRIO: agendar uma reunião com o Megan.

BOT: Eu encontrei 200 resultados, inclua um nome e sobrenome.

USUÁRIO: agendar uma reunião com o Megan Bowen.

BOT: OK, que horário você gostaria de reunir com o Megan Bowen?

USUÁRIO: 1:00 PM.

BOT: em que dia?

### <a name="supporting-too-many-commands"></a>Suporte a muitos comandos

Um bot que dá suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não será bem-sucedido ou exibido positivamente pelos usuários. Como há apenas 6 comandos visíveis no menu do bot atual, qualquer outra coisa provavelmente será usada com qualquer frequência. Os bots que se aprofundam em uma área específica em vez de tentar ser um assistente amplo funcionará e se comportarão melhor.

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a>Mantendo uma grande base de conhecimento de recuperação com respostas não classificadas

Os bots são mais adequados para interações curtas e rápidas, não pesquisando listas longas procurando por uma resposta.

## <a name="get-started"></a>Introdução

* [Bot de conversa do teams em C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Bot de conversa do Teams em JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Saiba mais

* [Noções básicas de bots no Teams](~/bots/bot-basics.md)
* [Criar um bot para o Teams](~/bots/how-to/create-a-bot-for-teams.md)
* [Planejar seu aplicativo](../../concepts/extensibility-points.md)
* [Criando seu aplicativo].. /(.. /designing-your-app/designing-overview.md)
* [Criar seu aplicativo](../../concepts/building-an-app.md)
* [Publicar seu aplicativo](../../concepts/deploy-and-publish/overview.md)
