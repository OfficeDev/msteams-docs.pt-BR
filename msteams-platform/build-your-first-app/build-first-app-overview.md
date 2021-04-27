---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: heath-hamilton
description: Saiba como começar com o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: d975383022089579a04317de73595106e7920c56
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019990"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a>Criar sua primeira visão geral do aplicativo do Microsoft Teams

Nas **lições de início,** você aprende a criar aplicativos básicos do Teams. Cada tutorial mostra como criar um aplicativo do Teams simples e real enquanto apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.

## <a name="what-youll-learn"></a>O que você aprenderá

Aqui está uma ideia do que você vai saber depois de passar pelas lições.

> [!div class="checklist"]
  >
  > * **Obter e** executar rapidamente com o Teams Toolkit : o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding para que você possa ter um aplicativo em execução em minutos.
  > * **Configure seu aplicativo com o App Studio:** especifique os recursos e serviços que seu aplicativo do Teams usa.
  > * **Escopo da audiência do seu aplicativo:** crie um aplicativo do Teams para uso pessoal, colaboração ou ambos.
> * **Obter experiência com ferramentas e SDKs** do Teams : Personalizar seu aplicativo com a ajuda do SDK do cliente JavaScript do Teams. Por exemplo, altere o esquema de cores do aplicativo para corresponder ao tema do Teams. Além disso, saiba mais sobre ferramentas comuns para criar e gerenciar bots.
  > * **Expanda em seu aplicativo**: ao longo das lições, você encontrará tópicos relacionados em que provavelmente está interessado (como diretrizes de autenticação e design).

## <a name="teams-app-fundamentals"></a>Fundamentos do aplicativo teams

Antes de começar os tutoriais, você deve saber o seguinte sobre como criar aplicativos para o Teams.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Os aplicativos podem ter vários recursos e pontos de entrada

Um aplicativo do Teams é feito de um ou mais recursos de plataforma [(como](../concepts/capabilities-overview.md) as pessoas usam o aplicativo) e pontos de entrada [(onde](../concepts/extensibility-points.md) as pessoas usam o aplicativo).

### <a name="teams-doesnt-host-your-app"></a>O Teams não hospeda seu aplicativo

Um aplicativo do Teams inclui as seguintes partes importantes:

* A lógica, o armazenamento de dados e as chamadas de API que a energia do aplicativo. Esses serviços não são hospedados pelo Teams e devem estar acessíveis por meio de HTTPS.
* O cliente do Teams (web, área de trabalho ou celular) onde as pessoas usam seu aplicativo.
* Sua ID do aplicativo, que permite configurar seu aplicativo com o App Studio.

## <a name="get-prerequisites"></a>Obter pré-requisitos

Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.

### <a name="set-up-your-development-account"></a>Configurar sua conta de desenvolvimento

Você precisa de uma conta do Teams que permita o sideload de aplicativo personalizado. (Sua conta pode já fornecer isso.)

1. Se você tiver uma conta do Teams, verifique se pode fazer sideload de aplicativos no Teams:
    1. No cliente do Teams, selecione **Aplicativos**.
    1. Procure uma opção para **Carregar um aplicativo personalizado.**

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde no Teams você pode carregar um aplicativo personalizado.":::
    
    Se você não vir o botão, não terá permissão para carregar aplicativos personalizados em sua organização. Você pode obter esse recurso se inscrever para uma assinatura gratuita do desenvolvedor do Microsoft 365.

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Obter sua assinatura gratuita de desenvolvedor do Microsoft 365</b></summary>

Você pode obter uma conta de teste gratuita do Teams que permite o sideload de aplicativos ao ingressar no programa de desenvolvedor do Microsoft 365. (O processo de registro leva aproximadamente dois minutos.)

1. Vá para o programa de desenvolvedor do [Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).
1. Selecione **Ingressar agora** e siga as instruções na tela.
1. Quando você chegar à tela de boas-vindas, selecione **Configurar assinatura do E5**.
1. Configurar sua conta de administrador. Depois de concluir, você deverá ver uma tela como esta.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa de desenvolvedor do Microsoft 365.":::
1. Faça logoff no Teams usando a conta de administrador que você acabou de configurar.
1. Verifique se agora você tem **a opção Carregar um aplicativo** personalizado.

</details>

> [!Note]
> Se você ainda não puder fazer sideload de aplicativos, consulte [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

### <a name="install-your-development-tools"></a>Instalar suas ferramentas de desenvolvimento

Você pode criar aplicativos do Teams com suas ferramentas preferenciais, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para Visual Studio Code.

O Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS. Para depurar determinados tipos de aplicativos localmente, como um bot, você aprenderá a usar [o ngrok](../concepts/build-and-test/debug.md#locally-hosted) para configurar um túnel seguro entre o Teams e seu aplicativo. (Os aplicativos do Production Teams são hospedados na nuvem.)

1. Instale o [Node.js](https://nodejs.org/en/).
1. Instale [ngrok](https://ngrok.com/download) se você estiver criando um bot ou extensão de mensagens e crie um [túnel usando ngrok](https://docs.microsoft.com/microsoftteams/platform/tutorials/get-started-dotnet-app-studio#tunnel-using-ngrok).
1. Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download). (As versões anteriores podem não funcionar com o kit de ferramentas.)
1. Em Visual Studio Código, selecione **Extensões** na Barra de Atividades à esquerda e instale o :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Microsoft Teams **Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração mostrando onde, Visual Studio Código, você pode instalar a extensão Toolkit Microsoft Teams.":::

## <a name="about-the-tutorials"></a>Sobre os tutoriais

Você pode começar com qualquer uma das lições de início **do** Teams. Se você não tiver certeza de onde ir primeiro, siga nosso caminho amigável iniciante e crie um "Hello, World!" app.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de habilidades mostrando caminhos de aprendizado para as lições de &quot;começar&quot; do Teams." border="false":::

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
