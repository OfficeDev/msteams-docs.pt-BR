---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a criar Microsoft Teams aplicativos com Node.js.
keywords: getting started node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 84c3452c739f67c2908d698b627b5651ff9d5d7a
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254337"
---
# <a name="build-your-first-microsoft-teams-app-using-nodejs"></a>Crie seu primeiro aplicativo Microsoft Teams usando Node.js

Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando Node.js. Ele também orienta você pelas etapas para: 

1. [Preparar seu ambiente](#prepare-environment)
1. [Obter pré-requisitos](#GetPrerequisites)
1. [Baixar o exemplo](#DownloadSample)
1. [Criar e executar o exemplo](#BuildRun)
1. [Hospedar o aplicativo de exemplo](#HostSample)
1. [Atualizar as credenciais do aplicativo hospedado](#updatecredentials)
1. [Configurar a guia do aplicativo](#ConfigureTheAppTab)

<a name="prepare-environment"></a>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

### <a name="download-and-host-your-app"></a>Baixar e hospedar seu aplicativo

Siga estas etapas para baixar e hospedar um aplicativo simples de "hello world" Teams.

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa das seguintes ferramentas. Se você ainda não os tiver, poderá instalá-los a partir desses links.

- [Git](https://git-scm.com/downloads)
- [Node.js e NPM](https://nodejs.org/)
- Obter qualquer editor de texto ou IDE. Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

Se você vir opções para adicionar , , e ao PATH durante a `git` `node` `npm` `code` instalação, selecione as opções. 

Verifique se as ferramentas estão disponíveis executando o seguinte em uma janela de terminal:

> [!NOTE]
> Use a janela de terminal com a que você está mais confortável em sua plataforma. Esses exemplos usam Bash (que está incluído no Git), mas esses scripts serão executados na maioria das plataformas.

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 2.3.0
Local version 4.0.2
```

Você pode ter uma versão diferente desses aplicativos. Isso não deve ser um problema, exceto gulp. Para gulp, você precisará usar a versão 4.0.0 ou posterior.

Se você não tiver o gulp instalado (ou tiver a versão errada instalada), faça isso agora executando `npm install gulp` na janela do terminal.

Se você tiver instalado Visual Studio Code, você poderá verificar a instalação executando:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Baixar o exemplo

Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) exemplo para começar. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador local:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações no seu GitHub para referência futura.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repositório for clonado, execute o comando alterar diretório no terminal para alterar o diretório para o exemplo:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Para criar o exemplo, você precisa instalar todas as suas dependências. Execute o seguinte comando para fazer isso:

```bash
npm install
```

Você deve ver várias dependências sendo instaladas. Após a instalação, você pode executar o aplicativo com o seguinte comando:

```bash
npm start
```

Quando o aplicativo hello-world é iniciado, ele é `App started listening on port 3333` exibido na janela do terminal.

> [!NOTE]
> Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem uma variável de ambiente PORT definida. Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.

Neste ponto, você pode abrir uma janela do navegador e navegar até as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

## <a name="deploy-your-sample-app"></a>Implantar seu aplicativo de exemplo

Lembre-se de que os aplicativos Microsoft Teams são aplicativos Web expondo um ou mais recursos. Para que Teams plataforma de carregamento do aplicativo, seu aplicativo deve ser acessível pela Internet. Para tornar seu aplicativo acessível pela Internet, você precisa *hospedar* seu aplicativo.

Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto de extremidade da Web. [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com *o ngrok,* você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para seu ambiente. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalá-la, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui:

```bash
ngrok http 3333 -host-header=localhost:3333
```

*O Ngrok* ouvirá as solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333. Você pode verificar abrindo seu navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo. Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console em vez dessa URL.

> [!NOTE]
> Se você tiver usado uma porta diferente na [com](#build-and-run-the-sample) build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o *túnel ngrok.*
> [!TIP]
> É uma boa ideia executar *o ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo de nó que talvez você tenha que parar, recriar e executar de novo. A *sessão ngrok* retornará informações úteis de depuração nesta janela.

Há uma versão paga do *ngrok* que permite nomes persistentes. Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em seu computador de desenvolvimento. Se o computador for desligado ou for parar, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários. Se você tiver que reiniciar o serviço, ele retornará um novo endereço e será preciso atualizar todos os lugares que usam esse endereço.

Anote a URL do seu aplicativo. Você precisará disso mais tarde quando registrar o aplicativo com Teams app studio ou Portal do Desenvolvedor.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Implantar seu aplicativo para Microsoft Teams

Neste ponto, você tem um aplicativo hospedado na Internet, mas ainda não tem como dizer Teams onde procurar ou até mesmo o que seu aplicativo é chamado. Para fazer isso, agora você precisa criar um pacote de aplicativos. Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o Teams cliente usará para exibir e identidade visual adequadamente seu aplicativo. Você pode criar manualmente esse pacote de aplicativos ou usar o App Studio ou o Portal do Desenvolvedor, ferramentas que são Teams, que simplificarão o processo de registro do aplicativo. O App Studio e o Portal do Desenvolvedor são as maneiras recomendadas de criar e atualizar o pacote de aplicativos.

Para qualquer um dos métodos, você precisará do seguinte:

- A URL onde seu aplicativo pode ser encontrado na Internet.
- Ícones que Teams usarão para fazer a marca do aplicativo. O exemplo vem com ícones de espaço reservado localizados em "src\static\images. O App Studio também fornecerá ícones padrão, se necessário.

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

O aplicativo de exemplo exige que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma anotação anteriormente:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Como fazer isso difere dependendo de como você hospedou seu aplicativo. O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código para seu aplicativo, mas não são expostos a terceiros que podem examinar os arquivos que compusem seu site.

Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente local. Há muitas maneiras de fazer isso, mas a mais fácil, se você estiver usando Visual Studio Code, é adicionar uma configuração [de início](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):

``` 
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

Onde:

MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é a ID e a senha, respectivamente, para seu bot.
NODE_DEBUG mostrará o que está acontecendo em seu bot no console Visual Studio Code depuração.
NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura por ele na pasta src).

> [!Note]
> Se você não tiver parado npm no início do tutorial, precisará ser executado para que Visual Studio Code suas variáveis de configuração de início `npm stop` corretamente.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode `Hello World` escolher na lista Adicionar **uma** guia. Em seguida, você será apresentado com uma caixa de diálogo de configuração. Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e clicar em **Salvar,** você pode ver a `Hello World` guia carregada com a guia escolhida:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Teste seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` , seguido de sua mensagem. Isso é chamado de **\@ menção**. Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

**Para testar sua extensão de mensagens**
1. Selecione os três pontos abaixo da caixa de entrada no seu exibição de conversa. Um menu com o **aplicativo "Hello World"** é exibido.
1. Selecione o menu. Um conjunto de textos aleatórios é exibido. Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Selecione um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior:

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

 ## <a name="see-also"></a>Confira também

* [Visão geral dos tutoriais](code-samples.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)