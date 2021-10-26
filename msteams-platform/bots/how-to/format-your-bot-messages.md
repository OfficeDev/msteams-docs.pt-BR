---
title: Formatar suas mensagens de bot
author: surbhigupta
description: Adicionar formatação rica às mensagens de bot
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 7a8bcc272163a14836fb4b7324cd7ba617bb5409
ms.sourcegitcommit: 781e7b82240075e9d1f55e97f3f1dcbba82a5e4d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2021
ms.locfileid: "60566222"
---
# <a name="format-your-bot-messages"></a>Formatar suas mensagens de bot

A formatação de mensagens permite que você traga o melhor em mensagens bot. Você pode formatar suas mensagens bot para incluir cartões rich que são anexos que contêm elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante.

## <a name="format-text-content"></a>Formatar conteúdo de texto

Para formatar suas mensagens bot, você pode definir a propriedade opcional para controlar como o conteúdo de texto da mensagem bot [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) é renderizado.

Microsoft Teams oferece suporte às seguintes opções de formatação:

| `TextFormat` value | Descrição |
| --- | --- |
| plain | O texto deve ser tratado como texto bruto sem formatação aplicada.|
| Markdown | O texto deve ser tratado como formatação de marcação e renderizado no canal conforme apropriado. |
| xml | O texto é uma marcação XML simples. |

Teams oferece suporte a um subconjunto de marcas de marcação e xml ou formatação HTML.

Atualmente, as seguintes limitações se aplicam à formatação:

* As mensagens somente texto não suportam formatação de tabela.
* Os cartões rich suportam a formatação somente na propriedade text, não nas propriedades title ou subtitle.
* Os cartões rich não suportam marcação ou formatação de tabela.

Depois de formatar o conteúdo de texto, certifique-se de que sua formatação funcione em todas as plataformas com suporte Microsoft Teams.

## <a name="cross-platform-support"></a>Suporte entre plataformas

Atualmente, alguns estilos não têm suporte em todas as plataformas. A tabela a seguir fornece uma lista de estilos e quais desses estilos são suportados em mensagens somente texto e cartões rich:

| Style                     | Mensagens somente texto | Rich cards - somente XML |
| ---                       | :---: | :---: |
| Negrito                      | ✔ | ✖ |
| Itálico                    | ✔ | ✔ |
| Header (níveis 1 &ndash; 3) | ✖ | ✔ |
| Tachado             | ✖ | ✔ |
| Régua horizontal           | ✖ | ✖ |
| Lista não ordenada            | ✖ | ✔ |
| Lista ordenada              | ✖ | ✔ |
| Texto pré-formatado         | ✔ | ✔ |
| Blockquote                | ✔ | ✔ |
| Hiperlink                 | ✔ | ✔ |
| Link de imagem                | ✔ | ✖ |

Depois de verificar o suporte entre plataformas, verifique se o suporte por plataformas individuais também está disponível.

## <a name="support-by-individual-platform"></a>Suporte por plataforma individual

O suporte para formatação de texto varia de acordo com o tipo de mensagem e plataforma.

### <a name="text-only-messages"></a>Mensagens somente texto

A tabela a seguir fornece uma lista de estilos, que são suportados na área de trabalho, iOS e Android:

| Style                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| Negrito                      | ✔ | ✔ | ✔ |
| Itálico                    | ✔ | ✔ | ✔ |
| Header (níveis 1 &ndash; 3) | ✖ | ✖ | ✖ |
| Tachado             | ✔ | ✔ | ✖ |
| Régua horizontal           | ✖ | ✖ | ✖ |
| Lista não ordenada            | ✔ | ✖ | ✖ |
| Lista ordenada              | ✔ | ✖ | ✖ |
| Texto pré-formatado         | ✔ | ✔ | ✔ |
| Blockquote                | ✔ | ✔ | ✔ |
| Hiperlink                 | ✔ | ✔ | ✔ |
| Link de imagem                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Cartões

Para suporte a cartão, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Atualizar e excluir mensagens de bot](~/bots/how-to/update-and-delete-bot-messages.md)
