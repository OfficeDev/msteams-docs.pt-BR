---
title: Noções básicas sobre conversas
description: Neste módulo, saiba mais sobre o tipo de conversa do bot em um canal, chat pessoal e escopos de chat em grupo no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 23a72486ffb76d207eeabbef23b5ec5238234dc4
ms.sourcegitcommit: b918181217995a47be34632e1051d0f4d4d481b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67321212"
---
# <a name="conversation-basics"></a>Noções básicas sobre conversas

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários. A tabela a seguir fornece os três tipos de conversas, também chamados de escopos no Teams:

| Tipo de conversa | Descrição |
| ------- | ----------- |
| `channel` | Esse tipo de conversa é visível para todos os membros do canal. |
| `personal` | Esse tipo de conversa inclui conversas entre bots e um único usuário. |
| `groupChat` | Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários. Ele também habilita seu bot em chats de reunião. |

Um bot se comporta de maneira diferente, dependendo da conversa em que ele está envolvido:

* Bots nas conversas de chat de canal e grupo exigem que o usuário @mencione o bot para invocá-lo em um canal.

* Os bots em uma conversa um-para-um não exigem um @mention. Todas as mensagens enviadas pelo usuário são encaminhadas para o bot.

> [!NOTE]
> Os bots podem ser habilitados para receber todas as mensagens de canal em uma equipe sem @mentioned permissões de RSC (consentimento específicos do recurso). No momento, esse recurso está disponível somente em [visualização pública do desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md). Para obter mais informações, confira [receber todas as mensagens de canal com o RSC](channel-messages-with-rsc.md).

Para que o bot funcione em uma conversa ou escopo específico, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).

Cada mensagem em uma conversa de bot é um `Activity` objeto do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem em seu bot e o bot manipula a mensagem. Além disso, para definir os comandos principais aos quais o bot responde, você pode adicionar um menu de comandos com uma lista suspensa de comandos para o bot. Os bots em um grupo ou canal só recebem mensagens quando são mencionados o @nomedobot. O Teams envia notificações ao bot de eventos de conversa que ocorrem em escopos onde o bot está ativo. Você pode capturar esses eventos em seu código e tomar medidas sobre eles.

Um bot também pode enviar mensagens proativas aos usuários. Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta a uma solicitação de um usuário. Você pode formatar suas mensagens de bot para incluir cartões avançados que incluem elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante. O bot pode atualizar mensagens dinamicamente depois de enviá-las, em vez de ter suas mensagens como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método `DeleteActivity` do Bot Framework.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mensagens em conversas de bot](~/bots/how-to/conversations/conversation-messages.md)
