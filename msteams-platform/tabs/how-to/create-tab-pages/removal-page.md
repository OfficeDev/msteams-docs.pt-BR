---
title: Criar uma página de remoção de guias
author: laujan
description: Como criar uma página de remoção de tabulação
keywords: teams tabs group channel configurble remove delete
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8f01780dce9aa0450169d4c699471bb2ac5bd9a0
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019584"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Modificar ou remover uma guia grupo de canais

Você pode estender e aprimorar a experiência do usuário suportando opções de remoção e modificação em seu aplicativo. O Teams permite que os usuários renomeiem ou removam uma guia canal/grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, sua experiência de remoção de tabulação pode incluir a designação do que acontece com o conteúdo quando sua guia é removida ou dar aos usuários opções pós-remoção, como excluir ou arquivar o conteúdo.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Permitir que sua guia seja reconfigurada após a instalação

Seu **manifest.json** define os recursos e recursos da guia. A propriedade da instância de tabulação assume um valor Boolean que indica se um usuário pode modificar ou reconfigurar a guia depois `canUpdateConfiguration` que ela for criada:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: `true`|

Quando sua guia for carregada em um canal ou chat de grupo, o Teams adicionará um menu suspenso com o botão direito do mouse para sua guia. As opções disponíveis são determinadas pela `canUpdateConfiguration` configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | description |
| ----------------------- | :----: | ----- | ----------- |
|     Settings            |   √    |       |A `configurationUrl` página é recarregada em um IFrame permitindo que o usuário reconfigure a guia.  |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme aparece na barra de guias.          |
|     Remover              |   √    |   √   |  Se a propriedade e o valor são incluídos na página de configuração , a página de remoção é carregada em `removeURL` um IFrame e apresentada ao usuário.   Se uma página de remoção não estiver incluída, o usuário será apresentado com uma caixa de diálogo confirmar.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Criar uma página de remoção de tabulação para seu aplicativo

A página de remoção opcional é uma página HTML que você hospeda e é exibida quando a guia é removida. A URL da página de remoção é designada pelo `setSettings()` método em sua página de configuração. Assim como todas as páginas em seu aplicativo, a página de remoção deve estar em conformidade com os requisitos [de guia do Teams.](../../../tabs/how-to/tab-requirements.md)

### <a name="register-a-remove-handler"></a>Registrar um manipulador de remoção

Opcionalmente, na lógica da página de remoção, você pode invocar o manipulador de eventos quando o usuário `registerOnRemoveHandler((RemoveEvent) => {}` remover uma configuração de guia existente. O método entra na interface e executa o código no [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) manipulador quando um usuário tenta remover o conteúdo. Ele é usado para executar operações de limpeza, como a remoção do recurso subjacente que powering o conteúdo da guia. Somente um manipulador de remoção pode ser registrado por vez.

A `RemoveEvent` interface descreve um objeto com dois métodos:

* A `notifySuccess()` função é necessária. Indica que a remoção do recurso subjacente foi bem-sucedida e seu conteúdo pode ser removido.

* A `notifyFailure(string)` função é opcional. Indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de cadeia de caracteres opcional especifica um motivo para a falha. Se fornecido, essa cadeia de caracteres será exibida para o usuário; caso contrário, um erro genérico é exibido.

#### <a name="use-the-getsettings-function"></a>Usar a `getSettings()` função

Você pode usar `getSettings()` para designar o conteúdo da guia a ser removido. A função assume e fornece os valores de propriedade `getSettings((Settings) =>{})` [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) de configurações válidos que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Usar a `getContext()` função

Você pode usar `getContext()` para recuperar o contexto atual no qual o quadro está sendo executado. A função usa os valores de propriedade válidos que você pode usar na lógica da página de remoção para determinar o conteúdo a ser exibido `getContext((Context) =>{})` [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) na página de `Context` remoção.

#### <a name="include-authentication"></a>Incluir autenticação

Você pode exigir autenticação antes de permitir que um usuário exclua o conteúdo da guia. As informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização. Consulte [Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Certifique-se de que todos os domínios usados em suas páginas de tabulação estão listados na `manifest.json` `validDomains` matriz.

Abaixo está um bloco de código de remoção de tabulação de exemplo:

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

Quando um usuário seleciona **Remover** do menu suspenso da guia, o Teams carregará a página opcional (designada na página de configuração `removeUrl` ) em um IFrame.  Aqui, o usuário é apresentado com um botão carregado com a função que chama e habilita o botão Remover localizado próximo à parte inferior da página de remoção `onClick()` `microsoftTeams.settings.setValidityState(true)` IFrame. 

Após a execução do manipulador remove ou `removeEvent.notifySuccess()` `removeEvent.notifyFailure()` notifica o Teams sobre o resultado da remoção de conteúdo.

>[!NOTE]
>Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, o Teams removerá a guia em casos de sucesso e falha.\
>O Teams habilita **o botão Remover** após 5 segundos, mesmo que sua guia não tenha chamado `setValidityState()` .\
>Quando o usuário seleciona **Remover** o Teams, remove a guia após 30 segundos, independentemente de suas ações ter sido concluídas.
