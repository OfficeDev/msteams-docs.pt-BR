---
title: Criar uma página de remoção de guias
author: laujan
description: Como criar uma página de remoção de guia
keywords: guias do teams grupo de grupos configuráveis remover excluir
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4ee060b8ef1f439ed4f8e4007e63606ce34c3d24
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964589"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Modificar ou remover uma guia de grupo de canais

Você pode estender e aprimorar a experiência do usuário oferecendo suporte às opções de remoção e modificação no seu aplicativo. O Microsoft Teams permite que os usuários renomeie ou removam uma guia de canal/grupo e você possa permitir que os usuários reconfigurem sua guia após a instalação. Além disso, sua experiência de remoção de guia pode incluir a designação do que acontece com o conteúdo quando sua guia é removida ou com opções de remoção de usuários, como excluir ou arquivar o conteúdo.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Habilitar sua guia para ser reconfigurada após a instalação

O **manifest.js** define os recursos e recursos da guia. A Propriedade Tab Instance `canUpdateConfiguration` tem um valor Boolean que indica se um usuário pode modificar ou reconfigurar a guia após ela ser criada:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Será `true`|

Quando sua guia for carregada para um chat de grupo ou canal, o Microsoft Teams adicionará um menu suspenso de clique com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela `canUpdateConfiguration` configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | description |
| ----------------------- | :----: | ----- | ----------- |
|     Configurações            |   √    |       |A `configurationUrl` página é recarregada em um iframe, permitindo que o usuário Reconfigure a guia.  |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme ele aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a  `removeURL` propriedade e o valor são incluídos na **página de configuração**, a **página de remoção** é carregada em um iframe e apresentada ao usuário. Se uma página de remoção não for incluída, a caixa de diálogo confirmar será exibida para o usuário.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de guia para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da página de remoção é designada pelo `setSettings()` método dentro da sua página de configuração. Como em todas as páginas em seu aplicativo, a página de remoção deve estar em conformidade com [os requisitos de guia do teams](~/tabs/how-to/add-tab.md).

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, em sua lógica de página de remoção, você pode invocar o `registerOnRemoveHandler((RemoveEvent) => {}` manipulador de eventos quando o usuário remove uma configuração de guia existente. O método utiliza a [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) interface e executa o código no manipulador quando um usuário tenta remover conteúdo. Ele é usado para realizar operações de limpeza, como remover o recurso subjacente que força o conteúdo da guia. Somente um manipulador de remoção pode ser registrado por vez.

A `RemoveEvent` interface descreve um objeto com dois métodos:

* A `notifySuccess()` função é necessária. Ela indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A `notifyFailure(string)` função é opcional. Ela indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, esta cadeia de caracteres é exibida para o usuário; caso contrário, um erro genérico é exibido.

#### <a name="use-the-getsettings-function"></a>Usar a `getSettings()` função

Você pode usar `getSettings()` o para designar o conteúdo da guia a ser removido. A `getSettings((Settings) =>{})` função assume o [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) e fornece os valores de propriedade de configurações válidos que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Usar a `getContext()` função

Você pode usar `getContext()` o para recuperar o contexto atual no qual o quadro está sendo executado. A `getContext((Context) =>{})` função assume o [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) e fornece valores de `Context` Propriedade válidos que você pode usar em sua lógica de página de remoção para determinar o conteúdo a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

Você pode exigir autenticação antes de permitir que um usuário exclua o conteúdo da guia. As informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Confira [o fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Certifique-se de que todos os domínios usados nas páginas da guia estão listados na `manifest.json` `validDomains` matriz.

Veja a seguir um exemplo de bloco de código de remoção de guia:

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

Quando um usuário seleciona **remover** no menu suspenso da guia, o Teams carregará a página opcional `removeUrl` (designada na **página de configuração**) em um iframe. Aqui, o usuário recebe um botão carregado com a `onClick()` função que chama `microsoftTeams.settings.setValidityState(true)` e habilita o botão **remover** localizado próximo à parte inferior da página de remoção iframe.

Após a execução do manipulador remove, `removeEvent.notifySuccess()` ou `removeEvent.notifyFailure()` notifica as equipes sobre o resultado da remoção de conteúdo.

>[!NOTE]
>Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, o Microsoft Teams removerá a guia nos casos de êxito e de falha. \
>O Microsoft Teams habilita o botão **remover** após 5 segundos, mesmo se sua guia não tiver chamado `setValidityState()` . \
>Quando o usuário seleciona **remover** o Teams remove a guia após 30 segundos, independentemente de suas ações terem sido concluídas.
