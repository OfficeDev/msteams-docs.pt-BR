---
title: Configurar opções de instalação padrão para seu aplicativo
description: Saiba como especificar as opções de instalação padrão Teams seu aplicativo e a funcionalidade padrão para escopos compartilhados.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: 9055b765c30f83c4031ad0e2ba5f18f4e747ac3f
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66122898"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a>Configurar opções de instalação padrão para seu Microsoft Teams aplicativo

É comum um aplicativo dar suporte a vários cenários no Teams, mas talvez você o tenha projetado com um escopo e funcionalidade específicos em mente. Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você poderá garantir que a primeira opção de instalação que os usuários veem na loja seja Adicionar **a uma equipe**.

:::row:::
   :::column span="2":::

![Adicionar um exemplo de lista suspensa de aplicativos](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

Se o principal recurso do aplicativo for um bot, você também poderá tornar o bot a funcionalidade padrão quando um usuário instalar seu aplicativo em uma equipe.

## <a name="configure-your-apps-default-install-scope"></a>Configurar o escopo de instalação padrão do aplicativo

Configure o escopo de instalação padrão para seu aplicativo. Você pode definir apenas um escopo por vez.

Para configurar o escopo de instalação padrão no manifesto do aplicativo:

1. Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.
2. Defina o valor de escopo de instalação padrão como `personal`, seja, `team`, `groupchat`ou `meetings`.

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Para obter mais informações, consulte o [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Configurar a funcionalidade padrão para escopos compartilhados

Configure a funcionalidade padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou chat de grupo.

> [!NOTE]
> `defaultGroupCapability` fornece a funcionalidade padrão que será adicionada à equipe, ao groupchat ou à reunião. Selecione uma guia, um bot ou um conector como a funcionalidade padrão para seu aplicativo, mas você deve garantir que forneceu a funcionalidade selecionada na definição do aplicativo.

Para configurar detalhes no manifesto do aplicativo:

1. Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.
2. Defina um valor de `team`, `groupchat`ou `meetings`.
3. Para a funcionalidade de grupo selecionada, as funcionalidades de grupo disponíveis são, `bot`ou `tab``connector`.

    > [!NOTE]
    > Você pode selecionar apenas uma funcionalidade padrão, `bot`ou `tab`para a `connector` funcionalidade de grupo selecionada.

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> Para obter mais informações, consulte o [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um pacote do aplicativo](~/concepts/build-and-test/apps-package.md)
