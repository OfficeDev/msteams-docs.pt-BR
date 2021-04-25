---
title: Extensões de mensagens
author: clearab
description: Uma visão geral das extensões de mensagens na plataforma do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a6d4f478541724cd2643068d9e1615a15b03fd13
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995880"
---
# <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários interajam com seu serviço Web por meio de botões e formulários no cliente do Microsoft Teams. Eles podem pesquisar ou iniciar ações em um sistema externo a partir da área de mensagem de composição, da caixa de comando ou diretamente de uma mensagem. Você pode enviar de volta os resultados dessa interação para o cliente do Microsoft Teams na forma de um cartão ricamente formatado. Este documento fornece uma visão geral da extensão de mensagens, tarefas executadas em diferentes cenários, trabalho de extensão de mensagens, comandos de ação e pesquisa e desfraldamento de link.

A imagem a seguir exibe os locais de onde as extensões de mensagens são invocadas:

![locais de invocação de extensão de mensagens](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="scenarios-where-messaging-extensions-are-used"></a>Cenários em que extensões de mensagens são usadas

| Cenário | Exemplo |
|:-----------------|:-----------------|
|Você deseja que algum sistema externo faça uma ação e o resultado da ação seja enviado de volta para sua conversa.|Reserve um recurso e permita que o canal saiba o intervalo de tempo reservado.|
|Você deseja encontrar algo em um sistema externo e compartilhar os resultados com a conversa.|Pesquise um item de trabalho no Azure DevOps e compartilhe-o com o grupo como um Cartão Adaptável.|
|Você deseja concluir uma tarefa complexa envolvendo várias etapas ou muitas informações em um sistema externo e compartilhar os resultados com uma conversa.|Crie um bug em seu sistema de controle com base em uma mensagem do Teams, atribua esse bug a Bob e envie um cartão para o thread de conversa com os detalhes do bug.|

## <a name="understand-how-messaging-extensions-work"></a>Entender como funcionam as extensões de mensagens

Uma extensão de mensagens consiste em um serviço Web que você hospeda e um manifesto de aplicativo, que define de onde seu serviço Web é invocado no cliente do Microsoft Teams. O serviço Web aproveita o esquema de mensagens da Estrutura de Bot e o protocolo de comunicação segura, portanto, você deve registrar seu serviço Web como um bot na Estrutura de Bots. 

> [!NOTE]
> Embora você possa criar o serviço Web manualmente, use [o SDK da Estrutura de Bots](https://github.com/microsoft/botframework) para trabalhar com o protocolo.

No manifesto do aplicativo do Microsoft Teams, uma única extensão de mensagens é definida com até dez comandos diferentes. Cada comando define um tipo, como ação ou pesquisa e os locais no cliente de onde ele é invocado. Os locais de invocação são área de composição de mensagem, barra de comandos e mensagem. Ao chamar, o serviço Web recebe uma mensagem HTTPS com uma carga JSON, incluindo todas as informações relevantes. Responda com uma carga JSON, permitindo que o cliente do Teams saiba a próxima interação a ser habilitada. 

## <a name="types-of-messaging-extension-commands"></a>Tipos de comandos de extensão de mensagens

Há dois tipos de comandos de extensão de mensagens, comando de ação e comando de pesquisa. O tipo de comando de extensão de mensagens define os elementos da interface do usuário e os fluxos de interação disponíveis para seu serviço Web. Algumas interações, como autenticação e configuração, estão disponíveis para ambos os tipos de comandos.

### <a name="action-commands"></a>Comandos de ação

Comandos de ação são usados para apresentar aos usuários um pop-up modal para coletar ou exibir informações. Quando o usuário envia o formulário, o serviço Web responde inserindo uma mensagem diretamente na conversa ou inserindo uma mensagem na área de mensagem de redação. Depois disso, o usuário pode enviar a mensagem. Você pode encadeá-los para fluxos de trabalho mais complexos.

Os comandos de ação são disparados da área de mensagem de composição, da caixa de comando ou de uma mensagem. Quando o comando é invocado de uma mensagem, a carga JSON inicial enviada para o bot inclui a mensagem inteira de que ele foi invocado. A imagem a seguir exibe o módulo de tarefa de comando de ação de extensão de mensagens: módulo de tarefa de ação de ![ extensão de mensagens](~/assets/images/task-module.png)

### <a name="search-commands"></a>Comandos de pesquisa

Os comandos de pesquisa permitem que os usuários pesquisem informações em um sistema externo manualmente por meio de uma caixa de pesquisa ou colar um link a um domínio monitorado na área de mensagem de composição e inserir os resultados da pesquisa em uma mensagem. No fluxo de comando de pesquisa mais básico, a mensagem de invocação inicial inclui a cadeia de caracteres de pesquisa que o usuário enviou. Você responde com uma lista de visualizações de cartões e cartões. O cliente do Teams renderiza uma lista de visualizações de cartão para o usuário. Quando o usuário seleciona um cartão na lista, o cartão de tamanho completo é inserido na área de mensagem de composição.

Os cartões são disparados da área de mensagem de redação ou da caixa de comando e não disparados de uma mensagem. Eles não podem ser disparados de uma mensagem.
A imagem a seguir exibe o módulo de tarefa de comando de pesquisa de extensão de mensagens:

![comando de pesquisa de extensão de mensagens](~/assets/images/search-extension.png)

> [!NOTE]
> Para obter mais informações sobre cartões, consulte [o que são cartões](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Desenrolamento de link

Um serviço Web é chamado quando uma URL é colar na área de mensagem de redação. Essa funcionalidade é conhecida como desarmamento de link. Você pode se inscrever para receber uma invocação quando URLs que contêm um determinado domínio são colar na área de mensagem de redação. Seu serviço Web pode "desafraldar" a URL em um cartão detalhado, fornecendo mais informações do que o cartão de visualização do site padrão. Você pode adicionar botões para permitir que os usuários tomem medidas imediatamente sem sair do cliente do Microsoft Teams.
As imagens a seguir exibem o recurso de desfralização de link quando um link é passado na extensão de mensagens:
 
![link unfurl](../assets/images/messaging-extension/unfurl-link.png)

![link desfraldamento](../assets/images/messaging-extension/link-unfurl.gif)

## <a name="code-sample"></a>Exemplo de código

| **Exemplo de nome** | **Descrição** | **.NET** | **Node.js** | **Python** |
|------------|-------------|----------------|------------|
| Extensão de mensagens com comandos baseados em ação | Este exemplo ilustra como criar uma extensão de mensagens baseada em ação. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Extensão de mensagens com comandos baseados em pesquisa | Este exemplo ilustra como criar uma Extensão de Mensagens baseada em Pesquisa. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Criar uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)


## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Definir comando de extensão de mensagens de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)

> [!div class="nextstepaction"]
> [Definir o comando de extensão de mensagens de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
