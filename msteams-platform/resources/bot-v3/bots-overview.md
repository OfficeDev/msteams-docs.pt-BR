---
title: Adicionar bots aos aplicativos do Microsoft Teams
description: Descreve como começar a desenvolver bots no Microsoft Teams
ms.topic: conceptual
keywords: desenvolvimento de bots do Teams
ms.date: 05/20/2018
ms.openlocfilehash: 226340500f59754d603f21b7868eecab38f942af
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014401"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicionar bots aos aplicativos do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Crie e conecte bots inteligentes para interagir naturalmente com os usuários do Microsoft Teams por meio de chat. Ou forneça um bot simples baseado em comandos, a ser usado como sua interface de "linha de comando" para sua experiência mais ampla de aplicativos do Teams. Você pode fazer um bot somente de notificação, que pode enviar informações relevantes aos usuários diretamente para eles em um canal ou mensagem direta. Você pode até mesmo trazer seu bot existente baseado em Estrutura de Bot e adicionar suporte específico do Teams para fazer sua experiência se sobresspaldar.

![Exemplo de um bot que auxilia um usuário](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: bots

Um bot aparece como qualquer outro membro da equipe com o qual você interage em uma conversa, exceto que ele tem um ícone de avatar hexagonal e está sempre online.

Um bot se comporta de forma diferente dependendo do tipo de conversa em que ele está envolvido. Os bots no Teams suportam vários tipos de conversas (chamados de escopos no manifesto [do aplicativo).](~/resources/schema/manifest-schema.md)

* `teams` Também chamadas de conversas de canal
* `personal` Conversas entre um bot e um único usuário
* `groupChat` Uma conversa entre um bot e dois ou mais usuários

Confira [Ter uma conversa com um bot do Microsoft Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md) para obter mais informações.

Com os aplicativos do Microsoft Teams, você pode tornar o bot a estrela da sua experiência ou apenas um auxiliar. Os bots são distribuídos como parte do pacote mais amplo do aplicativo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou extensões [de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md)

## <a name="bot-apis"></a>Bot APIs

O Microsoft Teams é compatível com a maioria [do Microsoft Bot Framework.](https://dev.botframework.com/) (Se você já tiver um bot baseado na Estrutura de Bot, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams.) Recomendamos que você use C# ou Node.js para tirar proveito de [nossos SDKs.](/microsoftteams/platform/#pivot=sdk-tools) Esses pacotes estendem as classes e métodos básicos do SDK do Bot Builder:

* Usando tipos de cartão especializados, como o cartão do Conector do Office 365
* Consumindo e definindo dados de canal específicos do Teams em atividades
* Processar solicitações de extensão de mensagens

As extensões do SDK instalam dependências, incluindo o SDK do Construtor de Bots.

* **.NET** Para usar as extensões do Microsoft Teams para o SDK do Construtor de Bots para .NET, instale o pacote [NuGet Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) no projeto do Visual Studio. Para Node.js desenvolvimento, a funcionalidade BotBuilder para Microsoft Teams foi incorporada ao [SDK](https://github.com/microsoft/botframework-sdk) do Bot Framework a partir da v4.6.

*Consulte também exemplos* [de Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

> [!IMPORTANT]
> Você pode desenvolver aplicativos do Teams em qualquer outra tecnologia de programação na Web e chamar as [APIs REST](/bot-framework/rest-api/bot-framework-rest-overview) do Bot Framework diretamente, mas deve executar todo o tratamento de token por conta própria.

*O Teams App Studio* ajuda você a criar e configurar o manifesto do aplicativo e pode criar seu bot do Bot Framework para você. Ele também contém uma biblioteca de controle react e um construtor de cartão interativo.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Os webhooks de saída permitem que você crie um bot simples para interação básica, como sair de um fluxo de trabalho ou outros comandos simples que você possa precisar. Os webhooks de saída só estão na equipe na qual você os cria e se destinam a processos simples específicos do fluxo de trabalho da empresa. Consulte [webhooks de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md) para obter mais informações.

## <a name="build-a-great-teams-bot"></a>Criar um ótimo bot do Teams

Os tópicos a seguir orientarão você durante o processo de criação de um ótimo bot para o Teams.

* [Crie um bot:](~/resources/bot-v3/bots-create.md)aproveite as excelentes ferramentas, documentação e comunidade fornecidas pela equipe do Bot Framework.
* [Converse com seu bot:](~/resources/bot-v3/bot-conversations/bots-conversations.md)adicione o fluxo de conversa básica e aproveite a funcionalidade específica do canal. Se você desenvolver no .NET ou Node.js, use nossas extensões para o SDK do Construtor de Bots para simplificar seu trabalho.
* [Usando cartões em seu bot](~/resources/bot-v3/bots-cards.md) Criar cartões para se comunicar e aceitar a resposta do usuário.
* [Responder a eventos de bot.](~/resources/bot-v3/bots-notifications.md)
* [Bots somente notificação](~/resources/bot-v3/bots-notification-only.md) Usar bots para enviar notificações para seu aplicativo.
* [Obter contexto](~/resources/bot-v3/bots-context.md) Obter informações sobre o usuário.
* [Menus de bot](~/resources/bot-v3/bots-menus.md) Usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md) Enviar e receber arquivos de bots.
* [Usando guias com bots](~/resources/bot-v3/bots-with-tabs.md) Fazer guias e bots funcionarem juntos.
* [Teste seu bot:](~/resources/bot-v3/bots-test.md)adicione seu bot para conversas pessoais ou em equipe para vê-lo em ação.
