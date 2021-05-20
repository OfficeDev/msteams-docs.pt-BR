---
title: 'Tutorial - Crie seu primeiro aplicativo usando C #'
description: Saiba como começar a construir aplicativos Microsoft Teams com C# ou .NET.
keywords: começando .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: eaa37f1ccb7944ee18bb62ae47882dc4a715b165
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566884"
---
# <a name="create-your-first-teams-app-using-c"></a>Crie seu primeiro aplicativo de Teams usando C #

Este tutorial ajuda você a criar um aplicativo Microsoft Teams usando C#. Para fazer isso, você deve:

* Preparar seu ambiente
* Obter pré-requisitos
* Baixe a amostra
* Criar e executar o exemplo
* Hospede o aplicativo de amostra
* Atualize as credenciais para o seu aplicativo hospedado
* Configure a guia do aplicativo

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para completar este tutorial, você precisa instalar as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instalar o Visual Studio](https://www.visualstudio.com/downloads/)

Você pode instalar a edição comunitária gratuita de Visual Studio. Durante a instalação, se houver uma opção para adicionar `git` ao caminho, selecione-o. Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Use uma janela de terminal adequada em sua plataforma. Esses exemplos usam o Git Bash, mas podem ser executados na maioria das plataformas.

Abra a versão mais recente do Visual Studio e instale quaisquer atualizações.

Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixe a amostra

Você pode começar com um simples [Olá, Mundo!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) amostra em C#. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de amostras para o computador:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) para modificar e salvar suas alterações em GitHub.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repo for clonado, use Visual Studio para abrir o arquivo de solução **Microsoft.Teams. Samples.HelloWorld.sln** do diretório **Microsoft-Teams-Samples/samples/app-hello-world/csharp** da amostra. Em seguida, selecione **Criar solução** no menu **Construir.** Para executar a amostra, pressione **F5** ou selecione Iniciar a **depuração** no menu **Debug.**

Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo lançado. Você pode ir aos seguintes URLs para verificar se todos os URLs do aplicativo estão carregando:

- `https://localhost:44327/`
- `https://localhost:44327/hello`
- `https://localhost:44327/first`
- `https://localhost:44327/second`

<a name="HostSample"></a>

> [!Note]
> Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Para obter mais informações, consulte [esta pergunta no Stack Overflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hospede o aplicativo de amostra

Aplicativos em Microsoft Teams são aplicativos web que fornecem um ou mais recursos. Para que a plataforma Teams carregue seu aplicativo, seu aplicativo deve estar disponível na internet. Para fazer isso, você precisa hospedar seu aplicativo. Você pode hospedá-lo Microsoft Azure gratuitamente ou criar um túnel para o processo local no seu computador usando `ngrok` . Depois de hospedar seu aplicativo, observe sua URL raiz, como `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel usando ngrok

Para testes rápidos, você pode executar o aplicativo em seu computador e criar um túnel para ele através de um ponto final da Web. [`ngrok`](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço web, como `https://d0ac14a5.ngrok.io` . Você pode [baixar e instalar](https://ngrok.com/download) ngrok e adicioná-lo a um local em seu `PATH` .

Depois de `ngrok` instalar, abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:

```bash
ngrok http 44327 -host-header=localhost:44327
```

`Ngrok` ouve as solicitações da internet e as encaminha para o seu aplicativo em execução na porta 44327. Para verificar, abra seu navegador e vá `https://d0ac14a5.ngrok.io/hello` para carregar a página de olá do seu aplicativo. Em vez desta URL, use o endereço de encaminhamento exibido `ngrok` na sessão do console.

> [!NOTE]
> Se você tiver usado uma porta diferente na etapa [de construção e execução,](#build-and-run-the-sample) certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.

> [!TIP]
> É uma boa ideia correr `ngrok` em uma janela terminal diferente. Isso é feito para evitar `ngrok` correr sem interferir no aplicativo. Você tem que parar, reconstruir e refazer o aplicativo. A `ngrok` sessão fornece informações úteis de depuração nesta janela.

O aplicativo só está disponível durante a sessão atual em seu computador. Se a máquina estiver desligada ou for dormir, o serviço não estará mais disponível. Lembre-se disso quando você compartilha o aplicativo para testes para outros usuários. Se você tiver que reiniciar o serviço, o aplicativo retorna um novo endereço e você deve atualizar todos os locais que usam esse endereço. A versão paga `ngrok` não tem essa limitação.

### <a name="host-in-azure"></a>Anfitrião em Azure

Microsoft Azure hospeda seu aplicativo .NET em um nível gratuito usando infraestrutura compartilhada. Isso é suficiente para executar a `Hello World` amostra. Para obter mais informações, consulte [a criação de uma nova conta gratuita do Azure](https://azure.microsoft.com/free/).

Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure:

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualize as credenciais para o seu aplicativo hospedado

O aplicativo de amostra requer que as variáveis de ambiente sejam definidas para os valores salvos no arquivo de texto.

Abra o arquivo `appsettings.json`. Atualize o valor **do MicrosoftAppId** com o seu ID de bot que você salvou no arquivo de texto. Atualize o **MicrosoftAppPassword** com a senha do bot que você salvou.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Depois que essas alterações forem feitas, reconstrua o aplicativo. Se você estiver usando ngrok, execute o aplicativo localmente e se estiver hospedando no Azure, reimplante o aplicativo.

## <a name="configure-the-app-tab"></a>Configure a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você deve configurá-lo para mostrar conteúdo. Vá para um canal na equipe onde instalou o aplicativo de amostra e selecione o botão **'+'** para adicionar uma nova guia. Escolha **Hello World** na lista Adicionar **uma** guia. Uma caixa de diálogo de configuração é exibida que permite que você escolha a guia para exibir neste canal. Depois de selecionar a guia e selecionar **Salvar** a `Hello World` guia é carregada com a guia.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Teste seu bot em Teams

Agora você pode testar o bot em Teams. Selecione um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` . Isso é chamado de **\@ menção.** O bot responde a qualquer mensagem que você enviar.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Teste sua extensão de mensagens

Para testar sua extensão de mensagens, você pode selecionar **...** abaixo da caixa de entrada em sua visualização de conversação. Um menu com o aplicativo **'Hello World'** é exibido. Ao selecioná-lo, um conjunto de textos aleatórios é exibido. Você pode selecionar um dos textos aleatórios e que está inserido na sua conversa.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Selecione um dos textos aleatórios. Um cartão formatado e pronto para enviar com sua própria mensagem é mostrado.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
