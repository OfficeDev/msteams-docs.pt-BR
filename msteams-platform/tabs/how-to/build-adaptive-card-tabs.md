---
title: Criar guias de cartão adaptável
author: KirtiPereira
description: Saiba como criar guias usando Cartões Adaptáveis em que o front-end é renderizado com Cartões Adaptáveis, o back-end é alimentado por um bot. Explore as atividades de invocação e manipule envios.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: c4b0db0f67af2cf28f5930d4ad0b09e51fb11815
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450461"
---
# <a name="build-tabs-with-adaptive-cards"></a>Criar guias com Cartões Adaptáveis

> [!IMPORTANT]
>
> As guias com Cartões Adaptáveis atualmente só têm suporte como aplicativos pessoais.

Ao desenvolver uma guia usando o método tradicional, você pode ter estes problemas:

* Considerações sobre HTML e CSS
* Tempos de carregamento lentos
* Restrições de iFrame
* Manutenção e custos do servidor

As guias do Cartão Adaptável são uma nova maneira de criar guias no Teams. Em vez de incorporar conteúdo da Web em um IFrame, você pode renderizar Cartões Adaptáveis em uma guia. Enquanto o front-end é renderizado com Adaptive Cards, o back-end é alimentado por um bot. O bot é responsável por aceitar solicitações e responder adequadamente com o Cartão Adaptável renderizado.

Você pode criar suas guias com blocos de construção prontos para interface do usuário (UI) nativos na área de trabalho, na Web e em dispositivos móveis. Este artigo ajuda você a entender as alterações necessárias para serem feitas no manifesto do aplicativo. O artigo também identifica como a atividade de invocação solicita e envia informações na guia com Cartões Adaptáveis e seu efeito no fluxo de trabalho do módulo de tarefa.

A imagem a seguir mostra guias de build com Cartões Adaptáveis desktop e móvel:

:::image type="content" source="../../assets/images/adaptive-cards-rendered-in-tabs.png" alt-text="Exemplo de Cartão Adaptável renderizado em guias.":::

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a Cartões Adaptáveis para criar guias, você deve:

* Familiarize-se com o [desenvolvimento de bots](../../bots/what-are-bots.md), [Cartões adaptáveis](https://adaptivecards.io/) e [módulos de tarefas](../../task-modules-and-cards/task-modules/task-modules-bots.md) no Teams.
* Tenha um bot em execução no Teams para seu desenvolvimento.

## <a name="changes-to-app-manifest"></a>Alterações no manifesto do aplicativo

Aplicativos pessoais que renderizam guias devem incluir uma matriz `staticTabs` no manifesto do aplicativo. As guias cartão adaptável são renderizadas quando a propriedade `contentBotId` é fornecida na definição `staticTab`. As definições de guia estáticas devem conter uma `contentBotId`, especificando uma guia Cartão Adaptável ou uma `contentUrl`, especificando uma experiência típica de guia de conteúdo da Web hospedada.

> [!NOTE]
> A propriedade `contentBotId` está disponível no manifesto versão 1.9 ou posterior.

Forneça a propriedade `contentBotId` com a `botId` com a qual a guia Cartão Adaptável deve se comunicar. O `entityId` configurado para a guia Cartão Adaptável é enviado no parâmetro `tabContext` de cada solicitação de invocação e pode ser usado para diferenciar as Guias de Cartão Adaptável que são ativadas pelo mesmo bot. Para obter mais informações sobre outros campos de definição de guia estática, consulte [esquema de manifesto](../../resources/schema/manifest-schema.md#statictabs).

A seguir está um exemplo de manifesto da guia Cartão Adaptável:

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
  "id": "00000000-0000-0000-0000-000000000000",
  "version": "0.0.1",
  "packageName": "acprototype",
  "developer": {
    "name": "Contoso",
    "websiteUrl": "https://contoso.yourwebsite.com",
    "privacyUrl": "https://contoso.yourwebsite.com/privacy.html",
    "termsOfUseUrl": "https://contoso.yourwebsite.com/terms.html"
  },
  "name": {
    "short": "Contoso",
    "full": "Contoso Home"
  },
  "description": {
    "short": "Add short description here",
    "full": "Add full description here"
  },
  "icons": {
    "outline": "icon-outline.png",
    "color": "icon-color.png"
  },
  "accentColor": "#D85028",
  "configurableTabs": [],
  "staticTabs": [
    {
      "entityId": "homeTab",
      "name": "Home",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    },
    {
      "entityId": "moreTab",
      "name": "More",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    }
  ],
  "connectors": [],
  "composeExtensions": [],
  "permissions": ["identity", "messageTeamMembers"],
  "validDomains": [
    "contoso.yourwebsite.com",
    "token.botframework.com"
  ]
}
```

## <a name="invoke-activities"></a>Invocar atividades

A comunicação entre a guia Cartão Adaptável e o bot é feita por meio de `invoke` atividades. Cada atividade `invoke` tem um **nome** correspondente. Use o nome de cada atividade para diferenciar cada solicitação. `tab/fetch` e `tab/submit` são as atividades abordadas nesta seção.

> [!NOTE]
>
> * Os bots precisam enviar todas as respostas para [serviço URL](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#base-uri&preserve-view=true). A URL do serviço é recebida como parte do conteúdo `activity`.
> * O tamanho da carga de invocação aumentou para 80 kb.

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a>Buscar Cartão Adaptável para renderizar em uma guia

`tab/fetch` é a primeira solicitação de invocação que seu bot recebe quando um usuário abre uma guia Cartão Adaptável. Quando seu bot recebe a solicitação, ele envia uma resposta de **continuação** de guia ou uma resposta de **autenticação** de guia.
A resposta **continue** inclui uma matriz para **cartas**, que é renderizada verticalmente na guia na ordem da matriz.

> [!NOTE]
> Para obter mais informações sobre a resposta de **autenticação**, consulte [autenticação](#authentication).

O código a seguir fornece exemplos de `tab/fetch` solicitação e resposta:

**`tab/fetch` solicitação**

```json
// tab/fetch POST request: agents/{botId}/invoke
{
    "name": "tab/fetch",
    "value: {
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        },
        "context": {
            "theme": "default"
            }
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}"
}
```

**`tab/fetch` resposta**

```json
// tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
                {
                    "card": adaptiveCard1,
                },
                {
                    "card": adaptiveCard2,
                },
                {
                    "card": adaptiveCard3
                }  
            ]
        },
    },
    "responseType": "tab"
}
```

### <a name="handle-submits-from-adaptive-card"></a>Manipular envios do Cartão Adaptável

Depois que um Cartão Adaptável é renderizado na guia, ele pode responder às interações do usuário. Essa resposta é tratada pela solicitação `tab/submit` invocação.

Quando um usuário seleciona um botão na guia Cartão Adaptável, a solicitação `tab/submit` é disparada para o bot com os dados correspondentes por meio da função `Action.Submit` do Cartão Adaptável. Os dados do Cartão Adaptável estão disponíveis por meio da propriedade de dados da solicitação `tab/submit`. Você recebe uma das seguintes respostas à sua solicitação:

* Um código de status HTTP `200` resposta sem corpo. Uma resposta 200 vazia não resulta em nenhuma ação executada pelo cliente.
* A guia `200` padrão **continua** a resposta, conforme explicado em buscar [Cartão Adaptável](#fetch-adaptive-card-to-render-to-a-tab). Uma resposta de **continuação** de guia aciona o cliente para atualizar a guia Cartão Adaptável renderizada com os Cartões Adaptáveis fornecidos na matriz de cartões da resposta de **continuação**.

O código a seguir fornece exemplos de `tab/submit` solicitação e resposta:

**`tab/submit` solicitação**

```json
// tab/submit POST request: agents/{botId}/invoke:
{
    "name": "tab/submit",
    "value": {
        "data": {
            "type": "tab/submit",
            //...<data properties>
            },
        "context": {
            "theme": "default"
            },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
            },
        },
    "conversation": {
           "id": "{generated_conversation_id}" 
        },
    "imdisplayname": "{user_display_name}"
}
```

**`tab/submit` resposta**

```json
//tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
              {
                "card": adaptiveCard1,
                },
              {
                "card": adaptiveCard2,
                } 
            ]
        },
    },
    "responseType": "tab"
}
```

## <a name="understand-task-module-workflow"></a>Entender o fluxo de trabalho do módulo de tarefas

O módulo de tarefa também usa o Cartão Adaptável para invocar solicitações e respostas `task/fetch` e `task/submit`. Para obter mais informações, consulte [o uso de módulos de tarefas em bots do Microsoft Teams](../../task-modules-and-cards/task-modules/task-modules-bots.md).

Com a introdução da guia Cartão Adaptável, há uma alteração em como o bot responde a uma solicitação `task/submit`. Se você estiver usando uma guia Cartão Adaptável, o bot responderá à solicitação de invocação `task/submit` com a guia padrão **continuar** e fechará o módulo de tarefa. A guia Cartão Adaptável é atualizada renderizando a nova lista de cartões fornecidos na guia **continuar corpo** da resposta.

### <a name="invoke-taskfetch"></a>Invocar `task/fetch`

O código a seguir fornece exemplos de `task/fetch` solicitação e resposta:

**`task/fetch` solicitação**

```json
// task/fetch POST request: agents/{botId}/invoke
{
    "name": "task/fetch",
    "value": {
        "data": {
            "type": "task/fetch"
        },
        "context": {
            "theme": "default",
        },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        }
    },
    "imdisplayname": "{user_display_name}",
    "conversation": {
        "id": "{generated_conversation_id}"
    } 
}
```

**`task/fetch` resposta**

```json
// task/fetch POST response: agents/{botId}/invoke
{
    "task": {
        "value": {
            "title": "Ninja Cat",
            "height": "small",
            "width": "small",
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": adaptiveCard,
            }
        },
    "type": "continue"
    },
    "responseType": "task"
}
```

### <a name="invoke-tasksubmit"></a>Invocar `task/submit`

O código a seguir fornece exemplos de `task/submit` solicitação e resposta:

**`task/submit` solicitação**

```json
// task/submit POST request: agent/{botId}/invoke:
{
    "name": "task/submit",
    "value": {
        "data": {serialized_data_object},
        "context": {
            "theme": "default"
        },
    "tabContext": {
        "tabEntityId": "{tab_entity_id}"
        },
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}",
}
```

**`task/submit` tipo de resposta da guia**

```json
// tab/fetch **continue** POST response: 
{
    "task":{
        "value": {
            "tab": {
                "type": "continue",
                "value": {
                    "cards": [
                        {
                            "card": adaptiveCard1
                        },
                        {
                            "card": adaptiveCard2
                        }
                    ]
                }
            }
        },
        "type": "continue"
    },
    "responseType": "task"
}
```

## <a name="authentication"></a>Autenticação

Nas seções anteriores, você viu que a maioria dos paradigmas de desenvolvimento pode ser estendida das solicitações e respostas do módulo de tarefa em solicitações e respostas de tabulação. Quando se trata de lidar com a autenticação, o fluxo de trabalho para a guia Cartão Adaptável segue o padrão de autenticação para extensões de mensagem. Para obter mais informações, consulte [adicionar autenticação](../../messaging-extensions/how-to/add-authentication.md).

`tab/fetch` solicitações podem ter uma **continuar** ou uma resposta **autenticação**. Quando uma solicitação `tab/fetch` é disparada e recebe uma guia **autenticação**, a página de entrada é mostrada ao usuário.

**Para obter um código de autenticação por meio de `tab/fetch` invocar**

1. Abra seu aplicativo. A página de entrada é exibida.

    > [!NOTE]
    > O logotipo do aplicativo é fornecido por meio da propriedade `icon` definida no manifesto do aplicativo. O título que aparece após o logotipo é definido na propriedade `title` retornada no corpo da resposta de **autenticação** da guia.

1. Selecione **Entrar**.  Você será redirecionado para a URL de autenticação fornecida na propriedade `value` do corpo da resposta **auth**.
1. Uma janela pop-up será exibida. Essa janela pop-up hospeda sua página da Web usando a URL de autenticação.
1. Depois de entrar, feche a janela. Um **código de autenticação inicial** é enviado ao cliente do Teams.
1. Em seguida, o cliente do Teams emiti novamente a solicitação `tab/fetch` para seu serviço, que inclui o código de autenticação fornecido pela página da Web hospedada.

### <a name="tabfetch-authentication-data-flow"></a>`tab/fetch` fluxo de dados de autenticação

A imagem a seguir fornece uma visão geral de como o fluxo de dados de autenticação funciona para uma chamada `tab/fetch`.

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Exemplo de fluxo de autenticação da guia cartão adaptável.":::

**`tab/fetch` resposta de autenticação**

O código a seguir fornece um exemplo de `tab/fetch` resposta de autenticação:

```json
// tab/auth POST response (openURL)
{
    "tab": {
        "type": "auth",
        "suggestedActions":{
            "actions":[
                {
                    "type": "openUrl",
                    "value": "https://example.com/auth",
                    "title": "Sign in to this app"
                }
            ]
        }
    }
}
```

### <a name="example"></a>Exemplo

O código a seguir mostra um exemplo de solicitação reemitida:

```json
{
    "name": "tab/fetch",
    "type": "invoke",
    "timestamp": "2021-01-15T00:10:12.253Z",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "{id}",
        "name": "John Smith",
        "aadObjectId": "00000000-0000-0000-0000-000000000000"
    },
    "conversation": {
        "tenantId": "{tenantId}",
        "id": "tab:{guid}"
    },
    "recipients": {
        "id": "28:00000000-0000-0000-0000-000000000000",
        "name": "ContosoApp"
    },
    "entities": [
        {
            "locale": "en-us",
            "country": "US",
            "platform": "Windows",
            "timezone": "America/Los_Angeles",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": { "id": "00000000-0000-0000-0000-000000000000" },
        "source": { "name": "message" }
    },
    "value": {
        "tabContext": { "tabEntityId": "homeTab" },
        "state": "0.43195668034524815"
    },
    "locale": "en-US",
    "localTimeZone": "America/Los_Angeles"
}
```

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo** | **Descrição** |**.NET** | **Node.js** |
|----------------|-----------------|--------------|--------------|
| Mostrar Cartões Adaptáveis na guia Teams | Código de exemplo de guia do Microsoft Teams, que demonstra como mostrar Cartões Adaptáveis no Teams. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-adaptive-cards/csharp)| [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-adaptive-cards/nodejs) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Link de guias desdobradas e Exibição de Estágio](~/tabs/tabs-link-unfurling.md)

## <a name="see-also"></a>Confira também

* [Cartão Adaptável](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
