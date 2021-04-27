---
title: Distribuir seu aplicativo
description: Descreve as três opções para distribuir seu aplicativo'
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office distribute AppSource sideload upload app
ms.openlocfilehash: a033b90be436fbf20ef11fe95059d04388cefdf8
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020776"
---
# <a name="distribute-your-microsoft-teams-app"></a>Distribuir seu aplicativo do Microsoft Teams

Depois de criar seu aplicativo, há três opções para distribuí-lo:

1. [Carregue seu aplicativo diretamente](#upload-your-app-directly).
2. [Publique seu aplicativo no catálogo de aplicativos da sua organização.](#publish-to-your-organizations-app-catalog)
3. [Publique seu aplicativo por meio do AppSource](#publish-to-appsource).

## <a name="enterprise-organizations"></a>Organizações empresariais

### <a name="upload-your-app-directly"></a>Carregar seu aplicativo diretamente

Essa é a maneira mais fácil de testar e usar seu aplicativo. Se você for o proprietário da equipe e/ou carregar aplicativos personalizados estiver [habilitado,](/microsoftteams/admin-settings)poderá carregar [diretamente (ou fazer sideload)](./apps-upload.md) do aplicativo e começar a usá-lo imediatamente. No entanto, se você quiser compartilhar o aplicativo com outras pessoas, você terá que enviar seu pacote de aplicativos e pedir que eles carreguem ele de forma independente.

Se você quiser distribuir seu aplicativo mais amplamente, o Teams fornece uma galeria no aplicativo para que os usuários encontrem ou descubram aplicativos do Teams de alta qualidade. Para ter sua solução disponível na galeria, você deve publicar no catálogo de aplicativos da sua organização ou [publicar no AppSource](./appsource/publish.md). [](#publish-to-your-organizations-app-catalog)

### <a name="publish-to-your-organizations-app-catalog"></a>Publicar no catálogo de aplicativos da sua organização

O catálogo de aplicativos da sua organização contém aplicativos exclusivos da sua organização e está completamente sob o controle da sua organização. Você pode encontrar mais informações no artigo Publicar aplicativos no catálogo [*de aplicativos da sua organização.*](/microsoftteams/tenant-apps-catalog-teams) Esse recurso só pode ser gerenciado por usuários do Teams com Microsoft Office privilégios de administrador de locatários 365.

### <a name="publish-to-appsource"></a>Publicar no AppSource

O AppSource (anteriormente conhecido como Office Store) fornece um local conveniente para você distribuir seu aplicativo do Microsoft Teams, bem como outros tipos de extensibilidade do Office 365, como os complementos do Office e os complementos do SharePoint. Siga nossas diretrizes para [enviar seu aplicativo para AppSource](./appsource/publish.md).

## <a name="government-community-cloud-gcc-organizations"></a>Organizações de Nuvem da Comunidade Governamental (GCC)

### <a name="upload-your-custom-app-directly-to-teams"></a>Carregar seu aplicativo personalizado diretamente no Teams

 Como administrador de locatários GCC, você decidirá se deve carregar um aplicativo personalizado em seu ambiente de locatário e se deve publicá-lo no catálogo de aplicativos do locatário. A Microsoft não possui nem controla seus aplicativos personalizados, portanto, você deve garantir que todos os pontos de extremidade sejam compatíveis com os requisitos da sua organização. Além disso, se a solução do aplicativo incluir um bot ou extensão de mensagem, você precisará concluir o registro [da Estrutura](https://dev.botframework.com/) de Bot da seguinte maneira:

1. Na página **Conectar-se aos canais,** em **Adicionar um canal em destaque,** selecione **Teams**.
1. Navegue até **a página Configurar MSTeams** *(consulte* abaixo).
1. Em **Mensagens,** selecione o botão de opção **Microsoft Teams for Government Customers.**
1. No canto inferior esquerdo da página, selecione **Salvar**.  

>[!IMPORTANT]
> Não é possível usar a configuração comercial do Teams para carregar/fazer o sideload do aplicativo personalizado em um ambiente GCC, você deve selecionar o botão de opção **Microsoft Teams for Government Customers** para uma configuração compatível com GCC.

![Página de configuração de mensagens do Teams](../../assets/images/gcc-configure.png)

> [!NOTE]
>
> * As instruções de carregamento para ambientes GCC, apresentadas acima, se aplica a aplicativos personalizados do Teams. </br>
> * Os aplicativos Microsoft compatíveis são habilitados no ambiente GCC, por padrão, no Teams.
> * Aplicativos de terceiros estão desabilitados no nível do locatário e devem ser gerenciados por meio das políticas de permissão do [aplicativo da sua organização.](/microsoftteams/teams-app-permission-policies) Verifique se você revisa todos os aplicativos de terceiros para garantir que eles se alinham às políticas e procedimentos da sua organização.

> [!TIP]
>
> Os parceiros de desenvolvedor do Microsoft 365 fornecem detalhes de segurança, tratamento de dados e conformidade para seus aplicativos do Teams de terceiros por meio do Programa de Certificação de Aplicativos do [Microsoft 365.](/microsoft-365-app-certification/overview) *Consulte também Certificação* [de Aplicativos do Microsoft Teams.](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/application-certification)
</br></br>
