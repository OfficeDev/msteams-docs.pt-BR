---
title: Estender um aplicativo de guia pessoal do Teams Microsoft 365
description: Estender um aplicativo de guia pessoal do Teams Microsoft 365
ms.date: 02/11/2022
ms.topic: tutorial
ms.custom: Microsoft 365 apps
ms.localizationpriority: high
ms.openlocfilehash: 873a6fa6207d122581e18cef0ae922ffca87762f
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111518"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Estender uma guia pessoal do Teams Microsoft 365

> [!NOTE]
> *Extendindo uma guia pessoal do Teams em Microsoft 365* está disponível atualmente apenas em [Visualização do desenvolvedor público](../resources/dev-preview/developer-preview-intro.md). Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

As guias pessoais fornecem uma ótima maneira de aprimorar a experiência do Microsoft Teams. Usando guias pessoais, você pode fornecer a um usuário acesso ao aplicativo diretamente no Teams, sem que o usuário precise sair da experiência ou entrar novamente. Com essa versão prévia, as guias pessoais podem se acender em outros Microsoft 365 aplicativos. Este tutorial demonstra o processo de pegar uma guia pessoal existente do Teams e atualizá-la para ser executada em experiências da área de trabalho e da Web do Outlook e também do Office na Web (office.com).

Atualizar seu aplicativo pessoal para ser executado no Outlook e no Office Home envolve estas etapas:

> [!div class="checklist"]
>
> * Atualizar o manifesto do aplicativo
> * Atualizar suas referências do SDK do TeamsJS
> * Corrigir os cabeçalhos da Política de Segurança de Conteúdo
> * Atualize seu Microsoft Azure Active Directory (Azure AD) registro de aplicativo para SSO (logon único)

Testar seu aplicativo exigirá as seguintes etapas:

> [!div class="checklist"]
>
> * Registre seu locatário Microsoft 365 no *Versões direcionadas do Office 365*
> * Configurar sua conta para acessar as versões prévias dos aplicativos do Outlook e do Office
> * Realizar sideload do aplicativo atualizado no Teams

Após essas etapas, seu aplicativo deverá aparecer nas versões prévias do Outlook e dos aplicativos do Office.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de:

* Um locatário Microsoft 365 área restrita do Programa para Desenvolvedores
* Seu locatário de área restrita registrado em *Versões direcionadas do Office 365*
* Um computador com aplicativos do Office instalados do *Canal beta* do Microsoft 365 Apps
* (Opcional) [Kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para o Microsoft Visual Studio Code para ajudar a atualizar seu código

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Preparar sua guia pessoal para a atualização

Se você tiver um aplicativo de guia pessoal existente, faça uma cópia ou uma ramificação do projeto de produção para testar e atualizar a ID do aplicativo no manifesto do aplicativo para usar um novo identificador (diferente da ID do aplicativo de produção).

Se você quiser usar o código de exemplo para concluir este tutorial, siga as etapas de configuração em [Introdução ao exemplo de lista de tarefas](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) para criar um aplicativo de guia pessoal usando a extensão kit de ferramentas do Teams para Visual Studio Code. Ou você pode começar com o mesmo exemplo de [Lista de tarefas atualizada para a visualização de TeamsJS SDK v2](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend-M365) e prosseguir para [Visualização sua guia pessoal em outras experiências do Microsoft 365](#preview-your-personal-tab-in-other-microsoft-365-experiences). O exemplo atualizado também está disponível na extensão Kit de ferramentas do Teams: *Desenvolvimento* > *Ver amostras* > **Lista de tarefas (funciona no Teams, Outlook e Office)**.

:::image type="content" source="images/toolkit-todo-sample.png" alt-text="Amostra de Lista de tarefas (Funciona no Teams, Outlook e Office) no Kit de Ferramentas do Teams":::

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

Você precisará usar o esquema [Manifesto de visualização do desenvolvedor do Teams](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) e o manifesto `Microsoft 365 DevPreview` para permitir que sua guia pessoal do Teams seja executada no Office e no Outlook.

Você pode usar o Kit de Ferramentas do Teams para atualizar o manifesto do aplicativo ou aplicar as alterações manualmente:

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta de Comando*: `Ctrl+Shift+P`
1. Execute o `Teams: Upgrade Teams manifest to support Outlook and Office apps` e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas em vigor.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o manifesto do aplicativo Teams e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Se você usou o Teams Toolkit para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos `Ctrl+Shift+P` e localize **Teams: Validar arquivo de manifesto** ou selecione a opção no menu Implantação do Kit de Ferramentas do Teams (procure o ícone do Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Kit de ferramentas do Teams 'Validar arquivo de manifesto' no menu 'Implantação'":::

## <a name="update-sdk-references"></a>Atualizar referências do SDK

Para ser executado no Outlook e no Office, seu aplicativo precisará depender do pacote npm `@microsoft/teams-js@2.0.0-beta.1` (ou de uma versão *beta* posterior). Embora o código com versões de nível inferior do `@microsoft/teams-js` seja compatível com o Outlook e o Office, os avisos de reprovação serão registrados e o suporte para versões de nível inferior do `@microsoft/teams-js` no Outlook e no Office acabará.

Você pode usar o Kit de Ferramentas do Teams para ajudar a automatizar algumas das alterações de código para adotar a próxima versão do `@microsoft/teams-js` mas se você quiser executar as etapas manualmente, consulte [Visualização do SDK do cliente JavaScript do Microsoft Teams](using-teams-client-sdk-preview.md) para obter detalhes.

1. Abra a *paleta de Comando*: `Ctrl+Shift+P`
1. Execute o comando `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Após a conclusão, o utilitário terá atualizado o arquivo `package.json` com a dependência da Visualização do TeamsJS SDK (`@microsoft/teams-js@2.0.0-beta.1` ou posterior), e seus arquivos `*.js/.ts` e `*.jsx/.tsx` serão atualizados com:

> [!div class="checklist"]
>
> * `package.json` à Visualização do SDK do TeamsJS
> * Instruções de importação para Visualização do SDK do TeamsJS
> * [Função, enumeração e chamadas de interface](using-teams-client-sdk-preview.md#apis-organized-into-capabilities) para a Visualização do SDK do TeamsJS
> * `TODO` comentar lembretes para revisar áreas que podem ser afetadas por alterações de interface [Contexto](using-teams-client-sdk-preview.md#updates-to-the-context-interface)
> * `TODO` lembretes de comentário para garantir que [a conversão para funções de promessas de funções de estilo de retorno de chamada](using-teams-client-sdk-preview.md#callbacks-converted-to-promises) tenha ido bem em todos os sites de chamadas que a ferramenta encontrou

> [!IMPORTANT]
> O código *.html* não tem suporte nas ferramentas de atualização e exigirá alterações manuais.

> [!NOTE]
> Se você quiser atualizar manualmente seu código, consulte [Visualização do SDK do cliente JavaScript do Microsoft Teams](using-teams-client-sdk-preview.md) para saber mais sobre as alterações necessárias.

## <a name="configure-content-security-policy-headers"></a>Configurar cabeçalhos de Política de Segurança de Conteúdo

[Assim como no Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs), os aplicativos de guia são hospedados em ([elementos iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)) nos clientes Web do Office e Outlook.

Se seu aplicativo usa cabeçalhos de [Política de segurança de conteúdo](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) (CSP), verifique se você está permitindo todos os seguintes [ancestrais de quadro](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) em seus cabeçalhos de CSP:

|Microsoft 365 host| permissão de ancestral de quadro|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Atualizar o registro de aplicativo do Azure AD para SSO

Azure Active Directory o SSO (logon único) para guias pessoais funciona da mesma maneira no Office e no Outlook [como no Teams](/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso), no entanto, você precisará adicionar vários identificadores de aplicativo cliente ao registro de aplicativo do Azure AD de seu aplicativo de guia no portal *Registros de aplicativo* do locatário.

1. Entre no [portal do Microsoft Azure](https://portal.azure.com) com sua conta de locatário da área restrita.
1. Abra a folha **Registros de aplicativo**.
1. Selecione o nome do aplicativo de guia pessoal para abrir o registro do aplicativo.
1. Selecionar **Expor uma API** (em *Gerenciar*).

:::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorizar IDs do cliente da folha *Registros de aplicativo* no portal do Azure":::

Na seção **Aplicativos do cliente autorizados**, verifique se todos os valores a seguir `Client Id` foram adicionados:

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

A etapa final é realizar o sideload da guia pessoal atualizada ([pacote de aplicativos](/microsoftteams/platform/concepts/build-and-test/apps-package)) no Microsoft Teams. Depois de concluído, seu aplicativo estará disponível para execução no Office e no Outlook, além do Teams.

1. Empacote seu aplicativo do Teams ([ícones de manifesto e aplicativo](/microsoftteams/platform/resources/schema/manifest-schema#icons)) em um arquivo zip. Se você usou o Kit de Ferramentas do Teams para criar seu aplicativo, pode fazer isso facilmente usando a opção de **pacote de metadados Zip Teams** no menu *Implantação* do Kit de Ferramentas do Teams ou na paleta de comandos `Ctrl+Shift+P` do Visual Studio Code:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Zip Teams metadata package' na extensão do Kit de Ferramentas do Teams para Visual Studio Code":::

1. Faça logon no Teams com sua conta de locatário da área restrita e verifique se você está na Visualização pública do desenvolvedor. Você pode verificar se está na Visualização no cliente do Teams clicando nas reticências (**...**) pelo seu perfil de usuário e abrindo **Sobre** para verificar se a opção *Visualização do Desenvolvedor* está ativada.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Do menu de reticências do Teams, abra 'Sobre' e verifique se a opção 'Visualização do Desenvolvedor' está marcada":::

1. Abra o painel *Aplicativos*, e clique em **Carregue um aplicativo personalizado** e, em seguida, **Carregue para mim ou minhas equipes**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="'Carregar um aplicativo personalizado' no painel 'Aplicativos' do Teams":::

1. Selecione o pacote do aplicativo e clique em *Open*.

Após o sideload por meio do Teams, sua guia pessoal estará disponível no Outlook e no Office. Certifique-se de entrar com as mesmas credenciais usadas para fazer o sideload do aplicativo no Teams.

Você pode fixar o aplicativo para acesso rápido ou encontrar seu aplicativo nas reticências (**...**) entre aplicativos recentes na barra lateral à esquerda.

> [!NOTE]
> Fixar um aplicativo no Teams não o fixará como um aplicativo no Office.com ou no Outlook.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Visualizar sua guia pessoal em outras Microsoft 365 experiências

Quando você atualiza sua guia pessoal do Teams e a faz sideload no Teams, ela é executada no Outlook no Windows, na Web, no Office no Windows e na Web (office.com). Veja como visualizar essas experiências de Microsoft 365.

### <a name="outlook-on-windows"></a>Outlook no Windows

Para exibir seu aplicativo em execução no Outlook na área de trabalho do Windows:

1. Inicie o Outlook e entre usando sua conta de locatário de desenvolvimento.
1. Clique nas reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Clique no ícone do aplicativo para iniciar seu aplicativo no Outlook.

:::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Outlook para ver suas guias pessoais instaladas":::

### <a name="outlook-on-the-web"></a>Outlook na Web

Para exibir seu aplicativo no Outlook na Web:

1. Navegue até [Outlook na Web](https://outlook.office.com) e entre usando sua conta de locatário de desenvolvimento.
1. Clique nas reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Clique no ícone do aplicativo para iniciar e visualizar seu aplicativo em execução no Outlook na Web.

:::image type="content" source="images/outlook-web-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do outlook.com para ver as guias pessoais instaladas":::

### <a name="office-on-windows"></a>Office no Windows

Para exibir seu aplicativo em execução no Office na área de trabalho do Windows:

1. Inicie o Office e entre usando sua conta de locatário de desenvolvimento.
1. Clique nas reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Clique no ícone do aplicativo para iniciar seu aplicativo no Office.

:::image type="content" source="images/office-desktop-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do cliente da área de trabalho do Office para ver suas guias pessoais instaladas":::

### <a name="office-on-the-web"></a>Office na Web

Para visualizar seu aplicativo em execução no Office na Web:

1. Faça logon office.com credenciais de locatário de teste.
1. Clique nas reticências (**...**) na barra lateral. O título do aplicativo com sideload aparecerá entre os aplicativos instalados.
1. Clique no ícone do aplicativo para iniciar seu aplicativo no Office na Web.

:::image type="content" source="images/office-web-more-apps.png" alt-text="Clique na opção de reticências ('Mais aplicativos') na barra lateral do office.com para ver as guias pessoais instaladas":::

## <a name="next-steps"></a>Próximas etapas

As guias pessoais habilitadas para Outlook e Office estão em versão prévia e não têm suporte para uso em produção. Veja como distribuir seu aplicativo de guia pessoal para visualizar audiências para fins de teste.

### <a name="single-tenant-distribution"></a>Distribuição de locatário único

As guias pessoais habilitadas para Outlook e Office podem ser distribuídas para um público-alvo de visualização em um locatário de teste (ou produção) de uma das três maneiras:

#### <a name="teams-client"></a>Cliente do Teams

No menu *Aplicativos*, selecione *Gerenciar seus aplicativos* > **Enviar um aplicativo para sua organização**. Isso requer a aprovação do seu administrador de TI.

#### <a name="microsoft-teams-admin-center"></a>Centro de Administração do Microsoft Teams

Como administrador do Teams, você pode carregar e pré-instalar o pacote de aplicativos para o locatário da sua organização a partir de [administrador de Teams](https://admin.teams.microsoft.com/). Consulte [Carregue seus aplicativos personalizados no centro de administração do Microsoft Teams](/MicrosoftTeams/upload-custom-apps) para obter detalhes.

#### <a name="microsoft-admin-center"></a>Centro de Administração da Microsoft

Como administrador global, você pode carregar e pré-instalar o pacote do aplicativo do [administrador de Microsoft](https://admin.microsoft.com/). Consulte [Testar e implantar aplicativos do Microsoft 365 por parceiros no portal de aplicativos integrados](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) para obter detalhes.

### <a name="multitenant-distribution"></a>Distribuição multilocatário

A distribuição Microsoft AppSource não tem suporte durante essa visualização inicial do desenvolvedor das guias pessoais do Outlook e do Office.
