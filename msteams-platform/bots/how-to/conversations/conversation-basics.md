---
title: Noções básicas sobre conversas
description: Introdução às conversas
ms.topic: overview
ms.author: anclear
keyword: conversations basics messages
ms.openlocfilehash: eff1c6fe18f7b2ba082b5075b6c1806f41b68a6b
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996034"
---
# <a name="conversation-basics"></a>Noções básicas sobre conversas

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários. A tabela a seguir fornece os três tipos de conversas, também chamados de escopos no Teams:

| Tipo de conversa | Descrição |
| ------- | ----------- |
| `channel` | Esse tipo de conversa é visível para todos os membros do canal. |
| `personal` | Esse tipo de conversa inclui conversas entre bots e um único usuário. |
| `groupChat` | Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários. Ele também habilita seu bot em chats de reunião. |

Um bot se comporta de forma diferente, dependendo da conversa em que ele está envolvido:

* Bots em conversas de chat de canal e grupo exigem que o usuário @ mencione o bot para invocá-lo em um canal.
* Bots em uma conversa um para um não exigem uma menção @. Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.

Para que o bot funcione em uma determinada conversa ou escopo, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).

Cada mensagem em uma conversa bot é `Activity` um objeto do tipo `messageType: message` . Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot e o bot lida com a mensagem. Além disso, para definir os comandos principais aos quais o bot responde, você pode adicionar um menu de comando com uma lista lista de comandos suspensos para seu bot. Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname. O Teams envia notificações ao bot para eventos de conversa que ocorrem em escopos onde o bot está ativo. Você pode capturar esses eventos em seu código e tomar medidas sobre eles. 

Um bot também pode enviar mensagens proativas aos usuários. Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Você pode formatar suas mensagens bot para incluir cartões rich que incluem elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante. O Bot pode atualizar dinamicamente as mensagens depois de enviá-las, em vez de ter suas mensagens como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mensagens em conversas de bot](~/bots/how-to/conversations/conversation-messages.md)
