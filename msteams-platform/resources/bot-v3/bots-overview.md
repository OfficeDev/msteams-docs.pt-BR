---
title: Adicione bots a aplicativos Microsoft Teams
description: Descreve como começar a desenvolver bots em Microsoft Teams
ms.topic: conceptual
keywords: desenvolvimento de bots equipes
localization_priority: Normal
ms.date: 05/20/2018
ms.openlocfilehash: 674576efccb2916b8a82ae27310d8fe49909a782
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566751"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicione bots a aplicativos Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Construa e conecte bots inteligentes para interagir com Microsoft Teams usuários naturalmente através do chat. Ou fornecer um bot baseado em comandos simples, para ser usado como sua interface "linha de comando" para sua experiência mais ampla Teams aplicativo. Você pode fazer um bot somente de notificação, que pode levar informações relevantes para seus usuários diretamente para eles em um canal ou mensagem direta. Você pode até mesmo trazer o bot baseado em Bot Framework existente e adicionar suporte específico Teams para fazer sua experiência brilhar.

![Exemplo de um bot auxiliando um usuário](~/assets/images/bot_example.png)

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: Bots

Um bot aparece como qualquer outro membro da equipe com quem você interage em uma conversa, exceto que ele tem um ícone de avatar hexagonal e está sempre online.

Um bot se comporta de forma diferente dependendo do tipo de conversa em que está envolvido. Bots em Teams suportam vários tipos de conversas chamadas escopos no manifesto do [aplicativo](~/resources/schema/manifest-schema.md).

* `teams` Também chamadas de conversas de canal.
* `personal` Conversas entre um bot e um único usuário.
* `groupChat` Uma conversa entre um bot e 2 ou mais usuários.

Para obter mais informações, [consulte Tenha uma conversa com um bot Microsoft Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Com Microsoft Teams aplicativos, você pode fazer do bot a estrela da sua experiência, ou apenas um ajudante. Os bots são distribuídos como parte de seu pacote de aplicativos mais amplo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou [extensões de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md)

## <a name="bot-apis"></a>Bot APIs

Microsoft Teams apoia a maior parte do [Microsoft Bot Framework.](https://dev.botframework.com/) (Se você já tem um bot baseado no Bot Framework, você pode facilmente adaptá-lo para trabalhar em Microsoft Teams.) Recomendamos que você use C# ou Node.js para aproveitar [nossos SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e os métodos básicos SDK do Construtor de Bot:

* Usando tipos de cartões especializados como o cartão Office 365 Connector.
* Consumindo e definindo dados de canais específicos Teams sobre atividades.
* Processar solicitações de extensão de mensagens.

As extensões SDK instalam dependências, incluindo o Bot Builder SDK.

* **.NET** Para usar as extensões Microsoft Teams para o Bot Builder SDK para .NET, instale o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet no seu projeto Visual Studio. Para Node.js desenvolvimento, o BotBuilder for Microsoft Teams funcionalidade foi incorporado ao [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) a partir de v4.6.

> [!IMPORTANT]
> Você pode desenvolver aplicativos Teams em qualquer outra tecnologia de programação web e chamar diretamente as [APIs do Bot Framework REST,](/bot-framework/rest-api/bot-framework-rest-overview) mas você deve executar todos os tokens manuseando a si mesmo.

*Teams App Studio* ajuda você a criar e configurar seu manifesto de aplicativo e pode criar seu bot Framework para você. Ele também contém uma biblioteca de controle de React e um construtor de cartões interativo.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Webhooks de saída permitem que você crie um bot simples para interação básica, como iniciar um fluxo de trabalho ou outros comandos simples que você pode precisar. Os webhooks de saída vivem apenas na equipe em que você os cria e são destinados a processos simples específicos do fluxo de trabalho da sua empresa. Para obter mais informações, consulte [webhooks de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Construa um ótimo robô Teams

Os seguintes tópicos irão guiá-lo durante o processo de criação de um ótimo bot para Teams:

* [Crie um bot](~/resources/bot-v3/bots-create.md): Aproveite as grandes ferramentas, documentação e comunidade fornecidas pela equipe do Bot Framework.
* [Fale com seu bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): Adicione fluxo básico de conversação e aproveite a funcionalidade específica do canal. Se você se desenvolver em .NET ou Node.js, use nossas extensões para o Bot Builder SDK para simplificar seu trabalho.
* [Usando cartões em seu bot](~/resources/bot-v3/bots-cards.md): Designar cartões para comunicar e aceitar a resposta do usuário.
* [Responda a eventos de bot](~/resources/bot-v3/bots-notifications.md)
* [Bots somente de notificação](~/resources/bot-v3/bots-notification-only.md): Usando bots para enviar notificações para o seu aplicativo.
* [Obter contexto](~/resources/bot-v3/bots-context.md): Obtenha informações sobre o usuário.
* [Menus de bot](~/resources/bot-v3/bots-menus.md): Usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md): Envio e recebimento de arquivos de bots.
* [Usando guias com bots](~/resources/bot-v3/bots-with-tabs.md): Fazer abas e bots funcionarem juntos.
* [Teste seu bot](~/resources/bot-v3/bots-test.md): Adicione seu bot para conversas pessoais ou de equipe para vê-lo em ação.

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).