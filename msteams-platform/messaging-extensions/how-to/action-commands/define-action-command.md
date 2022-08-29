---
title: Definir comandos de ação de extensão de mensagem
author: surbhigupta
description: Neste módulo, aprenda a definir comandos de ação de extensão de mensagens com o exemplo de manifesto do aplicativo no Microsoft Teams.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0b51d34aaacfe38c077b03b5df8bb6a9227c5b61
ms.sourcegitcommit: 217025a61ed9c3b76b507fe95563142abc6d0318
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67363456"
---
# <a name="define-message-extension-action-commands"></a>Definir comandos de ação de extensão de mensagem

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> Quando uma ação de mensagem é iniciada, os detalhes do anexo não são enviados como parte da atividade de `turncontext` invocação.

Os comandos de ação permitem apresentar aos usuários um pop-up modal chamado módulo de tarefa no Teams. O módulo de tarefa coleta ou exibe informações, processa a interação e envia as informações de volta para o Teams. Este documento orienta você sobre como selecionar locais de invocação de comando de ação, criar seu módulo de tarefa, enviar mensagem final ou cartão, criar comando de ação usando o app studio ou criar manualmente.

Antes de criar o comando de ação, você deve decidir os seguintes fatores:

1. [De onde o comando de ação pode ser disparado?](#select-action-command-invoke-locations)
1. [Como o módulo de tarefa será criado?](#select-how-to-create-your-task-module)
1. [A mensagem final ou o cartão será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?](#select-how-the-final-message-is-sent)

Confira o vídeo a seguir para saber como definir comandos de ação de extensão de mensagem:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OANG]
<br>

## <a name="select-action-command-invoke-locations"></a>Selecionar locais de invocação de comando de ação

Primeiro, você deve decidir o local de onde o comando de ação deve ser invocado. Ao especificar o `context` no manifesto do aplicativo, o comando pode ser invocado de um ou mais dos seguintes locais:

* Área redigir mensagem: os botões na parte inferior da área de mensagem de redação.

    Contexto do comando = redigir

* Caixa de comando: fazer @menção do seu aplicativo na caixa de comando.

    Contexto de comandos = commandBox

   > [!NOTE]
   > Se a extensão de mensagem for invocada na caixa de comando, você não poderá responder com uma mensagem de bot inserida diretamente na conversa.

* Mensagem: Diretamente de uma mensagem existente por meio do menu de estouro `...` em uma mensagem.

    Contexto de comandos = mensagem

    > [!NOTE]
    > A invocação inicial para o bot inclui um objeto JSON que contém a mensagem da qual ele foi invocado. Você pode processar a mensagem antes de apresentá-la com um módulo de tarefa.

A imagem a seguir exibe os locais dos quais o comando de ação é invocado:

:::image type="content" source="~/assets/images/messaging-extension-invoke-locations.png" alt-text="Locais de invocação de comando de ação":::

## <a name="select-how-to-create-your-task-module"></a>Selecione como criar seu módulo de tarefa

Além de selecionar de onde o comando pode ser invocado, você também deve selecionar como preencher o formulário no módulo de tarefa para seus usuários. Você tem as três opções a seguir para criar o formulário renderizado dentro do módulo de tarefa:

* **Lista estática de parâmetros**: Esse é o método mais simples. Você pode definir uma lista de parâmetros no manifesto do aplicativo que o cliente do Teams renderiza, mas não pode controlar a formatação nesse caso.
* **Cartão Adaptável**: Você pode optar por usar um Cartão Adaptável, que fornece maior controle sobre a interface do usuário, mas ainda limita você aos controles e opções de formatação disponíveis.
* **Exibição da Web inserida**: Você pode optar por inserir uma exibição da Web personalizada no módulo de tarefa para ter um controle completo sobre a interface do usuário e os controles.

Se você optar por criar o módulo de tarefa com uma lista estática de parâmetros e quando o usuário enviar o módulo de tarefa, a extensão de mensagem será chamada. Ao usar uma exibição da Web inserida ou um Cartão Adaptável, sua extensão de mensagem deve manipular um evento de invocação inicial do usuário, criar o módulo de tarefa e retorná-lo ao cliente.

## <a name="select-how-the-final-message-is-sent"></a>Selecione como a mensagem final é enviada

Na maioria dos casos, o comando de ação resulta em um cartão inserido na caixa de mensagem de redação. O usuário pode enviá-lo para o canal ou chat. Nesse caso, a mensagem vem do usuário e o bot não pode editar nem atualizar o cartão ainda mais.

Se a extensão da mensagem for invocada da caixa de redação ou diretamente de uma mensagem, o serviço Web poderá inserir a resposta final diretamente no canal ou chat. Nesse caso, o Cartão Adaptável vem do bot, o bot o atualiza e responde ao thread de conversa, se necessário. Você deve adicionar o objeto `bot` ao manifesto do aplicativo usando a mesma ID e definindo os escopos apropriados.

## <a name="add-the-action-command-to-your-app-manifest"></a>Adicionar o comando de ação ao manifesto do aplicativo

Para adicionar o comando de ação ao manifesto do aplicativo, você deve adicionar um novo objeto `composeExtension` ao nível superior do JSON do manifesto do aplicativo. Você pode usar uma das seguintes maneiras de fazer isso:

* [Criar um comando de ação usando o Portal do Desenvolvedor](#create-an-action-command-using-developer-portal)
* [Criar um comando de ação manualmente](#create-an-action-command-manually)

### <a name="create-an-action-command-using-developer-portal"></a>Criar um comando de ação usando o Portal do Desenvolvedor

Você pode criar um comando de ação usando o **Portal do Desenvolvedor**.

# <a name="app-studio"></a>[App Studio](#tab/AS)

> [!NOTE]
> O pré-requisito para criar um comando de ação é que você já tenha criado uma extensão de mensagem. Para obter informações sobre como criar uma extensão de mensagem, consulte [criar uma extensão de mensagem](~/messaging-extensions/how-to/create-messaging-extension.md).

Para criar um comando de ação:

1. Abra **o Portal do** Desenvolvedor no cliente do Microsoft Teams e selecione a **guia Aplicativos** . Se você já tiver criado o pacote do aplicativo no **Portal do** Desenvolvedor, selecione na lista. Se você não tiver criado um pacote do aplicativo, importe um existente.
1. Depois de importar um pacote de aplicativos, selecione **Extensões de mensagem** em **Recursos do aplicativo**.
1. Para criar uma extensão de mensagem, você precisa de um bot registrado pela Microsoft. Você pode usar um bot existente ou criar um novo bot. Selecione **Criar nova opção de bot** , dê um nome ao novo bot e, em seguida, **selecione Criar**.

   :::image type="content" source="../../../assets/images/tdp/bot-page.png" alt-text="A captura de tela mostra como criar um bot no Portal do Desenvolvedor.":::

1. Para usar um bot existente, selecione Selecionar um bot existente e escolha os **bots** existentes na lista suspensa ou insira uma **ID de bot** se você já tiver uma ID de bot criada.

1. Selecione o escopo da extensão de mensagens e selecione **Salvar**.

1. Selecione **Adicionar um comando** na seção **Comando** para incluir os comandos, que decidem o comportamento da extensão de mensagem.

   :::image type="content" source="../../../assets/images/tdp/add-a-command.PNG" alt-text="A captura de tela mostra como adicionar um comando para definir o comportamento da extensão da mensagem.":::

1. Selecione **Ação e** , em seguida, selecione o tipo de parâmetro.

1. Insira **a ID do comando**, **o título do comando** e a **descrição do comando**.

1. Insira todos os parâmetros e selecione o tipo de entrada na lista suspensa.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-parameter.PNG" alt-text="A captura de tela mostra como adicionar parâmetros para definir o comando para a extensão de mensagem.":::

1. Selecione **Adicionar um domínio em** Links **de Visualização**.

1. Insira um domínio válido e selecione **Adicionar**.

   :::image type="content" source="../../../assets/images/tdp/add-domain.PNG" alt-text="A captura de tela mostra como adicionar um domínio válido à extensão de mensagens para desfralhamentos de link.":::

1. Selecione **Salvar**.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-save.PNG" alt-text="A captura de tela mostra como salvar todas as configurações e parâmetros da extensão de mensagem.":::

**Para adicionar parâmetros adicionais**

1. Selecione elipse na seção comando e, em seguida, selecione **Editar parâmetro**.

   :::image type="content" source="../../../assets/images/tdp/edit-parameters.PNG" alt-text="Capturas de tela mostram como adicionar parâmetros adicionais à extensão de mensagem.":::

1. Selecione **Adicionar parâmetros e** insira todos os parâmetros.

   :::image type="content" source="../../../assets/images/tdp/add-parameter.PNG" alt-text="A captura de tela mostra como adicionar parâmetros adicionais à extensão de mensagem."lightbox="../../../assets/images/tdp/add-a-parameters.PNG":::

### <a name="create-an-action-command-manually"></a>Criar um comando de ação manualmente

Para adicionar manualmente o comando de extensão de mensagem baseada em ação ao manifesto do aplicativo, você deve adicionar os seguintes parâmetros à matriz de objetos `composeExtension.commands`:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui a esse comando. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser `action`. | Não | 1.4 |
| `fetchTask` | Essa propriedade é definida como `true` para um cartão adaptável ou exibição da Web inserida para seu módulo de tarefa, e`false` para obter uma lista estática de parâmetros ou ao carregar a exibição da Web por um `taskInfo`. | Não | 1.4 |
| `context` | Essa propriedade é uma matriz opcional de valores que define de onde a extensão de mensagem é invocada. Os valores possíveis são `message`, `compose` ou `commandBox`. O valor padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Se você estiver usando uma lista estática de parâmetros, também deverá adicionar os seguintes parâmetros:

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade descreve a lista estática de parâmetros para o comando. Use somente quando `fetchTask` for `false`. | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Essa propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo de entrada necessário. Os valores possíveis incluem `text`, `textarea`, `number`, `date`, `time`, `toggle`. O valor padrão é definido como `text`. | Não | 1.4 |

Se você estiver usando um modo de exibição da Web inserido, opcionalmente, `taskInfo` poderá adicionar o objeto para buscar o modo de exibição da Web sem chamar o bot diretamente. Se você selecionar essa opção, o comportamento será semelhante ao do uso de uma lista estática de parâmetros. Já que a primeira interação com o bot é [responder à ação de envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Se você estiver usando um objeto `taskInfo` , deverá definir o parâmetro `fetchTask` como `false`.

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
|`taskInfo`|Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem. | Não | 1.4 |
|`taskInfo.title`|Título do módulo de tarefa inicial. |Não | 1.4 |
|`taskInfo.width`|Largura do módulo de tarefa, um número em pixels ou layout padrão, como `large`, `medium` ou `small`. |Não | 1.4 |
|`taskInfo.height`|Altura do módulo de tarefa, um número em pixels ou layout padrão, como `large`, `medium` ou `small`.|Não | 1.4 |
|`taskInfo.url`|URL inicial do modo de exibição da Web.|Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto do aplicativo

A seção a seguir é um exemplo de um objeto `composeExtensions` definindo dois comandos de ação. Não é um exemplo do manifesto completo. Para obter o esquema completo do manifesto do aplicativo, consulte [aplicar esquema de manifesto](~/resources/schema/manifest-schema.md):

```json
...
"composeExtensions": [
  {
    "botId": "c8fa3cf6-b1f0-4ba8-a5bf-a241bc29adf3",
    "scopes": [
      "personal",
      "groupchat"
    ],
    "commands": [
      {
        "id": "To do",
        "type": "action",
        "title": "Create To do",
        "description": "Create a To do",
        "initialRun": true,
        "fetchTask": false,
        "context": [
          "commandBox",
          "compose"
        ],
        "parameters": [
          {
            "name": "Name",
            "title": "Title",
            "description": "To do Title",
            "inputType": "text"
          },
          {
            "name": "Description",
            "title": "Description",
            "description": "Description of the task",
            "inputType": "textarea"
          },
          {
            "name": "Date",
            "title": "Date",
            "description": "Due date for the task",
            "inputType": "date"
          }
        ]
      }
    ],
    "canUpdateConfiguration": true,
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "yourapp.onmicrosoft.com"
          ]
        }
      }
    ]
  }
]
...
```

## <a name="code-sample"></a>Exemplo de código

| Nome de exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Ação de extensão de mensagem do Teams| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../../sbs-meetingextension-action.yml) para criar a extensão de mensagem baseada em ação do Teams.

## <a name="next-step"></a>Próxima etapa

Se você estiver usando um Cartão Adaptável ou uma exibição da Web inserida sem um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Se você estiver usando os parâmetros ou uma exibição da Web inserida com um objeto, a `taskInfo` próxima etapa será:

> [!div class="nextstepaction"]
> [Responder ao envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
