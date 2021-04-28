---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 0afcce50a4779421016c23c4ec4e3d25cc3401d1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058611"
---
# <a name="add-a-default-install-scope-and-group-capability"></a>Adicionar um escopo de instalação padrão e funcionalidade de grupo

É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente. Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**

![Adicionar um aplicativo](../../assets/images/compose-extensions/addanapp.png)

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
> [Escolha como distribuir o aplicativo](overview.md)
