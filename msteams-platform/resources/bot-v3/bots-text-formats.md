---
title: Formatação de texto suportada em conversas
description: Descreve o suporte de formatação de texto em conversas de bot
keywords: bots mensagens de conversas
ms.topic: how-to
localization_priority: Normal
ms.date: 03/29/2018
ms.openlocfilehash: dfb91e18a2ad895ae5b48c905046a22449304fc6
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566744"
---
# <a name="formatting-bot-messages"></a>Formatar mensagens de bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Você pode definir a propriedade opcional [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) para controlar como o conteúdo de texto da sua mensagem é renderizado.

Microsoft Teams suporta as seguintes opções de formatação:

| Valor TextFormat | Descrição |
| --- | --- |
| planície | O texto deve ser tratado como texto bruto sem nenhuma formatação aplicada. |
| Markdown | O texto deve ser tratado como formatação de Markdown e prestado no canal conforme apropriado; consulte [Formatação de conteúdo de texto](#formatting-text-content) para estilos suportados. |
| XML | O texto é uma marcação XML simples; consulte [Formatação de conteúdo de texto](#formatting-text-content) para estilos suportados. |

## <a name="formatting-text-content"></a>Formatação de conteúdo de texto

Microsoft Teams suporta um subconjunto de tags de formatação de Markdown e XML (HTML).

Atualmente, aplicam-se as seguintes limitações:

* Mensagens somente de texto não suportam formatação de tabela

Para obter informações sobre a formatação em cartões, consulte [Teams Referência de Cartão](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Suporte multiplataforma

Para garantir que sua formatação funcione em todas as plataformas suportadas por Microsoft Teams, esteja ciente de que alguns estilos não são suportados no momento em todas as plataformas.

| Style                     | Mensagens somente de texto | Cartões (somente XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| cabeçalho (níveis &ndash; 13) | ✖                  | ✔                |
| strikethrough             | ✖                  | ✔                |
| regra horizontal           | ✖                  | ✖                |
| lista não rdenada            | ✖                  | ✔                |
| lista ordenada              | ✖                  | ✔                |
| texto pré-formado         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| hiperlink                 | ✔                  | ✔                |
| link de imagem                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

#### <a name="text-only-messages"></a>Mensagens somente de texto

| Style                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| cabeçalho (níveis &ndash; 13) | ✖       | ✖   | ✖       |
| strikethrough             | ✔       | ✔   | ✖       |
| regra horizontal           | ✖       | ✖   | ✖       |
| lista não rdenada            | ✔       | ✖   | ✖       |
| lista ordenada              | ✔       | ✖   | ✖       |
| texto pré-formado         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| hiperlink                 | ✔       | ✔   | ✔       |
| link de imagem                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Exemplos de formatação de texto

| Style | Exemplo | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| cabeçalho (níveis &ndash; 13) | **Texto** | `### Text` | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| lista não rdenada | <ul><li>texto</li><li>texto</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formado | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
