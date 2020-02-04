---
title: Definir comandos de pesquisa de extensão de mensagens
author: clearab
description: Definir comandos de pesquisa de extensão de mensagens para os aplicativos do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: b6837fb8a131d8ce3e2bbd0c51c2861dbffda2bc
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672762"
---
# <a name="define-messaging-extension-search-commands"></a>Definir comandos de pesquisa de extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Os comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados da pesquisa em uma mensagem na forma de um cartão.

## <a name="choose-messaging-extension-invoke-locations"></a>Escolher locais de invocação de mensagens

A primeira coisa que você precisa decidir é onde o comando de pesquisa pode ser acionado (ou mais especificamente, *invocado*) a partir do. O comando de pesquisa pode ser chamado a partir de um ou dos dois locais a seguir:

* Os botões na parte inferior da área de redação da mensagem
* Por @mentioning na caixa comando

Quando invocado da área de mensagem de composição, o usuário terá a opção de enviar os resultados para a conversa. Quando invocado na caixa comando, o usuário pode interagir com o cartão resultante ou copiá-lo para uso em qualquer lugar.

## <a name="add-the-command-to-your-app-manifest"></a>Adicione o comando ao manifesto do aplicativo

Agora que você decidiu como os usuários irão interagir com seu comando de pesquisa, é hora de adicioná-lo ao manifesto do seu aplicativo. Para fazer isso, você adicionará um `composeExtension` novo objeto ao nível superior de seu aplicativo JSON de manifesto. Você pode fazer isso com a ajuda do App Studio ou manualmente.

### <a name="create-a-command-using-app-studio"></a>Criar um comando usando o app Studio

As etapas a seguir supõem que você já tenha [criado uma extensão de mensagens](~/messaging-extensions/how-to/create-messaging-extension.md).

1. No cliente Microsoft Teams, abra o **app Studio** e selecione a guia **Editor de manifesto** .
2. Se você já criou seu pacote de aplicativos no app Studio, escolha-o na lista. Caso contrário, você pode importar um pacote de aplicativos existente.
3. Clique no botão **Adicionar** na seção comando.
4. Escolha **permitir que os usuários consultem o serviço para obter informações e insiram isso em uma mensagem**.
5. Adicione uma **ID de comando** e um **título**.
6. Selecione onde você deseja que seu comando de pesquisa seja disparado. Selecionar a **mensagem** não altera atualmente o comportamento do seu comando de pesquisa.
7. Adicione o parâmetro de pesquisa.
8. Clique em Salvar.

### <a name="manually-create-a-command"></a>Criar um comando manualmente

Para adicionar manualmente seu comando de pesquisa de extensão de mensagens ao manifesto do seu aplicativo, você precisará adicionar os parâmetros `composeExtension.commands` de acompanhamento à sua matriz de objetos.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `id` | ID exclusiva que você atribui a este comando. A solicitação do usuário incluirá essa ID. | Sim | 1.0 |
| `title` | Nome do comando. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `description` | Texto de ajuda que indica o que esse comando faz. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `type` | Deve ser `query` | Não | 1.4 |
|`initialRun` | Se definido como **true**, indica que este comando deve ser executado assim que o usuário escolhe este comando na interface do usuário. | Não | 1.0 |
| `context` | Matriz opcional de valores que define o contexto no qual a ação de pesquisa está disponível. Os valores possíveis `message`são `compose`,, `commandBox`ou. O padrão é `["compose", "commandBox"]`. | Não | 1,5 |

Você também precisará adicionar os detalhes do parâmetro Search, que definirá o texto visível para o usuário no cliente Teams.

| Nome da propriedade | Finalidade | Obrigatório? | Versão mínima do manifesto |
|---|---|---|---|
| `parameters` | Lista estática de parâmetros para o comando. | Não | 1.0 |
| `parameter.name` | O nome do parâmetro. Isso é enviado para o serviço na solicitação do usuário. | Sim | 1.0 |
| `parameter.description` | Descreve os fins deste parâmetro ou o exemplo do valor que deve ser fornecido. Esse valor é exibido na interface do usuário. | Sim | 1.0 |
| `parameter.title` | Título ou rótulo curto de parâmetro amigável. | Sim | 1.0 |
| `parameter.inputType` | Defina como o tipo de entrada obrigatória. Os valores possíveis `text`incluem `textarea`, `number` `date` `time`,,, `toggle`. O padrão é definido como`text` | Não | 1.4 |

#### <a name="app-manifest-example"></a>Exemplo de manifesto de aplicativo

Veja a seguir um exemplo de um `composeExtensions` objeto que define um comando de pesquisa. Não é um exemplo de manifesto completo, para o esquema de manifesto de aplicativo completo, consulte: [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

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

Agora que você adicionou o comando de pesquisa, precisará [lidar com a solicitação de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]