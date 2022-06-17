---
title: Conversas um-para-um com bots
description: Neste módulo, aprenda o cenário de ponta a ponta de ter uma conversa um-para-um com um bot no Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: e973e335558a54187a11d5146b52c5774d3cf758
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144324"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Ter uma conversa pessoal (um para um) com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários se envolvam em conversas diretas com bots criados no [Microsoft Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true). Os usuários podem encontrar bots na galeria Descobrir Aplicativos e adicioná-los à experiência do Teams para conversas pessoais. Os proprietários e usuários da equipe com as permissões apropriadas também podem adicionar bots como membros da equipe. Para obter mais informações, consulte [Interagir em um canal de equipe](~/resources/bot-v3/bot-conversations/bots-conv-channel.md), que não apenas os disponibiliza nos canais dessa equipe, mas também para usuários de chat pessoal.

O chat pessoal difere do chat em canais em que o usuário não precisa @mention o bot. Se um bot for usado em vários contextos, como nos seguintes escopos:
* Pessoal
* Chat em grupo
* Canal

Você precisa detectar se o bot está em um chat em grupo ou canal e processar mensagens um pouco diferente. Para obter mais informações, [Interaja em um canal de equipe ou chat em grupo](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

## <a name="designing-a-great-personal-bot"></a>Criando um ótimo bot pessoal

Um ótimo bot no Microsoft Teams ajuda os usuários a obter as informações de que precisam, tudo dentro do contexto da experiência do Teams. As conversas pessoais com um bot são trocas privadas entre um bot e seu usuário; eles são uma ótima maneira de fornecer informações específicas e relevantes para esse usuário no contexto pessoal. Um bot no chat pessoal é um diálogo entre o serviço e o indivíduo, em que um bot em um chat em grupo ou canal transmite tudo para um grupo de pessoas.

Dependendo da experiência que você deseja criar, talvez o bot precise trabalhar em vários escopos– pessoal, chat em grupo e equipe. O trabalho para dar suporte a mais de um escopo é mínimo. No Teams, não há expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que o bot faça sentido e forneça valor ao usuário em qualquer escopo que você escolher para dar suporte.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Prática recomendada: mensagens de boas-vindas em conversas pessoais

Seu bot deve [enviar proativamente](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) uma mensagem de boas-vindas para um chat pessoal na primeira vez (e apenas na primeira vez) que um usuário iniciar um chat pessoal com seu bot. Esta recomendação não se aplica a contatos pela primeira vez em um canal.
