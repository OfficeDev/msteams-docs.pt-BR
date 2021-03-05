---
title: Definir comandos de pesquisa de extensão de mensagens
author: clearab
description: Definir comandos de pesquisa de extensão de mensagens para aplicativos do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 18bac3049fec8fead168c12f2832bfbbb72cf609
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449266"
---
# <a name="define-messaging-extension-search-commands"></a>Definir comandos de pesquisa de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão.

> [!NOTE]
> O limite de tamanho do cartão de resultado é de 28 KB. O cartão não será enviado se seu tamanho exceder 28 KB. 

## <a name="choose-messaging-extension-invoke-locations"></a>Escolher locais de invocação de extensão de mensagens

A primeira coisa que você precisa decidir é de onde o comando de pesquisa pode ser acionado (ou especificamente, *invocado*). Seu comando de pesquisa pode ser invocado de um ou ambos os seguintes locais:

* Os botões na parte inferior da área de mensagem de redação
* Por @mentioning na caixa de comando

Quando invocado da área de mensagem de redação, o usuário terá a opção de enviar os resultados para a conversa. Quando invocado da caixa de comando, o usuário pode interagir com o cartão resultante ou copiá-lo para uso em outro lugar.

## <a name="add-the-command-to-your-app-manifest"></a>Adicionar o comando ao manifesto do aplicativo

Agora que você decidiu como os usuários interagirão com seu comando de pesquisa, é hora de adicioná-lo ao manifesto do aplicativo. Para fazer isso, você adicionará um novo objeto ao nível superior do JSON do `composeExtension` manifesto do aplicativo. Você pode fazer isso com a ajuda do App Studio ou manualmente.

### <a name="create-a-command-using-app-studio"></a>Criar um comando usando o App Studio

O pré-requisito para criar um comando de pesquisa é que você já deve criar uma extensão de mensagens. Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**Para criar um comando de pesquisa**

1. No cliente do Microsoft Teams, abra **o App Studio** e selecione a guia Editor **de** manifesto.
1. Se você já criou um pacote de aplicativos no **App Studio**, escolha-o na lista. Se você não tiver criado um pacote de aplicativos, importe um existente.
1. Depois de importar um pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**.
1. Selecione **Adicionar** na seção **Comando** na página extensões de mensagens.
1. Escolha **Permitir que os usuários consultem seu serviço para obter informações e insira-os em uma mensagem**.
1. Adicione uma **ID de Comando** e um **Título.**
1. Selecione o local de onde o comando de pesquisa deve ser acionado. Selecionar **mensagem** no momento não altera o comportamento do comando de pesquisa.
1. Adicione o parâmetro de pesquisa e selecione **Salvar**.
 
### <a name="manually-create-a-command"></a>Criar manualmente um comando

Para adicionar manualmente o comando de pesquisa de extensão de mensagens ao manifesto do aplicativo, você precisará adicionar os seguintes parâmetros à `composeExtension.commands` sua matriz de objetos.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a esse comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `description` | Texto de ajuda que indica o que esse comando faz. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `type` | Deve ser `query` | Não | 1.4 |
|`initialRun` | Se definido como **true**, indica que esse comando deve ser executado assim que o usuário escolher esse comando na interface do usuário. | Não | 1.0 |
| `context` | Matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível. Os valores possíveis `message` são `compose` , ou `commandBox` . O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Você também precisará adicionar os detalhes do parâmetro de pesquisa, que definirá o texto visível para seu usuário no cliente do Teams.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Lista estática de parâmetros para o comando. | Não | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado ao seu serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve as finalidades desse parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor aparece na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo de parâmetro fácil de usar curto. | Sim | 1.0 |
| `parameter.inputType` | De acordo com o tipo de entrada necessário. Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` . Padrão é definido como `text` | Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto do aplicativo

Veja a seguir um exemplo de `composeExtensions` um objeto que define um comando de pesquisa. Não é um exemplo do manifesto completo, para o esquema de manifesto completo do aplicativo, consulte: [Esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

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

## <a name="next-steps"></a>Próximas etapas

Agora que você adicionou o comando de pesquisa, precisará lidar [com a solicitação de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
