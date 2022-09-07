---
title: Criar um novo aplicativo de Teams
author: zyxiaoyuer
description: Neste módulo, saiba como criar um novo aplicativo do Teams usando o Kit de Ferramentas do Teams
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: e64daa0c3288f97286177e814204404522a6d6b9
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616584"
---
# <a name="create-a-new-teams-project"></a>Criar um novo projeto do Teams

Você pode criar um novo projeto do Teams selecionando **Criar um novo aplicativo do Teams** no Kit de Ferramentas do Teams. Você pode criar os seguintes tipos de aplicativo no Kit de Ferramentas do Teams:

| Tipo de aplicativo | Definição |
| --- | --- |
| Aplicativo Básico do Teams | Os aplicativos básicos do Teams são aplicativos de extensão de guia, bot ou mensagem que você pode criar e personalizar com base em suas necessidades. |
| Aplicativo Teams baseado em cenário | Os aplicativos do Teams baseados em cenário são bot de notificação, bot de comando, guia habilitada para SSO ou aplicativo de guia SPFx e é adequado para um cenário específico. Por exemplo, o bot de notificação é adequado apenas para enviar notificação e não é usado para chat. |

## <a name="create-a-new-teams-app"></a>Criar um novo aplicativo de Teams

As etapas para criar um novo aplicativo teams são semelhantes para todos os tipos de aplicativo, exceto SPFx e bot de notificação. As etapas a seguir ajudam você a criar um novo aplicativo guia:

**Para criar um aplicativo**

1. Abra o Visual Studio Code.
1. Selecione o ícone do Kit de Ferramentas do :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: Teams.
1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-teams-app.png" alt-text="Barra lateral do kit de ferramentas do Teams":::

1. Selecione **Criar um novo aplicativo do Teams para** criar um aplicativo usando o Kit de Ferramentas do Teams.

   :::image type="content" source="../assets/images/teams-toolkit-v2/select-create-app.png" alt-text="Criar um aplicativo":::

1. Para este tutorial, selecione **Tab** como a capacidade de criar seu aplicativo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/select-tabapp1.png" alt-text="Selecionar Funcionalidade do Aplicativo":::

   > [!NOTE]
   > Você pode selecionar qualquer tipo de funcionalidade com base em suas necessidades.

1. Selecione **JavaScript** como linguagem de programação.

    :::image type="content" source="../assets/images/teams-toolkit-v2/select-language-tab.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação":::

1. Selecione o local para o workspace do projeto e **selecione Pasta**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/select-folder1.png" alt-text="select-folder":::

1. Para este tutorial, insira como `helloworld` o nome do aplicativo. Selecione **Enter**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/enter-name-tab.png" alt-text="Captura de tela mostrando onde inserir o nome do aplicativo":::

   > [!NOTE]
   > Você pode inserir seu próprio nome de aplicativo para outros recursos e garantir que use apenas caracteres alfanuméricos.

   O aplicativo de guia do Teams é criado em alguns segundos.

    :::image type="content" source="../assets/images/teams-toolkit-v2/tap-app-created1.png" alt-text="Captura de tela mostrando o aplicativo criado":::

### <a name="directory-structure-for-different-app-types"></a>Estrutura de diretório para diferentes tipos de aplicativo

O Kit de Ferramentas do Teams fornece todos os componentes para a criação de um aplicativo. Depois de criar o projeto, você pode exibir as pastas e os arquivos do projeto no **Explorer**.

<br>
<details>
<summary><b>Estrutura de diretório para o aplicativo básico do Teams</b></summary>

Você tem três tipos diferentes de aplicativo básico do Teams e a estrutura de diretório é semelhante a todos os tipos de aplicativos. O exemplo a seguir mostra uma estrutura básica do diretório do aplicativo de guia do Teams:

| Nome da pasta | Conteúdos |
| --- | --- |
| `.fx/configs` | Arquivos de configuração que o usuário pode personalizar para o aplicativo Teams. |
| - `.fx/configs/config.<envName>.json` | Arquivo de configuração para cada ambiente. |
| - `.fx/configs/azure.parameters.<envName>.json` | Arquivo de parâmetros para provisionamento do BICEP do Azure para cada ambiente. |
| - `.fx/configs/projectSettings.json` | Configurações globais de projeto que se aplicam a todos os ambientes. |
| `tabs` | Código para a funcionalidade tab necessária em runtime, como o aviso de privacidade, os termos de uso e as guias de configuração. |
| - `tabs/src/index.jsx` | Ponto de entrada para o aplicativo de front-end, em que o componente principal do aplicativo é renderizado com `ReactDOM.render()` |
| - `tabs/src/components/App.jsx` | Código para lidar com o roteamento de URL no aplicativo. Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams. |
| - `tabs/src/components/Tab.jsx` | Código para implementar a interface do usuário do seu aplicativo. |
| - `tabs/src/components/TabConfig.jsx` | Código para implementar a interface do usuário que configura seu aplicativo. |
| `templates/appPackage` | Arquivos de modelo de manifesto do aplicativo e os ícones do aplicativo: color.png e outline.png. |
| - `templates/appPackage/manifest.template.json` | Manifesto do aplicativo para executar o aplicativo no ambiente local ou remoto.  |
| `templates/azure` | Arquivos de modelo BICEP |

> [!NOTE]
> Se você tiver um bot ou aplicativo de extensão de mensagem, as pastas relevantes serão adicionadas à estrutura de diretório.

Para saber mais sobre a estrutura de diretórios de diferentes tipos de aplicativo básico do Teams, consulte a tabela a seguir:

| Tipo de aplicativo | Links |
| --- | --- |
| Para aplicativo guia | [Crie seu primeiro aplicativo de guia usando JavaScript](../sbs-gs-javascript.yml) |
| Para o aplicativo de bot | [Crie seu primeiro aplicativo de bot usando JavaScript](../sbs-gs-bot.yml) |
| Para o aplicativo de extensão de mensagem | [Criar seu primeiro aplicativo de extensão de mensagem usando JavaScript](../sbs-gs-msgext.yml) |

</details>
<br>
<details>
<summary><b>Estrutura de diretório para o aplicativo Teams baseado em cenário</b></summary>

Você tem quatro tipos diferentes de aplicativos do Teams baseados em cenário e a estrutura de diretórios é semelhante a todos os tipos de aplicativos. O exemplo a seguir mostra uma estrutura de diretório do aplicativo Teams do bot de notificação baseada em cenário:

A nova pasta do projeto contém o seguinte conteúdo:

| Nome da pasta | Conteúdos |
| --- | --- |
| `.fx` | Definições de nível de projeto, configuração e informações de ambiente |
| `.vscode` | Arquivos do VS Code para depuração local |
| `bot` | O código-fonte do bot |
| `templates` | Modelos para o manifesto do aplicativo Teams e os recursos correspondentes do Azure |

A implementação de notificação principal na **pasta do bot** e ela contém:

| Nome do arquivo | Conteúdos |
| --- | --- |
| `src/adaptiveCards/` | Modelos para cartão adaptável  |
| `src/internal/` | Código de inicialização gerado para a funcionalidade de notificação |
| `src/index.*s` | O ponto de entrada para manipular mensagens de bot e enviar notificações |
| `.gitignore` | Arquivo para excluir arquivos locais do projeto de bot |
| `package.json` | O arquivo de pacote npm para o projeto de bot |

> [!NOTE]
> Se você tiver um bot de comando, uma guia habilitada para SSO ou um aplicativo de guia SPFx, as pastas relevantes serão adicionadas à estrutura de diretório.

Para saber mais sobre a estrutura de diretório de diferentes tipos de aplicativos do Teams baseados em cenário, consulte a tabela a seguir:

| Tipo de aplicativo | Links |
| --- | --- |
| Para aplicativo de bot de notificação | [Enviar notificação para o Teams](../sbs-gs-notificationbot.yml) |
| Para o aplicativo de bot de comando | [Criar bot de comando](../sbs-gs-commandbot.yml) |
| Para o aplicativo de guia SPFx | [Criar um aplicativo Teams com SPFx](../sbs-gs-spfx.yml) |

</details>
<br>
<details>
<summary><b>Estrutura de diretório para aplicativo de várias funcionalidades</b></summary>

Você pode adicionar mais recursos ao aplicativo Teams existente usando a adição de recursos. Por exemplo, se você adicionar o aplicativo de bot ao aplicativo de guia existente, o Kit de Ferramentas do Teams adicionará a pasta do bot com arquivos e código relevantes.

A imagem a seguir mostra a estrutura de diretório do aplicativo guia:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tabapp-directory.png" alt-text="Estrutura do diretório do aplicativo tab":::

A imagem a seguir mostra a estrutura de diretório do aplicativo guia com o recurso de bot:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tab-app-with-bot-app.png" alt-text="Aplicativo tab com estrutura de diretório do aplicativo de bot":::

</details>

## <a name="see-also"></a>Confira também

* [Criar um aplicativo do Teams com o Blazor](../sbs-gs-blazorupdate.yml)
* [Criar um aplicativo Teams com C# ou .NET](../sbs-gs-csharp.yml)
* [Pré-requisitos para todos os tipos de ambiente e criar seu aplicativo teams](tools-prerequisites.md)
* [Preparar-se para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
