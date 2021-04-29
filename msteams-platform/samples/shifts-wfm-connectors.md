---
title: Conectores de Turnos prontos para produção
description: Conectores de turnos de gerenciamento de força de trabalho para o Teams
ms.topic: reference
author: laujan
ms.date: 03/09/2020
localization_priority: Normal
keywords: Kronos dos conectores do Microsoft Teams
ms.author: lajanuar
ms.openlocfilehash: 459797dd3f8425223c0dcbedc335955bf106ae37
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075735"
---
# <a name="production-ready-shifts-connectors"></a>Conectores de Turnos prontos para produção  

Os conectores de gerenciamento de força de trabalho do Teams Shifts (WFM) são integrações prontas para produção, de código aberto e orientadas pela comunidade, úteis para os funcionários de primeira linha. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de funcionários de primeira linha com Turnos do Teams. 

Cada conector fornece orientações detalhadas para implantação e integração à sua organização. O código-fonte completo está disponível no repositório do GitHub. Você pode explorar em detalhes ou bifurcação e personalizar para atender às suas necessidades específicas.   

Este documento fornece uma visão geral dos principais benefícios dos conectores WFM do Teams Shifts, do conector de Turnos do Kronos para o Teams e do conector de turnos JDA-para-Teams.

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a>Principais benefícios dos conectores WFM do Teams Shifts

A seguir estão os principais benefícios dos conectores WFM do Teams Shifts:

* **Experiência de plug and play:** Todos os conectores WFM shifts incluem ARM scripts de implantação do Azure que permitem hospedar todos os serviços necessários no Microsoft Azure. Nenhuma codificação é necessária para implantar os aplicativos.

* **Código pronto para produção:** Todos os conectores shifts estão em conformidade com as práticas recomendadas de segurança e infraestrutura e todas as alterações enviadas à comunidade são revisadas para garantir a conformidade contínua.

* **Personalizável e extensível:**   Enquanto todos os conectores WFM shifts estão prontos para implantação para uso imediato, com toda a base de códigos e scripts de implantação prontamente disponíveis. Você pode personalizá-los ou estendá-los facilmente para se ajustar às suas necessidades exclusivas.

* **Documentação detalhada & suporte:**   Todos os conectores WFM shifts são acompanhados por documentação de ponta a ponta para as etapas de arquitetura, implantação e configuração da solução. Os repositórios do conector são monitorados, para que você possa relatar quaisquer problemas, desafios ou dificuldades encontrados por meio do rastreador de Problemas do GitHub do repositório.

* **Integração perfeita:** A integração entre soluções WFM e Turnos do Teams permite que os funcionários de primeira linha usem o aplicativo Turnos do Teams para exibir ou gerenciar seus horários de turno e agendamento e usar todos os outros recursos avançados de colaboração fornecidos no Teams desde seu dispositivo móvel ou área de trabalho sem precisar alternar o contexto para outro aplicativo.  

**Exibição de turnos abertos no Teams** 

A exibição de turnos no Teams é mostrada na imagem a seguir: 

![Abrir turnos no Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a>Conector de turnos de Kronos para Teams

Com código de código aberto, você pode integrar a Central de Força de Trabalho kronos versão 8.1 e acima, com turnos do Teams, como, aplicativo do Teams desktop ou móvel para os seguintes cenários de funcionários e gerentes de linha de base:

* Exibir agendamento.

* Publicar e solicitar turnos abertos.

* Troca de turnos.

* Solicitar tempo de folga.

* Ofereça turnos.

Para obter mais informações sobre a implantação do conector de turnos do Kronos-to-Teams, consulte [Get it on GitHub](https://aka.ms/KronosShiftsConnector).

## <a name="jda-to-teams-shifts-connector"></a>Conector de turnos JDA para Teams

Com código de código aberto, você pode integrar o JDA, como BlueYonder Versão 17.2 e acima, com Turnos do Teams, como aplicativo do Teams para área de trabalho ou móvel do Teams, para os seguintes cenários de gerente e trabalho de primeira linha:

* Publicar turnos e agendar grupos no JDA e exibi-los no Teams.

* Habilita cenários de agendamento ricos, incluindo solicitação de trocas de turno e tempo de folga.

* Definir a disponibilidade do usuário usando a [API do Microsoft Graph para Turnos.](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true)

Para obter mais informações sobre contribuição e sugestão, consulte [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</br></br>

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
