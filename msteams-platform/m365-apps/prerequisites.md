---
title: 'Configurar seu ambiente de desenvolvimento para estender os aplicativos do Teams pelo Microsoft 365:'
description: Requisitos para configurar seu ambiente de desenvolvimento para estender aplicativos do Teams no Microsoft 365. Conheça as configurações necessárias para executar builds de aplicativos do Microsoft Teams e do Microsoft Office.
ms.date: 05/24/2022
ms.custom: m365apps
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 99050d8b8db4fac38e9d36c42a6c3efe7f1bf28d
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789909"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Configurar seu ambiente de desenvolvimento para estender os aplicativos do Teams pelo Microsoft 365:

O ambiente de desenvolvimento para estender aplicativos do Teams pelo Microsoft 365 é semelhante ao desenvolvimento do Microsoft Teams. Este artigo discute as configurações específicas necessárias para executar builds de visualização do Microsoft Teams e Microsoft Office aplicativos para visualizar os aplicativos do Teams em execução no Outlook e no Office.

Para configurar seu ambiente de desenvolvimento:

> [!div class="checklist"]
>
> * [Obter o Locatário de desenvolvedor do Microsoft 365 desenvolvedor (área restrita) e habilitar o sideload](#prepare-a-developer-tenant-for-testing)
> * [Registrar seu locatário Microsoft 365 em *Versões direcionadas do Office 365*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Instalar as compilações do Canal Beta dos Aplicativos do Microsoft 365 em seu ambiente de teste](#install-office-apps-in-your-test-environment)
> * [Alternar para a versão de Pré-visualização do desenvolvedor do Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Opcional*] [Instalar a extensão Kir de ferramentas do Teams para o Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Preparar um Locatário de desenvolvedor para teste

Você precisa de uma área restrita de assinatura de desenvolvedor do Microsoft 365para configurar seu ambiente de desenvolvimento. Se você ainda não tiver uma, crie um [locatário de área restrita](/office/developer-program/microsoft-365-developer-program-get-started) ou obtenha um locatário de teste por meio de sua organização.

Você também precisa habilitar o sideload para seu locatário:

 1. Entre no [centro de administração do Teams](https://admin.teams.microsoft.com/dashboard) com suas credenciais de locatário de teste.

 1. Acesse aplicativos  > **do Teams****Gerenciar aplicativos**.

 1. Na parte superior direita, selecione **Configurações de aplicativo em toda a organização**.

 1. Em Aplicativos personalizados, ative a **Interação com** alternância de aplicativo personalizado e **Salvar**.

    :::image type="content" source="images/teams-admin-enable-sideloading.png" alt-text="A captura de tela é um exemplo que permite sideload para aplicativos personalizados do Teams Administração Center":::

 1. Além das configurações de aplicativo em toda a organização, as configurações de política de aplicativo personalizadas também permitem que os usuários carreguem aplicativos personalizados no Teams. Para obter mais informações, consulte [gerenciar políticas e configurações de aplicativo personalizados](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

 1. No centro de administração do Teams, acesse **políticas de instalação** de **aplicativos** >  do Teams e selecione **Política global (padrão em toda a organização).**

 1. Ative **Carregar aplicativos personalizados** e selecione **Salvar**.

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrar seu locatário de desenvolvedor para versões direcionadas do Office 365

> [!IMPORTANT]
> Pode levar até cinco dias após a criação de um [locatário de área restrita do desenvolvedor do Microsoft 365](/office/developer-program/microsoft-365-developer-program-get-started) e a inscrição nas [versões direcionadas do Office 365](#enroll-your-developer-tenant-for-office-365-targeted-releases) para que os aplicativos de equipes sideload apareçam no Outlook e no Office.

Para registrar seu locatário de teste para versões direcionadas do Office 365:

1. Acesse o [Centro de administração do Microsoft 365](https://admin.microsoft.com) com suas credenciais de administrador.
1. Vá para **Settings** > **Configurações da organização** > **Perfil da organização**.
1. Selecione **Preferências de versão**..
1. Selecione qualquer preferência de *Versão de destino*:
    1. **Versão de destino para todos**
    1. **Versão de destino para usuários selecionados**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="A captura de tela é um exemplo que mostra o menu &quot;Preferências de lançamento&quot; Centro de administração do Microsoft 365 com a opção de versão direcionada selecionada.":::

1. Selecione **Salvar**.

Para obter mais informações sobre Office 365 opções de versão, consulte [configurar as opções de versão Standard ou Targeted](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) em *Centro de administração do Microsoft 365 ajuda*.

## <a name="install-office-apps-in-your-test-environment"></a>Instalar aplicativos do Office em seu ambiente de teste

### <a name="desktop"></a>Desktop

Você pode visualizar aplicativos do Teams em execução no Outlook na área de trabalho do Windows usando um *build de Canal beta* recente. Verifique se você precisa [alterar o canal de atualização Microsoft 365 Apps](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) para que seu locatário de teste instale um Office 365 build do Canal Beta.

Para instalar o Office 365 Canal beta aplicativos em seu ambiente de teste:

1. Entre em seu ambiente de teste com suas credenciais de locatário de teste.
1. Baixe a [Ferramenta de Implantação do Office](https://www.microsoft.com/download/details.aspx?id=49117) e extraia para uma pasta local.
1. Vá para a pasta local e abra *configuration-Office365-x86.xml* (ou **x64.xml*, dependendo do seu ambiente) em um editor de texto e atualize o valor *Channel* para `BetaChannel`.
1. Abra o Prompt de Comando e vá para o caminho da pasta local.
1. Execute `setup.exe /configure configuration-Office365-x86.xml` (ou use o arquivo **x64.xml*, dependendo da configuração).
1. Abra o Outlook (cliente da área de trabalho) e configure a conta de email usando suas credenciais de locatário de teste.
1. Abra **Arquivo** > **Conta do Office** > **Sobre o Outlook** para confirmar que você está executando uma compilação do Outlook de *Canal Beta* do Microsoft 365.

    :::image type="content" source="images/outlook-about-beta-channel.png" alt-text="A captura de tela é um exemplo que mostra sobre o Outlook para verificar se você está executando um build do Canal Beta.":::

1. Verifique se o *Microsoft Edge WebView2 Runtime* está instalado. Abra no Windows o **Iniciar** > **Aplicativos e recursos** e pesquise o **modo de exibição da Web**:

    :::image type="content" source="images/windows-addremove-webview2.png" alt-text="A captura de tela é um exemplo que mostra o campo de pesquisa em suas configurações do Windows.":::

    Se não estiver listado, instale o [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) em seu ambiente de teste.

### <a name="mobile"></a>Dispositivo móvel

Você pode visualizar as guias pessoais do Teams em execução no aplicativo do Office para Android ingressando no programa beta.

Para instalar a versão beta mais recente do aplicativo do Office, crie para seu dispositivo Android físico ou emulador android:

1. Verifique se você usa um [dispositivo Android compatível com](https://support.google.com/googleplay/answer/1727131) o Google Play.
1. Inicie a **Play Store** em seu dispositivo Android.
1. Pesquise o office e selecione **Microsoft Office: Editar & Compartilhar**.
1. Selecione o botão **Instalar** .

    :::image type="content" source="images/office-android-install.png" alt-text="A captura de tela é um exemplo que mostra o botão de instalação do Microsoft Office: Editar & aplicativo Compartilhar na Google Play Store.":::

1. Selecione **Ingressar** **na seção Ingressar na versão beta** após a conclusão da instalação.

    :::image type="content" source="images/office-android-join-beta.png" alt-text="A captura de tela é um exemplo que mostra a tela Ingressar na tela beta.":::

1. Inicie o aplicativo do Office e entre com suas credenciais de locatário de teste.
1. Abra o perfil **(eu) > Configurações** e role até a parte inferior do menu.
2. Verifique se você usa o aplicativo do Office versão 16.0.15726.20000 ou superior para Android.

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Alternar para a versão de Pré-visualização do desenvolvedor do Teams

Certifique-se de alternar para a [Pré-visualização pública de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) do cliente do Microsoft Teams.

1. Entre no Teams com suas credenciais de locatário da área restrita.
1. No menu de reticências (**...**) ao lado do seu perfil de usuário, selecione **Sobre** > **Pré-visualização do Desenvolvedor**. Uma caixa de diálogo é exibida, selecione **Alternar para pré-visualização do desenvolvedor**.
1. Depois que o aplicativo do Teams for reiniciado, vá para o menu de reticências (**...**) ao lado do seu perfil de usuário e verifique se **Pré-visualização de desenvolvedor** está selecionado.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="A captura de tela é um exemplo que mostra a opção de visualização do desenvolvedor público no Teams.":::

## <a name="install-visual-studio-code-and-teams-toolkit-extension"></a>Instalar a Visual Studio Code e a extensão do Kit de Ferramentas do Teams

Opcionalmente, você pode usar o [Visual Studio Code](https://code.visualstudio.com/) para estender os aplicativos do Teams para o Office e o Outlook.

The extension [Teams Toolkit for Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0` or later) provides commands that can help modify your existing Teams code to be compatible with Outlook and Office. For more information, see [enable Teams personal tab for Office and Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-step"></a>Próxima etapa

Criar ou atualizar um aplicativo do Teams para ser executado no Microsoft 365:

> [!div class="nextstepaction"]
> [Habilitar uma guia pessoal do Teams para Office e Outlook](extend-m365-teams-personal-tab.md)
> [!div class="nextstepaction"]
> [Habilitar uma extensão de mensagens do Teams para o Outlook](extend-m365-teams-message-extension.md)
