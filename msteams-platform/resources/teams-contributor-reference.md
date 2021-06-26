---
title: Contribuir para Teams documentação
description: etapas para criar e publicar Teams documentação
author: surbhigupta
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: a567b0462397780650d6173df9dae1b340a06f97
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140507"
---
# <a name="contribute-to-teams-documentation"></a><span data-ttu-id="0b4eb-103">Contribuir para Teams documentação</span><span class="sxs-lookup"><span data-stu-id="0b4eb-103">Contribute to Teams documentation</span></span>

<span data-ttu-id="0b4eb-104">Teams documentação faz parte da biblioteca de documentação técnica do **Microsoft Docs.**</span><span class="sxs-lookup"><span data-stu-id="0b4eb-104">Teams documentation is part of the **Microsoft Docs** technical documentation library.</span></span> <span data-ttu-id="0b4eb-105">O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-105">The content is organized into groups called docsets, each representing a group of related documents managed as a single entity.</span></span> <span data-ttu-id="0b4eb-106">Os artigos no mesmo docset têm a mesma extensão de caminho de URL após **docs.microsoft.com**.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-106">Articles in the same docset have the same URL path extension after **docs.microsoft.com**.</span></span> <span data-ttu-id="0b4eb-107">Por exemplo, `/docs.microsoft.com/microsoftteams/...` é o início do caminho do arquivo Teams docset.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-107">For example, `/docs.microsoft.com/microsoftteams/...` is the beginning of the Teams docset file path.</span></span> <span data-ttu-id="0b4eb-108">Teams artigos são escritos na sintaxe Markdown e hospedados em GitHub.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-108">Teams articles are written in Markdown syntax and hosted on GitHub.</span></span>

## <a name="set-up-your-workspace"></a><span data-ttu-id="0b4eb-109">Configurar seu espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="0b4eb-109">Set up your workspace</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0b4eb-110">Instalar [o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-110">Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).</span></span>
> * <span data-ttu-id="0b4eb-111">Instalar [Visual Studio Code](https://code.visualstudio.com/) (VS Code).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-111">Install [Visual Studio Code](https://code.visualstudio.com/) (VS Code).</span></span>
> * <span data-ttu-id="0b4eb-112">Instale [o Pacote de Autoria de Documentos](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente do VS Code Marketplace.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-112">Install [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) directly from the VS Code Marketplace.</span></span>
<br><span data-ttu-id="0b4eb-113">&emsp;&emsp; ou</span><span class="sxs-lookup"><span data-stu-id="0b4eb-113">&emsp;&emsp; or</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0b4eb-114">Instalar dentro VS Code:</span><span class="sxs-lookup"><span data-stu-id="0b4eb-114">Install within VS Code:</span></span>

   1. <span data-ttu-id="0b4eb-115">Selecione o **ícone Extensões** na barra de atividades lateral ou use o comando **Exibir => Extensões** ou Ctrl+Shift+X e, pesquise o **Microsoft Docs Authoring Pack**.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-115">Select the **Extensions icon** on the side activity bar or use the **View => Extensions** command or Ctrl+Shift+X and, search for **Microsoft Docs Authoring Pack**.</span></span>
   1. <span data-ttu-id="0b4eb-116">Selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-116">Select **Install**.</span></span>
   1. <span data-ttu-id="0b4eb-117">Após a instalação, **o botão Instalar** muda para o botão **Gerenciar** engrenagem.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-117">After installation, the **Install** changes to the **Manage** gear button.</span></span>

## <a name="review-the-microsoft-docs-contributors-guide"></a><span data-ttu-id="0b4eb-118">Revisar o Guia de Colaboradores do Microsoft Docs</span><span class="sxs-lookup"><span data-stu-id="0b4eb-118">Review the Microsoft Docs Contributors Guide</span></span>

<span data-ttu-id="0b4eb-119">O guia de colaboradores fornece orientações para criar, publicar e atualizar conteúdo técnico na **plataforma Microsoft Docs.**</span><span class="sxs-lookup"><span data-stu-id="0b4eb-119">The contributors guide provides direction to create, publish, and update technical content on the **Microsoft Docs** platform.</span></span> 

## <a name="microsoft-writing-style-and-content-guides"></a><span data-ttu-id="0b4eb-120">Guias de escrita, estilo e conteúdo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="0b4eb-120">Microsoft Writing, Style, and Content Guides</span></span>

* <span data-ttu-id="0b4eb-121">**[Guia de Estilo de](/style-guide/welcome)** Escrita da Microsoft : o Guia de Estilo de Escrita da Microsoft é um recurso abrangente para escrita técnica e reflete a abordagem moderna da Microsoft para voz e estilo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-121">**[Microsoft Writing Style Guide](/style-guide/welcome)**: Microsoft Writing Style Guide is a comprehensive resource for technical writing and reflects Microsoft's modern approach to voice and style.</span></span> <span data-ttu-id="0b4eb-122">Para fazer referência fácil, adicione este guia online ao menu **Favoritos do** navegador.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-122">For easy reference, add this online guide to your browser's **Favorites** menu.</span></span>

* <span data-ttu-id="0b4eb-123">**[Escrevendo conteúdo de desenvolvedor](/style-guide/developer-content/)**: Teams conteúdo específico é destinado a um público desenvolvedor com uma compreensão fundamental dos conceitos e processos de programação.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-123">**[Writing developer content](/style-guide/developer-content/)**: Teams specific content is aimed at a developer audience with a fundamental understanding of programming concepts and processes.</span></span> <span data-ttu-id="0b4eb-124">É importante que você forneça informações claras e tecnicamente precisas de maneira atraente, mantendo o tom e o estilo da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-124">It is important that you must provide clear, technically accurate information in a compelling manner while maintaining Microsoft's tone and style.</span></span>

* <span data-ttu-id="0b4eb-125">**[Escrevendo instruções passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)** a passo: Experiências aplicadas e interativas são uma ótima maneira de os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-125">**[Writing step-by-step instructions](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: Applied and interactive experiences are a great way for developers to learn about Microsoft products and technologies.</span></span> <span data-ttu-id="0b4eb-126">Apresentar procedimentos complexos ou simples em um formato progressivo é natural e amigável.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-126">Presenting complex or simple procedures in a progressive format is natural and user friendly.</span></span>

## <a name="markdown-reference"></a><span data-ttu-id="0b4eb-127">Referência markdown</span><span class="sxs-lookup"><span data-stu-id="0b4eb-127">MarkDown reference</span></span>

<span data-ttu-id="0b4eb-128">**As páginas do Microsoft Docs** são escritas **em sintaxe MarkDown** e analisados por meio de um [mecanismo Markdig.](https://github.com/lunet-io/markdig)</span><span class="sxs-lookup"><span data-stu-id="0b4eb-128">**Microsoft Docs** pages are written in **MarkDown** syntax and parsed through a [Markdig](https://github.com/lunet-io/markdig) engine.</span></span> <span data-ttu-id="0b4eb-129">Para obter mais informações sobre marcas específicas e convenções de formatação, consulte [Docs Markdown reference](/contribute/markdown-reference).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-129">For more information on specific tags and formatting conventions, see [Docs Markdown reference](/contribute/markdown-reference).</span></span>

## <a name="file-paths"></a><span data-ttu-id="0b4eb-130">Caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="0b4eb-130">File Paths</span></span>

<span data-ttu-id="0b4eb-131">Ao usar caminhos relativos e criar links para outros conjuntos de documentos, é importante definir um caminho de arquivo válido para hiperlinks em sua documentação.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-131">When using relative paths and creating links to other docsets, it is important to set a valid file path for hyperlinks in your documentation.</span></span> <span data-ttu-id="0b4eb-132">Sua com build só GitHub se o caminho do arquivo estiver correto ou válido.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-132">Your build succeeds on GitHub only if the file path is correct or valid.</span></span>
 
<span data-ttu-id="0b4eb-133">Para obter mais informações sobre hiperlinks e caminhos de arquivo, [consulte usar links na documentação](/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-133">For more information on hyperlinks and file paths, see [use links in documentation](/contribute/how-to-write-links).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b4eb-134">Para fazer referência a um artigo que **faz parte do** Teams de plataforma:</span><span class="sxs-lookup"><span data-stu-id="0b4eb-134">To reference an article that is **part of** the Teams platform docset:</span></span><br>
> <span data-ttu-id="0b4eb-135">&emsp;&#x2714; Use um caminho relativo sem uma barra à frente.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-135">&emsp;&#x2714; Use a relative path without a leading forward slash.</span></span><br>
> <span data-ttu-id="0b4eb-136">&emsp;&#x2714; Incluir a extensão de arquivo Markdown.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-136">&emsp;&#x2714; Include the Markdown file extension.</span></span><br>
><span data-ttu-id="0b4eb-137">Ex: **diretório pai/diretório/caminho para** article.md —> criando um aplicativo para [Microsoft Teams](../concepts/building-an-app.md)</span><span class="sxs-lookup"><span data-stu-id="0b4eb-137">Ex:  **parent directory/directory/path-to-article.md** —> [Building an app for Microsoft Teams](../concepts/building-an-app.md)</span></span> <br><br>
> <span data-ttu-id="0b4eb-138">Para fazer referência a um artigo da biblioteca do Microsoft Docs **que não faz** parte do Teams de plataforma:</span><span class="sxs-lookup"><span data-stu-id="0b4eb-138">To reference a Microsoft Docs library article that **is not part of** the Teams platform docset:</span></span><br>
> <span data-ttu-id="0b4eb-139">&emsp;&#x2714; Use um caminho relativo que comece com uma barra para frente.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-139">&emsp;&#x2714; Use a relative path that begins with a forward slash.</span></span><br>
> <span data-ttu-id="0b4eb-140">&emsp;&#x2714; Não inclua a extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-140">&emsp;&#x2714; Do not include the file extension.</span></span> <br> <span data-ttu-id="0b4eb-141">Ex: **/docset/address-to-file-location** —> [Use](/graph/api/resources/teams-api-overview) a API do Microsoft Graph para trabalhar com Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0b4eb-141">Ex:  **/docset/address-to-file-location** —> [Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)</span></span><br><br>
> <span data-ttu-id="0b4eb-142">Para fazer referência a uma página fora da biblioteca do Microsoft Docs, como GitHub, use o caminho de `https` arquivo completo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-142">To reference a page outside of the Microsoft Docs library, such as GitHub, use the full `https` file path.</span></span><br>

## <a name="code-samples-and-snippets"></a><span data-ttu-id="0b4eb-143">Exemplos de código e trechos de código</span><span class="sxs-lookup"><span data-stu-id="0b4eb-143">Code Samples and Snippets</span></span>

<span data-ttu-id="0b4eb-144">Exemplos de código desempenham uma função importante para usar APIs e SDKs de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-144">Code samples play an important role to use APIs and SDKs effectively.</span></span> <span data-ttu-id="0b4eb-145">Exemplos de código bem apresentados podem comunicar como as coisas funcionam mais claramente do que texto descritivo e informações instrucionais sozinhos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-145">Well presented code samples can communicate how things work more clearly than descriptive text and instructional information alone.</span></span> <span data-ttu-id="0b4eb-146">Seus exemplos de código devem ser precisos, concisos, bem documentados e amigáveis ao leitor.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-146">Your code samples must be accurate, concise, well documented, and reader friendly.</span></span> <span data-ttu-id="0b4eb-147">O código fácil de ler deve ser fácil de entender, testar, depurar, manter, modificar e estender.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-147">Code that is easy to read must be easy to understand, test, debug, maintain, modify, and extend.</span></span> <span data-ttu-id="0b4eb-148">Para obter mais informações, [consulte como incluir código em documentos](/contribute/code-in-docs).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-148">For more information, see [how to include code in docs](/contribute/code-in-docs).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b4eb-149">Também consulte</span><span class="sxs-lookup"><span data-stu-id="0b4eb-149">See also</span></span>

* [<span data-ttu-id="0b4eb-150">Microsoft Docs</span><span class="sxs-lookup"><span data-stu-id="0b4eb-150">Microsoft Docs</span></span>](/)
* [<span data-ttu-id="0b4eb-151">guia colaboradores</span><span class="sxs-lookup"><span data-stu-id="0b4eb-151">contributors guide</span></span>](/contribute)
* [<span data-ttu-id="0b4eb-152">Estilo docs e início rápido de voz</span><span class="sxs-lookup"><span data-stu-id="0b4eb-152">Docs style and voice quick start</span></span>](/contribute/style-quick-start)
* [<span data-ttu-id="0b4eb-153">Borda de corte : Capacidade de leitura do código-fonte Dicas</span><span class="sxs-lookup"><span data-stu-id="0b4eb-153">Cutting Edge : Source Code Readability Tips</span></span>](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [<span data-ttu-id="0b4eb-154">Teams documentação</span><span class="sxs-lookup"><span data-stu-id="0b4eb-154">Teams documentation</span></span>](/microsoftteams/platform/overview)
* [<span data-ttu-id="0b4eb-155">GitHub</span><span class="sxs-lookup"><span data-stu-id="0b4eb-155">GitHub</span></span>](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)


## <a name="next-step"></a><span data-ttu-id="0b4eb-156">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0b4eb-156">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b4eb-157">Obter atualizações do Microsoft Docs e os comunicados mais recentes</span><span class="sxs-lookup"><span data-stu-id="0b4eb-157">Get Microsoft Docs updates and the latest announcements</span></span>](/teamblog)
