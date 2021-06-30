---
title: Adicionar Power Virtual Agents chatbot ao Teams
author: surbhigupta
description: integrando um Power Virtual Agents chatbot na Teams plataforma
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2aa8cc510033768b68cf01cbb5b0327bffe13154
ms.sourcegitcommit: f62634c59b697107e5bb3c38867b21007d328b1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53196247"
---
# <a name="add-power-virtual-agents-chatbot"></a><span data-ttu-id="296a7-103">Adicionar um chatbot de Agentes Virtuais de Energia</span><span class="sxs-lookup"><span data-stu-id="296a7-103">Add Power Virtual Agents chatbot</span></span> 

<span data-ttu-id="296a7-104">Power Virtual Agents é uma solução de interface gráfica sem código guiada que capacita todos os membros da sua equipe a criar chatbots ricos e conversacionais que se integram facilmente à plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="296a7-104">Power Virtual Agents is a no-code, guided graphical interface solution that empowers every member of your team to create rich, conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="296a7-105">Todo o conteúdo Power Virtual Agents renderiza naturalmente em Teams.</span><span class="sxs-lookup"><span data-stu-id="296a7-105">All content authored in Power Virtual Agents renders naturally in Teams.</span></span> <span data-ttu-id="296a7-106">Power Virtual Agents bots se envolvem com usuários na tela Teams de chat nativa.</span><span class="sxs-lookup"><span data-stu-id="296a7-106">Power Virtual Agents bots engage with users in the Teams native chat canvas.</span></span> <span data-ttu-id="296a7-107">Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem precisar configurar um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="296a7-107">The IT administrators, business analysts, domain specialists, and skilled app developers can design, develop, and publish intelligent virtual agents for Teams without having to setup a development environment.</span></span> <span data-ttu-id="296a7-108">Eles podem criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="296a7-108">They can create a web service, or directly register with the Bot Framework.</span></span> 

<span data-ttu-id="296a7-109">Este documento orienta você sobre como disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents e adicionar seu bot ao Teams usando o App Studio.</span><span class="sxs-lookup"><span data-stu-id="296a7-109">This document guides you on how to make your chatbot available in Teams through the Power Virtual Agents portal, and add your bot to Teams using App Studio.</span></span> 

<span data-ttu-id="296a7-110">Power Virtual Agents permite criar chatbots poderosos que podem responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.</span><span class="sxs-lookup"><span data-stu-id="296a7-110">Power Virtual Agents lets you create powerful chatbots that can answer questions posed by your customers, other employees, or visitors to your website or service.</span></span>

<span data-ttu-id="296a7-111">Esses bots podem ser criados facilmente sem a necessidade de desenvolvedores ou desenvolvedores de dados.</span><span class="sxs-lookup"><span data-stu-id="296a7-111">These bots can be created easily without the need for data scientists or developers.</span></span>

> [!NOTE]
> <span data-ttu-id="296a7-112">Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário, são compartilhados com Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="296a7-112">By adding your chatbot to Microsoft Teams, some of the data, such as bot content and user chat content, is shared with Microsoft Teams.</span></span> <span data-ttu-id="296a7-113">Isso significa que seus dados fluem fora da conformidade da sua organização e dos limites [geográficos ou regionais.](/power-virtual-agents/data-location)</span><span class="sxs-lookup"><span data-stu-id="296a7-113">It means that your data flows outside of your [organization’s compliance and geographic or regional boundaries](/power-virtual-agents/data-location).</span></span> <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a><span data-ttu-id="296a7-114">Disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents site</span><span class="sxs-lookup"><span data-stu-id="296a7-114">Make your chatbot available in Teams through the Power Virtual Agents portal</span></span>

<span data-ttu-id="296a7-115">Para disponibilizar seu chatbot no Teams por meio do portal Power Virtual Agents, execute as seguintes etapas de processo:</span><span class="sxs-lookup"><span data-stu-id="296a7-115">To make your chatbot available in Teams through the Power Virtual Agents portal, you must perform the following process steps:</span></span>

<span data-ttu-id="296a7-116">**Para disponibilizar o chatbot no Teams**</span><span class="sxs-lookup"><span data-stu-id="296a7-116">**To make the chatbot available in Teams**</span></span>

1. <span data-ttu-id="296a7-117">**Publicar o conteúdo de bot mais recente**</span><span class="sxs-lookup"><span data-stu-id="296a7-117">**Publish the latest bot content**</span></span>  
<span data-ttu-id="296a7-118">Depois de criar um chatbot no portal Power Virtual Agents, você deve publicar seu bot antes Teams os usuários possam interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="296a7-118">After creating a chatbot in the Power Virtual Agents portal, you must publish your bot before Teams users can interact with it.</span></span> <span data-ttu-id="296a7-119">Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente.](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content)</span><span class="sxs-lookup"><span data-stu-id="296a7-119">For more information, see [Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span></span>

   ![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

1. <span data-ttu-id="296a7-121">**Configurar o Teams canal**</span><span class="sxs-lookup"><span data-stu-id="296a7-121">**Configure the Teams channel**</span></span>  
<span data-ttu-id="296a7-122">Depois de publicar seu bot, adicione o canal Teams para disponibilizar o bot para Teams usuários.</span><span class="sxs-lookup"><span data-stu-id="296a7-122">After publishing your bot, add the Teams channel to make the bot available to Teams users.</span></span>

   ![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

1. <span data-ttu-id="296a7-124">**Gerar uma ID de aplicativo para seu chatbot**</span><span class="sxs-lookup"><span data-stu-id="296a7-124">**Generate an App ID for your chatbot**</span></span>  
<span data-ttu-id="296a7-125">Depois de adicionar o Teams ao chatbot, uma **ID de** aplicativo é gerada na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="296a7-125">After adding the Teams channel to your chatbot, an **App ID** is generated in the dialog box.</span></span> <span data-ttu-id="296a7-126">A ID do aplicativo é um identificador gerado pela Microsoft exclusivo para seu bot.</span><span class="sxs-lookup"><span data-stu-id="296a7-126">The App ID is a unique Microsoft generated identifier for your bot.</span></span> <span data-ttu-id="296a7-127">Salve a ID do aplicativo para criar um pacote de aplicativos para Teams.</span><span class="sxs-lookup"><span data-stu-id="296a7-127">Save the App ID to create an app package for Teams.</span></span>

## <a name="add-your-bot-to-teams-using-app-studio"></a><span data-ttu-id="296a7-128">Adicionar seu bot ao Teams usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="296a7-128">Add your bot to Teams using App Studio</span></span>

<span data-ttu-id="296a7-129">Se [o carregamento de aplicativos](/microsoftteams/admin-settings) personalizados estiver habilitado em sua instância Teams, você poderá usar Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente.</span><span class="sxs-lookup"><span data-stu-id="296a7-129">If [uploading custom apps is enabled](/microsoftteams/admin-settings) in your Teams instance, you can use Teams App Studio to directly upload your chatbot and start using it immediately.</span></span> <span data-ttu-id="296a7-130">Para compartilhar seu chatbot, você pode solicitar que o administrador disponibilizar seu bot no catálogo de aplicativos de locatário ou pode enviar seu pacote de aplicativos para outras pessoas e pedir que eles o carreguem independentemente.</span><span class="sxs-lookup"><span data-stu-id="296a7-130">To share your chatbot, you can request your admin to make your bot available in the tenant app catalog or you can send your app package to others and ask them to upload it independently.</span></span>

1. <span data-ttu-id="296a7-131">**Instalar o App Studio no Teams**</span><span class="sxs-lookup"><span data-stu-id="296a7-131">**Install App Studio in Teams**</span></span>  
<span data-ttu-id="296a7-132">App Studio é um Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="296a7-132">App Studio is a Teams app.</span></span> <span data-ttu-id="296a7-133">Instale o App Studio no Teams que simplifica o processo de criação e registro de bots Teams:</span><span class="sxs-lookup"><span data-stu-id="296a7-133">Install App Studio from the Teams store that simplifies the process of bot creation and registration in Teams:</span></span> 

   1. <span data-ttu-id="296a7-134">Selecione o ícone da loja de aplicativos Teams instância e pesquise **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="296a7-134">Select the app store icon from Teams instance, and search for **App Studio**.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. <span data-ttu-id="296a7-135">Selecione o **grupo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="296a7-135">Select the **App Studio** tile and select **Install** in the pop-up dialog box.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. <span data-ttu-id="296a7-136">**Criar o Teams de aplicativo no App Studio**</span><span class="sxs-lookup"><span data-stu-id="296a7-136">**Create the Teams app manifest in App Studio**</span></span>  
<span data-ttu-id="296a7-137">Bots no Teams são definidos por um arquivo JSON de manifesto de aplicativo que fornece as informações básicas sobre seu bot e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="296a7-137">Bots in Teams are defined by an app manifest JSON file that provides the basic information about your bot and its capabilities.</span></span> <span data-ttu-id="296a7-138">No **App Studio,** selecione **Editor de manifesto** e selecione Criar um novo **aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="296a7-138">In **App Studio**, select **Manifest editor**, and select **Create a new app**.</span></span>

    ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. <span data-ttu-id="296a7-140">**Adicionar detalhes do bot**</span><span class="sxs-lookup"><span data-stu-id="296a7-140">**Add your bot details**</span></span>  
<span data-ttu-id="296a7-141">Conclua todos os campos necessários.</span><span class="sxs-lookup"><span data-stu-id="296a7-141">Complete all the required fields.</span></span> <span data-ttu-id="296a7-142">Para uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="296a7-142">For a full description of each field see [manifest schema definition](../../resources/schema/manifest-schema.md).</span></span>

    ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. <span data-ttu-id="296a7-144">**Configurar seu bot** Para configurar o bot, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="296a7-144">**Set up your bot** To set-up the bot, perform the following steps:</span></span> 
     1. <span data-ttu-id="296a7-145">Abra a **guia Bots.**</span><span class="sxs-lookup"><span data-stu-id="296a7-145">Open the **Bots** tab.</span></span> 
     1. <span data-ttu-id="296a7-146">Selecione **Configurar**  >  **bot existente** e insira o nome do bot.</span><span class="sxs-lookup"><span data-stu-id="296a7-146">Select **Setup** > **Existing bot** and enter the name of your bot.</span></span>

   ![Configuração de bot](../../assets/images/get-started/bot-set-up.png) 

   <span data-ttu-id="296a7-148">A imagem a seguir mostra como configurar um bot existente:</span><span class="sxs-lookup"><span data-stu-id="296a7-148">The following image depicts how to set-up an existing bot:</span></span>      

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)
       
1. <span data-ttu-id="296a7-150">**Adicionar sua ID do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="296a7-150">**Add your App ID**</span></span>  
<span data-ttu-id="296a7-151">Para adicionar a ID do aplicativo, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="296a7-151">To add your App ID, perform the following steps:</span></span>  
    1. <span data-ttu-id="296a7-152">Selecione **Conexão para uma id de bot diferente** e colar a **ID do aplicativo** que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="296a7-152">Select **Connect to a different bot id** and paste the **App Id** you copied earlier.</span></span> 
    1. <span data-ttu-id="296a7-153">Selecione **Salvar**  >  **Pessoal de**  >  **Escopo**.</span><span class="sxs-lookup"><span data-stu-id="296a7-153">Select **Scope** > **Personal** > **Save**.</span></span>

    ![adicionar id do aplicativo](../../assets/images/get-started/add-app-id.png)

1. <span data-ttu-id="296a7-155">**Adicionar domínios válidos para seu bot**</span><span class="sxs-lookup"><span data-stu-id="296a7-155">**Add valid domains for your bot**</span></span>  
<span data-ttu-id="296a7-156">Esta etapa só será necessária se o bot exigir que o usuário entre.</span><span class="sxs-lookup"><span data-stu-id="296a7-156">This step is only required if your bot requires the user to sign in.</span></span> <span data-ttu-id="296a7-157">Selecione **Domínios e permissões** e, no campo **Domínios Válidos,** forneça a seguinte entrada:</span><span class="sxs-lookup"><span data-stu-id="296a7-157">Select **Domains and permissions** and in the **Valid Domains** field, provide the following input:</span></span>

    ```bash
       token.botframework.com
    ```

1. <span data-ttu-id="296a7-158">**Testar e distribuir seu bot**</span><span class="sxs-lookup"><span data-stu-id="296a7-158">**Test and distribute your bot**</span></span>  
<span data-ttu-id="296a7-159">Abra **a guia Testar e distribua** e selecione **Instalar** para adicionar seu bot diretamente à sua Teams instância.</span><span class="sxs-lookup"><span data-stu-id="296a7-159">Open **Test and distribute** tab and select **Install** to add your bot directly to your Teams instance.</span></span> <span data-ttu-id="296a7-160">Como alternativa, você pode baixar o pacote de aplicativos concluído para compartilhar com Teams usuários ou fornecer ao administrador para disponibilizar seu bot no catálogo de aplicativos de locatário.</span><span class="sxs-lookup"><span data-stu-id="296a7-160">Alternately, you can download the completed app package to share with Teams users or provide it to your admin to make your bot available in the tenant app catalog.</span></span>

1. <span data-ttu-id="296a7-161">**Iniciar um chat** </span><span class="sxs-lookup"><span data-stu-id="296a7-161">**Start a chat** </span></span>  
<span data-ttu-id="296a7-162">O processo de configuração para adicionar seu Power Virtual Agents de chat ao Teams está concluído.</span><span class="sxs-lookup"><span data-stu-id="296a7-162">The set-up process for adding your Power Virtual Agents chat bot to Teams is complete.</span></span> <span data-ttu-id="296a7-163">Agora você pode iniciar uma conversa com seu bot em um chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="296a7-163">You can now start a conversation with your bot in a personal chat.</span></span>

## <a name="see-also"></a><span data-ttu-id="296a7-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="296a7-164">See also</span></span>

* [<span data-ttu-id="296a7-165">Agentes virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="296a7-165">Power Virtual Agents</span></span>](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  
* <span data-ttu-id="296a7-166">[Crie um chatbot para Teams com o Microsoft Power Virtual Agents](../bot-features.md#bots-with-power-virtual-agents).</span><span class="sxs-lookup"><span data-stu-id="296a7-166">[Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-with-power-virtual-agents).</span></span>  
* [<span data-ttu-id="296a7-167">Power Virtual Agents portal</span><span class="sxs-lookup"><span data-stu-id="296a7-167">Power Virtual Agents portal</span></span>](https://powervirtualagents.microsoft.com)
* [<span data-ttu-id="296a7-168">Publicar seu Power Virtual Agents bot</span><span class="sxs-lookup"><span data-stu-id="296a7-168">Publish your Power Virtual Agents bot</span></span>](/power-virtual-agents/publication-fundamentals-publish-channels)
* <span data-ttu-id="296a7-169">[Segurança e conformidade em Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span><span class="sxs-lookup"><span data-stu-id="296a7-169">[Security and compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="296a7-170">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="296a7-170">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="296a7-171">Criar um assistente virtual</span><span class="sxs-lookup"><span data-stu-id="296a7-171">Create a Virtual Assistant</span></span>](~/samples/virtual-assistant.md)
