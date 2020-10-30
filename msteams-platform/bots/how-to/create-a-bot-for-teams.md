---
title: Criar um bot usando o App Studio
author: clearab
description: Saiba como criar um bot do Microsoft Teams usando o App Studio.
ms.topic: conceptual
localization_priority: Priority
ms.author: anclear
ms.openlocfilehash: 3d4f954afd56bf6ee442b57961c9d6b736ffa4d8
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796348"
---
# <a name="create-a-bot-using-app-studio"></a>Criar um bot usando o App Studio

> [!TIP]
> Procurando uma maneira mais rápida para iniciar? Crie um [bot](../../build-your-first-app/build-bot.md) utilizando o kit de ferramentas do Microsoft Teams.

Será necessário concluir as etapas a seguir para criar um bot de conversa:

1. Preparar seu ambiente de desenvolvimento.
1. Criar seu serviço Web.
1. Registre seu serviço Web como um bot com o Microsoft bot Framework.
1. Crie seu manifesto de aplicativo e seu pacote de aplicativos.
1. Carregar seu pacote do aplicativo para o Microsoft Teams.

Criar seu serviço Web, registrar seu serviço da Web e criar seu pacote de aplicativos, com a estrutura bot pode ser feito em qualquer ordem. No entanto, como as três partes estão muito entrelaçadas, não importa em que ordem você as realize, você precisará retornar para atualizar as outras pessoas. Seu registro precisa do ponto de extremidade de mensagem de seu serviço Web implantado e o seu serviço Web precisa do ID e da senha criados a partir do seu registro. Seu manifesto de aplicativo também precisa do ID de registro para conectar o Teams ao seu serviço Web.

À medida que você cria o bot, você se move regularmente entre alterar o manifesto do aplicativo e implantar o código no seu serviço Web. Ao trabalhar com o manifesto do aplicativo, tenha em mente que você pode manipular manualmente o arquivo JSON ou fazer alterações por meio do aplicativo Studio. De qualquer forma, você precisará implantar (carregar) novamente o aplicativo do Teams, quando fizer uma alteração no manifesto. No entanto, não é necessário fazer isso quando você implanta alterações no serviço da Web.

Confira a [documentação do bot Framework](/azure/bot-service/) para obter mais informações sobre a estrutura bot.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Criar seu serviço Web

O coração do seu bot é o seu serviço Web. Ele definirá uma rota simples, geralmente `/api/messages`, para receber todas as solicitações. Para começar, você tem algumas opções:

* Comece com o exemplo de bot de conversa do Teams em[C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot) ou [JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot).
* Se você estiver usando o JavaScript, use o [Gerador Yeoman do Microsoft Teams](https://github.com/OfficeDev/generator-teams) para a exibição de scaffold do aplicativo do Teams, incluindo seu serviço Web. Isso é particularmente útil ao criar um aplicativo do Teams que contenha mais do que apenas um bot de conversa.
* Criar seu serviço Web a partir do zero. Você pode optar por adicionar o SDK do verificador de bot para o seu idioma ou trabalhar diretamente com as cargas JSON.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrar seu serviço Web com a estrutura bot

> [!IMPORTANT]
> Ao registrar seu serviço Web, certifique-se de definir o **Nome de exibição** com o mesmo nome que você usou para o seu **Nome Curto** no manifesto do aplicativo. Quando o aplicativo for distribuído por carregamento direto ou por meio do catálogo de aplicativos de uma organização, as mensagens enviadas para uma conversa pelo bot usarão o **nome de exibição** nome de exibição do registro, em vez do **nome curto** do aplicativo.

Registrar seu serviço Web com a estrutura bot fornece um canal de comunicação seguro entre o cliente do Teams e seu serviço Web. O cliente do Teams e o seu serviço Web nunca se comunicam diretamente. Em vez disso, as mensagens são encaminhadas pelo serviço de estrutura de bot (o Microsoft Teams usa uma instância separada desse serviço compatível com os padrões do Office 365).

Você tem duas opções ao registrar seu serviço Web com a estrutura bot. Você pode usar o [app Studio](#using-app-studio) ou o [portal herdado](#in-the-legacy-portal) para registrar o bot sem usar uma assinatura do Azure. Ou, se você já tiver uma assinatura do Azure (ou não se importar em criar uma), você poderá usar o [portal do Azure](#with-an-azure-subscription) para registrar seu serviço Web.

### <a name="without-an-azure-subscription"></a>Sem uma assinatura do Azure.

Se você não quiser criar seu registro de bot no Azure, **deverá** usar esse link-https://dev.botframework.com/bots/newou o aplicativo Studio. Se você clicar no botão *criar um bot* , no portal de estrutura de bot, você criará seu registro de bot no Microsoft Azure e será necessário fornecer uma assinatura do Azure. Para gerenciar seu registro ou migrar para uma assinatura do Azure após a criação, vá para: https://dev.botframework.com/bots.

Ao editar as propriedades de um registro de estrutura de bot existente não registrado no Azure, você verá uma coluna "status de migração" e um botão azul "migrar" que o levará para o portal do Microsoft Azure. Não selecione o botão "migrar", a menos que você queira fazer isso. Em vez disso, selecione o **nome** do bot e você poderá editar suas propriedades:

   ![Editar propriedades de bot](~/assets/images/bots/bf-migrate-bot-to-azure.png)

Situações em que você **deve** ter o registro de bot no Azure (por meio de sua criação no portal do Azure ou na migração):

* Você deseja usar o [OAuthPrompt](./authentication/auth-flow-bot.md) da estrutura de bot para autenticação.
* Você deseja habilitar canais adicionais, como o chat na Web, linha direta ou Skype.

#### <a name="using-app-studio"></a>Usando o aplicativo Studio

O *App Studio* é um aplicativo do Teams que ajuda a criar aplicativos do Teams, incluindo o registro de serviço Web como um bot, a criação de um manifesto e de um pacote de aplicativos, e atualização de configurações. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Confira [Introdução ao Teams app Studio](../../concepts/build-and-test/app-studio-overview.md).

Lembre-se de que, se você usar o aplicativo Studio para registrar seu serviço Web, precisará acessar o https://dev.botframework.com/bots para gerenciar seu registro.

#### <a name="in-the-legacy-portal"></a>No portal herdado

Crie seu registro de bot usando esse link: https://dev.botframework.com/bots/new. **Lembre-se de adicionar o Microsoft Teams como um canal da lista de canais em destaque após criar seu bot.** Sinta-se à vontade para usar novamente o ID do aplicativo da Microsoft que você gerou, caso já tenha criado seu pacote/manifesto de aplicativos.

   ![Página de registro do bot Framework](~/assets/images/bots/bfregister.png)

### <a name="with-an-azure-subscription"></a>Com uma assinatura do Azure.

Você também pode registrar seu serviço Web Criando um recurso de registro de canais de bot no portal do Azure.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

O [portal de estrutura de bot](https://dev.botframework.com) é otimizado para registro de bots no Microsoft Azure. Aqui estão algumas coisas que você precisa saber:

* O canal do Microsoft Teams para bots registado no Azure é **gratuito** . As mensagens enviadas por meio do canal do Teams NÃO contarão como as mensagens consumidas para o bot.
* Se você registrá-lo usando o Microsoft Azure, seu código de bot não precisará ser *hospedado* no Microsoft Azure.
* Se você registrar um bot usando o portal do Microsoft Azure, é necessário ter uma conta do Microsoft Azure. Você pode [criar uma gratuitamente](https://azure.microsoft.com/free/). Para verificar sua identidade ao criar uma conta do Azure, você deve fornecer um cartão de crédito, mas ele não será cobrado. É sempre gratuito criar e usar bots com o Microsoft Teams.

## <a name="create-your-app-manifest-and-package"></a>Criar o manifesto do aplicativo e o pacote

O [manifesto do aplicativo](~/resources/schema/manifest-schema.md) define os metadados para o seu aplicativo, os pontos de extensão que o aplicativo está usando e aponta para os serviços da Web onde esses pontos de extensão se conectam. Você pode usar o aplicativo Studio para ajudá-lo a criar seu manifesto de aplicativo ou a criá-lo manualmente.

### <a name="add-using-app-studio"></a>Adicionar usando o aplicativo Studio

1. No cliente do Teams, abra o aplicativo Studio no menu de estouro **...** no trilho de navegação à esquerda. Se o aplicativo Studio ainda não estiver instalado, você poderá fazer isso pesquisando por ele.
2. Na guia **Editor de manifesto** selecione **Criar um novo aplicativo** (ou se você estiver adicionando um bot a um aplicativo existente, é possível importar seu pacote de aplicativos)
3. Adicione os detalhes do aplicativo (Confira [definição de esquema de manifesto](~/resources/schema/manifest-schema.md) para obter descrições completas de cada campo).
4. Na guia **bots** , selecione o botão **Configurar** .
5. Você pode criar um novo registro de serviço Web ( **novo bot** ) ou, se você já tiver registrado um, selecione **bot existente** .
6. Selecione os recursos e os escopos necessários para seu bot.
7. Se necessário, atualize o endereço do ponto de extremidade do bot para apontar para o seu bot. Ela deve ser similar a `https://someplace.com/api/messages`.
8. Opcionalmente, adicione [comandos de bot](~/bots/how-to/create-a-bot-commands-menu.md).
9. Opcionalmente, você poderá baixar o pacote do aplicativo concluído na guia **testar e distribuir** .

### <a name="create-it-manually"></a>Criar manualmente

Assim como nas extensões de mensagens e guias, você atualiza o [manifesto de aplicativo](~/resources/schema/manifest-schema.md) para definir o seu bot. Adicione a nova estrutura JSON de nível superior no manifesto do aplicativo com a propriedade `bots`.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID de aplicativo geral.|
|`needsChannelSelector`|Boolean|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: `false`.|
|`isNotificationOnly`|Boolean|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: `false`.|
|`supportsFiles`|Boolean|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: `false`.|
|`scopes`|Matriz de enumeração|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|

Opcionalmente, você pode definir uma ou mais listas de comandos que você pode recomendar para os usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo `object`. Você deve definir uma lista de comandos separada para cada escopo compatível com o bot. *Confira* [menus de bot](./create-a-bot-commands-menu.md), para obter mais informações.

|Name| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumeração|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10|✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

#### <a name="simple-manifest-example"></a>Exemplo de manifesto simples

O exemplo a seguir é um objeto bot simples, com duas listas de comando definidas. Esse não é o arquivo de manifesto completo do aplicativo, apenas a parte específica das extensões de mensagens.

```json
...
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command N",
              "description": "Description of Command N"
            }
          ]
        },
        {
          "scopes": [ "personal", "groupchat" ],
          "commands": [
            {
              "title": "Personal command 1",
              "description": "Description of Personal command 1"
            },
            {
              "title": "Personal command N",
              "description": "Description of Personal command N"
            }
          ]
        }
      ]
    }
  ],
...
```

#### <a name="create-your-app-package-manually"></a>Crie seu pacote de aplicativos manualmente

Para criar um pacote de aplicativos, você precisa adicionar seu manifesto de aplicativo e, opcionalmente, os ícones de aplicativo a um arquivo. zip. Confira [Criar seu pacote de aplicativo](~/concepts/build-and-test/apps-package.md) para obter detalhes completos. Certifique-se de que o arquivo. zip contenha somente os arquivos necessários e não tenha outra estrutura de pastas dentro dele.

## <a name="upload-your-package-to-microsoft-teams"></a>Carregar um pacote do aplicativo para o Microsoft Teams

> [!NOTE]
> Para carregar o bot com êxito, o administrador de locatários deve primeiro [permitir o carregamento](/microsoftteams/manage-apps#manage-org-wide-app-settings) de aplicativos personalizados ou de terceiros no Teams.

Se você estiver usando o aplicativo Studio, é possível instalar seu aplicativo a partir da guia **Testar e distribuir** do **Editor de manifesto** . Como alternativa, você pode instalar o pacote do aplicativo clicando no menu de estouro de `...` do trilho de navegação à esquerda, clicando em **Mais aplicativos** e, em seguida, em **Carregar um link personalizado do aplicativo** . Você também pode importar um manifesto de aplicativo ou pacote de aplicativos para o aplicativo Studio para fazer atualizações adicionais antes de carregar.

## <a name="bots-in-teams-meetings"></a>Bots nas reuniões do Teams

O Teams oferecem suporte à invocação de bot durante reuniões. Quando o bot recebe a mensagem de invocação, ele pode identificar o usuário e o locatário de `userId` e `tenantId`. O `meetingId` pode ser encontrado como parte do objeto `channelData`. O bot pode usar o `userId` e `meetingId`  para a solicitação da API do `GetParticipant` para recuperar funções de usuário.

## <a name="next-steps"></a>Próximas etapas

* [Princípios básicos de conversas](./conversations/conversation-basics.md)
* [Inscreva-se em eventos de conversa](./conversations/subscribe-to-conversation-events.md)
