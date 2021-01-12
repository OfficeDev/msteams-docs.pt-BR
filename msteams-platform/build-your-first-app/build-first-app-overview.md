---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: heath-hamilton
description: Saiba como começar a usar o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 06e26c57e6f6d3fd0bbeb981ef7ab46c8217bb4a
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795458"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a>Criar sua primeira visão geral do aplicativo Microsoft Teams

Na criação das **lições do seu primeiro aplicativo,** você cria aplicativos básicos do Teams. Cada tutorial explica como criar um aplicativo teams simples e real ao mesmo tempo em que apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.

## <a name="what-youll-learn"></a>O que você aprenderá

Aqui está uma ideia do que você vai saber depois de passar pelas lições.

> [!div class="checklist"]
  >
  > * **Começar rapidamente com** o Kit de Ferramentas do Teams: o Kit de Ferramentas do Microsoft Teams para Visual Studio Code cuida da criação do projeto do aplicativo e do scaffolding para que você possa ter um aplicativo em execução em minutos.
  > * **Configure seu aplicativo com o App Studio:** especifique os recursos e serviços que seu aplicativo do Teams usa.
  > * **Escopo do público do seu aplicativo:** crie um aplicativo do Teams para uso pessoal, colaboração ou ambos.
> * **Obter experiência com ferramentas e SDKs do Teams:** personalize seu aplicativo com a ajuda do SDK do cliente JavaScript do Teams. Por exemplo, altere o esquema de cores do seu aplicativo para corresponder ao tema do Teams. Além disso, saiba mais sobre as ferramentas comuns para criar e gerenciar bots.
  > * **Expanda seu aplicativo:** ao longo das lições, você encontrará tópicos relacionados em que provavelmente está interessado (como diretrizes de autenticação e design).

## <a name="teams-app-fundamentals"></a>Conceitos básicos do aplicativo Teams

Antes de começar os tutoriais, você deve saber o seguinte sobre como criar aplicativos para o Teams.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Os aplicativos podem ter vários recursos e pontos de entrada

Um aplicativo teams é feito de um ou mais recursos de plataforma [(como](../concepts/capabilities-overview.md) as pessoas usam o aplicativo) e pontos de entrada [(onde](../concepts/extensibility-points.md) as pessoas descubram o aplicativo).

### <a name="teams-doesnt-host-your-app"></a>O Teams não hospeda seu aplicativo

Um aplicativo do Teams inclui as seguintes partes importantes:

* A lógica, o armazenamento de dados e as chamadas à API que ligarão seu aplicativo. Esses serviços não são hospedados pelo Teams e devem estar acessíveis via HTTPS.
* O cliente do Teams (web, desktop ou dispositivos móveis) onde as pessoas usam seu aplicativo.
* Sua ID de aplicativo, que permite configurar seu aplicativo com o App Studio.

## <a name="get-prerequisites"></a>Obter pré-requisitos

Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.

### <a name="set-up-your-development-account"></a>Configurar sua conta de desenvolvimento

Você precisa de uma conta do Teams que permita o sideload de aplicativo personalizado. (Sua conta pode já fornecer isso.)

1. Se você tiver uma conta do Teams, verifique se pode fazer o sideload de aplicativos no Teams:
    1. No cliente do Teams, selecione **Aplicativos.**
    1. Procure uma opção para **carregar um aplicativo personalizado.**

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Imagem mostrando onde no Teams você pode carregar um aplicativo personalizado.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Selecione aqui</b> se não conseguir ver a opção de sideload ou se não tiver uma conta do Teams.</summary>

Você pode obter uma conta de teste gratuita do Teams que permite o sideload do aplicativo in joining the Microsoft 365 developer program. (O processo de registro leva aproximadamente dois minutos.)

1. Vá para o [programa de desenvolvedor do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)
1. Selecione **Ingressar Agora** e siga as instruções na tela.
1. Quando chegar à tela de boas-vindas, selecione **Configurar assinatura do E5.**
1. Configurar sua conta de administrador. Depois de concluir, você deverá ver uma tela como esta.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa para desenvolvedores do Microsoft 365.":::
1. Entre no Teams usando a conta de administrador que você acabou de configurar.
1. Verifique se agora você tem **a opção Carregar um aplicativo** personalizado.

</details>

> [!Note]
> Se você ainda não conseguir fazer o sideload de aplicativos, confira habilitar aplicativos personalizados do Teams e [ativar o carregamento de aplicativos personalizados.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

### <a name="install-your-development-tools"></a>Instalar suas ferramentas de desenvolvimento

Você pode criar aplicativos do Teams com suas ferramentas preferidas, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para Visual Studio Code.

O Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS. Para depurar certos tipos de aplicativos localmente, como um bot, você aprenderá a usar [o ngrok](../concepts/build-and-test/debug.md#locally-hosted) para configurar um túnel seguro entre o Teams e seu aplicativo. (Os aplicativos do Teams de produção são hospedados na nuvem.)

1. Instale o [Node.js](https://nodejs.org/en/).
1. Instale [o ngrok](https://ngrok.com/download) se você planeja criar um bot ou extensão de mensagens.
1. Instale a versão mais recente do [Visual Studio Code.](https://code.visualstudio.com/download) (As versões anteriores podem não funcionar com o kit de ferramentas.)
1. No Visual Studio Code, selecione **Extensões na** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Barra de Atividades à esquerda e instale o Kit de Ferramentas do Microsoft **Teams.**

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Imagem mostrando onde no Visual Studio Code você pode instalar a extensão do Kit de Ferramentas do Microsoft Teams.":::

## <a name="about-the-tutorials"></a>Sobre os tutoriais

Você pode começar com qualquer um dos Teams para **criar suas primeiras lições de** aplicativo. Se você não tiver certeza de onde ir primeiro, siga nosso caminho amigável para iniciantes e crie um "Hello, World!" app.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de habilidades mostrando caminhos de aprendizagem para os tutoriais de &quot;criar seu primeiro aplicativo&quot; do Teams." border="false":::

## <a name="next-step"></a>Próxima etapa

Depois de configurar sua conta e seu ambiente, você pode começar a criar.

### <a name="beginner-friendly-tutorial"></a>Tutorial amigável para iniciantes

> [!div class="nextstepaction"]
> [Criar um aplicativo "Hello, World!"](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a>Outros tutoriais

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)
