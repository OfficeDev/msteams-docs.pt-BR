---
title: Criar um menu de comandos para o seu bot
author: surbhigupta
description: Saiba como criar e manipular um menu de comando para o bot do Microsoft Teams e as práticas recomendadas. Saiba como remover comandos do manifesto.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 0e0f9ce9ada0cde0aa6f7b6b29c7badb07dd7db9
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100900"
---
# <a name="create-a-commands-menu"></a>Criar um menu de comandos

> [!NOTE]
> É recomendável que você crie um bot de comando seguindo o guia passo a passo para criar um bot de comando com [JavaScript](../../sbs-gs-commandbot.yml) usando a nova ferramenta de desenvolvimento de geração para o Teams. Para obter mais informações sobre o Kit de Ferramentas do Teams, consulte [Visão geral do Kit](../../toolkit/teams-toolkit-fundamentals.md) de Ferramentas do Teams Visual Studio Code e do Kit de Ferramentas [do Teams para Visual Studio](../../toolkit/teams-toolkit-overview-visual-studio.md).

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Para definir um conjunto de comandos principais aos quais o bot pode responder, você pode adicionar um menu de comandos com uma lista suspensa de comandos para o bot. A lista de comandos é apresentada aos usuários na área de composição de mensagem quando eles estão em conversa com o bot. Selecione um comando na lista para inserir a cadeia de caracteres de comando na caixa de mensagem de redação e selecione **Enviar**.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="conversations/Media/bot-menu-sample.png" alt-text="Bot-command-menu":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="conversations/Media/mobile-bot-menu-sample.png" alt-text="Mobile-bot-command-menu":::

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Criar um menu de comandos para o seu bot

Os menus de comando são definidos no manifesto do aplicativo. Você pode usar o **Portal do Desenvolvedor** para criar ou adicioná-los manualmente no manifesto do aplicativo.

### <a name="create-a-command-menu-for-your-bot-using-developer-portal"></a>Criar um menu de comando para o bot usando o Portal do Desenvolvedor

Um pré-requisito para criar um menu de comando para o bot é que você deve editar um manifesto de aplicativo existente. As etapas para adicionar um menu de comando são as mesmas, independentemente de você criar um novo manifesto ou editar um existente.

Para criar um menu de comando para o bot usando o Portal do Desenvolvedor:

1. Abra o Teams e selecione **Aplicativos** no painel esquerdo. Na página **Aplicativos** , pesquise **o Portal do** Desenvolvedor e selecione **Abrir**.

   :::image type="content" source="../../assets/images/tdp/add-dev-portal.png" alt-text="Captura de tela que mostra como adicionar o Portal do Desenvolvedor ao cliente do Teams.":::
  
1. No **Portal do Desenvolvedor**, selecione a **guia Aplicativos** . Se você não tiver um pacote de aplicativo existente, poderá criar ou importar um aplicativo existente. Para obter mais informações, consulte [o Portal do Desenvolvedor para Teams](../../concepts/build-and-test/teams-developer-portal.md).

1. Selecione **a guia** Aplicativos, **selecione Recursos do** aplicativo no painel esquerdo e, em seguida, **selecione Bots**.

1. Selecione **Adicionar um comando na** **seção Comandos** .

   :::image type="content" source="../../assets/images/tdp/add-a-bot-command.png" alt-text="A captura de tela mostra como adicionar um comando para o bot no Portal do Desenvolvedor.":::

1. Insira o **Comando** que aparece como o menu de comando do bot.

1. Insira a **Descrição** que aparece sob o texto do comando no menu. **A** descrição deve ser uma breve explicação da finalidade do comando.

1. Marque a **caixa de** seleção Escopo e, em seguida, **selecione Adicionar**.
   Isso define onde o menu de comando deve aparecer.

   :::image type="content" source="../../assets/images/tdp/bot-command.png" alt-text="A captura de tela mostra como adicionar um comando, uma descrição e escopos para o bot.":::

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Criar um menu de comando para o bot editando Manifest.json

Another way to create a command menu is to create it directly in the manifest file while developing your bot source code. To use this method, follow these points:

* Cada menu dá suporte a até dez comandos.
* Crie um único menu de comando que funcione em todos os escopos.
* Crie um menu de comando diferente para cada escopo.

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a>Exemplo de manifesto para menu único para ambos os escopos

O código de exemplo de manifesto para um único menu para ambos os escopos é o seguinte:

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "scopes": [
        "personal",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team",
            "personal"
          ],
          "commands":[
            {
              "title":"Help",
              "description":"Displays this help message"
            },
            {
              "title":"Search Flights",
              "description":"Search flights from Seattle to Phoenix May 2-5 departing after 3pm"
            },
            {
              "title":"Search Hotels",
              "description":"Search hotels in Portland tonight"
            },
            {
              "title":"Best Time to Fly",
              "description":"Best time to fly to London for a 5 day trip this summer"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

#### <a name="manifest-example-for-the-menu-for-each-scope"></a>Exemplo de manifesto para o menu para cada escopo

O código de exemplo de manifesto para o menu de cada escopo é o seguinte:

```json
{
  ...
  "bots":[
    {
      "botId":"<Microsoft app ID for your bot>",
      "scopes": [
        "groupChat",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for channels"
            }
          ]
        },
        {
          "scopes":[
            "groupChat"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for group chat"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

Você deve lidar com os comandos do menu em seu código bot, assim como lida com qualquer mensagem dos usuários. Você pode lidar com comandos de menu no código do bot analisando a parte **\@Menção** do texto da mensagem.

## <a name="handle-menu-commands-in-your-bot-code"></a>Lidar com comandos de menu no código do bot

Os bots em um grupo ou canal respondem somente quando são mencionados `@botname` em uma mensagem. Cada mensagem recebida por um bot quando em um escopo de grupo ou canal contém seu nome no texto da mensagem. Antes de lidar com o comando que está sendo retornado, a análise de mensagem deve lidar com a mensagem recebida por um bot com seu nome.

> [!NOTE]
> Para lidar com os comandos no código, eles são enviados ao bot como uma mensagem normal. Você deve lidar com eles como lidaria com qualquer outra mensagem de seus usuários. Os comandos no código inserem texto pré-configurado na caixa de texto. Em seguida, o usuário deve enviar esse texto da maneira como faria com qualquer outra mensagem.

# <a name="c"></a>[C#](#tab/dotnet)

Você pode analisar a parte **Menção\@** do texto da mensagem usando um método estático fornecido com o Microsoft Bot Framework. É um método da classe `Activity` chamado `RemoveRecipientMention`.

O código C# para analisar a parte **\@Menção** do texto da mensagem é o seguinte:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Você pode analisar a parte **Menção\@** do texto da mensagem usando um método estático fornecido com o Bot Framework. É um método da classe `TurnContext` chamado `removeMentionText`.

O código JavaScript para analisar a parte **\@Menção** do texto da mensagem é o seguinte:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

You can parse out the **@Mention** portion of the message text using a static method provided with the Bot Framework. It is a method of the `TurnContext` class named `remove_recipient_mention`.

O código Python para analisar a parte **\@Menção** do texto da mensagem é o seguinte:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Para habilitar o bom funcionamento do código do bot, há algumas práticas recomendadas que você deve seguir.

## <a name="command-menu-best-practices"></a>Práticas recomendadas do menu de comando

A seguir estão as práticas recomendadas do menu de comando:

* Mantenha-o simples: o menu do bot destina-se a apresentar os principais recursos do bot.
* Keep it short: Menu options must not be long and must not be complex natural language statements. They must be simple commands.
* Mantenha-o invocável: ações ou comandos do menu do bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.

> [!NOTE]
> Se você remover qualquer comando do manifesto, deverá reimplantar seu aplicativo para implementar as alterações. Em geral, todas as alterações no manifesto exigem que você reimplante seu aplicativo.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Conversas em canal e em grupo](~/bots/how-to/conversations/channel-and-group-conversations.md)
