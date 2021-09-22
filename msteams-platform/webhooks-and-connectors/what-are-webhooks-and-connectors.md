---
title: Webhooks e conectores
author: clearab
description: Entenda como webhooks e conectores podem conectar seus serviços Web ao Teams cliente.
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3b7dd6b907ec1af0467c40bda53422cc75e503bc
ms.sourcegitcommit: 8feddafb51b2a1a85d04e37568b2861287f982d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2021
ms.locfileid: "59475752"
---
# <a name="webhooks-and-connectors"></a>Webhooks e conectores

Webhooks e conectores ajudam a conectar os serviços Web a canais e equipes em Microsoft Teams. Webhooks são retorno de chamada HTTP definido pelo usuário que notifica os usuários sobre qualquer ação que tenha sido realizada no canal Microsoft Teams usuário. É uma maneira de um aplicativo obter dados em tempo real. Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web. Eles expõem um ponto de extremidade HTTPS para seu serviço postar mensagens na forma de cartões.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Webhooks ajudam a Teams se integrar com aplicativos externos. Com Webhooks de saída, você pode enviar mensagens de texto de um canal para os serviços Web. Depois de configurar os Webhooks de saída, os usuários podem @mention Webhook de saída e enviar uma mensagem para os serviços Web. O serviço responde dentro de dez segundos à mensagem com um texto ou um cartão.

> [!NOTE]
> Os Webhooks de saída são configurados por equipe e não podem ser incluídos como parte de um aplicativo Teams normal.

## <a name="connectors"></a>Conectores

Os conectores permitem que os usuários assinem para receber notificações e mensagens dos serviços Web. Eles expõem o ponto de extremidade HTTPS para que o serviço poste mensagens Teams canais, normalmente na forma de cartões.

### <a name="incoming-webhooks"></a>Webhooks de entrada

Webhooks de entrada ajudam a postar mensagens de aplicativos para Teams. Se os Webhooks de entrada estão habilitados para uma equipe em qualquer canal, ele expõe o ponto de extremidade HTTPS, que aceita o JSON formatado corretamente e insere as mensagens nesse canal. Por exemplo, você pode criar um Webhook de entrada em seu canal DevOps, configurar sua com build e, simultaneamente, implantar e monitorar serviços para enviar alertas.

### <a name="office-365-connectors"></a>Conectores de Office 365

Office 365 Os conectores permitem que você crie uma página de configuração personalizada para seu Webhook de Entrada e empacote-os como parte de um Teams app. Você envia mensagens principalmente usando Office 365 conector e tem a capacidade de adicionar um conjunto limitado de ações de cartão a eles. Por exemplo, um conector de clima que permite que os usuários selecionem um local e uma hora do dia, para receber atualizações sobre o clima de amanhã. Eles são configurados em um nível de canal, mas são instalados em um nível de equipe.

> [!NOTE]
> Você pode distribuir o Office 365 conector Teams aplicativo para nosso AppStore.

## <a name="create-and-send-messages"></a>Criar e enviar mensagens

As mensagens ativas permitem que os usuários adoeciem sem sair do cliente de email, aumentando o envolvimento do usuário. Com Office 365 e Webhooks de entrada, você pode enviar mensagens postando uma carga JSON na URL do webhook.

## <a name="see-also"></a>Confira também

* [Criar um Webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
