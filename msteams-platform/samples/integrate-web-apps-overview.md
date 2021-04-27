---
title: Integrar aplicativos Web
author: Rajeshwari-v
description: Uma visão geral da integração de aplicativos Web e recursos de dispositivo com o aplicativo Microsoft Teams.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 6493f493b2bfc67a23aebfb5142aff60cf0afe93
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020236"
---
# <a name="integrate-web-apps"></a>Integrar aplicativos Web

Você pode fornecer uma experiência de usuário enriquecida integrando os recursos de um aplicativo Web existente na plataforma do Microsoft Teams. Certifique-se de [seguir as diretrizes de design do Teams](~/concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo ao Teams.
Este documento fornece uma visão geral dos pré-requisitos para integrar aplicativos Web com o Teams, plataforma Power para criar aplicativos do Power, Agentes Virtuais do Power, Assistente Virtual, modelos de aplicativo, conectores de turno, LMS Moodle, criação de um botão Share-to-Teams para seu site, a adição de uma guia do Microsoft Teams no SharePoint, a criação de links profundos e a integração de recursos do dispositivo.

## <a name="prerequisites"></a>Pré-requisitos   

Para uma integração eficaz, certifique-se de ter uma melhor compreensão dos seguintes pré-requisitos:
* Recursos do Teams. 
* Requisitos do SharePoint para armazenamento de arquivos e dados.
* Requisitos de API.
* Autenticação.
* Vinculação profunda do seu aplicativo com o Teams.
* Mapeie os casos de uso do aplicativo para os recursos da plataforma teams.
* Determine os pontos de entrada do aplicativo, como uso pessoal, colaboração ou ambos.

## <a name="low-code-platforms"></a>Plataformas de código baixo

As plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software e exigem pouca ou nenhuma codificação para criar aplicativos e processos. Você pode criar aplicativos personalizados facilmente com plataformas de código baixo. Essas plataformas consistem em uma interface visual, conectores para serviços back-end e um sistema de gerenciamento de ciclo de vida de aplicativos integrado para criar, depurar, implantar e manter aplicativos. A Microsoft fornece os seguintes gateways inovadores para criar rapidamente aplicativos compatíveis com o Teams usando atributos de código baixos:
* Plataforma Microsoft Power
* Modelos de aplicativo do Microsoft Teams

## <a name="microsoft-power-platform"></a>Plataforma Microsoft Power

A plataforma Microsoft Power combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate e Agentes Virtuais do Power em uma plataforma de aplicativo poderosa. Essas tecnologias capacitam você a criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado.

### <a name="power-apps"></a>Power Apps

Com o Power Apps, você pode criar aplicativos de negócios que se conectam aos dados da sua empresa e são adaptados às necessidades da sua organização. Os Aplicativos Do Power permitem uma ampla variedade de cenários de aplicativos para resolver desafios de negócios por meio de aplicativos de tela. Depois de criar o aplicativo, você pode exportá-lo do portal do criador do Power Apps e incorporar no Microsoft Teams.

### <a name="power-virtual-agents"></a>Agentes virtuais do Power

O Power Virtual Agent é uma solução de interface gráfica sem código e guiada. Ele é criado na Plataforma do Microsoft Power e na Estrutura de Bots. Ele capacita todos os membros da sua equipe a criar e manter chatbots de conversação ricos que se integram facilmente à plataforma do Teams. Você pode projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.

### <a name="create-virtual-assistant"></a>Criar Assistente Virtual

O Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários. 

## <a name="app-templates"></a>Modelos de aplicativo

Você pode usar o modelo de aplicativo para criar aplicativos personalizados feitos para atender às suas necessidades organizacionais. Esses são aplicativos prontos para produção para o Microsoft Teams que são orientados pela comunidade, de código aberto e disponíveis no GitHub. Cada modelo contém instruções detalhadas para implantar e instalar o aplicativo para sua organização. Ele fornece um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente. 

## <a name="teams-shifts-work-force-management-connectors"></a>Teams Shifts Work Force Management connectors

Os conectores de Gerenciamento de Força de Trabalho de Turnos do Teams são integrações prontas para produção, de código aberto e orientadas pela comunidade. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de funcionários de primeira linha com Turnos do Teams.

## <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Moodle é um LMS (Sistema de Gerenciamento de Aprendizagem) de código aberto popular. Agora, ele está integrado ao Microsoft Teams. Essa integração ajuda educadores e professores a colaborarem em torno de cursos de miojo, fazer perguntas sobre notas e atribuições e manter-se atualizados com notificações diretamente no Teams.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Criar um botão Compartilhar no Teams para o seu site

Sites de terceiros podem usar o script do launcher para incorporar os botões Compartilhar ao Teams em suas páginas da Web. Quando você seleciona o botão, ele inicia a experiência Compartilhar para o Teams em uma janela pop-up. Isso permite compartilhar um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar o contexto.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Adicionar uma guia do Microsoft Teams no SharePoint

Você pode obter uma experiência de integração rica entre o Microsoft Teams e o SharePoint adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx. 

## <a name="create-deep-link"></a>Criar link profundo

Você pode criar links profundos para as entidades no Teams. Você pode criar links para informações e recursos no Teams. Esses links profundos navegam para conteúdo e informações em sua guia. Você pode usar links profundos para vincular seu aplicativo com o Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência do Teams mais nativa.

## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivo

A plataforma do Microsoft Teams está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte. A plataforma do Teams aprimorada permite que os parceiros acessem e integrem os recursos de dispositivo nativo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local usando APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams. 

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Mapear os casos de uso do aplicativo para os recursos da plataforma Teams](~/concepts/design/map-use-cases.md)

> [!div class="nextstepaction"]
> [Determinar os pontos de entrada do aplicativo](~/concepts/extensibility-points.md)

> [!div class="nextstepaction"]
> [Integrar aplicativos Web](~/samples/integrating-web-apps.md)

> [!div class="nextstepaction"]
> [Criar aplicativos personalizados de baixo código para o Microsoft Teams](~/samples/teams-low-code-solutions.md)

> [!div class="nextstepaction"]
> [Adicionar um chatbot de agentes virtuais de energia](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)

> [!div class="nextstepaction"]
> [Criar assistente virtual](~/samples/virtual-assistant.md)

> [!div class="nextstepaction"]
> [Modelos de aplicativos para o Teams](~/samples/app-templates.md)

> [!div class="nextstepaction"]
> [Conectores de Turno prontos para produção](~/samples/shifts-wfm-connectors.md)

> [!div class="nextstepaction"]
> [Instalar o Moodle LMS](~/resources/moodleinstructions.md)

> [!div class="nextstepaction"]
> [Criar um botão compartilhar para o Teams](~/concepts/build-and-test/share-to-teams.md)

> [!div class="nextstepaction"]
> [Adicionar uma guia do Teams ao SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)

> [!div class="nextstepaction"]
> [Criar links detalhados](~/concepts/build-and-test/deep-links.md)

> [!div class="nextstepaction"]
> [Funcionalidades de dispositivo](~/concepts/device-capabilities/device-capabilities-overview.md)
