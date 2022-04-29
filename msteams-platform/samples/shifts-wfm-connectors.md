---
title: Conectores de Turnos prontos para produção
description: Saiba mais sobre os benefícios de usar conectores de Turnos de gerenciamento de Mão de Obra para o Teams, como o conector Kronos-to-Teams Shifts e o conector de Turnos JDA para Teams
ms.topic: reference
author: surbhigupta
ms.date: 03/09/2020
ms.localizationpriority: high
keywords: Conectores Kronos do Microsoft Teams
ms.author: lajanuar
ms.openlocfilehash: 3a294d20bc2032df7ef5dfa225922e9dccabf1df
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111763"
---
# <a name="production-ready-shifts-connectors"></a>Conectores de Turnos prontos para produção  

Os conectores de WFM (gerenciamento de mão de obra) são integrações prontas para produção, de software livre e controladas pela comunidade, úteis para trabalhadores de primeira linha. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de trabalhadores de linha de frente com o Teams Shifts.

Cada conector fornece diretrizes detalhadas para implantação e integração à sua organização. O código-fonte completo está disponível no repositório GitHub. Você pode explorar detalhadamente ou bifurcar e personalizar para atender às suas necessidades específicas.

Este documento fornece uma visão geral dos principais benefícios dos conectores WFM do Teams Shifts, do Conector de Turnos Kronos para Teams e do conector de Turnos JDA para o Teams.

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a>Principais benefícios dos conectores WFM do Teams Shifts

A seguir estão os principais benefícios dos conectores WFM do Teams Shifts:

* **Experiência simples**: todos os conectores de Turnos de WFM incluem scripts de implantação do ARM Azure que permitem hospedar todos os serviços necessários no Microsoft Azure. Nenhuma codificação é necessária para implantar os aplicativos.

* **código pronto para produção**: todos os conectores de Turnos estão em conformidade com as práticas recomendadas de segurança e infraestrutura e todas as alterações enviadas pela comunidade são revisadas para garantir a conformidade contínua.

* **Personalizável e extensível:** embora todos os conectores de Turnos para WFM estejam prontos para implantação para uso imediato, com toda a base de código e scripts de implantação prontamente disponíveis. Você pode personalizá-los ou estendê-los facilmente para atender às suas necessidades exclusivas.

* **Documentação detalhada:** todos os modelos de aplicativo são acompanhados pela documentação de ponta a ponta sobre as etapas de arquitetura, implantação e configuração da solução. Os repositórios de conectores são monitorados, para que você possa relatar problemas, desafios ou dificuldades encontrados por meio do rastreador de Problemas do repositório GitHub. 

* **Integração perfeita:** a integração entre as soluções de WFM e o Teams Shifts permite que os funcionários de primeira linha usem o aplicativo Teams Shifts para exibir ou gerenciar suas agendas e horários de turnos e usar todos os outros recursos avançados de colaboração fornecidos no Teams diretamente de seu dispositivo móvel ou área de trabalho sem precisar alternar o contexto para outro aplicativo.  

Abrir o modo de exibição de turnos no Teams:

O modo de exibição turnos no Teams é mostrado na imagem a seguir:

![Turnos abertos no Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a>Conector de Shifts Kronos para o Teams

Com o código de software livre, você pode integrar o Kronos Workforce Central versão 8.1 e superior, como  Teams Shifts, como aplicativos de área de trabalho ou móveis do Teams para os seguintes cenários de gerente e trabalho de primeira linha:

* Exibir agenda.

* Publicar e solicitar turnos abertos.

* Trocar turnos.

* Solicitar folga.

* Oferecer turnos.

Para obter mais informações sobre a implantação do conector de Turnos Kronos para Teams, consulte [Obter no GitHub](https://aka.ms/KronosShiftsConnector).

## <a name="jda-to-teams-shifts-connector"></a>Conector de Turnos JDA para o Teams

Com o código de software livre, você pode integrar o JDA, como o BlueYonder versão 17.2 e superior, com o Teams Shifts, como o aplicativo Teams para área de trabalho ou móvel, para os seguintes cenários de gerente e trabalho de primeira linha:

* Publique turnos e agende grupos no JDA e exiba-os no Teams.

* Habilite cenários de agendamento avançados, incluindo solicitação de trocas de turno e folga.

* Defina a disponibilidade do usuário usando a [ API do Microsoft Graph para Turnos](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).

Para obter mais informações sobre contribuição e sugestão, consulte [Obter no GitHub](https://aka.ms/JDAShiftsConnector).

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
