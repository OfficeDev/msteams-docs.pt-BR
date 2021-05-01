---
title: Empacote seu aplicativo
description: Saiba como empacotar seu aplicativo Microsoft Teams para testar, carregar e armazenar publicação.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: e477539a9b8eaa0c869a2070fcd20b74aecfe490
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101699"
---
# <a name="create-a-microsoft-teams-app-package"></a>Criar um pacote Microsoft Teams aplicativo

Você precisa de um pacote de aplicativos, no entanto, planeja distribuir seu Microsoft Teams aplicativo. Um pacote válido é um arquivo ZIP que contém o seguinte:

* **Manifesto do aplicativo**: descreve como seu aplicativo está configurado, incluindo seus recursos, recursos necessários e outros atributos importantes.
* **Ícones do aplicativo:** cada pacote requer uma cor e um ícone de contorno para seu aplicativo.

## <a name="app-manifest"></a>Manifesto do aplicativo

O arquivo de manifesto do aplicativo deve estar no nível superior do pacote com o nome `manifest.json` . 

Ao publicar no Teams, certifique-se de que seu manifesto faça referência ao [esquema mais recente.](~/resources/schema/manifest-schema.md)

## <a name="app-icons"></a>Ícones de aplicativo

Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: uma versão de cor e de contorno.

> [!Note]
> Se seu aplicativo tiver um bot ou uma extensão de mensagens, seus ícones também serão incluídos no registro do serviço Microsoft Azure Bot.

Para que seu aplicativo passe na Teams de armazenamento, esses ícones devem atender aos seguintes requisitos de tamanho.

### <a name="color-icon"></a>Ícone de cor

A versão colorida do ícone é exibida na maioria Teams cenários e deve ter 192 x 192 pixels. Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.

Teams automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot. Para cortar o símbolo sem perder detalhes, inclua 48 pixels de preenchimento ao redor do símbolo.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams de cores e diretrizes de design." border="false":::

### <a name="outline-icon"></a>Ícone de contorno

Um ícone de contorno é exibido em dois cenários:

* Quando seu aplicativo estiver em uso e "içada" na barra de aplicativos no lado esquerdo do Teams.
* Quando um usuário fixa a extensão de mensagens do aplicativo.

O ícone deve ter 32 x 32 pixels. Ele pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida). O ícone de contorno não deve ter nenhum preenchimento extra ao redor do símbolo.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams diretrizes de design de ícone de estrutura." border="false":::

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

O ícone de cor enviado no pacote do aplicativo deve ser quadrado. Não arredonde os cantos do ícone. Teams ajusta automaticamente o raio do canto.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Não: copiar outras marcas

Seus ícones não devem imitar produtos protegidos por direitos autorais que você não possui (por exemplo, um design semelhante a um produto ou marca da Microsoft).

### <a name="examples"></a>Exemplos

Veja como os ícones de aplicativo aparecem em diferentes Teams recursos e contextos.

#### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando a aparência de um ícone de aplicativo em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a>Bot (canal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a>Extensão de mensagem

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<texto alt>" border="false":::

## <a name="next-step"></a>Próxima etapa

Escolha como você planeja distribuir seu aplicativo:

> [!div class="nextstepaction"]
> [Fazer sideload do aplicativo Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Publicar seu aplicativo em sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Publicar seu aplicativo na loja](~/concepts/deploy-and-publish/appsource/publish.md)
