---
title: Combinar bots com guias
description: Descreve como usar guias e bots juntos
keywords: desenvolvimento de guias de bots do teams
ms.topic: conceptual
ms.date: 03/15/2018
ms.openlocfilehash: d8ef669f55d5edbb9795fa2d34277bd2e2dccc7c
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696595"
---
# <a name="combine-bots-with-tabs"></a>Combinar bots com guias

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots e guias funcionam bem juntos e geralmente são combinados em um único serviço back-end. Esta seção descreve as práticas recomendadas e padrões comuns para usar guias e bots juntos.

## <a name="associating-user-identities-across-bot-and-tab"></a>Associando identidades de usuário ao bot e à guia

Por exemplo: suponha que seu aplicativo de tabulação use um sistema de ID proprietário para proteger seu conteúdo. Suponha que você também tenha um bot que possa interagir com o usuário. Normalmente, você vai querer mostrar conteúdo na guia que é específico para o usuário de exibição. O desafio é que a ID do usuário em seu sistema é provavelmente diferente da ID de usuário do Microsoft Teams. Então, como você associa essas duas identidades?
Em geral, a abordagem recomendada é entrar com o usuário com o bot usando o mesmo sistema de identidade usado para fornecer autenticação para o conteúdo da guia. Você pode implementá-lo por meio da ação de login, que normalmente registra o usuário por meio de um fluxo OAuth.

Esse fluxo funciona melhor se o provedor de identidade implementar o protocolo OAuth 2.0. Em seguida, você pode associar a ID de usuário do Teams às credenciais do usuário do seu próprio serviço de identidade.

   ![Associando identidades](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Criar links profundos para guias em mensagens de seu bot

Talvez você queira usar guias para mostrar mais conteúdo do que pode caber dentro de um cartão ou fornecer uma maneira de concluir tarefas complexas de preenchimento de formulário usando a tela de tabulação. Por exemplo, considere navegar o usuário para a guia quando clicar no cartão do bot. Para isso acontecer, você precisará codificar a mensagem do bot para incluir uma URL de [link](~/concepts/build-and-test/deep-links.md) profundo, por meio da marcação ou como o destino da ação openUrl.

Os links profundos dependem de uma entityId, que é um valor opaco que mapeia para uma entidade exclusiva em seu sistema. Quando a guia é criada, você armazena um estado simples (por exemplo, sinalizador) no back-end indicando que a guia foi criada no canal. Quando o bot constrói uma mensagem, ele pode direcionar a entityId associada a essa guia.

**Observação:** em chats pessoais, como as guias são "estáticas" e instaladas com o aplicativo, você sempre pode assumir sua existência e, assim, construir links profundos de acordo.

## <a name="sending-notifications-for-tab-updates"></a>Envio de notificações para atualizações de tabulação

Muitas vezes, você vai querer notificar o usuário final sempre que uma atualização ou uma ação do usuário ocorrer em uma guia. Um exemplo de cenário é atribuir uma tarefa ou tíquete a um colega membro da equipe e notificar esse membro da equipe.

Há duas maneiras de alcançar esse cenário:

1. Se você quiser notificar um canal inteiro, seu bot poderá postar uma mensagem de forma assíncrona no canal. Não há como um bot criar proativamente a conversa de tabulação se ela não foi criada com a guia.

2. Se você quiser apenas notificar o destinatário ou as partes interessadas envolvidas na ação, seu bot poderá enviar uma mensagem de chat pessoal para o usuário. Primeiro, verifique se existe uma conversa pessoal entre o bot e o usuário. Caso não seja, você pode chamar `CreateConversation` para iniciar o chat pessoal.

Em ambos os casos, use notificações de eventos com sabedoria e nunca spam do usuário com atualizações desnecessárias.
