---
title: Desenvolver extensões de mensagens
description: Descreve como começar a usar extensões de mensagens em Microsoft Teams
ms.topic: overview
ms.localizationpriority: medium
keywords: extensões de mensagens do teams messaging extensions
ms.openlocfilehash: ea07ae8c7a7a16f5187adfe6dbe5f52d8bf47056
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155186"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a>Desenvolver extensões de mensagens para Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Extensões de mensagens são uma maneira poderosa de os usuários se envolverem com seu aplicativo Microsoft Teams. Com essa funcionalidade, os usuários podem consultar ou postar informações de e para o serviço e postar essas informações, na forma de cartões, em uma mensagem.

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As extensões de mensagens aparecem ao longo da parte inferior da caixa de redação. Alguns são integrados, como Emoji, Giphy e Sticker. Escolha o **botão Mais Opções** (**&#8943;**) para ver outras extensões de mensagens, incluindo aquelas que você adiciona na galeria de aplicativos ou carrega você mesmo.

Como você usaria extensões de mensagens? Aqui estão algumas possibilidades:

* Itens de trabalho e bugs
* Tíquetes de suporte ao cliente
* Gráficos de uso e relatórios
* Imagens e conteúdo de mídia
* Oportunidades de vendas e leads

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

Há basicamente dois tipos de extensões de mensagens que você pode criar para Teams hoje. Os tópicos a seguir orientarão você durante o processo de criação deles:

* [Extensões de mensagens baseadas em pesquisa:](~/resources/messaging-extension-v3/search-extensions.md)consulte seu serviço para obter informações e insira-as em uma mensagem. Exemplo: Procure um item de trabalho
* [Extensões de mensagens baseadas em](~/resources/messaging-extension-v3/create-extensions.md)ação : Coletar informações do usuário e postar em um serviço de terceiros. Exemplo: Criar um item de trabalho
