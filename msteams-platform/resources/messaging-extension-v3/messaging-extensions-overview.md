---
title: Desenvolver extensões de mensagem
description: Neste módulo, saiba como começar a usar extensões de mensagem no Microsoft Teams
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: c81df30b71bbdba19842e45f06b4c9bb930e4c0d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143974"
---
# <a name="develop-message-extensions-for-microsoft-teams"></a>Desenvolver extensões de mensagem para Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagem são uma maneira eficiente para os usuários se envolverem com seu aplicativo Microsoft Teams. Com essa funcionalidade, os usuários podem consultar ou postar informações de e para seu serviço e postar essas informações, na forma de cartões, diretamente em uma mensagem.

![Exemplo de cartão de extensão de mensagem](~/assets/images/compose-extensions/ceexample.png)

As extensões de mensagem aparecem na parte inferior da caixa de redação. Alguns são internos, como Emoji, gif e Sticker. Escolha o **botão Mais Opções** (**&#8943;**) para ver outras extensões de mensagem, incluindo aquelas que você adiciona da galeria de aplicativos ou carrega por conta própria.

Como você usaria extensões de mensagem? Aqui estão algumas possibilidades:

* Itens de trabalho e bugs.
* Tíquetes de suporte ao cliente.
* Gráficos e relatórios de uso.
* Imagens e conteúdo de mídia.
* Oportunidades de vendas e clientes potenciais.

## <a name="types-of-message-extensions"></a>Tipos de extensões de mensagens

Há principalmente dois tipos de extensões de mensagem que você pode criar para Teams hoje. Os tópicos a seguir orientarão você durante o processo de criação deles:

* [Extensões de mensagem baseadas em pesquisa](~/resources/messaging-extension-v3/search-extensions.md): consulte seu serviço para obter informações e insira-as em uma mensagem. Exemplo: Pesquisar um item de trabalho
* [Extensões de mensagem baseadas em ação](~/resources/messaging-extension-v3/create-extensions.md): colete informações do usuário e poste em um serviço de terceiros. Exemplo: Criar um item de trabalho
