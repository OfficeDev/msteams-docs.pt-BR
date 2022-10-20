---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Neste módulo, aprenda o Kit de Ferramentas do Teams, a Instalação do Kit de Ferramentas do Teams e o percurso do usuário do Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 786bfd318f1cefa4329e54b5a19cba89a823bb5b
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615335"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams

O Kit de Ferramentas do Teams simplifica a introdução ao desenvolvimento de aplicativos para o Microsoft Teams usando o Visual Studio e o Visual Studio Code.

* Começar com um modelo de projeto ou de um exemplo
* Economize tempo de configuração com o registro e a configuração automatizados do aplicativo
* Executar e depurar para o Teams diretamente de ferramentas familiares
* Padrões inteligentes para hospedagem no Azure usando infraestrutura como código e Bicep
* Criar configurações exclusivas, como desenvolvimento, teste e produção usando o recurso Ambientes
* Traga seu aplicativo para sua organização ou o teams App Store usando ferramentas de publicação internas

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="Percurso do usuário do Kit de Ferramentas do Teams" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

## <a name="available-for-visual-studio-and-visual-studio-code"></a>Disponível para Visual Studio e Visual Studio Code

O Kit de Ferramentas do Teams está disponível gratuitamente para Visual Studio Code e dá suporte ao Visual Studio 2022 Community, Professional e Enterprise. Visite a [documentação Instalar o Kit de Ferramentas do Teams](./install-Teams-Toolkit.md) para obter mais informações sobre instalação e configuração.

| Kit de ferramentas do Teams | Visual Studio | Visual Studio Code |
| - | ------------- | ------------------ |
| Instalação | Disponível no Instalador do Visual Studio | Disponível no VS Marketplace |
| Compilar com | C#, .NET, ASP.NET, Blazor | JavaScript, TypeScript, React, SPFx |

## <a name="features"></a>Recursos

### <a name="project-templates"></a>Modelos de projeto

O Kit de Ferramentas do Teams reduz a complexidade da introdução a modelos para cenários comuns de aplicativos de linha de negócios e padrões inteligentes para acelerar seu tempo de produção. Se você já estiver familiarizado com o desenvolvimento de aplicativos do Teams, também poderá começar diretamente com modelos voltados para funcionalidades. Ou seja, Tab, Bot, Extensão de Mensagens.

::: zone pivot="visual-studio-code"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app.png" alt-text="Criar novo menu de aplicativo do Teams no VS Code":::
::: zone-end

::: zone pivot="visual-studio"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app-vs.png" alt-text="Criar novo menu de aplicativo do Teams no VS Code":::
::: zone-end

### <a name="automatic-registration-and-configuration"></a>Registro e configuração automáticos

Economize tempo e permita que o kit de ferramentas registre automaticamente o aplicativo no Portal do Desenvolvedor do Teams e defina configurações como o Azure Active Directory automaticamente quando você executar ou depurar o aplicativo pela primeira vez. Entre com sua conta do Microsoft 365 para controlar onde o aplicativo está configurado e personalize o manifesto de Azure AD incluído quando precisar de mais flexibilidade.

::: zone pivot="visual-studio-code"

### <a name="multiple-environments"></a>Vários ambientes

Com os recursos de Ambientes, você pode criar agrupamentos diferentes de recursos de nuvem para simplificar a execução e o teste do aplicativo. Use o ambiente de "desenvolvimento" com sua assinatura do Azure ou crie um com uma assinatura diferente para preparo, teste e produção.

### <a name="quick-access-to-teams-developer-portal"></a>Acesso rápido ao Portal do Desenvolvedor do Teams

Acesse rapidamente o Portal do Desenvolvedor do Teams, no qual você pode configurar, distribuir e gerenciar seu aplicativo. Para obter mais informações, consulte [gerenciar seus aplicativos do Teams usando o Portal do Desenvolvedor](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Portal do Desenvolvedor":::

::: zone-end

::: zone pivot="visual-studio"

#### <a name="teamsfx-net-sdk-reference-docs"></a>Documentos de referência do SDK do .NET do TeamsFx

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
