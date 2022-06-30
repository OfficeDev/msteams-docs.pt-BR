---
title: Introdução - Visão geral
description: Neste módulo, saiba como começar a usar a documentação do desenvolvedor do Microsoft Teams que apresenta ferramentas comuns, conceitos fundamentais e recursos avançados.
ms.localizationpriority: high
ms.topic: reference
ms.openlocfilehash: 050e4a7bbf078686fa400858c684c6500ca71c1c
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558699"
---
# <a name="get-started"></a>Introdução

Bem-vindo ao Início da criação e implantação de aplicativos personalizados para Microsoft Teams!

Percorra as etapas para criar um aplicativo básico e real do Teams. A Introdução também apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.

Tenha uma ideia do que você aprenderá:

- Obter e executar rapidamente com o Kit de ferramentas do Microsoft Teams (uma extensão Visual Studio Code).
- Obter experiência com os Kit de ferramentas e SDKs.
- Configure e crie diferentes tipos de aplicativos do Teams.

Vamos dar uma olhada rápida nas opções de ambiente de compilação que você pode escolher e no roteiro para criar e implantar um aplicativo do Teams.

:::image type="content" source="../assets/images/get-started/gs-build-options.png" alt-text="Ilustração mostrando etapas básicas para criar e implantar um aplicativo do Teams":::

## <a name="app-capabilities-and-development-tools"></a>Recursos de aplicativo e ferramentas de desenvolvimento

Dependendo dos recursos que você deseja para seu aplicativo, escolha um conjunto de ferramentas de desenvolvimento apropriado.

| Recursos do aplicativo | Interações do usuário | Ferramentas recomendadas | SDKs | Pilhas de tecnologia / idiomas |
|--------|-------------|--------|--------|--------|
| Guias | Uma experiência da Web incorporada em tela inteira. | O Microsoft Visual Studio Code com extensão Kit de ferramentas do Teams ou a [CLI do TeamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) se preferir usar a CLI | [SDK TeamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) para bibliotecas principais e [SDK do cliente do Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) para funcionalidades da interface do usuário | Tecnologia Web em geral, HTML, CSS e JavaScript (incl. React). |
| Bots | Um bot de chat que conversa com membros. | Visual Studio Code com a extensão Kit de ferramentas do Teams ou a [CLI do TeamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [SDK do TeamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) e [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C#, Java e Python. |
| Extensões de mensagens | Atalhos para inserir conteúdo externo em uma conversa ou tomar medidas em mensagens. | Visual Studio Code com a extensão Kit de ferramentas do Teams ou a [CLI do TeamsFx](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [SDK do TeamsFx](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) e [SDK da Estrutura de Bots](https://dev.botframework.com/) | Node.js, C#, Java e Python. |

*Você não está limitado a usar essas pilhas específicas!*

Se você já estiver familiarizado com o fluxo de trabalho Yeoman, talvez prefira usar o [Gerador YoTeams Yeoman](https://github.com/pnp/generator-teams/blob/master/docs/docs/tutorials/build-your-first-microsoft-teams-app.md) para criar seus aplicativos.

> [!WARNING]
> Se você estiver usando o App Studio, recomendamos que você tente o Portal do Desenvolvedor para configurar, distribuir e gerenciar seus aplicativos do Teams.<br> O App Studio será preterido até 30 de junho de 2022.

## <a name="build-your-first-teams-app"></a>Crie seu primeiro aplicativo do Teams

Agora, vamos criar seu primeiro aplicativo Teams. Mas primeiro, escolha seu idioma (ou estrutura) e prepare seu ambiente de desenvolvimento.

> [!div class="nextstepaction"]
> [Criar um aplicativo de guia do Teams com JavaScript usando React](../sbs-gs-javascript.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo de bot do Teams com JavaScript](../sbs-gs-bot.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo de extensão de mensagem do Teams com JavaScript usando React](../sbs-gs-msgext.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo do Teams com o Blazor](../sbs-gs-blazorupdate.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo Teams com SPFx](../sbs-gs-spfx.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo Teams com C# ou .NET](../sbs-gs-csharp.yml)
> [!div class="nextstepaction"]
> [Criar um aplicativo Teams com Node.js](../sbs-gs-nodejs.yml)
> [!div class="nextstepaction"]
> [Compilar um bot de notificação com JavaScript](../sbs-gs-notificationbot.yml)
> [!div class="nextstepaction"]
> [Compilar um bot de comando com JavaScript](../sbs-gs-commandbot.yml)
> [!div class="nextstepaction"]

## <a name="see-also"></a>Confira também

* [Exemplos do Microsoft Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples#microsoft-teams-samples)
* [Recursos Git e GitHub](/contribute/additional-resources)
