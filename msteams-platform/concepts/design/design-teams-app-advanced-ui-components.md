---
title: Projetar seu aplicativo com componentes avançados da interface do usuário
author: heath-hamilton
description: Saiba mais sobre os Teams da interface do usuário, como trilhas, barra de notificação, modo de exibição de estágio, juntamente com casos de uso relevantes.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: reference
ms.openlocfilehash: 2b009d4a31181ed1794dafdb8e224b7239bebd81
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123416"
---
# <a name="designing-your-microsoft-teams-app-with-advanced-ui-components"></a>Criando seu aplicativo Microsoft Teams com componentes avançados da interface do usuário

Os componentes a seguir são uma [combinação de](~/concepts/design/design-teams-app-basic-ui-components.md) componentes básicos da interface do usuário que você pode usar para situações Teams de design comuns, como navegação.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Com base <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent interface</a> do usuário, o kit de interface do usuário do Microsoft Teams inclui componentes e padrões que são projetados especificamente para criar Teams aplicativos. No kit de interface do usuário, você pode pegar e inserir os componentes listados aqui diretamente em seu design e ver mais exemplos de como usar cada componente.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="breadcrumb"></a>Trilha

Trilhas são um auxílio de navegação que transmite a hierarquia do aplicativo. Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e permitem acesso com um clique a níveis mais altos nessa hierarquia.

### <a name="top-use-cases"></a>Principais casos de uso

* Hierarquia de comunicação
* Navegação

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/ui-templates/mobile-breadcrumb.png" alt-text="O exemplo mostra um modelo de trilha no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de trilha na área de trabalho." border="false":::

## <a name="left-nav"></a>Navegação à esquerda

Use a navegação à esquerda para navegar por várias páginas em sua Teams guia. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.

### <a name="top-use-cases"></a>Principais casos de uso

* Navegue por várias páginas em uma Teams guia.
* Dividir aplicativos complexos em várias páginas.

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/ui-templates/mobile-left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda na área de trabalho." border="false":::

## <a name="notification-bar"></a>Notification bar

Uma barra de notificação é uma área dedicada para exibir mensagens breves e importantes que não exigem que o usuário tome medidas imediatas. Cores e ícones específicos da tela de fundo são associados a tipos específicos de mensagens (veja abaixo).

Você pode implementar uma barra de notificação usando o Fluent de alerta [da interface do](https://fluentsite.z22.web.core.windows.net/0.59.0/components/alert/definition) usuário.

### <a name="top-use-cases"></a>Principais casos de uso

* Mensagens críticas, erros e avisos
* Mensagens de êxito
* Mensagens informativas ou promocionais

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/ui-templates/mobile-notification-bar.png" alt-text="O exemplo mostra o modelo de interface do usuário da barra de notificação no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="O exemplo mostra modelos de interface do usuário da barra de notificação na área de trabalho." border="false":::

## <a name="stage-view"></a>Modo de exibição de estágio

O modo de exibição de estágio permite que os usuários vejam conteúdo, como uma imagem, arquivo ou site, em uma superfície grande no Teams sem alternar o contexto. Esse componente destina-se principalmente à exibição de conteúdo. Não o use para interações complexas.

Veja como implementar o modo [de exibição de estágio](~/tabs/tabs-link-unfurling.md).

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir conteúdo em uma superfície grande dentro Teams em vez de outro aplicativo ou navegador
* Mídia em destaque ou outro conteúdo avançado

### <a name="mobile"></a>Celular

Seu aplicativo pode iniciar um estágio de um Cartão Adaptável, link compartilhado ou componentes visuais (como um gráfico).

:::image type="content" source="../../assets/images/ui-templates/mobile-stage.png" alt-text="O exemplo mostra um modelo de estágio no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de estágio na área de trabalho." border="false":::

## <a name="toolbar"></a>Barra de ferramentas

Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.

### <a name="top-use-cases"></a>Principais casos de uso

* Ações contextuais no conteúdo do aplicativo
* Filtro contextual e localização
* Navegação e trilhas

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/ui-templates/mobile-toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas na área de trabalho." border="false":::
