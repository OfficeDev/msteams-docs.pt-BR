---
title: Contribuir com a documentação do Teams
description: Conheça as etapas para criar e publicar a documentação do Teams
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
ms.openlocfilehash: 4a0c522b5e9d4bcf99ee884de41b1d75846b004a
ms.sourcegitcommit: 377a4b712b50a211851aeecc1029414939945390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68044662"
---
# <a name="contribute-to-teams-documentation"></a>Contribuir com a documentação do Teams

A documentação do Teams faz parte da biblioteca **de documentação técnica do Microsoft Learn** . O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade. Os artigos no mesmo docset têm a mesma extensão de caminho de URL após `learn.microsoft.com`. Por exemplo, `/learn.microsoft.com/microsoftteams/...` é o início do caminho do arquivo do conjunto de documentos do Teams. Os artigos do Teams são escritos na sintaxe de Markdown e hospedados no GitHub.

## <a name="set-up-your-workspace"></a>Configurar seu espaço de trabalho

> [!div class="checklist"]
>
> * Instalar [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instalar [Microsoft Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Install [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) directly from the VS Code Marketplace.
<br>&emsp;&emsp; ou
> [!div class="checklist"]
>
> * Instalar dentro VS Code:

   1. Selecione o **ícone Extensões** na barra de atividades lateral ou use o comando **View => Extensions** ou Ctrl+Shift+X e pesquise **o Pacote de Criação do Docs**.
   1. Selecionar **Instalar**.
   1. Após a instalação, o **Instalar** muda para o botão de engrenagem **Gerenciar**.

## <a name="review-the-microsoft-docs-contributor-guide"></a>Examinar o guia Microsoft Docs colaborador

O guia de colaboradores fornece a direção para criar, publicar e atualizar conteúdo técnico na **plataforma Microsoft Learn** .

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de Estilo de Escrita da Microsoft](/style-guide/welcome)**: o Guia de Estilo de Escrita da Microsoft é um recurso abrangente para escrita técnica e reflete a abordagem moderna da Microsoft para voz e estilo. Para facilitar a referência, adicione este guia online ao menu **Favoritos** do navegador.

* **[Escrever conteúdo do desenvolvedor](/style-guide/developer-content/)**: o conteúdo específico do Teams é destinado a um público-alvo de desenvolvedores com uma compreensão fundamental dos conceitos e processos de programação. É importante que você forneça informações claras e tecnicamente precisas de maneira atraente, mantendo o tom e o estilo da Microsoft.

* **[Escrevendo instruções passo a passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: experiências interativas e aplicadas são uma ótima maneira para os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. Apresentar procedimentos complexos ou simples em um formato progressivo é natural e amigável.

## <a name="markdown-reference"></a>Referência de MarkDown

**As páginas do Microsoft Learn** são escritas **em sintaxe MarkDown** e analisadas por meio de um [mecanismo markdig](https://github.com/lunet-io/markdig) . Para obter mais informações sobre tags específicas e convenções de formatação, consulte a [referência do Docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Caminhos de Arquivo

Ao usar caminhos relativos e criar links para outros conjuntos de documentos, é importante definir um caminho de arquivo válido para hiperlinks em sua documentação. Seu build será bem-sucedido no GitHub somente se o caminho do arquivo estiver correto ou válido.

Para obter mais informações sobre hiperlinks e caminhos de arquivo, consulte [use links na documentação](/contribute/how-to-write-links).

> [!IMPORTANT]
> Para fazer referência a um artigo que faz **parte do** conjunto de documentos da plataforma Teams:<br>
> &emsp;✔ Use um caminho relativo sem uma barra invertida.<br>
> &emsp;✔ Inclua a extensão de arquivo Markdown.<br>
>Ex:  **parent directory/directory/path-to-article.md** —> [Compilando um aplicativo para o Microsoft Teams](../concepts/building-an-app.md) <br><br>
> Para fazer referência a um artigo do Microsoft Learn **que não faz parte do docset** da plataforma Teams:<br>
> &emsp;✔ Use um caminho relativo que comece com uma barra.<br>
> &emsp;&#x2714; Do not include the file extension. <br>
> Ex:  **/docset/address-to-file-location** —> [Use a API do Microsoft Graph para trabalhar com o Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Para fazer referência a uma página fora do Microsoft Learn, como o GitHub, use o caminho completo `https` do arquivo.<br>

## <a name="code-samples-and-snippets"></a>Exemplos de código e snippets

Os exemplos de código desempenham uma função importante para usar APIs e SDKs com eficiência. Exemplos de código bem apresentados podem comunicar como as coisas funcionam mais claramente do que apenas texto descritivo e informações instrucionais. Seus exemplos de código devem ser precisos, concisos, bem documentados e amigáveis ao leitor. O código que é fácil de ler deve ser fácil de entender, testar, depurar, manter, modificar e estender. Para obter mais informações, [consulte como incluir código em um artigo](/contribute/code-in-docs).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obter as atualizações do Microsoft Learn e os comunicados mais recentes](/teamblog)

## <a name="see-also"></a>Confira também

* [Microsoft Learn](/)
* [Guia do colaborador da documentação do Microsoft Learn](/contribute)
* [Início rápido de estilo e voz do Microsoft Learn](/contribute/style-quick-start)
* [De ponta: dicas de legibilidade do código-fonte](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Documentação do Teams](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
