---
title: Controles de colaboração
author: surbhigupta
description: Neste módulo, saiba como os controles de colaboração permitem que os criadores criem aplicativos que se integram aos serviços do Microsoft 365, como Planner, Bookings e Outlook.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: fa0cb45921820a61fbfd7112a50f28eb9230fb4b
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373021"
---
# <a name="collaboration-controls"></a>Controles de colaboração

Os controles de Colaboração permitem aplicar o Microsoft 365 e o Microsoft Teams para Aprovações, Arquivos, Reuniões, Anotações e Tarefas para habilitar a colaboração contextual em torno de processos de negócios. Esses controles permitem que você crie experiências colaborativas personalizadas que podem ser exibidas no Teams. As soluções que compõem controles de Colaboração permitem que os criadores criem aplicativos que se integram aos serviços do Microsoft 365, como Planner, Bookings, Outlook e SharePoint, de maneira pouco codificada.

Esses controles dão a você o poder de simplificar a colaboração de fluxo de trabalho dos usuários criando aplicativos de linha de negócios e trabalhando sem alternar o contexto de aplicativo para aplicativo com o seguinte

* Aprovações
* Arquivos
* Reuniões
* Notas
* Tarefas

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

A seguir estão alguns dos principais recursos dos controles de colaboração:

* **Microsoft Planner tarefas:** crie tarefas e atribua-as a membros de um registro para que eles possam exibir uma lista consolidada de tarefas no aplicativo controlado por modelos e aplicativos de tarefas no Microsoft Teams.

* **Tarefas do Dataverse:** Crie tarefas que podem ser atribuídas a usuários externos à sua organização.

* **Observações do Dataverse:** Crie anotações atribuídas a um registro em seu aplicativo.

* **Reuniões do Outlook:** Agende reuniões com clientes e funcionários internos e conecte-se perfeitamente com outras pessoas com o Microsoft Teams com uma seleção de um botão.

* **Arquivos do SharePoint:** Compartilhe arquivos com membros de um registro para que você possa pesquisar, referenciar e editar artefatos relevantes em um local centralizado apoiado pelo SharePoint.

* **Aprovações:** Simplifique as solicitações em sua equipe.

> [!NOTE]
> Ao configurar e usar os vários recursos do Microsoft 365 de controles de Colaboração mencionados anteriormente, você está concedendo permissão para que os dados do usuário passem pelo API do Graph e aceitando os termos de uso da [API da Microsoft](/legal/microsoft-apis/terms-of-use?context=graph%2Fcontext). Para obter mais informações, consulte [o Microsoft Graph](/graph/overview).

## <a name="how-collaboration-controls-works"></a>Como os controles de colaboração funcionam

Os controles são executados em um MDA (Aplicativo Controlado por Modelo) do Power Apps que pode ser implantado no Microsoft Teams. O MDA é executado no Microsoft Dataverse e pode ser integrado a um modelo de dados personalizado. Os controles se integram com o Microsoft Graph para tarefas do Planner, calendários do Outlook e do Teams e arquivos do SharePoint. Os controles de Colaboração não se integram diretamente a fontes externas, como um sistema de registro ou um portal.

* Os dados podem ser adicionados ao Dataverse de fontes externas por meio de APIs OData padrão.

* Os dados podem ser lidos do Dataverse por meio de APIs OData padrão e enviados a fontes externas, como um sistema de registro ou um portal.

:::image type="content" source="~/assets/images/collaboration-control/consumption-mda.png" alt-text="Ciclo de vida da colaboração":::
