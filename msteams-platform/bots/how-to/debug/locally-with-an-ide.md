---
title: Testar e depurar seu bot localmente
author: clearab
description: Testando e depurando seu bot localmente com um IDE
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 52676d35599560704e5bb72d85e09860174fdaf1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058373"
---
# <a name="test-and-debug-your-bot-locally"></a><span data-ttu-id="40df1-103">Testar e depurar seu bot localmente</span><span class="sxs-lookup"><span data-stu-id="40df1-103">Test and debug your bot locally</span></span>

<span data-ttu-id="40df1-104">Ao testar seu bot, você precisa levar em consideração os contextos em que deseja que seu bot seja executado e qualquer funcionalidade que você possa ter adicionado ao bot que exija dados específicos do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-104">When testing your bot you need to take into consideration both the contexts you want your bot to run in, and any functionality you may have added to your bot that requires data specific to Microsoft Teams.</span></span> <span data-ttu-id="40df1-105">Certifique-se de que o método escolhido para testar seu bot se alinhe com sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="40df1-105">Make sure that the method you choose to test your bot aligns with its functionality.</span></span>

## <a name="test-by-uploading-to-teams"></a><span data-ttu-id="40df1-106">Testar carregando no Teams</span><span class="sxs-lookup"><span data-stu-id="40df1-106">Test by uploading to Teams</span></span>

<span data-ttu-id="40df1-107">A maneira mais abrangente de testar seu bot é criando um pacote de aplicativos e carregando-o no Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-107">The most comprehensive way to test your bot is by creating an app package and uploading it to Teams.</span></span> <span data-ttu-id="40df1-108">Este é o único método para testar a funcionalidade completa disponível para o bot, em todos os escopos.</span><span class="sxs-lookup"><span data-stu-id="40df1-108">This is the only method to test the full functionality available to your bot, across all scopes.</span></span>

<span data-ttu-id="40df1-109">Há dois métodos para carregar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="40df1-109">There are two methods for uploading your app:</span></span>
* <span data-ttu-id="40df1-110">Use [o App Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40df1-110">Use [App Studio](~/concepts/build-and-test/app-studio-overview.md).</span></span>
* <span data-ttu-id="40df1-111">[Crie um pacote de aplicativo](~/concepts/build-and-test/apps-package.md) manualmente e carregue seu [aplicativo](~/concepts/deploy-and-publish/apps-upload.md).</span><span class="sxs-lookup"><span data-stu-id="40df1-111">[Create an app package](~/concepts/build-and-test/apps-package.md) manually, and then [upload your app](~/concepts/deploy-and-publish/apps-upload.md).</span></span>

> [!NOTE]
> <span data-ttu-id="40df1-112">Se você precisar alterar seu manifesto e carregar seu aplicativo de novo, [exclua](#delete-a-bot-from-teams) seu bot antes de carregar seu pacote de aplicativo alterado.</span><span class="sxs-lookup"><span data-stu-id="40df1-112">If you need to alter your manifest and re-upload your app, you must [delete your bot](#delete-a-bot-from-teams) before uploading your altered app package.</span></span>

## <a name="debug-your-bot-locally"></a><span data-ttu-id="40df1-113">Depurar seu bot localmente</span><span class="sxs-lookup"><span data-stu-id="40df1-113">Debug your bot locally</span></span>

<span data-ttu-id="40df1-114">Se você estiver hospedando seu bot localmente durante o desenvolvimento, precisará usar um serviço de túnel como [o ngrok](https://ngrok.com/) para testar seu bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-114">If you are hosting your bot locally during development, you need to use a tunneling service like [ngrok](https://ngrok.com/) in order to test your bot.</span></span> <span data-ttu-id="40df1-115">Depois de baixar e instalar o ngrok, adicione ao seu caminho e execute o seguinte comando `ngrok` para iniciar o serviço de túnel:</span><span class="sxs-lookup"><span data-stu-id="40df1-115">After you download and install ngrok, add `ngrok` to your path, and run the following command to start the tunneling service:</span></span>

```bash
ngrok http <port> -host-header=localhost:<port>
```

<span data-ttu-id="40df1-116">Use o ponto de extremidade https fornecido pelo ngrok no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40df1-116">Use the https endpoint provided by ngrok in your app manifest.</span></span> 

> [!NOTE]
> <span data-ttu-id="40df1-117">Se você fechar a janela de comando e reiniciar, uma nova URL será gerada e você precisará atualizar seu endereço de ponto de extremidade do bot para usá-la.</span><span class="sxs-lookup"><span data-stu-id="40df1-117">If you close your command window and restart, a new URL is generated and you need to update your bot endpoint address to use it.</span></span>

## <a name="test-your-bot-without-uploading-to-teams"></a><span data-ttu-id="40df1-118">Testar seu bot sem carregar no Teams</span><span class="sxs-lookup"><span data-stu-id="40df1-118">Test your bot without uploading to Teams</span></span>

<span data-ttu-id="40df1-119">Ocasionalmente, pode ser necessário testar seu bot sem instalá-lo como um aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-119">Occasionally, it may be necessary to test your bot without installing it as an app in Teams.</span></span> <span data-ttu-id="40df1-120">Fornecemos dois métodos para testar o bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-120">We provide two methods for testing the bot.</span></span> <span data-ttu-id="40df1-121">Testar seu bot sem instalá-lo como aplicativo pode ser útil para garantir que o bot está disponível e respondendo, no entanto, ele não permitirá que você teste a amplitude completa da funcionalidade do Microsoft Teams que você pode ter adicionado ao bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-121">Testing your bot without installing it as an app can be useful to ensure your bot is available and responding, however it won't allow you to test the full breadth of Microsoft Teams functionality you may have added to your bot.</span></span> <span data-ttu-id="40df1-122">Se você precisar testar totalmente seu bot, consulte [testando carregando](#test-by-uploading-to-teams).</span><span class="sxs-lookup"><span data-stu-id="40df1-122">If you need to fully test your bot, see [testing by uploading](#test-by-uploading-to-teams).</span></span>

### <a name="use-the-bot-emulator"></a><span data-ttu-id="40df1-123">Usar o Emulador de Bot</span><span class="sxs-lookup"><span data-stu-id="40df1-123">Use the Bot Emulator</span></span>

<span data-ttu-id="40df1-124">O Emulador da Estrutura de Bots é um aplicativo de área de trabalho que permite que os desenvolvedores de bots testem e depurem seus bots localmente ou remotamente.</span><span class="sxs-lookup"><span data-stu-id="40df1-124">The Bot Framework Emulator is a desktop application that permits bot developers to test and debug their bots locally or remotely.</span></span> <span data-ttu-id="40df1-125">O emulador ajuda você a conversar com seu bot e inspecionar as mensagens que seu bot envia e recebe.</span><span class="sxs-lookup"><span data-stu-id="40df1-125">The emulator helps you to chat with your bot and inspect the messages that your bot sends and receives.</span></span> <span data-ttu-id="40df1-126">Isso pode ser útil para verificar se o bot está disponível e respondendo.</span><span class="sxs-lookup"><span data-stu-id="40df1-126">This can be useful for verifying that your bot is available and responding.</span></span> <span data-ttu-id="40df1-127">No entanto, o emulador não permite que você teste nenhuma funcionalidade específica do Teams adicionada ao bot, nem as respostas do bot são uma representação visual precisa de como elas são renderizadas no Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-127">However, the emulator does not permit you to test any Teams-specific functionality you have added to the bot, nor the responses from your bot are an accurate visual representation of how they are rendered in Teams.</span></span> <span data-ttu-id="40df1-128">Se você precisar testar qualquer uma dessas coisas, é melhor [carregar seu bot](#test-by-uploading-to-teams).</span><span class="sxs-lookup"><span data-stu-id="40df1-128">If you need to test either of those things it is best to [upload your bot](#test-by-uploading-to-teams).</span></span>

<span data-ttu-id="40df1-129">Para obter mais informações, [consulte instruções completas sobre o Emulador](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true)da Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="40df1-129">For more information, see [complete instructions on the Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).</span></span>

### <a name="talk-to-your-bot-directly-by-id"></a><span data-ttu-id="40df1-130">Fale com seu bot diretamente por ID</span><span class="sxs-lookup"><span data-stu-id="40df1-130">Talk to your bot directly by ID</span></span>

> [!Important]
> <span data-ttu-id="40df1-131">Conversar com seu bot por ID destina-se apenas a fins de teste básicos.</span><span class="sxs-lookup"><span data-stu-id="40df1-131">Talking to your bot by ID is intended for basic testing purposes only.</span></span> <span data-ttu-id="40df1-132">Qualquer funcionalidade específica do Teams adicionada ao bot não funciona.</span><span class="sxs-lookup"><span data-stu-id="40df1-132">Any Teams-specific functionality you have added to your bot fails to work.</span></span>

<span data-ttu-id="40df1-133">Você também pode iniciar uma conversa com seu bot usando sua ID.</span><span class="sxs-lookup"><span data-stu-id="40df1-133">You can also initiate a conversation with your bot by using its ID.</span></span> <span data-ttu-id="40df1-134">Quando um bot é adicionado por meio de um desses métodos, ele não pode ser abordada em conversas de canal e você não pode tirar proveito de outros recursos de aplicativo do Microsoft Teams, como guias ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="40df1-134">When a bot has been added through one of these methods it is not addressable in channel conversations and you cannot take advantage of other Microsoft Teams app capabilities like tabs or messaging extensions.</span></span> <span data-ttu-id="40df1-135">Você pode iniciar uma conversa de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="40df1-135">You can initiate a conversation in one of the following ways:</span></span>

* <span data-ttu-id="40df1-136">Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Canais,** selecione **Adicionar ao Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="40df1-136">On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Channels**, select **Add to Microsoft Teams**.</span></span> <span data-ttu-id="40df1-137">O Microsoft Teams inicia um chat pessoal com seu bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-137">Microsoft Teams launches a personal chat with your bot.</span></span>

* <span data-ttu-id="40df1-138">Fazer referência direta à ID do aplicativo do bot de dentro do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="40df1-138">Directly reference your bot's app ID from within Microsoft Teams:</span></span>
   1. <span data-ttu-id="40df1-139">Na página [Painel de Bot](https://dev.botframework.com/bots) para seu bot, em **Detalhes**, copie a **ID** do Aplicativo microsoft para seu bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-139">On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Details**, copy the **Microsoft App ID** for your bot.</span></span>
  
      ![Obter o AppID para o bot](~/assets/images/bots_appid_botframework.png)
  
   2. <span data-ttu-id="40df1-141">Abra o Microsoft Teams, no painel **Chat,** selecione o **ícone Adicionar chat.**</span><span class="sxs-lookup"><span data-stu-id="40df1-141">Open Microsoft Teams, on the **Chat** pane, select the **Add chat** icon.</span></span> <span data-ttu-id="40df1-142">Em **Para:**, colar a ID do aplicativo Microsoft do seu bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-142">In **To:**, paste your bot's Microsoft App ID.</span></span>
  
      ![Carregando bots](~/assets/images/bots_uploading.png)

      <span data-ttu-id="40df1-144">A ID do aplicativo deve ser resolvida com o nome do bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-144">The app ID must resolve to your bot name.</span></span>

   3. <span data-ttu-id="40df1-145">Selecione seu bot e envie uma mensagem para iniciar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="40df1-145">Select your bot and send a message to initiate a conversation.</span></span>
      <span data-ttu-id="40df1-146">Como alternativa, você pode colar a ID do aplicativo do bot na caixa de pesquisa na parte superior esquerda do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-146">Alternatively, you can paste your bot's app ID in the search box in the top left in Microsoft Teams.</span></span> <span data-ttu-id="40df1-147">Na página resultados da pesquisa, navegue até a guia **Pessoas** para ver seu bot e começar a conversar com ele.</span><span class="sxs-lookup"><span data-stu-id="40df1-147">In the search results page, navigate to the **People** tab to see your bot and to start chatting with it.</span></span>

<span data-ttu-id="40df1-148">Seu bot recebe o `conversationUpdate` evento à medida que você adiciona os bots a uma equipe, sem as informações da equipe no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="40df1-148">Your bot receives the `conversationUpdate` event as you add the bots to a team, without the team information in the `channelData` object.</span></span>

## <a name="block-a-bot-in-personal-chat"></a><span data-ttu-id="40df1-149">Bloquear um bot no chat pessoal</span><span class="sxs-lookup"><span data-stu-id="40df1-149">Block a bot in personal chat</span></span>

<span data-ttu-id="40df1-150">Os usuários podem optar por impedir que seu bot envie mensagens de chat pessoais.</span><span class="sxs-lookup"><span data-stu-id="40df1-150">Users can choose to block your bot from sending personal chat messages.</span></span> <span data-ttu-id="40df1-151">Eles podem alternar isso clicando com o botão direito do mouse no bot no canal de chat e escolhendo **Bloquear conversa bot**.</span><span class="sxs-lookup"><span data-stu-id="40df1-151">They may toggle this by right-clicking your bot in the chat channel and choosing **Block bot conversation**.</span></span> <span data-ttu-id="40df1-152">Isso significa que seus bots continuam a enviar mensagens, no entanto, o usuário não recebe as mensagens.</span><span class="sxs-lookup"><span data-stu-id="40df1-152">This means, your bots continues to send messages, however, the user does not receive the messages.</span></span>

![Bloqueando um bot](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a><span data-ttu-id="40df1-154">Remover um bot de uma equipe</span><span class="sxs-lookup"><span data-stu-id="40df1-154">Remove a bot from a team</span></span>

<span data-ttu-id="40df1-155">Os usuários podem excluir o bot escolhendo o ícone de lixeira na lista de bots no ponto de vista da equipe.</span><span class="sxs-lookup"><span data-stu-id="40df1-155">Users can delete the bot by choosing the trash-can icon on the bots list in their team's view.</span></span> <span data-ttu-id="40df1-156">Isso remove apenas o bot do uso dessa equipe, os usuários individuais ainda podem interagir no contexto pessoal.</span><span class="sxs-lookup"><span data-stu-id="40df1-156">This only removes the bot from that team's use, individual users can still interact in personal context.</span></span> <span data-ttu-id="40df1-157">Os bots no contexto pessoal não podem ser desabilitados ou removidos pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="40df1-157">Bots in personal context cannot be disabled or removed by users.</span></span>

## <a name="disable-a-bot-in-teams"></a><span data-ttu-id="40df1-158">Desabilitar um bot no Teams</span><span class="sxs-lookup"><span data-stu-id="40df1-158">Disable a bot in Teams</span></span>

<span data-ttu-id="40df1-159">Para impedir que seu bot receba mensagens, vá para o Painel de **Bot e** edite o canal do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-159">To stop your bot from receiving messages, go to your **Bot Dashboard** and edit the Microsoft Teams channel.</span></span> <span data-ttu-id="40df1-160">Des limpar **a opção Habilitar no Microsoft Teams.**</span><span class="sxs-lookup"><span data-stu-id="40df1-160">Clear the **Enable on Microsoft Teams** option.</span></span> <span data-ttu-id="40df1-161">Isso impede que os usuários interajam com o bot, no entanto, ele ainda será descoberto e os usuários ainda poderão adicioná-lo ao Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-161">This prevents users from interacting with the bot, however, it will still be discoverable and users will still be able to add it to Teams.</span></span>

## <a name="delete-a-bot-from-teams"></a><span data-ttu-id="40df1-162">Excluir um bot do Teams</span><span class="sxs-lookup"><span data-stu-id="40df1-162">Delete a bot from Teams</span></span>

<span data-ttu-id="40df1-163">Para remover completamente o bot do Teams, vá até seu Painel de **Bot e** edite o canal do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="40df1-163">To remove your bot completely from Teams, go to your **Bot Dashboard** and edit the Microsoft Teams channel.</span></span> <span data-ttu-id="40df1-164">Escolha o **botão Excluir** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="40df1-164">Choose the **Delete** button at the bottom.</span></span> <span data-ttu-id="40df1-165">Isso impede que os usuários descubram, adicionem e interajam com seu bot.</span><span class="sxs-lookup"><span data-stu-id="40df1-165">This prevents users from discovering, adding, and interacting with your bot.</span></span> <span data-ttu-id="40df1-166">Isso não remove o bot das instâncias do Teams de outros usuários, no entanto, ele também deixa de funcionar para eles.</span><span class="sxs-lookup"><span data-stu-id="40df1-166">This does not remove the bot from other user's Teams instances, however, it stops functioning for them as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="40df1-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="40df1-167">See also</span></span>

- [<span data-ttu-id="40df1-168">Depurar o bot com o middleware de inspeção</span><span class="sxs-lookup"><span data-stu-id="40df1-168">Debug your bot with inspection middleware</span></span>](/azure/bot-service/bot-service-debug-inspection-middleware)

- [<span data-ttu-id="40df1-169">Depurar seus chamados e o bot de reunião localmente</span><span class="sxs-lookup"><span data-stu-id="40df1-169">Debug your calling and meeting bot locally</span></span>](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
