---
title: Estender um aplicativo de guia pessoal do Teams Microsoft 365
description: Estender um aplicativo de guia pessoal do Teams Microsoft 365
ms.date: 05/24/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: abdd21eae707b2edf180a77f3fe25aaed3b165e5
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654564"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Estender uma guia pessoal do Teams Microsoft 365

As guias pessoais fornecem uma ótima maneira de aprimorar a experiência do Microsoft Teams. Usando guias pessoais, você pode fornecer a um usuário acesso ao aplicativo diretamente no Teams, sem que o usuário precise sair da experiência ou entrar novamente. Com essa versão prévia, as guias pessoais podem se acender em outros Microsoft 365 aplicativos. Este tutorial demonstra o processo de pegar uma guia pessoal existente do Teams e atualizá-la para ser executada em experiências da área de trabalho e da Web do Outlook e também do Office na Web (office.com).

Atualizar seu aplicativo pessoal para ser executado em Outlook e Office envolve estas etapas:

> [!div class="checklist"]
>
> * Atualizar o manifesto do aplicativo
> * Atualizar suas referências do SDK do TeamsJS
> * Corrigir os cabeçalhos da Política de Segurança de Conteúdo
> * Atualize seu Microsoft Azure Active Directory (Azure AD) registro de aplicativo para SSO (logon único)
> * Realizar sideload do aplicativo atualizado no Teams

O restante deste guia explicará essas etapas e mostrará como visualizar sua guia pessoal em outros Microsoft 365 aplicativos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de:

* Um locatário Microsoft 365 área restrita do Programa para Desenvolvedores
* Seu locatário de área restrita registrado em *Versões direcionadas do Office 365*
* Um computador com aplicativos do Office instalados do *Canal beta* do Microsoft 365 Apps
* (Opcional) [Kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para o Microsoft Visual Studio Code para ajudar a atualizar seu código

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Preparar sua guia pessoal para a atualização

Se você tiver um aplicativo de guia pessoal existente, faça uma cópia ou uma ramificação do projeto de produção para testar e atualizar a ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção, para teste).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de configuração no [](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) Exemplo de Lista de Tarefas Pendentes para criar um aplicativo de guia pessoal usando a extensão Teams Toolkit para Visual Studio Code e, em seguida, retorne a este artigo para atualizá-lo para Microsoft 365.

Como alternativa, você pode usar um aplicativo Hello *World* do Sign-On básico já habilitado Microsoft 365 na seção de início rápido a seguir e, em seguida, pular para [Sideload](#sideload-your-app-in-teams) do aplicativo no Teams.

### <a name="quickstart"></a>Início rápido

Para começar com uma [guia pessoal](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) que já está habilitada para execução no Outlook e Office, use Teams Toolkit extensão para Visual Studio Code.

1. No Visual Studio Code, abra a paleta de comandos (`Ctrl+Shift+P`), digite `Teams: Create a new Teams app`.
1. Selecione **a guia pessoal habilitada para SSO**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Amostra de Lista de tarefas (Funciona no Teams, Outlook e Office) no Kit de Ferramentas do Teams":::

1. Selecione um local no computador local para a pasta do workspace.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) `Teams: Provision in the cloud` e digite para criar os recursos de aplicativo necessários (Serviço de Aplicativo plano, Armazenamento conta, Aplicativo de Funções, Identidade Gerenciada) em sua conta do Azure.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Deploy to the cloud` para implantar o código de exemplo nos recursos provisionados no Azure e inicie o aplicativo.

A partir daqui, você pode pular para [Sideload do aplicativo no Teams](#sideload-your-app-in-teams) e visualizar seu aplicativo no Outlook e Office. (O manifesto do aplicativo e as chamadas à API do TeamsJS já foram atualizados para Microsoft 365.)

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar a versão [](../resources/schema/manifest-schema.md) `1.13` do esquema de manifesto Teams desenvolvedor para habilitar sua guia pessoal do Teams para ser executada Outlook e Office.

Você tem duas opções para atualizar o manifesto do aplicativo:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a paleta de comandos: `Ctrl+Shift+P`.
1. Execute o `Teams: Upgrade Teams manifest` e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas em vigor.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o Teams manifesto do aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Se você usou o kit de ferramentas do Teams para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos (`Ctrl+Shift+P`) e **localize Teams: Validar arquivo de manifesto**.

## <a name="update-sdk-references"></a>Atualizar referências do SDK

Para ser executado Outlook e Office, seu aplicativo precisará fazer referência ao npm pacote `@microsoft/teams-js@2.0.0` (ou superior). Embora o código com versões de nível inferior tenha suporte no Outlook e no Office, os avisos de substituição serão registrados e o suporte para versões de nível inferior do TeamsJS no Outlook e no Office eventualmente será interrompida.

Você pode usar Teams Toolkit para ajudar a identificar e automatizar as alterações de código necessárias para atualizar das versões do TeamsJS 1.x para o TeamsJS versão 2.0.0. Como alternativa, você pode executar as mesmas etapas manualmente; consulte o [Microsoft Teams SDK do cliente JavaScript](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para obter detalhes.

1. Abra a *paleta comando*: `Ctrl+Shift+P`.
1. Execute o comando `Teams: Upgrade Teams JS SDK and code references`.

Após a conclusão, *o arquivo package.json* fará referência `@microsoft/teams-js@2.0.0` (ou superior) `*.js/.ts` `*.jsx/.tsx` e seus arquivos serão atualizados com:

> [!div class="checklist"]
> * Instruções de importação para teams-js@2.0.0
> * [Chamadas de função, enumeração e interface](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para teams-js@2.0.0
> * `TODO` lembretes de comentário sinalizando áreas que podem ser afetadas por alterações [de interface de](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface) contexto
> * `TODO` lembretes de comentário para [converter funções de retorno de chamada em promessas](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> O código *.html* não tem suporte nas ferramentas de atualização e exigirá alterações manuais.


## <a name="configure-content-security-policy-headers"></a>Configurar cabeçalhos de Política de Segurança de Conteúdo

Como no Microsoft Teams, os aplicativos de tabulação são hospedados em elementos [de iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) Office e Outlook web.

Se seu aplicativo usa cabeçalhos [CSP (Política](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) de Segurança de Conteúdo), [certifique-se](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) de permitir todos os seguintes ancestrais de quadro em seus cabeçalhos CSP:

|Microsoft 365 host| permissão de ancestral de quadro|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Atualizar o registro de aplicativo do Azure AD para SSO

[Azure Active Directory (AD) SSO (](../tabs/how-to/authentication/auth-aad-sso.md)logon único) para guias pessoais funciona da mesma maneira no Office e no Outlook como no Teams. No entanto, você precisará adicionar vários identificadores de aplicativo cliente ao registro Azure AD aplicativo de Azure AD do aplicativo guia *no portal de* Registros de aplicativo locatário.

1. Entre no [portal do Microsoft Azure](https://portal.azure.com) com sua conta de locatário da área restrita.
1. Abra a folha **Registros de aplicativo**.
1. Selecione o nome do aplicativo de guia pessoal para abrir o registro do aplicativo.
1. Selecionar **Expor uma API** (em *Gerenciar*).

    :::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorizar IDs do cliente da folha *Registros de aplicativo* no portal do Azure":::

1. Na seção **Aplicativos do cliente autorizados**, verifique se todos os valores a seguir `Client Id` foram adicionados:

|Microsoft 365 aplicativo cliente | ID do cliente |
|--|--|
|Área de trabalho do Teams, celular |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Web do Teams |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Office.com  |4765445b-32c6-49b0-83e6-1d93765276ca|
|Office para a área de trabalho  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
|Outlook para área de trabalho | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-app-in-teams"></a>Faça o sideload do seu aplicativo do Teams

A etapa final para executar seu aplicativo no Office e Outlook é fazer sideload do pacote de aplicativos de guia pessoal atualizado no [](..//concepts/build-and-test/apps-package.md) Microsoft Teams.

1. Empacote seu Teams aplicativo ([ícones](../resources/schema/manifest-schema.md) de manifesto [e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, poderá fazer isso facilmente usando a opção **Compactar o pacote de metadados do Teams** no menu *Implantação* do Kit de Ferramentas do Teams:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Pacote de metadados do Zip Teams' na extensão do Kit de Ferramentas do Teams para Visual Studio Code":::

1. Entre no Teams com sua conta de locatário de área restrita e alterne para o modo *de Visualização do* Desenvolvedor. Selecione o menu de reticências (**...**) pelo perfil do usuário e, em seguida, selecione: Sobre > **Desenvolvedor.**

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No Teams de reticências, abra 'Sobre' e selecione a opção 'Visualização do Desenvolvedor'":::

1. Selecione *Aplicativos* para abrir **o painel Gerenciar seus** aplicativos. Em seguida, **selecione Publicar um aplicativo**.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Abra o painel 'Gerenciar seus aplicativos' e selecione 'Publicar um aplicativo'":::

1. Escolha **Upload uma opção de aplicativo personalizado** e selecione o pacote do aplicativo.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="'Upload um aplicativo personalizado' no Teams":::

Após o sideload para Teams, sua guia pessoal estará disponível no Outlook e Office. Certifique-se de entrar com as mesmas credenciais usadas para entrar no Teams sideload do aplicativo.

Você pode fixar o aplicativo para acesso rápido ou encontrar seu aplicativo nas reticências (**...**) entre aplicativos recentes na barra lateral à esquerda. Fixar um aplicativo no Teams não o fixará como um aplicativo no Office ou Outlook.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Visualizar sua guia pessoal em outras Microsoft 365 experiências

Veja como visualizar seu aplicativo em execução no Office e Outlook, web e Windows desktop.

> [!NOTE]
> Desinstalar seu aplicativo Teams também o removerá dos catálogos mais  aplicativos no Outlook e Office. Se você estiver usando o aplicativo de exemplo Teams Toolkit fornecido acima

### <a name="outlook-on-windows"></a>Outlook no Windows

Para exibir seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook e entre usando sua conta de locatário de desenvolvimento.
1. Na barra lateral, selecione  **Mais Aplicativos**. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo Outlook.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Outlook para ver suas guias pessoais instaladas":::

### <a name="outlook-on-the-web"></a>Outlook na Web

Para exibir seu aplicativo no Outlook na Web:

1. Navegue até [Outlook na Web](https://outlook.office.com) e entre usando sua conta de locatário de desenvolvimento.
1. Selecione as reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar e visualizar seu aplicativo em execução Outlook na Web.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do outlook.com para ver as guias pessoais instaladas":::

### <a name="office-on-windows"></a>Office no Windows

Para exibir seu aplicativo em execução no Office na área de trabalho do Windows:

1. Inicie o Office e entre usando sua conta de locatário de desenvolvimento.
1. Selecione as reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo Office.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Office para ver suas guias pessoais instaladas":::

### <a name="office-on-the-web"></a>Office na Web

Para visualizar seu aplicativo em execução no Office na Web:

1. Faça logon office.com credenciais de locatário de teste.
1. Selecione o **ícone Aplicativos** na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo Office na Web.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Clique na opção 'Mais aplicativos' na barra lateral do office.com para ver as guias pessoais instaladas":::

## <a name="troubleshooting"></a>Solução de problemas

Atualmente, um subconjunto de Teams tipos de aplicativos e funcionalidades tem suporte em Outlook e Office clientes. Esse suporte se expandirá ao longo do tempo. 

Consulte o [Microsoft 365 para verificar](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook) o suporte ao host para vários recursos do TeamsJS.

Para obter um resumo geral Microsoft 365 suporte de host e plataforma para aplicativos Teams, consulte [Estender Teams aplicativos](overview.md) em Microsoft 365.

Você pode verificar o suporte de host de um determinado recurso em runtime `isSupported()` chamando a função nesse recurso (namespace) e ajustando o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo ilumine a interface do usuário e a funcionalidade em hosts que dão suporte a ele e forneça uma experiência de fallback normal em hosts que não dão suporte. Para obter mais informações, consulte [Diferenciar sua experiência de aplicativo](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Use os canais [Microsoft Teams comunidade de desenvolvedores para](/microsoftteams/platform/feedback) relatar problemas e fornecer comentários.

### <a name="debugging"></a>Depuração

No Teams Toolkit, você pode depurar (`F5`) seu aplicativo guia em execução no Office e Outlook, além de Teams.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Escolha entre Teams, Outlook e Office destinos de depuração no Teams Toolkit":::

Na primeira execução da depuração local para Office ou Outlook, você será solicitado a entrar em sua conta de locatário do Microsoft 365 e instalar um certificado de teste autoassinado. Você também será solicitado a instalar manualmente Teams. Selecione **Instalar no Teams** para abrir uma janela do navegador e instalar manualmente seu aplicativo. Em seguida, **clique em Continuar** para continuar a depurar seu aplicativo Office/Outlook.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Toolkit diálogo Teams instalação":::

Forneça comentários e relate quaisquer problemas com a experiência Teams Toolkit depuração no [Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx/issues).

## <a name="next-steps"></a>Próximas etapas

Publique seu aplicativo para ser detectável Teams, Outlook e Office:

> [!div class="nextstepaction"]
> [Publicar Teams aplicativos para Outlook e Office](publish.md)

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
| Lista de Tarefas Pendentes | Lista de tarefas pendentes editáveis com SSO criado com React e Azure Functions. Funciona somente no Teams (use este aplicativo de exemplo para experimentar o processo de atualização descrito neste tutorial). | [Exibir](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Lista de tarefas pendentes (Microsoft 365) | Lista de tarefas pendentes editáveis com SSO criado com React e Azure Functions. Funciona em Teams, Outlook, Office. | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Editor de Imagens (Microsoft 365) | Criar, editar, abrir e salvar imagens usando o Microsoft API do Graph. Funciona em Teams, Outlook, Office. | [View](https://github.com/OfficeDev/m365-extensibility-image-editor) |
