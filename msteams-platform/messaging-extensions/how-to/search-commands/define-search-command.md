---
title: Definir comandos de pesquisa de extensão de mensagem
author: surbhigupta
description: Neste módulo, saiba mais sobre os comandos de pesquisa de extensão de mensagem Teams aplicativos, para criar um comando de pesquisa por meio do manifesto do aplicativo e manualmente.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 10bb71580ac67db155bd14b74325635ae22e6840
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189615"
---
# <a name="define-message-extension-search-commands"></a>Definir comandos de pesquisa de extensão de mensagem

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de pesquisa de extensão de mensagem permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão. Este documento orienta você sobre como selecionar locais de invocação de comando de pesquisa e adicionar o comando de pesquisa ao manifesto do aplicativo.

> [!NOTE]
> O limite de tamanho do cartão de resultado é de 28 KB. O cartão não será enviado se seu tamanho exceder 28 KB.

Confira o vídeo a seguir para saber como definir comandos de pesquisa de extensão de mensagem:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OIvK]
<br>

## <a name="select-search-command-invoke-locations"></a>Selecionar locais de invocação de comando de pesquisa

O comando de pesquisa é invocado de qualquer um ou ambos os seguintes locais:

* Área redigir mensagem: os botões na parte inferior da área de mensagem de redação.
* Caixa de comando: @mentioning na caixa de comando.

  Quando o comando de pesquisa é invocado da área de mensagem de composição, o usuário envia os resultados para a conversa. Quando ele é invocado na caixa de comando, o usuário interage com o cartão resultante ou o copia para uso em outro lugar.

A imagem a seguir exibe os locais de invocação do comando de pesquisa:

:::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-locations.png" alt-text="Locais de invocação de comando de pesquisa":::

## <a name="add-the-search-command-to-your-app-manifest"></a>Adicionar o comando de pesquisa ao manifesto do aplicativo

Para adicionar o comando de pesquisa ao manifesto do aplicativo, `composeExtension` você deve adicionar um novo objeto ao nível superior do JSON do manifesto do aplicativo. Você pode adicionar o comando de pesquisa com a ajuda do App Studio ou manualmente.

### <a name="create-a-search-command-using-app-studio"></a>Criar um comando de pesquisa usando o App Studio

O pré-requisito para criar um comando de pesquisa é que você já deve ter criado uma extensão de mensagem. Para obter informações sobre como criar uma extensão de mensagem, consulte [criar uma extensão de mensagem](~/messaging-extensions/how-to/create-messaging-extension.md).

Para criar um comando de pesquisa:

1. Abra **App Studio** no cliente do Microsoft Teams e selecione a guia **Editor de Manifesto**.
1. Se você já criou o pacote do aplicativo **no App Studio**, selecione na lista. Se você não tiver criado um pacote do aplicativo, importe um existente.
1. Depois de importar o pacote do aplicativo, selecione **Extensões de mensagem** em **Funcionalidades**. Você obtém uma janela pop-up para configurar a extensão de mensagem.
1. Selecione **Configurar** na janela para incluir a extensão de mensagem na experiência do aplicativo. A imagem a seguir exibe a página de configuração da extensão de mensagem:

    :::image type="content" source="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt-text="Configuração da extensão de mensagem":::

1. Para criar a extensão de mensagem, você precisa de um bot registrado pela Microsoft. Você pode usar um bot existente ou criar um novo bot. Selecione a opção **Criar novo bot**, dê um nome para o novo bot e selecione **Criar**. A imagem a seguir exibe a criação do bot para a extensão de mensagem:

    :::image type="content" source="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt-text="Criar bot para extensão de mensagem":::

1. Para usar um bot existente, selecione **Usar bot existente** e selecione **Selecionar em um dos meus bots existentes** para escolher os bots existentes na lista suspensa, dê um **nome de Bot** e selecione **Salvar** ou selecione **Conectar-se a uma ID de bot diferente** se você já tiver uma ID de bot criada, dê um **nome de Bot** e selecione **Salvar**.

    :::image type="content" source="~/assets/images/messaging-extension/use-existing-bot.png" alt-text="Usar o bot existente para a extensão de mensagem":::

1. Selecione **Adicionar** na seção **Comando da** página de extensões de mensagem para incluir os comandos, que decidem o comportamento da extensão da mensagem.
A imagem a seguir exibe a adição de comando para a extensão de mensagem:

    :::image type="content" source="~/assets/images/messaging-extension/include-command.png" alt-text="Comando Incluir":::

1. Selecione **Permitir que os usuários consultem seu serviço para obter informações e inseri-lo em uma mensagem**. A imagem a seguir exibe a seleção do parâmetro de comando de pesquisa:

    :::image type="content" source="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt-text="Seleção de parâmetro de comando de pesquisa":::

1. Adicione uma **ID de Comando** e um **Título**.
1. Selecione o local de onde o comando de pesquisa deve ser invocado. A imagem a seguir exibe o local de invocação do comando de pesquisa:

    :::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt-text="Seleção de localização de invocação de comando de pesquisa":::

1. Adicione o parâmetro de pesquisa e selecione **Salvar**.

### <a name="create-a-search-command-manually"></a>Criar um comando de pesquisa manualmente

Para adicionar manualmente o comando de pesquisa de extensão de mensagem ao manifesto do aplicativo, você deve adicionar os seguintes parâmetros à sua `composeExtension.commands` matriz de objetos:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui ao comando de pesquisa. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `description` | Essa propriedade é um texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser um `query`. | Não | 1.4 |
|`initialRun` | Se essa propriedade for definida como **true**, ela indicará que esse comando deverá ser executado assim que o usuário selecionar esse comando na interface do usuário. | Não | 1.0 |
| `context` | Essa propriedade é uma matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível. Os valores possíveis são `message`, `compose` ou `commandBox`. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Você deve adicionar os detalhes do parâmetro de pesquisa, que define o texto visível para o usuário no Teams cliente.

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade define uma lista estática de parâmetros para o comando. | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Essa propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo de entrada necessária. Os valores possíveis `text`incluem `textarea`, `number`, , `date`, `time`. `toggle` O padrão é definido como `text`. | Não | 1.4 |

#### <a name="example"></a>Exemplo

A seção a seguir é um exemplo do manifesto do aplicativo simples do objeto `composeExtensions` que define um comando de pesquisa:

```json
{
...
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
...
}
```

Para obter o manifesto completo do aplicativo, consulte [o esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="code-sample"></a>Exemplo de código

| Nome de exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Pesquisa de extensão de mensagem do Teams   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para criar](../../../sbs-messagingextension-searchcommand.yml) uma extensão de mensagem baseada em pesquisa.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Responda aos comandos de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).
