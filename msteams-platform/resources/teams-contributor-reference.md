---
title: Contribuir com a documentação do Teams
description: Conheça as etapas para criar e publicar Teams documentação
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
ms.openlocfilehash: 165f5df18395d329aa2f383d2f07e6f7ff3afdcf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143078"
---
# <a name="contribute-to-teams-documentation"></a>Contribuir com a documentação do Teams

A documentação do Teams faz parte da documentação técnica de **Microsoft Docs**. O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade. Os artigos no mesmo docset têm a mesma extensão de caminho de URL após **docs.microsoft.com**. Por exemplo, `/docs.microsoft.com/microsoftteams/...` é o início do caminho do arquivo do conjunto de documentos do Teams. Os artigos do Teams são escritos na sintaxe de Markdown e hospedados no GitHub.

## <a name="set-up-your-workspace"></a>Configurar seu espaço de trabalho

> [!div class="checklist"]
>
> * Instalar [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instalar [Microsoft Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Instalar [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente do VS Code Marketplace.<br>&emsp;&emsp; ou
[!div class="checklist"]
>
> * Instalar dentro VS Code:

   1. Selecione o **ícone Extensões** na barra de atividades lateral ou use o comando **Exibir => Extensões** ou Ctrl+Shift+X e procure por **Microsoft Docs Authoring Pack**.
   1. Selecionar **Instalar**.
   1. Após a instalação, o **Instalar** muda para o botão de engrenagem **Gerenciar**.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Examinar o guia Microsoft Docs colaboradores

O guia de colaboradores fornece orientação para criar, publicar e atualizar conteúdo técnico na plataforma **Microsoft Docs**.

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de Estilo de Escrita da Microsoft](/style-guide/welcome)**: o Guia de Estilo de Escrita da Microsoft é um recurso abrangente para escrita técnica e reflete a abordagem moderna da Microsoft para voz e estilo. Para facilitar a referência, adicione este guia online ao menu **Favoritos** do navegador.

* **[Escrever conteúdo do desenvolvedor](/style-guide/developer-content/)**: o conteúdo específico do Teams é destinado a um público-alvo de desenvolvedores com uma compreensão fundamental dos conceitos e processos de programação. É importante que você forneça informações claras e tecnicamente precisas de maneira atraente, mantendo o tom e o estilo da Microsoft.

* **[Escrevendo instruções passo a passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: experiências interativas e aplicadas são uma ótima maneira para os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. Apresentar procedimentos complexos ou simples em um formato progressivo é natural e amigável.

## <a name="markdown-reference"></a>Referência de MarkDown

As páginas do **Microsoft Docs** são escritas na sintaxe **MarkDown** e analisadas por meio de um mecanismo [Markdig](https://github.com/lunet-io/markdig). Para obter mais informações sobre tags específicas e convenções de formatação, consulte a [referência do Docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Caminhos de Arquivo

Ao usar caminhos relativos e criar links para outros conjuntos de documentos, é importante definir um caminho de arquivo válido para hiperlinks em sua documentação. Seu build será bem-sucedido no GitHub somente se o caminho do arquivo estiver correto ou válido.

Para obter mais informações sobre hiperlinks e caminhos de arquivo, consulte [use links na documentação](/contribute/how-to-write-links).

> [!IMPORTANT]
> Para fazer referência a um artigo que faz **parte do** conjunto de documentos da plataforma Teams:<br>
> &emsp;✔ Use um caminho relativo sem uma barra invertida.<br>
> &emsp;✔ Inclua a extensão de arquivo Markdown.<br>
>Ex:  **parent directory/directory/path-to-article.md** —> [Compilando um aplicativo para o Microsoft Teams](../concepts/building-an-app.md) <br><br>
> Para referenciar um Microsoft Docs de biblioteca que **não faz parte do** conjunto de documentos da plataforma Teams:<br>
> &emsp;✔ Use um caminho relativo que comece com uma barra.<br>&emsp;✔ Não inclua a extensão de arquivo.<br>
> Ex:  **/docset/address-to-file-location** —> [Use a API do Microsoft Graph para trabalhar com o Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Para fazer referência a uma página fora da biblioteca Microsoft Docs, como o GitHub, use o caminho completo do arquivo `https`.<br>

## <a name="code-samples-and-snippets"></a>Exemplos de código e snippets

Os exemplos de código desempenham uma função importante para usar APIs e SDKs com eficiência. Exemplos de código bem apresentados podem comunicar como as coisas funcionam mais claramente do que apenas texto descritivo e informações instrucionais. Seus exemplos de código devem ser precisos, concisos, bem documentados e amigáveis ao leitor. O código que é fácil de ler deve ser fácil de entender, testar, depurar, manter, modificar e estender. Para obter mais informações, consulte [como incluir código em documentos](/contribute/code-in-docs).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obtenha atualizações do Microsoft Docs e os anúncios mais recentes](/teamblog)

## <a name="see-also"></a>Confira também

* [Microsoft Docs](/)
* [Guia de Colaboradores](/contribute)
* [Estilo de documentos e início rápido de voz](/contribute/style-quick-start)
* [De ponta: dicas de legibilidade do código-fonte](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Documentação do Teams](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
