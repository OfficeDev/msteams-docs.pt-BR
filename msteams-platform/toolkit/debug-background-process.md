---
title: Depurar processos em segundo plano
author: zyxiaoyuer
description: Função do Visual Studio Code e do Kit de Ferramentas do Teams durante a depuração local
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: 74aa3ef53aab329b0b2acae34dc976c142703e0e
ms.sourcegitcommit: 5e5d2d3fb621bcbd9d792a5b450f95167ec8548b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63731549"
---
# <a name="debug-background-process"></a>Depurar processo em segundo plano

O fluxo de trabalho de depuração local envolve os arquivos `.vscode/launch.json` e `.vscode/tasks.json` para configurar o depurador no Visual Studio Code, o Visual Studio Code inicia os depuradores e o depurador Microsoft Edge ou Chrome inicia uma nova instância do navegador da seguinte maneira:

1. O arquivo `launch.json` configura o depurador no Visual Studio Code. 

2. Visual Studio Code executa o `preLaunchTask`, `Pre Debug Check & Start All` no arquivo `.vscode/tasks.json`.

3. Visual Studio Code, em seguida, inicia os depuradores especificados nas configurações compostas, como **Anexar ao Bot**, **Anexar ao back-end**, **Anexar ao front-end** e **Iniciar bot**.

4.  Microsoft Edge ou depurador do Chrome inicia uma nova instância do navegador e abre uma página da Web para carregar o cliente do Teams.

## <a name="prerequisites"></a>Pré-requisitos

O Kit de Ferramentas do Teams verifica os seguintes pré-requisitos durante o processo de depuração:

* Node.js, aplicável aos seguintes tipos de projeto:

  |Tipo de projeto|Versão LTS do Node.js|
  |----------|--------------------------------|
  |Guia sem Azure Functions | 10, 12, **14 (recomendado)**, 16 |
  |Guia com Azure Functions | 10, 12, **14 (recomendado)**|
  |Bot |  10, 12, **14 (recomendado)**, 16|
  |Extensão de mensagem | 10, 12, **14 (recomendado)**, 16 |

   
* Microsoft 365 conta com credenciais válidas, o kit de ferramentas do Teams solicitará que você entre em uma Microsoft 365, caso ainda não tenha entrado.

* O carregamento ou sideload de aplicativo personalizado para seu locatário do desenvolvedor está ativado. Caso contrário, a depuração local será encerrada.

* Versão binária do Ngrok 2.3, aplicável ao bot e à extensão de mensagens.  Se o Ngrok não estiver instalado ou a versão não corresponder ao requisito, o kit de ferramentas do Teams instalará o pacote NPM do Ngrok `ngrok@4.2.2` no `~/.fx/bin/ngrok`. O binário Ngrok é gerenciado pelo pacote Ngrok NPM em `/.fx/bin/ngrok/node modules/ngrok/bin`.

* Azure Functions Core Tools versão 3. Se Azure Functions Core Tools não estiver instalado ou se a versão não corresponder ao requisito, o kit de ferramentas do Teams instalará Azure Functions Core Tools pacote NPM, azure-functions-core-tools@3 para **Windows** e para **macOs** em `~/.fx/bin/func`. O Azure Functions Core Tools pacote NPM no `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` gerencia Azure Functions Core Tools binário. Para Linux, a depuração local é encerrada.

* SDK do .NET Core versão, aplicável para Azure Functions. Se SDK do .NET Core não estiver instalado ou se a versão não corresponder ao requisito, o Kit de Ferramentas do Teams instalará o SDK do .NET Core para Windows e MacOS no `~/.fx/bin/dotnet`. Para Linux, a depuração local é encerrada.

  A tabela a seguir lista as versões do .NET Core:

  | Plataforma  | Software|
  | --- | --- |
  |Windows, macOs (x64) e Linux | **3.1 (recomendado)**, 5.0, 6.0 |
  |macOs (arm64) |6.0 |

* Certificado de desenvolvimento, se o certificado de desenvolvimento para localhost não estiver instalado para a guia no Windows ou macOS, o kit de ferramentas do Teams solicitará que você o instale.

* Azure Functions de associação definidas em `api/extensions.csproj`. Se Azure Functions de associação não estiver instalada, o Kit de Ferramentas do Teams instalará Azure Functions de associação.

* Pacotes NPM, aplicáveis ao aplicativo tab, ao aplicativo de bot, ao aplicativo de extensão de mensagens e Azure Functions. Se o NPM não estiver instalado, o Kit de Ferramentas do Teams instalará todos os pacotes NPM.

* Bot e extensão de mensagens. O Kit de Ferramentas do Teams inicia o Ngrok para criar um túnel HTTP para o bot e a extensão de mensagens.

* As portas disponíveis, se tab, bot, extensão de mensagens e Azure Functions portas não estiverem disponíveis, a depuração local será encerrada.

  A tabela a seguir lista as portas disponíveis para componentes:

  | Componente  | Porta |
  | --- | --- |
  | Tab | 53000 |
  | Bot ou extensão de mensagens | 3978 |
  | Inspetor de nó para bot ou extensão de mensagens | 9239 |
  | Azure Functions | 7071 |
  | Inspetor de nó para Azure Functions | 9229 |


<!-- The following table lists the limitations if the required software is unavailable for debugging:

|Project type|Installation| Limitation|
|----------|--------------------------------|-----|
|Tab without Azure functions | Node.js LTS versions 10, 12, **14 (recommended)**, 16 | The local debug terminates, if Node.js is not installed or the version doesn't match the requirement.|
|Tab with Azure functions | Node.js LTS versions 10, 12, **14 (recommended)** |The local debug terminates, if Node.js is not installed or the version doesn't match the requirement.|
|Bot | Node.js LTS versions 10, 12, **14 (recommended)**, 16|The local debug terminates, if Node.js is not installed or the version doesn't match the requirement.|
|Messaging extension | Node.js LTS versions 10, 12, **14 (recommended)**, 16 |The local debug terminates, if Node.js is not installed or the version doesn't match the requirement.|
|Sign in to Microsoft 365 account | Microsoft 365 credentials |Teams toolkit prompts you to sign in to Microsoft 365 account, if you haven't signed in. |
|Bot, messaging extension | Ngrok version 2.3| • If Ngrok is not installed or the version doesn't match the requirement, the Teams toolkit installs Ngrok NPM package `ngrok@4.2.2` in `~/.fx/bin/ngrok`. </br> • The Ngrok binary is managed by Ngrok NPM package in `/.fx/bin/ngrok/node modules/ngrok/bin`.|
|Azure functions | Azure Functions Core Tools version 3| • If Azure Functions Core Tools is not installed or the version doesn't match the requirement, the Teams toolkit installs Azure Functions Core Tools NPM package, azure-functions-core-tools@3 for **Windows** and for **macOs** in  `~/.fx/bin/func`. </br> • The Azure Functions Core Tools NPM package in  `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` manages Azure Functions Core Tools binary. For Linux, the local debug terminates.|
|Azure functions |.NET Core SDK version|• If .NET Core SDK is not installed or the version  doesn't match the requirement, the toolkit installs .NET Core SDK for Windows and macOS in `~/.fx/bin/dotnet`.</br> • For Linux, the local debug terminates.|
|Azure functions | Azure functions binding extensions defined in `api/extensions.csproj`| If Azure functions binding extensions is not installed, the toolkit installs Azure functions binding extensions.|
|NPM packages| NPM packages for tab app, bot app, messaging extension app, and Azure functions|If NPM is not installed, the toolkit installs all NPM packages.|
|Bot and messaging extension | Ngrok |Toolkit starts Ngrok to create a HTTP tunnel for bot and messaging extension. |

> [!NOTE]
> If tab, bot, messaging extension, and Azure functions ports are unavailable, the local debug terminates.

Use the following .NET Core versions:

| Platform  | Software|
| --- | --- |
|Windows, macOs (x64), Linux | **3.1 (recommended)**, 5.0, 6.0 |
|macOs (arm64) |6.0 |


> [!NOTE]
> If the development certificate for localhost is not installed for tab in Windows or macOS, the Teams toolkit prompts you to install it.</br> -->


Quando você seleciona **Iniciar Depuração (F5)**, o canal de saída do Kit de Ferramentas do Teams exibe o progresso e o resultado depois de verificar os pré-requisitos.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/prerequisites-debugcheck.png" alt-text="pré-requisitos":::

## <a name="register-and-configure-your-teams-app"></a>Registrar e configurar seu aplicativo Teams

No processo de configuração, o Kit de Ferramentas do Teams prepara os seguintes registros e configurações para seu aplicativo Teams:

1. [Registra e configura o aplicativo do Azure AD](#registers-and-configures-azure-ad-application): O Kit de Ferramentas do Teams registra e configura seu aplicativo do Azure AD.

1. [Registra e configura o bot](#registers-and-configures-bot): O Kit de Ferramentas do Teams registra e configura seu bot para aplicativo de extensão de mensagens ou guia.

1. [Registers e configura o aplicativo Teams](#registers-and-configures-teams-app): O Kit de Ferramentas do Teams registra e configura seu aplicativo Teams.

### <a name="registers-and-configures-azure-ad-application"></a>Registra e configura o aplicativo do Azure AD

1. Registra um aplicativo do Azure AD.

1. Cria um segredo do cliente.

1. Expõe uma API.

    a. Configura o URI da ID do Aplicativo. Para guia, `api://localhost/{appId}`. Para extensão de bot ou de mensagens, `api://botid-{botid}`.

    b. Adiciona um escopo chamado `access_as_user`. Habilita-o para **Administrador e usuários**.

A tabela a seguir lista as configurações Microsoft 365 aplicativo cliente com as IDs do cliente:

  | Microsoft 365 aplicativo cliente |  ID do cliente  |
  | --- | --- |
  | Área de trabalho do Teams, celular | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
  | Web do Teams | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
  | Office.com | 4345a7b9-9a63-4910-a426-35363201d503 |
  | Office.com | 4765445b-32c6-49b0-83e6-1d93765276ca |
  | Office para a área de trabalho | 0ec893e0-5785-4de6-99da-4ed124e5296c |
  | Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
  | Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
  | Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

4. Configura permissões de API. Adiciona permissão do Microsoft Graph para **User.Read**.

A tabela a seguir lista a configuração da autenticação da seguinte maneira:

  | Tipo de projeto | URIs de redirecionamento para a Web | URIs de redirecionamento para aplicativo de página única |
  | --- | --- | --- |
  | Tab | `https://localhost:53000/auth-end.html` | `https://localhost:53000/auth-end.html?clientId={appId>}` |
  | Bot ou extensão de mensagens | `https://ngrok.io/auth-end.html` | NA |
  
### <a name="registers-and-configures-bot"></a>Registra e configura o bot 

Para aplicativo de guia ou aplicativo de extensão de mensagens:

1. Registra um aplicativo do Azure AD.

1. Cria um Segredo do Cliente para o aplicativo do Azure AD.

1. Registra um bot no [Microsoft Bot Framework](https://dev.botframework.com/) usando o aplicativo do Azure AD.

1. Adiciona o canal do Microsoft Teams.

1. Configura o ponto de extremidade de mensagens como `https://{ngrokTunnelId}.ngrok.io/api/messages`.

### <a name="registers-and-configures-teams-app"></a>Registra e configura o aplicativo Teams

Registra um aplicativo Teams no [Developer](https://dev.teams.microsoft.com/home) usando o modelo de manifesto em `templates/appPackage/manifest.local.template.json`.

Depois de registrar e configurar o aplicativo, os arquivos de depuração locais são gerados.

## <a name="take-a-tour-of-your-app-source-code"></a>Faça um tour pelo código-fonte do aplicativo

Você pode exibir as pastas e os arquivos do projeto na área Explorer do Visual Studio Code depois que o Kit de Ferramentas do Teams registrar e configurar seu aplicativo. A tabela a seguir lista os arquivos de depuração locais e os tipos de configuração:

| Nome da pasta| Conteúdos| Tipo de configuração de depuração |
| --- | --- | --- |
|  `.fx/configs/localSettings.json` | Arquivo de configuração de depuração local | Os valores de cada configuração geram e salvam durante a depuração local. |
|  `templates/appPackage/manifest.local.template.json` | Arquivo de modelo de manifesto do aplicativo Teams para depuração local | Os espaços reservados no arquivo são resolvidos durante a depuração local. |
|  `tabs/.env.teams.local`  | Arquivo de variáveis de ambiente para a guia  | Os valores de cada variável de ambiente geram e salvam durante a depuração local. |
|  `bot/.env.teamsfx.local` | Arquivo de variáveis de ambiente para bot e extensão de mensagens| Os valores de cada variável de ambiente geram e salvam durante a depuração local. |
| `api/.env.teamsfx.local`  | Arquivo de variáveis de ambiente para Azure Functions | Os valores de cada variável de ambiente geram e salvam durante a depuração local. |


## <a name="see-also"></a>Confira também

[Depurar seu aplicativo Teams usando o Kit de Ferramentas do Teams](debug-local.md)