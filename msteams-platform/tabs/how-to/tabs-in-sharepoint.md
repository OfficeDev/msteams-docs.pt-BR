---
title: Adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx
author: laujan
description: Como implantar sua guia do teams existente no SharePoint como uma Web Part da estrutura do SharePoint.
keywords: guias do Microsoft Teams desenvolvimento do SharePoint Framework
ms.topic: conceptual
ms.author: ''
ms.openlocfilehash: b29cd29891779a69a0342f10d383792b3818590a
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672687"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a><span data-ttu-id="dbfcb-104">Adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx</span><span class="sxs-lookup"><span data-stu-id="dbfcb-104">Adding a Microsoft Teams tab in SharePoint as an SPFx web part</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbfcb-105">Este recurso atualmente está em versão prévia e está sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-105">This feature is currently in preview and is subject to change.</span></span> <span data-ttu-id="dbfcb-106">Não há suporte para uso em ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-106">It is not supported for use in production environments.</span></span> <span data-ttu-id="dbfcb-107">Agradecemos por seus comentários sobre essa funcionalidade na [lista de problemas de documentos de desenvolvimento do SharePoint](https://github.com/SharePoint/sp-dev-docs/issues).</span><span class="sxs-lookup"><span data-stu-id="dbfcb-107">Your feedback and input around this capability is welcome using the [SharePoint Dev Docs issue list](https://github.com/SharePoint/sp-dev-docs/issues).</span></span>

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="dbfcb-108">Integração avançada entre o Teams e o SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-108">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="dbfcb-109">Com a edição de novembro do Teams e do SharePoint Framework v.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-109">With the November release of Teams and SharePoint Framework v.</span></span> <span data-ttu-id="dbfcb-110">1,7, os desenvolvedores têm dois recursos avançados:</span><span class="sxs-lookup"><span data-stu-id="dbfcb-110">1.7, developers have two powerful capabilities:</span></span>

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="dbfcb-111">Guias do teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-111">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="dbfcb-112">Crie experiências de aplicativos avançados no SharePoint trazendo seu aplicativo do Microsoft Teams para o SharePoint (este artigo).</span><span class="sxs-lookup"><span data-stu-id="dbfcb-112">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
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
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="dbfcb-113">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="dbfcb-113">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="dbfcb-114">Traga suas Web Parts do SharePoint para o Microsoft Teams e permita que o SharePoint gerencie a hospedagem para você.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-114">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="dbfcb-115">Guias do teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-115">Teams tabs in SharePoint</span></span>

<span data-ttu-id="dbfcb-116">Com o SharePoint Framework v. 1.7, estamos dando suporte à capacidade dos desenvolvedores de usar suas guias de equipes e hospedá-lo no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-116">With SharePoint Framework v.1.7, we’re now supporting the ability for developers to take their Teams tabs and host it in SharePoint.</span></span> <span data-ttu-id="dbfcb-117">Como guias hospedados no SharePoint, obtenha uma experiência de "página inteira" semelhante, expondo todos os recursos das guias do teams enquanto mantém o contexto e a familiaridade de um site do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-117">As Tabs hosted in SharePoint get a similar "full page" experience, exposing the all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="dbfcb-118">Estrutura do SharePoint no Teams</span><span class="sxs-lookup"><span data-stu-id="dbfcb-118">SharePoint Framework in Teams</span></span>

<span data-ttu-id="dbfcb-119">Você também pode implementar suas guias do Microsoft Teams usando o SharePoint Framework.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-119">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="dbfcb-120">Para desenvolvedores do SharePoint, isso simplifica significativamente o processo de desenvolvimento para guias do teams porque as Web Parts da estrutura do SharePoint são hospedadas no SharePoint sem necessidade de serviços externos, como o Azure.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-120">For SharePoint developers, this significantly simplifies the development process for Teams tabs because SharePoint Framework web parts are hosted within SharePoint without any need for external services such as Azure.</span></span> [<span data-ttu-id="dbfcb-121">Saiba mais sobre como usar a estrutura do SharePoint no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-121">Learn more about using the SharePoint Framework in Teams.</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a><span data-ttu-id="dbfcb-122">Introdução</span><span class="sxs-lookup"><span data-stu-id="dbfcb-122">Introduction</span></span>

<span data-ttu-id="dbfcb-123">Estas instruções explicarão como você pode obter uma guia de um aplicativo de exemplo do Microsoft Teams e usá-lo no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-123">These instructions will explain how you can take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> <span data-ttu-id="dbfcb-124">Usaremos uma guia que já está hospedada no Azure para se concentrar no trabalho de integração necessário.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-124">We will be using a tab that's already hosted on Azure in order to focus on the required integration work.</span></span>

<span data-ttu-id="dbfcb-125">O aplicativo de exemplo que estamos usando é um aplicativo de gerenciamento de talento.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-125">The sample app we're using is a Talent Management application.</span></span> <span data-ttu-id="dbfcb-126">Ele gerencia o processo de contratação de candidatos para posições abertas de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-126">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="dbfcb-127">(O próprio aplicativo, embora pareça bom, não faz nada.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-127">(The app itself, while it looks nice, doesn't actually do anything.</span></span> <span data-ttu-id="dbfcb-128">Queremos nos concentrar na criação de um aplicativo do Teams e carregá-lo no Microsoft Teams, não criar um aplicativo de gerenciamento de talento real.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-128">We want to focus on building a Teams app and loading it into Teams, not create a real talent management application.)</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="dbfcb-129">Benefícios dessa abordagem</span><span class="sxs-lookup"><span data-stu-id="dbfcb-129">Benefits of this approach</span></span>

- <span data-ttu-id="dbfcb-130">Acessar os usuários do SharePoint com sua guia do teams existente</span><span class="sxs-lookup"><span data-stu-id="dbfcb-130">Reach SharePoint users with your existing Teams tab</span></span>
- <span data-ttu-id="dbfcb-131">Carregue o manifesto do aplicativo diretamente no catálogo de aplicativos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-131">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="dbfcb-132">Os pacotes de aplicativos do Microsoft [Teams](~/concepts/build-and-test/apps-package.md) agora são compatíveis com o SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-132">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint</span></span>
- <span data-ttu-id="dbfcb-133">Os usuários finais configuram a guia em uma página assim como qualquer outra Web Part do SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-133">End users configure the tab on a page just like any other SharePoint web part</span></span>
- <span data-ttu-id="dbfcb-134">Sua guia pode acessar seu [contexto](~/tabs/how-to/access-teams-context.md) assim que possível ao executar o no Teams</span><span class="sxs-lookup"><span data-stu-id="dbfcb-134">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) just as it can when running inside Teams</span></span>

## <a name="step-1-testing-the-sample-app"></a><span data-ttu-id="dbfcb-135">Etapa 1: testar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="dbfcb-135">Step 1: Testing the sample app</span></span>

<span data-ttu-id="dbfcb-136">Baixe o manifesto do aplicativo de exemplo [**aqui**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span><span class="sxs-lookup"><span data-stu-id="dbfcb-136">Download the sample app manifest from [**here**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

<span data-ttu-id="dbfcb-137">No Microsoft Teams, clique no ícone do repositório no canto inferior esquerdo e, em seguida, em "carregar um aplicativo personalizado" no canto inferior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-137">In Microsoft Teams, click on the Store icon at the lower left and then "Upload a custom app" at the lower left.</span></span> <span data-ttu-id="dbfcb-138">O arquivo a ser carregado estará localizado na pasta downloads; Ele é chamado de TalentMgmt-Azure. zip.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-138">The file to upload will be located in your Downloads folder; it's called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="dbfcb-139">Se tudo correr bem, você verá a tela de instalação/consentimento para o aplicativo de gerenciamento de talento.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-139">If all goes well, you'll see the install/consent screen for the talent management app.</span></span> <span data-ttu-id="dbfcb-140">Escolha a equipe que você deseja instalar e clique no botão instalar.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-140">Choose the team you want to install to and click the Install button.</span></span> <span data-ttu-id="dbfcb-141">Agora você está livre para experimentar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-141">You're now free to experiment with the app.</span></span>

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a><span data-ttu-id="dbfcb-142">Etapa 2: usar a guia Teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-142">Step 2: Using the Teams tab in SharePoint</span></span>

<span data-ttu-id="dbfcb-143">Carregue e implante seu pacote de aplicativos do teams no seu catálogo de `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`aplicativos do SharePoint `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, por exemplo,.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-143">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, e.g. `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

<span data-ttu-id="dbfcb-144">Quando solicitado, habilite "tornar esta solução disponível para todos os sites na organização":</span><span class="sxs-lookup"><span data-stu-id="dbfcb-144">When prompted, enable "Make this solution available to all sites in the organization":</span></span>

![](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

<span data-ttu-id="dbfcb-145">Em seu site, crie uma nova página clicando no botão de engrenagem no canto superior direito e, em seguida, "adicionar uma página":</span><span class="sxs-lookup"><span data-stu-id="dbfcb-145">In your site, create a new page by clicking in the gear button at the upper right and then "Add a page":</span></span>

![](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

<span data-ttu-id="dbfcb-146">Você verá a experiência de criação de páginas do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-146">You'll see the SharePoint Pages authoring experience.</span></span> <span data-ttu-id="dbfcb-147">Nomeie a página "guia minhas equipes".</span><span class="sxs-lookup"><span data-stu-id="dbfcb-147">Name your page "My Teams Tab".</span></span>

<span data-ttu-id="dbfcb-148">Abra a caixa de ferramentas da Web Part pressionando o botão + e selecione sua guia Teams (chamada "contoso HR").</span><span class="sxs-lookup"><span data-stu-id="dbfcb-148">Open the web part toolbox by pressing the + button, and select your Teams Tab (named "Contoso HR").</span></span> <span data-ttu-id="dbfcb-149">As Web Parts são classificadas em ordem alfabética; Se for uma lista longa, você poderá usar a barra de pesquisa para encontrá-la.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-149">Web parts are sorted alphabetically; if it's a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="dbfcb-150">Isso criará uma Web Part na tela de desenho que contém a guia de suas equipes:</span><span class="sxs-lookup"><span data-stu-id="dbfcb-150">This will create a web part in the canvas that contains your Teams tab:</span></span>

![](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

<span data-ttu-id="dbfcb-151">Pressione o botão "publicar" ao concluir a edição.</span><span class="sxs-lookup"><span data-stu-id="dbfcb-151">Press the "Publish" button when you are finished editing.</span></span>

<span data-ttu-id="dbfcb-152">Talvez você queira clicar em "Adicionar página à navegação" para ter uma referência rápida à página na barra de navegação esquerda:</span><span class="sxs-lookup"><span data-stu-id="dbfcb-152">You may want to click "Add page to navigation" to have a quick reference to your page in the left navigation bar:</span></span>

![](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="dbfcb-153">Etapa 3: explorar as páginas do aplicativo no SharePoint</span><span class="sxs-lookup"><span data-stu-id="dbfcb-153">Step 3: Explore App Pages in SharePoint</span></span>

<span data-ttu-id="dbfcb-154">Depois que a página for publicada, você poderá explorar [a ativação do aplicativo do Microsoft Teams para uma experiência mais completa dentro do SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span><span class="sxs-lookup"><span data-stu-id="dbfcb-154">Once your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="dbfcb-155">Isso converte a página atual em uma página de aplicativo, mostrando o layout de página normal do SharePoint com uma experiência de página inteira para a guia Teams:</span><span class="sxs-lookup"><span data-stu-id="dbfcb-155">This converts the current page into an App Page, showing the normal SharePoint page layout with a full-page experience for the Teams tab:</span></span>

![](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="more-information"></a><span data-ttu-id="dbfcb-156">Mais informações</span><span class="sxs-lookup"><span data-stu-id="dbfcb-156">More information</span></span>

- [<span data-ttu-id="dbfcb-157">Criando guias do Microsoft Teams usando a Estrutura do SharePoint – Tutorial</span><span class="sxs-lookup"><span data-stu-id="dbfcb-157">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [<span data-ttu-id="dbfcb-158">Usar páginas de aplicativos de parte única no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dbfcb-158">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
