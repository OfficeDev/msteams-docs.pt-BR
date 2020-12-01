---
title: Autenticação de logon único com o Teams Toolkit e o Visual Studio Code for Tabs
description: Criar uma guia que ofereça suporte a chamadas de logon único e Microsoft Graph diretamente dentro do Visual Studio Code com o Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit guias de autenticação do Azure Graph plataforma de identidade do Azure
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: fe734143975688cd35c510cd68cd0779a2200a18
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49477730"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="88096-104">Autenticação de logon único com o Teams Toolkit e o Visual Studio Code for Tabs</span><span class="sxs-lookup"><span data-stu-id="88096-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

<span data-ttu-id="88096-105">O Microsoft Teams Toolkit permite que você crie autenticação de logon único (SSO) para aplicativos de guia diretamente no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="88096-105">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication  for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="88096-106">O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa, incluindo o provisionamento do registro da plataforma de identidade da Microsoft no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="88096-106">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="88096-107">Introdução — criar um projeto</span><span class="sxs-lookup"><span data-stu-id="88096-107">Get started — create a project</span></span>

1. <span data-ttu-id="88096-108">Criar um novo projeto no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="88096-108">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="88096-109">Selecione Tab como o tipo de extensão que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="88096-109">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="88096-110">Selecione a opção para dar suporte ao SSO.</span><span class="sxs-lookup"><span data-stu-id="88096-110">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="88096-111">Após a instalação, você deve ver o Teams Toolkit na barra de atividade de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88096-111">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="88096-112">Caso contrário, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="88096-112">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="88096-113">Configurar seu projeto</span><span class="sxs-lookup"><span data-stu-id="88096-113">Configure your project</span></span>

1. <span data-ttu-id="88096-114">Para habilitar o SSO no Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="88096-114">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="88096-115">O Teams Toolkit provisionará o registro de aplicativo em seu nome.</span><span class="sxs-lookup"><span data-stu-id="88096-115">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="88096-116">Insira a URL onde seu aplicativo será hospedado e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="88096-116">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="88096-117">O registro do aplicativo será configurado usando a URL fornecida.</span><span class="sxs-lookup"><span data-stu-id="88096-117">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="88096-118">Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="88096-118">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="88096-119">Se quiser saber mais sobre como o registro do seu aplicativo do Azure será provisionado, _Confira_  nosso [suporte de logon único (SSO) para a documentação de guias](../tabs/how-to/authentication/auth-aad-sso.md) .</span><span class="sxs-lookup"><span data-stu-id="88096-119">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="88096-120">Você precisará ir para **registros de aplicativo do Azure** e atualizar seu *URI de API* e *redirecionar URLs* sempre que você alterar essa URL.</span><span class="sxs-lookup"><span data-stu-id="88096-120">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="88096-121">Executar o projeto</span><span class="sxs-lookup"><span data-stu-id="88096-121">Run your project</span></span>

1. <span data-ttu-id="88096-122">Selecione **NPM instalar** na `api-server` pasta.</span><span class="sxs-lookup"><span data-stu-id="88096-122">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="88096-123">Em seguida, **NPM iniciar**.</span><span class="sxs-lookup"><span data-stu-id="88096-123">Then **npm start**.</span></span>
1. <span data-ttu-id="88096-124">Selecione **NPM instalar** na `.src` pasta.</span><span class="sxs-lookup"><span data-stu-id="88096-124">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="88096-125">Em seguida, **NPM iniciar**.</span><span class="sxs-lookup"><span data-stu-id="88096-125">Then **npm start**.</span></span>
1. <span data-ttu-id="88096-126">Se você estiver usando um serviço de encapsulamento como o [ngrok](https://ngrok.com/), execute-o e verifique se a URL corresponde ao que você inseriu no assistente de criação de projeto.</span><span class="sxs-lookup"><span data-stu-id="88096-126">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="88096-127">Caso contrário, você precisará atualizar seu URI de _API_ e _redirecionar a URL_ no registro de aplicativo que foi criado no Azure.</span><span class="sxs-lookup"><span data-stu-id="88096-127">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="88096-128">Navegue até a barra de atividade no lado esquerdo da janela de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88096-128">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="88096-129">Selecione o ícone **executar** para exibir o modo de exibição **executar e depurar** .</span><span class="sxs-lookup"><span data-stu-id="88096-129">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="88096-130">Você também pode usar o atalho de teclado **Ctrl + Shift + D**.</span><span class="sxs-lookup"><span data-stu-id="88096-130">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="88096-131">Você pode não ver a caixa de diálogo instalar aplicativo no navegador se as janelas pop-up estiverem desabilitadas para seu navegador.</span><span class="sxs-lookup"><span data-stu-id="88096-131">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="88096-132">Se isso acontecer, habilite as janelas pop-up e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="88096-132">If this happens, enable pop-up windows and refresh the page.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="88096-133">Saiba mais: criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="88096-133">Learn more: Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
