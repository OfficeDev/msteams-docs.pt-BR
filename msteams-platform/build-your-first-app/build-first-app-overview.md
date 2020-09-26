---
title: Introdução à criação do primeiro aplicativo do teams
author: heath-hamilton
description: Visão geral e pré-requisitos para a criação do primeiro aplicativo do Microsoft Teams
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: quickstart
ms.openlocfilehash: 7431230487f1644de8b17b0b9e143819395b7527
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279706"
---
# <a name="build-your-first-teams-app-overview"></a>Criar sua primeira visão geral do App Teams

Nas aulas **Compilar suas primeiras aplicativos** , você cria aplicativos básicos do teams. Cada tutorial percorre como criar um aplicativo simples e de equipe real ao apresentar as ferramentas comuns, conceitos fundamentais e recursos mais avançados.

## <a name="what-youll-learn"></a>O que você aprenderá

Aqui está uma ideia do que você saberá depois de percorrer as lições.

> [!div class="checklist"]
  >
  > * **Comece a trabalhar rapidamente com o Teams Toolkit**: o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding, para que você possa ter um aplicativo em execução em minutos.
  > * **Defina seu aplicativo com o manifesto**: o manifesto do aplicativo é onde você especifica os recursos e serviços que seu aplicativo da equipe usa.
  > * **Escopo do seu aplicativo público**: Crie um aplicativo do teams para uso pessoal, colaboração ou ambos.
  > * **Obtenha experiência com estruturas do teams**: Personalize seu aplicativo (por exemplo, altere seu esquema de cores para corresponder ao tema do Teams) com a ajuda do SDK do JavaScript do teams. Além disso, saiba mais sobre as ferramentas comuns para criar e gerenciar bots.
  > * **Expanda em seu aplicativo**: em todas as lições, você encontrará tópicos relacionados que provavelmente você está interessado (como diretrizes de autenticação e Design).

## <a name="teams-app-fundamentals"></a>Conceitos básicos do aplicativo Teams

Antes de começar os tutoriais, você deve saber o seguinte sobre a criação de aplicativos para o Microsoft Teams.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Os aplicativos podem ter vários recursos e pontos de entrada

Os aplicativos do teams são compostos por um ou mais [recursos de plataforma](../concepts/capabilities-overview.md) e [pontos de entrada](../concepts/extensibility-points.md). Você pode apresentar seu aplicativo usando vários [componentes e convenções de interface do usuário](../concepts/extensibility-points.md#ui-components)específicos para equipes, como módulos de cartões e tarefas.

### <a name="teams-doesnt-host-your-app"></a>O Microsoft Teams não hospeda seu aplicativo

Um aplicativo do teams inclui três partes importantes:

* A lógica, o armazenamento de dados e as chamadas de API que alimentam o aplicativo. Esses serviços não são hospedados pelo Microsoft Teams e devem ser acessíveis via HTTPS.
* O cliente do Microsoft Teams (Web, desktop ou celular) onde as pessoas usam o aplicativo.
* Seu pacote de aplicativos, que você usa para instalar o aplicativo no Teams. Ele contém metadados do aplicativo e ponteiros para seus serviços hospedados.

## <a name="get-prerequisites"></a>Obter pré-requisitos

Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.

### <a name="set-up-your-development-account"></a>Configurar sua conta de desenvolvimento

Você precisa de uma conta do Microsoft Teams que permite o Sideload de aplicativos personalizado. (Sua conta já pode fornecer isso).

1. Se você tiver uma conta do Microsoft Teams, verifique se você pode Sideload aplicativos no Microsoft Teams:
    1. No cliente do Microsoft Teams, selecione **aplicativos**.
    1. Procure uma opção para **carregar um aplicativo personalizado**.

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde você pode carregar um aplicativo personalizado no Microsoft Teams.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Selecione aqui</b> se você não conseguir ver a opção Sideload ou se não tiver uma conta do teams.</summary>

Você pode obter uma conta de teste gratuita do teams que permite que o aplicativo Sideload ingresse no programa de desenvolvedor do 365 da Microsoft. (O processo de registro leva aproximadamente dois minutos.)

1. Vá para o [programa Microsoft 365 Developer](https://developer.microsoft.com/microsoft-365/dev-program).
1. Selecione **ingressar agora** e siga as instruções na tela.
1. Quando você chegar à tela de boas-vindas, selecione **Configurar a assinatura E5**.
1. Configurar sua conta de administrador. Após concluir, você verá uma tela como esta.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê após se inscrever no programa de desenvolvedor do Microsoft 365.":::
1. Faça logon no Microsoft Teams usando a conta de administrador que você acabou de configurar.
1. Verifique se agora você tem a opção **carregar um aplicativo personalizado** .

</details>

### <a name="install-your-development-tools"></a>Instalar suas ferramentas de desenvolvimento

Você pode criar aplicativos do teams com suas ferramentas preferenciais, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para o Visual Studio Code.

O Microsoft Teams exibe o conteúdo do aplicativo apenas por meio de conexões HTTPS. Como você hospedará seu primeiro aplicativo localmente para poupar tempo, aprenderá a usar o [ngrok para configurar um túnel seguro](../concepts/build-and-test/debug.md#locally-hosted) entre o Teams e seu aplicativo. (Os aplicativos de equipe de nível de produção são hospedados na nuvem.)

1. Instale o [Node.js](https://nodejs.org/en/).
1. Instale o [ngrok](https://ngrok.com/download).
1. Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download). (As versões anteriores podem não funcionar com o kit de ferramentas.)
1. No Visual Studio Code, selecione **extensões** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: na barra de atividades à esquerda e instale o **Microsoft Teams Toolkit**.
    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração que mostra onde no Visual Studio Code você pode instalar a extensão do kit de ferramentas do Microsoft Teams.":::

## <a name="about-the-tutorials"></a>Sobre os tutoriais

Você pode começar com qualquer um dos Teams **Construa suas primeiras lições de aplicativos** . Se você não tem certeza de onde começar, siga nosso caminho amigável de iniciantes e crie um "Olá, mundo!" aplicativo.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de qualificações que mostra os planos de aprendizado dos tutoriais de criação dos seus primeiros aplicativos do teams." border="false":::

## <a name="next-step"></a>Próxima etapa

Depois de configurar sua conta e ambiente, você pode começar a criar.

### <a name="beginner-friendly-tutorial"></a>Tutorial amigável de iniciantes

> [!div class="nextstepaction"]
> [Criar um aplicativo "Olá, mundo!"](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a>Outros tutoriais

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)