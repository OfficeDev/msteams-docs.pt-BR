---
title: Carregar seu aplicativo personalizado no Microsoft Teams
description: Descreve como carregar seu aplicativo no Microsoft Teams
keywords: Carregamento de aplicativos do teams
ms.openlocfilehash: 256a9bea48ed816f2e9912006dd2fe7301743919
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44453879"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="419d4-104">Carregar um pacote do aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="419d4-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="419d4-105">Para testar a experiência do aplicativo no Microsoft Teams, você precisa carregar seu aplicativo para o Teams.</span><span class="sxs-lookup"><span data-stu-id="419d4-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="419d4-106">O carregamento adiciona o aplicativo à equipe selecionada e você e os membros da equipe podem interagir com ele, como os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="419d4-106">Uploading adds the app to the team you select, and you and your team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="419d4-107">Carregar um pacote atualizado para um aplicativo existente com um bot pode não mostrar as alterações de tabulação quando visualizado por meio da janela conversas.</span><span class="sxs-lookup"><span data-stu-id="419d4-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the Conversations window.</span></span> <span data-ttu-id="419d4-108">É melhor acessá-lo por meio do surgimento dos aplicativos ou teste em um ambiente de teste limpo.</span><span class="sxs-lookup"><span data-stu-id="419d4-108">It's better to access it via the Apps fly-out, or test on a clean test environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="419d4-109">Criar seu pacote de carregamento</span><span class="sxs-lookup"><span data-stu-id="419d4-109">Create your upload package</span></span>

<span data-ttu-id="419d4-110">Para o desenvolvimento, bem como o envio do AppSource (anteriormente Office Store), você deve criar um pacote que contenha as informações para descrever sua experiência.</span><span class="sxs-lookup"><span data-stu-id="419d4-110">For development as well as AppSource (formerly Office Store) submission you must create an uploadable package that contains the information to describe your experience.</span></span> <span data-ttu-id="419d4-111">O pacote, um arquivo. zip, contém o manifesto do aplicativo e os ícones que definem exclusivamente sua experiência.</span><span class="sxs-lookup"><span data-stu-id="419d4-111">The package, a .zip file, contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="419d4-112">Para criar um pacote de carregamento, consulte [criar o pacote para seu aplicativo do Microsoft Teams](../build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="419d4-112">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="419d4-113">Com seu pacote criado, agora você pode carregá-lo em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="419d4-113">With your package created, you can now upload it into a team.</span></span> <span data-ttu-id="419d4-114">Depois de carregado, ele estará disponível para todos os usuários da equipe selecionada e apenas para os usuários dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="419d4-114">Once uploaded it will be available for all users in the selected team, and only the users of that team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="419d4-115">Carregar seu pacote no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="419d4-115">Load your package into Teams</span></span>

<span data-ttu-id="419d4-116">Você pode testar seu pacote carregando-o no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="419d4-116">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="419d4-117">Para que o carregamento funcione, o administrador de locatário deve primeiro [habilitar o carregamento de aplicativos](/microsoftteams/admin-settings).</span><span class="sxs-lookup"><span data-stu-id="419d4-117">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="419d4-118">Há duas maneiras de carregar seu aplicativo para o Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="419d4-118">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="419d4-119">Usando o repositório</span><span class="sxs-lookup"><span data-stu-id="419d4-119">Using the Store</span></span>
* <span data-ttu-id="419d4-120">Usando a guia aplicativos</span><span class="sxs-lookup"><span data-stu-id="419d4-120">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="419d4-121">Carregar seu pacote em uma equipe ou conversa usando a loja</span><span class="sxs-lookup"><span data-stu-id="419d4-121">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="419d4-122">No canto inferior esquerdo do Teams, escolha o ícone de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="419d4-122">In the lower left corner of Teams, choose the Store icon.</span></span> <span data-ttu-id="419d4-123">Na página loja, escolha "carregar um aplicativo personalizado".</span><span class="sxs-lookup"><span data-stu-id="419d4-123">On the Store page, choose "Upload a custom app".</span></span>

   ![Exibir equipe](../../assets/images/store-upload-a-custom-app.png)

2. <span data-ttu-id="419d4-125">Na caixa de diálogo *abrir* , navegue até o pacote que você deseja carregar e escolha *abrir*.</span><span class="sxs-lookup"><span data-stu-id="419d4-125">In the *Open* dialog, navigate to the package you want to upload and choose *Open*.</span></span>

<span data-ttu-id="419d4-126">O pacote carregado agora deve estar disponível para uso na equipe ou conversa especificada na caixa de diálogo de consentimento.</span><span class="sxs-lookup"><span data-stu-id="419d4-126">The uploaded package should now be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="419d4-127">Se seu aplicativo não aparecer, o motivo mais comum é um erro no manifesto, principalmente IDs para o aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="419d4-127">If your app does not appear, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span> <span data-ttu-id="419d4-128">Se o aplicativo não tiver escopo para conversas, essa opção não será exibida.</span><span class="sxs-lookup"><span data-stu-id="419d4-128">If the app is not scoped for conversations, that option will not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="419d4-129">Os aplicativos em conversas estão atualmente na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md)e a opção não será exibida se o Microsoft Teams não estiver em execução nesse modo.</span><span class="sxs-lookup"><span data-stu-id="419d4-129">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option will not appear if Teams is not running in that mode.</span></span>

![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="419d4-131">Carregar seu pacote em uma equipe usando a guia aplicativos</span><span class="sxs-lookup"><span data-stu-id="419d4-131">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="419d4-132">Na equipe de destino, escolha *mais opções* (**&#8943;**) e escolha *Gerenciar equipe*.</span><span class="sxs-lookup"><span data-stu-id="419d4-132">In the target team, choose *More options* (**&#8943;**) and choose *Manage team*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="419d4-133">Você deve ser o proprietário da equipe ou o proprietário deve permitir que os usuários adicionem os tipos de aplicativos apropriados para que essa funcionalidade seja exibida.</span><span class="sxs-lookup"><span data-stu-id="419d4-133">You must be the team owner, or the owner must allow users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="419d4-134">Selecione a guia aplicativos e, em seguida, escolha *carregar um aplicativo personalizado* no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="419d4-134">Select the Apps tab, and then choose *Upload a custom app* on the lower right.</span></span>

   ![Carregar ponto de entrada](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="419d4-136">Navegue até o pacote. zip e selecione-o em seu computador.</span><span class="sxs-lookup"><span data-stu-id="419d4-136">Browse to and select your .zip package from your computer.</span></span>

4. <span data-ttu-id="419d4-137">Após uma breve pausa, você verá seu aplicativo carregado na lista.</span><span class="sxs-lookup"><span data-stu-id="419d4-137">After a brief pause you will see your uploaded app in the list.</span></span>

   ![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

<span data-ttu-id="419d4-139">Se seu aplicativo não carregar, o motivo mais comum é um erro no manifesto, principalmente IDs para o aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="419d4-139">If your app does not load, the most common reason is an error in the manifest, particularly ids for the app, bot and messaging extensions.</span></span>

## <a name="accessing-your-uploaded-configurable-tab"></a><span data-ttu-id="419d4-140">Acessar a guia configurável do carregado</span><span class="sxs-lookup"><span data-stu-id="419d4-140">Accessing your uploaded configurable tab</span></span>

<span data-ttu-id="419d4-141">Se o aplicativo contiver guias, os usuários poderão fixá-los em qualquer conversa ou canal de equipe usando o fluxo da Galeria de guias padrão:</span><span class="sxs-lookup"><span data-stu-id="419d4-141">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="419d4-142">Vá para um canal da equipe.</span><span class="sxs-lookup"><span data-stu-id="419d4-142">Go to a channel in the team.</span></span> <span data-ttu-id="419d4-143">Escolha *+* (*Adicionar uma guia*) à direita das guias existentes.</span><span class="sxs-lookup"><span data-stu-id="419d4-143">Choose *+* (*Add a tab*) to the right of the existing tabs.</span></span>

2. <span data-ttu-id="419d4-144">Selecione sua guia na galeria que aparece.</span><span class="sxs-lookup"><span data-stu-id="419d4-144">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="419d4-145">Aceite o prompt de consentimento.</span><span class="sxs-lookup"><span data-stu-id="419d4-145">Accept the consent prompt.</span></span>

4. <span data-ttu-id="419d4-146">Configure sua guia por meio de sua [página de configuração](../../tabs/how-to/create-tab-pages/configuration-page.md) e escolha *salvar*.</span><span class="sxs-lookup"><span data-stu-id="419d4-146">Configure your tab via its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and choose *Save*.</span></span>

  ![A caixa de diálogo Adicionar uma guia, apresentando uma galeria de guias disponíveis](../../assets/images/tab_gallery.png)

## <a name="accessing-your-uploaded-bot"></a><span data-ttu-id="419d4-148">Acessar o bot carregado</span><span class="sxs-lookup"><span data-stu-id="419d4-148">Accessing your uploaded bot</span></span>

<span data-ttu-id="419d4-149">Quando você adiciona um bot a uma equipe, ele deve ser útil para qualquer pessoa nessa equipe, dentro e fora dos canais da equipe, dependendo da definição do escopo do bot.</span><span class="sxs-lookup"><span data-stu-id="419d4-149">When you add a bot to a team, it should be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="419d4-150">Você e outros membros da equipe verão uma postagem no canal geral indicando que o bot foi adicionado à equipe.</span><span class="sxs-lookup"><span data-stu-id="419d4-150">You and other team members will see a post in the General channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="419d4-151">Para um bot habilitado para o Microsoft Teams, você pode começar invocando o bot, @mentioning o nome do bot, que deve ser concluído.</span><span class="sxs-lookup"><span data-stu-id="419d4-151">For a teams-enabled bot, you can start by invoking your bot by @mentioning the name of the bot, which should autocomplete.</span></span>

<span data-ttu-id="419d4-152">Para testar chats diretos com o bot, você pode acessá-lo por meio da página inicial do aplicativo, @mention-lo em um canal ou procurá-lo na nova janela de **chat** .</span><span class="sxs-lookup"><span data-stu-id="419d4-152">To test direct chats with your bot, you can either access it via the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="419d4-153">Ao adicionar o bot a uma conversa para testar chats diretos com o bot, você pode @mention-lo em uma conversa ou procurá-lo na nova janela de **chat** .</span><span class="sxs-lookup"><span data-stu-id="419d4-153">When you add your bot to a conversation To test direct chats with your bot, you can @mention it in a conversation, or search for it in the **New Chat** window.</span></span>

## <a name="accessing-your-uploaded-connector"></a><span data-ttu-id="419d4-154">Acessando seu conector carregado</span><span class="sxs-lookup"><span data-stu-id="419d4-154">Accessing your uploaded Connector</span></span>

<span data-ttu-id="419d4-155">Com o aplicativo carregado na equipe ou na conversa, os usuários podem configurar um conector usando o fluxo da Galeria de conectores padrão:</span><span class="sxs-lookup"><span data-stu-id="419d4-155">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="419d4-156">Vá para um canal da equipe.</span><span class="sxs-lookup"><span data-stu-id="419d4-156">Go to a channel in the team.</span></span> <span data-ttu-id="419d4-157">Escolha *mais opções* (*&#8943;*) e escolha *conectores*.</span><span class="sxs-lookup"><span data-stu-id="419d4-157">Choose *More options* (*&#8943;*) and choose *Connectors*.</span></span>

2. <span data-ttu-id="419d4-158">Selecione seu conector na seção **carregado** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="419d4-158">Select your Connector from the **Uploaded** section at the bottom.</span></span>

3. <span data-ttu-id="419d4-159">Configure seu conector por meio de sua [página de configuração](../../webhooks-and-connectors/how-to/connectors-creating.md) e escolha *salvar*.</span><span class="sxs-lookup"><span data-stu-id="419d4-159">Configure your Connector via its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and choose *Save*.</span></span>

  ![A caixa de diálogo Adicionar uma guia, apresentando uma galeria de guias disponíveis.](../../assets/images/connector_gallery.png)

## <a name="accessing-your-uploaded-messaging-extension"></a><span data-ttu-id="419d4-161">Acessar sua extensão de mensagens carregadas</span><span class="sxs-lookup"><span data-stu-id="419d4-161">Accessing your uploaded messaging extension</span></span>

<span data-ttu-id="419d4-162">Um aplicativo carregado com uma extensão de mensagens aparece automaticamente no menu *mais opções* (*&#8943;*) na caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="419d4-162">An uploaded app with a messaging extension automatically appears in the *More options* (*&#8943;*) menu in the compose box.</span></span>

![Extensões de mensagens](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="removing-or-updating-your-app"></a><span data-ttu-id="419d4-164">Remover ou atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="419d4-164">Removing or updating your app</span></span>

<span data-ttu-id="419d4-165">Se você deseja remover o aplicativo, selecione o ícone Lixeira ao lado do nome do aplicativo na lista de bots do modo de exibição do teams.</span><span class="sxs-lookup"><span data-stu-id="419d4-165">If you want to remove your app, select the trash-can icon next to the app name in the View Teams bots list.</span></span>

<span data-ttu-id="419d4-166">Se você alterar as informações do manifesto, remova primeiro o aplicativo e, em seguida, adicione o pacote atualizado (por [carregar seu pacote em uma equipe](#load-your-package-into-teams)).</span><span class="sxs-lookup"><span data-stu-id="419d4-166">If you change manifest information, you must first remove the app and then add the updated package (per [Load your package into a team](#load-your-package-into-teams)).</span></span> <span data-ttu-id="419d4-167">Observe que, em geral, as alterações de código no serviço não exigem que você carregue novamente seu manifesto, a menos que essas alterações exijam atualizações de manifesto (como alterações na URL ou na ID do aplicativo da Microsoft para seu bot).</span><span class="sxs-lookup"><span data-stu-id="419d4-167">Note that, in general, code changes on your service do not require you to re-upload your manifest, unless those changes require manifest updates (such as changes to the URL or the Microsoft app ID for its bot).</span></span>

> [!NOTE]
> <span data-ttu-id="419d4-168">Não é possível remover completamente um bot do contexto pessoal.</span><span class="sxs-lookup"><span data-stu-id="419d4-168">There is no way to completely remove a bot from personal context.</span></span> <span data-ttu-id="419d4-169">Se o bot for removido e adicionado novamente, a comunicação adicional com o bot será acrescentada à conversa anterior.</span><span class="sxs-lookup"><span data-stu-id="419d4-169">If the bot is removed and re-added, additional communication with the bot will append to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="419d4-170">Notas de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="419d4-170">Troubleshooting notes</span></span>

* <span data-ttu-id="419d4-171">Se o manifesto não carregar, verifique se você seguiu todas as instruções em [criar o pacote](../../concepts/build-and-test/apps-package.md) e validou seu manifesto no [esquema](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="419d4-171">If the manifest doesn't load, please double-check that you followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>

