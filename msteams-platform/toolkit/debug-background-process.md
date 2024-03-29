---
title: Depurar processos em segundo plano
author: surbhigupta
description: Neste módulo, como o Visual Studio Code e o Kit de Ferramentas do Teams funcionam durante o processo de depuração local, também como registrar e configurar seu aplicativo teams
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: 4d654d5da598b9bf2b9bacfc189c97df08f9a359
ms.sourcegitcommit: 707dad21dc3cf79ac831afe05096c0341bcf2fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68653641"
---
# <a name="debug-background-process"></a>Depurar processo em segundo plano

O processo de depuração local envolve os `.vscode/launch.json` arquivos `.vscode/tasks.json` e os arquivos para configurar o depurador no Microsoft Visual Studio Code. O Visual Studio Code inicia os depuradores e o Microsoft Edge ou o Google Chrome inicia uma nova instância do navegador.

O fluxo de trabalho do processo de depuração é o seguinte:

1. `launch.json` file configures the debugger in Visual Studio Code.

2. Visual Studio Code executa o **pré-inicialização compostoTask**, **inicie o aplicativo Teams localmente** no `.vscode/tasks.json` arquivo.

3. Visual Studio Code, em seguida, inicia os depuradores especificados nas configurações compostas, como **Anexar ao Bot**, **Anexar ao back-end**, **Anexar ao front-end** e **Iniciar bot**.

4. O Microsoft Edge ou o Google Chrome inicia uma nova instância do navegador e abre uma página da Web para carregar o cliente do Teams.

## <a name="verification-of-prerequisites"></a>Verificação de pré-requisitos

O Kit de Ferramentas do Teams verifica os seguintes pré-requisitos durante o processo de depuração:

* Node.js, aplicável aos seguintes tipos de projeto:

  |Tipo de projeto|Versão LTS do Node.js|
  |----------|--------------------------------|
  |Guia | 14, 16 (recomendado) |
  |Guia SPFx | 14, 16 (recomendado)|
  |Bot |  14, 16 (recomendado)|
  |Extensão de mensagem | 14, 16 (recomendado) |

* O Kit de Ferramentas do Teams solicitará que você entre na conta do Microsoft 365, caso ainda não tenha entrado com suas credenciais válidas.
* O carregamento ou sideload de aplicativo personalizado para seu locatário do desenvolvedor está ativado para evitar o encerramento de depuração local.
* O Kit de Ferramentas do Teams instala o pacote NPM `ngrok@4.2.2` `~/.fx/bin/ngrok`do Ngrok, se o Ngrok não estiver instalado ou se a versão não corresponder ao requisito. A versão binária Ngrok 2.3 é aplicável ao bot e à extensão de mensagem. O binário Ngrok é gerenciado pelo pacote Ngrok NPM em `/.fx/bin/ngrok/node modules/ngrok/bin`.
* O Azure Functions Kit de Ferramentas do Teams instala um pacote NPM do Teams Core Tools, azure-functions-core-tools@3 para **Windows** e **MacOs**`~/.fx/bin/func`, se o Azure Functions Core Tools versão 4 não estiver instalado ou se a versão não corresponder ao requisito. O pacote NPM do Azure Functions Core Tools em `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` gerencia o binário do Azure Functions Core Tools. Para Linux, a depuração local é encerrada.
* O Kit de Ferramentas do Teams instala o SDK do .NET Core para **Windows** e **MacOS** `~/.fx/bin/dotnet`na versão do SDK do .NET Core aplicável ao Azure Functions, se o SDK do .NET Core não estiver instalado ou a versão não corresponder ao requisito. Para Linux, a depuração local é encerrada.

  A tabela a seguir lista as versões do .NET Core:

  | Plataforma  | Software|
  | --- | --- |
  |Windows, macOS (x64) e Linux | **3.1 (recomendado)**, 5.0, 6.0 |
  |macOS (arm64) |6.0 |

* Certificado de desenvolvimento, se o certificado de desenvolvimento para localhost não estiver instalado para a guia no **Windows** ou **macOS**, o Kit de Ferramentas do Teams solicitará que você o instale.
* Azure Functions de associação definidas `api/extensions.csproj`em , se Azure Functions de associação não estiver instalada, o Kit de Ferramentas do Teams instalará Azure Functions de associação.
* Pacotes NPM, aplicáveis ao aplicativo tab, ao aplicativo de bot, ao aplicativo de extensão de mensagens e Azure Functions. Se os pacotes NPM não estiverem instalados, o Kit de Ferramentas do Teams instalará todos os pacotes NPM.
* Extensão de bot e mensagem, o Kit de Ferramentas do Teams inicia o Ngrok para criar um túnel HTTP para extensão de bot e mensagem.
* Portas disponíveis, se guia, bot, extensão de mensagem e portas do Azure Functions não estiverem disponíveis, a depuração local será encerrada.

  A tabela a seguir lista as portas disponíveis para componentes:

  | Componente  | Porta |
  | --- | --- |
  | Tab | 53000 |
  | Extensão de bot ou mensagem | 3978 |
  | Inspetor de nó para bot ou extensão de mensagens | 9239 |
  | Azure Functions | 7071 |
  | Inspetor de nó para Azure Functions | 9229 |

<!-- The following table lists the limitations if the required software is unavailable for debugging:

|Project type|Installation| Limitation|
|----------|--------------------------------|-----|
|Tab without Azure functions | Node.js LTS versions 10, 12, **14 (recommended)**, 16 | The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Tab with Azure functions | Node.js LTS versions 10, 12, **14 (recommended)** |The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Bot | Node.js LTS versions 10, 12, **14 (recommended)**, 16|The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Message extension | Node.js LTS versions 10, 12, **14 (recommended)**, 16 |The local debug terminates, if Node.js isn't installed or the version doesn't match the requirement.|
|Sign-in to Microsoft 365 account | Microsoft 365 credentials |Teams Toolkit prompts you to sign-in to Microsoft 365 account, if you haven't signed in. |
|Bot, message extension | Ngrok version 2.3| • If Ngrok isn't installed or the version doesn't match the requirement, the Teams Toolkit installs Ngrok NPM package `ngrok@4.2.2` in `~/.fx/bin/ngrok`. </br> • The Ngrok binary is managed by Ngrok NPM package in `/.fx/bin/ngrok/node modules/ngrok/bin`.|
|Azure functions | Azure Functions Core Tools version 3| • If Azure Functions Core Tools isn't installed or the version doesn't match the requirement, the Teams Toolkit installs Azure Functions Core Tools NPM package, azure-functions-core-tools@3 for **Windows** and for **macOs** in  `~/.fx/bin/func`. </br> • The Azure Functions Core Tools NPM package in `~/.fx/bin/func/node_modules/azure-functions-core-tools/bin` manages Azure Functions Core Tools binary. For Linux, the local debug terminates.|
|Azure functions |.NET Core SDK version|• If .NET Core SDK isn't installed or the version  doesn't match the requirement, the Toolkit installs .NET Core SDK for Windows and macOS in `~/.fx/bin/dotnet`.</br> • For Linux, the local debug terminates.|
|Azure functions | Azure functions binding extensions defined in `api/extensions.csproj`| If Azure functions binding extensions isn't installed, the Toolkit installs Azure functions binding extensions.|
|NPM packages| NPM packages for tab app, bot app, message extension app, and Azure functions|If NPM isn't installed, the Toolkit installs all NPM packages.|
|Bot and message extension | Ngrok |Toolkit starts Ngrok to create a HTTP tunnel for bot and message extension. |

> [!NOTE]
> If tab, bot, message extension, and Azure functions ports are unavailable, the local debug terminates.

Use the following .NET Core versions:

| Platform  | Software|
| --- | --- |
|Windows, macOs (x64), Linux | **3.1 (recommended)**, 5.0, 6.0 |
|macOs (arm64) |6.0 |

> [!NOTE]
> If the development certificate for localhost isn't installed for tab in Windows or MacOS, the Teams Toolkit prompts you to install it.</br> -->

Quando você seleciona **Iniciar Depuração (F5)**, o canal de saída do Kit de Ferramentas do Teams exibe o progresso e o resultado depois de verificar os pré-requisitos.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/prerequisites-debugcheck1.png" alt-text="Resumo da verificação de pré-requisitos" lightbox="../assets/images/teams-toolkit-v2/debug/prerequisites-debugcheck1.png":::

## <a name="register-and-configure-teams-app"></a>Registrar e configurar o aplicativo do Teams

No processo de configuração, o Kit de ferramentas do Teams prepara os seguintes registros e configurações para seu aplicativo do Teams:

1. [Registra e configura o Microsoft Azure Active Directory (Azure AD)](#registers-and-configures-microsoft-azure-active-directoryazure-ad-app)

1. [Registra e configura o bot](#registers-and-configures-bot).

1. [Registra e configura o aplicativo Teams](#registers-and-configures-teams-app).

### <a name="registers-and-configures-microsoft-azure-active-directoryazure-ad-app"></a>Registra e configura o Microsoft Azure Active Directory (Azure AD)

1. Registra um Azure AD aplicativo.

1. Cria um segredo do cliente.

1. Expõe uma API.

    a. Configura o URI da ID do Aplicativo. Para guia, `api://localhost/{appId}`. Para bot ou extensão de mensagem, `api://botid-{botid}`.

    b. Adiciona um escopo chamado `access_as_user`. Habilita-o para **Administrador e usuários**.

4. Configura permissões de API. Adiciona permissão do Microsoft Graph para **User.Read**.

    A tabela a seguir lista a configuração da autenticação:

      | Tipo de projeto | URIs de redirecionamento para a Web | URIs de redirecionamento para aplicativo de página única |
      | --- | --- | --- |
      | Tab | `https://localhost:53000/auth-end.html` | `https://localhost:53000/auth-end.html?clientId={appId>}` |
      | Extensão de bot ou mensagem | `https://ngrok.io/auth-end.html` | NA |

    A tabela a seguir lista as configurações do aplicativo cliente do Microsoft 365 com as IDs de cliente:

      | Microsoft 365 aplicativo cliente | ID do cliente |
      | --- | --- |
      | Área de trabalho do Teams, celular | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
      | Web do Teams | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
      | Office.com | 4345a7b9-9a63-4910-a426-35363201d503 |
      | Office.com | 4765445b-32c6-49b0-83e6-1d93765276ca |
      | Office para a área de trabalho | 0ec893e0-5785-4de6-99da-4ed124e5296c |
      | Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
      | Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
      | Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

### <a name="registers-and-configures-bot"></a>Registra e configura o bot

Para aplicativo de guia ou aplicativo de extensão de mensagens:

1. Registra um aplicativo do Azure AD.

1. Cria um Segredo do Cliente para o aplicativo do Azure AD.

1. Registra um bot no [Microsoft Bot Framework](https://dev.botframework.com/) usando o aplicativo do Azure AD.

1. Adiciona o Canal do Teams.

1. Configura o ponto de extremidade de mensagens como `https://{ngrokTunnelId}.ngrok.io/api/messages`.

### <a name="registers-and-configures-teams-app"></a>Registra e configura o aplicativo Teams

Registra um aplicativo do Teams no [Portal do Desenvolvedor](https://dev.teams.microsoft.com/home) usando o modelo de manifesto em `templates/appPackage/manifest.template.json`.

Após o registro e a configuração do aplicativo, são gerados arquivos de depuração locais.

## <a name="take-a-tour-of-your-app-source-code"></a>Faça um tour pelo código-fonte do aplicativo

Você pode exibir as pastas e os arquivos do projeto no **Explorer** no Visual Studio Code depois que o Kit de Ferramentas do Teams registrar e configurar seu aplicativo. A tabela a seguir lista os arquivos de depuração locais e os tipos de configuração:

| Nome da pasta| Conteúdos| Tipo de configuração de depuração |
| --- | --- | --- |
|  `.fx/configs/config.local.json` | Arquivo de configuração de depuração local | Os valores de cada configuração geram e salvam durante a depuração local. |
|  `templates/appPackage/manifest.template.json` | Arquivo de modelo de manifesto do aplicativo Teams para depuração local | Os espaços reservados no arquivo durante a depuração local. |
|  `tabs/.env.teams.local`  | Arquivo de variáveis de ambiente para a guia | Os valores de cada variável de ambiente geram e salvam durante a depuração local. |
|  `bot/.env.teamsfx.local` | Arquivo de variáveis de ambiente para bot e extensão de mensagens| Os valores de cada variável de ambiente geram e salvam durante a depuração local. |
| `api/.env.teamsfx.local`  | Arquivo de variáveis de ambiente para Azure Functions | Os valores de cada variável de ambiente geram e salvam durante a depuração local. |

## <a name="see-also"></a>Confira também

* [Depurar seu aplicativo Teams usando o Kit de Ferramentas do Teams](debug-local.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
* [Visualizar e personalizar o manifesto do aplicativo Teams](TeamsFx-preview-and-customize-app-manifest.md)
