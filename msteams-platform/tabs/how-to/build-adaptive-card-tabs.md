---
title: Criar guias de cartão adaptáveis
author: KirtiPereira
description: Criar guias usando Cartões Adaptáveis
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 4359b20d5839b86955082b7a5da8db262e13600c
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179899"
---
# <a name="build-tabs-with-adaptive-cards"></a>Criar guias com Cartões Adaptáveis

> [!IMPORTANT]
> * Esse recurso está na [Visualização do Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md) e tem suporte na área de trabalho e em dispositivos móveis. O suporte no navegador da Web está chegando em breve.
> * Atualmente, as guias com Cartões Adaptáveis têm suporte apenas como aplicativos pessoais.

Ao desenvolver uma guia usando o método tradicional, você pode executar esses problemas, como considerações HTML e CSS, tempos de carga lentos, restrições de iFrame e manutenção e custos do servidor. As guias Cartão Adaptável são uma nova maneira de criar guias no Teams. Em vez de incorporar conteúdo da Web em um IFrame, você pode renderizar Cartões Adaptáveis em uma guia. Enquanto o front-end é renderizado com Cartões Adaptáveis, o back-end é alimentado por um bot. O bot é responsável por aceitar solicitações e responder adequadamente com o Cartão Adaptável renderizado.

Você pode criar suas guias com blocos de IU (interface do usuário) prontos que pareçam nativos na área de trabalho, na Web e no celular. Este artigo ajuda você a entender as alterações necessárias para serem feitas no manifesto do aplicativo, como as solicitações de atividade de invocação e envia informações na guia com Cartões Adaptáveis e o impacto no fluxo de trabalho do módulo de tarefas.

A imagem a seguir mostra guias de com build com Cartões Adaptáveis na área de trabalho e no celular:

:::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Exemplo de Cartão Adaptável renderizado em guias." border="false":::

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a usar Cartões Adaptáveis para criar guias, você deve:

* Familiarizar-se com o desenvolvimento [de bots,](../../bots/what-are-bots.md)cartões [adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)e [módulos](../../task-modules-and-cards/task-modules/task-modules-bots.md) de tarefa no Teams.
* Tenha um bot em execução Teams seu desenvolvimento.
* Estar em [Visualização de Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="changes-to-app-manifest"></a>Alterações no manifesto do aplicativo

Aplicativos pessoais que renderizar guias devem incluir uma `staticTabs` matriz no manifesto do aplicativo. As guias Cartão Adaptável são renderizadas quando `contentBotId` a propriedade é fornecida na `staticTab` definição. As definições de tabulação estáticas devem conter uma guia , especificando uma guia Cartão Adaptável ou uma , especificando uma experiência típica de guia de `contentBotId` `contentUrl` conteúdo da Web hospedada.

> [!NOTE]
> A propriedade está disponível no manifesto `contentBotId` versão 1.9 ou posterior.

Forneça a propriedade com a guia Cartão Adaptável com a que `contentBotId` `botId` deve se comunicar. A guia Cartão Adaptável configurada é enviada no parâmetro de cada solicitação de invocação e pode ser usada para diferenciar guias de cartão adaptáveis que são alimentadas pelo `entityId` `tabContext` mesmo bot. Para obter mais informações sobre outros campos de definição de tabulação estática, consulte [esquema de manifesto](../../resources/schema/manifest-schema.md#statictabs).

A seguir está um manifesto de guia cartão adaptável de exemplo:

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

A comunicação entre sua guia Cartão Adaptável e seu bot é feita por meio de `invoke` atividades. Cada `invoke` atividade tem um nome **correspondente**. Use o nome de cada atividade para diferenciar cada solicitação. `tab/fetch` e `tab/submit` são as atividades abordadas nesta seção.

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a>Buscar Cartão Adaptável para renderizar em uma guia

`tab/fetch`é a primeira solicitação de invocação que seu bot recebe quando um usuário abre uma guia Cartão Adaptável. Quando o bot recebe a solicitação,  ele envia uma resposta de continuação de tabulação ou uma **resposta de tabulação.**
A **resposta continue** inclui uma matriz para **cartões**, que é renderizada verticalmente para a guia na ordem da matriz.

> [!NOTE]
> Para obter mais informações sobre **a resposta de autenticação,** consulte [authentication](#authentication).

O código a seguir fornece exemplos de `tab/fetch` solicitação e resposta:

**`tab/fetch` request**

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

**`tab/fetch` response**

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
                }
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

Depois que um Cartão Adaptável é renderizado na guia, ele deve ser capaz de responder às interações do usuário. Essa resposta é manipulada pela `tab/submit` solicitação de invocação.

Quando um usuário seleciona um botão na guia Cartão Adaptável, a solicitação é disparada para o bot com os dados correspondentes por meio da função `tab/submit` `Action.Submit` de Cartão Adaptável. Os dados do Cartão Adaptável estão disponíveis por meio da propriedade data da `tab/submit` solicitação. Você recebe uma das seguintes respostas à sua solicitação:

* Uma resposta de código de status HTTP `200` sem corpo. Uma resposta 200 vazia não resulta em nenhuma ação tomada pelo cliente.
* A guia `200` padrão **continua** a resposta, conforme explicado em [fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab). Uma resposta **de continuação** de tabulação dispara o cliente para atualizar a guia Cartão Adaptável renderizado com os Cartões Adaptáveis fornecidos na matriz de cartões da **resposta continuar.**

O código a seguir fornece exemplos de `tab/submit` solicitação e resposta:

**`tab/submit` request**

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

**`tab/submit` response**

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

O módulo de tarefa também usa Cartão Adaptável para invocar `task/fetch` e `task/submit` solicitações e respostas. Para obter mais informações, [consulte using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).

Com a introdução da guia Cartão Adaptável, há uma alteração na forma como o bot responde a uma `task/submit` solicitação. Se você estiver usando uma guia Cartão Adaptável, o bot responderá à solicitação de invocação com a guia padrão continuará a resposta e `task/submit` fechará o módulo de tarefa.  A guia Cartão Adaptável é atualizada renderizando a nova lista de cartões fornecidos na guia continuar **o** corpo da resposta.

### <a name="invoke-taskfetch"></a>Invocar `task/fetch`

O código a seguir fornece exemplos de `task/fetch` solicitação e resposta:

**`task/fetch` request**
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

**`task/fetch` response**

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

**`task/submit` request**

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

**`task/submit` tipo de resposta de tabulação**

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

Nas seções anteriores deste artigo, você viu que a maioria dos paradigmas de desenvolvimento pode ser estendida das solicitações e respostas do módulo de tarefas em solicitações e respostas de tabulação. Quando se trata de lidar com a autenticação, a guia fluxo de trabalho para Cartão Adaptável segue o padrão de autenticação para extensões de mensagens. Para obter mais informações, consulte [add authentication](../../messaging-extensions/how-to/add-authentication.md).

`tab/fetch`solicitações podem ter uma **resposta continue** **ou auth.** Quando uma solicitação é acionada e recebe uma resposta `tab/fetch` **de tabulação,** a página de login é mostrada ao usuário.

**Para obter um código de autenticação por meio de `tab/fetch` invocação**

1. Abra seu aplicativo. A página de login é exibida.

    > [!NOTE]
    > O logotipo do aplicativo é fornecido por meio `icon` da propriedade definida no manifesto do aplicativo. O título que aparece depois que o logotipo é definido na `title` propriedade retornada no corpo **da resposta de tabulação.**

1. Selecione **Entrar**.  Você é redirecionado para a URL de autenticação fornecida na `value` propriedade do corpo **da** resposta de autenticação.
1. Uma janela pop-up será exibida. Essa janela pop-up hospeda sua página da Web usando a URL de autenticação.
1. Depois de entrar, feche a janela. Um **código de autenticação** é enviado para o Teams cliente.
1. O Teams cliente em seguida reeditará a solicitação para seu serviço, que inclui o código de autenticação fornecido `tab/fetch` pela página da Web hospedada.

### <a name="tabfetch-authentication-data-flow"></a>`tab/fetch` fluxo de dados de autenticação

A imagem a seguir fornece uma visão geral de como o fluxo de dados de autenticação funciona para uma `tab/fetch` invocação.

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Exemplo de fluxo de tabulação de cartão adaptável." border="false":::

**`tab/fetch` resposta de auth**

O código a seguir fornece um exemplo de `tab/fetch` resposta de auth:

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

O código a seguir mostra um exemplo de solicitação reeditar:

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

## <a name="see-also"></a>Confira também

* [Cartão Adaptável](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Link de guias desdobradas e Exibição de Estágio](~/tabs/tabs-link-unfurling.md)