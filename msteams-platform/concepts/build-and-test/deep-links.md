---
title: Criar links de fundo
description: Descreve links aprofundados e como usá-los em seus aplicativos
keywords: deeplink de link profundo do teams
ms.openlocfilehash: 03580c4d15c82da70402d68d85b0d28f8afa670e
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796327"
---
# <a name="create-deep-links-to-content-and-features-in-microsoft-teams"></a>Criar links detalhados para conteúdo e recursos no Microsoft Teams

Você pode criar links para informações e recursos dentro do cliente do teams. Exemplos de onde isso pode ser útil:

* Navegar o usuário para o conteúdo em uma das guias do seu aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário sobre uma atividade importante. Quando o usuário toca na notificação, o link profundo navega para a guia para que o usuário possa exibir mais detalhes sobre a atividade.
* O aplicativo automatiza ou simplifica determinadas tarefas do usuário, como criar um chat ou agendar uma reunião, preenchendo os links detalhados com os parâmetros necessários. Isso evita a necessidade de que os usuários insiram informações manualmente.

## <a name="deep-linking-to-your-tab"></a>Vinculação profunda à sua guia

Você pode criar links de profunda para entidades no Microsoft Teams. Normalmente, isso é usado para criar links que navegam para conteúdo e informações dentro da sua guia. Por exemplo, se sua guia contiver uma lista de tarefas, os membros da equipe poderão criar e compartilhar links para tarefas individuais. Quando clicado, o link navega até sua guia que se concentra no item específico. Para implementá-lo, você deve adicionar uma ação de "Copiar link" a cada item, de qualquer forma mais adequada à sua interface do usuário. Quando o usuário executa essa ação, você chama `shareDeepLink()` para exibir uma caixa de diálogo contendo um link que o usuário pode copiar para a área de transferência. Ao fazer essa chamada, você também passa uma ID para o seu item, que você recebe no [contexto](~/tabs/how-to/access-teams-context.md) quando o link é seguido e sua guia é recarregada.

Como alternativa, você também pode gerar links detalhados programaticamente, usando o formato especificado mais adiante neste tópico. Você pode querer usá-los nas mensagens de [bot](~/bots/what-are-bots.md) e de [conexão](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) que informam aos usuários sobre as alterações na sua guia ou nos itens dela.

> [!NOTE]
> Isso é diferente dos links fornecidos pelo item de menu **Copiar link para guia** , que apenas gera um link profundo que aponta para essa guia.

### <a name="showing-a-deep-link-to-an-item-within-your-tab"></a>Mostrando um link profundo para um item na sua guia

Para mostrar uma caixa de diálogo que contém um link profundo a um item na sua guia, chame `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`

Forneça estes campos:

* `subEntityId`&emsp;Um identificador exclusivo para o item na sua guia para o qual você está vinculado de forma profunda
* `subEntityLabel`&emsp;Um rótulo para o item a ser usado para exibir o link profundo
* `subEntityWebUrl`&emsp;Um campo opcional com uma URL de fallback a ser usada se o cliente não tiver suporte para renderizar a guia

### <a name="generating-a-deep-link-to-your-tab"></a>Gerando um link profundo para sua guia

> [!NOTE]
> Guias estáticas têm um escopo de guias "pessoal" e configuráveis têm um escopo de "equipe". Os dois tipos de guia têm uma sintaxe levemente diferente, pois somente a guia configurável tem uma `channel` propriedade associada ao objeto Context. Consulte a referência do [manifesto](~/resources/schema/manifest-schema.md) para obter mais informações sobre escopos pessoais e de equipe.
> [!NOTE]
> Os links profundos funcionarão corretamente somente se a guia tiver sido configurada usando a biblioteca v 0,4 ou posterior e por ter uma ID de entidade. Os links de profundidade para guias sem IDs de entidade ainda navegam até a guia, mas não podem fornecer a ID de subentidade para a guia.

Use este formato para um link profundo que você pode usar em um bot, conector ou uma placa de extensão de mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

Os parâmetros de consulta são:

* `appId`&emsp;A ID do manifesto; por exemplo, "fe4a8eba-2a31-4737-8E33-e5fae6fee194"
* `entityId`&emsp;A ID do item na guia, que você forneceu ao [Configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md); por exemplo, "tasklist123"
* `entityWebUrl`ou `subEntityWebUrl` &emsp; um campo opcional com uma URL de fallback a ser usado se o cliente não tiver suporte para renderizar a guia; por exemplo, " https://tasklist.example.com/123 " ou " https://tasklist.example.com/list123/task456 "
* `entityLabel`ou `subEntityLabel` &emsp; um rótulo para o item na sua guia, para usar ao exibir o link profundo; por exemplo, "lista de tarefas 123" ou "tarefa 456"
* `context`&emsp;Um objeto JSON que contém os seguintes campos:
  * `subEntityId`&emsp;Uma ID para o item _dentro_ da guia; por exemplo, "task456"
  * `channelId`&emsp;O Microsoft Teams Channel ID (disponível no [contexto](~/tabs/how-to/access-teams-context.md)da guia; por exemplo, "19: cbe3683f25094106b826c9cada3afbe0@thread. Skype". Esta propriedade só está disponível em guias configuráveis com um escopo de "equipe". Ele não está disponível em guias estáticas, que têm um escopo de "pessoal".

Exemplos:

* Vincular a uma guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Vincular a um item de tarefa na guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Vincular a uma guia estática em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Vincular a um item de tarefa na guia estática: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Certifique-se de que todos os parâmetros de consulta são codificados corretamente com URI. Para facilitar a leitura, os exemplos acima não estão, mas você deve. Usando o último exemplo:
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consuming-a-deep-link-from-a-tab"></a>Consumindo um link profundo de uma guia

Ao navegar para um link profundo, o Microsoft Teams simplesmente navega até a guia e fornece um mecanismo por meio da biblioteca JavaScript do Microsoft Teams para recuperar a ID da subentidade (se ela existir).

A [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) chamada retorna um contexto que inclui o `subEntityId` campo se a guia foi navegada por meio de um link profundo.

## <a name="deep-linking-from-your-tab"></a>Vinculação profunda da sua guia

Você pode fazer o deeplink para conteúdo no Microsoft Teams na sua guia. Isso é útil se sua guia precisa vincular a outro conteúdo no Microsoft Teams, como um canal, mensagem, outra guia ou até abrir uma caixa de diálogo de agendamento. Para acionar um deeplink da sua guia, você deve chamar:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Isso navegará até a URL correta ou disparará uma ação de cliente, como abrir uma caixa de diálogo de instalação de agendamento ou de aplicativo. Exemplo:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Vinculação profunda a um chat

Você pode criar links de fundo para chats privados entre usuários especificando o conjunto de participantes. Se um chat não existir com os participantes especificados, o link navegará o usuário para um novo chat vazio. Novos chats serão criados no estado de rascunho até que o usuário envie a primeira mensagem. Opcionalmente, você pode especificar o nome do chat (se ele ainda não existir), junto com o texto que deve ser inserido na caixa de composição do usuário. Você pode pensar nesse recurso como um atalho para o usuário realizar a ação manual de navegar para ou criar o chat e, em seguida, digitar a mensagem.

Como um caso de uso de exemplo, se você estiver retornando um perfil de usuário do Office 365 do seu bot como um cartão, esse link profundo poderá permitir que o usuário Converse facilmente com essa pessoa.

### <a name="generating-a-deep-link-to-a-chat"></a>Gerando um link profundo para um chat

Use este formato para um link profundo que você pode usar em um bot, conector ou uma placa de extensão de mensagens:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`&emsp;A lista separada por vírgulas de IDs de usuário que representam os participantes do chat. O usuário que executa a ação sempre é incluído como um participante. No momento, o campo de ID do usuário oferece suporte somente ao Microsoft Azure AD UserPrincipalName (normalmente, um endereço de email).
* `topicName`&emsp;Um campo opcional para o nome de exibição do chat, no caso de um chat com três ou mais usuários. Se esse campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`&emsp;Um campo opcional para o texto da mensagem que você deseja inserir na caixa de composição do usuário atual enquanto o chat estiver em um estado de rascunho.

Para usar esse link profundo com seu bot, você pode especificá-lo como o destino da URL no botão do cartão ou tocar a ação através do `openUrl` tipo de ação.

## <a name="linking-to-the-scheduling-dialog"></a>Vincular à caixa de diálogo de agendamento

> [!Note]
> No momento, este recurso está no Developer Preview.

Você pode criar links de profunda para a caixa de diálogo de agendamento interno do cliente do teams. Isso é especialmente útil se o seu aplicativo ajuda o usuário a concluir o calendário ou tarefas relacionadas a agendamento.

### <a name="generating-a-deep-link-to-the-scheduling-dialog"></a>Gerando um link profundo para a caixa de diálogo de agendamento

Use este formato para um link profundo que você pode usar em um bot, conector ou uma placa de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Os parâmetros de consulta são:

* `attendees`&emsp;A lista separada por vírgulas opcional de IDs de usuário que representam os participantes da reunião. O usuário que executa a ação é o organizador da reunião. No momento, o campo de ID do usuário oferece suporte somente ao Microsoft Azure AD UserPrincipalName (normalmente, um endereço de email).
* `startTime`&emsp;A hora de início opcional do evento. Deve estar no [formato ISO 8601 longo](https://en.wikipedia.org/wiki/ISO_8601), por exemplo "2018-03-12T23:55:25 + 02:00".
* `endTime`&emsp;A hora de término opcional do evento, também no formato ISO 8601.
* `subject`&emsp;Um campo opcional para o assunto da reunião.
* `content`&emsp;Um campo opcional para o campo detalhes da reunião.

No momento, não há suporte para a especificação do local. Ao gerar os horários de início e término, certifique-se de especificar o deslocamento UTC (fuso horário).

Para usar esse link profundo com seu bot, você pode especificá-lo como o destino da URL no botão do cartão ou tocar a ação através do `openUrl` tipo de ação.
