## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="af158-101">Implantar seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="af158-101">Deploy your app to Azure</span></span>

<span data-ttu-id="af158-102">A implantação consiste em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="af158-102">Deployment consists of two steps.</span></span>  <span data-ttu-id="af158-103">Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento), em seguida, o código que com o seu aplicativo é copiado para os recursos de nuvem criados.</span><span class="sxs-lookup"><span data-stu-id="af158-103">First, necessary cloud resources are created (also known as provisioning), then the code that makes up your app is copied into the created cloud resources.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="af158-104">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af158-104">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="af158-105">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="af158-105">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="af158-106">Selecione a Teams Toolkit na barra lateral selecionando o ícone Teams.</span><span class="sxs-lookup"><span data-stu-id="af158-106">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="af158-107">Selecione **Provisionamento na Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="af158-107">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

1. <span data-ttu-id="af158-109">Se necessário, selecione uma assinatura a ser usada para os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="af158-109">If required, select a subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="af158-110">Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af158-110">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="af158-111">Uma caixa de diálogo avisa que os custos podem ser incorridos ao executar recursos no Azure.</span><span class="sxs-lookup"><span data-stu-id="af158-111">A dialog warns you that costs may be incurred when running resources in Azure.</span></span>  <span data-ttu-id="af158-112">Pressione **Provision**.</span><span class="sxs-lookup"><span data-stu-id="af158-112">Press **Provision**.</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Captura de tela da caixa de diálogo de provisionamento.":::

   <span data-ttu-id="af158-114">O processo de provisionamento criará recursos na nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="af158-114">The provisioning process will create resources in the Azure cloud.</span></span>  <span data-ttu-id="af158-115">Isso levará algum tempo.</span><span class="sxs-lookup"><span data-stu-id="af158-115">This will take some time.</span></span>  <span data-ttu-id="af158-116">Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="af158-116">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="af158-117">Após alguns minutos, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="af158-117">After a few minutes, you will see the following notice:</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento.":::

1. <span data-ttu-id="af158-119">Depois que o provisionamento for concluído, selecione **Implantar na Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="af158-119">Once provisioning is complete, select **Deploy to the Cloud**.</span></span>  <span data-ttu-id="af158-120">Assim como no provisionamento, esse processo leva algum tempo.</span><span class="sxs-lookup"><span data-stu-id="af158-120">As with provisioning, this process takes some time.</span></span>  <span data-ttu-id="af158-121">Você pode monitorar o processo observando as caixas de diálogo no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="af158-121">You can monitor the process by watching the dialogs in the bottom right corner.</span></span> <span data-ttu-id="af158-122">Após alguns minutos, você verá um aviso de conclusão.</span><span class="sxs-lookup"><span data-stu-id="af158-122">After a few minutes, you will see a completion notice.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="af158-123">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="af158-123">Command Line</span></span>](#tab/cli)

<span data-ttu-id="af158-124">Em sua janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="af158-124">In your terminal window:</span></span>

1. <span data-ttu-id="af158-125">Executar `teamsfx provision` .</span><span class="sxs-lookup"><span data-stu-id="af158-125">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="af158-126">Você pode ser solicitado a fazer logoff na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="af158-126">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="af158-127">Se necessário, você será solicitado a selecionar uma assinatura do Azure a ser usada para os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="af158-127">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="af158-128">Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af158-128">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="af158-129">Executar `teamsfx deploy` .</span><span class="sxs-lookup"><span data-stu-id="af158-129">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> <span data-ttu-id="af158-130">**Qual é a diferença entre Provisionar e Implantar?**</span><span class="sxs-lookup"><span data-stu-id="af158-130">**What's the difference between Provision and Deploy?**</span></span>
>
> <span data-ttu-id="af158-131">A **etapa Provision** criará recursos no Azure e no M365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript, etc.) é copiado para os recursos.</span><span class="sxs-lookup"><span data-stu-id="af158-131">The **Provision** step will create resources in Azure and M365 for your app, but no code (HTML, CSS, JavaScript, etc.) is copied to the resources.</span></span>  <span data-ttu-id="af158-132">A **etapa Implantar** copiará o código do aplicativo para os recursos criados durante a etapa de provisionamento.</span><span class="sxs-lookup"><span data-stu-id="af158-132">The **Deploy** step will copy the code for your app to the resources you created during the provision step.</span></span>  <span data-ttu-id="af158-133">É comum implantar várias vezes sem provisionar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="af158-133">It is common to deploy multiple times without provisioning new resources.</span></span> <span data-ttu-id="af158-134">Como a etapa de provisionamento pode levar algum tempo para ser concluída, ela é separada da etapa de implantação.</span><span class="sxs-lookup"><span data-stu-id="af158-134">Since the provision step can take some time to complete, it is separate from the deployment step.</span></span>

<span data-ttu-id="af158-135">Depois que as etapas de provisionamento e implantação são concluídas:</span><span class="sxs-lookup"><span data-stu-id="af158-135">Once the provisioning and deployment steps are finished:</span></span>

1. <span data-ttu-id="af158-136">No Visual Studio Code, abra o painel de depuração (**Ctrl+Shift+D**  /  **⌘⇧-D** ou **Exibir > Executar**)</span><span class="sxs-lookup"><span data-stu-id="af158-136">From Visual Studio Code, open the debug panel (**Ctrl+Shift+D** / **⌘⇧-D** or **View > Run**)</span></span>
1. <span data-ttu-id="af158-137">Selecione **Iniciar Remoto (Borda)** no drop-down de configuração de início.</span><span class="sxs-lookup"><span data-stu-id="af158-137">Select **Launch Remote (Edge)** from the launch configuration drop-down.</span></span>
1. <span data-ttu-id="af158-138">Pressione o botão Reproduzir para iniciar seu aplicativo - agora em execução remotamente no Azure!</span><span class="sxs-lookup"><span data-stu-id="af158-138">Press the Play button to launch your app - now running remotely from Azure!</span></span>
