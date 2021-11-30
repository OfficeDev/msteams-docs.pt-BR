---
title: Estender Teams aplicativos em Microsoft 365 (visualização)
description: Estender suas Teams de aplicativo para outras áreas de alto uso de Microsoft 365
ms.date: 11/15/2021
ms.topic: overview
ms.openlocfilehash: 97bbec718d2bff33cfca99bf2cedaae9533fbd92
ms.sourcegitcommit: 660273bc6833ab84ba7550e6b374ea6e3780459d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61233502"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender Teams aplicativos em Microsoft 365

> [!NOTE]
> Essa visualização inicial do desenvolvedor destina-se a fornecer aos desenvolvedores Teams [](/microsoftteams/platform/feedback) aplicativos existentes a chance de experimentar a nova funcionalidade e fornecer comentários sobre essa expansão da plataforma de desenvolvedor do Teams para outras áreas de alto uso do ecossistema Microsoft 365.

Você pode testar seus aplicativos Teams em execução no Microsoft Office e no Outlook atualizando seu código para usar o novo SDK do cliente [javaScript do Microsoft Teams v2 Preview](using-teams-client-sdk-preview.md) e manifesto de visualização do desenvolvedor Microsoft Teams [.](../resources/schema/manifest-schema-dev-preview.md)

Com essa visualização, você pode:

- Estenda as guias Teams [pessoais existentes](/microsoftteams/platform/tabs/how-to/create-personal-tab) para Outlook para área de trabalho e na Web e também Microsoft Office Home (office.com).
- Estenda as extensões Teams de mensagens baseadas em pesquisa [existentes](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) Outlook para área de trabalho e na Web.

Para comentários e problemas, continue usando os canais Microsoft Teams [comunidade de desenvolvedores relevantes.](/microsoftteams/platform/feedback)

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Teams guias pessoais em Office e Outlook

Com essa visualização, você pode estender um aplicativo de guia pessoal Teams para ser executado no Outlook no Windows desktop e na Web e também Microsoft Office Home (office.com).

Após o sideload para Teams, sua guia pessoal aparece como um dos aplicativos instalados no Outlook e Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução no outlook.com":::

## <a name="teams-messaging-extensions-in-outlook"></a>Teams extensões de mensagens no Outlook

Com essa visualização, você pode estender suas extensões de mensagens baseadas em pesquisa Teams para a área de trabalho Outlook na Web e Windows, permitindo que os clientes pesquisem e compartilhem resultados por meio da área de mensagem de redação do Outlook, além de Microsoft Teams clientes.

Depois de fazer sideload para Teams, sua extensão de mensagens aparece como um dos aplicativos instalados na área de Outlook de mensagem de composição.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução no outlook.com":::

## <a name="next-step"></a>Próxima etapa

Configurar seu ambiente de dev para estender Teams aplicativos em Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
