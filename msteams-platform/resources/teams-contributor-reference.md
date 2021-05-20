---
title: Contribuindo para a documentação Microsoft Teams
description: etapas para a criação e publicação Teams documentação
author: laujan
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: 52253bb096857e2cb883295c8ae6b58518506d9a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566226"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Contribuindo para a documentação Microsoft Teams

[Teams documentação](/microsoftteams/platform/overview) faz parte da biblioteca de documentação técnica do [Microsoft Docs.](https://docs.microsoft.com/) O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade. Os artigos no mesmo docset têm a mesma extensão de caminho de URL após *o docs <span></span> .microsoft.com*.  Por exemplo, `/docs.microsoft.com/microsoftteams/...` é o início do Teams o caminho do arquivo docset. Teams artigos são escritos na sintaxe [markdown](#markdown-reference) e hospedados em [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform).

## <a name="set-up-your-workspace"></a>Configure seu espaço de trabalho

> [!div class="checklist"]
>
> * Instale [o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instale [Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Instale [o Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente do VS Code Marketplace.
<br>&emsp;&emsp; ou

> [!div class="checklist"]
>
> * Instalação de dentro de VS Code:

   1. Selecione o **ícone Extensões** na barra de atividades laterais ou use o comando **Exibir => Extensões** (Ctrl+Shift+X) e pesquise pelo *Docs Authoring Pack* (Microsoft).
   1. Selecione o botão **Instalar.**
   1. Uma vez concluída a instalação, o botão **Instalar** será trocado para o botão **Gerenciar marchas.**

## <a name="review-the-microsoft-docs-contributors-guide"></a>Revise o Guia de Colaboradores do Microsoft Docs

O [guia de colaboradores](/contribute) oferece orientação para criar, publicar e atualizar conteúdo técnico na plataforma Microsoft Docs.

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de estilo de escrita da Microsoft](/style-guide/welcome)**. Considere adicionar este guia on-line ao menu **Favoritos** do seu navegador. É um recurso abrangente para a escrita técnica atual e reflete a abordagem moderna da Microsoft para voz e estilo.

* **[Escrevendo conteúdo do desenvolvedor](/style-guide/developer-content/)**. Teams conteúdo específico é voltado para um público desenvolvedor com uma compreensão fundamental dos conceitos e processos de programação. É importante que você forneça informações claras e tecnicamente precisas de forma convincente, mantendo o tom e o estilo da Microsoft.

* **[Escrevendo instruções passo a passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)**. Experiências aplicadas e interativas são uma ótima maneira de os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. Apresentar procedimentos complexos ou simples em formato progressivo é natural e fácil de usar.

## <a name="markdown-reference"></a>Referência MarkDown

 As páginas do Microsoft Docs são escritas na sintaxe markdown e analisadas através de um motor [Markdig.](https://github.com/lunet-io/markdig) Consulte *a* [referência do Docs Markdown](/contribute/markdown-reference) para tags específicas e convenções de formatação.

## <a name="file-paths"></a>Caminhos de arquivo

Definir um caminho de arquivo válido para hiperlinks em sua documentação pode ser um desafio, especialmente ao usar caminhos relativos e criar links para outros docsets.  Sua compilação não terá sucesso em GitHub se o caminho do arquivo estiver incorreto ou inválido.

Para obter mais informações sobre hiperlinks e caminhos de arquivos, consulte [Usar links na documentação](/contribute/how-to-write-links).

>[!IMPORTANT]
> Para fazer referência a um artigo que faz *parte do* Teams plataforma docset:<br>
> &emsp;&#x2714; Use um caminho relativo sem uma barra dianteira.<br>
> &emsp;&#x2714; Incluir a extensão do arquivo Markdown.<br>
>Ex:  **diretório/diretório/caminho para article.md** — > `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> Para fazer referência a um artigo da biblioteca do Microsoft Docs que *não faz parte do* docset da plataforma Teams:<br>
> &emsp;&#x2714; Use um caminho relativo que começa com uma barra para a frente.<br>
> &emsp;&#x2714; Não inclua a extensão do arquivo. <br> Ex:  **/docset/address-to-file-location** — > `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Para consultar uma página fora da biblioteca do Microsoft Docs, como GitHub, use o caminho completo do `https` arquivo.<br>

## <a name="code-samples-and-snippets"></a>Amostras de código e trechos

As amostras de código desempenham um papel importante para ajudar os desenvolvedores a usar com sucesso APIs e SDKs. Amostras de código bem apresentadas podem comunicar como as coisas funcionam mais claramente do que texto descritivo e informações instrucionais sozinhos. Suas amostras de código devem ser precisas, concisas, bem documentadas e, o mais importante, amigáveis aos leitores. Código fácil de ler também é fácil de entender, testar, depurar, manter, modificar e estender. Para obter mais informações, consulte [Como incluir código em documentos](/contribute/code-in-docs).

## <a name="see-also"></a>Confira também

* [Estilo docs e início rápido de voz](/contribute/style-quick-start)
* [Ponta: Dicas de Legibilidade do Código Fonte](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Receba as atualizações do Microsoft Docs e os últimos anúncios](/teamblog)
