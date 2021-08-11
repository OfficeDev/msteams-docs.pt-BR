---
title: Criar uma página de conteúdo
author: surbhigupta
description: como criar uma página de conteúdo
keywords: teams tabs group channel configurble static
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: f6f673420de73d786ddee95b4da7870750f3e6851a80f6ad71b1e606d650ba60
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708305"
---
# <a name="create-a-content-page-for-your-tab"></a>Criar uma página de conteúdo para sua guia

Uma página de conteúdo é uma página da Web renderizada no Teams cliente. Elas fazem parte de:

* Uma guia personalizada com escopo pessoal: nesse caso, a página de conteúdo é a primeira página que o usuário encontra.
* Uma guia personalizada de canal ou grupo: a página de conteúdo é exibida após o usuário fixar e configurar a guia no contexto apropriado.
* Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): você pode criar uma página de conteúdo e in-locar como um webview dentro de um módulo de tarefa. A página é renderizada dentro do pop-up modal.

Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das diretrizes aqui se aplica independentemente de como a página de conteúdo é apresentada ao usuário.

## <a name="tab-content-and-design-guidelines"></a>Diretrizes de design e conteúdo de tabulação

O objetivo geral da guia é fornecer acesso a conteúdo significativo e envolvente que tenha valor prático e uma finalidade evidente. Você deve se concentrar em tornar seu design de tabulação limpo, intuitivo e imersivo de conteúdo.

Para obter mais informações, consulte [diretrizes de design de guias](~/tabs/design/tabs.md) e Microsoft Teams de [validação do armazenamento.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

## <a name="integrate-your-code-with-teams"></a>Integrar seu código com Teams

Para que sua página seja exibida Teams, você deve incluir o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada. 

O código a seguir fornece um exemplo de como sua página e o Teams cliente se comunicam:

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.10.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    microsoftTeams.initialize();
    </script>
...
</body>
```

## <a name="access-additional-content"></a>Acessar conteúdo adicional

Você pode acessar conteúdo adicional usando o SDK para interagir com o Teams, criar links profundos, usar módulos de tarefa e verificar se os domínios de URL estão incluídos na `validDomains` matriz.

### <a name="use-the-sdk-to-interact-with-teams"></a>Use o SDK para interagir com Teams

O [Teams cliente JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode encontrar úteis durante o desenvolvimento de sua página de conteúdo.

### <a name="deep-links"></a>Links profundos

Você pode criar links profundos para entidades Teams. Eles são usados para criar links que navegam até conteúdo e informações em sua guia. Para obter mais informações, [consulte create deep links to content and features in Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Módulos de tarefas

Um módulo de tarefa é uma experiência pop-up modal que você pode disparar da guia. Em uma página de conteúdo, você pode usar módulos de tarefa para apresentar formulários para coletar informações adicionais, exibir os detalhes de um item em uma lista ou apresentar o usuário com informações adicionais. Os próprios módulos de tarefa podem ser páginas de conteúdo adicionais ou criados completamente usando Cartões Adaptáveis. Para obter mais informações, [consulte using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md).

### <a name="valid-domains"></a>Domínios válidos

Verifique se todos os domínios de URL usados em suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md). Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.

> [!NOTE]
> A funcionalidade principal da guia existe dentro Teams e não fora do Teams.

## <a name="show-a-native-loading-indicator"></a>Mostrar um indicador de carregamento nativo

A partir [do esquema de manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um indicador de carregamento [nativo.](../../../resources/schema/manifest-schema.md#showloadingindicator) Por exemplo, página [de conteúdo de tabulação,](#integrate-your-code-with-teams) [página](removal-page.md) [de configuração,](configuration-page.md)página de remoção e [módulos de tarefa nas guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> * O comportamento em clientes móveis não é configurável por meio da propriedade indicador de carregamento nativo. Os clientes móveis mostram esse indicador por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe. Esse indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é descartada assim que a solicitação é concluída.

Se você indicar no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção de guias e todos os módulos de tarefa baseados em iframe devem `showLoadingIndicator : true`  seguir estas etapas:

**Para mostrar o indicador de carregamento**

1. Adicione `"showLoadingIndicator": true` ao manifesto.
1. Chamar `microsoftTeams.initialize();`.
1. Como etapa **obrigatória,** chame para `microsoftTeams.appInitialization.notifySuccess()` notificar Teams que seu aplicativo carregou com êxito. Teams, em seguida, oculta o indicador de carregamento, se aplicável. Se `notifySuccess`  não for chamado dentro de 30 segundos, presume-se que o aplicativo esteja com o tempo decoro e uma tela de erro com uma opção de nova tentativa será exibida.
1. **Opcionalmente**, se você estiver pronto para imprimir na tela e desejar carregar o restante do conteúdo do aplicativo, poderá ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();` .
1. Se o aplicativo não for carregado, você poderá chamar para `microsoftTeams.appInitialization.notifyFailure(reason);` Teams que houve um erro. Uma tela de erro é mostrada ao usuário. O código a seguir fornece um exemplo de motivos de falha do aplicativo:

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)
