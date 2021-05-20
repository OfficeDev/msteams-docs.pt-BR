---
title: Autenticação de login único com Teams Toolkit e Visual Studio Code para guias
description: Crie uma guia que suporte chamadas de login único e microsoft Graph diretamente dentro de Visual Studio Code com o Microsoft Teams Toolkit
keywords: equipes visual estúdio code toolkit tabs sso graph authentication Azure plataforma de identidade
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 11e642ce335dae4344f1c730b73763e9172fd76c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566828"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="8e2cf-104">Autenticação de login único com Teams Toolkit e Visual Studio Code para guias</span><span class="sxs-lookup"><span data-stu-id="8e2cf-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

<span data-ttu-id="8e2cf-105">O Microsoft Teams Toolkit permite criar autenticação SSO (Single Sign-on) para aplicativos de guia diretamente dentro de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-105">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication  for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="8e2cf-106">O kit de ferramentas orienta você durante o processo e fornece tudo o que você precisa, incluindo fornecer seu registro de plataforma de identidade da Microsoft no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-106">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="8e2cf-107">Comece — crie um projeto</span><span class="sxs-lookup"><span data-stu-id="8e2cf-107">Get started — create a project</span></span>

1. <span data-ttu-id="8e2cf-108">Crie um novo projeto no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-108">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="8e2cf-109">Selecione a guia como o tipo de extensão que você gostaria de criar.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-109">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="8e2cf-110">Selecione a opção para suportar OSO.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-110">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="8e2cf-111">Após a instalação, você deve ver o Teams Toolkit na barra de atividades Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-111">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="8e2cf-112">Caso não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para fácil acesso.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-112">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="8e2cf-113">Configure seu projeto</span><span class="sxs-lookup"><span data-stu-id="8e2cf-113">Configure your project</span></span>

1. <span data-ttu-id="8e2cf-114">Para habilitar o SSO dentro Teams, seu aplicativo deve ter um recurso de registro de aplicativo Azure.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-114">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="8e2cf-115">O Teams Toolkit irá providenciar o registro do aplicativo em seu nome.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-115">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="8e2cf-116">Digite a URL onde seu aplicativo será hospedado e selecione **o próximo**.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-116">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="8e2cf-117">Seu registro de aplicativo será configurado usando a URL fornecida.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-117">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="8e2cf-118">Os detalhes de configuração do registro do aplicativo serão `.env` armazenados nos arquivos no código-fonte do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-118">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="8e2cf-119">Se você quiser saber mais sobre como seu registro de aplicativo do Azure será provisionado, _consulte_  nosso [suporte de login único (SSO) para](../tabs/how-to/authentication/auth-aad-sso.md) documentação de guias.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-119">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="8e2cf-120">Você precisará ir aos **Registros de Aplicativos do Azure** e atualizar sua *API URI* e *redirecionar URLs* sempre que você alterar esta URL.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-120">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="8e2cf-121">Execute seu projeto</span><span class="sxs-lookup"><span data-stu-id="8e2cf-121">Run your project</span></span>

1. <span data-ttu-id="8e2cf-122">Selecione **a instalação npm** da `api-server` pasta.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-122">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="8e2cf-123">Então **npm começar**.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-123">Then **npm start**.</span></span>
1. <span data-ttu-id="8e2cf-124">Selecione **a instalação npm** da `.src` pasta.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-124">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="8e2cf-125">Então **npm começar**.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-125">Then **npm start**.</span></span>
1. <span data-ttu-id="8e2cf-126">Se você estiver usando um serviço de tunelamento como [ngrok,](https://ngrok.com/)execute-o e certifique-se de que a URL corresponda ao que você inseriu no assistente de criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-126">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="8e2cf-127">Se isso não acontecer, você precisará atualizar sua _API URI_ e _redirecionar_ URL no registro do aplicativo que foi criado no Azure.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-127">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="8e2cf-128">Navegue até a barra de atividade no lado esquerdo da janela Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-128">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="8e2cf-129">Selecione o ícone **Executar** para exibir a **exibição de Executar e Depurar.**</span><span class="sxs-lookup"><span data-stu-id="8e2cf-129">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="8e2cf-130">Você também pode usar o atalho de teclado **Ctrl+Shift+D**.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-130">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="8e2cf-131">Você pode não ver o aplicativo instalar diálogo no navegador se as janelas pop-up forem desativadas para o seu navegador.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-131">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="8e2cf-132">Se isso acontecer, habilite janelas pop-up e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="8e2cf-132">If this happens, enable pop-up windows and refresh the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e2cf-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e2cf-133">See also</span></span>

- [<span data-ttu-id="8e2cf-134">Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8e2cf-134">Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
