---
title: Criar links detalhados
description: Descreve links profundos e como usá-los em seus aplicativos
ms.topic: how-to
localization_priority: Normal
keywords: links profundos do teams deeplink
ms.openlocfilehash: fb681cc2dc07f8ae042fe57d6249e986fefa1b7b
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058331"
---
# <a name="create-deep-links"></a>Criar links detalhados 

Você pode criar links para informações e recursos no Teams. Os cenários em que a criação de links profundos são úteis são:

* Navegando o usuário para conteúdo dentro de uma das guias do aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário de uma atividade importante. Quando o usuário toca na notificação, o link profundo navega até a guia para que o usuário possa exibir mais detalhes sobre a atividade.
* Seu aplicativo automatiza ou simplifica determinadas tarefas do usuário, como criar um chat ou agendar uma reunião, preenchendo previamente os links profundos com parâmetros necessários. Isso evita a necessidade de os usuários inserirem manualmente informações.

> [!NOTE]
>
> Um deeplink inicia o navegador primeiro antes de navegar para o conteúdo. O comportamento de links profundos em entidades do Teams é o seguinte:
>
> **Guia**:  
> ✔ navega diretamente para a url do deeplink.
>
> **Bot**:  
> ✔ Deeplink no corpo do cartão: abre primeiro no navegador.  
> ✔ Deeplink adicionado à ação OpenURL no Cartão Adaptável: navega diretamente para a url do deeplink.  
> ✔ texto de marcação de hiperlink no cartão: abre primeiro no navegador.  
>
> **Chat**:  
> ✔ Marcação de hiperlink de mensagem de texto: navega diretamente para a URL do deeplink.  
> ✔ link passado na conversa de chat geral: navega diretamente para a URL do deeplink.

## <a name="deep-linking-to-your-tab"></a>Vinculação profunda à sua guia

Você pode criar links profundos para entidades no Teams. Isso é usado para criar links que navegam até conteúdo e informações em sua guia. Por exemplo, se sua guia contiver uma lista de tarefas, os membros da equipe poderão criar e compartilhar links para tarefas individuais. Quando você seleciona o link, ele navega até sua guia que se concentra no item específico. Para implementar isso, adicione uma ação de **link** de cópia a cada item, da maneira que melhor se adequar à interface do usuário. Quando o usuário toma essa ação, você chama para exibir uma caixa de diálogo contendo um link que o usuário `shareDeepLink()` pode copiar para a área de transferência. Ao fazer essa chamada, você também passa uma ID para [](~/tabs/how-to/access-teams-context.md) seu item, que você volta ao contexto quando o link é seguido e sua guia é recarregada.

Como alternativa, você também pode gerar links profundos programaticamente, usando o formato especificado posteriormente neste tópico. Você pode usar links profundos em [mensagens bot](~/bots/what-are-bots.md) e [conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) que informam os usuários sobre alterações na guia ou itens dentro dela.

> [!NOTE]
> Esse link profundo é diferente dos links fornecidos pelo item de menu Copiar **para** guia, que apenas gera um link profundo que aponta para essa guia.

>[!NOTE]
> Atualmente, o shareDeepLink não funciona em plataformas móveis.

### <a name="showing-a-deep-link-to-an-item-within-your-tab"></a>Mostrando um link profundo para um item em sua guia

Para mostrar uma caixa de diálogo que contém um link profundo para um item em sua guia, chame `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`

Forneça os seguintes campos:

* `subEntityId`: Um identificador exclusivo para o item em sua guia à qual você está vinculando profundamente.
* `subEntityLabel`: Um rótulo para o item a ser usado para exibir o link profundo.
* `subEntityWebUrl`: Um campo opcional com uma URL de fallback a ser usada se o cliente não dá suporte à renderização da guia.

### <a name="generating-a-deep-link-to-your-tab"></a>Gerando um link profundo para sua guia

> [!NOTE]
> As guias pessoais têm um escopo, enquanto guias de canal e `personal` grupo usam ou `team` `group` escopos. Os dois tipos de tabulação têm uma sintaxe ligeiramente diferente, pois somente a guia configurável tem uma propriedade `channel` associada ao objeto de contexto. Consulte a [referência de](~/resources/schema/manifest-schema.md) manifesto para obter mais informações sobre escopos de tabulação.

> [!NOTE]
> Os links profundos funcionam corretamente somente se a guia foi configurada usando a biblioteca v0.4 ou posterior e, por isso, tem uma ID de entidade. Links profundos para guias sem IDs de entidade ainda navegam até a guia, mas não podem fornecer a ID da sub entidade para a guia.

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Se o bot enviar uma mensagem contendo um com um link profundo, uma nova guia do navegador será aberta quando o usuário `TextBlock` selecionar o link. Isso acontece no Chrome e no aplicativo da área de trabalho do Microsoft Teams, ambos em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um , a guia Teams será aberta na guia navegador atual quando o usuário `Action.OpenUrl` selecionar o link. Uma nova guia do navegador não é aberta.

Os parâmetros de consulta são:

| Nome do parâmetro | Descrição | Exemplo |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | A ID do manifesto. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | A ID do item na guia, que você forneceu ao [configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md).|Tasklist123|
| `entityWebUrl` ou `subEntityWebUrl`&emsp; | Um campo opcional com uma URL de fallback a ser usada se o cliente não suportar renderizar a guia. | https://tasklist.example.com/123 ou https://tasklist.example.com/list123/task456 |
| `entityLabel` ou `subEntityLabel`&emsp; | Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo. | Lista de tarefas 123 ou "Tarefa 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Um objeto JSON contendo os campos a seguir</br></br> * Uma ID do item na guia. </br></br> * A ID do canal do Microsoft Teams que está disponível no contexto da [guia](~/tabs/how-to/access-teams-context.md). | 
| `subEntityId`&emsp; | Uma ID do item na guia. |Task456 |
| `channelId`&emsp; | A ID do canal do Microsoft Teams que está disponível no contexto da [guia](~/tabs/how-to/access-teams-context.md). Essa propriedade só está disponível em guias configuráveis com um escopo de **equipe**. Ele não está disponível em guias estáticas, que têm um escopo **de pessoal**.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Exemplos:

* Link para uma guia configurável em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para um item de tarefa na guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para uma guia estática em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link para um item de tarefa na guia estática: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Verifique se todos os parâmetros de consulta estão codificados CORRETAMENTE corretamente. Você deve seguir os exemplos de preceeding usando o último exemplo:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consuming-a-deep-link-from-a-tab"></a>Consumir um link profundo de uma guia

Ao navegar para um link profundo, o Microsoft Teams simplesmente navega até a guia e fornece um mecanismo por meio da biblioteca JavaScript do Microsoft Teams para recuperar a ID da sub-entidade se ela existir.

A [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) chamada retorna um contexto que inclui o campo se a guia for `subEntityId` navegada por um link profundo.

## <a name="deep-linking-from-your-tab"></a>Vinculação profunda de sua guia

Você pode se enroscar no conteúdo no Teams a partir de sua guia. Isso será útil se sua guia precisar vincular a outro conteúdo no Teams, como um canal, uma mensagem, outra guia ou até mesmo para abrir uma caixa de diálogo de agendamento. Para disparar um deeplink de sua guia, você deve chamar:

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

Você pode criar links profundos para chats privados entre usuários especificando o conjunto de participantes. Se um chat não existir com os participantes especificados, o link navegará para um novo chat vazio. Novos chats são criados em estado de rascunho até que o usuário envie a primeira mensagem. Caso contrário, você poderá especificar o nome do chat se ele ainda não existir, juntamente com o texto que deve ser inserido na caixa de redação do usuário. Você pode pensar nesse recurso como um atalho para o usuário tomar a ação manual de navegar para ou criar o chat e, em seguida, digitar a mensagem.

Como exemplo de caso de uso, se você estiver retornando um perfil de usuário do Office 365 do bot como um cartão, esse link profundo poderá permitir que o usuário converse facilmente com essa pessoa.

### <a name="generate-a-deep-link-to-a-chat"></a>Gerar um link profundo para um chat

Use esse formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: A lista separada por vírgulas de IDs de usuário que representam os participantes do chat. O usuário que executa a ação está sempre incluído como participante. Atualmente, o campo ID do usuário dá suporte ao UserPrincipalName do Azure AD, como apenas um endereço de email.
* `topicName`: Um campo opcional para o nome de exibição do chat, no caso de um chat com 3 ou mais usuários. Se esse campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`: Um campo opcional para o texto da mensagem que você deseja inserir na caixa de redação do usuário atual enquanto o chat está em um estado de rascunho.

Para usar esse link profundo com seu bot, especifique-o como o destino da URL no botão do cartão ou toque em ação por meio do tipo `openUrl` de ação.

## <a name="generate-deep-links-to-file-in-channel"></a>Gerar links profundos para o arquivo no canal

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/I/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Os parâmetros de consulta são:

* `tenantId`: Exemplo de ID de locatário, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Tipo de arquivo com suporte, como docx, pptx, xlsx e pdf
* `objectUrl`: URL do objeto do arquivo, https://microsoft.sharepoint.com/teams/(filepath)
* `baseUrl`: URL base do arquivo, https://microsoft.sharepoint.com/teams
* `serviceName`: Nome do serviço, ID do aplicativo
* `threadId`: o threadId é a ID de equipe da equipe onde o arquivo está armazenado. Ele é opcional e não pode ser definido para arquivos armazenados na pasta do OneDrive de um usuário. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: ID de grupo do arquivo, ae063b79-5315-4ddb-ba70-27328ba6c31e

A seguir está o formato de exemplo de deeplink para arquivos:

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
## <a name="deep-links-for-sharepoint-framework-tabs"></a>Links profundos para guias da Estrutura do SharePoint

O seguinte formato de link profundo pode ser usado em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Quando um bot envia uma mensagem TextBlock com um link profundo, uma nova guia do navegador é aberta quando os usuários selecionam o link. Isso acontece no aplicativo de área de trabalho do Chrome e do Microsoft Teams em execução no Linux.
> Se o bot enviar a mesma URL de link profundo para um , a guia Teams será aberta no navegador atual quando o usuário `Action.OpenUrl` selecionar o link. Nenhuma nova guia do navegador é aberta.

Os parâmetros de consulta são:

* `appID`: Sua ID de manifesto **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: A ID do item que você forneceu [ao configurar a guia](~/tabs/how-to/create-tab-pages/configuration-page.md). Por exemplo, **tasklist123**.
* `entityWebUrl`: Um campo opcional com uma URL de fallback a ser usada se o cliente não suportar a renderização da guia - https://tasklist.example.com/123 ou https://tasklist.example.com/list123/task456 .
* `entityName`: Um rótulo para o item em sua guia, a ser usado ao exibir o link profundo, a Lista de Tarefas 123 ou a Tarefa 456.

Exemplo: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="linking-to-the-scheduling-dialog"></a>Vinculando à caixa de diálogo de agendamento

> [!NOTE]
> Esse recurso está atualmente na visualização do desenvolvedor.

Você pode criar links profundos para a caixa de diálogo de agendamento interno do Teams. Isso é especialmente útil se seu aplicativo ajudar o usuário a concluir o calendário ou agendar tarefas relacionadas.

### <a name="generating-a-deep-link-to-the-scheduling-dialog"></a>Gerando um link profundo para a caixa de diálogo de agendamento

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Os parâmetros de consulta são:

* `attendees`: a lista opcional separada por vírgulas de IDs de usuário que representam os participantes da reunião. O usuário que executa a ação é o organizador da reunião. O campo ID do usuário atualmente só dá suporte ao UserPrincipalName do Azure AD, normalmente um endereço de email.
* `startTime`: A hora de início opcional do evento. Isso deve estar no [formato ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)longo , por *exemplo, 2018-03-12T23:55:25+02:00*.
* `endTime`: A hora de término opcional do evento, também no formato ISO 8601.
* `subject`: Um campo opcional para o assunto da reunião.
* `content`: Um campo opcional para o campo de detalhes da reunião.

> [!NOTE]
> Atualmente, não há suporte para especificar o local. Você deve especificar o deslocamento UTC, isso significa fusos horários ao gerar seus horários de início e término.

Para usar esse link profundo com seu bot, você pode especificar isso como o destino da URL no botão do cartão ou tocar em ação por meio do tipo `openUrl` de ação.

## <a name="see-also"></a>Confira também

- [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)