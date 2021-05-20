---
title: Empacote seu aplicativo
description: Aprenda a empacotar seu aplicativo Microsoft Teams para testes, upload e publicação na loja.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 219e2d5341707ed51b7e0a3a8077f93df9eac640
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565211"
---
# <a name="create-a-microsoft-teams-app-package"></a>Crie um pacote de aplicativo Microsoft Teams

Você precisa de um pacote de aplicativo no entanto, você planeja distribuir seu aplicativo Microsoft Teams. Um pacote válido é um arquivo ZIP que contém o seguinte:

* **Manifesto do aplicativo**: Descreve como seu aplicativo está configurado, incluindo seus recursos, recursos necessários e outros atributos importantes.
* **Ícones do** aplicativo : Cada pacote requer um ícone de cor e contorno para o seu aplicativo.

## <a name="app-manifest"></a>Manifesto do aplicativo

Seu arquivo manifesto do aplicativo deve estar no nível superior do pacote com o nome `manifest.json` . 

Ao publicar na loja Teams, certifique-se de que seu manifesto faz referência ao último [esquema](~/resources/schema/manifest-schema.md).

## <a name="app-icons"></a>Ícones de aplicativos

Seu pacote de aplicativos deve incluir duas versões PNG do ícone do seu aplicativo: uma versão colorida e de contorno.

> [!Note]
> Se o seu aplicativo tiver uma extensão de bot ou mensagens, seus ícones também serão incluídos no registro do seu Microsoft Azure Bot Service.

Para que seu aplicativo passe Teams revisão da loja, esses ícones devem atender aos seguintes requisitos de tamanho.

### <a name="color-icon"></a>Ícone de cor

A versão colorida do seu ícone é exibida na maioria dos cenários Teams e deve ser de 192x192 pixels. Seu símbolo de ícone (96x96 pixels) pode ser de qualquer cor, mas deve sentar-se em um fundo quadrado sólido ou totalmente transparente.

Teams planta automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot. Para cortar o símbolo sem perder nenhum detalhe, inclua 48 pixels de preenchimento em torno de seu símbolo.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams ícone de cores e orientação de design." border="false":::

### <a name="outline-icon"></a>Ícone de contorno

Um ícone de contorno é exibido em dois cenários:

* Quando seu aplicativo está em uso e "içado" na barra de aplicativos no lado esquerdo de Teams.
* Quando um usuário fixa a extensão de mensagens do seu aplicativo.

O ícone deve ser de 32x32 pixels. Pode ser branco com um fundo transparente ou transparente com um fundo branco (nenhuma outra cor é permitida). O ícone de contorno não deve ter nenhum preenchimento extra em torno do símbolo.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams orientação de design de ícones de contorno." border="false":::

### <a name="best-practices"></a>Práticas recomendadas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar seus ícones de aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Faça: Siga as diretrizes precisas do ícone de contorno

Os valores RGB de branco usados em seu ícone devem ser Vermelho: 255, Verde: 255, Azul: 255. Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido para 0.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do seu aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Não: Crop em uma forma quadrada circular ou arredondada

O ícone de cor enviado no pacote do aplicativo deve ser quadrado. Não vire os cantos do seu ícone. Teams ajusta automaticamente o raio do canto.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Não: Copie outras marcas

Seus ícones não devem imitar nenhum produto protegido por direitos autorais que você não possui. Por exemplo, um design semelhante a um produto ou marca da Microsoft.

### <a name="examples"></a>Exemplos

Veja como os ícones dos aplicativos aparecem em diferentes Teams recursos e contextos.

#### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo parece em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a>Bot (canal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a>Extensão de mensagem

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<>de texto alt " border="false":::

## <a name="next-step"></a>Próxima etapa

Escolha como planeja distribuir seu aplicativo:

> [!div class="nextstepaction"]
> [Carregar lateralmente seu aplicativo em Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Publique seu aplicativo em sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Publique seu aplicativo na loja](~/concepts/deploy-and-publish/appsource/publish.md)
