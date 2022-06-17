---
title: Criar uma página de conteúdo
author: surbhigupta
description: Neste módulo, saiba como criar uma página de conteúdo para suas diretrizes de design e conteúdo de guia e guia
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 646e7f1a1177330fdb4db64b7e6cd1bde0df5db5
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142203"
---
# <a name="create-a-content-page-for-your-tab"></a>Criar uma página de conteúdo para sua guia

Uma página de conteúdo é uma página da Web renderizada no Teams cliente, que faz parte de:

* Uma guia personalizada com escopo pessoal: nesse caso, a página de conteúdo é a primeira página que o usuário encontra.
* Uma guia personalizada de canal ou grupo: a página de conteúdo é exibida depois que o usuário fixa e configura a guia no contexto apropriado.
* Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): você pode criar uma página de conteúdo e inseri-la como um modo de exibição da Web dentro de um módulo de tarefa. A página é renderizada dentro do pop-up modal.

Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das diretrizes aqui se aplica independentemente de como a página de conteúdo é apresentada ao usuário.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="tab-content-and-design-guidelines"></a>Diretrizes de design e conteúdo da guia

O objetivo geral da guia é fornecer acesso ao conteúdo significativo e envolvente que tem um valor prático e uma finalidade evidente. 

Você precisa se concentrar em tornar seu design de guia limpo, intuitivo de navegação e imersivo de conteúdo. Para obter mais informações, consulte [diretrizes de design de guia](~/tabs/design/tabs.md) [e Microsoft Teams de validação do repositório](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

## <a name="integrate-your-code-with-teams"></a>Integrar seu código com o Teams

Para que sua página seja exibida no Teams, você deve incluir o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e incluir uma chamada para `app.initialize()` após o carregamento da página.

O código a seguir fornece um exemplo de como sua página e o cliente do Teams se comunicam:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v2.0.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    app.initialize();
    </script>
...
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

## <a name="access-additional-content"></a>Acessar conteúdo adicional

Você pode acessar conteúdo adicional usando o SDK para interagir com o Teams, criar links profundos, usar módulos de tarefa e verificar se os domínios de URL estão incluídos na matriz `validDomains`.

### <a name="use-the-sdk-to-interact-with-teams"></a>Usar o SDK para interagir com o Teams

A [SDK JavaScript do cliente do Teams](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode achar úteis ao desenvolver sua página de conteúdo.

### <a name="deep-links"></a>Links profundos

Você pode criar links profundos para entidades no Teams. Eles são usados para criar links que navegam para conteúdo e informações em sua guia. Para obter mais informações, [consulte criar links profundos para conteúdo e recursos no Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Módulos de tarefas

Um módulo de tarefa é uma experiência pop-up modal que você pode disparar na guia. Em uma página de conteúdo, use módulos de tarefa para apresentar formulários para coletar informações adicionais, exibir os detalhes de um item em uma lista ou apresentar ao usuário informações adicionais. Os próprios módulos de tarefa podem ser páginas de conteúdo adicionais ou criados completamente usando Cartões adaptáveis. Para obter mais informações, consulte [usando módulos de tarefas em bots do Microsoft Teams](~/task-modules-and-cards/task-modules/task-modules-tabs.md).

### <a name="valid-domains"></a>Domínios válidos

Verifique se todos os domínios de URL usados em suas guias estão incluídos na matriz `validDomains` em seu [manifesto](~/concepts/build-and-test/apps-package.md). Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.

> [!NOTE]
> A funcionalidade principal da guia existe no Teams e não fora do Teams.

## <a name="show-a-native-loading-indicator"></a>Mostrar um indicador de carregamento nativo

A partir do [esquema de manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um [indicador de carregamento nativo](../../../resources/schema/manifest-schema.md#showloadingindicator). Por exemplo, [página de conteúdo da guia](#integrate-your-code-with-teams), [página de configuração](configuration-page.md), [página de remoção](removal-page.md) e [módulos de tarefa em guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
>
> * O comportamento em clientes móveis não é configurável por meio da propriedade do indicador de carregamento nativo. Os clientes móveis mostram esse indicador por padrão em páginas de conteúdo e módulos de tarefas baseados em iframe. Esse indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é ignorada assim que a solicitação é concluída.

Se você indicar `showLoadingIndicator : true` no manifesto do aplicativo, todas as configurações de guia, conteúdo, páginas de remoção e todos os módulos de tarefa baseados em iframe deverão seguir estas etapas:

Para mostrar o indicador de carregamento:

1. Adicione `"showLoadingIndicator": true` ao manifesto.
1. Chamar `app.initialize();`.
1. Como etapa **obrigatória**, chame `app.notifySuccess()` para notificar o Teams de que seu aplicativo foi carregado com êxito. Em seguida, Teams oculta o indicador de carregamento, se aplicável. Se `notifySuccess` não for chamado dentro de 30 segundos, Teams o aplicativo tiver tempo limite e exibirá uma tela de erro com uma opção de repetição.
1. **Opcionalmente**, se você estiver pronto para imprimir na tela e desejar carregar lentamente o restante do conteúdo do aplicativo, poderá ocultar o indicador de carregamento manualmente `app.notifyAppLoaded();`chamando.
1. Se o aplicativo não for carregado, `app.notifyFailure({reason: app.FailedReason.Timeout, message: "failure message"});` você poderá ligar para Teams sobre a falha e, opcionalmente, fornecer uma mensagem de falha. Uma tela de erro é mostrada para o usuário. O código a seguir mostra a enumeração que define os possíveis motivos pelos quais você pode indicar a falha de carregamento do aplicativo:

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Link de guias desdobradas e Exibição de Estágio](~/tabs/tabs-link-unfurling.md)
* [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Guias do DevTools para o Microsoft Teams](~/tabs/how-to/developer-tools.md)
