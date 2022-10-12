---
title: Estender um aplicativo de guia pessoal do Teams Microsoft 365
description: Saiba como atualizar seu aplicativo de guia pessoal para ser executado no Outlook e no Office, além do Microsoft Teams.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 99b95d72e75bf43381ea441cf2e94f9cf63edc7e
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537588"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Estender uma guia pessoal do Teams Microsoft 365

As guias pessoais fornecem uma ótima maneira de aprimorar a experiência do Microsoft Teams. Usando guias pessoais, você pode fornecer a um usuário acesso ao aplicativo diretamente no Teams, sem que o usuário precise sair da experiência ou entrar novamente. Com essa versão prévia, as guias pessoais podem se acender em outros Microsoft 365 aplicativos. Este tutorial demonstra o processo de pegar uma guia pessoal existente do Teams e atualizá-la para ser executada nas experiências da Web e da área de trabalho do Outlook e do Office, bem como no aplicativo do Office para Android.

Atualizar seu aplicativo pessoal para execução no Outlook e no Office envolve estas etapas:

> [!div class="checklist"]
>
> * Atualize seu manifesto do aplicativo.
> * Atualize as referências do SDK do TeamsJS.
> * Altere os cabeçalhos da Política de Segurança de Conteúdo.
> * Atualize o Microsoft Azure Active Directory (Azure AD) do aplicativo para SSO (logon único).
> * Realize sideload do aplicativo atualizado no Teams.

O restante deste guia orienta você por essas etapas e mostra como visualizar sua guia pessoal em outros aplicativos do Microsoft 365.

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

Se você tiver um aplicativo de guia pessoal existente, faça uma cópia ou uma ramificação do projeto de produção para testar e atualizar a ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção, para teste).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de configuração no [](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) Exemplo de Lista de Tarefas para criar um aplicativo de guia pessoal usando a extensão kit de ferramentas do Teams para Visual Studio Code e, em seguida, retorne a este artigo para atualizá-lo para o Microsoft 365.

Como alternativa, você pode usar um aplicativo Hello *World* de logon único básico já habilitado para o Microsoft 365 na seção início [](#quickstart) rápido a seguir e, em seguida, pular para [Sideload do aplicativo no Teams](#sideload-your-app-in-teams).

### <a name="quickstart"></a>Início rápido

Para começar com uma [guia pessoal](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) que já está habilitada para execução no Outlook e no Office, use a extensão kit de ferramentas do Teams para Visual Studio Code.

1. No Visual Studio Code, abra a paleta de comandos (`Ctrl+Shift+P`), digite `Teams: Create a new Teams app`.
1. Selecione **a guia pessoal habilitada para SSO**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Amostra de Lista de tarefas (Funciona no Teams, Outlook e Office) no Kit de Ferramentas do Teams":::

1. Selecione um local no computador local para a pasta do workspace.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) `Teams: Provision in the cloud` e digite para criar os recursos de aplicativo necessários (Serviço de Aplicativo plano, conta de armazenamento, Aplicativo de Funções, Identidade Gerenciada) em sua conta do Azure.
1. Abra a paleta de comandos (`Ctrl+Shift+P`) e digite `Teams: Deploy to the cloud` para implantar o código de exemplo nos recursos provisionados no Azure e iniciar o aplicativo.

A partir daqui, você pode pular para [Sideload do](#sideload-your-app-in-teams) aplicativo no Teams e visualizar seu aplicativo no Outlook e no Office. (O manifesto do aplicativo e as chamadas à API do TeamsJS já foram atualizados para o Microsoft 365.)

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar a versão do esquema de manifesto do desenvolvedor do [Teams](../resources/schema/manifest-schema.md) `1.13` para permitir que sua guia pessoal do Teams seja executada no Outlook e no Office.

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

Se você usou o kit de ferramentas do Teams para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos (`Ctrl+Shift+P`) e **localize o Teams: Validar arquivo de manifesto**.

## <a name="update-sdk-references"></a>Atualizar referências do SDK

Para ser executado no Outlook e no Office, seu aplicativo precisará fazer referência ao pacote npm `@microsoft/teams-js@2.0.0` (ou superior). Embora o código com versões de nível inferior seja compatível com o Outlook e o Office, os avisos de substituição são registrados e o suporte para versões de nível inferior do TeamsJS no Outlook e no Office acabará por parar.

Você pode usar o Kit de Ferramentas do Teams para ajudar a identificar e automatizar as alterações de código necessárias para atualizar das versões do TeamsJS 1.x para o TeamsJS versão 2.x.x. Como alternativa, você pode executar as mesmas etapas manualmente; consulte o [SDK do cliente JavaScript do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para obter detalhes.

1. Abra a *paleta comando*: `Ctrl+Shift+P`.
1. Execute o comando `Teams: Upgrade Teams JS SDK and code references`.

Após a conclusão, *o arquivo package.json* fará referência `@microsoft/teams-js@2.0.0` (ou superior) `*.js/.ts` `*.jsx/.tsx` e seus arquivos serão atualizados com:

> [!div class="checklist"]
>
> * Instruções de importação para teams-js@2.x.x
> * [Chamadas de função, enumeração e interface](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) para teams-js@2.x.x
> * `TODO` lembretes de comentário sinalizando áreas que podem ser afetadas por alterações [de interface de](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface) contexto
> * `TODO` lembretes de comentário para [converter funções de retorno de chamada em promessas](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> O código *dentro.html* arquivos não é compatível com as ferramentas de atualização e exige alterações manuais.

## <a name="configure-content-security-policy-headers"></a>Configurar cabeçalhos de Política de Segurança de Conteúdo

Assim como no Microsoft Teams, os aplicativos de tabulação são hospedados em [elementos iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) em clientes Web do Office e do Outlook.

Se seu aplicativo usa cabeçalhos [CSP (Política](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) de Segurança de Conteúdo), [certifique-se](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) de permitir todos os seguintes ancestrais de quadro em seus cabeçalhos CSP:

|Microsoft 365 host| permissão de ancestral de quadro|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Atualizar o registro de aplicativo do Azure AD para SSO

[O SSO (logon único) do Azure Active Directory (AD)](../tabs/how-to/authentication/tab-sso-overview.md) para guias pessoais funciona da mesma maneira no Office e no Outlook do Teams. No entanto, você precisará adicionar vários identificadores de aplicativo cliente ao registro Azure AD aplicativo de Azure AD do aplicativo guia *no portal de* Registros de aplicativo locatário.

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
    > Alguns aplicativos cliente do Microsoft 365 compartilham IDs de cliente.

## <a name="sideload-your-app-in-teams"></a>Faça o sideload do seu aplicativo do Teams

A etapa final para executar seu aplicativo no Office e no Outlook é fazer sideload do pacote de aplicativos [de guia pessoal](..//concepts/build-and-test/apps-package.md) atualizado no Microsoft Teams.

1. Empacote o aplicativo Teams ([ícones de manifesto e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip.[](../resources/schema/manifest-schema.md) Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, pode fazer isso facilmente usando a opção de pacote de metadados **Zip Teams** no menu **Implantação** do Kit de Ferramentas do Teams.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Pacote de metadados do Zip Teams' na extensão do Kit de Ferramentas do Teams para Visual Studio Code":::

1. Entre no Teams com sua conta de locatário da área restrita e alterne para o modo de *Visualização do Desenvolvedor*. Selecione o menu de reticências (**...**) em seu perfil de usuário e selecione: **sobre** > **Visualização do desenvolvedor**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="No menu de reticências do Teams, abra 'Sobre' e selecione a opção 'Visualização do Desenvolvedor'":::

1. Selecione **Aplicativos** para abrir o painel **Gerenciar seus aplicativos**. Selecione **Publicar um aplicativo**.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Abra o painel 'Gerenciar seus aplicativos' e selecione 'Publicar um aplicativo'":::

1. Escolha **Carregar uma opção de aplicativo** personalizado e selecione o pacote do aplicativo.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Opção 'Carregar um aplicativo personalizado' no Teams":::

Depois de ser recarregada para o Teams, sua guia pessoal estará disponível no Outlook e no Office. Você deve entrar com as mesmas credenciais usadas para realizar o sideload do aplicativo no Teams. Ao executar o aplicativo do Office para Android, você precisa reiniciar o aplicativo para usar seu aplicativo de guia pessoal do aplicativo do Office.

Você pode fixar o aplicativo para acesso rápido ou encontrar seu aplicativo nas reticências (**...**) entre aplicativos recentes na barra lateral à esquerda. Fixar um aplicativo no Teams não o fixa como um aplicativo no Office ou no Outlook.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Visualizar sua guia pessoal em outras Microsoft 365 experiências

Veja como visualizar seu aplicativo em execução no Office e no Outlook, na Web e em clientes da área de trabalho do Windows.

> [!NOTE]
> Desinstalar seu aplicativo do Teams também o remove dos catálogos **Mais** Aplicativos no Outlook e no Office. Se você estiver usando o aplicativo de exemplo do Kit de Ferramentas do Teams fornecido acima.

### <a name="outlook-on-windows"></a>Outlook no Windows

Para exibir seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook e entre usando sua conta de locatário de desenvolvimento.
1. Na barra lateral, selecione  **Mais Aplicativos**. O título do aplicativo com sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no Outlook.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Outlook para ver suas guias pessoais instaladas":::

### <a name="outlook-on-the-web"></a>Outlook na Web

Para exibir seu aplicativo no Outlook na Web:

1. Acesse o [Outlook na Web](https://outlook.office.com) e entre usando sua conta de locatário de desenvolvimento.
1. Na barra lateral, selecione  **Mais Aplicativos**. O título do aplicativo com sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar e visualizar seu aplicativo em execução Outlook na Web.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do outlook.com para ver as guias pessoais instaladas":::

### <a name="office-on-windows"></a>Office no Windows

Para exibir seu aplicativo em execução no Office na área de trabalho do Windows:

1. Inicie o Office e entre usando sua conta de locatário de desenvolvimento.
1. Selecione o **ícone Aplicativos** na barra lateral. O título do aplicativo com sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no Office.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Office para ver suas guias pessoais instaladas":::

### <a name="office-on-the-web"></a>Office na Web

Para visualizar seu aplicativo em execução no Office na Web:

1. Faça logon **office.com** com credenciais de locatário de teste.
1. Selecione o **ícone Aplicativos** na barra lateral. O título do aplicativo com sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo Office na Web.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Clique na opção 'Mais aplicativos' na barra lateral do office.com para ver as guias pessoais instaladas":::

### <a name="office-app-for-android"></a>Aplicativo do Office para Android

> [!NOTE]
> Antes de instalar o aplicativo, execute [as etapas para instalar o build beta do aplicativo do Office](prerequisites.md#mobile) mais recente e fazer parte do programa beta.

Para exibir seu aplicativo em execução no aplicativo do Office para Android:

1. Inicie o aplicativo do Office e entre usando sua conta de locatário de desenvolvimento. Se o aplicativo do Office para Android já estava em execução antes do sideload do aplicativo no Teams, você precisará reiniciá-lo para vê-lo entre seus aplicativos instalados.
1. Selecione o **ícone Aplicativos** . Seu aplicativo de sideload aparece entre os aplicativos instalados.
1. Selecione o ícone do aplicativo para iniciar seu aplicativo no aplicativo do Office para Android.

:::image type="content" source="images/office-mobile-apps.png" alt-text="Toque na opção 'Aplicativos' na barra lateral do aplicativo do Office para ver suas guias pessoais instaladas":::

## <a name="troubleshooting"></a>Solução de problemas

Atualmente, há suporte para um subconjunto de recursos e tipos de aplicativos do Teams nos clientes do Outlook e do Office. Esse suporte se expande ao longo do tempo.

Consulte o [suporte do Microsoft 365 para](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook) verificar o suporte ao host para vários recursos do TeamsJS.

Para obter um resumo geral do suporte de host e plataforma do Microsoft 365 para aplicativos do Teams, consulte Estender aplicativos [do Teams no Microsoft 365](overview.md).

Você pode verificar o suporte de host de um determinado recurso em runtime `isSupported()` chamando a função nesse recurso (namespace) e ajustando o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo ilumine a interface do usuário e a funcionalidade em hosts que dão suporte a ele e forneça uma experiência de fallback normal em hosts que não dão suporte. Para obter mais informações, consulte [Diferenciar sua experiência de aplicativo](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Use os canais da[Comunidade de desenvolvedores do Microsoft Teams](/microsoftteams/platform/feedback) para relatar problemas e fornecer comentários.

### <a name="debugging"></a>Depuração

No Kit de Ferramentas do Teams, você pode depurar (`F5`) seu aplicativo de guia em execução no Office e no Outlook, além do Teams.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Escolha entre os destinos de depuração do Teams, Outlook e Office no Kit de Ferramentas do Teams":::

Na primeira execução da depuração local no Office ou no Outlook, você será solicitado a entrar em sua conta de locatário do Microsoft 365 e instalar um certificado de teste autoassinado. Você também será solicitado a instalar manualmente o Teams. Selecione **Instalar no Teams** para abrir uma janela do navegador e instalar manualmente seu aplicativo. Em seguida **, selecione** Continuar para continuar a depurar seu aplicativo no Office/Outlook.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Instalação da caixa de diálogo kit de ferramentas do Teams":::

Forneça comentários e relate quaisquer problemas com a experiência de depuração do Kit de Ferramentas do Teams no [Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx/issues).

#### <a name="mobile-debugging"></a>Depuração móvel

A depuração do Kit de Ferramentas do Teams (`F5`) ainda não tem suporte com o aplicativo do Office para Android. Veja como depurar remotamente seu aplicativo em execução no aplicativo do Office para Android:

1. Se você depurar usando um dispositivo Android físico, conecte-o ao computador de desenvolvimento e habilite a opção de [depuração USB](https://developer.android.com/studio/debug/dev-options). Isso é habilitado por padrão com o emulador do Android.
1. Inicie o aplicativo do Office em seu dispositivo Android.
1. Abra seu perfil **Me > Configurações > Permitir depuração** e alterne a opção para Habilitar **depuração remota**.

    :::image type="content" source="images/office-android-enable-remote-debugging.png" alt-text="Captura de tela mostrando Habilitar depuração remota":::

1. **Configurações de Saída**.
1. Saia da tela do perfil.
1. Selecione **Aplicativos** e inicie seu aplicativo de sideload para ser executado no aplicativo do Office.
1. Verifique se o dispositivo Android está conectado ao computador de desenvolvimento. No computador de desenvolvimento, abra o navegador na página de inspeção do DevTools. Por exemplo, vá para o `edge://inspect/#devices` Microsoft Edge para exibir uma lista de WebViews do Android habilitados para depuração.
1. Localize a `Microsoft Teams Tab` URL com a guia e selecione **Inspecionar** para iniciar a depuração do aplicativo com o DevTools.

    :::image type="content" source="images/office-android-debug.png" alt-text="captura de tela mostrando a lista de webviews no devtool":::

1. Depure seu aplicativo guia no Android WebView. Da mesma forma que você [depura remotamente](/microsoft-edge/devtools-guide-chromium/remote-debugging) um site normal em um dispositivo Android.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
| Lista de Tarefas Pendentes | Lista de tarefas pendentes editáveis com SSO criado com React e Azure Functions. Funciona somente no Teams (use este aplicativo de exemplo para experimentar o processo de atualização descrito neste tutorial). | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Lista De Tarefas Pendentes (Microsoft 365) | Lista de tarefas pendentes editáveis com SSO criado com React e Azure Functions. Funciona no Teams, Outlook, Office. | [Exibir](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Editor de Imagens (Microsoft 365) | Criar, editar, abrir e salvar imagens usando o Microsoft API do Graph. Funciona no Teams, Outlook, Office. | [View](https://github.com/OfficeDev/m365-extensibility-image-editor) |
| Página de inicialização de exemplo (Microsoft 365) | Demonstra a autenticação de SSO e os recursos do SDK do TeamsJS como disponíveis em hosts diferentes. Funciona no Teams, Outlook, Office. | [View](https://github.com/OfficeDev/microsoft-teams-library-js/tree/main/apps/sample-app) |
| Aplicativo Pedidos northwind | Demonstra como usar o Microsoft TeamsJS SDK V2 para estender o aplicativo teams para outros aplicativos host M365. Funciona no Teams, Outlook, Office. Otimizado para dispositivos móveis.| [View](https://github.com/microsoft/app-camp/tree/main/experimental/ExtendTeamsforM365) |

## <a name="next-step"></a>Próxima etapa

Publique seu aplicativo para ser detectável no Teams, no Outlook e no Office:

> [!div class="nextstepaction"]
> [Publicar aplicativos do Teams para Outlook e Office](publish.md)
