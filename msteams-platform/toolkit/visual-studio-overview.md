---
title: Criar aplicativos com o Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o Microsoft Teams Toolkit
keywords: kit de ferramentas do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: johmil
ms.openlocfilehash: 6a0f466ba0d95312695be8b5460fc949e3f70811
ms.sourcegitcommit: 4ac93d69927791a8ccf678ca5ee83e63b51566b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2021
ms.locfileid: "53095511"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Criar aplicativos com o Teams Toolkit e Visual Studio

O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio. O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="prerequisites"></a>Pré-requisitos

1. [Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).

2. Certifique-se de que o **<span>ASP.NET</span> e** o módulo de desenvolvimento da Web foram adicionados à sua Visual Studio instância. Para obter mais informações, consulte [Modify Visual Studio by adding or remove workloads and components](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true).

![Módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

## <a name="install-the-teams-toolkit"></a>Instalar o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [marketplace do Visual Studio ou](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) diretamente no menu **Extensões** no Visual Studio.

## <a name="use-the-toolkit"></a>Usar o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Execute seu aplicativo em Teams](#install-and-run-your-app-locally)
- [Valide o seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo Teams projeto

1. Iniciar Visual Studio 2019.
2. Selecione **Criar um novo projeto**.
3. Pesquise **Microsoft Teams App e** selecione **Próximo**.
4. Na **configuração do novo projeto,** insira **o** nome Project, **Local** e Nome **da solução.**
5. Selecione **Próximo** para inserir um nome para o aplicativo.
6. Na tela Informações Adicionais, insira um **Nome do Aplicativo** e Nome do Desenvolvedor **ou** Empresa para seu Teams app.

## <a name="configure-your-app"></a>Configurar seu aplicativo

No seu núcleo, o Teams aplicativo abrange três componentes:

- O Microsoft Teams cliente (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.
- Um servidor que responde a solicitações de conteúdo exibido em Teams. Por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.
- Um Teams de aplicativo consiste em três arquivos:

    > [!div class="checklist"]
    >
    > - O manifest.json
    > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.
    > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.

Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

> [!NOTE]
>Se você ainda não fez isso, você deve entrar na sua conta Microsoft 365 para continuar com o processo de desenvolvimento.
>
> Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura Microsoft 365 programa de [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é gratuito por 90 dias e é renovado desde que você o use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura de desenvolvedor Microsoft 365 gratuita [,](https://aka.ms/MyVisualStudioBenefits)ativa para o tempo de vida da sua assinatura Visual Studio. Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](/office/developer-program/office-365-developer-program-get-started)

### <a name="configuration-steps"></a>Etapas de configuração

1. Para configurar seu aplicativo, selecione o menu **Project > TeamsFx > Configurar para SSO...**

Quando solicitado, entre em sua conta da Microsoft que tenha um locatário do M365.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

Pressione F5 para iniciar a depuração. A caixa de diálogo de instalação do aplicativo é exibida no Teams cliente.

## <a name="validate-your-app"></a>Valide o seu aplicativo

O **Project > do TeamsFx Validar** > Teams manifesto permite verificar se o pacote do aplicativo é válido.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

No [portal](https://dev.teams.microsoft.com/home)do desenvolvedor do Teams , você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte do Aplicativo para todos os Teams usuários.

- Seu administrador de TI revisará esses envios.
- Você pode retornar à página **Publicar** para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Isso também é onde você pode enviar atualizações para seu aplicativo ou cancelar quaisquer envios ativos no momento.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar e executar seu primeiro aplicativo Microsoft Teams com o Blazor](../get-started/first-app-blazor.md)
