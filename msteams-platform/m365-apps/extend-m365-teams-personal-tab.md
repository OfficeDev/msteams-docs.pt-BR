---
title: Estender um Teams guia pessoal em Microsoft 365
description: Estender um Teams guia pessoal em Microsoft 365
ms.date: 11/15/2021
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 27d690ca72ffe41fdcdfe39fcd5d7c203c9b3e7c
ms.sourcegitcommit: c65a868744e4108b5d786de2350981e3f1f05718
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62081069"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Estender uma Teams guia pessoal entre Microsoft 365

> [!NOTE]
> *Estender uma guia Teams pessoal em* Microsoft 365 está disponível no momento apenas na [visualização do desenvolvedor público.](../resources/dev-preview/developer-preview-intro.md) Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

As guias pessoais fornecem uma ótima maneira de aprimorar a experiência Microsoft Teams pessoal. Usando guias pessoais, você pode fornecer a um usuário acesso ao seu aplicativo dentro Teams, sem que o usuário tenha que deixar a experiência ou entrar novamente. Com essa visualização, as guias pessoais podem ser acesas em outros Microsoft 365 aplicativos. Este tutorial demonstra o processo de tomar uma guia Teams pessoal existente e atualizá-la para ser executado em experiências da Outlook da área de trabalho e da Web e também Office na Web (office.com).

Atualizar seu aplicativo pessoal para ser executado no Outlook e Office Home envolve estas etapas:

> [!div class="checklist"]
> * Atualizar o manifesto do aplicativo
> * Atualizar suas referências do SDK do TeamsJS 
> * Alterar seus headers de Política de Segurança de Conteúdo
> * Atualizar seu AAD registro de aplicativo para SSO (registro único)

Testar seu aplicativo exigirá as seguintes etapas:

> [!div class="checklist"]
> * Registrar seu locatário do M365 *em Office 365 Versões Direcionadas*
> * Configurar sua conta para acessar versões de visualização de Outlook e Office aplicativos
> * Fazer sideload do aplicativo atualizado em Teams

Após essas etapas, seu aplicativo deve aparecer nas versões de visualização Outlook e Office aplicativos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará:

* Um locatário Microsoft 365 área de área de trabalho do Programa de Desenvolvedores
* Seu locatário de área de Office 365 *Versões Direcionadas*
* Um computador com Office aplicativos instalados no canal Microsoft 365 Apps *beta*
* (Opcional) [Teams Toolkit](https://aka.ms/teams-toolkit) extensão para Visual Studio Code ajudar a atualizar seu código

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Preparar sua guia pessoal para a atualização

Se você tiver um aplicativo de guia pessoal existente, faça uma cópia ou uma ramificação do seu projeto de produção para testar e atualizar a ID do aplicativo no manifesto do aplicativo para usar um novo identificador (distinto da ID do aplicativo de produção).

Se você quiser usar código de exemplo para concluir este tutorial, siga as etapas de instalação em Introdução a [Todo List Sample](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) para criar um aplicativo de guia pessoal usando a extensão Teams Toolkit para Visual Studio Code. Ou, você pode começar com o mesmo Exemplo de Lista Inteira atualizado para o [TeamsJS SDK v2 Preview](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend-M365) e prosseguir para Visualizar sua guia pessoal em outras experiências Microsoft 365 [do](#preview-your-personal-tab-in-other-microsoft-365-experiences)TeamsJS. O exemplo atualizado também está disponível em uma extensão *Teams Toolkit:* Amostras de Exibição de Desenvolvimento Toda List (Funciona em  >    >  **Teams, Outlook e Office)**.

:::image type="content" source="images/toolkit-todo-sample.png" alt-text="Exemplo de Lista Inteira (Funciona em Teams, Outlook e Office) em Teams Toolkit":::


## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar o [](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) esquema de manifesto Teams de visualização do desenvolvedor e a versão do manifesto para habilitar sua guia pessoal Teams para ser executado em Office e `m365DevPreview` Outlook.

Você pode usar o Teams Toolkit para atualizar o manifesto do aplicativo ou aplicar as alterações manualmente:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Abra a *paleta Comando:*`Ctrl+Shift+P`
1. Execute o `Teams: Upgrade Teams manifest to support Outlook and Office apps` comando e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra seu Teams de aplicativo e atualize `$schema` o e com os seguintes `manifestVersion` valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```
---

Se você usou Teams Toolkit para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar quaisquer erros. Abra a paleta de comandos e encontre Teams: Valide o arquivo de manifesto ou selecione a opção no menu Implantação do Teams Toolkit (procure o ícone Teams no lado esquerdo do `Ctrl+Shift+P` Visual Studio Code). 

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Teams Toolkit opção &quot;Validar arquivo de manifesto&quot; no menu 'Implantação'":::

## <a name="update-sdk-references"></a>Atualizar referências do SDK

Para ser executado em Outlook e Office, seu aplicativo precisará depender do pacote npm (ou de uma `@microsoft/teams-js@2.0.0-beta.1` versão *beta* posterior). Embora o código com versões de nível versões de Outlook e Office Office serão, `@microsoft/teams-js` eventualmente, `@microsoft/teams-js` cessadas. Outlook

Você pode usar o Teams Toolkit para ajudar a automatizar algumas das alterações de código para adotar a próxima versão de , mas se quiser executar as etapas `@microsoft/teams-js` manualmente, consulte [Microsoft Teams JavaScript client SDK Preview](using-teams-client-sdk-preview.md) para obter detalhes.

1. Abra a *paleta Comando:*`Ctrl+Shift+P`
1. Executar o comando `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Após a conclusão, o utilitário atualizará seu arquivo com a dependência do TeamsJS SDK Preview ( ou posterior) e seus arquivos serão `package.json` `@microsoft/teams-js@2.0.0-beta.1` atualizados `*.js/.ts` `*.jsx/.tsx` com:

> [!div class="checklist"]
> * `package.json` referências ao TeamsJS SDK Preview
> * Instruções de importação para o TeamsJS SDK Preview
> * [Chamadas de Função, Enum e Interface](using-teams-client-sdk-preview.md#apis-organized-into-capabilities) para Visualização do SDK do TeamsJS
> * `TODO` lembretes de comentário para revisar áreas que podem ser afetadas por alterações de interface [de](using-teams-client-sdk-preview.md#updates-to-the-context-interface) contexto
> * `TODO` lembretes de comentário para garantir que as funções de conversão para [promessas](using-teams-client-sdk-preview.md#callbacks-converted-to-promises) de funções de estilo de retorno de chamada foram bem em todos os sites de chamada encontrados pela ferramenta

> [!IMPORTANT]
> O código *.html* arquivos não é suportado pela ferramenta de atualização e exigirá alterações manuais.

> [!NOTE]
> Se você deseja atualizar manualmente seu código, consulte [Microsoft Teams JavaScript client SDK Preview](using-teams-client-sdk-preview.md) para saber mais sobre as alterações necessárias.

## <a name="configure-content-security-policy-headers"></a>Configurar os headers da Política de Segurança de Conteúdo

[Assim como no Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs), os aplicativos de tabulação são hospedados em ([elementos iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)) em Office e Outlook web.

Se seu aplicativo [](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) fizer uso de headers de Política de Segurança de Conteúdo (CSP), [certifique-se](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) de que você está permitindo todos os seguintes ancestrais de quadro em seus headers CSP:

|Microsoft 365 host| permissão frame-ancestral|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com` |

## <a name="update-aad-app-registration-for-sso"></a>Atualizar AAD registro de aplicativo para SSO

Azure Active Directory O logor único (SSO) para guias pessoais funciona da mesma maneira no Office e no Outlook como no [Teams](/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso), no entanto, você precisará adicionar vários identificadores de aplicativo cliente ao registro do aplicativo AAD do aplicativo de tabulação no portal de registros de *aplicativos* do locatário.

1. Entre no [portal do Azure](https://portal.azure.com) com sua conta de locatário de área de reserva.
1. Abra a **folha Registros de** aplicativo.
1. Selecione o nome do aplicativo de guia pessoal para abrir seu registro de aplicativo. 
1. Selecione  **Expor uma API** (em *Gerenciar*).

:::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorizar IDs de cliente da folha *Registros de aplicativo* no Portal do Azure":::

Na seção **Aplicativos cliente autorizados,** verifique se todos os seguintes `Client Id` valores são adicionados:

|Microsoft 365 cliente | ID do cliente |
|--|--|
|Teams desktop, mobile |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Teams Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Office.com  |4345a7b9-9a63-4910-a426-35363201d503|
|Office.com  |4765445b-32c6-49b0-83e6-1d93765276ca|
|Office desktop  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
|Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-0000000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-app-in-teams"></a>Faça o sideload do seu aplicativo do Teams

A etapa final é fazer sideload da guia pessoal atualizada ([pacote de aplicativos](/microsoftteams/platform/concepts/build-and-test/apps-package)) no Microsoft Teams. Depois de concluído, seu aplicativo estará disponível para ser executado em Office e Outlook, além de Teams.

1. Empacote seu Teams aplicativo [(ícones](/microsoftteams/platform/resources/schema/manifest-schema#icons)de manifesto e aplicativo ) em um arquivo zip. Se você usou Teams Toolkit para criar seu aplicativo, pode facilmente fazer isso usando a opção de pacote de **metadados zip Teams** no menu Implantação do Teams Toolkit ou na Paleta de Comando do  `Ctrl+Shift+P` Visual Studio Code:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Opção 'Pacote Teams de metadados zip' Teams Toolkit extensão para Visual Studio Code":::

1. Faça logoff Teams com sua conta de locatário de área de segurança e verifique se você está na Visualização do Desenvolvedor Público. Você pode verificar se você está na visualização no cliente Teams clicando no menu reellipse (**...**)  pelo perfil de usuário e abrindo **Sobre** para verificar se a opção Visualização do Desenvolvedor está alternada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No Teams menu de releições, abra a opção 'Sobre' e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

1. Abra o *painel Aplicativos* e clique **Upload um aplicativo** personalizado e, em seguida, Upload para mim ou minhas **equipes.**

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Botão &quot;Upload um aplicativo personalizado&quot; no painel Teams &quot;Aplicativos&quot;":::

1. Selecione seu pacote de aplicativos e clique em *Abrir*.

Depois de ser recarregada Teams, sua guia pessoal estará disponível Outlook e Office. Certifique-se de entrar com as mesmas credenciais usadas para fazer sideload do aplicativo Teams.

Você pode fixar o aplicativo para acesso rápido, ou pode encontrar seu aplicativo no sobrevoo de releitos (**...**) entre aplicativos recentes na barra lateral à esquerda.

> [!NOTE]
> Fixar um aplicativo no Teams não o fixará como um aplicativo em Office.com ou Outlook.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Visualizar sua guia pessoal em outras Microsoft 365 experiências

Quando você atualiza sua guia Teams pessoal e a descarrega no Teams, ela também será Outlook clientes de área de trabalho e web e Office na Web (office.com). Veja como visualizar essas experiências Microsoft 365.

### <a name="outlook"></a>Outlook

Para exibir seu aplicativo em execução Outlook na área de trabalho Windows, Outlook e entre usando sua conta de locatário dev. Clique nas releições (**...**) na barra lateral. Seu título de aplicativo sideload aparecerá entre seus aplicativos instalados.

:::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Clique na opção releições ('Mais aplicativos') na barra lateral do cliente da área de trabalho Office para ver suas guias pessoais instaladas":::

Clique no ícone do aplicativo para iniciar seu aplicativo Outlook.

### <a name="outlook-on-the-web"></a>Outlook na Web

Para exibir seu aplicativo Outlook na Web, visite https://outlook.office.com e entre usando sua conta de locatário dev. Clique nas releições (**...**) na barra lateral. Seu título de aplicativo sideload aparecerá entre seus aplicativos instalados.

:::image type="content" source="images/outlook-web-more-apps.png" alt-text="Clique na opção releitos ('Mais aplicativos') na barra lateral do outlook.com para ver suas guias pessoais instaladas":::

Clique no ícone do aplicativo para iniciar e visualizar seu aplicativo em execução Outlook na Web.

### <a name="office-on-the-web"></a>Office na Web

> [!IMPORTANT]
> Consulte as atualizações mais recentes no [Microsoft Teams - Microsoft 365 Blog](https://devblogs.microsoft.com/microsoft365dev/) do Desenvolvedor para verificar se o suporte Office.com para Teams aplicativos pessoais está disponível para seu locatário de teste.

Para visualizar seu aplicativo em execução Office na Web, faça logoff office.com com credenciais de locatário de teste. Clique nas releições (**...**) na barra lateral. Seu título de aplicativo sideload aparecerá entre seus aplicativos instalados.

Clique no ícone do aplicativo para iniciar seu aplicativo no Office Home.

## <a name="next-steps"></a>Próximas etapas

Outlook e Office pessoais habilitadas para uso estão em visualização e não têm suporte para uso de produção. Veja como distribuir seu aplicativo de guia pessoal para visualizar audiências para fins de teste.

### <a name="single-tenant-distribution"></a>Distribuição de locatário único

Outlook e Office pessoais habilitadas para Office podem ser distribuídas para um público-alvo de visualização em um locatário de teste (ou produção) de uma das três maneiras:

#### <a name="teams-client"></a>Teams cliente

No menu *Aplicativos,* selecione *Gerenciar seus*  >  **aplicativos Envie um aplicativo para sua organização.** Isso requer aprovação do administrador de IT.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Como administrador Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização de https://admin.teams.microsoft.com/ . Consulte [Upload seus aplicativos personalizados no centro de administração Microsoft Teams para](/MicrosoftTeams/upload-custom-apps) obter detalhes.

#### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote de aplicativos de https://admin.microsoft.com/ . Consulte [Test and deploy Microsoft 365 Apps by partners in the Integrated apps portal](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) for details.

### <a name="multi-tenant-distribution"></a>Distribuição de vários locatários

A distribuição para o Microsoft AppSource não é suportada durante essa visualização inicial do desenvolvedor do Outlook e Office guias Teams pessoais.
