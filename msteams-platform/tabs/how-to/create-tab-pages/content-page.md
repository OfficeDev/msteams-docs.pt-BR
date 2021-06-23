---
title: Criar uma página de conteúdo
author: surbhigupta
description: como criar uma página de conteúdo
keywords: teams tabs group channel configurble static
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: abb073cee4a9417ee4a9f095acdbe18c5e6d7713
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068525"
---
# <a name="create-a-content-page-for-your-tab"></a>Criar uma página de conteúdo para sua guia

Uma página de conteúdo é uma página da Web renderizada no Teams cliente. Normalmente, eles fazem parte de:

* Uma guia personalizada com escopo pessoal: nesta instância, a página de conteúdo é a primeira página que o usuário encontra.
* Uma guia personalizada de canal/grupo: depois que o usuário fixar e configurar a guia no contexto apropriado, a página de conteúdo será exibida.
* Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): você pode criar uma página de conteúdo e in-locar como um webview dentro de um módulo de tarefa. A página será renderizada dentro do pop-up modal.

Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das diretrizes aqui se aplicaria independentemente de como a página de conteúdo é apresentada ao usuário final.

## <a name="tab-content-and-design-guidelines"></a>Diretrizes de design e conteúdo de tabulação

O objetivo geral da guia deve ser fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e uma finalidade evidente. Isso não significa que você deve deixar um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de tabulação limpo, intuitivo de navegação e imersivo de conteúdo.

Para obter mais informações, consulte as diretrizes de [design de tabulação](~/tabs/design/tabs.md) [e Microsoft Teams de validação do armazenamento](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

## <a name="integrate-your-code-with-teams"></a>Integrar seu código com Teams

Para que sua página seja exibida Teams, você deve incluir o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada. É assim que sua página e o Teams cliente se comunicam:

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
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

## <a name="accessing-additional-content"></a>Acessando conteúdo adicional

### <a name="using-the-sdk-to-interact-with-teams"></a>Usando o SDK para interagir com Teams

O [Teams cliente JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode encontrar úteis durante o desenvolvimento de sua página de conteúdo.

### <a name="deep-links"></a>Links profundos

Você pode criar links profundos para entidades Teams. Normalmente, eles são usados para criar links que navegam para conteúdo e informações em sua guia. Para obter mais informações, [consulte Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Módulos de Tarefa

Um módulo de tarefa é uma experiência pop-up modal que você pode disparar da guia. Normalmente, em uma página de conteúdo, você não deseja navegar pelo usuário por várias páginas. Em vez disso, você usará módulos de tarefa para apresentar formulários para coletar informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outra vez que precisar apresentar ao usuário informações adicionais. Os próprios módulos de tarefa podem ser páginas de conteúdo adicionais ou criados completamente usando Cartões Adaptáveis. Consulte [Usando módulos de tarefa em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.

### <a name="valid-domains"></a>Domínios válidos

Verifique se todos os domínios de URL usados em suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md). Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto. No entanto, não se esqueça de que a funcionalidade principal da guia existe Teams e não fora do Teams.

## <a name="reorder-static-personal-tabs"></a>Reordenar guias pessoais estáticas

A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal. Em particular, um desenvolvedor pode mover a guia de *chat* bot, que sempre é padrão para a primeira posição, em qualquer lugar no header da guia do aplicativo pessoal. Declaramos duas guias reservadas entityId palavras-chave, *conversas* e *sobre*.

Se você criar um bot com *um escopo* pessoal, ele será a primeira posição de tabulação em um aplicativo pessoal por padrão. Se quiser movê-lo para outra posição, adicione um objeto de guia estático ao manifesto com a palavra-chave reservada, *conversas*. A *guia* conversa é exibida na Web ou na área de trabalho com base em onde você adiciona a guia *de* conversa na `staticTabs` matriz. 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="show-a-native-loading-indicator"></a>Mostrar um indicador de carregamento nativo

A partir [do esquema de manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um indicador de carregamento nativo onde quer que o conteúdo da Web seja carregado Teams. [](../../../resources/schema/manifest-schema.md#showloadingindicator) Por exemplo, página [de conteúdo de tabulação,](#integrate-your-code-with-teams) [página](removal-page.md) [de configuração,](configuration-page.md)página de remoção e [módulos de tarefa nas guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> * O comportamento em clientes móveis não é configurável por meio dessa propriedade de manifesto. Os clientes móveis mostram um indicador de carregamento nativo por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe. Esse indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é descartada assim que a solicitação é concluída.
> * Se você indicar no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção de guias e todos os módulos de tarefa baseados em iframe devem seguir o protocolo obrigatório  `"showLoadingIndicator : true`  abaixo:

**Para mostrar o indicador de carregamento**

* Adicione `"showLoadingIndicator": true` ao manifesto. 
* Lembre-se de chamar `microsoftTeams.initialize();` .
* **Opcional**: se você estiver pronto para imprimir na tela e desejar carregar o restante do conteúdo do aplicativo, poderá ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();`
* **Obrigatório**: Por fim, `microsoftTeams.appInitialization.notifySuccess()` chame para notificar Teams que seu aplicativo carregou com êxito. Teams ocultará o indicador de carregamento, se aplicável. Se  `notifySuccess`  não for chamado dentro de 30 segundos, será assumido que o tempo decorria do aplicativo e uma tela de erro com uma opção de nova tentativa aparecerá.
* Se o aplicativo não for carregado, você poderá chamar para `microsoftTeams.appInitialization.notifyFailure(reason);` Teams que houve um erro. Em seguida, uma tela de erro será mostrada ao usuário:

    ```typescript
    ``
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```
    >
