---
title: Definir comandos de ação de extensão de mensagens
author: clearab
description: Uma visão geral dos comandos de ação de extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: be2135477c4234187f374aef215f90e8329fb74e
ms.sourcegitcommit: 5739245903278d521ec920427248b6b48676e637
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49778398"
---
# <a name="define-messaging-extension-action-commands"></a>Definir comandos de ação de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de ação permitem que você apresente aos usuários um pop-up modal (chamado de módulo de tarefa no Teams) para coletar ou exibir informações e processar sua interação e enviar informações de volta para o Teams. Antes de criar seu comando, você precisará decidir:

1. De onde o comando de ação pode ser disparado?
1. Como o módulo de tarefa será criado?
1. A mensagem ou o cartão final será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de redação de mensagens para o usuário enviar?

## <a name="choose-action-command-invoke-locations"></a>Escolher locais de invocação de comando de ação

A primeira coisa que você precisa decidir é de onde o comando de ação pode ser disparado (ou, mais especificamente, *invocado).* Especificando o manifesto do aplicativo, o comando pode ser invocado em um ou `context` mais dos seguintes locais:

* Os botões na parte inferior da área de mensagem de composição.
* Ao @mentioning seu aplicativo na caixa de comando. Observação: você não poderá responder com uma mensagem de bot inserida diretamente na conversa se sua extensão de mensagens for invocada na caixa de comando.
* Diretamente de uma mensagem existente por meio do ... menu de estouro em uma mensagem. Observação: a invocação inicial para seu bot incluirá um objeto JSON que contém a mensagem da qual foi invocado, que você pode processar antes de apresentá-los com um módulo de tarefa.

## <a name="choose-how-to-build-your-task-module"></a>Escolher como criar seu módulo de tarefa

Além de escolher de onde o comando pode ser invocado, você também deve escolher como preencher o formulário no módulo de tarefa para seus usuários. Você tem três opções para criar o formulário renderizado dentro do módulo de tarefa:

* **Lista estática de parâmetros** - esta é a opção mais simples. Você pode definir uma lista de parâmetros (campos de entrada) no manifesto do aplicativo que o cliente do Teams renderizará. Você não pode controlar a formatação com essa opção.
* **Cartão adaptável** - Você pode optar por usar um cartão adaptável, que oferece maior controle sobre a interface do usuário, mas ainda limita você aos controles disponíveis e às opções de formatação.
* **Exibição da Web** incorporada – se precisar de controle total sobre a interface do usuário e os controles, você pode optar por inserir um exibição da Web personalizado no módulo de tarefa.

Se você optar por criar seu módulo de tarefa com uma lista estática de parâmetros, a primeira chamada para sua extensão de mensagens será quando um usuário enviar o módulo de tarefa. Ao usar uma exibição da Web incorporada ou um cartão adaptável, sua extensão de mensagens precisará manipular um evento de invocação inicial do usuário, criar o módulo de tarefa e retorciá-lo para o cliente.

## <a name="choose-how-the-final-message-will-be-sent"></a>Escolher como a mensagem final será enviada

Na maioria dos casos, o comando de ação resultará em um cartão inserido na caixa de mensagem de redação. Em seguida, o usuário pode decidir enviá-lo para o canal ou chat. Nesse caso, a mensagem vem do usuário, e seu bot não poderá editar ou atualizar o cartão ainda mais.

Se sua extensão de mensagens for disparada a partir da caixa de redação ou diretamente de uma mensagem, seu serviço Web poderá inserir a resposta final diretamente no canal ou chat. Nesse caso, o cartão adaptável vem do bot, o bot poderá atualizá-lo e o bot também pode responder ao thread de conversa, se necessário. Você precisará adicionar o objeto ao manifesto do aplicativo `bot` usando a mesma ID e definindo os escopos apropriados.

## <a name="add-the-command-to-your-app-manifest"></a>Adicionar o comando ao manifesto do aplicativo

Agora que você decidiu como os usuários irão interagir com o comando de ação, é hora de adicioná-lo ao manifesto do aplicativo. Para fazer isso, você adicionará um novo `composeExtension` objeto ao nível superior do JSON do manifesto do aplicativo. Você pode fazer isso com a ajuda do App Studio ou manualmente.

### <a name="create-a-command-using-app-studio"></a>Criar um comando usando o App Studio

As etapas a seguir presumem que você já [tenha criado uma extensão de mensagens.](~/messaging-extensions/how-to/create-messaging-extension.md)

1. No cliente do Microsoft Teams, abra **o App Studio** e selecione a guia Editor **de** Manifesto.
2. Se você já criou o pacote do aplicativo no App Studio, escolha-o na lista. Caso não seja, você pode importar um pacote do aplicativo existente.
3. Clique no **botão** Adicionar na seção Comando.
4. Choose **Allow users to trigger actions in external services while inside of Teams**.
5. Se você quiser usar um conjunto estático de parâmetros para criar seu módulo de tarefa, selecione essa opção. Caso contrário, escolha **buscar um conjunto dinâmico de parâmetros do seu bot.**
6. Adicione uma **ID de comando** e um **título.**
7. Selecione de onde você deseja que seu comando de ação seja disparado.
8. Se você estiver usando parâmetros para seu módulo de tarefa, adicione o primeiro.
9. Click Save
10. Se você precisar adicionar mais parâmetros, clique no botão **Adicionar** na **seção Parâmetros** para adicioná-los.

### <a name="manually-create-a-command"></a>Criar manualmente um comando

Para adicionar manualmente o comando de extensão de mensagens baseado em ação ao manifesto do aplicativo, você precisará adicionar os parâmetros a seguir à sua `composeExtension.commands` matriz de objetos.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a este comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Deve ser `action` | Não | 1.4 |
| `fetchTask` | `true` for an adaptive card or embedded web view for your task module, `false` for a static list of parameters or when loading the web view by a `taskInfo` | Não | 1.4 |
| `context` | Matriz opcional de valores que define de onde a extensão de mensagens pode ser invocada. Os valores possíveis `message` `compose` são , ou `commandBox` . O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Se você estiver usando uma lista estática de parâmetros, também os adicionará.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Lista estática de parâmetros do comando. Usar somente quando `fetchTask` for `false` | Não | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve as finalidades desse parâmetro ou exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo de parâmetros curtos amigáveis. | Sim | 1.0 |
| `parameter.inputType` | De acordo com o tipo de entrada necessário. Os valores possíveis `text` `textarea` incluem , `number` , , `date` , `time` `toggle` . O padrão é definido como `text` | Não | 1.4 |

Se você estiver usando um recurso de exibição da Web incorporado, opcionalmente, poderá adicionar o objeto para buscar sua exibição `taskInfo` da Web sem chamar seu bot diretamente. Se você optar por usar essa opção, o comportamento é semelhante ao uso de uma lista estática de parâmetros em que a primeira interação com seu bot responderá à ação de envio do módulo de [tarefa.](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md) Se você estiver usando um `taskInfo` objeto, certifique-se de também definir o `fetchTask` parâmetro como `false` .

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
|`taskInfo`|Especificar o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens| Não | 1.4 |
|`taskInfo.title`|Título inicial do módulo de tarefa|Não | 1.4 |
|`taskInfo.width`|Largura do módulo de tarefa - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'|Não | 1.4 |
|`taskInfo.height`|Altura do módulo de tarefa - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'|Não | 1.4 |
|`taskInfo.url`|URL inicial de exibição da Web|Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto do aplicativo

Veja a seguir um exemplo de um `composeExtensions` objeto que define dois comandos de ação. Não é um exemplo do manifesto completo, para o esquema de manifesto do aplicativo completo, confira: Esquema [de manifesto do aplicativo.](~/resources/schema/manifest-schema.md)

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

## <a name="next-steps"></a>Próximas etapas

Se você estiver usando um cartão adaptável ou uma exibição da Web incorporada sem um `taskInfo` objeto, você vai querer:

* [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Se você estiver usando parâmetros ou uma exibição da Web incorporada com um objeto, a `taskInfo` próxima etapa será:

* [Responder ao envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
