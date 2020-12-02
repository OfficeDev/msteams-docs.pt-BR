---
title: Criar um menu de comando para o bot
author: clearab
description: Como criar um menu de comando para o bot do Microsoft Teams
ms.topic: overview, command menu
ms.author: anclear
ms.openlocfilehash: ccbacc6ec6f18a38512d81dc898d0b14357d6ef7
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552483"
---
# <a name="bot-command-menus"></a>Menus de comando do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> Menus de bot não aparecerão em clientes móveis.

Adicionar menu de comando para seu bot permite que você defina um conjunto de comandos principais que seu bot possa sempre responder. A lista de comandos é apresentada ao usuário acima da área de mensagem de redação quando está convertida com o bot. A seleção de um comando na lista inserirá a cadeia de caracteres de comando na caixa de mensagem de redação, todos os usuários precisarão ser selecionados **Enviar**.

![Menu de comando do bot](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a>Criar um menu de comando para o bot

Menus de comando são definidos no manifesto do aplicativo. Você pode usar o app Studio para ajudá-lo a criá-los ou adicioná-los manualmente.

### <a name="creating-a-command-menu-for-your-bot-using-app-studio"></a>Criando um menu de comando para o bot usando o app Studio

As instruções aqui presumem que você esteja editando um manifesto de aplicativo existente. As etapas para adicionar um menu de comando são as mesmas, se você está criando um novo manifesto ou editando um existente.

1. Abra o app Studio no... menu de estouro no trilho esquerdo de navegação. Se você não tiver o app Studio disponível, você pode baixá-lo. Consulte [Installing app Studio](https://aka.ms/teams-app-studio#installing-app-studio) para obter mais informações sobre como usar o app Studio.

    ![App Studio](./conversations/media/AppStudio.png)

2. Uma vez no app Studio, selecione a guia **Editor do manifesto** .

3. Na coluna à esquerda do modo de exibição editor de manifesto na seção **recursos** , selecione **bots**.

4. Na coluna à direita do modo de exibição editor de manifesto na seção **comandos** , selecione o botão **Adicionar** .

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-CommandMenu-Add.png)

5. A **nova** tela de comando será exibida. Insira o **texto do comando** que você deseja que apareça como o comando de menu e o **texto de ajuda** que você deseja que apareçam diretamente sob o texto do comando no menu. Isso deve ser uma breve explicação da finalidade do comando.

6. Em seguida, selecione o (s) escopo (s) onde deseja que este menu de comando apareça e, em seguida, selecione o botão **salvar** .

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="creating-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Criar um menu de comando para o bot editando **Manifest.jsem**

Outra abordagem válida para a criação de um menu de comando é criá-lo diretamente no arquivo de manifesto ao desenvolver o código-fonte do bot. Aqui estão algumas coisas que você deve ter em mente ao usar essa abordagem:

1. Cada menu oferece suporte a até 10 comandos.

2. Você pode criar um único menu de comando que funcionará em todos os escopos.

3. Você pode criar um menu de comando diferente para cada escopo

#### <a name="manifest-example---single-menu-for-both-scopes"></a>Exemplo de manifesto – menu único para ambos os escopos

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

#### <a name="manifest-example---menu-for-each-scope"></a>Exemplo de manifesto-menu para cada escopo

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

## <a name="handling-menu-commands-in-your-bot-code"></a>Manipular comandos de menu no seu código de bot

Os bots em um grupo ou canal respondem apenas quando são mencionados ("@botname") em uma mensagem. Como resultado, todas as mensagens recebidas por um bot quando em um escopo de grupo ou canal conterão seu próprio nome no texto da mensagem retornado. Você precisa garantir que as alças de análise da mensagem antes de manipular o comando retornado.

> **Observação** Para manipular os comandos no código, eles são enviados ao bot como uma mensagem regular. Portanto, você precisa tratá-los como faria para qualquer outra mensagem de seus usuários. Eles são puramente um tratamento de interface do usuário que insere texto pré-configurado na caixa de texto. O usuário deve então enviar esse texto como faria para qualquer outra mensagem.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Você pode analisar a parte de **\@ menção** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `Activity` classe chamado `RemoveRecipientMention` .

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Você pode analisar a parte de **\@ menção** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `TurnContext` classe chamado `removeMentionText` .

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)


Você pode analisar a parte **@Mention** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `TurnContext` classe chamado `remove_recipient_mention` .

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

## <a name="command-menu-best-practices"></a>Práticas recomendadas do menu de comandos

* **Mantenha-o simples**: o menu bot é destinado a apresentar os principais recursos do bot.
* **Mantenha-** o em breve: as opções de menu não devem ser extremamente longas e instruções de linguagem natural complexas, que devem ser comandos simples.
* **Mantenha-o em invocação**: as ações/comandos do menu do bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.

> **Observação** Se você remover qualquer comando do manifesto, será necessário reimplantar seu aplicativo para que as alterações entrem em vigor. Em geral, qualquer alteração no manifesto exige isso.
