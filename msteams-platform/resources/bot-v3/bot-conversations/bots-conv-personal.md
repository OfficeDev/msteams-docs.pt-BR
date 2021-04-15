---
title: Conversas 1 a 1 com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa 1 a 1 com um bot no Microsoft Teams
keywords: teams scenarios 1on1 1to1 conversation bot
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: 43b44d15b675db2fa6c38d6661858c4e0a595039
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696665"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Ter uma conversa pessoal (um para um) com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários se envolvam em conversas diretas com bots integrados à [Estrutura do Microsoft Bot.](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) Os usuários podem encontrar bots na galeria Descobrir Aplicativos e adicioná-los à experiência do Teams para conversas pessoais. Os proprietários e usuários de equipe com as permissões apropriadas também podem adicionar bots como membros da equipe (consulte [Interact in a team channel](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)), que não só os disponibiliza nos canais dessa equipe, mas também para chat pessoal para todos esses usuários.

O chat pessoal difere do chat nos canais, já que o usuário não precisa @mention o bot. Se um bot for usado em vários contextos (pessoal, groupChat ou canal), você precisará detectar se o bot está em um chat de grupo ou canal e processar mensagens de forma um pouco diferente. Confira [Interagir em um canal de equipe ou chat em grupo](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.

## <a name="designing-a-great-personal-bot"></a>Projetando um ótimo bot pessoal

Um ótimo bot no Microsoft Teams ajuda os usuários a obter as informações necessárias, tudo dentro do contexto da experiência do Teams. Conversas pessoais com um bot são trocas privadas entre um bot e seu usuário; eles são uma ótima maneira de fornecer informações específicas e relevantes para esse usuário no contexto pessoal. Um bot no chat pessoal é realmente uma caixa de diálogo entre seu serviço e o indivíduo, onde um bot em um chat de grupo ou canal transmite tudo para um grupo de pessoas.

Dependendo da experiência que você deseja criar, o bot pode precisar trabalhar em vários escopos - pessoal, groupChat e/ou equipe. O trabalho para dar suporte a mais de um escopo é mínimo. Não há expectativa no Teams de que seu bot funcione em todos os escopos, mas você deve garantir que o bot faça sentido e fornece valor para o usuário em qualquer escopo que você escolher dar suporte.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Prática prática: mensagens de boas-vindas em conversas pessoais

Seu bot deve [enviar proativamente](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) uma mensagem de boas-vindas para um chat pessoal na primeira vez (e somente na primeira vez) em que um usuário inicia um chat pessoal com seu bot. (Esta recomendação não se aplica a contatos pela primeira vez em um canal.)
