---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
keywords: Diretrizes de design de equipes guias de referência de aplicativos pessoais
ms.openlocfilehash: 928fb8586434eca9cc1577fd45c6b94594724d7f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672717"
---
# <a name="tabs-on-mobile"></a>Guias em dispositivos móveis

> [!Important]
> O suporte completo para guias em clientes móveis estará disponível em breve. Para se preparar para esta alteração, você deve seguir as orientações ao criar suas guias. Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md). e as `...` guias de chat de canal/grupo estão disponíveis no menu de excedentes da guia.
>
> Quando o suporte completo para guias é liberado:
>
> * Todas as guias sempre estarão disponíveis em dispositivos móveis
> * O `contentUrl` **será carregado no cliente do Mobile Teams**.
> * Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.
> * Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.

As guias personalizadas podem fazer parte de um canal, de um chat de grupo ou de um aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot de um para um).

Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta de aplicativos. O aplicativo só pode ser instalado a partir de um cliente da Web ou da área de trabalho, e pode levar até 24 horas para aparecer em clientes móveis.

As guias de grupo e canal também estão disponíveis em clientes móveis. O comportamento padrão é atualmente usar o `websiteUrl` para iniciar sua guia em uma janela do navegador. No entanto, eles podem ser carregados em um cliente móvel clicando `...` no menu de excedentes ao lado da guia e escolhendo **abrir**, que `contentUrl` usará o para carregar a guia dentro do cliente móvel do Microsoft Teams.

![gaveta de aplicativos móveis](~/assets/images/app-drawer.png)

## <a name="developer-considerations-for-mobile-support"></a>Considerações de desenvolvedor para suporte móvel

Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams Android e iOS. As seções a seguir descrevem alguns dos principais cenários que você precisa considerar.

### <a name="testing-on-mobile-clients"></a>Testando clientes móveis

Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades. Para dispositivos Android, você pode usar o [devtools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto estiver sendo executado. Recomendamos que você teste em dispositivos de desempenho alto e baixo, bem como em um Tablet.

### <a name="responsive-design"></a>Design responsivo

Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, é necessário seguir princípios de [design responsivos](https://www.w3schools.com/html/html_responsive.asp) . Todas as construções de chave devem estar acessíveis em dispositivos móveis, e os modos de exibição não devem ser distorcidos. Verifique se a guia é carregada em um dispositivo móvel, se todos os botões e links estão facilmente acessíveis usando a navegação baseada em Finger.

### <a name="authentication"></a>Autenticação

Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK do teams JS para pelo menos a versão 1.4.1.

### <a name="low-bandwidth--intermittent-connections"></a>Baixa largura de banda & conexões intermitentes

Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes. Seu aplicativo deve lidar com os tempos limite de forma adequada fornecendo uma mensagem contextual para o usuário. Você também deve fazer os indicadores de progresso do usuário para fornecer comentários aos seus usuários para todos os processos de execução demorada.

## <a name="design-considerations-for-mobile"></a>Considerações de design para dispositivos móveis

Nossa plataforma móvel permite que os aplicativos sejam uma experiência de imersão com o conteúdo do aplicativo tirando toda a tela da navegação do teams principal. Para criar uma experiência de imersão que se ajuste perfeitamente no cliente Microsoft Teams, siga as diretrizes abaixo.

### <a name="layouts"></a>Layouts

Escolher o layout correto para sua guia é importante. Considere o tipo de informação que você está apresentando e escolha um layout que a organize para facilitar o consumo. Algumas opções potenciais estão descritas abaixo.

#### <a name="single-canvas"></a>Tela única

Esta é uma grande área onde o trabalho é concluído. O aplicativo wiki segue esse padrão. Se você tiver um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.

![layout de tela única](~/assets/images/mobile-single-canvas.png)

#### <a name="list"></a>Listar

As listas são ótimas para classificar e filtrar grandes quantidades de dados e são excelentes para manter as coisas mais importantes na parte superior. É útil usar colunas classificável. As ações podem ser adicionadas a cada item de lista no menu de reticências.

![layout de lista](~/assets/images/mobile-list.png)

#### <a name="grid"></a>Encaixe

As grades são úteis para mostrar elementos que são altamente visuais. Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.

![layout de grade](~/assets/images/mobile-grid.png)

### <a name="tabs-with-bots-on-mobile"></a>Guias com bots em dispositivos móveis

Veja a seguir um exemplo de aplicativo pessoal que contém duas guias estáticas e um bot.

![guias e bots em dispositivos móveis](~/assets/images/mobile-tab-with-bot.png)

### <a name="ui-components"></a>Componentes da interface do usuário

#### <a name="color-palettes"></a>Paletas de cores

Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Microsoft Teams. Como o Microsoft Teams Mobile tem dois temas de cor (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.

##### <a name="light-color"></a>Cor clara

![paleta de cores claras](~/assets/images/light-color.png)

##### <a name="dark-color"></a>Cor escura

![paleta de cores escuras](~/assets/images/dark-color.png)

#### <a name="buttons-and-controls"></a>Botões e controles

A maneira como os botões são estilizados ajuda a comunicar o tipo de ação que eles disparam. Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase. Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone. Para comunicar diferentes níveis em uma hierarquia, projetamos os botões principal e secundário dentro de cada categoria.

![recolhe](~/assets/images/buttons.png)

![controles de seleção](~/assets/images/selection-controls.png)

![Chiclets e pills](~/assets/images/chiclets-and-pills.png)

#### <a name="typography"></a>Tipografia

A tipografia deve ser clara e proposital. Enfatize informações importantes e evite usar várias fontes e tamanhos para reduzir a confusão. Recomendamos o uso de maiúsculas e minúsculas e evitar o uso de todos os Caps para a localização e a legibilidade.

![Typograph móvel](~/assets/images/mobile-typography.png)

#### <a name="fields-and-flyouts"></a>Campos e submenus

Os campos são áreas onde os usuários podem inserir texto. Os submenus são mais leves do que os diálogos e aparecem no painel superior.

##### <a name="list-controls"></a>Controles de lista

![controles de lista móvel](~/assets/images/mobile-list-controls.png)

##### <a name="field-controls"></a>Controles de campo

![controles de campo móvel](~/assets/images/mobile-field-controls.png)
