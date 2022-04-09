---
title: Criar uma página de remoção de guias
author: surbhigupta
description: Como criar uma página de remoção de guia
keywords: teams tabs group channel configurble remove delete
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: ea29959bf79b5e46e876f75570dcb437fa56888f
ms.sourcegitcommit: 61003a14e8a179e1268bbdbd9cf5e904c5259566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64736865"
---
# <a name="create-a-removal-page"></a>Criar uma página de remoção

Você pode estender e aprimorar a experiência do usuário dando suporte a opções de remoção e modificação em seu aplicativo. Teams permite que os usuários renomeiem ou removam uma guia de canal ou grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, a experiência de remoção de tabulação fornece aos usuários opções pós-remoção para excluir ou arquivar conteúdo.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Permitir que sua guia seja reconfigurada após a instalação

Você `manifest.json` define os recursos e as funcionalidades da guia. A propriedade da instância `canUpdateConfiguration` de tabulação usa um valor booliano que indica se um usuário pode modificar ou reconfigurar a guia depois que ela é criada. A tabela a seguir fornece os detalhes da propriedade:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. O padrão é `true`. |

Quando sua guia é carregada em um canal ou chat em grupo, Teams adiciona um menu suspenso de clique com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela configuração`canUpdateConfiguration`. A tabela a seguir fornece os detalhes da configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | descrição |
| ----------------------- | :----: | ----- | ----------- |
|     Settings            |   √    |       |A `configurationUrl` página é recarregada em um IFrame, permitindo que o usuário reconfigure a guia. |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme ele aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a `removeURL` propriedade e o valor forem incluídos na página **de** configuração, a página de remoção será carregada em um IFrame e apresentada ao usuário. Se uma página de remoção não estiver incluída, o usuário receberá uma caixa de diálogo de confirmação.          |

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de guia para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da página de remoção é designada pelo método `setSettings()` em sua página de configuração. Assim como todas as páginas em seu aplicativo, a página de remoção deve estar [em conformidade Teams pré-requisitos da guia](../../../tabs/how-to/tab-requirements.md).

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, na lógica da página de remoção, `registerOnRemoveHandler((RemoveEvent) => {}` você pode invocar o manipulador de eventos quando o usuário remove uma configuração de guia existente. O método usa a [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) interface e executa o código no manipulador quando um usuário tenta remover o conteúdo. O método é usado para executar operações de limpeza, como a remoção do recurso subjacente que está utilizando o conteúdo da guia. Por vez, apenas um manipulador de remoção pode ser registrado.

A `RemoveEvent` interface descreve um objeto com dois métodos:

* A `notifySuccess()` função é necessária. Indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A `notifyFailure(string)` função é opcional. Indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, essa cadeia de caracteres será exibida para o usuário; caso contrário, um erro genérico será exibido.

#### <a name="use-the-getsettings-function"></a>Usar a `getSettings()` função

Você pode usar `getSettings()`para atribuir o conteúdo da guia a ser removido. A `getSettings((Settings) =>{})` função usa e fornece os [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) valores de propriedade de configurações válidos que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Usar a `getContext()` função

Você pode usar `getContext()` para obter o contexto atual no qual o quadro está em execução. A `getContext((Context) =>{})` função usa o [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). A função fornece valores de `Context` propriedade válidos que você pode usar em sua lógica de página de remoção para determinar o conteúdo a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

A autenticação é necessária antes de permitir que um usuário exclua o conteúdo da guia. Informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Consulte [Microsoft Teams de autenticação para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Verifique se todos os domínios usados em suas páginas de guia estão listados na `manifest.json` `validDomains` matriz.

Este é um bloco de código de remoção de guia de exemplo:

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

Quando um usuário seleciona Remover  no menu suspenso da guia, `removeUrl` o Teams carrega a página opcional atribuída na página de configuração **em um** IFrame. O usuário é mostrado um botão carregado `onClick()` `microsoftTeams.settings.setValidityState(true)` com a função que chama e habilita o  botão Remover mostrado na parte inferior do IFrame da página de remoção.

Depois que o manipulador de remoção é executado `removeEvent.notifyFailure()` ou `removeEvent.notifySuccess()` notifica Teams resultado da remoção de conteúdo.

>[!NOTE]
>
> * Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, o Teams remove a guia em casos de êxito e de falha.
> * Depois de invocar o `registerOnRemoveHandler` manipulador de eventos, você terá 15 segundos para responder ao método. Por padrão, Teams habilita **o botão Remover** após cinco segundos, mesmo que você não chame `setValidityState(true)`.
> * Quando o usuário seleciona **Remover**, Teams a guia após 30 segundos, independentemente de as ações serem concluídas ou não.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md)
