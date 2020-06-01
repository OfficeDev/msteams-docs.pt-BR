---
title: Plataforma para desenvolvedores do Microsoft Teams
author: clearab
description: Página de visão geral descrevendo a plataforma de desenvolvedor do Microsoft Teams e como começar a criar aplicativos para o Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 5225669ccc8c76bb532d045df6b65105c893e734
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455482"
---
# <a name="what-are-microsoft-teams-apps"></a>O que são aplicativos do Microsoft Teams?

O Microsoft Teams é um espaço de trabalho de colaboração no Office 365 que se integra com aplicativos e serviços que as pessoas usam para fazer o trabalho em conjunto. A plataforma de desenvolvedor do Microsoft Teams permite que os desenvolvedores integrem seus próprios aplicativos e serviços para melhorar a produtividade, tomar decisões mais rapidamente, fornecer foco (reduzindo a alternância de contexto) e criar colaboração em torno de conteúdo e fluxos de trabalho existentes. Os aplicativos criados na plataforma do Microsoft Teams são pontes entre o cliente do Teams e seus serviços e fluxos de trabalho; colocá-los diretamente no contexto da plataforma de colaboração.

## <a name="what-can-teams-apps-do"></a>O que os aplicativos do teams podem fazer?

Os aplicativos criados na plataforma do Microsoft Teams concentram-se principalmente no aumento da colaboração e na melhoria da produtividade. Seu aplicativo pode ser algo simples, como notificações de lançamento de outros sistemas ou aplicativos multifacetados complexos. Só tenha em mente que o Microsoft Teams é uma plataforma de colaboração social; os melhores aplicativos se concentram em ajudar as pessoas a se expressarm e a trabalhar melhor juntos.

* **Colabore em itens em sistemas externos.** Um dos principais cenários de um aplicativo personalizado do Microsoft Teams é trazer informações ou itens para o Microsoft Teams de outro lugar e ter uma conversa em torno dela. Você pode enviar informações para o Microsoft Teams, permitir que os usuários pesquisem e o recebam sob demanda, ou disponibilizá-lo em um modo de exibição da Web incorporado.

* **Disparar fluxos de trabalho de conversas.** Freqüentemente as conversas resultam na necessidade de iniciar um fluxo de trabalho ou concluir alguma ação; Dê uma nota sobre isso, revise minha solicitação pull, converta-a em um líder de vendas, etc. O aplicativo do Microsoft Teams pode colocar o acesso a esse fluxo de trabalho dentro do teams.

* **Notifique a equipe de eventos importantes.** Doente de notificações por email? Envie notificações para o Microsoft Teams! Enviar notificações diretamente aos usuários, a um canal, ao feed de atividades ou a qualquer pessoa que se inscrever neles.

* **Incorporar funcionalidade de outros sites/serviços.** Às vezes, você só precisa tornar seu aplicativo mais fácil de descobrir. Incorpore seu aplicativo de página única existente ou crie algo a partir do zero para o Microsoft Teams.

## <a name="how-do-teams-apps-work"></a>Como os aplicativos do teams funcionam?

A primeira coisa a saber sobre aplicativos personalizados para o Microsoft Teams (além de quão incríveis podem ser), é que o Microsoft Teams não é um serviço de hospedagem. Seu pacote de aplicativos contém metadados sobre seu aplicativo (nome, ícones, etc.) e ponteiros para os serviços Web que você hospeda para o seu aplicativo. O Microsoft Teams fornece o mecanismo de distribuição, construções de interface do usuário/UX para que você possa aproveitar e APIs que você pode usar para aumentar as informações e ações disponíveis para seu aplicativo.

Um aplicativo do teams consiste em três partes principais:

* **O cliente Microsoft Teams (Web, desktop ou celular)** onde os usuários irão interagir com seu aplicativo.
* **Seu pacote de aplicativos do Microsoft Teams** que cria o aplicativo instalado pelos seus usuários e que contém os metadados e ponteiros de seu aplicativo para seus serviços.
* **Seu serviço, fluxo de trabalho ou site** que executa a lógica necessária, o armazenamento de dados e as chamadas de API para alimentar o aplicativo.

É importante ter em mente que qualquer funcionalidade que você expor em um aplicativo do Microsoft Teams está disponível pela Internet, a menos que você execute etapas adicionais para protegê-lo. Se você estiver fornecendo acesso a informações confidenciais ou protegidas, certifique-se de que seus serviços estão no mínimo Autenticando o ponto de extremidade conectando ao seu aplicativo ou [autentique seus usuários](concepts/authentication/authentication.md).

## <a name="how-can-you-share-your-teams-app"></a>Como você pode compartilhar seu aplicativo do Microsoft Teams?

Quando estiver pronto para compartilhar seus aplicativos do Microsoft Teams, você terá três opções, dependendo de quem é o público-alvo.

* **[Carregar seu aplicativo diretamente](concepts/deploy-and-publish/apps-upload.md)** Se seu aplicativo só precisa ser compartilhado para sua equipe ou algumas pessoas em sua organização, você pode compartilhar seu pacote de aplicativos e carregá-lo diretamente.
* **[Publicar em seu catálogo de aplicativos organizacional](concepts/deploy-and-publish/apps-upload.md)** Você pode compartilhar seu aplicativo com toda a sua organização por meio do seu catálogo de aplicativos.
* **[Publicar na loja de aplicativos públicos](concepts/deploy-and-publish/apps-upload.md)** Se seu aplicativo for para todos, você poderá publicá-lo em nossa loja de aplicativos públicos. Dependendo de suas metas, você pode estar qualificado para assistência de marketing e vendas.

## <a name="get-started"></a>Introdução

* [Criar um bot e um aplicativo de guia no C #](tutorials/get-started-dotnet-app-studio.md)
* [Criar um bot e um aplicativo de guia em JavaScript/node. js](tutorials/get-started-nodejs-app-studio.md)

## <a name="learn-more"></a>Saiba mais

* [Pontos de extensibilidade no cliente do Teams](concepts/extensibility-points.md)
* [Criando aplicativos para o Teams](concepts/building-an-app.md)
