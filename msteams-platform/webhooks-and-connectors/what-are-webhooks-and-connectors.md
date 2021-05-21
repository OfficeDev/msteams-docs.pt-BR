---
title: O que são webhooks e conectores?
author: clearab
description: Entenda como webhooks e conectores podem conectar seus serviços Web ao Teams cliente.
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

O webhook de saída permite que os usuários enviem mensagens de texto de um canal para seus serviços da Web. Depois de configurado, os usuários poderão @mention webhook de saída e enviar uma mensagem para seu serviço. Seu serviço terá cinco segundos para enviar uma resposta à mensagem, potencialmente contendo texto ou um cartão.

Os webhooks de saída são configurados por equipe, não podem ser incluídos como parte de um aplicativo Teams normal. Eles são mais adequados para concluir cargas de trabalho específicas da equipe que não exigem grandes quantidades de informações a serem coletadas ou trocadas.

Para obter mais informações, [consulte Create an outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).

## <a name="connectors"></a>Conectores

Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web. Eles expõem um ponto de extremidade HTTPS para o seu serviço postar mensagens - normalmente na forma de cartões.

### <a name="incoming-webhooks"></a>Webhooks de entrada

Webhooks de entrada são o tipo mais simples de conector. Para qualquer canal em equipe (se eles estão habilitados para essa equipe), você pode optar por expor um ponto de extremidade HTTPS que aceitará JSON formatado corretamente e inserirá mensagens nesse canal. Eles são uma maneira rápida e fácil de conectar um canal ao seu serviço e são mais usados para cenários exclusivos de uma determinada equipe. Por exemplo, você pode criar um webhook de entrada em seu canal DevOps e configurar seus serviços de com build, implantação e monitoramento para enviar alertas.

Para obter mais informações, consulte [Create an incoming webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).

### <a name="office-365-connectors"></a>Conectores de Office 365

Office 365 Os conectores permitem que você crie uma página de configuração personalizada para seu webhook de entrada e empacote-os como parte de um Teams app. Em seguida, você pode distribuir esse aplicativo de forma mais ampla ou até mesmo para a nossa loja de aplicativos. Você envia mensagens principalmente usando Office 365 conector e tem a capacidade de adicionar um conjunto limitado de ações de cartão a eles também. Um bom exemplo disso é um conector de clima que permite que os usuários escolham um local e hora do dia para receber atualizações sobre o clima de amanhã. Eles são configurados em um nível de canal, mas são instalados em um nível de equipe.

Para obter mais informações, [consulte Create an Office 365 Connector](~/webhooks-and-connectors/how-to/connectors-creating.md).
