---
title: Pesquisar com extensões de mensagens
description: Descreve como desenvolver extensões de mensagens baseadas na pesquisa
keywords: pesquisa de extensões de mensagens de extensões de mensagens do teams
ms.date: 07/20/2019
ms.openlocfilehash: b791e7cc8f9a311d0610573f2fa3659578c29c7d
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "44801039"
---
# <a name="search-with-messaging-extensions"></a>Pesquisar com extensões de mensagens

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagens baseadas em pesquisa permitem consultar seu serviço e postar essas informações na forma de um cartão, diretamente na sua mensagem

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As seções a seguir descrevem como fazer isso.

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a>Extensões de mensagens de tipo de pesquisa

Para a extensão de mensagens com base na pesquisa, defina o `type` parâmetro como `query` . Veja a seguir um exemplo de um manifesto com um único comando de pesquisa. Uma única extensão de mensagens pode ter até 10 comandos diferentes associados a ela. Isso pode incluir vários comandos de pesquisa e múltiplos baseados em ação.

#### <a name="complete-app-manifest-example"></a>Exemplo de manifesto de aplicativo completo

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

### <a name="test-via-uploading"></a>Testar via carregamento

Você pode testar sua extensão de mensagens carregando seu aplicativo.

Para abrir sua extensão de mensagens, navegue até qualquer um dos seus chats ou canais. Escolha o botão **mais opções** (**&#8943;**) na caixa redigir e escolha sua extensão de mensagens.

## <a name="add-event-handlers"></a>Adicionar manipuladores de eventos

A maior parte do seu trabalho envolve o `onQuery` evento, que lida com todas as interações na janela de extensão de mensagens.

Se você definir `canUpdateConfiguration` `true` no manifesto, habilite o item de menu **configurações** para sua extensão de mensagens e também deve lidar `onQuerySettingsUrl` e `onSettingsUpdate` .

### <a name="handle-onquery-events"></a>Manipular eventos onquery

Uma extensão de mensagens recebe um `onQuery` evento quando algo acontece na janela de extensão de mensagens ou é enviado para a janela.

Se sua extensão de mensagens usa uma página de configuração, seu manipulador para `onQuery` deve primeiro verificar qualquer informação de configuração armazenada; se a extensão de mensagens não estiver configurada, retorne uma `config` resposta com um link para sua página de configuração. Lembre-se de que a resposta da página de configuração também é manipulada pelo `onQuery` . (A única exceção é quando a página de configuração é chamada pelo manipulador de `onQuerySettingsUrl` ; consulte a seção a seguir.

Se sua extensão de mensagens requer autenticação, verifique as informações de estado do usuário; Se o usuário não estiver conectado, siga as instruções na seção [autenticação](#authentication) mais adiante neste tópico.

Em seguida, verifique se `initialRun` o está definido; em caso afirmativo, execute a ação apropriada, como fornecer instruções ou uma lista de respostas.

O restante do manipulador para `onQuery` solicitar informações ao usuário, exibe uma lista de cartões de visualização e retorna o cartão selecionado pelo usuário.

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Manipular eventos onQuerySettingsUrl e onSettingsUpdate

O `onQuerySettingsUrl` e os `onSettingsUpdate` eventos trabalham em conjunto para habilitar o item de menu **configurações** .

![Capturas de tela de locais do item de menu configurações](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

O manipulador de `onQuerySettingsUrl` retorno da URL para a página de configuração; após o fechamento da página de configuração, o manipulador para `onSettingsUpdate` aceitar e salvar o estado retornado. (Este é o único caso no qual `onQuery` *não* recebe a resposta da página de configuração.)

## <a name="receive-and-respond-to-queries"></a>Receber e responder a consultas

Cada solicitação para sua extensão de mensagens é feita por meio de um `Activity` objeto que é publicado na sua URL de retorno de chamada. A solicitação contém informações sobre o comando de usuário, como valores de ID e de parâmetro. A solicitação também fornece metadados sobre o contexto no qual sua extensão foi invocada, incluindo o ID de usuário e de locatário, junto com a ID de chat ou as identificações de canal e equipe.

### <a name="receive-user-requests"></a>Receber solicitações de usuário

Quando um usuário realiza uma consulta, o Microsoft Teams envia o serviço de um objeto da estrutura de bot padrão `Activity` . Seu serviço deve executar sua lógica para um `Activity` que tenha `type` definido como `invoke` e `name` definido como um tipo com suporte `composeExtension` , conforme mostrado na tabela a seguir.

Além das propriedades de atividade de bot padrão, a carga contém os seguintes metadados de solicitação:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação; deve ser `invoke` . |
|`name`| Tipo de comando que é emitido para o serviço. Atualmente, há suporte para os seguintes tipos: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| ID de objeto do Azure Active Directory do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação tiver sido feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação tiver sido feita em um canal). |
|`clientInfo`|Metadados opcionais sobre o software cliente usado para enviar a mensagem de um usuário. A entidade pode conter duas propriedades:<br>O `country` campo contém o local detectado do usuário.<br>O `platform` campo descreve a plataforma do cliente de mensagens. <br>Para obter informações adicionais, *Confira* [tipos de entidade não IRI — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Os próprios parâmetros de solicitação são encontrados no objeto value, que inclui as seguintes propriedades:

| Nome da propriedade | Finalidade |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros. Cada objeto Parameter contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
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

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Receber solicitações de links inseridos na caixa de mensagem de composição

Como alternativa (ou adicional) para pesquisar seu serviço externo, você pode usar uma URL inserida na caixa de mensagem de composição para consultar seu serviço e retornar um cartão. Na captura de tela abaixo de um usuário colou em uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.

![Exemplo de link Unfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Para habilitar sua extensão de mensagens para interagir com os links dessa forma, primeiro você precisará adicionar a `messageHandlers` matriz ao manifesto do aplicativo, como no exemplo abaixo:

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

Após adicionar o domínio para ouvir o manifesto do aplicativo, você precisará alterar o código do bot para [responder](#respond-to-user-requests) à solicitação de invocação abaixo.

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

### <a name="respond-to-user-requests"></a>Responder às solicitações do usuário

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para o serviço. Nesse ponto, o código tem cinco segundos para fornecer uma resposta HTTP para a solicitação. Durante esse tempo, o serviço pode executar pesquisa adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados que correspondem à consulta do usuário. A resposta deve indicar um código de status HTTP `200 OK` e um objeto Application/JSON válido com o seguinte corpo:

|Nome da propriedade|Finalidade|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Há suporte para os seguintes tipos: <br>`result`: exibe uma lista de resultados de pesquisa <br>`auth`: solicita que o usuário autentique <br>`config`: solicita que o usuário configure a extensão de mensagens <br>`message`: exibe uma mensagem de texto sem formatação |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result` . <br>Atualmente, há suporte para os seguintes tipos: <br>`list`: uma lista de objetos Card contendo campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos Attachment válidos. Usado para respostas do tipo `result` . <br>Atualmente, há suporte para os seguintes tipos: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas do tipo `auth` ou `config` . |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message` . |

#### <a name="response-card-types-and-previews"></a>Tipos e visualizações de cartões de resposta

Oferecemos suporte para os seguintes tipos de anexo:

* [Cartão de miniaturas](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão de conexão do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Consulte [cartões](~/task-modules-and-cards/what-are-cards.md) para obter uma visão geral.

Para saber como usar os tipos de cartão de miniatura e herói, confira [Adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

Para obter documentação adicional sobre a placa de conector do Office 365, consulte [usando cartões de conector do office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item. A visualização é gerada de duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um herói ou cartão de miniatura.
* Extraído do básico `title` , `text` e das `image` Propriedades do anexo. Eles são usados apenas se a `preview` propriedade não estiver definida e essas propriedades estiverem disponíveis.

Você pode exibir uma visualização de um cartão de conexão adaptável ou do Office 365 na lista de resultados, simplesmente definindo sua propriedade Preview; Isso não é necessário se os resultados já são herói ou cartões em miniatura. Se você usar o anexo de visualização, ele deve ser um herói ou cartão de miniatura. Se nenhuma propriedade Preview for especificada, a visualização do cartão falhará e nada será exibido.

#### <a name="response-example"></a>Exemplo de resposta

Este exemplo mostra uma resposta com dois resultados, combinando formatos de cartão diferentes: conector e adaptável do Office 365. Embora você provavelmente queira usar um formato de cartão em sua resposta, ele mostra como a `preview` propriedade de cada elemento da `attachments` coleção deve definir explicitamente uma visualização no formato herói ou miniatura, conforme descrito acima.

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
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
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

Se você definir `initialRun` para `true` no manifesto, o Microsoft Teams emitirá uma consulta "padrão" quando o usuário abrir pela primeira vez a extensão de mensagens. O serviço pode responder a essa consulta com um conjunto de resultados previamente preenchidos. Isso pode ser útil para exibir, por exemplo, itens exibidos recentemente, favoritos ou qualquer outra informação que não seja dependente da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, exceto com um parâmetro `initialRun` cujo valor de cadeia de caracteres é `true` .

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

Todas as solicitações para seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID de objeto do Azure Active Directory.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Os `id` `aadObjectId` valores e são garantidos do usuário do Microsoft Teams. Eles podem ser usados como chaves para procurar credenciais ou qualquer estado em cache em seu serviço. Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário. Se aplicável, a solicitação também contém as IDs de canal e equipe das quais a solicitação foi originada.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes de poder usar a extensão de mensagens. Se você escreveu um bot ou uma guia que entra no usuário, esta seção deve ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
2. Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID de usuário do teams.
3. Se o usuário não tiver sido autenticado, envie uma `auth` resposta com uma `openUrl` ação sugerida, incluindo a URL de autenticação.
4. O cliente do Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.
5. Após o usuário entrar, você deve fechar sua janela e enviar um "código de autenticação" para o cliente do teams.
6. Em seguida, o cliente do teams emite novamente a consulta para o serviço, o que inclui o código de autenticação passado na etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de entrada. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responder com uma ação de entrada

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo `openUrl` que inclui a URL de autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de logon

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
> Para que a experiência de entrada seja hospedada em um pop-up de equipes, a parte de domínio da URL deve estar na lista de domínios válidos de seu aplicativo. (Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de entrada

Sua experiência de entrada deve ser responsiva e ajustada em uma janela pop-up. Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client), que usa a transmissão de mensagens.

Assim como ocorre com outras experiências incorporadas no Microsoft Teams, seu código dentro da janela precisa primeiro chamar `microsoftTeams.initialize()` . Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do teams para sua janela, o que pode passá-la para a URL de entrada OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de entrada

Quando a solicitação de entrada é concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:

1. Gere um código de segurança. (Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, junto com as credenciais obtidas por meio do fluxo de entrada (como tokens OAuth 2,0).
2. Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela é fechada e o controle é passado para o cliente Teams. Agora, o cliente pode reemitir a consulta de usuário original, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para pesquisar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.

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

## <a name="sdk-support"></a>Suporte a SDK

### <a name="net"></a>.NET

Para receber e lidar com consultas com o SDK do bot Builder para .NET, você pode verificar o `invoke` tipo de ação na atividade de entrada e, em seguida, usar o método auxiliar no pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) para determinar se é uma atividade de extensão de mensagens.

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
*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
