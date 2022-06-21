---
title: Formatação de texto com suporte em conversas
description: Neste módulo, aprenda o suporte à formatação de texto em conversas de bot e formatação de conteúdo de texto Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/29/2018
ms.openlocfilehash: 0aea1472a323c0161567c4661c02956568cb2187
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189731"
---
# <a name="formatting-bot-messages"></a>Formatar mensagens de bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Você pode definir a propriedade opcional [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) para controlar como o conteúdo de texto da mensagem é renderizado.

O Microsoft Teams dá suporte às seguintes opções de formatação:

| Valor textformat | Descrição |
| --- | --- |
| Sem formatação | O texto deve ser tratado como texto bruto sem nenhuma formatação aplicada. |
| Markdown | O texto deve ser tratado como formatação markdown e renderizado no canal conforme apropriado; consulte [Formatação de conteúdo de texto](#formatting-text-content) para estilos com suporte. |
| xml | O texto é uma marcação XML simples; consulte [Formatação de conteúdo de texto](#formatting-text-content) para estilos com suporte. |

## <a name="formatting-text-content"></a>Formatando conteúdo de texto

Teams dá suporte a um subconjunto de marcas de formatação Markdown e XML (HTML).

Atualmente, as seguintes limitações se aplicam:
* As mensagens somente texto não dão suporte à formatação da tabela.

Para obter informações sobre formatação em cartões, [consulte Teams Referência de Cartão](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Suporte à plataforma cruzada.

Para garantir que sua formatação funcione em todas as plataformas compatíveis com o Teams, lembre-se de que alguns estilos atualmente não têm suporte em todas as plataformas.

| Style                     | Mensagens somente texto | Cartões (somente XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| cabeçalho (níveis 1&ndash;3) | ✖                  | ✔                |
| Tachado             | ✖                  | ✔                |
| regra horizontal           | ✖                  | ✖                |
| lista não ordenada            | ✖                  | ✔                |
| lista ordenada              | ✖                  | ✔                |
| texto pré-formatado         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| hiperlink                 | ✔                  | ✔                |
| link de imagem                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

#### <a name="text-only-messages"></a>Mensagens somente texto

| Style                     | Área de trabalho | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| cabeçalho (níveis 1&ndash;3) | ✖       | ✖   | ✖       |
| Tachado             | ✔       | ✔   | ✖       |
| regra horizontal           | ✖       | ✖   | ✖       |
| lista não ordenada            | ✔       | ✖   | ✖       |
| lista ordenada              | ✔       | ✖   | ✖       |
| texto pré-formatado         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| hiperlink                 | ✔       | ✔   | ✔       |
| link de imagem                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Exemplos de formatação de texto

| Estilo | Exemplo | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| cabeçalho (níveis 1&ndash;3) | **Texto** | `### Text` | `<h3>Text</h3>` |
| Tachado | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
