---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: e4568b0d562226dec955b3a0d843d1358132bd8bc270ae004a35218e26c35ef6
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708067"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a>Configurar opções de instalação padrão para seu Microsoft Teams app

É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente. Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**

:::row:::
   :::column span="2":::

![Adicionar um exemplo suspenso de aplicativo](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

Se o recurso principal do aplicativo for um bot, você também poderá tornar o bot o recurso padrão quando um usuário instala seu aplicativo em uma equipe.

## <a name="configure-your-apps-default-install-scope"></a>Configurar o escopo de instalação padrão do aplicativo

Configure o escopo de instalação padrão para seu aplicativo. Você pode definir apenas um escopo por vez.

**Para configurar o escopo de instalação padrão no manifesto do aplicativo**

1. Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.
2. Definir o valor de escopo de instalação padrão como `personal` , `team` , ou `groupchat` `meetings` .

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Configurar o recurso padrão para escopos compartilhados

Configure o recurso padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou groupchat.

> [!NOTE]
> `defaultGroupCapability` fornece o recurso padrão que será adicionado à equipe, groupchat ou reunião. Selecione uma guia, bot ou conector como o recurso padrão para seu aplicativo, mas você deve garantir que tenha fornecido o recurso selecionado na definição do aplicativo.

**Para configurar detalhes no manifesto do aplicativo**

1. Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.
2. Definir um valor `team` de `groupchat` , ou `meetings` .
3. Para a funcionalidade de grupo selecionada, os recursos de grupo disponíveis `bot` são, `tab` , ou `connector` . 

    > [!NOTE]
    > Você pode selecionar apenas um recurso `bot` padrão, , `tab` ou para o recurso de grupo `connector` selecionado.

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um pacote do aplicativo](~/concepts/build-and-test/apps-package.md)
