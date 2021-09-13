---
title: Criar uma página de remoção de guias
author: surbhigupta
description: Como criar uma página de remoção de tabulação
keywords: teams tabs group channel configurble remove delete
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b519b4ff7251979f97affb0c567f0e9813142b6e
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155093"
---
# <a name="create-a-removal-page"></a>Criar uma página de remoção

Você pode estender e aprimorar a experiência do usuário suportando opções de remoção e modificação em seu aplicativo. Teams permite que os usuários renomeiem ou removam uma guia de canal ou grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, a experiência de remoção de tabulação fornece aos usuários opções pós-remoção para excluir ou arquivar conteúdo.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Permitir que sua guia seja reconfigurada após a instalação

Seu **manifest.json** define os recursos e recursos da guia. A propriedade da instância de tabulação tem um valor Boolean que indica se um usuário pode modificar ou `canUpdateConfiguration` reconfigurar a guia depois que ela for criada. A tabela a seguir fornece os detalhes da propriedade:

|Name| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. O padrão é `true`. |

Quando sua guia é carregada em um chat de canal ou grupo, Teams adiciona um menu suspenso com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela `canUpdateConfiguration` configuração. A tabela a seguir fornece os detalhes da configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | description |
| ----------------------- | :----: | ----- | ----------- |
|     Configurações            |   √    |       |A `configurationUrl` página é recarregada em um IFrame permitindo que o usuário reconfigure a guia. |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a propriedade e o valor são incluídos na página de configuração , a página de remoção é carregada em `removeURL` um IFrame e apresentada ao usuário.   Se uma página de remoção não estiver incluída, o usuário será apresentado com uma caixa de diálogo confirmar.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de tabulação para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da página de remoção é designada pelo `setSettings()` método em sua página de configuração. Assim como todas as páginas em seu aplicativo, a página de remoção deve estar em conformidade [com Teams pré-requisitos da guia](../../../tabs/how-to/tab-requirements.md).

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, na lógica da página de remoção, você pode invocar o manipulador de eventos quando o usuário `registerOnRemoveHandler((RemoveEvent) => {}` remover uma configuração de guia existente. O método entra na interface e executa o código no [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) manipulador quando um usuário tenta remover o conteúdo. O método é usado para executar operações de limpeza, como a remoção do recurso subjacente que está no conteúdo da guia. Por vez, apenas um manipulador de remoção pode ser registrado.

A `RemoveEvent` interface descreve um objeto com dois métodos:

* A `notifySuccess()` função é necessária. Indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A `notifyFailure(string)` função é opcional. Indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, essa cadeia de caracteres será exibida para o usuário; senão um erro genérico é exibido.

#### <a name="use-the-getsettings-function"></a>Usar a `getSettings()` função

Você pode usar `getSettings()` para atribuir o conteúdo da guia a ser removido. A função assume e fornece os valores de propriedade `getSettings((Settings) =>{})` [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) de configurações válidos que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Usar a `getContext()` função

Você pode usar `getContext()` para obter o contexto atual no qual o quadro está sendo executado. A `getContext((Context) =>{})` função assume o [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) . A função fornece valores de propriedade válidos que você pode usar na lógica da página de remoção para determinar o conteúdo `Context` a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

A autenticação é necessária antes de permitir que um usuário exclua o conteúdo da guia. As informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Consulte [Microsoft Teams fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Certifique-se de que todos os domínios usados em suas páginas de tabulação estão listados na `manifest.json` `validDomains` matriz.

Veja a seguir um bloco de código de remoção de tabulação de exemplo:

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

Quando um usuário seleciona **Remover** do menu suspenso da guia, Teams carrega a página opcional atribuída na página de configuração , em `removeUrl` um IFrame. O usuário é mostrado um botão carregado com a função que chama e habilita o botão Remover mostrado na parte inferior da página de remoção `onClick()` `microsoftTeams.settings.setValidityState(true)` IFrame. 

Depois que o manipulador de remoção for executado, `removeEvent.notifySuccess()` ou `removeEvent.notifyFailure()` notifica Teams do resultado de remoção de conteúdo.

>[!NOTE]
> * Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, Teams remove a guia em casos de sucesso e falha.
> * Teams habilita o **botão Remover** após cinco segundos, mesmo que sua guia não tenha chamado `setValidityState()` .
> * Quando o usuário seleciona **Remover**, Teams remove a guia após 30 segundos, independentemente de as ações ter sido concluídas ou não.

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)