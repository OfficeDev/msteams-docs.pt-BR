---
title: Criar um bot
description: Descreve como criar bots em Microsoft Teams
ms.topic: how-to
keywords: criação de bots equipes
localization_priority: Normal
ms.date: 12/07/2018
ms.openlocfilehash: 67aa3e2cfd1950dced84785a9f6f35cfd4d5ff85
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566772"
---
# <a name="create-a-bot"></a>Criar um bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Todos os bots criados usando o Microsoft Bot Framework estão configurados e prontos para trabalhar em Microsoft Teams.

Para obter mais informações, consulte [a Documentação do Quadro de Bots](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) para obter informações gerais sobre bots.

## <a name="create-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

**Teams App Studio** é uma ferramenta que pode ajudar a criar seu bot e um pacote de aplicativos que faz referência ao seu bot. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Para obter mais informações, consulte [Getting started with Teams App Studio](~/concepts/build-and-test/app-studio-overview.md). As etapas que seguem assumem que você está configurando seu bot à mão e não usando **Teams App Studio**:

1. Crie o bot usando este link: https://dev.botframework.com/bots/new . **Lembre-se de adicionar o Microsoft Teams como um canal da lista de canais em destaque após criar seu bot.** Sinta-se à vontade para usar novamente o ID do aplicativo da Microsoft que você gerou, caso já tenha criado seu pacote/manifesto de aplicativos.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

> [!NOTE]
> Se você não deseja criar seu bot no Azure, você **deve** usar este link para criar um novo bot: https://dev.botframework.com/bots/new . Se você clicar no **Criar um bot** no portal Bot Framework, você [criará seu bot em Microsoft Azure](#bots-and-microsoft-azure) em vez disso.

2. Construa o bot usando o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet, o [Bot Framework SDK](https://github.com/microsoft/botframework-sdk)ou a [API do Conector de Bot](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).

3. Teste o bot usando o [Bot Framework Emulator](/bot-framework/debug-bots-emulator).

4. Implante o bot em um serviço de nuvem, como [Microsoft Azure](https://azure.microsoft.com/). Alternativamente, execute seu aplicativo localmente e use um serviço de tunelamento como [ngrok](https://ngrok.com) para expor um ponto final https:// para o seu bot, como `https://45az0eb1.ngrok.io/api/messages` .

> [!NOTE]
> ## <a name="bots-and-microsoft-azure"></a>Bots e Microsoft Azure
> A partir de dezembro de 2017, o portal Bot Framework é otimizado para o registro de bots em Microsoft Azure. Aqui estão algumas coisas que você precisa saber:
>
> * O canal do Microsoft Teams para bots registado no Azure é gratuito. As mensagens enviadas pelo canal Teams não contarão para as mensagens consumidas para o bot.
> * Embora seja possível [criar um novo bot Framework sem](https://dev.botframework.com/bots/new) usar o Azure, você deve usar essa URL ( , que não está mais exposta no portal Bot https://dev.botframework.com/bots/new) Framework.
> * Quando você edita as propriedades de um bot existente na [lista de seus bots no Bot Framework,](https://dev.botframework.com/bots) como seu "ponto final de mensagens", o que é comum ao desenvolver um bot pela primeira vez, especialmente se você usar [ngrok,](https://ngrok.com)você verá a coluna "Status de migração" e um botão azul "Migrate" que o levará ao portal Microsoft Azure. Não clique no botão "Migrar" a menos que seja isso que você quer fazer; em vez disso, clique no nome do bot e você pode editar suas propriedades:</br>
   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)
> * Se você registrar seu bot usando Microsoft Azure, seu código de bot não precisa ser *hospedado* em Microsoft Azure.
> * Se você registrar um bot usando o portal do Microsoft Azure, é necessário ter uma conta do Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade ao criar uma, você deve fornecer um cartão de crédito, mas ele não será cobrado; é sempre livre para criar e usar bots com Microsoft Teams.
> * Agora você pode usar o App Studio para registrar/atualizar informações do aplicativo e do bot diretamente dentro Microsoft Teams. Você só terá que usar o portal Microsoft Azure para adicionar ou configurar outros canais do Bot Framework, como Direct Line, Web Chat, Skype e Facebook Messenger.

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).