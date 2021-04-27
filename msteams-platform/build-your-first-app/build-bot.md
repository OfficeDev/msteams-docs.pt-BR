---
title: Começar - Criar um bot
author: heath-hamilton
description: Crie rapidamente um bot do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 5dfbfa05d2f1e36bbc14bd929cb2592303081522
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019997"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Criar um bot para o Microsoft Teams

Você criará um aplicativo *de bot* básico neste tutorial. Um bot age como um intermediário entre usuários do Teams e seu serviço Web. As pessoas podem conversar com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas executadas pelo seu serviço.

## <a name="your-assignment"></a>Sua atribuição

Seu local de trabalho criou um aplicativo do Teams que usa [guias para](../build-your-first-app/build-personal-tab.md) superfícier informações importantes de contato. Por exemplo, os colegas têm acesso rápido ao número de telefone do help desk. Mas, em vez de chamar, e se as pessoas pudessem entrar em contato com o help desk usando um chatbot? Seu chefe pede que você veja a rapidez com que um bot de conversa básica pode ser executado no Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot usando o microsoft Teams Toolkit para Visual Studio Código
> * Identificar algumas das configurações do aplicativo e os scaffolding relevantes para bots
> * Hospedar um aplicativo localmente
> * Configurar um bot para o Teams
> * Fazer sideload e testar um bot no Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não entendeu e instalou os [pré-requisitos de](build-first-app-overview.md#get-prerequisites)desenvolvimento do Teams.

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:

* **Configurações de aplicativos e scaffolding relevantes** para bots
* **Bot** que é registrado automaticamente no Serviço de Bot do Microsoft Azure

> [!TIP]
> Se você não tiver criado um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Bot** e **Next.**
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.)
1. Vá para **Configurar bot** e selecione Criar um **novo Bot,** em **seguida, Criar Registro de Bot**. Se tiver êxito, seu novo bot terá um status **Registrado.**
1. Selecione **Concluir** na parte inferior da tela e escolha um local para criar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. Identificar componentes relevantes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o teams Toolkit. Vamos ver os principais componentes para a criação de um bot.

### <a name="app-configurations"></a>Configurações de aplicativo

Para exibir ou atualizar as configurações do bot, selecione **App Studio** no kit de ferramentas e acesse **Bots**.

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como o bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens `botActivityHandler.js` específicas, como "Hello").

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar seu aplicativo em um servidor Web local (porta 3978).

1. Caso ainda não tenha feito isso, instale [ngrok](https://ngrok.com/download).
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo, ) já que o `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.

Com essa URL, o Teams (que requer conexões HTTPS) poderá túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-your-bot"></a>4. Configure seu bot

Para usar um bot no Teams, você deve registrá-lo com o Serviço bot do Azure. Para sua sorte, isso é feito automaticamente quando você configura seu aplicativo usando o teams Toolkit.

Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens de usuário (ou seja, solicitações) enviadas para o bot. Normalmente, a URL se parece com `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Abrir o Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **Endereço do ponto** de extremidade bot, insira a URL do ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` adeque `/api/messages` a ele.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no teams Toolkit.":::

Seu bot poderá responder a mensagens no Teams.

## <a name="5-build-and-run-your-app"></a>5. Crie e execute seu aplicativo

Você configurou uma URL para hospedar seu bot e configurá-lo para manipular mensagens. É hora de fazer o aplicativo funcionar.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá a seguinte mensagem indicando que seu bot está escutando atividades em seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Fazer sideload do bot no Teams

Com o bot em execução, você pode instalá-lo no Teams.

> [!TIP]
> Se você ainda não fez sideload de um aplicativo do Teams antes e correu para problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Em Visual Studio Código, pressione a **tecla F5** para iniciar um cliente Web do Teams.
1. Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**. (Você pode adicionar o bot a um canal ou chat, mas é menos intrusivo para outras pessoas testar um bot em um chat um-a-um.)

## <a name="7-test-your-bot"></a>7. Teste seu bot

Agora, para a parte divertida: vamos dizer "Olá" ao seu bot.

1. Na caixa de redação, envie uma `Hello` mensagem.

Seu bot responde a algo como a mensagem a seguir.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário dizer &quot;Hello&quot; para um bot do Teams e obter uma resposta.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um bot básico do Teams que pode se comunicar com os usuários um-a-um ou em configurações de grupo (canais e chats).

## <a name="troubleshooting"></a>Solução de Problemas

As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>Bot não está conectado ao Teams

Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está conectado ao canal do Teams do Serviço de Bot [do Azure ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Teams. Nesse caso, um canal é como o Serviço bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Saiba mais

* [Veja o que mais os bots do Teams podem fazer com um de nossos exemplos](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* Siga nossas [diretrizes de design](../bots/design/bots.md) e crie com modelos [de interface](../concepts/design/design-teams-app-ui-templates.md) do usuário prontos para produção para criar uma experiência perfeita.
* [Autenticação bot no Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Criar um bot sem o kit de ferramentas](../resources/bot-v3/bots-create.md)
