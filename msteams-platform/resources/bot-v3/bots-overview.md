---
title: Adicionar bots a Microsoft Teams aplicativos
description: Descreve como começar a desenvolver bots no Microsoft Teams
ms.topic: conceptual
keywords: desenvolvimento de bots do Teams
ms.localizationpriority: medium
ms.date: 05/20/2018
ms.openlocfilehash: 164c8e518e38d506bbaf80f59edebfb18c07acec
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103422"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicionar bots a Microsoft Teams aplicativos

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Crie e conecte bots inteligentes para interagir com Microsoft Teams usuários naturalmente por meio do chat. Ou forneça um bot simples baseado em comandos, a ser usado como sua interface de "linha de comando" para sua experiência mais Teams aplicativo. Você pode criar um bot somente notificação, que pode enviar por push informações relevantes para seus usuários diretamente para eles em um canal ou mensagem direta. Você pode até mesmo trazer seu bot baseado no Bot Framework existente e adicionar Teams suporte específico para fazer sua experiência brilhar.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis no GCC-High e departamento de defesa (DOD).

![Exemplo de um bot que ajuda um usuário](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: Bots

Um bot aparece como qualquer outro membro da equipe com o qual você interage em uma conversa, exceto que ele tem um ícone de avatar hexagonal e está sempre online.

Um bot se comporta de maneira diferente dependendo do tipo de conversa em que ele está envolvido. Os bots Teams dão suporte a vários tipos de conversas chamadas escopos no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).

* `teams` Também chamadas de conversas de canal.
* `personal` Conversas entre um bot e um único usuário.
* `groupChat` Uma conversa entre um bot e dois ou mais usuários.

Para obter mais informações, [consulte Ter uma conversa com um Microsoft Teams bot](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Com Microsoft Teams aplicativos, você pode tornar o bot a estrela de sua experiência ou apenas um auxiliar. Os bots são distribuídos como parte do pacote mais amplo do aplicativo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou [extensões de mensagem](~/messaging-extensions/what-are-messaging-extensions.md).

## <a name="bot-apis"></a>Bot APIs

Microsoft Teams dá suporte à maioria dos [Microsoft Bot Framework](https://dev.botframework.com/). (Se você já tiver um bot baseado no Bot Framework, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams.) Recomendamos que você use C# ou Node.js para aproveitar nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e os métodos básicos SDK do Construtor de Bot:

* Usando tipos de cartão especializados, como o cartão Office 365 Connector.
* Consumindo e definindo Teams dados de canal específicos em atividades.
* Processando solicitações de extensão de mensagem.

As extensões do SDK instalam dependências, incluindo o SDK do Bot Builder.

* **.NET** Para usar as extensões Microsoft Teams para o SDK do Bot Builder para .NET, instale o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet em seu projeto Visual Studio. Para Node.js desenvolvimento, o BotBuilder para Microsoft Teams funcionalidade foi incorporado ao [SDK do Bot Framework](https://github.com/microsoft/botframework-sdk) desde a v4.6.

> [!IMPORTANT]
> Você pode desenvolver Teams aplicativos em qualquer outra tecnologia de programação na Web e chamar as [APIs REST do Bot Framework](/bot-framework/rest-api/bot-framework-rest-overview) diretamente, mas deve executar todo o tratamento de token por conta própria.

*Teams App Studio ajuda* você a criar e configurar o manifesto do aplicativo e pode criar seu bot do Bot Framework para você. Ele também contém uma biblioteca React controle e um construtor de cartões interativo.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Os webhooks de saída permitem que você crie um bot simples para interação básica, como o início de um fluxo de trabalho ou outros comandos simples que você possa precisar. Os webhooks de saída vivem apenas na equipe na qual você os cria e são destinados a processos simples específicos para o fluxo de trabalho da sua empresa. Para obter mais informações, consulte [webhooks de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Criar um bot de Teams excelente

Os tópicos a seguir orientarão você pelo processo de criação de um ótimo bot para Teams:

* [Criar um bot](~/resources/bot-v3/bots-create.md): aproveite as excelentes ferramentas, a documentação e a comunidade fornecidas pela equipe do Bot Framework.
* [Fale com seu bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): adicione o fluxo de conversa básico e aproveite a funcionalidade específica do canal. Se você desenvolver no .NET ou Node.js, use nossas extensões para o SDK do Bot Builder para simplificar seu trabalho.
* [Usando cartões em seu bot](~/resources/bot-v3/bots-cards.md): crie cartões para se comunicar e aceitar a resposta do usuário.
* [Responder a eventos de bot](~/resources/bot-v3/bots-notifications.md)
* [Bots somente notificação](~/resources/bot-v3/bots-notification-only.md): usando bots para enviar notificações para seu aplicativo.
* [Obter contexto](~/resources/bot-v3/bots-context.md): obter informações sobre o usuário.
* [Menus de bot](~/resources/bot-v3/bots-menus.md): usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md): enviando e recebendo arquivos de bots.
* [Usando guias com bots](~/resources/bot-v3/bots-with-tabs.md): fazer guias e bots funcionarem juntos.
* [Teste seu bot](~/resources/bot-v3/bots-test.md): adicione seu bot para conversas pessoais ou de equipe para vê-lo em ação.

## <a name="see-also"></a>Confira também

[Exemplos do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
