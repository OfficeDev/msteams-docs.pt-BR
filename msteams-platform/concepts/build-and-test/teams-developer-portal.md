---
title: Gerenciar seus aplicativos com o Portal do Desenvolvedor
description: Saiba como gerenciar seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams.
keywords: iniciando equipes do portal do desenvolvedor
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 950ca7e09f5b87647cb62b66a545a0b1cec33a7d
ms.sourcegitcommit: 25c02757fe207cdff916ba63aa215f88e24e1d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2021
ms.locfileid: "52667437"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a><span data-ttu-id="1a44d-104">Gerenciar seus aplicativos com o Portal do Desenvolvedor para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a44d-104">Manage your apps with the Developer Portal for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="1a44d-105">O Portal do Desenvolvedor para Teams está atualmente em [visualização de desenvolvedor público.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="1a44d-105">The Developer Portal for Teams is currently in [public developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

<span data-ttu-id="1a44d-106">O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus Microsoft Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1a44d-106">The <a href="https://dev.teams.microsoft.com" target="_blank">Developer Portal for Teams</a> is the primary tool for configuring, distributing, and managing your Microsoft Teams apps.</span></span> <span data-ttu-id="1a44d-107">Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de tempo de execução e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1a44d-107">With the Developer Portal, you can collaborate with colleagues on your app, set up runtime environments, and much more.</span></span>

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Captura de tela mostrando a home page do Portal do Desenvolvedor para Teams.":::

## <a name="register-an-app"></a><span data-ttu-id="1a44d-109">Registrar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a44d-109">Register an app</span></span>

<span data-ttu-id="1a44d-110">O Portal do Desenvolvedor fornece algumas maneiras de registrar um Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1a44d-110">The Developer Portal provides a couple ways to register a Teams app:</span></span>

* <span data-ttu-id="1a44d-111">Registrar um aplicativo novo</span><span class="sxs-lookup"><span data-stu-id="1a44d-111">Register a brand new app</span></span>
* <span data-ttu-id="1a44d-112">Importar um pacote de aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="1a44d-112">Import an existing app package</span></span>

> [!NOTE]
> <span data-ttu-id="1a44d-113">Se você criar um aplicativo usando o [Microsoft Teams Toolkit para](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)Visual Studio Code , poderá gerenciar esse aplicativo no Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1a44d-113">If you create an app using the [Microsoft Teams Toolkit for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension), you can manage that app in the Developer Portal.</span></span>

## <a name="set-up-an-environment"></a><span data-ttu-id="1a44d-114">Configurar um ambiente</span><span class="sxs-lookup"><span data-stu-id="1a44d-114">Set up an environment</span></span>

<span data-ttu-id="1a44d-115">Você pode configurar ambientes e variáveis globais para ajudar a fazer a transição do aplicativo do tempo de execução local para a produção.</span><span class="sxs-lookup"><span data-stu-id="1a44d-115">You can configure environments and global variables to help transition your app from your local runtime to production.</span></span> <span data-ttu-id="1a44d-116">As variáveis globais são usadas em todos os ambientes.</span><span class="sxs-lookup"><span data-stu-id="1a44d-116">Global variables are used across all environments.</span></span>

<span data-ttu-id="1a44d-117">**Para configurar um ambiente**</span><span class="sxs-lookup"><span data-stu-id="1a44d-117">**To set up an environment**</span></span>

1. <span data-ttu-id="1a44d-118">No Portal do Desenvolvedor, selecione o aplicativo em que você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="1a44d-118">In the Developer Portal, select the app you're working on.</span></span>
2. <span data-ttu-id="1a44d-119">Vá até a **página Ambientes** e selecione **+ Adicionar um ambiente**.</span><span class="sxs-lookup"><span data-stu-id="1a44d-119">Go to the **Environments** page and select **+ Add an environment**.</span></span>
3. <span data-ttu-id="1a44d-120">Selecione **+ Adicionar uma variável** para criar variáveis de configuração para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1a44d-120">Select **+ Add a variable** to create configuration variables for your environment.</span></span>

<span data-ttu-id="1a44d-121">**Para usar variáveis**</span><span class="sxs-lookup"><span data-stu-id="1a44d-121">**To use variables**</span></span>

<span data-ttu-id="1a44d-122">Use os nomes de variáveis em vez de valores codificados para definir as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a44d-122">Use the variable names instead of hard-coded values to set your app configurations.</span></span>

1. <span data-ttu-id="1a44d-123">Insira `{{` em qualquer campo no Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1a44d-123">Enter `{{` in any field in the Developer Portal.</span></span> <span data-ttu-id="1a44d-124">Um menu suspenso com todas as variáveis que você criou para o ambiente escolhido juntamente com as variáveis globais é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a44d-124">A dropdown with all the variables you've created for the chosen environment along with the global variables appears.</span></span>  
1. <span data-ttu-id="1a44d-125">Antes de baixar o pacote do aplicativo (por exemplo, ao se preparar para publicar no Teams store), selecione o ambiente que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="1a44d-125">Before downloading your app package (for example, when getting ready to publish to the Teams store), select the environment you want to use.</span></span> <span data-ttu-id="1a44d-126">As configurações do aplicativo são atualizadas automaticamente com base no ambiente.</span><span class="sxs-lookup"><span data-stu-id="1a44d-126">Your app configurations update automatically based on the environment.</span></span> 

## <a name="identify-app-owners"></a><span data-ttu-id="1a44d-127">Identificar proprietários de aplicativos</span><span class="sxs-lookup"><span data-stu-id="1a44d-127">Identify app owners</span></span>

<span data-ttu-id="1a44d-128">Cada aplicativo inclui uma página **Proprietários,** onde você pode compartilhar o registro do aplicativo com colegas em sua organização. A **função Colaborador** tem as mesmas permissões que a função **Owner,** exceto a capacidade de excluir um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a44d-128">Each app includes an **Owners** page, where you can share your app registration with colleagues in your org. The **Contributor** role has the same permissions as the **Owner** role except the ability to delete an app.</span></span>

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a><span data-ttu-id="1a44d-129">Configurar os recursos do aplicativo e outros metadados importantes</span><span class="sxs-lookup"><span data-stu-id="1a44d-129">Configure your app's capabilities and other important metadata</span></span>

<span data-ttu-id="1a44d-130">Um Teams app é um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="1a44d-130">A Teams app is a web app.</span></span> <span data-ttu-id="1a44d-131">Como todos os aplicativos Web, seu código-fonte normalmente é desenvolvido em um IDE ou editor de código e hospedado em algum lugar na nuvem (como o Azure).</span><span class="sxs-lookup"><span data-stu-id="1a44d-131">Like all web apps, its source code is typically developed in an IDE or code editor and hosted somewhere in the cloud (like Azure).</span></span>

<span data-ttu-id="1a44d-132">Para instalar e renderizar seu aplicativo Teams, você deve incluir um conjunto de configurações que Teams reconhece.</span><span class="sxs-lookup"><span data-stu-id="1a44d-132">To install and render your app in Teams, you must include a set of configurations that Teams recognizes.</span></span> <span data-ttu-id="1a44d-133">Isso tradicionalmente foi feito por meio da criação de um manifesto de aplicativo, um arquivo JSON que contém todos os metadados que Teams precisa para exibir o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a44d-133">This has traditionally been done by crafting an app manifest, a JSON file that contains all the metadata Teams needs to display your app content.</span></span> <span data-ttu-id="1a44d-134">O Portal do Desenvolvedor abstrai esse processo e inclui novos recursos e ferramentas para ajudá-lo a ter mais êxito.</span><span class="sxs-lookup"><span data-stu-id="1a44d-134">The Developer Portal abstracts this process and includes new features and tooling to help you be more successful.</span></span>

## <a name="test-your-app-directly-in-teams"></a><span data-ttu-id="1a44d-135">Teste seu aplicativo diretamente no Teams</span><span class="sxs-lookup"><span data-stu-id="1a44d-135">Test your app directly in Teams</span></span>

<span data-ttu-id="1a44d-136">O Portal do Desenvolvedor oferece opções para testar e depurar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1a44d-136">The Developer Portal provides options for testing and debugging your app:</span></span>

* <span data-ttu-id="1a44d-137">Na página **Visão** geral, você pode ver um instantâneo de se as configurações do seu aplicativo são validadas em Teams casos de teste da loja.</span><span class="sxs-lookup"><span data-stu-id="1a44d-137">On the **Overview** page, you can see a snapshot of whether your app's configurations validate against Teams store test cases.</span></span>
* <span data-ttu-id="1a44d-138">O **botão Visualizar Teams** permite que você iniciar seu aplicativo rapidamente no cliente Teams para depuração.</span><span class="sxs-lookup"><span data-stu-id="1a44d-138">The **Preview in Teams** button lets you launch your app quickly in the Teams client for debugging.</span></span>

## <a name="distribute-your-app"></a><span data-ttu-id="1a44d-139">Distribuir seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a44d-139">Distribute your app</span></span>

<span data-ttu-id="1a44d-140">No Portal do Desenvolvedor, use o botão **Distribuir** para baixar um pacote de aplicativos, publicar em sua organização ou publicar no Teams store.</span><span class="sxs-lookup"><span data-stu-id="1a44d-140">From the Developer Portal, use the **Distribute** button to download an app package, publish to your org, or publish to the Teams store.</span></span>

<span data-ttu-id="1a44d-141">Para obter mais informações, [consulte distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a44d-141">For more information, see [distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).</span></span>

## <a name="analyze-your-apps-usage"></a><span data-ttu-id="1a44d-142">Analisar o uso do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a44d-142">Analyze your app's usage</span></span>

<span data-ttu-id="1a44d-143">Na página **Visão** geral, você pode ver o número total de usuários ativos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a44d-143">On the **Overview** page, you can see the total number of active users for your app.</span></span> <span data-ttu-id="1a44d-144">Essas métricas estão disponíveis para aplicativos publicados na Teams ou no catálogo de aplicativos de uma organização por meio do Portal do Desenvolvedor e com escopo para a ID do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a44d-144">These metrics are available for apps published to the Teams store or an org's app catalog through Developer Portal and scoped to the app ID.</span></span>

| <span data-ttu-id="1a44d-145">Indicador</span><span class="sxs-lookup"><span data-stu-id="1a44d-145">Metric</span></span> | <span data-ttu-id="1a44d-146">Definição</span><span class="sxs-lookup"><span data-stu-id="1a44d-146">Definition</span></span> |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a44d-147">*R30 mensal*</span><span class="sxs-lookup"><span data-stu-id="1a44d-147">*Monthly R30*</span></span> | <span data-ttu-id="1a44d-148">A métrica de uso padrão.</span><span class="sxs-lookup"><span data-stu-id="1a44d-148">The default usage metric.</span></span> <span data-ttu-id="1a44d-149">Ele mostra a contagem de usuários ativos exclusivos que usaram seu aplicativo nessa janela de 30 dias de rolagem em UTC.</span><span class="sxs-lookup"><span data-stu-id="1a44d-149">It shows you the count of unique active users that used your app within that rolling 30-day window in UTC.</span></span> |
| <span data-ttu-id="1a44d-150">*Diariamente*</span><span class="sxs-lookup"><span data-stu-id="1a44d-150">*Daily*</span></span> | <span data-ttu-id="1a44d-151">Mostra a contagem de usuários ativos exclusivos que usaram seu aplicativo em um determinado dia em UTC.</span><span class="sxs-lookup"><span data-stu-id="1a44d-151">Shows you the count of unique active users that used your app in a given day in UTC.</span></span> |

<span data-ttu-id="1a44d-152">O uso mensal e diário é mostrado nos últimos sete, 30 dias e 60 dias.</span><span class="sxs-lookup"><span data-stu-id="1a44d-152">Monthly and daily usage is shown for the past seven, 30 days, and 60 days.</span></span> <span data-ttu-id="1a44d-153">Você deve ver o uso refletido para um determinado dia dentro de 24 a 48 horas.</span><span class="sxs-lookup"><span data-stu-id="1a44d-153">You should see usage reflected for a given day within 24-48 hours.</span></span> <span data-ttu-id="1a44d-154">O uso de novos aplicativos pode levar de 3 a 5 dias para ser exibido.</span><span class="sxs-lookup"><span data-stu-id="1a44d-154">Usage for new apps can take up to 3-5 days to display.</span></span>

## <a name="use-tools-to-create-app-features"></a><span data-ttu-id="1a44d-155">Usar ferramentas para criar recursos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a44d-155">Use tools to create app features</span></span>

<span data-ttu-id="1a44d-156">O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar alguns recursos principais de Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1a44d-156">The Developer Portal also includes tools to help you build some key features of Teams apps.</span></span> <span data-ttu-id="1a44d-157">Algumas dessas ferramentas incluem:</span><span class="sxs-lookup"><span data-stu-id="1a44d-157">Some of these tools include:</span></span>

* <span data-ttu-id="1a44d-158">**Estúdio de cena**: Projetar cenas do modo Juntos personalizadas para Teams reuniões.</span><span class="sxs-lookup"><span data-stu-id="1a44d-158">**Scene studio**: Design custom Together mode scenes for Teams meetings.</span></span>
* <span data-ttu-id="1a44d-159">**Editor de Cartões Adaptáveis**: Crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1a44d-159">**Adaptive Cards editor**: Create and preview Adaptive Cards to include with your apps.</span></span>
* <span data-ttu-id="1a44d-160">**plataforma de identidade da Microsoft gerenciamento**: registre seus aplicativos com o Azure Active Directory (Azure AD) para ajudar os usuários a entrar e fornecer acesso a APIs.</span><span class="sxs-lookup"><span data-stu-id="1a44d-160">**Microsoft identity platform management**: Register your apps with Azure Active Directory (Azure AD) to help users sign in and provide access to APIs.</span></span>
