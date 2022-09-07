---
title: Editar manifesto do Azure Active Directory no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Descreve o gerenciamento de aplicativos do Azure Active Directory no Kit de Ferramentas do Teams
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 2091649581686b376d2486a874118d36fd6a984b
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616650"
---
# <a name="edit-azure-ad-manifest"></a>Editar Azure AD manifesto

O [manifesto do Azure Active Directory (Azure AD)](/azure/active-directory/develop/reference-app-manifest) contém definições de todos os atributos de um objeto Azure AD aplicativo no plataforma de identidade da Microsoft.

O Kit de Ferramentas do Teams agora gerencia Azure AD aplicativo com o arquivo de manifesto como a fonte da verdade durante o ciclo de vida de desenvolvimento de aplicativos do Teams.

Esta seção cobre:

* [Personalizar Azure AD de manifesto](#customize-azure-ad-manifest-template)
* [Azure AD espaços reservados do modelo de manifesto](#azure-ad-manifest-template-placeholders)
* [Criar e visualizar Azure AD manifesto com lente de código](#author-and-preview-azure-ad-manifest-with-code-lens)
* [Implantar Azure AD do aplicativo para o ambiente local](#deploy-azure-ad-application-changes-for-local-environment)
* [Implantar Azure AD de aplicativo para o ambiente remoto](#deploy-azure-ad-application-changes-for-remote-environment)
* [Exibir Azure AD aplicativo no portal do Azure](#view-azure-ad-application-on-the-azure-portal)
* [Usar um aplicativo Azure AD existente](#use-an-existing-azure-ad-application)
* [Azure AD aplicativo no ciclo de vida de desenvolvimento de aplicativos do Teams](#azure-ad-application-in-teams-application-development-lifecycle)

## <a name="customize-azure-ad-manifest-template"></a>Personalizar Azure AD de manifesto

Você pode personalizar Azure AD de manifesto para atualizar Azure AD aplicativo.

1. Abra `aad.template.json` em seu projeto.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add template.png" alt-text="template":::

2. Atualize o modelo diretamente ou [faça referência a valores de outro arquivo](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#Placeholders-in-AAD-manifest-template). Você pode ver vários cenários de personalização aqui:
  
   * [Adicionar uma permissão de aplicativo](#add-an-application-permission)
   * [Pré-autorizar um aplicativo cliente](#preauthorize-a-client-application)
   * [Atualizar a URL de redirecionamento para resposta de autenticação](#update-redirect-url-for-authentication-response)

3. [Implante Azure AD de aplicativo para o ambiente local](#deploy-azure-ad-application-changes-for-local-environment).
  
4. [Implante Azure AD do aplicativo para o ambiente remoto](#deploy-azure-ad-application-changes-for-remote-environment).

### <a name="add-an-application-permission"></a>Adicionar uma permissão de aplicativo

Se o aplicativo Teams exigir mais permissões para chamar a API com permissões adicionais, `requiredResourceAccess` você precisará atualizar a propriedade no modelo Azure AD manifesto. Você pode ver o exemplo a seguir para esta propriedade:

```JSON

   "requiredResourceAccess": [
    {
        "resourceAppId": "Microsoft Graph",
        "resourceAccess": [
            {
                "id": "User.Read", // For Microsoft Graph API, you can also use uuid for permission id
                "type": "Scope" // Scope is for delegated permission
            },
            {
                "id": "User.Export.All",
                "type": "Role" // Role is for application permission
            }
        ]
    },
    {
        "resourceAppId": "Office 365 SharePoint Online",
        "resourceAccess": [
            {
                "id": "AllSites.Read",
                "type": "Scope"
            }
        ]
    }
]
```

* `resourceAppId` é usada para APIs diferentes. Para `Microsoft Graph` e `Office 365` `SharePoint Online`, insira o nome diretamente em vez de UUID e, para outras APIs, use UUID.

* `resourceAccess.id` é usada para permissões diferentes. Para `Microsoft Graph` e `Office 365 SharePoint Online`, insira o nome da permissão diretamente em vez de UUID e, para outras APIs, use UUID.

* `resourceAccess.type` é usada para permissão delegada ou permissão de aplicativo. `Scope` significa permissão delegada e significa `Role` permissão de aplicativo.

### <a name="preauthorize-a-client-application"></a>Pré-autorizar um aplicativo cliente

Você pode usar a `preAuthorizedApplications` propriedade para autorizar um aplicativo cliente a indicar que a API confia no aplicativo. Os usuários não consentem quando o cliente chama a API exposta. Você pode ver o exemplo a seguir para esta propriedade:

```JSON

    "preAuthorizedApplications": [
        {
            "appId": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
            "permissionIds": [
                "{{state.fx-resource-aad-app-for-teams.oauth2PermissionScopeId}}"
            ]
        }
        ...
    ]
```

`preAuthorizedApplications.appId` é usada para o aplicativo que você deseja autorizar. Se você não souber a ID do aplicativo e souber apenas o nome do aplicativo, use as seguintes etapas para pesquisar a ID do aplicativo:

1. Vá para [portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) e abra **Registros de Aplicativo**.

1. Selecione **Todos os aplicativos** e pesquise o nome do aplicativo.

1. Selecione o nome do aplicativo e obtenha a ID do aplicativo na página de visão geral.

### <a name="update-redirect-url-for-authentication-response"></a>Atualizar a URL de redirecionamento para resposta de autenticação

  As URLs de redirecionamento são usadas ao retornar respostas de autenticação, como tokens após a autenticação bem-sucedida. Você pode personalizar URLs de redirecionamento usando a propriedade `replyUrlsWithType`. Por exemplo, para adicionar como `https://www.examples.com/auth-end.html` URL de redirecionamento, você pode adicioná-la como o exemplo a seguir:

``` JSON
"replyUrlsWithType": [
    ...
    {
        "url": "https://www.examples.com/auth-end.html",
        "type": "Spa"
    }
]
```

## <a name="azure-ad-manifest-template-placeholders"></a>Azure AD espaços reservados do modelo de manifesto

O Azure AD de manifesto contém argumentos de espaço reservado com {{...}} instruções que são substituídas durante a compilação para ambientes diferentes. Você pode criar referências a variáveis de arquivo de configuração, arquivo de estado e ambiente com os argumentos de espaço reservado.

### <a name="reference-state-file-values-in-azure-ad-manifest-template"></a>Valores de arquivo de estado de referência Azure AD modelo de manifesto

O arquivo de estado está localizado em `.fx\states\state.xxx.json` (xxx representa um ambiente diferente). O exemplo a seguir mostra o arquivo de estado típico:

``` JSON
{
    "solution": {
        "teamsAppTenantId": "uuid",
        ...
    },
    "fx-resource-aad-app-for-teams": {
        "applicationIdUris": "api://xxx.com/uuid",
        ...
    }
    ...
}
```

Você pode usar esse argumento de espaço reservado no Azure AD: `{{state.fx-resource-aad-app-for-teams.applicationIdUris}}` para apontar o `applicationIdUris` valor na `fx-resource-aad-app-for-teams` propriedade.

### <a name="reference-config-file-values-in-azure-ad-manifest-template"></a>Referenciar valores de arquivo de configuração Azure AD modelo de manifesto

O arquivo de configuração está localizado em `.fx\configs\config.xxx.json` (xxx representa um ambiente diferente). O exemplo a seguir mostra o arquivo de configuração:

``` JSON
{
  "$schema": "https://aka.ms/teamsfx-env-config-schema",
  "description": "description.",
  "manifest": {
    "appName": {
      "short": "app",
      "full": "Full name for app"
    }
  }
}
```

Você pode usar o argumento de espaço reservado no Azure AD: `{{config.manifest.appName.short}}` para referenciar o `short` valor.

### <a name="reference-environment-variable-in-azure-ad-manifest-template"></a>Variável de ambiente de referência Azure AD modelo de manifesto

Às vezes, você não deseja codificar os valores no modelo Azure AD manifesto. Por exemplo, quando o valor é um segredo. Azure AD arquivo de modelo de manifesto dá suporte a valores de variáveis de ambiente de referência. Você pode usar a sintaxe em `{{env.YOUR_ENV_VARIABLE_NAME}}` valores de parâmetro para informar as ferramentas para resolver a variável de ambiente atual do valor.

## <a name="author-and-preview-azure-ad-manifest-with-code-lens"></a>Criar e visualizar Azure AD manifesto com lente de código

Azure AD arquivo de modelo de manifesto tem lentes de código para revisar e editar.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/preview view.png" alt-text="visualização":::

### <a name="azure-ad-manifest-template-file"></a>Azure AD arquivo de modelo de manifesto

Há uma lente de código de visualização no início do arquivo de modelo Azure AD manifesto. Selecione a lente de código para gerar um Azure AD com base no ambiente selecionado.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add codelens.png" alt-text="addcodelens":::

### <a name="placeholder-argument-code-lens"></a>Lente de código de argumento de espaço reservado

A lente de código do argumento de espaço reservado ajuda você a examinar rapidamente os valores para depuração local e desenvolver o ambiente. Se o mouse passar o mouse sobre o argumento de espaço reservado, ele mostrará a caixa de dica de ferramenta para os valores de todo o ambiente.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add arguments.png" alt-text="addarguments":::

### <a name="required-resource-access-code-lens"></a>Lente de código de acesso de recurso necessária

É diferente do esquema de [manifesto Azure AD](/azure/active-directory/develop/reference-app-manifest) `resourceAppId` `resourceAccess` que e a ID `requiredResourceAccess` na propriedade só dão suporte a UUID. Azure AD de manifesto no Kit de Ferramentas do Teams também dá suporte a cadeias de caracteres e permissões que podem ser lidas `Microsoft Graph` `Office 365 SharePoint Online` pelo usuário. Se você inserir UUID, a lente de código mostrará cadeias de caracteres legível pelo usuário; caso contrário, ela mostrará UUID.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add resource.png" alt-text="Addresource":::

### <a name="pre-authorized-applications-code-lens"></a>Lente de código de aplicativos pré-autorizados

A lente de código mostra o nome do aplicativo para a ID do aplicativo pré-autorizado para a `preAuthorizedApplications` propriedade.

## <a name="deploy-azure-ad-application-changes-for-local-environment"></a>Implantar Azure AD do aplicativo para o ambiente local

1. Selecione a `Preview` lente de código em `aad.template.json`.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy1.png" alt-text="deploy1":::

2. Selecione **o ambiente local** .
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy2.png" alt-text="deploy2":::

3. Selecione a `Deploy Azure AD Manifest` lente de código em `aad.local.json`.

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy3.png" alt-text="deploy3":::

4. As alterações para Azure AD aplicativo usado no ambiente local são implantadas.
  
## <a name="deploy-azure-ad-application-changes-for-remote-environment"></a>Implantar Azure AD de aplicativo para o ambiente remoto

1. Abra a paleta de comandos e selecione: `Teams: Deploy Azure Active Directory application manifest`.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy4.png" alt-text="deploy4":::

2. Você também pode clicar com o botão direito do mouse no `aad.template.json` menu de contexto e `Deploy Azure Active Directory application manifest` selecionar.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy5.png" alt-text="deploy5":::

## <a name="view-azure-ad-application-on-the-azure-portal"></a>Exibir Azure AD aplicativo no portal do Azure

1. Copie a Azure AD ID do cliente do aplicativo do `state.xxx.json` arquivo () na `fx-resource-aad-app-for-teams` propriedade.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view1.png" alt-text="view1":::

   > [!NOTE]
   > xxx na ID do cliente indica o nome do ambiente em que você implantou o Azure AD aplicativo

2. Acesse [portal do Azure e](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) entre na conta do Microsoft 365.
  
   > [!NOTE]
   > Verifique se as credenciais de logon do aplicativo Teams e da conta M365 são as mesmas.

3. Abra [a página Registros de Aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), pesquise o aplicativo Azure AD usando a ID do cliente que você copiou antes.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view2.png" alt-text="Mododeexibição2":::

4. Selecione Azure AD aplicativo no resultado da pesquisa para exibir as informações detalhadas.
  
5. Na Azure AD informações do aplicativo, selecione o `Manifest` menu para exibir o manifesto deste aplicativo. O esquema do manifesto é o mesmo do arquivo `aad.template.json` . Para obter mais informações sobre o manifesto, consulte o [manifesto do aplicativo do Azure Active Directory](/azure/active-directory/develop/reference-app-manifest).
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view3.png" alt-text="view3":::

6. Você pode selecionar **Outro Menu** para exibir ou configurar Azure AD aplicativo por meio do portal.
  
## <a name="use-an-existing-azure-ad-application"></a>Usar um aplicativo Azure AD existente

Você pode usar o aplicativo Azure AD existente para o projeto do Teams. Para obter mais informações, consulte Usar um aplicativo Azure AD [existente para](https://github.com/OfficeDev/TeamsFx/wiki/Customize-provision-behaviors#use-an-existing-aad-app-for-your-teams-app) seu aplicativo teams.

## <a name="azure-ad-application-in-teams-application-development-lifecycle"></a>Azure AD aplicativo no ciclo de vida de desenvolvimento de aplicativos do Teams

Você precisa interagir com o aplicativo Azure AD durante vários estágios do ciclo de vida de desenvolvimento de aplicativos do Teams.

1. **Para criar o Project**

      Você pode criar um projeto com o Kit de Ferramentas do Teams que vem com suporte a SSO por padrão, como `SSO-enabled tab`. Para obter mais informações sobre como criar um novo aplicativo, consulte [criar um novo aplicativo do Teams usando o Kit de Ferramentas do Teams](create-new-project.md). Um Azure AD de manifesto é criado automaticamente para você em `templates\appPackage\aad.template.json`. O Kit de Ferramentas do Teams cria ou atualiza o aplicativo Azure AD durante o desenvolvimento local ou enquanto você move o aplicativo para a nuvem.

2. **Para adicionar o SSO ao bot ou à guia**

      Depois de criar um aplicativo do Teams sem SSO interno, o Kit de Ferramentas do Teams ajuda você a adicionar o SSO ao projeto de forma incremental. Como resultado, um Azure AD de manifesto é criado automaticamente para você em `templates\appPackage\aad.template.json`.

      O Kit de Ferramentas do Teams cria ou atualiza o aplicativo Azure AD durante a próxima sessão de depuração local ou enquanto você move o aplicativo para a nuvem.

3. **Para compilar localmente**

    O Kit de Ferramentas do Teams executa as seguintes funções durante o desenvolvimento local ou é conhecido como F5:

    * Leia o `state.local.json` arquivo para localizar um aplicativo Azure AD existente. Se um Azure AD já existir, o Kit de Ferramentas do Teams reutilizará o aplicativo Azure AD existente. Caso contrário, você precisará criar um novo aplicativo usando o `aad.template.json` arquivo.

    * Inicialmente ignora algumas propriedades no arquivo de manifesto que exigem mais contexto (como a propriedade replyUrls que requer um ponto de extremidade de depuração local) durante a criação de um novo aplicativo Azure AD com o arquivo de manifesto.

    * Após a inicialização do ambiente de desenvolvimento local com êxito, os identifierUris do aplicativo Azure AD, replyUrls e outras propriedades que não estão disponíveis durante o estágio de criação são atualizados adequadamente.

    * As alterações feitas em seu aplicativo Azure AD serão carregadas durante a próxima sessão de depuração local. Você pode ver as [Azure AD do aplicativo para](https://github.com/OfficeDev/TeamsFx/wiki/) aplicar as alterações manualmente Azure AD do aplicativo.

4. **Para provisionar recursos de nuvem**

      Você precisa provisionar recursos de nuvem e implantar seu aplicativo ao mover seu aplicativo para a nuvem. Nos estágios, como o desenvolvimento local, o Kit de Ferramentas do Teams:

      * Leia o `state.{env}.json` arquivo para localizar um aplicativo Azure AD existente. Se um Azure AD já existir, o Kit de Ferramentas do Teams reutilize o aplicativo Azure AD existente. Caso contrário, você precisará criar um novo aplicativo usando o `aad.template.json` arquivo.

      * Inicialmente ignora algumas propriedades no arquivo de manifesto que exigem mais contexto (como a propriedade replyUrls requer front-end ou ponto de extremidade do bot) durante a criação de um novo aplicativo Azure AD com o arquivo de manifesto.

      * Depois que o provisionamento de outros recursos for concluído, Azure AD identifierUris e replyUrls do aplicativo serão atualizados de acordo com os pontos de extremidade corretos.

5. **Para criar aplicativo**

    * Implantar no comando de nuvem implanta seu aplicativo nos recursos provisionados. Ele não inclui a implantação de Azure AD de aplicativo que você fez.

    * Você pode ver, Implantar [alterações Azure AD aplicativo para](#deploy-azure-ad-application-changes-for-remote-environment) o ambiente remoto para implantar Azure AD de aplicativo para o ambiente remoto.

    * O Kit de Ferramentas do Teams atualiza Azure AD aplicativo de acordo com o arquivo Azure AD modelo de manifesto.

## <a name="limitations"></a>Limitações

1. A extensão do Kit de Ferramentas do Teams não dá suporte a todas as propriedades listadas Azure AD esquema de manifesto.
  
      A tabela a seguir lista as propriedades que não têm suporte na extensão do Kit de Ferramentas do Teams:

      |**Propriedades sem suporte**|**Motivo**|
      |-----------|----------|
      |passwordCredentials|Não permitido no manifesto|
      |createdDateTime|Somente leitura e não é possível alterar|
      |logoUrl|Somente leitura e não é possível alterar|
      |publisherDomain|Somente leitura e não é possível alterar|
      |oauth2RequirePostResponse|Não existe no API do Graph|
      |oauth2AllowUrlPathMatching|Não existe no API do Graph|
      |samlMetadataUrl|Não existe no API do Graph|
      |orgRestrictions|Não existe no API do Graph|
      |certificação|Não existe no API do Graph|

2. Atualmente, a propriedade `requiredResourceAccess` pode usar o nome do aplicativo de recurso legível pelo usuário ou cadeias de caracteres de nome de permissão somente para `Microsoft Graph` `Office 365 SharePoint Online` APIs. Para outras APIs, você precisa usar o UUID. Você pode seguir estas etapas para recuperar IDs de portal do Azure:

    * Registre um novo Azure AD aplicativo no [portal do Azure](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
    * Selecione `API permissions` na página Azure AD aplicativo.
    * Selecione `add a permission` para adicionar a permissão desejada.
    * Selecione `Manifest`, na `requiredResourceAccess` propriedade, você pode encontrar as IDs de API e permissões.

## <a name="see-also"></a>Confira também

* [Visualizar e personalizar o manifesto do aplicativo no Kit de Ferramentas](TeamsFx-preview-and-customize-app-manifest.md)
