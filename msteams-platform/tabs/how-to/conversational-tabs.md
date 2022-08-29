---
title: Criar abas para conversação
author: surbhigupta
description: Aprenda a criar guias de conversa no Microsoft Teams para iniciar, continuar, aprimorar e fechar uma conversa.
ms.topic: conceptual
ms.author: lomeybur
ms.localizationpriority: high
ms.openlocfilehash: 37816fab1f8ca402e806dec3ec5cca77dd15cf95
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450419"
---
# <a name="create-conversational-tabs"></a>Criar abas para conversação

As subentidades de conversa fornecem uma maneira de permitir que os usuários tenham conversas sobre subentidades em sua guia. Como tarefa específica, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade. Um canal tradicional ou guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário requer uma conversa mais focada. O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou porque o conteúdo mudou ao longo do tempo, tornando a conversa irrelevante para o conteúdo mostrado. As subentidades de conversa fornecem uma experiência de conversa muito mais focada para guias dinâmicas.

As subentidades de conversa só têm suporte em canais. Eles podem ser usados de uma guia pessoal ou estática para criar ou continuar conversas em guias que já estão fixadas a um canal. A guia estática será útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.

## <a name="prerequisites"></a>Pré-requisitos

Para dar suporte a subentidades de conversa, seu aplicativo Web de guia deve ter a capacidade de armazenar um mapeamento entre conversas de subentidades ↔ em um banco de dados de back-end. O `conversationId` é fornecido, mas você deve armazená-lo e `conversationId` de volta ao Teams para que os usuários continuem a conversa.

## <a name="start-a-new-conversation"></a>Iniciar uma nova conversa

Para iniciar uma nova conversa, use a `openConversation()` função. Iniciar e continuar uma conversa é tudo tratado por esse método. As entradas para a função mudam dependendo de qual ação você deseja executar, da perspectiva do usuário, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**OpenConversation** usa as seguintes entradas para iniciar uma conversa em um canal:

* **subEntityId**: a ID de sua subentidade específica. Por exemplo, tarefa-123.
* **entityId**: a ID da instância da guia quando ela foi criada. A ID é importante para se referir à mesma instância de tabulação.
* **channelId**: o canal no qual a instância da guia reside.
   > [!NOTE]
   > A **channelId** é opcional para guias de canal. No entanto, é recomendável manter sua implementação entre canais e guias estáticas da mesma forma.
* **título**: o título que é mostrado ao usuário no painel de chat.

A maioria desses valores também pode ser recuperada da [`app.getContext()`](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-getcontext&preserve-view=true) API (`microsoftTeams.getContext()` no TeamsJS v1). Para obter mais informações, consulte [a interface PageInfo](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-pageinfo&preserve-view=true)

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

A imagem a seguir mostra o painel de conversa:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/start-conversation.png" alt-text="iniciar conversas":::

Se o usuário iniciar uma conversa, será importante escutar o retorno de chamada desse evento para recuperar e salvar a **conversationId**:

```javascript
⁠microsoftTeams.conversations.openConversation({
    ...,
    onStartConversation: (conversationResponse) => {
        ⁠// console.log(conversationResponse)
    },
});
```

O `conversationResponse` objeto contém informações relacionadas à conversa que foi iniciada. É recomendável que você salve todas as propriedades desse objeto de resposta para uso posterior.

## <a name="continue-a-conversation"></a>Continuar uma conversa

Depois que uma conversa é iniciada, `openConversation()` as chamadas subsequentes a serem necessárias, que você também fornece as mesmas entradas que no início de uma nova conversa, mas também inclui [a](#start-a-new-conversation) **conversationId**. O painel de conversa é aberto para os usuários com a conversa apropriada em exibição. Os usuários podem ver mensagens novas ou recebidas em tempo real.

A imagem a seguir mostra o painel de conversa com a conversa apropriada:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/continue-conversation.png" alt-text="continuar conversas":::

## <a name="enhance-a-conversation"></a>Aprimorar uma conversa

É importante que sua guia inclua [links profundos para sua subentidade](~/concepts/build-and-test/deep-links.md). Por exemplo, o usuário selecionando o link profundo do tab chiclet na conversa do canal. O comportamento esperado é receber o link profundo, abrir essa subentidade e, em seguida, abrir o painel de conversa para essa subentidade.

Para dar suporte a subentidades de conversa de sua guia pessoal ou estática, você não precisa alterar nada em sua implementação. Só há suporte para iniciar ou continuar conversas de guias de canal que já estão fixadas. O suporte a guias estáticas permite que você forneça um único local para que os usuários interajam com todas as suas subentidades. É importante que você `subEntityId`salve o , `entityId``channelId` e quando sua guia for originalmente criada em um canal para ter as propriedades corretas ao abrir o modo de exibição de conversa em uma guia estática.

## <a name="close-a-conversation"></a>Fechar uma conversa

Você pode fechar manualmente o modo de exibição de conversa chamando a `closeConversation()` função.

```javascript
microsoftTeams.conversations.closeConversation();
```

Você também pode escutar um evento quando os usuários **selecionam Fechar (X)** no modo de exibição de conversa.

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
|Guia Criar Conversa| Aplicativo de exemplo de guia do Microsoft Teams para demonstrar a guia Criar conversa. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/nodejs) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Alterações na margem da guia](~/resources/removing-tab-margins.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
