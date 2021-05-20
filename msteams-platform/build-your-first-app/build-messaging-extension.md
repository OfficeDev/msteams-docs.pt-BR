---
title: Comece - Construa uma extensão de mensagens
author: girliemac
description: Crie rapidamente uma extensão de mensagens Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: c120a5b5d878c549cde008c3e1ccc71743a4e24f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566058"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a>Construa sua primeira extensão de mensagens para Microsoft Teams

Existem dois tipos de *extensões* de mensagens Teams: [comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e [comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md).

Este tutorial ensina você a criar um *comando de pesquisa* (também conhecido como *extensão de mensagens baseada em pesquisa),* que é um atalho para encontrar conteúdo externo e compartilhá-lo em Teams. Os usuários podem acessar comandos de pesquisa da Teams compor ou caixa de comando.

## <a name="what-youll-learn"></a>O que você vai aprender

* Crie um robô de extensão de projeto de aplicativo e de gerenciamento de mensagens usando o Microsoft Teams Toolkit para Visual Studio Code.
* Entenda as configurações do aplicativo e os andaimes relevantes para as extensões de mensagens.
* Hospede um aplicativo localmente.
* Configure o bot para sua extensão de mensagens.
* Sideload e teste uma extensão de mensagens em Teams.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e construir um aplicativo de Teams simples. Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para sua extensão de mensagens:

* **Configurações de aplicativos e andaimes** relevantes para extensões de mensagens.
* **Bot** para sua extensão de mensagens que é automaticamente registrado no serviço de Microsoft Azure Bot.

**Para criar seu projeto de aplicativo**

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha **Criar um novo aplicativo de Teams**.
1. Quando solicitado, faça login com sua conta de desenvolvimento Microsoft 365.
1. Na tela do **projeto Select,** na Pesquisa **de Extensões de Mensagens,** clique em  >   **JS (JavaScript)**. 
1. Digite um nome para o aplicativo Teams. Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.
1. Selecione **Criar um novo Bot** e clique em Criar registro de **bot.** Se for bem sucedido, seu novo bot terá um *status registrado.* Agora, seu bot está automaticamente registrado no serviço de Microsoft Azure Bot. 
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em sua máquina local.

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do seu aplicativo

Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.

* Configurações do aplicativo: Para visualizar ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e vá para **extensões de mensagens**.
* Andaimes de aplicativos: O andaime do aplicativo fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com como sua extensão de mensagens (ou tecnicamente, o [bot da extensão de mensagens](#4-configure-the-bot-for-your-messaging-extension)) responde a consultas de pesquisa em Teams.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Configure um túnel seguro para o seu aplicativo

Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor web local (porta 3978). Você vai usar [ngrok](https://ngrok.com/download) para montar um túnel seguro para o localhost. Consulte [construir seu primeiro bot para Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) para obter detalhes. 

1. Se você ainda não fez isso, instale [ngrok](https://ngrok.com/download).
1. Em um terminal, `ngrok http -host-header=rewrite 3978` corra.
1. Copie a URL HTTPS na saída (por `https://468b9ab725e9.ngrok.io` exemplo), já que Teams requer conexões HTTPS.

   Com esta URL, Teams (que requer conexões HTTPS) será capaz de túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Configure o bot para sua extensão de mensagens

As extensões de mensagens dependem de bots para enviar e processar solicitações de usuários de Teams para o seu serviço hospedado. O bot deve ser registrado no Azure Bot Service, que foi feito quando você configurar seu aplicativo usando o Teams Toolkit.

Você ainda deve especificar uma URL de ponto final do bot para receber e processar consultas de pesquisa na extensão de mensagens. Normalmente, a URL se parece `https://HOST_URL/api/messages` com . Você pode configurar isso rapidamente no kit de ferramentas.

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha Open **Microsoft Teams Toolkit**.
1. Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a configuração.
1. No campo **de endereços de ponto final do Bot,** digite a URL ngrok (por `https://468b9ab725e9.ngrok.io` exemplo, ) onde você está hospedando o bot e `/api/messages` anexar a ele.

   Seu bot será capaz de lidar com consultas na sua extensão de mensagens.

## <a name="5-build-and-run-your-app"></a>5. Construa e execute seu aplicativo

Você configurou uma URL para hospedar sua extensão de mensagens e configurou-a para lidar com pesquisas. É hora de colocar seu aplicativo em funcionamento.

1. Abra o terminal e vá para o diretório raiz do seu projeto de aplicativo.
1. `npm install`Corra.
1. `npm start`Corra.

   Se for bem-sucedido, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está ouvindo a atividade em seu `localhost` :

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Acarregue a extensão de mensagens em Teams

Com a extensão de mensagens em execução, você pode instalá-la em Teams.

> [!TIP]
> Se você nunca mais regou um aplicativo de Teams antes e se deparar com problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Em Visual Studio Code, selecione a tecla **F5** para lançar um Teams cliente web.
1. No aplicativo instalar a caixa de diálogo, selecione **Adicionar para mim**.

## <a name="7-test-your-messaging-extension"></a>7. Teste sua extensão de mensagens

Saiba como as extensões de mensagens funcionam em um bate-papo Teams.

1. Comece uma nova conversa. Na caixa de composição, selecione **Mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: e selecione o aplicativo de extensão de mensagens que você acabou de carregar lateralmente.
1. Tente procurar algo (por exemplo, **Tickets**). Se o seu aplicativo estiver funcionando, você verá os resultados de pesquisa de amostra (você pode adicionar o seu próprio mais tarde).

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de composição Teams.":::

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para completar este tutorial.

**Bot não está conectado a Teams**

Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja [conectado ao *canal* Teams do Azure Bot Service](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal em Teams. Neste caso, um canal é como o Azure Bot Service conecta seu bot a Teams ou outro [aplicativo de comunicação suportado da Microsoft ou de terceiros.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="see-also"></a>Confira também

* [Teams compor ou mandar caixa](../messaging-extensions/what-are-messaging-extensions.md) 
* [Inclua um recurso de desvendamento de link](../messaging-extensions/how-to/link-unfurling.md)
* [Diretrizes de design](../messaging-extensions/design/messaging-extension-design.md) 
* [Modelos de interface do usuário prontos para produção](../concepts/design/design-teams-app-ui-templates.md) 
* [Adicionar autenticação](../messaging-extensions/how-to/add-authentication.md)
* [Crie uma extensão de mensagens baseada em ação](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Definir comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [Responda às pesquisas dos usuários](../messaging-extensions/how-to/search-commands/respond-to-search.md)
