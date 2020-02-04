---
title: O que são WebHooks e conectores?
author: clearab
description: Entenda como os WebHooks e conectores podem conectar seus serviços Web ao cliente do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2be6f82bba0efe05a22a8da9da0acc1e0ad6fa00
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672442"
---
# <a name="what-are-webhooks-and-connectors"></a>O que são WebHooks e conectores?

WebHooks e conectores são uma maneira simples de conectar seus serviços Web a canais e equipes no Microsoft Teams. 

## <a name="outgoing-webhooks"></a>WebHooks de saída

Os WebHooks de saída permitem que os usuários enviem mensagens de texto de um canal para seus serviços Web. Após a configuração, os usuários poderão @mention seu webhook de saída e enviar uma mensagem para o serviço. O serviço terá cinco segundos para enviar uma resposta para a mensagem, potencialmente contendo texto ou um cartão.

Os WebHooks de saída são configurados em uma base por equipe, não podem ser incluídos como parte de um aplicativo de equipes normal. Eles são mais adequados para concluir as cargas de trabalho específicas da equipe que não exigem que grandes quantidades de informações sejam coletadas ou trocadas.

Confira [criar um webhook de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Conectores

Os conectores permitem que os usuários assinem receber notificações e mensagens de seus serviços Web. Eles expõem um ponto de extremidade HTTPS para o seu serviço postar mensagens para-normalmente na forma de cartões.

### <a name="incoming-webhooks"></a>WebHooks de entrada

Os WebHooks de entrada são um tipo de conector mais simples. Para qualquer canal no Team (se eles estiverem habilitados para essa equipe), você pode optar por expor um ponto de extremidade HTTPS que aceitará corretamente o JSON e inserir mensagens nesse canal. Eles são uma maneira rápida e fácil de conectar um canal ao seu serviço e são mais usados para cenários que são exclusivos para uma equipe específica. Por exemplo, você pode criar um webhook de entrada no seu canal do DevOps e configurar seus serviços de compilação, implantação e monitoramento para enviar alertas.

Confira [criar um webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Conectores de Office 365

Os conectores do Office 365 permitem criar uma página de configuração personalizada para o webhook de entrada e empacotá-los como parte de um aplicativo do teams. Em seguida, você pode distribuir esse aplicativo de forma mais ampla, ou até mesmo a nossa loja de aplicativos. Você envia mensagens principalmente usando cartões de conector do Office 365 e também tem a capacidade de adicionar um conjunto limitado de ações de cartão a eles. Um bom exemplo disso é um conector meteorológico que permite que os usuários escolham um local e hora do dia para receber atualizações sobre o clima de amanhã. Eles são configurados em um nível de canal, mas são instalados em nível de equipe.

Confira [criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md).