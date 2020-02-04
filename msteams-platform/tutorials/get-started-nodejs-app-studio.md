---
title: Introdução ao app Studio e node. js
description: Introdução à criação de ótimos aplicativos no Microsoft Teams usando node. js e app Studio
keywords: Getting Started node. js NodeJS app Studio
ms.date: 11/09/2018
ms.openlocfilehash: 36da6d7445ad7780f6bbbf52ccce3e558c76be72
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672884"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-nodejs-and-app-studio"></a>Introdução à plataforma do Microsoft Teams com node. js e app Studio

A plataforma de desenvolvedor do [Microsoft Teams](/microsoftteams/) facilita a extensão de equipes e a integração de seus próprios aplicativos e serviços diretamente no espaço de trabalho do Microsoft Teams. Esses aplicativos podem ser distribuídos para sua empresa ou para o Teams em todo o mundo.

Para estender o Microsoft Teams, você precisa criar um aplicativo do Microsoft Teams. Um aplicativo do Microsoft Teams é um aplicativo Web que você hospeda. Esse aplicativo pode ser integrado ao espaço de trabalho do usuário no Microsoft Teams.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Baixar e hospedar seu aplicativo

Siga estas etapas para baixar e hospedar um aplicativo simples "Olá mundo" no Microsoft Teams.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Obter pré-requisitos

Para concluir este tutorial, você precisa das ferramentas a seguir. Se você ainda não os tiver, poderá instalá-los a partir desses links.

- [Git](https://git-scm.com/downloads)
- [Node. js e NPM](https://nodejs.org/)
- Obtenha qualquer editor de texto ou IDE. Você pode instalar e usar o [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

Se você vir opções para adicionar `git`, `node`, `npm`e `code` ao caminho durante a instalação, escolha fazer isso. Será útil.

Verifique se as ferramentas estão disponíveis executando o seguinte em uma janela de terminal:

> [!NOTE]
> Use a janela do terminal com a qual você se sente mais confortável em sua plataforma. Estes exemplos usam o bash (incluído no git), mas esses scripts serão executados na maioria das plataformas.

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 4.0.2
```

Você pode ter uma versão diferente desses aplicativos. Isso não deve ser um problema, exceto para o Gulp. Para o Gulp, você precisará usar a versão 4.0.0 ou posterior.

Se você não tiver o Gulp instalado (ou se tiver a versão incorreta instalada), faça- `npm install gulp` o agora executando na janela do terminal.

Se você tiver instalado o Visual Studio Code, é possível verificar a instalação executando:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Você pode continuar a usar esta janela de terminal para executar os comandos a seguir neste tutorial.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Baixar o exemplo

Fornecemos um simples [Olá, mundo!](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) exemplo para começar. Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repositório](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) se quiser modificar e fazer check-in de suas alterações no repositório do GitHub para referência futura.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Criar e executar o exemplo

Depois que o repositório for clonado, mude para o diretório que contém o exemplo:

```bash
cd msteams-samples-hello-world-nodejs
```

Para criar o exemplo, você precisa instalar todas as suas dependências. Execute o seguinte comando para fazer isso:

```bash
npm install
```

Você deve ver uma porção de dependências que está sendo instalada. Após a conclusão, é possível executar o aplicativo:

```bash
npm start
```

Quando o aplicativo Hello-World é iniciado, ele `App started listening on port 3333` é exibido na janela do terminal.

> [!NOTE]
> Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem um conjunto de variáveis de ambiente de porta. Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.

Neste ponto, você pode abrir uma janela do navegador e navegar até as seguintes URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hospedar o aplicativo de exemplo

Lembre-se de que aplicativos no Microsoft Teams são aplicativos da Web que expõem um ou mais recursos. Para que a plataforma do teams carregue seu aplicativo, seu aplicativo deve estar acessível pela Internet. Para tornar seu aplicativo alcançável da Internet, você precisa *hospedar* seu aplicativo.

Para teste local, você pode executar o aplicativo na sua máquina local e criar um túnel para ele com um ponto de extremidade da Web. o [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso. Com o *ngrok* , você pode obter um endereço da `https://d0ac14a5.ngrok.io` Web como (esta URL é apenas um exemplo). Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para o seu ambiente. Certifique-se de adicioná-lo a um local `PATH`no seu.

Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel. O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.

```bash
ngrok http 3333 -host-header=localhost:3333
```

O *Ngrok* ouvirá as solicitações da Internet e irá encaminhá-las para seu aplicativo em execução na porta 3333. Você pode verificar abrindo seu navegador e indo `https://d0ac14a5.ngrok.io/hello` para carregar a página de saudação do aplicativo. Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console, em vez desta URL.

> [!NOTE]
> Se você tiver usado uma porta diferente na etapa [criar e executar](#build-and-run-the-sample) acima, certifique-se de usar o mesmo número de porta para instalar o túnel *ngrok* .
> [!TIP]
> É uma boa ideia executar o *ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo do nó, que pode ser mais tarde interrompido, recriar e executar novamente. A sessão do *ngrok* retornará informações úteis de depuração nesta janela.

Há uma versão paga do *ngrok* que permite nomes persistentes. Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento. Se o computador estiver desligado ou chegar à suspensão, o serviço não estará mais disponível. Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários. Se for necessário reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar cada lugar que usa esse endereço.

Lembre-se, anote a URL do aplicativo porque você precisará disso mais tarde, quando registrar o aplicativo com o Teams usando o app Studio. O bloco de notas funciona bem para essa finalidade.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Implantar seu aplicativo no Microsoft Teams

Neste ponto, você tem um aplicativo hospedado na Internet, mas não tem nenhuma forma de informar às equipes onde procurá-lo, ou até mesmo o que seu aplicativo é chamado. Para fazer isso, agora você precisa criar um pacote de aplicativos. Isso é pouco mais que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o cliente Teams usará para exibir e marcar corretamente o seu aplicativo. Você pode criar manualmente esse pacote de aplicativos ou pode usar o app Studio, uma ferramenta executada no Teams que simplificará o processo de registro do aplicativo. O app Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.

Para ambos os métodos, você precisará do seguinte:

- A URL onde seu aplicativo pode ser encontrado na Internet.
- Ícones que as equipes usarão para marcar seu aplicativo. O exemplo vem com ícones de espaço reservado localizados em "src\static\images. O app Studio também fornecerá ícones padrão, se necessário.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Atualizar seu aplicativo hospedado

O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez antes.

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

O modo como você faz isso difere dependendo de como você hospedáou seu aplicativo. O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte de seu ambiente-eles podem ser acessados pelo código para seu aplicativo, mas não estão expostos a terceiros que podem examinar os arquivos que fazem parte de seu site.

Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente locais. Há várias maneiras de fazer isso, mas a mais fácil, se você estiver usando o Visual Studio Code, é adicionar uma [configuração de lançamento](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):

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

MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é a ID e a senha, respectivamente, para o bot.
NODE_DEBUG mostrará o que está acontecendo no bot no console de depuração de código do Visual Studio.
NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele o procura na pasta src).

> [!Note]
> Se você não tiver parado o NPM de versões anteriores no tutorial, você precisará executar `npm stop` para que o Visual Studio Code retorne suas variáveis de configuração de inicialização corretamente.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Configurar a guia aplicativo

Após instalar o aplicativo em uma equipe, você precisará configurá-lo para exibir o conteúdo. Vá para um canal na equipe e clique no botão **"+"** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista **Adicionar uma guia** . Em seguida, será exibida uma caixa de diálogo de configuração. Esta caixa de diálogo permitirá que você escolha qual guia será exibida neste canal. Depois de selecionar a guia e clicar em `Save` , você poderá ver `Hello World` a guia carregada com a guia escolhida.

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Captura de tela da configuração" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot no Teams. Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name`, seguido de sua mensagem. Isso é chamado de ** \@menção**. Qualquer mensagem enviada ao bot será enviada de volta para você como resposta.

<img width="450px" title="Respostas de bot" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no modo de exibição de conversa. Um menu será exibido com o aplicativo **"Olá mundo"** . Quando você clicar nele, verá um número de textos aleatórios. Você pode escolher qualquer uma delas e ela será inserida na conversa.

<img width="430px" title="Menu de extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" title="Resultado da extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Escolha um dos textos aleatórios, e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.

<img width="430px" title="Envio de extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
