---
title: Referência de diretrizes de design
description: Descreve as diretrizes para a criação de um aplicativo pessoal
keywords: Diretrizes de design do Microsoft Teams aplicativos pessoais da estrutura de referência
ms.openlocfilehash: 6a07b618d78a3ad79850713052c88ef178c1ecc1
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672525"
---
# <a name="personal-apps"></a>Aplicativos pessoais

> [!Important]
> O suporte completo para guias em clientes móveis estará disponível em breve. Para se preparar para essa alteração, você deve seguir as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias. Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
>
> Quando o suporte completo para guias é liberado:
>
> * Todas as guias sempre estarão disponíveis em dispositivos móveis
> * O `contentUrl` **será carregado no cliente do Mobile Teams**.
> * Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.

Um aplicativo pessoal é um aplicativo com escopo pessoal. Como desenvolvedor de aplicativos, você tem a opção de fornecer uma versão do seu aplicativo que é criada para o usuário individual. Nesta versão, a coleção de guias (e o bot, se você incluiu uma), foram projetadas para a pessoa. Dessa forma, você pode criar uma interação um-em-um com seus usuários.

Um aplicativo pessoal é onde alguém pode ver tudo o que é o seu e todos os itens que foram exibidos recentemente no aplicativo. Ele coloca tudo em um só lugar. Na captura de tela a seguir, a contoso é um aplicativo pessoal no submenu de aplicativo pessoal.

![imagem do menu de estouro de aplicativos](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a>Diretrizes

Um aplicativo pessoal normalmente contém as seguintes guias:

### <a name="your-tab"></a>Sua guia

Este é o local onde os usuários verão todas as suas coisas. É seu espaço pessoal. A guia pode ser organizada como uma lista, uma grade, colunas ou uma tela única... o que funcionar melhor para o seu aplicativo. Para obter informações adicionais sobre como criar guias eficazes, consulte: [Design de guias (~/Tabs/design/Tabs.MD).

Como essa guia pode mostrar itens de vários canais, cada item deve exibir sua própria equipe, canal e guia para que o usuário possa ver facilmente onde ele se originou.

![Guia tarefas pessoais](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a>Recentemente

A guia **recente** permite que alguém Navegue por tudo o que exibiu recentemente em seu aplicativo. Ela é listada em ordem cronológica (do mais para menos recente). Clicar em um item nesta lista navegará o usuário para o canal e a guia do item.

![Guia recente](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a>Todos

Esta é uma lista de todas as suas guias na organização da pessoa (com as quais elas têm acesso, assim mesmo). Em outras palavras, ele mostra a eles em qualquer lugar em que o aplicativo está sendo usado. Como ocorre com a guia **recente** , selecionar algo na lista trará o usuário diretamente para o canal e a guia relevantes.

### <a name="bot"></a>Bot

Um bot não é necessário, mas é uma ótima maneira de se comunicar de forma direta e privada com seus usuários. A notificação é uma das funções mais importantes de um aplicativo pessoal e qual é a melhor maneira de notificá-lo do que com comunicação direta?

Os bots entregam mensagens na forma de cartões, que podem fornecer informações específicas (como um alerta que o novo conteúdo está disponível) ou atualizações amplas (como uma lista de tarefas diárias). Para obter informações adicionais sobre como projetar bots efetivos, consulte: [Design de bot (~/bots/design/bots.MD).

![Saudação de bot](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a>Ajuda e configurações

O conteúdo da ajuda permite que os usuários descubram as nuances de seu aplicativo. Adicione uma guia **configurações** para ter a possibilidade de personalizá-la.

### <a name="about"></a>Sobre

Inclua uma guia **sobre** para fornecer informações como números de versão, recursos, privacidade e links de permissões.

## <a name="best-practices"></a>Práticas recomendadas

### <a name="communicate-directly-with-your-users"></a>Comunicar-se diretamente com seus usuários

Use um bot para notificar os usuários sobre alterações e novos recursos.

### <a name="customize-your-tabs"></a>Personalizar suas guias...

Sinta-se à vontade para adicionar outras guias que ajudarão os usuários a realizar tarefas específicas.

### <a name="and-make-them-relevant-to-every-user"></a>... e torná-los relevantes a todos os usuários

Cada guia que você declarar no manifesto do aplicativo ficará visível para todos os usuários. Por exemplo, se seu aplicativo pessoal é uma ferramenta de relatório de despesas que é usada por gerentes e funcionários, uma guia de **aprovação** deve fornecer conteúdo que seja significativo para ambas as funções.
