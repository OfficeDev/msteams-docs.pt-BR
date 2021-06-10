---
title: Criar abas para conversação
author: laujan
description: Criar chat de sub entidade conversacional para suas guias de canal
keywords: canal de guias do teams configurável
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 4171265a3ef4ad917661e258dd7305f82411c5ef
ms.sourcegitcommit: 118f7261d313feeac5b398fef56a44bd90104b2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2021
ms.locfileid: "52709639"
---
# <a name="create-conversational-tabs"></a>Criar abas para conversação

As sub-entidades de conversação proporcionam uma maneira de permitir que os usuários tenham conversas sobre sub-entidades em sua guia, como tarefas específicas, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade. Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário pode querer uma conversa mais focada. O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou o conteúdo alterado com o tempo, tornando a conversa irrelevante para o conteúdo que está sendo mostrado. As sub-entidades de conversa proporcionam uma experiência de conversa muito mais focada para guias dinâmicas.

As sub-entidades de conversa só têm suporte em canais. No entanto, eles podem ser usados de uma guia pessoal ou estática para criar ou continuar conversas em guias que já *estão* fixadas a um canal. A guia estática é útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.

## <a name="prerequisites"></a>Pré-requisitos

Para dar suporte a sub-entidades de conversação, seu aplicativo Web de tabulação deve ter a capacidade de armazenar um mapeamento entre sub-entidades ↔ conversas em um banco de dados back-end. Forneceremos o , mas será sua responsabilidade armazená-lo e devolvê-lo Teams para que os usuários `conversationId` `conversationId` continuem a conversa.

## <a name="start-a-new-conversation"></a>Iniciar uma nova conversa

Para iniciar uma nova conversa, use a `openConversation()` função. No entanto, iniciar e continuar uma conversa é manipulado por esse método, as entradas para a função mudam dependendo da ação que você deseja tomar. Da perspectiva dos usuários, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**OpenConversation** assume as seguintes entradas para iniciar uma conversa em um canal:

* **subEntityId**: essa é a ID da sua sub-entidade específica. Por exemplo, tarefa-123.
* **entityId**: essa é a ID da instância da guia quando ela foi criada. A ID é importante para se referir à mesma instância de tabulação.
* **channelId**: este é o canal no qual a instância de tabulação reside.
   > [!NOTE]
   > O **channelId** é opcional para guias de canal. No entanto, é recomendável que você queira manter sua implementação entre canais e guias estáticas da mesma forma.
* **title**: Este é o título que é mostrado ao usuário no painel de chat.

A maioria desses valores também pode ser recuperada da `getContext` API.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Isso abrirá o painel de conversa.

![Sub Entidades de Conversação - Iniciar Conversa](~/assets/images/tabs/conversational-subentities/start-conversation.png)

Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversationId**:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

O `conversationReponse` objeto contém informações relacionadas à conversa que acabou de ser iniciada. Recomendamos que você salve todas as propriedades deste objeto de resposta para reutilização posteriormente.

## <a name="continue-a-conversation"></a>Continuar uma conversa

Depois que uma conversa é iniciada, as chamadas subsequentes exigem que você também forneça as mesmas entradas como em Iniciar uma nova conversa de guia de canal , mas também incluir `openConversation()` [a](#Starting a new channel tab conversation) **conversationId**. O painel de conversa é aberto para o usuário com a conversa apropriada em exibição. Os usuários podem ver mensagens novas ou de entrada em tempo real.

![Sub Entidades de Conversação - Continuar Conversa](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a>Aprimorar uma conversa

Por fim, é importante que sua guia consuma [deeplinks para sua sub-entidade](~/concepts/build-and-test/deep-links.md). Por exemplo, o usuário clicando no deeplink da guia da conversa do canal. O comportamento esperado é que você receba o deeplink, abra essa sub entidade e abra o painel de conversa para essa sub-entidade específica.

Para dar suporte a sub-entidades de conversa a partir de sua guia pessoal ou estática, você não precisa alterar nada sobre sua implementação. Só há suporte para conversas in-comodas ou contínuas de guias de canal que já estão fixadas. As guias estáticas de suporte permitem que você forneça um único local para que seus usuários interajam com todas as suas sub-entidades. No entanto, é importante que você salve o , e quando sua guia for originalmente criada em um canal para que você tenha as propriedades certas ao abrir o modo de exibição de conversa em uma guia `subEntityId` `entityId` `channelId` estática.

## <a name="close-a-conversation"></a>Fechar uma conversa

Você pode fechar manualmente o modo de exibição de conversa chamando a `closeConversation()` função.

```javascript
microsoftTeams.conversations.closeConversation();
```

Você também pode escutar um evento quando o exibição de conversa é fechado por um usuário.

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
