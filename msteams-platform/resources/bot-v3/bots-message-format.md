---
title: Formato de mensagem bot
description: Descreve os detalhes da formatação para mensagens bot
keywords: teams scenarios channels conversation bot message
ms.topic: reference
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: 06037bd3fb23ace11eea763747dc64d763ac3c42
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020643"
---
# <a name="message-formatting-for-bots"></a>Formatação de mensagens para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Você pode definir a propriedade opcional para controlar como o conteúdo de texto da mensagem [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) é renderizado.

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
* Os cartões rich suportam formatação somente na propriedade text, não nas propriedades title ou subtitle
* Os cartões rich não suportam formatação de tabela ou markdown

## <a name="cross-platform-support"></a>Suporte entre plataformas

Para garantir que sua formatação funcione em todas as plataformas com suporte do Microsoft Teams, esteja ciente de que alguns estilos atualmente não têm suporte em todas as plataformas.

| Style                     | Mensagens somente texto | Rich cards (somente XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| header (níveis 1 &ndash; 3) | ✖ | ✔ |
| strikethrough             | ✖ | ✔ |
| regra horizontal           | ✖ | ✖ |
| lista semordenagem            | ✖ | ✔ |
| lista ordenada              | ✖ | ✔ |
| texto pré-formatado         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| hiperlink                 | ✔ | ✔ |
| link de imagem                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

### <a name="text-only-messages"></a>Mensagens somente texto

| Style                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| header (níveis 1 &ndash; 3) | ✖ | ✖ | ✖ |
| strikethrough             | ✔ | ✔ | ✖ |
| regra horizontal           | ✖ | ✖ | ✖ |
| lista semordenagem            | ✔ | ✖ | ✖ |
| lista ordenada              | ✔ | ✖ | ✖ |
| texto pré-formatado         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| hiperlink                 | ✔ | ✔ | ✔ |
| link de imagem                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Cartões

Consulte [Formatação de Cartão para](~/task-modules-and-cards/cards/cards-format.md) suporte em cartões.
