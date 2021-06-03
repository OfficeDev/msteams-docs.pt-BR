---
title: 'Iniciar: Compilar seu primeiro aplicativo do Teams com React'
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Kit de ferramentas do Microsoft Teams e o React.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: 8c6a957dc01cfaac0f8463166a6647d6b18babed
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721833"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a>Compilar e executar seu primeiro aplicativo do Microsoft Teams com React

Neste tutorial, você criará um novo aplicativo Microsoft Teams no React que implementa um aplicativo pessoal simples para extrair informações do Microsoft Graph. (Um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.) Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo do Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.

O aplicativo que é compilado exibe informações básicas para o usuário atual.  Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.

## <a name="before-you-begin"></a>Antes de você começar

Certifique-se de que o seu ambiente de desenvolvimento esteja configurado, instalando os [pré-requisitos](prerequisites.md)

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="create-your-project"></a>Criar seu projeto

Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar capacidades**, a capacidade da **Guia** já será selecionada.  Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. Na etapa **Recursos em nuvem**, pressione **OK**.  Não precisamos de recursos adicionais em nuvem para este tutorial.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

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
1. Escolha a capacidade **Guia**.
1. Selecione **Azure** como hospedagem front-end.
1. Não selecione nenhum recurso em nuvem.
1. Selecione **JavaScript** como linguagem de programação.
1. Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.
1. Insira um nome adequado para seu aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.

Assim que todas as perguntas forem respondidas, o seu projeto será criado.

---

## <a name="take-a-tour-of-the-source-code"></a>Faça um tour pelo código-fonte

Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).

Uma vez que o Kit de ferramentas do Teams configura seu projeto, você tem os componentes para compilar um aplicativo pessoal básico para o Teams. Os diretórios e arquivos do projeto são exibidos na área do Explorador do Visual Studio Code.

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para um aplicativo pessoal no Visual Studio Code.":::

O Kit de ferramentas cria automaticamente scaffolding para você no diretório do projeto com base nas capacidades que você adicionou durante a instalação. O Kit de ferramentas do Teams mantém o estado de seu aplicativo no diretório `.fx`.  Entre outros itens deste diretório:

- Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.
- O manifesto do aplicativo para publicação no Portal do Desenvolvedor do Teams é armazenado em `manifest.source.json`.
- As configurações que você escolheu ao criar o projeto são armazenadas em `settings.json`.

Como você selecionou a capacidade de guias durante a instalação, o Kit de ferramentas do Teams reúne todo o código necessário para uma guia básica no diretório `tabs`. Dentro deste diretório há vários arquivos importantes:

- `tabs/src/index.jsx` é o ponto de entrada do front-end do aplicativo, onde o componente principal `App` é renderizado com `ReactDOM.render()`.
- `tabs/src/components/App.jsx` lida com o roteamento de URLs em seu aplicativo. Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams.
- `tabs/src/components/Tab.jsx` contém o código para implementar a IU do seu aplicativo.
- `tabs/src/components/TabConfig.jsx` contém o código para implementar a IU que configura seu aplicativo.

Várias guias são exigidas pelo runtime do Teams, incluindo o aviso de privacidade, os termos de uso e as guias de configuração.  O código para o aviso de privacidade e os termos de uso estão localizados no mesmo diretório.

Quando se adiciona a funcionalidade da nuvem, diretórios adicionais são adicionados ao projeto.  Principalmente, o diretório `api` retém o código para qualquer Azure Functions que você escreva.

## <a name="run-your-app-locally"></a>Executar seu aplicativo localmente

O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.  Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:

- Um aplicativo está registrado no Azure Active Directory.  Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.
- Uma API da Web é hospedada para auxiliar nas tarefas de autenticação, atuando como um proxy entre o aplicativo e o Azure Active Directory.  Isto é executado pelo Azure Functions Core Tools.  Ele pode ser acessado na URL `https://localhost:5000`.
- Os recursos HTML, CSS e JavaScript que compõem o front-end do aplicativo são hospedados em um serviço local. Ele pode ser acessado em `https://localhost:3000`.
- Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.  O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.

Depois de fazer isso, o aplicativo pode ser carregado dentro do cliente do Teams.  Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a>Compilar e executar seu aplicativo localmente em Visual Studio Code

Para compilar e executar seu aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída.  Isto pode levar de 3 a 5 minutos para ser concluído.

   O Kit de ferramentas lhe solicitará a instalação de um certificado local, se necessário. Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`. Selecione Sim quando aparecer a seguinte caixa de diálogo:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. O navegador da Web começa a executar o aplicativo. Se for solicitado a abrir Teams área de trabalho, selecione **Cancelar** para permanecer no navegador. Você também pode ser solicitado a alternar para a área de trabalho Teams outras vezes; selecione o Teams web quando isso acontecer.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. Você pode ser solicitado a entrar.  Em caso afirmativo, entre com sua conta M365.
1. Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.

Seu aplicativo agora será exibido:

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Captura de tela do aplicativo concluído":::

Você pode fazer atividades normais de depuração como se isso fosse qualquer outro aplicativo Web (como a configuração de pontos de interrupção). O aplicativo dá suporte à recarga dinâmica.  Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</summary>

Quando você pressionou F5, o Kit de ferramentas do Teams:

1. Registrou seu aplicativo no Azure Active Directory.
1. *Fez o sideload* de seu aplicativo no Teams.
1. Iniciou a execução do back-end de seu aplicativo localmente usando o [Azure Functions Core Tools](/azure/azure-functions/functions-run-local?#start).
1. Iniciou a hospedagem local do front-end de seu aplicativo.
1. Iniciou o Microsoft Teams em um navegador da Web com um comando para instruir o Teams a fazer o sideload a partir de `https://localhost:3000/tab` (a URL está registrada dentro do manifesto do aplicativo).

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</summary>

Para executar com êxito seu aplicativo no Teams, você deve ter uma conta do Teams que permite o sideload de aplicativo. Para obter mais informações sobre abertura de conta, confira [pré-requisitos](prerequisites.md#enable-sideloading).

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você implanta o seu aplicativo no Azure</summary>

Antes da implantação, o aplicativo era executado localmente:

1. O back-end é executado usando o _Azure Functions Core Tools_.
1. O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.

A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure.

1. O back-end (se configurado) usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Armazenamento do Microsoft Azure.
1. O front-end do aplicativo será implantado em uma conta de Armazenamento do Microsoft Azure configurada para hospedagem Web estática.

</details>

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre outros métodos para criar aplicativos do Teams:

- [Criar um aplicativo do Teams com o Blazor](first-app-blazor.md)
- [Criar um aplicativo do Teams como uma Web Part do SharePoint](first-app-spfx.md) (Azure não é necessário)
- [Criar um programa bot de conversação](first-app-bot.md)
- [Criar uma extensão de mensagem](first-message-extension.md)
