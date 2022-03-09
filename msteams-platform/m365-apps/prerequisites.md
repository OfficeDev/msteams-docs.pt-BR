---
title: Configurar seu ambiente de dev para estender Teams aplicativos em Microsoft 365
description: Aqui estão os pré-requisitos para estender seus aplicativos Teams de Microsoft 365
ms.date: 02/11/2022
ms.openlocfilehash: eec44e149e81b420c507b0580896d2c5a4a99cc2
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355997"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Configurar seu ambiente de dev para estender Teams aplicativos em Microsoft 365

> [!NOTE]
> Estender o aplicativo teams Microsoft 365 está disponível atualmente apenas na [visualização de desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

O ambiente de desenvolvimento para estender Teams aplicativos em Microsoft 365 é semelhante ao Microsoft Teams desenvolvimento. Este artigo discute configurações específicas necessárias para executar builds de visualização de aplicativos Microsoft Teams e Microsoft Office para visualizar Teams aplicativos em execução no Outlook e Office.

Para configurar seu ambiente de desenvolvimento:

> [!div class="checklist"]
> * [Obter Microsoft 365 locatário do Desenvolvedor (Área Desarmado) e habilitar o sideload](#prepare-a-developer-tenant-for-testing)
> * [Registrar seu Microsoft 365 locatário *em Office 365 Versões Direcionadas*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Configure sua conta para acessar versões de visualização de Outlook e Office](#install-office-apps-in-your-test-environment)
> * [Alternar para a versão de visualização do desenvolvedor Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Opcional*] [Instalar Teams Toolkit extensão para Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Preparar um locatário de desenvolvedor para teste

Você precisa de um Microsoft 365 de assinatura de desenvolvedor para configurar seu ambiente de desenvolvimento. Se você ainda não tiver um, crie um locatário de [área](/office/developer-program/microsoft-365-developer-program-get-started) de trabalho ou receba um locatário de teste por meio de sua organização.

Depois de ter um locatário, você precisa habilitar o sideload para seu locatário, consulte [enable sideloading](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading). Para verificar se o sideload está habilitado, entre no Teams, selecione **Aplicativos** e verifique se Upload **uma opção de aplicativo** personalizada.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="Upload uma opção de aplicativo personalizada":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrar seu locatário de desenvolvedor para Office 365 versões direcionadas

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Microsoft Teams - blog](https://devblogs.microsoft.com/microsoft365dev/) do desenvolvedor Microsoft 365 para verificar se o suporte Outlook.com e Office.com para aplicativos Teams está disponível para seu locatário de teste.

Para registrar seu locatário de teste para Office 365 versões direcionadas:

1. Entre [no Centro de administração do Microsoft 365 com](https://admin.microsoft.com) suas credenciais de locatário de teste.
1. Vá para **Configurações** >  **Perfil Configurações** >  **Organização.**
1. Selecione **Preferências de versão**.
1. Selecione qualquer *preferência de versão direcionada* :
    1. **Lançamento de destino para todos**
    1. **Versão de destino para usuários selecionados**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Centro de administração do Microsoft 365 menu 'Preferências de versão' com opção de versão direcionada selecionada":::
    
1. Selecione **Salvar**.

Para obter mais informações sobre Office 365 de versão, consulte [Configurar as opções de versão Standard ou Targeted](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) Centro de administração do Microsoft 365 *ajuda*.

## <a name="install-office-apps-in-your-test-environment"></a>Instalar Office aplicativos em seu ambiente de teste

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Microsoft Teams -](https://devblogs.microsoft.com/microsoft365dev/) blog do desenvolvedor Microsoft 365 para verificar se o Outlook para suporte Windows área de trabalho para extensões de mensagens Teams está disponível para seu locatário de teste.

Você pode visualizar Teams aplicativos em execução Outlook em Windows desktop usando uma com build do *Canal Beta recente*. Verifique se você precisa alterar [o canal de atualização Microsoft 365 Apps](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) seu locatário de teste para instalar uma com Office 365 do Canal Beta.

Para instalar Office 365 aplicativos do Canal Beta em seu ambiente de teste:

1. Entre em seu ambiente de teste com suas credenciais de locatário de teste.
1. Baixe a [Office de Implantação e](https://www.microsoft.com/download/details.aspx?id=49117) extraia para uma pasta local.
1. Vá para a pasta *local e abra* configuration-Office365-x86.xml(ou **x64.xml*, dependendo do seu ambiente) em um editor de texto e atualize o valor *channel* para `BetaChannel`.
1. Abra o Prompt de Comando e navegue até o caminho da pasta local.
1. Execute `setup.exe /configure configuration-Office365-x86.xml` (ou use o arquivo **x64.xml* , dependendo da configuração).
1. Abra Outlook (cliente da área de trabalho) e configurar a conta de email usando suas credenciais de locatário de teste.
1. Abrir **Arquivo** >  **Office AccountAbout** >  **Outlook**.  
   Se o número de com build **for 14416** ou superior e o canal for *o Canal Beta*, você está executando Microsoft 365 com build do Canal beta.
1. No canto superior direito, a turn on the **Coming Soon** toggle.
    
    :::image type="content" source="images/outlook-coming-soon.png" alt-text="Opção de alternância 'Em breve' Outlook":::

> [!NOTE]
> Talvez seja necessário fechar Outlook e reiniciar o computador para que o *botão Em* Breve apareça.

Você pode verificar o suporte de locatário de teste para sua conta de locatário:

* Para Teams guias pessoais em execução no office.com, outlook.com e Outlook para área de trabalho Windows, entre com suas credenciais de locatário de teste e verifique se há releições (**...**) na barra lateral esquerda do Office ou Outlook.

    :::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="Opção Ellipses ('...') na barra lateral esquerda do Outlook":::

* Para extensões de mensagens no outlook.com e Outlook para Windows, verifique se há mais aplicativos na parte inferior do  painel de Outlook de mensagens de composição.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Opção 'Mais aplicativos' no painel de Outlook de mensagens de composição":::

> [!NOTE]
> Se você tiver optado por versões do Canal Beta, mas não vir essas opções de releituras, é provável que o suporte ao recurso de visualização esteja em processo de implantação para seu locatário. Para saber mais sobre as atualizações mais recentes, [consulte Microsoft Teams Blog do Desenvolvedor](https://devblogs.microsoft.com/microsoft365dev/).

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Alternar para a versão de visualização do desenvolvedor Teams

Certifique-se de alternar para [a Visualização de Desenvolvedor Público](../resources/dev-preview/developer-preview-intro.md) do seu Microsoft Teams cliente.

1. Entre no Teams com suas credenciais de locatário de área desarmão.
1. No menu reellipse (**...**) ao lado do perfil de usuário, selecione **Sobrea visualização do AboutDeveloper** > . Uma caixa de diálogo é exibida, selecione **Alternar para visualização do desenvolvedor**.
1. Depois que o Teams do aplicativo for reiniciado, vá para o menu de reellipse (**...**) ao lado do seu perfil de usuário e verifique se **a** Visualização do Desenvolvedor está selecionada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Opção de visualização de desenvolvedor público Teams":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Instalar Visual Studio Code e Teams Toolkit de visualização

Opcionalmente, você pode usar [Visual Studio Code](https://code.visualstudio.com/) para estender Teams aplicativos para Office e Outlook.

A extensão [Teams Toolkit para](https://aka.ms/teams-toolkit) Visual Studio Code (`v2.10.0` ou posterior) fornece comandos que podem ajudar a modificar seu código Teams existente para ser compatível com Outlook e Office. Para obter mais informações, consulte [enable Teams personal tab for Office and Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-steps"></a>Próximas etapas

- [Habilitar uma guia pessoal do Teams para Office e Outlook](extend-m365-teams-personal-tab.md)
- [Habilitar uma extensão de mensagens do Teams para o Outlook](extend-m365-teams-message-extension.md)
