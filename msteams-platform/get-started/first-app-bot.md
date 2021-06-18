---
title: Introdução - Construa o seu primeiro bot de conversação
author: adrianhall
description: Crie um bot de conversação para o Microsoft Teams usando o Kit de ferramentas do Teams.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: e59980e7f33c326c16faefd412f9845e47f234e5
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994256"
---
# <a name="build-your-first-conversational-bot-for-microsoft-teams"></a>Criar o seu primeiro bot de conversação para o Microsoft Teams

Um bot atua como um intermediário entre um usuário do Teams e um serviço Web.  Os usuários podem bater papo com um bot para obter informações rapidamente, iniciar fluxos de trabalho ou qualquer outra coisa que seu serviço Web possa fazer.  Neste tutorial, você aprenderá como construir, executar e implantar um aplicativo bot do Teams.

## <a name="before-you-begin"></a>Antes de você começar

Certificar-se de que o seu ambiente de desenvolvimento esteja configurado instalando os [Pré-requisitos](prerequisites.md)

> [!div class="nextstepaction"]
> [Instalar Pré-requisitos](prerequisites.md)

## <a name="create-your-project"></a>Criar o seu projeto

Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar recursos**, selecione **Bot** e anule a seleção **Guia**.  Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Captura de tela que mostra como adicionar recursos ao seu novo aplicativo.":::

1. Na etapa **Registro de bot**, selecione **Criar um novo registro de bot**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

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
1. Selecione o recurso **Bot** e anule a seleção o recurso da **Guia**.
1. Selecione **Criar um novo registro de bot**.
1. Selecione **JavaScript** como linguagem de programação.
1. Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.
1. Insira um nome adequado para seu aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.

Assim que todas as perguntas forem respondidas, o seu projeto será criado.

---

## <a name="take-a-tour-of-the-source-code"></a>Faça um tour pelo código-fonte

Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).

Uma extensão de mensagem usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com o seu serviço por meio de uma conversa.  Após o andaime, o seu projeto ficará assim:

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

O código do bot é armazenado no diretório `bot`.  O `bots/teamsBot.js` é o principal ponto de entrada para o bot e as caixas de diálogo são armazenadas no diretório `dialogs`.

> [!Tip]
> Familiarize-se com os bots fora do Teams antes de integrar o seu primeiro bot dentro do Teams.  Você pode localizar mais informações sobre os bots analisando os tutoriais do [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).

## <a name="run-your-app-locally"></a>Executar o seu aplicativo localmente

O Kit de ferramentas do Teams permite hospedar o seu aplicativo localmente.  Para fazer isso:

- Um Aplicativo do Azure Active Directory é registrado no locatário M365.
- Um manifesto do aplicativo é enviado ao Centro de Desenvolvedor para o Teams.
- Uma API é executada localmente usando o Azure Functions Core Tools para oferecer suporte ao seu aplicativo.
- [ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e o código do seu bot.

Para compilar e executar o seu aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída.  Isto pode levar de 3 a 5 minutos para ser concluído.

1. O navegador da Web começa a executar o aplicativo. Se for solicitado a abrir Teams área de trabalho, selecione **Cancelar** para permanecer no navegador. Você também pode ser solicitado a alternar para a área de trabalho Teams outras vezes; selecione o Teams web quando isso acontecer.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. Você pode ser solicitado a entrar.  Em caso afirmativo, entre com sua conta M365.
1. Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.

Assim que o aplicativo for carregado, você será levado diretamente para uma sessão de bate-papo com o bot.  Você pode digitar `intro` para mostrar um cartão de apresentação e `show` para mostrar seus detalhes do Microsoft Graph.  (Isso exigirá uma aprovação de permissões adicionais).

A depuração funciona normalmente - experimente você mesmo! Abra o arquivo `bot/dialogs/rootDialog.js` e localize o método `triggerCommand(...)`.  Defina um ponto de interrupção no caso padrão.  Em seguida, digite algum texto.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</summary>

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

## <a name="see-also"></a>Confira também

- [Criar um aplicativo do Teams com o React](first-app-react.md)
- [Criar um aplicativo do Teams com o Blazor](first-app-blazor.md)
- [Criar um aplicativo do Teams como uma Web Part do SharePoint](first-app-spfx.md) (Azure não é necessário)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma extensão de mensagem](first-message-extension.md)
