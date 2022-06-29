---
title: Projetar seu aplicativo com componentes avançados da interface do usuário
author: heath-hamilton
description: Saiba mais sobre os componentes da interface do usuário do Teams, como trilhas, barra de notificação, exibição de estágio junto com casos de uso relevantes.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: reference
ms.openlocfilehash: 30d429bf927b3cb9422fc4f3ea238ce9eceae49e
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485717"
---
# <a name="designing-your-microsoft-teams-app-with-advanced-ui-components"></a>Projetando seu aplicativo Microsoft Teams com componentes avançados da interface do usuário

Os componentes a seguir são uma combinação de [componentes básicos da interface](~/concepts/design/design-teams-app-basic-ui-components.md) do usuário que você pode usar para situações comuns de design do Teams, como navegação.

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Com base <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">na interface do usuário fluente</a>, o Kit de Interface do Usuário do Microsoft Teams inclui componentes e padrões projetados especificamente para a criação de aplicativos do Teams. No kit de interface do usuário, você pode pegar e inserir os componentes listados aqui diretamente em seu design e ver mais exemplos de como usar cada componente.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="breadcrumb"></a>Trilha

Trilhas são um auxílio de navegação que transmite a hierarquia do aplicativo. Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e permitem acesso com um clique a níveis mais altos nessa hierarquia.

### <a name="top-use-cases"></a>Principais casos de uso

* Hierarquia de comunicação
* Navegação

### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/ui-templates/mobile-breadcrumb.png" alt-text="O exemplo mostra um modelo de trilha no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de trilha na área de trabalho." border="false":::

## <a name="left-nav"></a>Navegação à esquerda

Use a navegação à esquerda para procurar várias páginas em sua guia Do Teams. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.

### <a name="top-use-cases"></a>Principais casos de uso

* Navegue por várias páginas em uma guia do Teams.
* Dividir aplicativos complexos em várias páginas.

### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/ui-templates/mobile-left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda na área de trabalho." border="false":::

## <a name="notification-bar"></a>Notification bar

Uma barra de notificação é uma área dedicada para exibir mensagens breves e importantes que não exigem que o usuário tome medidas imediatas. Cores e ícones específicos da tela de fundo são associados a tipos específicos de mensagens (veja abaixo).

Você pode implementar uma barra de notificação usando o componente de alerta do [Fluent UI.](https://fluentsite.z22.web.core.windows.net/0.59.0/components/alert/definition)

### <a name="top-use-cases"></a>Principais casos de uso

* Mensagens críticas, erros e avisos.
* Mensagens de êxito
* Mensagens informativas ou promocionais

### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/ui-templates/mobile-notification-bar.png" alt-text="O exemplo mostra o modelo de interface do usuário da barra de notificação no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="O exemplo mostra modelos de interface do usuário da barra de notificação na área de trabalho." border="false":::

## <a name="stage-view"></a>Modo de exibição de estágio

O modo de exibição de estágio permite que os usuários vejam conteúdo, como uma imagem, arquivo ou site, em uma superfície grande no Teams sem alternar o contexto. Esse componente destina-se principalmente à exibição de conteúdo. Não o use para interações complexas.

Veja como implementar o modo [de exibição de estágio](~/tabs/tabs-link-unfurling.md).

### <a name="top-use-cases"></a>Principais casos de uso

* Exiba conteúdo em uma superfície grande no Teams em vez de outro aplicativo ou navegador.
* Mídia em destaque ou outro conteúdo avançado

### <a name="mobile"></a>Dispositivo móvel

Seu aplicativo pode iniciar um estágio de um Cartão Adaptável, link compartilhado ou componentes visuais (como um gráfico).

:::image type="content" source="../../assets/images/ui-templates/mobile-stage.png" alt-text="O exemplo mostra um modelo de estágio no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de estágio na área de trabalho." border="false":::

## <a name="toolbar"></a>Barra de ferramentas

Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.

### <a name="top-use-cases"></a>Principais casos de uso

* Ações contextuais no conteúdo do aplicativo.
* Filtro contextual e localização.
* Navegação e trilhas.

### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/ui-templates/mobile-toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas no celular." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas na área de trabalho." border="false":::
