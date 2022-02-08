---
title: Contribuir com a documentação do Teams
description: etapas para criar e publicar Teams documentação
author: surbhigupta
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: contributor-guide
---

# <a name="contribute-to-teams-documentation"></a>Contribuir com a documentação do Teams

Teams documentação faz parte da biblioteca de documentação técnica do **Microsoft Docs**. O conteúdo é organizado em grupos chamados docsets, cada um representando um grupo de documentos relacionados gerenciados como uma única entidade. Os artigos no mesmo docset têm a mesma extensão de caminho de **URL após docs.microsoft.com**. Por exemplo, `/docs.microsoft.com/microsoftteams/...` é o início do caminho do arquivo Teams docset. Teams artigos são escritos na sintaxe Markdown e hospedados em GitHub.

## <a name="set-up-your-workspace"></a>Configurar seu espaço de trabalho

> [!div class="checklist"]
>
> * Instale [o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
> * Instalar [Microsoft Visual Studio Código](https://code.visualstudio.com/) (VS Code).
> * Instale [o Pacote de Autoria de Documentos](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) diretamente do VS Code Marketplace.
<br>&emsp;&emsp; ou

> [!div class="checklist"]
>
> * Instalar dentro VS Code:

   1. Selecione o **ícone Extensões** na barra de atividades lateral ou use o comando **Exibir => Extensões** ou Ctrl+Shift+X e, pesquise o **Microsoft Docs Authoring Pack**.
   1. Selecionar **Instalar**.
   1. Após a instalação, **o botão Instalar** muda para **o botão Gerenciar** engrenagem.

## <a name="review-the-microsoft-docs-contributors-guide"></a>Revisar o Guia de Colaboradores do Microsoft Docs

O guia de colaboradores fornece orientações para criar, publicar e atualizar conteúdo técnico na **plataforma Microsoft Docs** . 

## <a name="microsoft-writing-style-and-content-guides"></a>Guias de escrita, estilo e conteúdo da Microsoft

* **[Guia de Estilo de](/style-guide/welcome)** Escrita da Microsoft: o Guia de Estilo de Escrita da Microsoft é um recurso abrangente para escrita técnica e reflete a abordagem moderna da Microsoft para voz e estilo. Para fazer referência fácil, adicione este guia online ao menu **Favoritos do** navegador.

* **[Escrevendo conteúdo de desenvolvedor](/style-guide/developer-content/)**: Teams conteúdo específico é destinado a um público desenvolvedor com uma compreensão fundamental dos conceitos e processos de programação. É importante que você forneça informações claras e tecnicamente precisas de maneira atraente, mantendo o tom e o estilo da Microsoft.

* **[Escrevendo instruções passo a passo](/style-guide/procedures-instructions/writing-step-by-step-instructions)**: Experiências aplicadas e interativas são uma ótima maneira de os desenvolvedores aprenderem sobre produtos e tecnologias da Microsoft. Apresentar procedimentos complexos ou simples em um formato progressivo é natural e amigável.

## <a name="markdown-reference"></a>Referência markdown

**As páginas do Microsoft Docs** são escritas **em sintaxe MarkDown** e analisados por meio de um [mecanismo Markdig](https://github.com/lunet-io/markdig) . Para obter mais informações sobre marcas específicas e convenções de formatação, consulte [Referência docs Markdown](/contribute/markdown-reference).

## <a name="file-paths"></a>Caminhos de arquivo

Ao usar caminhos relativos e criar links para outros conjuntos de documentos, é importante definir um caminho de arquivo válido para hiperlinks em sua documentação. Sua com build só GitHub se o caminho do arquivo estiver correto ou válido.
 
Para obter mais informações sobre hiperlinks e caminhos de arquivo, [consulte usar links na documentação](/contribute/how-to-write-links).

> [!IMPORTANT]
> Para fazer referência a um artigo que **faz parte do** docset Teams plataforma:<br>
> &emsp;&#x2714; Use um caminho relativo sem uma barra à frente.<br>
> &emsp;&#x2714; Incluir a extensão de arquivo Markdown.<br>
>Ex: **diretório pai/diretório/caminho para** article.md —> [criando um aplicativo para Microsoft Teams](../concepts/building-an-app.md) <br><br>
> Para fazer referência a um artigo da biblioteca do Microsoft Docs **que não faz parte do** docset Teams plataforma:<br>
> &emsp;&#x2714; Use um caminho relativo que comece com uma barra para frente.<br>
> &emsp;&#x2714; Não inclua a extensão de arquivo. <br> Ex: **/docset/address-to-file-location** —> [Use a API do Microsoft Graph para trabalhar com Microsoft Teams](/graph/api/resources/teams-api-overview)<br><br>
> Para fazer referência a uma página fora da biblioteca do Microsoft Docs, como GitHub, use o caminho de arquivo `https` completo.<br>

## <a name="code-samples-and-snippets"></a>Exemplos de código e trechos de código

Exemplos de código desempenham uma função importante para usar APIs e SDKs de forma eficaz. Exemplos de código bem apresentados podem comunicar como as coisas funcionam mais claramente do que texto descritivo e informações instrucionais sozinhos. Seus exemplos de código devem ser precisos, concisos, bem documentados e amigáveis ao leitor. O código fácil de ler deve ser fácil de entender, testar, depurar, manter, modificar e estender. Para obter mais informações, [consulte como incluir código em documentos](/contribute/code-in-docs).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obter atualizações do Microsoft Docs e os comunicados mais recentes](/teamblog)

## <a name="see-also"></a>Confira também

* [Microsoft Docs](/)
* [Guia colaboradores](/contribute)
* [Estilo docs e início rápido de voz](/contribute/style-quick-start)
* [Borda de ponta: dicas de capacidade de leitura do código-fonte](/archive/msdn-magazine/2014/october/cutting-edge-source-code-readability-tips)
* [Teams documentação](/microsoftteams/platform/overview)
* [GitHub](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform)
