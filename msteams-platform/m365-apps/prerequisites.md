---
title: Configurar seu ambiente de dev para estender Teams aplicativos em Microsoft 365
description: Aqui estão os pré-requisitos para estender seus aplicativos Teams aplicativos Microsoft 365
ms.date: 11/15/2021
ms.topic: how-to
ms.custom: m365apps
ms.openlocfilehash: 967e45bb59c431476ead902e1413ab743c566779
ms.sourcegitcommit: 239807b74aa222452559509d49c4f2808cd9c9ca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61391343"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-m365-preview"></a>Configurar seu ambiente de dev para estender Teams aplicativos em todo o M365 (visualização)

O ambiente de desenvolvimento para estender Teams aplicativos em Microsoft 365 é semelhante ao que você usa para Microsoft Teams desenvolvimento. Este artigo discute configurações específicas necessárias para executar builds de visualização de aplicativos Microsoft Teams e Microsoft Office para visualizar Teams aplicativos em execução no Outlook e Office. Para configurar seu ambiente de desenvolvimento, você precisará:

> [!div class="checklist"]
> * [Obter um Locatário do Desenvolvedor M365 (Área Desastiçada) e habilitar o sideload](#prepare-a-developer-tenant-for-testing)
> * [Registrar seu locatário do M365 *em Office 365 Versões Direcionadas*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Configure sua conta para acessar versões de visualização de Outlook e Office](#install-office-apps-in-your-test-environment)
> * [Alternar para a versão de visualização do desenvolvedor Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Opcional*] [Instalar Teams Toolkit extensão para Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Preparar um locatário de desenvolvedor para teste

Se você ainda não tiver um, crie um locatário de área de Microsoft 365 assinatura do desenvolvedor ou obtenha um locatário de teste por meio de sua organização. [](/office/developer-program/microsoft-365-developer-program-get-started)

Depois de ter um locatário, você precisará habilitar o [](https://admin.microsoft.com) [sideload](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading) para seu locatário Centro de administração do Microsoft 365 entrar no Centro de administração do Microsoft 365 e navegar para Mostrar Todos os aplicativos > Teams > Teams > políticas de Instalação > **Global**.  Alternar em Upload **aplicativos personalizados** e **Salvar**.

Se você tiver um locatário existente, verifique se o sideload está habilitado ao entrar Teams e selecionar **Aplicativos**. Você verá a opção **Upload aplicativo personalizado** se o sideload estiver habilitado para seu locatário.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="O sideload está habilitado para seu locatário se você vir a opção de &quot;Upload um aplicativo personalizado&quot; no painel Teams &quot;Aplicativos&quot;":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrar seu locatário de desenvolvedor para Office 365 versões direcionadas

> [!IMPORTANT]
> Consulte o mais recente no [Microsoft Teams - Microsoft 365 Blog](https://devblogs.microsoft.com/microsoft365dev/category/teams/) do Desenvolvedor para verificar se o outlook.com e o office.com para aplicativos Teams estão disponíveis para seu locatário de teste.

Para visualizar Teams aplicativos em execução outlook.com ou office.com, opte pelo locatário de teste para Office 365 [versões direcionadas.](/microsoft-365/admin/manage/release-options-in-office-365#targeted-release)

1. Entre no Centro de administração do Microsoft 365 usando credenciais para seu locatário de [](https://admin.microsoft.com/AdminPortal/Home?#/Settings/OrganizationProfile) teste e navegue até *a* guia Perfil organizacional ( Configurações Perfil da organização de  >  *configurações* da  >>  organização )). Selecione **Preferências de versão** e selecione uma das preferências de *versão* direcionada:

  :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Centro de administração do Microsoft 365 menu 'Preferências de versão' com opção de versão direcionada selecionada":::

  Para obter mais informações sobre Office 365 de versão, consulte [Configurar as](/microsoft-365/admin/manage/release-options-in-office-365) opções de versão Standard ou Targeted Centro de administração do Microsoft 365 *ajuda*.

1. Verifique se o locatário tem suporte para Teams guias pessoais em execução no office.com e outlook.com fazendo login com suas credenciais de locatário de teste. Se você vir uma opção de releitos (**...**) na barra lateral (o ponto de entrada para guias pessoais Teams sideload), seu locatário terá suporte.

  :::image type="content" source="images/outlook-web-ellipses.png" alt-text="Reellipses '...' ponto de entrada para aplicativos de tabulação Teams sideload no outlook.com":::

1. Verifique o suporte de locatário de teste para extensões de mensagens em outlook.com verificando se há a opção Mais **aplicativos** na área de Outlook de mensagem de redação.

> [!NOTE]
> Se você tiver optado por versões direcionadas, mas não vir essas opções, é provável que o suporte a recursos de visualização ainda esteja em processo de implantação para seu locatário. Para saber mais sobre as atualizações mais recentes, [consulte Microsoft Teams Blog do Desenvolvedor.](https://devblogs.microsoft.com/microsoft365dev/category/teams/)

## <a name="install-office-apps-in-your-test-environment"></a>Instalar Office aplicativos em seu ambiente de teste

> [!IMPORTANT]
> Consulte o Microsoft Teams mais recente [- Microsoft 365 Blog](https://devblogs.microsoft.com/microsoft365dev/category/teams/) do Desenvolvedor para verificar se o Outlook para suporte Windows área de trabalho para extensões de mensagens Teams está disponível para seu locatário de teste.

Você pode visualizar Teams aplicativos em execução Outlook em Windows desktop usando uma com build do *Canal Beta* recente. Para instalar uma Outlook do Canal Beta em seu ambiente de teste, você provavelmente precisará alterar o canal Microsoft 365 Apps [de](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) atualização do seu locatário de teste.

Aqui estão as etapas para instalar Office 365 *aplicativos do Canal Beta* em seu ambiente de teste:

1. Faça logoff em seu ambiente de teste usando sua conta de locatário de teste.
1. Baixe a [Office de Implantação e](https://www.microsoft.com/download/details.aspx?id=49117) extraia para uma pasta local.
1. Abra *configuration-Office365-x86.xml* (ou o **x64.xml*, dependendo do seu ambiente) em um editor de texto e atualize o valor *do Canal* para `BetaChannel` .
1. Em um Prompt de Comando elevado, execute `setup.exe /configure configuration-Office365-x86.xml` (ou use o arquivo **x64.xml,* dependendo da configuração).
1. Abra Outlook (cliente da área de trabalho) e configurar a conta de email usando suas credenciais de locatário de teste.
1. Em Outlook, abra **File** Office Account About Outlook , e confirme se você está no Canal Beta e se o número de com build é  >    >   **14416** ou superior. 
1. Alterne no botão **Em Breve** no canto da janela Outlook cliente:

   :::image type="content" source="images/outlook-coming-soon.png" alt-text="Botão 'Em breve' no Outlook da área de trabalho alternado para 'On'}":::

  > [!NOTE]
  > Talvez seja necessário fechar o Outlook e reiniciar o computador para que o *botão Em* Breve apareça.

Você pode verificar se o locatário dá suporte Teams guias pessoais em execução no Outlook para uma área de trabalho Windows fazendo login com suas credenciais de locatário de teste e procurando uma opção de releitos (**...**) na barra lateral (o ponto de entrada para guias pessoais Teams sideload).

:::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="Reellipses '...' ponto de entrada para aplicativos de tabulação Teams sideloaded no Outlook para área de trabalho":::

Da mesma forma, você pode verificar o suporte de locatário de teste para  extensões de mensagens no Outlook para Windows desktop verificando a opção Mais aplicativos na faixa de opções de redação Outlook mensagem.

> [!NOTE]
> Se você tiver optado por versões do Canal Beta, mas não vir essas opções de releituras, é provável que o suporte a recursos de visualização ainda esteja em processo de implantação para seu locatário. Para saber mais sobre as atualizações mais recentes, [consulte Microsoft Teams Blog do Desenvolvedor.](https://devblogs.microsoft.com/microsoft365dev/category/teams/)

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Alternar para a versão de visualização do desenvolvedor Teams

Certifique-se de que você opte pela [*Visualização*](../resources/dev-preview/developer-preview-intro.md) do Desenvolvedor Público do seu Microsoft Teams cliente.

1. Entre no Teams com sua conta de locatário de área desarmativa.
1. No menu reellipse (**...**) ao lado do seu perfil de usuário, selecione **Sobre** e selecione a opção **Visualização do** desenvolvedor.
1. Depois que a caixa de diálogo for exibida, selecione **Alternar** para visualização do desenvolvedor para reiniciar Teams e verifique se a Visualização do Desenvolvedor está habilitada.

:::image type="content" source="images/teams-dev-preview.png" alt-text="No Teams menu de releições, abra a opção 'Sobre' e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Instalar Visual Studio Code e Teams Toolkit de visualização

Opcionalmente, você pode tirar proveito Visual Studio Code [ajudar](https://code.visualstudio.com/) a estender Teams aplicativos para Office e Outlook.

A extensão [Teams Toolkit](https://aka.ms/teams-toolkit) para Visual Studio Code ( ou posterior) fornece comandos que podem ajudar a modificar seu código Teams existente para ser compatível com Outlook e `v2.10.0` Office. Continue a [habilitar Teams guia pessoal para que](extend-m365-teams-personal-tab.md) Office e Outlook saiba mais.

## <a name="next-steps"></a>Próximas etapas

- [Habilitar uma guia pessoal do Teams para Office e Outlook](extend-m365-teams-personal-tab.md)
- [Habilitar uma extensão de mensagens do Teams para o Outlook](extend-m365-teams-message-extension.md)