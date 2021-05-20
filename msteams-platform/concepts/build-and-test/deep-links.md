---
title: Criar links detalhados
description: Descreve links profundos e como usá-los em seus aplicativos
ms.topic: how-to
localization_priority: Normal
keywords: equipes deep link deeplink
ms.openlocfilehash: 837d180b06f69b9be49d898c62b9ab8ee64d51d0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566051"
---
# <a name="create-deep-links"></a>Criar links detalhados 

Você pode criar links para informações e recursos dentro de Teams. Os cenários em que a criação de links profundos são úteis são os seguintes:

* Navegando pelo usuário até o conteúdo dentro de uma das guias do seu aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário de uma atividade importante. Quando o usuário toca na notificação, o link profundo navega até a guia para que o usuário possa visualizar mais detalhes sobre a atividade.
* Seu aplicativo automatiza ou simplifica certas tarefas do usuário, como criar um chat ou agendar uma reunião, prepondo os links profundos com parâmetros necessários. Isso evita a necessidade de os usuários inserirem informações manualmente.

> [!NOTE]
>
> Um deeplink lança o navegador primeiro antes de navegar para o conteúdo. O comportamento de ligações profundas em entidades Teams são os seguintes:
>
> **Guia:**  
> ✔ navega diretamente para a url deeplink.
>
> **Bot:**  
> ✔ Deeplink no corpo do cartão: Abre primeiro no navegador.  
> ✔ Deeplink adicionado à ação OpenURL em Cartão Adaptável: Navega diretamente para a url do deeplink.  
> ✔ texto de marcação do Hyperlink no cartão: Abre primeiro no navegador.  
>
> **Bate-papo**:  
> ✔ marcação de hiperlink de mensagem de texto: navega diretamente para url deeplink.  
> ✔ Link colado em conversa geral de bate-papo: Navega diretamente para url deeplink.

## <a name="deep-linking-to-your-tab"></a>Ligação profunda à sua guia

Você pode criar links profundos para entidades em Teams. Isso é usado para criar links que navegam para conteúdo e informações dentro de sua guia. Por exemplo, se sua guia contiver uma lista de tarefas, os membros da equipe podem criar e compartilhar links para tarefas individuais. Ao selecionar o link, ele navega até a guia que se concentra no item específico. Para implementar isso, você adiciona uma ação **de link de cópia** a cada item, da melhor forma que se adapte melhor à sua interface do usuário. Quando o usuário toma essa ação, você chama `shareDeepLink()` para exibir uma caixa de diálogo contendo um link que o usuário pode copiar para a área de transferência. Quando você faz esta chamada, você também passa um ID para o seu item, que você recebe de volta no [contexto](~/tabs/how-to/access-teams-context.md) quando o link é seguido e sua guia é recarregada.

Alternativamente, você também pode gerar links profundos programáticamente, usando o formato especificado posteriormente neste tópico. Você pode usar links profundos em mensagens [de bot](~/bots/what-are-bots.md) e [conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) que informam os usuários sobre alterações na sua guia ou em itens dentro dele.

> [!NOTE]
> Este link profundo é diferente dos links fornecidos pelo link Copiar para o item do menu **da guia,** que apenas gera um link profundo que aponta para esta guia.

>[!NOTE]
> Atualmente, o shareDeepLink não funciona em plataformas móveis.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Mostre um link profundo para um item dentro de sua guia

Para mostrar uma caixa de diálogo que contenha um link profundo para um item dentro de sua guia, ligue `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })` .

Forneça os seguintes campos:

* `subEntityId`: Um identificador exclusivo para o item dentro da sua guia ao qual você está se conectando profundamente.
* `subEntityLabel`: Um rótulo para o item a ser usado para exibir o elo profundo.
* `subEntityWebUrl`: Um campo opcional com uma URL de recuo para usar se o cliente não suportar a renderização da guia.

### <a name="generate-a-deep-link-to-your-tab"></a>Gere um link profundo para sua guia

> [!NOTE]
> As guias pessoais têm um `personal` escopo, enquanto as guias de canais e grupos usam `team` ou `group` escopos. Os dois tipos de guia têm uma sintaxe ligeiramente diferente, uma vez que apenas a guia configurável tem uma `channel` propriedade associada ao seu objeto de contexto. Consulte a referência [manifesto](~/resources/schema/manifest-schema.md) para obter mais informações sobre os escopos da guia.

> [!NOTE]
> Links profundos funcionam corretamente somente se a guia foi configurada usando a biblioteca v0.4 ou posterior e por causa disso tem um ID de entidade. Links profundos para guias sem IDs de entidade ainda navegam até a guia, mas não podem fornecer o ID da sub-entidade para a guia.

Use o seguinte formato para um link profundo que você pode usar em um cartão de extensão de bot, conector ou mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Se o bot enviar uma mensagem contendo um `TextBlock` com um link profundo, uma nova guia do navegador será aberta quando o usuário selecionar o link. Isso acontece no Chrome e no Microsoft Teams aplicativo de desktop, ambos rodando no Linux.
> Se o bot enviar a mesma URL de link profundo para `Action.OpenUrl` uma, a guia Teams será aberta na guia atual do navegador quando o usuário selecionar o link. Uma nova guia do navegador não é aberta.

Os parâmetros de consulta são:

| Nome do parâmetro | Descrição | Exemplo |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | A iD do seu manifesto. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | O ID do item na guia, que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md).|Lista de tarefas123|
| `entityWebUrl` ou `subEntityWebUrl`&emsp; | Um campo opcional com uma URL de recuo para usar se o cliente não suportar a renderização da guia. | https://tasklist.example.com/123 ou https://tasklist.example.com/list123/task456 |
| `entityLabel` ou `subEntityLabel`&emsp; | Uma etiqueta para o item em sua guia, para usar ao exibir o link profundo. | Lista de tarefas 123 ou "Tarefa 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Um objeto JSON contendo os seguintes campos:</br></br> * Um ID para o item dentro da guia. </br></br> * O ID do canal Microsoft Teams que está disponível no [contexto](~/tabs/how-to/access-teams-context.md)da guia . | 
| `subEntityId`&emsp; | Um ID para o item dentro da guia. |Tarefa456 |
| `channelId`&emsp; | O Microsoft Teams iD do canal que está disponível no [contexto](~/tabs/how-to/access-teams-context.md)da guia . Esta propriedade só está disponível em guias configuráveis com um escopo de **equipe**. Não está disponível em guias estáticas, que têm um escopo **pessoal**.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Exemplos:

* Link para uma guia configurável em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para um item de tarefa dentro da guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para uma guia estática em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link para um item de tarefa dentro da guia estática: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Certifique-se de que todos os parâmetros de consulta estejam devidamente codificados pelo URI. Você deve seguir os exemplos preceeding usando o último exemplo:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Consuma um link profundo de uma guia

Ao navegar para um link profundo, Microsoft Teams simplesmente navega até a guia e fornece um mecanismo através da biblioteca javaScript Microsoft Teams para recuperar o ID da sub-entidade se ele existir.

A [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) chamada retorna um contexto que inclui o campo se a guia for `subEntityId` navegada através de um link profundo.

## <a name="deep-linking-from-your-tab"></a>Ligação profunda da sua guia

Você pode se aprofundar no conteúdo Teams da sua guia. Isso é útil se sua guia precisar vincular-se a outros conteúdos em Teams, como um canal, mensagem, outra guia ou até mesmo para abrir uma caixa de diálogo de agendamento. Para ativar um deeplink da sua guia, você deve ligar:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Essa chamada navega até a URL correta ou aciona uma ação do cliente, como abrir um agendamento ou instalar um aplicativo de diálogo. Veja o seguinte exemplo:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Ligação profunda a um bate-papo

Você pode criar links profundos para chats privados entre os usuários especificando o conjunto de participantes. Se um chat não existir com os participantes especificados, o link navega pelo usuário para um novo chat vazio. Novos chats são criados em estado de rascunho até que o usuário envie a primeira mensagem. Caso contrário, você pode especificar o nome do chat se ele ainda não existir, juntamente com texto que deve ser inserido na caixa de composição do usuário. Você pode pensar nesse recurso como um atalho para o usuário tomar a ação manual de navegar ou criar o chat e, em seguida, digitar a mensagem.

Como exemplo de caso de uso, se você estiver retornando um perfil de usuário Office 365 do seu bot como cartão, este link profundo pode permitir que o usuário converse facilmente com essa pessoa.

### <a name="generate-a-deep-link-to-a-chat"></a>Gere um link profundo para um bate-papo

Use este formato para um link profundo que você pode usar em um cartão de extensão de bot, conector ou mensagens:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: A lista separada de vima de IDs de usuário representando os participantes do chat. O usuário que realiza a ação está sempre incluído como participante. Atualmente, o campo User ID suporta o Azure AD UserPrincipalName, como apenas um endereço de e-mail.
* `topicName`: Um campo opcional para o nome de exibição do chat, no caso de um chat com 3 ou mais usuários. Se este campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`: Um campo opcional para o texto da mensagem que você deseja inserir na caixa de composição do usuário atual enquanto o chat estiver em um estado de rascunho.

Para usar este link profundo com o seu bot, especifique-o como o alvo URL no botão do seu cartão ou toque em ação através do `openUrl` tipo de ação.

## <a name="generate-deep-links-to-file-in-channel"></a>Gerar links profundos para arquivar no canal

O seguinte formato de link profundo pode ser usado em um cartão de extensão de bot, conector ou mensagens:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Os parâmetros de consulta são:

* `tenantId`: Exemplo de ID do inquilino, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Tipo de arquivo suportado, como docx, pptx, xlsx e pdf
* `objectUrl`: URL do objeto do arquivo, https://microsoft.sharepoint.com/teams/(filepath)
* `baseUrl`: URL base do arquivo, https://microsoft.sharepoint.com/teams
* `serviceName`: Nome do serviço, ID do aplicativo
* `threadId`: O threadId é o ID da equipe onde o arquivo está armazenado. É opcional e não pode ser definido para arquivos armazenados na pasta OneDrive do usuário. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: ID do grupo do arquivo, ae063b79-5315-4ddb-ba70-27328ba6c31e

A seguir está o formato de amostra de deeplink para arquivos:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80 ?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

### <a name="serialization-of-this-object"></a>Serialização deste objeto:
```
{
tenantId: "0d9b645f-597b-41f0-a2a3-ef103fbd91bb",
filetype: = "pptx",
objectUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform/Shared Documents/FC7- Bot and Action Infra/Kaizala Actions in Adaptive Cards - Deck.pptx",
baseUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform",
serviceName: "teams",
threadId: = "19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype",
groupId: "ae063b79-5315-4ddb-ba70-27328ba6c31e"
}
```
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Ligação profunda para guias Estrutura do SharePoint

O seguinte formato de link profundo pode ser usado em um cartão de extensão de bot, conector ou mensagens: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Quando um bot envia uma mensagem TextBlock com um link profundo, uma nova guia do navegador é aberta quando os usuários selecionam o link. Isso acontece no Chrome e Microsoft Teams aplicativo de desktop rodando no Linux.
> Se o bot enviar a mesma URL de link profundo em `Action.OpenUrl` uma, a guia Teams será aberta no navegador atual quando o usuário selecionar o link. Nenhuma nova guia do navegador é aberta.

Os parâmetros de consulta são:

* `appID`: Seu manifesto ID **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: O ID do item fornecido ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md). Por exemplo, **lista de tarefas123**.
* `entityWebUrl`: Um campo opcional com uma URL de recuo para usar se o cliente não suportar a renderização da guia - https://tasklist.example.com/123 ou https://tasklist.example.com/list123/task456 .
* `entityName`: Um rótulo para o item em sua guia, para usar ao exibir o link profundo, Lista de Tarefas 123 ou Tarefa 456.

Exemplo: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Ligação profunda com o diálogo de agendamento

> [!NOTE]
> Este recurso está atualmente em visualização de desenvolvedores.

Você pode criar links profundos para o Teams diálogo de agendamento incorporado. Isso é especialmente útil se o seu aplicativo ajudar o usuário a completar o calendário ou agendar tarefas relacionadas.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Gere um link profundo para a caixa de diálogo de agendamento

Use o seguinte formato para um link profundo que você pode usar em um bot, Connector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Os parâmetros de consulta são:

* `attendees`: A lista opcional separada de vima de IDs de usuário representando os participantes da reunião. O usuário que realiza a ação é o organizador do encontro. O campo user ID atualmente suporta apenas o Azure AD UserPrincipalName, normalmente um endereço de e-mail.
* `startTime`: Horário de início opcional do evento. Isso deve ser no [formato ISO 8601 longo,](https://en.wikipedia.org/wiki/ISO_8601)por exemplo *2018-03-12T23:55:25+02:00*.
* `endTime`: O horário final opcional do evento, também no formato ISO 8601.
* `subject`: Campo facultativo para o tema da reunião.
* `content`: Campo opcional para o campo de detalhes da reunião.

> [!NOTE]
> Atualmente, especificar o local não é suportado. Você deve especificar o deslocamento UTC, significa fusos horários ao gerar seus horários de início e término.

Para usar este link profundo com o seu bot, você pode especificar isso como o alvo URL no botão do seu cartão ou tocar em ação através do `openUrl` tipo de ação.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Ligação profunda com uma chamada de áudio ou áudio-vídeo

Você pode criar links profundos para invocar chamadas de áudio ou áudio-vídeo para um único usuário ou um grupo de usuários, especificando o tipo de chamada, como *áudio* ou *av*, e os participantes. Depois que o link profundo é invocado e antes de fazer a chamada, Teams cliente de desktop solicita uma confirmação para fazer a chamada. Em caso de chamada em grupo, você pode chamar um conjunto de usuários de VoIP e um conjunto de usuários de PSTN na mesma invocação deeplink. 

Em caso de chamada de vídeo, o cliente pedirá confirmação e ativará o vídeo do chamador para a chamada. O receptor da chamada tem a opção de responder apenas por áudio ou áudio e vídeo, através da janela de notificação de chamadas Teams.

> [!NOTE]
> Este deeplink não pode ser usado para invocar uma reunião.

### <a name="generate-a-deep-link-to-a-call"></a>Gere um link profundo para uma chamada

| Elo profundo | Formatar | Exemplo |
|-----------|--------|---------|
| Faça uma chamada de áudio | https://teams.microsoft.com/l/call/0/0?users=&lt;usuário1 &gt; , &lt; usuário2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Faça uma chamada de áudio e vídeo | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withvideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true |
|Faça uma chamada de áudio e vídeo com uma fonte de parâmetro opcional | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; comvideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true&source=demoApp |  
| Faça uma chamada de áudio e vídeo para uma combinação de usuários voip e PSTN | https://teams.microsoft.com/l/call/0/0?users=&lt;usuário1 &gt; ,4: &lt; número de telefone&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
A seguir estão os parâmetros de consulta:
* `users`: A lista separada de vima de IDs de usuário representando os participantes da chamada. Atualmente, o campo User ID suporta o Azure AD UserPrincipalName, normalmente um endereço de e-mail, ou no caso de uma chamada PSTN, ele suporta uma pstn mri 4: &lt; número de telefone &gt; .
* `Withvideo`: Este é um parâmetro opcional, que você pode usar para fazer uma chamada de vídeo. A configuração deste parâmetro só ligará a câmera do chamador. O receptor da chamada tem a opção de responder através de chamada de áudio ou áudio e vídeo através da janela de notificação de chamadas Teams. 
* `Source`: Este é um parâmetro opcional, que informa sobre a origem do deeplink.

## <a name="code-sample"></a>Exemplo de código

| Nome da amostra | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|ID de sub-entidade de consumo de deep link  |Microsoft Teams aplicativo de exemplo para demonstrar deeplink do chat do bot para o ID sub-entidade que consome guias.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)

