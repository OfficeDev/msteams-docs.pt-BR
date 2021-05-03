---
title: Começar - Criar uma extensão de mensagens
author: girliemac
description: Crie rapidamente uma extensão Microsoft Teams de mensagens usando a Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: 91a5a15697163ee9103607511047a6411a5acf1a
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068756"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a>Crie sua primeira extensão de mensagens para Microsoft Teams

Há dois tipos de extensões Teams *de mensagens:* comandos [de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e comandos [de ação.](../messaging-extensions/how-to/action-commands/define-action-command.md)

Este tutorial ensina a criar um comando de pesquisa *(também* conhecido como extensão de mensagens baseada em pesquisa *),* que é um atalho para localizar conteúdo externo e compartilhamento no Teams. Os usuários podem acessar comandos de pesquisa Teams caixa de comando ou composição.

## <a name="what-youll-learn"></a>O que você aprenderá

* Crie um projeto de aplicativo e um bot de extensão de mensagens usando o Microsoft Teams Toolkit para Visual Studio Code.
* Entenda as configurações do aplicativo e os scaffolding relevantes para extensões de mensagens.
* Hospedar um aplicativo localmente.
* Configure o bot para sua extensão de mensagens.
* Fazer sideload e testar uma extensão de mensagens Teams.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e criar um aplicativo Teams simples. Para obter mais informações, [consulte create your first Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

A Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para a extensão de mensagens:

* **Configurações de aplicativo e scaffolding relevantes** para extensões de mensagens
* **Bot** para sua extensão de mensagens que é registrada automaticamente com o serviço Microsoft Azure Bot

**Para criar seu projeto de aplicativo**

1. Em Visual Studio Code, selecione **Microsoft Teams** barra de atividades à esquerda e escolha Criar um novo Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. Quando solicitado, entre com sua conta Microsoft 365 de desenvolvimento.
1. Na tela **Selecionar projeto,** em **Pesquisa de Extensões de**  >  **Mensagens,** clique em **JS (JavaScript)**. 
1. Insira um nome para seu Teams app. Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.
1. Selecione **Criar um novo Bot** e clique em Criar Registro **de** Bot. Se tiver êxito, seu novo bot terá um status *Registrado.* Agora, seu bot é registrado automaticamente com o serviço Microsoft Azure Bot. 
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em seu computador local.

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.

* Configurações do aplicativo: para exibir ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e acesse **Extensões de mensagens.**
* Estrutura de aplicativos: o scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como sua extensão de mensagens (ou tecnicamente, o bot da extensão de mensagens ) responde às consultas de pesquisa no `botActivityHandler.js` Teams. [](#4-configure-the-bot-for-your-messaging-extension)

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978). Você usará o [ngrok](https://ngrok.com/download) para configurar um túnel seguro para localhost. Consulte [build your first bot for Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) for details. 

1. Caso ainda não tenha feito isso, instale [ngrok](https://ngrok.com/download).
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo, ) já que Teams `https://468b9ab725e9.ngrok.io` requer conexões HTTPS.

   Com essa URL, Teams (que requer conexões HTTPS) poderá túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Configure o bot para sua extensão de mensagens

As extensões de mensagens dependem de bots para enviar e processar solicitações de usuários Teams para seu serviço hospedado. O bot deve ser registrado no Serviço bot do Azure, que foi feito quando você configura seu aplicativo usando o Teams Toolkit.

Você ainda deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens. Normalmente, a URL se parece com `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. Em Visual Studio Code, selecione **Microsoft Teams** à esquerda da Barra de Atividades :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: e escolha Abrir **Microsoft Teams Toolkit**.
1. Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **Endereço do ponto** de extremidade bot, insira a URL do ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` adeque `/api/messages` a ele.

   Seu bot poderá lidar com consultas em sua extensão de mensagens.

## <a name="5-build-and-run-your-app"></a>5. Crie e execute seu aplicativo

Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas. É hora de fazer o aplicativo funcionar.

1. Abra o terminal e vá para o diretório raiz do seu projeto de aplicativo
1. Executar `npm install` .
1. Executar `npm start` .

   Se tiver êxito, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está escutando atividades em seu `localhost` :

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Fazer sideload da extensão de mensagens no Teams

Com a extensão de mensagens em execução, você pode instalá-la Teams.

> [!TIP]
> Se você não tiver sideloaded de um aplicativo Teams antes e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Em Visual Studio Code, selecione a **tecla F5** para iniciar um cliente Teams Web.
1. Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**.

## <a name="7-test-your-messaging-extension"></a>7. Teste sua extensão de mensagens

Saiba como as extensões de mensagens funcionam em um Teams chat.

1. Inicie um novo chat. Na caixa de redação, selecione **Mais** e selecione o aplicativo de extensão de mensagens :::image type="icon" source="../assets/icons/teams-client-more.png"::: que você acabou de fazer sideload.
1. Tente pesquisar algo (por exemplo, **Tíquetes).** Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar seus próprios posteriormente).

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de Teams de composição.":::

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.

**Bot não está conectado ao Teams**

Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja conectado ao canal de Teams do Serviço de Bot [do Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

É importante entender que isso não é o mesmo que um canal no Teams. Nesse caso, um canal é como o Serviço de Bot do Azure conecta seu bot ao Teams ou outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="see-also"></a>Confira também

* [Teams caixa de comando ou composição](../messaging-extensions/what-are-messaging-extensions.md) 
* [Incluir um recurso de desfralização de link](../messaging-extensions/how-to/link-unfurling.md)
* [Diretrizes de design](../messaging-extensions/design/messaging-extension-design.md) 
* [Modelos de interface do usuário prontos para produção](../concepts/design/design-teams-app-ui-templates.md) 
* [Adicionar autenticação](../messaging-extensions/how-to/add-authentication.md)
* [Criar uma extensão de mensagens baseada em ação](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Definir comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [Responder às pesquisas dos usuários](../messaging-extensions/how-to/search-commands/respond-to-search.md)