---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração Moodle para Microsoft Teams
keywords: Teams Plug-ins de integração de aplicativo miojo
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 54f4fec4e240f866c686ed715bd5093a319a2a48
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069171"
---
# <a name="install-moodle-lms"></a><span data-ttu-id="ea771-104">Instalar o Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="ea771-104">Install Moodle LMS</span></span>

<span data-ttu-id="ea771-105">Neste artigo, você aprenderá a instalar o Moodle LMS.</span><span class="sxs-lookup"><span data-stu-id="ea771-105">In this article you'll learn how to install the Moodle LMS.</span></span>

> [!NOTE]
> <span data-ttu-id="ea771-106">Para ajudar os administradores de IT a configurar facilmente o Moodle e Teams integração, os Plug-ins de Moodle de Microsoft 365 de código aberto são atualizados para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ea771-106">To help IT admins to easily set-up Moodle and Teams integration, open-source Microsoft 365 Moodle Plugins is updated for the following:</span></span>
>
> * <span data-ttu-id="ea771-107">Registro automático do servidor Moodle com [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="ea771-107">Auto-registration of your Moodle server with [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span></span>
>
> * <span data-ttu-id="ea771-108">Implantação de um clique do bot do Assistente de miojo no Azure.</span><span class="sxs-lookup"><span data-stu-id="ea771-108">One-click deployment of your Moodle Assistant bot to Azure.</span></span>
>
> * <span data-ttu-id="ea771-109">Provisionamento automático de equipes e sincronização automática de inscrições de equipe para todos ou selecione Cursos de miojo.</span><span class="sxs-lookup"><span data-stu-id="ea771-109">Auto-provisioning of teams and auto-synchronization of team enrollments for all or select Moodle courses.</span></span>
>
> * <span data-ttu-id="ea771-110">Instalação automática da guia Moodle e do bot do assistente de miojo em cada equipe sincronizada.</span><span class="sxs-lookup"><span data-stu-id="ea771-110">Auto-installation of the Moodle tab and the Moodle assistant bot into each synchronized team.</span></span>
>
> <span data-ttu-id="ea771-111">Para saber mais sobre a funcionalidade que essa integração fornece, consulte [Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).</span><span class="sxs-lookup"><span data-stu-id="ea771-111">To learn more about the functionality this integration provides, see [Microsoft Teams and Moodle](https://education.microsoft.com/resource/3dffb3a8).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea771-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea771-112">Prerequisites</span></span>

<span data-ttu-id="ea771-113">A seguir estão os pré-requisitos para instalar o Moodle:</span><span class="sxs-lookup"><span data-stu-id="ea771-113">Following are the prerequisites to install Moodle:</span></span>

* <span data-ttu-id="ea771-114">Credenciais de administrador de miojo.</span><span class="sxs-lookup"><span data-stu-id="ea771-114">Moodle administrator credentials.</span></span>

* <span data-ttu-id="ea771-115">Credenciais de administrador do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-115">Azure AD administrator credentials.</span></span>

* <span data-ttu-id="ea771-116">Uma assinatura do Azure onde você pode criar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="ea771-116">An Azure subscription where you can create new resources.</span></span>

## <a name="1-install-the-microsoft-365-moodle-plugins"></a><span data-ttu-id="ea771-117">1. Instalar os plug-ins Microsoft 365 Moodle</span><span class="sxs-lookup"><span data-stu-id="ea771-117">1. Install the Microsoft 365 Moodle Plugins</span></span>

<span data-ttu-id="ea771-118">A integração de miojo no Microsoft Teams é alimentada pelo conjunto de [plug-ins Microsoft 365 Moodle de código aberto.](https://github.com/Microsoft/o365-moodle)</span><span class="sxs-lookup"><span data-stu-id="ea771-118">Moodle integration in Microsoft Teams is powered by the open source [Microsoft 365 Moodle plugins set](https://github.com/Microsoft/o365-moodle).</span></span>

### <a name="requisite-applications-and-plugins"></a><span data-ttu-id="ea771-119">Requisito de aplicativos e plug-ins</span><span class="sxs-lookup"><span data-stu-id="ea771-119">Requisite applications and plugins</span></span>

<span data-ttu-id="ea771-120">Certifique-se de instalar e baixar o seguinte antes de prosseguir com a instalação Microsoft 365 plug-ins Moodle:</span><span class="sxs-lookup"><span data-stu-id="ea771-120">Ensure to install and download the following before proceeding with the Microsoft 365 Moodle plugins installation:</span></span>

1. <span data-ttu-id="ea771-121">Certifique-se de instalar [uma versão estável atual do Moodle](https://download.moodle.org/releases/latest/).</span><span class="sxs-lookup"><span data-stu-id="ea771-121">Ensure to install a [current stable version of Moodle](https://download.moodle.org/releases/latest/).</span></span>

1. <span data-ttu-id="ea771-122">Baixe e salve o Moodle [OpenID Conexão](https://moodle.org/plugins/auth_oidc) e os [plug-ins Microsoft 365 Integration](https://moodle.org/plugins/local_o365) para o computador local.</span><span class="sxs-lookup"><span data-stu-id="ea771-122">Download and save the Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) and the [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) plugins to your local computer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea771-123">Instalar os plug-ins de integração Conexão Microsoft 365 OpenID são necessários para a integração Teams.</span><span class="sxs-lookup"><span data-stu-id="ea771-123">Installing the OpenID Connect and Microsoft 365 Integration plugins are required for the Teams integration.</span></span>
    >
    > <span data-ttu-id="ea771-124">Além disso, os [plug-ins Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) são altamente recomendados.</span><span class="sxs-lookup"><span data-stu-id="ea771-124">In addition, the [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) plugins is highly recommended.</span></span>

### <a name="microsoft-365-moodle-plugins"></a><span data-ttu-id="ea771-125">Microsoft 365 Plug-ins de moodle</span><span class="sxs-lookup"><span data-stu-id="ea771-125">Microsoft 365 Moodle plugins</span></span>

1. <span data-ttu-id="ea771-126">Entre no servidor Moodle como administrador e selecione **Administração** de site no bloco Configurações [localizado](https://docs.moodle.org/22/en/Settings_block) no painel de navegação esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ea771-126">Sign in to your Moodle server as an administrator and select **Site administration** from the [Settings block](https://docs.moodle.org/22/en/Settings_block) located in the left navigation panel.</span></span>

1. <span data-ttu-id="ea771-127">Selecione a **guia Plug-ins** e selecione **Instalar plug-ins**.</span><span class="sxs-lookup"><span data-stu-id="ea771-127">Select the **Plugins** tab, and then select **Install plugins**.</span></span>

1. <span data-ttu-id="ea771-128">Na seção **Instalar plug-ins do arquivo ZIP,** selecione **Escolher um arquivo**.</span><span class="sxs-lookup"><span data-stu-id="ea771-128">From the **Install plugins from ZIP file** section, select **Choose a file**.</span></span>

1. <span data-ttu-id="ea771-129">Selecione **Upload uma opção de** arquivo no painel de navegação esquerdo, procure o arquivo que você baixou e selecione Upload este **arquivo**.</span><span class="sxs-lookup"><span data-stu-id="ea771-129">Select **Upload a file** option from the left navigation panel, browse for the file that you downloaded, and select **Upload this file**.</span></span>

1. <span data-ttu-id="ea771-130">Selecione **Administração do site** no painel de navegação esquerdo para retornar ao painel de administração.</span><span class="sxs-lookup"><span data-stu-id="ea771-130">Select **Site administration** from the left navigation panel to return to your admin dashboard.</span></span> <span data-ttu-id="ea771-131">Role para baixo até os **plug-ins locais** e selecione o link **Microsoft 365 Integração.**</span><span class="sxs-lookup"><span data-stu-id="ea771-131">Scroll down to the **Local plugins** and select the **Microsoft 365 Integration** link.</span></span>

    > [!IMPORTANT]
    >
    > * <span data-ttu-id="ea771-132">Mantenha sua Microsoft 365 de configuração do Moodle Plugins aberta em uma guia de navegador separada, pois você precisa retornar a esse conjunto de páginas durante todo o processo.</span><span class="sxs-lookup"><span data-stu-id="ea771-132">Keep your Microsoft 365 Moodle Plugins configuration page open in a separate browser tab as you need to return to this set of pages throughout the process.</span></span>  
    >
    > * <span data-ttu-id="ea771-133">Se você não tiver um site Moodle existente, vá para o Moodle no repo do [Azure](https://github.com/azure/moodle) e implante rapidamente uma instância de Moodle e personalize-a de acordo com suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="ea771-133">If you do not have an existing Moodle site, go to the [Moodle on Azure](https://github.com/azure/moodle) repo, and quickly deploy a Moodle instance and customize it to your needs.</span></span>

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a><span data-ttu-id="ea771-134">2. Configure a conexão entre os plug-ins Microsoft 365 e Azure Active Directory (Azure AD)</span><span class="sxs-lookup"><span data-stu-id="ea771-134">2. Configure the connection between the Microsoft 365 plugins and Azure Active Directory (Azure AD)</span></span>

<span data-ttu-id="ea771-135">Você deve configurar a conexão entre os Microsoft 365 e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-135">You must configure the connection between the Microsoft 365 plugins and Azure AD.</span></span>

### <a name="requisites"></a><span data-ttu-id="ea771-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea771-136">Requisites</span></span>

<span data-ttu-id="ea771-137">Registre Moodle como um aplicativo no Azure AD, usando o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea771-137">Register Moodle as an application in your Azure AD, using the PowerShell script.</span></span> <span data-ttu-id="ea771-138">O script do Powershell provisiona o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ea771-138">The Powershell script provisions the following:</span></span>

* <span data-ttu-id="ea771-139">Um novo aplicativo do Azure AD para seu locatário Microsoft 365, que é usado pelo Microsoft 365 Plug-ins de m massa.</span><span class="sxs-lookup"><span data-stu-id="ea771-139">A new Azure AD application for your Microsoft 365 tenant, which is used by the Microsoft 365 Moodle Plugins.</span></span>
* <span data-ttu-id="ea771-140">O aplicativo para seu Microsoft 365 locatário, configurar as URLs e permissões de resposta necessárias para o aplicativo provisionado e retorna `AppID` o e `Key` .</span><span class="sxs-lookup"><span data-stu-id="ea771-140">The app for your Microsoft 365 tenant, set up the required reply URLs and permissions for the provisioned app, and returns the `AppID` and `Key`.</span></span>

<span data-ttu-id="ea771-141">Use a página de instalação de Plug-ins de miojo gerados e em sua página de instalação de Microsoft 365 Moodle para configurar seu site de servidor `AppID` `Key` Moodle com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-141">Use the generated `AppID` and `Key` in your Microsoft 365 Moodle Plugins setup page to configure your Moodle server site with Azure AD.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="ea771-142">O script do PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve concluir a configuração manualmente seguindo as etapas descritas nas páginas de versão Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2.](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release)</span><span class="sxs-lookup"><span data-stu-id="ea771-142">The PowerShell script is not updated with the latest configuration items, therefore, you must complete the configuration manually following the steps outlined in the Moodle [3.8.0.4 and 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) and [3.8.0.5 and 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) release pages.</span></span>
>
> * <span data-ttu-id="ea771-143">Para obter mais informações sobre como registrar sua instância Moodle manualmente, consulte [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span><span class="sxs-lookup"><span data-stu-id="ea771-143">For more information on registering your Moodle instance manually, see [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span></span>

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a><span data-ttu-id="ea771-144">A guia Moodle para Microsoft Teams de informações</span><span class="sxs-lookup"><span data-stu-id="ea771-144">The Moodle tab for Microsoft Teams information flow</span></span>

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. <span data-ttu-id="ea771-145">Na página Microsoft 365 Plug-ins de integração, selecione a **guia** Instalação.</span><span class="sxs-lookup"><span data-stu-id="ea771-145">From the Microsoft 365 Integration plugins page, select the **Setup** tab.</span></span>

1. <span data-ttu-id="ea771-146">Selecione o **botão Baixar Script do PowerShell** e salve-o como uma pasta ZIP no computador local.</span><span class="sxs-lookup"><span data-stu-id="ea771-146">Select the **Download PowerShell Script** button and save it as a ZIP folder to your local computer.</span></span>

1. <span data-ttu-id="ea771-147">Prepare o script do PowerShell do arquivo ZIP da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="ea771-147">Prepare the PowerShell script from the ZIP file as follows:</span></span> 

    1. <span data-ttu-id="ea771-148">Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.</span><span class="sxs-lookup"><span data-stu-id="ea771-148">Download and extract the `Moodle-AzureAD-Powershell.zip` file.</span></span>
    1. <span data-ttu-id="ea771-149">Abra a pasta extraída.</span><span class="sxs-lookup"><span data-stu-id="ea771-149">Open the extracted folder.</span></span>
    1. <span data-ttu-id="ea771-150">Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ea771-150">Right-click on the `Moodle-AzureAD-Script.ps1` file and select **Properties**.</span></span>
    1. <span data-ttu-id="ea771-151">Na guia **Geral** da janela Propriedades, selecione a caixa de seleção ao lado do atributo Security localizado `Unblock` na parte inferior da janela. </span><span class="sxs-lookup"><span data-stu-id="ea771-151">Under the **General** tab of the Properties window, select the `Unblock` checkbox next to the **Security** attribute located at the bottom of the window.</span></span>
    1. <span data-ttu-id="ea771-152">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea771-152">Select **OK**.</span></span>
    1. <span data-ttu-id="ea771-153">Copie o caminho do diretório para a pasta extraída.</span><span class="sxs-lookup"><span data-stu-id="ea771-153">Copy the directory path to the extracted folder.</span></span>

1. <span data-ttu-id="ea771-154">Execute o PowerShell como administrador:</span><span class="sxs-lookup"><span data-stu-id="ea771-154">Run PowerShell as an administrator:</span></span>

    1. <span data-ttu-id="ea771-155">Selecione Iniciar.</span><span class="sxs-lookup"><span data-stu-id="ea771-155">Select Start.</span></span>
    1. <span data-ttu-id="ea771-156">Digite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea771-156">Type PowerShell.</span></span>
    1. <span data-ttu-id="ea771-157">Clique com o botão direito **do mouse Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ea771-157">Right-click on **Windows PowerShell**.</span></span>
    1. <span data-ttu-id="ea771-158">Selecione **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="ea771-158">Select **Run as Administrator**.</span></span>

1. <span data-ttu-id="ea771-159">Navegue até o diretório desacortado digitando `cd .../.../Moodle-AzureAD-Powershell` onde está o caminho para o `.../...` diretório.</span><span class="sxs-lookup"><span data-stu-id="ea771-159">Navigate to the unzipped directory by typing `cd .../.../Moodle-AzureAD-Powershell` where `.../...` is the path to the directory.</span></span>

1. <span data-ttu-id="ea771-160">Execute o script do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ea771-160">Execute the PowerShell script:</span></span>

    1. <span data-ttu-id="ea771-161">Insira `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="ea771-161">Enter `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.</span></span>
    1. <span data-ttu-id="ea771-162">Insira `./Moodle-AzureAD-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ea771-162">Enter `./Moodle-AzureAD-Script.ps1`.</span></span>
    1. <span data-ttu-id="ea771-163">Entre na sua conta Microsoft 365 administrador na janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="ea771-163">Sign in to your Microsoft 365 administrator account in the pop-up window.</span></span>
    1. <span data-ttu-id="ea771-164">Insira o nome do Aplicativo do Azure AD, por exemplo, plug-ins Moodle ou Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-164">Enter the name of the Azure AD Application, for example, Moodle or Moodle plugins.</span></span>
    1. <span data-ttu-id="ea771-165">Insira a URL do servidor Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-165">Enter the URL for your Moodle server.</span></span>
    1. <span data-ttu-id="ea771-166">Copie a **ID do Aplicativo ( `AppID` ) e** **a Chave do Aplicativo( `Key` )** geradas pelo script e salve-as.</span><span class="sxs-lookup"><span data-stu-id="ea771-166">Copy the **Application ID (`AppID`)** and **Application Key(`Key`)** generated by the script and save them.</span></span>

1. <span data-ttu-id="ea771-167">Em seguida, você deve adicionar `AppID` o e ao Microsoft 365 `Key` Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="ea771-167">Next you must add the `AppID` and `Key` to the Microsoft 365 Moodle Plugins.</span></span> <span data-ttu-id="ea771-168">Volte para a página de administração de plug-ins, Administração do site > Plug-ins > Microsoft 365 Integração.</span><span class="sxs-lookup"><span data-stu-id="ea771-168">Return to the plugins administration page, Site administration > Plugins > Microsoft 365 Integration.</span></span>

1. <span data-ttu-id="ea771-169">Na guia **Instalação,** adicione o `AppID` e você `Key` copiou anteriormente e selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="ea771-169">On the **Setup** tab add the `AppID` and `Key` you copied previously, and then select **Save changes**.</span></span> <span data-ttu-id="ea771-170">Após a atualização da página, você pode ver uma nova seção **Escolher método de conexão**.</span><span class="sxs-lookup"><span data-stu-id="ea771-170">After the page refreshes, you can see a new section **Choose connection method**.</span></span>

1. <span data-ttu-id="ea771-171">No método **Escolher conexão,** selecione a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações novamente.**</span><span class="sxs-lookup"><span data-stu-id="ea771-171">In the **Choose connection method**, select the checkbox labeled **Default**, and then select **Save changes** again.</span></span>

1. <span data-ttu-id="ea771-172">Após a atualização da página, você pode ver outra nova seção Consentimento do **administrador & informações adicionais**.</span><span class="sxs-lookup"><span data-stu-id="ea771-172">After the page refreshes you can see another new section **Admin consent & additional information**.</span></span>
    1. <span data-ttu-id="ea771-173">Selecione **Fornecer o** link Fornecer Consentimento de Administrador, insira Microsoft 365 suas credenciais de Administrador Global e aceite conceder as permissões. </span><span class="sxs-lookup"><span data-stu-id="ea771-173">Select **Provide Admin Consent** link, enter your Microsoft 365 Global Administrator credentials, then **Accept** to grant the permissions.</span></span>
    1. <span data-ttu-id="ea771-174">Ao lado do **campo Locatário do Azure AD,** selecione o **botão Detectar.**</span><span class="sxs-lookup"><span data-stu-id="ea771-174">Next to the **Azure AD Tenant** field, select the **Detect** button.</span></span>
    1. <span data-ttu-id="ea771-175">Ao lado da **URL OneDrive for Business ,** selecione o botão **Detectar.**</span><span class="sxs-lookup"><span data-stu-id="ea771-175">Next to the **OneDrive for Business URL**, select the **Detect** button.</span></span>
    1. <span data-ttu-id="ea771-176">Depois que os campos preencherem, selecione o **botão Salvar alterações** novamente.</span><span class="sxs-lookup"><span data-stu-id="ea771-176">After the fields populate, select the **Save changes** button again.</span></span>

1. <span data-ttu-id="ea771-177">Selecione o **botão Atualizar** para verificar a instalação e, em seguida, selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="ea771-177">Select the **Update** button to verify the installation, and then select **Save changes**.</span></span>

1. <span data-ttu-id="ea771-178">Sincronizar usuários entre seu servidor Moodle e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-178">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="ea771-179">Para começar:</span><span class="sxs-lookup"><span data-stu-id="ea771-179">To get started:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea771-180">Dependendo do ambiente, você pode selecionar diferentes opções durante este estágio.</span><span class="sxs-lookup"><span data-stu-id="ea771-180">Depending on your environment, you can select different options during this stage.</span></span>

1. <span data-ttu-id="ea771-181">Sincronizar usuários entre seu servidor Moodle e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-181">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="ea771-182">Dependendo do ambiente, você pode selecionar diferentes opções durante este estágio.</span><span class="sxs-lookup"><span data-stu-id="ea771-182">Depending on your environment, you can select different options during this stage.</span></span> <span data-ttu-id="ea771-183">Para começar:</span><span class="sxs-lookup"><span data-stu-id="ea771-183">To get started:</span></span>
    1. <span data-ttu-id="ea771-184">Alternar para **a guia Sincronizar Configurações**.</span><span class="sxs-lookup"><span data-stu-id="ea771-184">Switch to the **Sync Settings tab**.</span></span>

    1. <span data-ttu-id="ea771-185">Na seção **Sincronizar usuários com o Azure AD,** selecione as caixas de seleção que se aplicam ao seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="ea771-185">In the **Sync users with Azure AD** section, select the checkboxes that apply to your environment.</span></span> <span data-ttu-id="ea771-186">Você deve selecionar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ea771-186">You must select the following:</span></span>  

        <span data-ttu-id="ea771-187">✔ Criar contas no Moodle para usuários no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-187">✔ Create accounts in Moodle for users in Azure AD.</span></span>

        <span data-ttu-id="ea771-188">✔ atualizar todas as contas no Moodle para usuários no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea771-188">✔ Update all accounts in Moodle for users in Azure AD.</span></span>

    1. <span data-ttu-id="ea771-189">Na seção **Restrição de** Criação de Usuário, você pode configurar um filtro para limitar os usuários do Azure AD sincronizados com moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-189">In the **User Creation Restriction** section, you can setup a filter to limit the Azure AD users that is synced to Moodle.</span></span>
    1. <span data-ttu-id="ea771-190">A **seção Mapeamento de** Campo do Usuário permite que você personalize o mapeamento de campo do Azure AD para Moodle User Profile.</span><span class="sxs-lookup"><span data-stu-id="ea771-190">The **User Field Mapping** section allows you to customize the Azure AD to Moodle User Profile field mapping.</span></span>
    1. <span data-ttu-id="ea771-191">Na seção **Teams Sincronização,** você pode selecionar para criar automaticamente Grupos, como equipes para alguns ou todos, de seus cursos de Moodle existentes.</span><span class="sxs-lookup"><span data-stu-id="ea771-191">In the **Teams Sync** section, you can select to automatically create Groups, such as teams for some, or all, of your existing Moodle courses.</span></span>

13. <span data-ttu-id="ea771-192">Para [validar trabalhos de](https://docs.moodle.org/310/en/Cron) cron e execute-os manualmente para a primeira executar, selecione o **link** da página Gerenciamento de tarefas agendadas na seção Sincronizar usuários com **o Azure AD.**</span><span class="sxs-lookup"><span data-stu-id="ea771-192">To validate [cron](https://docs.moodle.org/310/en/Cron) jobs and run them manually for the first run, select the **Scheduled tasks management page** link in the **Sync users with Azure AD** section.</span></span> <span data-ttu-id="ea771-193">Isso o leva à página **Tarefas Agendadas.**</span><span class="sxs-lookup"><span data-stu-id="ea771-193">This takes you to the **Scheduled Tasks** page.</span></span>

    1. <span data-ttu-id="ea771-194">Role para baixo e encontre o trabalho **Sincronizar usuários com o Azure AD** e selecione **Executar agora**.</span><span class="sxs-lookup"><span data-stu-id="ea771-194">Scroll down and find the **Sync users with Azure AD** job and select **Run now**.</span></span>
    1. <span data-ttu-id="ea771-195">Se você selecionar criar Grupos com base em cursos existentes, também poderá executar o trabalho Criar grupos de usuários **Microsoft 365.**</span><span class="sxs-lookup"><span data-stu-id="ea771-195">If you select to create Groups based on existing courses, you can also run the **Create user groups in Microsoft 365** job.</span></span>

    > [!NOTE]
    >
    > <span data-ttu-id="ea771-196">O Moodle [Cron](https://docs.moodle.org/310/en/Cron) é executado de acordo com o cronograma da tarefa.</span><span class="sxs-lookup"><span data-stu-id="ea771-196">The Moodle [Cron](https://docs.moodle.org/310/en/Cron) runs according to the task schedule.</span></span> <span data-ttu-id="ea771-197">O agendamento padrão é uma vez por dia.</span><span class="sxs-lookup"><span data-stu-id="ea771-197">The default schedule is once a day.</span></span> <span data-ttu-id="ea771-198">No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.</span><span class="sxs-lookup"><span data-stu-id="ea771-198">However, the cron must run more frequently to keep everything in sync.</span></span>

1. <span data-ttu-id="ea771-199">Retorne à página de administração de plug-ins, administração de **site > Plug-> Microsoft 365 Integração** e selecione a página **Teams Configurações.**</span><span class="sxs-lookup"><span data-stu-id="ea771-199">Return to the plugins administration page, **Site administration > Plugins > Microsoft 365 Integration**, and select the **Teams Settings** page.</span></span>

1. <span data-ttu-id="ea771-200">Na página **Teams Configurações,** configure as configurações necessárias para habilitar a integração Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea771-200">On the **Teams Settings** page, configure the required settings to enable the Teams app integration.</span></span>

    1. <span data-ttu-id="ea771-201">Para **habilitar o Conexão OpenID,** selecione o link **Gerenciar** Autenticação e selecione o ícone do olho na linha **Conexão OpenId** se estiver acinzentado.</span><span class="sxs-lookup"><span data-stu-id="ea771-201">To enable **OpenID Connect**, select the **Manage Authentication** link, and select the eye icon on the **OpenId Connect** line if it is greyed out.</span></span>
    1. <span data-ttu-id="ea771-202">Para habilitar a incorporação de quadro, selecione o link **Segurança HTTP** e selecione a caixa de seleção ao lado **de Permitir a incorporação de quadro**.</span><span class="sxs-lookup"><span data-stu-id="ea771-202">To enable frame embedding, select the **HTTP Security** link, and then select the checkbox next to **Allow frame embedding**.</span></span>
    1. <span data-ttu-id="ea771-203">Para habilitar os serviços Web, que habilitam os recursos da API Moodle, selecione o **link** Recursos Avançados e, em seguida, verifique se a caixa de seleção ao lado de Habilitar serviços **Web** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="ea771-203">To enable web services, which enables the Moodle API features, select the **Advanced Features** link, and then ensure the checkbox next to **Enable web services** is selected.</span></span>
    1. <span data-ttu-id="ea771-204">Para habilitar os serviços externos para Microsoft 365, selecione o link **Serviços externos** e, em seguida:</span><span class="sxs-lookup"><span data-stu-id="ea771-204">To enable the external services for Microsoft 365, select the **External services** link, and then:</span></span>  

        <span data-ttu-id="ea771-205">✔ Selecione **Editar** na **linha Moodle Microsoft 365 Webservices.**</span><span class="sxs-lookup"><span data-stu-id="ea771-205">✔ Select **Edit** on the **Moodle Microsoft 365 Webservices** row.</span></span>

        <span data-ttu-id="ea771-206">✔ Marque a caixa de seleção ao lado de **Habilitado** e, em seguida, **selecione Salvar Alterações**</span><span class="sxs-lookup"><span data-stu-id="ea771-206">✔ Select the checkbox next to **Enabled**, then select **Save Changes**</span></span>

    1. <span data-ttu-id="ea771-207">Edite suas permissões de usuário autenticadas para permitir que eles criem tokens de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ea771-207">Edit your authenticated user permissions to allow them to create web service tokens.</span></span>

        <span data-ttu-id="ea771-208">✔ Selecione o **link de usuário autenticado da função** de edição.</span><span class="sxs-lookup"><span data-stu-id="ea771-208">✔ Select the **Editing role Authenticated user** link.</span></span>

        <span data-ttu-id="ea771-209">✔ role para baixo e encontre **o recurso Criar** um token de serviço Web e selecione a caixa **de** seleção Permitir.</span><span class="sxs-lookup"><span data-stu-id="ea771-209">✔ Scroll down and find the **Create a web service token** capability and select the **Allow** checkbox.</span></span>

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a><span data-ttu-id="ea771-210">3. Implantar o Moodle Assistant Bot no Azure</span><span class="sxs-lookup"><span data-stu-id="ea771-210">3. Deploy the Moodle Assistant Bot to Azure</span></span>

<span data-ttu-id="ea771-211">O bot de assistente de miojo gratuito para Microsoft Teams ajuda professores e alunos a responder a perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-211">The free Moodle assistant bot for Microsoft Teams helps teachers and students answer questions about their courses, assignments, grades, and other information in Moodle.</span></span> <span data-ttu-id="ea771-212">O bot também envia notificações Moodle para alunos e professores no Teams.</span><span class="sxs-lookup"><span data-stu-id="ea771-212">The bot also sends Moodle notifications to students and teachers within Teams.</span></span> <span data-ttu-id="ea771-213">O bot é um projeto de código aberto mantido pela Microsoft e está disponível [no](https://github.com/microsoft/Moodle-Teams-Bot)GitHub .</span><span class="sxs-lookup"><span data-stu-id="ea771-213">The bot is an open-source project maintained by Microsoft, and is available on [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).</span></span>

> [!NOTE]
>
> * <span data-ttu-id="ea771-214">Implante recursos em sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="ea771-214">Deploy resources to your Azure subscription.</span></span> <span data-ttu-id="ea771-215">Todos os recursos foram configurados usando a **camada** gratuita.</span><span class="sxs-lookup"><span data-stu-id="ea771-215">All resources were configured using the **free** tier.</span></span> <span data-ttu-id="ea771-216">Dependendo do uso do bot, você pode ter que dimensionar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="ea771-216">Depending on the usage of your bot, you may have to scale these resources.</span></span>
>
> * <span data-ttu-id="ea771-217">Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).</span><span class="sxs-lookup"><span data-stu-id="ea771-217">To use the Moodle tab without the bot, skip to [4](#4-deploy-your-microsoft-teams-app).</span></span>

### <a name="moodle-bot-information-flow"></a><span data-ttu-id="ea771-218">Fluxo de informações de bot de miojo</span><span class="sxs-lookup"><span data-stu-id="ea771-218">Moodle bot information flow</span></span>

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

<span data-ttu-id="ea771-219">Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade da Microsoft.](https://identity.microsoft.com/Landing)</span><span class="sxs-lookup"><span data-stu-id="ea771-219">To install the bot, you must register it on the [Microsoft Identity Platform](https://identity.microsoft.com/Landing).</span></span> <span data-ttu-id="ea771-220">Isso permite que o bot se autenture nos pontos de extremidade da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea771-220">This allows your bot to authenticate against your Microsoft endpoints.</span></span> 

<span data-ttu-id="ea771-221">**Para registrar seu bot**</span><span class="sxs-lookup"><span data-stu-id="ea771-221">**To register your bot**</span></span>

1. <span data-ttu-id="ea771-222">Vá para a página de administração de plug-ins e selecione **Plug-ins**.</span><span class="sxs-lookup"><span data-stu-id="ea771-222">Go to the plugins administration page, and then select **Plugins**.</span></span> <span data-ttu-id="ea771-223">Em **Microsoft 365 Integração**, selecione a **guia Teams Configurações.**</span><span class="sxs-lookup"><span data-stu-id="ea771-223">Under **Microsoft 365 Integration**, select the **Teams Settings** tab.</span></span>

1. <span data-ttu-id="ea771-224">Selecione o link do Portal de Registro de **Aplicativos** da Microsoft e entre com sua ID da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea771-224">Select the **Microsoft Application Registration Portal** link and sign in with your Microsoft ID.</span></span>

1. <span data-ttu-id="ea771-225">Insira um nome para seu aplicativo, como MoodleBot e selecione o **botão Criar.**</span><span class="sxs-lookup"><span data-stu-id="ea771-225">Enter a name for your app, such as MoodleBot and select the **Create** button.</span></span>

1. <span data-ttu-id="ea771-226">Copie a **ID do** Aplicativo e a colar no campo **ID** do Aplicativo Bot na **página Equipe Configurações.**</span><span class="sxs-lookup"><span data-stu-id="ea771-226">Copy the **Application ID** and paste it into the **Bot Application ID** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="ea771-227">Selecione o **botão Gerar Nova Senha.**</span><span class="sxs-lookup"><span data-stu-id="ea771-227">Select the **Generate New Password** button.</span></span> <span data-ttu-id="ea771-228">Copie a senha gerada e a colar no campo Senha do Aplicativo **Bot** na **página Configurações** Equipe.</span><span class="sxs-lookup"><span data-stu-id="ea771-228">Copy the generated password and and paste it into the **Bot Application Password** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="ea771-229">Role até a parte inferior do formulário e selecione **Salvar Alterações**.</span><span class="sxs-lookup"><span data-stu-id="ea771-229">Scroll to the bottom of the form and select **Save Changes**.</span></span>

<span data-ttu-id="ea771-230">Depois de gerar a ID e a senha do aplicativo, implante seu bot no Azure:</span><span class="sxs-lookup"><span data-stu-id="ea771-230">After generating your application ID and password, deploy your bot to Azure:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ea771-231">Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como a ID do Aplicativo Bot, a Senha do Aplicativo Bot e o Segredo do Moodle na página **Teams Configurações.**</span><span class="sxs-lookup"><span data-stu-id="ea771-231">Select **Deploy to Azure** and complete the form with the necessary information, such as the Bot Application ID, Bot Application Password, and the Moodle Secret on the **Teams Settings** page.</span></span> <span data-ttu-id="ea771-232">As informações do Azure estão na página **Instalação.**</span><span class="sxs-lookup"><span data-stu-id="ea771-232">The Azure information is on the **Setup** page.</span></span> 
> * <span data-ttu-id="ea771-233">Depois de concluir o formulário, selecione a caixa de seleção para concordar com os termos e condições.</span><span class="sxs-lookup"><span data-stu-id="ea771-233">After completing the form, select the checkbox to agree to the terms and conditions.</span></span>
> * <span data-ttu-id="ea771-234">Selecione **Comprar**.</span><span class="sxs-lookup"><span data-stu-id="ea771-234">Select **Purchase**.</span></span> <span data-ttu-id="ea771-235">Todos os recursos do Azure são implantados na camada gratuita.</span><span class="sxs-lookup"><span data-stu-id="ea771-235">All Azure resources are deployed to the free tier.</span></span>

<span data-ttu-id="ea771-236">Após a conclusão da implantação dos recursos no Azure, você deve configurar os plug-ins Microsoft 365 Moodle com um ponto de extremidade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ea771-236">After the resources have completed deploying to Azure, you must configure the Microsoft 365 Moodle plugins with a messaging endpoint.</span></span> <span data-ttu-id="ea771-237">Você deve obter o ponto de extremidade do bot no Azure:</span><span class="sxs-lookup"><span data-stu-id="ea771-237">You must get the endpoint from your bot in Azure:</span></span>

1. <span data-ttu-id="ea771-238">Entre no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ea771-238">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

1. <span data-ttu-id="ea771-239">No painel esquerdo, selecione **Grupos** de recursos e selecione o grupo de recursos que você usou ou criou ao implantar o bot.</span><span class="sxs-lookup"><span data-stu-id="ea771-239">In the left pane, select **Resource groups** and select the resource group you used or created, while deploying your bot.</span></span>

1. <span data-ttu-id="ea771-240">Selecione o **recurso Bot do WebApp** na lista de recursos no grupo.</span><span class="sxs-lookup"><span data-stu-id="ea771-240">Select the **WebApp Bot** resource from the list of resources in the group.</span></span>

1. <span data-ttu-id="ea771-241">Copie o **Ponto de Extremidade de Mensagens** da seção **Visão** Geral.</span><span class="sxs-lookup"><span data-stu-id="ea771-241">Copy the **Messaging Endpoint** from the **Overview** section.</span></span>

1. <span data-ttu-id="ea771-242">No Moodle, abra a **página Equipe Configurações** do seu Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="ea771-242">In Moodle, open the **Team Settings** page of your Microsoft 365 Moodle Plugins.</span></span>

1. <span data-ttu-id="ea771-243">No campo **Ponto de Extremidade bot,** cole a URL que você acabou de copiar e altere as mensagens *de* palavra para *webhook*.</span><span class="sxs-lookup"><span data-stu-id="ea771-243">In the **Bot Endpoint** field paste the URL you just copied and change the word *messages* to *webhook*.</span></span> <span data-ttu-id="ea771-244">A URL deve aparecer da seguinte forma: `https://botname.azurewebsites.net/api/webhook`</span><span class="sxs-lookup"><span data-stu-id="ea771-244">The URL must appear as follows: `https://botname.azurewebsites.net/api/webhook`</span></span>

1. <span data-ttu-id="ea771-245">Selecione **Salvar Alterações**.</span><span class="sxs-lookup"><span data-stu-id="ea771-245">Select **Save Changes**.</span></span>

1. <span data-ttu-id="ea771-246">Depois de salvar as alterações, volte para a guia **Equipe** Configurações, selecione o botão **Baixar** arquivo de manifesto e salve o pacote de manifesto do aplicativo em seu computador para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="ea771-246">After saving the changes, go back to the **Team Settings** tab, select the **Download manifest file** button, and save the app manifest package to your computer for further use.</span></span>

## <a name="4-deploy-your-microsoft-teams-app"></a><span data-ttu-id="ea771-247">4. Implante seu aplicativo Microsoft Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea771-247">4. Deploy your Microsoft Teams app</span></span>

<span data-ttu-id="ea771-248">Depois que seu bot foi implantado no Azure e configurado para falar com seu servidor Moodle, você deve implantar seu Microsoft Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea771-248">After your bot deployed to Azure and configured to talk to your Moodle server, you must deploy your Microsoft Teams app.</span></span> <span data-ttu-id="ea771-249">Para fazer isso, você deve carregar o arquivo de manifesto do aplicativo que você baixou da página Microsoft 365 Moodle Plugins Team Configurações página na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="ea771-249">To do this you must load the app manifest file that you downloaded from the Microsoft 365 Moodle Plugins Team Settings page in the previous step.</span></span>

<span data-ttu-id="ea771-250">Antes de instalar o aplicativo, você deve garantir a habilitação de aplicativos externos e o carregamento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ea771-250">Before you install the app you must ensure to enable external apps and uploading of apps.</span></span> <span data-ttu-id="ea771-251">Para obter mais informações, [consulte Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="ea771-251">For more information, see [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span> 

<span data-ttu-id="ea771-252">**Para implantar seu aplicativo**</span><span class="sxs-lookup"><span data-stu-id="ea771-252">**To deploy your app**</span></span> 

1. <span data-ttu-id="ea771-253">Abra **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="ea771-253">Open **Microsoft Teams**.</span></span> 

1. <span data-ttu-id="ea771-254">Selecione o **ícone aplicativo** na área inferior esquerda da barra de navegação.</span><span class="sxs-lookup"><span data-stu-id="ea771-254">Select the **App** icon on the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="ea771-255">Selecione o Upload um link **de aplicativo** personalizado na lista de opções.</span><span class="sxs-lookup"><span data-stu-id="ea771-255">Select the **Upload a custom app** link from the list of options.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ea771-256">Se você estiver conectado como um administrador global, deverá ter a opção de carregar o aplicativo no catálogo de aplicativos da sua organização, caso contrário, você só poderá carregar o aplicativo para uma equipe na qual você é membro.</span><span class="sxs-lookup"><span data-stu-id="ea771-256">If you are logged in as a global administrator, you must have the option of uploading the app to your organization's app catalog, otherwise you can only load the app for a team in which you are a member.</span></span>

4. <span data-ttu-id="ea771-257">Selecione o `manifest.zip` pacote que você baixou anteriormente e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="ea771-257">Select the `manifest.zip` package you downloaded previously and select **Save**.</span></span> <span data-ttu-id="ea771-258">Se você não tiver baixado o pacote de manifesto do aplicativo, poderá baixar Configurações guia **Equipe** da página de configuração de plug-ins no Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-258">If you have not downloaded the app manifest package, you can download from the **Team Settings** tab of the plugins configuration page in Moodle.</span></span>

<span data-ttu-id="ea771-259">Agora que você tem o aplicativo instalado, você pode adicionar a guia a qualquer canal ao que tiver acesso.</span><span class="sxs-lookup"><span data-stu-id="ea771-259">Now that you have the app installed, you can add the tab to any channel that you have access to.</span></span> <span data-ttu-id="ea771-260">Para fazer isso, navegue até o canal, selecione o símbolo **mais** (➕) e selecione seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="ea771-260">To do so, navigate to the channel, select the **plus** (➕) symbol and select your app from the list.</span></span> <span data-ttu-id="ea771-261">Siga os prompts para concluir a adição de sua guia de curso miojo a um canal.</span><span class="sxs-lookup"><span data-stu-id="ea771-261">Follow the prompts to finish adding your Moodle course tab to a channel.</span></span>

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a><span data-ttu-id="ea771-262">5. Permitir a criação automática de guias Moodle no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ea771-262">5. Allow automatic creation of Moodle tabs in Microsoft Teams</span></span>

<span data-ttu-id="ea771-263">Embora as guias Moodle sejam criadas manualmente no Microsoft Teams, você pode decidir crie-as automaticamente quando as equipes são criadas a partir da sincronização do curso.</span><span class="sxs-lookup"><span data-stu-id="ea771-263">Although the Moodle tabs are created manually in Microsoft Teams, you can decide to create them automatically when teams are created from course synchronization.</span></span> <span data-ttu-id="ea771-264">Para fazer isso, você deve configurar a ID do aplicativo Microsoft Teams carregado no Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-264">To do this, you must configure the ID of the uploaded Microsoft Teams app in Moodle.</span></span>

<span data-ttu-id="ea771-265">**Para permitir a criação automática de guias Moodle**</span><span class="sxs-lookup"><span data-stu-id="ea771-265">**To allow automatic creation of Moodle tabs**</span></span>

1. <span data-ttu-id="ea771-266">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ea771-266">Open Microsoft Teams.</span></span>

1. <span data-ttu-id="ea771-267">Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.</span><span class="sxs-lookup"><span data-stu-id="ea771-267">Select the Apps icon from the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="ea771-268">Localize o aplicativo **Moodle** carregado > selecione o ícone **de** opções > selecione **copiar link**.</span><span class="sxs-lookup"><span data-stu-id="ea771-268">Locate the uploaded **Moodle app** > select the **options** icon > select **copy link**.</span></span>

1. <span data-ttu-id="ea771-269">Em um editor de texto, colar o conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="ea771-269">In a text editor, paste the copied content.</span></span> <span data-ttu-id="ea771-270">Ele deve conter uma URL como ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span><span class="sxs-lookup"><span data-stu-id="ea771-270">It must contain a URL such as ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span></span> <span data-ttu-id="ea771-271">Copie a última parte da URL, como , que é a `00112233-4455-6677-8899-aabbccddeeff` ID do Microsoft Teams app.</span><span class="sxs-lookup"><span data-stu-id="ea771-271">Copy the last part of the URL, such as  `00112233-4455-6677-8899-aabbccddeeff`, which is the ID of the Microsoft Teams app.</span></span>

1. <span data-ttu-id="ea771-272">No Moodle, abra **a guia Teams aplicativo Moodle** na página de configuração Microsoft 365 Plug-ins de Moodle.</span><span class="sxs-lookup"><span data-stu-id="ea771-272">In Moodle, open the **Teams Moodle app** tab from your Microsoft 365 Moodle Plugins configuration page.</span></span>

1. <span data-ttu-id="ea771-273">Colar a ID do aplicativo Microsoft Teams no campo ID do aplicativo Moodle e salvar alterações.</span><span class="sxs-lookup"><span data-stu-id="ea771-273">Paste the ID of the Microsoft Teams app into the Moodle app ID field, and save changes.</span></span>

<span data-ttu-id="ea771-274">Quando um curso Moodle é sincronizado, o Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral do Teams e o configura para conter a página de curso do curso Moodle a partir do qual ele é sincronizado.</span><span class="sxs-lookup"><span data-stu-id="ea771-274">When a Moodle course is synced, Microsoft Teams automatically installs the Moodle app in the team, creates a Moodle tab in the General channel of Teams, and configures it to contain the course page for the Moodle course from which it is synced.</span></span> <span data-ttu-id="ea771-275">Agora você pode começar a trabalhar com seus cursos de miojo diretamente Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ea771-275">You can now start working with your Moodle courses directly from Microsoft Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="ea771-276">Para compartilhar qualquer solicitação de recurso ou comentários conosco, visite nossa [página user voice](https://microsoftteams.uservoice.com/forums/916759-moodle).</span><span class="sxs-lookup"><span data-stu-id="ea771-276">To share any feature requests or feedback with us, visit our [User Voice page](https://microsoftteams.uservoice.com/forums/916759-moodle).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea771-277">Confira também</span><span class="sxs-lookup"><span data-stu-id="ea771-277">See also</span></span>

- [<span data-ttu-id="ea771-278">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="ea771-278">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
- [<span data-ttu-id="ea771-279">Moodle</span><span class="sxs-lookup"><span data-stu-id="ea771-279">Moodle</span></span>](https://moodle.org/)
- <span data-ttu-id="ea771-280">[Documentação de miojo](https://docs.moodle.org/34/en/Installing_plugins).</span><span class="sxs-lookup"><span data-stu-id="ea771-280">[Moodle documentation](https://docs.moodle.org/34/en/Installing_plugins).</span></span>

