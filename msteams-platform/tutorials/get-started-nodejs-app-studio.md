---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a construir aplicativos Microsoft Teams com Node.js.
keywords: começando node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 46272671443e07432513b667af424b5c5be05f2e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566534"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a>Crie seu primeiro aplicativo de Microsoft Teams usando Node.js

Este tutorial ajuda você a começar a criar um aplicativo Microsoft Teams usando Node.js.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Baixe e hospede seu aplicativo

Siga estas etapas para baixar e hospedar um aplicativo simples "Hello world" em Teams.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Obter pré-requisitos

Para completar este tutorial, você precisa das seguintes ferramentas. Se você ainda não os tiver, você pode instalá-los a partir desses links.

- [Git](https://git-scm.com/downloads)
- [Node.js e NPM](https://nodejs.org/)
- Obtenha qualquer editor de texto ou IDE. Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

Se você vir opções para `git` `node` adicionar, `npm` e ao PATH durante `code` a instalação, opte por fazê-lo. Será útil.

Verifique se as ferramentas estão disponíveis executando as seguintes em uma janela de terminal:

> [!NOTE]
> Use a janela do terminal com a sua plataforma. Esses exemplos usam bash (que está incluído no Git), mas esses scripts serão executados na maioria das plataformas.

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

Você pode ter uma versão diferente desses aplicativos. Isso não deve ser um problema, exceto para gole. Para o gol de gol, você precisará usar a versão 4.0.0 ou posterior.

Se você não tiver o gole instalado (ou tiver a versão errada instalada), faça-o agora, executando `npm install gulp` na janela do terminal.

Se você tiver instalado Visual Studio Code, você pode verificar a instalação executando:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Você pode continuar a usar esta janela de terminal para executar os comandos que seguem neste tutorial.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Baixe a amostra

Nós fornecemos um simples [Olá, Mundo!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) amostra para começar. Em uma janela terminal, execute o seguinte comando para clonar o repositório de amostras para sua máquina local:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações em seu GitHub repo para referência futura.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Uma vez que o repo é clonado, mude para o diretório que contém a amostra:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Para construir a amostra, você precisa instalar todas as suas dependências. Execute o seguinte comando para fazer isso:

```bash
npm install
```

Você deveria ver um monte de dependências sendo instaladas. Uma vez terminados, você pode executar o aplicativo:

```bash
npm start
```

Quando o aplicativo hello-world é iniciado, ele é exibido `App started listening on port 3333` na janela do terminal.

> [!NOTE]
> Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem um conjunto variável de ambiente PORT. Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.

Neste ponto, você pode abrir uma janela do navegador e navegar para os seguintes URLs para verificar se todos os URLs do aplicativo estão carregando:

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hospede o aplicativo de amostra

Lembre-se que os aplicativos em Microsoft Teams são aplicativos web expondo um ou mais recursos. Para que a plataforma Teams carregue seu aplicativo, seu aplicativo deve ser acessível a partir da internet. Para tornar seu aplicativo acessível a partir da internet, você precisa *hospedar* seu aplicativo.

Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto final da Web. [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com *o ngrok* você pode obter um endereço web como `https://d0ac14a5.ngrok.io` (esta URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) *ngrok* para o seu ambiente. Certifique-se de adicioná-lo a um local em seu `PATH` .

Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. A amostra usa a porta 3333, então não deixe de especificá-la aqui:

```bash
ngrok http 3333 -host-header=localhost:3333
```

*A Ngrok* ouvirá as solicitações da internet e as encaminhará para o seu aplicativo que será executado na porta 3333. Você pode verificar abrindo seu navegador e indo `https://d0ac14a5.ngrok.io/hello` para carregar a página de olá do seu aplicativo. Por favor, certifique-se de usar o endereço de encaminhamento exibido por *ngrok* na sessão do console em vez desta URL.

> [!NOTE]
> Se você tiver usado uma porta diferente na [construção e executar](#build-and-run-the-sample) passo acima, certifique-se de usar o mesmo número de porta para configurar o túnel *ngrok.*
> [!TIP]
> É uma boa ideia executar *ngrok* em uma janela de terminal diferente para mantê-lo funcionando sem interferir com o aplicativo de nó que você pode mais tarde ter que parar, reconstruir e reexer. A sessão *ngrok* retornará informações úteis de depuração nesta janela.

Há uma versão paga de *ngrok* que permite nomes persistentes. Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual na sua máquina de desenvolvimento. Se a máquina estiver desligada ou for dormir, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para testes por outros usuários. Se você tiver que reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar todos os lugares que usarem esse endereço.

Lembre-se, anote a URL do seu aplicativo porque você precisará disso mais tarde quando registrar o aplicativo com Teams usando o estúdio App. Bloco de notas funciona bem para este fim.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Implante seu aplicativo para Microsoft Teams

Neste ponto você tem um aplicativo hospedado na internet, mas você ainda não tem como dizer Teams onde procurá-lo, ou mesmo como seu aplicativo é chamado. Para fazer isso, agora você tem que criar um pacote de aplicativos. Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o Teams cliente usará para exibir e marcar corretamente seu aplicativo. Você pode criar manualmente este pacote de aplicativos, ou pode usar o App Studio, uma ferramenta que é executada em Teams que simplificará o processo de registro do aplicativo. App Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.

Para qualquer outro método, você precisará do seguinte:

- A URL onde seu aplicativo pode ser encontrado na internet.
- Ícones que Teams usarão para marcar seu aplicativo. A amostra vem com ícones de espaço reservado localizados em imagens "src\estática\. O App Studio também fornecerá ícones padrão, se necessário.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Atualize seu aplicativo hospedado

O aplicativo de amostra requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma nota anteriormente:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Como você faz isso difere dependendo de como você hospedou seu aplicativo. O importante sobre o uso de variáveis ambientais é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código do seu aplicativo, mas eles não estão expostos a terceiros que podem examinar os arquivos que compõem seu site.

Se você estiver executando o aplicativo usando ngrok, você precisará configurar algumas variáveis ambientais locais. Existem muitas maneiras de fazer isso, mas o mais fácil, se você estiver usando Visual Studio Code, é adicionar uma [configuração de lançamento:](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)

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

MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é o ID e senha, respectivamente, para o seu bot.
NODE_DEBUG mostrará o que está acontecendo no seu bot no console de depuração Visual Studio Code.
NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura-o na pasta src).

> [!Note]
> Se você não parou npm de antes no tutorial, você precisará executar para que Visual Studio Code para pegar suas variáveis de configuração de `npm stop` lançamento corretamente.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Configure a guia do aplicativo

Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo. Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode escolher `Hello World` entre a lista Adicionar uma **guia.** Em seguida, você será apresentado com um diálogo de configuração. Esta caixa de diálogo permitirá que você escolha qual guia exibir neste canal. Depois de selecionar a guia e `Save` clicar, você pode ver a `Hello World` guia carregada com a guia escolhida:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Teste seu bot em Teams

Agora você pode interagir com o bot em Teams. Escolha um canal na equipe onde você registrou seu aplicativo e `@your-bot-name` digite , seguido de sua mensagem. Isso é chamado de **\@ menção.** Qualquer mensagem que você enviar para o bot será enviada de volta para você como uma resposta:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Teste sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na sua visualização de conversação. Um menu aparecerá com o aplicativo **'Hello World'** nele. Quando você clicar nele, você verá uma série de textos aleatórios. Você pode escolher qualquer um deles e ele será inserido em sua conversa:

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios e verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior:

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
