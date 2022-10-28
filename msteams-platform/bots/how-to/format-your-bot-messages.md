---
title: Formatar suas mensagens de bot
author: surbhigupta
description: Saiba como formatar e estilizar suas mensagens de bot, como strikethrough, ordered e unordered list, hyperlink ou image link. Entenda o suporte entre plataformas.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: b0db9f9d9e55dc3f11474dac4b8c6563caf5fd1b
ms.sourcegitcommit: bb15ce26cd65bec90991b703069424ab4b4e1a61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68772297"
---
# <a name="format-your-bot-messages"></a>Formatar suas mensagens de bot

A formatação de mensagens permite que você destaque o melhor nas mensagens de bot. Você pode formatar suas mensagens de bot para incluir cartões avançados como anexos que contêm elementos interativos, como botões, texto, imagens e assim por diante.

> [!NOTE]
> O limite de tamanho da mensagem do bot é de 40 KB. Se o limite de tamanho da mensagem do bot exceder 40 KB, o bot receberá um `413` código de status (`RequestEntityTooLarge`), que contém o código de `MessageSizeTooBig`erro . O limite de tamanho da mensagem do bot inclui toda a carga de mensagem codificada como UTF-16 e não inclui imagens codificadas do Base64.

## <a name="format-text-content"></a>Formatar o conteúdo de texto

Para formatar suas mensagens de bot, você pode definir a propriedade opcional [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) para controlar como o conteúdo de texto da mensagem de bot é renderizado.

O Microsoft Teams dá suporte às seguintes opções de formatação:

| `TextFormat` valor | Descrição |
| --- | --- |
| Sem formatação | O texto deve ser tratado como texto bruto sem formatação aplicada.|
| Markdown | O texto deve ser tratado como formatação de markdown e renderizado no canal conforme for apropriado. |
| xml | O texto é uma marcação XML simples. |

O Teams dá suporte a um subconjunto de rótulos de formatação de markdown XML ou HTML.

Atualmente, as seguintes limitações se aplicam à formatação:

* Mensagens somente texto não dão suporte à formatação de tabela.
* Os cartões avançados dão suporte à formatação somente na propriedade de texto, não nas propriedades de título ou subtítulo.
* Cartões ricos não dão suporte a markdown ou formatação de tabela.

Depois de formatar o conteúdo de texto, verifique se a formatação funciona em todas as plataformas com suporte do Teams.

## <a name="cross-platform-support"></a>Suporte à plataforma cruzada.

Atualmente, não há suporte para alguns estilos em todas as plataformas. A tabela a seguir fornece uma lista de estilos e quais desses estilos têm suporte em mensagens somente texto e cartões avançados:

| Style                     | Mensagens somente texto | Cartões avançados – somente XML |
| ---                       | :---: | :---: |
| Negrito                      | ✔️️ | ❌ |
| Itálico                    | ✔️ | ✔️ |
| Cabeçalho (níveis 1&ndash;3) | ❌ | ✔️ |
| Tachado             | ❌ | ✔️ |
| Régua horizontal           | ❌ | ❌ |
| Lista não ordenada            | ❌ | ✔️ |
| Lista ordenada              | ❌ | ✔️ |
| Texto pré-formatado         | ✔️ | ✔️ |
| Blockquote                | ✔️ | ✔️ |
| Hiperlink                 | ✔️ | ✔️ |
| Link da imagem                | ❌ | ❌ |

Depois de verificar o suporte de plataforma cruzada, verifique se o suporte por plataformas individuais também está disponível.

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e de plataforma.

### <a name="text-only-messages"></a>Mensagens somente texto

A tabela a seguir fornece uma lista de estilos com suporte na área de trabalho, no iOS e no Android:

| Style                     | Área de trabalho | iOS | Android |
| ---                       | :---: | :---: | :---: |
| Negrito                      | ✔️ | ✔️ | ✔️ |
| Itálico                    | ✔️ | ✔️ | ✔️ |
| Cabeçalho (níveis 1&ndash;3) | ❌ | ❌ | ❌ |
| Tachado             | ✔️ | ✔️ | ❌ |
| Régua horizontal           | ❌ | ❌ | ❌ |
| Lista não ordenada            | ✔️ | ❌ | ❌ |
| Lista ordenada              | ✔️ | ❌ | ❌ |
| Texto pré-formatado         | ✔️ | ✔️ | ✔️ |
| Blockquote                | ✔️ | ✔️ | ✔️ |
| Hiperlink                 | ✔️ | ✔️ | ✔️ |
| Link da imagem                | ❌ | ❌ | ❌ |

### <a name="cards"></a>Cartões

Para obter suporte a cartão, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Atualizar e excluir mensagens de bot](~/bots/how-to/update-and-delete-bot-messages.md)
