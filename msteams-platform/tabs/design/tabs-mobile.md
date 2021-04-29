---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para projetar guias que funcionam em dispositivos móveis.
ms.topic: conceptual
localization_priority: Normal
keywords: guias móveis da estrutura de referência de diretrizes de design do teams
ms.openlocfilehash: cdcaddf5ba0fb18537e87daa4b459c7377225f76
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075693"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Você pode incluir guias em canais móveis do Teams, chats e aplicativos pessoais.

## <a name="accessing-personal-tabs"></a>Acessando guias pessoais

Você pode acessar guias pessoais na gaveta do aplicativo.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a gaveta de aplicativos móveis do Teams." border="false":::

## <a name="accessing-channel-tabs"></a>Acessando guias de canal

Você pode acessar guias de canal e grupo selecionando o botão **Mais** no canal ou chat no qual eles foram adicionados.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel do Teams." border="false":::

## <a name="design-considerations"></a>Considerações de design

Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal do Teams. Para criar uma experiência imersiva que se ajuste ao Teams, siga estas diretrizes.

### <a name="responsive-design"></a>Design responsivo

Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, ela precisa seguir princípios de [design responsivo.](https://www.w3schools.com/html/html_responsive.asp) Todas as construções principais devem ser acessíveis em dispositivos móveis, e os exibições não devem ser distorcidos. Certifique-se de que, quando a guia for carregada em um dispositivo móvel, todos os botões e links serão facilmente acessíveis usando a navegação baseada em dedos.

### <a name="layouts"></a>Layouts

Escolher o layout correto para sua guia é importante. Você deve considerar o tipo de informação que está apresentando e escolher um layout que as organize para facilitar o consumo. Algumas opções possíveis são descritas abaixo.

#### <a name="single-canvas"></a>Tela única

Esta é uma área grande onde o trabalho é feito. O aplicativo Wiki do Teams segue esse padrão. Se você tiver um aplicativo que não separe conteúdo em componentes menores, isso seria um bom ajuste.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma guia de tela única móvel do Teams." border="false":::

#### <a name="list"></a>List

As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes na parte superior. É útil usar colunas sortíveis. As ações podem ser adicionadas a cada item de lista no menu reellipse.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista móvel do Teams." border="false":::

#### <a name="grid"></a>Grade

As grades são úteis para mostrar elementos altamente visuais. Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel do Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Guias com bots no celular

O exemplo a seguir é um aplicativo pessoal que tem guias e um bot.

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo do Teams móvel que tem guias e um bot." border="false":::

## <a name="ui-components"></a>Componentes da interface do usuário

### <a name="color-palettes"></a>Paletas de cores

Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Teams. Como o teams mobile tem dois temas de cores (claro e escuro), é uma boa ideia garantir que seu aplicativo tenha uma ótima aparência em ambos.

#### <a name="light-color"></a>Cor clara

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Cor escura

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Botões e controles

A maneira como os botões são estilados ajuda a comunicar que tipo de ação eles disparam. Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase. Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone. Para comunicar níveis diferentes em uma hierarquia, projetamos botões primários e secundários em cada categoria.

#### <a name="buttons"></a>Botões

Botões primários e secundários.

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Controles de seleção

Botões de rádio, caixas de seleção e alternâncias.

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Chiclets e comprimidos

![chiclets e comprimidos](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Tipografia

A tipografia deve ser clara e proposital. Enfatizar informações importantes e evitar usar várias fontes e tamanhos para reduzir a confusão. Recomendamos usar o caso de frase e evitar o uso de todas as caps para localização e legibilidade.

![tipografia móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Campos e flyouts

Campos são áreas onde os usuários podem inserir texto. Os flyouts são mais leves do que as caixas de diálogo e aparecem no painel superior.

#### <a name="list-controls"></a>Controles de lista

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Controles de campo

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Considerações sobre desenvolvedores

Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes Android e iOS do Microsoft Teams. As seções abaixo delineam alguns dos principais cenários que você precisa considerar.

### <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK JavaScript do Teams para pelo menos a versão 1.4.1.

### <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Clientes móveis regularmente precisam funcionar com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com quaisquer tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário. Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.

> [!NOTE]
> As guias são habilitadas no celular somente depois que o aplicativo é adicionado a uma lista de permitir, com base na entrada da equipe de aprovação. Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com.

### <a name="testing-on-mobile-clients"></a>Testes em clientes móveis

Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução. Recomendamos que você teste em dispositivos de alto e baixo desempenho, bem como em um tablet.

### <a name="distribution"></a>Distribuição

Os aplicativos listados no armazenamento do Teams devem ser aprovados para que o uso móvel funcione corretamente no cliente móvel do Teams. O comportamento das guias depende da aprovação do aplicativo.

#### <a name="channel-and-group-tab-behavior"></a>Comportamento da guia canal e grupo

* **Comportamento quando aprovado**: abre no cliente móvel do Teams usando a configuração do `contentUrl` aplicativo.
* **Comportamento quando não aprovado**: abre no navegador padrão do dispositivo usando a configuração do aplicativo (que também deve ser incluído na função `websiteUrl` do `setSettings()` código-fonte). No entanto, os usuários ainda podem carregar a guia no cliente móvel do Teams selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` aplicativo.

#### <a name="personal-app-behavior"></a>Comportamento do aplicativo pessoal

* **Comportamento quando aprovado**: Cada guia no aplicativo pessoal é exibida no cliente móvel do Teams usando suas respectivas `contentUrl` configurações.
* **Comportamento quando não aprovado**: o aplicativo pessoal não está disponível no cliente móvel do Teams.

#### <a name="non-teams-store-app-behavior"></a>Comportamento de aplicativo que não é do Teams store

Se você estiver fazendo sideload do aplicativo ou publicação no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que os aplicativos da loja do Teams aprovados pela Microsoft para dispositivos móveis.
