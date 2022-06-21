---
title: Estender aplicativos do Teams pelo Microsoft 365 (Pré-visualização)
description: Saiba como criar e atualizar suas experiências Teams aplicativo para outras áreas de alto uso de Microsoft 365.
ms.date: 05/24/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: a595626fab5a8e3d98e45066392cfad8d7604a22
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189888"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

Com as versões mais recentes do [SDK do cliente JavaScript](../tabs/how-to/using-teams-client-sdk.md) (versão 2.0.0), do manifesto do aplicativo [do Teams](../resources/schema/manifest-schema.md) (versão 1.13) e [do Teams Toolkit](../toolkit/visual-studio-code-overview.md), você pode criar e atualizar aplicativo Microsoft Teams s Teams para execução em outros aplicativos de alto uso Microsoft 365  e publique-os no Marketplace comercial da [Microsoft (Microsoft AppSource](https://appsource.microsoft.com/)).

Estender seu aplicativo Teams em Microsoft 365 fornece uma maneira simplificada de fornecer aplicativos multiplataforma para um público-alvo expandido do usuário: de uma única base de código, você pode criar experiências de aplicativo personalizadas para ambientes Teams, Outlook e Office. Os usuários finais não precisam sair do contexto do trabalho para usar seu aplicativo, e os administradores se beneficiam de um fluxo de trabalho de gerenciamento e implantação consolidado.

A Teams de aplicativos continua evoluindo e expandindo holisticamente no Microsoft 365 ecossistema. Aqui está o suporte atual de Teams da plataforma de aplicativos em Microsoft 365 (Teams, Outlook e Office como hosts de aplicativo):

|          | Elemento de manifesto do aplicativo | Teams suporte |Outlook* | Office* | Notas |
|--|--|--|--|--|--|
| [**Guias**](../tabs/what-are-tabs.md) (escopo pessoal)    |`staticTabs`  | Web, Área de Trabalho, Celular | Web (Lançamento direcionado), Área de Trabalho (Canal Beta) | Web (versão direcionada)| O escopo de canal e grupo ainda não tem suporte para Microsoft 365. Veja [as anotações](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Extensões de mensagem**](../messaging-extensions/what-are-messaging-extensions.md) (baseadas em pesquisa)| `composeExtensions` | Web, Área de Trabalho, Celular| Web (Lançamento direcionado), Área de Trabalho (Canal Beta)| - |Ainda não há suporte para a ação Microsoft 365. Veja [as anotações](extend-m365-teams-message-extension.md#preview-your-message-extension-in-outlook). |
| [**Graph conectores**](/graph/connecting-external-content-connectors-overview)| `graphConnector` | Web, Área de Trabalho, Celular| Web, Área de Trabalho | Web| Ver [anotações](#graph-connectors)
| [**Office suplementos**](/office/dev/add-ins/develop/json-manifest-overview) (versão prévia) | `extensions` | - | Web, Área de Trabalho | - | Disponível somente na versão [do manifesto devPreview](../resources/schema/manifest-schema-dev-preview.md) . Veja [as anotações](#office-add-ins-preview).|

\*A [Microsoft 365 de lançamento](/microsoft-365/admin/manage/release-options-in-office-365) direcionada e Microsoft 365 Apps registro de [](/deployoffice/change-update-channels) canal de atualização exigem a aceitação do administrador para toda a organização ou usuários selecionados. Os canais de atualização são específicos do dispositivo e se aplicam somente a instalações de Office em execução Windows.

Para obter diretrizes sobre o manifesto do aplicativo Teams e as diretrizes de controle de versão do SDK, bem como mais detalhes sobre o suporte à funcionalidade atual da plataforma Teams em Microsoft 365, consulte Teams visão geral do [SDK do cliente JavaScript](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Damos boas-vindas aos seus comentários e relatórios de problemas à medida que você expande Teams aplicativos para serem executados em todo o Microsoft 365 ecossistema! Use os canais regulares [Microsoft Teams comunidade de desenvolvedores](/microsoftteams/platform/feedback) para enviar comentários.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Guias pessoais e extensões de mensagens Outlook e Office

Alcance seus usuários onde eles estão, bem no contexto do trabalho, estendendo seu aplicativo Web como um aplicativo de guia pessoal do Teams que também é executado no Outlook e Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução no Outlook, no Office e no Teams":::

Você também pode estender suas extensões de mensagem de Teams baseadas em pesquisa para a área de trabalho do Outlook na Web e do Windows, permitindo que seus clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além de Microsoft Teams clientes.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Extensão de mensagem em execução no Outlook e no Teams":::

Criar seu aplicativo com o [manifesto Teams aplicativo](../resources/schema/manifest-schema.md) e Teams [SDK do cliente JavaScript](../tabs/how-to/using-teams-client-sdk.md) fornece um processo de desenvolvimento consolidado. Ao permitir que você forneça uma experiência simplificada de implantação, instalação e administrador para seus clientes, você pode expandir o alcance e o uso potenciais do seu aplicativo.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Usar Teams manifesto do aplicativo em Microsoft 365

Com o objetivo de simplificar e simplificar o ecossistema de desenvolvedores do Microsoft 365, continuaremos expandindo o manifesto do aplicativo Teams para outras áreas do Microsoft 365 com o seguinte.

### <a name="graph-connectors"></a>Graph conectores

Com os conectores do Microsoft Graph, sua organização pode indexar dados de terceiros para que eles apareçam como resultados Pesquisa da Microsoft, expandindo os tipos de fontes de conteúdo pesquisáveis em seus Teams aplicativos.
Para obter mais informações, consulte [a visão geral Graph conectores do Microsoft Pesquisa da Microsoft](/microsoftsearch/connectors-overview).

Para começar a usar conectores de grafo em aplicativos Teams, confira o exemplo [](https://aka.ms/teamsfx-graph-connector-sample) de conectores Teams Toolkit Graph e a referência do esquema de manifesto da versão prévia do [Microsoft Teams](../resources/schema/manifest-schema-dev-preview.md) Developer.

### <a name="office-add-ins-preview"></a>Office suplementos (versão prévia)

Agora você pode definir e implantar Office suplementos na versão prévia [do desenvolvedor do](../resources/schema/manifest-schema-dev-preview.md) manifesto Microsoft Teams aplicativo. Atualmente, essa versão prévia está limitada Outlook suplementos em execução no Office para Windows.

Para obter mais informações, consulte [Manifesto do Teams para Suplementos do Office (visualização)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-appsource-submission"></a>Envio do Microsoft AppSource

Junte-se ao número crescente de aplicativos de Teams de produção no repositório [Microsoft AppSource](https://appsource.microsoft.com/) com suporte expandido para Outlook e Office visualização (versão direcionada). O processo de envio de aplicativos para aplicativos Teams habilitados para [Outlook e Office](../concepts/deploy-and-publish/appsource/publish.md) é o mesmo que para aplicativos Teams tradicionais; a única diferença é que você usará Teams um manifesto do aplicativo versão [1.13](../tabs/how-to/using-teams-client-sdk.md) no pacote do aplicativo, que apresenta suporte para aplicativos Teams executados em Microsoft 365.

Depois de publicado como um aplicativo Teams habilitado para Teams, seu aplicativo será detectável como um aplicativo inserível nas lojas Outlook e Aplicativo do Office, além da Teams Store. Microsoft 365 Ao executar em Outlook e Office, seu aplicativo usa as mesmas permissões concedidas no Teams. Teams administradores podem [gerenciar o acesso a Teams aplicativos em](/MicrosoftTeams/manage-third-party-teams-apps) Microsoft 365 para usuários em sua organização.

Para obter mais informações, [consulte Publicar Teams aplicativos para Microsoft 365](publish.md).

## <a name="next-step"></a>Próxima etapa

Configure seu ambiente de desenvolvimento para criar Teams aplicativos para Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
