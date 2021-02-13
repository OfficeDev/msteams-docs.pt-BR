---
title: Criar links profundos para o conteúdo
description: Descreve links profundos e como usá-los em seus aplicativos
ms.topic: how-to
keywords: deeplink do link do Teams
ms.openlocfilehash: d6efe7332035320d2114e0e834d1c971ccc7108c
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231558"
---
# <a name="create-deep-links-to-content-and-features-in-microsoft-teams"></a>Criar links profundos para conteúdo e recursos no Microsoft Teams

Você pode criar links para informações e recursos no Teams. Exemplos em que a criação de links profundos é útil são:

* Navegar pelo usuário até o conteúdo dentro de uma das guias do seu aplicativo. Por exemplo, seu aplicativo pode ter um bot que envia mensagens notificando o usuário sobre uma atividade importante. Quando o usuário toca na notificação, o link profundo navega até a guia para que o usuário possa exibir mais detalhes sobre a atividade.
* Seu aplicativo automatiza ou simplifica determinadas tarefas do usuário, como criar um chat ou agendar uma reunião, preenchendo previamente os links profundos com os parâmetros necessários. Isso evita a necessidade de os usuários inserirem informações manualmente.

> [!NOTE]
>
> Um deeplink inicia o navegador primeiro antes de navegar para conteúdo e informações da seguinte forma:
>
> **Guia**:  
> ✔ navega diretamente para a URL do deeplink.
>
> **Bot**:  
> ✔ Deeplink no corpo do cartão - Abre primeiro no navegador.  
> ✔ Deeplink adicionado à ação OpenURL no Cartão Adaptável - Navega diretamente para a URL do deeplink.  
> ✔ texto de markdown de hiperlink no cartão - Abre primeiro no navegador.  
>
> **Chat**:  
> ✔ de hiperlink de mensagem de texto: navega diretamente para a URL do deeplink.  
> ✔ Link passado em conversa de chat geral - Navega diretamente para a URL do deeplink.

## <a name="deep-linking-to-your-tab"></a>Vinculação profunda à sua guia

Você pode criar links profundos para entidades no Teams. Normalmente, isso é usado para criar links que navegam para conteúdo e informações em sua guia. Por exemplo, se a guia contiver uma lista de tarefas, os membros da equipe poderão criar e compartilhar links para tarefas individuais. Quando você seleciona o link, ele navega até a guia que se concentra no item específico. Para implementar isso, adicione uma ação de "copiar link" a cada item, da maneira mais adequada à interface do usuário. Quando o usuário faz essa ação, você chama para exibir uma caixa de diálogo contendo um link que o usuário pode `shareDeepLink()` copiar para a área de transferência. Ao fazer essa chamada, você também passa uma ID para [](~/tabs/how-to/access-teams-context.md) o item, que você volta ao contexto quando o link é seguido e sua guia é recarregada.

Como alternativa, você também pode gerar links profundos programaticamente, usando o formato especificado posteriormente neste tópico. Você pode usá-los [](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) em [mensagens de bot](~/bots/what-are-bots.md) e conector que informam aos usuários sobre alterações em sua guia ou itens dentro dela.

> [!NOTE]
> Esse link profundo é diferente dos links fornecidos pelo **link** Copiar para o item de menu guia, que gera apenas um link profundo que aponta para essa guia.

>[!NOTE]
> Atualmente, o shareDeepLink não funciona em plataformas móveis.

### <a name="showing-a-deep-link-to-an-item-within-your-tab"></a>Mostrando um link profundo para um item dentro de sua guia

Para mostrar uma caixa de diálogo que contém um link profundo para um item na guia, chame `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`

Forneça estes campos:

* `subEntityId`&emsp;Um identificador exclusivo para o item dentro de sua guia ao qual você está vinculando profundamente
* `subEntityLabel`&emsp;Um rótulo para o item a ser usado para exibir o link profundo
* `subEntityWebUrl`&emsp;Um campo opcional com uma URL de fallback a ser usada se o cliente não suportar a renderização da guia

### <a name="generating-a-deep-link-to-your-tab"></a>Gerando um link profundo para sua guia

> [!NOTE]
> As guias pessoais têm um escopo, enquanto as guias de canal e `personal` grupo usam ou têm `team` `group` escopos. Os dois tipos de guia têm uma sintaxe ligeiramente diferente, pois somente a guia configurável tem uma propriedade `channel` associada ao seu objeto de contexto. Consulte a [referência do](~/resources/schema/manifest-schema.md) manifesto para obter mais informações sobre escopos de guia.

> [!NOTE]
> Os links profundos funcionam corretamente somente se a guia foi configurada usando a biblioteca v0.4 ou posterior e, por isso, tem uma ID de entidade. Links profundos para guias sem IDs de entidade ainda navegam até a guia, mas não podem fornecer a ID da sub-entidade para a guia.

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Se o bot enviar uma mensagem contendo um link profundo, uma nova guia do navegador será aberta quando o usuário `TextBlock` selecionar o link. Isso acontece no Chrome e no aplicativo da área de trabalho Do Microsoft Teams, ambos executados no Linux.
> Se o bot enviar a mesma URL de link profundo para uma, a guia Teams será aberta na guia atual do navegador quando o usuário `Action.OpenUrl` selecionar o link. Nenhuma nova guia do navegador é aberta.

Os parâmetros de consulta são:

* `appId`&emsp;A ID do manifesto; por exemplo, "fe4a8eba-2a31-4737-8e33-e5fae6fee194"
* `entityId`&emsp;A ID do item na guia, que você forneceu ao [configurar a guia;](~/tabs/how-to/create-tab-pages/configuration-page.md) por exemplo, "tasklist123"
* `entityWebUrl`ou um campo opcional com uma URL de fallback a ser usado se o cliente não suportar a renderização da guia; por `subEntityWebUrl` &emsp; exemplo, " https://tasklist.example.com/123 ou https://tasklist.example.com/list123/task456 "
* `entityLabel`ou um rótulo para o item na guia, a ser usado ao exibir o link profundo; por exemplo, "Lista de Tarefas `subEntityLabel` &emsp; 123" ou "Tarefa 456"
* `context`&emsp;Um objeto JSON que contém os seguintes campos:
  * `subEntityId`&emsp;Uma ID para o item _na_ guia; por exemplo, "task456"
  * `channelId`&emsp;A ID do canal do Microsoft Teams que está disponível no contexto da [guia;](~/tabs/how-to/access-teams-context.md) por exemplo, "19:cbe3683f25094106b826c9cada3afbe0@thread.skype". Essa propriedade só está disponível em guias configuráveis com um escopo de "equipe". Ele não está disponível em guias estáticas, que têm um escopo de "pessoal".

Exemplos:

* Link para uma guia configurável em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para um item de tarefa na guia configurável: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link para uma guia estática em si: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link para um item de tarefa dentro da guia estática: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Verifique se todos os parâmetros de consulta estão codificados corretamente no URI. Você deve seguir os exemplos de pré-pré-uso usando o último exemplo:
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consuming-a-deep-link-from-a-tab"></a>Consumindo um link profundo de uma guia

Ao navegar até um link profundo, o Microsoft Teams simplesmente navega até a guia e fornece um mecanismo por meio da biblioteca JavaScript do Microsoft Teams para recuperar a ID da sub-entidade, se ela existir.

A [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) chamada retorna um contexto que inclui o campo se a guia for `subEntityId` navegada por um link profundo.

## <a name="deep-linking-from-your-tab"></a>Vinculação profunda de sua guia

Você pode se desvincular ao conteúdo do Teams na guia. Isso será útil se sua guia precisar vincular a outro conteúdo no Teams, como um canal, uma mensagem, outra guia ou até mesmo abrir uma caixa de diálogo de agendamento. Para disparar um deeplink da guia, você deve chamar:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Essa chamada o guiará até a URL correta ou disparará uma ação do cliente, como abrir uma caixa de diálogo de agendamento ou instalação de aplicativo. Veja o seguinte exemplo:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Vinculação profunda a um chat

Você pode criar links profundos para chats privados entre usuários especificando o conjunto de participantes. Se não existir um chat com os participantes especificados, o link navegará para o usuário para um novo chat vazio. Novos chats são criados em estado de rascunho até que o usuário envie a primeira mensagem. Caso contrário, você poderá especificar o nome do chat se ele ainda não existir, juntamente com o texto que deve ser inserido na caixa de redação do usuário. Você pode pensar nesse recurso como um atalho para o usuário tomar a ação manual de navegar ou criar o chat e digitar a mensagem.

Como exemplo de caso de uso, se você estiver retornando um perfil de usuário do Office 365 do bot como um cartão, esse link profundo poderá permitir que o usuário converse facilmente com essa pessoa.

### <a name="generating-a-deep-link-to-a-chat"></a>Gerando um link profundo para um chat

Use esse formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Exemplo: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: a lista separada por vírgulas de IDs de usuário que representam os participantes do chat. O usuário que executa a ação é sempre incluído como participante. Atualmente, o campo ID de usuário dá suporte ao UserPrincipalName do Azure AD, normalmente apenas um endereço de email.
* `topicName`: Um campo opcional para o nome de exibição do chat, no caso de um chat com três ou mais usuários. Se esse campo não for especificado, o nome de exibição do chat será baseado nos nomes dos participantes.
* `message`: Um campo opcional para o texto da mensagem que você deseja inserir na caixa de redação do usuário atual enquanto o chat está em um estado de rascunho.

Para usar esse link profundo com seu bot, você pode especificar isso como o destino da URL no botão do cartão ou tocar na ação por meio do tipo `openUrl` de ação.

### <a name="generating-a-deep-link-to-a-call"></a>Gerando um link profundo para uma chamada

Use esse formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens:

`https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>`

Exemplo: `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Os parâmetros de consulta são:

* `users`: a lista separada por vírgulas de IDs de usuário que representam os participantes da chamada. O usuário que executa a ação é sempre incluído como participante. Atualmente, o campo ID de usuário dá suporte ao UserPrincipalName do Azure AD, normalmente apenas um endereço de email.

## <a name="linking-to-the-scheduling-dialog"></a>Vinculação à caixa de diálogo de agendamento

> [!Note]
> Esse recurso está atualmente na visualização do desenvolvedor.

Você pode criar links profundos para a caixa de diálogo de agendamento interno do Teams. Isso é especialmente útil se seu aplicativo ajuda o usuário a concluir tarefas relacionadas ao calendário ou agendamento.

### <a name="generating-a-deep-link-to-the-scheduling-dialog"></a>Gerando um link profundo para a caixa de diálogo de agendamento

Use o seguinte formato para um link profundo que você pode usar em um bot, conector ou cartão de extensão de mensagens: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Exemplo: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Os parâmetros de consulta são:

* `attendees`: a lista opcional separada por vírgulas de IDs de usuário que representam os participantes da reunião. O usuário que está executando a ação é o organizador da reunião. Atualmente, o campo ID de usuário só dá suporte ao UserPrincipalName do Azure AD, normalmente um endereço de email.
* `startTime`: a hora de início opcional do evento. Deve estar no formato [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)longo, por exemplo "2018-03-12T23:55:25+02:00".
* `endTime`: a hora de término opcional do evento, também no formato ISO 8601.
* `subject`: um campo opcional para o assunto da reunião.
* `content`: um campo opcional para o campo de detalhes da reunião.

Atualmente, não há suporte para a especificação do local. Você deve especificar o deslocamento UTC, o que significa fusos horários ao gerar as horas de início e de término.

Para usar esse link profundo com seu bot, você pode especificar isso como o destino da URL no botão do cartão ou tocar na ação por meio do tipo `openUrl` de ação.
