---
title: O que são webhooks e conectores?
author: clearab
description: Entenda como webhooks e conectores podem conectar seus serviços web ao cliente Teams.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e36b73c0eaed5068311dae6c1ef8fdc073432334
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566800"
---
# <a name="what-are-webhooks-and-connectors"></a>O que são webhooks e conectores?

Os ganchos e conectores da Web são uma maneira simples de conectar seus serviços da Web aos canais e equipes no Microsoft Teams. 

## <a name="outgoing-webhooks"></a>Webhooks de saída

O webhook de saída permite que os usuários enviem mensagens de texto de um canal para seus serviços da Web. Uma vez configurados, seus usuários poderão @mention seu webhook de saída e enviar uma mensagem para o seu serviço. Seu serviço terá cinco segundos para enviar uma resposta à mensagem, potencialmente contendo texto ou cartão.

Os webhooks de saída são configurados por equipe, não podem ser incluídos como parte de um aplicativo de Teams normal. Eles são mais adequados para completar cargas de trabalho específicas da equipe que não requerem grandes quantidades de informações para serem coletadas ou trocadas.

Para obter mais informações, consulte [Criar um webhook de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Conectores

Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web. Eles expõem um ponto final HTTPS para o seu serviço para postar mensagens - normalmente na forma de cartões.

### <a name="incoming-webhooks"></a>Webhooks de entrada

Webhooks de entrada são o tipo mais simples de conector. Para qualquer canal em equipe (se eles estiverem habilitados para essa equipe) você pode optar por expor um ponto final HTTPS que aceitará json corretamente formatado e inserirá mensagens nesse canal. Eles são uma maneira rápida e fácil de conectar um canal ao seu serviço, e são melhor usados para cenários que são exclusivos de uma determinada equipe. Por exemplo, você pode criar um webhook de entrada em seu canal de DevOps e configurar seus serviços de compilação, implantação e monitoramento para enviar alertas.

Para obter mais informações, consulte [Criar um webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Conectores de Office 365

Office 365 Os conectores permitem que você crie uma página de configuração personalizada para o seu webhook de entrada e embale-os como parte de um aplicativo Teams. Em seguida, você pode distribuir esse aplicativo de forma mais ampla, ou até mesmo para a nossa loja de aplicativos. Você envia mensagens principalmente usando Office 365 cartões Connector, e tem a capacidade de adicionar um conjunto limitado de ações de cartão a eles também. Um bom exemplo disso é um conector meteorológico que permite que os usuários escolham um local e hora do dia para receber atualizações sobre o tempo de amanhã. Eles são configurados em um nível de canal, mas são instalados em um nível de equipe.

Para obter mais informações, consulte [Criar um conector de Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md).
