---
title: Criar uma página de conteúdo
author: laujan
description: como criar uma página de conteúdo
keywords: guias do teams com o canal de grupo configurado como estático
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: ad1e1a015526fd723670ea7eda735ebf88f85bf8
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552532"
---
# <a name="create-a-content-page-for-your-tab"></a>Criar uma página de conteúdo para sua guia

Uma página de conteúdo é uma página da Web que é renderizada no cliente Teams. Normalmente, são parte de:

* Uma guia personalizada de escopo pessoal-nesta instância, a página de conteúdo é a primeira página que o usuário encontra.
* Uma guia personalizada de canal/grupo, depois que o usuário fixa e configura a guia no contexto apropriado, a página de conteúdo é exibida.
* Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md) -você pode criar uma página de conteúdo e incorporá-la como uma WebView dentro de um módulo de tarefa. A página será renderizada dentro do popup modal.

Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das orientações aqui aplica-se independentemente de como a página de conteúdo é apresentada ao usuário final.

## <a name="tab-content-and-style-guidelines"></a>Diretrizes de conteúdo e estilo da guia

O objetivo geral da guia é fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e uma finalidade evidente. Isso não significa que você tenha um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de guia limpo, intuitivo e de aparência de conteúdo. Veja [conteúdo e conversas, tudo de uma vez usando guias](~/tabs/design/tabs.md) e a [orientação do processo de aprovação do Microsoft Teams app](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)

## <a name="integrate-your-code-with-teams"></a>Integrar seu código com o Microsoft Teams

Para que sua página seja exibida no Teams, você deve incluir o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latestadd &preserve-view=true) e incluir uma chamada para `microsoftTeams.initialize()` depois que a página for carregada. É assim que sua página e o cliente Teams se comunicam:

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

## <a name="accessing-additional-content"></a>Acessar conteúdo adicional

### <a name="using-the-sdk-to-interact-with-teams"></a>Usando o SDK para interagir com o Microsoft Teams

O [SDK JavaScript do teams Client](~/tabs/how-to/using-teams-client-sdk.md) fornece várias funções adicionais que podem ser úteis ao desenvolver sua página de conteúdo.

### <a name="deep-links"></a>Deep links

Você pode criar links de profunda para entidades no Microsoft Teams. Normalmente, são usados para criar links que navegam para conteúdo e informações dentro de sua guia. Consulte [criar links de profundas para conteúdo e recursos no Microsoft Teams](~/concepts/build-and-test/deep-links.md).

### <a name="task-modules"></a>Módulos de tarefa

Um módulo de tarefa é uma experiência do tipo pop-up modal que você pode disparar na sua guia. Normalmente, em uma página de conteúdo, você não deseja navegar pelo usuário por várias páginas. Em vez disso, você usará os módulos de tarefas para apresentar formulários de coleta de informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outro momento necessário para apresentar informações adicionais ao usuário. Os próprios módulos de tarefas podem ser páginas de conteúdo adicionais ou criados completamente usando cartões adaptáveis. Consulte [usando módulos de tarefas em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.

### <a name="valid-domains"></a>Domínios válidos

Certifique-se de que todos os domínios de URL usados nas suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md). Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto. No entanto, lembre-se de que a funcionalidade principal da sua guia existe no Microsoft Teams e não fora do teams.

## <a name="show-a-native-loading-indicator"></a>Mostrar um indicador de carregamento nativo

A partir [do esquema de manifesto v 1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um [indicador de carregamento nativo](../../../resources/schema/manifest-schema.md#showloadingindicator) sempre que o conteúdo da Web é carregado no Teams, por exemplo, [página de conteúdo da guia](#integrate-your-code-with-teams), página de [configuração](configuration-page.md), [página de remoção](removal-page.md) e [módulos de tarefa em guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).

> [!NOTE]
> 1. O indicador de carregamento nativo ainda não é suportado em dispositivos móveis.
> 2. Se você indicar  `"showLoadingIndicator : true`  no manifesto do aplicativo, todas as páginas configuração de guia, conteúdo e remoção e todos os módulos de tarefa com base em iframe devem seguir o protocolo obrigatório, abaixo:


1. Para mostrar o indicador de carregamento, adicione-o `"showLoadingIndicator": true` ao seu manifesto. 
2. Lembre-se de chamar `microsoftTeams.initialize();` .
3. **Opcional**. Se você estiver pronto para imprimir na tela e quiser carregar o restante do conteúdo do aplicativo, você pode ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();`
4. **Obrigatório**. Por fim, chame `microsoftTeams.appInitialization.notifySuccess()` para notificar as equipes de que seu aplicativo carregou com êxito. O Microsoft Teams ocultará o indicador de carregamento, se aplicável. Se  `notifySuccess`  não for chamado dentro de 30 segundos, será considerado que seu aplicativo esgotou o tempo limite e uma tela de erro com uma opção de repetição será exibida.
5. Se o aplicativo não puder ser carregado, você poderá chamá-lo `microsoftTeams.appInitialization.notifyFailure(reason);` para permitir que as equipes saibam que houve um erro. Uma tela de erro será exibida para o usuário:

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
