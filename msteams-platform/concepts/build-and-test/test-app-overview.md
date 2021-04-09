---
title: Testar a visão geral do aplicativo
description: Descreve o processo para testar seu aplicativo personalizado do Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o aplicativo de teste de carregamento do Teams de locatário do Microsoft 365
ms.openlocfilehash: b199ca4be31b546364091b754cdb890c8c0dd7d0
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634773"
---
# <a name="test-your-app"></a><span data-ttu-id="ee05a-104">Testar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ee05a-104">Test your app</span></span>

<span data-ttu-id="ee05a-105">Depois de integrar seu aplicativo ao Microsoft Teams, você deve testar seu aplicativo antes de publicá-lo.</span><span class="sxs-lookup"><span data-stu-id="ee05a-105">After integrating your app with Microsoft Teams, you must test your app before publishing it.</span></span> <span data-ttu-id="ee05a-106">O objetivo final é obter o máximo de usuários para seu aplicativo, portanto, garantir que o aplicativo seja testado em vários dispositivos que os usuários poderiam usar.</span><span class="sxs-lookup"><span data-stu-id="ee05a-106">The ultimate goal is to get as many users for your app, therefore, ensure to test the app on multiple devices that users could use.</span></span> <span data-ttu-id="ee05a-107">Para testar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ee05a-107">For testing your app:</span></span>

* <span data-ttu-id="ee05a-108">Preparar seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ee05a-108">Prepare your Microsoft 365 tenant</span></span>
* <span data-ttu-id="ee05a-109">Escolha um espaço de trabalho para testar e depurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ee05a-109">Choose a workspace to test and debug your app</span></span>
* <span data-ttu-id="ee05a-110">Adicionar dados de teste ao locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ee05a-110">Add test data to your Microsoft 365 tenant</span></span>

## <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="ee05a-111">Preparar seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ee05a-111">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="ee05a-112">Antes de começar a testar seu aplicativo, prepare seu locatário de teste do Microsoft 365 e habilita o aplicativo personalizado do Teams para que você carregue seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee05a-112">Before you start testing your app, prepare your Microsoft 365 test tenant and enable custom Teams app allow you to upload your app.</span></span> <span data-ttu-id="ee05a-113">Você deve se inscrever no programa de desenvolvedor do Microsoft 365 e gerenciar as configurações do Teams para sua organização.</span><span class="sxs-lookup"><span data-stu-id="ee05a-113">You must sign-up for Microsoft 365 developer program and manage the Teams settings for your organization.</span></span> <span data-ttu-id="ee05a-114">Configure sua assinatura de desenvolvedor e configure-a por meio da preparação do locatário do [Microsoft 365.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="ee05a-114">Set up your developer subscription and configure it through [prepare your Microsoft 365 Tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

## <a name="test-and-debug"></a><span data-ttu-id="ee05a-115">Testar e depurar</span><span class="sxs-lookup"><span data-stu-id="ee05a-115">Test and debug</span></span>

<span data-ttu-id="ee05a-116">Para testar e depurar seu aplicativo, você deve criar pelo menos um espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee05a-116">To test and debug your app, you must create at least one workspace.</span></span> <span data-ttu-id="ee05a-117">Você pode selecionar uma configuração de teste, como host local ou host baseado em nuvem para testar e depurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee05a-117">You can select a test setup, such as local host or cloud-based host to test and debug the app.</span></span> <span data-ttu-id="ee05a-118">As diretrizes para depurar seu aplicativo do Teams são fornecidas para carregar e executar a experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee05a-118">Guidance to debug your Teams app is provided to load and run your app experience.</span></span> <span data-ttu-id="ee05a-119">Para obter mais informações, [consulte choose a set up and run your Microsoft Teams app](~/concepts/build-and-test/debug.md).</span><span class="sxs-lookup"><span data-stu-id="ee05a-119">For more information, see [choose a set up and run your Microsoft Teams app](~/concepts/build-and-test/debug.md).</span></span>

<span data-ttu-id="ee05a-120">Teste seu bot localmente.</span><span class="sxs-lookup"><span data-stu-id="ee05a-120">Test your bot locally.</span></span> <span data-ttu-id="ee05a-121">Para obter mais informações, consulte [depurar seu bot localmente com um IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span><span class="sxs-lookup"><span data-stu-id="ee05a-121">For more information, see [debug your bot locally with an IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span></span> <span data-ttu-id="ee05a-122">Você também pode depurar seu bot com [middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) e [ferramentas adaptáveis.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ee05a-122">You can also debug your bot with [inspection middleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) and [adaptive tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true).</span></span> 

<span data-ttu-id="ee05a-123">Para exibir os logs do console, exibir ou modificar solicitações de html, css e rede durante o tempo de execução, adicione pontos de interrupção ao código JavaScript e execute a depuração interativa acesse o DevTools.</span><span class="sxs-lookup"><span data-stu-id="ee05a-123">To view the console logs, view or modify html, css, and network requests during runtime, add breakpoints to your JavaScript code, and perform interactive debugging access the DevTools.</span></span> <span data-ttu-id="ee05a-124">Para obter mais informações, [consulte Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ee05a-124">For more information, see [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md).</span></span> 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a><span data-ttu-id="ee05a-125">Adicionar dados de teste ao locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ee05a-125">Add test data to your Microsoft 365 tenant</span></span>

<span data-ttu-id="ee05a-126">Adicione os dados de teste ao locatário de teste do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ee05a-126">Add the test data to Microsoft 365 test tenant.</span></span> <span data-ttu-id="ee05a-127">Para obter mais informações, consulte [add test data to your Office 365 test tenant](~/concepts/build-and-test/test-data.md), and complete all the prerequisites before you start uploading your test data.</span><span class="sxs-lookup"><span data-stu-id="ee05a-127">For more information, see [add test data to your Office 365 test tenant](~/concepts/build-and-test/test-data.md), and complete all the prerequisites before you start uploading your test data.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee05a-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee05a-128">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee05a-129">Depurar sua guia</span><span class="sxs-lookup"><span data-stu-id="ee05a-129">Debug your tab</span></span>](~/tabs/how-to/developer-tools.md)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="ee05a-130">Depurar seus bots</span><span class="sxs-lookup"><span data-stu-id="ee05a-130">Debug your bots</span></span>](~/bots/how-to/debug/locally-with-an-ide.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee05a-131">Testar permissões RSC</span><span class="sxs-lookup"><span data-stu-id="ee05a-131">Test RSC permissions</span></span>](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a><span data-ttu-id="ee05a-132">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ee05a-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee05a-133">Preparar seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ee05a-133">Prepare your Microsoft 365 tenant</span></span>](~/concepts/build-and-test/prepare-your-o365-tenant.md)
