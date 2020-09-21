---
title: Adicionar autenticação ao bot do Microsoft Teams
author: clearab
description: Como adicionar a autenticação OAuth a um bot no Microsoft Teams.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 403072efeccdd09e46ac93e2e811ee2d10131668
ms.sourcegitcommit: aabfd65a67e1889ec16f09476bc757dd4a46ec5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48097883"
---
# <a name="add-authentication-to-your-teams-bot"></a><span data-ttu-id="30dc7-103">Adicionar autenticação ao bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="30dc7-103">Add authentication to your Teams bot</span></span>

<span data-ttu-id="30dc7-104">Há ocasiões em que você pode precisar criar bots no Microsoft Teams que podem acessar recursos em nome do usuário, como um serviço de email.</span><span class="sxs-lookup"><span data-stu-id="30dc7-104">There are times when you may need to create bots in Microsoft Teams that can access resources on behalf of the user, such as a mail service.</span></span>

<span data-ttu-id="30dc7-105">Este artigo demonstra como usar a autenticação do SDK do Azure bot Service v4, com base no OAuth 2,0.</span><span class="sxs-lookup"><span data-stu-id="30dc7-105">This article demonstrates how to use Azure Bot Service v4 SDK authentication, based on OAuth 2.0.</span></span> <span data-ttu-id="30dc7-106">Isso facilita o desenvolvimento de um bot que pode usar tokens de autenticação com base nas credenciais do usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-106">This makes it easier to develop a bot that can use authentication tokens based on the user's credentials.</span></span> <span data-ttu-id="30dc7-107">A chave é o uso de provedores de **identidade**, como veremos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="30dc7-107">Key in all this is the use of **identity providers**, as we will see later.</span></span>

<span data-ttu-id="30dc7-108">O OAuth 2,0 é um padrão aberto para autenticação e autorização usados pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="30dc7-108">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="30dc7-109">Uma compreensão básica do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="30dc7-109">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

<span data-ttu-id="30dc7-110">Consulte [OAuth 2 simplificado](https://aka.ms/oauth2-simplified) para obter uma compreensão básica e o [OAuth 2,0](https://oauth.net/2/) para a especificação completa.</span><span class="sxs-lookup"><span data-stu-id="30dc7-110">See [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) for a basic understanding, and [OAuth 2.0](https://oauth.net/2/) for the complete specification.</span></span>

<span data-ttu-id="30dc7-111">Para obter mais informações sobre como o serviço de bot do Azure trata a autenticação, confira [autenticação do usuário em uma conversa](https://aka.ms/azure-bot-authentication).</span><span class="sxs-lookup"><span data-stu-id="30dc7-111">For more information about how the Azure Bot Service handles authentication, see [User authentication within a conversation](https://aka.ms/azure-bot-authentication).</span></span>

<span data-ttu-id="30dc7-112">Neste artigo, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="30dc7-112">In this article you'll learn:</span></span>

- <span data-ttu-id="30dc7-113">**Como criar um bot habilitado para autenticação**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-113">**How to create an authentication-enabled bot**.</span></span> <span data-ttu-id="30dc7-114">Você usará o [cs-auth-Sample][teams-auth-bot-cs] para lidar com as credenciais de entrada do usuário e a geração do token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-114">You'll use [cs-auth-sample][teams-auth-bot-cs] to handle user sign-in credentials and the generating the authentication token.</span></span>
- <span data-ttu-id="30dc7-115">**Como implantar o bot no Azure e associá-lo a um provedor de identidade**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-115">**How to deploy the bot to Azure and associate it with an identity provider**.</span></span> <span data-ttu-id="30dc7-116">O provedor emite um token com base nas credenciais de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-116">The provider issues a token based on user sign-in credentials.</span></span> <span data-ttu-id="30dc7-117">O bot pode usar o token para acessar recursos, como um serviço de email, que requer autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-117">The bot can use the token to access resources, such as a mail service, which require authentication.</span></span> <span data-ttu-id="30dc7-118">Para obter mais informações, consulte  [Microsoft Teams Authentication Flow for bots](auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="30dc7-118">For more information see  [Microsoft Teams authentication flow for bots](auth-flow-bot.md).</span></span>
- <span data-ttu-id="30dc7-119">**Como integrar o bot no Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-119">**How to integrate the bot within Microsoft Teams**.</span></span> <span data-ttu-id="30dc7-120">Após a integração do bot, você poderá entrar e trocar mensagens com ela em um chat.</span><span class="sxs-lookup"><span data-stu-id="30dc7-120">Once the bot has been integrated, you can sign in and exchange messages with it in a chat.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30dc7-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="30dc7-121">Prerequisites</span></span>

- <span data-ttu-id="30dc7-122">Conhecimento das [noções básicas de bot][concept-basics], [Gerenciamento de estado][concept-state], a biblioteca de [caixas de diálogo][concept-dialogs]e como implementar o [fluxo de conversa seqüencial][simple-dialog].</span><span class="sxs-lookup"><span data-stu-id="30dc7-122">Knowledge of [bot basics][concept-basics], [managing state][concept-state], the [dialogs library][concept-dialogs], and how to [implement sequential conversation flow][simple-dialog].</span></span>
- <span data-ttu-id="30dc7-123">Conhecimento sobre o desenvolvimento do Azure e do OAuth 2,0.</span><span class="sxs-lookup"><span data-stu-id="30dc7-123">Knowledge of Azure and OAuth 2.0 development.</span></span>
- <span data-ttu-id="30dc7-124">As versões atuais do Visual Studio e git.</span><span class="sxs-lookup"><span data-stu-id="30dc7-124">The current versions of Visual Studio and Git.</span></span>
- <span data-ttu-id="30dc7-125">Conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="30dc7-125">Azure account.</span></span> <span data-ttu-id="30dc7-126">Se necessário, você pode criar uma [conta gratuita do Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="30dc7-126">If needed, you can create an [Azure free account](https://azure.microsoft.com/free/).</span></span>
- <span data-ttu-id="30dc7-127">O exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="30dc7-127">The following sample.</span></span>

    | <span data-ttu-id="30dc7-128">Amostra</span><span class="sxs-lookup"><span data-stu-id="30dc7-128">Sample</span></span> | <span data-ttu-id="30dc7-129">Versão do BotBuilder</span><span class="sxs-lookup"><span data-stu-id="30dc7-129">BotBuilder version</span></span> | <span data-ttu-id="30dc7-130">Demonstra</span><span class="sxs-lookup"><span data-stu-id="30dc7-130">Demonstrates</span></span> |
    |:---|:---:|:---|
    | <span data-ttu-id="30dc7-131">**Autenticação de bot** no [cs-auth-Sample][teams-auth-bot-cs]</span><span class="sxs-lookup"><span data-stu-id="30dc7-131">**Bot authentication** in [cs-auth-sample][teams-auth-bot-cs]</span></span> | <span data-ttu-id="30dc7-132">V4</span><span class="sxs-lookup"><span data-stu-id="30dc7-132">v4</span></span> | <span data-ttu-id="30dc7-133">Suporte do OAuthCard</span><span class="sxs-lookup"><span data-stu-id="30dc7-133">OAuthCard support</span></span> |
    | <span data-ttu-id="30dc7-134">**Autenticação de bot** no [js-auth-Sample][teams-auth-bot-js]</span><span class="sxs-lookup"><span data-stu-id="30dc7-134">**Bot authentication** in [js-auth-sample][teams-auth-bot-js]</span></span> | <span data-ttu-id="30dc7-135">V4</span><span class="sxs-lookup"><span data-stu-id="30dc7-135">v4</span></span>| <span data-ttu-id="30dc7-136">Suporte do OAuthCard</span><span class="sxs-lookup"><span data-stu-id="30dc7-136">OAuthCard support</span></span>  |
    | <span data-ttu-id="30dc7-137">**Autenticação de bot** no [py-auth-Sample][teams-auth-bot-py]</span><span class="sxs-lookup"><span data-stu-id="30dc7-137">**Bot authentication** in [py-auth-sample][teams-auth-bot-py]</span></span> | <span data-ttu-id="30dc7-138">V4</span><span class="sxs-lookup"><span data-stu-id="30dc7-138">v4</span></span> | <span data-ttu-id="30dc7-139">Suporte do OAuthCard</span><span class="sxs-lookup"><span data-stu-id="30dc7-139">OAuthCard support</span></span> |

## <a name="create-the-resource-group"></a><span data-ttu-id="30dc7-140">Criar o grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="30dc7-140">Create the resource group</span></span>

<span data-ttu-id="30dc7-141">O grupo de recursos e o plano de serviço não são estritamente necessários, mas permitem que você libere convenientemente os recursos que você criou.</span><span class="sxs-lookup"><span data-stu-id="30dc7-141">The resource group and the service plan aren't strictly necessary, but they allow you to conveniently release the resources you create.</span></span> <span data-ttu-id="30dc7-142">Essa é uma boa prática para manter seus recursos organizados e gerenciáveis.</span><span class="sxs-lookup"><span data-stu-id="30dc7-142">This is good practice for keeping your resources organized and manageable.</span></span>

<span data-ttu-id="30dc7-143">Você usa um grupo de recursos para criar recursos individuais para a estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-143">You use a resource group to create individual resources for the Bot Framework.</span></span> <span data-ttu-id="30dc7-144">Para desempenho, verifique se esses recursos estão localizados na mesma região do Azure.</span><span class="sxs-lookup"><span data-stu-id="30dc7-144">For performance, ensure that these resources are located in the same Azure region.</span></span>

1. <span data-ttu-id="30dc7-145">No seu navegador, entre no [**portal do Azure**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="30dc7-145">In your browser, sign into the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="30dc7-146">No painel de navegação esquerdo, selecione **grupos de recursos**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-146">In the left navigation panel, select **Resource groups**.</span></span>
1. <span data-ttu-id="30dc7-147">Na parte superior esquerda da janela exibida, selecione a guia **Adicionar** para criar um novo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-147">In the upper left of the displayed window, select **Add** tab to create a new resource group.</span></span> <span data-ttu-id="30dc7-148">Você será solicitado a fornecer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="30dc7-148">You'll be prompted to provide the following:</span></span>
    1. <span data-ttu-id="30dc7-149">**Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-149">**Subscription**.</span></span> <span data-ttu-id="30dc7-150">Use sua assinatura existente.</span><span class="sxs-lookup"><span data-stu-id="30dc7-150">Use your existing subscription.</span></span>
    1. <span data-ttu-id="30dc7-151">**Grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-151">**Resource group**.</span></span> <span data-ttu-id="30dc7-152">Insira o nome do grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-152">Enter the name for the resource group.</span></span> <span data-ttu-id="30dc7-153">Um exemplo poderia ser  *TeamsResourceGroup*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-153">An example could be  *TeamsResourceGroup*.</span></span> <span data-ttu-id="30dc7-154">Lembre-se de que o nome deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-154">Remember that the name must be unique.</span></span>
    1. <span data-ttu-id="30dc7-155">No menu suspenso **região** , selecione *oeste dos EUA*ou uma região perto de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-155">From the **Region** drop-down menu, select *West US*, or a region close to your applications.</span></span>
    1. <span data-ttu-id="30dc7-156">Selecione o botão **revisar e criar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-156">Select the **Review and create** button.</span></span> <span data-ttu-id="30dc7-157">Você verá uma faixa que lê a *validação aprovada*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-157">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="30dc7-158">Selecione o botão **criar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-158">Select the **Create** button.</span></span> <span data-ttu-id="30dc7-159">Pode levar alguns minutos para criar o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-159">It may take a few minutes to create the resource group.</span></span>

> [!TIP]
> <span data-ttu-id="30dc7-160">Da mesma forma que os recursos que você criará posteriormente neste tutorial, é uma boa ideia fixar esse grupo de recursos no painel para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="30dc7-160">As with the resources you'll create later in this tutorial, it's a good idea to pin this resource group to your dashboard for easy access.</span></span> <span data-ttu-id="30dc7-161">Se quiser fazer isso, selecione o ícone de PIN & # 128204; no canto superior direito do painel.</span><span class="sxs-lookup"><span data-stu-id="30dc7-161">If you'd like to do so, select the pin icon &#128204; in the upper right of the dashboard.</span></span>

## <a name="create-the-service-plan"></a><span data-ttu-id="30dc7-162">Criar o plano de serviço</span><span class="sxs-lookup"><span data-stu-id="30dc7-162">Create the service plan</span></span>

1. <span data-ttu-id="30dc7-163">No [**portal do Azure**][azure-portal], no painel de navegação à esquerda, selecione **criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-163">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Create a resource**.</span></span>
1. <span data-ttu-id="30dc7-164">Na caixa de pesquisa, digite *plano de serviço de aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-164">In the search box, type *App Service Plan*.</span></span> <span data-ttu-id="30dc7-165">Selecione o cartão de **plano do serviço de aplicativo** nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="30dc7-165">Select the **App Service Plan** card from the search results.</span></span>
1. <span data-ttu-id="30dc7-166">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-166">Select **Create**.</span></span>
1. <span data-ttu-id="30dc7-167">Você será solicitado a fornecer as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="30dc7-167">You'll be asked to provide the following information:</span></span>
    1. <span data-ttu-id="30dc7-168">**Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-168">**Subscription**.</span></span> <span data-ttu-id="30dc7-169">Você pode usar uma assinatura existente.</span><span class="sxs-lookup"><span data-stu-id="30dc7-169">You can use an existing subscription.</span></span>
    1. <span data-ttu-id="30dc7-170">**Grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-170">**Resource Group**.</span></span> <span data-ttu-id="30dc7-171">Selecione o grupo que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="30dc7-171">Select the group you created earlier.</span></span>
    1. <span data-ttu-id="30dc7-172">**Nome**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-172">**Name**.</span></span> <span data-ttu-id="30dc7-173">Insira o nome do plano de serviço.</span><span class="sxs-lookup"><span data-stu-id="30dc7-173">Enter the name for the service plan.</span></span> <span data-ttu-id="30dc7-174">Um exemplo poderia ser  *TeamsServicePlan*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-174">An example could be  *TeamsServicePlan*.</span></span> <span data-ttu-id="30dc7-175">Lembre-se de que o nome deve ser exclusivo no grupo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-175">Remember that the name must be unique, within the group.</span></span>
    1. <span data-ttu-id="30dc7-176">**Sistema operacional**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-176">**Operating System**.</span></span> <span data-ttu-id="30dc7-177">Selecione *Windows* ou seu sistema operacional aplicável.</span><span class="sxs-lookup"><span data-stu-id="30dc7-177">Select *Windows* or your applicable OS.</span></span>
    1. <span data-ttu-id="30dc7-178">**Região**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-178">**Region**.</span></span> <span data-ttu-id="30dc7-179">Selecione *oeste dos EUA* ou uma região perto de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-179">Select *West US* or a region close to your applications.</span></span>
    1. <span data-ttu-id="30dc7-180">**Camada de preços**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-180">**Pricing Tier**.</span></span> <span data-ttu-id="30dc7-181">Verifique se *S1 padrão* está selecionado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-181">Make sure that *Standard S1* is selected.</span></span> <span data-ttu-id="30dc7-182">Este deve ser o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="30dc7-182">This should be the default value.</span></span>
    1. <span data-ttu-id="30dc7-183">Selecione o botão **revisar e criar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-183">Select the **Review and create** button.</span></span> <span data-ttu-id="30dc7-184">Você verá uma faixa que lê a *validação aprovada*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-184">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="30dc7-185">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-185">Select **Create**.</span></span> <span data-ttu-id="30dc7-186">Pode levar alguns minutos para criar o plano de serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-186">It may take a few minutes to create the app service plan.</span></span> <span data-ttu-id="30dc7-187">O plano será listado no grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-187">The plan will be listed in the resource group.</span></span>

## <a name="create-the-bot-channels-registration"></a><span data-ttu-id="30dc7-188">Criar o registro de canais de bot</span><span class="sxs-lookup"><span data-stu-id="30dc7-188">Create the bot channels registration</span></span>

<span data-ttu-id="30dc7-189">O registro de canais de bot registra seu serviço Web como um bot com a estrutura de bot, desde que você tenha uma ID de aplicativo da Microsoft e uma senha de aplicativo (segredo do cliente).</span><span class="sxs-lookup"><span data-stu-id="30dc7-189">The bot channels registration registers your web service as a bot with the Bot Framework, provided you have a Microsoft App Id and App password (client secret).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30dc7-190">Você só precisa registrar seu bot se ele não estiver hospedado no Azure.</span><span class="sxs-lookup"><span data-stu-id="30dc7-190">You only need to register your bot if it is not hosted in Azure.</span></span> <span data-ttu-id="30dc7-191">Se você [criou um bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) por meio do portal do Azure, ele já está registrado com o serviço.</span><span class="sxs-lookup"><span data-stu-id="30dc7-191">If you [created a bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) through the Azure portal then it is already registered with the service.</span></span> <span data-ttu-id="30dc7-192">Se você criou o bot por meio da [estrutura de bot](https://dev.botframework.com/bots/new) ou [AppStudio](~/concepts/build-and-test/app-studio-overview.md) seu bot não está registrado no Azure.</span><span class="sxs-lookup"><span data-stu-id="30dc7-192">If you created your bot through the [Bot Framework](https://dev.botframework.com/bots/new) or [AppStudio](~/concepts/build-and-test/app-studio-overview.md) your bot isn't registered in Azure.</span></span>

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> <span data-ttu-id="30dc7-193">O recurso de registro de canais de bot mostrará a região **global** , mesmo se você selecionar oeste dos EUA.</span><span class="sxs-lookup"><span data-stu-id="30dc7-193">The Bot Channels Registration resource will show the **Global** region even if you selected West US.</span></span> <span data-ttu-id="30dc7-194">Isso é esperado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-194">This is expected.</span></span>

<span data-ttu-id="30dc7-195">Para obter mais informações, consulte [Create a bot for Teams](../create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="30dc7-195">For more information, see [Create a bot for Teams](../create-a-bot-for-teams.md).</span></span>

## <a name="create-the-identity-provider"></a><span data-ttu-id="30dc7-196">Criar o provedor de identidade</span><span class="sxs-lookup"><span data-stu-id="30dc7-196">Create the identity provider</span></span>

<span data-ttu-id="30dc7-197">Você precisa de um provedor de identidade que possa ser usado para autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-197">You need an identity provider that can be used for authentication.</span></span>
<span data-ttu-id="30dc7-198">Neste procedimento, você usará um provedor do Azure AD; outros provedores de identidade compatíveis com o Azure AD também podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="30dc7-198">In this procedure you'll use an Azure AD provider; other Azure AD supported identity providers can also be used.</span></span>

1. <span data-ttu-id="30dc7-199">No [**portal do Azure**][azure-portal], no painel de navegação à esquerda, selecione **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-199">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Azure Active Directory**.</span></span>
    > [!TIP]
    > <span data-ttu-id="30dc7-200">Você precisará criar e registrar esse recurso do Azure AD em um locatário no qual você pode concordar em delegar permissões solicitadas por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-200">You'll need to create and register this Azure AD resource in a tenant in which you can consent to delegate permissions requested by an application.</span></span>
    > <span data-ttu-id="30dc7-201">Para obter instruções sobre como criar um locatário, confira [acessar o portal e criar um locatário](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span><span class="sxs-lookup"><span data-stu-id="30dc7-201">For instruction on creating a tenant, see [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span></span>
1. <span data-ttu-id="30dc7-202">No painel esquerdo, selecione **registros de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-202">In the left panel, select **App registrations**.</span></span>
1. <span data-ttu-id="30dc7-203">No painel direito, selecione a guia **novo registro** , no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-203">In the right panel, select the **New registration** tab, in the upper left.</span></span>
1. <span data-ttu-id="30dc7-204">Você será solicitado a fornecer as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="30dc7-204">You'll be asked to provide the following information:</span></span>
   1. <span data-ttu-id="30dc7-205">**Nome**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-205">**Name**.</span></span> <span data-ttu-id="30dc7-206">Insira o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-206">Enter the name for the application.</span></span> <span data-ttu-id="30dc7-207">Um exemplo poderia ser  *BotTeamsIdentity*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-207">An example could be  *BotTeamsIdentity*.</span></span> <span data-ttu-id="30dc7-208">Lembre-se de que o nome deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-208">Remember that the name must be unique.</span></span>
   1. <span data-ttu-id="30dc7-209">Selecione os **tipos de conta com suporte** para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-209">Select the **Supported account types** for your application.</span></span> <span data-ttu-id="30dc7-210">Selecione *contas em qualquer diretório organizacional (qualquer diretório do Azure ad-multilocatário) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-210">Select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
   1. <span data-ttu-id="30dc7-211">Para o **URI de redirecionamento**:</span><span class="sxs-lookup"><span data-stu-id="30dc7-211">For the **Redirect URI**:</span></span><br/>
       <span data-ttu-id="30dc7-212">&#x2713;selecione **Web**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-212">&#x2713;Select **Web**.</span></span> <br/>
       <span data-ttu-id="30dc7-213">&#x2713; definir a URL como `https://token.botframework.com/.auth/web/redirect` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-213">&#x2713; Set the URL to `https://token.botframework.com/.auth/web/redirect`.</span></span>
   1. <span data-ttu-id="30dc7-214">Selecione **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-214">Select **Register**.</span></span>

1. <span data-ttu-id="30dc7-215">Depois que ele for criado, o Azure exibirá a página **visão geral** do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-215">Once it is created, Azure displays the **Overview** page for the app.</span></span> <span data-ttu-id="30dc7-216">Copie e salve as seguintes informações em um arquivo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-216">Copy and save the following information to a file:</span></span>

    1. <span data-ttu-id="30dc7-217">O valor da **ID do aplicativo (cliente)** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-217">The **Application (client) ID** value.</span></span> <span data-ttu-id="30dc7-218">Você usará esse valor mais tarde como a *ID do cliente* ao registrar esse aplicativo de identidade do Azure no bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-218">You'll use this value later as the *Client ID* when you register this Azure identity application with your bot.</span></span>
    1. <span data-ttu-id="30dc7-219">O valor da **ID do diretório (locatário)** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-219">The **Directory (tenant) ID** value.</span></span> <span data-ttu-id="30dc7-220">Você também usará esse valor mais tarde como a *ID de locatário* para registrar esse aplicativo de identidade do Azure no bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-220">You'll also use this value later as the *Tenant ID* to register this Azure identity application with your bot.</span></span>

1. <span data-ttu-id="30dc7-221">No painel esquerdo, selecione **certificados & segredos** para criar um segredo do cliente para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-221">In the left panel, select **Certificates & secrets** to create a client secret for your application.</span></span>

   1. <span data-ttu-id="30dc7-222">Em **segredos do cliente**, selecione &#x2795; **novo segredo do cliente**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-222">Under **Client secrets**, select &#x2795; **New client secret**.</span></span>
   1. <span data-ttu-id="30dc7-223">Adicione uma descrição para identificar esse segredo de outras pessoas que você talvez precise criar para esse aplicativo, como o *aplicativo de identidade de bot no Microsoft Teams*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-223">Add a description to identify this secret from others you might need to create for this app, such as *Bot identity app in Teams*.</span></span>
   1. <span data-ttu-id="30dc7-224">Definir **expira** para sua seleção.</span><span class="sxs-lookup"><span data-stu-id="30dc7-224">Set **Expires** to your selection.</span></span>
   1. <span data-ttu-id="30dc7-225">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-225">Select **Add**.</span></span>
   1. <span data-ttu-id="30dc7-226">Antes de sair desta página, **Registre o segredo**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-226">Before leaving this page, **record the secret**.</span></span> <span data-ttu-id="30dc7-227">Você usará esse valor mais tarde como o _segredo do cliente_ quando registrar seu aplicativo do Azure AD com o bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-227">You'll use this value later as the _Client secret_ when you register your Azure AD application with your bot.</span></span>

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a><span data-ttu-id="30dc7-228">Configurar a conexão do provedor de identidade e registrá-la com o bot</span><span class="sxs-lookup"><span data-stu-id="30dc7-228">Configure the identity provider connection and register it with the bot</span></span>

<span data-ttu-id="30dc7-229">Observação: há duas opções para os provedores de serviços aqui-Azure AD v1 e Azure AD v2.</span><span class="sxs-lookup"><span data-stu-id="30dc7-229">Note-there are two options for Service Providers here-Azure AD V1 and Azure AD V2.</span></span>  <span data-ttu-id="30dc7-230">As diferenças entre os dois provedores são resumidas [aqui](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), mas em geral, o v2 fornece mais flexibilidade com relação à alteração das permissões de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-230">The differences between the two providers are summarized [here](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), but in general, V2 provides more flexibility with respect to changing bot permissions.</span></span>  <span data-ttu-id="30dc7-231">As permissões de API do Graph estão listadas no campo escopos, e à medida que novas são adicionadas, os bots permitirão que os usuários concordem nas novas permissões na próxima entrada.</span><span class="sxs-lookup"><span data-stu-id="30dc7-231">Graph API permissions are listed in the scopes field, and as new ones are added, bots will allow users to consent to the new permissions on the next sign in.</span></span>  <span data-ttu-id="30dc7-232">Para o v1, o consentimento de bot deve ser excluído pelo usuário para novas permissões a serem solicitadas na caixa de diálogo do OAuth.</span><span class="sxs-lookup"><span data-stu-id="30dc7-232">For V1, the bot consent must be deleted by the user for new permissions to be prompted in the OAuth dialog.</span></span> 

#### <a name="azure-ad-v1"></a><span data-ttu-id="30dc7-233">Azure AD v1</span><span class="sxs-lookup"><span data-stu-id="30dc7-233">Azure AD V1</span></span>

1. <span data-ttu-id="30dc7-234">No [**portal do Azure**][azure-portal], selecione o grupo de recursos no painel.</span><span class="sxs-lookup"><span data-stu-id="30dc7-234">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="30dc7-235">Selecione o link de registro do canal do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-235">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="30dc7-236">Na página recurso, selecione **configurações**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-236">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="30dc7-237">Em **configurações de conexão OAuth** próximo à parte inferior da página, selecione **Adicionar configuração**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-237">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="30dc7-238">Preencha o formulário de acordo com as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="30dc7-238">Complete the form as follows:</span></span>

    1. <span data-ttu-id="30dc7-239">**Nome**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-239">**Name**.</span></span> <span data-ttu-id="30dc7-240">Insira um nome para a conexão.</span><span class="sxs-lookup"><span data-stu-id="30dc7-240">Enter a name for the connection.</span></span> <span data-ttu-id="30dc7-241">Você usará esse nome no bot no `appsettings.json` arquivo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-241">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="30dc7-242">Por exemplo *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-242">For example *BotTeamsAuthADv1*.</span></span>
    1. <span data-ttu-id="30dc7-243">**Provedor de serviços**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-243">**Service Provider**.</span></span> <span data-ttu-id="30dc7-244">Selecione **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-244">Select **Azure Active Directory**.</span></span> <span data-ttu-id="30dc7-245">Depois que você selecionar isso, os campos específicos do Azure AD serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-245">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="30dc7-246">**ID do cliente**. Insira a ID do aplicativo (cliente) que você registrou para seu aplicativo do provedor de identidade do Azure nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="30dc7-246">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="30dc7-247">**Segredo do cliente**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-247">**Client secret**.</span></span> <span data-ttu-id="30dc7-248">Insira o segredo que você gravou para seu aplicativo do provedor de identidade do Azure nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="30dc7-248">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="30dc7-249">**Tipo de concessão**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-249">**Grant Type**.</span></span> <span data-ttu-id="30dc7-250">Inserir `authorization_code` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-250">Enter `authorization_code`.</span></span>
    1. <span data-ttu-id="30dc7-251">**URL de logon**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-251">**Login URL**.</span></span> <span data-ttu-id="30dc7-252">Inserir `https://login.microsoftonline.com` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-252">Enter `https://login.microsoftonline.com`.</span></span>
    1. <span data-ttu-id="30dc7-253">**ID do locatário**, digite a **ID do diretório (locatário)** registrada anteriormente para seu aplicativo de identidade do Azure ou **comum** , dependendo do tipo de conta com suporte selecionado quando você criou o aplicativo do provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="30dc7-253">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="30dc7-254">Para decidir qual o valor a ser atribuído siga estes critérios:</span><span class="sxs-lookup"><span data-stu-id="30dc7-254">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="30dc7-255">Se você selecionou *contas nesse diretório organizacional apenas (Microsoft somente um locatário)* ou *contas em qualquer diretório organizacional (Microsoft AAD Directory-multilocatário)* , insira a **ID do locatário** que você gravou anteriormente para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="30dc7-255">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="30dc7-256">Este será o locatário associado aos usuários que podem ser autenticados.</span><span class="sxs-lookup"><span data-stu-id="30dc7-256">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="30dc7-257">Se você selecionou *contas em qualquer diretório organizacional (qualquer usuário do AAD-multilocatário e contas pessoais da Microsoft, por exemplo, Skype, Xbox, Outlook)* , insira a palavra **comum** em vez de uma ID de locatário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-257">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="30dc7-258">Caso contrário, o aplicativo AAD verificará o locatário cuja ID foi selecionada e excluirá contas pessoais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="30dc7-258">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    <span data-ttu-id="30dc7-259">0.</span><span class="sxs-lookup"><span data-stu-id="30dc7-259">h.</span></span> <span data-ttu-id="30dc7-260">Para **URL de recurso**, insira `https://graph.microsoft.com/` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-260">For **Resource URL**, enter `https://graph.microsoft.com/`.</span></span> <span data-ttu-id="30dc7-261">Isso não é usado no exemplo de código atual.</span><span class="sxs-lookup"><span data-stu-id="30dc7-261">This is not used in the current code sample.</span></span>  
    <span data-ttu-id="30dc7-262">i.</span><span class="sxs-lookup"><span data-stu-id="30dc7-262">i.</span></span> <span data-ttu-id="30dc7-263">Deixe **escopos** em branco.</span><span class="sxs-lookup"><span data-stu-id="30dc7-263">Leave **Scopes** blank.</span></span> <span data-ttu-id="30dc7-264">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-264">The following image is an example:</span></span>

    ![visão Adv1 da cadeia de conexão do App bots do Team](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. <span data-ttu-id="30dc7-266">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-266">Select **Save**.</span></span>

#### <a name="azure-ad-v2"></a><span data-ttu-id="30dc7-267">Azure AD v2</span><span class="sxs-lookup"><span data-stu-id="30dc7-267">Azure AD V2</span></span>

1. <span data-ttu-id="30dc7-268">No [**portal do Azure**][azure-portal], selecione o grupo de recursos no painel.</span><span class="sxs-lookup"><span data-stu-id="30dc7-268">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="30dc7-269">Selecione o link de registro do canal do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-269">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="30dc7-270">Na página recurso, selecione **configurações**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-270">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="30dc7-271">Em **configurações de conexão OAuth** próximo à parte inferior da página, selecione **Adicionar configuração**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-271">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="30dc7-272">Preencha o formulário de acordo com as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="30dc7-272">Complete the form as follows:</span></span>

    1. <span data-ttu-id="30dc7-273">**Nome**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-273">**Name**.</span></span> <span data-ttu-id="30dc7-274">Insira um nome para a conexão.</span><span class="sxs-lookup"><span data-stu-id="30dc7-274">Enter a name for the connection.</span></span> <span data-ttu-id="30dc7-275">Você usará esse nome no bot no `appsettings.json` arquivo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-275">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="30dc7-276">Por exemplo *BotTeamsAuthADv2*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-276">For example *BotTeamsAuthADv2*.</span></span>
    1. <span data-ttu-id="30dc7-277">**Provedor de serviços**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-277">**Service Provider**.</span></span> <span data-ttu-id="30dc7-278">Selecione **Azure Active Directory v2**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-278">Select **Azure Active Directory v2**.</span></span> <span data-ttu-id="30dc7-279">Depois que você selecionar isso, os campos específicos do Azure AD serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-279">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="30dc7-280">**ID do cliente**. Insira a ID do aplicativo (cliente) que você registrou para seu aplicativo do provedor de identidade do Azure nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="30dc7-280">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="30dc7-281">**Segredo do cliente**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-281">**Client secret**.</span></span> <span data-ttu-id="30dc7-282">Insira o segredo que você gravou para seu aplicativo do provedor de identidade do Azure nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="30dc7-282">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="30dc7-283">**URL do token do Exchange**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-283">**Token Exchange URL**.</span></span> <span data-ttu-id="30dc7-284">Deixe em branco.</span><span class="sxs-lookup"><span data-stu-id="30dc7-284">Leave this blank.</span></span>
    1. <span data-ttu-id="30dc7-285">**ID do locatário**, digite a **ID do diretório (locatário)** registrada anteriormente para seu aplicativo de identidade do Azure ou **comum** , dependendo do tipo de conta com suporte selecionado quando você criou o aplicativo do provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="30dc7-285">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="30dc7-286">Para decidir qual o valor a ser atribuído siga estes critérios:</span><span class="sxs-lookup"><span data-stu-id="30dc7-286">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="30dc7-287">Se você selecionou *contas nesse diretório organizacional apenas (Microsoft somente um locatário)* ou *contas em qualquer diretório organizacional (Microsoft AAD Directory-multilocatário)* , insira a **ID do locatário** que você gravou anteriormente para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="30dc7-287">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="30dc7-288">Este será o locatário associado aos usuários que podem ser autenticados.</span><span class="sxs-lookup"><span data-stu-id="30dc7-288">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="30dc7-289">Se você selecionou *contas em qualquer diretório organizacional (qualquer usuário do AAD-multilocatário e contas pessoais da Microsoft, por exemplo, Skype, Xbox, Outlook)* , insira a palavra **comum** em vez de uma ID de locatário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-289">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="30dc7-290">Caso contrário, o aplicativo AAD verificará o locatário cuja ID foi selecionada e excluirá contas pessoais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="30dc7-290">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    1. <span data-ttu-id="30dc7-291">Para **escopos**, insira uma lista delimitada por espaço de permissões de gráfico que esse aplicativo requer por exemplo: user. Read User. ReadBasic. All mail. Read</span><span class="sxs-lookup"><span data-stu-id="30dc7-291">For **Scopes**, enter a space-delimited list of graph permissions this application requires e.g.: User.Read User.ReadBasic.All Mail.Read</span></span> 

1. <span data-ttu-id="30dc7-292">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-292">Select **Save**.</span></span>

### <a name="test-the-connection"></a><span data-ttu-id="30dc7-293">Testar a conexão</span><span class="sxs-lookup"><span data-stu-id="30dc7-293">Test the connection</span></span>

1. <span data-ttu-id="30dc7-294">Selecione a entrada de conexão para abrir a conexão que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-294">Select the connection entry to open the connection you just created.</span></span>
1. <span data-ttu-id="30dc7-295">Selecione **testar conexão** na parte superior do painel **configuração de conexão do provedor de serviços** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-295">Select **Test Connection** at the top of the **Service Provider Connection Setting** panel.</span></span>
1. <span data-ttu-id="30dc7-296">Na primeira vez que você fizer isso, abrirá uma nova janela do navegador solicitando que você selecione uma conta.</span><span class="sxs-lookup"><span data-stu-id="30dc7-296">The first time you do this will open a new browser window asking you to select an account.</span></span> <span data-ttu-id="30dc7-297">Selecione aquele que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-297">Select the one you want to use.</span></span>
1. <span data-ttu-id="30dc7-298">Em seguida, você será solicitado a permitir que o provedor de identidade use seus dados (credenciais).</span><span class="sxs-lookup"><span data-stu-id="30dc7-298">Next, you'll be asked to allow to the identity provider to use your data (credentials).</span></span> <span data-ttu-id="30dc7-299">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-299">The following image is an example:</span></span>

    ![Cadeia de conexão de autenticação de Adv1 de bot de equipes](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. <span data-ttu-id="30dc7-301">Selecione **aceitar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-301">Select **Accept**.</span></span>
1. <span data-ttu-id="30dc7-302">Isso deve ser redirecionado para uma **conexão de teste para uma página com \<your-connection-name> êxito** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-302">This should then redirect you to a **Test Connection to \<your-connection-name> Succeeded** page.</span></span> <span data-ttu-id="30dc7-303">Atualize a página se você receber um erro.</span><span class="sxs-lookup"><span data-stu-id="30dc7-303">Refresh the page if you get an error.</span></span> <span data-ttu-id="30dc7-304">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-304">The following image is an example:</span></span>

  ![Adv1 de Seq de conexão do aplicativo de bots do Microsoft Teams](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

<span data-ttu-id="30dc7-306">O nome da conexão é usado pelo código do bot para recuperar os tokens de autenticação do usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-306">The connection name is used by the bot code to retrieve user authentication tokens.</span></span>

## <a name="prepare-the-bot-sample-code"></a><span data-ttu-id="30dc7-307">Preparar o código de exemplo de bot</span><span class="sxs-lookup"><span data-stu-id="30dc7-307">Prepare the bot sample code</span></span>

<span data-ttu-id="30dc7-308">Com as configurações preliminares concluídas, vamos nos concentrar na criação do bot a ser usado neste artigo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-308">With the preliminary settings done, let's focus on the creation of the bot to use in this article.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="30dc7-309">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="30dc7-309">C#/.NET</span></span>](#tab/dotnet)

1. <span data-ttu-id="30dc7-310">Clone [cs-auth-Sample][teams-auth-bot-cs].</span><span class="sxs-lookup"><span data-stu-id="30dc7-310">Clone [cs-auth-sample][teams-auth-bot-cs].</span></span>
1. <span data-ttu-id="30dc7-311">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30dc7-311">Launch Visual Studio.</span></span>
1. <span data-ttu-id="30dc7-312">Na barra de ferramentas **, selecione Arquivo-> Open-> Project/Solution** e abra o projeto bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-312">From the toolbar select **File -> Open -> Project/Solution** and open the bot project.</span></span>
1. <span data-ttu-id="30dc7-313">Naappsettings.jsde atualização C# \*\* da\*\* seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="30dc7-313">In C# Update **appsettings.json** as follows:</span></span>

    - <span data-ttu-id="30dc7-314">Defina `ConnectionName` como o nome da conexão do provedor de identidade que você adicionou ao registro do canal de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-314">Set `ConnectionName` to the name of the identity provider connection you added to the bot channel registration.</span></span> <span data-ttu-id="30dc7-315">O nome usado neste exemplo é *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-315">The name we used in this example is *BotTeamsAuthADv1*.</span></span>
    - <span data-ttu-id="30dc7-316">Defina `MicrosoftAppId` como a **ID do aplicativo bot** que você salvou no momento do registro do canal de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-316">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="30dc7-317">Defina `MicrosoftAppPassword` como o **segredo do cliente** que você salvou no momento do registro do canal do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-317">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="30dc7-318">Defina o `ConnectionName` como o nome da conexão do provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="30dc7-318">Set the `ConnectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="30dc7-319">Dependendo dos caracteres no seu segredo de bot, talvez seja necessário escapar da senha por XML.</span><span class="sxs-lookup"><span data-stu-id="30dc7-319">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="30dc7-320">Por exemplo, qualquer e comercial (&) precisará ser codificado como `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-320">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. <span data-ttu-id="30dc7-321">No Gerenciador de soluções, navegue até a `TeamsAppManifest` pasta, abra `manifest.json` e defina `id` e `botId` para o **ID do aplicativo bot** que você salvou no momento do registro do canal de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-321">In the Solution Explorer, navigate to the `TeamsAppManifest` folder, open `manifest.json` and set `id` and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="javascript"></a>[<span data-ttu-id="30dc7-322">JavaScript</span><span class="sxs-lookup"><span data-stu-id="30dc7-322">JavaScript</span></span>](#tab/node-js)

1. <span data-ttu-id="30dc7-323">[Nó clone-auth-Sample][teams-auth-bot-js].</span><span class="sxs-lookup"><span data-stu-id="30dc7-323">Clone [node-auth-sample][teams-auth-bot-js].</span></span>
1. <span data-ttu-id="30dc7-324">Em um console, navegue até o projeto:</span><span class="sxs-lookup"><span data-stu-id="30dc7-324">In a console, navigate to the project:</span></span> </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. <span data-ttu-id="30dc7-325">Instalar módulos</span><span class="sxs-lookup"><span data-stu-id="30dc7-325">Install modules</span></span></br></br>
`npm install`
1. <span data-ttu-id="30dc7-326">Atualize a configuração **. env** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="30dc7-326">Update the **.env** configuration as follows:</span></span>

    - <span data-ttu-id="30dc7-327">Defina `MicrosoftAppId` como a **ID do aplicativo bot** que você salvou no momento do registro do canal de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-327">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="30dc7-328">Defina `MicrosoftAppPassword` como o **segredo do cliente** que você salvou no momento do registro do canal do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-328">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="30dc7-329">Defina o `connectionName` como o nome da conexão do provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="30dc7-329">Set the `connectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="30dc7-330">Dependendo dos caracteres no seu segredo de bot, talvez seja necessário escapar da senha por XML.</span><span class="sxs-lookup"><span data-stu-id="30dc7-330">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="30dc7-331">Por exemplo, qualquer e comercial (&) precisará ser codificado como `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-331">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. <span data-ttu-id="30dc7-332">Na `teamsAppManifest` pasta, abra `manifest.json` e defina `id`  como sua ID do aplicativo da **Microsoft** e `botId` para o **ID do aplicativo bot** que você salvou no momento do registro do canal de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-332">In the `teamsAppManifest` folder, open `manifest.json` and set `id`  to your **Microsoft App ID** and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="python"></a>[<span data-ttu-id="30dc7-333">Python</span><span class="sxs-lookup"><span data-stu-id="30dc7-333">Python</span></span>](#tab/python)

1. <span data-ttu-id="30dc7-334">Clone [py-auth-Sample][teams-auth-bot-py] no repositório do github.</span><span class="sxs-lookup"><span data-stu-id="30dc7-334">Clone [py-auth-sample][teams-auth-bot-py] from the github repository.</span></span>
1. <span data-ttu-id="30dc7-335">Atualizar **config.py**:</span><span class="sxs-lookup"><span data-stu-id="30dc7-335">Update **config.py**:</span></span>

    - <span data-ttu-id="30dc7-336">Defina `ConnectionName` como o nome da configuração de conexão OAuth que você adicionou ao bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-336">Set `ConnectionName` to the name of the OAuth connection setting you added to your bot.</span></span>
    - <span data-ttu-id="30dc7-337">Defina `MicrosoftAppId` e `MicrosoftAppPassword` para a ID de aplicativo do bot e o segredo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-337">Set `MicrosoftAppId` and `MicrosoftAppPassword` to your bot's app ID and app secret.</span></span>

      <span data-ttu-id="30dc7-338">Dependendo dos caracteres no seu segredo de bot, talvez seja necessário escapar da senha por XML.</span><span class="sxs-lookup"><span data-stu-id="30dc7-338">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="30dc7-339">Por exemplo, qualquer e comercial (&) precisará ser codificado como `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-339">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a><span data-ttu-id="30dc7-340">Implantar o bot no Azure</span><span class="sxs-lookup"><span data-stu-id="30dc7-340">Deploy the bot to Azure</span></span>

<span data-ttu-id="30dc7-341">Para implantar o bot, siga as etapas descritas em como [implantar seu bot no Azure](https://aka.ms/azure-bot-deployment-cli).</span><span class="sxs-lookup"><span data-stu-id="30dc7-341">To deploy the bot, follow the steps in the how to [Deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span></span>

<span data-ttu-id="30dc7-342">Como alternativa, enquanto no Visual Studio, você pode seguir estas etapas:</span><span class="sxs-lookup"><span data-stu-id="30dc7-342">Alternatively, while in Visual Studio, you can follow these steps:</span></span>

1. <span data-ttu-id="30dc7-343">No Visual Studio *Solution Explorer* , selecione e segure (ou clique com o botão direito do mouse) o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="30dc7-343">In Visual Studio *Solution Explorer* select and hold (or right-click) the project name.</span></span>
1. <span data-ttu-id="30dc7-344">No menu suspenso, selecione **publicar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-344">In the drop-down menu, select **Publish**.</span></span>
1. <span data-ttu-id="30dc7-345">Na janela exibida, selecione o **novo** link.</span><span class="sxs-lookup"><span data-stu-id="30dc7-345">In the displayed window, select the **New** link.</span></span>
1. <span data-ttu-id="30dc7-346">Na janela de diálogo, selecione **serviço de aplicativo** à esquerda e **crie novo** à direita.</span><span class="sxs-lookup"><span data-stu-id="30dc7-346">In the dialog window, select **App Service** on the left and **Create New** on the right.</span></span>
1. <span data-ttu-id="30dc7-347">Selecione o botão **publicar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-347">Select the **Publish** button.</span></span>
1. <span data-ttu-id="30dc7-348">Na próxima janela de diálogo, insira as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="30dc7-348">In the next dialog window, enter the required information.</span></span> <span data-ttu-id="30dc7-349">Este é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-349">The following is an example:</span></span>

   ![auth-app-Service](../../../assets/images/authentication/auth-bot-app-service.png)

1. <span data-ttu-id="30dc7-351">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-351">Select **Create**.</span></span>
1. <span data-ttu-id="30dc7-352">Se a implantação for concluída com êxito, você deverá vê-la refletida no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30dc7-352">If the deployment completes successfully, you should see it reflected in Visual Studio.</span></span> <span data-ttu-id="30dc7-353">Além disso, uma página é exibida no navegador padrão dizendo que *o bot está pronto!*.</span><span class="sxs-lookup"><span data-stu-id="30dc7-353">Moreover, a page is displayed in your default browser saying *Your bot is ready!*.</span></span> <span data-ttu-id="30dc7-354">A URL será semelhante a esta: `https://botteamsauth.azurewebsites.net/` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-354">The URL will be similar to this: `https://botteamsauth.azurewebsites.net/`.</span></span> <span data-ttu-id="30dc7-355">Salve-o em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-355">Save it to a file.</span></span>
1. <span data-ttu-id="30dc7-356">No navegador, navegue até o [**portal do Azure**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="30dc7-356">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="30dc7-357">Verifique o grupo de recursos, o bot deve ser listado junto com os outros recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-357">Check your resource group, the bot should be listed along with the other resources.</span></span> <span data-ttu-id="30dc7-358">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-358">The following image is an example:</span></span>

    ![Teams-bot-auth-app-Service-Group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. <span data-ttu-id="30dc7-360">No grupo de recursos, selecione o nome de registro do canal de bot (link).</span><span class="sxs-lookup"><span data-stu-id="30dc7-360">In the resource group, select the bot channel registration name (link).</span></span>
1. <span data-ttu-id="30dc7-361">No painel esquerdo, selecione **configurações**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-361">In the left panel, select **Settings**.</span></span>
1. <span data-ttu-id="30dc7-362">Na caixa **ponto de extremidade de mensagens** , digite a URL obtida acima seguida por `api/messages` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-362">In the **Messaging endpoint** box, enter the URL obtained above followed by `api/messages`.</span></span> <span data-ttu-id="30dc7-363">Este é um exemplo: `https://botteamsauth.azurewebsites.net/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-363">This is an example: `https://botteamsauth.azurewebsites.net/api/messages`.</span></span>
1. <span data-ttu-id="30dc7-364">Selecione o botão **salvar** no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-364">Select the **Save** button in the upper left.</span></span>

## <a name="test-the-bot-using-the-emulator"></a><span data-ttu-id="30dc7-365">Testar o bot usando o emulador</span><span class="sxs-lookup"><span data-stu-id="30dc7-365">Test the bot using the Emulator</span></span>

<span data-ttu-id="30dc7-366">Se você ainda não tiver feito isso, instale o [emulador do Microsoft bot Framework](https://aka.ms/bot-framework-emulator-readme).</span><span class="sxs-lookup"><span data-stu-id="30dc7-366">If you haven't done it already, install the [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span></span> <span data-ttu-id="30dc7-367">Consulte também [depurar com o emulador](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span><span class="sxs-lookup"><span data-stu-id="30dc7-367">See also [Debug with the Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span></span>

<span data-ttu-id="30dc7-368">Para que o logon de exemplo de bot funcione, você deve configurar o emulador conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-368">In order for the bot sample login to work you must configure the Emulator as shown below.</span></span>

### <a name="configure-the-emulator-for-authentication"></a><span data-ttu-id="30dc7-369">Configurar o emulador para autenticação</span><span class="sxs-lookup"><span data-stu-id="30dc7-369">Configure the Emulator for authentication</span></span>

<span data-ttu-id="30dc7-370">Se um bot exigir autenticação, você deve configurar o emulador conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-370">If a bot requires authentication, you must configure the Emulator as shown below.</span></span>

1. <span data-ttu-id="30dc7-371">Inicie o emulador.</span><span class="sxs-lookup"><span data-stu-id="30dc7-371">Start the Emulator.</span></span>
1. <span data-ttu-id="30dc7-372">No emulador, selecione o ícone de engrenagem &#9881; na parte inferior esquerda ou a guia **configurações de emulador** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="30dc7-372">In the Emulator, select the gear icon &#9881; in the bottom left, or the **Emulator Settings** tab in the upper right.</span></span>
1. <span data-ttu-id="30dc7-373">Marque a caixa de seleção **usar tokens de autenticação da versão 1,0**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-373">Check the box by **Use version 1.0 authentication tokens**.</span></span>
1. <span data-ttu-id="30dc7-374">Insira o caminho local para a ferramenta **ngrok** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-374">Enter the local path to the **ngrok** tool.</span></span> <span data-ttu-id="30dc7-375">*Consulte* o ngrok [de integração de](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok))tunelamento/emulador da estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-375">*See* the Bot Framework Emulator / ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span></span> <span data-ttu-id="30dc7-376">Para obter mais informações sobre a ferramenta, consulte [ngrok](https://ngrok.com/).</span><span class="sxs-lookup"><span data-stu-id="30dc7-376">For more tool information, see [ngrok](https://ngrok.com/).</span></span>
1. <span data-ttu-id="30dc7-377">Marque a caixa de seleção **executar ngrok quando o emulador for iniciado**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-377">Check the box by **Run ngrok when the Emulator starts up**.</span></span>
1. <span data-ttu-id="30dc7-378">Selecione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-378">Select the **Save** button.</span></span>

<span data-ttu-id="30dc7-379">Quando o bot exibe um cartão de entrada e o usuário seleciona o botão de entrada, o emulador abre uma página que o usuário pode usar para entrar com o provedor de autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-379">When the bot displays a sign-in card and the user selects the sign-in button, the Emulator opens a page that the user can use to sign in with the authentication provider.</span></span>
<span data-ttu-id="30dc7-380">Depois que o usuário faz isso, o provedor gera um token de usuário e o envia ao bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-380">Once the user does so, the provider generates a user token and sends it to the bot.</span></span> <span data-ttu-id="30dc7-381">Depois, o bot pode agir em nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-381">After that, the bot can act on behalf of the user.</span></span>

### <a name="test-the-bot-locally"></a><span data-ttu-id="30dc7-382">Testar o bot localmente</span><span class="sxs-lookup"><span data-stu-id="30dc7-382">Test the bot locally</span></span>

<span data-ttu-id="30dc7-383">Depois de configurar o mecanismo de autenticação, você pode executar o teste de bot real.</span><span class="sxs-lookup"><span data-stu-id="30dc7-383">After you have configured the authentication mechanism, you can perform the actual bot testing.</span></span>  

1. <span data-ttu-id="30dc7-384">Execute o exemplo de bot localmente no seu computador, via Visual Studio por exemplo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-384">Run the bot sample locally on your machine, via Visual Studio for example.</span></span>
1. <span data-ttu-id="30dc7-385">Inicie o emulador.</span><span class="sxs-lookup"><span data-stu-id="30dc7-385">Start the Emulator.</span></span>
1. <span data-ttu-id="30dc7-386">Selecione o botão **abrir bot** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-386">Select the **Open bot** button.</span></span>
1. <span data-ttu-id="30dc7-387">Na **URL do bot**, digite a URL local do bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-387">In the **Bot URL**, enter the bot's local URL.</span></span> <span data-ttu-id="30dc7-388">Normalmente, `http://localhost:3978/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-388">Usually, `http://localhost:3978/api/messages`.</span></span>
1. <span data-ttu-id="30dc7-389">Na **ID do aplicativo da Microsoft** , digite a ID do aplicativo do bot no `appsettings.json` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-389">In the **Microsoft App ID** enter the bot's app ID from `appsettings.json`.</span></span>
1. <span data-ttu-id="30dc7-390">Na **senha do aplicativo da Microsoft** , digite a senha do aplicativo do bot no `appsettings.json` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-390">In the **Microsoft App password** enter the bot's app password from the `appsettings.json`.</span></span>
1. <span data-ttu-id="30dc7-391">Selecione **conectar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-391">Select **Connect**.</span></span>
1. <span data-ttu-id="30dc7-392">Depois que o bot estiver em funcionamento, insira qualquer texto para exibir o cartão de entrada.</span><span class="sxs-lookup"><span data-stu-id="30dc7-392">After the bot is up and running, enter any text to display the sign-in card.</span></span>
1. <span data-ttu-id="30dc7-393">Selecione o botão **entrar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-393">Select the **Sign in** button.</span></span>
1. <span data-ttu-id="30dc7-394">É exibida uma caixa de diálogo pop-up para **confirmar a abertura da URL**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-394">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="30dc7-395">Isso é para permitir que o usuário do bot (você) seja autenticado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-395">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="30dc7-396">Selecione **Confirmar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-396">Select **Confirm**.</span></span>
1. <span data-ttu-id="30dc7-397">Se for solicitado, selecione a conta do usuário aplicável.</span><span class="sxs-lookup"><span data-stu-id="30dc7-397">If asked, select the applicable user's account.</span></span>
1. <span data-ttu-id="30dc7-398">Dependendo da configuração usada para o emulador, você receberá uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="30dc7-398">Depending which configuration you used for the Emulator, you get one of the following:</span></span>
    1. <span data-ttu-id="30dc7-399">**Usando o código de verificação de entrada**</span><span class="sxs-lookup"><span data-stu-id="30dc7-399">**Using sign-in verification code**</span></span>  
      <span data-ttu-id="30dc7-400">&#x2713; uma janela é aberta exibindo o código de validação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-400">&#x2713; A window is opened displaying the validation code.</span></span>  
      <span data-ttu-id="30dc7-401">&#x2713; Copie e insira o código de validação na caixa chat para concluir a entrada.</span><span class="sxs-lookup"><span data-stu-id="30dc7-401">&#x2713; Copy and enter the validation code into the chat box to complete the sign-in.</span></span>
    1. <span data-ttu-id="30dc7-402">**Usando tokens de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-402">**Using authentication tokens**.</span></span>  
      <span data-ttu-id="30dc7-403">&#x2713; você está conectado com base em suas credenciais.</span><span class="sxs-lookup"><span data-stu-id="30dc7-403">&#x2713; You're logged in based on your credentials.</span></span>

    <span data-ttu-id="30dc7-404">A imagem a seguir é um exemplo da interface do usuário do bot após o logon:</span><span class="sxs-lookup"><span data-stu-id="30dc7-404">The following image is an example of the bot UI after you've logged in:</span></span>

    ![emulador de logon do bot de autenticação](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. <span data-ttu-id="30dc7-406">Se você selecionar **Sim** quando o bot solicitar *que você deseja exibir seu token?*, você receberá uma resposta semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="30dc7-406">If you select **Yes** when the bot asks *Would you like to view your token?*, you'll get a response similar to the following:</span></span>

    ![token de emulador de logon do bot de autenticação](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. <span data-ttu-id="30dc7-408">Digite **logout** na caixa chat de entrada para sair. Isso libera o token de usuário e o bot não poderá atuar em seu nome até que você entre novamente.</span><span class="sxs-lookup"><span data-stu-id="30dc7-408">Enter **logout** in the input chat box to sign out. This releases the user token, and the bot won't be able to act on your behalf until you sign in again.</span></span>

> [!NOTE]
> <span data-ttu-id="30dc7-409">A autenticação de bot requer o uso do **serviço do conector do bot**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-409">Bot authentication requires use of the **Bot Connector Service**.</span></span> <span data-ttu-id="30dc7-410">O serviço acessa as informações de registro dos canais de bot para o bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-410">The service accesses the bot channels registration information for your bot.</span></span>

## <a name="test-the-deployed-bot"></a><span data-ttu-id="30dc7-411">Testar o bot implantado</span><span class="sxs-lookup"><span data-stu-id="30dc7-411">Test the deployed bot</span></span>

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. <span data-ttu-id="30dc7-412">No navegador, navegue até o [**portal do Azure**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="30dc7-412">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="30dc7-413">Encontre o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-413">Find your resource group.</span></span>
1. <span data-ttu-id="30dc7-414">Selecione o link de recurso.</span><span class="sxs-lookup"><span data-stu-id="30dc7-414">Select the resource link.</span></span> <span data-ttu-id="30dc7-415">A página de recursos é exibida.</span><span class="sxs-lookup"><span data-stu-id="30dc7-415">The resource page is displayed.</span></span>
1. <span data-ttu-id="30dc7-416">Na página recurso, selecione **testar no chat da Web**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-416">In the resource page, select **Test in Web Chat**.</span></span> <span data-ttu-id="30dc7-417">O bot é iniciado e exibe as saudações predefinidas.</span><span class="sxs-lookup"><span data-stu-id="30dc7-417">The bot starts and displays the predefined greetings.</span></span>
1. <span data-ttu-id="30dc7-418">Digite qualquer coisa na caixa chat.</span><span class="sxs-lookup"><span data-stu-id="30dc7-418">Type anything in the chat box.</span></span>
1. <span data-ttu-id="30dc7-419">Selecione a caixa **entrar** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-419">Select the **Sign in** box.</span></span>
1. <span data-ttu-id="30dc7-420">É exibida uma caixa de diálogo pop-up para **confirmar a abertura da URL**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-420">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="30dc7-421">Isso é para permitir que o usuário do bot (você) seja autenticado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-421">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="30dc7-422">Selecione **Confirmar**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-422">Select **Confirm**.</span></span>
1. <span data-ttu-id="30dc7-423">Se for solicitado, selecione a conta do usuário aplicável.</span><span class="sxs-lookup"><span data-stu-id="30dc7-423">If asked, select the applicable user's account.</span></span>
    <span data-ttu-id="30dc7-424">A imagem a seguir é um exemplo da interface do usuário do bot após o logon:</span><span class="sxs-lookup"><span data-stu-id="30dc7-424">The following image is an example of the bot UI after you have logged in:</span></span>

    ![logon de bot de autenticação implantado](../../../assets/images/authentication/auth-bot-login-deployed.PNG)<span data-ttu-id="30dc7-426">.</span><span class="sxs-lookup"><span data-stu-id="30dc7-426">.</span></span>

1. <span data-ttu-id="30dc7-427">Selecione o botão **Sim** para exibir o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-427">Select the **Yes** button to display your authentication token.</span></span> <span data-ttu-id="30dc7-428">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-428">The following image is an example:</span></span>

    ![token de logon de bot de auth implantado](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG)<span data-ttu-id="30dc7-430">.</span><span class="sxs-lookup"><span data-stu-id="30dc7-430">.</span></span>

1. <span data-ttu-id="30dc7-431">Digite logout para sair.</span><span class="sxs-lookup"><span data-stu-id="30dc7-431">Enter logout to sign out.</span></span>

    ![logoff de autenticação do bot implantado](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> <span data-ttu-id="30dc7-433">Se você estiver tendo problemas para entrar, tente testar a conexão novamente, conforme descrito nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="30dc7-433">If you're having problems signing in, try to test the connection again as described in the previous steps.</span></span> <span data-ttu-id="30dc7-434">Isso pode recriar o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="30dc7-434">This could recreate the authentication token.</span></span>
> <span data-ttu-id="30dc7-435">Com o cliente de chat da Web do bot Framework no Azure, talvez seja necessário entrar várias vezes antes de a autenticação ser estabelecida corretamente.</span><span class="sxs-lookup"><span data-stu-id="30dc7-435">With the Bot Framework Web Chat client in Azure, you may need to sign in several times before the authentication is established correctly.</span></span>

## <a name="install-and-test-the-bot-in-teams"></a><span data-ttu-id="30dc7-436">Instalar e testar o bot no Teams</span><span class="sxs-lookup"><span data-stu-id="30dc7-436">Install and test the bot in Teams</span></span>

1. <span data-ttu-id="30dc7-437">No seu projeto bot, verifique se a `TeamsAppManifest` pasta contém o `manifest.json` junto com um `outline.png` e `color.png` arquivos.</span><span class="sxs-lookup"><span data-stu-id="30dc7-437">In your bot project, ensure that the `TeamsAppManifest` folder contains the `manifest.json` along with an `outline.png` and `color.png` files.</span></span>
1. <span data-ttu-id="30dc7-438">No Gerenciador de soluções, navegue até a `TeamsAppManifest` pasta.</span><span class="sxs-lookup"><span data-stu-id="30dc7-438">In Solution Explorer, navigate to the `TeamsAppManifest` folder.</span></span> <span data-ttu-id="30dc7-439">Edit `manifest.json` atribuindo os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="30dc7-439">Edit `manifest.json` by assigning the following values:</span></span>
    1. <span data-ttu-id="30dc7-440">Certifique-se de que a **ID do aplicativo bot** recebida no momento do registro do canal de bot está atribuída a `id` e `botId` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-440">Ensure that the **bot App ID** you received at the time of the bot channel registration is assigned to `id` and `botId`.</span></span>
    1. <span data-ttu-id="30dc7-441">Atribua este valor: `validDomains: [ "token.botframework.com" ]` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-441">Assign this value: `validDomains: [ "token.botframework.com" ]`.</span></span>
1. <span data-ttu-id="30dc7-442">Selecionar e **compactar** os `manifest.json` `outline.png` arquivos, e `color.png` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-442">Select and **zip** the `manifest.json`, `outline.png`, and `color.png` files.</span></span>
1. <span data-ttu-id="30dc7-443">Abra **o Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-443">Open **Microsoft Teams**.</span></span>
1. <span data-ttu-id="30dc7-444">No painel esquerdo, na parte inferior, selecione o **ícone aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-444">In the left panel, at the bottom, select the **Apps icon**.</span></span>
1. <span data-ttu-id="30dc7-445">No painel direito, na parte inferior, selecione **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-445">In the right panel, at the bottom, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="30dc7-446">Navegue até a `TeamsAppManifest` pasta e carregue o manifesto zipado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-446">Navigate to the `TeamsAppManifest` folder and upload the zipped manifest.</span></span>
<span data-ttu-id="30dc7-447">O seguinte assistente é exibido:</span><span class="sxs-lookup"><span data-stu-id="30dc7-447">The following wizard is displayed:</span></span>

    ![carregamento de equipes de bot de autenticação](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. <span data-ttu-id="30dc7-449">Selecione o botão **Adicionar a uma equipe** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-449">Select the **Add to a team** button.</span></span>
1. <span data-ttu-id="30dc7-450">Na janela seguinte, selecione a equipe onde você deseja usar o bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-450">In the next window, select the team where you want to use the bot.</span></span>
1. <span data-ttu-id="30dc7-451">Selecione o botão **configurar um bot** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-451">Select the **Set up a bot** button.</span></span>
1. <span data-ttu-id="30dc7-452">Selecione os três pontos (&#x25cf;&#x25cf;&#x25cf;) no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-452">Select the three dots (&#x25cf;&#x25cf;&#x25cf;) in the left panel.</span></span> <span data-ttu-id="30dc7-453">Em seguida, selecione o ícone do **app Studio** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-453">Then select the **App Studio** icon.</span></span>
1. <span data-ttu-id="30dc7-454">Selecione a guia **Editor de manifesto** . Você deve ver o ícone do bot que você carregou.</span><span class="sxs-lookup"><span data-stu-id="30dc7-454">Select the **Manifest editor** tab. You should see the icon for the bot you uploaded.</span></span>
1. <span data-ttu-id="30dc7-455">Além disso, você deve ser capaz de ver o bot listado como um contato na lista de chat que você pode usar para trocar mensagens com o bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-455">Also, you should be able to see the bot listed as a contact in the chat list that you can use to exchange messages with the bot.</span></span>

### <a name="testing-the-bot-locally-in-teams"></a><span data-ttu-id="30dc7-456">Testando o bot localmente no Teams</span><span class="sxs-lookup"><span data-stu-id="30dc7-456">Testing the bot locally in Teams</span></span>

<span data-ttu-id="30dc7-457">O Microsoft Teams é um produto totalmente baseado em nuvem, que exige que todos os serviços que ele acessa estejam disponíveis na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="30dc7-457">Microsoft Teams is an entirely cloud-based product, it requires all services it accesses to be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="30dc7-458">Portanto, para permitir que o bot (nosso exemplo) funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar uma instância em execução local externamente acessível por meio de uma ferramenta de **encapsulamento** .</span><span class="sxs-lookup"><span data-stu-id="30dc7-458">Therefore, to enable the bot (our sample) to work in Teams, you need to either publish the code to the cloud of your choice, or make a locally running instance externally accessible via a **tunneling** tool.</span></span> <span data-ttu-id="30dc7-459">Recomendamos o  [ngrok](https://ngrok.com/download), que cria uma URL endereçável externamente para uma porta que você abre localmente no seu computador.</span><span class="sxs-lookup"><span data-stu-id="30dc7-459">We recommend  [ngrok](https://ngrok.com/download), which creates an externally addressable URL for a port you open locally on your machine.</span></span>
<span data-ttu-id="30dc7-460">Para configurar o ngrok em preparação para executar seu aplicativo do Microsoft Teams localmente, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="30dc7-460">To set up ngrok in preparation for running your Microsoft Teams app locally, follow these steps:</span></span>

1. <span data-ttu-id="30dc7-461">Em uma janela de terminal, vá para o diretório onde você `ngrok.exe` instalou.</span><span class="sxs-lookup"><span data-stu-id="30dc7-461">In a terminal window, go the directory where you have `ngrok.exe` installed.</span></span> <span data-ttu-id="30dc7-462">Sugerimos definir o caminho da *variável de ambiente* para apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="30dc7-462">We suggest setting the *environment variable* path to point to it.</span></span>
1. <span data-ttu-id="30dc7-463">Executar, por exemplo, `ngrok http 3978 --host-header=localhost:3978` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-463">Run, for example, `ngrok http 3978 --host-header=localhost:3978`.</span></span> <span data-ttu-id="30dc7-464">Substitua o número da porta, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-464">Replace the port number as needed.</span></span>
<span data-ttu-id="30dc7-465">Isso inicia o ngrok para escutar na porta que você especificar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-465">This launches ngrok to listen on the port you specify.</span></span> <span data-ttu-id="30dc7-466">Em retorno, ele fornece uma URL endereçável externamente, válida por enquanto o ngrok está em execução.</span><span class="sxs-lookup"><span data-stu-id="30dc7-466">In return, it gives you an externally addressable URL, valid for as long as ngrok is running.</span></span> <span data-ttu-id="30dc7-467">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-467">The following image is an example:</span></span>

    ![Cadeia de caracteres de conexão de autenticação do aplicativo bot do teams Adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG)<span data-ttu-id="30dc7-469">.</span><span class="sxs-lookup"><span data-stu-id="30dc7-469">.</span></span>

1. <span data-ttu-id="30dc7-470">Copie o endereço HTTPS de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="30dc7-470">Copy the forwarding HTTPS address.</span></span> <span data-ttu-id="30dc7-471">Ele deve ser semelhante ao seguinte: `https://dea822bf.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-471">It should be similar to the following: `https://dea822bf.ngrok.io/`.</span></span>
1. <span data-ttu-id="30dc7-472">Anexar `/api/messages` para obter `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-472">Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages`.</span></span> <span data-ttu-id="30dc7-473">Este é o **ponto de extremidade das mensagens** para o bot executado localmente em sua máquina e alcançável pela Web em um chat no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="30dc7-473">This is the **messages endpoint** for the bot running locally on your machine and reachable over the web in a chat in Microsoft Teams.</span></span>
1. <span data-ttu-id="30dc7-474">Uma etapa final a ser executada é atualizar o ponto de extremidade das mensagens do bot implantado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-474">One final step to perform is to update the messages endpoint of the deployed bot.</span></span> <span data-ttu-id="30dc7-475">No exemplo, implantamos o bot no Azure.</span><span class="sxs-lookup"><span data-stu-id="30dc7-475">In the example, we deployed the bot in Azure.</span></span> <span data-ttu-id="30dc7-476">Portanto, \* \* vamos executar estas etapas:</span><span class="sxs-lookup"><span data-stu-id="30dc7-476">So \*\*let's perform these steps:</span></span>
    1. <span data-ttu-id="30dc7-477">No navegador, navegue até o [**portal do Azure**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="30dc7-477">In your browser navigate to the [**Azure portal**][azure-portal].</span></span>
    1. <span data-ttu-id="30dc7-478">Selecione o **registro do canal do bot**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-478">Select your **Bot Channel Registration**.</span></span>
    1. <span data-ttu-id="30dc7-479">No painel esquerdo, selecione **configurações**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-479">In the left panel, select **Settings**.</span></span>
    1. <span data-ttu-id="30dc7-480">No painel direito, na caixa **ponto de extremidade de mensagens** , digite a URL ngrok, no nosso exemplo, `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="30dc7-480">In the right panel, in the **Messaging endpoint** box, enter the ngrok URL, in our example, `https://dea822bf.ngrok.io/api/messages`.</span></span>
1. <span data-ttu-id="30dc7-481">Inicie seu bot localmente, por exemplo no modo de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30dc7-481">Start your bot locally, for example in Visual Studio debug mode.</span></span>
1. <span data-ttu-id="30dc7-482">Teste o bot durante a execução local usando o **chat da Web de teste**do portal da estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-482">Test the bot while running locally using the Bot Framework portal's **Test Web chat**.</span></span> <span data-ttu-id="30dc7-483">Assim como o emulador, esse teste não permite acessar a funcionalidade específica da equipe.</span><span class="sxs-lookup"><span data-stu-id="30dc7-483">Like the Emulator, this test doesn't allow you to access Teams-specific functionality.</span></span>
1. <span data-ttu-id="30dc7-484">Na janela do terminal onde `ngrok` o está sendo executado, você pode ver o tráfego http entre o bot e o cliente de chat da Web.</span><span class="sxs-lookup"><span data-stu-id="30dc7-484">In the terminal window where `ngrok` is running you can see HTTP traffic between the bot and the web chat client.</span></span> <span data-ttu-id="30dc7-485">Se você quiser um modo de exibição mais detalhado, em uma janela do navegador, insira- `http://127.0.0.1:4040` o na janela anterior do terminal.</span><span class="sxs-lookup"><span data-stu-id="30dc7-485">If you want a more detailed view, in a browser window enter `http://127.0.0.1:4040` you obtained from the previous terminal window.</span></span> <span data-ttu-id="30dc7-486">A imagem a seguir é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="30dc7-486">The following image is an example:</span></span>

    ![testes de ngrok de equipes de bot de autenticação](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png)<span data-ttu-id="30dc7-488">.</span><span class="sxs-lookup"><span data-stu-id="30dc7-488">.</span></span>

> [!NOTE]
> <span data-ttu-id="30dc7-489">Se você parar e reiniciar o ngrok, a URL será alterada.</span><span class="sxs-lookup"><span data-stu-id="30dc7-489">If you stop and restart ngrok, the URL changes.</span></span> <span data-ttu-id="30dc7-490">Para usar o ngrok em seu projeto e dependendo dos recursos que você está usando, você deve atualizar todas as referências de URL.</span><span class="sxs-lookup"><span data-stu-id="30dc7-490">To use ngrok in your project, and depending on the capabilities you're using, you must update all URL references.</span></span>
 

## <a name="additional-information"></a><span data-ttu-id="30dc7-491">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="30dc7-491">Additional information</span></span>

### <a name="teamsappmanifestmanifestjson"></a><span data-ttu-id="30dc7-492">TeamsAppManifest/manifest.jsem</span><span class="sxs-lookup"><span data-stu-id="30dc7-492">TeamsAppManifest/manifest.json</span></span>

<span data-ttu-id="30dc7-493">Este manifesto contém as informações necessárias para que o Microsoft Teams se conecte ao bot.</span><span class="sxs-lookup"><span data-stu-id="30dc7-493">This manifest contains information needed by Microsoft Teams to connect with the bot.</span></span>  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0.0",
  "id": "",
  "packageName": "com.teams.auth.bot",
  "developer": {
    "name": "TeamsBotAuth",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.teams.com/privacy",
    "termsOfUseUrl": "https://www.teams.com/termsofuse"
  },
  "icons": {
    "color": "color.png",
    "outline": "outline.png"
  },
  "name": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "description": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "accentColor": "#FFFFFF",
  "bots": [
    {
      "botId": "",
      "scopes": [
        "groupchat",
        "team"
      ],
      "supportsFiles": false,
      "isNotificationOnly": false
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [ "token.botframework.com" ]
}
```

<span data-ttu-id="30dc7-494">Com a autenticação, o Microsoft Teams se comporta de forma ligeiramente diferente de outros canais, conforme explicado abaixo.</span><span class="sxs-lookup"><span data-stu-id="30dc7-494">With authentication, Teams behaves slightly differently than other channels, as explained below.</span></span>

### <a name="handling-invoke-activity"></a><span data-ttu-id="30dc7-495">Tratamento da atividade de invocação</span><span class="sxs-lookup"><span data-stu-id="30dc7-495">Handling Invoke Activity</span></span>

<span data-ttu-id="30dc7-496">Uma **atividade de invocação** é enviada ao bot em vez da atividade de evento usada por outros canais.</span><span class="sxs-lookup"><span data-stu-id="30dc7-496">An **Invoke Activity** is sent to the bot rather than the Event Activity used by other channels.</span></span>
<span data-ttu-id="30dc7-497">Isso é feito com a subclasse de **ActivityHandler**.</span><span class="sxs-lookup"><span data-stu-id="30dc7-497">This is done by sub-classing the **ActivityHandler**.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="30dc7-498">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="30dc7-498">C#/.NET</span></span>](#tab/dotnet-sample)

<span data-ttu-id="30dc7-499">**Bots/DialogBot. cs**</span><span class="sxs-lookup"><span data-stu-id="30dc7-499">**Bots/DialogBot.cs**</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

<span data-ttu-id="30dc7-500">**Bots/TeamsBot. cs**</span><span class="sxs-lookup"><span data-stu-id="30dc7-500">**Bots/TeamsBot.cs**</span></span>

<span data-ttu-id="30dc7-501">A *atividade chamar* deve ser encaminhada para a caixa de diálogo se o **OAuthPrompt** for usado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-501">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a><span data-ttu-id="30dc7-502">TeamsActivityHandler.cs</span><span class="sxs-lookup"><span data-stu-id="30dc7-502">TeamsActivityHandler.cs</span></span>

```csharp

protected virtual Task OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    switch (turnContext.Activity.Name)
    {
        case "signin/verifyState":
            return OnSigninVerifyStateAsync(turnContext, cancellationToken);

        default:
            return Task.CompletedTask;
    }
}

protected virtual Task OnSigninVerifyStateAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    return Task.CompletedTask;
}
```

# <a name="javascript"></a>[<span data-ttu-id="30dc7-503">JavaScript</span><span class="sxs-lookup"><span data-stu-id="30dc7-503">JavaScript</span></span>](#tab/node-js-dialog-sample)

<span data-ttu-id="30dc7-504">**bots/dialogBot.js**</span><span class="sxs-lookup"><span data-stu-id="30dc7-504">**bots/dialogBot.js**</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

<span data-ttu-id="30dc7-505">**bots/teamsBot.js**</span><span class="sxs-lookup"><span data-stu-id="30dc7-505">**bots/teamsBot.js**</span></span>

<span data-ttu-id="30dc7-506">A *atividade chamar* deve ser encaminhada para a caixa de diálogo se o **OAuthPrompt** for usado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-506">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

<span data-ttu-id="30dc7-507">**caixas de diálogo/mainDialog.js**</span><span class="sxs-lookup"><span data-stu-id="30dc7-507">**dialogs/mainDialog.js**</span></span>

<span data-ttu-id="30dc7-508">Em uma etapa da caixa de diálogo, use `beginDialog` para iniciar o prompt do OAuth, que solicita ao usuário para entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-508">Within a dialog step, use `beginDialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="30dc7-509">Se o usuário já estiver conectado, isso gerará um evento de resposta de token, sem avisar o usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-509">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="30dc7-510">Caso contrário, o usuário será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-510">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="30dc7-511">O serviço do Azure bot envia o evento de resposta do token após o usuário tentar entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-511">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

<span data-ttu-id="30dc7-512">Na etapa da caixa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="30dc7-512">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="30dc7-513">Se ele não for nulo, o usuário entrou com êxito.</span><span class="sxs-lookup"><span data-stu-id="30dc7-513">If it is not null, the user successfully signed in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

<span data-ttu-id="30dc7-514">**bots/logoutDialog.js**</span><span class="sxs-lookup"><span data-stu-id="30dc7-514">**bots/logoutDialog.js**</span></span>

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[<span data-ttu-id="30dc7-515">Python</span><span class="sxs-lookup"><span data-stu-id="30dc7-515">Python</span></span>](#tab/python-sample)

<span data-ttu-id="30dc7-516">**bots/dialog_bot. py**</span><span class="sxs-lookup"><span data-stu-id="30dc7-516">**bots/dialog_bot.py**</span></span>

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

<span data-ttu-id="30dc7-517">**bots/teams_bot. py**</span><span class="sxs-lookup"><span data-stu-id="30dc7-517">**bots/teams_bot.py**</span></span>

<span data-ttu-id="30dc7-518">A *atividade chamar* deve ser encaminhada para a caixa de diálogo se o **OAuthPrompt** for usado.</span><span class="sxs-lookup"><span data-stu-id="30dc7-518">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

<span data-ttu-id="30dc7-519">**caixas de diálogo/main_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="30dc7-519">**dialogs/main_dialog.py**</span></span>

<span data-ttu-id="30dc7-520">Em uma etapa da caixa de diálogo, use `begin_dialog` para iniciar o prompt do OAuth, que solicita ao usuário para entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-520">Within a dialog step, use `begin_dialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="30dc7-521">Se o usuário já estiver conectado, isso gerará um evento de resposta de token, sem avisar o usuário.</span><span class="sxs-lookup"><span data-stu-id="30dc7-521">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="30dc7-522">Caso contrário, o usuário será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-522">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="30dc7-523">O serviço do Azure bot envia o evento de resposta do token após o usuário tentar entrar.</span><span class="sxs-lookup"><span data-stu-id="30dc7-523">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

<span data-ttu-id="30dc7-524">Na etapa da caixa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="30dc7-524">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="30dc7-525">Se ele não for nulo, o usuário entrou com êxito.</span><span class="sxs-lookup"><span data-stu-id="30dc7-525">If it is not null, the user successfully signed in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

<span data-ttu-id="30dc7-526">**caixas de diálogo/logout_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="30dc7-526">**dialogs/logout_dialog.py**</span></span>

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [<span data-ttu-id="30dc7-527">Saiba mais sobre como adicionar a adição de autenticação por meio do serviço do Azure bot</span><span class="sxs-lookup"><span data-stu-id="30dc7-527">Learn about adding adding authentication via Azure Bot Service</span></span>](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
