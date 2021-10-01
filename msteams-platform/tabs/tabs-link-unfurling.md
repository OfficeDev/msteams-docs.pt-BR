---
title: Link de guias desdobradas e Exibição de Estágio
author: Rajeshwari-v
description: Como desatar um link, abrir o Stage View e fixar uma guia com Microsoft Teams app.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: cc77667a8782f2f519d6dc3e6af74949a9dcbed2
ms.sourcegitcommit: 329447310013a2672216793dab79145b24ef2cd2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2021
ms.locfileid: "60017300"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Link de guias desdobradas e Exibição de Estágio

> [!NOTE]
> Esse recurso está disponível somente na [visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.

O Stage View é um novo componente de interface do usuário (UI), que permite renderizar o conteúdo que é aberto em tela inteira em Teams e fixado como uma guia.
 
> [!NOTE]
> No momento, Teams clientes móveis não suportam guias link desfraldamento e Exibição de Estágio. Os clientes móveis usam `websiteUrl` o atributo fornecido pelo desenvolvedor para abrir a página no navegador da Web do dispositivo.

## <a name="stage-view"></a>Exibição de estágio

O Stage View é um componente de interface do usuário de tela inteira que você pode invocar para exibir o conteúdo da Web. O serviço de desatração de link existente é atualizado para que ele seja usado para transformar URLs em uma guia usando um Cartão Adaptável e Serviços de Chat. Quando um usuário envia uma URL em um chat ou canal, a URL é desfraldada para um Cartão Adaptável. O usuário pode selecionar **Exibir** no cartão e fixar o conteúdo como uma guia diretamente do Stage View.

## <a name="advantage-of-stage-view"></a>Vantagem da exibição de estágio

O Stage View ajuda a fornecer uma experiência mais perfeita de exibição de conteúdo em Teams. Os usuários podem abrir e exibir o conteúdo fornecido pelo aplicativo sem sair do contexto, e eles podem fixar o conteúdo no chat ou canal para acesso rápido futuro. Isso leva a um envolvimento de usuário mais alto com seu aplicativo.

## <a name="stage-view-vs-task-module"></a>Exibição de estágio versus módulo de tarefa

|Exibição de estágio|Módulo de tarefa|
|:-----------|:-----------|
|O Modo de Exibição de Estágio é útil quando você tem conteúdo avançado para exibir para os usuários, como uma página, um painel, um arquivo e assim por diante. Ele fornece recursos avançados que ajudam a renderizar seu conteúdo na tela inteira.|[O módulo de](../task-modules-and-cards/task-modules/task-modules-tabs.md) tarefas é especialmente útil para exibir mensagens que exigem atenção do usuário ou coletar informações necessárias para mover para a próxima etapa.|
  
## <a name="invoke-stage-view"></a>Invocar exibição de estágio

Você pode invocar o Modo de Exibição de Estágio das seguintes maneiras:

* [Invocar exibição de estágio do cartão adaptável](#invoke-stage-view-from-adaptive-card)
* [Invocar Exibição de Estágio por meio de um link profundo](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Invocar exibição de estágio do cartão adaptável

Quando o usuário insula uma URL no cliente da área de [](../task-modules-and-cards/cards/cards-actions.md) trabalho Teams, o bot é invocado e retorna um Cartão Adaptável com a opção de abrir a URL em um estágio. Depois que um estágio é lançado e o é fornecido, você pode adicionar a capacidade de fixar `tabInfo` o estágio como uma guia.  

As imagens a seguir exibem um estágio aberto de um Cartão Adaptável:

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="700"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="700"/>

### <a name="example"></a>Exemplo

A seguir está o código para abrir um estágio de um Cartão Adaptável:

```json
{
    type: "Action.Submit",
    name: "View",
    data: {
          msteams: {
            type: "invoke",
            value: {
                type: "tab/tabInfoAction",
                tabInfo: {
                    contentUrl: contentUrl,
                    websiteUrl: websiteUrl,
                    name: "Tasks",
                    entityId: "entityId"
                 }
                }
            }
        }
} 
```

O `invoke` tipo de solicitação deve ser `composeExtension/queryLink` .

> [!NOTE]
> * `invoke` o fluxo de trabalho é semelhante ao fluxo de `appLinking` trabalho atual. 
> * Para manter a consistência, é recomendável nomear `Action.Submit` como `View` .
> * `websiteUrl` é uma propriedade necessária a ser passada no `TabInfo` objeto.

A seguir está o processo para invocar o Stage View:

* Quando o usuário seleciona **Exibir**, o bot recebe uma `invoke` solicitação. O tipo de solicitação é `composeExtension/queryLink` .
* `invoke` response from bot contains an Adaptive Card with type `tab/tabInfoAction` in it.
* O bot responde com um `200` código.

> [!NOTE]
> Atualmente, Teams clientes móveis não suportam o recurso Modo de Exibição de Estágio. Quando um usuário seleciona **Exibir** em um cliente móvel, o usuário é levado para o navegador do dispositivo. O navegador abre a URL especificada no `websiteUrl` parâmetro do `TabInfo` objeto.

## <a name="invoke-stage-view-through-deep-link"></a>Invocar Exibição de Estágio por meio de um link profundo

Para invocar o Stage View por meio de um link profundo de sua guia, você deve quebrar a URL de link profundo na `microsoftTeams.executeDeeplink(url)` API. O link profundo também pode ser passado por uma `OpenURL` ação no cartão.

A imagem a seguir exibe um Stage View invocado por meio de um link profundo:

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a>Sintaxe

A seguir está a sintaxe do deeplink: 

https://teams.microsoft.com/l/stage/{appId}/0?context={\"contentUrl \" : \" "[contentUrl]" \" , \" websiteUrl \" : \" "[websiteUrl]" \" , nome : \" \" \" Contoso \" }
 
### <a name="examples"></a>Exemplos

Quando um usuário insinua uma URL, ela é desfraldada em um cartão Adaptável.

A seguir estão os exemplos de link profundo para invocar o Stage View:

**Exemplo 1**

https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl".:"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

**Exemplo 2**

https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl".:"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

> [!NOTE]
> * O `name` é opcional em link profundo. Se não estiver incluído, o nome do aplicativo o substituirá.
> * O link profundo também pode ser passado por uma `OpenURL` ação.
> * Atualmente, Teams clientes móveis não suportam o recurso Modo de Exibição de Estágio. Quando os usuários selecionam um link profundo para um Stage View, eles são levados para o navegador da Web do dispositivo. O navegador da Web abre a URL especificada no `websiteUrl` parâmetro do link profundo.
> * Ao iniciar um Estágio a partir de um determinado contexto, verifique se seu aplicativo funciona nesse contexto. Por exemplo, se o seu Stage View for lançado a partir de um aplicativo pessoal, você deve garantir que seu aplicativo tenha um escopo pessoal.

## <a name="tab-information-property"></a>Propriedade Tab information

| Nome da propriedade | Tipo | Número de caracteres | Descrição |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | String | 64 | Essa propriedade é um identificador exclusivo para a entidade que a guia exibe. Esse é um campo obrigatório.|
| `name` | String | 128 | Essa propriedade é o nome de exibição da guia na interface do canal. Esse campo é opcional.|
| `contentUrl` | String | 2048 | Essa propriedade é a URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams. Esse é um campo obrigatório.|
| `websiteUrl?` | String | 2048 | Essa propriedade é a URL https:// para apontar, se um usuário selecionar para exibir em um navegador. Esse é um campo obrigatório.|
| `removeUrl?` | String | 2048 | Essa propriedade é a URL https:// que aponta para a interface do usuário a ser exibida quando o usuário exclui a guia. Este é um campo opcional.|

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Guia no exibição de estágio |Microsoft Teams exemplo de guia para demonstração de guia no exibição de estágio.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|
    

## <a name="see-also"></a>Confira também

* [Vinculação de extensões de mensagens](~/messaging-extensions/how-to/link-unfurling.md)
* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)
