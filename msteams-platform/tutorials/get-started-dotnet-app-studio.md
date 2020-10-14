---
title: Introdução ao C#/.NET
description: Introdução à criação de aplicativos ótimos no Microsoft Teams usando o C#/.NET
keywords: Introdução ao .net c# Csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 3aca72a43765036c0014a9e16fa585575fe97b2e
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452839"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-cnet-and-app-studio"></a>Introdução à plataforma do Microsoft Teams com o C#/.NET e o app Studio

A plataforma de desenvolvedor do [Microsoft Teams](/microsoftteams/) facilita a extensão de equipes e a integração de seus próprios aplicativos e serviços diretamente no espaço de trabalho do Microsoft Teams. Esses aplicativos podem ser distribuídos para sua empresa ou para o Teams em todo o mundo.

Para estender o Microsoft Teams, você precisará criar um aplicativo do Microsoft Teams. Um aplicativo do Microsoft Teams é um aplicativo Web que você hospeda. Esse aplicativo pode ser integrado ao espaço de trabalho do usuário no Microsoft Teams.

Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams usando C# no .NET. Você pode testar o aplicativo carregando-o em uma equipe para a qual tenha permissões ou em um locatário de teste criado usando o programa de desenvolvedor do Office.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa obter as seguintes ferramentas:

- [Instalar o Git](https://git-scm.com/downloads)
- [Instale o Visual Studio](https://www.visualstudio.com/downloads/). Você pode instalar a edição gratuita da Comunidade.

Se você vir uma opção para adicionar `git` ao caminho durante a instalação, escolha fazer isso. Será útil.

Verifique a `git` instalação executando o seguinte em uma janela de terminal:
> [!NOTE]
> Use a janela do terminal com a qual você se sente mais confortável em sua plataforma. Estes exemplos usam o bash, mas serão executados na maioria das plataformas.

```bash
$ git --version
git version 2.17.1.windows.2

```

Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações, se mostradas.

Você pode continuar a usar esta janela de terminal para executar os comandos a seguir neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Fornecemos um simples [Olá, mundo!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) exemplo em C# para ajudá-lo a começar. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repositório](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) se quiser modificar e fazer check-in de suas alterações no GitHub para referência futura.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repositório é clonado, use o Visual Studio para abrir o arquivo `Microsoft.Teams.Samples.HelloWorld.sln` de solução no diretório raiz do exemplo e clique `Build Solution` no `Build` menu. Você pode executar o exemplo pressionando `F5` ou escolhendo `Start Debugging` o `Debug` menu.

Quando o aplicativo for iniciado, você verá uma janela do navegador aberta com a raiz do aplicativo iniciado. Você pode navegar até as seguintes URLs para verificar se todas as URLs de aplicativo estão sendo carregadas:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> Se você receber uma mensagem de erro `Could not find a part of the path … bin\roslyn\csc.exe` , tente atualizar o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Confira [esta pergunta sobre StackOverflow](https://stackoverflow.com/questions/32780315) para obter mais detalhes.

## <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Lembre-se de que aplicativos no Microsoft Teams são aplicativos da Web que expõem um ou mais recursos. Para que a plataforma do teams carregue seu aplicativo, seu aplicativo deve estar acessível pela Internet. Para tornar seu aplicativo alcançável da Internet, você precisa hospedar seu aplicativo. Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento usando o `ngrok` . Quando você terminar de hospedar seu aplicativo, anote sua URL raiz. Ele terá uma aparência semelhante a: `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Túnel usando ngrok

Para testes rápidos, você pode executar o aplicativo na sua máquina local e criar um túnel para ele por meio de um ponto de extremidade da Web. o [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com o ngrok, você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (esta URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) o ngrok para o seu ambiente. Certifique-se de adicioná-lo a um local no seu `PATH` .

Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.

```bash
ngrok http 3333 -host-header=localhost:3333
```

O Ngrok ouvirá as solicitações da Internet e irá encaminhá-las para seu aplicativo em execução na porta 3333. Você pode verificar abrindo seu navegador e indo para `https://d0ac14a5.ngrok.io/hello` carregar a página de saudação do aplicativo. Certifique-se de usar o endereço de encaminhamento exibido pelo ngrok em sua sessão de console, em vez desta URL.

> [!NOTE]
> Se você tiver usado uma porta diferente na etapa [criar e executar](#build-and-run-the-sample) acima, certifique-se de usar o mesmo número de porta para instalar o `ngrok` túnel.
> [!TIP]
> É uma boa ideia executar `ngrok` em uma janela diferente do terminal para mantê-la em execução sem interferir no aplicativo, que pode ser mais tarde interrompido, recriar e executar novamente. A `ngrok` sessão retornará informações de depuração úteis nesta janela.

O aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento. Se o computador estiver desligado ou chegar à suspensão, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários. Se for necessário reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar cada lugar que usa esse endereço. A versão paga do Ngrok não tem essa limitação.

### <a name="host-in-azure"></a>Host no Azure

O Microsoft Azure permite que você hospede seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada. Isso será suficiente para executar este `Hello World` exemplo. Consulte [criar uma nova conta gratuita](https://azure.microsoft.com/free/) para obter mais informações.

O Visual Studio oferece suporte interno à implantação de aplicativos para diferentes provedores, incluindo o Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais para seu aplicativo hospedado

O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez antes.

Abra o appsettings.jsem arquivo. Atualize o valor *MicrosoftAppId* com a ID de bot que você salvou anteriormente. Atualize o *MicrosoftAppPassword* com a senha de bot que você salvou anteriormente.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Depois que essas alterações forem feitas, reconstrua o aplicativo. Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.

## <a name="configure-the-app-tab"></a>Configurar a guia aplicativo

Após instalar o aplicativo em uma equipe, você precisará configurá-lo para exibir o conteúdo. Vá para um canal na equipe em que você instalou o exemplo de aplicativo e clique no botão **"+"** para adicionar uma nova guia. Em seguida, você pode escolher `Hello World` na lista **Adicionar uma guia** . Em seguida, será exibida uma caixa de diálogo de configuração. Esta caixa de diálogo permitirá que você escolha qual guia será exibida neste canal. Depois de selecionar a guia e clicar em `Save` , você poderá ver a `Hello World` guia carregada com a guia escolhida.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` . Isso é chamado de ** \@ menção**. Qualquer mensagem enviada ao bot será enviada de volta para você como resposta.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no modo de exibição de conversa. Um menu será exibido com o aplicativo **"Olá mundo"** . Quando você clicar nele, verá um monte de textos aleatórios aparecendo. Você pode escolher qualquer uma delas e ela será inserida na conversa.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios, e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
