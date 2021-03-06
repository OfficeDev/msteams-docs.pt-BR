---
title: Bots no Microsoft Teams
author: surbhigupta
description: Uma visão geral dos bots Microsoft Teams.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 655684ef4f2a93d3f9c3858e3bf5a84eab4bd43c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068971"
---
# <a name="bots-in-microsoft-teams"></a>Bots no Microsoft Teams

Um bot também conhecido como chatbot ou bot de conversa é um aplicativo que executa tarefas automatizadas simples e repetitivas executadas pelos usuários, como atendimento ao cliente ou equipe de suporte. Exemplos de bots no uso diário incluem bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem. A interação com um bot pode ser uma resposta e uma pergunta rápida, ou pode ser uma conversa complexa que fornece acesso aos serviços.

> [!VIDEO https://www.youtube-nocookie.com/embed/zSIysk0yL0Q]

Os bots de conversa permitem aos usuários interagir com o serviço Web por meio de texto, cartões interativos e módulos de tarefas.

![Invocar bot usando texto](~/assets/images/invokebotwithtext.png)

![Invocar bot usando cartão](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Os bots de conversa são extremamente flexíveis e podem ser escopos para lidar com alguns comandos simples ou tarefas complexas, com inteligência artificial e processamento de linguagem natural. Eles podem ser um aspecto de um aplicativo maior ou ser completamente autônomo.

Encontrar a combinação correta de cartões, texto e módulos de tarefa são fundamentais para criar um bot útil. A imagem a seguir mostra um usuário conversando com um bot em um chat um para um usando cartões interativos e de texto:

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Exemplo de bot de perguntas frequentes" border="true":::

Cada interação entre o usuário e o bot é representada como uma atividade. Quando um bot recebe uma atividade, ele a passa para seus manipuladores de atividades. Para obter mais informações, consulte [manipuladores de atividade de bot.](~/bots/bot-basics.md) 

Além disso, os bots são aplicativos que têm uma interface de conversa. Você pode interagir com um bot usando texto, cartões interativos e fala. Um bot se comporta de forma diferente, dependendo se a conversa é um canal ou conversa de chat de grupo, ou é uma conversa um para um. As conversas são manipuladas por meio do conector da Estrutura do Bot. Para obter mais informações, consulte [noções básicas de conversa.](~/bots/how-to/conversations/conversation-basics.md)

Seu bot exige informações contextuais, como detalhes do perfil do usuário para acessar conteúdo relevante e aprimorar a experiência do bot. Para obter mais informações, [consulte obter Teams contexto](~/bots/how-to/get-teams-context.md). 

Você também pode enviar e receber arquivos por meio do bot usando GRAPH APIs ou apIs Teams bot. Para obter mais informações, [consulte enviar e receber arquivos por meio do bot](~/bots/how-to/bots-filesv4.md).

Além disso, o limite de taxa é usado para otimizar bots usados para seu Teams aplicativo. Para proteger Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada. Para obter mais informações, consulte [optimize your bot with rate limiting in Teams](~/bots/how-to/rate-limit.md).

Com as APIs Graph Microsoft para chamadas e reuniões online, Microsoft Teams aplicativos agora podem interagir com os usuários usando voz e vídeo. Para obter mais informações, consulte [chamadas e reuniões bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md). 

Você pode usar as APIs Teams bot para obter informações para um ou mais membros de um chat ou equipe. Para obter mais informações, consulte [alterações nas APIs Teams bot para buscar](~/resources/team-chat-member-api-changes.md)membros de equipe ou chat.

## <a name="see-also"></a>Confira também

[Criar um bot para o Teams](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Bots e SDKs](~/bots/bot-features.md)
