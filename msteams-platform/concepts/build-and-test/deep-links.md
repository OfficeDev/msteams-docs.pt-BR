---
title: Criar links detalhados
description: Descreve links profundos e como usá-los em seus aplicativos
ms.topic: how-to
ms.localizationpriority: high
keywords: link profundo do link do teams
ms.openlocfilehash: 9d9e0ff794d413be1959e8e8ddaef1086acc307d
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821385"
---
# <a name="create-deep-links"></a>Criar links detalhados 

Você pode criar links de informações e recursos no Teams. Os cenários em que a criação de links profundos são úteis são os seguintes:

* Levar o usuário até o conteúdo dentro de uma das guias do aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário de uma atividade importante. Quando o usuário toca na notificação, o link profundo navega até a guia para que o usuário possa exibir mais detalhes sobre a atividade.
* Seu aplicativo automatiza ou simplifica determinadas tarefas do usuário, como criar um chat ou agendar uma reunião, preenchendo previamente os links profundos com os parâmetros necessários. Isso evita a necessidade de os usuários inserirem informações manualmente.

> [!NOTE]
>
> Um link profundo inicia o navegador antes de navegar até o conteúdo. O comportamento de links profundos em entidades do Teams é o seguinte:
>
> **Tab**:  
> ✔ navega diretamente para a URL do link profundo.
>
> **Bot**:  
> ✔ Link profundo no corpo do cartão: abre primeiro no navegador.  
> ✔ Link profundo adicionado à ação OpenURL no Cartão Adaptável: navega diretamente para a URL do link profundo.  
> ✔ texto de markdown do Hiperlink no cartão: abre primeiro no navegador.  
>
> **Chat**:  
> ✔ Markdown de hiperlink de mensagem de texto: navega diretamente para a URL de link profundo.  
> ✔ Link colado na conversa de chat geral: navega diretamente para a URL de link profundo.

## <a name="deep-linking-to-your-tab"></a>Vinculação profunda à sua guia

Você pode criar links profundos para entidades no Teams. Isso é usado para criar links que navegam até o conteúdo e as informações na sua guia. Por exemplo, se sua guia contiver uma lista de tarefas, os membros da equipe poderão criar e compartilhar links para tarefas individuais. Quando você seleciona o link, ele navega até a guia que se concentra no item específico. Para implementar isso, adicione uma ação **copiar link** a cada item, da maneira mais adequada à interface do usuário. Quando o usuário executa essa ação, você chama `shareDeepLink()` para exibir uma caixa de diálogo que contém um link que o usuário pode copiar para a área de transferência. Ao fazer essa chamada, você também passa uma ID para o item. Você o obtém de volta no [contexto](~/tabs/how-to/access-teams-context.md) quando o link é seguido e sua guia é recarregada.

Como alternativa, você também pode gerar links profundos programaticamente, usando o formato especificado posteriormente neste tópico. Você pode usar links profundos nas mensagens do [bot](~/bots/what-are-bots.md) e do [conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) que informam os usuários sobre alterações em sua guia ou em itens dentro dela.

> [!NOTE]
> Esse link profundo é diferente dos links fornecidos pelo item de menu **Copiar para a guia**, que apenas gera um link profundo que aponta para essa guia.

>[!NOTE]
> Atualmente, o shareDeepLink não funciona em plataformas móveis.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Mostrar um link profundo para um item dentro de sua guia

Para mostrar uma caixa de diálogo que contém um link profundo para um item em sua guia, chame `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`.

Forneça os seguintes campos:

* `subEntityId`: Um identificador exclusivo para o item em sua guia para o qual você está criando um link direto.
* `subEntityLabel`: Um rótulo para o item a ser usado para exibir o link profundo.
* `subEntityWebUrl`: Um campo opcional com uma URL de fallback a ser usada se o cliente não for compatível com a renderização da guia.

### <a name="generate-a-deep-link-to-your-tab"></a>Gerar um link profundo para sua guia

> [!NOTE]
> As guias pessoais têm um escopo `personal`, enquanto as guias de canal e grupo usam escopos `team` ou `group`. Os dois tipos de guia têm uma sintaxe ligeiramente diferente, pois apenas a guia configurável possui uma propriedade `channel` associada ao seu objeto de contexto. Para obter mais informações, consulte a [referência do manifesto](~/resources/schema/manifest-schema.md).

> [!NOTE]
> Os links profundos só funcionarão corretamente se a guia tiver sido configurada usando a biblioteca v0.4 ou posterior e, por isso, tiver uma ID de entidade. Links profundos para guias sem IDs de entidade ainda navegam até a guia, mas não podem fornecer a ID da sub-entidade para a guia.

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Se o bot enviar uma mensagem contendo um `TextBlock` com um link profundo, uma nova guia do navegador será aberta quando o usuário selecionar o link. Isso acontece no Chrome e no aplicativo da área de trabalho do Microsoft Teams, ambos em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um `Action.OpenUrl`, a guia do Teams será aberta na guia atual do navegador quando o usuário selecionar o link. Uma nova guia do navegador não está aberta.

Os parâmetros de consulta são:

| Nome do parâmetro | Descrição | Exemplo |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | A ID do manifesto. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | A ID do item na guia, que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md).|Tasklist123|
| `entityWebUrl` ou `subEntityWebUrl`&emsp; | Um campo opcional com uma URL de fallback a ser usada se o cliente não for compatível com a renderização da guia. | `https://tasklist.example.com/123` ou `https://tasklist.example.com/list123/task456` |
| `entityLabel` ou `subEntityLabel`&emsp; | Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo. | Task List 123 ou "Task 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Um objeto JSON que contém os seguintes campos:</br></br> * Uma ID do item na guia. </br></br> * A ID do canal do Microsoft Teams que está disponível na guia [contexto](~/tabs/how-to/access-teams-context.md). | 
| `subEntityId`&emsp; | Uma ID do item na guia. |Tarefa456 |
| `channelId`&emsp; | A ID do canal do Microsoft Teams que está disponível na guia [contexto](~/tabs/how-to/access-teams-context.md). Essa propriedade só está disponível em guias configuráveis com um escopo de **equipe**. Ele não está disponível em guias estáticas, que têm um escopo de **pessoal**.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Exemplos:

* Link para uma guia configurável em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para um item de tarefa na guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para uma guia estática em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link para um item de tarefa na guia estática: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Verifique se todos os parâmetros de consulta estão codificados corretamente no URI. Você deve seguir os exemplos anteriores usando o último exemplo:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Consumir um link profundo de uma guia

Ao navegar até um link profundo, o Microsoft Teams navega até a guia e fornece um mecanismo por meio da biblioteca JavaScript do Microsoft Teams para recuperar a ID da sub-entidade, se ela existir.

A chamada [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) retornará um contexto que inclui o campo `subEntityId` se a guia for navegada por um link profundo.

## <a name="deep-linking-from-your-tab"></a>Vinculação profunda de sua guia

Você pode fazer a vinculação profunda do conteúdo no Teams em sua guia. Isso será útil se sua guia precisar se vincular a outro conteúdo no Teams, como um canal, mensagem, outra guia ou até mesmo para abrir uma caixa de diálogo de agendamento. Para disparar um link profundo da guia, você deve chamar:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Essa chamada navega até a URL correta ou dispara uma ação do cliente, como abrir uma caixa de diálogo de agendamento ou instalação de aplicativo. Veja o seguinte exemplo:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Vinculação profunda a um chat

Você pode criar links profundos para chats privados entre usuários especificando o conjunto de participantes. Se um chat não existir com os participantes especificados, o link navegará para um novo chat vazio. Novos chats são criados em estado de rascunho até que o usuário envie a primeira mensagem. Caso contrário, você poderá especificar o nome do chat se ele ainda não existir, juntamente com o texto que deve ser inserido na caixa de redação do usuário. Você pode pensar nesse recurso como um atalho para o usuário executar a ação manual de navegar ou criar o chat e, em seguida, digitar a mensagem.

Como exemplo de caso de uso, se você estiver retornando um perfil de usuário do Office 365 do seu bot como um cartão, esse link profundo poderá permitir que o usuário converse facilmente com essa pessoa.

### <a name="generate-a-deep-link-to-a-chat"></a>Gerar link profundo para um chat

Use este formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: A lista separada por vírgulas de IDs de usuário que representam os participantes do chat. O usuário que executa a ação é sempre incluído como um participante. Atualmente, o campo ID do usuário dá suporte ao UserPrincipalName do Microsoft Azure Active Directory (Azure AD), como apenas um endereço de email.
* `topicName`: Um campo opcional para o nome de exibição do chat, em chats com três ou mais usuários. Se esse campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`: Um campo opcional para o texto da mensagem que você deseja inserir na caixa de redação do usuário atual enquanto o chat está em um estado de rascunho.

Para usar esse link profundo com o bot, especifique-o como o destino da URL no botão do cartão ou toque em ação por meio do tipo de ação`openUrl`.

## <a name="generate-deep-links-to-file-in-channel"></a>Gerar links profundos para o arquivo no canal

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Os parâmetros de consulta são:

* `fileId`: ID de arquivo exclusiva do Sharepoint Online, também conhecido como sourcedoc. Por exemplo, 1FA202A5-3762-4F10-B550-C04F81F6ACBD
* `tenantId`: Exemplo de ID do locatário, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: tipo de arquivo com suporte, como docx, pptx, xlsx e pdf
* `objectUrl`: URL do objeto do arquivo. O formato é `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. Por exemplo, `https://microsoft.sharepoint.com/teams/(filepath)`
* `baseUrl`: URL base do arquivo. O formato é `https://{tenantName}.sharepoint.com/sites/{TeamName}`. Por exemplo, `https://microsoft.sharepoint.com/teams`
* `serviceName`: Nome do serviço, ID do aplicativo. Por exemplo, equipes.
* `threadId`: threadId é a ID da equipe em que o arquivo está armazenado. Ela é opcional e não pode ser definida para arquivos armazenados na pasta do OneDrive de um usuário. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: ID do grupo do arquivo, ae063b79-5315-4ddb-ba70-27328ba6c31e 

> [!NOTE]
> Você pode ver `threadId` e `groupId` na URL do canal.  

O seguinte formato de link profundo é usado em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

O seguinte formato de exemplo mostra o link profundo para arquivos:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

### <a name="serialization-of-this-object"></a>Serialização deste objeto:
```
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

Crie link profundos para o aplicativo depois que ele for listado na loja do Teams. Para criar um link para iniciar o Teams, acrescente a ID do aplicativo à seguinte URL: `https://teams.microsoft.com/l/app/<your-app-id>`. Uma caixa de diálogo é exibida para instalar o aplicativo. 
  
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Vinculação profunda para guias da Estrutura do SharePoint

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Quando um bot envia uma mensagem TextBlock com um link profundo, uma nova guia do navegador é aberta quando os usuários selecionam o link. Isso acontece no Chrome e no aplicativo da área de trabalho do Microsoft Teams em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um `Action.OpenUrl`, a guia do Teams será aberta no navegador atual quando o usuário selecionar o link. Nenhuma nova guia do navegador está aberta.

Os parâmetros de consulta são:

* `appID`: sua ID de manifesto, por exemplo, **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: a ID do item que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md). Por exemplo, **tasklist123**.
* `entityWebUrl`: Um campo opcional com uma URL de fallback a ser usada se o cliente não for compatível com a renderização da guia `https://tasklist.example.com/123` ou `https://tasklist.example.com/list123/task456`.
* `entityName`: Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo, Task List 123 ou Task 456.

Exemplo: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Vinculação profunda à caixa de diálogo de agendamento

> [!NOTE]
> Esse recurso está atualmente na versão prévia do desenvolvedor.

Você pode criar links profundos para a caixa de diálogo de agendamento interna do Teams. Isso é especialmente útil se seu aplicativo ajuda o usuário a concluir o calendário ou agendar tarefas relacionadas.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Gerar um link profundo para a caixa de diálogo de agendamento

Use o seguinte formato para um link profundo que você pode usar em um bot, Conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

> [!NOTE]
> Os parâmetros de pesquisa não dão suporte ao sinal `+` no lugar do espaço em branco (` `). Verifique se o código de codificação de URI retorna `%20` para espaços, por exemplo, `?subject=test%20subject` é bom, mas `?subject=test+subject` é ruim.

Os parâmetros de consulta são:

* `attendees`: A lista opcional separada por vírgulas de IDs de usuário que representam os participantes da reunião. O usuário que executa a ação é o organizador da reunião. Atualmente, o campo ID de usuário dá suporte apenas ao UserPrincipalName do Azure AD, normalmente um endereço de email.
* `startTime`: A hora de início opcional do evento. Isso deve estar em um [formato ISO 8601 longo](https://en.wikipedia.org/wiki/ISO_8601), por exemplo, *2018-03-12T23:55:25+02:00*. 
* `endTime`: A hora de término opcional do evento, também no formato ISO 8601.
* `subject`: Um campo opcional para o assunto da reunião.
* `content`: Um campo opcional para o campo de detalhes da reunião.

> [!NOTE]
> Atualmente, não há suporte para especificar o local. Você deve especificar a diferença UTC, ou seja, os fusos horários ao gerar os horários de início e término.

Para usar esse link profundo com o bot, você pode especificá-lo como o destino da URL no botão do cartão ou toque em ação por meio do tipo de ação`openUrl`.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Vinculação profunda a uma chamada de áudio ou chamada de vídeo com áudio.

Você pode criar links profundos para invocar somente chamadas de áudio ou áudio/vídeo para um único usuário ou um grupo de usuários, especificando o tipo de chamada, como *áudio* ou *av* e os participantes. Depois que o link profundo é invocado e antes de fazer a chamada, o cliente da área de trabalho do Teams solicita uma confirmação para fazer a chamada. No caso de chamada em grupo, você pode chamar um conjunto de usuários VoIP e um conjunto de usuários PSTN na mesma invocação de link profundo. 

No caso de uma chamada de vídeo, o cliente solicitará confirmação e ativará o vídeo do chamador para a chamada. O receptor da chamada tem a opção de responder somente por áudio ou áudio e vídeo, por meio da janela de notificação de chamada do Teams.

> [!NOTE]
> Este link profundo não pode ser usado para invocar uma reunião.

### <a name="generate-a-deep-link-to-a-call"></a>Gerar um link profundo para uma chamada

| Link profundo | Formatar | Exemplo |
|-----------|--------|---------|
| Fazer uma chamada de áudio | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Fazer uma chamada de áudio e vídeo | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true |
|Fazer uma chamada de áudio e vídeo com uma fonte de parâmetro opcional | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp |  
| Fazer uma chamada de áudio e vídeo para uma combinação de usuários VoIP e PSTN | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,4:&lt;phonenumber&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Estes são os parâmetros de consulta:
* `users`: A lista separada por vírgulas de IDs de usuário que representam os participantes da chamada. Atualmente, o campo ID de Usuário dá suporte ao UserPrincipalName do Azure AD, normalmente um endereço de email ou, no caso de uma chamada PSTN, ele dá suporte a um pstn mri 4:&lt;phonenumber&gt;.
* `withVideo`: Esse é um parâmetro opcional, que você pode usar para fazer uma chamada de vídeo. Definir esse parâmetro só ativará a câmera do chamador. O receptor da chamada tem a opção de responder por meio de chamada de áudio ou áudio e vídeo por meio da janela de notificação de chamada do Teams. 
* `Source`: esse é um parâmetro opcional, que informa sobre a origem do link profundo.

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|ID de Subentidade de Consumo de Link Profundo  |Aplicativo de exemplo do Microsoft Teams para demonstrar o link profundo do chat do bot para a ID de Subentidade de consumo de guias.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Moodle LMS](~/resources/moodleinstructions.md)
