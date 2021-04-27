---
title: Empacote seu aplicativo
description: Saiba como empacotar seu aplicativo do Microsoft Teams para testar, carregar e armazenar publicação.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: c8341f3d83b5e6610e44276d6732affa1d1c1e91
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020137"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Criar um pacote de aplicativos para seu aplicativo do Microsoft Teams

Os aplicativos no Teams são definidos por um arquivo JSON de manifesto do aplicativo e agrupados em um pacote de aplicativos com seus ícones. Você precisará de um pacote de aplicativos para carregar e instalar seu aplicativo no Teams e publicar no catálogo de aplicativos linha de negócios ou no AppSource.

Um pacote de aplicativos do Teams é um arquivo .zip que contém o seguinte:

* Um arquivo de manifesto chamado , que especifica atributos do seu aplicativo e aponta para os recursos necessários para sua experiência, como o local de sua página de configuração de tabulação ou a ID do aplicativo Microsoft para seu `manifest.json` bot.
* [Ícones de cor e de contorno para seu aplicativo](#app-icons).

## <a name="creating-a-manifest"></a>Criando um manifesto

**O Teams App Studio** pode ajudar a configurar seu manifesto. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Para obter mais informações, consulte [Visão geral do App Studio](~/concepts/build-and-test/app-studio-overview.md).

Seu arquivo de manifesto deve ser chamado de "manifest.json" e estar no nível superior do pacote de carregamento. Observe que manifestos e pacotes construídos anteriormente podem dar suporte a uma versão mais antiga do esquema. Para aplicativos do Teams e especialmente o envio do AppSource (antigo Office Store), você deve usar o esquema de [manifesto atual.](~/resources/schema/manifest-schema.md)

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar IntelliSense suporte semelhante do editor de código:
>
> `"$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",`
 
## <a name="app-icons"></a>Ícones de aplicativo

Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: um ícone de cor e um ícone de contorno. Para que seu aplicativo passe na revisão do AppSource, esses ícones devem atender aos seguintes requisitos de tamanho.

> [!Note]
> Se seu aplicativo tiver um bot ou extensão de mensagens, seus ícones também serão incluídos no registro do Serviço de Bot do Microsoft Azure.

### <a name="color-icon"></a>Ícone de cor

A versão colorida do ícone é exibida na maioria dos cenários do Teams e deve ter 192 x 192 pixels. Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor ou cores, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.

O Teams cria automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot. Inclua 48 pixels de preenchimento ao redor do símbolo para que essas colheitas possam ser feitas sem perder detalhes.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Ícone de cores e diretrizes de design do Teams." border="false":::

### <a name="outline-icon"></a>Ícone de contorno

Um ícone de contorno é exibido em dois cenários:

* Quando seu aplicativo está em uso e "içada" na barra de aplicativos à esquerda do Teams.
* quando um usuário fixa a extensão de mensagens do aplicativo.

O ícone deve ter 32 x 32 pixels. Ele pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida). O ícone de contorno não deve ter nenhum preenchimento extra ao redor do símbolo.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Diretrizes de design de ícone de estrutura do Teams." border="false":::

### <a name="best-practices"></a>Práticas recomendadas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar ícones do aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Fazer: siga as diretrizes precisas do ícone de contorno

Os valores RGB de branco usados em seu ícone devem ser Vermelho: 255, Verde: 255, Azul: 255. Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido como 0.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Não: Corte em uma forma quadrada circular ou arredondada

O ícone de cor enviado no pacote do aplicativo deve ser quadrado. Não arredonde os cantos do ícone. O Teams ajusta automaticamente o raio de canto.

   :::column-end:::
:::row-end:::

### <a name="examples"></a>Exemplos

Veja como os ícones de aplicativo aparecem em diferentes recursos e contextos do Teams.

#### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando a aparência de um ícone de aplicativo em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a>Bot (canal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a>Extensão de mensagem

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<texto alt>" border="false":::
