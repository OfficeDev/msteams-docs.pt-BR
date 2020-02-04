---
title: Criar uma extensão de mensagens
author: clearab
description: Como criar uma extensão de mensagens para um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 5d70ee361bdf32024f3cbdb56505a8aa410e7db0
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672953"
---
# <a name="create-a-messaging-extension-in-microsoft-teams"></a>Criar uma extensão de mensagens no Microsoft Teams

Em um nível alto, você precisará concluir as etapas a seguir para criar uma extensão de mensagens.

1. Preparar seu ambiente de desenvolvimento
2. Criar e implantar seu serviço Web (ao desenvolver o uso de um serviço de encapsulamento como o ngrok para executá-lo localmente)
3. Registrar seu serviço Web com a estrutura de bot
4. Criar seu pacote de aplicativos
5. Carregar seu pacote no Microsoft Teams

A criação do seu serviço Web, a criação do pacote de aplicativos e o registro do serviço Web com a estrutura de bot podem ser feitas em qualquer ordem. Como essas três partes estão desentrelaçadas, não importa a ordem em que você precisará retornar para atualizar as outras. Seu registro precisa do ponto de extremidade de mensagens do seu serviço Web implantado e seu serviço Web precisa da ID e senha criadas a partir do seu registro. O manifesto do aplicativo também precisa dessa ID para conectar o Microsoft Teams ao seu serviço Web.

À medida que você está criando sua extensão de mensagens, você vai migrar regularmente entre alterar o manifesto do aplicativo e implantar o código no seu serviço Web. Ao trabalhar com o manifesto do aplicativo, tenha em mente que você pode manipular manualmente o arquivo JSON ou fazer alterações através do App Studio. De qualquer forma, você precisará implantar (carregar) seu aplicativo no Teams quando fizer uma alteração no manifesto, mas não é necessário fazê-lo ao implantar as alterações no serviço Web.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Criar seu serviço Web

O coração de sua extensão de mensagens é seu serviço Web. Ele definirá uma única rota, geralmente `/api/messages`, para receber todas as solicitações. Se você estiver começando a partir do zero, terá algumas opções para escolher.

* Use um de nossos tutoriais de [QuickStartES](#learn-more) que orientarão você durante a criação do seu serviço Web.
* Escolha uma das amostras de extensão de mensagens disponíveis no [repositório de exemplo da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples) para começar.
* Se você estiver usando o JavaScript, use o [gerador Yeoman para o Microsoft Teams](https://github.com/OfficeDev/generator-teams) para estruturar seu aplicativo do Teams, incluindo o serviço Web.
* Crie seu serviço Web do zero. Você pode optar por adicionar o SDK da estrutura de bot para o seu idioma ou pode trabalhar diretamente com as cargas JSON.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrar seu serviço Web com a estrutura de bot

As extensões de mensagens aproveitam o esquema de mensagens da estrutura de bot e o protocolo de comunicação seguro; Se você ainda não tiver um, você precisará registrar seu serviço Web na estrutura de bot. A ID do aplicativo da Microsoft (consultaremos isso como o seu ID de bot de dentro do teams para identificá-lo a partir de outras IDs de aplicativos que você pode estar trabalhando) e o ponto de extremidade de mensagens que seu registrador com a estrutura de bot será usado em sua extensão de mensagens para receber e responder a req uests. Se você estiver usando um registro existente, certifique-se [de habilitar o canal do Microsoft Teams](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0).

Se você seguir um dos QuickStarts ou iniciar a partir de um dos exemplos disponíveis, será guiado através do registro do seu serviço Web. Se quiser registrar manualmente seu serviço, você terá três opções para fazer isso. Se você optar por se registrar sem usar uma assinatura do Azure, não será possível aproveitar o fluxo de autenticação OAuth simplificado fornecido pela estrutura do bot. Você poderá migrar seu registro para o Azure após a criação.

* Se você tiver uma assinatura do Azure (ou quiser criar uma nova), poderá registrar o serviço Web manualmente usando o portal do Azure. Crie um recurso "registro de canais de bot". Você pode escolher a camada de preços gratuita, uma vez que as mensagens do Microsoft Teams não contam com relação ao total de mensagens permitidas por mês.
* Se não quiser usar uma assinatura do Azure, você pode usar o portal de [registro herdado](https://dev.botframework.com/bots/new).
* O app Studio também pode ajudá-lo a registrar o serviço Web (bot). Os serviços Web registrados por meio do App Studio não são registrados no Azure. Você pode usar o [portal herdado](https://dev.botframework.com/bots) para exibir, gerenciar e migrar seus registros.

## <a name="create-your-app-manifest"></a>Criar o manifesto do aplicativo

Você pode usar o app Studio para ajudá-lo a criar o manifesto do aplicativo ou criá-lo manualmente.

### <a name="create-your-app-manifest-using-app-studio"></a>Criar seu manifesto de aplicativo usando o app Studio

Você pode usar o aplicativo App Studio no cliente Microsoft Teams para ajudar a criar seu manifesto de aplicativo.

1. No cliente do Microsoft Teams, abra o app Studio no menu **de excedentes** no trilho esquerdo de navegação. Se ainda não estiver instalado, você pode fazê-lo pesquisando.
2. Na guia **Editor de manifesto** , selecione **criar um novo aplicativo** (ou se você estiver adicionando uma extensão de mensagens a um aplicativo existente, poderá importar seu pacote de aplicativos)
3. Adicione os detalhes do aplicativo (Confira [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter descrições completas de cada campo).
4. Na guia **extensões de mensagens** , clique no botão **Configurar** .
5. Você pode criar um novo serviço Web (bot) para que sua extensão de mensagens seja usada, ou se já tiver registrado um SELECT/Add-lo aqui.
6. Se necessário, atualize seu endereço de ponto de extremidade de bot para apontar para o bot. Ele deve ser semelhante `https://someplace.com/api/messages`.
7. O botão **Adicionar** na seção **comando** orientará você na adição de comandos à extensão do sistema de mensagens. Consulte a seção [saiba mais](#learn-more) para obter links para mais informações sobre como adicionar comandos. Lembre-se de que você pode definir até 10 comandos para sua extensão de mensagens.
8. A seção **manipuladores de mensagens** permite que você adicione um domínio para o qual as mensagens serão disparadas. Confira [link Unfurling](~/messaging-extensions/how-to/link-unfurling.md) para obter mais informações.

Na guia **concluir => teste e distribuição** , você pode **baixar** seu pacote de aplicativos (que inclui o manifesto do aplicativo, bem como seus ícones de aplicativo) ou **instalar** o pacote.

### <a name="create-your-app-manifest-manually"></a>Criar o manifesto do aplicativo manualmente

Como com bots e guias, você atualiza o [manifesto do aplicativo](~/resources/schema/manifest-schema.md#composeextensions) de seu aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades controlam como sua extensão de mensagens aparece e se comporta no cliente Microsoft Teams. As extensões de mensagens têm suporte a partir da versão v 1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declarar sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior em seu manifesto de aplicativo `composeExtensions` com a propriedade. Você cria uma única extensão de mensagens para seu aplicativo, com até 10 comandos.

> [!NOTE]
> O manifesto se refere a extensões de `composeExtensions`mensagens como. Isso é para manter a compatibilidade com versões anteriores.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Finalidade | Obrigatório? |
|---|---|---|
| `botId` | A ID exclusiva do aplicativo da Microsoft para o bot, conforme registrado na estrutura do bot. Isso deve ser normalmente o mesmo que a ID do aplicativo de suas equipes gerais. | Sim |
| `canUpdateConfiguration` | Habilita o item de menu **configurações** . | Não |
| `commands` | Matriz de comandos que esta extensão de mensagens suporta. Você está limitado a 10 comandos. | Sim |

#### <a name="define-your-commands"></a>Definir seus comandos

Sua extensão de mensagens deve declarar um ou mais comandos, que definem onde seus usuários podem disparar sua extensão de mensagens e o tipo de interação. Consulte [saiba mais](#learn-more) para obter mais informações sobre os comandos de extensão de mensagens.

#### <a name="simple-manifest-example"></a>Exemplo de manifesto simples

O exemplo a seguir é um objeto de extensão de mensagem simples no manifesto de aplicativo com um comando de pesquisa. Este não é o arquivo de manifesto do aplicativo inteiro, apenas a parte específica para extensões de mensagens. Consulte [esquema de manifesto de aplicativo](~/resources/schema/manifest-schema.md) para obter um exemplo completo.

```json
...
"composeExtensions": [
  {
    "botId": "abcd1234-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "searchCmd",
        "description": "Search you ToDo's",
        "title": "Search",
        "initialRun": true,
        "parameters": [
          {
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }
        ]
      }
    ]
  }
]
...
```

## <a name="add-your-invoke-message-handlers"></a>Adicionar seus manipuladores de mensagens de chamada

Quando seus usuários disparam sua extensão de mensagens, você precisará lidar com a mensagem de chamada inicial, coletar algumas informações do usuário e, em seguida, processar essas informações e responder de forma adequada. Para fazer isso, primeiro você precisará decidir que tipo de comandos você deseja adicionar à sua extensão de mensagens e [adicionar comandos de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md) ou [Adicionar um comando de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md).

## <a name="next-steps"></a>Próximas etapas

* [Criar comandos de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Criar comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Link Unfurling](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Saiba mais

Experimente em um QuickStart:

* Início rápido para C #
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Início rápido para JavaScript
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Saiba mais sobre os conceitos de extensões de mensagens:

* [Entender os recursos do aplicativo Teams?](~/concepts/extensibility-points.md)
* [O que são extensões de mensagens?](~/messaging-extensions/what-are-messaging-extensions.md)
