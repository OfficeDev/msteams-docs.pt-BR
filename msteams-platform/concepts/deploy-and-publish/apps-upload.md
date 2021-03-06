---
title: Carregar seu aplicativo personalizado
description: Descreve como carregar seu aplicativo no Microsoft Teams
ms.topic: how-to
ms.author: lajanuar
keywords: carregamento de aplicativos do teams
ms.openlocfilehash: 3ca086cf8dbb992de84b22b7499f739d7c80b9d6
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479876"
---
# <a name="upload-an-app-package-to-microsoft-teams"></a><span data-ttu-id="f5bd8-104">Carregar um pacote do aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f5bd8-104">Upload an app package to Microsoft Teams</span></span>

<span data-ttu-id="f5bd8-105">Para testar sua experiência de aplicativo no Microsoft Teams, você precisa carregar seu aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-105">To test your app experience within Microsoft Teams, you need to upload your app to Teams.</span></span> <span data-ttu-id="f5bd8-106">O carregamento adiciona o aplicativo à equipe selecionada e todos os membros da equipe podem interagir com ele como usuários finais.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-106">Uploading adds the app to the selected team and all the team members can interact with it like end users.</span></span>

> [!NOTE]
> <span data-ttu-id="f5bd8-107">Carregar um pacote atualizado para um aplicativo existente com um bot pode não mostrar alterações na guia quando exibido pela janela de conversas.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-107">Uploading an updated package for an existing app with a bot might not show tab changes when viewed through the conversations window.</span></span> <span data-ttu-id="f5bd8-108">Você pode acessar o aplicativo por meio do sub-uso ou teste de aplicativos em um ambiente limpo.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-108">You can access the app through the apps fly-out or test in a clean environment.</span></span>

## <a name="create-your-upload-package"></a><span data-ttu-id="f5bd8-109">Criar seu pacote de carregamento</span><span class="sxs-lookup"><span data-stu-id="f5bd8-109">Create your upload package</span></span>

<span data-ttu-id="f5bd8-110">Para desenvolvimento e envio do AppSource, você deve criar um pacote que você pode carregar.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-110">For development and AppSource submission, you must create a package that you can upload.</span></span> <span data-ttu-id="f5bd8-111">O pacote deve conter as informações para descrever sua experiência.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-111">The package must contain the information to describe your experience.</span></span> <span data-ttu-id="f5bd8-112">O pacote é um arquivo .zip que contém o manifesto do aplicativo e ícones que definem sua experiência com exclusividade.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-112">The package is a .zip file that contains the application manifest and icons that uniquely define your experience.</span></span>

<span data-ttu-id="f5bd8-113">Para criar um pacote de carregamento, consulte [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="f5bd8-113">To create an upload package, see [Create the package for your Microsoft Teams app](../build-and-test/apps-package.md).</span></span>

<span data-ttu-id="f5bd8-114">Depois de criar o pacote, carregue-o em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-114">After you create the package, upload it into a team.</span></span> <span data-ttu-id="f5bd8-115">O pacote carregado só está disponível para os usuários da equipe selecionada.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-115">The uploaded package is only available to the users of the selected team.</span></span>

## <a name="load-your-package-into-teams"></a><span data-ttu-id="f5bd8-116">Carregar seu pacote no Teams</span><span class="sxs-lookup"><span data-stu-id="f5bd8-116">Load your package into Teams</span></span>

<span data-ttu-id="f5bd8-117">Você pode testar seu pacote carregando-o no Teams.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-117">You can test your package by uploading it into Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="f5bd8-118">Para carregar para funcionar, o administrador do locatário deve primeiro [habilitar o carregamento de aplicativos.](/microsoftteams/admin-settings)</span><span class="sxs-lookup"><span data-stu-id="f5bd8-118">For uploading to work, your tenant admin must first [enable uploading of apps](/microsoftteams/admin-settings).</span></span>

<span data-ttu-id="f5bd8-119">Há duas maneiras de carregar seu aplicativo no Teams:</span><span class="sxs-lookup"><span data-stu-id="f5bd8-119">There are two ways to upload your app to Teams:</span></span>

* <span data-ttu-id="f5bd8-120">Usando a Loja</span><span class="sxs-lookup"><span data-stu-id="f5bd8-120">Using the Store</span></span>
* <span data-ttu-id="f5bd8-121">Usando a guia Aplicativos</span><span class="sxs-lookup"><span data-stu-id="f5bd8-121">Using the Apps tab</span></span>

## <a name="upload-your-package-into-a-team-or-conversation-using-the-store"></a><span data-ttu-id="f5bd8-122">Carregar seu pacote em uma equipe ou conversa usando a Loja</span><span class="sxs-lookup"><span data-stu-id="f5bd8-122">Upload your package into a team or conversation using the Store</span></span>

1. <span data-ttu-id="f5bd8-123">No canto inferior esquerdo do Teams, escolha o **ícone da** Loja.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-123">In the lower left corner of Teams, choose the **Store** icon.</span></span> <span data-ttu-id="f5bd8-124">Na página Da Loja, escolha **Carregar um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="f5bd8-124">On the Store page, choose **Upload a custom app**.</span></span>

  ![Exibir equipe](../../assets/images/store-upload-a-custom-app2.png)

2. <span data-ttu-id="f5bd8-126">Na caixa **de diálogo Abrir,** navegue até o pacote que você deseja carregar e escolha Abrir.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-126">In the **Open** dialog, navigate to the package you want to upload and choose Open.</span></span>

   ![Adicionar menu](../../assets/images/NewappAddmenudropdown.png)

<span data-ttu-id="f5bd8-128">O pacote carregado deve estar disponível para uso na equipe ou na conversa especificada na caixa de diálogo de consentimento.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-128">The uploaded package must be available for use in the team or conversation specified in the consent dialog.</span></span> <span data-ttu-id="f5bd8-129">Se seu aplicativo não aparecer, o motivo mais comum será um erro no manifesto, especialmente as IDs do aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-129">If your app does not appear, the most common reason is an error in the manifest, particularly IDs for the app, bot, and messaging extensions.</span></span> <span data-ttu-id="f5bd8-130">Se o aplicativo não tiver escopo para conversas, essa opção não aparecerá.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-130">If the app is not scoped for conversations that option does not appear.</span></span>

>[!NOTE]
> <span data-ttu-id="f5bd8-131">Os aplicativos em conversas estão atualmente [na](../../resources/dev-preview/developer-preview-intro.md)Visualização do Desenvolvedor e a opção não aparece se o Teams não estiver sendo executado nesse modo.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-131">Apps in conversations is currently in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md), and the option does not appear if Teams is not running in that mode.</span></span>

![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

## <a name="upload-your-package-into-a-team-using-the-apps-tab"></a><span data-ttu-id="f5bd8-133">Carregar seu pacote em uma equipe usando a guia Aplicativos</span><span class="sxs-lookup"><span data-stu-id="f5bd8-133">Upload your package into a team using the Apps tab</span></span>

1. <span data-ttu-id="f5bd8-134">Na equipe de destino, escolha **Mais opções** (**&#8943;**) e selecione **Gerenciar equipe**.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-134">In the target team, choose **More options** (**&#8943;**) and select **Manage team**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f5bd8-135">Você deve ser o proprietário da equipe ou o proprietário deve dar acesso aos usuários para adicionar os tipos de aplicativo apropriados para que essa funcionalidade apareça.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-135">You must be the team owner or the owner must give access to users to add the appropriate app types for this functionality to appear.</span></span>

2. <span data-ttu-id="f5bd8-136">Selecione a **guia Aplicativos** e escolha **Carregar um aplicativo personalizado** no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-136">Select the **Apps** tab and choose **Upload a custom app** on the lower right.</span></span>

   ![Ponto de entrada de carregamento](../../assets/images/UploadACustomApp.png)

3. <span data-ttu-id="f5bd8-138">Selecione seu pacote .zip no computador.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-138">Select your .zip package from the computer.</span></span>

4. <span data-ttu-id="f5bd8-139">Você pode ver seu aplicativo carregado na lista.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-139">You can see your uploaded app in the list.</span></span>

   ![Exemplo de bot na lista de bots carregados](../../assets/images/botinlist.jpg)

<span data-ttu-id="f5bd8-141">Se o aplicativo não for carregado, o motivo mais comum será um erro no manifesto, especialmente as IDs do aplicativo, bot e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-141">If your app does not load, the most common reason is an error in the manifest, particularly IDs for the app, bot, and messaging extensions.</span></span>

## <a name="access-your-uploaded-configurable-tab"></a><span data-ttu-id="f5bd8-142">Acessar sua guia configurável carregada</span><span class="sxs-lookup"><span data-stu-id="f5bd8-142">Access your uploaded configurable tab</span></span>

<span data-ttu-id="f5bd8-143">Se o aplicativo contiver guias, os usuários poderão fixá-las em qualquer conversa ou canal de equipe usando o fluxo de galeria de guias padrão:</span><span class="sxs-lookup"><span data-stu-id="f5bd8-143">If the app contains tabs, users can pin them to any conversation or team channel using the standard tab gallery flow:</span></span>

1. <span data-ttu-id="f5bd8-144">Vá para um canal na equipe.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-144">Go to a channel in the team.</span></span> <span data-ttu-id="f5bd8-145">Escolha **+** adicionar uma guia à direita das guias existentes.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-145">Choose **+** to add a tab to the right of the existing tabs.</span></span>

2. <span data-ttu-id="f5bd8-146">Selecione sua guia na galeria exibida.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-146">Select your tab from the gallery that appears.</span></span>

3. <span data-ttu-id="f5bd8-147">Aceite o prompt de consentimento.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-147">Accept the consent prompt.</span></span>

4. <span data-ttu-id="f5bd8-148">Configure sua guia por meio de sua [página de configuração](../../tabs/how-to/create-tab-pages/configuration-page.md) e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-148">Configure your tab through its [configuration page](../../tabs/how-to/create-tab-pages/configuration-page.md) and select **Save**.</span></span>

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis](../../assets/images/tab_gallery.png)

## <a name="access-your-uploaded-bot"></a><span data-ttu-id="f5bd8-150">Acessar seu bot carregado</span><span class="sxs-lookup"><span data-stu-id="f5bd8-150">Access your uploaded bot</span></span>

<span data-ttu-id="f5bd8-151">Depois de adicionar o bot a uma equipe, ele deve ser usável por qualquer pessoa nessa equipe, dentro e fora dos canais de equipe, dependendo da definição do escopo do bot.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-151">After adding the bot to a team, it must be usable by anyone on that team, inside and outside the team channels, depending on bot scope definition.</span></span> <span data-ttu-id="f5bd8-152">Todos os membros da equipe podem ver uma postagem no **canal Geral** indicando que o bot foi adicionado à equipe.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-152">All team members can see a post in the **General** channel indicating that the bot has been added to the team.</span></span>

<span data-ttu-id="f5bd8-153">Para um bot do Teams, você pode começar invocando seu bot @mentioning o nome do bot.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-153">For a Teams bot, you can start by invoking your bot by @mentioning the name of the bot.</span></span>

<span data-ttu-id="f5bd8-154">Para testar chats diretos com seu bot, você pode acessá-lo por meio da página @mention app em um canal ou pesquisá-lo na janela **Novo Chat.**</span><span class="sxs-lookup"><span data-stu-id="f5bd8-154">To test direct chats with your bot, you can either access it through the App home, @mention it in a channel, or search for it in the **New Chat** window.</span></span>

<span data-ttu-id="f5bd8-155">Você pode @mention o bot em uma conversa ou pesquisá-lo na janela **Novo Chat** para testar chats diretos com seu bot.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-155">You can @mention the bot in a conversation or search for it in the **New Chat** window to test direct chats with your bot.</span></span>

## <a name="access-your-uploaded-connector"></a><span data-ttu-id="f5bd8-156">Acessar o conector carregado</span><span class="sxs-lookup"><span data-stu-id="f5bd8-156">Access your uploaded Connector</span></span>

<span data-ttu-id="f5bd8-157">Com o aplicativo carregado na equipe ou na conversa, os usuários podem configurar um Conector usando o fluxo de galeria de Conectores padrão:</span><span class="sxs-lookup"><span data-stu-id="f5bd8-157">With the app loaded in the team or conversation, users can set up a Connector using the standard Connectors gallery flow:</span></span>

1. <span data-ttu-id="f5bd8-158">Vá para um canal na equipe.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-158">Go to a channel in the team.</span></span> <span data-ttu-id="f5bd8-159">Escolha **Mais opções** (*&#8943;*) e escolha **Conectores**.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-159">Choose **More options** (*&#8943;*) and choose **Connectors**.</span></span>

2. <span data-ttu-id="f5bd8-160">Selecione seu Conector na **seção Sideloaded** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-160">Select your Connector from the **Sideloaded** section at the bottom.</span></span>

3. <span data-ttu-id="f5bd8-161">Configure seu conector por meio de sua [página de configuração](../../webhooks-and-connectors/how-to/connectors-creating.md) e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-161">Configure your connector through its [configuration page](../../webhooks-and-connectors/how-to/connectors-creating.md) and select **Save**.</span></span>

  ![A caixa de diálogo Adicionar uma guia, com uma galeria de guias disponíveis.](../../assets/images/connector_gallery.png)

## <a name="access-your-uploaded-messaging-extension"></a><span data-ttu-id="f5bd8-163">Acessar sua extensão de mensagens carregada</span><span class="sxs-lookup"><span data-stu-id="f5bd8-163">Access your uploaded messaging extension</span></span>

<span data-ttu-id="f5bd8-164">Um aplicativo carregado com uma extensão de mensagens aparece automaticamente no menu **Mais** opções (*&#8943;*) na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-164">An uploaded app with a messaging extension automatically appears in the **More options** (*&#8943;*) menu in the compose box.</span></span>

![Extensões de mensagens](../../assets/images/compose-extensions/cesampleapp.png)

## <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="f5bd8-166">Adicionar um escopo de instalação padrão e funcionalidade de grupo</span><span class="sxs-lookup"><span data-stu-id="f5bd8-166">Add a default install scope and group capability</span></span>

> [!NOTE]
> <span data-ttu-id="f5bd8-167">O escopo de instalação padrão e a funcionalidade de grupo estão disponíveis apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-167">The default install scope and group capability is currently available in developer preview only.</span></span>

<span data-ttu-id="f5bd8-168">Embora a instalação de um aplicativo no escopo pessoal funcione para a maioria dos aplicativos, alguns dos aplicativos na Loja do Teams suportam escopos pessoais e de equipe.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-168">Although installing an app in the personal scope works for most apps, some of the apps in Teams Store support both personal and team scopes.</span></span>
<span data-ttu-id="f5bd8-169">Alguns desses aplicativos se destinam a trabalhar em uma equipe, reuniões ou uma conversa de grupo, com a experiência de aplicativo pessoal sendo secundária.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-169">Some of these apps are intended to work in a team, meetings, or a groupchat, with personal app experience being secondary.</span></span>
<span data-ttu-id="f5bd8-170">A seleção de escopo de instalação padrão ajuda você a especificar `defaultInstallScope` os aplicativos que você publica.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-170">The default install scope selection helps you to specify the `defaultInstallScope` for the apps that you publish.</span></span> <span data-ttu-id="f5bd8-171">A experiência de instalação do aplicativo disponibiliza as opções padrão para o usuário, enquanto o restante é movido sob a divisa conforme realçado na imagem.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-171">The app installation experience makes the default options available to the user, while the rest is moved under the chevron as highlighted in the image.</span></span>

![Adicionar um aplicativo](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="f5bd8-173">A `defaultInstallScope` propriedade dá suporte a valores, como pessoal, equipe, groupchat ou reuniões.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-173">The `defaultInstallScope` property supports values, such as personal, team, groupchat, or meetings.</span></span>

> [!NOTE]
><span data-ttu-id="f5bd8-174">`defaultGroupCapability` fornece o recurso padrão adicionado à equipe, groupchat ou reuniões.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-174">`defaultGroupCapability` provides the default capability that is added to the team, groupchat or meetings.</span></span> <span data-ttu-id="f5bd8-175">Escolha uma guia, bot ou conector como o recurso padrão para seu aplicativo, mas você deve garantir que tenha fornecido o recurso selecionado na definição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-175">Choose a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

## <a name="remove-or-update-your-app"></a><span data-ttu-id="f5bd8-176">Remover ou atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f5bd8-176">Remove or update your app</span></span>

<span data-ttu-id="f5bd8-177">Para remover seu aplicativo, selecione o ícone de exclusão ao lado do nome do aplicativo na lista Exibir bots **do Teams.**</span><span class="sxs-lookup"><span data-stu-id="f5bd8-177">To remove your app, select the delete icon next to the app name in the **View Teams** bots list.</span></span> <span data-ttu-id="f5bd8-178">Se você alterar as informações do manifesto, primeiro remova o aplicativo e adicione o pacote atualizado, consulte [Carregar seu pacote em uma equipe](#load-your-package-into-teams).</span><span class="sxs-lookup"><span data-stu-id="f5bd8-178">If you change manifest information, first remove the app and then add the updated package, see [Load your package into a team](#load-your-package-into-teams).</span></span> <span data-ttu-id="f5bd8-179">As alterações de código em seu serviço não exigem que você carregue seu manifesto novamente.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-179">Code changes on your service do not require you to upload your manifest again.</span></span> <span data-ttu-id="f5bd8-180">No entanto, se as alterações de código exigirem atualizações de manifesto, como alterações na URL ou na ID do aplicativo microsoft para seu bot, você deve carregar o manifesto novamente.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-180">However, if the code changes require manifest updates, such as changes to the URL or the Microsoft app ID for its bot, you must upload the manifest again.</span></span>

> [!NOTE]
> <span data-ttu-id="f5bd8-181">Não é possível remover um bot de um contexto pessoal inteiramente.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-181">You cannot remove a bot from a personal context entirely.</span></span> <span data-ttu-id="f5bd8-182">Se o bot for removido e adicionado novamente, a comunicação adicional com o bot será acrescentada à conversa anterior.</span><span class="sxs-lookup"><span data-stu-id="f5bd8-182">If the bot is removed and added again, additional communication with the bot appends to the previous conversation.</span></span>

## <a name="troubleshooting-notes"></a><span data-ttu-id="f5bd8-183">Anotações de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="f5bd8-183">Troubleshooting notes</span></span>

<span data-ttu-id="f5bd8-184">Se o manifesto não for carregado, verifique se você seguiu todas as instruções em [Criar](../../concepts/build-and-test/apps-package.md) o pacote e validou seu manifesto em relação ao [esquema](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f5bd8-184">If the manifest fails to load, check if you have followed all the instructions in [Create the package](../../concepts/build-and-test/apps-package.md) and validated your manifest against the [schema](../../resources/schema/manifest-schema.md).</span></span>
