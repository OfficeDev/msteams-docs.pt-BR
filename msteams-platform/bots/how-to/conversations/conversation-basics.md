---
title: Noções básicas sobre conversas
description: Introdução às conversas de bot em um canal, chat pessoal e um ambiente de chat em grupo.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
keyword: conversations basics messages groupchap group channel
ms.openlocfilehash: ec8e5b2d632912aac6cc9e1e06e6db3a7f1ed948
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887438"
---
# <a name="conversation-basics"></a>Noções básicas sobre conversas

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre seu Microsoft Teams bot e um ou mais usuários. A tabela a seguir fornece os três tipos de conversas, também chamados de escopos Teams:

| Tipo de conversa | Descrição |
| ------- | ----------- |
| `channel` | Esse tipo de conversa é visível para todos os membros do canal. |
| `personal` | Esse tipo de conversa inclui conversas entre bots e um único usuário. |
| `groupChat` | Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários. Ele também habilita seu bot em chats de reunião. |

Um bot se comporta de forma diferente, dependendo da conversa em que ele está envolvido:

* Bots nas conversas de chat de canal e grupo exigem que o usuário @mencione o bot para invocá-lo em um canal.

* Os bots em uma conversa um para um não exigem um @mention. Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.

> [!NOTE]
> Os bots podem ser habilitados para receber todas as mensagens de canal em uma equipe sem @mentioned usando permissões RSC (consentimento específico do recurso). Esse recurso está disponível apenas na [visualização de desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md) público. Para obter mais informações, [consulte receive all channel messages with RSC](channel-messages-with-rsc.md).

Para que o bot funcione em uma determinada conversa ou escopo, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).

Cada mensagem em uma conversa bot é `Activity` um objeto do tipo `messageType: message` . Quando um usuário envia uma mensagem, Teams a mensagem para o bot e o bot lida com a mensagem. Além disso, para definir os comandos principais aos quais o bot responde, você pode adicionar um menu de comando com uma lista lista de comandos suspensos para seu bot. Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname. Teams envia notificações ao bot para eventos de conversa que ocorrem em escopos onde o bot está ativo. Você pode capturar esses eventos em seu código e tomar medidas sobre eles.

Um bot também pode enviar mensagens proativas aos usuários. Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Você pode formatar suas mensagens bot para incluir cartões rich que incluem elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante. O Bot pode atualizar dinamicamente as mensagens depois de enviá-las, em vez de ter suas mensagens como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mensagens em conversas de bot](~/bots/how-to/conversations/conversation-messages.md)
