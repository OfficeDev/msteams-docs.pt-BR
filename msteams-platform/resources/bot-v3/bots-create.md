---
title: Criar um bot
description: Descreve como criar bots no Microsoft Teams
keywords: criação de bots do teams
ms.date: 12/07/2018
ms.openlocfilehash: cb2d0974baf1d36a4acf077c219eb12449a5721a
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672500"
---
# <a name="create-a-bot"></a>Criar um bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Todos os bots criados usando o Microsoft bot Framework estão configurados e prontos para trabalhar no Microsoft Teams.

Consulte a [documentação da estrutura do bot](/azure/bot-service/?view=azure-bot-service-3.0) para obter informações gerais sobre bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

O *Teams app Studio* é uma ferramenta que pode ajudar a criar seu bot e um pacote de aplicativos que faz referência ao bot. Ele também contém uma biblioteca de controle de reagir e exemplos configuráveis para cartões. Confira [introdução ao Teams app Studio](~/concepts/build-and-test/app-studio-overview.md). As etapas a seguir pressupõem que você está configurando o bot e não usando o *Teams app Studio*.

1. Crie o bot usando este link: https://dev.botframework.com/bots/new. **Certifique-se de adicionar o Microsoft Teams como um canal da lista de canais de destaque depois de criar seu bot.** Sinta-se livre para reutilizar qualquer ID do aplicativo da Microsoft gerado se você já criou seu pacote/manifesto do aplicativo.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Se não quiser criar seu bot no Azure, você **deve** usar este link para criar um novo bot: https://dev.botframework.com/bots/new. Se você clicar no botão *criar um bot* no portal da estrutura do bot, você [criará seu bot no Microsoft Azure](#bots-and-microsoft-azure) em vez disso.

2. Construa o bot usando o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , o pacote [botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) NPM ou a [API do conector do bot](https://docs.microsoft.com/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Teste o bot usando o [emulador da estrutura de bot](https://docs.microsoft.com/bot-framework/debug-bots-emulator).

4. Implantar o bot em um serviço de nuvem, como [o Microsoft Azure](https://azure.microsoft.com/). Como alternativa, execute o aplicativo localmente e use um serviço de encapsulamento, [ngrok](https://ngrok.com) para expor um ponto de extremidade https://para o bot `https://45az0eb1.ngrok.io/api/messages`, como.

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots e Microsoft Azure
> A partir de dezembro de 2017, o portal da estrutura do bot é otimizado para registrar bots no Microsoft Azure. Veja algumas coisas que você precisa saber:
>
> * O canal do Microsoft Teams para bots registrados no Azure é gratuito. As mensagens enviadas pelo canal Teams não serão contadas em direção às mensagens consumidas para o bot.
> * Embora seja possível [criar um novo bot da estrutura de bot](https://dev.botframework.com/bots/new) sem usar o Azure, você deve usar essa URLhttps://dev.botframework.com/bots/new)(, que não está mais exposta no portal da estrutura do bot.
> * Ao editar as propriedades de um bot existente na [lista de seus bots na estrutura de bot](https://dev.botframework.com/bots) , como seu "ponto de extremidade de mensagem", que é comum ao desenvolver primeiro um bot, especialmente se você usar o [ngrok](https://ngrok.com), verá a coluna "status de migração" e um botão azul "migrar" que o levará ao portal do Microsoft Azure. Não clique no botão "migrar", a menos que seja o que você deseja fazer; em vez disso, clique no nome do bot e você pode editar suas propriedades:</br>
   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Se você registrar seu bot usando o Microsoft Azure, seu código de bot não precisará estar *hospedado* no Microsoft Azure.
> * Se você registrar um bot usando o portal do Microsoft Azure, você precisará de uma conta do Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade quando você cria um, você deve fornecer um cartão de crédito, mas ele não será cobrado; é sempre gratuito criar e usar bots com o Microsoft Teams.
> * Agora você pode usar o app Studio para registrar/atualizar as informações de aplicativo e de bot diretamente no Microsoft Teams. Você só terá que usar o portal do Microsoft Azure para adicionar/configurar outros canais da estrutura de bot, como linha direta, chat Web, Skype e Facebook Messenger.
