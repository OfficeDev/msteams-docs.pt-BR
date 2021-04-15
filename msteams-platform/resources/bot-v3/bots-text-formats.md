---
title: Formatação de texto com suporte em conversas
description: Descreve o suporte à formatação de texto em conversas de bot
keywords: bots mensagens de conversas
ms.topic: how-to
ms.date: 03/29/2018
ms.openlocfilehash: d8cb4ffd18871737ed4a64443800938f424910c9
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696056"
---
# <a name="formatting-bot-messages"></a>Formatar mensagens de bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Você pode definir a propriedade opcional para controlar como o conteúdo de texto da mensagem [`TextFormat`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) é renderizado.

O Microsoft Teams dá suporte às seguintes opções de formatação:

| Valor TextFormat | Descrição |
| --- | --- |
| plain | O texto deve ser tratado como texto bruto sem formatação aplicada. |
| Markdown | O texto deve ser tratado como formatação markdown e renderizado no canal conforme apropriado; consulte [Formatando conteúdo de texto](#formatting-text-content) para estilos com suporte |
| xml | O texto é uma marcação XML simples; consulte [Formatando conteúdo de texto](#formatting-text-content) para estilos com suporte |

## <a name="formatting-text-content"></a>Formatação de conteúdo de texto

O Microsoft Teams dá suporte a um subconjunto de marcas de formatação Markdown e XML (HTML).

Atualmente, as seguintes limitações se aplicam:

* Mensagens somente texto não suportam formatação de tabela

Para obter informações sobre formatação em cartões, consulte a [Referência de Cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Suporte entre plataformas

Para garantir que sua formatação funcione em todas as plataformas com suporte do Microsoft Teams, esteja ciente de que alguns estilos atualmente não têm suporte em todas as plataformas.

| Style                     | Mensagens somente texto | Cartões (somente XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| header (níveis 1 &ndash; 3) | ✖                  | ✔                |
| strikethrough             | ✖                  | ✔                |
| regra horizontal           | ✖                  | ✖                |
| lista semordenagem            | ✖                  | ✔                |
| lista ordenada              | ✖                  | ✔                |
| texto pré-formatado         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| hiperlink                 | ✔                  | ✔                |
| link de imagem                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

#### <a name="text-only-messages"></a>Mensagens somente texto

| Style                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| header (níveis 1 &ndash; 3) | ✖       | ✖   | ✖       |
| strikethrough             | ✔       | ✔   | ✖       |
| regra horizontal           | ✖       | ✖   | ✖       |
| lista semordenagem            | ✔       | ✖   | ✖       |
| lista ordenada              | ✔       | ✖   | ✖       |
| texto pré-formatado         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| hiperlink                 | ✔       | ✔   | ✔       |
| link de imagem                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Exemplos de formatação de texto

| Style | Exemplo | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| header (níveis 1 &ndash; 3) | **Text** | `### Text` | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| lista semordenagem | <ul><li>texto</li><li>texto</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
