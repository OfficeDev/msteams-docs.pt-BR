---
title: Formatar suas mensagens de bot
author: surbhigupta
description: Neste módulo, saiba como adicionar formatação e estilos avançados às suas mensagens de bot, como tachado, lista ordenada e não ordenada, hiperlink, link de imagem e muito mais.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 63c201e2126181793ce09a962b5352fb3418cff2
ms.sourcegitcommit: 217025a61ed9c3b76b507fe95563142abc6d0318
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67363491"
---
# <a name="format-your-bot-messages"></a>Formatar suas mensagens de bot

A formatação de mensagens permite que você destaque o melhor nas mensagens de bot. Você pode formatar suas mensagens de bot para incluir cartões avançados como anexos que contêm elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante.

> [!NOTE]
> O limite de tamanho da mensagem do bot é de 40 KB. Se o limite de tamanho da mensagem do bot exceder 40 KB, o bot `413` receberá um código de status (`RequestEntityTooLarge`), que contém o código de erro `MessageSizeTooBig`. O limite de tamanho de mensagem do bot inclui todo o conteúdo da mensagem codificado como UTF-16 e não inclui imagens codificadas em Base64.

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

* As mensagens somente texto não dão suporte à formatação de tabela.
* Os cartões avançados dão suporte à formatação somente na propriedade de texto, não nas propriedades de título ou subtítulo.
* Os cartões avançados não dão suporte a markdown ou formatação de tabela.

Depois de formatar o conteúdo do texto, verifique se a formatação funciona em todas as plataformas compatíveis com o Teams.

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
