---
title: Pesquisa com extensões de mensagens
description: Descreve como desenvolver extensões de mensagens baseadas em pesquisa
keywords: equipes de extensões de mensagens de extensões de mensagens pesquisa
ms.topic: how-to
localization_priority: Normal
ms.date: 07/20/2019
ms.openlocfilehash: 515472838ff2ad35ef5dd295043ec27c53edb4f1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566724"
---
# <a name="search-with-messaging-extensions"></a>Pesquisa com extensões de mensagens

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagens baseadas em pesquisa permitem que você consulte seu serviço e poste essas informações na forma de um cartão, apenas na sua mensagem.

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As seguintes seções descrevem como fazer isso:

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a>Extensões de mensagem tipo de pesquisa

Para extensão de mensagens baseada em pesquisa, defina o `type` parâmetro para `query` . Abaixo está um exemplo de um manifesto com um único comando de pesquisa. Uma única extensão de mensagens pode ter até 10 comandos diferentes associados a ela. Isso pode incluir vários comandos baseados em pesquisa e vários comandos baseados em ação.

#### <a name="complete-app-manifest-example"></a>Exemplo completo de manifesto de aplicativo

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

### <a name="test-via-uploading"></a>Teste via upload

Você pode testar sua extensão de mensagens carregando seu aplicativo.

Para abrir sua extensão de mensagens, navegue até qualquer um de seus chats ou canais. Escolha o botão **Mais opções** (**&#8943;)** na caixa de composição e escolha sua extensão de mensagens.

## <a name="add-event-handlers"></a>Adicionar manipuladores de eventos

A maior parte do seu trabalho envolve o `onQuery` evento, que lida com todas as interações na janela de extensão de mensagens.

Se você definir `canUpdateConfiguration` no `true` manifesto, você habilita o item **Configurações** menu para sua extensão de mensagens e também deve manusear `onQuerySettingsUrl` e `onSettingsUpdate` .

### <a name="handle-onquery-events"></a>Lidar com eventos deQuery

Uma extensão de mensagens recebe um `onQuery` evento quando algo acontece na janela de extensão de mensagens ou é enviado para a janela.

Se sua extensão de mensagens usar uma página de configuração, o manipulador `onQuery` deve primeiro verificar se há informações de configuração armazenadas; se a extensão de mensagens não estiver configurada, retorne uma resposta com um link para sua página de `config` configuração. Esteja ciente de que a resposta da página de configuração também é tratada por `onQuery` . A única exceção é quando a página de configuração é chamada pelo manipulador `onQuerySettingsUrl` para; veja a seguinte seção:

Se sua extensão de mensagem exigir autenticação, verifique as informações do estado do usuário; se o usuário não estiver loto, siga as instruções na seção [Autenticação](#authentication) mais tarde neste tópico.

Em seguida, verifique se `initialRun` está definido; se sim, tome as medidas apropriadas, como fornecer instruções ou uma lista de respostas.

O restante do seu manipulador solicita `onQuery` informações ao usuário, exibe uma lista de cartões de visualização e devolve o cartão selecionado pelo usuário.

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Lidar com eventos de OnQuerySettingsUrl e onSettingsUpdate

Os `onQuerySettingsUrl` `onSettingsUpdate` eventos trabalham juntos para habilitar o item do menu **Configurações.**

![Capturas de tela de locais do item do menu Configurações](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

O manipulador para `onQuerySettingsUrl` devolver a URL para a página de configuração; após o fechamento da página de configuração, o manipulador para aceitar e salvar o estado `onSettingsUpdate` retornado. Este é o único caso em que `onQuery` *não* recebe a resposta da página de configuração.

## <a name="receive-and-respond-to-queries"></a>Receba e responda às consultas

Cada solicitação para sua extensão de mensagens é feita através de um `Activity` objeto que é postado na url de retorno de chamada. A solicitação contém informações sobre o comando do usuário, como ID e valores de parâmetros. A solicitação também fornece metadados sobre o contexto em que sua extensão foi invocada, incluindo identificação do usuário e inquilino, juntamente com iD de chat ou canal e IDs da equipe.

### <a name="receive-user-requests"></a>Receba solicitações do usuário

Quando um usuário realiza uma consulta, Microsoft Teams envia ao seu serviço um objeto padrão do Bot `Activity` Framework. Seu serviço deve executar sua lógica para um `Activity` que tenha definido e definido para um tipo `type` `invoke` `name` `composeExtension` suportado, como mostrado na tabela a seguir.

Além das propriedades de atividade padrão do bot, a carga contém os seguintes metadados de solicitação:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação; deve `invoke` ser. |
|`name`| Tipo de comando que é emitido para o seu serviço. Atualmente, os seguintes tipos são suportados: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory o usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`clientInfo`|Metadados opcionais sobre o software cliente usado para enviar a mensagem de um usuário. A entidade pode conter duas propriedades:<br>O `country` campo contém a localização detectada pelo usuário.<br>O `platform` campo descreve a plataforma de clientes de mensagens. <br>Para obter informações adicionais, *consulte* [os tipos de entidades não-IRI — clienteInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Os parâmetros de solicitação em si são encontrados no objeto de valor, que inclui as seguintes propriedades:

| Nome da propriedade | Objetivo |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros: Cada objeto parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros de paginação: <br>`skip`: pular a contagem para esta consulta <br>`count`: número de elementos para retornar |

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

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Receba solicitações de links inseridos na caixa de mensagens de composição

Como alternativa (ou além disso) para pesquisar seu serviço externo, você pode usar uma URL inserida na caixa de mensagens de composição para consultar seu serviço e retornar um cartão. Na captura de tela abaixo, um usuário colou em uma URL para um item de trabalho em Azure DevOps que a extensão de mensagens resolveu em um cartão.

![Exemplo de desenrolar de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Para permitir que sua extensão de mensagens interaja com links desta maneira, você primeiro precisará adicionar o `messageHandlers` array ao seu manifesto de aplicativo, como no exemplo abaixo:

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

Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você precisará alterar seu código de bot para [responder](#respond-to-user-requests) à solicitação abaixo de invocação.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Se o aplicativo devolver vários itens, apenas o primeiro será usado.

### <a name="respond-to-user-requests"></a>Responder às solicitações do usuário

Quando o usuário realiza uma consulta, Microsoft Teams emite uma solicitação HTTP síncron sua para o seu serviço. Nesse ponto, seu código tem 5 segundos para fornecer uma resposta HTTP à solicitação. Durante esse tempo, seu serviço pode realizar pesquisa adicional ou qualquer outra lógica de negócio necessária para atender à solicitação.

Seu serviço deve responder com os resultados que correspondem à consulta do usuário. A resposta deve indicar um código de status HTTP `200 OK` e um objeto de aplicativo/json válido com o seguinte corpo:

|Nome da propriedade|Objetivo|
|---|---|
|`composeExtension`|Envelope de resposta de alto nível.|
|`composeExtension.type`|Tipo de resposta. Os seguintes tipos são suportados: <br>`result`: exibe uma lista de resultados de pesquisa <br>`auth`: o usuário se autentica <br>`config`: pede ao usuário para configurar a extensão de mensagens <br>`message`: exibe uma mensagem de texto simples |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`list`: uma lista de objetos de cartão contendo miniaturas, títulos e campos de texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos de fixação válidos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas de tipo `auth` ou `config` . |
|`composeExtension.text`|Mensagem para exibir. Usado para respostas do tipo `message` . |

#### <a name="response-card-types-and-previews"></a>Tipos e pré-visualizações de cartões de resposta

Apoiamos os seguintes tipos de anexo:

* [Cartão de miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão de herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Placa conectora](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptativo](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para obter mais informações, consulte [Cartões](~/task-modules-and-cards/what-are-cards.md) para obter uma visão geral.

Para aprender a usar os tipos de miniatura e cartão de herói, consulte [Adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

Para obter documentação adicional sobre a placa Office 365 Conector, consulte [Usando Office 365 cartões Connector](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface do Microsoft Teams UI com uma visualização de cada item. A visualização é gerada de duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` acessório só pode ser um cartão Herói ou Miniatura.
* Extraído do `title` `text` básico, e `image` propriedades do acessório. Estes são usados apenas se a `preview` propriedade não estiver definida e essas propriedades estiverem disponíveis.

Você pode exibir uma visualização de uma placa Conector Adaptável ou Office 365 na lista de resultados simplesmente definindo sua propriedade de visualização; isso não é necessário se os resultados já são cartões de herói ou miniatura. Se você usar o anexo de pré-visualização, ele deve ser um cartão Hero ou Miniatura. Se nenhuma propriedade de visualização for especificada, a visualização do cartão falhará e nada será exibido.

#### <a name="response-example"></a>Exemplo de resposta

Este exemplo mostra uma resposta com dois resultados, misturando diferentes formatos de cartão: Office 365 Conector e Adaptive. Embora você provavelmente queira ficar com um formato de cartão em sua resposta, ele mostra como a `preview` propriedade de cada elemento na coleção deve definir explicitamente uma `attachments` visualização em formato de herói ou miniatura como descrito acima.

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

Se você definir `initialRun` no `true` manifesto, Microsoft Teams emitir uma consulta "padrão" quando o usuário abrir a extensão de mensagens pela primeira vez. Seu serviço pode responder a esta consulta com um conjunto de resultados pré-adulterados. Isso pode ser útil para exibir, por exemplo, itens, favoritos ou qualquer outra informação que não dependa da entrada do usuário.

A consulta padrão tem a mesma estrutura de qualquer consulta regular do usuário, exceto com um parâmetro `initialRun` cujo valor de sequência é `true` .

#### <a name="request-example-for-a-default-query"></a>Solicitar exemplo para uma consulta padrão

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

Cada solicitação aos seus serviços inclui o ID ofuscado do usuário que realizou a solicitação, bem como o nome de exibição do usuário e Azure Active Directory ID do objeto.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

O `id` valor e os `aadObjectId` valores são garantidos como sendo do Teams usuário autenticado. Eles podem ser usados como chaves para procurar credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém o Azure Active Directory ID de inquilino do usuário, que pode ser usado para identificar a organização do usuário. Se aplicável, a solicitação também contém a equipe e os IDs do canal dos quais a solicitação teve origem.

## <a name="authentication"></a>Autenticação

Se o seu serviço exigir a autenticação do usuário, você precisa fazer login no usuário antes que ele possa usar a extensão de mensagens. Se você escreveu um bot ou uma guia que assina no usuário, esta seção deve ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
2. Seu serviço verifica se o usuário primeiro foi autenticado inspecionando o Teams ID do usuário.
3. Se o usuário não tiver autenticado, envie de volta uma `auth` resposta com uma `openUrl` ação sugerida, incluindo a URL de autenticação.
4. O cliente Microsoft Teams lança uma janela pop-up hospedando sua página da Web usando a URL de autenticação dada.
5. Depois que o usuário entrar, você deve fechar sua janela e enviar um "código de autenticação" para o cliente Teams.
6. O cliente Teams reedita então a consulta ao seu serviço, que inclui o código de autenticação aprovado na etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de login. Isso efetivamente "fecha o loop" para terminar a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responda com uma ação de login

Para solicitar que um usuário não autenticado faça login, responda com uma ação sugerida do tipo que inclui a URL de `openUrl` autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de login

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
> Para que a experiência de login seja hospedada em um pop-up Teams, a parte de domínio da URL deve estar na lista de domínios válidos do seu aplicativo. Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema manifesto.

### <a name="start-the-sign-in-flow"></a>Inicie o fluxo de login

Sua experiência de login deve ser responsiva e caber dentro de uma janela pop-up. Ele deve se integrar com o [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client), que usa passagem de mensagem.

Como acontece com outras experiências incorporadas que correm dentro Microsoft Teams, seu código dentro da janela precisa primeiro chamar `microsoftTeams.initialize()` . Se o seu código realizar um fluxo OAuth, você pode passar o Teams ID do usuário para a sua janela, que então pode passá-lo para a URL de login do OAuth.

### <a name="complete-the-sign-in-flow"></a>Complete o fluxo de login

Quando a solicitação de login for concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:

1. Gere um código de segurança. (Este pode ser um número aleatório.) Você precisa armazenar esse código em seu serviço, juntamente com as credenciais obtidas através do fluxo de login, tais como, tokens OAuth 2.0.
2. Ligue `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela fecha e o controle é passado para o Teams cliente. O cliente agora pode reeditar a consulta original do usuário, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para completar a sequência de autenticação e, em seguida, completar a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação reeditada

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

Para receber e lidar com consultas com o Bot Builder SDK para .NET, você pode verificar o `invoke` tipo de ação na atividade recebida e, em seguida, usar o método de ajuda no pacote de NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) para determinar se é uma atividade de extensão de mensagens.

#### <a name="example-code-in-net"></a>Código de exemplo em .NET

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

#### <a name="example-code-in-nodejs"></a>Código de exemplo em Node.js

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
