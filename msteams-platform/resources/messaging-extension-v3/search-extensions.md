---
title: Pesquisar com extensões de mensagem
description: Neste módulo, saiba como desenvolver extensões de mensagem baseadas em pesquisa
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 07/20/2019
ms.openlocfilehash: a555091558d66e070f09ec6df8338ac686657019
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142749"
---
# <a name="search-with-message-extensions"></a>Pesquisar com extensões de mensagem

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagem baseadas em pesquisa permitem que você consulte seu serviço e poste essas informações na forma de um cartão, diretamente em sua mensagem.

![Exemplo de cartão de extensão de mensagem](~/assets/images/compose-extensions/ceexample.png)

As seções a seguir descrevem como fazer isso:

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

## <a name="search-type-message-extensions"></a>Extensões de mensagem de tipo de pesquisa

Para a extensão de mensagem baseada em pesquisa, defina `type` o parâmetro como `query`. Veja abaixo um exemplo de um manifesto com um único comando de pesquisa. Uma única extensão de mensagem pode ter até 10 comandos diferentes associados a ela. Isso pode incluir várias pesquisas e vários comandos baseados em ação.

### <a name="complete-app-manifest-example"></a>Exemplo de manifesto completo do aplicativo

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.bing",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://bingbotservice.azurewebsites.net/",
    "privacyUrl": "http://bingbotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://bingbotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "Bing",
    "full": "Bing"
  },
  "description": {
    "short": "Find Bing search results",
    "full": "Find Bing search results and share them with your team members."
  },
  "icons": {
    "outline": "bing-outline.jpg",
    "color": "bing-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [{
          "id": "searchCmd",
          "description": "Search Bing for information on the web",
          "title": "Search",
          "initialRun": true,
          "parameters": [{
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "bingbotservice.azurewebsites.net",
    "*.bingbotservice.azurewebsites.net"
  ]
}
```

## <a name="test-via-uploading"></a>Testar por meio do upload

Você pode testar sua extensão de mensagem carregando seu aplicativo.

Para abrir sua extensão de mensagem, navegue até qualquer um dos seus chats ou canais. Escolha o **botão Mais opções** (**&#8943;**) na caixa de redação e escolha sua extensão de mensagem.

## <a name="add-event-handlers"></a>Adicionar manipuladores de eventos

A maior parte do seu trabalho envolve o `onQuery` evento, que manipula todas as interações na janela de extensão de mensagem.

Se você definir `canUpdateConfiguration` como `true` no manifesto, habilitará o item **de menu Configurações para sua** extensão de mensagem e também deverá manipular `onQuerySettingsUrl` e .`onSettingsUpdate`

## <a name="handle-onquery-events"></a>Manipular eventos onQuery

Uma extensão de mensagem recebe um `onQuery` evento quando algo acontece na janela de extensão da mensagem ou é enviado para a janela.

Se a extensão de mensagem usar uma página de configuração, `onQuery` o manipulador deverá primeiro verificar se há informações de configuração armazenadas; se a `config` extensão da mensagem não estiver configurada, retorne uma resposta com um link para a página de configuração. Lembre-se de que a resposta da página de configuração também é tratada por `onQuery`. A única exceção é quando a página de configuração é chamada pelo manipulador para `onQuerySettingsUrl`; consulte a seção a seguir:

Se a extensão de mensagem exigir autenticação, verifique as informações de estado do usuário; se o usuário não estiver conectado, siga as instruções [na seção](#authentication) Autenticação mais adiante neste tópico.

Em seguida, verifique se `initialRun` está definido; nesse caso, execute a ação apropriada, como fornecer instruções ou uma lista de respostas.

O restante do manipulador solicita `onQuery` informações ao usuário, exibe uma lista de cartões de visualização e retorna o cartão selecionado pelo usuário.

## <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Manipular eventos onQuerySettingsUrl e onSettingsUpdate

Os `onQuerySettingsUrl` eventos e `onSettingsUpdate` os eventos funcionam juntos para habilitar **o Configurações** item de menu.

![Capturas de tela de locais do Configurações item de menu](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

O manipulador para `onQuerySettingsUrl` retorna a URL para a página de configuração; depois que a página de configuração é fechado, `onSettingsUpdate` o manipulador para aceita e salva o estado retornado. Esse é o único caso em que `onQuery` *não recebe* a resposta da página de configuração.

## <a name="receive-and-respond-to-queries"></a>Receber e responder a consultas

Todas as solicitações para a extensão de mensagem são feitas por meio `Activity` de um objeto que é postado na URL de retorno de chamada. A solicitação contém informações sobre o comando do usuário, como valores de parâmetro e ID. A solicitação também fornece metadados sobre o contexto no qual sua extensão foi invocada, incluindo id de usuário e locatário, juntamente com ID de chat ou canal e IDs de equipe.

### <a name="receive-user-requests"></a>Receber solicitações de usuário

Quando um usuário executa uma consulta, o Microsoft Teams envia ao serviço um objeto padrão do Bot Framework`Activity`. Seu serviço deve executar sua lógica para um `Activity` que `type` foi definido `invoke` `name` como e definido `composeExtension` como um tipo com suporte, conforme mostrado na tabela a seguir.

Além das propriedades de atividade de bot padrão, a carga contém os seguintes metadados de solicitação:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação; deve ser `invoke`. |
|`name`| Tipo de comando que é emitido para o serviço. Atualmente, há suporte para os seguintes tipos: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Microsoft Azure Active Directory (Azure AD) do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Microsoft Azure Active Directory (Azure AD) do locatário. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`clientInfo`|Metadados opcionais sobre o software cliente usado para enviar a mensagem de um usuário. A entidade pode conter duas propriedades:<br>O `country` campo contém o local detectado pelo usuário.<br>O `platform` campo descreve a plataforma do cliente de mensagens. <br>Para obter informações adicionais, *consulte tipos* [de entidade não IRI — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Os parâmetros de solicitação em si são encontrados no objeto de valor, que inclui as seguintes propriedades:

| Nome da propriedade | Objetivo |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros: cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros de paginação: <br>`skip`: ignorar contagem para esta consulta <br>`count`: número de elementos a serem retornados |

#### <a name="request-example"></a>Exemplo de solicitação

```json
{
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "searchKeywords",
        "value": "Toronto"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  "type": "invoke",
  "timestamp": "2017-05-01T15:45:51.876Z",
  "localTimestamp": "2017-05-01T08:45:51.876-07:00",
  "id": "f:622749630322482883",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
    "name": "Larry Jin",
    "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
  },
  "conversation": {
    "id": "19:skypespaces_8198cfe0dd2647ae91930f0974768a40@thread.skype"
  },
  "recipient": {
    "id": "28:b4922ea1-5315-4fd0-9b21-d941ab06e39f",
    "name": "TheComposeExtensionDev"
  },
  "entities": [
    {
    "type": "clientInfo",
      "country": "US",
      "platform": "Windows"
    }
  ]
}
```

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Receber solicitações de links inseridos na caixa de mensagem de redação

Como alternativa (ou além disso) à pesquisa de seu serviço externo, você pode usar uma URL inserida na caixa de mensagem de composição para consultar seu serviço e retornar um cartão. Na captura de tela abaixo, um usuário cole uma URL para um item de trabalho Azure DevOps que a extensão de mensagem resolveu em um cartão.

![Exemplo de desenrolamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Para permitir que a extensão de mensagem interaja com links dessa maneira, `messageHandlers` primeiro você precisará adicionar a matriz ao manifesto do aplicativo, como no exemplo abaixo:

```json
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
]
```

Depois de adicionar o domínio para escutar o manifesto do aplicativo, você precisará alterar o código do bot para responder à solicitação de [](#respond-to-user-requests) invocação abaixo.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Se o aplicativo retornar vários itens, somente o primeiro será usado.

### <a name="respond-to-user-requests"></a>Responder às solicitações do usuário

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para seu serviço. Nesse ponto, seu código tem 5 segundos para fornecer uma resposta HTTP à solicitação. Durante esse tempo, seu serviço pode executar uma pesquisa adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados correspondentes à consulta do usuário. A resposta deve indicar um código de status HTTP e `200 OK` um objeto json/aplicativo válido com o seguinte corpo:

|Nome da propriedade|Objetivo|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Há suporte para os seguintes tipos: <br>`result`: exibe uma lista de resultados da pesquisa <br>`auth`: solicita que o usuário se autentique <br>`config`: solicita que o usuário configure a extensão de mensagem <br>`message`: exibe uma mensagem de texto simples |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`list`: uma lista de objetos de cartão que contêm campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos de anexo válidos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas de tipo `auth` ou `config`. |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message`. |

#### <a name="response-card-types-and-previews"></a>Tipos de cartão de resposta e visualizações

Damos suporte aos seguintes tipos de anexo:

* [cartão de Miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [cartão Hero](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para obter mais informações, consulte [Cartões para](~/task-modules-and-cards/what-are-cards.md) obter uma visão geral.

Para saber como usar os tipos de cartão em miniatura e hero, consulte [Adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

Para obter documentação adicional sobre o cartão Office 365 Connector, consulte [Usando cartões Office 365 Connector](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface Microsoft Teams interface do usuário com uma visualização de cada item. A visualização é gerada de uma das duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um cartão Hero ou Thumbnail.
* Extraído do básico `title`, e `text`propriedades `image` do anexo. Eles serão usados somente se a `preview` propriedade não estiver definida e essas propriedades estarão disponíveis.

Você pode exibir uma visualização de um cartão Adaptável ou conector Office 365 na lista de resultados simplesmente definindo sua propriedade de visualização; isso não será necessário se os resultados já forem cartões hero ou miniatura. Se você usar o anexo de visualização, ele deverá ser um cartão Hero ou Thumbnail. Se nenhuma propriedade de visualização for especificada, a visualização do cartão falhará e nada será exibido.

#### <a name="response-example"></a>Exemplo de resposta

Este exemplo mostra uma resposta com dois resultados, combinando formatos de cartão diferentes: Office 365 Connector e Adaptável. Embora você provavelmente queira manter um formato de cartão em sua resposta, `preview` `attachments` ele mostra como a propriedade de cada elemento na coleção deve definir explicitamente uma visualização em formato hero ou miniatura, conforme descrito acima.

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        }
      },
      {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Container",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "Microsoft Corp (NASDAQ: MSFT)",
                  "size": "medium",
                  "isSubtle": true
                },
                {
                  "type": "TextBlock",
                  "text": "September 19, 4:00 PM EST",
                  "isSubtle": true
                }
              ]
            },
            {
              "type": "Container",
              "spacing": "none",
              "items": [
                {
                  "type": "ColumnSet",
                  "columns": [
                    {
                      "type": "Column",
                      "width": "stretch",
                      "items": [
                        {
                          "type": "TextBlock",
                          "text": "75.30",
                          "size": "extraLarge"
                        },
                        {
                          "type": "TextBlock",
                          "text": "▼ 0.20 (0.32%)",
                          "size": "small",
                          "color": "attention",
                          "spacing": "none"
                        }
                      ]
                    },
                    {
                      "type": "Column",
                      "width": "auto",
                      "items": [
                        {
                          "type": "FactSet",
                          "facts": [
                            {
                              "title": "Open",
                              "value": "62.24"
                            },
                            {
                              "title": "High",
                              "value": "62.98"
                            },
                            {
                              "title": "Low",
                              "value": "62.20"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ],
          "version": "1.0"
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "Microsoft Corp (NASDAQ: MSFT)",
            "text": "75.30 ▼ 0.20 (0.32%)"
          }
        }
      }
    ]
  }
}
```

### <a name="default-query"></a>Consulta padrão

Se você definir `initialRun` como `true` no manifesto, Microsoft Teams emite uma consulta "padrão" quando o usuário abre a extensão de mensagem pela primeira vez. Seu serviço pode responder a essa consulta com um conjunto de resultados pré-preenchidos. Isso pode ser útil para exibir, por exemplo, itens exibidos recentemente, favoritos ou qualquer outra informação que não dependa da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, exceto com um parâmetro cujo `initialRun` valor de cadeia de caracteres é `true`.

#### <a name="request-example-for-a-default-query"></a>Exemplo de solicitação para uma consulta padrão

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "initialRun",
        "value": "true"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  ⋮
}
```

## <a name="identify-the-user"></a>Identifique o usuário

Cada solicitação para seus serviços inclui a ID ofuscada do usuário que executou a solicitação, bem como o nome de exibição do usuário e a ID de objeto Microsoft Azure Active Directory (Azure AD).

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

O `id` e `aadObjectId` os valores são garantidos como os do usuário Teams autenticado. Eles podem ser usados como chaves para pesquisar credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém a ID de locatário Microsoft Azure Active Directory (Azure AD) do usuário, que pode ser usada para identificar a organização do usuário. Se aplicável, a solicitação também contém as IDs de equipe e canal das quais a solicitação foi originada.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação de usuário, você precisará entrar no usuário antes que ele possa usar a extensão de mensagem. Se você tiver escrito um bot ou uma guia que conecte o usuário, esta seção deverá ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
2. Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID Teams usuário.
3. Se o usuário não tiver sido autenticado, envie uma resposta com `auth` uma ação `openUrl` sugerida, incluindo a URL de autenticação.
4. O Microsoft Teams cliente inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação fornecida.
5. Depois que o usuário entrar, você deverá fechar a janela e enviar um "código de autenticação" para o Teams cliente.
6. O Teams em seguida, emiti a consulta para o serviço, que inclui o código de autenticação passado na etapa 5.

O serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de entrada. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responder com uma ação de entrada

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo `openUrl` que inclui a URL de autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de entrada

```json
{
  "composeExtension":{
    "type":"auth",
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

> [!NOTE]
> Para que a experiência de entrada seja hospedada em um pop-up Teams, a parte de domínio da URL deve estar na lista de domínios válidos do aplicativo. Para obter mais informações, confira [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de entrada

Sua experiência de entrada deve ser responsiva e se ajustar em uma janela pop-up. Ela deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client), que usa a passagem de mensagens.

Assim como com outras experiências inseridas em execução no Microsoft Teams, o código dentro da janela precisa primeiro chamar `microsoftTeams.initialize()`. Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do Teams para sua janela, que poderá passá-la para a URL de entrada do OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de entrada

Quando a solicitação de entrada for concluída e redirecionada de volta para sua página, ela deverá executar as seguintes etapas:

1. Gere um código de segurança. (Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de entrada, como tokens OAuth 2.0.
2. Chamar `microsoftTeams.authentication.notifySuccess` e passar o código de segurança.

Neste ponto, a janela fecha e o controle é passado para o Teams cliente. O cliente agora pode emitir novamente a consulta de usuário original, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para pesquisar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e, em seguida, concluir a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação reemitida

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "type": "clientInfo",
        "country": "US",
        "platform": "Web",
        
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

## <a name="sdk-support"></a>Suporte ao SDK

### <a name="net"></a>.NET

Para receber e manipular consultas com o SDK do Bot Builder para .NET, `invoke` você pode verificar o tipo de ação na atividade de entrada e usar o método auxiliar no pacote NuGet [Microsoft.Bot.Connector.Teams para](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) determinar se é uma atividade de extensão de mensagem.

#### <a name="example-code-in-net"></a>Código de exemplo no .NET

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
    if (activity.Type == ActivityTypes.Invoke) // Received an invoke
    {
        if (activity.IsComposeExtensionQuery())
        {
            // This is the response object that will get sent back to the messaging extension request.
            ComposeExtensionResponse invokeResponse = null;

            // This helper method gets the query as an object.
            var query = activity.GetComposeExtensionQueryData();

            if (query.CommandId != null && query.Parameters != null && query.Parameters.Count > 0)
            {
                // query.Parameters has the parameters sent by client
                var results = new ComposeExtensionResult()
                {
                    AttachmentLayout = "list",
                    Type = "result",
                    Attachments = new List<ComposeExtensionAttachment>(),
                };
                invokeResponse.ComposeExtension = results;
            }

            // Return the response
            return Request.CreateResponse<ComposeExtensionResponse>(HttpStatusCode.OK, invokeResponse);
        } else
        {
            // Handle other types of Invoke activities here.
        }
    } else {
      // Failure case catch-all.
      var response = Request.CreateResponse(HttpStatusCode.BadRequest);
      response.Content = new StringContent("Invalid request! This API supports only messaging extension requests. Check your query and try again");
      return response;
    }
}
```

### <a name="nodejs"></a>Node.js

#### <a name="example-code-in-nodejs"></a>Código de exemplo no Node.js

```javascript
require('dotenv').config();

import * as restify from 'restify';
import * as builder from 'botbuilder';
import * as teamBuilder from 'botbuilder-teams';

class App {
    run() {
        const server = restify.createServer();
        let teamChatConnector = new teamBuilder.TeamsChatConnector({
            appId: process.env.MICROSOFT_APP_ID,
            appPassword: process.env.MICROSOFT_APP_PASSWORD
        });

        // Command ID must match what's defined in manifest
        teamChatConnector.onQuery('<%= commandId %>',
            (event: builder.IEvent,
            query: teamBuilder.ComposeExtensionQuery,
            callback: (err: Error, result: teamBuilder.IComposeExtensionResponse, statusCode: number) => void) => {
                // Check for initialRun; i.e., when you should return default results
                // if (query.parameters[0].name === 'initialRun') {}

                // Check query.queryOptions.count and query.queryOptions.skip for paging

                // Return auth response
                // let response = teamBuilder.ComposeExtensionResponse.auth().actions([
                //     builder.CardAction.openUrl(null, 'https://authUrl', 'Please sign in')
                // ]).toResponse();

                // Return config response
                // let response = teamBuilder.ComposeExtensionResponse.config().actions([
                //     builder.CardAction.openUrl(null, 'https://configUrl', 'Please sign in')
                // ]).toResponse();

                // Return result response
                let response = teamBuilder.ComposeExtensionResponse.result('list').attachments([
                    new builder.ThumbnailCard()
                        .title('Test thumbnail card')
                        .text('This is a test thumbnail card')
                        .images([new builder.CardImage().url('https://bot-framework.azureedge.net/bot-icons-v1/bot-framework-default-9.png')])
                        .toAttachment()
                ]).toResponse();
                callback(null, response, 200);
            });
        server.post('/api/composeExtension', teamChatConnector.listen());
        server.listen(process.env.PORT, () => console.log(`listening to port:` + process.env.PORT));
    }
}

const app = new App();
app.run();
```

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
