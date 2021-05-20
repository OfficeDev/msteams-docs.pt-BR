---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração Moodle para Microsoft Teams
keywords: Teams Plugins de integração de aplicativos Moodle
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: d7fddad80ca08fd4ca8dee352cdcbc46e8e97dcd
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566716"
---
# <a name="install-moodle-lms"></a><span data-ttu-id="d9b19-104">Instalar o Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="d9b19-104">Install Moodle LMS</span></span>

<span data-ttu-id="d9b19-105">Neste artigo você aprenderá como instalar o Moodle LMS.</span><span class="sxs-lookup"><span data-stu-id="d9b19-105">In this article you'll learn how to install the Moodle LMS.</span></span>

> [!NOTE]
> <span data-ttu-id="d9b19-106">Para ajudar os administradores de TI a configurar facilmente o Moodle e a integração Teams, o Microsoft 365 Moodle Plugins de código aberto é atualizado para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9b19-106">To help IT admins to easily set-up Moodle and Teams integration, open-source Microsoft 365 Moodle Plugins is updated for the following:</span></span>
>
> * <span data-ttu-id="d9b19-107">Registro automático do seu servidor Moodle com [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="d9b19-107">Auto-registration of your Moodle server with [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span></span>
>
> * <span data-ttu-id="d9b19-108">Implantação de um clique do seu bot Moodle Assistant para o Azure.</span><span class="sxs-lookup"><span data-stu-id="d9b19-108">One-click deployment of your Moodle Assistant bot to Azure.</span></span>
>
> * <span data-ttu-id="d9b19-109">Auto-provisionamento de equipes e sincronização automática de matrículas em equipe para todos ou cursos de Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-109">Auto-provisioning of teams and auto-synchronization of team enrollments for all or select Moodle courses.</span></span>
>
> * <span data-ttu-id="d9b19-110">Instalação automática da guia Moodle e do bot assistente Moodle em cada equipe sincronizada.</span><span class="sxs-lookup"><span data-stu-id="d9b19-110">Auto-installation of the Moodle tab and the Moodle assistant bot into each synchronized team.</span></span>
>
> <span data-ttu-id="d9b19-111">Para saber mais sobre a funcionalidade que essa integração proporciona, consulte [Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).</span><span class="sxs-lookup"><span data-stu-id="d9b19-111">To learn more about the functionality this integration provides, see [Microsoft Teams and Moodle](https://education.microsoft.com/resource/3dffb3a8).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9b19-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d9b19-112">Prerequisites</span></span>

<span data-ttu-id="d9b19-113">A seguir estão os pré-requisitos para instalar o Moodle:</span><span class="sxs-lookup"><span data-stu-id="d9b19-113">Following are the prerequisites to install Moodle:</span></span>

* <span data-ttu-id="d9b19-114">Credenciais de administrador moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-114">Moodle administrator credentials.</span></span>

* <span data-ttu-id="d9b19-115">Credenciais de administrador azure ad.</span><span class="sxs-lookup"><span data-stu-id="d9b19-115">Azure AD administrator credentials.</span></span>

* <span data-ttu-id="d9b19-116">Uma assinatura do Azure onde você pode criar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="d9b19-116">An Azure subscription where you can create new resources.</span></span>

## <a name="1-install-the-microsoft-365-moodle-plugins"></a><span data-ttu-id="d9b19-117">1. Instale os plugins moodle Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d9b19-117">1. Install the Microsoft 365 Moodle Plugins</span></span>

<span data-ttu-id="d9b19-118">A integração moodle no Microsoft Teams é alimentada pelo conjunto de [plugins Moodle de](https://github.com/Microsoft/o365-moodle)código aberto Microsoft 365 .</span><span class="sxs-lookup"><span data-stu-id="d9b19-118">Moodle integration in Microsoft Teams is powered by the open source [Microsoft 365 Moodle plugins set](https://github.com/Microsoft/o365-moodle).</span></span>

### <a name="requisite-applications-and-plugins"></a><span data-ttu-id="d9b19-119">Aplicativos e plugins necessários</span><span class="sxs-lookup"><span data-stu-id="d9b19-119">Requisite applications and plugins</span></span>

<span data-ttu-id="d9b19-120">Certifique-se de instalar e baixar o seguinte antes de prosseguir com a instalação de plugins Microsoft 365 Moodle:</span><span class="sxs-lookup"><span data-stu-id="d9b19-120">Ensure to install and download the following before proceeding with the Microsoft 365 Moodle plugins installation:</span></span>

1. <span data-ttu-id="d9b19-121">Certifique-se de instalar uma [versão estável atual do Moodle](https://download.moodle.org/releases/latest/).</span><span class="sxs-lookup"><span data-stu-id="d9b19-121">Ensure to install a [current stable version of Moodle](https://download.moodle.org/releases/latest/).</span></span>

1. <span data-ttu-id="d9b19-122">Baixe e salve os Conexão Moodle [OpenID](https://moodle.org/plugins/auth_oidc) e os plugins [de Integração Microsoft 365](https://moodle.org/plugins/local_o365) para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="d9b19-122">Download and save the Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) and the [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) plugins to your local computer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9b19-123">A instalação dos plugins de integração Conexão e Microsoft 365 do OpenID é necessária para a integração Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-123">Installing the OpenID Connect and Microsoft 365 Integration plugins are required for the Teams integration.</span></span>
    >
    > <span data-ttu-id="d9b19-124">Além disso, os plugins [temáticos Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) são altamente recomendados.</span><span class="sxs-lookup"><span data-stu-id="d9b19-124">In addition, the [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) plugins is highly recommended.</span></span>

### <a name="microsoft-365-moodle-plugins"></a><span data-ttu-id="d9b19-125">Microsoft 365 Plugins moodle</span><span class="sxs-lookup"><span data-stu-id="d9b19-125">Microsoft 365 Moodle plugins</span></span>

1. <span data-ttu-id="d9b19-126">Faça login no servidor Moodle como administrador e selecione **a administração** do site no [bloco Configurações](https://docs.moodle.org/22/en/Settings_block) localizado no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="d9b19-126">Sign in to your Moodle server as an administrator and select **Site administration** from the [Settings block](https://docs.moodle.org/22/en/Settings_block) located in the left navigation panel.</span></span>

1. <span data-ttu-id="d9b19-127">Selecione a guia **Plugins** e selecione **Instalar plugins**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-127">Select the **Plugins** tab, and then select **Install plugins**.</span></span>

1. <span data-ttu-id="d9b19-128">Na **seção Instalar plugins da** seção de arquivos ZIP, selecione **Escolher um arquivo**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-128">From the **Install plugins from ZIP file** section, select **Choose a file**.</span></span>

1. <span data-ttu-id="d9b19-129">Selecione **Upload uma** opção de arquivo no painel de navegação esquerdo, navegue pelo arquivo que você baixou e selecione Upload este **arquivo**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-129">Select **Upload a file** option from the left navigation panel, browse for the file that you downloaded, and select **Upload this file**.</span></span>

1. <span data-ttu-id="d9b19-130">Selecione **a administração** do site no painel de navegação esquerdo para retornar ao painel de administração.</span><span class="sxs-lookup"><span data-stu-id="d9b19-130">Select **Site administration** from the left navigation panel to return to your admin dashboard.</span></span> <span data-ttu-id="d9b19-131">Desça até os **plugins locais** e selecione o link **Microsoft 365 Integração.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-131">Scroll down to the **Local plugins** and select the **Microsoft 365 Integration** link.</span></span>

    > [!IMPORTANT]
    >
    > * <span data-ttu-id="d9b19-132">Mantenha sua página de configuração Microsoft 365 Moodle Plugins aberta em uma guia de navegador separada, pois você precisa retornar a este conjunto de páginas durante todo o processo.</span><span class="sxs-lookup"><span data-stu-id="d9b19-132">Keep your Microsoft 365 Moodle Plugins configuration page open in a separate browser tab as you need to return to this set of pages throughout the process.</span></span>  
    >
    > * <span data-ttu-id="d9b19-133">Se você não tiver um site moodle existente, vá para o [Moodle on Azure](https://github.com/azure/moodle) repo e implante rapidamente uma instância moodle e personalize-a às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="d9b19-133">If you do not have an existing Moodle site, go to the [Moodle on Azure](https://github.com/azure/moodle) repo, and quickly deploy a Moodle instance and customize it to your needs.</span></span>

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a><span data-ttu-id="d9b19-134">2. Configure a conexão entre os plugins Microsoft 365 e Azure Active Directory (Azure AD)</span><span class="sxs-lookup"><span data-stu-id="d9b19-134">2. Configure the connection between the Microsoft 365 plugins and Azure Active Directory (Azure AD)</span></span>

<span data-ttu-id="d9b19-135">Você deve configurar a conexão entre os plugins Microsoft 365 e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-135">You must configure the connection between the Microsoft 365 plugins and Azure AD.</span></span>

### <a name="requisites"></a><span data-ttu-id="d9b19-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9b19-136">Requisites</span></span>

<span data-ttu-id="d9b19-137">Registre moodle como um aplicativo em seu Azure AD, usando o script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9b19-137">Register Moodle as an application in your Azure AD, using the PowerShell script.</span></span> <span data-ttu-id="d9b19-138">O script Powershell fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9b19-138">The Powershell script provisions the following:</span></span>

* <span data-ttu-id="d9b19-139">Um novo aplicativo Azure AD para seu inquilino Microsoft 365, que é usado pelo Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="d9b19-139">A new Azure AD application for your Microsoft 365 tenant, which is used by the Microsoft 365 Moodle Plugins.</span></span>
* <span data-ttu-id="d9b19-140">O aplicativo para o seu inquilino Microsoft 365, configure as URLs de resposta necessárias e as permissões para o aplicativo provisionado e devote o `AppID` e `Key` .</span><span class="sxs-lookup"><span data-stu-id="d9b19-140">The app for your Microsoft 365 tenant, set up the required reply URLs and permissions for the provisioned app, and returns the `AppID` and `Key`.</span></span>

<span data-ttu-id="d9b19-141">Use a página de configuração gerada `AppID` e em sua Microsoft 365 `Key` Moodle Plugins para configurar seu site de servidor Moodle com Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-141">Use the generated `AppID` and `Key` in your Microsoft 365 Moodle Plugins setup page to configure your Moodle server site with Azure AD.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="d9b19-142">O script PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve completar a configuração manualmente seguindo as etapas descritas nas páginas de versão Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2.](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release)</span><span class="sxs-lookup"><span data-stu-id="d9b19-142">The PowerShell script is not updated with the latest configuration items, therefore, you must complete the configuration manually following the steps outlined in the Moodle [3.8.0.4 and 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) and [3.8.0.5 and 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) release pages.</span></span>
>
> * <span data-ttu-id="d9b19-143">Para obter mais informações sobre o registro manual da sua instância Moodle, consulte [Registrar sua instância Moodle como um aplicativo](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span><span class="sxs-lookup"><span data-stu-id="d9b19-143">For more information on registering your Moodle instance manually, see [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span></span>

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a><span data-ttu-id="d9b19-144">A guia Moodle para Microsoft Teams fluxo de informações</span><span class="sxs-lookup"><span data-stu-id="d9b19-144">The Moodle tab for Microsoft Teams information flow</span></span>

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. <span data-ttu-id="d9b19-145">Na página Microsoft 365 plugins Integração, selecione a guia **Configuração.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-145">From the Microsoft 365 Integration plugins page, select the **Setup** tab.</span></span>

1. <span data-ttu-id="d9b19-146">Selecione o botão **Download PowerShell Script** e salve-o como uma pasta ZIP para o computador local.</span><span class="sxs-lookup"><span data-stu-id="d9b19-146">Select the **Download PowerShell Script** button and save it as a ZIP folder to your local computer.</span></span>

1. <span data-ttu-id="d9b19-147">Prepare o script PowerShell do arquivo ZIP da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d9b19-147">Prepare the PowerShell script from the ZIP file as follows:</span></span> 

    1. <span data-ttu-id="d9b19-148">Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.</span><span class="sxs-lookup"><span data-stu-id="d9b19-148">Download and extract the `Moodle-AzureAD-Powershell.zip` file.</span></span>
    1. <span data-ttu-id="d9b19-149">Abra a pasta extraída.</span><span class="sxs-lookup"><span data-stu-id="d9b19-149">Open the extracted folder.</span></span>
    1. <span data-ttu-id="d9b19-150">Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-150">Right-click on the `Moodle-AzureAD-Script.ps1` file and select **Properties**.</span></span>
    1. <span data-ttu-id="d9b19-151">Na guia **Geral** da janela Propriedades, selecione a caixa de `Unblock` seleção ao lado do atributo **Segurança** localizado na parte inferior da janela.</span><span class="sxs-lookup"><span data-stu-id="d9b19-151">Under the **General** tab of the Properties window, select the `Unblock` checkbox next to the **Security** attribute located at the bottom of the window.</span></span>
    1. <span data-ttu-id="d9b19-152">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-152">Select **OK**.</span></span>
    1. <span data-ttu-id="d9b19-153">Copie o caminho do diretório para a pasta extraída.</span><span class="sxs-lookup"><span data-stu-id="d9b19-153">Copy the directory path to the extracted folder.</span></span>

1. <span data-ttu-id="d9b19-154">Execute o PowerShell como administrador:</span><span class="sxs-lookup"><span data-stu-id="d9b19-154">Run PowerShell as an administrator:</span></span>

    1. <span data-ttu-id="d9b19-155">Selecione Iniciar.</span><span class="sxs-lookup"><span data-stu-id="d9b19-155">Select Start.</span></span>
    1. <span data-ttu-id="d9b19-156">Digite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9b19-156">Type PowerShell.</span></span>
    1. <span data-ttu-id="d9b19-157">Clique com o botão direito do mouse **em Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-157">Right-click on **Windows PowerShell**.</span></span>
    1. <span data-ttu-id="d9b19-158">Selecione **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-158">Select **Run as Administrator**.</span></span>

1. <span data-ttu-id="d9b19-159">Navegue até o diretório descompactado digitando `cd .../.../Moodle-AzureAD-Powershell` onde está o caminho para o `.../...` diretório.</span><span class="sxs-lookup"><span data-stu-id="d9b19-159">Navigate to the unzipped directory by typing `cd .../.../Moodle-AzureAD-Powershell` where `.../...` is the path to the directory.</span></span>

1. <span data-ttu-id="d9b19-160">Execute o script PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d9b19-160">Execute the PowerShell script:</span></span>

    1. <span data-ttu-id="d9b19-161">Entre `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="d9b19-161">Enter `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.</span></span>
    1. <span data-ttu-id="d9b19-162">Entre `./Moodle-AzureAD-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d9b19-162">Enter `./Moodle-AzureAD-Script.ps1`.</span></span>
    1. <span data-ttu-id="d9b19-163">Faça login na sua conta de administrador Microsoft 365 na janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="d9b19-163">Sign in to your Microsoft 365 administrator account in the pop-up window.</span></span>
    1. <span data-ttu-id="d9b19-164">Digite o nome do aplicativo Azure AD, por exemplo, plugins Moodle ou Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-164">Enter the name of the Azure AD Application, for example, Moodle or Moodle plugins.</span></span>
    1. <span data-ttu-id="d9b19-165">Digite a URL do servidor Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-165">Enter the URL for your Moodle server.</span></span>
    1. <span data-ttu-id="d9b19-166">Copie o ID do **aplicativo ( `AppID` )** e a **chave de aplicativo( `Key` )** gerado pelo script e salve-os.</span><span class="sxs-lookup"><span data-stu-id="d9b19-166">Copy the **Application ID (`AppID`)** and **Application Key(`Key`)** generated by the script and save them.</span></span>

1. <span data-ttu-id="d9b19-167">Em seguida, você deve adicionar o `AppID` e `Key` ao Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="d9b19-167">Next you must add the `AppID` and `Key` to the Microsoft 365 Moodle Plugins.</span></span> <span data-ttu-id="d9b19-168">Retorne à página de administração de plugins, administração do site > Plugins > Microsoft 365 Integration.</span><span class="sxs-lookup"><span data-stu-id="d9b19-168">Return to the plugins administration page, Site administration > Plugins > Microsoft 365 Integration.</span></span>

1. <span data-ttu-id="d9b19-169">Na guia **Configuração** adicione a `AppID` e `Key` copiou anteriormente e, em seguida, selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-169">On the **Setup** tab add the `AppID` and `Key` you copied previously, and then select **Save changes**.</span></span> <span data-ttu-id="d9b19-170">Após a atualização da página, você pode ver uma nova seção **Escolha o método de conexão**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-170">After the page refreshes, you can see a new section **Choose connection method**.</span></span>

1. <span data-ttu-id="d9b19-171">No **método Escolher conexão,** selecione a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações** novamente.</span><span class="sxs-lookup"><span data-stu-id="d9b19-171">In the **Choose connection method**, select the checkbox labeled **Default**, and then select **Save changes** again.</span></span>

1. <span data-ttu-id="d9b19-172">Após a atualização da página, você pode ver outra nova seção **consentimento do administrador & informações adicionais**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-172">After the page refreshes you can see another new section **Admin consent & additional information**.</span></span>
    1. <span data-ttu-id="d9b19-173">Selecione Fornecer link **de consentimento de administrador,** digite suas credenciais de administrador global Microsoft 365 e, em seguida, **aceite** conceder as permissões.</span><span class="sxs-lookup"><span data-stu-id="d9b19-173">Select **Provide Admin Consent** link, enter your Microsoft 365 Global Administrator credentials, then **Accept** to grant the permissions.</span></span>
    1. <span data-ttu-id="d9b19-174">Ao lado do campo **Inquilino Azure AD,** selecione o botão **Detectar.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-174">Next to the **Azure AD Tenant** field, select the **Detect** button.</span></span>
    1. <span data-ttu-id="d9b19-175">Ao lado da **URL OneDrive for Business,** selecione o botão **Detectar.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-175">Next to the **OneDrive for Business URL**, select the **Detect** button.</span></span>
    1. <span data-ttu-id="d9b19-176">Após o preenchimento dos campos, selecione novamente o botão **Salvar alterações.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-176">After the fields populate, select the **Save changes** button again.</span></span>

1. <span data-ttu-id="d9b19-177">Selecione o botão **Atualizar** para verificar a instalação e selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-177">Select the **Update** button to verify the installation, and then select **Save changes**.</span></span>

1. <span data-ttu-id="d9b19-178">Sincronize os usuários entre o servidor Moodle e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-178">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="d9b19-179">Para começar:</span><span class="sxs-lookup"><span data-stu-id="d9b19-179">To get started:</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9b19-180">Dependendo do seu ambiente, você pode selecionar diferentes opções durante esta etapa.</span><span class="sxs-lookup"><span data-stu-id="d9b19-180">Depending on your environment, you can select different options during this stage.</span></span>

1. <span data-ttu-id="d9b19-181">Sincronize os usuários entre o servidor Moodle e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-181">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="d9b19-182">Dependendo do seu ambiente, você pode selecionar diferentes opções durante esta etapa.</span><span class="sxs-lookup"><span data-stu-id="d9b19-182">Depending on your environment, you can select different options during this stage.</span></span> <span data-ttu-id="d9b19-183">Para começar:</span><span class="sxs-lookup"><span data-stu-id="d9b19-183">To get started:</span></span>
    1. <span data-ttu-id="d9b19-184">Mude para a **guia Sincronizar Configurações**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-184">Switch to the **Sync Settings tab**.</span></span>

    1. <span data-ttu-id="d9b19-185">Na seção Sincronizar com a seção **Azure AD,** selecione as caixas de seleção aplicáveis ao seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="d9b19-185">In the **Sync users with Azure AD** section, select the checkboxes that apply to your environment.</span></span> <span data-ttu-id="d9b19-186">Você deve selecionar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9b19-186">You must select the following:</span></span>  

        <span data-ttu-id="d9b19-187">✔ Criar contas no Moodle para usuários no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-187">✔ Create accounts in Moodle for users in Azure AD.</span></span>

        <span data-ttu-id="d9b19-188">✔ Atualize todas as contas no Moodle para usuários no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d9b19-188">✔ Update all accounts in Moodle for users in Azure AD.</span></span>

    1. <span data-ttu-id="d9b19-189">Na seção **Restrição de Criação do Usuário,** você pode configurar um filtro para limitar os usuários do Azure AD que está sincronizado com o Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-189">In the **User Creation Restriction** section, you can setup a filter to limit the Azure AD users that is synced to Moodle.</span></span>
    1. <span data-ttu-id="d9b19-190">A seção **de mapeamento de campo do usuário** permite personalizar o mapeamento de campo do Azure AD para o Moodle User Profile.</span><span class="sxs-lookup"><span data-stu-id="d9b19-190">The **User Field Mapping** section allows you to customize the Azure AD to Moodle User Profile field mapping.</span></span>
    1. <span data-ttu-id="d9b19-191">Na seção **Teams Sync,** você pode selecionar para criar automaticamente Grupos, como equipes para alguns ou todos, de seus cursos moodle existentes.</span><span class="sxs-lookup"><span data-stu-id="d9b19-191">In the **Teams Sync** section, you can select to automatically create Groups, such as teams for some, or all, of your existing Moodle courses.</span></span>

13. <span data-ttu-id="d9b19-192">Para validar [os trabalhos do cron](https://docs.moodle.org/310/en/Cron) e executá-los manualmente para a primeira execução, selecione o link de página de gerenciamento de **tarefas programadas** na seção Sincronizar com a seção **Azure AD.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-192">To validate [cron](https://docs.moodle.org/310/en/Cron) jobs and run them manually for the first run, select the **Scheduled tasks management page** link in the **Sync users with Azure AD** section.</span></span> <span data-ttu-id="d9b19-193">Isso leva você à página **Tarefas Programadas.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-193">This takes you to the **Scheduled Tasks** page.</span></span>

    1. <span data-ttu-id="d9b19-194">Role para baixo e encontre os usuários do Sync com o trabalho **do Azure AD** e selecione **Executar agora**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-194">Scroll down and find the **Sync users with Azure AD** job and select **Run now**.</span></span>
    1. <span data-ttu-id="d9b19-195">Se você selecionar para criar grupos com base em cursos existentes, você também pode executar os **grupos de usuários Criar em Microsoft 365** trabalho.</span><span class="sxs-lookup"><span data-stu-id="d9b19-195">If you select to create Groups based on existing courses, you can also run the **Create user groups in Microsoft 365** job.</span></span>

    > [!NOTE]
    >
    > <span data-ttu-id="d9b19-196">O Moodle [Cron](https://docs.moodle.org/310/en/Cron) funciona de acordo com o cronograma de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d9b19-196">The Moodle [Cron](https://docs.moodle.org/310/en/Cron) runs according to the task schedule.</span></span> <span data-ttu-id="d9b19-197">O cronograma padrão é uma vez por dia.</span><span class="sxs-lookup"><span data-stu-id="d9b19-197">The default schedule is once a day.</span></span> <span data-ttu-id="d9b19-198">No entanto, o cron deve correr com mais frequência para manter tudo em sincronia.</span><span class="sxs-lookup"><span data-stu-id="d9b19-198">However, the cron must run more frequently to keep everything in sync.</span></span>

1. <span data-ttu-id="d9b19-199">Retorne à página de administração de plugins, **administração do site > Plugins > Microsoft 365 Integration** e selecione a página **Teams Configurações.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-199">Return to the plugins administration page, **Site administration > Plugins > Microsoft 365 Integration**, and select the **Teams Settings** page.</span></span>

1. <span data-ttu-id="d9b19-200">Na página **Teams Configurações,** configure as configurações necessárias para ativar a integração Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9b19-200">On the **Teams Settings** page, configure the required settings to enable the Teams app integration.</span></span>

    1. <span data-ttu-id="d9b19-201">Para ativar **o OpenID Conexão,** selecione o link **Gerenciar autenticação** e selecione o ícone de olho na linha **Conexão OpenId** se ele estiver cinza.</span><span class="sxs-lookup"><span data-stu-id="d9b19-201">To enable **OpenID Connect**, select the **Manage Authentication** link, and select the eye icon on the **OpenId Connect** line if it is greyed out.</span></span>
    1. <span data-ttu-id="d9b19-202">Para ativar a incorporação de quadros, selecione o link **de segurança HTTP** e selecione a caixa de seleção ao lado para permitir a **incorporação do quadro**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-202">To enable frame embedding, select the **HTTP Security** link, and then select the checkbox next to **Allow frame embedding**.</span></span>
    1. <span data-ttu-id="d9b19-203">Para habilitar os serviços web, que habilitam os recursos da API Moodle, selecione o link **Recursos Avançados** e, em seguida, certifique-se de que a caixa de seleção ao lado **de Ativar serviços web** seja selecionada.</span><span class="sxs-lookup"><span data-stu-id="d9b19-203">To enable web services, which enables the Moodle API features, select the **Advanced Features** link, and then ensure the checkbox next to **Enable web services** is selected.</span></span>
    1. <span data-ttu-id="d9b19-204">Para habilitar os serviços externos para Microsoft 365, selecione o link **de serviços externos** e, em seguida,:</span><span class="sxs-lookup"><span data-stu-id="d9b19-204">To enable the external services for Microsoft 365, select the **External services** link, and then:</span></span>  

        <span data-ttu-id="d9b19-205">✔ Selecione **Editar** na linha **Moodle Microsoft 365 Webservices.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-205">✔ Select **Edit** on the **Moodle Microsoft 365 Webservices** row.</span></span>

        <span data-ttu-id="d9b19-206">✔ Selecione a caixa de seleção ao lado **habilitada** e selecione **Salvar alterações**</span><span class="sxs-lookup"><span data-stu-id="d9b19-206">✔ Select the checkbox next to **Enabled**, then select **Save Changes**</span></span>

    1. <span data-ttu-id="d9b19-207">Edite suas permissões autenticadas do usuário para permitir que eles criem tokens de serviço web.</span><span class="sxs-lookup"><span data-stu-id="d9b19-207">Edit your authenticated user permissions to allow them to create web service tokens.</span></span>

        <span data-ttu-id="d9b19-208">✔ Selecione a **função De edição Autenticado** link do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9b19-208">✔ Select the **Editing role Authenticated user** link.</span></span>

        <span data-ttu-id="d9b19-209">✔ Role para baixo e encontre o recurso **Criar um token de serviço web** e selecione a caixa de seleção **Permitir.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-209">✔ Scroll down and find the **Create a web service token** capability and select the **Allow** checkbox.</span></span>

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a><span data-ttu-id="d9b19-210">3. Implantar o Moodle Assistant Bot para o Azure</span><span class="sxs-lookup"><span data-stu-id="d9b19-210">3. Deploy the Moodle Assistant Bot to Azure</span></span>

<span data-ttu-id="d9b19-211">O bot assistente moodle gratuito para Microsoft Teams ajuda professores e alunos a responder perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-211">The free Moodle assistant bot for Microsoft Teams helps teachers and students answer questions about their courses, assignments, grades, and other information in Moodle.</span></span> <span data-ttu-id="d9b19-212">O bot também envia notificações moodle para alunos e professores dentro de Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-212">The bot also sends Moodle notifications to students and teachers within Teams.</span></span> <span data-ttu-id="d9b19-213">O bot é um projeto de código aberto mantido pela Microsoft, e está disponível em [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).</span><span class="sxs-lookup"><span data-stu-id="d9b19-213">The bot is an open-source project maintained by Microsoft, and is available on [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).</span></span>

> [!NOTE]
>
> * <span data-ttu-id="d9b19-214">Implante recursos para sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="d9b19-214">Deploy resources to your Azure subscription.</span></span> <span data-ttu-id="d9b19-215">Todos os recursos foram configurados usando o nível **livre.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-215">All resources were configured using the **free** tier.</span></span> <span data-ttu-id="d9b19-216">Dependendo do uso do seu bot, você pode ter que dimensionar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="d9b19-216">Depending on the usage of your bot, you may have to scale these resources.</span></span>
>
> * <span data-ttu-id="d9b19-217">Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).</span><span class="sxs-lookup"><span data-stu-id="d9b19-217">To use the Moodle tab without the bot, skip to [4](#4-deploy-your-microsoft-teams-app).</span></span>

### <a name="moodle-bot-information-flow"></a><span data-ttu-id="d9b19-218">Fluxo de informações do bot Moodle</span><span class="sxs-lookup"><span data-stu-id="d9b19-218">Moodle bot information flow</span></span>

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

<span data-ttu-id="d9b19-219">Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade Microsoft](https://identity.microsoft.com/Landing).</span><span class="sxs-lookup"><span data-stu-id="d9b19-219">To install the bot, you must register it on the [Microsoft Identity Platform](https://identity.microsoft.com/Landing).</span></span> <span data-ttu-id="d9b19-220">Isso permite que seu bot se autue contra seus pontos finais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d9b19-220">This allows your bot to authenticate against your Microsoft endpoints.</span></span> 

<span data-ttu-id="d9b19-221">**Para registrar seu bot**</span><span class="sxs-lookup"><span data-stu-id="d9b19-221">**To register your bot**</span></span>

1. <span data-ttu-id="d9b19-222">Vá para a página de administração de plugins e, em seguida, selecione **Plugins**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-222">Go to the plugins administration page, and then select **Plugins**.</span></span> <span data-ttu-id="d9b19-223">Em **Microsoft 365 Integração**, selecione a **Teams Configurações** guia.</span><span class="sxs-lookup"><span data-stu-id="d9b19-223">Under **Microsoft 365 Integration**, select the **Teams Settings** tab.</span></span>

1. <span data-ttu-id="d9b19-224">Selecione o link do **Portal de Registro de Aplicativos da Microsoft** e faça login com seu ID Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d9b19-224">Select the **Microsoft Application Registration Portal** link and sign in with your Microsoft ID.</span></span>

1. <span data-ttu-id="d9b19-225">Digite um nome para o seu aplicativo, como MoodleBot e selecione o botão **Criar.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-225">Enter a name for your app, such as MoodleBot and select the **Create** button.</span></span>

1. <span data-ttu-id="d9b19-226">Copie o **ID do aplicativo** e cole-o no campo **de ID do aplicativo bot** na página Configurações **equipe.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-226">Copy the **Application ID** and paste it into the **Bot Application ID** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="d9b19-227">Selecione o botão **Gerar nova senha.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-227">Select the **Generate New Password** button.</span></span> <span data-ttu-id="d9b19-228">Copie a senha gerada e cole-a no campo Senha do **aplicativo bot** na página **Team Configurações.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-228">Copy the generated password and and paste it into the **Bot Application Password** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="d9b19-229">Role até a parte inferior do formulário e selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-229">Scroll to the bottom of the form and select **Save Changes**.</span></span>

<span data-ttu-id="d9b19-230">Depois de gerar seu ID e senha do aplicativo, implante seu bot no Azure:</span><span class="sxs-lookup"><span data-stu-id="d9b19-230">After generating your application ID and password, deploy your bot to Azure:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d9b19-231">Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como o ID do aplicativo bot, a senha do aplicativo bot e o segredo moodle na página **Teams Configurações.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-231">Select **Deploy to Azure** and complete the form with the necessary information, such as the Bot Application ID, Bot Application Password, and the Moodle Secret on the **Teams Settings** page.</span></span> <span data-ttu-id="d9b19-232">As informações do Azure estão na página **Configuração.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-232">The Azure information is on the **Setup** page.</span></span> 
> * <span data-ttu-id="d9b19-233">Após preencher o formulário, selecione a caixa de seleção para concordar com os termos e condições.</span><span class="sxs-lookup"><span data-stu-id="d9b19-233">After completing the form, select the checkbox to agree to the terms and conditions.</span></span>
> * <span data-ttu-id="d9b19-234">Selecione **Compra**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-234">Select **Purchase**.</span></span> <span data-ttu-id="d9b19-235">Todos os recursos do Azure são implantados no nível livre.</span><span class="sxs-lookup"><span data-stu-id="d9b19-235">All Azure resources are deployed to the free tier.</span></span>

<span data-ttu-id="d9b19-236">Depois que os recursos terminarem a implantação no Azure, você deve configurar os plugins Microsoft 365 Moodle com um ponto final de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d9b19-236">After the resources have completed deploying to Azure, you must configure the Microsoft 365 Moodle plugins with a messaging endpoint.</span></span> <span data-ttu-id="d9b19-237">Você deve obter o ponto final do seu bot no Azure:</span><span class="sxs-lookup"><span data-stu-id="d9b19-237">You must get the endpoint from your bot in Azure:</span></span>

1. <span data-ttu-id="d9b19-238">Entre no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d9b19-238">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

1. <span data-ttu-id="d9b19-239">No painel esquerdo, selecione **grupos de recursos** e selecione o grupo de recursos que você usou ou criou, enquanto implanta seu bot.</span><span class="sxs-lookup"><span data-stu-id="d9b19-239">In the left pane, select **Resource groups** and select the resource group you used or created, while deploying your bot.</span></span>

1. <span data-ttu-id="d9b19-240">Selecione o recurso **Do WebApp Bot** na lista de recursos do grupo.</span><span class="sxs-lookup"><span data-stu-id="d9b19-240">Select the **WebApp Bot** resource from the list of resources in the group.</span></span>

1. <span data-ttu-id="d9b19-241">Copie o **ponto final de mensagens** da seção **Visão Geral.**</span><span class="sxs-lookup"><span data-stu-id="d9b19-241">Copy the **Messaging Endpoint** from the **Overview** section.</span></span>

1. <span data-ttu-id="d9b19-242">Em Moodle, abra a página **de Configurações da equipe** de seus plugins moodle Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d9b19-242">In Moodle, open the **Team Settings** page of your Microsoft 365 Moodle Plugins.</span></span>

1. <span data-ttu-id="d9b19-243">No campo **Bot Endpoint** cole a URL que você acabou de copiar e altere as *mensagens* de palavras para *webhook*.</span><span class="sxs-lookup"><span data-stu-id="d9b19-243">In the **Bot Endpoint** field paste the URL you just copied and change the word *messages* to *webhook*.</span></span> <span data-ttu-id="d9b19-244">A URL deve aparecer da seguinte forma: `https://botname.azurewebsites.net/api/webhook`</span><span class="sxs-lookup"><span data-stu-id="d9b19-244">The URL must appear as follows: `https://botname.azurewebsites.net/api/webhook`</span></span>

1. <span data-ttu-id="d9b19-245">Selecione **Salvar alterações**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-245">Select **Save Changes**.</span></span>

1. <span data-ttu-id="d9b19-246">Depois de salvar as alterações, volte para a guia **Team Configurações,** selecione o botão **de arquivo manifesto Download** e salve o pacote manifesto do aplicativo para uso adicional.</span><span class="sxs-lookup"><span data-stu-id="d9b19-246">After saving the changes, go back to the **Team Settings** tab, select the **Download manifest file** button, and save the app manifest package to your computer for further use.</span></span>

## <a name="4-deploy-your-microsoft-teams-app"></a><span data-ttu-id="d9b19-247">4. Implante seu aplicativo de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d9b19-247">4. Deploy your Microsoft Teams app</span></span>

<span data-ttu-id="d9b19-248">Depois que seu bot foi implantado no Azure e configurado para falar com seu servidor Moodle, você deve implantar seu aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-248">After your bot deployed to Azure and configured to talk to your Moodle server, you must deploy your Microsoft Teams app.</span></span> <span data-ttu-id="d9b19-249">Para fazer isso, você deve carregar o arquivo manifesto do aplicativo que você baixou da página Microsoft 365 Moodle Plugins Team Configurações na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d9b19-249">To do this you must load the app manifest file that you downloaded from the Microsoft 365 Moodle Plugins Team Settings page in the previous step.</span></span>

<span data-ttu-id="d9b19-250">Antes de instalar o aplicativo, você deve garantir para habilitar aplicativos externos e upload de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d9b19-250">Before you install the app you must ensure to enable external apps and uploading of apps.</span></span> <span data-ttu-id="d9b19-251">Para obter mais informações, consulte [Prepare seu inquilino Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="d9b19-251">For more information, see [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span> 

<span data-ttu-id="d9b19-252">**Para implantar seu aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d9b19-252">**To deploy your app**</span></span> 

1. <span data-ttu-id="d9b19-253">Aberto **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-253">Open **Microsoft Teams**.</span></span> 

1. <span data-ttu-id="d9b19-254">Selecione o ícone **App** na área inferior esquerda da barra de navegação.</span><span class="sxs-lookup"><span data-stu-id="d9b19-254">Select the **App** icon on the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="d9b19-255">Selecione o Upload um link **de aplicativo personalizado** na lista de opções.</span><span class="sxs-lookup"><span data-stu-id="d9b19-255">Select the **Upload a custom app** link from the list of options.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d9b19-256">Se você estiver logado como administrador global, você deve ter a opção de carregar o aplicativo para o catálogo de aplicativos da sua organização, caso contrário, você só pode carregar o aplicativo para uma equipe na qual você é um membro.</span><span class="sxs-lookup"><span data-stu-id="d9b19-256">If you are logged in as a global administrator, you must have the option of uploading the app to your organization's app catalog, otherwise you can only load the app for a team in which you are a member.</span></span>

4. <span data-ttu-id="d9b19-257">Selecione o `manifest.zip` pacote que você baixou anteriormente e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-257">Select the `manifest.zip` package you downloaded previously and select **Save**.</span></span> <span data-ttu-id="d9b19-258">Se você não baixou o pacote de manifesto do aplicativo, você pode baixar na **guia Team Configurações** da página de configuração de plugins no Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-258">If you have not downloaded the app manifest package, you can download from the **Team Settings** tab of the plugins configuration page in Moodle.</span></span>

<span data-ttu-id="d9b19-259">Agora que você tem o aplicativo instalado, você pode adicionar a guia a qualquer canal a que você tenha acesso.</span><span class="sxs-lookup"><span data-stu-id="d9b19-259">Now that you have the app installed, you can add the tab to any channel that you have access to.</span></span> <span data-ttu-id="d9b19-260">Para isso, navegue até o canal, selecione o símbolo **de mais** (➕) e selecione seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="d9b19-260">To do so, navigate to the channel, select the **plus** (➕) symbol and select your app from the list.</span></span> <span data-ttu-id="d9b19-261">Siga as instruções para terminar de adicionar sua guia de curso Moodle a um canal.</span><span class="sxs-lookup"><span data-stu-id="d9b19-261">Follow the prompts to finish adding your Moodle course tab to a channel.</span></span>

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a><span data-ttu-id="d9b19-262">5. Permitir a criação automática de guias Moodle em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d9b19-262">5. Allow automatic creation of Moodle tabs in Microsoft Teams</span></span>

<span data-ttu-id="d9b19-263">Embora as guias Moodle sejam criadas manualmente em Microsoft Teams, você pode decidir criá-las automaticamente quando as equipes são criadas a partir da sincronização do curso.</span><span class="sxs-lookup"><span data-stu-id="d9b19-263">Although the Moodle tabs are created manually in Microsoft Teams, you can decide to create them automatically when teams are created from course synchronization.</span></span> <span data-ttu-id="d9b19-264">Para fazer isso, você deve configurar o ID do aplicativo Microsoft Teams carregado no Moodle.</span><span class="sxs-lookup"><span data-stu-id="d9b19-264">To do this, you must configure the ID of the uploaded Microsoft Teams app in Moodle.</span></span>

<span data-ttu-id="d9b19-265">**Para permitir a criação automática de guias Moodle**</span><span class="sxs-lookup"><span data-stu-id="d9b19-265">**To allow automatic creation of Moodle tabs**</span></span>

1. <span data-ttu-id="d9b19-266">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-266">Open Microsoft Teams.</span></span>

1. <span data-ttu-id="d9b19-267">Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.</span><span class="sxs-lookup"><span data-stu-id="d9b19-267">Select the Apps icon from the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="d9b19-268">Localize o **aplicativo Moodle** carregado > selecione o ícone de **opções** > selecionar **link de cópia**.</span><span class="sxs-lookup"><span data-stu-id="d9b19-268">Locate the uploaded **Moodle app** > select the **options** icon > select **copy link**.</span></span>

1. <span data-ttu-id="d9b19-269">Em um editor de texto, cole o conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="d9b19-269">In a text editor, paste the copied content.</span></span> <span data-ttu-id="d9b19-270">Ele deve conter uma URL como ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span><span class="sxs-lookup"><span data-stu-id="d9b19-270">It must contain a URL such as ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span></span> <span data-ttu-id="d9b19-271">Copie a última parte da URL, como `00112233-4455-6677-8899-aabbccddeeff` , que é o ID do aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-271">Copy the last part of the URL, such as  `00112233-4455-6677-8899-aabbccddeeff`, which is the ID of the Microsoft Teams app.</span></span>

1. <span data-ttu-id="d9b19-272">No Moodle, abra a guia **do aplicativo Teams Moodle** na sua página de configuração do Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="d9b19-272">In Moodle, open the **Teams Moodle app** tab from your Microsoft 365 Moodle Plugins configuration page.</span></span>

1. <span data-ttu-id="d9b19-273">Cole o ID do aplicativo Microsoft Teams no campo de ID do aplicativo Moodle e salve as alterações.</span><span class="sxs-lookup"><span data-stu-id="d9b19-273">Paste the ID of the Microsoft Teams app into the Moodle app ID field, and save changes.</span></span>

<span data-ttu-id="d9b19-274">Quando um curso moodle é sincronizado, Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral de Teams e configura-o para conter a página do curso para o curso Moodle do qual ele é sincronizado.</span><span class="sxs-lookup"><span data-stu-id="d9b19-274">When a Moodle course is synced, Microsoft Teams automatically installs the Moodle app in the team, creates a Moodle tab in the General channel of Teams, and configures it to contain the course page for the Moodle course from which it is synced.</span></span> <span data-ttu-id="d9b19-275">Agora você pode começar a trabalhar com seus cursos moodle diretamente a partir de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d9b19-275">You can now start working with your Moodle courses directly from Microsoft Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="d9b19-276">Para compartilhar quaisquer solicitações de recursos ou feedback conosco, visite nossa [página de Voz do Usuário](https://microsoftteams.uservoice.com/forums/916759-moodle).</span><span class="sxs-lookup"><span data-stu-id="d9b19-276">To share any feature requests or feedback with us, visit our [User Voice page](https://microsoftteams.uservoice.com/forums/916759-moodle).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9b19-277">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9b19-277">See also</span></span>

- [<span data-ttu-id="d9b19-278">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="d9b19-278">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
- [<span data-ttu-id="d9b19-279">Moodle</span><span class="sxs-lookup"><span data-stu-id="d9b19-279">Moodle</span></span>](https://moodle.org/)
- <span data-ttu-id="d9b19-280">[Documentação moodle](https://docs.moodle.org/34/en/Installing_plugins).</span><span class="sxs-lookup"><span data-stu-id="d9b19-280">[Moodle documentation](https://docs.moodle.org/34/en/Installing_plugins).</span></span>

