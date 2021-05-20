---
title: Combine bots com guias
description: Descreve como usar guias e bots juntos
keywords: equipes bots desenvolvimento de guias
ms.topic: conceptual
localization_priority: Normal
ms.date: 03/15/2018
ms.openlocfilehash: 3273369ad1122355b792dc3d429c3a4eff7e1d47
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566450"
---
# <a name="combine-bots-with-tabs"></a>Combine bots com guias

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots e guias funcionam bem juntos, e muitas vezes são combinados em um único serviço back-end. Esta seção descreve as melhores práticas e padrões comuns para o uso de guias e bots juntos.

## <a name="associating-user-identities-across-bot-and-tab"></a>Associando identidades de usuário em bot e guia

Por exemplo: Suponha que seu aplicativo de guia use um sistema de ID proprietário para proteger seu conteúdo. Suponha que você também tenha um bot que possa interagir com o usuário. Normalmente, você vai querer mostrar conteúdo na guia que é específica para o usuário de visualização. O desafio é que o ID do usuário em seu sistema é provavelmente diferente do Microsoft Teams ID do usuário. Então, como você associa essas duas identidades?
Em geral, a abordagem recomendada é assinar o usuário com o bot usando o mesmo sistema de identidade usado para fornecer autenticação para o conteúdo da guia. Você pode implementar isso através da ação de login, que normalmente faz login no usuário através de um fluxo OAuth.

Esse fluxo funciona melhor se o seu provedor de identidade implementar o protocolo OAuth 2.0. Em seguida, você pode associar o Teams ID do usuário com as credenciais do usuário a partir de seu próprio serviço de identidade.

   ![Associando identidades](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Construindo links profundos para guias em mensagens do seu bot

Você pode querer usar guias para mostrar mais conteúdo do que pode caber dentro de um cartão, ou fornecer uma maneira de completar tarefas complexas de preenchimento de formulários usando a tela de guia. Por exemplo, considere navegar o usuário até a guia quando ele ou ela clicar no cartão do seu bot. Para que isso aconteça, você precisará codificar a mensagem do seu bot para incluir uma URL de [link profundo,](~/concepts/build-and-test/deep-links.md) seja através da marcação ou como alvo da ação openUrl.

Links profundos dependem de uma entidadeId, que é um valor opaco que mapeia para uma entidade única em seu sistema. Quando a guia é criada, você idealmente armazena algum estado simples, por exemplo, sinalizar em seu backend indicando que a guia foi criada no canal. Quando o seu bot constrói uma mensagem, ele pode atingir a entidadeId associada a essa guia.

> [!NOTE]
> em chats pessoais, pois as guias são "estáticas" e instaladas com o aplicativo, você sempre pode assumir sua existência e, assim, construir links profundos de acordo.

## <a name="sending-notifications-for-tab-updates"></a>Envio de notificações para atualizações de guias

Muitas vezes você vai querer notificar o usuário final sempre que uma atualização ou uma ação do usuário ocorrer em uma guia. Um cenário de exemplo é atribuir uma tarefa ou bilhete a um membro da equipe e, em seguida, notificar esse membro da equipe.

Há duas maneiras de alcançar este cenário:

1. Se você deseja notificar um canal inteiro, seu bot pode postar uma mensagem no canal. Não há como um bot criar proativamente a conversa de guia se ela não foi criada com a guia.

2. Se você deseja notificar apenas o destinatário ou as partes interessadas envolvidas com a ação, seu bot pode enviar uma mensagem de chat pessoal para o usuário. Primeiro, você deve verificar se existe uma conversa pessoal entre o seu bot e o usuário. Se não, você pode ligar `CreateConversation` para iniciar o bate-papo pessoal.

Em ambos os casos, use notificações de eventos com sabedoria e nunca spam o usuário com atualizações desnecessárias.
