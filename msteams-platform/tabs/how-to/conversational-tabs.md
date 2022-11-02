---
title: Criar abas para conversação
author: surbhigupta
description: Aprenda a criar guias de conversa no Microsoft Teams para iniciar, continuar, aprimorar e fechar uma conversa.
ms.topic: conceptual
ms.author: lomeybur
ms.localizationpriority: high
ms.openlocfilehash: fa54221a413b19704d80ec62feb1cf068e42d1a0
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820119"
---
# <a name="create-conversational-tabs"></a>Criar abas para conversação

As subentidades conversacionais fornecem uma maneira de permitir que os usuários tenham conversas sobre subentidades em sua guia. Como uma tarefa específica, um paciente e uma oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade. Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário requer uma conversa mais focada. O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou porque o conteúdo mudou ao longo do tempo, tornando a conversa irrelevante para o conteúdo mostrado. As subentidades conversacionais fornecem uma experiência de conversa muito mais focada para guias dinâmicas.

As subentidades conversacionais só têm suporte em canais. Eles podem ser usados a partir de uma guia pessoal ou estática para criar ou continuar conversas em guias que já estão fixadas em um canal. A guia estática será útil se você quiser fornecer um local para um usuário exibir e acessar conversas acontecendo em vários canais.

## <a name="prerequisites"></a>Pré-requisitos

Para dar suporte a subentidades de conversa, seu aplicativo Web de guia deve ter a capacidade de armazenar um mapeamento entre conversas de subentidades ↔ em um banco de dados de back-end. O `conversationId` é fornecido, mas você deve armazená-lo e devolvê-lo ao Teams para que `conversationId` os usuários continuem a conversa.

## <a name="start-a-new-conversation"></a>Iniciar uma nova conversa

Para iniciar uma nova conversa, use a `openConversation()` função. Iniciar e continuar uma conversa são todos tratados por esse método. As entradas para a função mudam dependendo de qual ação você deseja tomar, na perspectiva do usuário, isso abre o painel de conversa à direita da tela, seja para iniciar uma conversa ou continuar uma conversa.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** usa as seguintes entradas para iniciar uma conversa em um canal:

* **subEntityId**: A ID de sua sub-entidade específica. Por exemplo, task-123.
* **entityId**: a ID da instância da guia quando ela foi criada. A ID é importante para fazer referência à mesma instância de guia.
* **channelId**: o canal no qual reside a instância da guia.
   > [!NOTE]
   > O **channelId** é opcional para guias de canal. No entanto, é recomendável manter a implementação entre o canal e as guias estáticas da mesma forma.
* **título**: o título que é mostrado ao usuário no painel de chat.

A maioria desses valores também pode ser recuperada da [`app.getContext()`](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-getcontext&preserve-view=true) API (`microsoftTeams.getContext()` no TeamsJS v1). Para obter mais informações, consulte [Interface pageInfo](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-pageinfo&preserve-view=true)

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

A imagem a seguir mostra o painel de conversa:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/start-conversation.png" alt-text="iniciar conversas":::

Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversaId**:

```javascript
⁠microsoftTeams.conversations.openConversation({
    ...,
    onStartConversation: (conversationResponse) => {
        ⁠// console.log(conversationResponse)
    },
});
```

O `conversationResponse` objeto contém informações relacionadas à conversa iniciada. É recomendável que você salve todas as propriedades desse objeto de resposta para uso posterior.

## <a name="continue-a-conversation"></a>Continuar uma conversa

Depois que uma conversa é iniciada, chamadas subsequentes a `openConversation()` serem necessárias, que você também forneça as mesmas entradas que em [iniciar uma nova conversa](#start-a-new-conversation), mas também inclua a **conversationId**. O painel de conversa é aberto para os usuários com a conversa apropriada em exibição. Os usuários podem ver mensagens novas ou de entrada em tempo real.

A imagem a seguir mostra o painel de conversa com a conversa apropriada:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/continue-conversation.png" alt-text="continuar conversas":::

## <a name="enhance-a-conversation"></a>Aprimorar uma conversa

É importante que sua guia inclua [links profundos para sua sub-entidade](~/concepts/build-and-test/deep-links.md). Por exemplo, o usuário selecionando o link profundo da guia chiclet na conversa do canal. O comportamento esperado é receber o link profundo, abrir essa sub entidade e, em seguida, abrir o painel de conversa para essa sub entidade.

Para dar suporte a subentidades de conversa da sua guia pessoal ou estática, você não precisa alterar nada em sua implementação. Só oferecemos suporte a conversas iniciais ou contínuas de guias de canal que já estão fixadas. O suporte a guias estáticas permite que você forneça um único local para que seus usuários interajam com todas as suas subentidades. É importante que você salve o , `entityId`e `channelId` quando sua `subEntityId`guia é originalmente criada em um canal para ter as propriedades certas ao abrir o modo de exibição de conversa em uma guia estática.

## <a name="close-a-conversation"></a>Fechar uma conversa

Você pode fechar manualmente a exibição de conversa chamando a `closeConversation()` função.

```javascript
microsoftTeams.conversations.closeConversation();
```

Você também pode ouvir um evento quando os usuários **selecionarem Fechar (X)** no modo de exibição de conversa.

```javascript
⁠microsoftTeams.conversations.openConversation({
    ...,
    onCloseConversation: (conversationResponse) => {
        ⁠// console.log(conversationResponse)
    },
});
```

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Criar guia Conversacional| Aplicativo de exemplo de guia do Microsoft Teams para demonstrar a guia criar conversa. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/csharp) |  [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/nodejs) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Alterações na margem da guia](~/resources/removing-tab-margins.md)

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../what-are-tabs.md)
* [Criar uma guia pessoal](create-personal-tab.md)
* [Criar uma guia de canal ou guia de grupo](create-channel-group-tab.md)
* [Criar guias com Cartões Adaptáveis](build-adaptive-card-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
