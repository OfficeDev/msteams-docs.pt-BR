---
title: Definir comandos de ação de extensão de mensagens
author: clearab
description: Uma visão geral dos comandos de ação de extensão de mensagens
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f49e821ecb98659b4cfd68f93b37f1a8f611a9fb
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020713"
---
# <a name="define-messaging-extension-action-commands"></a>Definir comandos de ação de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de ação permitem que você apresente aos usuários um pop-up modal chamado módulo de tarefa Teams. O módulo de tarefa coleta ou exibe informações, processa a interação e envia as informações de volta para Teams. Este documento orienta você sobre como selecionar locais de invocação de comando de ação, criar seu módulo de tarefa, enviar mensagem final ou cartão, criar comando de ação usando o app studio ou crie-o manualmente. 

Antes de criar o comando de ação, você deve decidir os seguintes fatores:

1. [De onde o comando de ação pode ser disparado?](#select-action-command-invoke-locations)
1. [Como o módulo de tarefa será criado?](#select-how-to-create-your-task-module)
1. [A mensagem final ou o cartão será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a>Selecionar locais de invocação de comando de ação

Primeiro, você deve decidir o local de onde seu comando de ação deve ser invocado. Especificando o `context` no manifesto do aplicativo, seu comando pode ser invocado de um ou mais dos seguintes locais:

* Área de mensagem de redação: os botões na parte inferior da área de mensagem de composição.
* Caixa de comando: @mentioning seu aplicativo na caixa de comando. 
   > [!NOTE]
   > Se a extensão de mensagens for invocada da caixa de comando, você não poderá responder com uma mensagem bot inserida diretamente na conversa.

* Mensagem: diretamente de uma mensagem existente por meio do `...` menu de estouro em uma mensagem. 
    > [!NOTE] 
    > A invocação inicial ao bot inclui um objeto JSON que contém a mensagem da qual foi invocada. Você pode processar a mensagem antes de apresentá-la com um módulo de tarefa.

A imagem a seguir exibe os locais de onde o comando de ação é invocado:

![locais de invocação de comando de ação](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a>Selecione como criar seu módulo de tarefas

Além de selecionar de onde o comando pode ser invocado, você também deve selecionar como preencher o formulário no módulo de tarefas para seus usuários. Você tem as três opções a seguir para criar o formulário renderizado dentro do módulo de tarefa:   

* **Lista estática de parâmetros**: este é o método mais simples. Você pode definir uma lista de parâmetros no manifesto do aplicativo que o cliente Teams renderiza, mas não pode controlar a formatação nesse caso.
* **Cartão Adaptável**: você pode selecionar para usar um Cartão Adaptável, que fornece maior controle sobre a interface do usuário, mas ainda o limita nos controles disponíveis e opções de formatação.
* **Exibição da Web** incorporada : Você pode selecionar para inserir um exibição da Web personalizado no módulo de tarefas para ter um controle completo sobre a interface do usuário e os controles. 

Se você selecionar para criar o módulo de tarefa com uma lista estática de parâmetros e quando o usuário enviar o módulo de tarefa, a extensão de mensagens será chamada. Ao usar uma exibição da Web incorporada ou um Cartão Adaptável, sua extensão de mensagens deve manipular um evento de invocação inicial do usuário, criar o módulo de tarefa e devolvê-lo ao cliente.

## <a name="select-how-the-final-message-is-sent"></a>Selecione como a mensagem final é enviada

Na maioria dos casos, o comando de ação resulta em um cartão inserido na caixa de mensagem de redação. O usuário pode enviá-lo para o canal ou chat. Nesse caso, a mensagem vem do usuário, e o bot não pode editar ou atualizar o cartão ainda mais.

Se a extensão de mensagens for invocada da caixa de redação ou diretamente de uma mensagem, seu serviço Web poderá inserir a resposta final diretamente no canal ou chat. Nesse caso, o Cartão Adaptável vem do bot, o bot o atualiza e responde ao thread de conversa, se necessário. Você deve adicionar o `bot` objeto ao manifesto do aplicativo usando a mesma ID e definindo os escopos apropriados.

## <a name="add-the-action-command-to-your-app-manifest"></a>Adicionar o comando de ação ao manifesto do aplicativo

Para adicionar o comando de ação ao manifesto do aplicativo, você deve adicionar um novo objeto ao nível superior do manifesto `composeExtension` do aplicativo JSON. Você pode usar uma das seguintes maneiras de fazer isso:

* [Criar um comando de ação usando o App Studio](#create-an-action-command-using-app-studio)
* [Criar um comando de ação manualmente](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a>Criar um comando de ação usando o App Studio

> [!NOTE]
> O pré-requisito para criar um comando de ação é que você já criou uma extensão de mensagens. Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**Para criar um comando de ação**

1. Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** manifesto.
1. Se você já criou seu pacote de aplicativos **no App Studio,** selecione-o na lista. Se você não tiver criado um pacote de aplicativos, importe um existente.
1. Depois de importar um pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**. Você tem uma janela pop-up para configurar a extensão de mensagens.
1. Selecione **Configurar na** janela para incluir a extensão de mensagens na experiência do aplicativo. A imagem a seguir exibe a janela de configuração da extensão de mensagens:

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. Para criar uma extensão de mensagens, você precisa de um bot registrado da Microsoft. Você pode usar um bot existente ou criar um novo bot. Selecione **Criar nova opção bot,** dê um nome para o novo bot e selecione **Criar**. A imagem a seguir exibe a criação de bots para extensão de mensagens:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Selecione **Adicionar** na seção **Comando da** página extensões de mensagens para incluir os comandos que decidem o comportamento da extensão de mensagens.   
A imagem a seguir exibe a adição de comando para extensão de mensagens:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. Selecione **Permitir que os usuários acionem ações em serviços externos enquanto estão Teams**. A imagem a seguir exibe a seleção de comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. Para usar um conjunto estático de parâmetros para criar seu módulo de tarefa, selecione Definir um conjunto de **parâmetros estáticos para o comando**. 

    A imagem a seguir exibe a seleção de parâmetro estático do comando de ação:

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    A imagem a seguir exibe um exemplo de configuração de parâmetro estático: 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    A imagem a seguir exibe um exemplo de teste de parâmetro estático:

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. Para usar parâmetros dinâmicos, selecione **Para Buscar um conjunto dinâmico de parâmetros do bot**. A imagem a seguir exibe a seleção do parâmetro de comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. Adicione uma **ID de Comando** e um **Título.**
1. Selecione o local de onde você deseja invocar o comando de ação. A imagem a seguir exibe o local de invocação do comando de ação:

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. Selecione **Salvar**.
1. Para adicionar mais parâmetros, selecione o **botão Adicionar** na **seção Parâmetros.**

### <a name="create-an-action-command-manually"></a>Criar um comando de ação manualmente

Para adicionar manualmente o comando de extensão de mensagens baseada em ação ao manifesto do aplicativo, adicione os seguintes parâmetros à `composeExtension.commands` matriz de objetos:

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui a este comando. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser `action` um . | Não | 1.4 |
| `fetchTask` | Essa propriedade é definida como para um cartão adaptável ou exibição da Web incorporada para o módulo de tarefas e para uma lista estática de parâmetros ou ao carregar o visualização `true` da Web por um `false` `taskInfo` . | Não | 1.4 |
| `context` | Essa propriedade é uma matriz opcional de valores que define de onde a extensão de mensagens é invocada. Os valores possíveis são `message`, `compose` ou `commandBox`. O valor padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Se você estiver usando uma lista estática de parâmetros, também deverá adicionar os seguintes parâmetros:

| Nome da propriedade | Finalidade | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade descreve a lista estática de parâmetros do comando. Use somente quando `fetchTask` for `false` . | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Esta propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo de parâmetro fácil de usar. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo de entrada necessária. Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` . O valor padrão é definido como `text` . | Não | 1.4 |

Se você estiver usando uma exibição da Web incorporada, você pode, opcionalmente, adicionar o objeto para buscar sua `taskInfo` exibição da Web sem chamar seu bot diretamente. Se você selecionar essa opção, o comportamento será semelhante ao de usar uma lista estática de parâmetros. Na medida em que a primeira interação com seu bot está [respondendo à ação](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)de envio do módulo de tarefas . Se você estiver usando um `taskInfo` objeto, deverá definir o `fetchTask` parâmetro como `false` .

| Nome da propriedade | Finalidade | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
|`taskInfo`|Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens. | Não | 1.4 |
|`taskInfo.title`|Título inicial do módulo de tarefa. |Não | 1.4 |
|`taskInfo.width`|Largura do módulo de tarefa, um número em pixels ou layout `large` padrão, como , `medium` ou `small` . |Não | 1.4 |
|`taskInfo.height`|Altura do módulo de tarefa, um número em pixels ou layout `large` padrão, como , `medium` ou `small` .|Não | 1.4 |
|`taskInfo.url`|URL de exibição da Web inicial.|Não | 1.4 | 

#### <a name="app-manifest-example"></a>Exemplo de manifesto do aplicativo

A seção a seguir é um exemplo de um `composeExtensions` objeto que define dois comandos de ação. Não é um exemplo do manifesto completo. Para o esquema de manifesto completo do aplicativo, consulte [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md):

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

| Exemplo de nome           | Descrição | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams ação de extensão de mensagens| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams de extensão de mensagens   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Próxima etapa

Se você estiver usando um Cartão Adaptável ou uma exibição da Web incorporada sem um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Se você estiver usando os parâmetros ou uma exibição da Web incorporada com um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Responder ao envio do módulo de tarefas](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

