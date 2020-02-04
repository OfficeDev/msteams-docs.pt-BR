---
title: Formatar suas mensagens de bot
author: clearab
description: Adicionar formatação avançada às suas mensagens de bot
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a11d01233481371c66562e0fa27ab805b06e9391
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672597"
---
# <a name="format-your-bot-messages"></a>Formatar suas mensagens de bot

Você pode definir a propriedade [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) opcional para controlar como o conteúdo de texto da mensagem é renderizado.

O Microsoft Teams suporta as seguintes opções de formatação:

| Valor TextFormat | Descrição |
| --- | --- |
| comuns | O texto deve ser tratado como um texto bruto sem formatação aplicada.|
| redução | O texto deve ser tratado como formatação de redução e renderizado no canal, conforme apropriado. *Confira* [Formatando o conteúdo de texto](#formatting-text-content) para os estilos com suporte. |
| XML | O texto é marcação XML simples. *Confira* [Formatando o conteúdo de texto](#formatting-text-content) para os estilos com suporte. |

## <a name="formatting-text-content"></a>Formatando conteúdo de texto

O Microsoft Teams oferece suporte a um subconjunto de marcas de formatação de redução e XML (HTML).

Atualmente, as seguintes limitações se aplicam:

* As mensagens somente texto não oferecem suporte à formatação de tabela.
* Os cartões ricos dão suporte à formatação somente na propriedade Text, e não nas propriedades Title ou subtítulo.
* Os cartões avançados não oferecem suporte para redução ou formatação de tabela.

## <a name="cross-platform-support"></a>Suporte a várias plataformas

Para garantir que a formatação funcione em todas as plataformas compatíveis com o Microsoft Teams, lembre-se de que alguns estilos não são suportados atualmente em todas as plataformas.

| Estilo                     | Mensagens somente de texto | Cartões avançados (somente XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| cabeçalho (níveis 1&ndash;3) | ✖ | ✔ |
| tachado             | ✖ | ✔ |
| régua horizontal           | ✖ | ✖ |
| lista não ordenada            | ✖ | ✔ |
| lista ordenada              | ✖ | ✔ |
| texto pré-formatado         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| hyperlink                 | ✔ | ✔ |
| link de imagem                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

### <a name="text-only-messages"></a>Mensagens somente de texto

| Estilo                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| cabeçalho (níveis 1&ndash;3) | ✖ | ✖ | ✖ |
| tachado             | ✔ | ✔ | ✖ |
| régua horizontal           | ✖ | ✖ | ✖ |
| lista não ordenada            | ✔ | ✖ | ✖ |
| lista ordenada              | ✔ | ✖ | ✖ |
| texto pré-formatado         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| hyperlink                 | ✔ | ✔ | ✔ |
| link de imagem                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Placa

Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para suporte em cartões.
