---
title: Criar uma página de conteúdo
author: laujan
description: como criar uma página de conteúdo
keywords: equipes guias canal de grupo estática configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 136160cb9154d62be40d8e29075ac1fc86135a6b
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566674"
---
# <a name="create-a-content-page-for-your-tab"></a>Crie uma página de conteúdo para sua guia

Uma página de conteúdo é uma página da Web que é renderizada dentro do Teams cliente. Normalmente, estes fazem parte de:

* Uma guia personalizada com escopo pessoal: Neste caso, a página de conteúdo é a primeira página que o usuário encontra.
* Uma guia personalizada de canal/grupo: Depois que o usuário fixa e configura a guia no contexto apropriado, a página de conteúdo é exibida.
* Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): Você pode criar uma página de conteúdo e incorporá-la como uma webview dentro de um módulo de tarefa. A página será renderizada dentro do popup modal.

Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das orientações aqui se aplicaria independentemente de como a página de conteúdo é apresentada ao usuário final.

## <a name="tab-content-and-design-guidelines"></a>Guiar o conteúdo e as diretrizes de design

O objetivo geral da sua guia deve ser fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e um propósito evidente. Isso não significa que você deve renunciar a um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de guia limpo, intuitivo de navegação e conteúdo imersivo.

Para obter mais informações, consulte as [diretrizes de design](~/tabs/design/tabs.md) de guias e [as diretrizes de validação da loja Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

## <a name="integrate-your-code-with-teams"></a>Integre seu código com Teams

Para que sua página seja exibida em Teams, você deve incluir o [Microsoft Teams Cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e incluir uma chamada para `microsoftTeams.initialize()` depois que sua página for carregada. É assim que sua página e o Teams cliente se comunicam:

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

O [Teams cliente JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode achar úteis ao desenvolver sua página de conteúdo.

### <a name="deep-links"></a>Links profundos

Você pode criar links profundos para entidades em Teams. Normalmente, estes são usados para criar links que navegam para conteúdo e informações dentro de sua guia. Para obter mais informações, consulte [Criar links profundos para conteúdo e recursos em Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Módulos de tarefas

Um módulo de tarefa é uma experiência modal semelhante ao pop-up que você pode acionar a partir de sua guia. Normalmente em uma página de conteúdo você não quer navegar pelo usuário através de várias páginas. Em vez disso, você usará módulos de tarefa para apresentar formulários para coletar informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outra hora que você precisar apresentar ao usuário informações adicionais. Os módulos de tarefa em si podem ser páginas de conteúdo adicionais ou criadas completamente usando cartões adaptativos. Consulte [Usando módulos de tarefas em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.

### <a name="valid-domains"></a>Domínios válidos

Certifique-se de que todos os domínios de URL usados em suas guias estejam incluídos no `validDomains` array em seu [manifesto](~/concepts/build-and-test/apps-package.md). Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência manifesto esquema. No entanto, esteja ciente de que a funcionalidade central da sua guia existe dentro de Teams e não fora de Teams.

## <a name="reorder-static-personal-tabs"></a>Reordenar guias pessoais estáticas

Começando com a versão manifesto 1.7, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal. Em particular, um desenvolvedor pode mover a guia *de bate-papo do bot,* que sempre é padrão para a primeira posição, em qualquer lugar no cabeçalho da guia do aplicativo pessoal. Declaramos duas palavras-chave reservadas da tab EntityId, *conversas* e *sobre*.

Se você criar um bot com um escopo *pessoal,* ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão. Se você deseja movê-lo para outra posição, você deve adicionar um objeto de guia estática ao seu manifesto com a palavra-chave reservada, *conversas*. A guia *de conversação* é exibida na Web ou na área de trabalho com base em onde você adiciona a guia *de conversação* no `staticTabs` array. 

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

## <a name="show-a-native-loading-indicator"></a>Mostre um indicador de carregamento nativo

Começando com [o esquema manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um [indicador de carregamento nativo](../../../resources/schema/manifest-schema.md#showloadingindicator) onde quer que seu conteúdo da Web esteja carregado em Teams. Por exemplo, [página de conteúdo de guia,](#integrate-your-code-with-teams)página de [configuração,](configuration-page.md) [página de remoção](removal-page.md)e [módulos de tarefa em guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> * O comportamento dos clientes móveis não é configurável através desta propriedade manifesto. Os clientes móveis mostram um indicador de carregamento nativo por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe. Este indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é rejeitada assim que a solicitação é concluída.
> * Se você indicar  `"showLoadingIndicator : true`  no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção da guia e todos os módulos de tarefa baseados em iframe devem seguir o protocolo obrigatório, abaixo:

**Para mostrar o indicador de carregamento**

* Adicione `"showLoadingIndicator": true` ao seu manifesto. 
* Lembre-se de `microsoftTeams.initialize();` ligar.
* **Opcional**: Se você estiver pronto para imprimir na tela e desejar carregar o resto do conteúdo do aplicativo, você pode ocultar manualmente o indicador de carregamento ligando para `microsoftTeams.appInitialization.notifyAppLoaded();`
* **Obrigatório**: Por fim, ligue `microsoftTeams.appInitialization.notifySuccess()` para notificar Teams que seu aplicativo carregou com sucesso. Teams, em seguida, ocultará o indicador de carregamento, se aplicável. Se  `notifySuccess`  não for chamado dentro de 30 segundos, presume-se que seu aplicativo foi cronometrado e uma tela de erro com uma opção de repetição será exibida.
* Se o aplicativo não for carregado, você pode ligar `microsoftTeams.appInitialization.notifyFailure(reason);` para avisar Teams que houve um erro. Em seguida, uma tela de erro será mostrada ao usuário:

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
