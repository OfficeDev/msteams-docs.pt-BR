---
title: 'Introdução: Crie sua primeira extensão de mensagens'
author: adrianhall
description: Crie uma extensão de mensagens para o Microsoft Teams usando o Kit de Ferramentas do Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: eaecb045993f8dfd21f4c2c4359a4a3388d659e6
ms.sourcegitcommit: e50cdeb6b7f481e12911b2bb74a8da22af0bffac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2021
ms.locfileid: "52710645"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a>Crie e execute sua primeira extensão de mensagens para o Microsoft Teams

Há dois tipos de **extensões de mensagens** do Teams:

- [Comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) permitem pesquisar sistemas externos e inserir os resultados dessa pesquisa em uma mensagem em forma de cartão.
- [Comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md) permitem que você apresente aos usuários um pop-up modal para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Teams.

Neste tutorial, você criará um *comando de pesquisa* para pesquisar dados externos e inserir os resultados em uma mensagem.  

## <a name="before-you-begin"></a>Antes de começar

Certificar-se de que o seu ambiente de desenvolvimento esteja configurado instalando os [Pré-requisitos](prerequisites.md)

> [!div class="nextstepaction"]
> [Instalar Pré-requisitos](prerequisites.md)

## <a name="create-your-project"></a>Criar o seu projeto

Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Abra o Kit de Ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do Assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar recursos**, selecione **Extensão de Mensagem** e desmarque **Guia**. Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar recursos ao seu novo aplicativo.":::

1. Na etapa **Registro de bot**, selecione **Criar um novo registro de bot**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

   > [!NOTE]
   > As extensões de mensagens dependem dos bots para fornecer uma caixa de diálogo entre o usuário e seu código.

1. Na etapa **Linguagem de Programação**, selecione **JavaScript**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione uma pasta do espaço de trabalho.  Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.

1. Insira um nome adequado para seu aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.  Pressione **Inserir** para continuar.

O seu aplicativo do Teams será criado em alguns segundos.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Use a CLI `teamsfx` para criar o seu primeiro projeto.  Inicie pela pasta onde deseja criar a pasta do projeto.

``` bash
teamsfx new
```

A CLI lhe guiará através de algumas perguntas para criar o projeto.  Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).  Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.

1. Selecione **Criar um novo aplicativo do Teams**.
1. Selecione o **de Extensão de** mensagem e desmarque o **guia** recurso.
1. Selecione **Criar um novo registro de bot**.
1. Selecione **JavaScript** como linguagem de programação.
1. Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.
1. Insira um nome adequado para seu aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.

Assim que todas as perguntas forem respondidas, o seu projeto será criado.

---

## <a name="take-a-tour-of-the-source-code"></a>Faça um tour pelo código-fonte

Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).

Uma extensão de mensagem usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com o seu serviço por meio de uma conversa.  Após o andaime, o seu projeto ficará assim:

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

O código do bot é armazenado no diretório `bot`.  O `bots/messageExtensionBot.js` é o ponto de entrada principal da extensão de mensagens.

> [!Tip]
> Familiarize-se com bots fora do Teams antes de integrar seu primeiro bot no Teams.  Você pode localizar mais informações sobre os bots analisando os tutoriais do [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).

## <a name="run-your-app-locally"></a>Executar o seu aplicativo localmente

O Kit de ferramentas do Teams permite hospedar o seu aplicativo localmente.  Para fazer isso:

- Um Aplicativo Azure Active Directory é registrado no locatário do M365.
- Um manifesto do aplicativo é enviado ao Portal do Desenvolvedor para o Teams.
- Uma API é executada localmente usando as Ferramentas Principais de Funções do Azure para dar suporte ao seu aplicativo.
- [ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e sua extensão de mensagens.

Para criar e executar o aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída.  Isso pode levar de 3 a 5 minutos para ser concluído.

1. O Teams é carregado em um navegador da Web e você será solicitado a entrar. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Entre com sua conta do M365.

1. Pressione **Adicionar** para adicionar o aplicativo à sua conta.

Depois que o aplicativo for carregado, você será levado diretamente para uma caixa de diálogo de pesquisa:

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Sua extensão de mensagens baseada em pesquisa em ação":::

Digite algum texto na caixa de pesquisa e selecione uma das opções.  Um cartão adaptativo será adicionado à sua caixa de entrada.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você executar seu aplicativo localmente no depurador.</summary>

Quando você pressionou F5, o Kit de ferramentas do Teams:

1. Registrou seu aplicativo no Azure Active Directory.
1. Registrou seu aplicativo para "carregamento lateral" no Microsoft Teams.
1. Iniciou o back-end do aplicativo em execução localmente usando as [Ferramentas do Azure Function Core](/azure/azure-functions/functions-run-local?#start).
1. Iniciou um túnel ngrok para que o Teams possa se comunicar com o seu aplicativo.
1. Iniciou o Microsoft Teams com um comando para instruir o Teams a fazer o sideload do aplicativo.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</summary>

Para executar com êxito seu aplicativo no Teams, você deve ter uma conta de desenvolvimento do Microsoft 365 que permite o sideload do aplicativo. Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).

> [!TIP]
> Verifique se há problemas antes de fazer o sideload de seu aplicativo, usando a [ferramenta de validação de aplicativo](https://dev.teams.microsoft.com/appvalidation.html), que está incluída no kit de ferramentas. Corrija os erros para fazer o sideload do aplicativo com êxito.
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary>Saber o que acontece quando você implanta o seu aplicativo no Azure</summary>

Antes da implantação, o aplicativo era executado localmente:

1. O back-end é executado usando o _Azure Functions Core Tools_.
1. O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.

A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure. O back-end usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Serviço de Bot do Azure.

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a>Adicionar uma página de configuração à extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a>Exemplo de código

O Teams Config do Auth de Pesquisa para projetos de exemplo no GitHub, demonstre como criar extensões de mensagens que incluem uma página de configuração e a autenticação [do Serviço bot.](https://github.com/microsoft/BotBuilder-Samples#teams-samples) Os exemplos também demonstram como criar extensões de mensagem que aceitam solicitações de pesquisa e retornam os resultados depois que o usuário se inscreveu.

| **Exemplo de nome** | **Descrição** | **.NET** | **Node.js** | **Python** |
|-----------------|-----------------|-------------|--------------|--------|
| Construtor de bots | Para criar extensões de mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [View]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a>Exemplo de código adicional

> [!div class="nextstepaction"]
> [Exibir mais Exemplos de Estrutura de Bots em GitHub](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre outros métodos para criar aplicativos do Teams:

- [Criar um aplicativo do Teams com o React](first-app-react.md)
- [Criar um aplicativo do Teams com o Blazor](first-app-blazor.md)
- [Criar um aplicativo do Teams como uma Web Part do Microsoft Office SharePoint Online](first-app-spfx.md) (Azure não necessário)
- [Criar um bot de conversa](first-app-bot.md)
