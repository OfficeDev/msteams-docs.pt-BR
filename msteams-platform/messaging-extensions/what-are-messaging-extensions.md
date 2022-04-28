---
title: Extensões de mensagem
author: surbhigupta
description: Uma visão geral das extensões de mensagem na Microsoft Teams plataforma
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: c81f8ec4b1158275ab796883b268d2c7fa6ecfe8
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104109"
---
# <a name="message-extensions"></a>Extensões de mensagem

As extensões de mensagem permitem que os usuários interajam com seu serviço Web por meio de botões e formulários no Microsoft Teams cliente. Eles podem pesquisar ou iniciar ações em um sistema externo na área de mensagem de composição, na caixa de comando ou diretamente de uma mensagem. Você pode enviar de volta os resultados dessa interação para o cliente Microsoft Teams na forma de um cartão com formato avançado. Este documento fornece uma visão geral da extensão de mensagem, tarefas executadas em diferentes cenários, trabalho da extensão de mensagem, comandos de ação e pesquisa e de desaplicação de link.

A imagem a seguir exibe os locais dos quais as extensões de mensagem são invocadas:

![locais de invocação de extensão de mensagem](~/assets/images/messaging-extension-invoke-locations.png)

> [!NOTE]
> @mentioning extensões de mensagem não tem mais suporte na caixa de redação.

## <a name="scenarios-where-message-extensions-are-used"></a>Cenários em que as extensões de mensagem são usadas

| Cenário | Exemplo |
|:-----------------|:-----------------|
|Você deseja que algum sistema externo execute uma ação e o resultado da ação seja enviado de volta para sua conversa.|Reserve um recurso e permita que o canal saiba o intervalo de tempo reservado.|
|Você deseja encontrar algo em um sistema externo e compartilhar os resultados com a conversa.|Pesquise um item de trabalho Azure DevOps e compartilhe-o com o grupo como um Cartão Adaptável.|
|Você deseja concluir uma tarefa complexa envolvendo várias etapas ou muitas informações em um sistema externo e compartilhar os resultados com uma conversa.|Crie um bug no sistema de rastreamento com base em uma mensagem Teams, atribua esse bug a Bob e envie um cartão para o thread de conversa com os detalhes do bug.|

## <a name="understand-how-message-extensions-work"></a>Entender como funcionam as extensões de mensagem

Uma extensão de mensagem consiste em um serviço Web que você hospeda e um manifesto do aplicativo, que define de onde o serviço Web é invocado no Microsoft Teams cliente. O serviço Web aproveita o esquema de mensagens do Bot Framework e o protocolo de comunicação segura, portanto, você deve registrar seu serviço Web como um bot no Bot Framework.

> [!NOTE]
> Embora você possa criar o serviço Web manualmente, use o [SDK do Bot Framework](https://github.com/microsoft/botframework-sdk) para trabalhar com o protocolo.

No manifesto do aplicativo para Microsoft Teams, uma única extensão de mensagem é definida com até dez comandos diferentes. Cada comando define um tipo, como ação ou pesquisa e os locais no cliente de onde ele é invocado. Os locais de invocação são área de composição de mensagem, barra de comandos e mensagem. Ao invocar, o serviço Web recebe uma mensagem HTTPS com uma carga JSON, incluindo todas as informações relevantes. Responda com uma carga JSON, permitindo que o Teams cliente saiba a próxima interação a ser habilitada.

## <a name="types-of-message-extension-commands"></a>Tipos de comandos de extensão de mensagem

Há dois tipos de comandos de extensão de mensagem, comando de ação e comando de pesquisa. O tipo de comando de extensão de mensagem define os elementos da interface do usuário e os fluxos de interação disponíveis para seu serviço Web. Algumas interações, como autenticação e configuração, estão disponíveis para ambos os tipos de comandos.

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação são usados para apresentar aos usuários um pop-up modal para coletar ou exibir informações. Quando o usuário envia o formulário, o serviço Web responde inserindo uma mensagem na conversa diretamente ou inserindo uma mensagem na área de composição da mensagem. Depois disso, o usuário pode enviar a mensagem. Você pode encadear vários formulários para fluxos de trabalho mais complexos.

Os comandos de ação são disparados da área de mensagem de composição, da caixa de comando ou de uma mensagem. Quando o comando é invocado de uma mensagem, o conteúdo JSON inicial enviado ao bot inclui toda a mensagem da qual ele foi invocado. A imagem a seguir exibe o módulo de tarefa de comando de ação de extensão de mensagem: módulo ![de tarefa de comando de ação de extensão de mensagem](~/assets/images/task-module.png)

### <a name="search-commands"></a>Comandos de pesquisa

Os comandos de pesquisa permitem que os usuários pesquisem informações em um sistema externo manualmente por meio de uma caixa de pesquisa ou colando um link para um domínio monitorado na área de mensagem de composição e inserindo os resultados da pesquisa em uma mensagem. No fluxo de comando de pesquisa mais básico, a mensagem de invocação inicial inclui a cadeia de caracteres de pesquisa que o usuário enviou. Você responde com uma lista de cartões e visualizações de cartão. O Teams renderiza uma lista de visualizações de cartão para o usuário. Quando o usuário seleciona um cartão na lista, o cartão de tamanho completo é inserido na área de composição da mensagem.

Os cartões são disparados da área de mensagem de composição ou da caixa de comando e não são disparados de uma mensagem. Eles não podem ser disparados de uma mensagem.
A imagem a seguir exibe o módulo de tarefa de comando de pesquisa de extensão de mensagem:

![comando de pesquisa de extensão de mensagem](~/assets/images/search-extension.png)

> [!NOTE]
> Para obter mais informações sobre cartões, veja [o que são cartões](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Desenrolamento de link

Um serviço Web é invocado quando uma URL é colada na área de mensagem de composição. Essa funcionalidade é conhecida como desfralização de link. Você pode assinar para receber uma invocação quando as URLs que contêm um determinado domínio são coladas na área de mensagem de composição. Seu serviço Web pode "desenrolar" a URL em um cartão detalhado, fornecendo mais informações do que o cartão de visualização do site padrão. Você pode adicionar botões para permitir que os usuários executem imediatamente uma ação sem sair do Microsoft Teams cliente.
As imagens a seguir exibem o recurso de desfralização de link quando um link é colado na extensão de mensagem:

![unfurl link](../assets/images/messaging-extension/unfurl-link.png)

![vincular desfralhamento](../assets/images/messaging-extension/link-unfurl.gif)

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
| Extensão de mensagem com comandos baseados em pesquisa | Este exemplo ilustra como criar uma extensão de mensagem baseada em pesquisa. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
|Ação de extensão de mensagem para agendamento de tarefas|Este exemplo ilustra como agendar uma tarefa do comando de ação de extensão de mensagem e obter um cartão de lembrete em uma data e hora agendadas.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Definir comando de extensão de mensagem de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)

## <a name="see-also"></a>Confira também

* [Definir comando de extensão de mensagem de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Criar uma extensão de mensagem](../build-your-first-app/build-messaging-extension.md)
