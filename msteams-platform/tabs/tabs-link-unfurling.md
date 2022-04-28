---
title: Link de guias desdobradas e Exibição de Estágio
author: Rajeshwari-v
description: Saiba como desatar um link, abrir o Modo de Exibição de Estágio e fixar uma guia com Microsoft Teams aplicativo. Saiba mais sobre o modo de exibição de estágio e como invoá-lo usando o cartão adaptável usando exemplo e exemplo de código.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: 043129d6a81543ac00acf8b64da49f75282823a2
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104081"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Link de guias desdobradas e Exibição de Estágio

O Modo de Exibição de Estágio é um novo componente de interface do usuário, que permite renderizar o conteúdo que é aberto em tela inteira no Teams e fixado como uma guia.

## <a name="stage-view"></a>Modo de Exibição de Estágio

O Modo de Exibição de Estágio é um componente de interface do usuário de tela inteira que você pode invocar para exibir o conteúdo da Web. O serviço de desatar vínculo existente é atualizado para que ele seja usado para transformar URLs em uma guia usando um Cartão Adaptável e Serviços de Chat. Quando um usuário envia uma URL em um chat ou canal, a URL é desfralda para um Cartão Adaptável. O usuário pode selecionar **Exibir** no cartão e fixar o conteúdo como uma guia diretamente do Modo de Exibição de Estágio.

## <a name="advantage-of-stage-view"></a>Vantagem do modo de exibição de estágio

O Modo de Exibição de Estágio ajuda a fornecer uma experiência mais perfeita de exibição de conteúdo Teams. Os usuários podem abrir e exibir o conteúdo fornecido pelo seu aplicativo sem sair do contexto, e podem fixar o conteúdo no chat ou canal para acesso rápido futuro, levando a um maior envolvimento do usuário com seu aplicativo.

## <a name="stage-view-vs-task-module"></a>Modo de Exibição de Estágio versus Módulo de Tarefa

|Modo de Exibição de Estágio|Módulo de tarefa|
|:-----------|:-----------|
|O Modo de Exibição de Estágio é útil quando você tem conteúdo avançado para exibir aos usuários, como uma página, um dashboard, um arquivo e assim por diante. Ele fornece recursos avançados que ajudam a renderizar seu conteúdo na tela de tela inteira.|[O módulo](../task-modules-and-cards/task-modules/task-modules-tabs.md) de tarefa é especialmente útil para exibir mensagens que exigem atenção do usuário ou coletar informações necessárias para passar para a próxima etapa.|
  
## <a name="invoke-stage-view"></a>Invocar modo de exibição de estágio

Você pode invocar o Modo de Exibição de Estágio das seguintes maneiras:

* [Invocar o modo de exibição de estágio do Cartão Adaptável](#invoke-stage-view-from-adaptive-card)
* [Invocar o Modo de Exibição de Estágio por meio de um link profundo](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Invocar o modo de exibição de estágio do Cartão Adaptável

Quando o usuário insere uma URL no cliente Teams desktop, o bot é invocado e retorna um Cartão [Adaptável](../task-modules-and-cards/cards/cards-actions.md) com a opção de abrir a URL em um estágio. Depois que um estágio é iniciado e o `tabInfo` é fornecido, você pode adicionar a capacidade de fixar o estágio como uma guia.  

As imagens a seguir exibem um estágio aberto de um Cartão Adaptável:

[![Abrir um estágio do Cartão Adaptável](~/assets/images/tab-images/open-stage-from-adaptive-card1.png)](~/assets/images/tab-images/open-stage-from-adaptive-card1.png#lightbox)

[![Abrir um estágio](~/assets/images/tab-images/open-stage-from-adaptive-card2.png)](~/assets/images/tab-images/open-stage-from-adaptive-card2.png#lightbox)

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

O `invoke` tipo de solicitação deve ser `composeExtension/queryLink`.

> [!NOTE]
>
> * `invoke` o fluxo de trabalho é semelhante ao fluxo de trabalho `appLinking` atual.
> * Para manter a consistência, é recomendável nomear `Action.Submit` como `View`.
> * `websiteUrl` é uma propriedade necessária a ser passada no `TabInfo` objeto.

A seguir está o processo para invocar o Modo de Exibição de Estágio:

* Quando o usuário seleciona **Exibir**, o bot recebe uma solicitação `invoke` . O tipo de solicitação é `composeExtension/queryLink`.
* `invoke` A resposta do bot contém um Cartão Adaptável com o tipo `tab/tabInfoAction` nele.
* O bot responde com um `200` código.

> [!NOTE]
> Em Teams clientes móveis, invocar o Modo de Exibição de Estágio para aplicativos distribuídos por meio da [Teams Store](/platform/concepts/deploy-and-publish/apps-publish-overview.md) e não ter uma experiência otimizada para moblie abre o navegador da Web padrão do dispositivo. O navegador abre a URL especificada no `websiteUrl` parâmetro do `TabInfo` objeto.

## <a name="invoke-stage-view-through-deep-link"></a>Invocar o Modo de Exibição de Estágio por meio de um link profundo

Para invocar o Modo de Exibição de Estágio por meio do link profundo da guia, você deve encapsular a URL de link profundo na `microsoftTeams.executeDeeplink(url)` API. O link profundo também pode ser passado por meio de `OpenURL` uma ação no cartão.

### <a name="syntax"></a>Sintaxe

A seguir está a sintaxe de deeplink:

https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"contentUrl","websiteUrl":"websiteUrl","name":"Contoso"}
 
### <a name="examples"></a>Exemplos

Quando um usuário insere uma URL, ela é desfralda em um cartão adaptável.

A seguir estão os exemplos de link profundo para invocar o Modo de Exibição de Estágio:

**Exemplo 1: URL com threadId**

URL não codificada:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context={"contentUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191,"websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes:Miscellaneous","threadId":"19:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2"}

URL codificada:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%2C%22threadId%22%3A%2219:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2%22%7D

**Exemplo 2: URL sem threadId**

URL não codificada:

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context={"contentUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191,"websiteUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true,"title":"Quotes:Miscellaneous"}

Codificado

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%7D

> [!NOTE]
> Todos os deeplinks devem ser codificados antes de colar a URL. Não há suporte para URLs não codificadas.
>
> * É `name` opcional no link profundo. Se não estiver incluído, o nome do aplicativo o substituirá.
> * O link profundo também pode ser passado por meio de uma `OpenURL` ação.
> * Ao iniciar um Estágio de um determinado contexto, verifique se o aplicativo funciona nesse contexto. Por exemplo, se o Modo de Exibição de Estágio for iniciado de um aplicativo pessoal, você deverá garantir que seu aplicativo tenha um escopo pessoal.

## <a name="tab-information-property"></a>Propriedade de informações da guia

| Nome da propriedade | Tipo | Número de caracteres | Descrição |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | Cadeia de caracteres | 64 | Essa propriedade é um identificador exclusivo para a entidade que a guia exibe. Esse é um campo obrigatório.|
| `name` | Cadeia de caracteres | 128 | Essa propriedade é o nome de exibição da guia na interface do canal. Esse campo é opcional.|
| `contentUrl` | Cadeia de caracteres | 2048 | Essa propriedade é a URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams dados. Esse é um campo obrigatório.|
| `websiteUrl?` | String | 2048 | Essa propriedade é o https:// URL para apontar, se um usuário selecionar para exibir em um navegador. Esse é um campo obrigatório.|
| `removeUrl?` | Cadeia de caracteres | 2048 | Essa propriedade é a URL https:// que aponta para a interface do usuário a ser exibida quando o usuário exclui a guia. Este é um campo opcional.|

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Guia no modo de exibição de estágio |Microsoft Teams aplicativo de exemplo de guia para demonstrar a guia no modo de exibição de estágio.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)

## <a name="see-also"></a>Confira também

* [Link de extensões de mensagem desfraldando](~/messaging-extensions/how-to/link-unfurling.md)
* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
