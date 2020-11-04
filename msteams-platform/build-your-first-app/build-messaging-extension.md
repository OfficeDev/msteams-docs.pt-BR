---
title: Introdução-criar uma extensão de mensagens
author: heath-hamilton
description: Crie rapidamente uma extensão de mensagens do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: 68f2bf7c71182499dc8f6f50e03ea3d97f03ded2
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877076"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Criar uma extensão de mensagens para o Microsoft Teams

Há dois tipos de extensões de *mensagens* do Microsoft Teams: [comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e [comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md).

Nesta lição, você criará um *comando de pesquisa* (também conhecido como uma *extensão de mensagens baseada em pesquisa* ), que é um atalho para localizar conteúdo externo e compartilhá-lo no Microsoft Teams. Os usuários podem acessar os comandos de pesquisa a partir da [caixa de comando ou de composição do teams](../messaging-extensions/what-are-messaging-extensions.md).

## <a name="your-assignment"></a>Sua atribuição

O suporte técnico da sua organização comunica-se com os usuários por meio do Teams, mas os tíquetes residem em um sistema separado. Isso significa que a equipe de suporte deve continuamente voltar e avançar entre os aplicativos. Você investigará como você pode reduzir essa alteração de contexto por meio da criação de uma extensão de mensagens simples baseada em pesquisa para o Microsoft Teams.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo e um bot de extensão de mensagens usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar as propriedades de manifesto do aplicativo e alguns dos scaffolding relevantes para as extensões de mensagens
> * Hospedar um aplicativo localmente
> * Configurar o bot para sua extensão de mensagens
> * Sideload e testar uma extensão de mensagens no Microsoft Teams

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para sua extensão de mensagens:

* **Manifesto de aplicativo e scaffolding** relevantes para extensões de mensagens
* **Bot** para sua extensão de mensagens que é automaticamente registrado com o serviço de bot do Microsoft Azure

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Adicionar recursos** , selecione **extensão de mensagens** e **Avançar**.
1. Na tela **Configurar extensão de mensagens** , faça o seguinte:
    1. Escolha somente a opção **baseado em pesquisa** para o tipo de extensão de mensagens.
    1. Selecione **criar um novo bot** e **login** para entrar com sua conta de desenvolvimento do Microsoft 365.
    1. Armazene sua ID de bot e senha (você precisará de um pouco mais tarde).
    1. Opcion Insira um nome personalizado para o bot e selecione **criar**. (Este não é o nome do aplicativo Teams que você já especificou.)
    1. Selecione **não** para a opção vincular Unfurling.</br>
:::image type="content" source="../assets/images/build-your-first-app/choose-me-search.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot para sua extensão de mensagens.":::
1. Selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-identify-relevant-app-project-components"></a>2. identificar componentes de projeto de aplicativo relevantes

Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.

### <a name="app-manifest"></a>Manifesto do aplicativo

O trecho de código a seguir do manifesto do aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra as propriedades e os valores padrão relevantes para as extensões de mensagens.

```JSON
"composeExtensions": [
    {
        "botId": "{botId0}",
        "canUpdateConfiguration": true,
        "commands": [
            {
                "id": "searchQuery",
                "context": [
                    "compose",
                    "commandBox"
                ],
                "description": "Test command to run query",
                "title": "Search",
                "type": "query",
                "parameters": [
                    {
                        "name": "searchQuery",
                        "title": "Search Query",
                        "description": "Your search query",
                        "inputType": "text"
                    }
                ]
            }
        ]
    }
],
```

Vamos entender algumas das propriedades que o kit de ferramentas criou para você. (Veja a lista completa de propriedades com suporte [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) .)

* `botId`: A ID do bot que você criou configurando seu projeto. (Armazenado no `{botId0}` , você pode encontrar a ID real no `Development.env` .)
* `commands`: Comandos disponíveis para a extensão de mensagens. O kit de ferramentas ofereceu a você scaffolding um comando de pesquisa.
* `context`: Onde os usuários podem invocar a extensão de mensagens. Nesse caso, você pode iniciar a extensão de mensagens da caixa de comando ou de composição do teams.
* `description`: Texto de ajuda da interface do usuário que indica o que o comando faz ou como usá-lo.
* `parameters`: Inclui todos os parâmetros aceitos por um comando (você deve ter pelo menos um e até cinco).
* `parameters.description`: O texto da ajuda da interface do usuário que descreve a finalidade do parâmetro ou a entrada de exemplo.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding inclui um `.env` arquivo, localizado no diretório raiz do seu projeto, que armazena a ID e a senha do bot da extensão do sistema de mensagens.

Além disso, no diretório raiz, há um `botActivityHandler.js` arquivo para lidar com a sua extensão de mensagens (ou tecnicamente, o [bot da extensão de mensagens](#4-configure-the-bot-for-your-messaging-extension)) responde a consultas de pesquisa no Microsoft Teams.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).

1. Em um terminal, execute `ngrok http -host-header=rewrite 3978` .
1. Copie a URL HTTPS na saída, pois o Microsoft Teams requer conexões HTTPS.
1. Em seu `.publish` diretório, abra `Development.env` .
1. Substitua o `baseUrl0` valor pela URL copiada. (Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

O manifesto do aplicativo está apontando para o local em que você está hospedando o bot usado pela extensão de mensagens.

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Configure o bot para sua extensão de mensagens

As extensões de mensagens dependem de bots para enviar e processar solicitações de usuário do teams para seu serviço hospedado.

O bot deve ser registrado no serviço do Azure bot, que foi feito quando você configurou seu aplicativo usando o Teams Toolkit.

### <a name="specify-your-bot-id-and-password"></a>Especificar a ID e a senha do bot

Quando o bot é registrado com o serviço de bot do Azure, é atribuída uma ID e uma senha que o aplicativo de equipes deve conhecer.

1. Localize a ID e a senha do bot que você armazenou durante a instalação do kit de ferramentas.
1. No diretório raiz, abra o `.env` arquivo.
1. Defina sua ID de bot e senha para `BotId` as `BotPassword` Propriedades e, respectivamente.

### <a name="add-the-bot-endpoint-address"></a>Adicionar o endereço do ponto de extremidade do bot

Você deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens. Normalmente, a URL é semelhante `https://HOST_URL/api/messages` . Você pode configurar isso rapidamente no kit de ferramentas do teams.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. Vá para **Gerenciamento de bot > registros de bot existentes** e selecione o bot que você criou durante a instalação.
1. No campo **endereço do ponto de extremidade do bot** , insira o servidor Web local onde você está hospedando o bot ( `baseUrl10` valor) e anexe `/api/messages` a ele.

O bot será capaz de lidar com consultas em sua extensão de mensagens.

## <a name="5-run-your-app"></a>5. Execute o aplicativo

Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas. É hora de colocar seu aplicativo em funcionamento.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Se tiver êxito, você verá algo parecido com a seguinte mensagem, indicando que o serviço de extensão de mensagens está ouvindo a atividade no seu `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Sideload sua extensão de mensagens no Microsoft Teams

Com sua extensão de mensagens em execução, você pode instalá-lo no Microsoft Teams.

> [!TIP]
> Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#5-sideload-your-app-in-teams).

1. Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload.
1. Selecione **aplicativos** e, em seguida, escolha **carregar um aplicativo personalizado**.
1. Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` .
1. Na janela instalar, selecione **Adicionar** para instalar seu aplicativo.

## <a name="7-test-your-messaging-extension"></a>7. testar sua extensão de mensagens

Saiba como as extensões de mensagens funcionam em um chat do Microsoft Teams.

1. Inicie um novo chat. Na caixa redigir, selecione **mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: e escolha o aplicativo de extensão de mensagens que você acabou de suplementos foi feito.
1. Tente pesquisar algo (por exemplo, "bilhetes"). Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar o seu próprio mais tarde).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de composição do teams.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem uma extensão de mensagens básica do teams que está configurada para pesquisar conteúdo externo na caixa redigir ou comando.

## <a name="next-steps"></a>Próximas etapas

Confira as seguintes páginas para continuar e criar uma extensão de mensagens totalmente em destaque:

1. [Definir comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) que são relevantes para o serviço.
1. Configure seu serviço para [responder às pesquisas dos usuários](../messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="troubleshooting"></a>Solução de problemas

As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.

### <a name="toolkit-setup-fails"></a>Falha na instalação do kit de ferramentas

Ao configurar seu projeto de aplicativo com o Teams Toolkit, você recebe um erro depois de selecionar a opção **criar um novo bot** e fazer logon com sua conta de desenvolvimento do Microsoft 365.

Isso pode ser um problema de autenticação. Siga estas etapas para concluir a configuração do seu projeto.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **sair**.
1. Execute o processo de instalação novamente, conectando-se com a mesma conta e criando um novo bot.

### <a name="bot-isnt-connected-to-teams"></a>O bot não está conectado ao Teams

Se você instalou o aplicativo, mas não está funcionando, certifique-se de que o bot da extensão de mensagens está [conectado ao *canal* da equipe do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

É importante entender que isso não é o mesmo que um canal no Microsoft Teams. Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).

## <a name="learn-more"></a>Saiba mais

* [Incluir um recurso de Unfurling de link](../messaging-extensions/how-to/link-unfurling.md)
* [Adicionar autenticação](../messaging-extensions/how-to/add-authentication.md)
* [Criar uma extensão de mensagens baseada na ação](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft bot Framework](https://dev.botframework.com/)
