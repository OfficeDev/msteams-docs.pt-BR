---
title: Extensões de mensagens
author: surbhigupta
description: Uma visão geral das extensões de mensagens na plataforma Microsoft Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 54c0ce0139f6d70aca0c002edff2c60065c48b7b
ms.sourcegitcommit: 430bf416bb8d1b74f926c8b5d5ffd3dbb0782286
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65297139"
---
# <a name="message-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários interajam com seu serviço da Web por meio de botões e formulários no cliente Microsoft Teams. Eles podem pesquisar ou iniciar ações em um sistema externo a partir da área de composição da mensagem, da caixa de comando ou diretamente de uma mensagem. Em seguida, você pode enviar os resultados dessa interação de volta ao cliente Microsoft Teams, geralmente na forma de um cartão ricamente formatado.

Este documento fornece uma visão geral da extensão de mensagem, das tarefas executadas em diferentes cenários, do trabalho da extensão de mensagem, dos comandos de ação e de pesquisa e do desenrolamento de link.

A imagem a seguir exibe os locais dos quais as extensões de mensagem são invocadas:

:::image type="content" source="~/assets/images/messaging-extension-invoke-locations.png" alt-text="localizações de invocação de extensão de mensagem":::

> [!NOTE]
> @mencionar extensões de mensagem não tem mais suporte na caixa de redação.

## <a name="scenarios-where-message-extensions-are-used"></a>Cenários em que as extensões de mensagem são usadas

| Cenário | Exemplo |
|:-----------------|:-----------------|
|Você deseja que algum sistema externo execute uma ação e o resultado da ação seja enviado de volta para sua conversa.|Reserve um recurso e permita que o canal saiba o intervalo de tempo reservado.|
|Você deseja encontrar algo em um sistema externo e compartilhar os resultados com a conversa.|Pesquise um item de trabalho e compartilhe-o com o grupo como um Cartão adaptável.|
|Você deseja concluir uma tarefa complexa envolvendo várias etapas ou muitas informações em um sistema externo e compartilhar os resultados com uma conversa.|Crie um bug no seu sistema de acompanhamento com base em uma mensagem do Teams, atribua esse bug a um usuário e envie um cartão para o thread da conversa com os detalhes do bug.|

## <a name="understand-how-message-extensions-work"></a>Entenda como funcionam as extensões de mensagem

No Microsoft Teams, uma extensão de mensagem consiste em um serviço Web que você hospeda e um manifesto do aplicativo, que define onde seu serviço Web está hospedado. Elas tiram proveito do esquema de mensagens do Bot Framework e do protocolo de comunicação seguro, portanto, você também precisará registrar seu serviço da web como um bot no Bot Framework.

> [!NOTE]
> Embora você possa criar o serviço Web manualmente, use [DSK do Bot Framework](https://github.com/microsoft/botframework-sdk) para trabalhar com o protocolo.

No manifesto do aplicativo para o aplicativo do Microsoft Teams, uma única extensão de mensagem é definida com até dez comandos diferentes. Cada comando define um tipo, como ação ou pesquisa e os locais no cliente de onde ele é invocado. Os locais de invocação são área de composição de mensagem, barra de comandos e mensagem. Ao invocar, o serviço Web recebe uma mensagem HTTPS com uma carga JSON, incluindo todas as informações relevantes. Responda com uma carga JSON, permitindo que o cliente do Teams saiba a próxima interação a ser habilitada.

## <a name="types-of-message-extension-commands"></a>Tipos de comandos de extensão de mensagem

Há dois tipos de comandos de extensão de mensagem: comando de ação e comando de pesquisa. O tipo de comando de extensão de mensagem define os elementos de interface do usuário e os fluxos de interação disponíveis para seu serviço Web. Algumas interações, como autenticação e configuração, estão disponíveis para ambos os tipos de comandos.

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação permitem apresentar a seus usuários um pop-up modal para coletar ou exibir informações. Quando o usuário envia o formulário, o serviço Web responde inserindo uma mensagem diretamente na conversa ou inserindo uma mensagem na área de redação da mensagem. Depois disso, o usuário pode enviar a mensagem. Você pode encadear vários formulários para fluxos de trabalho mais complexos.

Os comandos de ação podem ser acionados na área de composição da mensagem, na caixa de comando ou em uma mensagem. Quando o comando é invocado de uma mensagem, a carga JSON inicial enviada ao bot inclui a mensagem inteira da qual ele foi invocado. A imagem a seguir exibe o módulo de tarefa de comando de ação de extensão de mensagem:

:::image type="content" source="~/assets/images/task-module.png" alt-text="Módulo de tarefa de comando de ação de extensão de mensagem":::

### <a name="search-commands"></a>Comandos de pesquisa

Os comandos de pesquisa permitem que seus usuários pesquisem informações em um sistema externo (manualmente por meio de uma caixa de pesquisa ou colando um link para um domínio monitorado na área de redigir mensagem) e, em seguida, inserir os resultados da pesquisa em uma mensagem. No fluxo de comando de pesquisa mais básico, a mensagem de chamada inicial incluirá a sequência de pesquisa enviada pelo usuário. Você responderá com uma lista de cartões e visualizações de cartões. O cliente do Teams renderiza uma lista de visualizações de cartão para o usuário. Quando o usuário seleciona um cartão, o cartão de tamanho completo é inserido na área de redação da mensagem.

Os cartões são disparados da área de mensagem de redação ou da caixa de comando e não são disparados de uma mensagem. Eles não podem ser disparados de uma mensagem.
A imagem a seguir exibe o módulo de tarefa de comando de pesquisa de extensão de mensagem:

:::image type="content" source="~/assets/images/search-extension.png" alt-text="Comando de pesquisa da extensão de mensagem":::

> [!NOTE]
> Para obter mais informações sobre cartões, consulte [o que são cartões](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Desenrolamento de link

Um serviço Web é invocado quando uma URL é colada na área de mensagem de redação. Essa funcionalidade é conhecida como desenrolamento de link. Você pode assinar para receber uma invocação quando as URLs que contêm um domínio específico são coladas na área de mensagem de redação. Seu serviço Web pode "desenrolar" a URL em um cartão detalhado, fornecendo mais informações do que o cartão de visualização do site padrão. Você pode adicionar botões para permitir que os usuários executem ações imediatamente sem sair do cliente do Microsoft Teams.
As imagens a seguir exibem o recurso de desenrolamento de link quando um link é colado na extensão de mensagem:

:::image type="content" source="../assets/images/messaging-extension/unfurl-link.png" alt-text="desenrolar link":::

![Desenrolamento de link](../assets/images/messaging-extension/link-unfurl.gif)

## <a name="code-snippets"></a>Trechos de código

O código a seguir fornece um exemplo de ação baseada em extensões de mensagem:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

 protected override Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
        {
            // Handle different actions using switch
            switch (action.CommandId)
            {
                case "HTML":
                    return new MessagingExtensionActionResponse
                    {
                        Task = new TaskModuleContinueResponse
                        {
                            Value = new TaskModuleTaskInfo
                            {
                                Height = 200,
                                Width = 400,
                                Title = "Task Module HTML Page",
                                Url = baseUrl + "/htmlpage.html",
                            },
                        },
                    };
                // return TaskModuleHTMLPage(turnContext, action);
                default:
                    string memberName = "";
                    var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
                    memberName = member.Name;
                    return new MessagingExtensionActionResponse
                    {
                        Task = new TaskModuleContinueResponse
                        {
                            Value = new TaskModuleTaskInfo
                            {
                                Card = <<AdaptiveAction card json>>,
                                Height = 200,
                                Width = 400,
                                Title = $"Welcome {memberName}",
                            },
                        },
                    };
            }
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

    async handleTeamsMessagingExtensionFetchTask(context, action) {
        switch (action.commandId) {
            case 'Static HTML':
                return staticHtmlPage();
        }
    }

    staticHtmlPage(){
        return {
            task: {
                type: 'continue',
                value: {
                    width: 450,
                    height: 125,
                    title: 'Task module Static HTML',
                    url: `${baseurl}/StaticPage.html`
                }
            }
        };
    }

```

---

O código a seguir fornece um exemplo de pesquisa baseada em extensões de mensagem:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
        {
            var text = query?.Parameters?[0]?.Value as string ?? string.Empty;

            var packages = new[] {
            new { title = "A very extensive set of extension methods", value = "FluentAssertions" },
            new { title = "Fluent UI Library", value = "FluentUI" }};

            // We take every row of the results and wrap them in cards wrapped in MessagingExtensionAttachment objects.
            // The Preview is optional, if it includes a Tap, that will trigger the OnTeamsMessagingExtensionSelectItemAsync event back on this bot.
            var attachments = packages.Select(package =>
            {
                var previewCard = new ThumbnailCard { Title = package.title, Tap = new CardAction { Type = "invoke", Value = package } };
                if (!string.IsNullOrEmpty(package.title))
                {
                    previewCard.Images = new List<CardImage>() { new CardImage(package.title, "Icon") };
                }

                var attachment = new MessagingExtensionAttachment
                {
                    ContentType = HeroCard.ContentType,
                    Content = new HeroCard { Title = package.title },
                    Preview = previewCard.ToAttachment()
                };

                return attachment;
            }).ToList();

            // The list of MessagingExtensionAttachments must we wrapped in a MessagingExtensionResult wrapped in a MessagingExtensionResponse.
            return new MessagingExtensionResponse
            {
                ComposeExtension = new MessagingExtensionResult
                {
                    Type = "result",
                    AttachmentLayout = "list",
                    Attachments = attachments
                }
            };
        }
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

async handleTeamsMessagingExtensionQuery(context, query) {
        const searchQuery = query.parameters[0].value;     
        const attachments = [];
                const response = await axios.get(`http://registry.npmjs.com/-/v1/search?${ querystring.stringify({ text: searchQuery, size: 8 }) }`);
                
                response.data.objects.forEach(obj => {
                        const heroCard = CardFactory.heroCard(obj.package.name);
                        const preview = CardFactory.heroCard(obj.package.name);
                        preview.content.tap = { type: 'invoke', value: { description: obj.package.description } };
                        const attachment = { ...heroCard, preview };
                        attachments.push(attachment);
                });
    
                return {
                    composeExtension:  {
                           type: 'result',
                           attachmentLayout: 'list',
                           attachments: attachments
                    }
                };
            }       
        }
```

---

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|------------|-------------|----------------|------------|------------|
| Extensão de mensagem com comandos baseados em ação | Este exemplo ilustra como criar uma extensão de mensagem baseada em ação. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Extensão de mensagem com comandos baseados em pesquisa | Este exemplo ilustra como criar uma extensão de mensagem baseada em pesquisa. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
|Ação de extensão de mensagem para agendamento de tarefas|Este exemplo ilustra como agendar uma tarefa do comando de ação de extensão de mensagem e obter um cartão de lembrete em uma data e hora agendadas.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Defina o comando de extensão de mensagem de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)

## <a name="see-also"></a>Confira também

* [Defina o comando de extensão de mensagem de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Crie uma extensão de mensagem](../build-your-first-app/build-messaging-extension.md)
