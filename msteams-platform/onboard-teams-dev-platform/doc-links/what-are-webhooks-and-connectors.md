---
title: O que são WebHooks e conectores?
author: clearab
description: Entenda como os WebHooks e conectores podem conectar seus serviços Web ao cliente do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 740806e43af94d5a5da876affec2070a5a461b11
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651815"
---
# <a name="what-are-webhooks-and-connectors"></a>O que são WebHooks e conectores?

Os WebHooks e conectores são maneiras diretas de conectar sistemas e serviços externos aos canais e chats do Microsoft Teams.

Os usuários podem, por exemplo, assinar notificações de outro aplicativo (normalmente na forma de cartões).

## <a name="incoming-webhooks"></a>WebHooks de entrada

Os WebHooks de entrada são o tipo mais simples de conector e um modo rápido e fácil de conectar o canal de uma equipe a um serviço externo. Para qualquer canal (se habilitado para essa equipe), você pode expor um ponto de extremidade HTTPS que aceita JSONmente formatado corretamente e insere mensagens no canal.

Confira [criar um webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="user-scenarios"></a>Cenários de usuário

Os WebHooks de entrada são melhores para cenários exclusivos para uma equipe específica. Por exemplo, você pode criar um webhook de entrada no canal do DevOps e configurar seus serviços de compilação, implantação e monitoramento para enviar alertas.

## <a name="office-365-connectors"></a>Conectores de Office 365

Um conector do Office 365 permite criar uma página de configuração personalizada para o seu webhook de entrada e empacotá-lo como parte de um aplicativo do teams. Em seguida, você pode distribuir esse aplicativo de forma mais ampla ou mesmo em nossa loja de aplicativos. Você envia mensagens principalmente usando cartões de conector do Office 365 que também podem ter um conjunto limitado de ações de cartão. Eles são configurados no nível do canal, mas instalados no nível da equipe.

Confira [criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md).

### <a name="user-scenarios"></a>Cenários de usuário

Um conector de clima que permite que você escolha um local e hora do dia para receber atualizações sobre a previsão de amanhã.

## <a name="outgoing-webhooks"></a>WebHooks de saída

Os WebHooks de saída permitem que os usuários enviem mensagens de texto de um canal para seus serviços Web. Após a configuração, os usuários podem @mention seu aplicativo e enviar uma mensagem para o serviço externo. Seu serviço tem cinco segundos para enviar uma resposta para a mensagem, potencialmente contendo texto ou um cartão.

Os WebHooks de saída são configurados em uma base por equipe e não podem ser incluídos como parte de um aplicativo de equipes normal.

Confira [criar um webhook de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

### <a name="user-scenarios"></a>Cenários de usuário

Os WebHooks de saída são mais adequados para a conclusão de fluxos de trabalho específicos da equipe que não exigem a coleta ou troca de grandes quantidades de informações.

## <a name="learn-more"></a>Saiba mais

* [Planejar seu aplicativo](../../concepts/extensibility-points.md)
* [Criar seu aplicativo](../../concepts/building-an-app.md)
* [Publicar seu aplicativo](../../concepts/deploy-and-publish/overview.md)
