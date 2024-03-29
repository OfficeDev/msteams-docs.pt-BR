---
title: Integrar aplicativos Web
author: Rajeshwari-v
description: Neste artigo, você vai começar a integrar aplicativos Web e recursos de dispositivo com o aplicativo Microsoft Teams. Power Platform para criar Power Apps, Power Virtual Agents, Assistente Virtual, modelos de aplicativo, conectores Shift, sistema de gerenciamento de aprendizagem Moodle.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 19cf5b580c2d25e90eb90bd1fef9a78c75111092
ms.sourcegitcommit: 937ea793889fc1efa9ec6a52374d5098be1117e0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67653178"
---
# <a name="integrate-web-apps"></a>Integrar aplicativos Web

Você pode fornecer uma experiência de usuário enriquecida integrando os recursos de um aplicativo Web existente na plataforma do Microsoft Teams. Siga as [Diretrizes de design do Teams](~/concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo do Teams.
Este documento fornece uma visão geral dos pré-requisitos para integrar aplicativos da Web com o Teams, plataforma Power para criar aplicativos Power, Power Virtual Agents, Virtual Assistant, modelos de aplicativos, conectores Shift, Moodle LMS, criação de um botão Share-to-Teams para o seu site, adição uma guia do Teams no SharePoint, criando links diretos e integrando recursos do dispositivo.

## <a name="prerequisites"></a>Pré-requisitos

Para uma integração eficaz, certifique-se de ter uma melhor compreensão dos seguintes pré-requisitos:

* Recursos do Teams.
* Requisitos do SharePoint para armazenamento de arquivos e dados.
* Requisitos de DNS.
* Autenticação.
* Vinculação profunda do seu aplicativo com o Teams.
* Mapear os casos de uso do seu aplicativo para recursos de plataforma do Teams.
* Determine os pontos de entrada do aplicativo, como uso pessoal, colaboração ou ambos.

## <a name="low-code-platforms"></a>Plataformas com pouco código

As plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software e exigem pouca ou nenhuma codificação para criar aplicativos e processos. Você pode criar aplicativos personalizados facilmente com plataformas com pouco código. Essas plataformas consistem em uma interface visual, conectores para serviços de back-end e um sistema de gerenciamento de ciclo de vida de aplicativo interno para criar, depurar, implantar e manter aplicativos. A Microsoft fornece os seguintes gateways inovadores para criar rapidamente aplicativos compatíveis com o Teams usando atributos de código baixo:

* Microsoft Power Platform.
* Modelos de aplicativos do Microsoft Teams.

## <a name="microsoft-power-platform"></a>Microsoft Power Platform

A plataforma Microsoft Power combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate e Power Virtual Agents em uma plataforma de aplicativo avançada. Essas tecnologias capacitam você a criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado.

>[!NOTE]
>Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na loja de aplicativos do Teams. Os aplicativos do Microsoft Power Platform podem ser publicados somente na loja de aplicativos de uma organização.

### <a name="power-apps"></a>Power Apps

Com o Power Apps, você pode criar aplicativos de negócios que se conectam aos seus dados corporativos e são adaptados às necessidades da sua organização. O Power Apps permite uma ampla variedade de cenários de aplicativos para resolver desafios de negócios por meio de aplicativos Canvas. Depois de criar o aplicativo, você pode exportá-lo do portal do criador do Power Apps e incorporá-lo no Teams.

### <a name="power-virtual-agents"></a>Agentes virtuais do Power

O Power Virtual Agent é uma solução de interface gráfica guiada sem código. Ele foi desenvolvido no Microsoft Power Platform e no Bot Framework. Ele permite que todos os membros da sua equipe criem e mantenham chatbots de conversação avançados que se integram facilmente à plataforma do Teams. Você pode projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com o Bot Framework.

### <a name="create-virtual-assistant"></a>Criar um Assistente Virtual

O Assistente Virtual é um modelo de software livre da Microsoft que permite criar uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários.

## <a name="app-templates"></a>Modelos de aplicativos

Você pode usar o modelo de aplicativo para criar aplicativos personalizados para atender às suas necessidades organizacionais. Os modelos de aplicativos são aplicativos prontos para produção para o Microsoft Teams orientadas pela comunidade, software livre e disponíveis no GitHub. Cada modelo contém instruções detalhadas para implantar e instalar o aplicativo para sua organização. Ele fornece um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente.

## <a name="install-moodle-lms"></a>Instalar o Moodle LMS

O Moodle é um LMS (Sistema de Gerenciamento de Aprendizagem) de software livre popular. Agora está integrado ao Teams. Esta integração ajuda educadores e professores a colaborarem em cursos do Moodle, fazerem perguntas sobre suas notas e suas tarefas e permanecerem atualizados com as notificações diretamente dentro do Teams.

## <a name="create-a-share-to-teams-button-for-your-website"></a>Criar um botão Compartilhar no Teams para o seu site

Sites de terceiros podem usar o script do inicializador para inserir botões Compartilhar no Teams em suas páginas da Web. Quando você seleciona o botão, ele inicia a experiência Compartilhar com o Teams em uma janela pop-up. Ele permite que você compartilhe um link diretamente para qualquer pessoa ou canal do Microsoft Teams sem alternar o contexto.

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a>Adicionar uma guia do Microsoft Teams no SharePoint

Você pode obter uma experiência de integração avançada entre o Teams e o SharePoint adicionando uma guia do Teams no SharePoint como uma Web Part SPFx.

## <a name="create-deep-link"></a>Criar links profundos

Você pode criar links profundos para entidades no Teams. Você pode criar links de informações e recursos no Teams. Esses links profundos navegam para conteúdo e informações em sua guia. Você pode usar links profundos para vincular seu aplicativo ao Teams à medida que eles reúnem várias partes de um aplicativo para uma experiência mais nativa do Teams.

## <a name="integrate-device-capabilities"></a>Integrar as funcionalidades do dispositivo

A plataforma Teams está aprimorando continuamente os recursos do desenvolvedor, alinhando-se às experiências internas integradas. A plataforma aprimorada do Teams permite que os parceiros acessem e integrem os recursos nativos do dispositivo, como câmera, leitor de código QR ou de código de barras, galeria de fotos, microfone e localização usando APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams.

## <a name="integrate-people-picker"></a>Integrar o Seletor de Pessoas

Além disso, você pode integrar o controle seletor de pessoas nativo do Teams que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.

## <a name="integrate-teams-in-your-external-app"></a>Integrar o Teams em seu aplicativo externo

Você pode incorporar suas próprias experiências no Teams criando aplicativos do Teams. Se você quiser *reverter* esse modelo e integrar o Teams ou outros recursos de comunicação em sua própria experiência de aplicativo externo, consulte [Serviços de Comunicação do Azure](/azure/communication-services/overview). Os serviços de Comunicação do Azure são serviços baseados em nuvem com APIs REST e SDKs de biblioteca de clientes para ajudá-lo a integrar a comunicação em seus próprios aplicativos personalizados. Você pode inserir componentes web genéricos ou no estilo do Teams para chamar e conversar com a ajuda da [ biblioteca de IU](https://azure.github.io/communication-ui-library/).

Os aplicativos dos Serviços de Comunicação do Azure podem usar a funcionalidade de visualização pública para [interoperar com o Teams](/azure/communication-services/concepts/teams-interop) e permitir que seu aplicativo personalizado ingresse em reuniões do Teams anonimamente. Por exemplo, você pode integrar chamadas de vídeo em um aplicativo de banco móvel e permitir que os usuários finais se reúnam virtualmente com funcionários do banco usando o Teams.

Você também pode integrar a identidade do Microsoft 365 para criar aplicativos externos que incorporam chamadas PSTN e de vídeo em nome de um usuário do Teams. Se você já usou [SDKs do Skype for Business](/skype-sdk/appsdk/skypeappsdk) no passado, esses recursos como parte do Serviços de Comunicação do Azure são recomendados como uma substituição.

## <a name="see-also"></a>Confira também

* [Mapear os casos de uso do seu aplicativo para recursos de plataforma do Teams](~/concepts/design/map-use-cases.md).
* [Determinar os pontos de entrada do aplicativo](~/concepts/extensibility-points.md).
* [Considerações para a integração do Microsoft Teams](~/samples/integrating-web-apps.md)
* [Criar aplicativos personalizados de baixo código para o Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Adicionar um chatbot de agentes virtuais de energia](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
* [Criar um assistente virtual](~/samples/virtual-assistant.md)
* [Modelos de aplicativos para o Teams](~/samples/app-templates.md)
* [Conectores de turnos prontos para produção](~/samples/shifts-wfm-connectors.md)
* [Instalar o Moodle LMS](~/resources/moodleinstructions.md)
* [Compartilhar no Teams a partir de aplicativos Web](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Adicionar uma guia do Teams ao SharePoint](~/tabs/how-to/tabs-in-sharepoint.md)
* [Criar links detalhados](~/concepts/build-and-test/deep-links.md)
* [Funcionalidades de dispositivo](~/concepts/device-capabilities/device-capabilities-overview.md)
* [Pessoas seletor](~/concepts/device-capabilities/people-picker-capability.md)
