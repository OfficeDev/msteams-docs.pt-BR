---
title: Combinar bots com guias
description: Descreve como usar guias e bots juntos
keywords: desenvolvimento de guias de bots do teams
ms.date: 03/15/2018
ms.openlocfilehash: 59ae8bc01f82c70dd7ea6869cb870e26acae1293
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672747"
---
# <a name="combine-bots-with-tabs"></a>Combinar bots com guias

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Os bots e guias funcionam bem juntos e são frequentemente combinados em um único serviço de back-end. Esta seção descreve as práticas recomendadas e os padrões comuns para usar guias e bots juntos.

## <a name="associating-user-identities-across-bot-and-tab"></a>Associando identidades de usuário ao bot e à guia

Por exemplo: Suponha que seu aplicativo de guia use um sistema de ID proprietário para proteger seu conteúdo. Suponha que você também tenha um bot que possa interagir com o usuário. Normalmente, você vai querer mostrar o conteúdo na guia específico para o usuário de exibição. O desafio é que a ID de usuário em seu sistema provavelmente é diferente da ID de usuário do Microsoft Teams. Então, como você associa essas duas identidades?
Em geral, a abordagem recomendada é assinar o usuário com o bot usando o mesmo sistema de identidade usado para fornecer autenticação para o conteúdo da guia. Você pode implementar isso por meio da ação de entrada, que geralmente faz logon no usuário por meio de um fluxo OAuth.

Esse fluxo funciona melhor se o seu provedor de identidade implementar o protocolo OAuth 2,0. Em seguida, você pode associar a ID de usuário da equipe às credenciais do usuário de seu próprio serviço de identidade.

   ![Associando identidades](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Construindo links profundas para guias em mensagens do bot

Você pode querer usar guias para mostrar mais conteúdo do que pode caber dentro de um cartão ou fornecer uma maneira de concluir tarefas complexas de preenchimento de formulários usando a tela da guia. Por exemplo, considere navegar o usuário para a guia ao clicar no cartão do bot. Para que isso aconteça, você precisará codificar a mensagem de seu bot para incluir uma URL de [link profundo](~/concepts/build-and-test/deep-links.md) , seja via marcação ou como o destino da ação openUrl.

Links profundos dependem de um EntityId, que é um valor opaco que mapeia para uma entidade exclusiva no seu sistema. Quando a guia é criada, você idealmente armazena um estado simples (por exemplo, sinalizador) no seu back-end, indicando que a guia foi criada no canal. Quando o bot cria uma mensagem, ele pode direcionar a EntityId associada a essa guia.

**Observação:** em bate-papos pessoais, como as guias são "estáticas" e instaladas com o aplicativo, você sempre pode supor sua existência e, assim, construir links profundas de acordo.

## <a name="sending-notifications-for-tab-updates"></a>Enviar notificações para atualizações de guia

Muitas vezes, você deverá notificar o usuário final sempre que uma atualização ou uma ação do usuário ocorrer em uma guia. Um cenário de exemplo é atribuir uma tarefa ou um tíquete a um membro da equipe colega e, em seguida, notificar esse membro da equipe.

Há duas maneiras de obter esse cenário:

1. Se você quiser notificar um canal inteiro, seu bot poderá postar uma mensagem de forma assíncrona no canal. Não há nenhuma maneira de um bot criar proativamente a conversa de guia se ela não tiver sido criada com a guia.

2. Se você quiser apenas notificar o destinatário ou partes interessadas envolvidas na ação, seu bot poderá enviar uma mensagem de chat pessoal para o usuário. Você deve primeiro verificar se uma conversa pessoal entre o bot e o usuário existe. Caso contrário, você pode ligar `CreateConversation` para iniciar o chat pessoal.

Em ambos os casos, use notificações de evento de forma inteligente e nunca spam o usuário com atualizações desnecessárias.
