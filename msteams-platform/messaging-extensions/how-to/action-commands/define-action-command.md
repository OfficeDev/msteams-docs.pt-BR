---
title: Definir comandos de ação de extensão de mensagem
author: surbhigupta
description: Uma visão geral dos comandos de ação de extensão de mensagem com exemplo de manifesto do aplicativo
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ae0c39136b69b2759908bbbc54d1fff244eae0af
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103935"
---
# <a name="define-message-extension-action-commands"></a>Definir comandos de ação de extensão de mensagem

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de ação permitem apresentar aos usuários um pop-up modal chamado módulo de tarefa Teams. O módulo de tarefa coleta ou exibe informações, processa a interação e envia as informações de volta para Teams. Este documento orienta você sobre como selecionar locais de invocação de comando de ação, criar seu módulo de tarefa, enviar mensagem final ou cartão, criar um comando de ação usando o App Studio ou crie-o manualmente.

Antes de criar o comando de ação, você deve decidir os seguintes fatores:

1. [De onde o comando de ação pode ser disparado?](#select-action-command-invoke-locations)
1. [Como o módulo de tarefa será criado?](#select-how-to-create-your-task-module)
1. [A mensagem final ou o cartão será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a>Selecionar locais de invocação de comando de ação

Primeiro, você deve decidir o local de onde o comando de ação deve ser invocado. Ao especificar o manifesto `context` do aplicativo, o comando pode ser invocado de um ou mais dos seguintes locais:

* Redação da área da mensagem: os botões na parte inferior da área de mensagem de composição.

    Contexto de comando = redigir

* Caixa de comando: @mentioning seu aplicativo na caixa de comando.

    Contexto de comandos = commandBox

   > [!NOTE]
   > Se a extensão de mensagem for invocada na caixa de comando, você não poderá responder com uma mensagem de bot inserida diretamente na conversa.

* Mensagem: diretamente de uma mensagem existente por meio do `...` menu de estouro em uma mensagem.

    Contexto de comandos = mensagem

    > [!NOTE]
    > A invocação inicial para o bot inclui um objeto JSON que contém a mensagem da qual ele foi invocado. Você pode processar a mensagem antes de apresentá-la com um módulo de tarefa.

A imagem a seguir exibe os locais dos quais o comando de ação é invocado:

![locais de invocação de comando de ação](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a>Selecione como criar seu módulo de tarefa

Além de selecionar de onde o comando pode ser invocado, você também deve selecionar como preencher o formulário no módulo de tarefa para seus usuários. Você tem as três opções a seguir para criar o formulário renderizado dentro do módulo de tarefa:

* **Lista estática de parâmetros**: esse é o método mais simples. Você pode definir uma lista de parâmetros no manifesto do aplicativo que o Teams cliente renderiza, mas não pode controlar a formatação nesse caso.
* **Cartão Adaptável**: você pode optar por usar um Cartão Adaptável, que fornece maior controle sobre a interface do usuário, mas ainda limita você nos controles e opções de formatação disponíveis.
* **Exibição da Web** inserida: você pode optar por inserir um modo de exibição da Web personalizado no módulo de tarefa para ter um controle completo sobre a interface do usuário e os controles.

Se você optar por criar o módulo de tarefa com uma lista estática de parâmetros e quando o usuário enviar o módulo de tarefa, a extensão da mensagem será chamada. Ao usar um modo de exibição da Web inserido ou um Cartão Adaptável, sua extensão de mensagem deve manipular um evento de invocação inicial do usuário, criar o módulo de tarefa e retorá-lo para o cliente.

## <a name="select-how-the-final-message-is-sent"></a>Selecione como a mensagem final é enviada

Na maioria dos casos, o comando de ação resulta em um cartão inserido na caixa de mensagem de composição. O usuário pode enviá-lo para o canal ou chat. Nesse caso, a mensagem vem do usuário e o bot não pode editar ou atualizar ainda mais o cartão.

Se a extensão de mensagem for invocada da caixa de redação ou diretamente de uma mensagem, o serviço Web poderá inserir a resposta final diretamente no canal ou chat. Nesse caso, o Cartão Adaptável vem do bot, o bot o atualiza e responde ao thread de conversa, se necessário. Você deve adicionar o `bot` objeto ao manifesto do aplicativo usando a mesma ID e definindo os escopos apropriados.

## <a name="add-the-action-command-to-your-app-manifest"></a>Adicionar o comando de ação ao manifesto do aplicativo

Para adicionar o comando de ação ao manifesto do aplicativo, você deve `composeExtension` adicionar um novo objeto ao nível superior do JSON do manifesto do aplicativo. Você pode usar uma das seguintes maneiras de fazer isso:

* [Criar um comando de ação usando o App Studio](#create-an-action-command-using-app-studio)
* [Criar um comando de ação manualmente](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a>Criar um comando de ação usando o App Studio

Você pode criar um comando de ação usando **o App Studio ou** o **Portal do Desenvolvedor**.

> [!NOTE]
> O App Studio será preterido em breve. Configure, distribua e gerencie seus Teams com o novo [Portal do Desenvolvedor](https://dev.teams.microsoft.com/).

# <a name="app-studio"></a>[App Studio](#tab/AS)

> [!NOTE]
> O pré-requisito para criar um comando de ação é que você já tenha criado uma extensão de mensagem. Para obter informações sobre como criar uma extensão de mensagem, consulte [criar uma extensão de mensagem](~/messaging-extensions/how-to/create-messaging-extension.md).

**Para criar um comando de ação**

1. Abra **o App Studio** no Microsoft Teams cliente e selecione a **guia Editor de** manifesto.
1. Se você já tiver criado o pacote do aplicativo **no App Studio**, selecione-o na lista. Se você não tiver criado um pacote do aplicativo, importe um existente.
1. Depois de importar um pacote de aplicativos, selecione **Extensões de mensagem** em **Funcionalidades**. Você obtém uma janela pop-up para configurar a extensão de mensagem.
1. Selecione **Configurar na** janela para incluir a extensão de mensagem na experiência do aplicativo. A imagem a seguir exibe a janela de configuração da extensão de mensagem:

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. Para criar uma extensão de mensagem, você precisa de um bot registrado pela Microsoft. Você pode usar um bot existente ou criar um bot. Selecione **Criar nova opção de bot** , dê um nome para o novo bot e selecione **Criar**. A imagem a seguir exibe a criação do bot para a extensão de mensagem:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Selecione **Adicionar** na seção **Comando da** página de extensões de mensagem para incluir os comandos que decidem o comportamento da extensão da mensagem.
A imagem a seguir exibe a adição de comando para a extensão de mensagem:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. Selecione **Permitir que os usuários disparem ações em serviços externos enquanto estiverem dentro Teams**. A imagem a seguir exibe a seleção do comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>

1. Para usar um conjunto estático de parâmetros para criar o módulo de tarefa, selecione **Definir um conjunto de parâmetros estáticos para o comando**.

    A imagem a seguir exibe a seleção de parâmetro estático do comando de ação:

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/>

    A imagem a seguir exibe um exemplo de configuração de parâmetro estático:

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    A imagem a seguir exibe um exemplo de teste de parâmetro estático:

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. Para usar parâmetros dinâmicos, selecione **Buscar um conjunto dinâmico de parâmetros do bot**. A imagem a seguir exibe a seleção de parâmetro de comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>

1. Adicione uma **ID de comando** e um **título**.
1. Selecione o local de onde você deseja invocar o comando de ação. A imagem a seguir exibe o local de invocação do comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. Selecione **Salvar**.
1. Para adicionar mais parâmetros, selecione **o botão Adicionar** na **seção Parâmetros** .

### <a name="create-an-action-command-manually"></a>Criar um comando de ação manualmente

Para adicionar manualmente o comando de extensão de mensagem baseada em ação ao manifesto do aplicativo, você deve adicionar os seguintes parâmetros `composeExtension.commands` à matriz de objetos:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui a esse comando. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser um `action`. | Não | 1.4 |
| `fetchTask` | Essa propriedade é definida como para `true` um cartão adaptável ou exibição da Web inserida para seu módulo de tarefa e`false` para uma lista estática de parâmetros ou ao carregar o modo de exibição da Web por um `taskInfo`. | Não | 1.4 |
| `context` | Essa propriedade é uma matriz opcional de valores que define de onde a extensão de mensagem é invocada. Os valores possíveis são `message`, `compose` ou `commandBox`. O valor padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Se você estiver usando uma lista estática de parâmetros, também deverá adicionar os seguintes parâmetros:

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade descreve a lista estática de parâmetros para o comando. Use somente quando `fetchTask` for `false`. | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Essa propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo de parâmetro amigável curto. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo de entrada necessário. Os valores possíveis incluem `text`, `textarea`, `number`, `date`, `time`, `toggle`. O valor padrão é definido como `text`. | Não | 1.4 |

Se você estiver usando um modo de exibição da Web inserido, opcionalmente, `taskInfo` poderá adicionar o objeto para buscar o modo de exibição da Web sem chamar o bot diretamente. Se você selecionar essa opção, o comportamento será semelhante ao uso de uma lista estática de parâmetros. Nesse caso, a primeira interação com o bot está [respondendo à ação de envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Se você estiver usando um `taskInfo` objeto, deverá definir o parâmetro `fetchTask` como `false`.

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
|`taskInfo`|Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem. | Não | 1.4 |
|`taskInfo.title`|Título inicial do módulo de tarefa. |Não | 1.4 |
|`taskInfo.width`|Largura do módulo de tarefa, um número em pixels ou layout padrão, como `large`, `medium`ou `small`. |Não | 1.4 |
|`taskInfo.height`|Altura do módulo de tarefa, um número em pixels ou layout padrão, como `large`, `medium`ou `small`.|Não | 1.4 |
|`taskInfo.url`|URL inicial do modo de exibição da Web.|Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto do aplicativo

A seção a seguir é um exemplo de um objeto `composeExtensions` que define dois comandos de ação. Não é um exemplo do manifesto completo. Para obter o esquema completo do manifesto do aplicativo, consulte o [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md):

```json
...
"composeExtensions": [
  {
    "botId": "12a3c29f-1fc5-4d97-a142-12bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "addTodo",
        "description": "Create a To Do item",
        "title": "Create To Do",
        "type": "action",
        "context": ["commandBox", "message", "compose"],
        "fetchTask": true,
        "parameters": [
          {
            "name": "Name",
            "description": "To Do Title",
            "title": "Title",
            "inputType": "text"
          },
          {
            "name": "Description",
            "description": "Description of the task",
            "title": "Description",
            "inputType": "textarea"
          },
          {
            "name": "Date",
            "description": "Due date for the task",
            "title": "Date",
            "inputType": "date"
          }
        ]
      },
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Reassign a todo item",
        "type": "action",
        "fetchTask": true,
      }
    ]
  }
]
...
```

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams de extensão de mensagem| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para criar](../../../sbs-meetingextension-action.yml) uma extensão Teams de mensagem baseada em ação.

## <a name="next-step"></a>Próxima etapa

Se você estiver usando um Cartão Adaptável ou uma exibição da Web inserida sem um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Se você estiver usando os parâmetros ou uma exibição da Web inserida com um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Responder ao envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
