---
title: Projetar seu aplicativo com componentes avançados da interface do usuário
author: heath-hamilton
description: Saiba mais sobre os componentes da interface do usuário usados em Teams .
ms.author: surbhigupta
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 6f2bd9cd237751adb15db45bbd6e3cdfea35ce09
ms.sourcegitcommit: b1f9162a0bbcd276064ae9e4f1e8bccc06cb7035
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53328076"
---
# <a name="designing-your-microsoft-teams-app-with-advanced-ui-components"></a>Projetando seu aplicativo Microsoft Teams com componentes avançados da interface do usuário

Os componentes a seguir são uma combinação de [componentes](~/concepts/design/design-teams-app-basic-ui-components.md) básicos da interface do usuário que você pode usar para situações Teams de design comuns, como a navegação.

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Com base <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent interface do</a>usuário, o kit de interface do usuário Microsoft Teams inclui componentes e padrões projetados especificamente para a criação de Teams aplicativos. No kit de interface do usuário, você pode pegar e inserir os componentes listados aqui diretamente em seu design e ver mais exemplos de como usar cada componente.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="breadcrumb"></a>Trilha

Os breadcrumbs são um auxílio de navegação que transmitem a hierarquia do aplicativo. Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e proporcionam acesso de um clique a níveis mais altos nessa hierarquia.

### <a name="top-use-cases"></a>Principais casos de uso

* Hierarquia de comunicações
* Navegação

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Exemplo mostra um modelo de breadcrumb na área de trabalho." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-breadcrumb.png" alt-text="Exemplo mostra um modelo de breadcrumb no celular." border="false":::

---

## <a name="left-nav"></a>Nav esquerdo

Use a navegação esquerda para navegar por várias páginas na guia Teams. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.

### <a name="top-use-cases"></a>Principais casos de uso

* Navegue por várias páginas em uma Teams guia.
* Separar aplicativos complexos em várias páginas.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Exemplo mostra um modelo de nav esquerdo na área de trabalho." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-left-nav.png" alt-text="Exemplo mostra um modelo de nav esquerdo no celular." border="false":::

---

## <a name="notification-bar"></a>Notification bar

Uma barra de notificação é uma área dedicada para exibir uma mensagem breve e importante que não exige que o usuário tome medidas imediatas. Cores e ícones específicos de plano de fundo estão associados a tipos específicos de mensagens (consulte abaixo).

### <a name="top-use-cases"></a>Principais casos de uso

* Mensagens críticas, erros e avisos
* Mensagens de sucesso
* Mensagens informativas ou promocionais

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Exemplo mostra modelos de interface do usuário da barra de notificação na área de trabalho." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-notification-bar.png" alt-text="Exemplo mostra o modelo de interface do usuário da barra de notificação no celular." border="false":::

---

## <a name="stage"></a>Estágio

O estágio permite que os usuários exibirem conteúdo, como uma imagem, arquivo ou site, em uma grande superfície no Teams sem alternar contexto. O estágio é principalmente para exibir conteúdo. Não use estágio para interações complexas.

Saiba como implementar o [estágio](~/tabs/tabs-link-unfurling.md).

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir conteúdo em uma superfície grande dentro Teams em vez de outro aplicativo ou navegador
* Mídia em destaque ou outro conteúdo rico

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Exemplo mostra um modelo de estágio na área de trabalho." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

Seu aplicativo pode iniciar um estágio de um Cartão Adaptável, um link compartilhado ou componentes visuais (como um gráfico).

:::image type="content" source="../../assets/images/ui-templates/mobile-stage.png" alt-text="Exemplo mostra um modelo de estágio no celular." border="false":::

---

## <a name="toolbar"></a>Barra de ferramentas

Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.

### <a name="top-use-cases"></a>Principais casos de uso

* Ações contextuais no conteúdo do aplicativo
* Filtro contextual e local
* Navegação e controles de navegação

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Exemplo mostra um modelo de barra de ferramentas na área de trabalho." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-toolbar.png" alt-text="Exemplo mostra um modelo de barra de ferramentas no celular." border="false":::

---
