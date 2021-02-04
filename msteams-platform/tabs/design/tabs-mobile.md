---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
ms.topic: conceptual
keywords: diretrizes de design de equipes guias móveis de estrutura de referência de aplicativos pessoais
ms.openlocfilehash: 70ff46e446b146b134f34830e8867133cbeeca14
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093285"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

> [!NOTE]
> Se você optar por que sua guia canal/grupo apareça em clientes móveis do Teams, a configuração deve ter um valor para `setSettings()` a `websiteUrl` propriedade (veja abaixo).

Guias personalizadas podem fazer parte de um canal, chat em grupo ou aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot um-para-um).

Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta do aplicativo. O aplicativo só pode ser instalado a partir de um cliente da Web ou de desktop e pode levar até 24 horas para aparecer em clientes móveis.

As guias de canal também estão disponíveis em dispositivos móveis. O comportamento padrão atualmente é usar o seu `websiteUrl` para iniciar a guia em uma janela do navegador. No entanto, eles podem ser carregados em um cliente móvel clicando no menu de estouro ao lado da guia e escolhendo Abrir , que usará a guia para carregar a guia dentro do cliente móvel do `...`  `contentUrl` Teams.

## <a name="accessing-personal-tabs"></a>Acessando guias pessoais

A ilustração a seguir mostra como você acessa uma guia pessoal no celular.

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a gaveta do aplicativo móvel do Teams." border="false":::

## <a name="accessing-channel-tabs"></a>Acessar guias de canal

A ilustração a seguir mostra como você acessa uma guia de canal no celular.

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel do Teams." border="false":::

## <a name="design-considerations"></a>Considerações de design

Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal do Teams. Para criar uma experiência imersiva que se ajuste ao Teams, siga estas diretrizes.

### <a name="responsive-design"></a>Design responsivo

Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, ela precisa seguir os [princípios de design responsivo.](https://www.w3schools.com/html/html_responsive.asp) Todas as construções de chave devem ser acessíveis em dispositivos móveis, e as exibições não devem ser distorcidas. Certifique-se de que, quando sua guia for carregada em um dispositivo móvel, todos os botões e links sejam facilmente acessíveis usando a navegação baseada no dedo.

### <a name="layouts"></a>Layouts

Escolher o layout correto para a guia é importante. Você deve considerar o tipo de informação que está apresentando e escolher um layout que as organize para facilitar o consumo. Algumas opções possíveis são descritas abaixo.

#### <a name="single-canvas"></a>Tela única

Esta é uma área grande onde o trabalho é feito. O aplicativo Wiki do Teams segue esse padrão. Se você tiver um aplicativo que não separe conteúdo em componentes menores, isso seria uma boa opção.

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma guia de tela única móvel do Teams." border="false":::

#### <a name="list"></a>Listar

As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes na parte superior. É útil usar colunas que podem ser ordenadas. Ações podem ser adicionadas a cada item de lista no menu de re elipses.

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista móvel do Teams." border="false":::

#### <a name="grid"></a>Grade

Grades são úteis para mostrar elementos que são altamente visuais. Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel do Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a>Guias com bots em dispositivos móveis

O exemplo a seguir é um aplicativo pessoal que tem guias e um bot.

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Imagem mostrando como o aplicativo móvel do Teams tem guias e um bot." border="false":::

## <a name="ui-components"></a>Componentes da interface do usuário

### <a name="color-palettes"></a>Paletas de cores

Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Teams. Como o teams mobile tem dois temas coloridos (claro e escuro), é uma boa ideia garantir que seu aplicativo tenha uma ótima aparência em ambos.

#### <a name="light-color"></a>Cor clara

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a>Cor escura

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a>Botões e controles

A maneira como os botões são estilcionados ajuda a comunicar o tipo de ação que disparam. Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase. Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone. Para comunicar níveis diferentes em uma hierarquia, projetamos botões primários e secundários em cada categoria.

#### <a name="buttons"></a>Botões

Botões primários e secundários.

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a>Controles de seleção

Botões de rádio, caixas de seleção e alternâncias.

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a>Mételets e suar

![quedas ereção](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a>Tipografia

A tipografia deve ser clara e proposital. Enfatizar informações importantes e evitar usar várias fontes e tamanhos para reduzir a confusão. Recomendamos usar o caso de sentença e evitar o uso de maiúsculas para localização e legibilidade.

![tipográfico móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a>Campos e flyouts

Campos são áreas onde os usuários podem inserir texto. Os flyouts são mais leves do que as caixas de diálogo e aparecem no painel superior.

#### <a name="list-controls"></a>Controles de lista

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a>Controles de campo

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a>Considerações sobre o desenvolvedor

Ao criar um aplicativo que inclui uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams para Android e iOS. As seções a seguir destacam alguns dos principais cenários que você precisa considerar.

### <a name="testing-on-mobile-clients"></a>Teste em clientes móveis

Você precisa validar se a guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução. Recomendamos que você teste em dispositivos de alto e baixo desempenho, bem como em um tablet.

### <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK JavaScript do Teams para pelo menos a versão 1.4.1.

### <a name="low-bandwidth-and-intermittent-connections"></a>Baixa largura de banda e conexões intermitentes

Clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com os tempos-tempos de forma adequada, fornecendo uma mensagem contextual para o usuário. Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.

> [!NOTE]
> As guias são habilitadas no celular somente depois que o aplicativo é adicionado a uma lista de autorização, com base na entrada da equipe de aprovação. Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com. 