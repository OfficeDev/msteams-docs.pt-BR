---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a criar aplicativos do Microsoft Teams com Node.js.
keywords: getting started node.js nodejs App Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 61be1056a07952c6cf166dbe183fa257ceaf7227
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294758"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a>Crie seu primeiro aplicativo do Microsoft Teams usando Node.js

Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams usando Node.js.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Baixar e hospedar seu aplicativo

Siga estas etapas para baixar e hospedar um aplicativo simples "hello world" no Teams.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa das seguintes ferramentas. Se você ainda não os tiver, poderá instalá-los a partir desses links.

- [Git](https://git-scm.com/downloads)
- [Node.js e NPM](https://nodejs.org/)
- Obter qualquer editor de texto ou IDE. Você pode instalar e usar [Visual Studio Código](https://code.visualstudio.com/download) gratuitamente.

Se você vir opções para adicionar , , e ao PATH durante a `git` `node` `npm` `code` instalação, escolha fazer isso. Ele será útil.

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

Se você tiver instalado Visual Studio Código, poderá verificar a instalação executando:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Baixar o exemplo

Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) exemplo para começar. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador local:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações no repositório do GitHub para referência futura.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repo for clonado, altere para o diretório que contém o exemplo:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Para criar o exemplo, você precisa instalar todas as suas dependências. Execute o seguinte comando para fazer isso:

```bash
npm install
```

Você deve ver várias dependências sendo instaladas. Depois que eles terminarem, você poderá executar o aplicativo:

```bash
npm start
```

Quando o aplicativo hello-world é iniciado, ele é `App started listening on port 3333` exibido na janela do terminal.

> [!NOTE]
> Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem uma variável de ambiente PORT definida. Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.

Neste ponto, você pode abrir uma janela do navegador e navegar até as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Lembre-se de que os aplicativos no Microsoft Teams são aplicativos Web expondo um ou mais recursos. Para que a plataforma do Teams carregue seu aplicativo, seu aplicativo deve ser acessível pela Internet. Para tornar seu aplicativo acessível pela Internet, você precisa *hospedar* seu aplicativo.

Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto de extremidade da Web. [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com *o ngrok,* você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para seu ambiente. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalá-la, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.

```bash
ngrok http 3333 -host-header=localhost:3333
```

*O Ngrok* ouvirá as solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333. Você pode verificar abrindo seu navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo. Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console em vez dessa URL.

> [!NOTE]
> Se você tiver usado uma porta diferente na [com](#build-and-run-the-sample) build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o *túnel ngrok.*
> [!TIP]
> É uma boa ideia executar *o ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo de nó que talvez você tenha que parar, recriar e executar de novo. A *sessão ngrok* retornará informações úteis de depuração nesta janela.

Há uma versão paga do *ngrok* que permite nomes persistentes. Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em seu computador de desenvolvimento. Se o computador for desligado ou for parar, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários. Se você tiver que reiniciar o serviço, ele retornará um novo endereço e será preciso atualizar todos os lugares que usam esse endereço.

Lembre-se de anotar a URL do seu aplicativo porque você precisará disso mais tarde quando registrar o aplicativo com o Teams usando o App studio. O bloco de notas funciona bem para essa finalidade.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Implantar seu aplicativo no Microsoft Teams

Neste ponto, você tem um aplicativo hospedado na Internet, mas ainda não tem como dizer ao Teams onde procurar por ele ou mesmo como seu aplicativo é chamado. Para fazer isso, agora você precisa criar um pacote de aplicativos. Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o cliente do Teams usará para exibir e sinalizar corretamente seu aplicativo. Você pode criar manualmente esse pacote de aplicativos ou usar o App Studio, uma ferramenta que é executado no Teams que simplificará o processo de registro do aplicativo. App Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.

Para qualquer um dos métodos, você precisará do seguinte:

- A URL onde seu aplicativo pode ser encontrado na Internet.
- Ícones que o Teams usará para fazer a marca do aplicativo. O exemplo vem com ícones de espaço reservado localizados em "src\static\images. O App Studio também fornecerá ícones padrão, se necessário.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Atualizar seu aplicativo hospedado

O aplicativo de exemplo exige que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma anotação anteriormente.

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Como fazer isso difere dependendo de como você hospedou seu aplicativo. O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código para seu aplicativo, mas não são expostos a terceiros que podem examinar os arquivos que compusem seu site.

Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente local. Há muitas maneiras de fazer isso, mas a mais fácil, se você estiver usando Visual Studio Código, é adicionar uma configuração [de lançamento](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):

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
NODE_DEBUG mostrará o que está acontecendo no bot no Visual Studio depuração de código.
NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura por ele na pasta src).

> [!Note]
> Se você não tiver interrompido npm de anteriormente no tutorial, você precisará executar para que o código Visual Studio para receber suas variáveis de configuração de `npm stop` início corretamente.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Configurar a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode `Hello World` escolher na lista Adicionar **uma** guia. Em seguida, você será apresentado com uma caixa de diálogo de configuração. Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e clicar em, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` , seguido de sua mensagem. Isso é chamado de **\@ menção**. Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no seu exibição de conversa. Um menu será aberto com o **aplicativo "Hello World"** nele. Ao clicar nele, você verá vários textos aleatórios. Você pode escolher qualquer um deles e ele será inserido em sua conversa.

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
