---
title: Noções básicas sobre conversas
description: Neste módulo, saiba mais sobre o tipo de conversa de bot em um canal, chat pessoal e escopos de chat em grupo no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: ab27bc6000712cd046d92d9e020bfbe8fa65daa0
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791814"
---
# <a name="conversation-basics"></a>Noções básicas sobre conversas

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários. A tabela a seguir fornece os três tipos de conversas, também chamados de escopos no Teams:

| Tipo de conversa | Descrição |
| ------- | ----------- |
| `channel` | Esse tipo de conversa é visível para todos os membros do canal. |
| `personal` | Esse tipo de conversa inclui conversas entre bots e um único usuário. |
| `groupChat` | Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários. Ele também habilita o bot em chats de reunião. |

Um bot se comporta de forma diferente dependendo da conversa em que está envolvido:

* Bots nas conversas de chat de canal e grupo exigem que o usuário @mencione o bot para invocá-lo em um canal.

* Bots em uma conversa privada não exigem uma @menção. Todas as mensagens enviadas pelas rotas do usuário para o bot.

> [!NOTE]
> Os bots podem ser habilitados para receber todas as mensagens de canal em uma equipe sem serem @mentioned usando permissões RSC (consentimento específico do recurso). No momento, esse recurso está disponível somente em [visualização pública do desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md). Para obter mais informações, confira [receber todas as mensagens de canal com o RSC](channel-messages-with-rsc.md).

Para que o bot funcione em uma conversa ou escopo específico, adicione suporte a esse escopo no [manifesto do aplicativo](~/resources/schema/manifest-schema.md).

Cada mensagem em uma conversa de bot é um `Activity` objeto do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot e o bot manipula a mensagem. Além disso, para definir comandos principais aos quais o bot responde, você pode adicionar um menu de comando com uma lista suspensa de comandos para o bot. Bots em um grupo ou canal só recebem mensagens quando são mencionados @botname. O Teams envia notificações ao bot de eventos de conversa que ocorrem em escopos onde o bot está ativo. Você pode capturar esses eventos em seu código e tomar medidas sobre eles.

Um bot também pode enviar mensagens proativas aos usuários. Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário. Você pode formatar suas mensagens de bot para incluir cartões avançados que incluem elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante. O bot pode atualizar dinamicamente as mensagens depois de enviá-las, em vez de ter suas mensagens como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método `DeleteActivity` do Bot Framework.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mensagens em conversas de bot](~/bots/how-to/conversations/conversation-messages.md)
