---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para projetar guias que funcionam no celular.
ms.topic: conceptual
localization_priority: Normal
keywords: equipes projetam diretrizes de referência quadro de aplicativos pessoais guias móveis
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566695"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

Você pode incluir guias em Teams canais móveis, chats e aplicativos pessoais.

## <a name="accessing-personal-tabs"></a>Acessando guias pessoais

Você pode acessar guias pessoais na gaveta de aplicativos.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a Teams gaveta de aplicativos móveis." border="false":::

## <a name="accessing-channel-tabs"></a>Acessando guias de canais

Você pode acessar guias de canais e grupos selecionando o botão **Mais** no canal ou chat no qual eles foram adicionados.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel Teams." border="false":::

## <a name="design-considerations"></a>Considerações de design

Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal Teams. Para criar uma experiência imersiva que se encaixe com Teams, siga essas diretrizes.

### <a name="responsive-design"></a>Design responsivo

Como sua guia pode ser aberta em dispositivos com uma ampla gama de tamanhos de tela, ela precisa seguir princípios [de design responsivos.](https://www.w3schools.com/html/html_responsive.asp) Todas as construções-chave devem ser acessíveis em dispositivos móveis, e as visualizações não devem ser distorcidas. Certifique-se de que quando sua guia estiver carregada em um dispositivo móvel, todos os botões e links são facilmente acessíveis usando navegação baseada em dedos.

### <a name="layouts"></a>Layouts

Escolher o layout correto para sua guia é importante. Você deve considerar o tipo de informação que está apresentando e escolher um layout que a organize para fácil consumo. Algumas opções potenciais estão descritas abaixo.

#### <a name="single-canvas"></a>Tela única

Esta é uma grande área onde o trabalho é feito. O aplicativo wiki Teams segue esse padrão. Se você tem um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma Teams guia de tela única móvel." border="false":::

#### <a name="list"></a>List

As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes no topo. É útil usar colunas classificadas. As ações podem ser adicionadas a cada item da lista no menu elipse.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista de celular Teams." border="false":::

#### <a name="grid"></a>grade

Grades são úteis para mostrar elementos altamente visuais. Ajuda a incluir um filtro ou controle de pesquisa na parte superior.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Guias com bots no celular

O exemplo a seguir é um aplicativo pessoal que tem guias e um bot:

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo de Teams móvel que tem guias e um bot." border="false":::

## <a name="ui-components"></a>Componentes de interface do usuário

### <a name="color-palettes"></a>Paletas de cores

Usar nossa paleta neutra aprovada para dados, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa em Teams. Como Teams celular tem dois temas de cores (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.

#### <a name="light-color"></a>Cor clara

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Cor escura

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Botões e controles

A forma como os botões são estilizados ajuda a comunicar que tipo de ação eles acionam. Mantemos uma ampla gama de botões que são formatados para mostrar diferentes níveis de ênfase. Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone. Para comunicar diferentes níveis em uma hierarquia, projetamos botões primários e secundários dentro de cada categoria.

#### <a name="buttons"></a>Botões

Botões primários e secundários.

![imagem botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Controles de seleção

Botões de rádio, caixas de seleção e alternâncias.

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Chiclets e pílulas

![chiclets e pílulas](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Tipografia

A tipografia deve ser clara e proposital. Enfatize informações importantes e evite o uso de várias fontes e tamanhos para reduzir a confusão. Recomendamos o uso de casos de sentença e evitar o uso de todas as tampas para localização e legibilidade.

![tipógrafo móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Campos e flyouts

Campos são áreas onde os usuários podem inserir texto. Os flyouts são mais leves do que os diálogos e aparecem do painel superior.

#### <a name="list-controls"></a>Controles de lista

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Controles de campo

![controles de campo móveis](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Considerações do desenvolvedor

Quando você está construindo um aplicativo que inclui uma guia, você precisa considerar (e testar) como sua guia funcionará tanto no Clientes Microsoft Teams Android quanto no iOS. As seções abaixo descrevem alguns dos principais cenários que você precisa considerar.

### <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizá-lo Teams JavaScript SDK para pelo menos a versão 1.4.1.

### <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com quaisquer intervalos apropriadamente, fornecendo uma mensagem contextual ao usuário. Você também deve fornecer indicadores de progresso para fornecer feedback aos seus usuários para quaisquer processos de longo prazo.

> [!NOTE]
> As guias são habilitadas no celular somente após o aplicativo ser adicionado a uma lista de permissões, com base na entrada da equipe de aprovação. Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com.

### <a name="testing-on-mobile-clients"></a>Testes em clientes móveis

Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar o [DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela está em execução. Recomendamos que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.

### <a name="distribution"></a>distribuição

Os aplicativos listados na loja Teams devem ser aprovados para que o uso do celular funcione corretamente no Teams cliente móvel. A disponibilidade e o comportamento da guia dependem se seu aplicativo é aprovado.

#### <a name="apps-on-teams-store-approved-for-mobile"></a>Aplicativos na loja Teams aprovados para celular

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado na loja Teams e aprovado para uso móvel:

|Recursos   |Disponibilidade móvel?   |Comportamento móvel|
|----------|-----------|------------|
|Canal <br /> e aba de grupo|Sim|A guia é aberta no Teams cliente móvel usando a configuração do seu `contentUrl` aplicativo.|
|Aplicativo pessoal|Sim|Cada guia na guia do aplicativo pessoal é aberta no Teams cliente móvel usando sua respectiva `contentUrl` configuração.|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Aplicativos na loja Teams não aprovados para celular

A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado na loja Teams, mas não aprovado para uso móvel:

| Recursos | Disponibilidade móvel? | Comportamento móvel |
|----------|-----------|------------|
|Guia de canal e grupo|Sim|A guia é aberta no navegador padrão do dispositivo em vez do Teams cliente móvel usando a configuração do seu `websiteUrl` aplicativo, que também deve ser incluída na função do seu código fonte `setSettings()` [](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true). No entanto, os usuários ainda podem visualizar a guia no Teams cliente móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Open**, o que aciona a configuração do seu `contentUrl` aplicativo.|
|Aplicativo pessoal|Não|Não aplicável|

#### <a name="apps-not-on-teams-store"></a>Aplicativos que não estão na loja Teams

Se você estiver carregando seu aplicativo ou publicando para o catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que Teams aplicativos de loja aprovados pela Microsoft para dispositivos móveis.
