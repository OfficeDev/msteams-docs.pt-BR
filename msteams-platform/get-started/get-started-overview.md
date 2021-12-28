---
title: Começar - Visão geral
description: Visão geral para Começar a Microsoft Teams De desenvolvedor
ms.localizationpriority: medium
ms.topic: reference
keywords: Microsoft Teams exemplos de desenvolvedor
ms.openlocfilehash: 9ab8014ad528aff9cfb0f4e271332981af3a8f29
ms.sourcegitcommit: 8935f54330c5685ff091f01e2b18c70502428054
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/28/2021
ms.locfileid: "61619799"
---
# <a name="get-started"></a>Introdução

Bem-vindo ao Início da criação e implantação de aplicativos personalizados para Microsoft Teams!

Ande pelas etapas para criar um aplicativo básico Teams real. O Introdução também apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.

Aqui está uma ideia do que você aprenderá:

- Obter e executar rapidamente com o Microsoft Teams Toolkit (uma extensão Visual Studio Code de usuário).
- Obter experiência com os Toolkit e SDKs.
- Configure e crie diferentes tipos de Teams aplicativos.

Vamos dar uma olhada rápida nas opções de ambiente de complicação que você pode escolher e o roteiro para criar e implantar um aplicativo Teams.

:::image type="content" source="../assets/images/get-started/gs-build-options.png" alt-text="Ilustração mostrando etapas básicas para criar e implantar um Teams aplicativo":::

## <a name="app-capabilities-and-development-tools"></a>Recursos de aplicativo e ferramentas de desenvolvimento

Dependendo dos recursos que você deseja para seu aplicativo, escolha um conjunto de ferramentas de desenvolvimento apropriado.

| Recursos do aplicativo | Interações do usuário | Ferramentas recomendadas | SDKs | Pilhas de tecnologia / idiomas |
|--------|-------------|--------|--------|--------|
| Guias | Uma experiência da Web incorporada em tela inteira. | VS Code com Teams Toolkit ou [CLI teamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) se preferir usar CLI | [SDK teamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) para núcleos e [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) Teams cliente para funcionalidades da interface do usuário | Tecnologia Web em geral, HTML, CSS e JavaScript (incl. React). |
| Bots | Um bot de chat que conversa com membros. | VS Code com Teams Toolkit ou [CLI teamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [SDK do TeamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) e [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C#, Java e Python. |
| Extensões de mensagens | Atalhos para inserir conteúdo externo em uma conversa ou tomar medidas em mensagens. | VS Code com Teams Toolkit ou [CLI teamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [SDK do TeamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) e [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C#, Java e Python. |

*Você não está limitado a usar essas pilhas específicas!*

Se você já estiver familiarizado com o fluxo de trabalho yeoman, talvez prefira usar o [Gerador YoTeams Yeoman](https://github.com/pnp/generator-teams/blob/master/docs/docs/tutorials/build-your-first-microsoft-teams-app.md) para criar seus aplicativos.

> [!NOTE]
> Se você estiver usando o App Studio, recomendamos que você tente o Portal do Desenvolvedor para configurar, distribuir e gerenciar seus Teams aplicativos.


## <a name="build-your-first-teams-app"></a>Criar seu primeiro Teams app

Agora, vamos criar seu primeiro aplicativo Teams. Mas primeiro, escolha seu idioma (ou estrutura) e prepare seu ambiente de desenvolvimento.

> [!div class="nextstepaction"]
> [Criar um Teams com JavaScript usando React](../sbs-gs-javascript.yml)

> [!div class="nextstepaction"]
> [Criar um Teams com SPFx](../sbs-gs-spfx.yml)

> [!div class="nextstepaction"]
> [Criar um Teams com C# ou .NET](../sbs-gs-csharp.yml)

> [!div class="nextstepaction"]
> [Criar um Teams com Node.js](../sbs-gs-nodejs.yml)

## <a name="see-also"></a>Confira também

* [Microsoft Teams exemplos](https://github.com/OfficeDev/Microsoft-Teams-Samples#microsoft-teams-samples)
* [Git e GitHub recursos](/contribute/additional-resources)
