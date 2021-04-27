---
title: Autenticação de login único com o Teams Toolkit e Visual Studio Código para guias
description: Crie uma guia que dá suporte a chamadas de logom único e do Microsoft Graph diretamente Visual Studio Código com o microsoft Teams Toolkit
keywords: Guias do kit de ferramentas de código visual studio do teams sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: daf9a1b0bb64fee9584d0f58d749cf2b1ccaa4ef
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018422"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="b8479-104">Autenticação de login único com o Teams Toolkit e Visual Studio Código para guias</span><span class="sxs-lookup"><span data-stu-id="b8479-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

<span data-ttu-id="b8479-105">A Toolkit do Microsoft Teams permite que você crie autenticação de logom único (SSO) para aplicativos de tabulação diretamente no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b8479-105">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication  for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="b8479-106">O kit de ferramentas orienta você pelo processo e fornece tudo o que você precisa, incluindo o provisionamento do registro da plataforma de identidade da Microsoft no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="b8479-106">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="b8479-107">Começar — criar um projeto</span><span class="sxs-lookup"><span data-stu-id="b8479-107">Get started — create a project</span></span>

1. <span data-ttu-id="b8479-108">Crie um novo projeto no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="b8479-108">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="b8479-109">Selecione a guia como o tipo de extensão que você gostaria de criar.</span><span class="sxs-lookup"><span data-stu-id="b8479-109">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="b8479-110">Selecione a opção para dar suporte ao SSO.</span><span class="sxs-lookup"><span data-stu-id="b8479-110">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="b8479-111">Após a instalação, você deve ver o teams Toolkit na barra de atividades Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b8479-111">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="b8479-112">Caso não seja, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="b8479-112">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="b8479-113">Configurar seu projeto</span><span class="sxs-lookup"><span data-stu-id="b8479-113">Configure your project</span></span>

1. <span data-ttu-id="b8479-114">Para habilitar o SSO no Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="b8479-114">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="b8479-115">O teams Toolkit provisione o registro do aplicativo em seu nome.</span><span class="sxs-lookup"><span data-stu-id="b8479-115">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="b8479-116">Insira a URL onde seu aplicativo será hospedado e selecione **o próximo**.</span><span class="sxs-lookup"><span data-stu-id="b8479-116">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="b8479-117">O registro do aplicativo será configurado usando a URL fornecida.</span><span class="sxs-lookup"><span data-stu-id="b8479-117">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="b8479-118">Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do projeto.</span><span class="sxs-lookup"><span data-stu-id="b8479-118">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="b8479-119">Se você quiser saber mais sobre como o registro do aplicativo  do Azure será provisionado, consulte nosso suporte de [SSO (login único)](../tabs/how-to/authentication/auth-aad-sso.md) para obter a documentação de guias.</span><span class="sxs-lookup"><span data-stu-id="b8479-119">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="b8479-120">Você precisará ir para Registros do **Aplicativo do Azure** e atualizar o *URI* da API e redirecionar *URLs* sempre que alterar essa URL.</span><span class="sxs-lookup"><span data-stu-id="b8479-120">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="b8479-121">Executar seu projeto</span><span class="sxs-lookup"><span data-stu-id="b8479-121">Run your project</span></span>

1. <span data-ttu-id="b8479-122">Selecione **npm install** na `api-server` pasta.</span><span class="sxs-lookup"><span data-stu-id="b8479-122">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="b8479-123">Em **seguida, npm start**.</span><span class="sxs-lookup"><span data-stu-id="b8479-123">Then **npm start**.</span></span>
1. <span data-ttu-id="b8479-124">Selecione **npm install** na `.src` pasta.</span><span class="sxs-lookup"><span data-stu-id="b8479-124">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="b8479-125">Em **seguida, npm start**.</span><span class="sxs-lookup"><span data-stu-id="b8479-125">Then **npm start**.</span></span>
1. <span data-ttu-id="b8479-126">Se você estiver usando um serviço de tunelamento como [ngrok,](https://ngrok.com/)execute-o e certifique-se de que a URL corresponde ao que você entrou no assistente de criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="b8479-126">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="b8479-127">Se isso não ocorrer, você precisará atualizar o _URI_ da API e _redirecionar a URL_ no registro do aplicativo criado no Azure.</span><span class="sxs-lookup"><span data-stu-id="b8479-127">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="b8479-128">Navegue até a barra de atividades no lado esquerdo da janela Visual Studio Código.</span><span class="sxs-lookup"><span data-stu-id="b8479-128">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="b8479-129">Selecione o **ícone Executar** para exibir o **exibição Executar e Depurar.**</span><span class="sxs-lookup"><span data-stu-id="b8479-129">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="b8479-130">Você também pode usar o atalho de teclado **Ctrl+Shift+D**.</span><span class="sxs-lookup"><span data-stu-id="b8479-130">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="b8479-131">Você pode não ver o diálogo de instalação do aplicativo no navegador se as janelas pop-up estão desabilitadas para o navegador.</span><span class="sxs-lookup"><span data-stu-id="b8479-131">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="b8479-132">Se isso acontecer, habilita as janelas pop-up e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="b8479-132">If this happens, enable pop-up windows and refresh the page.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8479-133">Saiba mais: criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="b8479-133">Learn more: Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
