---
title: Pesquisar com extensões de mensagens
description: Descreve como desenvolver extensões de mensagens baseadas em pesquisa
keywords: Pesquisa de extensões de mensagens de mensagens do teams
ms.topic: how-to
ms.date: 07/20/2019
ms.openlocfilehash: 7a4074fe4f3a15621729f4c549d31dc90d98e714
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696099"
---
# <a name="search-with-messaging-extensions"></a>Pesquisar com extensões de mensagens

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Extensões de mensagens baseadas em pesquisa permitem que você consulte seu serviço e poste essas informações na forma de um cartão, direto em sua mensagem

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As seções a seguir descrevem como fazer isso.

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a>Extensões de mensagem de tipo de pesquisa

Para a extensão de mensagens baseada em pesquisa, de `type` definir o parâmetro como `query` . Veja a seguir um exemplo de um manifesto com um único comando de pesquisa. Uma única extensão de mensagens pode ter até 10 comandos diferentes associados a ela. Isso pode incluir vários comandos baseados em ação e pesquisa.

#### <a name="complete-app-manifest-example"></a>Exemplo de manifesto completo do aplicativo

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

### <a name="test-via-uploading"></a>Testar por meio do carregamento

Você pode testar sua extensão de mensagens carregando seu aplicativo.

Para abrir sua extensão de mensagens, navegue até qualquer um dos seus chats ou canais. Escolha o **botão Mais opções** (**&#8943;**) na caixa de redação e escolha sua extensão de mensagens.

## <a name="add-event-handlers"></a>Adicionar manipuladores de eventos

A maior parte do seu trabalho envolve o evento, que lida com todas as interações na janela de extensão `onQuery` de mensagens.

Se você definir `canUpdateConfiguration` como `true` no manifesto, habilita o item de menu **Configurações** para sua extensão de mensagens e também deve manipular `onQuerySettingsUrl` e `onSettingsUpdate` .

### <a name="handle-onquery-events"></a>Manipular eventos onQuery

Uma extensão de mensagens recebe um evento quando algo acontece na janela de extensão de mensagens ou `onQuery` é enviado para a janela.

Se sua extensão de mensagens usa uma página de configuração, seu manipulador deve primeiro verificar se há informações de configuração armazenadas; se a extensão de mensagens não estiver configurada, retorne uma resposta com um link para sua página de `onQuery` `config` configuração. Esteja ciente de que a resposta da página de configuração também é manipulada por `onQuery` . (A única exceção é quando a página de configuração é chamada pelo manipulador para `onQuerySettingsUrl` ; consulte a seção a seguir.)

Se sua extensão de mensagens exigir autenticação, verifique as informações de estado do usuário; se o usuário não estiver assinado, siga as instruções na seção [Autenticação](#authentication) posteriormente neste tópico.

Em seguida, verifique se está definido; em caso afirmativa, tome as medidas apropriadas, como fornecer instruções `initialRun` ou uma lista de respostas.

O restante do manipulador solicita informações ao usuário, exibe uma lista de cartões de visualização e retorna `onQuery` o cartão selecionado pelo usuário.

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Manipular eventos onQuerySettingsUrl e onSettingsUpdate

Os `onQuerySettingsUrl` eventos e funcionam juntos para `onSettingsUpdate` habilitar o item de menu **Configurações.**

![Capturas de tela de locais do item de menu Configurações](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

Seu manipulador para retorna a URL da página de configuração; depois que a página de configuração é fechado, o manipulador aceita e `onQuerySettingsUrl` `onSettingsUpdate` salva o estado retornado. (Este é o único caso no qual `onQuery` *não recebe* a resposta da página de configuração.)

## <a name="receive-and-respond-to-queries"></a>Receber e responder a consultas

Todas as solicitações para sua extensão de mensagens são feitas por meio de um `Activity` objeto postado em sua URL de retorno de chamada. A solicitação contém informações sobre o comando do usuário, como ID e valores de parâmetro. A solicitação também fornece metadados sobre o contexto no qual sua extensão foi invocada, incluindo iD de usuário e locatário, juntamente com ID de chat ou canal e IDs de equipe.

### <a name="receive-user-requests"></a>Receber solicitações de usuário

Quando um usuário executa uma consulta, o Microsoft Teams envia ao seu serviço um objeto Da Estrutura de `Activity` Bot padrão. Seu serviço deve executar sua lógica para um que tenha definido como e definido como um tipo com suporte, conforme `Activity` mostrado na tabela a `type` `invoke` `name` `composeExtension` seguir.

Além das propriedades de atividade de bot padrão, a carga contém os seguintes metadados de solicitação:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação; deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Atualmente, os seguintes tipos são suportados: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| ID do objeto do Azure Active Directory do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`clientInfo`|Metadados opcionais sobre o software cliente usado para enviar a mensagem de um usuário. A entidade pode conter duas propriedades:<br>O `country` campo contém o local detectado pelo usuário.<br>O `platform` campo descreve a plataforma de cliente de mensagens. <br>Para obter informações adicionais, *consulte* Tipos de entidade [não IRI — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Os parâmetros de solicitação em si são encontrados no objeto value, que inclui as seguintes propriedades:

| Nome da propriedade | Objetivo |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros. Cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros paginação: <br>`skip`: ignorar a contagem dessa consulta <br>`count`: número de elementos a retornar |

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

Como alternativa (ou além disso) à pesquisa do seu serviço externo, você pode usar uma URL inserida na caixa de mensagem de redação para consultar seu serviço e retornar um cartão. Na captura de tela abaixo, um usuário firmou uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens resolveu em um cartão.

![Exemplo de desfraldamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Para permitir que sua extensão de mensagens interaja com links dessa forma, primeiro você precisará adicionar a matriz ao manifesto do aplicativo, como `messageHandlers` no exemplo abaixo:

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

Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você [](#respond-to-user-requests) precisará alterar seu código bot para responder à solicitação de invocação abaixo.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Se seu aplicativo retornar vários itens, apenas o primeiro será usado.

### <a name="respond-to-user-requests"></a>Responder a solicitações de usuário

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço. Nesse ponto, seu código tem 5 segundos para fornecer uma resposta HTTP à solicitação. Durante esse tempo, seu serviço pode realizar uma consulta adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados correspondentes à consulta do usuário. A resposta deve indicar um código de status HTTP e um `200 OK` objeto application/json válido com o seguinte corpo:

|Nome da propriedade|Objetivo|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Os seguintes tipos são suportados: <br>`result`: exibe uma lista de resultados da pesquisa <br>`auth`: pede ao usuário para autenticar <br>`config`: pede ao usuário para configurar a extensão de mensagens <br>`message`: exibe uma mensagem de texto simples |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`list`: uma lista de objetos de cartão que contêm campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos de anexo válidos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas de tipo `auth` ou `config` . |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message` . |

#### <a name="response-card-types-and-previews"></a>Tipos de cartão de resposta e visualizações

Suportamos os seguintes tipos de anexo:

* [Cartão de miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão de herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Consulte [Cartões para](~/task-modules-and-cards/what-are-cards.md) uma visão geral.

Para saber como usar os tipos de miniatura e cartão de herói, consulte [Adicionar cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)

Para obter documentação adicional sobre o cartão conector do Office 365, consulte [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item. A visualização é gerada de duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um cartão Hero ou Thumbnail.
* Extraído das propriedades `title` básicas `text` , e do `image` anexo. Eles são usados somente se `preview` a propriedade não estiver definida e essas propriedades estarão disponíveis.

Você pode exibir uma visualização de um cartão Adaptável ou conector do Office 365 na lista de resultados simplesmente definindo sua propriedade de visualização; isso não será necessário se os resultados já são cartões de miniatura ou herói. Se você usar o anexo de visualização, ele deve ser um cartão Hero ou Thumbnail. Se nenhuma propriedade de visualização for especificada, a visualização do cartão falhará e nada será exibido.

#### <a name="response-example"></a>Exemplo de resposta

Este exemplo mostra uma resposta com dois resultados, misturando diferentes formatos de cartão: Office 365 Connector e Adaptável. Embora você provavelmente queira manter um formato de cartão em sua resposta, ele mostra como a propriedade de cada elemento na coleção deve definir explicitamente uma visualização no formato hero ou miniatura, conforme descrito `preview` `attachments` acima.

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

Se você definir como no manifesto, o Microsoft Teams emite uma consulta "padrão" quando o usuário abre pela primeira vez a extensão `initialRun` `true` de mensagens. Seu serviço pode responder a essa consulta com um conjunto de resultados pré-populados. Isso pode ser útil para exibir, por exemplo, itens exibidos recentemente, favoritos ou qualquer outra informação que não dependa da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, exceto com um parâmetro cujo valor `initialRun` de cadeia de caracteres é `true` .

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

## <a name="identify-the-user"></a>Identificar o usuário

Todas as solicitações aos seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID do objeto do Azure Active Directory.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Os `id` valores e são `aadObjectId` garantidos como os do usuário do Teams autenticado. Elas podem ser usadas como chaves para procurar credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário. Se aplicável, a solicitação também contém as IDs de equipe e canal das quais a solicitação se originou.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes que ele possa usar a extensão de mensagens. Se você tiver escrito um bot ou uma guia que assina no usuário, esta seção deve ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
2. Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID do usuário do Teams.
3. Se o usuário não tiver sido autenticado, envie uma `auth` resposta com uma ação `openUrl` sugerida, incluindo a URL de autenticação.
4. O cliente do Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.
5. Depois que o usuário entrar, feche a janela e envie um "código de autenticação" para o cliente do Teams.
6. Em seguida, o cliente do Teams reenvia a consulta ao seu serviço, que inclui o código de autenticação passado na etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente fazer a spoof ou comprometer o fluxo de login. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responder com uma ação de login

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo que inclui a `openUrl` URL de autenticação.

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
> Para que a experiência de login seja hospedada em um pop-up do Teams, a parte de domínio da URL deve estar na lista de domínios válidos do aplicativo. (Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de login

Sua experiência de login deve ser responsiva e adequada dentro de uma janela pop-up. Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams,](/javascript/api/overview/msteams-client)que usa a passagem de mensagens.

Assim como com outras experiências incorporadas em execução no Microsoft Teams, seu código dentro da janela precisa chamar primeiro `microsoftTeams.initialize()` . Se seu código executar um fluxo OAuth, você poderá passar a ID do usuário do Teams para sua janela, que poderá passá-lo para a URL de entrada do OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de login

Quando a solicitação de login for concluída e redirecionar para sua página, ela deverá executar as seguintes etapas:

1. Gere um código de segurança. (Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon (como tokens OAuth 2.0).
2. Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela fecha e o controle é passado para o cliente do Teams. O cliente agora pode reeditar a consulta de usuário original, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação reemissão

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

Para receber e manipular consultas com o SDK do Construtor de Bots para .NET, você pode verificar o tipo de ação na atividade de entrada e usar o método auxiliar no pacote `invoke` NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) para determinar se é uma atividade de extensão de mensagens.

#### <a name="example-code-in-net"></a>Exemplo de código no .NET

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

#### <a name="example-code-in-nodejs"></a>Exemplo de código no Node.js

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
*Consulte também Exemplos* [da Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
