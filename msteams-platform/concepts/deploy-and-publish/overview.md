---
title: Distribuir seu aplicativo
description: Descreve as três opções para distribuir o aplicativo
keywords: Team Publish Store Office distribute AppSource Sideload upload app
ms.openlocfilehash: d3fd81e69f74b6332d9033412a7b6688239cd801
ms.sourcegitcommit: 02ab2cb7820dc8665bb4ec6a1a40c3b8b8f29d66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47340953"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir o aplicativo Microsoft Teams

Depois de criar seu aplicativo, há três opções para distribuí-lo:

1. [Carregar seu aplicativo diretamente](#upload-your-app-directly).
2. [Publique seu aplicativo no catálogo de aplicativos da sua organização](#publish-to-your-organizations-app-catalog).
3. [Publique seu aplicativo por meio do AppSource](#publish-to-appsource).

## <a name="enterprise-organizations"></a>Organizações corporativas

### <a name="upload-your-app-directly"></a>Carregar seu aplicativo diretamente

Essa é a maneira mais fácil de testar e usar o aplicativo. Se você for o proprietário da equipe e/ou o [carregamento de aplicativos personalizados estiver habilitado](/microsoftteams/admin-settings), você poderá [carregar diretamente (ou Sideload)](./apps-upload.md) o aplicativo e começar a usá-lo imediatamente. No entanto, se você quiser compartilhar o aplicativo com outras pessoas, será necessário enviá-los para o seu pacote de aplicativos e pedir que eles o carreguem de forma independente.

Se você quiser distribuir o aplicativo de forma mais ampla, o Microsoft Teams fornece uma galeria de aplicativos para que os usuários encontrem ou descubram aplicativos de alta qualidade. Para que sua solução seja disponibilizada na Galeria, você deve [publicar no catálogo de aplicativos da sua organização](#publish-to-your-organizations-app-catalog) ou [publicar no AppSource](./appsource/publish.md).

### <a name="publish-to-your-organizations-app-catalog"></a>Publicar no catálogo de aplicativos da sua organização

O catálogo de aplicativos da sua organização contém aplicativos exclusivos da sua organização e está totalmente sob o controle da sua organização. Você pode encontrar mais informações no artigo [*publicar aplicativos no catálogo de aplicativos da sua organização*](/microsoftteams/tenant-apps-catalog-teams). Este recurso só pode ser gerenciado por usuários do teams com privilégios de administrador de locatário do Microsoft Office 365.

### <a name="publish-to-appsource"></a>Publicar no AppSource

O AppSource (anteriormente conhecido como Office Store) fornece um local conveniente para que você distribua seu aplicativo do Microsoft Teams, bem como outros tipos de extensibilidade do Office 365, como suplementos do Office e suplementos do SharePoint. Siga nossas diretrizes para [enviar seu aplicativo para o AppSource](./appsource/publish.md).

## <a name="government-community-cloud-gcc-organizations"></a>Organizações da nuvem da Comunidade governamental (GCC)

### <a name="upload-your-custom-app-directly-to-teams"></a>Carregar seu aplicativo personalizado diretamente para o Microsoft Teams

 Como um administrador de locatários GCC, você decide se deseja carregar um aplicativo personalizado no seu ambiente de locatários e se ele deve ser publicado no catálogo de aplicativos do locatário. A Microsoft não possui ou controla seus aplicativos personalizados, portanto, você deve garantir que todos os pontos de extremidade estejam em conformidade com os requisitos da sua organização. Além disso, se a solução do aplicativo incluir um bot ou extensão de mensagem, você precisará concluir o registro da [estrutura do bot](https://dev.botframework.com/) da seguinte maneira:

1. Na página **conectar a canais** , em **Adicionar um canal de destaque**, selecione **equipes**.
1. Navegue até a página **Configurar MSTeams** (*Veja* abaixo).
1. Em **mensagens** , selecione o botão de opção do **Microsoft Teams para clientes do governo** .
1. No canto inferior esquerdo da página, selecione **salvar**.  

>[!IMPORTANT]
> Você não pode usar a configuração comercial do teams para carregar/Sideload seu aplicativo personalizado para um ambiente GCC, você deve selecionar o botão de opção **Microsoft Teams para clientes do governo** para obter uma configuração compatível com gcc.

![Página de configuração de mensagens do teams](../../assets/images/gcc-configure.png)

> [!NOTE]
>
> * As instruções de upload para ambientes GCC, apresentadas acima, aplicam-se a aplicativos personalizados do teams. </br>
> * Os aplicativos da Microsoft em conformidade estão habilitados no ambiente GCC, por padrão, no Teams.
> * Os aplicativos de terceiros estão desabilitados no nível do locatário e devem ser gerenciados por meio [das políticas de permissão de aplicativo](/microsoftteams/teams-app-permission-policies)da sua organização. Certifique-se de examinar todos os aplicativos de terceiros para garantir que eles fiquem alinhados às políticas e aos procedimentos da sua organização.

> [!TIP]
>
> Os parceiros de desenvolvedor do Microsoft 365 oferecem segurança, manipulação de dados e detalhes de conformidade para seus aplicativos de terceiros do teams por meio do [programa de certificação de aplicativos do Microsoft 365](/microsoft-365-app-certification/overview). *Consulte também* [certificação de aplicativos do Microsoft Teams](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/application-certification).
</br></br>
