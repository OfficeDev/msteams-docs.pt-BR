---
title: Criar links detalhados
description: Neste artigo, você aprenderá a criar links profundos e navegar por eles em seus aplicativos do Microsoft Teams usando guias.
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 7a9af415a6fdc4f2cb1f9fd04ba79e8b197a40fc
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243217"
---
# <a name="create-deep-links"></a>Criar links detalhados

Links profundos são um mecanismo de navegação que você pode usar para conectar usuários com informações e recursos no Teams e em aplicativo Teams. Os cenários em que a criação de links profundos são úteis são os seguintes:

* Levar o usuário até o conteúdo dentro de uma das guias do aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário de uma atividade importante. Quando o usuário toca na notificação, o link profundo navega até a guia para que o usuário possa exibir mais detalhes sobre a atividade.
* Seu aplicativo automatiza ou simplifica determinadas tarefas do usuário. Você pode criar um chat ou agendar uma reunião preenchendo previamente os links profundos com os parâmetros necessários. Evita a necessidade de os usuários inserirem informações manualmente.

O SDK do cliente JavaScript do Microsoft Teams (TeamsJS) simplifica o processo de navegação. Para muitos cenários, como navegar até conteúdo e informações em sua guia ou iniciar uma caixa de diálogo de chat. O SDK fornece APIs digitadas que fornecem experiência aprimorada e podem substituir o uso de links profundos. Essas APIs são recomendadas para aplicativos Teams que podem ser executados em outros hosts (Outlook, Office), pois também fornecem uma maneira de verificar se o recurso que está sendo usado tem suporte desse host. As seções a seguir mostram informações sobre vinculação profunda, mas também realçam como os cenários que antes exigiam isso foram alterados com a versão v2 do TeamsJS.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

> [!NOTE]
> O comportamento dos links profundos depende de vários fatores. A lista a seguir descreve o comportamento de links profundos em entidades do Teams.
>
> **Tab**:  
> ✔ Navega diretamente para a URL do link profundo.
>
> **Bot**:  
> ✔ Link profundo no corpo do cartão: abre primeiro no navegador.  
> ✔ Link profundo adicionado à ação OpenURL no Cartão Adaptável: navega diretamente para a URL do link profundo.  
> ✔ texto de markdown do Hiperlink no cartão: abre primeiro no navegador.  
>
> **Chat**:  
> ✔ Markdown de hiperlink de mensagem de texto: navega diretamente para a URL de link profundo.  
> ✔ Link colado na conversa de chat geral: navega diretamente para a URL de link profundo.
>
>
>O comportamento de navegação de um aplicativo Teams com extensão para o Microsoft 365 (Outlook/Office) depende de dois fatores:
>
> * O destino para o qual o link profundo aponta.
> * O host em que o aplicativo Teams está em execução
>
> Se o aplicativo Teams estiver em execução no host em que o link profundo é direcionado, seu aplicativo será aberto diretamente dentro do host. No entanto, se o aplicativo Teams estiver em execução em um host diferente do qual o link profundo é direcionado, o aplicativo será aberto primeiro no navegador.

## <a name="deep-link-to-your-tab"></a>Link profundo para sua guia

Você pode criar links profundos para entidades no Teams. Isso é usado para criar links que navegam até conteúdo e informações na sua guia. Por exemplo, se sua guia contiver uma lista de tarefas, os membros da equipe poderão criar e compartilhar links para tarefas individuais. Ao selecionar o link, ele navega até a guia que se concentra no item específico.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

Para implementar isso, adicione uma ação **copiar link** a cada item, da maneira mais adequada à interface do usuário. Quando o usuário executa essa ação, você chama [pages.shareDeepLink()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-sharedeeplink&preserve-view=true) para exibir uma caixa de diálogo que contém um link que o usuário pode copiar para a área de transferência. Ao fazer essa chamada, passe uma ID para o item. Você o obtém novamente no [contexto](~/tabs/how-to/access-teams-context.md) quando o link é seguido e sua guia é recarregada.

```javascript
pages.shareDeepLink({ subPageId: <subPageId>, subPageLabel: <subPageLabel>, subPageWebUrl: <subPageWebUrl> })
```

Você precisará substituir os campos pelas informações apropriadas:

* `subPageId`: um identificador exclusivo para o item da sua página à qual você tem uma vinculação profunda.
* `subPageLabel`: Um rótulo para o item a ser usado para exibir o link profundo.
* `subPageWebUrl`: uma URL de fallback a ser usada se o cliente não puder renderizar a página.

Para obter mais informações, consulte [pages.shareDeepLink()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-sharedeeplink&preserve-view=true).

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

Para implementar isso, adicione uma ação **copiar link** a cada item, da maneira mais adequada à interface do usuário. Quando o usuário executa essa ação, você chama `shareDeepLink()` para exibir uma caixa de diálogo que contém um link que o usuário pode copiar para a área de transferência. Ao fazer essa chamada, você também passa uma ID para o item. Você o obtém de volta no [contexto](~/tabs/how-to/access-teams-context.md) quando o link é seguido e sua guia é recarregada.

```javascript
microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })
```

Você precisará substituir os campos pelas informações apropriadas:

* `subEntityId`: um identificador exclusivo para o item da sua guia à qual você tem uma vinculação profunda.
* `subEntityLabel`: Um rótulo para o item a ser usado para exibir o link profundo.
* `subEntityWebUrl`: um campo opcional com uma URL de fallback a ser usada se o cliente não for compatível com a renderização da guia.

---

Como alternativa, é possível gerar links profundos programaticamente, usando o formato que será especificado posteriormente neste artigo. Você pode usar links profundos nas mensagens do [bot](~/bots/what-are-bots.md) e do [conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) que informam os usuários sobre alterações em sua guia ou em itens dentro dela.

> [!NOTE]
> Esse link profundo é diferente dos links fornecidos pelo item de menu **Copiar para a guia**, que apenas gera um link profundo que aponta para essa guia.

>[!IMPORTANT]
> Atualmente, o shareDeepLink não funciona em plataformas móveis.

### <a name="consume-a-deep-link-from-a-tab"></a>Consumir um link profundo de uma guia

Ao navegar até um link aprofundado, o Microsoft Teams simplesmente navega até a guia e fornece um mecanismo através da biblioteca JavaScript do Teams para recuperar a ID da sub-página, se ela existir.

A [`app.getContext()`](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-getcontext&preserve-view=true) chamada (`microsoftTeams.getContext()`) no TeamsJS v1) retorna uma promessa que será resolvida com o contexto que inclui a propriedade `subPageId` (subEntityId para TeamsJS v1) se a guia for navegada por um link profundo. Para obter mais informações, consulte a [interface PageInfo](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-pageinfo&preserve-view=true).

### <a name="generate-a-deep-link-to-your-tab"></a>Gerar um link profundo para sua guia

Embora seja recomendado usar `shareDeepLink()` para gerar um link direto para sua guia, também é possível criar um manualmente.

> [!NOTE]
>
> * As guias pessoais têm um escopo `personal`, enquanto as guias de canal e grupo usam escopos `team` ou `group`. Os dois tipos de guia têm uma sintaxe ligeiramente diferente, pois apenas a guia configurável possui uma propriedade `channel` associada ao seu objeto de contexto. Para obter mais informações sobre escopos de guias, consulte a referência do [manifesto](~/resources/schema/manifest-schema.md).
> * Os links profundos só funcionarão corretamente se a guia tiver sido configurada usando a biblioteca v0.4 ou posterior e, por isso, tiver uma ID de entidade. Links profundos para guias sem IDs de entidade ainda vão para a guia, mas não podem fornecer a ID da sub entidade para a guia.

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Se o bot enviar uma mensagem contendo um `TextBlock` com um link profundo, uma nova guia do navegador será aberta quando o usuário selecionar o link. Isto acontece no Chrome e no aplicativo da área de trabalho do Teams, ambos em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um `Action.OpenUrl`, a guia do Teams será aberta na guia atual do navegador quando o usuário selecionar o link. Uma nova aba do navegador não foi aberta.

<!--- TBD: Edit this article.
* Admonitions/alerts seem to be overused. 
* An important alert at the end of this table does not make sense. Also, it has a code snippet inside it.
* List items in the table are not formatted well in output.
* Some headings use -ing verbs.
* Example values and some URLs should be in backticks and not emphasized.
* Codeblock are missing language.
* Check for markdownlint errors.
* Table with just a row isn't really needed. Provide the content without tabulating it.
--->

Os parâmetros de consulta são:

| Nome do parâmetro | Descrição | Exemplo |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | A ID do Centro de Administração do Teams. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | A ID do item na guia, que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md). Ao gerar uma URL para vinculação profunda, continue a usar entityID como um nome de parâmetro na URL. Ao configurar a guia, o objeto de contexto refere-se à entityID como {page.id}. |Tasklist123|
| `entityWebUrl` ou `subEntityWebUrl`&emsp; | Um campo opcional com uma URL de fallback a ser usada se o cliente não for compatível com a renderização da guia. | `https://tasklist.example.com/123` ou `https://tasklist.example.com/list123/task456` |
| `entityLabel` ou `subEntityLabel`&emsp; | Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo. | Task List 123 ou "Task 456 |
| `context.subEntityId`&emsp; | Uma ID do item na guia. Ao gerar uma URL para vinculação profunda, continue a usar subEntityId como o nome do parâmetro na URL. Ao configurar a guia, o objeto de contexto refere-se à subEntityID como subPageID. |Tarefa456 |
| `context.channelId`&emsp; | ID do canal do Microsoft Teams que está disponível na guia [contexto](~/tabs/how-to/access-teams-context.md). Essa propriedade só está disponível em guias configuráveis com um escopo de **equipe**. Não está disponível em guias estáticas, que têm um escopo de **pessoal**.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |
| `chatId`&emsp; | A ChatId que está disponível na guia [contexto](~/tabs/how-to/access-teams-context.md) para o chat em grupo e reunião | 17:b42de192376346a7906a7dd5cb84b673@thread.v2 |
| `contextType`&emsp; |  O chat é o único contextType compatível para reuniões | chat |

**Exemplos**:

* Link para uma guia estática (pessoal) propriamente dita:

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`

* Link para um item dentro tarefa na guia estática (pessoal):

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

* Link para uma guia configurável em si: 

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`

* Link para um item de tarefa na guia configurável: 

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`

* Link para um aplicativo de guia adicionado a uma reunião ou chat em grupo:

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456?context={"chatId": "17:b42de192376346a7906a7dd5cb84b673@thread.v2","contextType":"chat"}`

> [!IMPORTANT]
> Verifique se todos os parâmetros de consulta estão codificados corretamente no URI. Você deve seguir os exemplos anteriores usando o último exemplo:
>
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

## <a name="navigation-from-your-tab"></a>Navegação a partir da sua guia

Você pode navegar até o conteúdo no Teams da guia usando o TeamsJS ou links profundos. Isso será útil se sua guia precisar conectar usuários a outro conteúdo no Teams, como a um canal, mensagem, outra guia ou até mesmo para abrir uma caixa de diálogo de agendamento. Anteriormente, a navegação poderia exigir um link profundo, mas agora ela pode ser realizada em muitas instâncias usando o SDK. As seções a seguir mostram os dois métodos, mas quando possível, recomenda-se o uso dos recursos digitados do SDK.

Um dos benefícios de usar o TeamsJS, principalmente para o aplicativo Teams que pode ser executado em outros hosts (Outlook e Office), é que é possível verificar se o host oferece suporte ao recurso que você está tentando usar. Para verificar o suporte de um host de uma funcionalidade, você pode usar a função `isSupported()` associada ao namespace da API. A Versão Prévia do SDK do TeamsJS v2 organiza APIs em funcionalidades por meio de namespaces. Por exemplo, antes do uso de uma API no namespace `pages` você pode verificar o valor booliano retornado de `pages.isSupported()` e executar a ação apropriada no contexto da interface do usuário do aplicativo e dos aplicativos.  

Para obter mais informações sobre recursos e APIs no TeamsJS, consulte [Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams](~/tabs/how-to/using-teams-client-sdk.md#apis-organized-into-capabilities).

### <a name="navigate-within-your-app"></a>Navegar em seu aplicativo

É possível navegar em um aplicativo usando o TeamsJS. O código a seguir demonstra como navegar para uma entidade específica dentro do aplicativo Teams.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

Você pode acionar a navegação de sua guia usando a função [pages.navigateToApp()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-navigatetoapp&preserve-view=true) conforme mostrado no código a seguir:

```javascript
if (pages.isSupported()) {
  const navPromise = pages.navigateToApp({ appId: <appId>, pageId: <pageId>, webUrl: <webUrl>, subPageId: <subPageId>, channelId:<channelId>});
  navPromise.
     then((result) => {/*Successful navigation*/}).
     catch((error) => {/*Failed navigation*/});
}
else { /* handle case where capability isn't supported */ }
```

Para obter mais informações sobre como usar a funcionalidade páginas, consulte [pages.navigateToApp()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-navigatetoapp&preserve-view=true) e o namespace [pages](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest&preserve-view=true) para outras opções de navegação. Se necessário, também é possível abrir diretamente um link direto usando a função [app.openLink()](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-openlink&preserve-view=true).

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

Para disparar um link profundo da sua guia, chame:

```javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

---

### <a name="open-a-scheduling-dialog"></a>Abrir uma caixa de diálogo de agendamento

> [!NOTE]
> Para abrir a caixa de diálogo de agendamento no Teams, os desenvolvedores precisam continuar usando o método original baseado em URL de link profundo, pois o Teams ainda não oferece suporte à funcionalidade de calendário.

Para obter mais informações sobre como trabalhar com o calendário, consulte o namespace [calendário](/javascript/api/@microsoft/teams-js/calendar?view=msteams-client-js-latest&preserve-view=true) na documentação de referência da API.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
// Open a scheduling dialog from your tab
if(calendar.isSupported()) {
   const calendarPromise = calendar.composeMeeting({
      attendees: ["joe@contoso.com", "bob@contoso.com"],
      content: "test content",
      endTime: "2018-10-24T10:30:00-07:00",
      startTime: "2018-10-24T10:00:00-07:00",
      subject: "test subject"});
   calendarPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");
```

---

Como alternativa, você pode criar manualmente links diretos para a caixa de diálogo de agendamento interno do Teams.

#### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Gerar um link profundo para a caixa de diálogo de agendamento

Embora seja recomendável usar as APIs digitados do TeamsJS, é possível criar manualmente links profundos para a caixa de diálogo de agendamento interna do Teams. Use o seguinte formato para um link profundo que você pode usar em um bot, Conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

> [!NOTE]
> Os parâmetros de pesquisa não dão suporte ao sinal `+` no lugar do espaço em branco (``). Verifique se o código de codificação de URI retorna `%20` para espaços, por exemplo, `?subject=test%20subject` é bom, mas `?subject=test+subject` é ruim.

Os parâmetros de consulta são:

* `attendees`: A lista opcional separada por vírgulas de IDs de usuário que representam os participantes da reunião. O usuário que executa a ação é o organizador da reunião. Atualmente, o campo ID de usuário dá suporte apenas ao UserPrincipalName do Azure AD, normalmente um endereço de email.
* `startTime`: A hora de início opcional do evento. Isso deve estar em um [formato ISO 8601 longo](https://en.wikipedia.org/wiki/ISO_8601), por exemplo, *2018-03-12T23:55:25+02:00*. 
* `endTime`: A hora de término opcional do evento, também no formato ISO 8601.
* `subject`: Um campo opcional para o assunto da reunião.
* `content`: Um campo opcional para o campo de detalhes da reunião.

> [!NOTE]
> Currently, specifying the location isn't supported. You must specify the UTC offset, it means time zones when generating your start and end times.

Para usar esse link profundo com o bot, você pode especificá-lo como o destino da URL no botão do cartão ou toque em ação por meio do tipo de ação`openUrl`.

### <a name="open-an-app-install-dialog"></a>Abrir uma caixa de diálogo de instalação de aplicativo

Você pode abrir uma caixa de diálogo de instalação de aplicativo do aplicativo Teams, conforme mostrado no código a seguir.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
// Open an app install dialog from your tab
if(appInstallDialog.isSupported()) {
    const dialogPromise = appInstallDialog.openAppInstallDialog({ appId: <appId>});
    dialogPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

Para obter mais informações sobre a caixa de diálogo de instalação, consulte a função [appInstallDialog.openAppInstallDialog()](/javascript/api/@microsoft/teams-js/appinstalldialog?view=msteams-client-js-latest#@microsoft-teams-js-appinstalldialog-openappinstalldialog&preserve-view=true) na documentação de referência da API.

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

---

### <a name="navigate-to-a-chat"></a>Navegar até um chat

Você pode navegar ou criar chats privados entre usuários com o TeamsJS especificando o conjunto de participantes. Se não houver um chat com os participantes especificados, o link direcionará o usuário para um novo chat vazio. Novos chats são criados em estado de rascunho até que o usuário envie a primeira mensagem. Caso contrário, você poderá especificar o nome do chat se ele ainda não existir, juntamente com o texto que deve ser inserido na caixa de texto do usuário. Você pode pensar nesse recurso como um atalho para o usuário executar a ação manual de navegar ou criar o chat e, em seguida, digitar a mensagem.

Como exemplo de caso de uso, se estiver retornando um perfil do Office 365 do seu bot como um cartão, esse link profundo poderá permitir que o usuário converse facilmente com essa pessoa. O exemplo a seguir demonstra como abrir uma mensagem de chat para um grupo de participantes com uma mensagem inicial.

```javascript
if(chat.isSupported()) {
    const chatPromise = chat.openGroupChat({ users: ["joe@contoso.com","bob@contoso.com"], topic: "Prep For Meeting Tomorrow", message: "Hi folks kicking off chat about our meeting tomorrow"});
    chatPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

Embora o uso das APIs fortemente tipadas seja recomendado, você pode usar o seguinte formato para um link profundo criado manualmente que pode ser usado em um bot, conector ou cartão de extensão de mensagem:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: A lista separada por vírgulas de IDs de usuário que representam os participantes do chat. O usuário que executa a ação é sempre incluído como um participante. Atualmente, o campo ID do usuário dá suporte ao UserPrincipalName do Microsoft Azure Active Directory (Azure AD), como apenas um endereço de email.
* `topicName`: um campo opcional para o nome de exibição do chat, se um chat tiver três ou mais usuários. Se este campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`: Um campo opcional para o texto da mensagem que você deseja inserir na caixa de redação do usuário atual enquanto o chat está em um estado de rascunho.

Para usar esse link profundo com o bot, especifique-o como o destino da URL no botão do cartão ou toque em ação por meio do tipo de ação`openUrl`.

### <a name="generate-deep-links-to-channel-conversation"></a>Gerar links profundos para a conversa do canal

Use esse formato de link profundo para ir para uma conversa específica no thread do canal:

`https://teams.microsoft.com/l/message/<channelId>/<parentMessageId>?tenantId=<tenantId>&groupId=<groupId>&parentMessageId=<parentMessageId>&teamName=<teamName>&channelName=<channelName>&createdTime=<createdTime>`

Exemplo: `https://teams.microsoft.com/l/message/<channelId>/1648741500652?tenantId=<tenantId>&groupId=<groupId>&parentMessageId=1648741500652&teamName=<teamName>&channelName=<channelName>&createdTime=1648741500652`

Os parâmetros de consulta são:

* `channelId`: ID do Canal da conversa. Por exemplo, `19:3997a8734ee5432bb9cdedb7c432ae7d@thread.tacv2`.
* `tenantId`: ID de locatário, como `0d9b645f-597b-41f0-a2a3-ef103fbd91bb`.
* `groupId`: ID do grupo do arquivo. Por exemplo, `3606f714-ec2e-41b3-9ad1-6afb331bd35d`.
* `parentMessageId`: ID da mensagem pai da conversa.
* `teamName`: nome da equipe.
* `channelName`: nome do canal da equipe.

> [!NOTE]
> Você pode ver `channelId` e `groupId` na URL do canal.

### <a name="generate-deep-links-to-file-in-channel"></a>Gerar links profundos para o arquivo no canal

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens: 

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Os parâmetros de consulta são:

* `fileId`: Unique file ID from Sharepoint Online, also known as `sourcedoc`. For example,`1FA202A5-3762-4F10-B550-C04F81F6ACBD`.
* `tenantId`: ID de locatário, como `0d9b645f-597b-41f0-a2a3-ef103fbd91bb`.
* `fileType`: tipo de arquivo compatível, como .docx, .pptx, .xlsx e .pdf.
* `objectUrl`: URL do objeto do arquivo. O formato é `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. Por exemplo, `https://microsoft.sharepoint.com/teams/(filepath)`.
* `baseUrl`: URL base do arquivo. O formato é `https://{tenantName}.sharepoint.com/sites/{TeamName}`. Por exemplo, `https://microsoft.sharepoint.com/teams`.
* `serviceName`: Nome do serviço, ID do aplicativo. Por exemplo, `teams`.
* `threadId`: threadId é a ID da equipe em que o arquivo está armazenado. É opcional e não pode ser definido para arquivos armazenados na pasta OneDrive de um usuário. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype.
* `groupId`: ID do grupo do arquivo. Por exemplo, `ae063b79-5315-4ddb-ba70-27328ba6c31e`.

> [!NOTE]
> Você pode ver `threadId` e `groupId` na URL do canal.  

O seguinte formato de link profundo é usado em um bot, conector ou cartão de extensão de mensagens: 

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

O formato de exemplo a seguir ilustra link profundo para arquivos:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

#### <a name="serialization-of-this-object"></a>Serialização deste objeto

```javascript
{
fileId: "5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80",
tenantId: "0d9b645f-597b-41f0-a2a3-ef103fbd91bb",
filetype: = "pptx",
objectUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform/Shared Documents/FC7- Bot and Action Infra/Kaizala Actions in Adaptive Cards - Deck.pptx",
baseUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform",
serviceName: "teams",
threadId: = "19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype",
groupId: "ae063b79-5315-4ddb-ba70-27328ba6c31e"
}
```

## <a name="deep-linking-to-an-app"></a>Vinculação profunda a um aplicativo

Criar link profundos para o aplicativo depois que ele for listado na Teams store. Para criar um link para iniciar o Teams, acrescente a ID do aplicativo à seguinte URL: `https://teams.microsoft.com/l/app/<your-app-id>`. Uma caixa de diálogo é exibida para instalar ou abrir o aplicativo.

> [!NOTE]
> Se o aplicativo tiver sido aprovado para a plataforma móvel, você poderá vincular-se a um aplicativo móvel. O Apple App Store Connect Team ID é necessário além disso para que o link profundo funcione no Teams-iOS. Para obter mais informações, [confira como atualizar a ID da equipe do Apple App Store Connect](../deploy-and-publish/appsource/prepare/update-apple-store-team-connect-id.md).

### <a name="deep-linking-for-sharepoint-framework-tabs"></a>Vinculação profunda para guias da Estrutura do SharePoint

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Quando um bot envia uma mensagem TextBlock com um link profundo, uma nova guia do navegador é aberta quando os usuários selecionam o link. Isso acontece no Chrome e no aplicativo da área de trabalho do Microsoft Teams em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um `Action.OpenUrl`, a guia do Teams será aberta no navegador atual quando o usuário selecionar o link. Nenhuma nova guia do navegador está aberta.

Os parâmetros de consulta são:

* `appID`: sua ID de manifesto, por exemplo, `fe4a8eba-2a31-4737-8e33-e5fae6fee194`.

* `entityID`: a ID do item que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md). Por exemplo, `tasklist123`.
* `entityWebUrl`: um campo opcional com uma URL de fallback para usar se o cliente não suportar a renderização da guia - `https://tasklist.example.com/123` ou `https://tasklist.example.com/list123/task456`.
* `entityName`: Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo, Task List 123 ou Task 456.

Exemplo: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList`

## <a name="navigate-to-an-audio-or-audio-video-call"></a>Navegue até uma chamada de áudio ou áudio/vídeo

Você pode invocar somente chamadas de áudio ou áudio/vídeo para um único usuário ou um grupo de usuários, especificando o tipo de chamada e os participantes. Antes de fazer a chamada, o cliente do Teams solicita uma confirmação para fazer a chamada. No caso de uma chamada de grupo, você pode chamar um conjunto de usuários VoIP e um conjunto de usuários PSTN na mesma invocação de link profundo.

Em uma chat com vídeo, o cliente solicitará a confirmação e habilitará o vídeo do chamador para a chamada. O receptor da chamada tem a opção de responder somente por áudio ou áudio e vídeo, por meio da janela de notificação de chamada do Teams.

> [!NOTE]
> Este método não pode ser usado para invocar uma reunião.

O código a seguir demonstra o uso do SDK do TeamsJS para iniciar uma chamada:

```javascript
if(call.isSupported()) {
    const callPromise = call.startCall({ targets: ["joe@contoso.com","bob@contoso.com","4:9876543210"], requestedModalities: [call.CallModalities.Audio], source: "demoApp"});
    callPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }

```

## <a name="generate-a-deep-link-to-share-content-to-stage-in-meetings"></a>Gerar um link profundo para compartilhar conteúdo para preparar em reuniões

Você também pode gerar um link profundo para [compartilhar o aplicativo](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md#share-entire-app-to-stage) para preparar e iniciar ou ingressar em uma reunião.

> [!Note]
> O link profundo para compartilhar conteúdo para preparar a reunião tem suporte apenas no cliente da área de trabalho do Teams.

Quando um link profundo é selecionado em um aplicativo por um usuário que faz parte de uma reunião em andamento, o aplicativo é compartilhado com o estágio e uma janela pop-up de permissão é exibida. Os usuários podem conceder permissões para os participantes, como coeditar um documento ou colaborar com um aplicativo.

:::image type="content" source="../../assets/images/intergrate-with-teams/screenshot-of-pop-up-permission.png" alt-text="A captura de tela é um exemplo que mostra uma janela pop-up de permissão.":::

Quando o usuário não está em uma reunião, o usuário é redirecionado para o calendário do Teams em que o usuário precisa ingressar em uma reunião ou uma reunião instantânea (reunir agora) pode ser iniciada.

:::image type="content" source="../../assets/images/intergrate-with-teams/Instant-meetnow-pop-up.png" alt-text="A captura de tela é um exemplo que mostra uma janela pop-up quando não há nenhuma reunião em andamento.":::

Depois que o usuário iniciar uma reunião instantânea (reunir agora), ele poderá adicionar participantes e interagir com o aplicativo.

:::image type="content" source="../../assets/images/intergrate-with-teams/Screenshot-ofmeet-now-option-pop-up.png" alt-text="A captura de tela é um exemplo que mostra uma opção para adicionar participantes e como interagir com o aplicativo.":::

Para adicionar um link profundo para compartilhar conteúdo no palco, você precisa ter um contexto de aplicativo. O contexto do aplicativo permite que o cliente do Teams busque o manifesto do aplicativo e verifique se o compartilhamento no estágio é possível. A seguir está um exemplo de contexto de aplicativo.

* `{ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9ec80a73-1d41-4bcb-8190-4b9eA9e29fbb" , "useMeetNow": false }`

Os parâmetros de consulta para o contexto do aplicativo são:

* `appID`: essa é a ID que pode ser obtida do manifesto do aplicativo.
* `appSharingUrl`: a URL que precisa ser compartilhada no estágio deve ser um domínio válido definido no manifesto do aplicativo. Se a URL não for um domínio válido, uma caixa de diálogo de erro será exibida para fornecer ao usuário uma descrição do erro.
* `useMeetNow`: isso inclui um parâmetro booliano que pode ser verdadeiro ou falso.
  * **True** – quando o `UseMeetNow` valor é true e se não houver nenhuma reunião em andamento, uma nova reunião reunir agora será iniciada. Quando houver uma reunião em andamento, esse valor será ignorado.

  * **False** – o valor `UseMeetNow` padrão é false, o que significa que quando um link profundo é compartilhado com o estágio e não há nenhuma reunião em andamento, um pop-up de calendário será exibido. Quando há uma reunião em andamento, o compartilhamento pode ser feito diretamente.

Verifique se todos os parâmetros de consulta estão codificados corretamente no URI e se o contexto do aplicativo deve ser codificado duas vezes na URL final. A seguir está um exemplo.

```json
var appContext= JSON.stringify({ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9cc80a93-1d41-4bcb-8170-4b9ec9e29fbb", "useMeetNow":false })
var encodedContext = encodeURIComponent(appcontext).replace(/'/g,"%27").replace(/"/g,"%22")
var encodedAppContext = encodeURIComponent(encodedContext).replace(/'/g,"%27").replace(/"/g,"%22")
```

Um link profundo pode ser iniciado na Web do Teams ou no cliente da área de trabalho do Teams.

* **Web do Teams** – Use o formato a seguir para iniciar um link profundo da Web do Teams para compartilhar conteúdo no palco.

    `https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`

    Exemplo: `https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Link profundo|Formatar|Exemplo|
    |---------|---------|---------|
    |Para compartilhar o aplicativo e abrir o calendário do Teams, quando UseMeeetNow for "false", o padrão é UseMeeetNow.|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|
    |Para compartilhar o aplicativo e iniciar uma reunião instantânea, quando UseMeeetNow for "true".|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

* **Cliente da área de** trabalho da equipe – use o formato a seguir para iniciar um link profundo do cliente da área de trabalho do Teams para compartilhar conteúdo no palco.

    `msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`

    Exemplo: `msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Link profundo|Formatar|Exemplo|
    |---------|---------|---------|
    |Para compartilhar o aplicativo e abrir o calendário do Teams, quando UseMeeetNow for "false", o padrão é UseMeeetNow.|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|
    |Para compartilhar o aplicativo e iniciar uma reunião instantânea, quando UseMeeetNow for "true".|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

Os parâmetros de consulta são:

* `deepLinkId`: qualquer identificador usado para correlação de telemetria.
* `fqdn`: `fqdn` é um parâmetro opcional, que pode ser usado para alternar para um ambiente apropriado de uma reunião para compartilhar um aplicativo no palco. Ele dá suporte a cenários em que um compartilhamento de aplicativo específico ocorre em um ambiente específico. O valor padrão é `fqdn` a URL da empresa e os valores possíveis são `Teams.live.com` para o Teams for Life `teams.microsoft.com`ou `teams.microsoft.us`.

Para compartilhar todo o aplicativo para preparar, no manifesto do aplicativo, você deve configurar `meetingStage` `meetingSidePanel` e, como contextos de quadro, ver o [manifesto do aplicativo](../../resources/schema/manifest-schema.md). Caso contrário, os participantes da reunião podem não conseguir ver o conteúdo no palco.

## <a name="generate-a-deep-link-to-a-call"></a>Gerar um link profundo para uma chamada

Embora o uso das APIs tipadas do TeamsJS seja recomendado, você também pode usar um link profundo criado manualmente para iniciar uma chamada.

| Link profundo | Formatar | Exemplo |
|-----------|--------|---------|
| Fazer uma chamada de áudio | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com` |
| Fazer uma chamada de áudio e vídeo | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>&withVideo=true` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true` |
|Fazer uma chamada de áudio e vídeo com uma fonte de parâmetro opcional | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>&withVideo=true&source=demoApp` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp` |  
| Fazer uma chamada de áudio e vídeo para uma combinação de usuários VoIP e PSTN | `https://teams.microsoft.com/l/call/0/0?users=<user1>,4:<phonenumber>` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210` |
  
Estes são os parâmetros de consulta:

* `users`: A lista separada por vírgulas de IDs de usuário que representam os participantes da chamada. Atualmente, o campo ID de usuário dá suporte ao UserPrincipalName do Azure AD, normalmente um endereço de email, ou em uma chamada PSTN, ele dá suporte a um pstn mri 4: &lt;phonenumber&gt;.
* `withVideo`: Esse é um parâmetro opcional, que você pode usar para fazer uma chamada de vídeo. Definir esse parâmetro só ativará a câmera do chamador. O receptor da chamada tem a opção de responder por meio de chamada de áudio ou áudio e vídeo por meio da janela de notificação de chamada do Teams.
* `Source`: esse é um parâmetro opcional, que informa sobre a origem do link profundo.

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|ID de Subentidade de Consumo de Link Profundo  | O aplicativo de amostra do Teams para demonstrar o link aprofundado do chat do bot para a guia que consome a ID da Subentidade.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Moodle LMS](~/resources/moodleinstructions.md)
