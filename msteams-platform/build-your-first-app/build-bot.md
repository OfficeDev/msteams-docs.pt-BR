---
title: Começar - Criar um bot
author: heath-hamilton
description: Crie rapidamente um bot do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: fbabd5130f0b7eb648a980f5f143792cc4c17933
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911944"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

Você criará um aplicativo *de bot* básico neste tutorial. Um bot age como um intermediário entre os usuários do Teams e seu serviço Web. As pessoas podem conversar com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas executadas pelo serviço.

## <a name="your-assignment"></a>Sua atribuição

Seu local de trabalho criou um aplicativo do Teams que usa [guias para](../build-your-first-app/build-personal-tab.md) destacar informações importantes de contato. Por exemplo, colegas têm acesso rápido ao número de telefone do help desk. Mas, em vez de chamar, e se as pessoas pudessem entrar em contato com o help desk usando um chatbot? Seu chefe solicita que você veja com que rapidez você pode fazer com que um bot de conversa básica seja executado no Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code
> * Identificar algumas das configurações do aplicativo e a scaffolding relevante para bots
> * Hospedar um aplicativo localmente
> * Configurar um bot para o Teams
> * Fazer sideload e testar um bot no Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não o fez, entenda e instale os pré-requisitos de desenvolvimento [do Teams.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:

* **Configurações de aplicativos e scaffolding** relevantes para bots
* **Bot** que é registrado automaticamente com o Serviço de Bot do Microsoft Azure

> [!TIP]
> Se você ainda não criou um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Bot** e **Next.**
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em seu computador local.)
1. Vá para **Configurar bot e** selecione Criar um novo **Bot** e Criar Registro **de Bot.** Se bem-sucedido, seu novo bot terá um status **registrado.**
1. Selecione **Concluir** na parte inferior da tela e escolha um local para criar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifique componentes relevantes do projeto do aplicativo

Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o Kit de Ferramentas do Teams. Vejamos os componentes principais para a criação de um bot.

### <a name="app-configurations"></a>Configurações do aplicativo

Para exibir ou atualizar as configurações do bot, selecione **App Studio** no kit de ferramentas e vá para **Bots.**

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding do aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como o bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens `botActivityHandler.js` específicas, como "Hello").

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar seu aplicativo em um servidor Web local (porta 3978).

1. Caso ainda não tenha feito isso, instale [o ngrok.](https://ngrok.com/download)
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo, ) já que o `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.

Com essa URL, o Teams (que requer conexões HTTPS) poderá usar o túnel para onde você está hospedando seu aplicativo `localhost` (na porta 3978).

## <a name="4-configure-your-bot"></a>4. Configure seu bot

Para usar um bot no Teams, você deve registrá-lo com o Serviço de Bot do Azure. Para você, isso é feito automaticamente quando você configura seu aplicativo usando o Kit de Ferramentas do Teams.

Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens do usuário (ou seja, solicitações) enviadas para o bot. Normalmente, a URL tem a `https://HOST_URL/api/messages` aparência. Você pode configurar isso rapidamente no kit de ferramentas.

1. No Visual Studio Code, selecione **o Microsoft Teams na** Barra de Atividades à esquerda e escolha Abrir o Kit de Ferramentas do Microsoft :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a configuração.
1. No campo **de endereço do ponto** de extremidade bot, insira a URL ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` `/api/messages` anexar a ele.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no Kit de Ferramentas do Teams.":::

Seu bot poderá responder a mensagens no Teams.

## <a name="5-build-and-run-your-app"></a>5. Crie e execute seu aplicativo

Você configurou uma URL para hospedar seu bot e configurou-a para manipular mensagens. É hora de começar a trabalhar com seu aplicativo.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.
1. Executar `npm start` .

Se bem-sucedido, você verá a seguinte mensagem indicando que seu bot está escutando atividades em `localhost` seu:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Fazer sideload do seu bot no Teams

Com o bot em execução, você pode instalá-lo no Teams.

> [!TIP]
> Se você ainda não tiver sideloaded de um aplicativo do Teams antes e tiver problemas, siga estas [instruções.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.
1. Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim.** (Você pode adicionar o bot a um canal ou chat, mas é menos intrusivo para outras pessoas testar um bot em um chat um-para-um.)

## <a name="7-test-your-bot"></a>7. Teste seu bot

Agora, para a parte divertida: vamos dizer "Hello" para seu bot.

1. Na caixa de redação, envie uma `Hello` mensagem.

Seu bot responde com algo parecido com a seguinte mensagem.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário dizendo &quot;Hello&quot; para um bot do Teams e recebendo uma resposta.":::

## <a name="well-done"></a>Bem feito

Parabéns! Você tem um bot básico do Teams que pode se comunicar com usuários um a um ou em configurações de grupo (canais e chats).

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>O bot não está conectado ao Teams

Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está conectado ao canal do Teams do Serviço de Bot do [Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

É importante entender que isso não é o mesmo que um canal no Teams. Nesse caso, um canal é como o Serviço de Bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicação com suporte da Microsoft ou de [terceiros.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Saiba mais

* [Veja o que mais os bots do Teams podem fazer com um de nossos exemplos](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* Siga nossas [diretrizes de design](../bots/design/bots.md) e crie com modelos de interface do usuário prontos para [produção](../concepts/design/design-teams-app-ui-templates.md) para criar uma experiência perfeita.
* [Autenticação de bot no Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Criar um bot sem o kit de ferramentas](../bots/how-to/create-a-bot-for-teams.md)
