---
title: Webhooks e conectores
author: clearab
description: Neste módulo, entenda como os webhooks e conectores podem conectar seus serviços Web ao cliente do Teams.
ms.localizationpriority: high
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: bb453367eb0d8f4c2c1a54681d67dc38fb3e0358
ms.sourcegitcommit: ef545fac5c0dbe970d81f53b1631930e9196eba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67991646"
---
# <a name="webhooks-and-connectors"></a>Webhooks e conectores

Webhooks e conectores ajudam a conectar os serviços Web a canais e equipes no Microsoft Teams. Webhooks são retornos de chamada HTTP definidos pelo usuário que notificam os usuários sobre qualquer ação tenha ocorrido no canal do Teams. É uma maneira de um aplicativo obter dados em tempo real. Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web. Eles expõem um ponto de extremidade HTTPS para o seu serviço postagem mensagens na forma de cartões.

> [!IMPORTANT]
> Você pode optar por criar um aplicativo do Teams do bot de notificação diferente dos webhooks de entrada. Eles têm um desempenho semelhante, mas o bot de notificação tem mais funcionalidades. Para obter mais informações, consulte [Criar um bot de notificação com JavaScript ou](../sbs-gs-notificationbot.yml) um exemplo [de notificação de webhook de entrada](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/incoming-webhook-notification). Para começar, baixe o [Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) agora e explore. Para obter mais informações, consulte [documentos do Kit de Ferramentas do Teams](../toolkit/teams-toolkit-fundamentals.md).

## <a name="outgoing-webhooks"></a>Webhooks de saída

Os webhooks ajudam o Teams a se integrarem a aplicativos externos. Com Webhooks de Saída, você pode enviar mensagens de texto de um canal para os serviços Web. Depois de configurar os Webhooks de Saída, os usuários podem @mencionar Webhooks de Saída e enviar uma mensagem para os serviços Web. O serviço responde dentro de 10 segundos à mensagem com um texto ou um cartão.

> [!NOTE]
> Os Webhooks de Saída são configurados por equipe e não podem ser incluídos como parte de um aplicativo normal do Teams.

## <a name="connectors"></a>Conectores

Os conectores permitem que os usuários se inscrevam para receber notificações e mensagens dos serviços Web. Eles expõem o ponto de extremidade HTTPS do serviço para postar mensagens nos canais do Teams, geralmente na forma de cartões.

### <a name="incoming-webhooks"></a>Webhooks recebidos

Os Webhooks Recebidos ajudam a postar mensagens de aplicativos para o Teams. Se os Webhooks de entrada estiverem habilitado para uma equipe em qualquer canal, ele expõe o ponto de extremidade HTTPS, que aceita JSON formatado corretamente e insere as mensagens neste canal. Por exemplo, você pode criar um Webhook de entrada em seu canal DevOps, configurar sua compilação e, simultaneamente, implantar e monitorar serviços para enviar alertas.

#### <a name="notification-bot-or-incoming-webhook---choose-the-right-one"></a>Bot de notificação ou webhook de entrada – escolha o certo

Antes de começar a aprender a criar webhooks de entrada, talvez você também queira saber que pode criar o Bot de Notificação usando o Kit de Ferramentas do Teams. Os Bots de Notificação podem habilitar uma experiência mais personalizável para atender a diferentes cenários de negócios.

Saiba mais sobre as diferenças entre o Bot de Notificação e o webhook de entrada para que você possa escolher soluções corretas para seus cenários:

| &nbsp; | Bot de notificação |  Webhook de entrada |
| --- | --- | --- |
| O que é isso? | Um aplicativo do Teams | Um recurso do Teams |
| Instalação necessária | Sim | Não |
| Cenários adequados | • Receber notificações e mensagens regulares periodicamente, por exemplo, receber notificações diárias das tarefas da equipe. <br>  • Receber notificações e mensagens com base em eventos reais. Por exemplo, depois que os colegas de equipe carregam arquivos, você recebe notificações. | Comunique-se com aplicativos externos e receba notificações e mensagens de outros aplicativos. |
| Configuração de escopo | • Canal do Teams <br> • Chat em grupo <br> • Chat pessoal | Canal do Teams |
| Processo de mensagem | Um Bot de Notificação funciona como um aplicativo do Teams. Você pode definir sua lógica de negócios para processar dados e mostrar dados em um formato personalizado. | O Webhook é um recurso do Teams em vez de um aplicativo do Teams, portanto, ele só recebe e mostra dados sem processamento. |
| Recuperar contexto do Teams | O Bot de Notificação pode recuperar o contexto do Teams, como as informações do canal ou do usuário, mensagens etc. | Não |
| Enviar Cartão Adaptável | Sim | Sim |
| Enviar uma mensagem de boas-vindas | Pode enviar uma mensagem de boas-vindas | Nenhuma mensagem de boas-vindas |
| Gatilho com suporte | Todos os gatilhos compatíveis. Se você usar o Kit de Ferramentas do Teams, poderá obter rapidamente projetos de modelo com os seguintes gatilhos: <br> • Gatilho de tempo hospedado nas funções do Azure. <br> • Restify o gatilho HTTP hospedado no serviço de aplicativo do Azure <br> • Gatilho HTTP hospedado no Azure Functions | Todos os gatilhos com suporte |
| Ferramentas de Compilação | • [Visão geral do Kit de Ferramentas do Teams para Visual Studio Code](../toolkit/teams-toolkit-fundamentals.md) <br> • [Visão geral do Kit de Ferramentas do Teams para Visual Studio](../toolkit/teams-toolkit-fundamentals.md) <br> • [Biblioteca teamsFx](../toolkit/TeamsFx-CLI.md) <br> • [SDK do TeamsFx](../toolkit/TeamsFx-SDK.md) | Nenhuma ferramenta é necessária |
| Recurso de nuvem necessário | Azure Bot Framework | Nenhum recurso necessário |
| Tutorial | [Compilar um bot de notificação com JavaScript](../sbs-gs-notificationbot.yml) | [exemplo de notificação de webhook de entrada](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/incoming-webhook-notification) |

### <a name="office-365-connectors"></a>Conectores de Office 365

Os Conectores do Office 365 permitem que você crie uma página de configuração personalizada para seu Webhook de entrada e os empacote como parte de um aplicativo do Teams. Você envia mensagens principalmente usando cartões do Conector do Office 365 e tem a capacidade de adicionar um conjunto limitado de ações de cartão a elas. Por exemplo, um conector meteorológico que permite que os usuários selecionem um local e qualquer hora do dia para receber atualizações sobre o clima de amanhã. Eles são configurados no nível do canal, mas são instalados no nível da equipe.

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
* [Compilar um bot de notificação com JavaScript](../sbs-gs-notificationbot.yml)
* [Crie seu primeiro aplicativo de bot usando JavaScript](../sbs-gs-bot.yml)
