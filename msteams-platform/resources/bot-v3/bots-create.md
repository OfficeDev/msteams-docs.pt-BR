---
title: Criar um bot
description: Descreve como criar bots no Microsoft Teams
ms.topic: how-to
keywords: criação de bots do Teams
ms.date: 12/07/2018
ms.openlocfilehash: d7c618adc99f814bd677e919923c4b616f293e17
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014086"
---
# <a name="create-a-bot"></a>Criar um bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Todos os bots criados usando o Microsoft Bot Framework estão configurados e prontos para funcionar no Microsoft Teams.

Consulte a [Documentação da Estrutura de Bot](/azure/bot-service/?view=azure-bot-service-3.0) para obter informações gerais sobre bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

*O Teams App Studio* é uma ferramenta que pode ajudar a criar seu bot e um pacote do aplicativo que faz referência ao seu bot. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Confira [Introdução ao Teams app Studio](~/concepts/build-and-test/app-studio-overview.md). As etapas a seguir presumem que você está configurando seu bot e não usando o *Teams App Studio.*

1. Crie o bot usando este link: https://dev.botframework.com/bots/new . **Lembre-se de adicionar o Microsoft Teams como um canal da lista de canais em destaque após criar seu bot.** Sinta-se à vontade para usar novamente o ID do aplicativo da Microsoft que você gerou, caso já tenha criado seu pacote/manifesto de aplicativos.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Se você não quiser criar seu bot no Azure, **deverá** usar este link para criar um novo bot: https://dev.botframework.com/bots/new . Se você clicar no botão *Criar um bot* no portal do Bot Framework, em vez disso, criará seu bot no Microsoft [Azure.](#bots-and-microsoft-azure)

2. Crie o bot usando o pacote [NuGet Microsoft.Bot.Connector.Teams,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) o [SDK](https://github.com/microsoft/botframework-sdk)da Estrutura de Bot ou a [API do Conector de Bot.](https://docs.microsoft.com/bot-framework/rest-api/bot-framework-rest-connector-api-reference) *Consulte também exemplos* [de Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)

3. Teste o bot usando o [Emulador da Estrutura de Bot.](https://docs.microsoft.com/bot-framework/debug-bots-emulator)

4. Implante o bot em um serviço de nuvem, como [o Microsoft Azure.](https://azure.microsoft.com/) Como alternativa, execute seu aplicativo localmente e use um serviço de túnel como [ngrok](https://ngrok.com) para expor um ponto de extremidade https:// seu bot, como `https://45az0eb1.ngrok.io/api/messages` .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots e Microsoft Azure
> A partir de dezembro de 2017, o portal do Bot Framework foi otimizado para registrar bots no Microsoft Azure. Aqui estão algumas coisas que você precisa saber:
>
> * O canal do Microsoft Teams para bots registado no Azure é gratuito. As mensagens enviadas pelo canal do Teams não contarão para as mensagens consumidas para o bot.
> * Embora seja possível criar um novo bot da Estrutura de [Bot](https://dev.botframework.com/bots/new) sem usar o Azure, você deve usar essa URL ( , que não está mais exposta no https://dev.botframework.com/bots/new) portal do Bot Framework.
> * Ao editar as propriedades de um bot existente na lista de [seus bots](https://dev.botframework.com/bots) no Bot Framework, como seu "ponto de extremidade de mensagens", que é comum ao desenvolver um bot pela primeira vez, especialmente se você usar [o ngrok,](https://ngrok.com)você verá a coluna "Status da migração" e um botão azul "Migrar" que o levará para o portal do Microsoft Azure. Não clique no botão "Migrar", a menos que você queira fazer isso. em vez disso, clique no nome do bot e você pode editar suas propriedades:</br>
   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Se você registrar seu bot usando o Microsoft Azure, seu código de bot não precisará ser *hospedado* no Microsoft Azure.
> * Se você registrar um bot usando o portal do Microsoft Azure, é necessário ter uma conta do Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade ao criar um, você deve fornecer um cartão de crédito, mas ele não será cobrado; É sempre gratuito criar e usar bots com o Microsoft Teams.
> * Agora você pode usar o App Studio para registrar/atualizar informações de aplicativos e bots diretamente no Microsoft Teams. Você só terá que usar o portal do Microsoft Azure para adicionar/configurar outros canais da Estrutura de Bot, como Linha Direta, Chat da Web, Skype e Facebook Messenger.
