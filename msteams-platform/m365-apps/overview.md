---
title: Estender Teams aplicativos em Microsoft 365 (versão prévia)
description: Estenda suas Teams de aplicativo para outras áreas de alto uso Microsoft 365
ms.date: 02/11/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 013bb773897965d51daaa485459eec78478292b3
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104340"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

> [!NOTE]
> Essa versão prévia inicial do desenvolvedor destina-se a fornecer aos desenvolvedores do Teams a chance de experimentar a nova funcionalidade e fornecer comentários [](/microsoftteams/platform/feedback) sobre essa expansão da plataforma de desenvolvedor do Teams para outras áreas de alto uso do ecossistema Microsoft 365.

Você pode testar seus aplicativos Teams em execução no Microsoft Office e no Outlook atualizando seu código para usar [o novo SDK do cliente JavaScript v2 Preview](using-teams-client-sdk-preview.md) e o manifesto de visualização do desenvolvedor do Microsoft Teams Microsoft Teams[.](../resources/schema/manifest-schema-dev-preview.md)

Com esta versão prévia, você pode:

- Estenda as Teams [pessoais existentes](/microsoftteams/platform/tabs/how-to/create-personal-tab) para Outlook área de trabalho e na Web e também Office na Web (office.com).
- Estenda as extensões Teams [de mensagens baseadas em pesquisa existentes](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) Outlook para área de trabalho e na Web.

Para comentários e problemas, continue usando os canais [Microsoft Teams comunidade de desenvolvedores relevantes](/microsoftteams/platform/feedback).

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Teams guias pessoais no Office e Outlook

Com essa versão prévia, você pode estender um aplicativo de guia pessoal Teams para ser executado no Outlook no Windows desktop e na Web e também Office na Web.

Após o sideload para Teams, sua guia pessoal aparece como um dos aplicativos instalados no Outlook e Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia Pessoal em execução Outlook, Office e Teams":::

## <a name="teams-message-extensions-in-outlook"></a>Teams extensões de mensagem no Outlook

Com essa versão prévia, você pode estender suas extensões de mensagem do Teams baseadas em pesquisa para a área de trabalho do Outlook na Web e do Windows, permitindo que os clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além de clientes do Microsoft Teams.

Após o sideload para Teams, sua extensão de mensagem aparece como um dos aplicativos instalados na área de Outlook de redação.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Extensão de mensagem em execução Outlook e Teams":::

## <a name="next-steps"></a>Próximas etapas

Configure seu ambiente de desenvolvimento para estender Teams aplicativos em Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
