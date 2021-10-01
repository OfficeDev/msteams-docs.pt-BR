---
title: Integrar aplicativos Web
author: Rajeshwari-v
description: Uma visão geral da integração de aplicativos Web e recursos de dispositivo com Microsoft Teams aplicativo.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: 7d4056a23f126d636de3920d02a316440e51564e
ms.sourcegitcommit: 329447310013a2672216793dab79145b24ef2cd2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2021
ms.locfileid: "60017307"
---
# <a name="integrate-web-apps"></a>Integrar aplicativos Web

Você pode fornecer uma experiência de usuário enriquecida integrando os recursos de um aplicativo Web existente Microsoft Teams plataforma. Certifique-se [de seguir Teams de design](~/concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo Teams.
Este documento fornece uma visão geral dos pré-requisitos para integrar aplicativos Web com o Teams, plataforma Power para criar aplicativos do Power, Power Virtual Agents, Assistente Virtual, modelos de aplicativo, conectores de turno, LMS Moodle, criação de um botão Share-to-Teams para seu site, adicionando uma guia Microsoft Teams no SharePoint, criando links profundos e integrando recursos de dispositivo.

## <a name="prerequisites"></a>Pré-requisitos   

Para uma integração eficaz, certifique-se de ter uma melhor compreensão dos seguintes pré-requisitos:
* Teams recursos. 
* SharePoint requisitos para armazenamento de arquivos e dados.
* Requisitos de API.
* Autenticação.
* Vinculação profunda do seu aplicativo com Teams.
* Mapeie os casos de uso do aplicativo para Teams da plataforma.
* Determine os pontos de entrada do aplicativo, como uso pessoal, colaboração ou ambos.

## <a name="low-code-platforms"></a>Plataformas de código baixo

As plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software e exigem pouca ou nenhuma codificação para criar aplicativos e processos. Você pode criar aplicativos personalizados facilmente com plataformas de código baixo. Essas plataformas consistem em uma interface visual, conectores para serviços back-end e um sistema de gerenciamento de ciclo de vida de aplicativos integrado para criar, depurar, implantar e manter aplicativos. A Microsoft fornece os seguintes gateways inovadores para criar rapidamente aplicativos compatíveis Teams usando atributos de código baixos:
* Plataforma Microsoft Power
* Microsoft Teams de aplicativos

## <a name="microsoft-power-platform"></a>Plataforma Microsoft Power

A plataforma Microsoft Power combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate e Power Virtual Agents em uma plataforma de aplicativos poderosa. Essas tecnologias capacitam você a criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado.

### <a name="power-apps"></a>Power Apps

Com Power Apps, você pode criar aplicativos de negócios que se conectam aos seus dados de negócios e são adaptados às necessidades da sua organização. Power Apps uma ampla variedade de cenários de aplicativos para resolver desafios de negócios por meio de aplicativos de tela. Depois de criar o aplicativo, você pode exportá-lo do portal do criador Power Apps e incorporar no Microsoft Teams.

### <a name="power-virtual-agents"></a>Agentes virtuais do Power

O Power Virtual Agent é uma solução de interface gráfica sem código e guiada. Ele é criado na Plataforma do Microsoft Power e na Estrutura de Bots. Ele permite que todos os membros da sua equipe criem e mantenham chatbots de conversação ricos que se integram facilmente à plataforma Teams. Você pode projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.

### <a name="create-virtual-assistant"></a>Criar um Assistente Virtual

Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários. 

## <a name="app-templates"></a>Modelos de aplicativo

Você pode usar o modelo de aplicativo para criar aplicativos personalizados feitos para atender às suas necessidades organizacionais. Esses são aplicativos prontos para produção para Microsoft Teams que são orientados pela comunidade, de código aberto e disponíveis no GitHub. Cada modelo contém instruções detalhadas para implantar e instalar o aplicativo para sua organização. Ele fornece um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente. 

## <a name="teams-shifts-work-force-management-connectors"></a>Teams Desloca conectores de Gerenciamento de Força de Trabalho

Teams Os conectores de Gerenciamento de Força de Trabalho de Turnos são integrações prontas para produção, de código aberto e orientadas pela comunidade. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de trabalhadores de primeira linha com Teams Turnos.

## <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Moodle é um sistema de gerenciamento de Learning (LMS) popular. Ele agora está integrado ao Microsoft Teams. Essa integração ajuda educadores e professores a colaborarem em torno de cursos de miojo, fazer perguntas sobre notas e atribuições e manter-se atualizados com notificações diretamente no Teams.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Criar um botão Compartilhar no Teams para o seu site

Sites de terceiros podem usar o script do launcher para incorporar o Share Teams botões em suas páginas da Web. Quando você seleciona o botão, ele inicia a experiência Compartilhar para Teams em uma janela pop-up. Isso permite compartilhar um link diretamente com qualquer pessoa ou canal Microsoft Teams sem alternar o contexto.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Adicione uma Microsoft Teams de SharePoint

Você pode obter uma experiência de integração rica entre Microsoft Teams e SharePoint adicionando uma guia Microsoft Teams no SharePoint como uma web part SPFx web part. 

## <a name="create-deep-link"></a>Criar link profundo

Você pode criar links profundos para as entidades Teams. Você pode criar links para informações e recursos dentro Teams. Esses links profundos navegam para conteúdo e informações em sua guia. Você pode usar links profundos para vincular seu aplicativo com Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência mais Teams nativa.

## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivo

Microsoft Teams plataforma está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte. A plataforma de Teams aprimorada permite que os parceiros acessem e integrem os recursos de dispositivo nativo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local usando APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams. 

## <a name="integrate-people-picker"></a>Integrar o Seletor de Pessoas

Você pode integrar o controle Teams seletor de pessoas nativas que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.

## <a name="integrate-teams-in-your-external-app"></a>Integrar Teams em seu aplicativo externo
Você pode incorporar suas próprias experiências em Microsoft Teams criando Teams aplicativos. Se você quiser  reverter esse modelo e integrar Teams ou outros recursos de comunicação à sua própria experiência de aplicativo externo, consulte Serviços de Comunicação do [Azure](/azure/communication-services/overview). Os Serviços de Comunicação do Azure são serviços baseados em nuvem com APIs REST e SDKs da biblioteca de clientes para ajudá-lo a integrar a comunicação aos seus próprios aplicativos personalizados. Você pode incorporar componentes Web genéricos ou Teams com estilo React para chamar e conversar com a ajuda da biblioteca [da interface do usuário.](https://azure.github.io/communication-ui-library/)

Os aplicativos dos Serviços de Comunicação do Azure podem usar a funcionalidade de visualização pública para [interoperar](/azure/communication-services/concepts/teams-interop) com o Teams e permitir que seu aplicativo personalizado participe Teams reuniões anonimamente. Por exemplo, você pode integrar a chamada de vídeo a um aplicativo bancário móvel e permitir que os usuários finais se encontrem virtualmente com funcionários do banco usando Microsoft Teams. 

Você também pode integrar Microsoft 365 identidade para criar aplicativos externos que incorporam vídeo e chamada PSTN em nome de um Teams usuário. Se você já usou [Skype for Business SDKs](/skype-sdk/appsdk/skypeappsdk) no passado, esses recursos como parte dos Serviços de Comunicação do Azure são recomendados como uma substituição.

## <a name="see-also"></a>Confira também

* [Mapear os casos de uso do aplicativo para Teams plataforma](~/concepts/design/map-use-cases.md)
* [Determinar os pontos de entrada do aplicativo](~/concepts/extensibility-points.md)
* [Integrar aplicativos Web](~/samples/integrating-web-apps.md)
* [Criar aplicativos personalizados de baixo código para Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Adicionar um chatbot de agentes virtuais de energia](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Criar assistente virtual](~/samples/virtual-assistant.md)
* [Modelos de aplicativos para o Teams](~/samples/app-templates.md)
* [Conectores de Turno prontos para produção](~/samples/shifts-wfm-connectors.md)
* [Instalar o Moodle LMS](~/resources/moodleinstructions.md)
* [Criar um botão compartilhar para o Teams](~/concepts/build-and-test/share-to-teams.md)
* [Adicionar uma guia do Teams ao SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Criar links detalhados](~/concepts/build-and-test/deep-links.md)
* [Funcionalidades de dispositivo](~/concepts/device-capabilities/device-capabilities-overview.md)
* [controle do se picker de pessoas](~/concepts/device-capabilities/people-picker-capability.md)
