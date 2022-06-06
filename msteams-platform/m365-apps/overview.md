---
title: Estender aplicativos do Teams pelo Microsoft 365 (Pré-visualização)
description: Estenda suas experiências de aplicativo do Teams para outras áreas de alto uso do Microsoft 365
ms.date: 05/24/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 5c4eb5ed51ab8679cffa7bfa8aff62af72e58d25
ms.sourcegitcommit: 73e6767127cb27462f819acd71a1e480580bcf83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2022
ms.locfileid: "65906243"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

Com as versões mais recentes do [SDK do cliente JavaScript do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) (versão 2.0.0), do manifesto do aplicativo [Teams](../resources/schema/manifest-schema.md) (versão 1.13) e do [Kit](../toolkit/visual-studio-code-overview.md) de Ferramentas do Teams, você pode criar e atualizar aplicativos do Teams para serem executados em outros produtos do Microsoft 365 de alto uso e publicá-los no Microsoft [AppSource (Marketplace](https://appsource.microsoft.com/) comercial da Microsoft).

Estender seu aplicativo Teams no Microsoft 365 fornece uma maneira simplificada de fornecer aplicativos multiplataforma para um público-alvo expandido do usuário: de uma única base de código, você pode criar experiências de aplicativo personalizadas para ambientes do Teams, Outlook e Office. Os usuários finais não precisam sair do contexto do trabalho para usar seu aplicativo, e os administradores se beneficiam de um fluxo de trabalho de gerenciamento e implantação consolidado.

A plataforma de aplicativos do Teams continua evoluindo e expandindo holisticamente para o ecossistema do Microsoft 365. Este é o suporte atual dos elementos da plataforma de aplicativos do Teams no Microsoft 365 (Teams, Outlook e Office como hosts de aplicativo):

|          | Elemento de manifesto do aplicativo | Suporte do Teams |Suporte do Outlook* | Suporte do Office* | Observações |
|--|--|--|--|--|--|
| [**Guias**](../tabs/what-are-tabs.md) (escopo pessoal)    |`staticTabs`  | Web, Área de Trabalho, Celular | Web (Lançamento direcionado), Área de Trabalho (Canal Beta) | Web (versão direcionada)| O escopo de canal e grupo ainda não é compatível com o Microsoft 365. Veja [as anotações](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Extensões de mensagem**](../messaging-extensions/what-are-messaging-extensions.md) (baseadas em pesquisa)| `composeExtensions` | Web, Área de Trabalho, Celular| Web (Lançamento direcionado), Área de Trabalho (Canal Beta)| - |Ainda não há suporte baseado em ação para o Microsoft 365. Veja [as anotações](extend-m365-teams-message-extension.md#preview-your-message-extension-in-outlook). |
| [**Conectores do Graph**](/microsoftsearch/connectors-overview)| `graphConnector` | Web, Área de Trabalho, Celular| Web, Área de Trabalho | Web| Ver [anotações](#graph-connectors)
| [**Suplementos do Office**](/office/dev/add-ins/develop/json-manifest-overview) (versão prévia) | `extensions` | - | Web, Área de Trabalho | - | Disponível somente na versão [do manifesto devPreview](../resources/schema/manifest-schema-dev-preview.md) . Veja [as anotações](#office-add-ins-preview).|

\* A [opção de lançamento direcionado do Microsoft 365 e](/microsoft-365/admin/manage/release-options-in-office-365) o registro do canal de atualização do [Microsoft 365 Apps](/deployoffice/change-update-channels) exigem a aceitação do administrador para toda a organização ou usuários selecionados. Os canais de atualização são específicos do dispositivo e se aplicam somente a instalações do Office em execução no Windows.

Para obter diretrizes sobre o manifesto do aplicativo Teams e as diretrizes de controle de versão do SDK, bem como mais detalhes sobre o suporte à funcionalidade da plataforma Teams atual no Microsoft 365, consulte a visão geral do [SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Damos boas-vindas aos seus comentários e relatórios de problemas conforme você expande os aplicativos do Teams para serem executados em todo o ecossistema do Microsoft 365! Use os canais regulares [da comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para enviar comentários.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Guias pessoais e extensões de mensagens no Outlook e no Office

Acesse seus usuários onde eles estão, bem no contexto do trabalho, estendendo seu aplicativo Web como um aplicativo de guia pessoal do Teams que também é executado no Outlook e no Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução no Outlook, no Office e no Teams":::

Você também pode estender suas extensões de mensagem do Teams baseadas em pesquisa para o Outlook na Web e na área de trabalho do Windows, permitindo que seus clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além de clientes do Microsoft Teams.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Extensão de mensagem em execução no Outlook e no Teams":::

Criar seu aplicativo com o manifesto mais [recente do aplicativo Teams](../resources/schema/manifest-schema.md) e [o SDK do cliente JavaScript do Teams](../tabs/how-to/using-teams-client-sdk.md) fornece um processo de desenvolvimento consolidado. Ao permitir que você forneça uma experiência simplificada de implantação, instalação e administrador para seus clientes, você pode expandir o alcance e o uso potenciais do seu aplicativo.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Usar o manifesto do aplicativo Teams no Microsoft 365

Com o objetivo de simplificar e simplificar o ecossistema de desenvolvedores do Microsoft 365, continuaremos expandindo o manifesto do aplicativo Teams para outras áreas do Microsoft 365 com o seguinte.

### <a name="graph-connectors"></a>Conectores do Graph

Com os conectores do Microsoft Graph, sua organização pode indexar dados de terceiros para que eles apareçam como resultados da Pesquisa da Microsoft, expandindo os tipos de fontes de conteúdo pesquisáveis em seus aplicativos do Teams.
Para obter mais informações, consulte [a visão geral dos conectores do Microsoft Graph para a Pesquisa da Microsoft](/microsoftsearch/connectors-overview).

Para começar a usar conectores de grafo em aplicativos do Teams, confira o exemplo de conectores do [Teams Toolkit Graph](https://aka.ms/teamsfx-graph-connector-sample) e a referência de esquema de manifesto da versão prévia [do Desenvolvedor do Microsoft Teams](../resources/schema/manifest-schema-dev-preview.md) .

### <a name="office-add-ins-preview"></a>Suplementos do Office (versão prévia)

Agora você pode definir e implantar Suplementos do Office na versão prévia do [desenvolvedor do manifesto](../resources/schema/manifest-schema-dev-preview.md) do aplicativo Microsoft Teams. Atualmente, essa versão prévia está limitada aos Suplementos do Outlook em execução na assinatura do Office para Windows.

Para obter mais informações, consulte [Manifesto do Teams para Suplementos do Office (visualização)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-appsource-submission"></a>Envio do Microsoft AppSource

Junte-se ao número crescente de aplicativos do Teams de produção na [loja do Microsoft AppSource](https://appsource.microsoft.com/) com suporte expandido para os públicos-alvo do Outlook e do Office preview (Versão direcionada). O processo [de envio de aplicativos para aplicativos do Teams](../concepts/deploy-and-publish/appsource/publish.md) habilitados para Outlook e Office é o mesmo para aplicativos tradicionais do Teams; a única diferença é que você usará o manifesto do aplicativo Teams versão [1.13](../tabs/how-to/using-teams-client-sdk.md) no pacote do aplicativo, que apresenta suporte para aplicativos do Teams executados no Microsoft 365.

Depois de publicado como um aplicativo do Teams habilitado para Microsoft 365, seu aplicativo será detectável como um aplicativo inserível nas lojas de aplicativos do Outlook e do Office, além da loja do Teams. Ao executar no Outlook e no Office, seu aplicativo usa as mesmas permissões concedidas no Teams. Os administradores do Teams [podem gerenciar o acesso aos aplicativos do Teams no Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) para usuários em sua organização.

Para obter mais informações, consulte [Publicar aplicativos do Teams para o Microsoft 365](publish.md).

## <a name="next-step"></a>Próxima etapa

Configure seu ambiente de desenvolvimento para criar aplicativos do Teams para o Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
