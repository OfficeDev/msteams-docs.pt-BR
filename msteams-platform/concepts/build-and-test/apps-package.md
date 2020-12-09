---
title: Empacotar seu aplicativo
description: Saiba como empacotar seu aplicativo do Microsoft Teams para testar, carregar e armazenar publicação.
ms.topic: conceptual
ms.openlocfilehash: 6929375c8d6a1602f01d83d15bfa0dab7f02a664
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605259"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a>Criar um pacote de aplicativos para seu aplicativo do Microsoft Teams

Os aplicativos no Teams são definidos por um arquivo JSON de manifesto de aplicativo e agrupados em um pacote de aplicativos com seus ícones. Você precisará de um pacote de aplicativos para carregar e instalar seu aplicativo no Microsoft Teams e publicar no catálogo de aplicativos de sua linha de negócios ou no AppSource.

Um pacote de aplicativos do Microsoft Teams é um arquivo. zip que contém o seguinte:

* Um arquivo de manifesto chamado `manifest.json` , que especifica os atributos do seu aplicativo e aponta para os recursos necessários para sua experiência, como o local da sua página de configuração da guia ou a ID do aplicativo da Microsoft para o bot.
* [Ícones de cor e estrutura de tópicos para seu aplicativo](#app-icons).

## <a name="creating-a-manifest"></a>Criar um manifesto

O *Teams app Studio* pode ajudar a configurar seu manifesto. Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões. Confira [visão geral do App Studio](~/concepts/build-and-test/app-studio-overview.md).

O arquivo de manifesto deve ser nomeado como "manifest.js" e estar no nível superior do pacote de carregamento. Observe que manifestos e pacotes criados anteriormente podem oferecer suporte a uma versão mais antiga do esquema. Para aplicativos do Teams e especialmente o envio do AppSource (anteriormente Office Store), você deve usar o [esquema de manifesto](~/resources/schema/manifest-schema.md)atual.

> [!TIP]
> Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código:
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="app-icons"></a>Ícones de aplicativos

Seu pacote de aplicativos deve incluir duas versões de PNG do seu ícone de aplicativo — um ícone de cor e um ícone de estrutura de tópicos. Para seu aplicativo passar a revisão do AppSource, esses ícones devem atender aos seguintes requisitos de tamanho.

> [!Note]
> Se seu aplicativo tiver um bot ou uma extensão de mensagens, seus ícones também serão incluídos no registro do serviço de bot do Microsoft Azure.

### <a name="color-icon"></a>Ícone de cor

A versão de cores do ícone é exibida na maioria dos cenários do Teams e deve ser 192x192 pixels. O símbolo de ícone (96x96 pixels) pode ser qualquer cor ou cores, mas deve estar em um plano de fundo de quadrado sólido ou totalmente transparente.

O Microsoft Teams corta automaticamente o ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma de hexágonos em cenários de bot. Inclua 48 pixels de preenchimento em torno do símbolo para que esses aparas possam ser feitos sem perder nenhum detalhe.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Ícone de cor da equipe diretrizes de design." border="false":::

### <a name="outline-icon"></a>Ícone de estrutura de tópicos

Um ícone de estrutura de tópicos é exibido em dois cenários:

* Quando seu aplicativo está em uso e "em guindaste" na barra de aplicativos à esquerda do teams.
* Quando um usuário fixa a extensão de mensagens do seu aplicativo.

O ícone deve ter 32x32 pixels. Pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida). O ícone de estrutura de tópicos não deve ter preenchimento extra em torno do símbolo.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Ícone de cor da equipe diretrizes de design." border="false":::

### <a name="best-practices"></a>Práticas recomendadas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como criar seus ícones de aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Faça: siga as diretrizes de ícone de estrutura de tópicos preciso

Os valores RGB de branco usados no seu ícone devem ser vermelhos: 255, verde: 255, azul: 255. Todas as outras partes do ícone de estrutura de tópicos devem ser totalmente transparentes, com o canal alfa definido como 0.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não criar seus ícones de aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Não: cortar em uma forma de quadrado circular ou arredondada

O ícone de cor enviado no pacote do aplicativo deve ser quadrado. Não arredondar os cantos do ícone. O Microsoft Teams ajusta automaticamente o raio do canto.

   :::column-end:::
:::row-end:::

### <a name="examples"></a>Exemplos

Veja como os ícones de aplicativo aparecem em diferentes recursos e contextos da equipe.

#### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo aparece em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a>Bot (canal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo procura um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a>Extensão de mensagens

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<texto alt>" border="false":::
