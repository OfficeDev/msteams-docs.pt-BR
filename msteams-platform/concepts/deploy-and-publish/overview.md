---
title: Distribuir seu aplicativo
description: Descreve as três opções para distribuir seu aplicativo.
ms.topic: conceptual
keywords: teams publish store office distribute AppSource sideload upload app
ms.openlocfilehash: 9c457608711bc491aeb9062a8ac2de58e78a90bd
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014184"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir seu aplicativo Microsoft Teams

Depois de criar seu aplicativo, há três opções para distribuí-lo:

1. [Carregue seu aplicativo diretamente.](#upload-your-app-directly)
2. [Publique seu aplicativo no catálogo de aplicativos da sua organização.](#publish-to-your-organizations-app-catalog)
3. [Publique seu aplicativo por meio do AppSource.](#publish-to-appsource)

## <a name="enterprise-organizations"></a>Organizações empresariais

### <a name="upload-your-app-directly"></a>Carregar seu aplicativo diretamente

Essa é a maneira mais fácil de testar e usar seu aplicativo. Se você for o proprietário da equipe e/ou carregar aplicativos personalizados estiver [habilitado,](/microsoftteams/admin-settings)poderá carregar [diretamente (ou fazer sideload)](./apps-upload.md) do aplicativo e começar a usá-lo imediatamente. No entanto, se quiser compartilhar o aplicativo com outras pessoas, você terá que enviar o pacote do aplicativo para elas e solicitar que elas o carreguem de forma independente.

Se você quiser distribuir seu aplicativo mais amplamente, o Teams fornece uma galeria no aplicativo para que os usuários encontrem ou descubram aplicativos do Teams de alta qualidade. Para ter sua solução disponível na galeria, você deve publicar no catálogo de aplicativos da sua organização ou publicar [no AppSource.](./appsource/publish.md) [](#publish-to-your-organizations-app-catalog)

### <a name="publish-to-your-organizations-app-catalog"></a>Publicar no catálogo de aplicativos da sua organização

O catálogo de aplicativos da sua organização contém aplicativos exclusivos da sua organização e está completamente sob o controle da sua organização. Você pode encontrar mais informações no artigo [*Publicar aplicativos no catálogo de aplicativos da sua organização.*](/microsoftteams/tenant-apps-catalog-teams) Esse recurso só pode ser gerenciado por usuários do Teams com privilégios de administrador de locatários do Microsoft Office 365.

### <a name="publish-to-appsource"></a>Publicar no AppSource

O AppSource (anteriormente conhecido como Office Store) fornece um local conveniente para você distribuir seu aplicativo Microsoft Teams, bem como outros tipos de extensibilidade do Office 365, como complementos do Office e do SharePoint. Siga nossas diretrizes para [enviar seu aplicativo ao AppSource.](./appsource/publish.md)

## <a name="government-community-cloud-gcc-organizations"></a>Organizações do Government Community Cloud (GCC)

### <a name="upload-your-custom-app-directly-to-teams"></a>Carregar seu aplicativo personalizado diretamente no Teams

 Como administrador de locatários GCC, você decidirá se deve carregar um aplicativo personalizado em seu ambiente de locatário e se deve publicá-lo no catálogo de aplicativos do locatário. A Microsoft não possui nem controla seus aplicativos personalizados, portanto, você deve garantir que todos os pontos de extremidade sejam compatíveis com os requisitos da sua organização. Além disso, se a solução do aplicativo incluir um bot ou extensão de mensagem, você precisará concluir o registro do [Bot Framework](https://dev.botframework.com/) da seguinte maneira:

1. Na página **Conectar-se aos** canais, em **Adicionar um canal em destaque,** selecione **Teams**.
1. Navegue até **a página Configurar MSTeams** *(veja* abaixo).
1. Em **Mensagens,** selecione o **botão de opção Microsoft Teams for Government Customers.**
1. No canto inferior esquerdo da página, selecione **Salvar**.  

>[!IMPORTANT]
> Você não pode usar a configuração comercial do Teams para carregar/fazer sideload de seu aplicativo personalizado em um ambiente GCC. Você deve selecionar o botão de opção **Microsoft Teams for Government Customers** para uma configuração compatível com GCC.

![Página de configuração de mensagens do Teams](../../assets/images/gcc-configure.png)

> [!NOTE]
>
> * As instruções de carregamento para ambientes GCC, apresentadas acima, se aplica aos aplicativos personalizados do Teams. </br>
> * Os aplicativos da Microsoft em conformidade são habilitados no ambiente GCC, por padrão, no Teams.
> * Aplicativos de terceiros estão desabilitados no nível do locatário e devem ser gerenciados por meio das políticas de permissão do aplicativo [da sua organização.](/microsoftteams/teams-app-permission-policies) Certifique-se de revisar todos os aplicativos de terceiros para garantir que eles se alinhem com as políticas e procedimentos da sua organização.

> [!TIP]
>
> Os parceiros desenvolvedores do Microsoft 365 fornecem detalhes de segurança, manipulação de dados e conformidade para seus aplicativos de terceiros do Teams por meio do Programa de Certificação de Aplicativos do [Microsoft 365.](/microsoft-365-app-certification/overview) *Confira também a Certificação* [de Aplicativos do Microsoft Teams.](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/application-certification)
</br></br>
