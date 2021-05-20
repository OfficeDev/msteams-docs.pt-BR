---
title: Conversas 1-on-1 com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa 1-em-1 com um bot em Microsoft Teams
keywords: cenários de equipes 1on1 1to1 chat bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: dff65e919485eff0443032995b934b7ae93c64eb
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566499"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Tenha uma conversa pessoal (um-a-um) com um bot Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams permite que os usuários se envolvam em conversas diretas com bots construídos no [Microsoft Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true). Os usuários podem encontrar bots na galeria Discover Apps e adicioná-los à sua Teams experiência para conversas pessoais. Proprietários de equipes e usuários com as permissões apropriadas também podem adicionar bots como membros da equipe. Para obter mais informações, consulte [Interact em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)de equipe , o que não só os disponibiliza nos canais dessa equipe, mas também para bate-papo pessoal para todos esses usuários.

O chat pessoal difere do chat nos canais em que o usuário não precisa @mention o bot. Se um bot for usado em vários contextos, como pessoal, groupChat ou canal, você precisa detectar se o bot está em um chat ou canal em grupo e processar mensagens um pouco diferente. Para obter mais informações, consulte [Interact em um canal de equipe ou bate-papo em grupo](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

## <a name="designing-a-great-personal-bot"></a>Projetando um grande bot pessoal

Um ótimo bot no Microsoft Teams ajuda os usuários a obter as informações de que precisam, tudo dentro do contexto da experiência Teams. Conversas pessoais com um bot são trocas privadas entre um bot e seu usuário; eles são uma ótima maneira de fornecer informações específicas e relevantes para esse usuário no contexto pessoal. Um bot no chat pessoal é realmente um diálogo entre o seu serviço e o indivíduo, onde um bot em um bate-papo em grupo ou canal transmite tudo para um grupo de pessoas.

Dependendo da experiência que você deseja criar, o bot pode precisar trabalhar em vários escopos - pessoal, groupchat e equipe. O trabalho para suportar mais de um escopo é mínimo. Não há expectativa em Teams que seu bot funcione em todos os escopos, mas você deve garantir que seu bot faça sentido e forneça valor ao usuário em qualquer escopo que você escolher para suportar.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Melhores práticas: Mensagens de boas-vindas em conversas pessoais

Seu bot deve enviar uma mensagem de boas-vindas [proativamente](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para um chat pessoal na primeira vez (e apenas na primeira vez) que um usuário inicia um bate-papo pessoal com seu bot. Esta recomendação não se aplica a contatos iniciantes em um canal.
