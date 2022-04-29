---
title: Estender aplicativos do Teams pelo Microsoft 365 (Pré-visualização)
description: Estenda suas experiências de aplicativo do Teams para outras áreas de alto uso do Microsoft 365
ms.date: 02/11/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 66ba17a638fc57b47febef34bea769e39cdea7e3
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111945"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Estender aplicativos do Teams pelo Microsoft 365

> [!NOTE]
> Essa pré-visualização inicial do desenvolvedor destina-se a fornecer aos desenvolvedores do Teams aplicativos existentes a chance de experimentar a nova funcionalidade e [fornecer comentários](/microsoftteams/platform/feedback) sobre essa expansão da plataforma de desenvolvedores do Teams para outras áreas de alto uso do ecossistema Microsoft 365.

Você pode testar seus aplicativos do Teams em execução no Microsoft Office e no Outlook atualizando seu código para usar o novo [SDK do cliente JavaScript do Microsoft Teams v2 Preview](using-teams-client-sdk-preview.md) e o [Manifesto de visualização do Desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) do Microsoft Teams .

Com esta pré-visualização, você pode:

- Estenda as [guias pessoias](/microsoftteams/platform/tabs/how-to/create-personal-tab) existentes do Teams para o Outlook para área de trabalho e na Web e também o Office na Web (office.com).
- Estenda as [extensões de mensagens baseadas em pesquisa existentes](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) do Teams para o Outlook para área de trabalho e na Web.

Para comentários e problemas, continue usando os canais relevantes da [Comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback).

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Guias pessoais do Teams no Office e no Outlook

Com essa visualização, você pode estender um aplicativo de guia pessoal do Teams para ser executado no Outlook na área de trabalho do Windows e na Web e também no Office na Web.

Após o sideload para o Teams, sua guia pessoal aparece como um dos aplicativos instalados no Outlook e no Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Guia pessoal em execução no Outlook, no Office e no Teams":::

## <a name="teams-message-extensions-in-outlook"></a>Extensões de mensagem do Teams no Outlook

Com essa visualização, você pode estender suas extensões de mensagem do Teams baseadas em pesquisa para o Outlook na Web e para a área de trabalho do Windows, permitindo que os clientes pesquisem e compartilhem resultados por meio da área de mensagem de composição do Outlook, além dos clientes do Microsoft Teams.

Após o sideload para o Teams, sua extensão de mensagem aparece como um dos aplicativos instalados na área de mensagem de composição do Outlook.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Extensão de mensagem em execução no Outlook e no Teams":::

## <a name="next-steps"></a>Próximas etapas

Configure seu ambiente de desenvolvimento para estender os aplicativos do Teams pelo Microsoft 365:

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)
