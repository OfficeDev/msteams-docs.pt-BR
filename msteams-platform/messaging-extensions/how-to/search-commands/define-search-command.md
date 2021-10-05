---
title: Definir comandos de pesquisa de extensão de mensagens
author: surbhigupta
description: Defina comandos de pesquisa de extensão de mensagens para Microsoft Teams aplicativos.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: none
ms.openlocfilehash: d87936832e3d302be295e14bbf952379a41aa694
ms.sourcegitcommit: 6573881f7e69d8e5ec8861f54df84e7d519f0511
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60096581"
---
# <a name="define-messaging-extension-search-commands"></a>Definir comandos de pesquisa de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão. Este documento orienta você sobre como selecionar locais de invocação de comando de pesquisa e adicionar o comando de pesquisa ao manifesto do aplicativo.

> [!NOTE]
> O limite de tamanho do cartão de resultado é de 28 KB. O cartão não será enviado se seu tamanho exceder 28 KB.

## <a name="select-search-command-invoke-locations"></a>Selecionar locais de invocação de comando de pesquisa

O comando de pesquisa é invocado de qualquer um ou ambos os seguintes locais:

* Área de mensagem de redação: os botões na parte inferior da área de mensagem de composição.
* Caixa de comando: @mentioning na caixa de comando.

Quando o comando de pesquisa é invocado da área de mensagem de composição, o usuário envia os resultados para a conversa. Quando ele é invocado da caixa de comando, o usuário interage com o cartão resultante ou o copia para uso em outro lugar.

A imagem a seguir exibe os locais de invocação do comando de pesquisa:

![locais de invocação de comando de pesquisa](~/assets/images/messaging-extension/search-command-invoke-locations.png)

## <a name="add-the-search-command-to-your-app-manifest"></a>Adicionar o comando de pesquisa ao manifesto do aplicativo

Para adicionar o comando de pesquisa ao manifesto do aplicativo, você deve adicionar um novo objeto ao nível superior `composeExtension` do manifesto JSON do aplicativo. Você pode adicionar o comando de pesquisa com a ajuda do App Studio ou manualmente.

### <a name="create-a-search-command"></a>Criar um comando de pesquisa 

Você pode criar o comando de pesquisa usando ** App Studio** ou **Portal do Desenvolvedor.**

> [!NOTE]
>  O App Studio será preterido em breve. Configure, distribua e gerencie seus aplicativos Teams com o novo [Portal do Desenvolvedor.](https://dev.teams.microsoft.com/)

# <a name="app-studio"></a>[App Studio](#tab/AS)

> [!NOTE]
> O pré-requisito para criar um comando de pesquisa é que você já deve ter criado uma extensão de mensagens. Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**Para criar um comando de pesquisa**

1. Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** Manifesto.
1.  Se você já criou seu pacote de aplicativos **no App Studio**, selecione na lista. Se você não tiver criado um pacote de aplicativos, importe um existente.
1. Depois de importar o pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**. Você tem uma janela pop-up para configurar a extensão de mensagens.
1. Selecione **Configurar na** janela para incluir a extensão de mensagens na experiência do aplicativo. A imagem a seguir exibe a página de configuração de extensão de mensagens: 

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. Para criar a extensão de mensagens, você precisa de um bot registrado da Microsoft. Você pode usar um bot existente ou criar um novo bot. Selecione **Criar nova opção bot,** dê um nome para o novo bot e selecione **Criar**. A imagem a seguir exibe a criação de bots para extensão de mensagens:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Selecione **Adicionar** na seção **Comando da** página extensões de mensagens para incluir os comandos que decidem o comportamento da extensão de mensagens.   
A imagem a seguir exibe a adição de comando para extensão de mensagens:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>
1. Selecione **Permitir que os usuários consultem seu serviço para obter informações e insira-os em uma mensagem**. A imagem a seguir exibe a seleção do parâmetro de comando de pesquisa:

    <img src="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt="search command parameter selection" width="500"/>

1. Adicione uma **ID de Comando** e um **Título.**
1. Selecione o local de onde o comando de pesquisa deve ser invocado. Selecionar **mensagem** no momento não altera o comportamento do comando de pesquisa. A imagem a seguir exibe o local de invocação do comando de pesquisa:

    <img src="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt="search command invoke location selection]" width="500"/>

1. Adicione o parâmetro de pesquisa e selecione **Salvar**.

# <a name="developer-portal"></a>[Portal do Desenvolvedor](#tab/DP)

**Para criar um comando de pesquisa usando o Portal do Desenvolvedor**

1. Vá para **[o portal do desenvolvedor.](https://dev.teams.microsoft.com/)**
    
   <img src="~/assets/images/tdp/tdp_home_1.png" alt="Screenshot of TDP" width="500"/>
    
1. Vá para **Aplicativos**.
    
    <img width="500px" alt="Screenshot of TDP Open" src="~/assets/images/tdp/screen2.png"/>
    
1. Se você já criou seu pacote de aplicativos no Portal do **Desenvolvedor,** selecione-o na lista. Se você não tiver criado um pacote de aplicativos, selecione **Importar um aplicativo existente.**

    <img width="500px" alt="Screenshot of import app in tdp" src="~/assets/images/tdp/screen3.png"/>

1. Vá para **Recursos do aplicativo**.  

    <img width="500px" alt="TDP messaging extension" src="~/assets/images/tdp/tdp-me.png"/>

1. Selecione **Extensões de mensagens dos** recursos do **aplicativo.** Uma janela pop-up aparece para configurar a extensão de mensagens.
    
   <img width="500px" alt="TDP messaging extension set up" src="~/assets/images/tdp/tdp-app-me.png"/>

1. Selecione **um bot de extensão de mensagem** na listada em ID de **extensões de mensagem** e selecione **Salvar**.

    <img width="500px" alt="TDP messaging extension bot" src="~/assets/images/tdp/tdp-me-bot.png"/>

1. Selecione **Adicionar um comando**. Uma janela pop-up parece adicionar comando.

    <img width="500px" alt="TDP messaging extension command" src="~/assets/images/tdp/tdp-me-add-command.png"/>

1. Selecione **pesquisar com base no** comando de pesquisa e insira campos de comando.

    <img width="500px" alt="TDP messaging extension search command" src="~/assets/images/tdp/tdp-me-search-command.png"/>

1. Insira campos de parâmetro e selecione **Salvar**.

    <img width="500px" alt="TDP messaging extension search parameter" src="~/assets/images/tdp/tdp-me-search-parameter.png"/>

---


### <a name="create-a-search-command-manually"></a>Criar um comando de pesquisa manualmente 

Para adicionar manualmente o comando de pesquisa de extensão de mensagens ao manifesto do aplicativo, adicione os seguintes parâmetros à `composeExtension.commands` sua matriz de objetos:

| Nome da propriedade | Objetivo | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | Essa propriedade é uma ID exclusiva que você atribui ao comando de pesquisa. A solicitação do usuário inclui essa ID. | Sim | 1.0 |
| `title` | Essa propriedade é um nome de comando. Esse valor aparece na interface do usuário (interface do usuário). | Sim | 1.0 |
| `description` | Essa propriedade é um texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Essa propriedade deve ser `query` um . | Não | 1.4 |
|`initialRun` | Se essa propriedade for definida como **true**, ele indicará que esse comando deve ser executado assim que o usuário selecionar esse comando na interface do usuário. | Não | 1.0 |
| `context` | Essa propriedade é uma matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível. Os valores possíveis são `message`, `compose` ou `commandBox`. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Você deve adicionar os detalhes do parâmetro de pesquisa, que define o texto visível para o usuário no Teams cliente.

| Nome da propriedade | Objetivo | É necessário? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Essa propriedade define uma lista estática de parâmetros para o comando. | Não | 1.0 |
| `parameter.name` | Essa propriedade descreve o nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Esta propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Essa propriedade é um título ou rótulo de parâmetro fácil de usar. | Sim | 1.0 |
| `parameter.inputType` | Essa propriedade é definida como o tipo de entrada necessária. Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` . O padrão é definido como `text` . | Não | 1.4 |

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

| Exemplo de nome           | Descrição | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams ação de extensão de mensagens| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams de extensão de mensagens   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Responder aos comandos de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

