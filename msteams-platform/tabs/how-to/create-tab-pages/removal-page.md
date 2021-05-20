---
title: Criar uma página de remoção de guias
author: laujan
description: Como criar uma página de remoção de guias
keywords: equipes guias canal de grupo configurável remover excluir
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: e1a1f38a2bcb3b5bc4bc54f469c8727e44d8695e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566667"
---
# <a name="modify-or-remove-a-channel-group-tab"></a>Modifique ou remova uma guia de grupo de canal

Você pode estender e melhorar a experiência do usuário, suportando opções de remoção e modificação em seu aplicativo. Teams permite que os usuários renomeiem ou removam uma guia canal/grupo e você pode permitir que os usuários reconfigurem sua guia após a instalação. Além disso, sua experiência de remoção de guias pode incluir designar o que acontece com o conteúdo quando sua guia é removida ou dar aos usuários opções pós-remoção, como excluir ou arquivar o conteúdo.

## <a name="enable-your-tab-to-be-reconfigured-after-installation"></a>Habilite que sua guia seja reconfigurada após a instalação

Sua **manifest.jsdefine** os recursos e recursos da sua guia. A propriedade da instância da guia `canUpdateConfiguration` tem um valor booleano que indica se um usuário pode modificar ou reconfigurar a guia depois de criada:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`canUpdateConfiguration`|Booliano|||Um valor indicando se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. inadimplência: `true`|

Quando sua guia for carregada em um canal ou bate-papo em grupo, Teams adicionará um menu suspenso com o botão direito do mouse para a sua guia. As opções disponíveis são determinadas pela `canUpdateConfiguration` configuração:

| `canUpdateConfiguration`| verdadeiro   | falso | descrição |
| ----------------------- | :----: | ----- | ----------- |
|     Configurações            |   √    |       |A `configurationUrl` página é recarregada em um IFrame, permitindo que o usuário reconfigure a guia.  |
|     Renomear              |   √    |   √   | O usuário pode alterar o nome da guia conforme aparece na barra de guia.          |
|     Remover              |   √    |   √   |  Se a  `removeURL` propriedade e o valor estiverem incluídos na página de **configuração,** a **página de remoção** será carregada em um IFrame e apresentada ao usuário. Se uma página de remoção não for incluída, o usuário será apresentado com uma caixa de diálogo confirmada.          |
|||||

## <a name="create-a-tab-removal-page-for-your-application"></a>Crie uma página de remoção de guias para seu aplicativo

A página de remoção opcional é uma página HTML hospedada e é exibida quando a guia é removida. A URL da página de remoção é designada pelo método dentro da `setSettings()` página de configuração. Como em todas as páginas do seu aplicativo, a página de remoção deve cumprir [Teams requisitos da guia](../../../tabs/how-to/tab-requirements.md).

### <a name="register-a-remove-handler"></a>Registre um manipulador de remoção

Opcionalmente, dentro da lógica da página de remoção, você pode invocar o `registerOnRemoveHandler((RemoveEvent) => {}` manipulador de eventos quando o usuário remover uma configuração de guia existente. O método leva na [`RemoveEvent`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.removeevent?view=msteams-client-js-latest&preserve-view=true) interface e executa o código no manipulador quando um usuário tenta remover conteúdo. Ele é usado para executar operações de limpeza, como remover o recurso subjacente que alimenta o conteúdo da guia. Apenas um manipulador de remoção pode ser registrado por vez.

A `RemoveEvent` interface descreve um objeto com dois métodos:

* A `notifySuccess()` função é necessária. Indica que a remoção do recurso subjacente foi bem sucedida e seu conteúdo pode ser removido.

* A `notifyFailure(string)` função é opcional. Indica que a remoção do recurso subjacente falhou e seu conteúdo não pode ser removido. O parâmetro de sequência de cordas opcional especifica uma razão para a falha. Se fornecido, esta sequência é exibida para o usuário; caso contrário, um erro genérico é exibido.

#### <a name="use-the-getsettings-function"></a>Use a `getSettings()` função

Você pode usar `getSettings()` para designar o conteúdo da guia a ser removido. A `getSettings((Settings) =>{})` função leva no e fornece as [`Settings interface`](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) configurações válidas valores de propriedade que podem ser recuperados.

#### <a name="use-the-getcontext-function"></a>Use a `getContext()` função

Você pode usar `getContext()` para recuperar o contexto atual em que o quadro está em execução. A `getContext((Context) =>{})` função leva no e fornece [`Context interface`](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) valores de propriedade válidos `Context` que você pode usar em sua lógica de página de remoção para determinar o conteúdo a ser exibido na página de remoção.

#### <a name="include-authentication"></a>Incluir autenticação

Você pode exigir autenticação antes de permitir que um usuário exclua o conteúdo da guia. As informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e solicitar urls de página de autorização. Consulte [Microsoft Teams fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-flow-tab.md). Certifique-se de que todos os domínios usados nas páginas da guia estejam listados no `manifest.json` `validDomains` array.

Abaixo está um bloco de código de remoção de guia de amostra:

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

Quando um usuário selecionar **Remover** do menu suspenso da guia, Teams carregará a página opcional `removeUrl` (designada na **página de configuração)** em um IFrame. Aqui, o usuário é apresentado com um botão carregado com a `onClick()` função que chama e habilita o botão `microsoftTeams.settings.setValidityState(true)` **Remover** localizado perto da parte inferior da página de remoção IFrame.

Após a execução do manipulador de `removeEvent.notifySuccess()` remoção, ou `removeEvent.notifyFailure()` notifica Teams do resultado de remoção de conteúdo.

>[!NOTE]
> * Para garantir que o controle de um usuário autorizado sobre uma guia não seja inibido, Teams removerá a guia em casos de sucesso e falha.\
> * Teams habilita o botão **Remover** após 5 segundos, mesmo que sua guia não tenha chamado `setValidityState()` .\
> * Quando o usuário seleciona **Remover** Teams remove a guia após 30 segundos, independentemente de suas ações terem sido concluídas.
