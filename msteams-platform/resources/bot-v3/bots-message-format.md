---
title: Formato de mensagem bot
description: Descreve os detalhes da formatação para mensagens de bot
keywords: cenários equipes canais mensagem bot conversação
ms.topic: reference
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: a9566331b259ba77f6770ff6394e8a788769af5d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566471"
---
# <a name="message-formatting-for-bots"></a>Formatação de mensagens para bots

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

* As mensagens somente de texto não suportam a formatação da tabela.
* Cartões ricos suportam a formatação apenas na propriedade de texto, não nas propriedades do título ou da legenda.
* Cartões ricos não suportam Marcação ou formatação de tabela.

## <a name="cross-platform-support"></a>Suporte multiplataforma

Para garantir que sua formatação funcione em todas as plataformas suportadas por Microsoft Teams, esteja ciente de que alguns estilos não são suportados no momento em todas as plataformas.

| Style                     | Mensagens somente de texto | Cartões ricos (somente XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| cabeçalho (níveis &ndash; 13) | ✖ | ✔ |
| strikethrough             | ✖ | ✔ |
| regra horizontal           | ✖ | ✖ |
| lista não rdenada            | ✖ | ✔ |
| lista ordenada              | ✖ | ✔ |
| texto pré-formado         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| hiperlink                 | ✔ | ✔ |
| link de imagem                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e por plataforma.

### <a name="text-only-messages"></a>Mensagens somente de texto

| Style                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| cabeçalho (níveis &ndash; 13) | ✖ | ✖ | ✖ |
| strikethrough             | ✔ | ✔ | ✖ |
| regra horizontal           | ✖ | ✖ | ✖ |
| lista não rdenada            | ✔ | ✖ | ✖ |
| lista ordenada              | ✔ | ✖ | ✖ |
| texto pré-formado         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| hiperlink                 | ✔ | ✔ | ✔ |
| link de imagem                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Cartões

Para obter mais informações, consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para obter suporte em cartões.
