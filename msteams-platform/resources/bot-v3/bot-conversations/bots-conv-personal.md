---
title: conversas 1-em-1 com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa 1-em-1 com um bot no Microsoft Teams
keywords: cenários de equipes 1on1 1to1 bot de conversa
ms.date: 05/20/2019
ms.openlocfilehash: e23bb98160125d7fdbb4521467e2f522d6b6ce40
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672946"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Ter uma conversa pessoal (de um em um) com um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams permite que os usuários participem de conversas diretas com bots criados no [Microsoft bot Framework](/azure/bot-service/?view=azure-bot-service-3.0). Os usuários podem encontrar bots na Galeria de aplicativos de descoberta e adicioná-los à experiência de suas equipes para conversas pessoais. Proprietários e usuários da equipe com as permissões apropriadas também podem adicionar bots como membros da equipe (consulte [interagir em um canal de equipe](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)), que não só os disponibilizam nos canais dessa equipe, mas também para o chat pessoal de todos esses usuários.

O chat pessoal difere do bate-papo em canais em que o usuário não precisa @mention o bot. Se um bot for usado em vários contextos (pessoal, groupChat ou canal), será necessário detectar se o bot está em um canal ou chat de grupo e processar mensagens um pouco diferente. Consulte [interagir em um canal de equipe ou chat de grupo](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.

## <a name="designing-a-great-personal-bot"></a>Criando um ótimo bot pessoal

Um ótimo bot no Microsoft Teams ajuda os usuários a obter as informações de que precisam, tudo dentro do contexto da experiência do Microsoft Teams. Conversas pessoais com um bot são trocas privadas entre um bot e seu usuário; Eles são uma ótima maneira de fornecer informações específicas e relevantes para esse usuário no contexto pessoal. Um bot no bate-papo pessoal é, na verdade, uma caixa de diálogo entre o serviço e o indivíduo, onde um bot em um canal ou bate-papo em grupo transmite tudo para um grupo de pessoas.

Dependendo da experiência que você deseja criar, o bot pode precisar trabalhar em vários escopos-pessoal, groupChat e/ou equipe. O trabalho para dar suporte a mais de um escopo é mínimo. Não há expectativas no Teams que seu bot funciona em todos os escopos, mas você deve garantir que seu bot faça sentido e fornece valor de usuário em qualquer escopo (s) que você optar por suportar.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Práticas recomendadas: mensagens de boas-vindas em conversas pessoais

O bot deve [Enviar](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) uma mensagem de boas-vindas para um chat pessoal pela primeira vez (e somente na primeira vez) um usuário inicia um chat pessoal com seu bot. (Essa recomendação não se aplica a contatos pela primeira vez em um canal.)
