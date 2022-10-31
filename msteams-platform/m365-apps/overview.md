---
title: Estender aplicativos do Teams pelo Microsoft 365 (Pré-visualização)
description: Saiba como estender aplicativos do Teams pelo Microsoft 365 (em execução no Teams, Outlook e Office como hosts de aplicativo).
ms.date: 10/10/2022
ms.topic: Conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 91586eefe21836118ed2f0a0071070ac2034bf76
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789874"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

Com as versões mais recentes do [SDK do cliente JavaScript do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) (versão 2.0.0 e posterior), [do manifesto do Aplicativo do Teams](../resources/schema/manifest-schema.md) (versão 1.13 e posterior) e do [Teams Toolkit](../toolkit/visual-studio-code-overview.md), você pode criar e atualizar aplicativos do Teams para executar em outros produtos microsoft 365 de alto uso e publicá-los no microsoft commercial marketplace ([Microsoft AppSource](https://appsource.microsoft.com/)) ou na loja de aplicativos privada da sua organização.

Estender seu aplicativo do Teams pelo Microsoft 365 fornece uma maneira simplificada de fornecer aplicativos entre plataformas para um público de usuário expandido: de uma única base de código, você pode criar experiências de aplicativo personalizadas para ambientes do Teams, Outlook e Office. Os usuários finais não precisarão sair do contexto de seu trabalho para usar seu aplicativo e os administradores se beneficiam de um fluxo de trabalho de gerenciamento e implantação consolidado.

A plataforma de aplicativos do Teams continua a evoluir e expandir de forma holística para o ecossistema do Microsoft 365. Aqui está o suporte atual dos elementos da plataforma de aplicativos do Teams no Microsoft 365 (Teams, Outlook e Office como hosts de aplicativo):

| Recursos do aplicativo Teams| Elemento manifesto do aplicativo | Suporte do Teams |Suporte ao Outlook* | Suporte ao Office* | Notas |
|--|--|--|--|--|--|
| [**Escopo pessoal tabs**](../tabs/what-are-tabs.md)    |`staticTabs`  | Web, Desktop, Mobile | Web (Versão direcionada), Área de Trabalho (Canal Beta) | Web (Versão direcionada), Área de Trabalho (Canal Beta), Móvel (Android)| O escopo do canal e do grupo ainda não tem suporte para o Microsoft 365. Confira [anotações](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Extensões de mensagem baseadas**](../messaging-extensions/what-are-messaging-extensions.md) em pesquisa| `composeExtensions` | Web, Desktop, Mobile| Web (Versão direcionada), Área de Trabalho (Canal Beta)| - |Ainda não há suporte para o Microsoft 365 baseado em ação. Confira [anotações](extend-m365-teams-message-extension.md#troubleshooting). |
| Desenrolamento de link | `composeExtensions.messageHandlers` | Web, Área de Trabalho | Web (Versão direcionada), Área de Trabalho (Canal Beta) | - | Ver [anotações](extend-m365-teams-message-extension.md#link-unfurling) |
| [**Suplementos do Office**](/office/dev/add-ins/develop/json-manifest-overview) (versão prévia) | `extensions` | - | Web, Área de Trabalho | - | Disponível apenas na versão [do manifesto de devPreview](../resources/schema/manifest-schema-dev-preview.md) . Confira [anotações](#office-add-ins-preview).|

\*A opção [microsoft 365 Targeted release](/microsoft-365/admin/manage/release-options-in-office-365) and [Microsoft 365 Apps update channel](/deployoffice/change-update-channels) enrollment require admin opt-in for entire organization or selected users. Os canais de atualização são específicos do dispositivo e se aplicam apenas às instalações do Office em execução no Windows.

Para obter diretrizes sobre o manifesto do aplicativo Teams e as diretrizes de versão do SDK e mais detalhes sobre o suporte atual à plataforma do Teams no Microsoft 365, consulte a [visão geral do SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Damos as boas-vindas aos seus comentários e relatórios de problemas à medida que você expande os aplicativos do Teams para serem executados no ecossistema do Microsoft 365! Use os [canais regulares da comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para enviar comentários.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Guias pessoais e extensões de mensagens no Outlook e no Office

Acesse seus usuários onde eles estão, bem no contexto de seu trabalho, estendendo seu aplicativo Web como um aplicativo de [guia pessoal do Teams](extend-m365-teams-personal-tab.md) que também é executado no Outlook e no Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="A captura de tela é um exemplo que mostra a guia Pessoal em execução no Outlook, Office e Teams.":::

No celular, você pode testar e depurar sua guia pessoal do Teams em execução no [aplicativo do Office para Android](extend-m365-teams-personal-tab.md#office-app-for-android).

:::image type="content" source="images/office-mobile-personal-tab.png" alt-text="A captura de tela é um exemplo que mostra a guia pessoal em execução no Office.":::

Você também pode estender suas [extensões de mensagens do Teams baseadas](extend-m365-teams-message-extension.md) em pesquisa para Outlook na Web e área de trabalho do Windows, permitindo que seus clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além de clientes do Microsoft Teams.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="A captura de tela é um exemplo que mostra a extensão de mensagem em execução no Outlook e no Teams.":::

[A desenrolação de](extend-m365-teams-message-extension.md#link-unfurling)  link funciona nos ambientes Web e Windows do Outlook da mesma forma que funciona no Microsoft Teams sem nenhum trabalho adicional do que usar o manifesto do aplicativo do Teams versão 1.13 ou posterior.

:::image type="content" source="images/outlook-teams-link-unfurling.png" alt-text="A captura de tela é um exemplo que mostra a desenrolação do Link em execução no Outlook e no Teams.":::

Crie seu aplicativo com o manifesto mais recente do [aplicativo Teams](../resources/schema/manifest-schema.md) e o [SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md) para beneficiar o processo de desenvolvimento de aplicativos do Microsoft 365 consolidado mais recente. Em seguida, forneça uma experiência simplificada de implantação, instalação e administrador para seus clientes que expanda o alcance e o uso do seu aplicativo.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Usar o manifesto do aplicativo teams no Microsoft 365

Com o objetivo de simplificar e simplificar o ecossistema de desenvolvedores do Microsoft 365, continuamos expandindo o manifesto do aplicativo Teams em outras áreas do Microsoft 365 com o seguinte.

### <a name="office-add-ins-preview"></a>Suplementos do Office (versão prévia)

Agora você pode definir e implantar suplementos do Office na [versão prévia do desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) do manifesto do aplicativo do Microsoft Teams. Atualmente, essa versão prévia está limitada aos suplementos do Outlook em execução na assinatura do Office para Windows.

Para obter mais informações, consulte [Manifesto do Teams para Suplementos do Office (visualização)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-commercial-marketplace-submission"></a>Envio do marketplace comercial da Microsoft

Junte-se ao crescente número de aplicativos do Teams de produção na loja do [Microsoft Commercial Marketplace](https://appsource.microsoft.com/) (Microsoft AppSource) com suporte expandido para públicos do Outlook e da versão prévia do Office (Versão Direcionada). O [processo de envio de aplicativo para aplicativos do Teams habilitados para Outlook e Office](../concepts/deploy-and-publish/appsource/publish.md) é o mesmo que para aplicativos tradicionais do Teams. A única diferença é que você usará o manifesto de aplicativo do Teams [versão 1.13](../tabs/how-to/using-teams-client-sdk.md) em seu pacote de aplicativos, que apresenta suporte para aplicativos do Teams executados no Microsoft 365.

Depois que seu aplicativo for publicado como um aplicativo do Teams habilitado para Microsoft 365, seu aplicativo será detectável como um aplicativo instalável nas lojas de aplicativos do Outlook e do Office, além da loja do Teams. Ao executar no Outlook e no Office, seu aplicativo usa as mesmas permissões concedidas no Teams. Os administradores do Teams podem [gerenciar o acesso aos aplicativos do Teams no Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) para usuários em sua organização.

Para obter mais informações, consulte [Publicar aplicativos do Teams para o Microsoft 365](publish.md).

## <a name="next-step"></a>Próxima etapa

Configure seu ambiente de desenvolvimento para criar aplicativos do Teams para o Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
