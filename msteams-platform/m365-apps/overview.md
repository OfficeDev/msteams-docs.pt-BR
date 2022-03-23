---
title: Estender Teams aplicativos em Microsoft 365 (visualização)
description: Estender suas Teams de aplicativo para outras áreas de alto uso da Microsoft 365
ms.date: 02/11/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 1936e6a660d77855e53257f40925cf54b05de0de
ms.sourcegitcommit: 5e5d2d3fb621bcbd9d792a5b450f95167ec8548b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63727285"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

> [!NOTE]
> Essa visualização inicial do desenvolvedor destina-se a fornecer aos desenvolvedores Teams aplicativos existentes a chance de experimentar a nova funcionalidade [](/microsoftteams/platform/feedback) e fornecer comentários sobre essa expansão da plataforma de desenvolvedor do Teams para outras áreas de alto uso do ecossistema Microsoft 365.

Você pode testar seus aplicativos Teams em execução no Microsoft Office e no Outlook atualizando seu código para usar [o novo SDK do cliente JavaScript do Microsoft Teams v2 Preview](using-teams-client-sdk-preview.md) e manifesto de visualização do desenvolvedor [Microsoft Teams.](../resources/schema/manifest-schema-dev-preview.md)

Com essa visualização, você pode:

- Estenda as guias Teams [pessoais existentes](/microsoftteams/platform/tabs/how-to/create-personal-tab) para Outlook para área de trabalho e na Web e também Office na Web (office.com).
- Estenda extensões Teams de mensagens [baseadas](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) em pesquisa para Outlook para área de trabalho e na Web.

Para comentários e problemas, continue usando os canais Microsoft Teams [comunidade de desenvolvedores relevantes](/microsoftteams/platform/feedback).

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Teams guias pessoais em Office e Outlook

Com essa visualização, você pode estender um aplicativo de guia Teams pessoal para ser executado Outlook na área Windows desktop e na Web e também Office na Web.

Após o sideload para Teams, sua guia pessoal aparece como um dos aplicativos instalados no Outlook e Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução Outlook, Office e Teams":::

## <a name="teams-messaging-extensions-in-outlook"></a>Teams extensões de mensagens no Outlook

Com essa visualização, você pode estender suas extensões de mensagens baseadas em pesquisa Teams para a área de trabalho Outlook na Web e Windows, permitindo que os clientes pesquisem e compartilhem resultados por meio da área de mensagem de redação do Outlook, além de Microsoft Teams clientes.

Após o sideload para Teams, sua extensão de mensagens aparece como um dos seus aplicativos instalados na área de Outlook de mensagem de composição.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Extensão de mensagens em execução Outlook e Teams":::

## <a name="next-steps"></a>Próximas etapas

Configurar seu ambiente de dev para estender Teams aplicativos em Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
