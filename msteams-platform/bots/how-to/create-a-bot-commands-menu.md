---
title: Criar um menu de comandos para o seu bot
author: surbhigupta
description: Saiba como criar um menu de comando para seu bot do Microsoft Teams com exemplos de código.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
keywords: menu de comando redigir mensagem conversa @menção
ms.openlocfilehash: 5b96a9b995806678596cc8cedd45f4bb6e80827c
ms.sourcegitcommit: 6f1bd36b1071e256bdc14e6ccb31dfdda9ca6d6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66048987"
---
# <a name="bot-command-menus"></a>Menus de comando do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Para definir um conjunto de comandos principais aos quais o bot pode responder, você pode adicionar um menu de comandos com uma lista suspensa de comandos para o bot. A lista de comandos é apresentada aos usuários na área de composição de mensagem quando eles estão em conversa com o bot. Selecione um comando na lista para inserir a cadeia de caracteres de comando na caixa de mensagem de redação e selecione **Enviar**.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="conversations/Media/bot-menu-sample.png" alt-text="Bot-command-menu":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="conversations/Media/mobile-bot-menu-sample.png" alt-text="Mobile-bot-command-menu":::

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Criar um menu de comandos para o seu bot

Os menus de comando são definidos no manifesto do aplicativo. Você pode usar o **App Studio** para criá-los ou adicioná-los manualmente no manifesto do aplicativo.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Criar um menu de comando para o bot usando o App Studio

Um pré-requisito para criar um menu de comando para o bot é que você deve editar um manifesto de aplicativo existente. As etapas para adicionar um menu de comando são as mesmas, independentemente de você criar um novo manifesto ou editar um existente.

**Para criar um menu de comando para o bot usando o App Studio**

1. Abra o Teams e selecione **Aplicativos** no painel esquerdo. Na página **Aplicativos**, busque o **App Studio** e selecione **Abrir**.

   > [!WARNING]
   > Se estiver usando o App Studio, recomendamos que tente o Portal do Desenvolvedor para configurar, distribuir e gerenciar seus aplicativos do Teams. O App Studio será preterido até 30 de junho de 2022

   :::image type="content" source="conversations/Media/AppStudio.png" alt-text="appstudio-media":::

2. No **App Studio**, selecione a guia **Editor de manifesto**. Se você não tiver um pacote de aplicativo existente, poderá criar ou importar um aplicativo existente. Para obter mais informações, consulte [atualizar o pacote do aplicativo C# no App Studio](../../get-started/deploy-csharp-app-studio.md)

3. No painel esquerdo do **Editor de manifesto** e na seção **Recursos**, selecione **Bots**.

4. No painel direito do **Editor de manifesto** e na seção **Comandos**, selecione **Adicionar**. A tela **Novo Comando** é exibida.

   :::image type="content" source="media/AppStudio-CommandMenu-Add.png" alt-text="Selecione o pacote de aplicativo" lightbox="media/AppStudio-CommandMenu-Add.png "border="true":::

5. Insira o **Texto do comando** que deve aparecer como o menu de comando do bot.

6. Insira o **Texto da ajuda** que deve aparecer sob o texto do comando no menu. O **Texto da ajuda** deve ser uma breve explicação da finalidade do comando.

7. Marque as caixas de seleção **Escopo** para selecionar onde esse menu de comando deve aparecer e selecione **Salvar**.

   :::image type="content" source="media/AppStudio-NewCommandMenu.png" alt-text="Botão de menu novos comandos do App Studio "lightbox="media/AppStudio-NewCommandMenu.png "border="true":::


### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Criar um menu de comando para o bot editando Manifest.json

Outra maneira de criar um menu de comando é criá-lo diretamente no arquivo de manifesto ao desenvolver o código-fonte do bot. Para usar esse método, siga estes pontos:

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

Você pode analisar a parte **@Menção** parte do texto da mensagem usando um método estático fornecido com o Bot Framework. É um método da classe `TurnContext` chamado `remove_recipient_mention`.

O código Python para analisar a parte **\@Menção** do texto da mensagem é o seguinte:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Para habilitar o bom funcionamento do código do bot, há algumas práticas recomendadas que você deve seguir.

## <a name="command-menu-best-practices"></a>Práticas recomendadas do menu de comando

A seguir estão as práticas recomendadas do menu de comando:

* Mantenha-o simples: o menu do bot destina-se a apresentar os principais recursos do bot.
* Seja breve: as opções de menu não devem ser longas e não devem ser instruções de linguagem natural complexas. Devem ser comandos simples.
* Mantenha-o invocável: ações ou comandos do menu do bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.

> [!NOTE]
> Se você remover qualquer comando do manifesto, deverá reimplantar seu aplicativo para implementar as alterações. Em geral, todas as alterações no manifesto exigem que você reimplante seu aplicativo.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Conversas em canal e em grupo](~/bots/how-to/conversations/channel-and-group-conversations.md)
