---
title: Adicionar bots a Microsoft Teams aplicativos
description: Descreve como começar a desenvolver bots no Microsoft Teams
ms.topic: conceptual
keywords: desenvolvimento de bots do teams
ms.localizationpriority: medium
ms.date: 05/20/2018
ms.openlocfilehash: afa83478ee478d74dbdedb5cd805719fc8434070
ms.sourcegitcommit: 6573881f7e69d8e5ec8861f54df84e7d519f0511
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60096546"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicionar bots a Microsoft Teams aplicativos

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Crie e conecte bots inteligentes para interagir com Microsoft Teams usuários naturalmente por meio do chat. Ou forneça um bot simples baseado em comandos, a ser usado como sua interface de "linha de comando" para sua experiência Teams aplicativo mais ampla. Você pode fazer um bot somente de notificação, que pode enviar informações relevantes para seus usuários diretamente para eles em um canal ou mensagem direta. Você pode até mesmo trazer seu bot baseado em Bot Framework existente e adicionar Teams suporte específico para fazer sua experiência brilhar.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis no Nuvem da Comunidade Governamental (GCC) mas não estão disponíveis no GCC-High e Departamento de Defesa (DOD).

![Exemplo de um bot ajudando um usuário](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: Bots

Um bot aparece como qualquer outro membro da equipe com o qual você interage em uma conversa, exceto que ele tem um ícone de avatar hexagonal e está sempre online.

Um bot se comporta de forma diferente, dependendo do tipo de conversa em que ele está envolvido. Os bots no Teams suportam vários tipos de conversas chamadas escopos no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).

* `teams` Também chamadas de conversas de canal.
* `personal` Conversas entre um bot e um único usuário.
* `groupChat` Uma conversa entre um bot e dois ou mais usuários.

Para obter mais informações, [consulte Have a conversation with a Microsoft Teams bot](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Com Microsoft Teams aplicativos, você pode tornar o bot a estrela da sua experiência ou apenas um auxiliar. Os bots são distribuídos como parte do pacote de aplicativos mais amplo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou extensões [de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md)

## <a name="bot-apis"></a>Bot APIs

Microsoft Teams suporta a maioria dos [Microsoft Bot Framework](https://dev.botframework.com/). (Se você já tiver um bot baseado na Estrutura de Bots, poderá adaptá-lo facilmente para trabalhar Microsoft Teams.) Recomendamos que você use C# ou Node.js tirar proveito dos [nossos SDKs.](/microsoftteams/platform/#pivot=sdk-tools) Esses pacotes estendem as classes e os métodos básicos SDK do Construtor de Bot:

* Usando tipos de cartão especializados, como o cartão Office 365 Conector.
* Consumindo e definindo Teams dados de canal específicos em atividades.
* Processamento de solicitações de extensão de mensagens.

As extensões do SDK instalam dependências, incluindo o SDK do Construtor de Bots.

* **.NET** Para usar as extensões Microsoft Teams do SDK do Construtor de Bots para .NET, instale o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet em seu projeto Visual Studio. Para Node.js desenvolvimento, a funcionalidade BotBuilder for Microsoft Teams foi incorporada ao [SDK](https://github.com/microsoft/botframework-sdk) da Estrutura de Bots a partir da v4.6.

> [!IMPORTANT]
> Você pode desenvolver Teams aplicativos em qualquer outra tecnologia de programação da Web e chamar as [APIs REST](/bot-framework/rest-api/bot-framework-rest-overview) da Estrutura de Bot diretamente, mas você deve executar todos os tokens manipulando a si mesmo.

*Teams App Studio* ajuda você a criar e configurar seu manifesto do aplicativo e pode criar seu bot da Estrutura de Bots para você. Ele também contém uma biblioteca de React de controle e um construtor de cartões interativo. 

## <a name="outgoing-webhooks"></a>Webhooks de saída

Webhooks de saída permitem que você crie um bot simples para interação básica, como o início de um fluxo de trabalho ou outros comandos simples que você pode precisar. Os webhooks de saída só vivem na equipe na qual você os cria e se destinam a processos simples específicos do fluxo de trabalho da sua empresa. Para obter mais informações, consulte [webhooks de saída.](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="build-a-great-teams-bot"></a>Criar um ótimo Teams bot

Os tópicos a seguir orientarão você durante o processo de criação de um ótimo bot para Teams:

* [Criar um bot](~/resources/bot-v3/bots-create.md): tire proveito das ótimas ferramentas, documentação e comunidade fornecidas pela equipe da Estrutura de Bots.
* [Converse com seu bot:](~/resources/bot-v3/bot-conversations/bots-conversations.md)adicione o fluxo básico de conversa e aproveite a funcionalidade específica do canal. Se você desenvolver no .NET ou Node.js, use nossas extensões para o SDK do Construtor de Bots para simplificar seu trabalho.
* [Usando cartões em seu bot](~/resources/bot-v3/bots-cards.md): Projetar cartões para se comunicar e aceitar a resposta do usuário.
* [Responder a eventos de bot](~/resources/bot-v3/bots-notifications.md)
* [Bots somente notificação:](~/resources/bot-v3/bots-notification-only.md)usando bots para enviar notificações para seu aplicativo.
* [Obter contexto](~/resources/bot-v3/bots-context.md): obter informações sobre o usuário.
* [Menus bot](~/resources/bot-v3/bots-menus.md): Usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md): Enviando e recebendo arquivos de bots.
* [Usando guias com bots:](~/resources/bot-v3/bots-with-tabs.md)fazer guias e bots funcionarem juntos.
* [Teste seu bot](~/resources/bot-v3/bots-test.md): adicione seu bot para conversas pessoais ou de equipe para vê-lo em ação.

## <a name="see-also"></a>Confira também

[Exemplos de Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).