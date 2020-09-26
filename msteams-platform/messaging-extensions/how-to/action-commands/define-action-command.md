---
title: Definir comandos de ação de extensão de mensagens
author: clearab
description: Uma visão geral das extensões de mensagens na plataforma do Microsoft Teams
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 89cf92260418701ef4809f5a13750b991b9f7acb
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279678"
---
# <a name="define-messaging-extension-action-commands"></a>Definir comandos de ação de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de ação permitem que você apresente aos seus usuários um pop-up modal (chamado de módulo de tarefa no Microsoft Teams) para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Microsoft Teams. Antes de criar seu comando, você precisará decidir:

1. De onde pode ser disparado o comando Action?
1. Como o módulo de tarefa será criado?
1. A mensagem ou o cartão final será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?

## <a name="choose-action-command-invoke-locations"></a>Selecionar locais de invocação de comando de ação

A primeira coisa que você precisa decidir é onde o comando de ação pode ser acionado (ou mais especificamente, *invocado*) a partir do. Ao especificar o `context` em seu manifesto de aplicativo, seu comando pode ser chamado a partir de um ou mais dos seguintes locais:

* Os botões na parte inferior da área de mensagem de composição.
* Por @mentioning seu aplicativo na caixa de comando. Observação: você não pode responder com uma mensagem de bot inserida diretamente na conversa se sua extensão de mensagens for invocada na caixa de comando.
* Diretamente de uma mensagem existente por meio de... menu de estouro em uma mensagem. Observação: a chamada inicial para o bot incluirá um objeto JSON que contém a mensagem da qual foi invocado, o que você pode processar antes de apresentá-los com um módulo de tarefa.

## <a name="choose-how-to-build-your-task-module"></a>Escolha como criar seu módulo de tarefa

Além de escolher onde o comando pode ser chamado, você também deve escolher como preencher o formulário no módulo de tarefa para seus usuários. Você tem três opções para criar o formulário que é renderizado no módulo de tarefa:

* **Lista estática de parâmetros** -esta é a opção mais simples. Você pode definir uma lista de parâmetros (campos de entrada) em seu manifesto de aplicativo que o cliente do teams processará. Você não pode controlar a formatação com essa opção.
* **Cartão adaptável** : você pode optar por usar um cartão adaptável, que oferece maior controle sobre a interface do usuário, mas ainda limita você sobre os controles disponíveis e as opções de formatação.
* **Modo de exibição da Web incorporado** -se você precisar de controle completo sobre a interface do usuário e os controles, você pode optar por inserir um modo de exibição da Web personalizado no módulo de tarefa.

Se você optar por criar seu módulo de tarefa com uma lista estática de parâmetros, a primeira chamada para sua extensão de mensagens será quando um usuário enviar o módulo de tarefa. Ao usar um modo de exibição da Web incorporado ou um cartão adaptável, sua extensão de mensagens precisará lidar com um evento de chamada inicial do usuário, criar o módulo de tarefa e retorná-lo ao cliente.

## <a name="choose-how-the-final-message-will-be-sent"></a>Escolha como a mensagem final será enviada

Na maioria dos casos, o comando de ação resultará em um cartão inserido na caixa de mensagem de composição. Em seguida, o usuário pode optar por enviá-lo para o canal ou chat. A mensagem nesse caso vem do usuário e seu bot não poderá editar ou atualizar o cartão mais tarde.

Se sua extensão de mensagens é disparada a partir da caixa de redação ou diretamente de uma mensagem, seu serviço Web pode inserir a resposta final diretamente no canal ou chat. Nesse caso, o cartão adaptável é proveniente do bot, o bot será capaz de atualizá-lo, e o bot também poderá responder ao thread de conversa, se necessário. Você precisará adicionar o `bot` objeto ao manifesto do seu aplicativo usando a mesma ID e definindo os escopos apropriados.

## <a name="add-the-command-to-your-app-manifest"></a>Adicione o comando ao manifesto do aplicativo

Agora que você decidiu como os usuários irão interagir com seu comando Action, é hora de adicioná-lo ao manifesto do seu aplicativo. Para fazer isso, você adicionará um novo `composeExtension` objeto ao nível superior de seu aplicativo JSON de manifesto. Você pode fazer isso com a ajuda do App Studio ou manualmente.

### <a name="create-a-command-using-app-studio"></a>Criar um comando usando o app Studio

As etapas a seguir supõem que você já tenha [criado uma extensão de mensagens](~/messaging-extensions/how-to/create-messaging-extension.md).

1. No cliente Microsoft Teams, abra o **app Studio** e selecione a guia **Editor de manifesto** .
2. Se você já criou seu pacote de aplicativos no app Studio, escolha-o na lista. Caso contrário, você pode importar um pacote de aplicativos existente.
3. Clique no botão **Adicionar** na seção comando.
4. Escolha **permitir que os usuários disparem ações em serviços externos enquanto estão dentro do teams**.
5. Se você deseja usar um conjunto estático de parâmetros para criar seu módulo de tarefa, selecione essa opção. Caso contrário, opte por **buscar um conjunto dinâmico de parâmetros do bot**.
6. Adicione uma **ID de comando** e um **título**.
7. Selecione onde você deseja que seu comando de ação seja disparado.
8. Se você estiver usando parâmetros para o módulo de tarefas, adicione o primeiro.
9. Click Save
10. Se você precisar adicionar mais parâmetros, clique no botão **Adicionar** na seção **parâmetros** para adicioná-los.

### <a name="manually-create-a-command"></a>Criar um comando manualmente

Para adicionar manualmente o comando de extensão de mensagens baseado em ação ao manifesto do seu aplicativo, você precisará adicionar os parâmetros de acompanhamento à sua `composeExtension.commands` matriz de objetos.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a este comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `type` | Deve ser `action` | Não | 1.4 |
| `fetchTask` | `true` para um cartão adaptável ou modo de exibição da Web incorporado para seu módulo de tarefa, `false` para uma lista estática de parâmetros ou ao carregar o modo de exibição da Web por um `taskInfo` | Não | 1.4 |
| `context` | Matriz opcional de valores que define onde a extensão de mensagens pode ser chamada. Os valores possíveis são `message` , `compose` , ou `commandBox` . O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Se você estiver usando uma lista estática de parâmetros, você também as adicionará.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Lista estática de parâmetros para o comando. Usar somente quando `fetchTask` for `false` | Não | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado para o serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve os fins deste parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Defina como o tipo de entrada obrigatória. Os valores possíveis incluem,,,, `text` `textarea` `number` `date` `time` `toggle` . O padrão é definido como `text` | Não | 1.4 |

Se você estiver usando um modo de exibição da Web incorporado, você pode opcionalmente adicionar o `taskInfo` objeto para buscar o modo de exibição da Web sem chamar o bot diretamente. Se você optar por usar essa opção, o comportamento será semelhante ao uso de uma lista estática de parâmetros em que a primeira interação com o bot será [responder à ação de envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Se você estiver usando um `taskInfo` objeto, certifique-se de também definir o `fetchTask` parâmetro como `false` .

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
|`taskInfo`|Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens| Não | 1.4 |
|`taskInfo.title`|Título do módulo de tarefa inicial|Não | 1.4 |
|`taskInfo.width`|Largura do módulo de tarefa: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '|Não | 1.4 |
|`taskInfo.height`|Altura do módulo de tarefa-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '|Não | 1.4 |
|`taskInfo.url`|URL de exibição inicial da Web|Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto de aplicativo

Veja a seguir um exemplo de um `composeExtensions` objeto que define dois comandos de ação. Não é um exemplo de manifesto completo, para o esquema de manifesto de aplicativo completo, consulte: [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

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
        "fetchTask": false,
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

Se você estiver usando um cartão adaptável ou um modo de exibição da Web incorporado sem um `taskInfo` objeto, convém:

* [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Se você estiver usando parâmetros ou um modo de exibição da Web incorporado com um `taskInfo` objeto, a próxima etapa para você é:

* [Responder ao envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
