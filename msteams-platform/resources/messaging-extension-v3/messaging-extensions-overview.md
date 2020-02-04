---
title: Desenvolver extensões de mensagens
description: Descreve como começar a usar as extensões de mensagens no Microsoft Teams
keywords: extensões de mensagens de extensões de mensagens do Microsoft Teams
ms.openlocfilehash: 6ba8f73d40f795a83f28707ef89c207c5d51d67c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672479"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a>Desenvolver extensões de mensagens para o Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagens são uma maneira poderosa para os usuários entrarem com seu aplicativo no Microsoft Teams. Com esse recurso, os usuários podem consultar ou postar informações de e para o seu serviço e postar essas informações, na forma de cartões, diretamente em uma mensagem.

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As extensões de mensagens aparecem ao longo da parte inferior da caixa de composição. Alguns são internos, como Emoji, Giphy e adesivo. Escolha o botão **mais opções** (**&#8943;**) para ver outras extensões de mensagens, incluindo aquelas que você adicionar da Galeria de aplicativos ou se carregar sozinho.

Como você usaria as extensões de mensagens? Veja algumas possibilidades:

* Itens de trabalho e bugs
* Tíquetes de atendimento ao cliente
* Relatórios e gráficos de uso
* Imagens e conteúdo de mídia
* Oportunidades de vendas e clientes potenciais

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

Há principalmente dois tipos de extensões de mensagens que você pode criar para o Microsoft Teams. Os tópicos a seguir orientarão você durante o processo de criação:

* [Pesquisar extensões de mensagens baseadas](~/resources/messaging-extension-v3/search-extensions.md): consulte o serviço para obter informações e insira-o em uma mensagem. Exemplo: Pesquisar um item de trabalho
* [Extensões de mensagens baseadas em ação](~/resources/messaging-extension-v3/create-extensions.md): coletar informações do usuário e postar em um serviço de terceiros. Exemplo: criar um item de trabalho
