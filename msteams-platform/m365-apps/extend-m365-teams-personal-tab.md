---
title: Estender um aplicativo de guia pessoal do Teams Microsoft 365
description: Saiba como atualizar seu aplicativo de guia pessoal para ser executado no Outlook e no Office, além do Microsoft Teams.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 2e16b27b0854e9dc4f92e1c7ce4dc35c2af1f5c4
ms.sourcegitcommit: 6926cf5eee55d5047c11ca13afc7f6f23e270396
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68739922"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Estender uma guia pessoal do Teams Microsoft 365

As guias pessoais fornecem uma ótima maneira de aprimorar a experiência do Microsoft Teams. Usando guias pessoais, você pode fornecer a um usuário acesso ao aplicativo diretamente no Teams, sem que o usuário precise sair da experiência ou entrar novamente. Com essa versão prévia, as guias pessoais podem se acender em outros Microsoft 365 aplicativos. Este tutorial demonstra o processo de usar uma guia pessoal do Teams existente e atualizá-la para ser executada nas experiências da área de trabalho e da Web do Outlook e do Office, bem como no aplicativo do Office para Android.

Atualizar seu aplicativo pessoal para ser executado no Outlook e no Office envolve estas etapas:

> [!div class="checklist"]
>
> * Atualize seu manifesto do aplicativo.
> * Atualize suas referências de SDK do TeamsJS.
> * Altere os cabeçalhos da Política de Segurança de Conteúdo.
> * Atualize seu registro de aplicativo Microsoft Azure Active Directory (Azure AD) para SSO (Logon Único).
> * Realize sideload do aplicativo atualizado no Teams.

O restante deste guia orienta você nestas etapas e mostra como visualizar sua guia pessoal em outros aplicativos do Microsoft 365.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de:

* Um locatário Microsoft 365 área restrita do Programa para Desenvolvedores
* Seu locatário de área restrita registrado em *Versões direcionadas do Office 365*
* Um computador com aplicativos do Office instalados do *Canal beta* do Microsoft 365 Apps
* (Opcional) Um dispositivo Android ou emulador com o aplicativo do Office para Android instalado e registrado no *programa beta*
* (Opcional) [Kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para o Microsoft Visual Studio Code para ajudar a atualizar seu código

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Preparar sua guia pessoal para a atualização

Se você tiver um aplicativo de guia pessoal existente, faça uma cópia ou um branch do projeto de produção para testar e atualizar sua ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do Aplicativo de produção, para teste).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de configuração no [Exemplo de Lista Todo](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) para criar um aplicativo de guia pessoal usando a extensão do Teams Toolkit para Visual Studio Code e, em seguida, retorne a este artigo para atualizá-lo para o Microsoft 365.

Como alternativa, você pode usar um aplicativo básico de logon único *hello world* já habilitado microsoft 365 na seção [início rápido](#quickstart) a seguir e, em seguida, pular para [Sideload seu aplicativo no Teams](#sideload-your-app-in-teams) .

### <a name="quickstart"></a>Início rápido

Para começar com uma [guia pessoal](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) que já está habilitada para ser executada no Outlook e no Office, use a extensão do Teams Toolkit para Visual Studio Code.

1. No Visual Studio Code, abra a paleta de comandos (`Ctrl+Shift+P`), digite `Teams: Create a new Teams app`.
1. Selecione **guia pessoal habilitada para SSO**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Amostra de Lista de tarefas (Funciona no Teams, Outlook e Office) no Kit de Ferramentas do Teams":::

1. Selecione um local no computador local para a pasta do workspace.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Provision in the cloud` para criar os recursos de aplicativo necessários (plano Serviço de Aplicativo, conta de armazenamento, Aplicativo de Funções, Identidade Gerenciada) em sua conta do Azure.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Deploy to the cloud` para implantar o código de exemplo nos recursos provisionados no Azure e iniciar o aplicativo.

A partir daqui, você pode ignorar para [Sideload seu aplicativo no Teams](#sideload-your-app-in-teams) e visualizar seu aplicativo no Outlook e no Office. (O manifesto do aplicativo e as chamadas da API do TeamsJS já foram atualizados para o Microsoft 365.)

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar a versão `1.13` do esquema de [manifesto do desenvolvedor do Teams](../resources/schema/manifest-schema.md) para habilitar sua guia pessoal do Teams a ser executada no Outlook e no Office.

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

Se você usou o kit de ferramentas do Teams para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos (`Ctrl+Shift+P`) e localize **o Teams: validar o arquivo de manifesto**.

## <a name="update-sdk-references"></a>Atualizar referências do SDK

Para ser executado no Outlook e no Office, seu aplicativo precisará fazer referência ao pacote `@microsoft/teams-js@2.0.0` npm (ou superior). Embora o código com versões de nível inferior tenha suporte no Outlook e no Office, os avisos de depreciação são registrados e o suporte para versões de nível inferior do TeamsJS no Outlook e no Office acabará por cessar.

Você pode usar o Teams Toolkit para ajudar a identificar e automatizar as alterações de código necessárias para atualizar de versões do TeamsJS 1.x para o TeamsJS versão 2.x.x. Como alternativa, você pode executar as mesmas etapas manualmente; Consulte o [SDK do cliente JavaScript do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para obter detalhes.

1. Abra a *paleta de comandos*: `Ctrl+Shift+P`.
1. Execute o comando `Teams: Upgrade Teams JS SDK and code references`.

Após a conclusão, o arquivo *package.json* fará referência `@microsoft/teams-js@2.0.0` (ou superior) e seus `*.js/.ts` arquivos e `*.jsx/.tsx` serão atualizados com:

> [!div class="checklist"]
>
> * Importar instruções para teams-js@2.x.x
> * [Chamadas de função, Enum e Interface](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para teams-js@2.x.x
> * `TODO`lembretes de comentário sinalizando áreas que podem ser afetadas por alterações de interface [de contexto](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface)
> * `TODO` lembretes de comentário para [converter funções de retorno de chamada em promessas](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> O código dentro *.html* arquivos não tem suporte pelas ferramentas de atualização e exige alterações manuais.

## <a name="configure-content-security-policy-headers"></a>Configurar cabeçalhos de Política de Segurança de Conteúdo

Assim como no Microsoft Teams, os aplicativos de guia são hospedados dentro [de elementos iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) em clientes Web do Office e do Outlook.

Se o aplicativo usar cabeçalhos CSP ( [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) ), certifique-se de permitir todos os [seguintes ancestrais de quadro](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) em seus cabeçalhos CSP:

|Microsoft 365 host| permissão de ancestral de quadro|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.microsoft365.com`, `*.office.com` |
| Outlook | `outlook.live.com`, `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Atualizar o registro de aplicativo do Azure AD para SSO

[O SSO (logon único) do Azure Active Directory (AD)](../tabs/how-to/authentication/tab-sso-overview.md) para guias pessoais funciona da mesma maneira no Office e no Outlook do que no Teams. No entanto, você precisará adicionar vários identificadores de aplicativo cliente ao registro de aplicativo Azure AD do aplicativo de guia no portal *de Registros de aplicativo* do locatário.

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
    |Office Web  |4765445b-32c6-49b0-83e6-1d93765276ca|
    |Office para a área de trabalho  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
    |Office mobile  | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Área de trabalho do Outlook, móvel | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook Web | bc59ab01-8403-45c6-8796-ac3ef710b3e3|

    > [!NOTE]
    > Alguns aplicativos cliente do Microsoft 365 compartilham IDs do cliente.

## <a name="sideload-your-app-in-teams"></a>Faça o sideload do seu aplicativo do Teams

A etapa final para executar seu aplicativo no Office e no Outlook é carregar o [pacote de aplicativos](..//concepts/build-and-test/apps-package.md) de guia pessoal atualizado no Microsoft Teams.

1. Empacotar seu aplicativo teams ([ícones de manifesto](../resources/schema/manifest-schema.md) e [aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, pode fazer isso facilmente usando a opção de pacote de metadados **Zip Teams** no menu **Implantação** do Kit de Ferramentas do Teams.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Pacote de metadados do Zip Teams' na extensão do Kit de Ferramentas do Teams para Visual Studio Code":::

1. Entre no Teams com sua conta de locatário da área restrita e alterne para o modo de *Visualização do Desenvolvedor*. Selecione o menu de reticências (**...**) em seu perfil de usuário e selecione: **sobre** > **Visualização do desenvolvedor**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No menu de reticências do Teams, abra 'Sobre' e selecione a opção 'Visualização do Desenvolvedor'":::

1. Selecione **Aplicativos** para abrir o painel **Gerenciar seus aplicativos**. Selecione **Publicar um aplicativo**.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Abra o painel 'Gerenciar seus aplicativos' e selecione 'Publicar um aplicativo'":::

1. Escolha **Carregar uma opção de aplicativo personalizado** e selecione seu pacote de aplicativos.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Opção 'Carregar um aplicativo personalizado' no Teams":::

Depois de ser sideload para o Teams, sua guia pessoal estará disponível no Outlook e no Office. Você deve entrar com as mesmas credenciais usadas para carregar o aplicativo no Teams. Ao executar o aplicativo do Office para Android, você precisa reiniciar o aplicativo para usar seu aplicativo de guia pessoal do aplicativo do Office.

Você pode fixar o aplicativo para acesso rápido ou encontrar seu aplicativo nas reticências (**...**) entre aplicativos recentes na barra lateral à esquerda. Fixar um aplicativo no Teams não o fixa como um aplicativo no Office ou no Outlook.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Visualizar sua guia pessoal em outras Microsoft 365 experiências

Veja como visualizar seu aplicativo em execução nos clientes office e outlook, Web e Windows desktop.

> [!NOTE]
> Desinstalar seu aplicativo do Teams também o remove dos catálogos **do More Apps** no Outlook e no Office. Se você estiver usando o aplicativo de exemplo do Teams Toolkit fornecido acima.

### <a name="outlook-on-windows"></a>Outlook no Windows

Para exibir seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook e entre usando sua conta de locatário de desenvolvimento.
1. Na barra lateral, selecione  **Mais Aplicativos**. O título do aplicativo sideload é exibido entre seus aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no Outlook.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Outlook para ver suas guias pessoais instaladas":::

### <a name="outlook-on-the-web"></a>Outlook na Web

Para exibir seu aplicativo no Outlook na Web:

1. Vá para [Outlook na Web](https://outlook.office.com) e entre usando sua conta de locatário de desenvolvimento.
1. Na barra lateral, selecione  **Mais Aplicativos**. O título do aplicativo sideload é exibido entre seus aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar e visualizar seu aplicativo em execução em Outlook na Web.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do outlook.com para ver as guias pessoais instaladas":::

### <a name="office-on-windows"></a>Office no Windows

Para exibir seu aplicativo em execução no Office na área de trabalho do Windows:

1. Inicie o Office e entre usando sua conta de locatário de desenvolvimento.
1. Selecione o ícone **Aplicativos** na barra lateral. O título do aplicativo sideload é exibido entre seus aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no Office.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Office para ver suas guias pessoais instaladas":::

### <a name="office-on-the-web"></a>Office na Web

Para visualizar seu aplicativo em execução no Office na Web:

1. Faça logon **em office.com** com credenciais de locatário de teste.
1. Selecione o ícone **Aplicativos** na barra lateral. O título do aplicativo sideload é exibido entre seus aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no Office na Web.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Clique na opção 'Mais aplicativos' na barra lateral do office.com para ver suas guias pessoais instaladas":::

### <a name="office-app-for-android"></a>Aplicativo do Office para Android

> [!NOTE]
> Antes de instalar o aplicativo, execute [as etapas para instalar o build beta do aplicativo do Office mais recente](prerequisites.md#mobile) e fazer parte do programa beta.

Para exibir seu aplicativo em execução no aplicativo do Office para Android:

1. Inicie o aplicativo do Office e entre usando sua conta de locatário de desenvolvimento. Se o aplicativo do Office para Android já estivesse em execução antes de carregar seu aplicativo no Teams, você precisará reiniciá-lo para vê-lo entre seus aplicativos instalados.
1. Selecione o ícone **Aplicativos** . Seu aplicativo sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no aplicativo do Office para Android.

:::image type="content" source="images/office-mobile-apps.png" alt-text="Toque na opção 'Aplicativos' na barra lateral do aplicativo do Office para ver suas guias pessoais instaladas":::

## <a name="troubleshooting"></a>Solução de problemas

Atualmente, há suporte para um subconjunto de tipos e recursos de aplicativos do Teams em clientes do Outlook e do Office. Esse suporte se expande ao longo do tempo.

Consulte o [suporte do Microsoft 365](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook) para verificar o suporte ao host para vários recursos do TeamsJS.

Para obter um resumo geral do suporte de host e plataforma do Microsoft 365 para aplicativos do Teams, consulte [Estender aplicativos do Teams no Microsoft 365](overview.md).

Você pode verificar se há suporte de host de uma determinada funcionalidade no runtime chamando a `isSupported()` função nesse recurso (namespace) e ajustando o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo ilumine a interface do usuário e a funcionalidade em hosts que dão suporte a ele e forneçam uma experiência de fallback graciosa em hosts que não o fazem. Para obter mais informações, confira [Diferenciar sua experiência de aplicativo](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Use os canais da[Comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para relatar problemas e fornecer comentários.

### <a name="debugging"></a>Depuração

No Teams Toolkit, você pode Depurar (`F5`) seu aplicativo de guia em execução no Office e no Outlook, além do Teams.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Escolha entre destinos de depuração do Teams, Outlook e Office no Teams Toolkit":::

Após a primeira execução da depuração local no Office ou no Outlook, você será solicitado a entrar em sua conta de locatário do Microsoft 365 e instalar um certificado de teste autoassinado. Você também será solicitado a instalar manualmente o Teams. Selecione **Instalar no Teams** para abrir uma janela do navegador e instalar manualmente seu aplicativo. Em seguida, selecione **Continuar** para continuar a depurar seu aplicativo no Office/Outlook.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Instalação do Teams na caixa de diálogo kit de ferramentas":::

Forneça comentários e reporte quaisquer problemas com a experiência de depuração do Teams Toolkit no [Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx/issues).

#### <a name="mobile-debugging"></a>Depuração móvel

A depuração do Teams Toolkit (`F5`) ainda não tem suporte com o aplicativo do Office para Android. Veja como depurar remotamente seu aplicativo em execução no aplicativo do Office para Android:

1. Se você depurar usando um dispositivo Android físico, conecte-o ao computador de desenvolvimento e habilite a opção de [depuração USB](https://developer.android.com/studio/debug/dev-options). Isso é habilitado por padrão com o emulador android.
1. Inicie o aplicativo do Office do seu dispositivo Android.
1. Abra seu perfil **Me > Configurações > Permitir depuração** e alterne na opção **Habilitar depuração remota**.

    :::image type="content" source="images/office-android-enable-remote-debugging.png" alt-text="Captura de tela mostrando Habilitar depuração remota":::

1. **Configurações de saída**.
1. Saia da tela do perfil.
1. Selecione **Aplicativos** e inicie seu aplicativo sideload para ser executado no aplicativo do Office.
1. Verifique se o dispositivo Android está conectado ao computador de desenvolvimento. No computador de desenvolvimento, abra o navegador até a página de inspeção DevTools. Por exemplo, acesse no Microsoft Edge para exibir uma lista de WebViews android habilitados para `edge://inspect/#devices` depuração.
1. Localize a `Microsoft Teams Tab` URL com sua guia e selecione **inspecionar** para começar a depurar seu aplicativo com DevTools.

    :::image type="content" source="images/office-android-debug.png" alt-text="captura de tela mostrando a lista de visões da Web no devtool":::

1. Depure seu aplicativo de guia no Android WebView. Da mesma forma, você [depura remotamente](/microsoft-edge/devtools-guide-chromium/remote-debugging) um site regular em um dispositivo Android.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
| Lista Todo | Lista de todos editáveis com SSO criado com React e Azure Functions. Funciona apenas no Teams (use este aplicativo de exemplo para tentar o processo de atualização descrito neste tutorial). | [Exibir](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Lista Todo (Microsoft 365) | Lista de todos editáveis com SSO criado com React e Azure Functions. Funciona no Teams, Outlook, Office. | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Editor de Imagens (Microsoft 365) | Criar, editar, abrir e salvar imagens usando o Microsoft API do Graph. Funciona no Teams, Outlook, Office. | [View](https://github.com/OfficeDev/m365-extensibility-image-editor) |
| Página inicial de exemplo (Microsoft 365) | Demonstra a autenticação do SSO e os recursos do SDK do TeamsJS como disponíveis em hosts diferentes. Funciona no Teams, Outlook, Office. | [View](https://github.com/OfficeDev/microsoft-teams-library-js/tree/main/apps/sample-app) |
| Aplicativo Northwind Orders | Demonstra como usar o SDK V2 do Microsoft TeamsJS para estender o aplicativo teams para outros aplicativos host M365. Funciona no Teams, Outlook, Office. Otimizado para dispositivos móveis.| [Exibir](https://github.com/microsoft/app-camp/tree/main/experimental/ExtendTeamsforM365) |

## <a name="next-step"></a>Próxima etapa

Publique seu aplicativo para ser detectável no Teams, no Outlook e no Office:

> [!div class="nextstepaction"]
> [Publicar aplicativos do Teams para Outlook e Office](publish.md)
