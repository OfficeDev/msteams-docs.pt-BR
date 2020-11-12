---
title: Contribuindo para a documentação do Microsoft Teams
description: etapas para criar e publicar a documentação do Microsoft Teams
author: laujan
ms.author: lajanuar
ms.topic: contributor-guide
ms.openlocfilehash: 80aaf7795a226c0437140fe72e1d74b07fa66775
ms.sourcegitcommit: f6029c8ff0c5315613a3efcd86777aa4cede39e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48995013"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Contribuindo para a documentação do Microsoft Teams

A [documentação do teams](/microsoftteams/platform/overview) é parte da biblioteca de documentação técnica do [Microsoft docs](https://docs.microsoft.com/) . O conteúdo é organizado em grupos chamados docsets, cada um deles representando um grupo de documentos relacionados gerenciados como uma entidade única. Os artigos no mesmo docset têm a mesma extensão de caminho de URL após *docs <span></span> . Microsoft.com*.  Por exemplo,  `/docs.microsoft.com/microsoftteams/...`   é o início do caminho de arquivo do teams docset. Os artigos do teams são escritos em sintaxe de  [redução](#markdown-reference) e hospedados no [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform).

## <a name="set-up-your-workspace"></a>Configurar seu espaço de trabalho

> [!div class="checklist"]
>
> * Instale o [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instale o [Visual Studio Code](https://code.visualstudio.com/) (vs Code).
> * Instalar o [pacote de criação de docs](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente a partir do vs Code Marketplace
<br>&emsp;&emsp; ou

> [!div class="checklist"]
>
> * Instalar de dentro do VS Code:

   1. Selecione o **ícone de extensões** na barra de atividades do lado ou use o comando **Exibir => Extensions** (Ctrl + Shift + X) e procure o *pacote de criação de docs* (Microsoft).
   1. Selecione o botão **instalar** .
   1. Depois que a instalação for concluída, o botão **instalar** mudará para o botão **gerenciar** engrenagem.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Analisar o guia de colaboradores de docs da Microsoft

O [guia contribuidores](/contribute) oferece orientações para criar, publicar e atualizar o conteúdo técnico no Microsoft/docs. *Confira também* o [estilo de docs e início rápido de voz](/contribute/style-quick-start) .

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de estilo de escrita da Microsoft](/style-guide/welcome)**. Considere adicionar este guia online ao menu **favoritos** do seu navegador. É um recurso abrangente para a escrita técnica de hoje e reflete a abordagem moderna da Microsoft para voz e estilo.

* **[Escrever o conteúdo do desenvolvedor](/style-guide/developer-content/)**. O conteúdo específico de equipes é direcionado a um público-alvo de desenvolvedor com uma compreensão fundamental de conceitos e processos de programação. É importante que você forneça informações claras, tecnicamente precisas, de forma atraente, mantendo o Tom e o estilo da Microsoft.

* **[Escrever instruções passo a passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)**. As experiências aplicadas e interativas são uma ótima maneira de os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. A apresentação de procedimentos complexos ou simples em um formato progressivo é natural e amigável.

## <a name="markdown-reference"></a>Referência de redução

 As páginas de docs da Microsoft são escritas em sintaxe de redução e analisadas por meio de um mecanismo do [Markdig](https://github.com/lunet-io/markdig) . *Confira* [referência de redução de docs](/contribute/markdown-reference) para marcas específicas e convenções de formatação.

## <a name="file-paths"></a>Caminhos de arquivo

A definição de um caminho de arquivo válido para hiperlinks na documentação pode ser um desafio, especialmente quando se usa caminhos relativos e cria links para outros docsets.  Sua compilação não terá êxito no GitHub se o caminho do arquivo estiver incorreto ou inválido.

Para obter mais informações sobre hiperlinks e caminhos de arquivo, *consulte* [use links na documentação](/contribute/how-to-write-links).

>[!IMPORTANT]
> Para fazer referência a um artigo que faz *parte da* plataforma de docset do Microsoft Teams:<br>
> &emsp;&#x2714; usar um caminho relativo sem uma barra de avanço à esquerda.<br>
> &emsp;&#x2714; incluir a extensão do arquivo de redução.<br>
>Ex:  **diretório pai/diretório/caminho-para-article. MD** — > `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> Para fazer referência a um <https://docs.microsoft.com/> artigo da biblioteca de docs da Microsoft () que *não faz parte da* plataforma do teams docset:<br>
> &emsp;&#x2714; use um caminho relativo que comece com uma barra.<br>
> &emsp;&#x2714; não inclua a extensão de arquivo. <br> Ex:  **/docset/address-to-file-location** — > `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`
>

## <a name="code-samples-and-snippets"></a>Exemplos de código e trechos

Exemplos de código desempenham um papel importante para ajudar os desenvolvedores a usarem APIs e SDKs com êxito. Exemplos de código bem apresentados podem comunicar como as coisas funcionam de forma mais clara do que o texto descritivo e informações instrutivas. Seus exemplos de código devem ser precisos, conciso, bem documentados e, mais importante, amigáveis para leitores. O código que é fácil de ler também é fácil de entender, testar, depurar, manter, modificar e estender. *Confira* [como incluir código em docs](/contribute/code-in-docs). Para obter dicas de legibilidade, *Confira também* [Cutting Edge: dicas de legibilidade do código-fonte](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Obter atualizações de documentos da Microsoft e os comunicados mais recentes](/teamblog)
