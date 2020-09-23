---
title: Criar um bot do Microsoft Teams
author: heath-hamilton
description: Saiba como criar um bot para seu primeiro aplicativo do Microsoft Teams.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: 7d3d1b63aace7fda971fb6ccaddddf631b4b2ad9
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210051"
---
# <a name="build-a-teams-bot"></a>Criar um bot do Microsoft Teams

Você criará um aplicativo de *bot* básico neste tutorial. Um bot atua como intermediário entre os usuários do Teams e o serviço Web. As pessoas podem bater papo com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas realizadas pelo serviço.

## <a name="your-assignment"></a>Sua atribuição

Seu local de trabalho está usando [guias](../build-your-first-app/build-personal-tab.md) para trazer informações importantes de contato no Microsoft Teams. Por exemplo, os colegas têm acesso rápido ao número de telefone de suporte técnico. Mas em vez de chamar, e se as pessoas pudessem entrar em contato com o suporte técnico usando um chatbot? Seu chefe pede que você veja com rapidez como você pode obter um bot de conversação básico e em execução no Microsoft Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar algumas das propriedades de manifesto do aplicativo e scaffolding relevantes para bots
> * Hospedar um aplicativo localmente
> * Configurar um bot para o Teams
> * Sideload e testar um bot no Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).

## <a name="create-your-app-project"></a>Criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:

* **Manifesto do aplicativo e scaffolding** relevantes para bots
* **Bot** que é registrado automaticamente com o serviço de bot do Microsoft Azure

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Adicionar recursos** , selecione **bot** e, em seguida, **Avançar**.
1. Selecione **criar um novo bot** e **login** para entrar com sua conta de desenvolvimento do Microsoft 365.<br/>
:::image type="content" source="../assets/images/build-your-first-app/vsc-create-bot.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot.":::
1. Armazene sua ID de bot e senha (você precisará de um pouco mais tarde).
1. Opcion Insira um nome personalizado para o bot e selecione **criar**. (Lembre-se de que esse é o nome do seu bot e não o nome do aplicativo Teams que você já especificou.)
1. Selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="identify-relevant-app-project-components"></a>Identificar componentes de projeto de aplicativo relevantes

Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para a criação de um bot.

### <a name="app-manifest"></a>Manifesto do aplicativo

O trecho de código a seguir do manifesto do aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra as propriedades e os valores padrão relevantes para bots.

```JSON
"bots": [
    {
        "botId": "{botId0}",
        "scopes": [
            "personal",
            "groupchat",
            "team"
        ],
        "supportsFiles": false,
        "isNotificationOnly": false,
        "commandLists": [
            {
                "scopes": [
                    "personal",
                    "groupchat",
                    "team"
                ],
                "commands": [
                    {
                        "title": "Hello",
                        "description": "Sends a hello message and @mention the sender"
                    }
                ]
            }
        ]
    }
],
```

Por enquanto, vamos apenas nos concentrar nas seguintes propriedades obrigatórias. (Veja a lista completa de propriedades com suporte [`bots`](../resources/schema/manifest-schema.md#bots) .)

* `botId`: A ID do bot que você criou configurando seu projeto. (Armazenado no `{botId0}` , você pode encontrar a ID real no `Development.env` .)
* `scopes`: Especifica se o bot está disponível nos `personal` `groupchat` `team` contextos, ou (por exemplo, canal).
* `commands`: Comandos disponíveis os usuários podem enviar para o bot.
* `title`: Nome do comando do bot exibido no cliente do teams.
* `description`: Uma breve descrição ou exemplo da sintaxe e dos argumentos para ajudar os usuários a entender o que é um comando bot.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com o modo como seu bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens específicas como "Hello").

O `.env` arquivo, também no diretório raiz, armazena a ID de bot e a senha.

## <a name="set-up-a-secure-tunnel-to-your-app"></a>Configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar seu bot em um servidor Web local (porta 3978).

1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída, pois o Microsoft Teams requer conexões HTTPS.
1. Em seu `.publish` diretório, abra `Development.env` .
1. Substitua o `baseUrl0` valor pela URL copiada. (Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

O manifesto do aplicativo está apontando para o local em que você está hospedando o bot.

## <a name="configuring-your-bot"></a>Configurando o bot

Para usar um bot no Teams, você deve registrá-lo com o serviço de bot do Azure. Sorte para você, isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.

### <a name="specify-your-bot-id-and-password"></a>Especificar a ID e a senha do bot

Quando o bot é registrado com o serviço de bot do Azure, é atribuída uma ID e uma senha que o aplicativo de equipes deve conhecer.

1. Localize a ID e a senha do bot que você armazenou durante a instalação do kit de ferramentas.
1. No diretório raiz, abra o `.env` arquivo.
1. Adicione a ID e a senha do bot ao `BotId` e `BotPassword` , respectivamente.

### <a name="add-the-bot-endpoint-address"></a>Adicionar o endereço do ponto de extremidade do bot

Você deve especificar uma URL de ponto de extremidade para receber e processar mensagens de usuário (ou seja, solicitações) enviadas ao bot. Normalmente, a URL é semelhante `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas do teams.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. Vá para **Gerenciamento de bot > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **endereço do ponto de extremidade do bot** , insira o servidor Web local onde você está hospedando o bot ( `baseUrl10` valor) e anexe `/api/messages` a ele.

    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no kit de ferramentas do teams.":::

Seu bot poderá responder às mensagens no Teams.

## <a name="run-your-app"></a>Executar o aplicativo

Você configurou uma URL para hospedar seu bot e configurá-la para lidar com as mensagens. É hora de colocar o bot em funcionamento.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá algo parecido com a seguinte mensagem, indicando que o seu bot está ouvindo a atividade no seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-bot-in-teams"></a>Sideload seu bot no Microsoft Teams

Com o bot em execução, você pode instalá-lo no Microsoft Teams.

> [!TIP]
> Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).

1. Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload.
1. Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.
1. Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` .
1. Na janela instalar, selecione **Adicionar** para instalar seu aplicativo.

## <a name="test-your-bot"></a>Testar o bot

Agora, para a parte divertida: Vamos dizer "Olá" ao seu bot em um chat de um a um.

1. No Teams, selecione **mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: no lado esquerdo.
1. Localize e escolha o bot que você acabou de suplementos foi feito.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/bot-teams-access.png" alt-text="Ilustração mostrando onde você acessa o bot no Microsoft Teams.":::
1. Na caixa redigir, envie uma `Hello` mensagem.

Seu bot responde com algo como a mensagem a seguir.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário diga "Olá" para um bot do Microsoft Teams e obtendo uma resposta.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um bot de equipe básico que pode se comunicar com os usuários, um ou em configurações de grupo (canais e chats).

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.

### <a name="toolkit-setup-fails"></a>Falha na instalação do kit de ferramentas

Ao configurar seu projeto de aplicativo com o Teams Toolkit, você recebe um erro depois de selecionar a opção **criar um novo bot** e fazer logon com sua conta de desenvolvimento do Microsoft 365.

Isso pode ser um problema de autenticação. Siga estas etapas para concluir a configuração do seu projeto.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **sair**.
1. Execute o processo de instalação novamente, conectando-se com a mesma conta e criando um novo bot.

### <a name="bot-isnt-connected-to-teams"></a>O bot não está conectado ao Teams

Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está [conectado ao *canal*Teams do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Microsoft Teams. Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).

## <a name="learn-more"></a>Saiba mais

* [Veja o que mais os bots de equipe podem fazer com um de nossos exemplos](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* [Autenticação de bot no Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft bot Framework](https://dev.botframework.com/)
* [Criar um bot sem o kit de ferramentas](../bots/how-to/create-a-bot-for-teams.md)
