---
title: 'Tutorial - Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar Microsoft Teams aplicativos com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 15b08078e15c8ed5ef23d6d9f78d2fc14da02440
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360723"
---
# <a name="build-your-first-teams-app-using-c"></a>Criar seu primeiro aplicativo Teams usando C #

Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando o .NET ou C#. Ele também orienta você pelas etapas para:

1. [Preparar seu ambiente](#prepare-your-environment)
1. [Obter pré-requisitos](#GetPrerequisites)
1. [Baixar o exemplo](#DownloadSample)
1. [Criar e executar o exemplo](#BuildRun)
1. [Hospedar o aplicativo de exemplo](#hostsample)
1. [Atualizar as credenciais do aplicativo hospedado](#updatecredentials)
1. [Configurar a guia do aplicativo](#configureapptab)

<a name="prepare-your-environment"></a>
[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa instalar as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instalar o Visual Studio](https://www.visualstudio.com/downloads/)

Você pode instalar a edição gratuita da comunidade Visual Studio. Durante a instalação, se houver uma opção para adicionar `git` ao caminho, selecione-o. Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Use uma janela de terminal adequada em sua plataforma. Esses exemplos usam Git Bash, mas podem ser executados na maioria das plataformas.

Abra a versão mais recente do Visual Studio e instale todas as atualizações.

Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) exemplo em C#. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) para modificar e salvar suas alterações no GitHub.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Você pode criar e executar o exemplo depois que ele for clonado. 

**Para criar e executar o exemplo clonado**

1. Abra o arquivo de **solução Microsoft.Teams. Samples.HelloWorld.sln** do **diretório Microsoft-Teams-Samples/samples/app-hello-world/csharp** do exemplo.
1. Selecione **Criar Solução** no menu Criar. 
1. Selecione a **tecla F5** ou selecione **Iniciar Depuração** no menu **Depurar** para executar o exemplo.

    Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado. Você pode ir para as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:

    - `https://localhost:44327/`
    - `https://localhost:44327/hello`
    - `https://localhost:44327/first`
    - `https://localhost:44327/second`

    > [!Note]
    > Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Para obter mais informações, [consulte esta pergunta em Stack Overflow](https://stackoverflow.com/questions/32780315).

    <a name="hostsample"></a>
    ## <a name="deploy-your-sample-app"></a>Implantar seu aplicativo de exemplo

    Os aplicativos Microsoft Teams são aplicativos Web que fornecem um ou mais recursos. Para que Teams plataforma de carregamento do aplicativo, seu aplicativo deve estar disponível na Internet. Para fazer isso, você precisa hospedar seu aplicativo. Você pode hospedá-lo Microsoft Azure gratuitamente ou criar um túnel para o processo local em seu computador usando `ngrok` . Depois de hospedar seu aplicativo, anote sua URL raiz, como `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel usando ngrok

Para testes rápidos, você pode executar o aplicativo em seu computador e criar um túnel para ele por meio de um ponto de extremidade da Web. [`ngrok`](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web, como `https://d0ac14a5.ngrok.io` . Você pode [baixar e instalar](https://ngrok.com/download) o ngrok e adicioná-lo a um local em seu `PATH` .

Depois de instalar `ngrok` , abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:

```bash
ngrok http 44327 -host-header=localhost:44327
```

`Ngrok` responde a solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327. 

**Para verificar a resposta**

1. Abra o navegador e vá para `https://d0ac14a5.ngrok.io/hello`. Isso carregará a página Hello do aplicativo.
1. Em vez da URL mencionada na Etapa 1, use o endereço de encaminhamento exibido `ngrok` na sessão do console.
    > [!NOTE]
    > Se você tiver usado uma porta diferente na etapa [de com](#build-and-run-the-sample) build e run, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.
    > [!TIP]
    > É uma boa ideia executar em `ngrok` uma janela de terminal diferente. Isso é feito para evitar `ngrok` a execução sem interferir no aplicativo. Você precisa parar, recriar e reprisar o aplicativo. A `ngrok` sessão fornece informações úteis de depuração nesta janela.

    O aplicativo só está disponível durante a sessão atual em seu computador. Se o computador for desligado ou for desligado, o serviço não estará mais disponível. Lembre-se disso quando você compartilhar o aplicativo para testes com outros usuários. Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar cada local que usa esse endereço. A versão paga `ngrok` do não tem essa limitação.

### <a name="host-in-azure"></a>Host no Azure

Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando infraestrutura compartilhada. Isso é suficiente para executar o `Hello World` exemplo. Para obter mais informações, [consulte criando uma nova conta gratuita do Azure](https://azure.microsoft.com/free/).

Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure:

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

**Atualizar o pacote do aplicativo**

# <a name="app-studio"></a>[App Studio](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[Portal do Desenvolvedor](#tab/DP)

**Para instalar o Portal do Desenvolvedor (visualização) Teams**


1. Selecione o **ícone Aplicativos** na parte inferior da barra à esquerda e procure o **Portal do Desenvolvedor.**

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. Selecione **Portal do Desenvolvedor** e selecione **Abrir**.

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. Selecione a guia Aplicativos e selecione **Importar um aplicativo existente.**

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. Selecione **Hello World** e selecione **Importar**. O **aplicativo Hello World** é importado no Portal do Desenvolvedor. 

    Você pode configurar seu aplicativo usando o Teams Portal do Desenvolvedor. O Manifesto é encontrado em Distribute. Você pode usar o Manifesto para configurar recursos, recursos necessários e outros atributos importantes para seu aplicativo. Para obter mais detalhes sobre como configurar seu aplicativo usando o Portal do Desenvolvedor, [consulte Teams Portal do Desenvolvedor.](../concepts/build-and-test/teams-developer-portal.md)

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>
---

<a name="updatecredentials"></a>
## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais do aplicativo hospedado

O aplicativo de exemplo exige que as variáveis de ambiente sejam definidas como os valores salvos no arquivo de texto.

**Para atualizar as credenciais do aplicativo hospedado**

1. Abra o arquivo `appsettings.json`. 
1. Atualize o **valor do MicrosoftAppId** com sua ID de bot que você salvou no arquivo de texto. 
1. Atualize **o MicrosoftAppPassword** com a senha de bot que você salvou.

    <img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

    Depois que essas alterações são feitas, reconstróa o aplicativo. Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.

<a name="configureapptab"></a>
## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em equipes, você deve configurá-lo para exibir o conteúdo. 

**Para configurar a guia do aplicativo**

1. Vá para um canal na equipe onde você instalou o aplicativo de exemplo e selecione o botão **'+'** para adicionar uma nova guia.
1. Selecione **Hello World** na lista Adicionar **uma** guia. Uma caixa de diálogo de configuração é exibida que permite selecionar a guia a ser exibida neste canal. 
1. Selecione **Salvar**. A `Hello World` guia é carregada com a guia.

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Teste seu bot no Teams

Agora você pode testar o bot Teams. 

**Para testar seu bot**

* Selecione um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` . Isso é chamado de **\@ menção**. O bot responde a qualquer mensagem enviada.

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

**Para testar sua extensão de mensagens**
1. Selecione **...** abaixo da caixa de entrada no seu exibição de conversa. Um menu com o **aplicativo "Hello World"** é exibido. 
1. Selecione o menu, um conjunto de textos aleatórios é exibido. Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.

    <img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Selecione um dos textos aleatórios. Um cartão formatado e pronto para enviar com sua própria mensagem é mostrado.

    <img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

## <a name="see-also"></a>Confira também

* [Visão geral dos tutoriais](code-samples.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)
