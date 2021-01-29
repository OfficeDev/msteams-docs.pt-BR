---
title: 'Tutorial : Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C#/.NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: c28c4d00c375b8e37f82c343eec2c5405ae0c1c8
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037036"
---
# <a name="create-your-first-microsoft-teams-app-using-c"></a>Criar seu primeiro aplicativo Do Microsoft Teams usando C #

Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams em C# no .NET.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa obter as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instale o Visual Studio.](https://www.visualstudio.com/downloads/) Você pode instalar a edição gratuita da comunidade.

Se você vir uma opção para adicionar `git` ao PATH durante a instalação, opte por fazer isso. Ele será útil.

Verifique sua `git` instalação executando o seguinte em uma janela de terminal:
> [!NOTE]
> Use a janela de terminal com a que você mais se sente confortável em sua plataforma. Esses exemplos usam Bash, mas serão executados na maioria das plataformas.

```bash
$ git --version
git version 2.17.1.windows.2

```

Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações, se mostrado.

Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) em C# para começar. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) se quiser modificar e fazer check-in de suas alterações no GitHub para referência futura.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução no diretório raiz do exemplo e clique `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` no `Build` menu. Você pode executar o exemplo pressionando `F5` ou escolhendo `Start Debugging` no `Debug` menu.

Quando o aplicativo for iniciado, você verá uma janela do navegador aberta com a raiz do aplicativo iniciada. Você pode navegar até as URLs a seguir para verificar se todas as URLs do aplicativo estão sendo carregadas:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> Se você receber um erro como `Could not find a part of the path … bin\roslyn\csc.exe` , tente atualizar o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Veja [esta pergunta no StackOverflow para](https://stackoverflow.com/questions/32780315) obter detalhes adicionais.

## <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Lembre-se de que os aplicativos no Microsoft Teams são aplicativos Web expondo um ou mais recursos. Para a plataforma do Teams carregar seu aplicativo, seu aplicativo deve estar acessível pela Internet. Para tornar seu aplicativo acessível pela Internet, você precisa hospedar seu aplicativo. Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento `ngrok` usando. Quando você terminar de hospedar seu aplicativo, anote sua URL raiz. Ele será parecido com: `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Túnel usando ngrok

Para testes rápidos, você pode executar o aplicativo em seu computador local e criar um túnel para ele por meio de um ponto de extremidade da Web. [O ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com ngrok, você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) o ngrok para seu ambiente. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.

```bash
ngrok http 3333 -host-header=localhost:3333
```

O Ngrok escutará solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333. Você pode verificar abrindo o navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo. Certifique-se de usar o endereço de encaminhamento exibido pelo ngrok na sessão do console em vez dessa URL.

> [!NOTE]
> Se você tiver usado uma [](#build-and-run-the-sample) porta diferente na com build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.
> [!TIP]
> É uma boa ideia executar em uma janela de terminal diferente para mantê-la em execução sem interferir no aplicativo, que talvez seja preciso parar, recriar `ngrok` e executar outra vez. A `ngrok` sessão retornará informações úteis de depuração nesta janela.

O aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento. Se o computador for desligado ou for para sleep, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários. Se você tiver que reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar todos os lugares que usam esse endereço. A versão paga do Ngrok não tem essa limitação.

### <a name="host-in-azure"></a>Host no Azure

O Microsoft Azure permite que você hospede seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada. Isso será suficiente para executar este `Hello World` exemplo. Confira [a criação de uma nova conta gratuita](https://azure.microsoft.com/free/) para obter mais informações.

O Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais para seu aplicativo hospedado

O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas com os valores que você anoou anteriormente.

Abra o appsettings.jsno arquivo. Atualize o *valor de MicrosoftAppId* com sua ID de Bot que você salvou anteriormente. Atualize *o MicrosoftAppPassword* com a senha de Bot salva anteriormente.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Depois que essas alterações são feitas, recomando o aplicativo. Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.

## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe em que você instalou o aplicativo de exemplo e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista Adicionar **uma** guia. Em seguida, você receberá uma caixa de diálogo de configuração. Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e clicar, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` . Isso é chamado de **\@ menção.** Qualquer mensagem enviada para o bot será enviada de volta como uma resposta.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na exibição de conversa. Um menu será aberto com o **aplicativo "Hello World"** nele. Ao clicar nele, você verá vários textos aleatórios aparecendo. Você pode escolher qualquer um deles e ele será inserido na conversa.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
