---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a4b70df70c7b9442e29953dae8a8c4e892cb72c1
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946484"
---
# <a name="add-a-default-install-scope-and-group-capability"></a>Adicionar um escopo de instalação padrão e funcionalidade de grupo

É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente. Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**

![Adicionar um aplicativo](../../assets/images/compose-extensions/addanapp.png)

Se o recurso principal do aplicativo for um bot, você também poderá tornar o bot o recurso padrão quando um usuário instala seu aplicativo em uma equipe. 

## <a name="configure-your-apps-default-install-scope"></a>Configurar o escopo de instalação padrão do aplicativo

Configure o escopo de instalação padrão para seu aplicativo. Você pode definir apenas um escopo por vez.

**Para configurar o escopo de instalação padrão no manifesto do aplicativo**

1. Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.
2. De definir um valor `personal` de , , ou `team` `groupchat` `meetings` (consulte um exemplo abaixo).

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Configurar o recurso padrão para escopos compartilhados

Configure o recurso padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou chat.

**Para configurar detalhes no manifesto do aplicativo**

1. Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.
2. Salve as atualizações.

    A seguir está um exemplo JSON:

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```
> [!NOTE]
> Para obter informações sobre o esquema completo, consulte [esquema de manifesto](~/resources/schema/manifest-schema.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Escolha como distribuir o aplicativo](overview.md)
