---
title: Conectores de Turnos prontos para produção
description: Saiba mais sobre os benefícios de usar conectores de turnos de gerenciamento de força de trabalho para Teams, como o conector De Turnos de Kronos para Teams e o conector de Turnos do JDA para Teams Shifts
ms.topic: reference
author: surbhigupta
ms.date: 03/09/2020
ms.localizationpriority: medium
keywords: Microsoft Teams conectores kronos
ms.author: lajanuar
ms.openlocfilehash: 84e16f26dbe8597089e601e0d7eadca12a4a4446
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453100"
---
# <a name="production-ready-shifts-connectors"></a>Conectores de Turnos prontos para produção  

Teams conectores de gerenciamento de força de trabalho (WFM) são integrações prontas para produção, de código aberto e orientadas pela comunidade, úteis para os funcionários de primeira linha. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de trabalhadores de primeira linha com Teams Turnos.

Cada conector fornece orientações detalhadas para implantação e integração à sua organização. O código-fonte completo está disponível GitHub repositório. Você pode explorar em detalhes ou bifurcação e personalizar para atender às suas necessidades específicas.

Este documento fornece uma visão geral dos principais benefícios dos conectores WFM do Teams Shifts, do Conector de Turnos de Kronos para Teams e do conector de Turnos do JDA para Teams Shifts.

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a>Principais benefícios dos conectores WFM Teams shifts

A seguir estão os principais benefícios dos conectores WFM Teams Shifts:

* **Experiência de plug and play:** Todos os conectores WFM shifts incluem ARM scripts de implantação do Azure que permitem hospedar todos os serviços necessários no Microsoft Azure. Nenhuma codificação é necessária para implantar os aplicativos.

* **Código pronto para produção:** Todos os conectores shifts estão em conformidade com as práticas recomendadas de segurança e infraestrutura e todas as alterações enviadas à comunidade são revisadas para garantir a conformidade contínua.

* **Personalizável e extensível:** Enquanto todos os conectores WFM shifts estão prontos para implantação para uso imediato, com toda a base de códigos e scripts de implantação prontamente disponíveis. Você pode personalizá-los ou estendá-los facilmente para se ajustar às suas necessidades exclusivas.

* **Documentação detalhada & suporte:** Todos os conectores WFM shifts são acompanhados por documentação de ponta a ponta para as etapas de arquitetura, implantação e configuração da solução. Os repositórios do conector são monitorados, para que você possa relatar quaisquer problemas, desafios ou dificuldades encontrados por meio do rastreador de GitHub problemas do repositório.

* **Integração perfeita:** A integração entre soluções WFM e turnos Teams permite que os funcionários de primeira linha usem o aplicativo shifts do Teams para exibir ou gerenciar seus horários e horários de turno e usar todos os outros recursos avançados de colaboração fornecidos no Teams desde seu dispositivo móvel ou desktop sem precisar alternar o contexto para outro aplicativo.  

Exibição de turnos abertos Teams:

A exibição de turnos no Teams é mostrada na imagem a seguir:

![Abrir turnos em Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a>Conector kronos-to-Teams shifts

Com código de código aberto, você pode integrar a Central de Força de Trabalho kronos versão 8.1 e acima, com turnos do Teams, como, aplicativo de Teams desktop ou móvel para os seguintes cenários de gerente e trabalho de primeira linha:

* Exibir agendamento.

* Publicar e solicitar turnos abertos.

* Troca de turnos.

* Solicitar tempo de folga.

* Ofereça turnos.

Para obter mais informações sobre a implantação do conector De turnos Teams Kronos, consulte [Get it on GitHub](https://aka.ms/KronosShiftsConnector).

## <a name="jda-to-teams-shifts-connector"></a>Conector de turnos de JDA para Teams

Com código de código aberto, você pode integrar o JDA, como BlueYonder Versão 17.2 e superior, com turnos do Teams, como aplicativo de Teams para os seguintes cenários de gerente e de trabalho de primeira linha:

* Publicar turnos e agendar grupos no JDA e exibi-los Teams.

* Habilita cenários de agendamento ricos, incluindo solicitação de trocas de turno e tempo de folga.

* Definir a disponibilidade do usuário [usando a API Graph Microsoft para Turnos](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).

Para obter mais informações sobre contribuição e sugestão, consulte [Get it on GitHub](https://aka.ms/JDAShiftsConnector).

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
