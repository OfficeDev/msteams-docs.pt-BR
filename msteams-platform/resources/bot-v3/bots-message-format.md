---
title: Formato de mensagem do bot
description: Neste módulo, saiba mais sobre a formatação de mensagens de bot
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 9e331a17940ee482a0c2adcb81b57a17823ab668
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190165"
---
# <a name="message-formatting-for-bots"></a>Formatação de mensagem para bots

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

* As mensagens somente texto não dão suporte à formatação de tabela.
* Os cartões avançados dão suporte à formatação somente na propriedade de texto, não nas propriedades de título ou subtítulo.
* Os cartões avançados não dão suporte a markdown ou formatação de tabela.

## <a name="cross-platform-support"></a>Suporte à plataforma cruzada.

Para garantir que sua formatação funcione em todas as plataformas compatíveis com o Teams, lembre-se de que alguns estilos atualmente não têm suporte em todas as plataformas.

| Style                     | Mensagens somente texto | Cartões avançados (somente XML) |
| ---                       | :---: | :---: |
| bold                      | ✔️️ | ❌ |
| italic                    | ✔️ | ✔️ |
| cabeçalho (níveis 1&ndash;3) | ❌ | ✔️ |
| Tachado             | ❌ | ✔️ |
| regra horizontal           | ❌ | ❌ |
| lista não ordenada            | ❌ | ✔️ |
| lista ordenada              | ❌ | ✔️ |
| texto pré-formatado         | ✔️ | ✔️ |
| blockquote                | ✔️ | ✔️ |
| hiperlink                 | ✔️ | ✔️ |
| link de imagem                | ✔️ | ❌ |

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

### <a name="text-only-messages"></a>Mensagens somente texto

| Style                     | Área de trabalho | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔️ | ✔️ | ✔️ |
| italic                    | ✔️ | ✔️ | ✔️ |
| cabeçalho (níveis 1&ndash;3) | ❌ | ❌ | ❌ |
| Tachado             | ✔️ | ✔️ | ❌ |
| regra horizontal           | ❌ | ❌ | ❌ |
| lista não ordenada            | ✔️ | ❌ | ❌ |
| lista ordenada              | ✔️ | ❌ | ❌ |
| texto pré-formatado         | ✔️ | ✔️ | ✔️ |
| blockquote                | ✔️ | ✔️ | ✔️ |
| hiperlink                 | ✔️ | ✔️ | ✔️ |
| link de imagem                | ✔️ | ✔️ | ✔️ |

### <a name="cards"></a>Cartões

Para obter mais informações, consulte [Formatação de Cartão](~/task-modules-and-cards/cards/cards-format.md) para obter suporte em cartões.
