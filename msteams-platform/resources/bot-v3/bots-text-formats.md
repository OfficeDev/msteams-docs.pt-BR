---
title: Formatação de texto com suporte em conversas
description: Descreve o suporte à formatação de texto em conversas de bot
keywords: mensagens de conversas de bots
ms.date: 03/29/2018
ms.openlocfilehash: cc6cba697a1f6907bfb13b94740e7bf9e92596da
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672483"
---
# <a name="formatting-bot-messages"></a>Formatando mensagens de bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Você pode definir a propriedade [`TextFormat`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) opcional para controlar como o conteúdo de texto da mensagem é renderizado.

O Microsoft Teams suporta as seguintes opções de formatação:

| Valor TextFormat | Descrição |
| --- | --- |
| comuns | O texto deve ser tratado como um texto bruto sem formatação aplicada |
| redução | O texto deve ser tratado como formatação de redução e renderizado no canal, conforme apropriado; consulte [Formatando o conteúdo de texto](#formatting-text-content) para estilos suportados |
| XML | O texto é marcação XML simples; consulte [Formatando o conteúdo de texto](#formatting-text-content) para estilos suportados |

## <a name="formatting-text-content"></a>Formatando conteúdo de texto

O Microsoft Teams oferece suporte a um subconjunto de marcas de formatação de redução e XML (HTML).

Atualmente, as seguintes limitações se aplicam:

* As mensagens somente texto não oferecem suporte à formatação de tabela

Para obter informações sobre formatação em cartões, consulte [referência de cartões de equipes](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Suporte a várias plataformas

Para garantir que a formatação funcione em todas as plataformas compatíveis com o Microsoft Teams, lembre-se de que alguns estilos não são suportados atualmente em todas as plataformas.

| Estilo                     | Mensagens somente de texto | Cartões (somente XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| cabeçalho (níveis 1&ndash;3) | ✖                  | ✔                |
| tachado             | ✖                  | ✔                |
| régua horizontal           | ✖                  | ✖                |
| lista não ordenada            | ✖                  | ✔                |
| lista ordenada              | ✖                  | ✔                |
| texto pré-formatado         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| hyperlink                 | ✔                  | ✔                |
| link de imagem                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

#### <a name="text-only-messages"></a>Mensagens somente de texto

| Estilo                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| cabeçalho (níveis 1&ndash;3) | ✖       | ✖   | ✖       |
| tachado             | ✔       | ✔   | ✖       |
| régua horizontal           | ✖       | ✖   | ✖       |
| lista não ordenada            | ✔       | ✖   | ✖       |
| lista ordenada              | ✔       | ✖   | ✖       |
| texto pré-formatado         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| hyperlink                 | ✔       | ✔   | ✔       |
| link de imagem                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Exemplos de formatação de texto

| Estilo | Exemplo | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| cabeçalho (níveis 1&ndash;3) | **Text** | `### Text` | `<h3>Text</h3>` |
| tachado | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| hyperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
