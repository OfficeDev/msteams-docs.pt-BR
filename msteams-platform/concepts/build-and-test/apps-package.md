---
title: Empacote o seu aplicativo
description: Saiba como empacotar seu aplicativo do Microsoft Teams para testar, carregar e armazenar a publicação.
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 7b895f30230a71db5953ffebc5dce2aa04972abb
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63356067"
---
# <a name="create-a-microsoft-teams-app-package"></a>Criar um pacote de aplicativo do Microsoft Teams

Você precisa de um pacote de aplicativos, no entanto, planeja distribuir seu aplicativo do Microsoft Teams. Um pacote válido é um arquivo ZIP que contém o seguinte:

* **Manifesto do aplicativo**: descreve como seu aplicativo está configurado, incluindo suas características, recursos necessários e outros atributos importantes.
* **Ícones do aplicativo**: cada pacote requer uma cor e um ícone de contorno para seu aplicativo.

## <a name="teams-doesnt-host-your-app"></a>O Teams não hospeda seu aplicativo

Quando um usuário instala seu aplicativo no Teams, ele instala um pacote de aplicativo que contém um único arquivo de configuração (também conhecido como manifesto do aplicativo) e os ícones do aplicativo. A lógica e o armazenamento de dados do aplicativo são hospedados em outro lugar, como no localhost durante o desenvolvimento e nos Serviços Web do Azure. O Teams acessa esses recursos via HTTPS.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Ilustração mostrando a hospedagem de aplicativos para aplicativos do Teams" border="true":::

## <a name="app-manifest"></a>Manifesto do aplicativo

O arquivo de manifesto do aplicativo deve estar no nível superior do pacote com o nome `manifest.json`.

Ao publicar no repositório do Teams, certifique-se de que seu manifesto faça referência ao [esquema](~/resources/schema/manifest-schema.md) mais recente.

## <a name="app-icons"></a>Ícones do aplicativo

Seu pacote de aplicativos deve incluir duas versões .png do ícone de seu aplicativo: Uma versão colorida e de contorno.

> [!Note]
> Se seu aplicativo tiver um bot ou uma extensão de mensagens, seus ícones também serão incluídos no registro do serviço de Bot do Microsoft Azure.

Para que seu aplicativo passe na revisão do repositório do Teams, esses ícones devem atender aos requisitos de tamanho a seguir.

### <a name="color-icon"></a>Ícone de cor

A versão colorida do seu ícone é exibida na maioria dos cenários do Teams e deve ter 192 x 192 pixels. Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.

O Teams corta automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários do bot. Para cortar o símbolo sem perder detalhes, inclua 48 pixels de preenchimento ao redor do símbolo.

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams de cores e diretrizes de design." border="false":::

### <a name="outline-icon"></a>Ícone de contorno

Um ícone de contorno é exibido em dois cenários:

* Quando seu aplicativo estiver em uso e "hospedado" na barra de aplicativos no lado esquerdo do Teams.
* Quando um usuário fixa a extensão de mensagens do aplicativo.

O ícone deve ter 32 x 32 pixels. Ele pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida). O ícone de contorno não deve ter nenhum preenchimento extra ao redor do símbolo.

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Diretrizes de design do ícone de estrutura do Teams." border="false":::

### <a name="best-practices"></a>Práticas recomendadas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar os ícones do aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a>Fazer: siga as diretrizes precisas do ícone de contorno

Os valores RGB de branco usados no seu ícone devem ser vermelho: 255, verde: 255,azul: 255. Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido como 0.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a>Não: corte em uma forma quadrada circular ou arredondada

O ícone de cor enviado no pacote do aplicativo deve ser quadrado. Não arredonde os cantos do ícone. O Teams ajusta automaticamente o raio do canto.

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a>Não: copiar outras marcas

Seus ícones não devem imitar produtos protegidos pelos direitos autorais que você não possui. Por exemplo, um design semelhante a um produto ou marca da Microsoft.

### <a name="examples"></a>Exemplos

Veja como os ícones de aplicativo aparecem em diferentes recursos e contextos do Teams.

#### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando a aparência de um ícone de aplicativo em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a>Bot (canal)

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a>Extensão de mensagem

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<alt text>" border="false":::

## <a name="next-step"></a>Próxima etapa

Escolha como você planeja distribuir seu aplicativo:

> [!div class="nextstepaction"]
> [Faça o sideload do seu aplicativo do Teams](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [Publique seu aplicativo na sua organização](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [Publique seu aplicativo na loja](~/concepts/deploy-and-publish/appsource/publish.md)

## <a name="see-also"></a>Confira também

[Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)
