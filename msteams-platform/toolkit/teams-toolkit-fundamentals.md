---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Neste módulo, aprenda o Kit de Ferramentas do Teams, a Instalação do Kit de Ferramentas do Teams e o percurso do usuário do Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: bdcf92b52956eee6db21eb03d115a494c0f063e9
ms.sourcegitcommit: dccb48902e08484692ab927415bcd3d61dc50db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2022
ms.locfileid: "67806770"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams

O Kit de Ferramentas do Teams é um recurso de funcionalidade que permite executar várias funções no Microsoft Visual Studio Code, bem como no Visual Studio. Com a ajuda do Kit de Ferramentas do Teams, você pode automatizar o processo desde a criação até a implantação e a personalização do aplicativo. Os vários recursos e vantagens do Kit de Ferramentas do Teams são discutidos na respectiva documentação para os ambientes escolhidos.

::: zone pivot="visual-studio-code"

## <a name="teams-toolkit-overview-for--visual-studio-code"></a>Visão geral do Kit de Ferramentas do Teams para Visual Studio Code

O Kit de Ferramentas do Teams permite que você crie, depure e implante seu aplicativo Teams diretamente Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as seguintes vantagens:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Serviços do Azure e do Microsoft 365 com abordagem de configuração zero.

Para o desenvolvimento de aplicativos do Teams, semelhante ao Kit de Ferramentas do Teams para o Visual Studio, você pode usar a [Ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste no Kit de ferramentas `teamsfx`.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de ferramentas do Teams

O Kit de ferramentas do Teams automatiza o trabalho manual e fornece uma ótima integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário do Kit de ferramentas do Teams:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="Percurso do usuário do Kit de Ferramentas do Teams" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

Os principais marcos desta jornada são:

1. Comece criando um novo projeto ou experimentando um aplicativo Teams de exemplo.
1. Adicione recursos ou edite o arquivo de manifesto conforme necessário.
1. Use a Microsoft 365 para compilar e depurar seu aplicativo Teams.
1. Use a conta do Azure para provisionar e implantar seu aplicativo na nuvem.
1. Publique seu aplicativo no Teams.

A tabela a seguir ajuda você a obter a visão geral do Kit de Ferramentas do Teams Visual Studio Code:

| Processo | Descrição |
| ---- | ---- |
| Instalar o Kit de Ferramentas do Teams | Você pode instalar o Kit de Ferramentas do Teams de duas maneiras: <br> - Usando Visual Studio Code <br> - Usando o Visual Studio Code Marketplace|
| Suporte para ambientes de build | Você tem dois tipos diferentes de ambiente: <br> – Javascript ou Typescript <br> - SPFx |
| Suporte para tipos de aplicativo e função do Azure | Há dois tipos diferentes de aplicativos: <br> – Aplicativo baseado em funcionalidade, como tab, bot, extensão de mensagem  <br> – Aplicativo teams baseado em cenário, como bot de notificação, bot de comando e guia pessoal habilitada para SSO |
| Desenvolver seu aplicativo Teams | Ele contém: <br> – Adicionar e gerenciar o ambiente <br> – Criar um aplicativo de várias funcionalidades <br> – Criar recursos de nuvem baseados em funcionalidade <br> – Integrar API de terceiros <br> – Personalizar o arquivo de manifesto <br> - SDK do TeamsFx |
| Depurar seu aplicativo Teams | Ele contém: <br> – Depurar seu aplicativo teams localmente <br> – Depurar processo em segundo plano|
| Hospedar seu aplicativo Teams | Ele contém: <br> – Provisionar recursos para a nuvem <br> – Implantar na nuvem|
| Testar seu aplicativo Teams | Ele contém: <br> – Integrar e collabrate <br> – Pacote de metadados do Zip Teams <br> - Fazer sideload e testar o aplicativo no ambiente do Teams <br> – Testar o comportamento do aplicativo em um ambiente diferente|
| Publicar seu aplicativo Teams | Ele contém: <br> - Publicar seu aplicativo <br> – Gerenciar a aprovação do administrador <br> - Publicar no repositório <br> – Integrar com o Portal do Desenvolvedor |

### <a name="entities-integrated-with-teams-toolkit"></a>Entidades integradas ao Kit de Ferramentas do Teams

O Kit de Ferramentas do Teams é uma extensão Visual Studio Code. Ele é integrado às seguintes entidades no Kit de Ferramentas do Teams, como o Azure AD e o Microsoft 365, o Portal do Desenvolvedor e o Microsoft Graph. Todas as entidades são integradas ao Kit de Ferramentas do Teams e ajudam os usuários a criar um aplicativo.

| Entidades | Descrição |
| ---- | ---- |
| Microsoft Azure AD  | O Azure Active Directory (Azure AD) é um serviço de gerenciamento de acesso e identidade baseado em nuvem. Esse serviço ajuda seus funcionários a acessar recursos externos, como o Microsoft 365, o portal do Azure e milhares de outros aplicativos SaaS. |
| Microsoft 365  | Conta de desenvolvedor do Teams ao desenvolver um aplicativo.|
| Portal do Desenvolvedor | O Portal do Desenvolvedor para Teams é a principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais. |
| Microsoft Graph | O Microsoft Graph é o gateway para dados e inteligência no Microsoft 365. Ele fornece um modelo de programação unificado que você pode usar para acessar a enorme quantidade de dados no Microsoft 365, Windows e Enterprise Mobility + Security. |

O Kit de ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

## <a name="manage-your-apps-using-developer-portal"></a>Gerenciar seus aplicativos usando o Portal do Desenvolvedor

Como o Kit de Ferramentas do Teams é integrado ao Portal do Desenvolvedor, você pode configurar, distribuir e gerenciar seu aplicativo usando o Portal do Desenvolvedor para [Teams](../concepts/build-and-test/teams-developer-portal.md) em DEPLOYMENT depois de criar um aplicativo. Para obter mais informações, consulte [gerenciar seus aplicativos do Teams usando o Portal do Desenvolvedor](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Portal do Desenvolvedor":::

::: zone-end

::: zone pivot="visual-studio"

## <a name="teams-toolkit-overview-for-visual-studio"></a>Visão geral do Kit de Ferramentas do Teams para Visual Studio

O Kit de Ferramentas do Teams para Visual Studio ajuda você a criar, depurar e implantar aplicativos do Microsoft Teams. O Kit de Ferramentas do Teams para Visual Studio é GA no Visual Studio 2022 versão 17.3. O desenvolvimento de aplicativos com o Kit de Ferramentas do Teams tem as vantagens de:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Azure e serviços Microsoft 365 com abordagem de configuração zero

Para o desenvolvimento de aplicativos do Teams, você também pode usar a [ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), semelhante ao Kit de Ferramentas do Teams para o código do Microsoft Visual Studio que inclui o Kit de Ferramentas `teamsfx`.

O Kit de Ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

> [!NOTE]
> O Kit de Ferramentas do Teams não está disponível em outras versões.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de Ferramentas do Teams

O Kit de Ferramentas do Teams automatiza o trabalho manual e fornece uma excelente integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png" alt-text="Percurso do usuário do kit de ferramentas do Teams" lightbox="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png":::

Os principais marcos desta jornada são:

1. Você pode começar criando um novo projeto ou tentar criar um aplicativo teams de exemplo.
1. Em seguida, você pode editar o código ou o arquivo de manifesto conforme necessário.
1. Para criar e depurar o aplicativo Teams, você pode usar sua conta do Microsoft 365.
1. Para provisionar e implantar seu aplicativo na nuvem, você pode usar sua conta do Azure.
1. Por fim, você pode publicar seu aplicativo no Teams.

As operações a seguir ainda não têm suporte no Kit de Ferramentas do Teams para Visual Studio em comparação com o Kit de Ferramentas do Teams para Microsoft Visual Studio Code, no entanto, elas estão planejadas no roteiro do produto futuro.

* Adicione outros recursos do Teams ao seu aplicativo do Teams.
* Adicionar mais recursos do Azure ao aplicativo Teams
* Adicione o SSO (logon único) ao aplicativo Teams.
* Adicione uma conexão de API ao aplicativo Teams.
* Personalize Microsoft Azure Active Directory (Azure AD) manifesto.
* Adicione pipelines de CI/CD.
* Gerenciar vários ambientes de nuvem.
* Colabore em projetos do Teams.
* Publique o aplicativo Teams.

### <a name="teamsfx-net-sdk-reference-docs"></a>Documentos de referência do SDK do .NET do TeamsFx

* [Microsoft.Extensions.DependencyInjection Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

::: zone-end

## <a name="see-also"></a>Confira também

* [Criar um novo aplicativo teams no Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)

