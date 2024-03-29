---
title: Link de guias desdobradas e Exibição de Estágio
author: Rajeshwari-v
description: Saiba mais sobre o modo de exibição de estágio, um componente de interface do usuário de tela inteira invocado para mostrar o conteúdo da Web. A desenrolamento de link é usada para transformar URLs em uma guia usando Cartões Adaptáveis.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 2563cfd266b967bd8c55c24491165c9979bad145
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820084"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Link de guias desdobradas e Exibição de Estágio

O Stage View é um novo componente da interface do usuário (interface do usuário). Ele permite renderizar o conteúdo que é aberto em tela inteira no Teams e fixado como uma guia.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="stage-view"></a>Modo de Exibição de Estágio

O Modo de Exibição de Estágio é um componente de interface do usuário IU de tela inteira que você pode invocar para exibir o conteúdo da web. O serviço de desenrolamento de link existente é atualizado para que ele seja usado para transformar URLs em uma guia usando um Cartão Adaptável e Serviços de Chat. Quando um usuário envia um URL em um chat ou canal, a URL é desfralda para um Cartão Adaptável. O usuário pode selecionar **Exibir** no cartão e fixar o conteúdo como uma guia diretamente do Modo de Exibição de Estágio.

## <a name="advantage-of-stage-view"></a>Vantagem do Modo de Exibição de Estágio

Stage View helps provide a more seamless experience of viewing content in Teams. Users can open and view the content provided by your app without leaving the context, and they can pin the content to the chat or channel for future quick access leading to a higher user engagement with your app.

## <a name="stage-view-vs-task-module"></a>Modo de Exibição de Estágio versus Módulo de tarefa

|Modo de Exibição de Estágio|Módulo de tarefa|
|:-----------|:-----------|
|O Modo de Exibição de Estágio é útil quando você tem conteúdo avançado para exibir aos usuários, como uma página, um painel, um arquivo e assim por diante. Ele fornece recursos avançados que ajudam a renderizar seu conteúdo na tela inteira.|[Módulo de tarefa](../task-modules-and-cards/task-modules/task-modules-tabs.md) é especialmente útil para exibir mensagens que exigem atenção do usuário ou coletar informações necessárias para passar para a próxima etapa.|
  
## <a name="invoke-stage-view"></a>Invocar Modo de Exibição de Estágio

Você pode invocar o Modo de Exibição de Estágio das seguintes maneiras:

* [Invocar o Modo de Exibição de Estágio do Cartão Adaptável](#invoke-stage-view-from-adaptive-card)
* [Invocar o Modo de Exibição de Estágio por meio de link profundo](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Invocar Modo de Exibição de Estágio do Cartão Adaptável

Quando o usuário insere uma URL no cliente da área de trabalho do Teams, o bot é invocado e devolve um [Cartão Adaptável](../task-modules-and-cards/cards/cards-actions.md) com a opção de abrir a URL em um estágio. Depois que um estágio é iniciado e o `tabInfo` é fornecido, você pode adicionar a capacidade de fixar o estágio como uma guia.  

As imagens a seguir exibem um estágio aberto de um Cartão Adaptável:

:::image type="content" source="../assets/images/tab-images/open-stage-from-adaptive-card1.png" alt-text="A captura de tela mostra o estágio aberto do cartão Adaptável."lightbox="~/assets/images/tab-images/open-stage-from-adaptive-card1.png":::

:::image type="content" source="../assets/images/tab-images/open-stage-from-adaptive-card2.png" alt-text="A captura de tela mostra o estágio aberto do cartão."lightbox="~/assets/images/tab-images/open-stage-from-adaptive-card2.png":::

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

O tipo de solicitação `invoke` deve ser `composeExtension/queryLink`.

> [!NOTE]
>
> * `invoke` fluxo de trabalho é semelhante ao fluxo de trabalho `appLinking` atual.
> * Para manter a consistência, é recomendável nomear `Action.Submit` como `View`.
> * `websiteUrl` é uma propriedade necessária a ser passada no objeto `TabInfo`.

Veja a seguir o processo para invocar o Modo de Exibição de Estágio:

* When the user selects **View**, the bot receives an `invoke` request. The request type is `composeExtension/queryLink`.
* `invoke` resposta do bot contém um Cartão Adaptável com o tipo `tab/tabInfoAction` nele.
* O bot responde com um `200` código.

> [!NOTE]
>
> Nos clientes móveis do Teams, invocar o Stage View para aplicativos distribuídos pela [loja do Teams](~/concepts/deploy-and-publish/apps-publish-overview.md) e não ter uma experiência otimizada para dispositivos móveis abre o navegador da Web padrão do dispositivo. O navegador abre a URL especificada no parâmetro `websiteUrl` do objeto `TabInfo`.

## <a name="invoke-stage-view-through-deep-link"></a>Invocar Modo de Exibição de Estágio por meio de link profundo

Para invocar o Modo de Exibição de Estágio por meio do link profundo de sua guia, você deve encapsular a URL de link profundo na API `app.openLink(url)`. O link profundo também pode ser passado por meio de uma ação `OpenURL` no cartão.

### <a name="syntax"></a>Sintaxe

A seguir está a sintaxe de link profundo:

`<https://teams.microsoft.com/l/stage/{appId}/0?context>={"contentUrl":"contentUrl","websiteUrl":"websiteUrl","name":"Contoso"}`

### <a name="examples"></a>Exemplos

Quando um usuário insere uma URL, ela é desenrolada em um cartão Adaptável.

A seguir estão os exemplos de link profundo para invocar o Modo de Exibição de Estágio:

**Exemplo 1: URL com threadId**

URL não Codificada:

`<https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context>={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous","threadId":"19:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2"}`

URL Codificada:

`<https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%2C%22threadId%22%3A%2219:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2%22%7D>`

**Exemplo 2: URL sem threadId**

URL não Codificada:

`<https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context>={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous"}`

Codificado

`<https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%7D>`

> [!NOTE]
> Todos os links profundos devem ser codificados antes de colar a URL. Não há suporte para URLs não codificadas.
>
> * O `name` é opcional no link profundo. Se não estiver incluído, o nome do aplicativo o substituirá.
> * O link profundo também pode ser passado por meio de uma ação `OpenURL`.
> * Ao iniciar um Estágio de um determinado contexto, verifique se o aplicativo funciona nesse contexto. Por exemplo, se o Modo de Exibição de Estágio for iniciado de um aplicativo pessoal, você deverá garantir que seu aplicativo tenha um escopo pessoal.

## <a name="tab-information-property"></a>Propriedade de informações da guia

| Nome da propriedade | Tipo | Número de caracteres | Descrição |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | Cadeia de caracteres | 64 | Essa propriedade é um identificador exclusivo para a entidade que a guia exibe. Esse é um campo obrigatório.|
| `name` | Cadeia de caracteres | 128 | Essa propriedade é o nome de exibição da guia na interface do canal. Esse campo é opcional.|
| `contentUrl` | Cadeia de caracteres | 2048 | This property is the https:// URL that points to the entity UI to be displayed in the Teams canvas. This is a required field.|
| `websiteUrl?` | Cadeia de caracteres | 2048 | This property is the https:// URL to point at, if a user selects to view in a browser. This is a required field.|
| `removeUrl?` | Cadeia de caracteres | 2048 | Essa propriedade é a https:// URL que aponta para a IU a ser exibida quando o usuário exclui a guia. Este é um campo opcional.|

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo | Descrição | C# |Node.js|
|-------------|-------------|------|----|
|Guia no modo de exibição de estágio |Aplicativo de exemplo de guia do Microsoft Teams para demonstrar a guia no modo de exibição de estágio.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](what-are-tabs.md)
* [Adicionar desenrolamento de link](../messaging-extensions/how-to/link-unfurling.md)
* [composeExtensions](../resources/schema/manifest-schema.md#composeextensions)
* [Criar guias com Cartões Adaptáveis](how-to/build-adaptive-card-tabs.md)
* [Criar links detalhados](../concepts/build-and-test/deep-links.md)
