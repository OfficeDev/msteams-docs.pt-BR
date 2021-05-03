---
title: Registro de canal bot do Azure
description: descreve os canais bot do Azure para registro
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta12
ms.openlocfilehash: 3cbbd204daf98f1c3528dcb6efcfde299a402912
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020944"
---
1. <span data-ttu-id="985e4-103">No portal [do Azure](https://ms.portal.azure.com/#home), em Serviços do Azure, selecione **Criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="985e4-103">In the [Azure portal](https://ms.portal.azure.com/#home), under Azure services, select **Create a resource**.</span></span>
1. <span data-ttu-id="985e4-104">Na caixa de pesquisa, digite "bot".</span><span class="sxs-lookup"><span data-stu-id="985e4-104">In the search box enter "bot".</span></span> <span data-ttu-id="985e4-105">E na lista lista listada, selecione **Registro de Canais de Bot**.</span><span class="sxs-lookup"><span data-stu-id="985e4-105">And in the drop-down list, select **Bot Channels Registration**.</span></span>
1. <span data-ttu-id="985e4-106">Selecione o **botão Criar.**</span><span class="sxs-lookup"><span data-stu-id="985e4-106">Select the **Create** button.</span></span>
1. <span data-ttu-id="985e4-107">Na folha **Registro de Canal** bot, forneça as informações solicitadas sobre seu bot.</span><span class="sxs-lookup"><span data-stu-id="985e4-107">In the **Bot Channel Registration** blade, provide the requested information about your bot.</span></span>
1. <span data-ttu-id="985e4-108">Deixe a **caixa de ponto de extremidade** Mensagens vazia por enquanto, você inserirá a URL necessária após a implantação do bot.</span><span class="sxs-lookup"><span data-stu-id="985e4-108">Leave the **Messaging endpoint** box empty for now, you will enter the required URL after deploying the bot.</span></span> <span data-ttu-id="985e4-109">A imagem a seguir mostra um exemplo das configurações de registro:</span><span class="sxs-lookup"><span data-stu-id="985e4-109">The following picture shows an example of the registration settings:</span></span>

    ![registro de canais de aplicativo bot](../../assets/images/authentication/auth-bot-channels-registration.png)

1. <span data-ttu-id="985e4-111">Clique **em ID e senha do** Aplicativo Microsoft e crie **Novo**.</span><span class="sxs-lookup"><span data-stu-id="985e4-111">Click **Microsoft App ID and password** and then **Create New**.</span></span>

    <span data-ttu-id="985e4-112">![Criar a ID do Aplicativo Microsoft ](../../assets/images/authentication/CreateMicrosoftAppID.png) ![ Criar nova ID do Aplicativo Microsoft](../../assets/images/authentication/CreateNewMicrosoftAppID.png)</span><span class="sxs-lookup"><span data-stu-id="985e4-112">![Create Microsoft App ID](../../assets/images/authentication/CreateMicrosoftAppID.png) ![Create New Microsoft App ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)</span></span>    

1. <span data-ttu-id="985e4-113">Clique **em Criar ID do Aplicativo no** link Portal de Registro de Aplicativos.</span><span class="sxs-lookup"><span data-stu-id="985e4-113">Click **Create App ID in the App Registration Portal** link.</span></span>

   ![Registros de aplicativos](../../assets/images/authentication/AppRegistration.png)
   
1. <span data-ttu-id="985e4-115">Na janela de registro **do aplicativo exibido,** clique na guia **Novo registro** no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="985e4-115">In the displayed **App registration** window, click the **New registration** tab in the upper left.</span></span>
1. <span data-ttu-id="985e4-116">Insira o nome do aplicativo bot que você está registrando, nós utilizamos *BotTeamsAuth* (você precisa selecionar seu próprio nome exclusivo).</span><span class="sxs-lookup"><span data-stu-id="985e4-116">Enter the name of the bot application you are registering, we used *BotTeamsAuth* (you need to select your own unique name).</span></span>
1. <span data-ttu-id="985e4-117">Para os **tipos de conta** com suporte, selecione Contas em qualquer diretório organizacional (Qualquer diretório do *Azure AD - Multitenant) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.</span><span class="sxs-lookup"><span data-stu-id="985e4-117">For the **Supported account types** select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
1. <span data-ttu-id="985e4-118">Clique no **botão Registrar.**</span><span class="sxs-lookup"><span data-stu-id="985e4-118">Click the **Register** button.</span></span> <span data-ttu-id="985e4-119">Depois de concluído, o Azure exibe a página *Visão* Geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="985e4-119">Once completed, Azure displays the *Overview* page for the application.</span></span>
1. <span data-ttu-id="985e4-120">Copie e salve em um arquivo o valor da **ID do** aplicativo (cliente).</span><span class="sxs-lookup"><span data-stu-id="985e4-120">Copy and save to a file the **Application (client) ID** value.</span></span>
1. <span data-ttu-id="985e4-121">No painel esquerdo, clique em **Certificado e segredos.**</span><span class="sxs-lookup"><span data-stu-id="985e4-121">In the left panel, click **Certificate and secrets**.</span></span>
    1. <span data-ttu-id="985e4-122">Em *Segredos do Cliente,* clique **em Novo segredo do cliente.**</span><span class="sxs-lookup"><span data-stu-id="985e4-122">Under *Client secrets*, click **New client secret**.</span></span>
    1. <span data-ttu-id="985e4-123">Adicione uma descrição para identificar esse segredo de outras pessoas que talvez você precise criar para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="985e4-123">Add a description to identify this secret from others you might need to create for this app.</span></span>
    1. <span data-ttu-id="985e4-124">Set *Expires* to your selection.</span><span class="sxs-lookup"><span data-stu-id="985e4-124">Set *Expires* to your selection.</span></span>
    1. <span data-ttu-id="985e4-125">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="985e4-125">Click **Add**.</span></span>
    1. <span data-ttu-id="985e4-126">Copie o segredo do cliente e salve-o em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="985e4-126">Copy the client secret and save it to a file.</span></span>
1. <span data-ttu-id="985e4-127">Volte para a janela **Registro** do Canal bot  e copie a *ID* do aplicativo e o segredo do cliente nas caixas **ID** do Aplicativo Microsoft e **Senha,** respectivamente.</span><span class="sxs-lookup"><span data-stu-id="985e4-127">Go back to the **Bot Channel Registration** window and copy the *App ID* and the *Client secret* in the **Microsoft App ID** and **Password** boxes, respectively.</span></span>
1. <span data-ttu-id="985e4-128">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="985e4-128">Click **OK**.</span></span>
1. <span data-ttu-id="985e4-129">Por fim, clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="985e4-129">Finally, click **Create**.</span></span>

<span data-ttu-id="985e4-130">Depois que o Azure tiver criado o recurso de registro, ele será incluído na lista de grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="985e4-130">After Azure has created the registration resource it will be included in the resource group list.</span></span>  

![grupo de registro de canais de aplicativo bot](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

<span data-ttu-id="985e4-132">Depois que o registro de canais de bot for criado, você precisará habilitar o Teams canal.</span><span class="sxs-lookup"><span data-stu-id="985e4-132">Once your bot channels registration is created, you'll need to enable the Teams channel.</span></span>

1. <span data-ttu-id="985e4-133">No portal [do Azure](https://ms.portal.azure.com/#home), em serviços do Azure, selecione o **Registro** de Canal bot que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="985e4-133">In the [Azure portal](https://ms.portal.azure.com/#home), under Azure services, select the **Bot Channel Registration** you just created.</span></span>
1. <span data-ttu-id="985e4-134">No painel esquerdo, clique em **Canais**.</span><span class="sxs-lookup"><span data-stu-id="985e4-134">In the left panel, click **Channels**.</span></span>
1. <span data-ttu-id="985e4-135">Clique no Microsoft Teams e escolha **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="985e4-135">Click the Microsoft Teams icon, then choose **Save**.</span></span>
