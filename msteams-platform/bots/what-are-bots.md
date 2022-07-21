---
title: Bots no Microsoft Teams
author: surbhigupta
description: Com esse roteiro de aprendizagem, comece a usar bots de conversa no Microsoft Teams e seus exemplos de código.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: f04f41ac100f243f7560f63364475cd877cf7bf3
ms.sourcegitcommit: eb480bf056a46837d18b4ea35e465486cc68f981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66912258"
---
# <a name="build-bots-for-teams"></a>Criar bots para o Teams

Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. O uso diário de bots inclui bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem. As interações com bots podem ser perguntas e respostas rápidas ou conversas complexas.

> [!IMPORTANT]
>
> * Atualmente, os bots estão disponíveis na Nuvem da Comunidade Governamental (GCC) e no GCC-High, mas não no Departamento de Defesa (DOD).
>
> * Os aplicativos de bot no Microsoft Teams estão disponíveis no GCC-High através do [Serviço de bot do Azure](/azure/bot-service/how-to-deploy-gov-cloud-high) e o registro do canal de bot deve ser feito no portal do Azure Governamental.
>
> * Os aplicativos no GCCH suportam apenas até a versão v1.10 do manifesto. Não há suporte para URLs de imagem em Cartões Adaptáveis no ambiente GCCH. Você pode substituir uma URL de imagem por uma DataUri codificada em Base64.

Os bots de conversas permitem que os usuários interajam com seu serviço Web usando texto, cartões interativos e módulos de tarefa.

:::image type="content" source="../assets/images/invokebotwithtext.png" alt-text="Serviço da Web usando texto"lightbox="../assets/images/invokebotwithtext.png":::

:::image type="content" source="../assets/images/invokebotwithcard.png" alt-text="serviço web usando cartões interativos"lightbox="../assets/images/invokebotwithcard.png"border="true":::

:::image type="content" source="../assets/images/task-module-example.png" alt-text="serviço web usando o módulo de tarefas"lightbox="../assets/images/task-module-example.png"border="true":::

Os bots de conversa são extremamente flexíveis. Os bots podem manipular alguns comandos básicos ou tarefas complexas que envolvem inteligência artificial e processamento de linguagem natural. Os bots podem fazer parte de um aplicativo maior ou ser autônomo.

Use a combinação certa de cartões, texto e módulos de tarefa para criar um bot útil. A imagem a seguir mostra um usuário conversando com um bot em um bate-papo individual usando cartões de texto e interativos.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Exemplo de bot de perguntas frequentes":::

Cada interação entre o usuário e o bot é representada como uma atividade. Quando um bot recebe uma atividade, ele a passa para seus manipuladores de atividades. Consulte [manipuladores de atividades do bot](~/bots/bot-basics.md).

Bots são aplicativos que têm uma interface de conversa. Você pode interagir com um bot usando texto, cartões interativos e fala. Um bot se comporta de forma diferente em uma conversa de chat de canal ou grupo e em uma conversa individual. As conversas são manipuladas pelo conector da Estrutura do Bot. Consulte [noções básicas de conversa](~/bots/how-to/conversations/conversation-basics.md).

Seu bot exige informações contextuais, como detalhes do perfil do usuário para acessar conteúdo relevante e aprimorar a experiência do bot. Consulte [obter o contexto do Teams](~/bots/how-to/get-teams-context.md).

Você pode enviar e receber arquivos pelo bot usando as APIs do Graph ou as APIs do bot do Teams. Consulte [enviar e receber arquivos pelo bot](~/bots/how-to/bots-filesv4.md).

O limite de taxas é usado para otimizar os bots usados no seu aplicativo do Teams. Para proteger o Teams e seus usuários, as APIs do bot fornecem um limite de taxa para solicitações de entrada. Consulte [otimizar seu bot com limitação de taxa no Teams](~/bots/how-to/rate-limit.md).

Com as APIs do Microsoft Graph para chamadas e reuniões online, os aplicativos do Teams já podem interagir com os usuários usando voz e vídeo. Consulte [bots de chamadas e reuniões](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

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
