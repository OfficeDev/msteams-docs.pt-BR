---
title: Criar uma página de remoção de guias
author: surbhigupta
description: Saiba como habilitar sua guia a ser reconfigurada após a instalação. Estenda a experiência do usuário dando suporte a opções de remoção e modificação no aplicativo Microsoft Teams.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 423cc386ca416fe116eb0bcb62c1238cae5547ff
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819937"
---
# <a name="create-a-removal-page"></a>Criar uma página de remoção

Você pode estender e aprimorar a experiência do usuário dando suporte a opções de remoção e modificação em seu aplicativo. O Teams permite que os usuários renomeiem ou removam uma guia de canal ou grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, a experiência de remoção de guia fornece aos usuários opções pós-remoção para excluir ou arquivar conteúdo.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Habilitar a reconfiguração da guia após a instalação

Seu `manifest.json` define os recursos e funcionalidades da guia. A propriedade da instância `canUpdateConfiguration` da guia usa um valor booliano que indica se um usuário pode modificar ou reconfigurar a guia após a criação. A tabela a seguir fornece os detalhes da propriedade:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. O padrão é `true`. |

Quando sua guia é carregada para um canal ou chat em grupo, o Teams adiciona um menu suspenso com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela configuração `canUpdateConfiguration`. A tabela a seguir fornece os detalhes da configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | description |
| ----------------------- | :----: | ----- | ----------- |
|     Configurações            |   √    |       |A `configurationUrl` página é recarregada em um iFrame permitindo que o usuário reconfigure a guia. |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme ele aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a propriedade e o  `removeURL` valor forem incluídos na **página de configuração**, a **página de remoção** será carregada em um iFrame e apresentada ao usuário. Se uma página de remoção não estiver incluída, o usuário será apresentado com uma caixa de diálogo confirmar.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de guia para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da `setConfig()` página de remoção é designada pelo método (ou `setSettings()` anterior ao TeamsJS v.2.0.0) em sua página de configuração. Assim como em todas as páginas em seu aplicativo, a página de remoção deve estar em conformidade com [pré-requisitos da guia Teams](../../../tabs/how-to/tab-requirements.md).

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, dentro da lógica da página de remoção, você pode invocar o `registerOnRemoveHandler((RemoveEvent) => {}` manipulador de eventos quando o usuário remover uma configuração de guia existente. O método usa a interface [`RemoveEvent`](/javascript/api/@microsoft/teams-js/pages.config.removeevent?view=msteams-client-js-latest&preserve-view=true) e executa o código no manipulador quando um usuário tenta remover o conteúdo. O método é usado para executar operações de limpeza, como remover o recurso subjacente que alimenta o conteúdo da guia. Por vez, somente um, o manipulador de remoção pode ser registrado.

A interface `RemoveEvent` descreve um objeto com dois métodos:

* A função `notifySuccess()` é necessária. Indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A função `notifyFailure(string)` é opcional. Ele indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, essa cadeia de caracteres será exibida para o usuário; caso contrário, um erro genérico será exibido.

#### <a name="use-the-getconfig-function"></a>Use a função `getConfig()`.

Você pode usar `getConfig()` (anteriormente `getSettings()`) para atribuir o conteúdo da guia a ser removido. A `getConfig()` função retorna uma promessa que é resolvida com o objeto Config e fornece os valores de propriedade de configurações válidas que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Use a função `getContext()`.

Você pode usar `getContext()` para obter o contexto atual no qual o quadro está sendo executado. A `getContext()` função retorna uma promessa que será resolvida com o objeto Context. O objeto Context fornece valores de propriedade válidos `Context` que você pode usar na lógica da página de remoção para determinar o conteúdo a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

A autenticação é necessária antes de permitir que um usuário exclua o conteúdo da guia. Informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Consulte[Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Verifique se todos os domínios usados em suas páginas de guia estão listados na matriz do `validDomains` manifesto do aplicativo.

A seguir está um bloco de código de remoção de guia de exemplo:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<body>
  <button onclick="onClick()">Delete this tab and all underlying data?</button>
  <script>
    await microsoftTeams.app.initialize();
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

Quando um usuário seleciona **Remover** do menu suspenso da guia, o Teams carrega a página opcional `removeUrl` atribuída em sua **página de configuração** em um iFrame. O usuário é mostrado um botão carregado com a `onClick()` função que chama `pages.config.setValidityState(true)` e habilita o botão **Remover** mostrado na parte inferior da página de remoção iFrame.

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

* [Compilar guias para o Teams](../../what-are-tabs.md)
* [Esquema de manifesto do aplicativo para o Teams](../../../resources/schema/manifest-schema.md)
* [Interface RemoveEvent](/javascript/api/@microsoft/teams-js/pages.config.removeevent)
* [Obtenha contexto para sua guia](../access-teams-context.md)
* [Criar uma guia pessoal](../create-personal-tab.md)
* [Criar uma guia de canal ou guia de grupo](../create-channel-group-tab.md)
