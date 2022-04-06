---
title: Integrar aplicativos Web
author: Rajeshwari-v
description: Uma visão geral da integração de aplicativos Web e recursos de dispositivo com Microsoft Teams aplicativo.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
keywords: power platform power apps people picker deep link virtual agent assistant share-to-Teams
ms.openlocfilehash: 8fe6b41f129497d439d9cf5ef391c800d6ddea0e
ms.sourcegitcommit: f892125106adb6731a20127f15d6e92f279127c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64685587"
---
# <a name="integrate-web-apps"></a>Integrar aplicativos Web

Você pode fornecer uma experiência de usuário enriquecida integrando os recursos de um aplicativo Web existente Microsoft Teams plataforma. Siga as [diretrizes Teams design para](~/concepts/design/understand-use-cases.md) tornar seu aplicativo nativo Teams.
Este documento fornece uma visão geral dos pré-requisitos para integrar aplicativos Web ao Teams, Power Platform para criar aplicativos Power, Power Virtual Agents, Assistente Virtual, modelos de aplicativo, conectores Shift, Moodle LMS, criando um botão Compartilhar para Teams para seu site, adicionando um Microsoft Teams  na guia SharePoint, criando links profundos e integrando recursos de dispositivo.

## <a name="prerequisites"></a>Pré-requisitos

Para uma integração eficaz, certifique-se de ter uma melhor compreensão dos seguintes pré-requisitos:

* Teams recursos.
* SharePoint requisitos para armazenamento de arquivos e dados.
* Requisitos de API.
* Autenticação.
* Vinculação profunda de seu aplicativo com Teams.
* Mapeie os casos de uso do aplicativo para Teams da plataforma.
* Determine os pontos de entrada do aplicativo, como uso pessoal, colaboração ou ambos.

## <a name="low-code-platforms"></a>Plataformas de baixo código

As plataformas de baixo código fornecem uma abordagem intuitiva para o desenvolvimento de software e exigem pouca ou nenhuma codificação para criar aplicativos e processos. Você pode criar aplicativos personalizados facilmente com plataformas de baixo código. Essas plataformas consistem em uma interface visual, conectores para serviços de back-end e um sistema de gerenciamento de ciclo de vida de aplicativo interno para criar, depurar, implantar e manter aplicativos. A Microsoft fornece os seguintes gateways inovadores para criar rapidamente aplicativos compatíveis com Teams usando atributos de código baixo:

* Plataforma Microsoft Power
* Microsoft Teams de aplicativo

## <a name="microsoft-power-platform"></a>Plataforma Microsoft Power

A plataforma Microsoft Power combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate e Power Virtual Agents em uma plataforma de aplicativo avançada. Essas tecnologias capacitam você a criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado.

>[!NOTE]
>Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na Teams de aplicativos. Os aplicativos do Microsoft Power Platform podem ser publicados somente na loja de aplicativos de uma organização.

### <a name="power-apps"></a>Power Apps

Com Power Apps, você pode criar aplicativos de negócios que se conectam aos seus dados corporativos e são adaptados às necessidades da sua organização. Power Apps uma ampla variedade de cenários de aplicativo para resolver desafios de negócios por meio de aplicativos de tela. Depois de compilar o aplicativo, você pode exportá-lo do portal do Power Apps maker e inseri-lo Microsoft Teams.

### <a name="power-virtual-agents"></a>Agentes virtuais do Power

O Power Virtual Agent é uma solução de interface gráfica sem código e guiada. Ele é criado no Microsoft Power Platform e no Bot Framework. Ele capacita todos os membros da sua equipe a criar e manter chatbots de conversação avançados que se integram facilmente à Teams plataforma. Você pode projetar, desenvolver e publicar agentes virtuais inteligentes para Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com o Bot Framework.

### <a name="create-virtual-assistant"></a>Criar um Assistente Virtual

Assistente Virtual é um modelo de software livre da Microsoft que permite criar uma solução de conversa robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários.

## <a name="app-templates"></a>Modelos de aplicativo

Você pode usar o modelo de aplicativo para criar aplicativos personalizados para atender às suas necessidades organizacionais. Esses são aplicativos prontos para produção para Microsoft Teams que são orientados pela comunidade, software livre e disponíveis GitHub. Cada modelo contém instruções detalhadas para implantar e instalar o aplicativo para sua organização. Ele fornece um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente.

## <a name="teams-shifts-work-force-management-connectors"></a>Teams shifts work force management connectors

Teams shifts work force management conectores são integrações prontas para produção, software livre e controladas pela comunidade. Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de trabalhadores de linha de frente com Teams Turnos.

## <a name="install-moodle-lms"></a>Instalar o Moodle LMS

O Moodle é um lmS (sistema de gerenciamento de software livre) Learning software livre. Agora ele está integrado ao Microsoft Teams. Essa integração ajuda educadores e professores a colaborar em torno de cursos do Moodle, fazer perguntas sobre notas e tarefas e manter-se atualizado com as notificações diretamente no Teams.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Criar um botão Compartilhar no Teams para o seu site

Sites de terceiros podem usar o script do inicializador para inserir o Compartilhamento Teams botões em suas páginas da Web. Quando você seleciona o botão, ele inicia o Compartilhamento Teams experiência em uma janela pop-up. Isso permite que você compartilhe um link diretamente com qualquer pessoa ou Microsoft Teams canal sem alternar o contexto.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Adicionar uma Microsoft Teams no SharePoint

Você pode obter uma experiência de integração avançada entre Microsoft Teams e SharePoint adicionando uma guia Microsoft Teams no SharePoint como uma SPFx web part.

## <a name="create-deep-link"></a>Criar link profundo

Você pode criar links profundos para as entidades Teams. Você pode criar links de informações e recursos no Teams. Esses links profundos navegam para conteúdo e informações em sua guia. Você pode usar links profundos para vincular seu aplicativo Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência Teams nativa.

## <a name="integrate-device-capabilities"></a>Integrar as funcionalidades do dispositivo

Microsoft Teams plataforma está aprimorando continuamente os recursos do desenvolvedor, alinhando-se com experiências internas internas. A plataforma Teams aprimorada permite que os parceiros acessem e integrem os recursos nativos do dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local usando APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams.

## <a name="integrate-people-picker"></a>Integrar o Seletor de Pessoas

Você pode integrar o Teams seletor de pessoas nativas que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.

## <a name="integrate-teams-in-your-external-app"></a>Integrar Teams em seu aplicativo externo

Você pode inserir suas próprias experiências no Microsoft Teams criando Teams aplicativos. Se você quiser reverter esse modelo  e integrar Teams ou outros recursos de comunicação em sua própria experiência de aplicativo externo, consulte [Serviços de Comunicação do Azure](/azure/communication-services/overview). Serviços de Comunicação do Azure são serviços baseados em nuvem com APIs REST e SDKs de biblioteca de clientes para ajudá-lo a integrar a comunicação em seus próprios aplicativos personalizados. Você pode inserir componentes web Teams genéricos ou React para chamar e conversar com a ajuda da biblioteca [de interface do usuário](https://azure.github.io/communication-ui-library/).

Serviços de Comunicação do Azure aplicativos podem usar a funcionalidade de visualização pública para [interoperar](/azure/communication-services/concepts/teams-interop) com o Teams e permitir que seu aplicativo personalizado ingresse Teams reuniões anonimamente. Por exemplo, você pode integrar chamadas de vídeo em um aplicativo bancário móvel e permitir que os usuários finais se reúnam virtualmente com funcionários do banco usando Microsoft Teams.

Você também pode integrar Microsoft 365 identidade para criar aplicativos externos que incorporam vídeo e chamada PSTN em nome de um Teams usuário. Se você já usou [Skype for Business SDKs](/skype-sdk/appsdk/skypeappsdk) no passado, esses recursos como parte do Serviços de Comunicação do Azure são recomendados como uma substituição.

## <a name="see-also"></a>Confira também

* [Mapear os casos de uso do aplicativo para Teams plataforma](~/concepts/design/map-use-cases.md)
* [Determinar os pontos de entrada do aplicativo](~/concepts/extensibility-points.md)
* [Considerações para a integração do Microsoft Teams](~/samples/integrating-web-apps.md)
* [Criar aplicativos personalizados de baixo código para Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Adicionar um chatbot de agentes virtuais de energia](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Criar assistente virtual](~/samples/virtual-assistant.md)
* [Modelos de aplicativos para o Teams](~/samples/app-templates.md)
* [Conectores shift prontos para produção](~/samples/shifts-wfm-connectors.md)
* [Instalar o Moodle LMS](~/resources/moodleinstructions.md)
* [Compartilhar com Teams de aplicativos Web](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Adicionar uma guia do Teams ao SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Criar links detalhados](~/concepts/build-and-test/deep-links.md)
* [Funcionalidades de dispositivo](~/concepts/device-capabilities/device-capabilities-overview.md)
* [controle do seletor de pessoas](~/concepts/device-capabilities/people-picker-capability.md)
