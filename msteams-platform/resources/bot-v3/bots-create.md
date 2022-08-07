---
title: Criar um bot
description: Neste módulo, saiba como criar bots usando o Microsoft Bot Framework e pronto para trabalhar no Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 12/07/2018
ms.openlocfilehash: 0f53f26c8cb54c1d21cbe305d3ea1d433bfb864b
ms.sourcegitcommit: fb0942afb8be32d92df282dec03fbb3b13f8f303
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2022
ms.locfileid: "67264166"
---
# <a name="create-a-bot"></a>Criar um bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Todos os bots criados usando o Microsoft Bot Framework estão configurados e prontos para funcionar no Microsoft Teams.

Para obter mais informações, consulte [a Documentação do Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) para obter informações gerais sobre bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

**O Teams App Studio** é uma ferramenta que pode ajudar a criar seu bot e um pacote de aplicativo que faz referência ao bot. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Para obter mais informações, consulte [Introdução ao Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). As etapas a seguir pressupõem que você esteja configurando seu bot manualmente e não usando o **Teams App Studio**:

1. Crie o bot usando o [Bot Framework](https://dev.botframework.com/bots/new). **Lembre-se de adicionar o Microsoft Teams como um canal da lista de canais em destaque após criar seu bot.** Sinta-se à vontade para usar novamente o ID do aplicativo da Microsoft que você gerou, caso já tenha criado seu pacote/manifesto de aplicativos.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Se você não quiser criar seu bot no Azure, **deverá usar esse** link para criar um novo bot: [o Bot Framework](https://dev.botframework.com/bots/new). Se você clicar em **Criar um bot** no portal do Bot Framework, criará seu [bot no Microsoft Azure](#bots-and-microsoft-azure) .

2. Crie o bot usando o [pacote NuGet Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , o  [SDK do Bot Framework](https://github.com/microsoft/botframework-sdk) ou a [API do Bot Connector](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Teste o bot usando o [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Implante o bot em um serviço de nuvem, como [o Microsoft Azure](https://azure.microsoft.com/). Como alternativa, execute seu aplicativo localmente e use um serviço de túnel como [o ngrok](https://ngrok.com) para expor um ponto de extremidade https:// para o bot, como `https://45az0eb1.ngrok.io/api/messages`.

> [!NOTE]
>
> ## <a name="bots-and-microsoft-azure"></a>Bots e Microsoft Azure
>
> A partir de dezembro de 2017, o portal do Bot Framework é otimizado para registrar bots no Microsoft Azure. Aqui estão algumas coisas que você precisa saber:
>
> * O canal do Microsoft Teams para bots registado no Azure é gratuito. As mensagens enviadas pelo canal do Teams não contarão para as mensagens consumidas para o bot.
> * Embora seja possível criar um bot [do Bot Framework](https://dev.botframework.com/bots/new) sem usar o Azure, você deve usar a criação de um [bot do Bot Framework](https://dev.botframework.com/bots/new), que não é mais exposto no portal do Bot Framework.
> * Ao editar as propriedades de um bot existente na lista de [bots no Bot Framework](https://dev.botframework.com/bots), como seu "ponto de extremidade de mensagens", que é comum ao desenvolver um bot pela primeira vez, especialmente se você usar [o ngrok](https://ngrok.com), você verá a coluna "Status da migração" e um botão azul "Migrar" que levará você para o Microsoft portal do Azure. Não clique no botão "Migrar", a menos que seja isso que você deseja fazer; em vez disso, clique no nome do bot e você pode editar suas propriedades:</br>
   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Se você registrar seu bot usando o Microsoft Azure, o código do bot não precisará ser *hospedado* no Microsoft Azure.
> * Se você registrar um bot usando portal do Azure, deverá ter uma conta do Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade ao criar uma, você deve fornecer um cartão de crédito, mas ele não será cobrado; É sempre gratuito criar e usar bots com o Teams.
> * Agora você pode usar o App Studio para registrar/atualizar informações do aplicativo e do bot diretamente no Teams. Você só precisará usar o portal do Azure para adicionar ou configurar outros canais do Bot Framework, como Direct Line, Webchat, Skype e Facebook Messenger.

> [!WARNING]
>
>* Se você estiver usando o App Studio, recomendamos que você tente o Portal do Desenvolvedor para configurar, distribuir e gerenciar seus aplicativos do Teams. O App Studio foi preterido em 01 de agosto de 2022.

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
