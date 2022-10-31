---
title: Definir comandos de pesquisa de extensão de mensagem
author: surbhigupta
description: Saiba mais sobre os comandos de pesquisa de extensão de mensagens para aplicativos do Teams, para criar um comando de pesquisa por meio do manifesto do aplicativo e manualmente.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: c126d6436c5fb091804c92caeb2876c09392bd9b
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791829"
---
# <a name="define-message-extension-search-commands"></a>Definir comandos de pesquisa de extensão de mensagem

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de pesquisa de extensão de mensagem permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão. Este documento orienta você sobre como selecionar locais de invocação de comando de pesquisa e adicionar o comando de pesquisa ao manifesto do aplicativo.

> [!NOTE]
> O limite de tamanho do cartão de resultado é de 28 KB. O cartão não será enviado se o tamanho exceder 28 KB.

Confira o vídeo a seguir para saber como definir comandos de pesquisa de extensão de mensagem:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OIvK]
<br>

## <a name="select-search-command-invoke-locations"></a>Selecionar locais de invocação de comando de pesquisa

O comando de pesquisa é invocado de qualquer um ou ambos os seguintes locais:

* Área redigir mensagem: os botões na parte inferior da área de mensagem de redação.
* Caixa de comando: por @mentioning na caixa de comando.

Quando um comando de pesquisa é invocado da área de mensagem de composição, o usuário envia os resultados para a conversa. Quando ele é invocado da caixa de comando, o usuário interage com o cartão resultante ou copia-o para uso em outro lugar.

A imagem a seguir exibe os locais de invocação do comando de pesquisa:

:::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-locations.png" alt-text="A captura de tela mostra os locais de invocação de um comando de pesquisa em um canal do Teams.":::

## <a name="add-the-search-command-to-your-app-manifest"></a>Adicionar o comando de pesquisa ao manifesto do aplicativo

Para adicionar o comando de pesquisa ao manifesto do aplicativo, você deve adicionar um novo `composeExtension` objeto ao nível superior do JSON do manifesto do aplicativo. Você pode adicionar o comando de pesquisa com a ajuda do Portal do Desenvolvedor ou manualmente.

### <a name="create-a-search-command-using-developer-portal"></a>Criar um comando de pesquisa usando o Portal do Desenvolvedor

O pré-requisito para criar um comando de pesquisa é que você já deve ter criado uma extensão de mensagem. Para obter informações sobre como criar uma extensão de mensagem, consulte [criar uma extensão de mensagem](~/messaging-extensions/how-to/create-messaging-extension.md).

**Para criar um comando de ação**

1. Abra o **Portal do Desenvolvedor** no cliente do Microsoft Teams e selecione a guia **Aplicativos** . Se você já criou seu pacote de aplicativos no **Portal do Desenvolvedor**, selecione na lista. Se você ainda não criou um pacote de aplicativo, importe um existente.
1. Depois de importar um pacote de aplicativo, selecione **Extensões de mensagem** em **Recursos de aplicativo**.
1. Para criar uma extensão de mensagem, você precisa de um bot registrado pela Microsoft. Você pode usar um bot existente ou criar um novo bot. Selecione **Criar nova opção de bot** , dê um nome ao novo bot e selecione **Criar**.

   :::image type="content" source="../../../assets/images/tdp/bot-page.png" alt-text="A captura de tela mostra as opções para configurar um bot para um aplicativo no Portal do Desenvolvedor do Teams.":::

1. Para usar um bot existente, **selecione Selecionar um bot existente** e escolha os bots existentes na lista suspensa ou selecione **Inserir uma ID do bot** se você já tiver uma ID do bot criada.

1. Selecione o escopo da extensão de mensagens e selecione **Salvar**.

1. Selecione **Adicionar um comando** na seção **Comando** para incluir os comandos, que decidem o comportamento da extensão de mensagem.
A imagem a seguir exibe a adição de comando para a extensão de mensagem:

   :::image type="content" source="../../../assets/images/tdp/add-a-command.PNG" alt-text="A captura de tela mostra como adicionar um comando no Portal do Desenvolvedor do Teams para definir o comportamento da extensão da mensagem.":::

1. Selecione **Pesquisar** e insira **ID de comando**, **título de comando** e **descrição do comando**.

1. Insira todos os parâmetros e selecione o tipo de entrada na lista suspensa.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-parameter.PNG" alt-text="A captura de tela mostra como adicionar um parâmetro para definir seu comando no Portal do Desenvolvedor do Teams para uma extensão de mensagem.":::

1. Selecione **Adicionar um domínio** em **Links de visualização**.

1. Insira domínio válido e selecione **Adicionar**.

   :::image type="content" source="../../../assets/images/tdp/add-domain.PNG" alt-text="A captura de tela mostra como adicionar um domínio válido à sua extensão de mensagens para a desenrolação de link.":::

1. Selecione **Salvar**.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-save.PNG" alt-text="A captura de tela mostra como salvar todas as suas configurações e parâmetros para sua extensão de mensagem.":::

**Para adicionar parâmetros adicionais**

1. Selecione reticências na seção comando e selecione **Editar parâmetro**.

   :::image type="content" source="../../../assets/images/tdp/edit-parameters.PNG" alt-text="Capturas de tela que mostram como editar parâmetros para sua extensão de mensagem.":::

1. Selecione **Adicionar parâmetros e insira** todos os parâmetros.

   :::image type="content" source="../../../assets/images/tdp/add-parameter.PNG" alt-text="A captura de tela mostra como adicionar parâmetros adicionais para sua extensão de mensagem."lightbox="../../../assets/images/tdp/add-a-parameters.PNG":::

### <a name="create-a-search-command-manually"></a>Criar um comando de pesquisa manualmente

Para adicionar manualmente o comando de pesquisa de extensão de mensagem ao manifesto do aplicativo, você deve adicionar os seguintes parâmetros à matriz `composeExtension.commands` de objetos:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui ao comando de pesquisa. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário (interface do usuário). | Sim | 1.0 |
| `description` | Essa propriedade é um texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser um `query`. | Não | 1.4 |
|`initialRun` | Se essa propriedade estiver definida como **true**, ela indica que esse comando deve ser executado assim que o usuário selecionar esse comando na interface do usuário. | Não | 1.0 |
| `context` | Essa propriedade é uma matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível. Os valores possíveis são `message`, `compose` ou `commandBox`. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Você deve adicionar os detalhes do parâmetro de pesquisa que define o texto visível para o usuário no cliente do Teams.

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade define uma lista estática de parâmetros para o comando. | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. O `parameter.name` é enviado para seu serviço na solicitação de usuário. | Sim | 1.0 |
| `parameter.description` | Essa propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo da entrada necessária. Os valores possíveis incluem , , , , , `toggle``time`. `date``number``textarea``text` O padrão é definido como `text`. | Não | 1.4 |
| `parameters.value` | Valor inicial para o parâmetro. Atualmente, o valor não tem suporte | Não | 1,5 |

#### <a name="example"></a>Exemplo

A seção a seguir é um exemplo do manifesto de aplicativo simples do `composeExtensions` objeto que define um comando de pesquisa:

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

Para o manifesto completo do aplicativo, consulte [Esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="code-sample"></a>Exemplo de código

| Nome de exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Pesquisa de extensão de mensagem do Teams   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../../sbs-messagingextension-searchcommand.yml) para criar uma extensão de mensagem baseada em pesquisa.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Responda aos comandos de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).
