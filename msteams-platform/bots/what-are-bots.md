---
title: Bots no Microsoft Teams
author: surbhigupta
description: Uma visão geral dos bots Microsoft Teams.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: a9f53654ba3240b973b77c05cd64a22c80237350
ms.sourcegitcommit: a6c39106ccc002d02a65e11627659e0c48981d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62014560"
---
# <a name="bots-in-microsoft-teams"></a>Bots no Microsoft Teams

Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. O uso diário de bots inclui bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem. As interações com bots podem responder e perguntas rápidas ou podem ser uma conversa complexa.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis no Nuvem da Comunidade Governamental (GCC) e não estão disponíveis no GCC-High e departamento de defesa (DOD).

Os bots de conversa permitem que os usuários interajam com seu serviço Web usando texto, cartões interativos e módulos de tarefa.

![Invocar bot usando texto](~/assets/images/invokebotwithtext.png)

![Invocar bot usando cartão](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Os bots de conversa são extremamente flexíveis. Os bots podem manipular alguns comandos básicos ou tarefas complexas que envolvem inteligência artificial e processamento de linguagem natural. Bots podem fazer parte de um aplicativo maior ou ser autônomo.

Use a combinação certa de cartões, texto e módulos de tarefa para criar um bot útil. A imagem a seguir mostra um usuário conversando com um bot em um chat um para um usando texto e cartões interativos.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Exemplo de bot de perguntas frequentes" border="true":::

Cada interação entre o usuário e o bot é representada como uma atividade. Quando um bot recebe uma atividade, ele a passa para seus manipuladores de atividades. Consulte [manipuladores de atividades do bot](~/bots/bot-basics.md).

Bots são aplicativos que têm uma interface de conversa. Você pode interagir com um bot usando texto, cartões interativos e fala. Um bot se comporta de forma diferente em uma conversa de chat de canal ou grupo e em uma conversa um para um. As conversas são manipuladas por meio do conector da Estrutura do Bot. Consulte [noções básicas de conversa](~/bots/how-to/conversations/conversation-basics.md).

Seu bot exige informações contextuais, como detalhes do perfil do usuário para acessar conteúdo relevante e aprimorar a experiência do bot. Consulte [obter Teams contexto](~/bots/how-to/get-teams-context.md).

Você pode enviar e receber arquivos por meio do bot usando Graph APIs ou apIs Teams bot. Consulte [enviar e receber arquivos por meio do bot](~/bots/how-to/bots-filesv4.md).

O limite de taxas é usado para otimizar bots usados para seu Teams aplicativo. Para proteger Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada. Consulte [otimizar seu bot com limitação de taxa em Teams](~/bots/how-to/rate-limit.md).

Com as APIs Graph Microsoft para chamadas e reuniões online, Microsoft Teams aplicativos agora podem interagir com os usuários usando voz e vídeo. Consulte [bots de chamadas e reuniões.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

Você pode usar as APIs Teams bot para obter informações para membros de um chat ou equipe. Consulte [alterações nas APIs Teams bot para buscar membros de equipe ou chat.](~/resources/team-chat-member-api-changes.md)

<!--- TBD: For quick scanning, see if the above information can be itemized as a list.
--->

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Bots e SDKs](~/bots/bot-features.md)

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C # | Node.js |
|----------------|-----------------|--------------|--------------|
| Lembrete de tarefa diária do bot| Demonstre como agendar uma tarefa recorrente e obter um lembrete em um horário agendado. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/nodejs) |

## <a name="see-also"></a>Confira também

* [Criar um bot para o Teams](~/bots/how-to/create-a-bot-for-teams.md)
* [Registrar chamadas e reuniões bot para Microsoft Teams](~/bots/calls-and-meetings/registering-calling-bot.md)
* [Adicionar autenticação ao seu Teams bot](~/bots/how-to/authentication/add-authentication.md)
* [Manipuladores de atividade de bot](~/bots/bot-basics.md)
* [Eventos de conversa em seu bot do Teams](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
