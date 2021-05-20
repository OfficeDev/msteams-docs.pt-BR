---
title: Adicione Power Virtual Agents chatbot ao Teams
author: laujan
description: integrando um chatbot Power Virtual Agents na plataforma Teams
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2a8f9c23eaa1acf2555b91cc4caf8d0f3298c114
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566114"
---
# <a name="add-power-virtual-agents-chatbot"></a><span data-ttu-id="f2737-103">Adicionar um chatbot de Agentes Virtuais de Energia</span><span class="sxs-lookup"><span data-stu-id="f2737-103">Add Power Virtual Agents chatbot</span></span> 

<span data-ttu-id="f2737-104">Power Virtual Agents é uma solução de interface gráfica guiada sem código que capacita cada membro de sua equipe a criar chatbots ricos e conversacionais que se integram facilmente com a plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-104">Power Virtual Agents is a no-code, guided graphical interface solution that empowers every member of your team to create rich, conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="f2737-105">Todo o conteúdo de autoria em Power Virtual Agents renderiza naturalmente em Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-105">All content authored in Power Virtual Agents renders naturally in Teams.</span></span> <span data-ttu-id="f2737-106">Power Virtual Agents bots se envolvem com os usuários na tela de bate-papo nativa Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-106">Power Virtual Agents bots engage with users in the Teams native chat canvas.</span></span> <span data-ttu-id="f2737-107">Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem ter que configurar um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f2737-107">The IT administrators, business analysts, domain specialists, and skilled app developers can design, develop, and publish intelligent virtual agents for Teams without having to setup a development environment.</span></span> <span data-ttu-id="f2737-108">Eles podem criar um serviço web ou se registrar diretamente no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="f2737-108">They can create a web service, or directly register with the Bot Framework.</span></span> 

<span data-ttu-id="f2737-109">Este documento orienta você sobre como disponibilizar seu chatbot em Teams através do portal Power Virtual Agents e adicionar seu bot a Teams usando o App Studio.</span><span class="sxs-lookup"><span data-stu-id="f2737-109">This document guides you on how to make your chatbot available in Teams through the Power Virtual Agents portal, and add your bot to Teams using App Studio.</span></span> 

<span data-ttu-id="f2737-110">Power Virtual Agents permite criar chatbots poderosos que podem responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.</span><span class="sxs-lookup"><span data-stu-id="f2737-110">Power Virtual Agents lets you create powerful chatbots that can answer questions posed by your customers, other employees, or visitors to your website or service.</span></span>

<span data-ttu-id="f2737-111">Esses bots podem ser criados facilmente sem a necessidade de cientistas de dados ou desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="f2737-111">These bots can be created easily without the need for data scientists or developers.</span></span>

> [!NOTE]
> <span data-ttu-id="f2737-112">Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de bate-papo do usuário, são compartilhados com Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-112">By adding your chatbot to Microsoft Teams, some of the data, such as bot content and user chat content, is shared with Microsoft Teams.</span></span> <span data-ttu-id="f2737-113">Isso significa que seus dados fluem fora da conformidade da sua [organização e das fronteiras geográficas ou regionais.](/power-virtual-agents/data-location)</span><span class="sxs-lookup"><span data-stu-id="f2737-113">It means that your data flows outside of your [organization’s compliance and geographic or regional boundaries](/power-virtual-agents/data-location).</span></span> <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a><span data-ttu-id="f2737-114">Disponibilize seu chatbot em Teams através do portal Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="f2737-114">Make your chatbot available in Teams through the Power Virtual Agents portal</span></span>

<span data-ttu-id="f2737-115">Para disponibilizar seu chatbot em Teams através do portal Power Virtual Agents, você deve executar as seguintes etapas do processo:</span><span class="sxs-lookup"><span data-stu-id="f2737-115">To make your chatbot available in Teams through the Power Virtual Agents portal, you must perform the following process steps:</span></span>

<span data-ttu-id="f2737-116">**Para disponibilizar o chatbot em Teams**</span><span class="sxs-lookup"><span data-stu-id="f2737-116">**To make the chatbot available in Teams**</span></span>

1. <span data-ttu-id="f2737-117">**Publique o conteúdo mais recente do bot**</span><span class="sxs-lookup"><span data-stu-id="f2737-117">**Publish the latest bot content**</span></span>  
<span data-ttu-id="f2737-118">Depois de criar um chatbot no portal Power Virtual Agents, você deve publicar seu bot antes de Teams os usuários possam interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="f2737-118">After creating a chatbot in the Power Virtual Agents portal, you must publish your bot before Teams users can interact with it.</span></span> <span data-ttu-id="f2737-119">Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span><span class="sxs-lookup"><span data-stu-id="f2737-119">For more information, see [Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span></span>

   ![publicar no portal de agentes virtuais de poder](../../assets/images/pva-publish.png)

1. <span data-ttu-id="f2737-121">**Configure o canal Teams**</span><span class="sxs-lookup"><span data-stu-id="f2737-121">**Configure the Teams channel**</span></span>  
<span data-ttu-id="f2737-122">Depois de publicar seu bot, adicione o canal Teams para disponibilizar o bot aos usuários Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-122">After publishing your bot, add the Teams channel to make the bot available to Teams users.</span></span>

   ![canais no portal de agentes virtuais de poder](../../assets/images/pva-channels.png)

1. <span data-ttu-id="f2737-124">**Gere um ID de aplicativo para o seu chatbot**</span><span class="sxs-lookup"><span data-stu-id="f2737-124">**Generate an App ID for your chatbot**</span></span>  
<span data-ttu-id="f2737-125">Depois de adicionar o canal Teams ao seu chatbot, um **ID do aplicativo** é gerado na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f2737-125">After adding the Teams channel to your chatbot, an **App ID** is generated in the dialog box.</span></span> <span data-ttu-id="f2737-126">O App ID é um identificador exclusivo gerado pela Microsoft para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="f2737-126">The App ID is a unique Microsoft generated identifier for your bot.</span></span> <span data-ttu-id="f2737-127">Salve o App ID para criar um pacote de aplicativos para Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-127">Save the App ID to create an app package for Teams.</span></span>

## <a name="add-your-bot-to-teams-using-app-studio"></a><span data-ttu-id="f2737-128">Adicione seu bot a Teams usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="f2737-128">Add your bot to Teams using App Studio</span></span>

<span data-ttu-id="f2737-129">Se [o upload de aplicativos personalizados estiver ativado](/microsoftteams/admin-settings) em sua Teams instância, você pode usar Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f2737-129">If [uploading custom apps is enabled](/microsoftteams/admin-settings) in your Teams instance, you can use Teams App Studio to directly upload your chatbot and start using it immediately.</span></span> <span data-ttu-id="f2737-130">Para compartilhar seu chatbot, você pode solicitar ao seu administrador para disponibilizar seu bot no catálogo do aplicativo de inquilino ou você pode enviar seu pacote de aplicativo para outros e pedir-lhes para carregá-lo independentemente.</span><span class="sxs-lookup"><span data-stu-id="f2737-130">To share your chatbot, you can request your admin to make your bot available in the tenant app catalog or you can send your app package to others and ask them to upload it independently.</span></span>

1. <span data-ttu-id="f2737-131">**Instalar o App Studio no Teams**</span><span class="sxs-lookup"><span data-stu-id="f2737-131">**Install App Studio in Teams**</span></span>  
<span data-ttu-id="f2737-132">App Studio é um aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="f2737-132">App Studio is a Teams app.</span></span> <span data-ttu-id="f2737-133">Instale o App Studio na loja Teams que simplificou o processo de criação e registro de bots em Teams:</span><span class="sxs-lookup"><span data-stu-id="f2737-133">Install App Studio from the Teams store that simplifies the process of bot creation and registration in Teams:</span></span> 

   1. <span data-ttu-id="f2737-134">Selecione o ícone da loja de aplicativos Teams instância e procure por **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="f2737-134">Select the app store icon from Teams instance, and search for **App Studio**.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. <span data-ttu-id="f2737-135">Selecione o **azulejo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="f2737-135">Select the **App Studio** tile and select **Install** in the pop-up dialog box.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. <span data-ttu-id="f2737-136">**Crie o manifesto do aplicativo Teams no App Studio**</span><span class="sxs-lookup"><span data-stu-id="f2737-136">**Create the Teams app manifest in App Studio**</span></span>  
<span data-ttu-id="f2737-137">Bots em Teams são definidos por um arquivo JSON manifesto de aplicativo que fornece as informações básicas sobre seu bot e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="f2737-137">Bots in Teams are defined by an app manifest JSON file that provides the basic information about your bot and its capabilities.</span></span> <span data-ttu-id="f2737-138">No **App Studio**, selecione o editor **Manifest** e selecione Criar um **novo aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="f2737-138">In **App Studio**, select **Manifest editor**, and select **Create a new app**.</span></span>

    ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. <span data-ttu-id="f2737-140">**Adicione os detalhes do seu bot**</span><span class="sxs-lookup"><span data-stu-id="f2737-140">**Add your bot details**</span></span>  
<span data-ttu-id="f2737-141">Complete todos os campos necessários.</span><span class="sxs-lookup"><span data-stu-id="f2737-141">Complete all the required fields.</span></span> <span data-ttu-id="f2737-142">Para obter uma descrição completa de cada campo, consulte [a definição do esquema manifesto](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f2737-142">For a full description of each field see [manifest schema definition](../../resources/schema/manifest-schema.md).</span></span>

    ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. <span data-ttu-id="f2737-144">**Configure seu bot** Para configurar o bot, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f2737-144">**Set up your bot** To set-up the bot, perform the following steps:</span></span> 
     1. <span data-ttu-id="f2737-145">Abra a guia **Bots.**</span><span class="sxs-lookup"><span data-stu-id="f2737-145">Open the **Bots** tab.</span></span> 
     1. <span data-ttu-id="f2737-146">Selecione **Configurar**  >  **bot existente** e digite o nome do seu bot.</span><span class="sxs-lookup"><span data-stu-id="f2737-146">Select **Setup** > **Existing bot** and enter the name of your bot.</span></span>

   ![Configuração do bot](../../assets/images/get-started/bot-set-up.png) 

   <span data-ttu-id="f2737-148">A imagem a seguir mostra como configurar um bot existente:</span><span class="sxs-lookup"><span data-stu-id="f2737-148">The following image depicts how to set-up an existing bot:</span></span>      

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)
       
1. <span data-ttu-id="f2737-150">**Adicione seu ID de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f2737-150">**Add your App ID**</span></span>  
<span data-ttu-id="f2737-151">Para adicionar seu ID de aplicativo, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f2737-151">To add your App ID, perform the following steps:</span></span>  
    1. <span data-ttu-id="f2737-152">Selecione **Conexão para um id de bot diferente** e cole o **Id** do aplicativo que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f2737-152">Select **Connect to a different bot id** and paste the **App Id** you copied earlier.</span></span> 
    1. <span data-ttu-id="f2737-153">Selecione Salvar pessoal **do escopo**  >    >  .</span><span class="sxs-lookup"><span data-stu-id="f2737-153">Select **Scope** > **Personal** > **Save**.</span></span>

    ![adicionar id aplicativo](../../assets/images/get-started/add-app-id.png)

1. <span data-ttu-id="f2737-155">**Adicione domínios válidos para o seu bot**</span><span class="sxs-lookup"><span data-stu-id="f2737-155">**Add valid domains for your bot**</span></span>  
<span data-ttu-id="f2737-156">Esta etapa só é necessária se o bot exigir que o usuário faça login.</span><span class="sxs-lookup"><span data-stu-id="f2737-156">This step is only required if your bot requires the user to sign in.</span></span> <span data-ttu-id="f2737-157">Selecione **Domínios e permissões** e no campo **Domínios Válidos,** forneça a seguinte entrada:</span><span class="sxs-lookup"><span data-stu-id="f2737-157">Select **Domains and permissions** and in the **Valid Domains** field, provide the following input:</span></span>

    ```bash
       token.botframework.com
    ```

1. <span data-ttu-id="f2737-158">**Teste e distribua seu bot**</span><span class="sxs-lookup"><span data-stu-id="f2737-158">**Test and distribute your bot**</span></span>  
<span data-ttu-id="f2737-159">Abra a guia **Teste e distribua** e selecione **Instalar** para adicionar seu bot diretamente à sua Teams instância.</span><span class="sxs-lookup"><span data-stu-id="f2737-159">Open **Test and distribute** tab and select **Install** to add your bot directly to your Teams instance.</span></span> <span data-ttu-id="f2737-160">Alternativamente, você pode baixar o pacote de aplicativos completo para compartilhar com Teams usuários ou fornecê-lo ao seu administrador para disponibilizar seu bot no catálogo do aplicativo de inquilino.</span><span class="sxs-lookup"><span data-stu-id="f2737-160">Alternately, you can download the completed app package to share with Teams users or provide it to your admin to make your bot available in the tenant app catalog.</span></span>

1. <span data-ttu-id="f2737-161">**Comece um bate-papo** </span><span class="sxs-lookup"><span data-stu-id="f2737-161">**Start a chat** </span></span>  
<span data-ttu-id="f2737-162">O processo de configuração para adicionar seu bot de chat Power Virtual Agents a Teams está completo.</span><span class="sxs-lookup"><span data-stu-id="f2737-162">The set-up process for adding your Power Virtual Agents chat bot to Teams is complete.</span></span> <span data-ttu-id="f2737-163">Agora você pode começar uma conversa com seu bot em um bate-papo pessoal.</span><span class="sxs-lookup"><span data-stu-id="f2737-163">You can now start a conversation with your bot in a personal chat.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2737-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2737-164">See also</span></span>

- [<span data-ttu-id="f2737-165">Agentes virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="f2737-165">Power Virtual Agents</span></span>](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- <span data-ttu-id="f2737-166">[Crie um chatbot para Teams com a Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).</span><span class="sxs-lookup"><span data-stu-id="f2737-166">[Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).</span></span>  

- [<span data-ttu-id="f2737-167">portal Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="f2737-167">Power Virtual Agents portal</span></span>](https://powervirtualagents.microsoft.com)

- [<span data-ttu-id="f2737-168">Publique seu bot de Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="f2737-168">Publish your Power Virtual Agents bot</span></span>](/power-virtual-agents/publication-fundamentals-publish-channels)

- <span data-ttu-id="f2737-169">[Segurança e conformidade em Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span><span class="sxs-lookup"><span data-stu-id="f2737-169">[Security and compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="f2737-170">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f2737-170">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2737-171">Criar assistente virtual</span><span class="sxs-lookup"><span data-stu-id="f2737-171">Create virtual assistant</span></span>](~/samples/virtual-assistant.md)

