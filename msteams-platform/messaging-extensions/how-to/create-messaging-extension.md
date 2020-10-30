---
title: Criar uma extensão de mensagens usando o app Studio
author: clearab
description: Saiba como criar uma extensão de mensagens do Microsoft Teams usando o app Studio.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: c3437457f7084d2d768af0f0db5208525c368682
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796180"
---
# <a name="create-a-messaging-extension-using-app-studio"></a>Criar uma extensão de mensagens usando o app Studio

> [!TIP]
> Procurando uma maneira mais rápida para iniciar? Crie uma [extensão de mensagens](../../build-your-first-app/build-messaging-extension.md) usando o Microsoft Teams Toolkit.

Em um nível alto, você precisará concluir as etapas a seguir para criar uma extensão de mensagens.

1. Preparar seu ambiente de desenvolvimento
2. Criar e implantar seu serviço Web (ao desenvolver o uso de um serviço de encapsulamento como o ngrok para executá-lo localmente)
3. Registrar seu serviço Web com a estrutura bot
4. Criar seu pacote de aplicativos
5. Carregar um pacote do aplicativo para o Microsoft Teams

A criação do seu serviço Web, a criação do pacote de aplicativos e o registro do serviço Web com a estrutura de bot podem ser feitas em qualquer ordem. Como essas três partes estão desentrelaçadas, não importa a ordem em que você precisará retornar para atualizar as outras. Seu registro precisa do ponto de extremidade de mensagens do seu serviço Web implantado e seu serviço Web precisa da ID e senha criadas a partir do seu registro. O manifesto do aplicativo também precisa dessa ID para conectar o Microsoft Teams ao seu serviço Web.

À medida que você está criando sua extensão de mensagens, você vai migrar regularmente entre alterar o manifesto do aplicativo e implantar o código no seu serviço Web. Ao trabalhar com o manifesto do aplicativo, tenha em mente que você pode manipular manualmente o arquivo JSON ou fazer alterações através do App Studio. De qualquer forma, você precisará implantar (carregar) seu aplicativo no Teams quando fizer uma alteração no manifesto, mas não é necessário fazê-lo ao implantar as alterações no serviço Web.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Criar seu serviço Web

O coração de sua extensão de mensagens é seu serviço Web. Ele definirá uma única rota, geralmente `/api/messages` , para receber todas as solicitações. Se você estiver começando a partir do zero, terá algumas opções para escolher.

* Use um de nossos tutoriais de [QuickStartES](#learn-more) que orientarão você durante a criação do seu serviço Web.
* Escolha uma das amostras de extensão de mensagens disponíveis no [repositório de exemplo da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples) para começar.
* Se você estiver usando o JavaScript, use o [gerador Yeoman para o Microsoft Teams](https://github.com/OfficeDev/generator-teams) para estruturar seu aplicativo do Teams, incluindo o serviço Web.
* Criar seu serviço Web a partir do zero. Você pode optar por adicionar o SDK do verificador de bot para o seu idioma ou trabalhar diretamente com as cargas JSON.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrar seu serviço Web com a estrutura bot

As extensões de mensagens aproveitam o esquema de mensagens da estrutura de bot e o protocolo de comunicação seguro; Se você ainda não tiver um, você precisará registrar seu serviço Web na estrutura de bot. A ID do aplicativo da Microsoft (vamos nos referir a isso como o seu ID de bot de dentro do teams para identificá-lo a partir de outras IDs de aplicativos que você pode estar trabalhando) e o ponto de extremidade de mensagens que seu registrador com a estrutura de bot será usado em sua extensão de mensagens para receber e responder a solicitações. Se você estiver usando um registro existente, certifique-se [de habilitar o canal do Microsoft Teams](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true).

Se você seguir um dos QuickStarts ou iniciar a partir de um dos exemplos disponíveis, será guiado através do registro do seu serviço Web. Se quiser registrar manualmente seu serviço, você terá três opções para fazer isso. Se você optar por se registrar sem usar uma assinatura do Azure, não será possível aproveitar o fluxo de autenticação OAuth simplificado fornecido pela estrutura do bot. Você poderá migrar seu registro para o Azure após a criação.

* Se você tiver uma assinatura do Azure (ou quiser criar uma nova), poderá registrar o serviço Web manualmente usando o portal do Azure. Crie um recurso "registro de canais de bot". Você pode escolher a camada de preços gratuita, uma vez que as mensagens do Microsoft Teams não contam com relação ao total de mensagens permitidas por mês.
* Se não quiser usar uma assinatura do Azure, você pode usar o portal de [registro herdado](https://dev.botframework.com/bots/new).
* O app Studio também pode ajudá-lo a registrar o serviço Web (bot). Os serviços Web registrados por meio do App Studio não são registrados no Azure. Você pode usar o [portal herdado](https://dev.botframework.com/bots) para exibir, gerenciar e migrar seus registros.

## <a name="create-your-app-manifest"></a>Criar o manifesto do aplicativo

Você pode usar o aplicativo Studio para ajudá-lo a criar seu manifesto de aplicativo ou a criá-lo manualmente.

### <a name="create-your-app-manifest-using-app-studio"></a>Criar seu manifesto de aplicativo usando o app Studio

Você pode usar o aplicativo App Studio no cliente Microsoft Teams para ajudar a criar seu manifesto de aplicativo.

1. No cliente do Teams, abra o aplicativo Studio no menu de estouro **...** no trilho de navegação à esquerda. Se ainda não estiver instalado, você pode fazê-lo pesquisando.
2. Na guia **Editor de manifesto** , selecione **criar um novo aplicativo** (ou se você estiver adicionando uma extensão de mensagens a um aplicativo existente, poderá importar seu pacote de aplicativos)
3. Adicione os detalhes do aplicativo (Confira [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter descrições completas de cada campo).
4. Na guia **extensões de mensagens** , clique no botão **Configurar** .
5. Você pode criar um novo serviço Web (bot) para que sua extensão de mensagens seja usada, ou se já tiver registrado um SELECT/Add-lo aqui.
6. Se necessário, atualize o endereço do ponto de extremidade do bot para apontar para o seu bot. Ela deve ser similar a `https://someplace.com/api/messages`.
7. O botão **Adicionar** na seção **comando** orientará você na adição de comandos à extensão do sistema de mensagens. Consulte a seção [saiba mais](#learn-more) para obter links para mais informações sobre como adicionar comandos. Lembre-se de que você pode definir até 10 comandos para sua extensão de mensagens.
8. A seção **manipuladores de mensagens** permite que você adicione um domínio para o qual as mensagens serão disparadas. Confira [link Unfurling](~/messaging-extensions/how-to/link-unfurling.md) para obter mais informações.

Na guia **concluir => teste e distribuição** , você pode **baixar** seu pacote de aplicativos (que inclui o manifesto do aplicativo, bem como seus ícones de aplicativo) ou **instalar** o pacote.

### <a name="create-your-app-manifest-manually"></a>Criar o manifesto do aplicativo manualmente

Como com bots e guias, você atualiza o [manifesto do aplicativo](~/resources/schema/manifest-schema.md#composeextensions) de seu aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades controlam como sua extensão de mensagens aparece e se comporta no cliente Microsoft Teams. As extensões de mensagens têm suporte a partir da versão v 1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declarar sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior em seu manifesto de aplicativo com a `composeExtensions` propriedade. Você cria uma única extensão de mensagens para seu aplicativo, com até 10 comandos.

> [!NOTE]
> O manifesto se refere a extensões de mensagens como `composeExtensions` . Isso é para manter a compatibilidade com versões anteriores.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Finalidade | Obrigatório? |
|---|---|---|
| `botId` | O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso deve ser normalmente o mesmo que a ID do aplicativo de suas equipes gerais. | Sim |
| `canUpdateConfiguration` | Habilita o item de menu **configurações** . | Não |
| `commands` | Matriz de comandos que esta extensão de mensagens suporta. Você está limitado a 10 comandos. | Sim |

#### <a name="define-your-commands"></a>Definir seus comandos

Sua extensão de mensagens deve declarar um ou mais comandos, que definem onde seus usuários podem disparar sua extensão de mensagens e o tipo de interação. Consulte [saiba mais](#learn-more) para obter mais informações sobre os comandos de extensão de mensagens.

#### <a name="simple-manifest-example"></a>Exemplo de manifesto simples

O exemplo a seguir é um objeto de extensão de mensagem simples no manifesto de aplicativo com um comando de pesquisa. Esse não é o arquivo de manifesto completo do aplicativo, apenas a parte específica das extensões de mensagens. Consulte [esquema de manifesto de aplicativo](~/resources/schema/manifest-schema.md) para obter um exemplo completo.

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

## <a name="messaging-extensions-in-teams-meetings"></a>Extensões de mensagens em reuniões do teams

Após a reunião começar, os participantes do teams podem interagir diretamente com sua extensão de mensagens durante uma chamada ativa. Considere o seguinte ao criar sua extensão de mensagens na reunião:

1. **Localização** Sua extensão de mensagens pode ser invocada a partir da área de mensagem de composição, da caixa de comando ou @mentioned no chat da reunião.

1. **Metadados** . Quando sua extensão de mensagens é invocada, ela pode identificar o usuário e o locatário de `userId` e `tenantId` . O `meetingId` pode ser encontrado como parte do objeto `channelData`. Seu aplicativo pode usar o `userId` e o `meetingId`  para a `GetParticipant` solicitação de API para recuperar funções de usuário.

1. **Tipo de comando** . Se sua extensão de mensagem usa [comandos baseados em ação](../../messaging-extensions/what-are-messaging-extensions.md#action-commands), ela deve seguir as guias autenticação de [logon único](../../tabs/how-to/authentication/auth-aad-sso.md) .

1. **Experiência do usuário** . Sua extensão de mensagens deve ter a aparência e se comportar da mesma forma que faria fora de uma reunião.

## <a name="next-steps"></a>Próximas etapas

* [Criar comandos de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Criar comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Desenrolamento de link](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Saiba mais

Experimente em um QuickStart:

* Início rápido para C #
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Início rápido para JavaScript
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Saiba mais sobre conceitos de desenvolvimento do teams:

* [Entender os recursos do aplicativo Teams](../../concepts/capabilities-overview.md)
* [O que são extensões de mensagens?](~/messaging-extensions/what-are-messaging-extensions.md)
