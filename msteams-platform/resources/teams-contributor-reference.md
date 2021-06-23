---
title: Contribuir para Microsoft Teams documentação
description: etapas para criar e publicar Teams documentação
author: surbhigupta
ms.author: lajanuar
localization_priority: Normal
ms.topic: contributor-guide
ms.openlocfilehash: 33296219b9d42b2ca26eb3c44df5c6429f5259ce
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069159"
---
# <a name="contributing-to-microsoft-teams-documentation"></a>Contribuir para Microsoft Teams documentação

[Teams documentação](/microsoftteams/platform/overview) faz parte da biblioteca de documentação técnica do [Microsoft Docs.](https://docs.microsoft.com) O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade. Os artigos no mesmo docset têm a mesma extensão de caminho de URL após *os documentos <span></span> .microsoft.com*.  Por exemplo, `/docs.microsoft.com/microsoftteams/...` é o início do caminho do arquivo Teams docset. Teams artigos são escritos na [sintaxe MarkDown](#markdown-reference) e hospedados [em GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform).

## <a name="set-up-your-workspace"></a>Configurar seu espaço de trabalho

> [!div class="checklist"]
>
> * Instalar [o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instalar [Visual Studio Code](https://code.visualstudio.com/) (VS Code).
> * Instale [o Pacote de Autoria de Documentos](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente do VS Code Marketplace.
<br>&emsp;&emsp; ou

> [!div class="checklist"]
>
> * Instalar de dentro VS Code:

   1. Selecione o **ícone Extensões** na barra de atividades lateral ou use o comando **Exibir => Extensões** (Ctrl+Shift+X) e procure o *Pacote* de Autoria de Documentos (Microsoft).
   1. Selecione o **botão Instalar.**
   1. Depois que a instalação for concluída, **o botão Instalar** mudará para o botão **Gerenciar** engrenagem.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Revisar o Guia de Colaboradores do Microsoft Docs

O [guia de colaboradores](/contribute) oferece orientações para a criação, publicação e atualização de conteúdo técnico na plataforma Microsoft Docs.

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de Estilo de Escrita da Microsoft](/style-guide/welcome)**. Considere adicionar este guia online ao menu **Favoritos do** navegador. É um recurso abrangente para a escrita técnica de hoje e reflete a abordagem moderna da Microsoft para voz e estilo.

* **[Escrevendo conteúdo do desenvolvedor](/style-guide/developer-content/)**. Teams conteúdo específico é destinado a um público desenvolvedor com uma compreensão fundamental dos conceitos e processos de programação. É importante que você forneça informações claras e tecnicamente precisas de maneira atraente, mantendo o tom e o estilo da Microsoft.

* **[Escrevendo instruções passo a passo.](/style-guide/procedures-instructions/writing-step-by-step-instructions)** Experiências aplicadas e interativas são uma ótima maneira para os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. Apresentar procedimentos complexos ou simples em um formato progressivo é natural e amigável.

## <a name="markdown-reference"></a>Referência markdown

 As páginas do Microsoft Docs são escritas em sintaxe MarkDown e analisados por meio de um [mecanismo Markdig.](https://github.com/lunet-io/markdig) Consulte *Referência* [de Marcação de Documentos para](/contribute/markdown-reference) marcas específicas e convenções de formatação.

## <a name="file-paths"></a>Caminhos de arquivo

Definir um caminho de arquivo válido para hiperlinks em sua documentação pode ser um desafio, especialmente ao usar caminhos relativos e criar links para outros conjuntos de documentos.  Sua com build não terá êxito na GitHub se o caminho do arquivo estiver incorreto ou inválido.

Para obter mais informações sobre hiperlinks e caminhos de arquivo, [consulte Usar links na documentação](/contribute/how-to-write-links).

>[!IMPORTANT]
> Para fazer referência a um artigo que *faz parte do* Teams de plataforma:<br>
> &emsp;&#x2714; Use um caminho relativo sem uma barra à frente.<br>
> &emsp;&#x2714; Incluir a extensão de arquivo Markdown.<br>
>Ex:  **diretório pai/diretório/caminho para article.md** —> `[Building an app for Microsoft Teams](../concepts/building-an-app.md)` <br><br>
> Para fazer referência a um artigo da biblioteca do Microsoft Docs *que não faz* parte do Teams de plataforma:<br>
> &emsp;&#x2714; Use um caminho relativo que comece com uma barra para frente.<br>
> &emsp;&#x2714; Não inclua a extensão de arquivo. <br> Ex:  **/docset/address-to-file-location** — > `[Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview)`<br><br>
> Para fazer referência a uma página fora da biblioteca do Microsoft Docs, como GitHub, use o caminho de `https` arquivo completo.<br>

## <a name="code-samples-and-snippets"></a>Exemplos de código e trechos de código

Os exemplos de código desempenham uma função importante para ajudar os desenvolvedores a usar apIs e SDKs com êxito. Exemplos de código bem apresentados podem comunicar como as coisas funcionam mais claramente do que texto descritivo e informações instrucionais sozinhos. Seus exemplos de código devem ser precisos, concisos, bem documentados e, o mais importante, amigáveis ao leitor. O código fácil de ler também é fácil de entender, testar, depurar, manter, modificar e estender. Para obter mais informações, [consulte Como incluir código em documentos](/contribute/code-in-docs).

## <a name="see-also"></a>Confira também

* [Estilo docs e início rápido de voz](/contribute/style-quick-start)
* [Borda de corte : Capacidade de leitura do código-fonte Dicas](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips).

> [!div class="nextstepaction"]
> [Obter atualizações do Microsoft Docs e os comunicados mais recentes](/teamblog)
