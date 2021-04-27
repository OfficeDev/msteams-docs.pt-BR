---
title: Começar - Criar uma extensão de mensagens
author: heath-hamilton
description: Crie rapidamente uma extensão de mensagens do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: f3b5bc9c749d5e5276c0c7af7ff92f4ff5a00d0b
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020867"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Criar uma extensão de mensagens para o Microsoft Teams

Há dois tipos de extensões de mensagens *do* Teams: comandos [de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e comandos de [ação.](../messaging-extensions/how-to/action-commands/define-action-command.md)

Nesta lição, você criará um comando de pesquisa *(também* conhecido como extensão de mensagens baseada em pesquisa *),* que é um atalho para localizar conteúdo externo e compartilhamento no Teams. Os usuários podem acessar comandos de pesquisa na [caixa de comando ou composição do Teams.](../messaging-extensions/what-are-messaging-extensions.md)

## <a name="your-assignment"></a>Sua atribuição

O help desk da sua organização se comunica com os usuários por meio do Teams, mas os tíquetes residem em um sistema separado. Isso significa que a equipe de suporte deve ir e voltar constantemente entre aplicativos. Você investigará como reduzir essa alternação de contexto criando uma extensão de mensagens simples baseada em pesquisa para o Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot de extensão de mensagens usando o microsoft Teams Toolkit para Visual Studio Código
> * Identificar as configurações do aplicativo e alguns dos scaffolding relevantes para extensões de mensagens
> * Hospedar um aplicativo localmente
> * Configurar o bot para sua extensão de mensagens
> * Fazer sideload e testar uma extensão de mensagens no Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não entendeu e instalou os [pré-requisitos de](build-first-app-overview.md#get-prerequisites)desenvolvimento do Teams.

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

A Toolkit do Microsoft Teams ajuda você a configurar os seguintes componentes para a extensão de mensagens:

* **Configurações de aplicativo e scaffolding relevantes** para extensões de mensagens
* **Bot** para a extensão de mensagens que é registrada automaticamente com o Serviço de Bot do Microsoft Azure

> [!TIP]
> Se você não tiver criado um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Extensão de Mensagens,** em **seguida, Próximo**.
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.)
1. Na tela **Configurar extensão de mensagens,** faça o seguinte:
    1. Escolha apenas a **opção baseada em** Pesquisa para o tipo de extensão de mensagens.
    1. Selecione **Criar um novo Bot** e Crie Registro de **Bot.** Se tiver êxito, seu novo bot terá um status **Registrado.**
    1. Por enquanto, selecione **Não** para a opção de desalinização do link.
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. Identificar componentes relevantes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o teams Toolkit.

### <a name="app-configurations"></a>Configurações de aplicativo

Para exibir ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e acesse **Extensões de mensagens.**

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como sua extensão de mensagens (ou tecnicamente, o bot da extensão de mensagens ) responde às consultas de pesquisa no `botActivityHandler.js` Teams. [](#4-configure-the-bot-for-your-messaging-extension)

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).

1. Caso ainda não tenha feito isso, instale [ngrok](https://ngrok.com/download).
1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída (por exemplo, ) já que o `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.

Com essa URL, o Teams (que requer conexões HTTPS) poderá túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Configure o bot para sua extensão de mensagens

As extensões de mensagens dependem de bots para enviar e processar solicitações de usuário do Teams para seu serviço hospedado. O bot deve ser registrado com o Serviço bot do Azure, que foi feito quando você configura seu aplicativo usando o teams Toolkit.

Você ainda deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens. Normalmente, a URL se parece com `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas.

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Abrir o Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **Endereço do ponto** de extremidade bot, insira a URL do ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` adeque `/api/messages` a ele.

Seu bot poderá lidar com consultas em sua extensão de mensagens.

## <a name="5-build-and-run-your-app"></a>5. Crie e execute seu aplicativo

Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas. É hora de fazer o aplicativo funcionar.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está escutando atividades em seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Fazer sideload da extensão de mensagens no Teams

Com a extensão de mensagens em execução, você pode instalá-la no Teams.

> [!TIP]
> Se você ainda não fez sideload de um aplicativo do Teams antes e correu para problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Em Visual Studio Código, pressione a **tecla F5** para iniciar um cliente Web do Teams.
1. Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**.

## <a name="7-test-your-messaging-extension"></a>7. Teste sua extensão de mensagens

Saiba como as extensões de mensagens funcionam em um chat do Teams.

1. Inicie um novo chat. Na caixa de redação, selecione **Mais** e escolha o aplicativo de extensão de mensagens :::image type="icon" source="../assets/icons/teams-client-more.png"::: que você acabou de fazer sideload.
1. Tente pesquisar algo (por exemplo, **Tíquetes).** Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar seus próprios posteriormente).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de redação do Teams.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem uma extensão básica de mensagens do Teams configurada para pesquisar conteúdo externo na caixa de composição ou comando.

## <a name="next-steps"></a>Próximas etapas

Consulte as páginas a seguir para continuar e criar uma extensão de mensagens totalmente em destaque:

1. [Defina comandos de](../messaging-extensions/how-to/search-commands/define-search-command.md) pesquisa relevantes ao seu serviço.
1. Configure seu serviço [para responder às pesquisas dos usuários.](../messaging-extensions/how-to/search-commands/respond-to-search.md)

## <a name="troubleshooting"></a>Solução de Problemas

As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.

### <a name="bot-isnt-connected-to-teams"></a>Bot não está conectado ao Teams

Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja conectado ao canal do Teams do Serviço de Bot do [Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

É importante entender que isso não é o mesmo que um canal no Teams. Nesse caso, um canal é como o Serviço bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Saiba mais

* [Incluir um recurso de desfralização de link](../messaging-extensions/how-to/link-unfurling.md)
* Siga nossas [diretrizes de design](../messaging-extensions/design/messaging-extension-design.md) e crie com modelos [de interface](../concepts/design/design-teams-app-ui-templates.md) do usuário prontos para produção para criar uma experiência perfeita.
* [Adicionar autenticação](../messaging-extensions/how-to/add-authentication.md)
* [Criar uma extensão de mensagens baseada em ação](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)

