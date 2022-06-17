---
title: Webhooks e conectores
author: clearab
description: Neste módulo, entenda como os webhooks e conectores podem conectar seus serviços Web ao cliente do Teams.
ms.localizationpriority: high
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 604f4bce563957afb477a58d47ef8235e4b5c30d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142175"
---
# <a name="webhooks-and-connectors"></a>Webhooks e conectores

Webhooks e conectores ajudam a conectar os serviços Web a canais e equipes no Microsoft Teams. Webhooks são retornos de chamada HTTP definidos pelo usuário que notificam os usuários sobre qualquer ação tenha ocorrido no canal do Microsoft Teams. É uma maneira de um aplicativo obter dados em tempo real. Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web. Eles expõem um ponto de extremidade HTTPS para o seu serviço postagem mensagens na forma de cartões.

## <a name="outgoing-webhooks"></a>Webhooks de saída

Os webhooks ajudam o Teams a se integrarem a aplicativos externos. Com Webhooks de Saída, você pode enviar mensagens de texto de um canal para os serviços Web. Depois de configurar os Webhooks de Saída, os usuários podem @mencionar Webhooks de Saída e enviar uma mensagem para os serviços Web. O serviço responde em dez segundos à mensagem com um texto ou um cartão.

> [!NOTE]
> Os Webhooks de Saída são configurados por equipe e não podem ser incluídos como parte de um aplicativo normal do Teams.

## <a name="connectors"></a>Conectores

Os conectores permitem que os usuários se inscrevam para receber notificações e mensagens dos serviços Web. Eles expõem o ponto de extremidade HTTPS do serviço para postar mensagens nos canais do Teams, geralmente na forma de cartões.

### <a name="incoming-webhooks"></a>Webhooks recebidos

Os Webhooks Recebidos ajudam a postar mensagens de aplicativos para o Teams. Se os Webhooks de entrada estiverem habilitado para uma equipe em qualquer canal, ele expõe o ponto de extremidade HTTPS, que aceita JSON formatado corretamente e insere as mensagens neste canal. Por exemplo, você pode criar um Webhook de entrada em seu canal DevOps, configurar sua compilação e, simultaneamente, implantar e monitorar serviços para enviar alertas.

### <a name="office-365-connectors"></a>Conectores de Office 365

Os Conectores do Office 365 permitem que você crie uma página de configuração personalizada para seu Webhook de entrada e os empacote como parte de um aplicativo do Teams. Você envia mensagens principalmente usando cartões do Conector do Office 365 e tem a capacidade de adicionar um conjunto limitado de ações de cartão a elas. Por exemplo, um conector meteorológico que permite aos usuários selecionar um local e uma hora do dia, para receber atualizações sobre o clima de amanhã. Eles são configurados em um nível de canal, mas são instalados no nível da equipe.

> [!NOTE]
> Você pode distribuir o aplicativo Conector do Office 365 para nossa AppStore.

## <a name="create-and-send-messages"></a>Criar e enviar mensagens

As mensagens acionáveis permitem que os usuários executem ações sem sair do cliente de email, aumentando o envolvimento do usuário. Com o Office 365 e os Webhooks de Entrada, você pode enviar mensagens publicando uma carga JSON no URL do webhook.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="see-also"></a>Confira também

* [Criar um webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
