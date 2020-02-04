---
title: O que são guias personalizadas no Microsoft Teams?
author: laujan
description: Uma visão geral das guias personalizadas na plataforma do Microsoft Teams
ms.topic: overview
ms.author: v-laujan
ms.openlocfilehash: 7560a9a7d19ca0182b2f5f45b304a96a0f2dddd4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672899"
---
# <a name="what-are-microsoft-teams-custom-tabs"></a>O que são guias personalizadas do Microsoft Teams?

As guias são páginas da Web com reconhecimento de equipes incorporadas no Microsoft Teams. Eles podem ser adicionados como parte de um canal dentro de uma equipe, um chat de grupo ou um aplicativo pessoal para um usuário individual. Como parte do seu aplicativo, você pode adicionar guias personalizadas para incorporar seu próprio conteúdo da Web no Microsoft Teams e usar o [SDK de cliente do JavaScript do teams](/javascript/api/overview/msteams-client), adicionar a funcionalidade específica da equipe ao conteúdo da Web.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookies por padrão. É recomendável que você defina o uso pretendido para seus cookies, em vez de confiar no comportamento padrão do navegador. *Confira* o [atributo SameSite cookie (atualização 2020)](../resources/samesite-cookie-update.md).

Há dois tipos de guias disponíveis em Teams-Channel/Group e pessoal. Uma guia de canal/grupo fornece conteúdo a canais e bate-papos de grupo e é uma ótima maneira de criar espaços colaborativos em torno de conteúdo dedicado baseado na Web. As guias pessoais, juntamente com bots de escopo pessoal, fazem parte de aplicativos pessoais e têm o escopo para um único usuário. Eles podem ser fixados na barra de navegação à esquerda para facilitar o acesso.

## <a name="tabs-user-scenarios"></a>Guias de cenários do usuário

**Cenário:** Traga um recurso baseado na Web existente dentro do teams. \
**Exemplo:** Você cria uma guia pessoal no aplicativo do Microsoft Teams que apresenta um site corporativo de informações aos usuários.

**Cenário:** Adicione páginas de suporte a um bot do teams ou extensão de mensagens. \
**Exemplo:** Você cria guias pessoais que fornecem informações sobre o conteúdo da página da Web e ajuda para os usuários.

**Cenário:** Fornecer acesso a itens com os quais os usuários interagem regularmente para colaboração e diálogo cooperativo. \
**Exemplo:** Você cria uma guia de canal/grupo com vinculação profunda a itens individuais.

## <a name="how-do-tabs-work"></a>Como funcionam as guias?

Uma guia personalizada é declarada no manifesto do aplicativo de seu pacote de aplicativos. Para cada página da Web que você deseja incluir como uma guia no seu aplicativo, defina uma URL e um escopo. Além disso, você precisa adicionar o [SDK do cliente JavaScript do teams](/javascript/api/overview/msteams-client) à sua página `microsoftTeams.initialize()` e ligar após a página ser carregada. Isso solicitará que o Microsoft Teams exiba sua página, conceda a você acesso a informações específicas de equipes (por exemplo, se o cliente do Microsoft Teams estiver executando o tema escuro) e permita que você execute ações com base nos resultados.

Se você optar por expor sua guia no canal/grupo ou escopo pessoal, precisará apresentar uma [página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) HTML com IFRAME na sua guia. Para guias pessoais, a URL do conteúdo é definida diretamente no manifesto pela `contentUrl` Propriedade na `staticTabs` matriz. O conteúdo da guia será o mesmo para todos os usuários.

Para guias de canal/grupo, você também precisa criar uma página de configuração adicional que permite que os usuários configurem a URL da página de conteúdo, normalmente usando parâmetros de cadeia de caracteres de consulta de URL para carregar o conteúdo apropriado para esse contexto. Isso ocorre porque a guia canal/grupo pode ser adicionada a várias equipes ou chats de grupo diferentes. Em cada instalação subsequente, os usuários poderão configurar a guia permitindo que você ajuste a experiência conforme necessário. Por exemplo, quando você adiciona a guia painel de DevOps do Microsoft Azure, a página de configuração permite que você escolha qual placa a guia carregará. A URL da página de configuração é especificada `configurationUrl` pela propriedade na `configurableTabs` matriz no manifesto do aplicativo.

Você pode ter um máximo de uma (1) guia de canal/grupo e até dezesseis (16) Guias pessoais por aplicativo.

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um `websiteUrl` valor para a propriedade (veja abaixo). As guias pessoais estão atualmente disponíveis no [Developer Preview](~/resources/dev-preview/developer-preview-intro.md). O suporte completo para guias em clientes móveis será lançado em breve. Para se preparar para a atualização, siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.
