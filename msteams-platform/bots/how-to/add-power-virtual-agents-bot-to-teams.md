---
title: Adicionar chatbot de Agentes Virtuais do Power ao Teams
author: laujan
description: integrando um chatbot do Power Virtual Agents na plataforma teams
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: bd1528d06f9e9f4ca3a03f167ecb3c537977fb61
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058618"
---
# <a name="add-power-virtual-agents-chatbot"></a><span data-ttu-id="58543-103">Adicionar um chatbot de Agentes Virtuais de Energia</span><span class="sxs-lookup"><span data-stu-id="58543-103">Add Power Virtual Agents chatbot</span></span> 

<span data-ttu-id="58543-104">O Power Virtual Agents é uma solução de interface gráfica sem código e orientada que capacita todos os membros da sua equipe a criar chatbots ricos e conversais que se integram facilmente à plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-104">Power Virtual Agents is a no-code, guided graphical interface solution that empowers every member of your team to create rich, conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="58543-105">Todo o conteúdo de autoria no Power Virtual Agents é renderiza naturalmente no Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-105">All content authored in Power Virtual Agents renders naturally in Teams.</span></span> <span data-ttu-id="58543-106">Os bots do Power Virtual Agents se envolvem com usuários na tela de chat nativa do Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-106">Power Virtual Agents bots engage with users in the Teams native chat canvas.</span></span> <span data-ttu-id="58543-107">Os administradores de TI, analistas de negócios, especialistas em domínio e desenvolvedores de aplicativos qualificados podem projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="58543-107">The IT administrators, business analysts, domain specialists, and skilled app developers can design, develop and publish intelligent virtual agents for Teams without having to setup a development environment.</span></span> <span data-ttu-id="58543-108">Eles podem criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="58543-108">They can create a web service, or directly register with the Bot Framework.</span></span> 

<span data-ttu-id="58543-109">Este documento orienta você sobre como disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents e adicionar seu bot ao Teams usando o App Studio.</span><span class="sxs-lookup"><span data-stu-id="58543-109">This document guides you on how to make your chatbot available in Teams through the Power Virtual Agents portal, and add your bot to Teams using App Studio.</span></span> 

<span data-ttu-id="58543-110">Os Agentes Virtuais do Power permitem que você crie chatbots poderosos que possam responder a perguntas feitas por seus clientes, outros funcionários ou visitantes do seu site ou serviço.</span><span class="sxs-lookup"><span data-stu-id="58543-110">Power Virtual Agents lets you create powerful chatbots that can answer questions posed by your customers, other employees, or visitors to your website or service.</span></span>

<span data-ttu-id="58543-111">Esses bots podem ser criados facilmente sem a necessidade de desenvolvedores ou desenvolvedores de dados.</span><span class="sxs-lookup"><span data-stu-id="58543-111">These bots can be created easily without the need for data scientists or developers.</span></span>

> [!NOTE]
> <span data-ttu-id="58543-112">Ao adicionar seu chatbot ao Microsoft Teams, alguns dos dados, como conteúdo de bot e conteúdo de chat do usuário, são compartilhados com o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-112">By adding your chatbot to Microsoft Teams, some of the data, such as bot content and user chat content, is shared with Microsoft Teams.</span></span> <span data-ttu-id="58543-113">Isso significa que seus dados fluem fora da conformidade da sua organização e dos limites [geográficos ou regionais.](/power-virtual-agents/data-location)</span><span class="sxs-lookup"><span data-stu-id="58543-113">It means that your data flows outside of your [organization’s compliance and geographic or regional boundaries](/power-virtual-agents/data-location).</span></span> <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a><span data-ttu-id="58543-114">Disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="58543-114">Make your chatbot available in Teams through the Power Virtual Agents portal</span></span>

<span data-ttu-id="58543-115">Para disponibilizar seu chatbot no Teams por meio do portal do Power Virtual Agents, você deve executar as seguintes etapas de processo:</span><span class="sxs-lookup"><span data-stu-id="58543-115">To make your chatbot available in Teams through the Power Virtual Agents portal, you must perform the following process steps:</span></span>

<span data-ttu-id="58543-116">**Para disponibilizar o chatbot no Teams**</span><span class="sxs-lookup"><span data-stu-id="58543-116">**To make the chatbot available in Teams**</span></span>

1. <span data-ttu-id="58543-117">**Publicar o conteúdo de bot mais recente**</span><span class="sxs-lookup"><span data-stu-id="58543-117">**Publish the latest bot content**</span></span>  
<span data-ttu-id="58543-118">Depois de criar um chatbot no portal do Power Virtual Agents, você deve publicar seu bot antes que os usuários do Teams possam interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="58543-118">After creating a chatbot in the Power Virtual Agents portal, you must publish your bot before Teams users can interact with it.</span></span> <span data-ttu-id="58543-119">Para obter mais informações, consulte [Publicar o conteúdo de bot mais recente.](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content)</span><span class="sxs-lookup"><span data-stu-id="58543-119">For more information, see [Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span></span>

   ![publicar no portal de agentes virtuais de energia](../../assets/images/pva-publish.png)

1. <span data-ttu-id="58543-121">**Configurar o canal do Teams**</span><span class="sxs-lookup"><span data-stu-id="58543-121">**Configure the Teams channel**</span></span>  
<span data-ttu-id="58543-122">Depois de publicar seu bot, adicione o canal do Teams para disponibilizar o bot aos usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-122">After publishing your bot, add the Teams channel to make the bot available to Teams users.</span></span>

   ![canais no portal de agentes virtuais de energia](../../assets/images/pva-channels.png)

1. <span data-ttu-id="58543-124">**Gerar uma ID de aplicativo para seu chatbot**</span><span class="sxs-lookup"><span data-stu-id="58543-124">**Generate an App ID for your chatbot**</span></span>  
<span data-ttu-id="58543-125">Depois de adicionar o canal do Teams ao chatbot, uma **ID de aplicativo** é gerada na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="58543-125">After adding the Teams channel to your chatbot, an **App ID** is generated in the dialog box.</span></span> <span data-ttu-id="58543-126">A ID do aplicativo é um identificador gerado pela Microsoft exclusivo para seu bot.</span><span class="sxs-lookup"><span data-stu-id="58543-126">The App ID is a unique Microsoft generated identifier for your bot.</span></span> <span data-ttu-id="58543-127">Salve a ID do aplicativo para criar um pacote de aplicativos para o Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-127">Save the App ID to create an app package for Teams.</span></span>

## <a name="add-your-bot-to-teams-using-app-studio"></a><span data-ttu-id="58543-128">Adicionar seu bot ao Teams usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="58543-128">Add your bot to Teams using App Studio</span></span>

<span data-ttu-id="58543-129">Se [o carregamento de aplicativos](/microsoftteams/admin-settings) personalizados estiver habilitado em sua instância do Teams, você poderá usar o Teams App Studio para carregar diretamente seu chatbot e começar a usá-lo imediatamente.</span><span class="sxs-lookup"><span data-stu-id="58543-129">If [uploading custom apps is enabled](/microsoftteams/admin-settings) in your Teams instance, you can use Teams App Studio to directly upload your chatbot and start using it immediately.</span></span> <span data-ttu-id="58543-130">Para compartilhar seu chatbot, você pode solicitar que o administrador disponibilizar seu bot no catálogo de aplicativos de locatário ou pode enviar seu pacote de aplicativos para outras pessoas e pedir que eles o carreguem independentemente.</span><span class="sxs-lookup"><span data-stu-id="58543-130">To share your chatbot, you can request your admin to make your bot available in the tenant app catalog or you can send your app package to others and ask them to upload it independently.</span></span>

1. <span data-ttu-id="58543-131">**Instalar o App Studio no Teams**</span><span class="sxs-lookup"><span data-stu-id="58543-131">**Install App Studio in Teams**</span></span>  
<span data-ttu-id="58543-132">App Studio é um aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-132">App Studio is a Teams app.</span></span> <span data-ttu-id="58543-133">Instale o App Studio no armazenamento do Teams que simplifica o processo de criação e registro de bots no Teams:</span><span class="sxs-lookup"><span data-stu-id="58543-133">Install App Studio from the Teams store that simplifies the process of bot creation and registration in Teams:</span></span> 

   1. <span data-ttu-id="58543-134">Selecione o ícone da loja de aplicativos na instância do Teams e procure **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="58543-134">Select the app store icon from Teams instance, and search for **App Studio**.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. <span data-ttu-id="58543-135">Selecione o **grupo App Studio** e selecione **Instalar** na caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="58543-135">Select the **App Studio** tile and select **Install** in the pop-up dialog box.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. <span data-ttu-id="58543-136">**Criar o manifesto do aplicativo do Teams no App Studio**</span><span class="sxs-lookup"><span data-stu-id="58543-136">**Create the Teams app manifest in App Studio**</span></span>  
<span data-ttu-id="58543-137">Bots no Teams são definidos por um arquivo JSON de manifesto do aplicativo que fornece as informações básicas sobre seu bot e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="58543-137">Bots in Teams are defined by an app manifest JSON file that provides the basic information about your bot and its capabilities.</span></span> <span data-ttu-id="58543-138">No **App Studio,** selecione **Editor de manifesto** e selecione Criar um novo **aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="58543-138">In **App Studio**, select **Manifest editor**, and select **Create a new app**.</span></span>  
<span data-ttu-id="58543-139">A imagem a seguir orienta você a criar um novo aplicativo no App Studio:</span><span class="sxs-lookup"><span data-stu-id="58543-139">The following image guides you to create a new app in App Studio:</span></span>  

   ![criar um novo aplicativo](../../assets/images/get-started/create-new-app.png)

1. <span data-ttu-id="58543-141">**Adicionar detalhes do bot**</span><span class="sxs-lookup"><span data-stu-id="58543-141">**Add your bot details**</span></span>  
<span data-ttu-id="58543-142">Conclua todos os campos necessários.</span><span class="sxs-lookup"><span data-stu-id="58543-142">Complete all the required fields.</span></span> <span data-ttu-id="58543-143">Para uma descrição completa de cada campo, consulte [definição de esquema de manifesto](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="58543-143">For a full description of each field see [manifest schema definition](../../resources/schema/manifest-schema.md).</span></span>   
<span data-ttu-id="58543-144">A imagem a seguir orienta você a adicionar os detalhes do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="58543-144">The following image guides you to add the app details:</span></span>  

   ![adicionar detalhes do aplicativo](../../assets/images/get-started/add-app-details.png)

1. <span data-ttu-id="58543-146">**Configurar seu bot** Para configurar o bot, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="58543-146">**Set up your bot** To set-up the bot, perform the following steps:</span></span> 
     1. <span data-ttu-id="58543-147">Abra a **guia Bots.**</span><span class="sxs-lookup"><span data-stu-id="58543-147">Open the **Bots** tab.</span></span> 
     1. <span data-ttu-id="58543-148">Selecione **Configurar**  >  **bot existente** e insira o nome do bot.</span><span class="sxs-lookup"><span data-stu-id="58543-148">Select **Setup** > **Existing bot** and enter the name of your bot.</span></span>

   <span data-ttu-id="58543-149">A imagem a seguir orienta você a configurar um bot:</span><span class="sxs-lookup"><span data-stu-id="58543-149">The following image guides you to set-up a bot:</span></span>    

   ![Configuração de bot](../../assets/images/get-started/bot-set-up.png) 

   <span data-ttu-id="58543-151">A imagem a seguir orienta você a configurar um bot existente:</span><span class="sxs-lookup"><span data-stu-id="58543-151">The following image guides you to set-up an existing bot:</span></span>      

   ![configuração de bot existente](../../assets/images/get-started/existing-bot-set-up.png)    
1. <span data-ttu-id="58543-153">**Adicionar sua ID do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="58543-153">**Add your App ID**</span></span>  
<span data-ttu-id="58543-154">Para adicionar a ID do aplicativo, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="58543-154">To add your App ID, perform the following steps:</span></span>  
    1. <span data-ttu-id="58543-155">Selecione **Conectar a uma id de bot diferente** e colar a **ID do aplicativo que** você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="58543-155">Select **Connect to a different bot id** and paste the **App Id** you copied earlier.</span></span> 
    1. <span data-ttu-id="58543-156">Selecione **Salvar**  >  **Pessoal de**  >  **Escopo**.</span><span class="sxs-lookup"><span data-stu-id="58543-156">Select **Scope** > **Personal** > **Save**.</span></span>      
<span data-ttu-id="58543-157">A imagem a seguir orienta você a configurar um bot existente:</span><span class="sxs-lookup"><span data-stu-id="58543-157">The following image guides you to set-up an existing bot:</span></span>    

   ![adicionar id do aplicativo](../../assets/images/get-started/add-app-id.png)

1. <span data-ttu-id="58543-159">**Adicionar domínios válidos para seu bot**</span><span class="sxs-lookup"><span data-stu-id="58543-159">**Add valid domains for your bot**</span></span>  
<span data-ttu-id="58543-160">Esta etapa só será necessária se o bot exigir que o usuário entre.</span><span class="sxs-lookup"><span data-stu-id="58543-160">This step is only required if your bot requires the user to sign in.</span></span> <span data-ttu-id="58543-161">Selecione **Domínios e permissões** e, no campo **Domínios Válidos,** forneça a seguinte entrada:</span><span class="sxs-lookup"><span data-stu-id="58543-161">Select **Domains and permissions** and in the **Valid Domains** field, provide the following input:</span></span>

    ```bash
       token.botframework.com
    ```

7.  <span data-ttu-id="58543-162">**Testar e distribuir seu bot**</span><span class="sxs-lookup"><span data-stu-id="58543-162">**Test and distribute your bot**</span></span>  
<span data-ttu-id="58543-163">Abra **a guia Teste e distribua** e selecione **Instalar** para adicionar seu bot diretamente à sua instância do Teams.</span><span class="sxs-lookup"><span data-stu-id="58543-163">Open **Test and distribute** tab and select **Install** to add your bot directly to your Teams instance.</span></span> <span data-ttu-id="58543-164">Como alternativa, você pode baixar o pacote de aplicativos concluído para compartilhar com usuários do Teams ou fornece-lo ao administrador para disponibilizar seu bot no catálogo de aplicativos do locatário.</span><span class="sxs-lookup"><span data-stu-id="58543-164">Alternately, you can download the completed app package to share with Teams users or provide it to your admin to make your bot available in the tenant app catalog.</span></span>

8. <span data-ttu-id="58543-165">**Iniciar um chat** </span><span class="sxs-lookup"><span data-stu-id="58543-165">**Start a chat** </span></span>  
<span data-ttu-id="58543-166">O processo de configuração para adicionar seu bot de chat do Power Virtual Agents ao Teams está concluído.</span><span class="sxs-lookup"><span data-stu-id="58543-166">The set-up process for adding your Power Virtual Agents chat bot to Teams is complete.</span></span> <span data-ttu-id="58543-167">Agora você pode iniciar uma conversa com seu bot em um chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="58543-167">You can now start a conversation with your bot in a personal chat.</span></span>

## <a name="see-also"></a><span data-ttu-id="58543-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="58543-168">See also</span></span>

- [<span data-ttu-id="58543-169">Agentes virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="58543-169">Power Virtual Agents</span></span>](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- <span data-ttu-id="58543-170">[Crie um chatbot para o Teams com agentes virtuais do Microsoft Power.](../bot-features.md#bots-and-the-microsoft-power-virtual-agents)</span><span class="sxs-lookup"><span data-stu-id="58543-170">[Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).</span></span>  

- [<span data-ttu-id="58543-171">Portal de Agentes Virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="58543-171">Power Virtual Agents portal</span></span>](https://powervirtualagents.microsoft.com)

- [<span data-ttu-id="58543-172">Publicar seu bot agentes virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="58543-172">Publish your Power Virtual Agents bot</span></span>](/power-virtual-agents/publication-fundamentals-publish-channels)

- <span data-ttu-id="58543-173">[Segurança e conformidade no Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span><span class="sxs-lookup"><span data-stu-id="58543-173">[Security and compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="58543-174">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="58543-174">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58543-175">Criar assistente virtual</span><span class="sxs-lookup"><span data-stu-id="58543-175">Create virtual assistant</span></span>](~/samples/virtual-assistant.md)

