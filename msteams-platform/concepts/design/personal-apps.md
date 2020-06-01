---
title: Referência de diretrizes de design
description: Descreve as diretrizes para a criação de um aplicativo pessoal
keywords: Diretrizes de design do Microsoft Teams aplicativos pessoais da estrutura de referência
ms.openlocfilehash: f66691234149afa56a6753dd51379c9f2355318e
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455496"
---
# <a name="personal-apps"></a>Aplicativos pessoais

> [!NOTE]
> O suporte completo para guias em clientes móveis é suportado no Microsoft Teams. Você deve seguir as [orientações para guias em dispositivos móveis](../../tabs/design/tabs-mobile.md) ao criar guias para plataformas móveis.

Um aplicativo pessoal é um aplicativo do teams com um escopo pessoal.  Como desenvolvedor de aplicativos, você tem a opção de fornecer uma versão do seu aplicativo que se concentra em interações com um único usuário. Pode ser um [bot de conversa](../../bots/what-are-bots.md) para participar de conversas de um-para-um com um usuário ou uma [guia pessoal](../../tabs/what-are-tabs.md) que forneça uma experiência Web incorporada. Os aplicativos pessoais permitem que os usuários exibam o conteúdo selecionado em um só lugar. Na captura de tela a seguir, a contoso é um aplicativo pessoal no submenu de aplicativo pessoal.

![imagem do menu de estouro de aplicativos](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a>Diretrizes

Um aplicativo pessoal normalmente contém as seguintes guias:

### <a name="your-tab"></a>Sua guia

Este é o local onde os usuários verão todas as suas coisas. É seu espaço pessoal. A guia pode ser organizada como uma lista, uma grade, colunas ou uma tela única... o que funcionar melhor para o seu aplicativo. Para obter informações adicionais sobre como criar guias eficazes, consulte: [design de guias](../../tabs/design/tabs.md).

Como essa guia pode mostrar itens de vários canais, cada item deve exibir sua própria equipe, canal e guia para que o usuário possa ver facilmente onde ele se originou.

![Guia tarefas pessoais](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a>Recentemente

A guia **recente** permite que alguém Navegue por tudo o que exibiu recentemente em seu aplicativo. Ela é listada em ordem cronológica (do mais para menos recente). Clicar em um item nesta lista navegará o usuário para o canal e a guia do item.

![Guia recente](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a>Todos

Esta é uma lista de todas as suas guias na organização da pessoa (com as quais elas têm acesso, assim mesmo). Em outras palavras, ele mostra a eles em qualquer lugar em que o aplicativo está sendo usado. Como ocorre com a guia **recente** , selecionar algo na lista trará o usuário diretamente para o canal e a guia relevantes.

### <a name="bot"></a>Bot

Um bot não é necessário, mas é uma ótima maneira de se comunicar de forma direta e privada com seus usuários. A notificação é uma das funções mais importantes de um aplicativo pessoal e qual é a melhor maneira de notificá-lo do que com comunicação direta?

Os bots entregam mensagens na forma de cartões, que podem fornecer informações específicas (como um alerta que o novo conteúdo está disponível) ou atualizações amplas (como uma lista de tarefas diárias). Para obter informações adicionais sobre como projetar bots efetivos, consulte: [design de bot](../../bots/design/bots.md).

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
