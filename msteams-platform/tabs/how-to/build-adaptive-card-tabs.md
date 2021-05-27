---
title: Criar guias de cartão adaptáveis
author: KirtiPereira
description: Criar guias usando Cartões Adaptáveis
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: d65fc537b5282c050d891a6a73ff114c630e2c1c
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668845"
---
# <a name="build-tabs-with-adaptive-cards"></a>Criar guias com Cartões Adaptáveis

> [!IMPORTANT]
> * Esse recurso está na [Visualização do Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md) e tem suporte na área de trabalho e em dispositivos móveis. O suporte no navegador da Web está chegando em breve.
> * Atualmente, as guias com Cartões Adaptáveis têm suporte apenas como aplicativos pessoais.

Use Cartões Adaptáveis para criar guias com facilidade. Você pode criar suas guias com blocos de IU da Interface do Usuário prontos que pareçam nativos na área de trabalho, na Web e no celular. A criação de guias com Cartões Adaptáveis centraliza todos os recursos do aplicativo Teams em torno de um back-end de bot e front-end cartão adaptável, eliminando a necessidade de um back-back diferente para seu bot e guias. Isso reduz consideravelmente os custos de servidor e manutenção do seu Teams app. Este artigo ajuda você a entender as alterações necessárias para serem feitas no manifesto do aplicativo, como as solicitações de atividade de invocação e envia informações na guia com Cartões Adaptáveis e o impacto no fluxo de trabalho do módulo de tarefas. 

A imagem a seguir mostra guias de com build com Cartões Adaptáveis na área de trabalho e no celular: :::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Exemplo de Cartão Adaptável renderizado em guias." border="false":::

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a usar Cartões Adaptáveis para criar guias, você deve:

* Familiarizar-se com o desenvolvimento [de bots,](../../bots/what-are-bots.md)cartões [adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)e [módulos de tarefa](../../task-modules-and-cards/task-modules/task-modules-bots.md) no Teams.
* Tenha um bot em execução Teams seu desenvolvimento.
* Estar em [Visualização de Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="changes-to-app-manifest"></a>Alterações no manifesto do aplicativo

Aplicativos pessoais que renderizar guias devem incluir uma `staticTabs` matriz no manifesto do aplicativo. A Guia cartão adaptável é renderizada quando `contentBotId` a propriedade é fornecida na `staticTab` definição. As definições de tabulação estáticas devem conter uma , especificando uma Guia de Cartão Adaptável ou uma , especificando uma experiência típica de guia de `contentBotId` `contentUrl` conteúdo da Web hospedado.

> [!NOTE]
> A `contentBotId` propriedade está disponível no momento versão 1.9 ou posterior. 

Forneça a propriedade com a guia cartão adaptável com a que `contentBotId` `botId` deve se comunicar. A configuração para a Guia Cartão Adaptável é enviada no parâmetro de cada solicitação de invocação e pode ser usada para diferenciar diferentes Guias de Cartão Adaptável que são alimentadas pelo `entityId` `tabContext` mesmo bot. Para obter mais informações sobre outros campos de definição de tabulação estática, consulte [esquema de manifesto](../../resources/schema/manifest-schema.md#statictabs).

A seguir está um manifesto de guia de cartão adaptável de exemplo:

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

A comunicação entre a guia Cartão Adaptável e o bot é feita por meio de `invoke` atividades. Cada `invoke` atividade tem um nome *correspondente*. Use o nome de cada atividade para diferenciar cada solicitação. `tab/fetch` e `tab/submit` são as atividades abordadas nesta seção.

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a>Buscar Cartão Adaptável para renderizar em uma guia

`tab/fetch` é a primeira solicitação de invocação que seu bot recebe quando um usuário abre uma Guia de Cartão Adaptável. Quando o bot receber a solicitação,  ele enviará uma resposta de continuação de tabulação ou uma **resposta de tabulação.**
A **resposta continue** inclui uma matriz para **cartões**, que é renderizada verticalmente para a guia na ordem da matriz.

> [!NOTE]
> A **resposta de autenticação** é explicada em detalhes na [seção autenticação.](#authentication)

Os seguintes trechos de código são exemplos de `tab/fetch` solicitação e resposta:

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

Quando um usuário seleciona um botão na guia Cartão Adaptável, a solicitação é disparada para o bot com os dados correspondentes por meio da `tab/submit` *função Action.Submit* do Cartão Adaptável. Os dados do Cartão Adaptável estão disponíveis por meio da propriedade data da `tab/submit` solicitação. Você receberá uma das seguintes respostas à sua solicitação:

* Uma resposta de código de status http `200` sem corpo. Uma resposta 200 vazia não resultará em nenhuma ação tomada pelo cliente.
* A guia `200` padrão **continua** a resposta, conforme explicado na seção Buscar [Cartão Adaptável.](#fetch-adaptive-card-to-render-to-a-tab) Uma resposta **de continuação** de tabulação dispara o cliente para atualizar a Guia cartão adaptável renderizado com os Cartões Adaptáveis fornecidos na matriz de cartões da **resposta continuar.**

Os seguintes trechos de código são exemplos de `tab/submit` solicitação e resposta:

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

O módulo de tarefa também usa Cartão Adaptável para invocar `task/fetch` e `task/submit` solicitações e respostas. Para obter mais informações, consulte [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).

No entanto, com a introdução da Guia Cartão Adaptável, há uma alteração na forma como o bot responde a uma `task/submit` solicitação. Se você estiver usando uma guia Cartão Adaptável, o bot responderá à solicitação de invocação com a guia padrão continuar a resposta e `task/submit` fechará o módulo de tarefa.  A Guia Cartão Adaptável é atualizada renderizando a nova lista de cartões fornecidos na guia continuar **o** corpo da resposta.

### <a name="invoke-taskfetch"></a>Invocar `task/fetch`

Os seguintes trechos de código são exemplos de `task/fetch` solicitação e resposta:

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

Os seguintes trechos de código são exemplos de `task/submit` solicitação e resposta:

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

Nas seções anteriores deste artigo, você viu que a maioria dos paradigmas de desenvolvimento poderia ser extrapolada das solicitações e respostas do módulo de tarefas em solicitações e respostas de tabulação. No entanto, quando se trata de lidar com a autenticação, o fluxo de trabalho para a Guia Cartão Adaptável segue o padrão de autenticação para extensões de mensagens. Para obter mais informações, consulte [add authentication](../../messaging-extensions/how-to/add-authentication.md). 

Na seção [invocar atividades,](#invoke-activities) você foi informado de que as solicitações podem ter uma `tab/fetch` resposta **continue** ou **auth.** Quando uma solicitação é acionada e recebe uma resposta `tab/fetch` **de tabulação,** a página de login é mostrada ao usuário. 

**Para obter um código de autenticação por meio de `tab/fetch` invocação**

1. Abra seu aplicativo. A página de login é exibida.

    > [!NOTE]
    > O logotipo do aplicativo é fornecido por meio da propriedade definida no manifesto do aplicativo e o título que aparece depois que o logotipo é definido na propriedade retornada no corpo da resposta de `icon` `title` **tabulação.**

1. Selecione **Entrar**.  Você é redirecionado para a URL de autenticação fornecida na `value` propriedade do corpo **da** resposta de autenticação. 
1. Uma janela pop-up será exibida. Essa janela pop-up hospeda sua página da Web usando a URL de autenticação.
1. Depois de entrar, feche a janela. Um *código de autenticação* é enviado para o Teams cliente.
1. O Teams cliente em seguida reeditará a solicitação para seu serviço, que inclui o código de autenticação fornecido `tab/fetch` pela página da Web hospedada. 

### <a name="tabfetch-authentication-data-flow"></a>`tab/fetch` fluxo de dados de autenticação

A imagem a seguir fornece uma visão geral de como o fluxo de dados de autenticação funciona para uma `tab/fetch` invocação.

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Exemplo de fluxo de tabulação de cartão adaptável." border="false":::

**`tab/fetch` resposta de auth**

O trecho de código a seguir é um exemplo de `tab/fetch` resposta de auth:

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

Veja a seguir um exemplo de solicitação reeditar:

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

> [!div class="nextstepaction"]
> [Cartão Adaptável](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)

