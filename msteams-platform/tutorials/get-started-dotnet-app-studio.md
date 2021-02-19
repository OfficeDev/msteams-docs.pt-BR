---
title: 'Tutorial - Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 29cc4e0f434bf9ece9c6073af84627acc048b628
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294751"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a>Crie seu primeiro aplicativo do Teams usando C# ou .NET

Este tutorial ajuda você a criar um aplicativo do Microsoft Teams usando C# ou .NET.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa obter as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instale Visual Studio](https://www.visualstudio.com/downloads/). Você pode instalar a edição gratuita da comunidade.

Durante a instalação, se houver uma opção para adicionar `git` ao PATH, escolha-o.

Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Use uma janela de terminal adequada em sua plataforma. Esses exemplos usam o Bash, mas são executados na maioria das plataformas.

Certifique-se de iniciar a versão mais recente do Visual Studio e instalar quaisquer atualizações.

Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) exemplo em C#. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador local:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório para](https://github.com/OfficeDev/Microsoft-Teams-Samples) modificar e salvar suas alterações no GitHub para referência.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução do `Microsoft.Teams.Samples.HelloWorld.sln` **diretório Microsoft-Teams-Samples/samples/app-hello-world/csharp** do exemplo e selecione no `Build Solution` `Build` menu. Para executar a pressione de `F5` exemplo ou escolha no `Start Debugging` `Debug` menu.

Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado. Você pode navegar até as URLs a seguir para verificar se todas as URLs do aplicativo estão sendo carregadas:

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second]https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Para obter mais informações, [consulte esta pergunta em StackOverflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Os aplicativos no Microsoft Teams são aplicativos Web que fornecem um ou mais recursos. Para que a plataforma do Teams carregue seu aplicativo, seu aplicativo deve ser acessível pela Internet. Para tornar seu aplicativo acessível pela Internet, você precisa hospedar seu aplicativo. Você pode hospedá-lo gratuitamente no Microsoft Azure ou criar um túnel para o processo local em sua máquina de desenvolvimento usando `ngrok` . Quando terminar de hospedar seu aplicativo, anote sua URL raiz. Por exemplo, `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Túnel usando ngrok

Para testes rápidos, você pode executar o aplicativo em sua máquina local e criar um túnel para ele por meio de um ponto de extremidade da Web. [ngrok](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` . Você pode [baixar e instalar](https://ngrok.com/download) o ngrok. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalar o ngrok, abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:

```bash
ngrok http 44327 -host-header=localhost:44327
```

O exemplo usa a porta 44327 para especificá-la.

O Ngrok escuta solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327. Para verificar, abra o navegador e vá `https://d0ac14a5.ngrok.io/hello` para carregar a página hello do aplicativo. Em vez dessa URL, use o endereço de encaminhamento exibido pelo ngrok na sessão do console.

> [!NOTE]
> Se você tiver usado uma porta diferente na etapa [de com](#build-and-run-the-sample) build e run, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.

> [!TIP]
> É uma boa ideia executar em `ngrok` uma janela de terminal diferente. Isso é feito para impedir que o ngrok seja executado sem interferir no aplicativo, que você precisa parar, recriar e executar. A `ngrok` sessão fornece informações úteis de depuração nesta janela.

O aplicativo só está disponível durante a sessão atual em sua máquina de desenvolvimento. Se o computador for desligado ou for desligado, o serviço não estará mais disponível. Lembre-se disso quando você compartilhar o aplicativo para testes com outros usuários. Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar cada local que usa esse endereço. A versão paga do ngrok não tem essa limitação.

### <a name="host-in-azure"></a>Host no Azure

O Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando infraestrutura compartilhada. Isso é suficiente para executar o `Hello World` exemplo. Para obter mais informações, consulte [criando uma nova conta gratuita](https://azure.microsoft.com/free/).

Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais do aplicativo hospedado

O aplicativo de exemplo exige que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma anotação anteriormente.

Abra o arquivo appsettings.json. Atualize o *valor do MicrosoftAppId* com sua ID de Bot que você salvou anteriormente. Atualize *o MicrosoftAppPassword* com a senha bot salva anteriormente.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Depois que essas alterações são feitas, reconstróa o aplicativo. Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.

## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe onde você instalou o aplicativo de exemplo e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode `Hello World` escolher na lista Adicionar **uma** guia. Em seguida, você será apresentado com uma caixa de diálogo de configuração. Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e clicar em, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` . Isso é chamado de **\@ menção**. Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no seu exibição de conversa. Um menu será aberto com o **aplicativo "Hello World"** nele. Ao clicar nele, você verá um monte de textos aleatórios sendo exibidos. Você pode escolher qualquer um deles e ele é inserido em sua conversa.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
