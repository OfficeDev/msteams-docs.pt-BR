---
title: Combinar bots com guias
description: Neste artigo, você aprenderá a usar guias e bots juntos, construindo links profundos para guias em mensagens de seu bot e desenvolvimento de guias de bots de equipes
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 03/15/2018
ms.openlocfilehash: f8199b65fded8c43af45cb303a400652e5516db2
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142091"
---
# <a name="combine-bots-with-tabs"></a>Combinar bots com guias

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots e guias funcionam juntos e geralmente são combinados em um único serviço de back-end. Esta seção descreve as práticas recomendadas e os padrões comuns para usar guias e bots juntos.

## <a name="associating-user-identities-across-bot-and-tab"></a>Associando identidades de usuário no bot e na guia

Por exemplo: suponha que seu aplicativo guia use um sistema de ID proprietário para proteger seu conteúdo. Suponha que você também tenha um bot que possa interagir com o usuário. Normalmente, você desejará mostrar o conteúdo na guia que é específico para o usuário de exibição. O desafio é que a ID de usuário em seu sistema provavelmente é diferente da ID Microsoft Teams usuário. Então, como você associa essas duas identidades?
Em geral, a abordagem recomendada é conectar o usuário com o bot usando o mesmo sistema de identidade usado para fornecer autenticação para o conteúdo da guia. Você pode implementar por meio da ação de entrada, que normalmente faz logon no usuário por meio de um fluxo OAuth.

Esse fluxo funcionará melhor se o provedor de identidade implementar o protocolo OAuth 2.0. Em seguida, você pode associar Teams ID de usuário com as credenciais do usuário de seu próprio serviço de identidade.

   ![Associando identidades](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Construindo links profundos para guias em mensagens do bot

Você deseja usar guias para mostrar mais conteúdo do que pode caber dentro de um cartão ou fornecer uma maneira de concluir tarefas complexas de preenchimento de formulário usando a tela da guia. Por exemplo, considere navegar até a guia do usuário quando ele clicar no cartão do bot. Para que isso aconteça, você precisará codificar a mensagem do bot para incluir uma URL de [link](~/concepts/build-and-test/deep-links.md) profundo, seja por meio da marcação ou como o destino da ação openUrl.

Os links profundos dependem de uma entityId, que é um valor opaco que mapeia para uma entidade exclusiva em seu sistema. Quando a guia é criada, o ideal é armazenar algum estado simples. Por exemplo, sinalizador no back-end indicando que a guia foi criada no canal. Quando o bot constrói uma mensagem, ele pode direcionar a entityId associada a essa guia.

> [!NOTE]
> em chats pessoais, como as guias são "estáticas" e instaladas com o aplicativo, você sempre pode assumir sua existência e, portanto, construir links profundos adequadamente.

## <a name="sending-notifications-for-tab-updates"></a>Enviar notificações para atualizações de tabulação

Muitas vezes, você desejará notificar o usuário final sempre que uma atualização ou uma ação do usuário ocorrer em uma guia. Um cenário de exemplo é atribuir uma tarefa ou tíquete a um colega membro da equipe e notificar esse membro da equipe.

Há duas maneiras de alcançar esse cenário:

1. Se você quiser notificar um canal inteiro, o bot poderá postar uma mensagem de forma assíncrona no canal. Não há como um bot criar proativamente a conversa de tabulação se ela não tiver sido criada com a guia.

2. Se você quiser apenas notificar o destinatário ou as partes interessadas envolvidas na ação, seu bot poderá enviar uma mensagem de chat pessoal para o usuário. Primeiro, você deve verificar se existe uma conversa pessoal entre o bot e o usuário. Caso contrário, você pode ligar `CreateConversation` para iniciar o chat pessoal.

Em ambos os casos, use notificações de eventos com sabedoria e nunca crie spam para o usuário com atualizações desnecessárias.
