---
title: Bots no Microsoft Teams
author: surbhigupta
description: Com esse roteiro de aprendizagem, comece a usar bots de conversa no Microsoft Teams e seus exemplos de código.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: 13f966d8c01cb6dcc9dc88fadaeb8ad0d348a2ff
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143708"
---
# <a name="bots-in-microsoft-teams"></a>Bots no Microsoft Teams

Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. O uso diário de bots inclui bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem. As interações com bots podem ser perguntas e respostas rápidas ou conversas complexas.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis na Nuvem da Comunidade Governamental (GCC) e no GCC-High, mas não no Departamento de Defesa (DOD).
> 
> Os aplicativos de bot no Microsoft Teams estão disponíveis no GCC-High através do [Serviço de bot do Azure](/azure/bot-service/channel-connect-teams).

Os bots de conversas permitem que os usuários interajam com seu serviço Web usando texto, cartões interativos e módulos de tarefa.

:::image type="content" source="../assets/images/invokebotwithtext.png" alt-text="Serviço da Web usando texto"lightbox="../assets/images/invokebotwithtext.png":::

:::image type="content" source="../assets/images/invokebotwithcard.png" alt-text="serviço web usando cartões interativos"lightbox="../assets/images/invokebotwithcard.png"border="true":::

:::image type="content" source="../assets/images/task-module-example.png" alt-text="serviço web usando o módulo de tarefas"lightbox="../assets/images/task-module-example.png"border="true":::

Os bots de conversa são extremamente flexíveis. Os bots podem manipular alguns comandos básicos ou tarefas complexas que envolvem inteligência artificial e processamento de linguagem natural. Os bots podem fazer parte de um aplicativo maior ou ser autônomo.

Use a combinação certa de cartões, texto e módulos de tarefa para criar um bot útil. A imagem a seguir mostra um usuário conversando com um bot em um bate-papo individual usando cartões de texto e interativos.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Exemplo de bot de perguntas frequentes" border="true":::

Cada interação entre o usuário e o bot é representada como uma atividade. Quando um bot recebe uma atividade, ele a passa para seus manipuladores de atividades. Consulte [manipuladores de atividades do bot](~/bots/bot-basics.md).

Bots são aplicativos que têm uma interface de conversa. Você pode interagir com um bot usando texto, cartões interativos e fala. Um bot se comporta de forma diferente em uma conversa de chat de canal ou grupo e em uma conversa individual. As conversas são manipuladas pelo conector da Estrutura do Bot. Consulte [noções básicas de conversa](~/bots/how-to/conversations/conversation-basics.md).

Seu bot exige informações contextuais, como detalhes do perfil do usuário para acessar conteúdo relevante e aprimorar a experiência do bot. Consulte [obter o contexto do Teams](~/bots/how-to/get-teams-context.md).

Você pode enviar e receber arquivos pelo bot usando as APIs do Graph ou as APIs do bot do Teams. Consulte [enviar e receber arquivos pelo bot](~/bots/how-to/bots-filesv4.md).

O limite de taxas é usado para otimizar os bots usados no seu aplicativo do Teams. Para proteger o Microsoft Teams e seus usuários, as APIs do bot fornecem um limite de taxa para solicitações de entrada. Consulte [otimizar seu bot com limitação de taxa no Teams](~/bots/how-to/rate-limit.md).

Com as APIs do Microsoft Graph para chamadas e reuniões online, os aplicativos do Microsoft Teams agora podem interagir com os usuários usando voz e vídeo. Confira [bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

Você pode usar as APIs do bot do Teams para obter informações dos membros de um chat ou equipe. Consulte [alterações nas APIs do bot do Teams para buscar membros de equipe ou chat](~/resources/team-chat-member-api-changes.md).

<!--- TBD: For quick scanning, see if the above information can be itemized as a list.
--->

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Bots e SDKs](~/bots/bot-features.md)

## <a name="code-samples"></a>Exemplos de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Lembrete de tarefa diária do bot| Demonstre como agendar uma tarefa recorrente e obter um lembrete em um horário agendado. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/nodejs) |

## <a name="see-also"></a>Confira também

* [Criar um bot para o Teams](../resources/bot-v3/bots-create.md)
* [Como os bots do Microsoft Teams funcionam](/azure/bot-service/bot-builder-basics-teams)
* [Registrar chamadas e reuniões do bot do Microsoft Teams](~/bots/calls-and-meetings/registering-calling-bot.md)
* [Adicionar autenticação ao seu bot do Teams](~/bots/how-to/authentication/add-authentication.md)
* [Manipuladores de atividade de bot](~/bots/bot-basics.md)
* [Eventos de conversa em seu bot do Teams](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
