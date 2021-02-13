---
title: 'Tutorial : Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: b37a8d555117e38383504dc99d82d564439a3ebf
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231516"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a>Crie seu primeiro aplicativo do Teams usando C# ou .NET

Este tutorial ajuda você a criar um aplicativo do Microsoft Teams em C# ou .NET.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa obter as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instale o Visual Studio.](https://www.visualstudio.com/downloads/) Você pode instalar a edição gratuita da comunidade.

Durante a instalação, se houver uma opção para adicionar `git` ao PATH, escolha-a.

Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Use uma janela de terminal adequada em sua plataforma. Esses exemplos usam Bash, mas são executados na maioria das plataformas.

Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações.

Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) em C#. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório para](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) modificar e salvar suas alterações no GitHub para referência.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução no diretório raiz do exemplo e `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` selecione no `Build` menu. Para executar o exemplo, `F5` pressione ou escolha no `Start Debugging` `Debug` menu.

Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado. Você pode navegar até as URLs a seguir para verificar se todas as URLs do aplicativo estão sendo carregadas:

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second]https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` comando. Para obter mais informações, [consulte esta pergunta no StackOverflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Os aplicativos no Microsoft Teams são aplicativos Web que fornecem um ou mais recursos. Para a plataforma do Teams carregar seu aplicativo, seu aplicativo deve estar acessível pela Internet. Para tornar seu aplicativo acessível pela Internet, você precisa hospedar seu aplicativo. Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento `ngrok` usando. Quando você terminar de hospedar seu aplicativo, anote sua URL raiz. Por exemplo, `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Túnel usando ngrok

Para testes rápidos, você pode executar o aplicativo no computador local e criar um túnel para ele por meio de um ponto de extremidade da Web. [ngrok](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web, como `https://d0ac14a5.ngrok.io` . Você pode [baixar e instalar](https://ngrok.com/download) o ngrok. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalar o ngrok, abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:

```bash
ngrok http 44327 -host-header=localhost:44327
```

O exemplo usa a porta 44327 para especificá-la.

O Ngrok escuta solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327. Para verificar, abra o navegador e vá `https://d0ac14a5.ngrok.io/hello` para carregar a página hello do aplicativo. Em vez dessa URL, use o endereço de encaminhamento exibido pelo ngrok na sessão do console.

> [!NOTE]
> Se você usou uma porta diferente na etapa de [com](#build-and-run-the-sample) build e de executar, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.

> [!TIP]
> É uma boa ideia executar em `ngrok` uma janela de terminal diferente. Isso é feito para impedir que o ngrok seja executado sem interferir no aplicativo, que você precisa parar, recriar e executar de novo. A `ngrok` sessão fornece informações úteis de depuração nesta janela.

O aplicativo só está disponível durante a sessão atual em seu computador de desenvolvimento. Se o computador for desligado ou ficar em sleep, o serviço não estará mais disponível. Lembre-se disso quando compartilhar o aplicativo para teste com outros usuários. Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar todos os locais que usam esse endereço. A versão paga do ngrok não tem essa limitação.

### <a name="host-in-azure"></a>Host no Azure

O Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada. Isso é suficiente para executar o `Hello World` exemplo. Para obter mais informações, consulte [a criação de uma nova conta gratuita.](https://azure.microsoft.com/free/)

O Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais do aplicativo hospedado

O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas com os valores que você anoou anteriormente.

Abra o appsettings.jsno arquivo. Atualize o *valor de MicrosoftAppId* com sua ID de Bot que você salvou anteriormente. Atualize *o MicrosoftAppPassword* com a senha de Bot salva anteriormente.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Depois que essas alterações são feitas, recomando o aplicativo. Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.

## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe em que você instalou o aplicativo de exemplo e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista Adicionar **uma** guia. Em seguida, você receberá uma caixa de diálogo de configuração. Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e clicar na guia, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe onde você registrou seu aplicativo e `@your-bot-name` digite. Isso é chamado de **\@ menção.** Qualquer mensagem enviada para o bot será enviada de volta como uma resposta.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na exibição de conversa. Um menu será aberto com o **aplicativo "Hello World"** nele. Ao clicar nele, você verá vários textos aleatórios aparecendo. Você pode escolher qualquer um deles e ele será inserido em sua conversa.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
