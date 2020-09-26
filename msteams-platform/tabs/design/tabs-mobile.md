---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
keywords: Diretrizes de design de equipes guias de referência de aplicativos pessoais
ms.openlocfilehash: a1939465b04a1fe4b803efaf83402852ca536059
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279754"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

> [!NOTE]
> Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um valor para a `websiteUrl` Propriedade (veja abaixo).

As guias personalizadas podem fazer parte de um canal, de um chat de grupo ou de um aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot de um para um).

Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta de aplicativos. O aplicativo só pode ser instalado a partir de um cliente da Web ou da área de trabalho, e pode levar até 24 horas para aparecer em clientes móveis.

As guias de canal também estão disponíveis em dispositivos móveis. O comportamento padrão é atualmente usar o `websiteUrl` para iniciar sua guia em uma janela do navegador. No entanto, eles podem ser carregados em um cliente móvel clicando no `...` menu de excedentes ao lado da guia e escolhendo **abrir**, que usará o `contentUrl` para carregar a guia dentro do cliente móvel do Microsoft Teams.

## <a name="accessing-personal-tabs"></a>Acessar guias pessoais

A ilustração a seguir mostra como acessar uma guia pessoal no Mobile.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a gaveta de aplicativos móveis do Microsoft Teams." border="false":::

## <a name="accessing-channel-tabs"></a>Acessar guias de canal

A ilustração a seguir mostra como você acessa uma guia canal no Mobile.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel do teams." border="false":::

## <a name="design-considerations"></a>Considerações de design

Nossa plataforma móvel permite que os aplicativos sejam uma experiência de imersão com o conteúdo do aplicativo tirando toda a tela da navegação do teams principal. Para criar uma experiência de imersão adequada ao Teams, siga estas diretrizes.

### <a name="responsive-design"></a>Design responsivo

Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, é necessário seguir princípios de [design responsivos](https://www.w3schools.com/html/html_responsive.asp) . Todas as construções de chave devem estar acessíveis em dispositivos móveis, e os modos de exibição não devem ser distorcidos. Verifique se a guia é carregada em um dispositivo móvel, se todos os botões e links estão facilmente acessíveis usando a navegação baseada em Finger.

### <a name="layouts"></a>Layouts

Escolher o layout correto para sua guia é importante. Considere o tipo de informação que você está apresentando e escolha um layout que a organize para facilitar o consumo. Algumas opções potenciais estão descritas abaixo.

#### <a name="single-canvas"></a>Tela única

Esta é uma grande área onde o trabalho é concluído. O aplicativo wiki do teams segue esse padrão. Se você tiver um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma guia de tela única para dispositivos móveis do Microsoft Teams." border="false":::

#### <a name="list"></a>Listar

As listas são ótimas para classificar e filtrar grandes quantidades de dados e são excelentes para manter as coisas mais importantes na parte superior. É útil usar colunas classificável. As ações podem ser adicionadas a cada item de lista no menu de reticências.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista do teams Mobile." border="false":::

#### <a name="grid"></a>Encaixe

As grades são úteis para mostrar elementos que são altamente visuais. Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel do teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Guias com bots em dispositivos móveis

O exemplo a seguir é um aplicativo pessoal que tem guias e um bot.

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo do Mobile Teams tem guias e um bot." border="false":::

## <a name="ui-components"></a>Componentes da interface do usuário

### <a name="color-palettes"></a>Paletas de cores

Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Microsoft Teams. Como o Microsoft Teams Mobile tem dois temas de cor (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.

#### <a name="light-color"></a>Cor clara

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Cor escura

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Botões e controles

A maneira como os botões são estilizados ajuda a comunicar o tipo de ação que eles disparam. Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase. Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone. Para comunicar diferentes níveis em uma hierarquia, projetamos os botões principal e secundário dentro de cada categoria.

#### <a name="buttons"></a>Botões

Botões principal e secundário.

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Controles de seleção

Botões de opção, caixas de seleção e alternações.

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Chiclets e pills

![Chiclets e pills](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Tipografia

A tipografia deve ser clara e proposital. Enfatize informações importantes e evite usar várias fontes e tamanhos para reduzir a confusão. Recomendamos o uso de maiúsculas e minúsculas e evitar o uso de todos os Caps para a localização e a legibilidade.

![Typograph móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Campos e submenus

Os campos são áreas onde os usuários podem inserir texto. Os submenus são mais simples do que as caixas de diálogo e aparecem no painel superior.

#### <a name="list-controls"></a>Controles de lista

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Controles de campo

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Considerações de desenvolvedor

Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams Android e iOS. As seções a seguir descrevem alguns dos principais cenários que você precisa considerar.

### <a name="testing-on-mobile-clients"></a>Testando clientes móveis

Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar o [devtools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto estiver sendo executado. Recomendamos que você teste em dispositivos de desempenho alto e baixo, bem como em um Tablet.

### <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK do JavaScript do Microsoft Teams para pelo menos a versão 1.4.1.

### <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com os tempos limite de forma adequada fornecendo uma mensagem contextual para o usuário. Você também deve fazer os indicadores de progresso do usuário para fornecer comentários aos seus usuários para todos os processos de execução demorada.
