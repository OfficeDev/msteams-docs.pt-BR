---
title: Carregar seu aplicativo personalizado
description: Descreve como carregar seu aplicativo no Microsoft Teams
ms.topic: how-to
keywords: aplicativos de equipes carregar
ms.openlocfilehash: 2e7a21dc27fdfe824ecacebabbb61a3b99ae8e79
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014338"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="5e7c1-104">Carregar um pacote do aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5e7c1-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="5e7c1-105">Para testar sua experiência de aplicativo no Microsoft Teams, você precisa carregar seu aplicativo para o Teams.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="5e7c1-106">Carregar adiciona o aplicativo à equipe selecionada, e você e os membros da equipe podem interagir com ele, como os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-106">Uploading adds the app to the team you select, and you and your team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="5e7c1-107">Carregar um pacote atualizado para um aplicativo existente com um bot pode não mostrar alterações na guia quando visualizado por meio da janela conversas.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the Conversations window.</span></span> <span data-ttu-id="5e7c1-108">É melhor acessá-lo por meio do sub-sub-uso de aplicativos ou testar em um ambiente de teste limpo.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-108">It's better to access it via the Apps fly-out, or test on a clean test environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="5e7c1-109">Criar seu pacote de upload</span><span class="sxs-lookup"><span data-stu-id="5e7c1-109">Create your upload package</span></span>

<span data-ttu-id="5e7c1-110">Para o desenvolvimento, bem como o envio ao AppSource (antigo Office Store), você deve criar um pacote que pode ser carregado contendo as informações para descrever sua experiência.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-110">For development as well as AppSource (formerly Office Store) submission you must create an uploadable package that contains the information to describe your experience.</span></span> <span data-ttu-id="5e7c1-111">O pacote, um arquivo .zip, contém o manifesto do aplicativo e ícones que definem exclusivamente sua experiência.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-111">The package, a .zip file, contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="5e7c1-112">Para criar um pacote de upload, [confira Criar o pacote para o aplicativo Microsoft Teams.](../build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="5e7c1-112">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="5e7c1-113">Com o pacote criado, agora você pode carregar em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-113">With your package created, you can now upload it into a team.</span></span> <span data-ttu-id="5e7c1-114">Depois de carregado, ele estará disponível para todos os usuários na equipe selecionada e somente para os usuários dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-114">Once uploaded it will be available for all users in the selected team, and only the users of that team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="5e7c1-115">Carregar seu pacote no Teams</span><span class="sxs-lookup"><span data-stu-id="5e7c1-115">Load your package into Teams</span></span>

<span data-ttu-id="5e7c1-116">Você pode testar seu pacote carregando-o no Teams.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-116">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="5e7c1-117">Para que o carregamento funcione, o administrador do locatário deve primeiro [habilitar o carregamento de aplicativos.](/microsoftteams/admin-settings)</span><span class="sxs-lookup"><span data-stu-id="5e7c1-117">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="5e7c1-118">Há duas maneiras de carregar seu aplicativo no Teams:</span><span class="sxs-lookup"><span data-stu-id="5e7c1-118">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="5e7c1-119">Usando a Loja</span><span class="sxs-lookup"><span data-stu-id="5e7c1-119">Using the Store</span></span>
* <span data-ttu-id="5e7c1-120">Usando a guia Aplicativos</span><span class="sxs-lookup"><span data-stu-id="5e7c1-120">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="5e7c1-121">Carregar seu pacote em uma equipe ou conversa usando a Loja</span><span class="sxs-lookup"><span data-stu-id="5e7c1-121">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="5e7c1-122">No canto inferior esquerdo do Teams, escolha o ícone da Loja.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-122">In the lower left corner of Teams, choose the Store icon.</span></span> <span data-ttu-id="5e7c1-123">Na página da Loja, escolha "Carregar um aplicativo personalizado".</span><span class="sxs-lookup"><span data-stu-id="5e7c1-123">On the Store page, choose "Upload a custom app".</span></span>

  ![Exibir equipe](../../assets/images/store-upload-a-custom-app2.png)

2. <span data-ttu-id="5e7c1-125">Na caixa *de* diálogo Abrir, navegue até o pacote que você deseja carregar e escolha *Abrir.*</span><span class="sxs-lookup"><span data-stu-id="5e7c1-125">In the *Open* dialog, navigate to the package you want to upload and choose *Open*.</span></span>

   ![Menu Adicionar](../../assets/images/NewappAddmenudropdown.png)

<span data-ttu-id="5e7c1-127">O pacote carregado agora deve estar disponível para uso na equipe ou na conversa especificada na caixa de diálogo de consentimento.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-127">The uploaded package should now be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="5e7c1-128">Se seu aplicativo não aparecer, o motivo mais comum será um erro no manifesto, especialmente ids para o aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-128">If your app does not appear, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span> <span data-ttu-id="5e7c1-129">Se o aplicativo não tiver escopo para conversas, essa opção não será exibida.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-129">If the app is not scoped for conversations, that option will not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="5e7c1-130">Os aplicativos em conversas estão atualmente [na](../../resources/dev-preview/developer-preview-intro.md)Visualização do Desenvolvedor e a opção não aparecerá se o Teams não estiver sendo executado nesse modo.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-130">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option will not appear if Teams is not running in that mode.</span></span>

![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="5e7c1-132">Carregar seu pacote em uma equipe usando a guia Aplicativos</span><span class="sxs-lookup"><span data-stu-id="5e7c1-132">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="5e7c1-133">Na equipe de destino, escolha *Mais opções* (**&#8943;**) e escolha *Gerenciar equipe*.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-133">In the target team, choose *More options* (**&#8943;**) and choose *Manage team*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5e7c1-134">Você deve ser o proprietário da equipe ou o proprietário deve permitir que os usuários adicionem os tipos de aplicativo apropriados para que essa funcionalidade apareça.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-134">You must be the team owner, or the owner must allow users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="5e7c1-135">Selecione a guia Aplicativos e escolha *Carregar um aplicativo personalizado* no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-135">Select the Apps tab, and then choose *Upload a custom app* on the lower right.</span></span>

   ![Ponto de entrada de carregamento](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="5e7c1-137">Navegue até e selecione seu pacote .zip no computador.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-137">Browse to and select your .zip package from your computer.</span></span>

4. <span data-ttu-id="5e7c1-138">Após uma breve pausa, você verá seu aplicativo carregado na lista.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-138">After a brief pause you will see your uploaded app in the list.</span></span>

   ![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

<span data-ttu-id="5e7c1-140">Se o aplicativo não carregar, o motivo mais comum será um erro no manifesto, especialmente ids para o aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-140">If your app does not load, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span>

## <a name="accessing-your-uploaded-configurable-tab"></a><span data-ttu-id="5e7c1-141">Acessando sua guia configurável carregada</span><span class="sxs-lookup"><span data-stu-id="5e7c1-141">Accessing your uploaded configurable tab</span></span>

<span data-ttu-id="5e7c1-142">Se o aplicativo contiver guias, os usuários poderão fixá-las em qualquer conversa ou canal de equipe usando o fluxo da galeria de guias padrão:</span><span class="sxs-lookup"><span data-stu-id="5e7c1-142">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="5e7c1-143">Vá para um canal na equipe.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-143">Go to a channel in the team.</span></span> <span data-ttu-id="5e7c1-144">Escolha *+* ( Adicionar uma *guia*) à direita das guias existentes.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-144">Choose *+* (*Add a tab*) to the right of the existing tabs.</span></span>

2. <span data-ttu-id="5e7c1-145">Selecione sua guia na galeria exibida.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-145">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="5e7c1-146">Aceite a solicitação de consentimento.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-146">Accept the consent prompt.</span></span>

4. <span data-ttu-id="5e7c1-147">Configure sua guia por meio de sua página [de configuração](../../tabs/how-to/create-tab-pages/configuration-page.md) e escolha *Salvar*.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-147">Configure your tab via its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and choose *Save*.</span></span>

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a><span data-ttu-id="5e7c1-149">Acessando seu bot carregado</span><span class="sxs-lookup"><span data-stu-id="5e7c1-149">Accessing your uploaded bot</span></span>

<span data-ttu-id="5e7c1-150">Quando você adiciona um bot a uma equipe, ele deve ser disponibilizado por qualquer pessoa dessa equipe, dentro e fora dos canais de equipe, dependendo da definição de escopo do bot.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-150">When you add a bot to a team, it should be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="5e7c1-151">Você e outros membros da equipe verão uma postagem no canal Geral indicando que o bot foi adicionado à equipe.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-151">You and other team members will see a post in the General channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="5e7c1-152">Para um bot habilitado para equipes, você pode começar invocando seu bot @mentioning o nome do bot, que deve ser preenchimento automático.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-152">For a teams-enabled bot, you can start by invoking your bot by @mentioning the name of the bot, which should autocomplete.</span></span>

<span data-ttu-id="5e7c1-153">Para testar chats diretos com seu bot, você pode acessá-lo por meio da página de aplicativo, @mention-lo em um canal ou pesquisá-lo na janela Novo **Chat.**</span><span class="sxs-lookup"><span data-stu-id="5e7c1-153">To test direct chats with your bot, you can either access it via the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="5e7c1-154">Ao adicionar seu bot a uma conversa para testar chats diretos com seu bot, você pode @mention-lo em uma conversa ou pesquisá-lo na janela Novo **Chat.**</span><span class="sxs-lookup"><span data-stu-id="5e7c1-154">When you add your bot to a conversation To test direct chats with your bot, you can @mention it in a conversation, or search for it in the **New Chat** window.</span></span>

## <a name="accessing-your-uploaded-connector"></a><span data-ttu-id="5e7c1-155">Acessando seu Conector carregado</span><span class="sxs-lookup"><span data-stu-id="5e7c1-155">Accessing your uploaded Connector</span></span>

<span data-ttu-id="5e7c1-156">Com o aplicativo carregado na equipe ou na conversa, os usuários podem configurar um Conector usando o fluxo da galeria de Conectores padrão:</span><span class="sxs-lookup"><span data-stu-id="5e7c1-156">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="5e7c1-157">Vá para um canal na equipe.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-157">Go to a channel in the team.</span></span> <span data-ttu-id="5e7c1-158">Escolha *Mais opções* (*&#8943;*) e escolha *Conectores*.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-158">Choose *More options* (*&#8943;*) and choose *Connectors*.</span></span>

2. <span data-ttu-id="5e7c1-159">Selecione o Conector na **seção Sideload** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-159">Select your Connector from the **Sideloaded** section at the bottom.</span></span>

3. <span data-ttu-id="5e7c1-160">Configure seu Conector por meio de sua página [de configuração](../../webhooks-and-connectors/how-to/connectors-creating.md) e escolha *Salvar*.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-160">Configure your Connector via its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and choose *Save*.</span></span>

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a><span data-ttu-id="5e7c1-162">Acessando sua extensão de mensagens carregada</span><span class="sxs-lookup"><span data-stu-id="5e7c1-162">Accessing your uploaded messaging extension</span></span>

<span data-ttu-id="5e7c1-163">Um aplicativo carregado com uma extensão de mensagens aparece automaticamente no menu Mais opções *(* *&#8943;*) na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-163">An uploaded app with a messaging extension automatically appears in the *More options* (*&#8943;*) menu in the compose box.</span></span>

![Extensões de mensagens](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a><span data-ttu-id="5e7c1-165">Removendo ou atualizando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e7c1-165">Removing or updating your app</span></span>

<span data-ttu-id="5e7c1-166">Se você quiser remover seu aplicativo, selecione o ícone de lixeira ao lado do nome do aplicativo na lista de bots do View Teams.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-166">If you want to remove your app, select the trash-can icon next to the app name in the View Teams bots list.</span></span>

<span data-ttu-id="5e7c1-167">Se você alterar as informações do manifesto, primeiro remova o aplicativo e, em seguida, adicione o pacote atualizado (de acordo com o carregamento do [pacote em uma equipe).](#load-your-package-into-teams)</span><span class="sxs-lookup"><span data-stu-id="5e7c1-167">If you change manifest information, you must first remove the app and then add the updated package (per [Load your package into a team](#load-your-package-into-teams)).</span></span> <span data-ttu-id="5e7c1-168">Observe que, em geral, as alterações de código em seu serviço não exigem que você recarde o manifesto, a menos que essas alterações recarram as atualizações do manifesto (como alterações na URL ou na ID do aplicativo da Microsoft para seu bot).</span><span class="sxs-lookup"><span data-stu-id="5e7c1-168">Note that, in general, code changes on your service do not require you to re-upload your manifest, unless those changes require manifest updates (such as changes to the URL or the Microsoft app ID for its bot).</span></span>

> [!NOTE]
> <span data-ttu-id="5e7c1-169">Não há nenhuma maneira de remover completamente um bot do contexto pessoal.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-169">There is no way to completely remove a bot from personal context.</span></span> <span data-ttu-id="5e7c1-170">Se o bot for removido e adicionado outra vez, a comunicação adicional com o bot será acrescentada à conversa anterior.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-170">If the bot is removed and re-added, additional communication with the bot will append to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="5e7c1-171">Notas de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="5e7c1-171">Troubleshooting notes</span></span>

* <span data-ttu-id="5e7c1-172">Se o manifesto não carregar, verifique se você seguiu [](../../concepts/build-and-test/apps-package.md) todas as instruções em Criar o pacote e validou seu manifesto em relação [ao esquema.](../../resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="5e7c1-172">If the manifest doesn't load, please double-check that you followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>
