---
title: Início rápido do Live Share
description: Neste módulo, saiba como experimentar rapidamente o exemplo de Rolo de Dados
ms.topic: concept
ms.localizationpriority: high
ms.author: stevenic
ms.openlocfilehash: 98150265f0c5876e726710cacc873db2ac23e9ee
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66484583"
---
---

# <a name="quick-start-guide"></a>Guia de início rápido

Introdução ao SDK do Live Share usando o exemplo de Rolo de Dados é uma evolução do [Início rápido do Fluid Framework](https://fluidframework.com/docs/start/quick-start/) e foi projetado para executar rapidamente um [exemplo de Rolo de Dados](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller) baseado em SDK do Live Share no host local do computador.

:::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="Exemplo de Rolo de Dados":::

> [!NOTE]
> Este guia explica como usar o Live Share localmente em um navegador. Para saber mais sobre como usar o SDK em uma reunião do Teams, experimente nosso [Tutorial do Agile Poker](../sbs-teams-live-share.yml).

## <a name="set-up-your-development-environment"></a>Defina seu ambiente de desenvolvimento

Para começar, instale:

* [Node.js](https://nodejs.org/en/download): O SDK do Live Share dá suporte ao Node.js LTS versões 12.17 e posteriores.
* [Versão mais recente do Visual Studio Code](https://code.visualstudio.com/).
* [Git](https://git-scm.com/downloads)

## <a name="build-and-run-the-dice-roller-app"></a>Compile e execute o aplicativo Rolo de Dados

1. Vá para o aplicativo de exemplo [Rolo de Dados](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller).

1. Clone o repositório [SDK do Live Share](https://github.com/microsoft/live-share-sdk) para testar o aplicativo de exemplo:

    ```bash
    $ git clone https://github.com/microsoft/live-share-sdk.git
    ```

1. Execute o comando a seguir para ir para a pasta de aplicativo de exemplo do Rolo de Dados:

   ```bash
    $ cd live-share-sdk\samples\01.dice-roller
   ```

1. Execute o seguinte comando para instalar o pacote de dependência:

    ```bash
    $ npm install
    ```

1. Execute o seguinte comando para iniciar o cliente e o servidor local:

   ```bash
   $ npm start
   ```
  
     Uma nova guia do navegador abre uma url `http://localhost:8080` e o jogo de Rolo de Dados é exibido.

1. Copie a URL completa no navegador, incluindo a ID e cole a URL em uma nova janela ou em um navegador diferente.

   Um segundo cliente para seu aplicativo de rolo de dados é aberto.

1. Abra as duas janelas e selecione o botão **Rolar** em uma janela. O estado dos dados muda em ambos os clientes.

    :::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="Várias guias do Rolo de Dados":::
  
   **Parabéns** você aprendeu a criar e executar um aplicativo usando o SDK do Live Share.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Tutorial de Rolo de Dados](teams-live-share-tutorial.md)

## <a name="see-also"></a>Confira também

* [Repositório do GitHub](https://github.com/microsoft/live-share-sdk)
* [Documentos de referência do SDK do Live Share](/javascript/api/@microsoft/live-share/)
* [Documentos de referência do SDK do Live Share Media](/javascript/api/@microsoft/live-share-media/)
* [Recursos do Live Share ](teams-live-share-capabilities.md)
* [Perguntas frequentes do Live Share](teams-live-share-faq.md)
* [Aplicativos do Teams em reuniões](teams-apps-in-meetings.md)
