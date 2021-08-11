---
title: Criar abas para conversação
author: surbhigupta
description: Criar chat de sub entidade conversacional para suas guias de canal
keywords: canal de guias do teams configurável
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 6c2574453f00735d4441c389648df375fc1d01046d2c8f558b470efe4f3392ca
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57705098"
---
# <a name="create-conversational-tabs"></a>Criar abas para conversação

As sub-entidades de conversação proporcionam uma maneira de permitir que os usuários tenham conversas sobre sub-entidades em sua guia, como tarefas específicas, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade. Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário exige uma conversa mais focada. O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou porque o conteúdo mudou com o tempo, tornando a conversa irrelevante para o conteúdo que está sendo mostrado. As sub-entidades de conversa proporcionam uma experiência de conversa muito mais focada para guias dinâmicas.

As sub-entidades de conversa só têm suporte em canais. Elas podem ser usadas de uma guia pessoal ou estática para criar ou continuar conversas em guias que já estão fixadas a um canal. A guia estática é útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.

## <a name="prerequisites"></a>Pré-requisitos

Para dar suporte a sub-entidades de conversação, seu aplicativo Web de tabulação deve ter a capacidade de armazenar um mapeamento entre sub-entidades ↔ conversas em um banco de dados back-end. O `conversationId` é fornecido, mas você deve armazená-lo e devolvê-lo Teams para que os `conversationId` usuários continuem a conversa.

## <a name="start-a-new-conversation"></a>Iniciar uma nova conversa

Para iniciar uma nova conversa, use a `openConversation()` função. Iniciar e continuar uma conversa são manipulados por esse método. As entradas para a função mudam dependendo da ação que você deseja tomar. Da perspectiva dos usuários, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**OpenConversation** assume as seguintes entradas para iniciar uma conversa em um canal:

* **subEntityId**: essa é a ID da sua sub-entidade específica. Por exemplo, tarefa-123.
* **entityId**: essa é a ID da instância da guia quando ela foi criada. A ID é importante para se referir à mesma instância de tabulação.
* **channelId**: este é o canal no qual a instância de tabulação reside.
   > [!NOTE]
   > O **channelId** é opcional para guias de canal. No entanto, é recomendável se você quiser manter sua implementação entre canais e guias estáticas da mesma forma.
* **title**: Este é o título que é mostrado ao usuário no painel de chat.

A maioria desses valores também pode ser recuperada da `getContext` API.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

A imagem a seguir mostra o painel de conversa:

![Sub-entidades de conversação - iniciar conversa](~/assets/images/tabs/conversational-subentities/start-conversation.png)

Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversationId**:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

O `conversationResponse` objeto contém informações relacionadas à conversa que foi iniciada. É recomendável que você salve todas as propriedades deste objeto de resposta para uso posterior.

## <a name="continue-a-conversation"></a>Continuar uma conversa

Depois que uma conversa é iniciada, as chamadas subsequentes exigem que você também forneça as mesmas entradas que no início de uma nova conversa , mas também inclua `openConversation()` **a conversationId**. [](#start-a-new-conversation) O painel de conversa é aberto para o usuário com a conversa apropriada em exibição. Os usuários podem ver mensagens novas ou de entrada em tempo real.

A imagem a seguir mostra o painel de conversa com a conversa apropriada:

![Sub-entidades de conversação - continuar a conversa](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a>Aprimorar uma conversa

É importante que sua guia inclua [links profundos para sua sub-entidade](~/concepts/build-and-test/deep-links.md). Por exemplo, o usuário selecionando o deeplink de guia da conversa do canal. O comportamento esperado é receber o deeplink, abrir essa sub-entidade e, em seguida, abrir o painel de conversa para essa sub-entidade.

Para dar suporte a sub-entidades de conversa a partir de sua guia pessoal ou estática, você não precisa alterar nada em sua implementação. Só há suporte para conversas in-comodas ou contínuas de guias de canal que já estão fixadas. As guias estáticas de suporte permitem que você forneça um único local para que seus usuários interajam com todas as sub-entidades. É importante que você salve o , e quando sua guia for originalmente criada em um canal para ter as propriedades certas ao abrir o exibição de conversa em `subEntityId` `entityId` uma guia `channelId` estática.

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

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Alterações na margem da guia](~/resources/removing-tab-margins.md)