---
title: Criar uma extensão de mensagem usando o App Studio
author: surbhigupta
description: Saiba como criar uma extensão Microsoft Teams de mensagens usando o App Studio.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 61bfed969b981bd5000bdb6eca0bbd77196e8086
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155148"
---
# <a name="create-a-messaging-extension-using-app-studio"></a>Criar uma extensão de mensagem usando o App Studio

> [!TIP]
> Procurando uma maneira mais rápida de começar? Crie uma [extensão de mensagens](../build-your-first-app/build-messaging-extension.md) usando a Microsoft Teams Toolkit.

Em um nível alto, você precisará concluir as etapas a seguir para criar uma extensão de mensagens.

1. Preparar seu ambiente de desenvolvimento
2. Crie e implante seu serviço Web (ao desenvolver use um serviço de tunelamento como ngrok para ser executado localmente)
3. Registrar seu serviço Web com a estrutura bot
4. Criar um pacote do aplicativo
5. Carregar um pacote do aplicativo para o Microsoft Teams

Criar seu serviço Web, criar seu pacote de aplicativos e registrar seu serviço Web com a Estrutura de Bot pode ser feito em qualquer ordem. Como essas três partes estão tão entrelaçadas, não importa qual ordem você as faça, você precisará retornar para atualizar as outras. Seu registro precisa do ponto de extremidade de mensagens do seu serviço Web implantado, e seu serviço Web precisa da ID e da senha criadas a partir do seu registro. O manifesto do aplicativo também precisa dessa ID para se conectar Teams seu serviço Web.

À medida que você estiver criando sua extensão de mensagens, você estará se movendo regularmente entre alterar o manifesto do aplicativo e implantar código no seu serviço Web. Ao trabalhar com o manifesto do aplicativo, lembre-se de que você pode manipular manualmente o arquivo JSON ou fazer alterações por meio do App Studio. De qualquer forma, você precisará implantar (carregar) seu aplicativo no Teams quando fizer uma alteração no manifesto, mas não é necessário fazer isso ao implantar alterações no seu serviço Web.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Criar seu serviço Web

O centro de sua extensão de mensagens é seu serviço Web. Ele definirá uma única rota, normalmente `/api/messages` , para receber todas as solicitações. Se você estiver começando do zero, você tem algumas opções para escolher.

* Use um dos nossos [tutoriais de](#learn-more) início rápido que o guiarão pela criação do seu serviço Web.
* Escolha um dos exemplos de extensão de mensagens disponíveis no repositório de exemplo da Estrutura de [Bots](https://github.com/Microsoft/BotBuilder-Samples) para começar.
* Se você estiver usando JavaScript, use o gerador [Yeoman](https://github.com/OfficeDev/generator-teams) para Microsoft Teams para aplicação Teams aplicativo, incluindo seu serviço Web.
* Criar seu serviço Web a partir do zero. Você pode optar por adicionar o SDK do verificador de bot para o seu idioma ou trabalhar diretamente com as cargas JSON.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrar seu serviço Web com a estrutura bot

As extensões de mensagens aproveitam o esquema de mensagens da Estrutura de Bot e o protocolo de comunicação seguro; se você ainda não tiver um, precisará registrar seu serviço Web na Estrutura de Bots. A ID do Aplicativo da Microsoft (vamos nos referir a isso como sua ID de Bot de dentro do Teams, para identificá-la de outras IDs de aplicativos com as quais você pode estar trabalhando) e o ponto de extremidade de mensagens com o qual seu registro na Estrutura de Bots será usado na extensão de mensagens para receber e responder às solicitações. Se você estiver usando um registro existente, certifique-se de [habilitar](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true)o canal Microsoft Teams .

Se você seguir um dos inícios rápidos ou começar a partir de um dos exemplos disponíveis, você será orientado a registrar seu serviço Web. Se você quiser registrar manualmente seu serviço, você tem três opções para fazer isso. Se você optar por se registrar sem usar uma assinatura do Azure, não poderá aproveitar o fluxo de autenticação OAuth simplificado fornecido pela Estrutura de Bots. Você poderá migrar seu registro para o Azure após a criação.

* Se você tiver uma assinatura do Azure (ou quiser criar uma nova), poderá registrar seu serviço Web manualmente usando o Portal do Azure. Crie um recurso "Registro de Canais bot". Você pode escolher a camada de preços gratuitos, pois as mensagens de Microsoft Teams não contam para o total de mensagens aceitável por mês.
* Se você não quiser usar uma assinatura do Azure, poderá usar o [portal de registro herdado.](https://dev.botframework.com/bots/new)
* O App Studio também pode ajudá-lo a registrar seu serviço Web (bot). Os serviços Web registrados por meio do App Studio não são registrados no Azure. Você pode usar o [portal herdado](https://dev.botframework.com/bots) para exibir, gerenciar e migrar seus registros.

## <a name="create-your-app-manifest"></a>Criar seu manifesto do aplicativo

Você pode usar o aplicativo Studio para ajudá-lo a criar seu manifesto de aplicativo ou a criá-lo manualmente.

### <a name="create-your-app-manifest-using-app-studio"></a>Criar seu manifesto do aplicativo usando o App Studio

Você pode usar o aplicativo App Studio de dentro do cliente Microsoft Teams para ajudar a criar o manifesto do aplicativo.

1. No cliente do Teams, abra o aplicativo Studio no menu de estouro **...** no trilho de navegação à esquerda. Se ainda não estiver instalado, você poderá fazer isso pesquisando por ele.
2. Na guia **Editor de manifesto,** selecione **Criar** um novo aplicativo (ou se você estiver adicionando uma extensão de mensagens a um aplicativo existente, você pode importar seu pacote de aplicativo)
3. Adicione os detalhes do aplicativo (Confira [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter descrições completas de cada campo).
4. Na guia **Extensões de Mensagens,** clique no botão **Instalação.**
5. Você pode criar um novo serviço Web (bot) para sua extensão de mensagens usar ou se você já registrou um selecione/adicione-o aqui.
6. Se necessário, atualize o endereço do ponto de extremidade do bot para apontar para o seu bot. Ela deve ser similar a `https://someplace.com/api/messages`.
7. O **botão Adicionar** na seção **Comando** orientará você através da adição de comandos à extensão de mensagens. Consulte a [seção Saiba mais](#learn-more) para obter mais informações sobre como adicionar comandos. Lembre-se de que você pode definir até 10 comandos para sua extensão de mensagens.
8. A **seção Manipuladores de** Mensagens permite que você adicione um domínio em que suas mensagens serão disparadas. Consulte [link unfurling](~/messaging-extensions/how-to/link-unfurling.md) para obter mais informações.

Na guia **Concluir =>** e distribuir, você pode **Baixar** o pacote do aplicativo (que inclui o manifesto do aplicativo, bem como os ícones do aplicativo) ou **Instalar** o pacote.

### <a name="create-your-app-manifest-manually"></a>Criar o manifesto do aplicativo manualmente

Assim como com bots e [](~/resources/schema/manifest-schema.md#composeextensions) guias, você atualiza o manifesto do aplicativo do aplicativo para incluir as propriedades de extensão de mensagens. Essas propriedades regem como sua extensão de mensagens aparece e se comporta no cliente Microsoft Teams de mensagens. As extensões de mensagens são suportadas começando com v1.0 do manifesto.

#### <a name="declare-your-messaging-extension"></a>Declarar sua extensão de mensagens

Para adicionar uma extensão de mensagens, inclua uma nova estrutura JSON de nível superior no manifesto do aplicativo com a `composeExtensions` propriedade. Você cria uma única extensão de mensagens para seu aplicativo, com até 10 comandos.

> [!NOTE]
> O manifesto refere-se a extensões de mensagens como `composeExtensions` . Isso é para manter a compatibilidade com compatibilidade com backward.

A definição de extensão é um objeto que tem a seguinte estrutura:

| Nome da propriedade | Finalidade | Obrigatório? |
|---|---|---|
| `botId` | O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Normalmente, isso deve ser o mesmo que a ID do seu aplicativo Teams geral. | Sim |
| `canUpdateConfiguration` | Habilita **Configurações** item de menu. | Não |
| `commands` | Matriz de comandos compatíveis com essa extensão de mensagens. Você está limitado a 10 comandos. | Sim |

#### <a name="define-your-commands"></a>Definir seus comandos

Sua extensão de mensagens deve declarar um ou mais comandos, que definem onde os usuários podem disparar sua extensão de mensagens e o tipo de interação. Confira [mais informações sobre](#learn-more) comandos de extensão de mensagens.

#### <a name="simple-manifest-example"></a>Exemplo de manifesto simples

O exemplo a seguir é um objeto de extensão de mensagens simples no manifesto do aplicativo com um comando de pesquisa. Esse não é o arquivo de manifesto completo do aplicativo, apenas a parte específica das extensões de mensagens. Confira [o esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md) para ver um exemplo completo.

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

#### <a name="complete-app-manifest-example"></a>Exemplo de manifesto completo do aplicativo

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

## <a name="add-your-invoke-message-handlers"></a>Adicionar seus manipuladores de mensagens de invocação

Quando os usuários acionarem a extensão de mensagens, você precisará lidar com a mensagem de invocação inicial, coletar algumas informações do usuário e processar essas informações e responder adequadamente. Para fazer isso, primeiro você precisará decidir que tipo de comandos deseja adicionar [](~/messaging-extensions/how-to/action-commands/define-action-command.md) à extensão de mensagens e adicionar comandos de ação ou adicionar comandos [de pesquisa.](~/messaging-extensions/how-to/search-commands/define-search-command.md)

## <a name="messaging-extensions-in-teams-meetings"></a>Extensões de mensagens em Teams reuniões

> [!NOTE]
> Se uma reunião ou chat de grupo tiver usuários federados na lista, Teams o acesso a extensões de mensagens para todos os usuários, incluindo o organizador.

Quando uma reunião começa, Teams os participantes podem interagir diretamente com sua extensão de mensagens durante uma chamada ao vivo. Considere o seguinte ao criar sua extensão de mensagens na reunião:

1. **Localização** Sua extensão de mensagens pode ser invocada da área de mensagem de redação, da caixa de comando ou @mentioned no chat da reunião.

1. **Metadados**. Quando sua extensão de mensagens é invocada, ela pode identificar o usuário e o locatário `userId` de `tenantId` e . O `meetingId` pode ser encontrado como parte do objeto `channelData`. Seu aplicativo pode usar e `userId` `meetingId`  para a solicitação de API recuperar funções `GetParticipant` de usuário.

1. **Tipo de comando**. Se a extensão da mensagem usar [comandos baseados em ação,](../messaging-extensions/what-are-messaging-extensions.md#action-commands)ela deverá seguir as guias [autenticação de login](../tabs/how-to/authentication/auth-aad-sso.md) único.

1. **Experiência do usuário**. A extensão de mensagens deve parecer e se comportar da mesma forma que faria fora de uma reunião.

## <a name="next-steps"></a>Próximas etapas

* [Criar comandos de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Criar comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Desenrolamento de link](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Saiba mais

Experimente em um início rápido:

* Início rápido para C #
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Início rápido para JavaScript
  * [Extensão de mensagens com comandos baseados em ação](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Extensão de mensagens com comandos baseados em pesquisa](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Saiba mais sobre Teams de desenvolvimento:

* [Compreender Teams de aplicativos](../concepts/capabilities-overview.md)
* [O que são extensões de mensagens?](../messaging-extensions/what-are-messaging-extensions.md)
