---
title: Criar um menu de comando para seu bot
author: surbhigupta
description: Saiba como criar um menu de comando para seu bot Microsoft Teams com exemplos de código.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
keywords: menu de comando redigir conversa de mensagem @mention
ms.openlocfilehash: bf9b6963b482a335175e5a9c75b6c928104ead26
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888234"
---
# <a name="bot-command-menus"></a>Menus de comando bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Para definir um conjunto de comandos principais aos quais o bot pode responder, você pode adicionar um menu de comando com uma lista lista de comandos suspensos para seu bot. A lista de comandos é apresentada aos usuários na área de mensagem de composição quando eles estão em conversa com seu bot. Selecione um comando na lista para inserir a cadeia de caracteres de comando na caixa de mensagem de composição e selecione **Enviar**.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Menu de comando bot](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

![Menu de comando de bot móvel](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Criar um menu de comando para seu bot

Os menus de comando são definidos no manifesto do aplicativo. Você pode usar o **App Studio para** criar ou adicioná-los manualmente no manifesto do aplicativo.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Criar um menu de comando para seu bot usando o App Studio

Um pré-requisito para criar um menu de comando para seu bot é que você deve editar um manifesto de aplicativo existente. As etapas para adicionar um menu de comando são as mesmas, se você criar um novo manifesto ou editar um existente.

**Para criar um menu de comando para seu bot usando o App Studio**

1. Abra Teams e selecione **Aplicativos** no painel esquerdo. Na página **Aplicativos,** procure o **App Studio** e selecione **Abrir**.
   > [!NOTE]
   > Se você não tiver o **App Studio,** poderá baixá-lo. Para obter mais informações, [consulte installing App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).

    ![App Studio](./conversations/media/AppStudio.png)

2. No **App Studio,** selecione a **guia Editor de** manifesto. Se você não tiver um pacote de aplicativos existente, poderá criar ou importar um aplicativo existente. Para obter mais informações, [consulte atualizar um pacote de aplicativos](~/get-started/deploy-csharp-app-studio.md).

3. No painel esquerdo do editor **de manifesto** e na seção **Recursos,** selecione **Bots**.

4. No painel direito do editor **de manifesto** e na seção **Comandos,** selecione **Adicionar**. A **tela Novo Comando** é exibida.

    ![Menu Comandos do App Studio Adicionar botão](./conversations/media/AppStudio-CommandMenu-Add.png)

5. Insira o **texto Comando** que deve aparecer como o menu de comando do bot.

6. Insira o **texto da Ajuda** que deve aparecer sob o texto do comando no menu. **O texto da** ajuda deve ser uma breve explicação sobre a finalidade do comando.

7. Selecione as **caixas de** seleção Escopo para selecionar onde esse menu de comando deve aparecer e selecione **Salvar**.

    ![Botão de menu novos comandos do App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Criar um menu de comando para seu bot editando Manifest.json

Outra maneira de criar um menu de comando é cria-lo diretamente no arquivo de manifesto enquanto desenvolve o código-fonte do bot. Para usar esse método, siga estes pontos:

* Cada menu dá suporte a até dez comandos.
* Crie um único menu de comando que funcione em todos os escopos.
* Crie um menu de comando diferente para cada escopo.

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a>Exemplo de manifesto para menu único para ambos os escopos

O código de exemplo de manifesto para menu único para ambos os escopos é o seguinte:

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

O código de exemplo de manifesto para o menu para cada escopo é o seguinte:

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

Você deve manipular comandos de menu em seu código de bot à medida que lida com qualquer mensagem dos usuários. Você pode manipular comandos de menu em seu código de bot ao analisar a parte **\@ Menção** do texto da mensagem.

## <a name="handle-menu-commands-in-your-bot-code"></a>Manipular comandos de menu em seu código de bot

Os bots em um grupo ou canal respondem somente quando são mencionados `@botname` em uma mensagem. Cada mensagem recebida por um bot quando em um escopo de grupo ou canal contém seu nome no texto da mensagem retornado. Antes de manipular o comando que está sendo retornado, a análise da mensagem deve manipular a mensagem recebida por um bot com seu nome.

> [!NOTE]
> Para manipular os comandos em código, eles são enviados para o bot como uma mensagem regular. Você deve lidar com eles como faria com qualquer outra mensagem de seus usuários. Os comandos no código inseram texto pré-configurado na caixa de texto. Em seguida, o usuário deve enviar esse texto como faz para qualquer outra mensagem.

# <a name="c"></a>[C#](#tab/dotnet)

Você pode analisar a parte **\@ Menção** do texto da mensagem usando um método estático fornecido com o Microsoft Bot Framework. É um método da classe `Activity` chamada `RemoveRecipientMention` .

O C# código para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Você pode analisar a parte **\@ Menção** do texto da mensagem usando um método estático fornecido com a Estrutura de Bot. É um método da classe `TurnContext` chamada `removeMentionText` .

O código JavaScript para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

Você pode analisar a parte **@Mention** do texto da mensagem usando um método estático fornecido com a Estrutura de Bot. É um método da classe `TurnContext` chamada `remove_recipient_mention` .

O código Python para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Para habilitar o funcionamento suave do código do bot, há poucas práticas recomendadas que você deve seguir.

## <a name="command-menu-best-practices"></a>Práticas recomendadas do menu de comando

A seguir estão as práticas recomendadas do menu de comando:

* Mantenha-o simples: o menu bot deve apresentar os principais recursos do bot.
* Mantenha-o curto: as opções de menu não devem ser longas e não devem ser instruções de idioma natural complexas. Eles devem ser comandos simples.
* Mantenha-o invocavel: ações ou comandos de menu bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.

> [!NOTE]
> Se você remover quaisquer comandos do manifesto, reimplante seu aplicativo para implementar as alterações. Em geral, quaisquer alterações no manifesto exigem que você reimplante seu aplicativo.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Conversas em canal e em grupo](~/bots/how-to/conversations/channel-and-group-conversations.md)
