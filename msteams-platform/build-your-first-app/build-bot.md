---
title: Comece - Construa um bot
author: girliemac
description: Crie rapidamente um bot de Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: 2cbd90b293e8ac8343febc7b3d23278d5bb5bf82
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565883"
---
# <a name="create-your-first-bot-for-teams"></a>Crie seu primeiro bot para Teams

Este tutorial ensina você a construir um aplicativo básico de bot. Um bot atua como um intermediário entre Teams usuários e seu aplicativo ou serviço web com uma interface de conversação. As pessoas podem conversar com um bot para obter rapidamente informações ou iniciar fluxos de trabalho e tarefas executadas pelo seu serviço.

## <a name="what-youll-learn"></a>O que você vai aprender

* Crie um projeto de aplicativo e bot usando o Microsoft Teams Toolkit para Visual Studio Code.
* Entenda as configurações de aplicativos Teams relevantes para os bots.
* Hospede e execute um aplicativo localmente usando uma solução de túnel local.
* Carga lateral e teste um bot em Teams.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e construir um aplicativo de Teams simples. Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md) 

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para o seu aplicativo: 

* **Configurações de aplicativos e andaimes** relevantes para bots.
* **Bot** que é automaticamente registrado no serviço de Microsoft Azure Bot.

**Para criar seu projeto de aplicativo**

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha **Criar um novo aplicativo de Teams**.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Captura de tela mostrando como criar um aplicativo no Teams Toolkit.":::

1. Quando solicitado, faça login com sua conta de desenvolvimento Microsoft 365. 
1. Na tela do projeto Selecionar, selecione Chat bots: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Captura de tela mostrando como criar um novo bot no Teams Toolkit.":::

1. Na tela do **projeto Configurar, digite** um nome para o seu bot. Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.
1. Selecione **Criar um novo registro de** bot create  >  **bot,** conforme mostrado na imagem a seguir:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Captura de tela mostrando nomear novo bot no Teams Toolkit.":::

    Se for bem sucedido, seu novo bot terá um **status registrado.** Agora, seu bot está automaticamente registrado no serviço de Microsoft Azure Bot. 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Captura de tela mostrando o registro de novo bot no Teams Toolkit.":::

1. Selecione **Terminar** na parte inferior da tela e salvar seu projeto em sua máquina.  

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do seu aplicativo

Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vejamos os principais componentes para a construção de um bot:

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Captura de tela mostrando um andaime de projeto no Teams Toolkit.":::

Se você criou uma guia em outro tutorial, o andaime do aplicativo para o bot é diferente. Ao contrário das guias, o desenvolvimento de bots não exige que você construa nenhum componente web front-end ou use o Teams Cliente JavaScript SDK.  Em vez disso, o andaime usa o [Microsoft Bot Framework](https://dev.botframework.com/), que é um SDK de código aberto para a construção de bots inteligentes de nível corporativo que podem funcionar na web, mobile e, claro, Teams! 

O `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, é o manipulador específico de Teams que lida com as atividades do bot, como como o bot responde a mensagens específicas. O andaime do aplicativo fornece um `botActivityHandler.js` arquivo localizado no diretório raiz do seu projeto, é o manipulador específico Teams que lida com atividades de bot, como como o bot responde a mensagens específicas.

## <a name="3-securely-expose-your-localhost-to-the-internet"></a>3. Exponha com segurança seu local à internet

Dê uma olhada no `index.js` arquivo, que cria um servidor HTTP e lida com roteamento para ouvir as solicitações recebidas do seu bot. O `/api/messages` URL de ponto final do seu aplicativo é para responder às solicitações do cliente: 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

Para encaminhar as solicitações à lógica do seu bot, você deve configurar uma URL acessível ao público, como `https://example.com/api/messages` , em vez de `https://localhost` . Como seu aplicativo está sendo executado a partir de seu localhost atualmente, você deve *túnel* da rede.

O tunelamento é um protocolo que permite transportar dados através de uma rede. E o túnel local lhe dá uma conexão entre sua máquina local e uma conexão remota. Para expor com segurança seu local à internet, recomendamos que você use a ferramenta de terceiros chamada **ngrok**. Isso lhe dará uma URL segura. 

1. Vá até o [site ngrok.com](https://ngrok.com/download) e siga as instruções para instalar e configurar ngrok em seu ambiente. 
    
    Adicione o caminho completo ao arquivo ngrok.exe que você instalou à variável de ambiente PATH do sistema. Os passos exatos são específicos para a concha que você está usando.

1.  Depois de terminar de configurá-lo, abra um terminal e `ngrok http -host-header=rewrite 3978` corra. 

    Agora, a ngrok fornece uma URL pública e segura que encaminha para o seu localhost na porta 3978, então copie a URL HTTPS, por exemplo, como mostrado na captura de tela abaixo, já que `https://287a4f4223bc.ngrok.io` Teams requer conexões HTTPS: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Captura de tela mostrando o túnel do localhost com ngrok.":::

1. Registre a URL no manifesto do aplicativo. 

## <a name="4-register-your-bot-endpoint"></a>4. Registre seu ponto final do bot

Para usar um bot em Teams, você deve registrá-lo no Serviço Azure Bot. Isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.

Você ainda deve especificar um endereço de ponto final para receber e processar mensagens do usuário ou solicitações enviadas ao bot. Normalmente, a URL se parece `https://HOST_URL/api/messages` com . Você pode configurar isso no kit de ferramentas.

1. Em Visual Studio Code, **Microsoft Teams Toolkit** aberto.
1. Selecione **bots**  >  **Registros de bots existentes** e selecione o bot criado durante a configuração. 
1. No campo de **endereços do ponto final do Bot,** digite a URL ngrok, por `https://287a4f4223bc.ngrok.io` exemplo, onde você está hospedando o bot e `/api/messages` anexar a ele:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Captura de tela mostrando como túnel localhost com ngrok.":::

    Seu bot será capaz de responder às mensagens em Teams, depois de configurar o ponto final corretamente. 

## <a name="5-build-and-run-your-app"></a>5. Construa e execute seu aplicativo

Você configurou uma URL para hospedar seu bot e configurou-o para lidar com mensagens. É hora de colocar seu aplicativo em funcionamento.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. `npm start`Corra.

   Se for bem-sucedido, você verá a seguinte mensagem indicando que seu bot está ouvindo a atividade em seu `localhost` :

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Carregar lateralmente seu bot em Teams

Com o bot funcionando, você pode instalá-lo em Teams.

> [!TIP]
> Se você nunca mais regou um aplicativo de Teams antes e se deparar com problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Em Visual Studio Code, selecione a tecla **F5** para lançar um Teams cliente web.
1. No aplicativo instalar a caixa de diálogo, selecione **Adicionar para mim**. 

   > [!Note]
   > Por padrão, o aplicativo é adicionado à sua mensagem de bate-papo direto 1:1, no entanto você pode optar por instalá-lo em uma equipe ou chat clicando na pequena seta ao lado **de Add para mim**. Neste tutorial, vamos clicar em Adicionar.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Captura de tela mostrando túnel localhost com ngrok.":::

## <a name="7-test-your-bot"></a>7. Teste seu bot

Vamos dizer "Olá" para o seu robô.

* Na caixa de composição, envie uma `Hello` mensagem.
    Seu bot responde com algo como a seguinte mensagem:

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Uma captura de tela mostrando um usuário dizer 'Olá' para um bot Teams e recebendo uma resposta.":::

    Agora você criou um bot básico de Teams que pode se comunicar com os usuários um a um ou em configurações de grupo (canais e chats) 🎉.

## <a name="troubleshoot-your-bot"></a>Solucionar problemas do seu bot

As informações a seguir podem ajudar se você tiver problemas para completar este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>Bot não está conectado a Teams


Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot esteja [conectado ao *canal* Teams do Azure Bot Service](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal em Teams. Neste caso, um canal é como o Azure Bot Service conecta seu bot a Teams ou outro [aplicativo de comunicação suportado da Microsoft ou de terceiros.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="see-also"></a>Confira também

* [Noções básicas de bot](../bots/bot-basics.md)
* [Crie uma guia pessoal para Microsoft Teams](../build-your-first-app/build-personal-tab.md)
* [Veja o que mais Teams bots podem fazer com uma de nossas amostras](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* [Diretrizes de design](../bots/design/bots.md) 
* [Modelos de interface do usuário prontos para produção](../concepts/design/design-teams-app-ui-templates.md)
* [Autenticação de bot em Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Crie um bot sem o kit de ferramentas](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)
