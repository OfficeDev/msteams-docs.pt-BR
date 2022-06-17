---
title: Adicionar bots a aplicativos do Microsoft Teams
description: Neste módulo, saiba como começar a desenvolver bots no Microsoft Teams e quais são todos os requisitos para adicionar um bot no Teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/20/2018
ms.openlocfilehash: 6c57371e0df5739d800fc07e46a014aeb3836bc8
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142357"
---
# <a name="add-bots-to-microsoft-teams-apps"></a>Adicionar bots a aplicativos do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Crie e conecte bots inteligentes para interagir com os usuários do Microsoft Teams naturalmente por meio do chat. Ou forneça um bot simples baseado em comandos, a ser usado como sua interface de "linha de comando" para ter uma experiência mais ampla do aplicativo do Teams. Você pode criar um bot somente notificação, que pode enviar por push informações relevantes para seus usuários diretamente para eles em um canal ou mensagem direta. Você pode até mesmo trazer sua Bot Framework existente e adicionar suporte específico do Teams para fazer sua experiência se destacar.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis no Nuvem da Comunidade Governamental (GCC) e GCC-High, mas não estão disponíveis no Departamento de Defesa (DOD).

:::image type="content" source="../../assets/images/bot_example.png" alt-text="Exemplo de um bot ajudando um usuário" border="true":::

## <a name="what-you-need-to-know-bots"></a>O que você precisa saber: bots

Um bot aparece como qualquer outro membro da equipe com o qual você interage em uma conversa, exceto que ele tem um ícone de avatar hexagonal e está sempre online.

Um bot se comporta de maneira diferente dependendo do tipo de conversa em que ele está envolvido. Os bots no Teams dão suporte a vários tipos de conversas chamadas escopos no [manifesto do aplicativo](~/resources/schema/manifest-schema.md).

* `teams` Também chamado de conversas de canal.
* `personal` Conversas entre bots e um único usuário.
* `groupChat` Uma conversa entre um bot e dois ou mais usuários.

Para obter mais informações, [Converse com um bot do Microsoft Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Com os aplicativos do Microsoft Teams, você pode tornar o bot a estrela de sua experiência ou apenas um auxiliar. Os bots são distribuídos como parte do pacote de aplicativos mais amplo, que pode incluir outros recursos, como [guias](~/tabs/what-are-tabs.md) ou [extensões de mensagem](~/messaging-extensions/what-are-messaging-extensions.md).

## <a name="bot-apis"></a>APIs de bot

O Microsoft Teams dá suporte à maioria dos [Bot Framework da Microsoft](https://dev.botframework.com/). (Se você já tiver um bot baseado no Bot Framework, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams). Recomendamos que você use C# ou Node.js para aproveitar nosso [SDKs](/microsoftteams/platform/#pivot=sdk-tools). Esses pacotes estendem as classes e os métodos básicos SDK do Construtor de Bot:

* Usando tipos de cartão especializados, como o cartão do Conector do Office 365.
* Consumindo e definindo dados de canal específicos do Teams em atividades.
* Processando solicitações de extensão de mensagem.

As extensões do SDK instalam dependências, incluindo o Bot Builder SDK.

* **.NET** Para usar as extensões do Microsoft Teams para o SDK do Bot Builder para .NET, instale o pacote NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) em seu projeto do Visual Studio. Para o desenvolvimento do Node.js, a funcionalidade BotBuilder para Microsoft Teams foi incorporada ao [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) a partir da v4.6.

> [!IMPORTANT]
> Você pode desenvolver aplicativos do Teams em qualquer outra tecnologia de programação na Web e chamar as[APIs REST do Bot Framework](/bot-framework/rest-api/bot-framework-rest-overview) diretamente, mas deve executar todo o tratamento de token por conta própria.

O *Teams App Studio* ajuda você a criar e configurar o manifesto do aplicativo e pode criar seu bot do Bot Framework para você. Ele também contém uma biblioteca de controle React e um construtor de cartões interativo.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Os webhooks de saída permitem que você crie um bot simples para interação básica, como iniciar um fluxo de trabalho ou outros comandos simples que você possa precisar. Os webhooks de saída só existem na equipe na qual você os cria e se destinam a processos simples específicos para o fluxo de trabalho da sua empresa. Para obter mais informações, consulte [hooks de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="build-a-great-teams-bot"></a>Crie um ótimo bot do Teams

Os artigos a seguir orientarão você pelo processo de criação de um ótimo bot para Teams:

* [Crie um bot](~/resources/bot-v3/bots-create.md): aproveite as excelentes ferramentas, documentação e comunidade fornecidas pela equipe do Bot Framework.
* [Converse com seu bot](~/resources/bot-v3/bot-conversations/bots-conversations.md): adicione o fluxo de conversa básico e aproveite a funcionalidade específica do canal. Se você desenvolve no .NET ou node.js, use nossas extensões para o SDK do Bot Builder para simplificar seu trabalho.
* [Usando cartões em seu bot](~/resources/bot-v3/bots-cards.md): crie cartões para se comunicar e aceitar a resposta do usuário.
* [Responder a eventos de bot](~/resources/bot-v3/bots-notifications.md)
* [Bots somente para notificação](~/resources/bot-v3/bots-notification-only.md): usando bots para enviar notificações para seu aplicativo.
* [Obtenha contexto](~/resources/bot-v3/bots-context.md): obtenha informações sobre o usuário.
* [Menus de bot](~/resources/bot-v3/bots-menus.md): usando menus em bots.
* [Bots e arquivos](~/resources/bot-v3/bots-files.md): enviando e recebendo arquivos de bots.
* [Usando guias com bots](~/resources/bot-v3/bots-with-tabs.md): fazendo com que guias e bots funcionem juntos.
* [Teste seu bot](~/resources/bot-v3/bots-test.md): adicione seu bot para conversas pessoais ou de equipe para vê-lo em ação.

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
