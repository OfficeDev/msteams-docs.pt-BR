---
title: Começar - Criar um bot
author: girliemac
description: Crie rapidamente um bot do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: dbb6f0a2497a0914d8e14473f1dbd6b2b225fc96
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068595"
---
# <a name="create-your-first-bot-for-teams"></a>Criar seu primeiro bot para o Teams

Este tutorial ensina você a criar um aplicativo de bot básico. Um bot age como um intermediário entre usuários do Teams e seu aplicativo Web ou serviço com uma interface de conversa. As pessoas podem conversar com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas executadas pelo seu serviço.

## <a name="what-youll-learn"></a>O que você aprenderá

* Crie um projeto de aplicativo e um bot usando o microsoft Teams Toolkit para Visual Studio Código.
* Entenda as configurações de aplicativo do Teams relevantes para bots.
* Hospede e execute um aplicativo localmente usando uma solução de túnel localhost.
* Fazer sideload e testar um bot no Teams.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e criar um aplicativo simples do Teams. Para obter mais informações, [consulte criar seu primeiro aplicativo do Microsoft Teams "Hello, World!".](../build-your-first-app/build-and-run.md) 

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo: 

* **Configurações de aplicativos e scaffolding relevantes** para bots
* **Bot** que é registrado automaticamente no Serviço de Bot do Microsoft Azure

**Para criar seu projeto de aplicativo**

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Captura de tela mostrando como criar um aplicativo no teams Toolkit.":::

1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365. 
1. Na tela Selecionar projeto, selecione Bots de conversa: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Captura de tela mostrando como criar um novo bot no teams Toolkit.":::

1. Na tela **Configurar projeto,** insira um nome para seu bot. Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.
1. Selecione **Criar um novo Registro de** Bot Criar  >  **Bot,** conforme mostrado na imagem a seguir:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Captura de tela mostrando a nomeação de novo bot no teams Toolkit.":::

    Se tiver êxito, seu novo bot terá um status **Registrado.** Agora seu bot é registrado automaticamente no Serviço de Bot do Microsoft Azure. 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Captura de tela mostrando o registro de novo bot no teams Toolkit.":::

1. Selecione **Concluir** na parte inferior da tela e salve seu projeto em seu computador.  

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o teams Toolkit. Vamos ver os principais componentes para a criação de um bot:

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Captura de tela mostrando um scaffold de projeto no teams Toolkit.":::

Se você criou uma guia em outro tutorial, o scaffolding do aplicativo para o bot é diferente. Ao contrário das guias, o desenvolvimento de bot não exige que você crie nenhum componente web front-end ou use o SDK do cliente JavaScript do Teams.  Em vez disso, o scaffolding usa o [Microsoft Bot Framework](https://dev.botframework.com/), que é um SDK de código aberto para criar bots inteligentes de nível empresarial que podem funcionar na Web, no celular e, claro, no Teams! 

O arquivo, localizado no diretório raiz do seu projeto, é o manipulador específico do Teams que lida com atividades de bot, como como o bot responde `botActivityHandler.js` a mensagens específicas. O scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, é o manipulador específico do Teams que lida com atividades de bot, como como o bot responde a mensagens `botActivityHandler.js` específicas.

## <a name="3-securely-expose-your-localhost-to-the-internet"></a>3. Expor seu localhost com segurança à Internet

Dê uma olhada no arquivo, que cria um servidor HTTP e lida com o roteamento para ouvir solicitações `index.js` de entrada para seu bot. A URL do ponto de extremidade do seu `/api/messages` aplicativo é para responder às solicitações do cliente: 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

Para encaminhar as solicitações para a lógica do bot, você deve configurar uma URL publicamente acessível, como , em `https://example.com/api/messages` vez de `https://localhost` . Como seu aplicativo está em execução no momento do seu localhost, você deve *canalizando* a rede.

O túnel é um protocolo que permite que você transporte dados em uma rede. E o túnel localhost fornece uma conexão entre o computador local e uma conexão remota. Para expor seu localhost com segurança à Internet, recomendamos que você use a ferramenta de terceiros chamada, **ngrok**. Isso lhe dará uma URL segura. 

1. Vá para o [site ngrok.com](https://ngrok.com/download) e siga a instrução para instalar e configurar o ngrok em seu ambiente. 
    
    Adicione o caminho completo ao arquivo ngrok.exe que você instalou à variável de ambiente PATH do sistema. As etapas exatas são específicas do shell que você está usando.

1.  Depois de terminar de defini-lo, abra um terminal e execute `ngrok http -host-header=rewrite 3978` . 

    Agora o ngrok fornece uma URL pública e segura que encaminha para o seu localhost na porta 3978, portanto, copie a URL HTTPS, por exemplo, conforme mostrado na captura de tela abaixo, já que o Teams requer conexões `https://287a4f4223bc.ngrok.io` HTTPS: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Captura de tela mostrando o tunelamento de localhost com ngrok.":::

1. Registre a URL no manifesto do aplicativo. 

## <a name="4-register-your-bot-endpoint"></a>4. Registre seu ponto de extremidade de bot

Para usar um bot no Teams, você deve registrá-lo com o Serviço bot do Azure. Isso é feito automaticamente quando você configura seu aplicativo usando o teams Toolkit.

Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens de usuário, ou solicitações, enviadas para o bot. Normalmente, a URL se parece com `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. Em Visual Studio Código, abra o **Microsoft Teams Toolkit**.
1. Selecione **Bots**  >  **Registros de bots existentes** e selecione o bot que você criou durante a instalação. 
1. No campo **endereço do ponto** de extremidade bot, insira a URL do ngrok, por exemplo, , onde você está hospedando o bot e `https://287a4f4223bc.ngrok.io` anexar a `/api/messages` ele:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Captura de tela mostrando como túnel localhost com ngrok.":::

    Seu bot poderá responder a mensagens no Teams depois de configurar o ponto de extremidade corretamente. 

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

1. Em Visual Studio Código, selecione a **chave F5** para iniciar um cliente Web do Teams.
1. Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**. 

   > [!Note]
   > Por padrão, o aplicativo é adicionado à sua mensagem de chat direta 1:1, no entanto, você pode optar por instalá-la a uma equipe ou chat clicando na pequena seta ao lado de **Adicionar para mim**. Neste tutorial, vamos clicar em Adicionar.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Captura de tela mostrando o localhost de tunelamento com ngrok.":::

## <a name="7-test-your-bot"></a>7. Teste seu bot

Vamos dizer "Olá" para seu bot.

* Na caixa de redação, envie uma `Hello` mensagem.
    Seu bot responde a algo como a seguinte mensagem:

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Uma captura de tela mostrando um usuário dizer &quot;Hello&quot; para um bot do Teams e obter uma resposta.":::

    Agora você criou um bot básico do Teams que pode se comunicar com usuários um-a-um ou em configurações de grupo (canais e chats) 🎉

## <a name="troubleshoot-your-bot"></a>Solucionar problemas de seu bot

As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>Bot não está conectado ao Teams


Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está conectado ao canal do Teams do Serviço de Bot [do Azure ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Teams. Nesse caso, um canal é como o Serviço bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="see-also"></a>Confira também

* [Noções básicas de bot](../bots/bot-basics.md)
* [Criar uma guia pessoal para o Microsoft Teams](../build-your-first-app/build-personal-tab.md)
* [Veja o que mais os bots do Teams podem fazer com um de nossos exemplos](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Princípios básicos de conversas](../bots/how-to/conversations/conversation-basics.md)
* [Diretrizes de design](../bots/design/bots.md) 
* [Modelos de interface do usuário prontos para produção](../concepts/design/design-teams-app-ui-templates.md)
* [Autenticação bot no Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Criar um bot sem o kit de ferramentas](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)
