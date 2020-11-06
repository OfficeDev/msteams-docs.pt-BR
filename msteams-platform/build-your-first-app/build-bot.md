---
title: Introdução-criar um bot
author: heath-hamilton
description: Crie rapidamente um bot do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 1229064ac6b7aab73c50048f0764c6a2353ab54a
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931733"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

Você criará um aplicativo de *bot* básico neste tutorial. Um bot atua como intermediário entre os usuários do Teams e o serviço Web. As pessoas podem bater papo com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas realizadas pelo serviço.

## <a name="your-assignment"></a>Sua atribuição

Seu local de trabalho criou um aplicativo do teams que usa [guias](../build-your-first-app/build-personal-tab.md) para informações de contato importantes da superfície. Por exemplo, os colegas têm acesso rápido ao número de telefone de suporte técnico. Mas em vez de chamar, e se as pessoas pudessem entrar em contato com o suporte técnico usando um chatbot? Seu chefe pede que você veja com rapidez como você pode obter um bot de conversação básico e em execução no Microsoft Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar algumas das configurações do aplicativo e scaffolding relevantes para bots
> * Hospedar um aplicativo localmente
> * Configurar um bot para o Teams
> * Sideload e testar um bot no Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:

* **Configurações do aplicativo e scaffolding** relevantes para bots
* **Bot** que é registrado automaticamente com o serviço de bot do Microsoft Azure

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos** , selecione **bot** e, em seguida, **Avançar**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Vá para **Configurar bot** e selecione **criar um novo bot** e, em seguida, **criar registro de bot**. Se tiver êxito, o novo bot terá um status **registrado** .
1. Selecione **concluir** na parte inferior da tela e escolha um local para criar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. identificar componentes de projeto de aplicativo relevantes

Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para a criação de um bot.

### <a name="app-configurations"></a>Configurações do aplicativo

Para exibir ou atualizar as configurações do bot, selecione o **app Studio** no kit de ferramentas e vá para **bots**.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com o modo como seu bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens específicas como "Hello").

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar seu aplicativo em um servidor Web local (porta 3978).

1. Caso ainda não tenha feito isso, instale o [ngrok](https://ngrok.com/download).
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo,), pois o Microsoft `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.

Com esta URL, o Teams (que requer conexões HTTPS) será habilitado para encapsular onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-your-bot"></a>4. configure seu bot

Para usar um bot no Teams, você deve registrá-lo com o serviço de bot do Azure. Sorte para você, isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.

Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens de usuário (ou seja, solicitações) enviadas ao bot. Normalmente, a URL é semelhante `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. Vá até **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **endereço do ponto de extremidade do bot** , insira a URL do ngrok (por exemplo, `https://468b9ab725e9.ngrok.io` ) em que você está hospedando o bot e anexe `/api/messages` a ela.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no kit de ferramentas do teams.":::

Seu bot poderá responder às mensagens no Teams.

## <a name="5-build-and-run-your-app"></a>5. Compilar e executar o aplicativo

Você configurou uma URL para hospedar seu bot e configurá-la para lidar com as mensagens. É hora de colocar seu aplicativo em funcionamento.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá a seguinte mensagem indicando que o seu bot está ouvindo a atividade no seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Sideload seu bot no Microsoft Teams

Com o bot em execução, você pode instalá-lo no Microsoft Teams.

> [!TIP]
> Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.
1. Na caixa de diálogo instalar aplicativo, selecione **Adicionar para mim**. (Você pode adicionar o bot a um canal ou chat, mas é menos intrusivo para que outras pessoas possam testar um bot em um chat de um em um.)

## <a name="7-test-your-bot"></a>7. teste seu bot

Agora, para a parte divertida: Vamos dizer "Olá" ao seu bot.

1. Na caixa redigir, envie uma `Hello` mensagem.

Seu bot responde com algo como a mensagem a seguir.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário diga &quot;Olá&quot; para um bot do Microsoft Teams e obtendo uma resposta.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um bot de equipe básico que pode se comunicar com os usuários, um ou em configurações de grupo (canais e chats).

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>O bot não está conectado ao Teams

Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está [conectado ao *canal* Teams do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Microsoft Teams. Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).

## <a name="learn-more"></a>Saiba mais

* [Veja o que mais os bots de equipe podem fazer com um de nossos exemplos](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* [Autenticação de bot no Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft bot Framework](https://dev.botframework.com/)
* [Criar um bot sem o kit de ferramentas](../bots/how-to/create-a-bot-for-teams.md)
