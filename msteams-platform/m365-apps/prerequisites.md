---
title: 'Configurar seu ambiente de desenvolvimento para estender os aplicativos do Teams pelo Microsoft 365:'
description: Estes são os pré-requisitos para estender seus aplicativos do Teams pelo Microsoft 365
ms.date: 02/11/2022
ms.localizationpriority: high
ms.openlocfilehash: 483ae6982dd51a16573655ed14dc93577642ba4b
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111497"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Configurar seu ambiente de desenvolvimento para estender os aplicativos do Teams pelo Microsoft 365:

> [!NOTE]
> Estender o aplicativo do Teams pelo Microsoft 365 está disponível atualmente apenas na [Pré-visualização pública do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).

O ambiente de desenvolvimento para estender aplicativos do Teams pelo Microsoft 365 é semelhante ao desenvolvimento do Microsoft Teams. Este artigo discute as configurações específicas necessárias para executar builds de visualização do Microsoft Teams e Microsoft Office aplicativos para visualizar os aplicativos do Teams em execução no Outlook e no Office.

Para configurar seu ambiente de desenvolvimento:

> [!div class="checklist"]
>
> * [Obter o Locatário de desenvolvedor do Microsoft 365 desenvolvedor (área restrita) e habilitar o sideload](#prepare-a-developer-tenant-for-testing)
> * [Registrar seu locatário Microsoft 365 em *Versões direcionadas do Office 365*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Configurar sua conta para acessar as versões de pré-visualização dos aplicativos do Outlook e do Office](#install-office-apps-in-your-test-environment)
> * [Alternar para a versão de Pré-visualização do desenvolvedor do Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Opcional*] [Instalar a extensão Kir de ferramentas do Teams para o Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Preparar um Locatário de desenvolvedor para teste

Você precisa de uma área restrita de assinatura de desenvolvedor do Microsoft 365para configurar seu ambiente de desenvolvimento. Se você ainda não tiver uma, crie um [locatário de área restrita](/office/developer-program/microsoft-365-developer-program-get-started) ou obtenha um locatário de teste por meio de sua organização.

Depois de ter um locatário, você precisa habilitar o sideload para seu locatário. Consulte [habilitar sideload](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading). Para verificar se o sideload está habilitado, entre no Teams, selecione **Aplicativos** e verifique a opção **Carregar um aplicativo personalizado**.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="Opção Carregue uma aplicativo personalizado":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrar seu locatário de desenvolvedor para versões direcionadas do Office 365

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Blog do desenvolvedor do Microsoft 365](https://devblogs.microsoft.com/microsoft365dev/) para verificar se o suporte do Outlook para área de trabalho do Windows para aplicativos pessoais do Teams está disponível para seu locatário de teste.

Para registrar seu locatário de teste para versões direcionadas do Office 365:

1. Acesse o [Centro de administração do Microsoft 365](https://admin.microsoft.com) com suas credenciais de administrador.
1. Vá para **Settings** > **Configurações da organização** > **Perfil da organização**.
1. Selecione **Preferências de versão**..
1. Selecione qualquer preferência de *Versão de destino*:
    1. **Versão de destino para todos**
    1. **Versão de destino para usuários selecionados**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Menu “Preferências de versão” do Centro de administração do Microsoft 365 menu com a opção Versão de destino selecionada":::

1. Selecione **Salvar**.

Para obter mais informações sobre as opções de versão do Office 365, consulte [Configurar as opções de versão padrão ou de destino](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) na *ajuda do centro de administração do Microsoft 365*.

## <a name="install-office-apps-in-your-test-environment"></a>Instalar aplicativos do Office em seu ambiente de teste

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Blog do desenvolvedor do Microsoft 365](https://devblogs.microsoft.com/microsoft365dev/) para verificar se o suporte do Outlook para área de trabalho do Windows para aplicativos pessoais do Teams está disponível para seu locatário de teste.

Você pode visualizar aplicativos do Teams em execução no Outlook na área de trabalho do Windows usando um *build de Canal beta* recente. Verifique se você precisa alterar o [canal de atualização do Microsoft 365 Apps](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) para o seu locatário de teste para instalar um build do Office 365 Canal beta.

Para instalar o Office 365 Canal beta aplicativos em seu ambiente de teste:

1. Entre em seu ambiente de teste com suas credenciais de locatário de teste.
1. Baixe a [Ferramenta de Implantação do Office](https://www.microsoft.com/download/details.aspx?id=49117) e extraia para uma pasta local.
1. Vá para a pasta local e abra *configuration-Office365-x86.xml* (ou **x64.xml*, dependendo do seu ambiente) em um editor de texto e atualize o valor *Channel* para `BetaChannel`.
1. Abra o Prompt de Comando e navegue até o caminho da pasta local.
1. Execute `setup.exe /configure configuration-Office365-x86.xml` (ou use o arquivo **x64.xml*, dependendo da configuração).
1. Abra o Outlook (cliente da área de trabalho) e configure a conta de email usando suas credenciais de locatário de teste.
1. Abra **Arquivo** > **Conta do Office** > **Sobre o Outlook**.  
   Se o número de build for **14416** ou superior e o canal for *Canal beta*, você está executando o buil de Canal beta do Microsoft 365.
1. No canto superior direito, ative o botão de alternância **Em breve**.

    :::image type="content" source="images/outlook-coming-soon.png" alt-text="Opção de alternância &quot;Em Breve&quot; no Outlook":::

> [!NOTE]
> Talvez seja necessário fechar o Outlook e reiniciar o computador para que o botão *Em breve* seja exibido.

Você pode verificar o suporte de locatário de teste para sua conta de locatário:

* Para as guias pessoais do Teams em execução no office.com, no outlook.com e no Outlook para Área de Trabalho do Windows, entre com suas credenciais de locatário de teste e verifique se há reticências (**...**) na barra lateral esquerda do Office ou do Outlook.

    :::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="A opção de reticências ('...') na barra lateral esquerda do Outlook":::

* Para extensões de mensagem no outlook.com Outlook para Windows, verifique opção **Mais Aplicativos** na parte inferior do painel redigir mensagem do Outlook.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Opção 'Mais aplicativos' no painel redigir mensagens do Outlook":::

> [!NOTE]
> Se você tiver optado por versões do Canal beta, mas não vir essas opções de reticências, é provável que o suporte a recursos de visualização esteja em processo de distribuição para seu locatário. Para obter as atualizações mais recentes, consulte o [Blog do Desenvolvedor do Microsoft Teams](https://devblogs.microsoft.com/microsoft365dev/).

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Alternar para a versão de Pré-visualização do desenvolvedor do Teams

Certifique-se de alternar para a [Pré-visualização pública de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) do cliente do Microsoft Teams.

1. Entre no Teams com suas credenciais de locatário da área restrita.
1. No menu de reticências (**...**) ao lado do seu perfil de usuário, selecione **Sobre** > **Pré-visualização do Desenvolvedor**. Uma caixa de diálogo é exibida, selecione **Alternar para pré-visualização do desenvolvedor**.
1. Depois que o aplicativo do Teams for reiniciado, vá para o menu de reticências (**...**) ao lado do seu perfil de usuário e verifique se **Pré-visualização de desenvolvedor** está selecionado.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Pré-visualização pública do desenvolvedor":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Instalar a Visual Studio Code e a extensão de Visualização do Kit de Ferramentas do Teams

Opcionalmente, você pode usar o [Visual Studio Code](https://code.visualstudio.com/) para estender os aplicativos do Teams para o Office e o Outlook.

A extensão [Kit de Ferramentas do Teams para Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0` ou posterior) fornece comandos que podem ajudar a modificar o código existente do Teams para serem compatíveis com o Outlook e o Office. Para obter mais informações, consulte [habilitar a guia pessoal do Teams para o Office e o Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-steps"></a>Próximas etapas

* [Habilitar uma guia pessoal do Teams para Office e Outlook](extend-m365-teams-personal-tab.md)
* [Habilitar uma extensão de mensagens do Teams para o Outlook](extend-m365-teams-message-extension.md)
