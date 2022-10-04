---
title: Instalar os Controles de colaboração
author: surbhigupta
description: Neste módulo, saiba como instalar controles de colaboração com aplicativos de energia e Microsoft 365 E3 e como instalar soluções de controles de colaboração.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 5a253c9e7373a2df9e1161e6d3fc9d9b1c8ccdaa
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373028"
---
# <a name="install-collaboration-controls"></a>Instalar os Controles de colaboração

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na versão [prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

Neste artigo, você aprenderá a instalar controles de colaboração. O seguinte é necessário para criar e implantar aplicativos Collaboration Manager usando os controles de colaboração:

* **Aplicativos de energia**: para criar e executar aplicativos controlados por modelos usando os controles de Colaboração.
* **M365 E3 ou superior**: para implantar aplicativos personalizados no Microsoft Teams e armazenar tarefas no Planner, arquivos no SharePoint e reuniões no Outlook.

Para instalar os componentes em um ambiente do Power Platform, as seguintes funções são necessárias:

* Personalizador de sistema
* Criador de ambiente

Para obter mais informações sobre privilégios de função, consulte [Configurar a segurança do usuário em um ambiente](/power-platform/admin/database-security#predefined-security-roles)

## <a name="install-the-collaboration-controls-solutions"></a>Instalar as soluções de controles de colaboração

Você instalará os controles de colaboração em seu ambiente do dataverse por meio [do Microsoft AppSource.](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1)

Você poderá configurar e usar os componentes em seu próprio aplicativo controlado por modelo somente depois de navegar até o [Microsoft AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1)  e instalar controles de Colaboração em seu ambiente de dataverse.

Os Controles de Colaboração incluem as seguintes soluções:

|**Soluções de configurações** | **Objetivo** |
|---|---|
| Configurações de controles de colaboração | Manter a infraestrutura de configurações que capacita os controles de colaboração |
| Objetos de configurações de controles de colaboração | Fornece valores de configurações predefinido que são usados pelos controles de Colaboração.|

|**Soluções de colaboração** | **Objetivo** |
|---|---|
| Tarefas de controles de colaboração  | Inclui o controle PCF de tarefas (estrutura de componentes do Power Apps). |
| Eventos de controles de colaboração | Inclui o controle PCF de eventos para reuniões do Outlook e do Teams e compromissos de reservas. |
| Observações de controles de colaboração | Inclui o controle PCF de anotações, que armazena anotações no Dataverse. |
| Arquivos de controles de colaboração | Inclui o controle PCF de arquivos para acessar arquivos no SharePoint. |
| Núcleo de controles de colaboração |Inclui APIs de Colaboração personalizadas, o modelo de dados de colaboração e tabelas virtuais para eventos, arquivos e controles de tarefa. |
| Aprovações de controles de colaboração | Inclui o novo controle PCF de Aprovações. |
| Conector de controles de colaboração | Inclui o novo conector do Power Automate de Colaboração |

> [!NOTE]
> Se você tiver uma versão existente dos controles instalados em seu ambiente, talvez seja necessário criar um ambiente novo e concluir uma nova instalação para atualizar com êxito para a versão mais recente.

Antes da instalação, você deve estar em um ambiente do Power Platform ou em um locatário de administração. Você precisará de um ambiente de dataverse com um banco de dados. Se você não tiver um, [precisará criar um](/power-platform/admin/create-environment) novo para continuar com a instalação.

Para instalar as soluções, navegue [até o Microsoft AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1) e conclua as seguintes etapas:

1. Selecione **o botão Obter** agora.

   :::image type="content" source="../assets/images/collaboration-control/preview-form.png" alt-text="Captura de tela do botão Obter agora para mostrar o controle colaboração."border="true":::

1. Entre com sua conta, preencha o formulário e selecione **Continuar**.

   :::image type="content" source="../assets/images/collaboration-control/overview.png" alt-text="Captura de tela do controle de colaboração de visão geral." border="true":::

   :::image type="content" source="../assets/images/collaboration-control/collaboration-controls-preview.png" alt-text="Captura de tela da visualização do controle de colaboração de instalação." border="true":::

1. Você será direcionado para o Power Platform Administração Center. Selecione um ambiente no menu suspenso e concorde com os termos e as instruções de política.

   > [!TIP]
   > Se você vir um erro de permissões ao selecionar o ambiente, tente selecionar fora do menu suspenso do ambiente para ver se isso resolve o problema.

   :::image type="content" source="../assets/images/collaboration-control/install-environment.png" alt-text="Captura de tela é um exemplo de instalação do ambiente de controle de colaboração." border="true":::

1. Selecione **Instalar**, a instalação pode levar aproximadamente 15 minutos para ser concluída.

1. Acesse , [https://make.powerapps.com/](https://make.powerapps.com/)também [https://make.preview.powerapps.com/](https://make.preview.powerapps.com/) há suporte se você estiver inscrito na versão prévia do Power Apps.

1. Verifique se você está no ambiente em que os controles estão instalados, pois você pode exibir o ambiente e alterá-lo, se necessário, no canto superior direito do portal do Power Apps.

1. Selecione a **guia** Soluções para exibir todas as soluções que você instalou no ambiente certo.

   :::image type="content" source="../assets/images/collaboration-control/solutions.png" alt-text="Captura de tela que mostra a guia Soluções para exibir o controle de colaboração de todas as soluções." border= "true":::

> [!NOTE]
> Os controles de colaboração são versão prévia e os elementos podem mudar ao longo do tempo com potencial para alterações interruptivas. Os controles de colaboração não têm suporte em ambientes de produção.

Após a instalação bem-sucedida de todas as soluções de Colaboração em seu ambiente, você poderá criar um novo aplicativo baseado em modelo que pode aproveitar os recursos de controle de colaboração.
