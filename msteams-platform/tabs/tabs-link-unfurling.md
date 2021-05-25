---
title: Guias vinculam desfraldamento e exibição de estágio
author: Rajeshwari-v
description: Como desatar um link, abrir o Stage View e fixar uma guia com Microsoft Teams app.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 7dfabfa58c49237e776af37a1ee40d707783d0dc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631216"
---
# <a name="tabs-link-unfurling-and-stage-view"></a><span data-ttu-id="cfeb4-103">Guias vinculam desfraldamento e exibição de estágio</span><span class="sxs-lookup"><span data-stu-id="cfeb4-103">Tabs link unfurling and Stage View</span></span>

> [!NOTE]
> <span data-ttu-id="cfeb4-104">Esse recurso está disponível somente na [visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-104">This feature is available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="cfeb4-105">O Stage View é um novo componente da interface do usuário, que permite renderizar o conteúdo que é aberto em tela inteira em Teams e fixado como uma guia.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-105">Stage View is a new UI component, which allows you to render the content that is opened in full screen in Teams and pinned as a tab.</span></span>
 
> [!NOTE]
> <span data-ttu-id="cfeb4-106">Atualmente, Teams clientes móveis não fazem nenhum link de guias de suporte para desfraldamento e Exibição de Estágio.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-106">Currently, Teams mobile clients do no support tabs link unfurling and Stage View.</span></span> <span data-ttu-id="cfeb4-107">Os clientes móveis usam `websiteUrl` o atributo fornecido pelo desenvolvedor para abrir a página no navegador da Web do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-107">Mobile clients use the `websiteUrl` attribute provided by the developer to open the page in the device's web browser.</span></span>

## <a name="stage-view"></a><span data-ttu-id="cfeb4-108">Exibição de estágio</span><span class="sxs-lookup"><span data-stu-id="cfeb4-108">Stage View</span></span>

<span data-ttu-id="cfeb4-109">O Stage View é um componente de interface do usuário de tela inteira que você pode invocar para exibir o conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-109">Stage View is a full screen UI component that you can invoke to surface your web content.</span></span> <span data-ttu-id="cfeb4-110">O serviço de desatração de link existente é atualizado para que ele seja usado para transformar URLs em uma guia usando um Cartão Adaptável e Serviços de Chat.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-110">The existing link unfurling service is updated so that it is used to turn URLs into a tab using an Adaptive Card and Chat Services.</span></span> <span data-ttu-id="cfeb4-111">Quando um usuário envia uma URL em um chat ou canal, a URL é desfraldada para um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-111">When a user sends a URL in a chat or channel, the URL is unfurled to an Adaptive Card.</span></span> <span data-ttu-id="cfeb4-112">O usuário pode selecionar **Exibir** no cartão e fixar o conteúdo como uma guia diretamente no Stage View.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-112">The user can select **View** in the card, and pin the content as a tab directly from the Stage View.</span></span>

## <a name="advantage-of-stage-view"></a><span data-ttu-id="cfeb4-113">Vantagem da exibição de estágio</span><span class="sxs-lookup"><span data-stu-id="cfeb4-113">Advantage of Stage View</span></span>

<span data-ttu-id="cfeb4-114">O Stage View ajuda a fornecer uma experiência mais perfeita de exibição de conteúdo em Teams.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-114">Stage View helps provide a more seamless experience of viewing content in Teams.</span></span> <span data-ttu-id="cfeb4-115">Os usuários podem abrir e exibir o conteúdo fornecido pelo aplicativo sem sair do contexto, e eles podem fixar o conteúdo no chat ou canal para acesso rápido futuro.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-115">Users can open and view the content provided by your app without leaving the context, and they can pin the content to the chat or channel for future quick access.</span></span> <span data-ttu-id="cfeb4-116">Isso leva a um envolvimento de usuário mais alto com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-116">This leads to a higher user engagement with your app.</span></span>

##  <a name="stage-view-vs-task-module"></a><span data-ttu-id="cfeb4-117">Exibição de estágio versus módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="cfeb4-117">Stage View vs. Task module</span></span>

|<span data-ttu-id="cfeb4-118">Exibição de estágio</span><span class="sxs-lookup"><span data-stu-id="cfeb4-118">Stage View</span></span>|<span data-ttu-id="cfeb4-119">Módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="cfeb4-119">Task module</span></span>|
|:-----------|:-----------|
|<span data-ttu-id="cfeb4-120">O Modo de Exibição de Estágio é útil quando você tem um conteúdo avançado para exibir aos usuários, como uma página, um painel, um arquivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-120">Stage View is useful when you have a rich content to display to the users, such as a page, a dashboard, a file, and so on.</span></span> <span data-ttu-id="cfeb4-121">Ele fornece o máximo de imóveis que ajuda a renderizar seu conteúdo na tela de tela inteira.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-121">It provides  maximum real estate that helps to render your content in the full-screen canvas.</span></span>|<span data-ttu-id="cfeb4-122">[O módulo de](../task-modules-and-cards/task-modules/task-modules-tabs.md) tarefas é especialmente útil para exibir mensagens que exigem a atenção do usuário ou coletar informações necessárias para mover para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-122">[Task module](../task-modules-and-cards/task-modules/task-modules-tabs.md) is especially useful to display messages that requires user's attention, or collect information required to move to the next step.</span></span>|
  
## <a name="invoke-the-stage-view"></a><span data-ttu-id="cfeb4-123">Invocar a exibição de estágio</span><span class="sxs-lookup"><span data-stu-id="cfeb4-123">Invoke the Stage View</span></span>

<span data-ttu-id="cfeb4-124">Você pode invocar o Modo de Exibição de Estágio das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-124">You can invoke the Stage View in the following  ways:</span></span> 

* [<span data-ttu-id="cfeb4-125">Invocar exibição de estágio do cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="cfeb4-125">Invoke Stage View from Adaptive Card</span></span>](#invoke-stage-view-from-adaptive-card)
* [<span data-ttu-id="cfeb4-126">Invocar Exibição de Estágio por meio de um link profundo</span><span class="sxs-lookup"><span data-stu-id="cfeb4-126">Invoke Stage View through deep link</span></span>](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a><span data-ttu-id="cfeb4-127">Invocar exibição de estágio do cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="cfeb4-127">Invoke Stage View from Adaptive Card</span></span>

<span data-ttu-id="cfeb4-128">Quando o usuário insula uma URL no cliente da área de [](../task-modules-and-cards/cards/cards-actions.md) trabalho Teams, o bot é invocado e retorna um Cartão Adaptável com a opção de abrir a URL em um estágio.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-128">When the user enters a URL on the Teams desktop client, the bot is invoked and returns an [Adaptive Card](../task-modules-and-cards/cards/cards-actions.md) with the option to open the URL in a stage.</span></span> <span data-ttu-id="cfeb4-129">Depois que um estágio é lançado e o é passado, você pode adicionar a capacidade de fixar o `tabInfo` estágio como uma guia.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-129">After a stage is launched and the `tabInfo` is passed in, you can add the ability to pin the stage as a tab.</span></span>  

<span data-ttu-id="cfeb4-130">As imagens a seguir exibem um estágio aberto de um Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-130">The following images display a stage opened from an Adaptive Card:</span></span>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="400"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="400"/>

### <a name="example"></a><span data-ttu-id="cfeb4-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfeb4-131">Example</span></span> 

<span data-ttu-id="cfeb4-132">A seguir está o código para abrir um estágio de um Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-132">Following is the code to open a stage from an Adaptive Card:</span></span>

```json
{
    type: "Action.Submit",
    name: "View",
    data: {
          msteams: {
            type: "invoke",
            value: {
                type: "tab/tabInfoAction",
                tabInfo: {
                    contentUrl: contentUrl,
                    websiteUrl: websiteUrl,
                    name: "Tasks",
                    entityId: "entityId"
                 }
                }
            }
        }
} 
```

<span data-ttu-id="cfeb4-133">O `invoke` tipo de solicitação deve ser `composeExtension/queryLink` .</span><span class="sxs-lookup"><span data-stu-id="cfeb4-133">The `invoke` request type must be `composeExtension/queryLink`.</span></span> 

> [!NOTE]
> * <span data-ttu-id="cfeb4-134">`invoke` o fluxo de trabalho é semelhante ao fluxo de `appLinking` trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-134">`invoke` workflow is similar to the current `appLinking` workflow.</span></span> 
> * <span data-ttu-id="cfeb4-135">Para manter a consistência, é recomendável nomear `Action.Submit` como `View` .</span><span class="sxs-lookup"><span data-stu-id="cfeb4-135">To maintain consistency, it is recommended to name the `Action.Submit` as `View`.</span></span>
> * <span data-ttu-id="cfeb4-136">`websiteUrl` é uma propriedade necessária a ser passada no `TabInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-136">`websiteUrl` is a required property to be passed in the `TabInfo` object.</span></span>

<span data-ttu-id="cfeb4-137">**Processo para invocar o Stage View**</span><span class="sxs-lookup"><span data-stu-id="cfeb4-137">**Process to invoke Stage View**</span></span>

1. <span data-ttu-id="cfeb4-138">Quando o usuário seleciona **Exibir**, o bot recebe uma `invoke` solicitação.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-138">When the user selects **View**, the bot receives an `invoke` request.</span></span> <span data-ttu-id="cfeb4-139">O tipo de solicitação é `composeExtension/queryLink` .</span><span class="sxs-lookup"><span data-stu-id="cfeb4-139">The request type is `composeExtension/queryLink`.</span></span>
1. <span data-ttu-id="cfeb4-140">`invoke` response from bot contains an Adaptive Card with type `tab/tabInfoAction` in it.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-140">`invoke` response from bot contains an Adaptive Card with type `tab/tabInfoAction` in it.</span></span>
1. <span data-ttu-id="cfeb4-141">O bot responde com um `200` código.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-141">The bot responds with a `200` code.</span></span>

> [!NOTE]
> <span data-ttu-id="cfeb4-142">Atualmente, Teams clientes móveis não suportam o recurso Modo de Exibição de Estágio.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-142">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="cfeb4-143">Quando um usuário seleciona **Exibir** em um cliente móvel, o usuário é levado para o navegador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-143">When a user selects **View** on a mobile client, the user is taken to the device's browser.</span></span> <span data-ttu-id="cfeb4-144">O navegador abre a URL especificada no `websiteUrl` parâmetro do `TabInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-144">The browser opens the URL specified in the `websiteUrl` parameter of the `TabInfo` object.</span></span>

## <a name="invoke-stage-view-through-deep-link"></a><span data-ttu-id="cfeb4-145">Invocar Exibição de Estágio por meio de um link profundo</span><span class="sxs-lookup"><span data-stu-id="cfeb4-145">Invoke Stage View through deep link</span></span>

<span data-ttu-id="cfeb4-146">Para invocar o Stage View por meio de um link profundo de sua guia, você deve quebrar a URL de link profundo na `microsoftTeams.executeDeeplink(url)` API.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-146">To invoke the Stage View through deep link from your tab, you must wrap the deep link URL in the `microsoftTeams.executeDeeplink(url)` API.</span></span> <span data-ttu-id="cfeb4-147">O deeplink também pode ser passado por uma `OpenURL` ação no cartão.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-147">The deeplink can also be passed through an `OpenURL` action in the card.</span></span>

<span data-ttu-id="cfeb4-148">A imagem a seguir exibe um Stage View invocado por meio de um link profundo:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-148">The following image displays a Stage View invoked through a deep link:</span></span>

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a><span data-ttu-id="cfeb4-149">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfeb4-149">Syntax</span></span> 

<span data-ttu-id="cfeb4-150">A seguir está a sintaxe do deeplink:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-150">Following is the deeplink syntax:</span></span>  
 
<span data-ttu-id="cfeb4-151"> https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"[contentUrl]","websiteUrl":"[websiteUrl]","name":"[name]"}</span><span class="sxs-lookup"><span data-stu-id="cfeb4-151">https://teams.microsoft.com/l/stage/{appId}/0?context={“contentUrl”:”[contentUrl]”,“websiteUrl”:”[websiteUrl]”,“name”:”[name]”}</span></span>

### <a name="examples"></a><span data-ttu-id="cfeb4-152">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cfeb4-152">Examples</span></span>

<span data-ttu-id="cfeb4-153">Quando um usuário insinua uma URL, ela é desfraldada em um cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-153">When a user enters a URL, it is unfurled into an Adaptive card.</span></span>
<span data-ttu-id="cfeb4-154">A seguir estão os exemplos de link profundo para invocar o Stage View:</span><span class="sxs-lookup"><span data-stu-id="cfeb4-154">Following are the deep link examples to invoke the Stage View:</span></span>

<span data-ttu-id="cfeb4-155">**Exemplo 1**</span><span class="sxs-lookup"><span data-stu-id="cfeb4-155">**Example 1**</span></span>

<span data-ttu-id="cfeb4-156"> https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl",:"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="cfeb4-156">https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

<span data-ttu-id="cfeb4-157">**Exemplo 2**</span><span class="sxs-lookup"><span data-stu-id="cfeb4-157">**Example 2**</span></span>

<span data-ttu-id="cfeb4-158"> https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl",:"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="cfeb4-158">https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

> [!NOTE]
> * <span data-ttu-id="cfeb4-159">O `name` é opcional em link profundo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-159">The `name` is optional in deep link.</span></span> <span data-ttu-id="cfeb4-160">Se não estiver incluído, o nome do aplicativo o substituirá.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-160">If not included, the app name replaces it.</span></span> 
> * <span data-ttu-id="cfeb4-161">O link profundo também pode ser passado por uma `OpenURL` ação.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-161">The deep link can also be passed through  an `OpenURL` action.</span></span>
> * <span data-ttu-id="cfeb4-162">Atualmente, Teams clientes móveis não suportam o recurso Modo de Exibição de Estágio.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-162">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="cfeb4-163">Quando os usuários selecionam um link profundo para um Stage View, eles são levados para o navegador da Web do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-163">When users selects a deep link to a Stage View, they are taken to their device's web browser.</span></span> <span data-ttu-id="cfeb4-164">O navegador da Web abre a URL especificada no `websiteUrl` parâmetro do link profundo.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-164">The web browser opens the URL specified in the `websiteUrl` parameter of the deep link.</span></span>
> * <span data-ttu-id="cfeb4-165">Ao iniciar um Estágio a partir de um determinado contexto, verifique se seu aplicativo funciona nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-165">When you launch a Stage from a certain context, ensure that your app works in that context.</span></span> <span data-ttu-id="cfeb4-166">Por exemplo, se o seu Stage View for lançado a partir de um aplicativo pessoal, você deve garantir que seu aplicativo tenha um escopo pessoal.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-166">For example, if your Stage View is launched from a personal app, you must ensure your app has a personal scope.</span></span>

## <a name="tab-information-property"></a><span data-ttu-id="cfeb4-167">Propriedade Tab information</span><span class="sxs-lookup"><span data-stu-id="cfeb4-167">Tab information property</span></span>

| <span data-ttu-id="cfeb4-168">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="cfeb4-168">Property name</span></span> | <span data-ttu-id="cfeb4-169">Tipo</span><span class="sxs-lookup"><span data-stu-id="cfeb4-169">Type</span></span> | <span data-ttu-id="cfeb4-170">Número de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-170">Number of characters</span></span> | <span data-ttu-id="cfeb4-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfeb4-171">Description</span></span> |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | <span data-ttu-id="cfeb4-172">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-172">String</span></span> | <span data-ttu-id="cfeb4-173">64</span><span class="sxs-lookup"><span data-stu-id="cfeb4-173">64</span></span> | <span data-ttu-id="cfeb4-174">Essa propriedade é um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-174">This property is a  unique identifier for the entity that the tab displays.</span></span> <span data-ttu-id="cfeb4-175">Esse é um campo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-175">This is a required field.</span></span>|
| `name` | <span data-ttu-id="cfeb4-176">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-176">String</span></span> | <span data-ttu-id="cfeb4-177">128</span><span class="sxs-lookup"><span data-stu-id="cfeb4-177">128</span></span> | <span data-ttu-id="cfeb4-178">Essa propriedade é o nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-178">This property is the display name of the tab in the channel interface.</span></span> <span data-ttu-id="cfeb4-179">Esse campo é opcional.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-179">This is an optional field.</span></span>|
| `contentUrl` | <span data-ttu-id="cfeb4-180">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-180">String</span></span> | <span data-ttu-id="cfeb4-181">2048</span><span class="sxs-lookup"><span data-stu-id="cfeb4-181">2048</span></span> | <span data-ttu-id="cfeb4-182">Essa propriedade é a URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-182">This property is the https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span> <span data-ttu-id="cfeb4-183">Esse é um campo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-183">This is a required field.</span></span>|
| `websiteUrl?` | <span data-ttu-id="cfeb4-184">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-184">String</span></span> | <span data-ttu-id="cfeb4-185">2048</span><span class="sxs-lookup"><span data-stu-id="cfeb4-185">2048</span></span> | <span data-ttu-id="cfeb4-186">Essa propriedade é a URL https:// para apontar, se um usuário selecionar para exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-186">This property is the https:// URL to point at, if a user selects to view in a browser.</span></span> <span data-ttu-id="cfeb4-187">Esse é um campo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-187">This is a required field.</span></span>|
| `removeUrl?` | <span data-ttu-id="cfeb4-188">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cfeb4-188">String</span></span> | <span data-ttu-id="cfeb4-189">2048</span><span class="sxs-lookup"><span data-stu-id="cfeb4-189">2048</span></span> | <span data-ttu-id="cfeb4-190">Essa propriedade é a URL https:// que aponta para a interface do usuário a ser exibida quando o usuário exclui a guia. Este é um campo opcional.</span><span class="sxs-lookup"><span data-stu-id="cfeb4-190">This property is the https:// URL that points to the UI to be displayed when the user deletes the tab. This is an optional field.</span></span>|

## <a name="see-also"></a><span data-ttu-id="cfeb4-191">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfeb4-191">See also</span></span>

[<span data-ttu-id="cfeb4-192">Vinculação de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="cfeb4-192">Messaging extensions link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)


