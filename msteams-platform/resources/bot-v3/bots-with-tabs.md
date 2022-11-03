---
title: Combinar bots com guias
description: Neste artigo, você aprenderá a usar guias e bots juntos, construindo links profundos para guias em mensagens do bot e desenvolvimento de guias de bots do teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 03/15/2018
ms.openlocfilehash: f993f3d8deb8b8a781c96627bf63c2eed350e6c8
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833020"
---
# <a name="combine-bots-with-tabs"></a>Combinar bots com guias

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots e guias funcionam juntos e geralmente são combinados em um único serviço de back-end. Esta seção descreve práticas recomendadas e padrões comuns para usar guias e bots juntos.

## <a name="associating-user-identities-across-bot-and-tab"></a>Associando identidades de usuário entre bot e guia

Por exemplo: suponha que seu aplicativo de guia use um sistema de ID proprietário para proteger seu conteúdo. Suponha que você também tenha um bot que possa interagir com o usuário. Normalmente, você deseja mostrar conteúdo na guia específica para o usuário de exibição. O desafio é que a ID do usuário em seu sistema provavelmente é diferente da ID do usuário do Microsoft Teams. Então, como você associa essas duas identidades?
Em geral, a abordagem recomendada é entrar com o usuário com o bot usando o mesmo sistema de identidade usado para fornecer autenticação para o conteúdo da guia. Você pode implementar por meio da ação de entrada, que normalmente faz logon no usuário por meio de um fluxo OAuth.

Esse fluxo funcionará melhor se o provedor de identidade implementar o protocolo OAuth 2.0. Em seguida, você pode associar a ID do usuário do Teams às credenciais do usuário do seu próprio serviço de identidade.

   :::image type="content" source="../../assets/images/bots/associating_contexts.png" alt-text="A captura de tela mostra as identidades de associação.":::

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Construir links profundos para guias em mensagens do bot

Você deseja usar guias para mostrar mais conteúdo que possa se encaixar dentro de um cartão ou fornecer uma maneira de concluir tarefas complexas de preenchimento de formulários usando a tela de guia. Por exemplo, considere navegar o usuário até a guia quando o usuário selecionar o cartão no bot. Para que isso aconteça, você precisará codificar a mensagem do bot para incluir uma URL de [link profundo](~/concepts/build-and-test/deep-links.md) , por meio da marcação ou como destino da ação openUrl.

Os links profundos dependem de uma entityId, que é um valor opaco que mapeia para uma entidade exclusiva em seu sistema. Quando a guia é criada, você armazena um estado simples. Por exemplo, sinalizador no back-end indicando que a guia é criada no canal. Quando o bot constrói uma mensagem, ele pode direcionar a entityId associada a essa guia.

> [!NOTE]
> Em chats pessoais, como as guias são *estáticas* e instaladas com o aplicativo, você sempre pode assumir sua existência e, assim, construir links profundos de acordo.

## <a name="sending-notifications-for-tab-updates"></a>Enviar notificações para atualizações de guia

Geralmente, você deseja notificar o usuário final sempre que uma atualização ou uma ação do usuário ocorrer em uma guia. Um cenário de exemplo é atribuir uma tarefa ou tíquete a um membro da equipe e notificar esse membro da equipe.

Há duas maneiras de alcançar este cenário:

1. Se você quiser notificar um canal inteiro, o bot poderá postar uma mensagem de forma assíncrona no canal. Não há como um bot criar proativamente a conversa de guia se ela não foi criada com a guia.

2. Se você quiser notificar apenas o destinatário ou as partes interessadas envolvidas com a ação, o bot poderá enviar uma mensagem de chat pessoal ao usuário. Primeiro, verifique se existe uma conversa pessoal entre o bot e o usuário. Caso contrário, você pode chamar `CreateConversation` para iniciar o chat pessoal.

Em ambos os casos, use notificações de evento com sabedoria e nunca envie spam ao usuário com atualizações desnecessárias.
