---
title: Criar uma página de remoção de guias
author: surbhigupta
description: Saiba como habilitar a reconfiguração da guia após a instalação. Estenda a experiência do usuário dando suporte a opções de remoção e modificação no aplicativo Microsoft Teams.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 964872d0de88d7462bec68d84f7b1e1ecf3681ec
ms.sourcegitcommit: 637b8f93b103297b1ff9f1af181680fca6f4499d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2022
ms.locfileid: "68499291"
---
# <a name="create-a-removal-page"></a>Criar uma página de remoção

Você pode estender e aprimorar a experiência do usuário dando suporte a opções de remoção e modificação em seu aplicativo. O Teams permite que os usuários renomeiem ou removam uma guia de canal ou grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, a experiência de remoção de guia fornece aos usuários opções pós-remoção para excluir ou arquivar conteúdo.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Habilitar a reconfiguração da guia após a instalação

Seu `manifest.json` define os recursos e funcionalidades da guia. A propriedade da instância `canUpdateConfiguration` de tabulação usa um valor booliano que indica se um usuário pode modificar ou reconfigurar a guia depois de criada. A tabela a seguir fornece os detalhes da propriedade:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. O padrão é `true`. |

Quando sua guia é carregada para um canal ou chat em grupo, o Teams adiciona um menu suspenso com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela configuração `canUpdateConfiguration`. A tabela a seguir fornece os detalhes da configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | description |
| ----------------------- | :----: | ----- | ----------- |
|     Configurações            |   √    |       |A `configurationUrl` página é recarregada em um iFrame, permitindo que o usuário reconfigure a guia. |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme ele aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a `removeURL` propriedade e o valor forem incluídos na página **de** configuração, a página de remoção será carregada em um iFrame e apresentada ao usuário. Se uma página de remoção não estiver incluída, o usuário receberá uma caixa de diálogo de confirmação.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de guia para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da página de remoção `setConfig()` é designada pelo método ( `setSettings()` ou anterior ao TeamsJS v.2.0.0) na página de configuração. Assim como em todas as páginas em seu aplicativo, a página de remoção deve estar em conformidade com [pré-requisitos da guia Teams](../../../tabs/how-to/tab-requirements.md).

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, na lógica da página de remoção, `registerOnRemoveHandler((RemoveEvent) => {}` você pode invocar o manipulador de eventos quando o usuário remove uma configuração de guia existente. O método usa a interface [`RemoveEvent`](/javascript/api/@microsoft/teams-js/pages.config.removeevent?view=msteams-client-js-latest&preserve-view=true) e executa o código no manipulador quando um usuário tenta remover o conteúdo. O método é usado para executar operações de limpeza, como remover o recurso subjacente que a energia do conteúdo da guia. Por vez, apenas um manipulador de remoção pode ser registrado.

A interface `RemoveEvent` descreve um objeto com dois métodos:

* A função `notifySuccess()` é necessária. Indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A função `notifyFailure(string)` é opcional. Indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, essa cadeia de caracteres será exibida para o usuário; caso contrário, um erro genérico será exibido.

#### <a name="use-the-getconfig-function"></a>Use a função `getConfig()`.

Você pode usar `getConfig()` (anteriormente `getSettings()`) para atribuir o conteúdo da guia a ser removido. A `getConfig()` função retorna uma promessa que é resolvida com o objeto Config e fornece os valores de propriedade de configurações válidos que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Use a função `getContext()`.

Você pode usar `getContext()` para obter o contexto atual no qual o quadro está sendo executado. A `getContext()` função retorna uma promessa que será resolvida com o objeto Context. O objeto Context fornece valores de `Context` propriedade válidos que você pode usar em sua lógica de página de remoção para determinar o conteúdo a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

A autenticação é necessária antes de permitir que um usuário exclua o conteúdo da guia. Informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Consulte[Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Verifique se todos os domínios usados em suas páginas de guia estão listados na matriz `validDomains` do manifesto do aplicativo.

A seguir está um bloco de código de remoção de guia de exemplo:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script type="module">
        import {app, pages} from 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js';
    await app.initialize();
    pages.config.registerOnRemoveHandler((removeEvent) => {
      // Here you can designate the tab content to be removed and/or archived.
        const configPromise = pages.getConfig();
        configPromise.
            then((configuration) => {
                configuration.contentUrl = "...";
                removeEvent.notifySuccess()}).
            catch((error) => {removeEvent.notifyFailure("failure message")});
    });

    const onClick() => {
        pages.config.setValidityState(true);
    }
  </script>
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script>
    microsoftTeams.initialize();
    microsoftTeams.settings.registerOnRemoveHandler((removeEvent) => {
      // Here you can designate the tab content to be removed and/or archived.
        microsoftTeams.settings.getSettings((settings) => {
        settings.contentUrl = "..."
        });
        removeEvent.notifySuccess();
    });

    const onClick() => {
        microsoftTeams.settings.setValidityState(true);
    }
  </script>
</body>
```

***

Quando um usuário seleciona **Remover** no menu suspenso da guia, o Teams `removeUrl` carrega a página opcional atribuída na página de configuração **em um** iFrame. O usuário é mostrado um botão carregado `onClick()` `pages.config.setValidityState(true)` com a função que chama e habilita o  botão Remover mostrado na parte inferior da página de remoção iFrame.

Depois que o manipulador de remoção é executado, `removeEvent.notifySuccess()` ou `removeEvent.notifyFailure()` notifica o Teams sobre o resultado da remoção de conteúdo.

>[!NOTE]
>
> * Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, o Teams remove a guia em casos de êxito e falha.
> * Depois de invocar o manipulador de eventos `registerOnRemoveHandler`, você terá 15 segundos para responder ao método. Por padrão, o Teams habilita o botão **Remover** depois de cinco segundos, mesmo que você não chame `setValidityState(true)`.
> * Quando o usuário seleciona **Remover**, o Teams remove a guia após 30 segundos, independentemente de as ações serem concluídas ou não.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)
