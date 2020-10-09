---
title: Empacotar seu aplicativo
description: Saiba como empacotar seu aplicativo para teste, upload e publicação no Microsoft Teams
keywords: pacote de aplicativos do teams
ms.topic: conceptual
ms.openlocfilehash: d2d49dcc5c4ccada0a75de5df6fda29a60e809f6
ms.sourcegitcommit: 560bf433129c16888135879e2703dbdeb38ec99f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48397698"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Criar um pacote de aplicativos para seu aplicativo do Microsoft Teams

Os aplicativos no Teams são definidos por um arquivo JSON de manifesto de aplicativo e agrupados em um pacote de aplicativos com seus ícones. Você precisará de um pacote de aplicativos para carregar e instalar seu aplicativo no Microsoft Teams e publicar no catálogo de aplicativos de sua linha de negócios ou no AppSource.

Um pacote de aplicativos do Microsoft Teams é um arquivo. zip que contém o seguinte:

* Um arquivo de manifesto chamado "manifest.js", que especifica os atributos do seu aplicativo e aponta para os recursos necessários para sua experiência, como o local da sua página de configuração da guia ou a ID do aplicativo da Microsoft para seu bot.
* Um ícone de "estrutura de tópicos" transparente e um ícone de "cor" completo. Consulte os [ícones](#icons) mais adiante neste tópico para obter mais informações.

## <a name="creating-a-manifest"></a>Criar um manifesto

O *Teams app Studio* pode ajudar a configurar seu manifesto. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Confira [visão geral do App Studio](~/concepts/build-and-test/app-studio-overview.md).

O arquivo de manifesto deve ser nomeado como "manifest.js" e estar no nível superior do pacote de carregamento. Observe que manifestos e pacotes criados anteriormente podem oferecer suporte a uma versão mais antiga do esquema. Para aplicativos do Teams e especialmente o envio do AppSource (anteriormente Office Store), você deve usar o [esquema de manifesto](~/resources/schema/manifest-schema.md)atual.

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código:
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`

## <a name="icons"></a>Ícones

> [!Note]
> Se seu aplicativo contiver um bot ou uma extensão de mensagens, os ícones usados serão os ícones carregados no seu registro de bot na estrutura do bot.

O Microsoft Teams requer dois ícones para a sua experiência de aplicativo, para serem usados no produto. Os ícones devem ser incluídos no pacote e referenciados por meio de caminhos relativos no manifesto. O comprimento máximo de cada caminho é de 2048 bytes, e o formato do ícone é. png.

### <a name="color"></a>color

O `color` ícone é usado no Microsoft Teams (em aplicativos e galerias de guias, bots, submenus e assim por diante). Este ícone deve ser 192x192 pixels. Seu ícone pode ser qualquer cor (ou cores), mas o plano de fundo deve ser a cor de destaque da marca. Ela também deve ter uma pequena quantidade de preenchimento em torno do ícone para acomodar o corte de hexágonos para a versão de bot do ícone.

### <a name="outline"></a>outline

O `outline` ícone é usado nestes lugares: a barra de aplicativos e as extensões de mensagens que o usuário marcou como "favorito". Este ícone deve ter 32x32 pixels. O ícone de estrutura de tópicos deve conter somente branco e transparência (sem outras cores). O ícone pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco. O ícone de estrutura de tópicos não deve ter preenchimento adicional ao redor do ícone e deve ser tão cortado possível e ainda manter as dimensões de 32x32. Veja alguns exemplos bons:

> [!TIP]
>  * A cor deve ser "branco" no RGB (vermelho: 255, verde: 255, azul: 255).
>  * Todas as outras partes do ícone devem ser transparentes.
>  * Para passar, o ícone pequeno deve ser totalmente transparente, o canal alfa para ser 0 e qualquer outro valor é uma falha.

![Exemplos de ícones de tópicos](~/assets/images/icons/sample20x20s.png)

Por exemplo, digamos que sua empresa seja contoso. Você enviaria dois ícones:

![Apresentação de ícones](~/assets/images/framework/framework_submit_icon.png)

Veja como os ícones aparecerão na interface do usuário:

#### <a name="bot-and-chiclet-in-channel-view"></a>Bot e Chiclet no modo de exibição de canal

![Bot e UX do Chiclet](~/assets/images/icons/botandchiclet.png)

#### <a name="flyout"></a>Janelas

![Submenu da Contoso de exemplo](~/assets/images/icons/flyout.png)

#### <a name="app-bar-and-home-screen"></a>Barra de aplicativos e tela inicial

![Exemplo de barra de aplicativos da Contoso homescreen](~/assets/images/icons/appbarhomescreen.png)
