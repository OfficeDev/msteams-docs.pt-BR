---
title: Bots e SDKs
author: clearab
description: Bots e SDKs no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: c76a3300229e038e0d6a93d2701b3b3c5a1286da
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697222"
---
# <a name="bots-and-sdks"></a>Bots e SDKs

Para criar um bot que funcione no Microsoft Teams, você pode usar um dos seguintes:
* Um bot existente criado no SDK da Estrutura do Microsoft Bot
* Serviço de chatbot do Power Virtual Agents
* Webhooks e conectores

## <a name="bots-and-the-microsoft-bot-framework"></a>Bots e a Estrutura do Microsoft Bot

O bot do Teams consiste nos três elementos a seguir:

* Um serviço web publicamente acessível hospedado por você.
* Seu registro de bot com a Estrutura de Bot.
* Seu pacote de aplicativos do Teams com o manifesto do aplicativo. Isso é o que os usuários instalam e conectam o cliente do Teams ao seu serviço Web, roteado por meio do serviço de bot.

A [Estrutura de Bot](https://dev.botframework.com/) é um SDK rico usado para criar bots usando C#, Java, Python e JavaScript. Se você já tiver um bot baseado na Estrutura de Bots, poderá facilmente modificá-lo para funcionar no Microsoft Teams. Use C# ou Node.js tirar proveito de nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e métodos básicos do SDK do Construtor de Bots da seguinte forma:

* Use tipos de cartão especializados, como o cartão conector do Office 365.
* Definir dados de canal específicos do Teams em atividades.
* Processar solicitações de extensão de mensagens.

> [!IMPORTANT]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar as [APIs REST da](/bot-framework/rest-api/bot-framework-rest-overview) Estrutura de Bot diretamente. Mas você deve executar o tratamento de token em todos os casos.

> [!TIP]
> O Teams App Studio ajuda você a criar e configurar seu manifesto do aplicativo e registrar seu serviço Web como um bot na Estrutura de Bots. Ele também contém uma biblioteca de controle react e um construtor de cartões interativo. Para obter mais informações, consulte [como começar com o Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="bots-and-the-microsoft-power-virtual-agents"></a>Bots e agentes virtuais do Microsoft Power

[O Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é um serviço de chatbot criado na plataforma do Microsoft Power e na Estrutura de Bots. O processo de desenvolvimento do Power Virtual Agent usa uma abordagem guiada, sem código e interface gráfica que permite aos membros da equipe criar e manter facilmente um agente virtual inteligente. Depois de criar seu chatbot no [portal do Power Virtual Agents,](https://powervirtualagents.microsoft.com)você pode integrá-lo facilmente ao [Teams](how-to/add-power-virtual-agents-bot-to-teams.md). Para obter mais informações sobre como começar, consulte a documentação do [Power Virtual Agents.](https://docs.microsoft.com/power-virtual-agents/)

## <a name="bots-and-webhooks-and-connectors"></a>Bots e webhooks e conectores

Webhooks e conectores conectam seu bot aos seus serviços Web. Usando webhooks e conectores, você pode criar um bot simples para interação básica, como a criação de um fluxo de trabalho ou outros comandos simples. Eles estão disponíveis apenas na equipe em que você os cria e se destinam a processos simples específicos do fluxo de trabalho da sua empresa. Para obter mais informações, consulte [o que são webhooks e conectores.](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="advantages-of-bots"></a>Vantagens dos bots

Os bots no Microsoft Teams podem fazer parte de uma conversa privadas, um chat em grupo ou um canal em uma equipe. Cada escopo fornece oportunidades e desafios exclusivos para seu bot de conversa.

| Em um canal | Em um chat em grupo | Em um chat um para um |
| :-- | :-- | :-- |
| Alcance massivo | Menos membros | Maneira tradicional |
| Concisa interações individuais | @mention para bot  | P&A bots |
| @mention para bot | Semelhante ao canal | Bots que contam as brincadeiras e fazem anotações |

### <a name="in-a-channel"></a>Em um canal

Os canais contêm conversas encadeadas entre várias pessoas até dois mil. Isso pode dar ao bot um grande alcance, mas as interações individuais devem ser concisas. Interações multi-turn tradicionais não funcionam. Em vez disso, você deve procurar usar cartões interativos ou módulos de tarefa ou mover a conversa para uma conversa um para um para coletar muitas informações. Seu bot só tem acesso a mensagens onde ele está `@mentioned` . Você pode recuperar mensagens adicionais da conversa usando o Microsoft Graph e permissões no nível da organização.

Os bots funcionam melhor em um canal nos seguintes casos:

* Notificações, onde você fornece um cartão interativo para os usuários receberem informações adicionais.
* Cenários de feedback, como pesquisas e pesquisas.
* Um único ciclo de solicitação ou resposta resolve interações e os resultados são úteis para vários membros da conversa.
* Bots sociais ou divertidos, onde você recebe uma imagem de gato incrível, escolhe aleatoriamente um vencedor e assim por diante.

### <a name="in-a-group-chat"></a>Em um chat em grupo

Os chats de grupo são conversas não-encadeadas entre três ou mais pessoas. Tendem a ter menos membros do que um canal e são mais temporários. Semelhante a um canal, seu bot só tem acesso a mensagens em que ele está `@mentioned` diretamente.

Nos casos em que os bots funcionam melhor em um canal também funcionam melhor em um chat em grupo.

### <a name="in-a-one-to-one-chat"></a>Em um chat um para um

O chat um para um é uma maneira tradicional de um bot de conversa interagir com um usuário. Alguns exemplos de bots conversais de um para um são os bots de Q&A, bots que iniciam fluxos de trabalho em outros sistemas, bots que contam as piadas e bots que fazem anotações. Antes de criar chatbots um para um, considere se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.

## <a name="disadvantages-of-bots"></a>Desvantagens dos bots

Uma caixa de diálogo extensa entre seu bot e o usuário é uma maneira lenta e complexa de concluir uma tarefa. Um bot que oferece suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não é bem-sucedido ou exibido positivamente pelos usuários.

### <a name="have-multi-turn-experiences-in-chat"></a>Ter experiências multi-turn no chat

Uma caixa de diálogo extensa exige que o desenvolvedor mantenha o estado. Para sair desse estado, um usuário deve ter um tempo de vida ou selecionar **Cancelar**. Além disso, o processo é tedioso. Por exemplo, consulte o seguinte cenário de conversa:

USER: Agende uma reunião com Megan.

BOT: Eu descobri 200 resultados, inclua um nome e sobrenome.

USER: Agende uma reunião com Megan Bowen.

BOT: OK, a que horas você gostaria de se encontrar com Megan Bowen?

USER: 13:00 pm.

BOT: Em qual dia?

### <a name="support-too-many-commands"></a>Dar suporte a muitos comandos

Como há apenas seis comandos visíveis no menu de bot atual, é improvável que algo mais seja usado com qualquer frequência. Bots que vão fundo em uma área específica em vez de tentar ser um trabalho de assistente amplo e melhor tarifa.

### <a name="maintain-a-large-knowledge-base"></a>Manter uma grande base de dados de conhecimento

Uma das desvantagens dos bots é que é difícil manter uma grande base de dados de conhecimento de recuperação com respostas sem controle. Os bots são mais adequados para interações curtas e rápidas e não passam por listas longas procurando uma resposta.

## <a name="code-sample"></a>Exemplo de código

|Exemplo de nome | Descrição | . NETCore | Node.js |
|----------------|-----------------|--------------|----------------|
| Bot de conversas do Teams | Manipulação de eventos de mensagens e conversas. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Manipuladores de atividades bot](~/bots/bot-basics.md)
