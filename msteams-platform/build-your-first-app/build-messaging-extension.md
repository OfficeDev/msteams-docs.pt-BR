---
title: Introdução-criar uma extensão de mensagens
author: heath-hamilton
description: Crie rapidamente uma extensão de mensagens do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 160878d92969d57680e6fa25eb6fc13e82bf2a82
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931747"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Criar uma extensão de mensagens para o Microsoft Teams

Há dois tipos de *extensões de mensagens* de aplicativos do teams: [comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e comandos de [ação](../messaging-extensions/how-to/action-commands/define-action-command.md).

Nesta lição, você criará um *comando de pesquisa* (também conhecido como uma *extensão de mensagens baseada em pesquisa* ), que é um atalho para localizar conteúdo externo e compartilhá-lo no Microsoft Teams. Os usuários podem acessar os comandos de pesquisa a partir da [caixa de comando ou de composição do teams](../messaging-extensions/what-are-messaging-extensions.md).

## <a name="your-assignment"></a>Sua atribuição

O suporte técnico da sua organização comunica-se com os usuários por meio do Teams, mas os tíquetes residem em um sistema separado. Isso significa que a equipe de suporte deve continuamente voltar e avançar entre os aplicativos. Você investigará como você pode reduzir essa alteração de contexto por meio da criação de uma extensão de mensagens simples baseada em pesquisa para o Microsoft Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot de extensão de mensagens usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar as configurações do aplicativo e alguns dos scaffolding relevantes para as extensões de mensagens
> * Hospedar um aplicativo localmente
> * Configurar o bot para sua extensão de mensagens
> * Sideload e testar uma extensão de mensagens no Microsoft Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para sua extensão de mensagens:

* **Configurações de aplicativo e scaffolding** relevantes para extensões de mensagens
* **Bot** para sua extensão de mensagens que é automaticamente registrado com o serviço de bot do Microsoft Azure

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos** , selecione **extensão de mensagens** e **Avançar**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Configurar extensão de mensagens** , faça o seguinte:
    1. Escolha somente a opção **baseado em pesquisa** para o tipo de extensão de mensagens.
    1. Selecione **criar um novo bot** e, em seguida, **crie o registro de bot**. Se tiver êxito, o novo bot terá um status **registrado** .
    1. Selecione **não** para a opção vincular Unfurling.
1. Selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. identificar componentes de projeto de aplicativo relevantes

Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.

### <a name="app-configurations"></a>Configurações do aplicativo

Para exibir ou atualizar as configurações da extensão de mensagens, selecione **app Studio** no kit de ferramentas e vá para **extensões de mensagens**.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para manipular como sua extensão de mensagens (ou tecnicamente, o [bot da extensão de mensagens](#4-configure-the-bot-for-your-messaging-extension)) responde a consultas de pesquisa no Microsoft Teams.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).

1. Caso ainda não tenha feito isso, instale o [ngrok](https://ngrok.com/download).
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo,), pois o Microsoft `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.

Com esta URL, o Teams (que requer conexões HTTPS) será habilitado para encapsular onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Configure o bot para sua extensão de mensagens

As extensões de mensagens dependem de bots para enviar e processar solicitações de usuário do teams para seu serviço hospedado. O bot deve ser registrado no serviço do Azure bot, que foi feito quando você configurou seu aplicativo usando o Teams Toolkit.

Você ainda deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens. Normalmente, a URL é semelhante `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. Vá até **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **endereço do ponto de extremidade do bot** , insira a URL do ngrok (por exemplo, `https://468b9ab725e9.ngrok.io` ) em que você está hospedando o bot e anexe `/api/messages` a ela.

O bot será capaz de lidar com consultas em sua extensão de mensagens.

## <a name="5-build-and-run-your-app"></a>5. Compilar e executar o aplicativo

Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas. É hora de colocar seu aplicativo em funcionamento.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá a seguinte mensagem indicando que o serviço de extensão de mensagens está ouvindo a atividade no seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Sideload sua extensão de mensagens no Microsoft Teams

Com sua extensão de mensagens em execução, você pode instalá-lo no Microsoft Teams.

> [!TIP]
> Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.
1. Na caixa de diálogo instalar aplicativo, selecione **Adicionar para mim**.

## <a name="7-test-your-messaging-extension"></a>7. testar sua extensão de mensagens

Saiba como as extensões de mensagens funcionam em um chat do Microsoft Teams.

1. Inicie um novo chat. Na caixa redigir, selecione **mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: e escolha o aplicativo de extensão de mensagens que você acabou de suplementos foi feito.
1. Tente pesquisar algo (por exemplo, **tíquetes** ). Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar o seu próprio mais tarde).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de composição do teams.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem uma extensão de mensagens básica do teams que está configurada para pesquisar conteúdo externo na caixa redigir ou comando.

## <a name="next-steps"></a>Próximas etapas

Confira as seguintes páginas para continuar e criar uma extensão de mensagens totalmente em destaque:

1. [Definir comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) que são relevantes para o serviço.
1. Configure seu serviço para [responder às pesquisas dos usuários](../messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>O bot não está conectado ao Teams

Se você instalou o aplicativo, mas não está funcionando, certifique-se de que o bot da extensão de mensagens está [conectado ao *canal* da equipe do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Microsoft Teams. Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).

## <a name="learn-more"></a>Saiba mais

* [Incluir um recurso de Unfurling de link](../messaging-extensions/how-to/link-unfurling.md)
* [Adicionar autenticação](../messaging-extensions/how-to/add-authentication.md)
* [Criar uma extensão de mensagens baseada na ação](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft bot Framework](https://dev.botframework.com/)
