---
title: Adicionar uma guia do Teams ao SharePoint
author: surbhigupta
description: Como implantar sua guia de Teams existente para SharePoint como uma web part Estrutura do SharePoint web part.
keywords: teams tabs sharepoint framework development
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 6720cf3fdc8a02d325bf775f4bf319b9d07ec17c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068645"
---
# <a name="add-teams-tab-to-sharepoint"></a><span data-ttu-id="f171c-104">Adicionar uma guia do Teams ao SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-104">Add Teams tab to SharePoint</span></span> 

<span data-ttu-id="f171c-105">Você pode obter uma experiência de integração rica entre Microsoft Teams e SharePoint adicionando uma guia Microsoft Teams no SharePoint como uma web part SPFx web part.</span><span class="sxs-lookup"><span data-stu-id="f171c-105">You can get a rich integration experience between Microsoft Teams and SharePoint by adding a Microsoft Teams tab in SharePoint as an SPFx web part.</span></span> <span data-ttu-id="f171c-106">Este documento orienta você sobre como você deve pegar uma guia de um aplicativo de exemplo Microsoft Teams e usá-lo em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f171c-106">This document guides you on how you to take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> 

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="f171c-107">Integração rica entre Teams e SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-107">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="f171c-108">Com a versão de novembro do Teams e Estrutura do SharePoint v.1.7, os desenvolvedores têm dois recursos avançados:</span><span class="sxs-lookup"><span data-stu-id="f171c-108">With the November release of Teams and SharePoint Framework v.1.7, developers have two powerful capabilities:</span></span>

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" alt="tab-in-sharepoint view"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="f171c-109">Teams Guias no SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-109">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="f171c-110">Crie experiências de aplicativos rich SharePoint trazendo seu aplicativo Teams para o Sharepoint (este artigo).</span><span class="sxs-lookup"><span data-stu-id="f171c-110">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" alt="web-part-exposed-as-a-tab" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="f171c-111">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="f171c-111">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="f171c-112">Traga suas SharePoint web parts para Teams e deixe SharePoint gerenciar a hospedagem para você.</span><span class="sxs-lookup"><span data-stu-id="f171c-112">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="f171c-113">Teams guias no SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-113">Teams tabs in SharePoint</span></span>

<span data-ttu-id="f171c-114">Com Estrutura do SharePoint v.1.7, você pode hospedar suas Teams de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f171c-114">With SharePoint Framework v.1.7, you can host your Teams tabs in SharePoint.</span></span> <span data-ttu-id="f171c-115">À medida que as guias hospedadas  no SharePoint obter uma experiência de página inteira semelhante, expondo todos os recursos das guias Teams enquanto mantém o contexto e a familiaridade de um site SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f171c-115">As tabs hosted in SharePoint get a similar **full page** experience, exposing all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="f171c-116">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="f171c-116">SharePoint Framework in Teams</span></span>

<span data-ttu-id="f171c-117">Você também pode implementar suas guias Microsoft Teams usando Estrutura do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f171c-117">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="f171c-118">Estrutura do SharePoint web parts são hospedadas em SharePoint sem qualquer necessidade de serviços externos, como o Azure.</span><span class="sxs-lookup"><span data-stu-id="f171c-118">SharePoint Framework web parts are hosted within SharePoint without any need for external services, such as Azure.</span></span> <span data-ttu-id="f171c-119">Para SharePoint desenvolvedores, isso simplifica significativamente o processo de desenvolvimento para Teams guias.</span><span class="sxs-lookup"><span data-stu-id="f171c-119">For SharePoint developers, this significantly simplifies the development process for Teams tabs.</span></span> <span data-ttu-id="f171c-120">Para obter mais informações sobre Estrutura do SharePoint em Teams, consulte como usar o Estrutura do SharePoint [em Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)</span><span class="sxs-lookup"><span data-stu-id="f171c-120">For more information on SharePoint Framework in Teams, see [how to use the SharePoint Framework in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)</span></span>

## <a name="introduction"></a><span data-ttu-id="f171c-121">Introdução</span><span class="sxs-lookup"><span data-stu-id="f171c-121">Introduction</span></span>

<span data-ttu-id="f171c-122">A guia usada aqui já está hospedada no Azure, para se concentrar no trabalho de integração necessário.</span><span class="sxs-lookup"><span data-stu-id="f171c-122">The tab used here is already hosted on Azure, to focus on the required integration work.</span></span>

<span data-ttu-id="f171c-123">O aplicativo de exemplo que está sendo usado é um aplicativo de Gerenciamento de Talentos.</span><span class="sxs-lookup"><span data-stu-id="f171c-123">The sample app that is being used is a Talent Management application.</span></span> <span data-ttu-id="f171c-124">Ele gerencia o processo de contratação de candidatos para posições abertas em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f171c-124">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="f171c-125">Crie um aplicativo Teams exemplo e carregue-o em Teams.</span><span class="sxs-lookup"><span data-stu-id="f171c-125">Build a sample Teams app and load it into Teams.</span></span> <span data-ttu-id="f171c-126">Não crie um aplicativo de gerenciamento de talentos real.</span><span class="sxs-lookup"><span data-stu-id="f171c-126">Do not create a real talent management application.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="f171c-127">Benefícios dessa abordagem</span><span class="sxs-lookup"><span data-stu-id="f171c-127">Benefits of this approach</span></span>

* <span data-ttu-id="f171c-128">Entre SharePoint usuários com sua guia Teams existente.</span><span class="sxs-lookup"><span data-stu-id="f171c-128">Reach SharePoint users with your existing Teams tab.</span></span>
* <span data-ttu-id="f171c-129">Upload seu manifesto do aplicativo diretamente para seu catálogo SharePoint aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f171c-129">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="f171c-130">[Teams pacotes de aplicativos](~/concepts/build-and-test/apps-package.md) agora são suportados por SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f171c-130">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint.</span></span>
* <span data-ttu-id="f171c-131">Os usuários configuram a guia em uma página como qualquer outra web part SharePoint web part.</span><span class="sxs-lookup"><span data-stu-id="f171c-131">The users configure the tab on a page just like any other SharePoint web part.</span></span>
* <span data-ttu-id="f171c-132">Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) da mesma forma que pode, ao executar dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="f171c-132">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) sameas it can, when running inside Teams.</span></span>

<span data-ttu-id="f171c-133">**Para adicionar Teams guia SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f171c-133">**To add Teams tab to SharePoint**</span></span>

<span data-ttu-id="f171c-134">Execute as seguintes etapas para adicionar Teams guia SharePoint:</span><span class="sxs-lookup"><span data-stu-id="f171c-134">Perform the following steps to add Teams tab to SharePoint:</span></span>

## <a name="1-test-the-sample-app"></a><span data-ttu-id="f171c-135">1. Teste o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="f171c-135">1. Test the sample app</span></span>

<span data-ttu-id="f171c-136">Baixe o [manifesto do aplicativo de exemplo](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span><span class="sxs-lookup"><span data-stu-id="f171c-136">Download the [sample app manifest](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

1. <span data-ttu-id="f171c-137">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f171c-137">Open Microsoft Teams.</span></span>
1. <span data-ttu-id="f171c-138">Selecione o **ícone Appstore** no canto inferior esquerdo da guia lateral.</span><span class="sxs-lookup"><span data-stu-id="f171c-138">Select the **Appstore** icon at the lower left of side tab.</span></span>
1. <span data-ttu-id="f171c-139">Selecione **Upload um aplicativo personalizado** no canto inferior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="f171c-139">Select **Upload a custom app** at the lower left.</span></span> <span data-ttu-id="f171c-140">A imagem a seguir exibe a tela correspondente:</span><span class="sxs-lookup"><span data-stu-id="f171c-140">The following image displays the corresponding screen:</span></span>  

    ![carregar um aplicativo personalizado](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. <span data-ttu-id="f171c-142">O arquivo a ser carregado está localizado na pasta **Downloads.**</span><span class="sxs-lookup"><span data-stu-id="f171c-142">The file to upload is located in your **Downloads** folder.</span></span> <span data-ttu-id="f171c-143">Ele é chamado TalentMgmt-Azure.zip.</span><span class="sxs-lookup"><span data-stu-id="f171c-143">It is called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="f171c-144">A imagem a seguir exibe a tela correspondente:</span><span class="sxs-lookup"><span data-stu-id="f171c-144">The following image displays the corresponding screen:</span></span>
 
    ![TalentMgmt no Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. <span data-ttu-id="f171c-146">Você pode ver a tela de instalação ou consentimento do aplicativo de gerenciamento de talentos.</span><span class="sxs-lookup"><span data-stu-id="f171c-146">You can see the install or consent screen for the talent management app.</span></span> <span data-ttu-id="f171c-147">Selecione a equipe que deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="f171c-147">Select the team you want to install.</span></span> 
1. <span data-ttu-id="f171c-148">Selecione Instalar **e** comece a experimentar com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f171c-148">Select the **Install** and start experimenting with the app.</span></span>

## <a name="2-use-teams-tab-in-sharepoint"></a><span data-ttu-id="f171c-149">2. Use Teams guia no SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-149">2. Use Teams tab in SharePoint</span></span>

1. <span data-ttu-id="f171c-150">Upload e implante seu pacote de aplicativos Teams no catálogo de aplicativos SharePoint, visitando `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` .</span><span class="sxs-lookup"><span data-stu-id="f171c-150">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span> <span data-ttu-id="f171c-151">Por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span><span class="sxs-lookup"><span data-stu-id="f171c-151">For example, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

1. <span data-ttu-id="f171c-152">Quando solicitado, **habilitar Tornar essa solução disponível para todos os sites da organização**.</span><span class="sxs-lookup"><span data-stu-id="f171c-152">When prompted, enable **Make this solution available to all sites in the organization**.</span></span>
<span data-ttu-id="f171c-153">A imagem a seguir exibe a tela correspondente:</span><span class="sxs-lookup"><span data-stu-id="f171c-153">The following image displays the corresponding screen:</span></span>

   ![Guias no exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. <span data-ttu-id="f171c-155">Em seu site, crie uma nova página selecionando o botão de engrenagem no canto superior direito e selecione **Adicionar uma página**.</span><span class="sxs-lookup"><span data-stu-id="f171c-155">In your site, create a new page by selecting the gear button at the upper right and then  select **Add a page**.</span></span>
<span data-ttu-id="f171c-156">A imagem a seguir exibe a tela correspondente:</span><span class="sxs-lookup"><span data-stu-id="f171c-156">The following image displays the corresponding screen:</span></span>

   ![Exibição do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. <span data-ttu-id="f171c-158">Você pode ver a experiência de SharePoint de autoria de páginas.</span><span class="sxs-lookup"><span data-stu-id="f171c-158">You can see the SharePoint pages authoring experience.</span></span> <span data-ttu-id="f171c-159">Nomeia sua página como **My Teams Tab.**</span><span class="sxs-lookup"><span data-stu-id="f171c-159">Name your page as **My Teams Tab**.</span></span>

1. <span data-ttu-id="f171c-160">Abra a caixa de ferramentas da Web Part pressionando o botão e selecione `+` sua guia Teams, chamada **Contoso HR**.</span><span class="sxs-lookup"><span data-stu-id="f171c-160">Open the web part toolbox by pressing the `+` button, and select your Teams Tab, named **Contoso HR**.</span></span> <span data-ttu-id="f171c-161">As Web Parts são classificação alfabética.</span><span class="sxs-lookup"><span data-stu-id="f171c-161">Web parts are sorted alphabetically.</span></span> <span data-ttu-id="f171c-162">Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la.</span><span class="sxs-lookup"><span data-stu-id="f171c-162">If it is a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="f171c-163">Isso cria uma Web Part na tela que contém sua guia Teams. A imagem a seguir exibe o visor de tabulação:</span><span class="sxs-lookup"><span data-stu-id="f171c-163">This creates a web part in the canvas that contains your Teams tab. The following image displays the tab view:</span></span>

   ![Exibição de tabulação](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. <span data-ttu-id="f171c-165">Pressione o **botão Publicar** depois de concluir a edição.</span><span class="sxs-lookup"><span data-stu-id="f171c-165">Press the **Publish** button after you finish  editing.</span></span>

1. <span data-ttu-id="f171c-166">Selecione **Adicionar página à navegação** para ter uma referência rápida à sua página na barra de navegação esquerda.</span><span class="sxs-lookup"><span data-stu-id="f171c-166">Select **Add page to navigation** to have a quick reference to your page in the left navigation bar.</span></span> <span data-ttu-id="f171c-167">A imagem a seguir exibe a guia no Sharepoint:</span><span class="sxs-lookup"><span data-stu-id="f171c-167">The following image displays the tab in Sharepoint:</span></span> 

   ![Guia na imagem do Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="f171c-169">3. Explorar páginas de aplicativo no SharePoint</span><span class="sxs-lookup"><span data-stu-id="f171c-169">3. Explore App Pages in SharePoint</span></span>

<span data-ttu-id="f171c-170">Depois que sua página for publicada, você poderá explorar transformar seu aplicativo Teams em uma experiência mais [completa dentro SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span><span class="sxs-lookup"><span data-stu-id="f171c-170">After your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="f171c-171">Isso converte a página atual em uma Página do Aplicativo, mostrando o layout de página SharePoint normal com uma experiência de página inteira para a guia Teams.</span><span class="sxs-lookup"><span data-stu-id="f171c-171">This converts the current page into an App Page, showing the normal SharePoint page layout with a full page experience for the Teams tab.</span></span> 

<span data-ttu-id="f171c-172">A imagem a seguir exibe a experiência completa do aplicativo Teams sharepoint: ![ imagem de guias no Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)</span><span class="sxs-lookup"><span data-stu-id="f171c-172">The following image displays the complete experience of Teams app in Sharepoint: ![Image of Tabs in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)</span></span>

## <a name="code-sample"></a><span data-ttu-id="f171c-173">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f171c-173">Code sample</span></span>
| <span data-ttu-id="f171c-174">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="f171c-174">**Sample name**</span></span> | <span data-ttu-id="f171c-175">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f171c-175">**Description**</span></span> | <span data-ttu-id="f171c-176">**SPFx**</span><span class="sxs-lookup"><span data-stu-id="f171c-176">**SPFx**</span></span> |
|-----------------|-----------------|----------|
| <span data-ttu-id="f171c-177">SPFx Web Part</span><span class="sxs-lookup"><span data-stu-id="f171c-177">SPFx web part</span></span> | <span data-ttu-id="f171c-178">SPFx exemplos de Web Part para guias, canais e grupos.</span><span class="sxs-lookup"><span data-stu-id="f171c-178">SPFx web part samples for tabs, channels, and groups.</span></span> | [<span data-ttu-id="f171c-179">View</span><span class="sxs-lookup"><span data-stu-id="f171c-179">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a><span data-ttu-id="f171c-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="f171c-180">See also</span></span>

* [<span data-ttu-id="f171c-181">Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial</span><span class="sxs-lookup"><span data-stu-id="f171c-181">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
* [<span data-ttu-id="f171c-182">Usar páginas de aplicativos de parte única no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f171c-182">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
* [<span data-ttu-id="f171c-183">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="f171c-183">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
