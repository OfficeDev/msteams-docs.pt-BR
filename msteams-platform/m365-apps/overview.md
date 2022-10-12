---
title: Estender aplicativos do Teams pelo Microsoft 365 (Pré-visualização)
description: Saiba como estender aplicativos do Teams no Microsoft 365 (em execução no Teams, no Outlook e no Office como hosts de aplicativo).
ms.date: 10/10/2022
ms.topic: Conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 4c05fbe0c763d9b650573e33edfa5e332aaba90d
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537533"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

Com as versões mais recentes do [SDK do cliente JavaScript do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) (versão 2.0.0 e posterior), do manifesto do aplicativo [Teams](../resources/schema/manifest-schema.md) (versão 1.13 e posterior) e do [Kit](../toolkit/visual-studio-code-overview.md) de Ferramentas do Teams, você pode criar e atualizar aplicativos do Teams para serem executados em outros produtos microsoft 365 de alto uso e publicá-los no Marketplace comercial da [Microsoft (Microsoft AppSource](https://appsource.microsoft.com/)) ou na loja de aplicativos particulares da sua organização.

Estender seu aplicativo Teams no Microsoft 365 fornece uma maneira simplificada de fornecer aplicativos multiplataforma para um público-alvo expandido do usuário: de uma única base de código, você pode criar experiências de aplicativo personalizadas para ambientes do Teams, Outlook e Office. Os usuários finais não precisam sair do contexto do trabalho para usar seu aplicativo, e os administradores se beneficiam de um fluxo de trabalho de gerenciamento e implantação consolidado.

A plataforma de aplicativos do Teams continua evoluindo e expandindo holisticamente para o ecossistema do Microsoft 365. Este é o suporte atual dos elementos da plataforma de aplicativos do Teams no Microsoft 365 (Teams, Outlook e Office como hosts de aplicativo):

| Recursos do aplicativo Teams| Elemento de manifesto do aplicativo | Suporte do Teams |Suporte do Outlook* | Suporte do Office* | Notas |
|--|--|--|--|--|--|
| [**Escopo pessoal de**](../tabs/what-are-tabs.md) guias    |`staticTabs`  | Web, Área de Trabalho, Celular | Web (Lançamento direcionado), Área de Trabalho (Canal Beta) | Web (Lançamento Direcionado), Área de Trabalho (Canal Beta), Celular (Android)| O escopo de canal e grupo ainda não é compatível com o Microsoft 365. Veja [as anotações](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Extensões de mensagem baseadas**](../messaging-extensions/what-are-messaging-extensions.md) em pesquisa| `composeExtensions` | Web, Área de Trabalho, Celular| Web (Lançamento direcionado), Área de Trabalho (Canal Beta)| - |Ainda não há suporte baseado em ação para o Microsoft 365. Veja [as anotações](extend-m365-teams-message-extension.md#troubleshooting). |
| Desenrolamento de link | `composeExtensions.messageHandlers` | Web, Área de Trabalho | Web (Lançamento direcionado), Área de Trabalho (Canal Beta) | - | Ver [anotações](extend-m365-teams-message-extension.md#link-unfurling) |
| [**Suplementos do Office**](/office/dev/add-ins/develop/json-manifest-overview) (versão prévia) | `extensions` | - | Web, Área de Trabalho | - | Disponível somente na versão [do manifesto devPreview](../resources/schema/manifest-schema-dev-preview.md) . Veja [as anotações](#office-add-ins-preview).|

\*A [opção de versão direcionada do Microsoft 365](/microsoft-365/admin/manage/release-options-in-office-365) e o registro Microsoft 365 Apps canal de atualização exigem a aceitação do administrador para toda a organização ou usuários selecionados.[](/deployoffice/change-update-channels) Os canais de atualização são específicos do dispositivo e se aplicam somente a instalações do Office em execução no Windows.

Para obter diretrizes sobre o manifesto do aplicativo Teams e as diretrizes de controle de versão do SDK e mais detalhes sobre o suporte à funcionalidade atual da plataforma Teams no Microsoft 365, consulte a visão geral do [SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Damos boas-vindas aos seus comentários e relatórios de problemas conforme você expande os aplicativos do Teams para serem executados em todo o ecossistema do Microsoft 365! Use os canais regulares [da comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para enviar comentários.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Guias pessoais e extensões de mensagens no Outlook e no Office

Acesse seus usuários onde eles estão, bem no contexto do trabalho, estendendo seu aplicativo Web como um aplicativo de guia pessoal do [Teams](extend-m365-teams-personal-tab.md) que também é executado no Outlook e no Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="A captura de tela é um exemplo que mostra a guia Pessoal em execução no Outlook, no Office e no Teams.":::

No celular, você pode testar e depurar sua guia pessoal do Teams em execução no [aplicativo do Office para Android](extend-m365-teams-personal-tab.md#office-app-for-android).

:::image type="content" source="images/office-mobile-personal-tab.png" alt-text="A captura de tela é um exemplo que mostra a guia pessoal em execução no Office.":::

Você também pode estender suas extensões de mensagem do [Teams baseadas](extend-m365-teams-message-extension.md) em pesquisa para o Outlook na Web e a área de trabalho do Windows, permitindo que seus clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além de clientes do Microsoft Teams.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="A captura de tela é um exemplo que mostra a extensão mensagem em execução no Outlook e no Teams.":::

[O link desfralamento](extend-m365-teams-message-extension.md#link-unfurling)  funciona em ambientes do Outlook Web e do Windows da mesma maneira que faz no Microsoft Teams sem nenhum trabalho adicional do que usar o manifesto do aplicativo Teams versão 1.13 ou posterior.

:::image type="content" source="images/outlook-teams-link-unfurling.png" alt-text="A captura de tela é um exemplo que mostra o link desfragando em execução no Outlook e no Teams.":::

Crie seu aplicativo com o manifesto mais [recente do aplicativo Teams](../resources/schema/manifest-schema.md) e [o SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md) para beneficiar o processo de desenvolvimento de aplicativos do Microsoft 365 consolidado mais recente. Em seguida, forneça uma experiência simplificada de implantação, instalação e administrador para seus clientes que expande o alcance e o uso do seu aplicativo.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Usar o manifesto do aplicativo Teams no Microsoft 365

Com o objetivo de simplificar e simplificar o ecossistema de desenvolvedores do Microsoft 365, continuaremos expandindo o manifesto do aplicativo Teams para outras áreas do Microsoft 365 com o seguinte.

### <a name="office-add-ins-preview"></a>Suplementos do Office (versão prévia)

Agora você pode definir e implantar Suplementos do Office na versão prévia do [desenvolvedor do manifesto](../resources/schema/manifest-schema-dev-preview.md) do aplicativo Microsoft Teams. Atualmente, essa versão prévia está limitada aos Suplementos do Outlook em execução na assinatura do Office para Windows.

Para obter mais informações, consulte [Manifesto do Teams para Suplementos do Office (visualização)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-commercial-marketplace-submission"></a>Envio do marketplace comercial da Microsoft

Junte-se ao número crescente de aplicativos do Teams de produção no repositório do Microsoft AppSource (Marketplace comercial da [Microsoft](https://appsource.microsoft.com/) ) com suporte expandido para audiências de visualização do Outlook e do Office (Versão direcionada). O processo [de envio de aplicativos para aplicativos do Teams](../concepts/deploy-and-publish/appsource/publish.md) habilitados para Outlook e Office é o mesmo para aplicativos tradicionais do Teams. A única diferença é que você usará o manifesto do aplicativo Teams versão [1.13](../tabs/how-to/using-teams-client-sdk.md) no pacote do aplicativo, que apresenta suporte para aplicativos do Teams executados no Microsoft 365.

Depois de publicado como um aplicativo do Teams habilitado para Microsoft 365, seu aplicativo será detectável como um aplicativo inserível nas lojas de aplicativos do Outlook e do Office, além da loja do Teams. Ao executar no Outlook e no Office, seu aplicativo usa as mesmas permissões concedidas no Teams. Os administradores do Teams [podem gerenciar o acesso aos aplicativos do Teams no Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) para usuários em sua organização.

Para obter mais informações, consulte [Publicar aplicativos do Teams para o Microsoft 365](publish.md).

## <a name="next-step"></a>Próxima etapa

Configure seu ambiente de desenvolvimento para criar aplicativos do Teams para o Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
