---
title: Autenticação de login único com Teams Toolkit e Visual Studio Code para guias
description: Crie uma guia que dá suporte a chamadas de logom único Graph Microsoft diretamente no Visual Studio Code com o Microsoft Teams Toolkit
keywords: Guias do kit de ferramentas de código visual studio do teams sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 2ef409a45b92240cced09d2d77793af33945589e
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721812"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="f9ff2-104">Autenticação de login único com Teams Toolkit e Visual Studio Code para guias</span><span class="sxs-lookup"><span data-stu-id="f9ff2-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9ff2-105">**Este documento se refere a uma versão antiga do Teams Toolkit**</span><span class="sxs-lookup"><span data-stu-id="f9ff2-105">**This document refers to an old version of Teams Toolkit**</span></span>
>
> <span data-ttu-id="f9ff2-106">Para obter informações atuais, leia [os pré-requisitos](../get-started/prerequisites.md) e siga um dos tutoriais mais novos.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-106">For current information, read the [prerequisites](../get-started/prerequisites.md) and follow  one of the newer tutorials.</span></span>

<span data-ttu-id="f9ff2-107">A Microsoft Teams Toolkit permite que você crie autenticação de logom único (SSO) para aplicativos de tabulação diretamente no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-107">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="f9ff2-108">O kit de ferramentas orienta você pelo processo e fornece tudo o que você precisa, incluindo provisionar seu registro plataforma de identidade da Microsoft no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-108">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="f9ff2-109">Começar — criar um projeto</span><span class="sxs-lookup"><span data-stu-id="f9ff2-109">Get started — create a project</span></span>

1. <span data-ttu-id="f9ff2-110">Crie um novo projeto no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-110">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="f9ff2-111">Selecione a guia como o tipo de extensão que você gostaria de criar.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-111">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="f9ff2-112">Selecione a opção para dar suporte ao SSO.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-112">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="f9ff2-113">Após a instalação, você deve ver o Teams Toolkit na barra de Visual Studio Code de atividade.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-113">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="f9ff2-114">Se não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** fixar o kit de ferramentas para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-114">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="f9ff2-115">Configurar seu projeto</span><span class="sxs-lookup"><span data-stu-id="f9ff2-115">Configure your project</span></span>

1. <span data-ttu-id="f9ff2-116">Para habilitar o SSO Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-116">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="f9ff2-117">O Teams Toolkit provisione o registro do aplicativo em seu nome.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-117">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="f9ff2-118">Insira a URL onde seu aplicativo será hospedado e selecione **o próximo**.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-118">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="f9ff2-119">O registro do aplicativo será configurado usando a URL fornecida.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-119">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="f9ff2-120">Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do projeto.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-120">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="f9ff2-121">Se você quiser saber mais sobre como o registro do aplicativo  do Azure será provisionado, consulte nosso suporte de [SSO (login único)](../tabs/how-to/authentication/auth-aad-sso.md) para obter a documentação de guias.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-121">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="f9ff2-122">Você precisará ir para Registros do **Aplicativo do Azure** e atualizar o *URI* da API e redirecionar *URLs* sempre que alterar essa URL.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-122">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="f9ff2-123">Executar seu projeto</span><span class="sxs-lookup"><span data-stu-id="f9ff2-123">Run your project</span></span>

1. <span data-ttu-id="f9ff2-124">Selecione **npm install** na `api-server` pasta.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-124">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="f9ff2-125">Em **seguida, npm start**.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-125">Then **npm start**.</span></span>
1. <span data-ttu-id="f9ff2-126">Selecione **npm install** na `.src` pasta.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-126">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="f9ff2-127">Em **seguida, npm start**.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-127">Then **npm start**.</span></span>
1. <span data-ttu-id="f9ff2-128">Se você estiver usando um serviço de tunelamento como [ngrok,](https://ngrok.com/)execute-o e certifique-se de que a URL corresponde ao que você entrou no assistente de criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-128">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="f9ff2-129">Se isso não ocorrer, você precisará atualizar o _URI_ da API e _redirecionar a URL_ no registro do aplicativo criado no Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-129">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="f9ff2-130">Navegue até a barra de atividades no lado esquerdo da janela Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-130">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="f9ff2-131">Selecione o **ícone Executar** para exibir o **exibição Executar e Depurar.**</span><span class="sxs-lookup"><span data-stu-id="f9ff2-131">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="f9ff2-132">Você também pode usar o atalho de teclado **Ctrl+Shift+D**.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-132">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="f9ff2-133">Você pode não ver o diálogo de instalação do aplicativo no navegador se as janelas pop-up estão desabilitadas para o navegador.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-133">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="f9ff2-134">Se isso acontecer, habilita as janelas pop-up e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="f9ff2-134">If this happens, enable pop-up windows and refresh the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9ff2-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9ff2-135">See also</span></span>

[<span data-ttu-id="f9ff2-136">Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f9ff2-136">Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
