---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Neste módulo, aprenda Kit de Ferramentas do Teams, Instalação do Teams Toolkit e Jornada de usuário do Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: cb3508bdd22f9d05c48e71b1b90ec4ffbf4c56af
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833160"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams

O Teams Toolkit torna simples começar o desenvolvimento de aplicativos para o Microsoft Teams usando o Visual Studio e Visual Studio Code.

* Comece com um modelo de projeto ou de um exemplo.
* Economize tempo de instalação com o registro e a configuração automatizados do aplicativo.
* Execute e depure para o Teams diretamente de ferramentas familiares.
* Padrões inteligentes para hospedagem no Azure usando infraestrutura como código e Bicep.
* Crie configurações exclusivas como desenvolvimento, teste e prod usando o recurso Ambientes.
* Traga seu aplicativo para sua organização ou o Teams App Store usando ferramentas de publicação internas.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="Jornada do usuário do Kit de Ferramentas do Teams" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

## <a name="available-for-visual-studio-and-visual-studio-code"></a>Disponível para Visual Studio e Visual Studio Code

O Teams Toolkit está disponível gratuitamente para Visual Studio Code e dá suporte ao Visual Studio 2022 Community, Professional e Enterprise. Visite a [documentação do Kit de Ferramentas do Teams de Instalação](./install-Teams-Toolkit.md) para obter mais informações sobre instalação e instalação.

| Kit de ferramentas do Teams | Visual Studio | Visual Studio Code |
| - | ------------- | ------------------ |
| Instalação | Disponível no Instalador do Visual Studio | Disponível no VS Marketplace |
| Compilar com | C#, .NET, ASP.NET, Blazor | JavaScript, TypeScript, React, SPFx |

## <a name="features"></a>Recursos

### <a name="project-templates"></a>Modelos de projeto

O Teams Toolkit reduz a complexidade de começar a usar modelos para cenários comuns de aplicativos de linha de negócios e padrões inteligentes para acelerar seu tempo de produção. Se você já estiver familiarizado com o desenvolvimento de aplicativos do Teams, também poderá começar diretamente com modelos focados em recursos. Ou seja, Tab, Bot, Extensão de Mensagens.

::: zone pivot="visual-studio-code"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app.png" alt-text="Criar um novo menu de aplicativo do Teams no VS Code":::
::: zone-end

::: zone pivot="visual-studio"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app-vs.png" alt-text="Criar um novo menu de aplicativo do Teams no VS Code":::
::: zone-end

### <a name="automatic-registration-and-configuration"></a>Registro e configuração automáticos

Economize tempo e deixe o kit de ferramentas registrar automaticamente o aplicativo no Portal do Desenvolvedor do Teams e configurar configurações como o Azure Active Directory automaticamente quando você executar ou depurar o aplicativo pela primeira vez. Entre com sua conta do Microsoft 365 para controlar onde o aplicativo está configurado e personalizar o manifesto de Azure AD incluído quando você precisar de mais flexibilidade.

::: zone pivot="visual-studio-code"

### <a name="multiple-environments"></a>Vários ambientes

Com os recursos de Ambientes, você pode criar diferentes agrupamentos de recursos de nuvem para tornar mais simples executar e testar seu aplicativo. Use o ambiente de "desenvolvimento" com sua assinatura do Azure ou crie um novo com uma assinatura diferente para preparo, teste e produção.

### <a name="quick-access-to-teams-developer-portal"></a>Acesso rápido ao Portal do Desenvolvedor do Teams

Acesse rapidamente o Portal do Desenvolvedor do Teams, onde você pode configurar, distribuir e gerenciar seu aplicativo. Para obter mais informações, confira [Gerenciar seus aplicativos do Teams usando o Portal do Desenvolvedor](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Portal do Desenvolvedor":::

::: zone-end

::: zone pivot="visual-studio"

#### <a name="teamsfx-net-sdk-reference-docs"></a>Documentos de referência do SDK do TeamsFx .NET

* [Microsoft.Extensions.DependencyInjection Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

::: zone-end

## <a name="see-also"></a>Confira também

* [Criar um novo aplicativo do Teams no Visual Studio](create-new-project.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo teams na nuvem usando o Visual Studio](deploy.md)
