---
title: Criar um bot
description: Descreve como criar bots no Microsoft Teams
ms.topic: how-to
keywords: Criação de bots do teams
ms.localizationpriority: medium
ms.date: 12/07/2018
ms.openlocfilehash: 6898f6bf30c41cd5e373db323a0e5ce742129aa8
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453149"
---
# <a name="create-a-bot"></a>Criar um bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Todos os bots criados usando o Microsoft Bot Framework estão configurados e prontos para trabalhar em Microsoft Teams.

Para obter mais informações, consulte [Documentação da Estrutura de Bots](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) para obter informações gerais sobre bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

**Teams App Studio** é uma ferramenta que pode ajudar a criar seu bot e um pacote de aplicativos que faz referência ao bot. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Para obter mais informações, consulte [Getting started with Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). As etapas a seguir pressupom que você está configurando seu bot manualmente e não usando **Teams App Studio**:

1. Crie o bot usando [a Estrutura de Bot](https://dev.botframework.com/bots/new). **Lembre-se de adicionar o Microsoft Teams como um canal da lista de canais em destaque após criar seu bot.** Sinta-se à vontade para usar novamente o ID do aplicativo da Microsoft que você gerou, caso já tenha criado seu pacote/manifesto de aplicativos.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Se você não quiser criar seu bot no Azure, use este link  para criar um novo bot: [Bot Framework](https://dev.botframework.com/bots/new). Se você clicar no **portal Criar um bot** no Portal da Estrutura de Bots, você criará seu [bot Microsoft Azure](#bots-and-microsoft-azure) vez.

2. Crie o bot usando o [pacote Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet, o [SDK](https://github.com/microsoft/botframework-sdk) da Estrutura de Bot ou a [API do Conector de Bot](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Teste o bot usando o [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Implante o bot em um serviço de nuvem, como [Microsoft Azure](https://azure.microsoft.com/). Como alternativa, execute seu aplicativo localmente e use um serviço de túnel como [o ngrok](https://ngrok.com) para expor um ponto de extremidade https:// para seu bot, como `https://45az0eb1.ngrok.io/api/messages`.

> [!NOTE]
>
> ## <a name="bots-and-microsoft-azure"></a>Bots e Microsoft Azure
>
> A partir de dezembro de 2017, o portal da Estrutura de Bots é otimizado para registrar bots em Microsoft Azure. Aqui estão algumas coisas que você precisa saber:
>
> * O canal do Microsoft Teams para bots registado no Azure é gratuito. As mensagens enviadas pelo canal Teams não contarão para as mensagens consumidas para o bot.
> * Embora seja possível criar um novo [bot](https://dev.botframework.com/bots/new) da Estrutura de Bot sem usar o Azure, você deve usar a criação de um novo [bot da Estrutura](https://dev.botframework.com/bots/new) de Bots, que não está mais exposto no portal da Estrutura de Bots.
> * Quando você edita as propriedades de um bot existente na lista de seus [bots no Bot Framework](https://dev.botframework.com/bots), como seu "ponto de extremidade de mensagens", que é comum ao desenvolver um bot pela primeira vez, especialmente se você usar [o ngrok](https://ngrok.com), você verá a coluna "Status de migração" e um botão azul "Migrar" que o levará para o portal Microsoft Azure. Não clique no botão "Migrar", a menos que seja isso que você deseja fazer; em vez disso, clique no nome do bot e você pode editar suas propriedades:</br>
   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Se você registrar seu bot usando Microsoft Azure, seu código de bot não precisará ser *hospedado no Microsoft Azure*.
> * Se você registrar um bot usando o portal do Azure, deverá ter uma conta Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade ao criar uma, você deve fornecer um cartão de crédito, mas ele não será cobrado; é sempre gratuito criar e usar bots com Microsoft Teams.
> * Agora você pode usar o App Studio para registrar/atualizar informações de aplicativo e bot diretamente no Microsoft Teams. Você só terá que usar o portal do Azure para adicionar ou configurar outros canais da Estrutura de Bot, como Linha Direta, Web Chat, Skype e Facebook Messenger.

## <a name="see-also"></a>Confira também

[Exemplos da Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
