---
title: Adicionar bots aos aplicativos do Microsoft Teams
description: Descreve como começar a desenvolver bots no Microsoft Teams
keywords: desenvolvimento de bots do teams
ms.date: 05/20/2018
ms.openlocfilehash: 58221e94520ef6e748bbd6c17fa7933813874c56
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228049"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicionar bots aos aplicativos do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Crie e conecte bots inteligentes para interagir com os usuários do Microsoft Teams naturalmente por meio de chat. Ou fornecer um bot simples baseado em comandos, para ser usado como a interface de linha de comando para sua experiência mais ampla de aplicativos do teams. Você pode criar um bot somente para notificação, que pode enviar informações relevantes aos seus usuários diretamente para eles em um canal ou em uma mensagem direta. Você pode até mesmo trazer o bot baseado na estrutura de bot existente e adicionar suporte específico ao Teams para fazer com que sua experiência se sobressaia.

![Exemplo de um bot que ajuda um usuário](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: bots

Um bot aparece exatamente como qualquer outro membro da equipe com o qual você interage em uma conversa, exceto pelo fato de ter um ícone de avatar hexágono e está sempre online.

Um bot se comporta de forma diferente dependendo do tipo de conversa em que está envolvido. Os bots no Teams dão suporte a vários tipos de conversas (chamadas de escopos no [manifesto do aplicativo](~/resources/schema/manifest-schema.md)).

* `teams`Também chamadas de conversas de canal
* `personal`Conversas entre um bot e um único usuário
* `groupChat`Uma conversa entre um bot e dois ou mais usuários

Confira uma [conversa com um bot do Microsoft Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md) para obter mais informações.

Com os aplicativos do Microsoft Teams, você pode tornar o bot a estrela de sua experiência ou apenas um auxiliar. Os bots são distribuídos como parte do pacote de aplicativos mais amplo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou [extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md).

## <a name="bot-apis"></a>APIs de bot

O Microsoft Teams é compatível com a maior parte do [Microsoft bot Framework](https://dev.botframework.com/). (Se você já tiver um bot baseado na estrutura de bot, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams.) Recomendamos que você use C# ou node. js para aproveitar os benefícios de nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e métodos do SDK do construtor de bot básicos:

* Usando tipos de cartões especializados como o cartão de conexão do Office 365
* Consumindo e configurando dados de canal específicos do teams em atividades
* Processar solicitações de extensão de mensagens

As extensões SDK instalam dependências, incluindo o SDK do bot Builder.

* **.Net** Para usar o Microsoft Teams Extensions para o SDK do bot Builder para .NET, instale o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) no seu projeto do Visual Studio. Para o desenvolvimento de Node. js, a funcionalidade do BotBuilder para Microsoft Teams foi incorporada ao [SDK da estrutura de bot](https://github.com/microsoft/botframework-sdk) a partir da v 4.6.

*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

> [!IMPORTANT]
> Você pode desenvolver aplicativos do teams em qualquer outra tecnologia de programação da Web e chamar as [APIs REST da estrutura de bot](/bot-framework/rest-api/bot-framework-rest-overview) diretamente, mas você deve executar todo o tratamento de tokens por conta própria.

O *Teams app Studio* ajuda você a criar e configurar seu manifesto de aplicativo e pode criar seu bot da estrutura de bot para você. Ele também contém uma biblioteca de controle de reagir e um construtor de cartões interativos.

## <a name="outgoing-webhooks"></a>WebHooks de saída

Os WebHooks de saída permitem que você crie um bot simples para interação básica, como o Iniciando de um fluxo de trabalho ou outros comandos simples que você possa precisar. Os WebHooks de saída residem apenas na equipe em que você os cria e se destinam a processos simples específicos do fluxo de trabalho de sua empresa. Confira [WebHooks de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md) para obter mais informações.

## <a name="build-a-great-teams-bot"></a>Criar um grande bot de equipes

Os tópicos a seguir guiarão você pelo processo de criação de um ótimo bot para o Teams.

* [Criar um bot](~/resources/bot-v3/bots-create.md): Aproveite as excelentes ferramentas, documentação e comunidade fornecidas pela equipe do bot Framework.
* [Fale com o seu bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): Adicionar fluxo de conversa básica e aproveitar a funcionalidade específica do canal. Se você desenvolver no .NET ou node. js, use nossas extensões para o SDK do bot Builder para simplificar seu trabalho.
* [Usando cartões no bot](~/resources/bot-v3/bots-cards.md) Cartões de design para se comunicar e aceitar a resposta do usuário.
* [Responder a eventos de bot](~/resources/bot-v3/bots-notifications.md).
* [Bots somente de notificação](~/resources/bot-v3/bots-notification-only.md) Usando bots para enviar notificações para seu aplicativo.
* [Obter contexto](~/resources/bot-v3/bots-context.md) Obter informações sobre o usuário.
* [Menus do bot](~/resources/bot-v3/bots-menus.md) Usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md) Envio e recebimento de arquivos de bots.
* [Usando guias com bots](~/resources/bot-v3/bots-with-tabs.md) Tornar guias e bots funcionando juntos.
* [Teste seu bot](~/resources/bot-v3/bots-test.md): Adicione seu bot para conversas pessoais ou de equipe para vê-lo em ação.
