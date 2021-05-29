---
title: 'Introdução: Crie sua primeira extensão de mensagens'
author: adrianhall
description: Crie uma extensão de mensagens para o Microsoft Teams usando o Kit de Ferramentas do Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: ad341c386cc9e1bf03cf6e25c0d8be8add0880c6
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "52698100"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a>Crie e execute sua primeira extensão de mensagens para o Microsoft Teams

Há dois tipos de **extensões de mensagens** do Teams:

- [Comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) permitem pesquisar sistemas externos e inserir os resultados dessa pesquisa em uma mensagem em forma de cartão.
- [Comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md) permitem que você apresente aos usuários um pop-up modal para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Teams.

Neste tutorial, você criará um *comando de pesquisa* para pesquisar dados externos e inserir os resultados em uma mensagem.  

## <a name="before-you-begin"></a>Antes de começar

Certifique-se de que seu ambiente de desenvolvimento está pronto instalando os [Pré-requisitos](prerequisites.md)

> [!div class="nextstepaction"]
> [Instalar Pré-requisitos](prerequisites.md)

## <a name="create-your-project"></a>Crie seu projeto

Use o Kit de Ferramentas do Teams para criar seu primeiro projeto:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Abra o Kit de Ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code.":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Local do link Criar Novo Projeto na barra lateral do Kit de Ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do Assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar recursos**, selecione **Extensão de Mensagem** e desmarque **Guia**. Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar recursos ao seu novo aplicativo.":::

1. Na etapa **registro do Bot**, selecione **Criar um novo registro de bot**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

   > [!NOTE]
   > As extensões de mensagens dependem dos bots para fornecer uma caixa de diálogo entre o usuário e seu código.

1. Na etapa **Linguagem de Programação**, selecione **JavaScript**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione uma pasta de espaço de trabalho.  Uma pasta será criada dentro da pasta do espaço de trabalho para o projeto que você está criando.

1. Insira um nome adequado para o aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.  Pressione **Enter** para continuar.

O aplicativo Teams será criado em poucos segundos.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Use o CLI `teamsfx` para criar seu primeiro projeto.  Inicie com a pasta onde você deseja criar a pasta de projeto.

``` bash
teamsfx new
```

O CLI faz algumas perguntas para criar o projeto.  Cada pergunta dirá como respondê-la (por exemplo, para usar as teclas de direção para selecionar uma opção).  Quando você tiver respondido à pergunta, confirme sua escolha pressionando **Enter**.

1. Selecione **Criar um novo aplicativo do Teams**.
1. Selecione o **de Extensão de** mensagem e desmarque o **guia** recurso.
1. Selecione **Criar um novo registro de bot**.
1. Selecione **JavaScript** como a linguagem de programação.
1. Pressione **Enter** para selecionar a pasta de espaço de trabalho padrão.
1. Insira um nome adequado para o aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.

Depois que todas as perguntas foram respondidas, seu projeto será criado.

---

## <a name="take-a-tour-of-the-source-code"></a>Fazer um tour pelo código-fonte

Se desejar ignorar esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).

Uma extensão de mensagens usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com seu serviço por meio de uma conversa.  Após a estruturação, seu projeto terá a seguinte aparência:

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

O código do bot é armazenado no diretório `bot`.  O `bots/messageExtensionBot.js` é o ponto de entrada principal da extensão de mensagens.

> [!Tip]
> Familiarize-se com bots fora do Teams antes de integrar seu primeiro bot no Teams.  Para saber mais sobre bots, confira os tutoriais de [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).

## <a name="run-your-app-locally"></a>Executar o aplicativo localmente

O Kit de Ferramentas do Teams permite hospedar o aplicativo localmente.  Para fazer isso:

- Um Aplicativo Azure Active Directory é registrado no locatário do M365.
- Um manifesto do aplicativo é enviado ao Portal do Desenvolvedor para o Teams.
- Uma API é executada localmente usando as Ferramentas Principais de Funções do Azure para dar suporte ao seu aplicativo.
- [ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e sua extensão de mensagens.

Para criar e executar o aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar o aplicativo no modo de depuração.

   > Quando você executar o aplicativo pela primeira vez, todas as dependências serão baixadas e o aplicativo será criado.  Uma janela do navegador é aberta automaticamente quando o build é concluído.  Isso pode levar de 3 a 5 minutos para ser concluído.

1. O Teams é carregado em um navegador da Web e você será solicitado a entrar. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Entre com sua conta do M365.

1. Pressione **Adicionar** para adicionar o aplicativo à sua conta.

Depois que o aplicativo for carregado, você será levado diretamente para uma caixa de diálogo de pesquisa:

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Sua extensão de mensagens baseada em pesquisa em ação":::

Digite algum texto na caixa de pesquisa e selecione uma das opções.  Um cartão adaptativo será adicionado à sua caixa de entrada.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você executar seu aplicativo localmente no depurador.</summary>

Quando você pressionou F5, o Kit de Ferramentas do Teams:

1. Registrou o aplicativo com o Azure Active Directory.
1. Registrou seu aplicativo para "sideloading" no Microsoft Teams.
1. Começou o back-end do aplicativo em execução localmente usando [Ferramentas Principais de Função do Azure](/azure/azure-functions/functions-run-local?#start).
1. Começou um túnel ngrok para que o Teams possa se comunicar com seu aplicativo.
1. Iniciou o Microsoft Teams com um comando para instruir o Teams a carregar o aplicativo por sideload.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</summary>

Para executar seu aplicativo com êxito no Teams, você deve ter uma conta de desenvolvimento do Microsoft 365 que permita o sideloading do aplicativo. Para saber mais sobre como abrir contas, confira [Pré-requisitos](prerequisites.md#enable-sideloading).

> [!TIP]
> Verifique se há problemas antes de carregar seu aplicativo por sideload, usando a [ferramenta de validação de aplicativo](https://dev.teams.microsoft.com/appvalidation.html), que está inclusa no kit de ferramentas. Corrija os erros para carregar o aplicativo por sideload com êxito.
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary>Saiba o que acontece quando você implanta seu aplicativo no Azure</summary>

Antes da implantação, o aplicativo estava sendo executado localmente:

1. O back-end é executado usando _Ferramentas Principais de Funções do Azure_.
1. O ponto de extremidade HTTP do aplicativo, em que o Microsoft Teams carrega o aplicativo, é executado localmente.

A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (carregamento) do código de back-end e front-end do aplicativo para o Azure. O back-end usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo Azure e o Serviço Azure Bot.

</details>

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre outros métodos para criar aplicativos do Teams:

- [Criar um aplicativo do Teams com o React](first-app-react.md)
- [Criar um aplicativo do Teams com o Blazor](first-app-blazor.md)
- [Criar um aplicativo do Teams como uma Web Part do Microsoft Office SharePoint Online](first-app-spfx.md) (Azure não necessário)
- [Criar um bot de conversa](first-app-bot.md)
