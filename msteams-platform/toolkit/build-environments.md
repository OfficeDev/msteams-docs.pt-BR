---
title: Preparar-se para criar aplicativos com o Kit de Ferramentas do Teams
author: surbhigupta
description: Neste artigo, você aprenderá a criar um ambiente do Kit de Ferramentas do Teams e gerenciar o aplicativo no Portal do Desenvolvedor
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 4c6862322b007433f3bdfcdc5da93ec5069c6a36
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617047"
---
# <a name="prepare-to-build-apps-using-microsoft-teams-toolkit"></a>Preparar-se para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams

O Kit de Ferramentas do Teams dá suporte a ambientes para a criação de aplicativos. O Kit de Ferramentas do Teams também ajuda a integrar Azure Functions recursos, bem como serviços de nuvem no aplicativo Teams que você criou.

:::image type="content" source="../assets/images/buildapps-TTK.png" alt-text="Preparar-se para criar aplicativos usando o Kit de Ferramentas do Teams":::

## <a name="build-environments"></a>Criar ambientes

O Kit de Ferramentas do Teams no Microsoft Visual Studio Code oferece um conjunto de ambientes para criar seu aplicativo do Teams. Você pode escolher qualquer um dos seguintes ambientes que melhor se adaptem ao seu aplicativo:

* JavaScript ou TypeScript
* Estrutura do SharePoint (SPFx)

### <a name="create-your-teams-app-using-javascript-or-typescript"></a>Criar seu aplicativo Teams usando JavaScript ou TypeScript

Os aplicativos criados com JavaScript têm as seguintes vantagens:

* O aplicativo vem com seus próprios recursos de interface do usuário e experiência do usuário que são ricos e amigáveis para o usuário.
* Fornece atualizações rápidas para aplicativos existentes.
* Distribui aplicativos em várias plataformas, como Android e iOS.
* Compatível para criar um aplicativo com APIs existentes.

O Kit de Ferramentas do Teams no Visual Studio Code dá suporte à criação dos seguintes aplicativos usando JavaScript ou TypeScript:

* Aplicativo guia: seu aplicativo guia pode ter conteúdo baseado na Web, você pode ter uma guia personalizada para o conteúdo da Web no Teams ou adicionar funcionalidade específica do Teams ao conteúdo da Web.
* Aplicativo de bot: os bots podem ser um chatbot ou um bot de conversa que permite realizar tarefas simples e repetitivas, como atendimento ao cliente ou equipe de suporte.
* Bot de notificação: você pode enviar mensagens no canal ou grupo do Teams ou chat pessoal por bots de notificação com solicitação HTTP.
* Bot de comando: você pode automatizar tarefas repetitivas usando o bot de comando. Os bots de comando ajudam você a responder a consultas simples ou comandos enviados em chats.
* Extensões de mensagem: você pode interagir com seu serviço Web por meio de botões e formulários. Funcionalidade fornecida pela extensão de mensagem.

### <a name="create-your-teams-app-using-spfx"></a>Criar seu aplicativo teams usando SPFx

O Kit de Ferramentas do Teams Visual Studio Code permite que você crie aplicativos de guia usando SPFx. Esses aplicativos têm as seguintes vantagens:

* Fornece fácil integração com os dados que residem no SharePoint com o Teams.
* Você pode integrar sua solução SPFx com suas APIs de negócios protegidas Microsoft Azure Active Directory (Azure AD).
* Fornece acessos a várias ferramentas de software livre.
* Cria para seus aplicativos avançados que podem fornecer uma ótima experiência do usuário.
* Integra-se com outras cargas de trabalho do Microsoft (Office) 365 facilmente.
* Oferece flexibilidade para hospedar aplicativos sempre que necessário.

## <a name="support-for-azure-functions"></a>Suporte para Azure Functions

Você pode usar o Kit de Ferramentas do Teams [para integrar Azure Functions](/azure/azure-functions/functions-overview) recursos à criação de aplicativos. Você pode se concentrar nas partes de código mais importantes e Azure Functions fazer o resto.
Azure Functions permitir que você implemente:

1. Lógica do sistema em seus blocos de código prontamente disponíveis. Esses blocos são chamados de funções.
1. À medida que as solicitações aumentam, Azure Functions atende ao requisito com o número de demandas necessárias.

O Azure Function se integra a uma matriz de serviços [de nuvem que](add-resource.md#types-of-cloud-resources) fornecem implementações com recursos avançados. A seguir estão apenas alguns cenários comuns para Azure Functions:

* Ao criar uma API Web
* Processando alterações no banco de dados
* Processando fluxos de dados de IoT
* Gerenciando filas de mensagens

## <a name="see-also"></a>Confira também

* [Kit de ferramentas do Teams para Visual Studio](visual-studio-overview.md)
* [Gerenciar seus aplicativos do Teams usando o Portal do Desenvolvedor](../concepts/build-and-test/teams-developer-portal.md)
* [Criar um novo aplicativo Teams usando o Kit de Ferramentas do Teams](create-new-project.md)
