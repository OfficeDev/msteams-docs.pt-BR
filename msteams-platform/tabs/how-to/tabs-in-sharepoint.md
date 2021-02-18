---
title: Adding a Microsoft Teams tab in SharePoint as an SPFx web part
author: laujan
description: Como implantar sua guia existente do Teams no SharePoint como uma Web Part da Estrutura do SharePoint.
keywords: teams tabs sharepoint framework development
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2e5d1b01aa5f7566e25c7720d6a0539386226576
ms.sourcegitcommit: 6caf503de5544fb8b9c8c6bef8eff4ff5a46068c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/17/2021
ms.locfileid: "50270788"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a><span data-ttu-id="4131c-104">Adding a Microsoft Teams tab in SharePoint as an SPFx web part</span><span class="sxs-lookup"><span data-stu-id="4131c-104">Adding a Microsoft Teams tab in SharePoint as an SPFx web part</span></span>

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="4131c-105">Integração rica entre o Teams e o SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-105">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="4131c-106">Com a versão de novembro do Teams e da Estrutura do SharePoint v.</span><span class="sxs-lookup"><span data-stu-id="4131c-106">With the November release of Teams and SharePoint Framework v.</span></span> <span data-ttu-id="4131c-107">1.7, os desenvolvedores têm dois recursos poderosos:</span><span class="sxs-lookup"><span data-stu-id="4131c-107">1.7, developers have two powerful capabilities:</span></span>

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
                        <h3><span data-ttu-id="4131c-108">Guias do Teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-108">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="4131c-109">Crie experiências de aplicativos ricos no SharePoint, trazendo seu aplicativo teams para o SharePoint (este artigo).</span><span class="sxs-lookup"><span data-stu-id="4131c-109">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" alt="web-part-exposed-as-a-tab" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="4131c-110">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="4131c-110">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="4131c-111">Traga suas Web Parts do SharePoint para o Teams e deixe que o SharePoint gerencie a hospedagem para você.</span><span class="sxs-lookup"><span data-stu-id="4131c-111">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="4131c-112">Guias do Teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-112">Teams tabs in SharePoint</span></span>

<span data-ttu-id="4131c-113">Com a Estrutura do SharePoint v.1.7, agora estamos dando suporte à capacidade de os desenvolvedores usarem suas guias do Teams e hospedá-los no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-113">With SharePoint Framework v.1.7, we’re now supporting the ability for developers to take their Teams tabs and host it in SharePoint.</span></span> <span data-ttu-id="4131c-114">As Guias hospedadas no SharePoint têm uma experiência semelhante de "página inteira", expondo todos os recursos das guias do Teams, mantendo o contexto e a familiaridade de um site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-114">As Tabs hosted in SharePoint get a similar "full page" experience, exposing the all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="4131c-115">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="4131c-115">SharePoint Framework in Teams</span></span>

<span data-ttu-id="4131c-116">Você também pode implementar as guias do Microsoft Teams usando a Estrutura do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-116">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="4131c-117">Para os desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento para as guias do Teams porque as Web Parts da Estrutura do SharePoint são hospedadas no SharePoint sem a necessidade de serviços externos, como o Azure.</span><span class="sxs-lookup"><span data-stu-id="4131c-117">For SharePoint developers, this significantly simplifies the development process for Teams tabs because SharePoint Framework web parts are hosted within SharePoint without any need for external services such as Azure.</span></span> [<span data-ttu-id="4131c-118">Saiba mais sobre como usar a Estrutura do SharePoint no Teams.</span><span class="sxs-lookup"><span data-stu-id="4131c-118">Learn more about using the SharePoint Framework in Teams.</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a><span data-ttu-id="4131c-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="4131c-119">Introduction</span></span>

<span data-ttu-id="4131c-120">Essas instruções explicarão como você pode fazer uma guia de um aplicativo de exemplo do Microsoft Teams e usá-lo no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-120">These instructions will explain how you can take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> <span data-ttu-id="4131c-121">Vamos usar uma guia que já está hospedada no Azure para se concentrar no trabalho de integração necessário.</span><span class="sxs-lookup"><span data-stu-id="4131c-121">We will be using a tab that's already hosted on Azure in order to focus on the required integration work.</span></span>

<span data-ttu-id="4131c-122">O aplicativo de exemplo que estamos usando é um aplicativo de Gerenciamento de Talentos.</span><span class="sxs-lookup"><span data-stu-id="4131c-122">The sample app we're using is a Talent Management application.</span></span> <span data-ttu-id="4131c-123">Ele gerencia o processo de contratação de candidatos para posições abertas em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4131c-123">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="4131c-124">(O aplicativo em si, embora pareça bom, na verdade não faz nada.</span><span class="sxs-lookup"><span data-stu-id="4131c-124">(The app itself, while it looks nice, doesn't actually do anything.</span></span> <span data-ttu-id="4131c-125">Queremos nos concentrar na criação de um aplicativo do Teams e no carregamento dele no Teams, não na criação de um aplicativo de gerenciamento de talentos reais.)</span><span class="sxs-lookup"><span data-stu-id="4131c-125">We want to focus on building a Teams app and loading it into Teams, not create a real talent management application.)</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="4131c-126">Benefícios dessa abordagem</span><span class="sxs-lookup"><span data-stu-id="4131c-126">Benefits of this approach</span></span>

- <span data-ttu-id="4131c-127">Alcance os usuários do SharePoint com a guia do Teams existente</span><span class="sxs-lookup"><span data-stu-id="4131c-127">Reach SharePoint users with your existing Teams tab</span></span>
- <span data-ttu-id="4131c-128">Carregue o manifesto do aplicativo diretamente no catálogo de aplicativos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-128">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="4131c-129">[Os pacotes de aplicativos](~/concepts/build-and-test/apps-package.md) do Teams agora são suportados pelo SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-129">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint</span></span>
- <span data-ttu-id="4131c-130">Os usuários finais configuram a guia em uma página como qualquer outra Web Part do SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-130">End users configure the tab on a page just like any other SharePoint web part</span></span>
- <span data-ttu-id="4131c-131">Sua guia pode acessar seu [contexto da](~/tabs/how-to/access-teams-context.md) mesma forma que pode ao executar no Teams</span><span class="sxs-lookup"><span data-stu-id="4131c-131">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) just as it can when running inside Teams</span></span>

## <a name="step-1-testing-the-sample-app"></a><span data-ttu-id="4131c-132">Etapa 1: testar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="4131c-132">Step 1: Testing the sample app</span></span>

<span data-ttu-id="4131c-133">Baixe o manifesto do aplicativo de exemplo [**a partir daqui.**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)</span><span class="sxs-lookup"><span data-stu-id="4131c-133">Download the sample app manifest from [**here**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

<span data-ttu-id="4131c-134">No Microsoft Teams, clique no ícone da Loja no canto inferior esquerdo e, em seguida, em "Carregar um aplicativo personalizado" no canto inferior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="4131c-134">In Microsoft Teams, click on the Store icon at the lower left and then "Upload a custom app" at the lower left.</span></span> <span data-ttu-id="4131c-135">O arquivo a ser carregado estará localizado em sua pasta Downloads; ele é chamado de TalentMgmt-Azure.zip.</span><span class="sxs-lookup"><span data-stu-id="4131c-135">The file to upload will be located in your Downloads folder; it's called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="4131c-136">Se tudo correr bem, você verá a tela de instalação/consentimento do aplicativo de gerenciamento de talentos.</span><span class="sxs-lookup"><span data-stu-id="4131c-136">If all goes well, you'll see the install/consent screen for the talent management app.</span></span> <span data-ttu-id="4131c-137">Escolha a equipe que você deseja instalar e clique no botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="4131c-137">Choose the team you want to install to and click the Install button.</span></span> <span data-ttu-id="4131c-138">Agora você está livre para experimentar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4131c-138">You're now free to experiment with the app.</span></span>

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a><span data-ttu-id="4131c-139">Etapa 2: Usar a guia Teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-139">Step 2: Using the Teams tab in SharePoint</span></span>

<span data-ttu-id="4131c-140">Carregue e implante o pacote de aplicativos do Teams no catálogo de aplicativos do SharePoint `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` visitando, por exemplo, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` .</span><span class="sxs-lookup"><span data-stu-id="4131c-140">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, e.g. `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

<span data-ttu-id="4131c-141">Quando solicitado, habilita "Disponibilizar esta solução para todos os sites da organização":</span><span class="sxs-lookup"><span data-stu-id="4131c-141">When prompted, enable "Make this solution available to all sites in the organization":</span></span>

![Guias no exibição do SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

<span data-ttu-id="4131c-143">Em seu site, crie uma nova página clicando no botão de engrenagem no canto superior direito e, em seguida, em "Adicionar uma página":</span><span class="sxs-lookup"><span data-stu-id="4131c-143">In your site, create a new page by clicking in the gear button at the upper right and then "Add a page":</span></span>

![Exibição do SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

<span data-ttu-id="4131c-145">Você verá a experiência de autoria de Páginas do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4131c-145">You'll see the SharePoint Pages authoring experience.</span></span> <span data-ttu-id="4131c-146">Nomeia sua página como "Guia Minhas Equipes".</span><span class="sxs-lookup"><span data-stu-id="4131c-146">Name your page "My Teams Tab".</span></span>

<span data-ttu-id="4131c-147">Abra a caixa de ferramentas da Web Part pressionando o botão + e selecione a guia Do Teams (chamada "Contoso HR").</span><span class="sxs-lookup"><span data-stu-id="4131c-147">Open the web part toolbox by pressing the + button, and select your Teams Tab (named "Contoso HR").</span></span> <span data-ttu-id="4131c-148">As Web Parts são ordenadas em ordem alfabética; se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la.</span><span class="sxs-lookup"><span data-stu-id="4131c-148">Web parts are sorted alphabetically; if it's a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="4131c-149">Isso criará uma Web Part na tela que contém a guia do Teams:</span><span class="sxs-lookup"><span data-stu-id="4131c-149">This will create a web part in the canvas that contains your Teams tab:</span></span>

![Exibição de guia](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

<span data-ttu-id="4131c-151">Pressione o botão "Publicar" quando terminar de editar.</span><span class="sxs-lookup"><span data-stu-id="4131c-151">Press the "Publish" button when you are finished editing.</span></span>

<span data-ttu-id="4131c-152">Você pode clicar em "Adicionar página à navegação" para ter uma referência rápida à sua página na barra de navegação esquerda:</span><span class="sxs-lookup"><span data-stu-id="4131c-152">You may want to click "Add page to navigation" to have a quick reference to your page in the left navigation bar:</span></span>

![Tab in Sharepoint image](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="4131c-154">Etapa 3: Explorar páginas de aplicativos no SharePoint</span><span class="sxs-lookup"><span data-stu-id="4131c-154">Step 3: Explore App Pages in SharePoint</span></span>

<span data-ttu-id="4131c-155">Depois que sua página for publicada, você poderá explorar como [transformar seu aplicativo teams em uma experiência mais completa no SharePoint.](/sharepoint/dev/spfx/web-parts/single-part-app-pages)</span><span class="sxs-lookup"><span data-stu-id="4131c-155">Once your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="4131c-156">Isso converte a página atual em uma página de aplicativo, mostrando o layout normal da página do SharePoint com uma experiência de página inteira para a guia do Teams:</span><span class="sxs-lookup"><span data-stu-id="4131c-156">This converts the current page into an App Page, showing the normal SharePoint page layout with a full-page experience for the Teams tab:</span></span>

![Imagem de guias no SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a><span data-ttu-id="4131c-158">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4131c-158">Code sample</span></span>
| <span data-ttu-id="4131c-159">**Nome do exemplo**</span><span class="sxs-lookup"><span data-stu-id="4131c-159">**Sample name**</span></span> | <span data-ttu-id="4131c-160">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4131c-160">**Description**</span></span> | <span data-ttu-id="4131c-161">**SPFx**</span><span class="sxs-lookup"><span data-stu-id="4131c-161">**SPFx**</span></span> |
|-----------------|-----------------|----------|
| <span data-ttu-id="4131c-162">Web Part SPFx</span><span class="sxs-lookup"><span data-stu-id="4131c-162">SPFx web part</span></span> | <span data-ttu-id="4131c-163">Exemplos de Web Part SPFx para guias, canais e grupos.</span><span class="sxs-lookup"><span data-stu-id="4131c-163">SPFx web part samples for tabs, channels, and groups.</span></span> | [<span data-ttu-id="4131c-164">View</span><span class="sxs-lookup"><span data-stu-id="4131c-164">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="more-information"></a><span data-ttu-id="4131c-165">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4131c-165">More information</span></span>

- [<span data-ttu-id="4131c-166">Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial</span><span class="sxs-lookup"><span data-stu-id="4131c-166">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [<span data-ttu-id="4131c-167">Usar páginas de aplicativos de parte única no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4131c-167">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
