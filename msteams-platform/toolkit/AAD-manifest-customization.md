---
title: Gerenciar Azure Active Directory aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Descreve o gerenciamento Azure Active Directory aplicativo no Teams Toolkit
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 4067b86bc3a8de0ed891e84ceef68f5f95741479
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65655098"
---
# <a name="azure-ad-manifest"></a>Azure AD manifesto

O [Azure Active Directory (Azure AD)](/azure/active-directory/develop/reference-app-manifest) contém definições de todos os atributos de um objeto Azure AD aplicativo no plataforma de identidade da Microsoft.

Teams Toolkit agora gerencia um Azure AD com o arquivo de manifesto como a origem da verdade durante os ciclos de vida de Teams de desenvolvimento de aplicativos.

## <a name="customize-azure-ad-manifest-template"></a>Personalizar Azure AD de manifesto

Você pode personalizar Azure AD de manifesto para atualizar Azure AD aplicativo.

1. Abra `aad.template.json` em seu projeto.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add template.png" alt-text="template":::

2. Atualize o modelo diretamente ou [faça referência a valores de outro arquivo](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#Placeholders-in-AAD-manifest-template). Você pode ver vários cenários de personalização aqui:
  
* [Adicionar uma permissão de aplicativo](#customize-requiredresourceaccess)
* [Pré-autorizar um aplicativo cliente](#customize-preauthorizedapplications)
* [Atualizar a URL de redirecionamento para resposta de autenticação](#customize-redirect-urls)

3. [Implante Azure AD de aplicativo para o ambiente local](#deploy-azure-ad-application-changes-for-local-environment).
  
4. [Implante Azure AD do aplicativo para o ambiente remoto](#deploy-azure-ad-application-changes-for-remote-environment).

### <a name="customize-requiredresourceaccess"></a>Personalizar requiredResourceAccess

Se o Teams requer mais permissões para chamar a API com permissões adicionais, `requiredResourceAccess` você precisará atualizar a propriedade no modelo Azure AD manifesto. Você pode ver o exemplo a seguir para esta propriedade:

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

* `resourceAppId` é para APIs diferentes, para e `Microsoft Graph` `Office 365` `SharePoint Online`, insira o nome diretamente em vez de UUID e, para outras APIs, use UUID.

* `resourceAccess.id` é para permissões diferentes, para e `Microsoft Graph` `Office 365 SharePoint Online`, insira o nome da permissão diretamente em vez de UUID e, para outras APIs, use UUID.

* `resourceAccess.type` é usada para permissão delegada ou permissão de aplicativo. `Scope` significa permissão delegada e significa `Role` permissão de aplicativo.

### <a name="customize-preauthorizedapplications"></a>Personalizar preAuthorizedApplications

Você pode usar a `preAuthorizedApplications` propriedade para autorizar um aplicativo cliente a indicar que a API confia no aplicativo e os usuários não consentem quando o cliente o chama de API exposta. Você pode ver o exemplo a seguir para esta propriedade:

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

`preAuthorizedApplications.appId` é usada para o aplicativo que você deseja autorizar. Se você não souber a ID do aplicativo, mas souber apenas o nome do aplicativo, poderá ir para o portal do Azure e seguir as etapas para pesquisar o aplicativo para localizar a ID:

1. Vá para [portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) e abra os registros de aplicativo.

1. Selecione **Todos os aplicativos** e pesquise o nome do aplicativo.

1. Selecione o nome do aplicativo e obtenha a ID do aplicativo na página de visão geral.

### <a name="customize-redirect-urls"></a>Personalizar URLs de redirecionamento

  As URLs de redirecionamento são usadas ao retornar respostas de autenticação, como tokens após a autenticação bem-sucedida. Você pode personalizar URLs `replyUrlsWithType`de redirecionamento usando a propriedade, por exemplo, `https://www.examples.com/auth-end.html` para adicionar como URL de redirecionamento, você pode adicioná-la como o exemplo a seguir:

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

Você pode usar esse argumento de espaço reservado no Azure AD: para `{{state.fx-resource-aad-app-for-teams.applicationIdUris}}` referenciar `applicationIdUris` o valor na `fx-resource-aad-app-for-teams` propriedade.

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

No início do arquivo de modelo Azure AD manifesto, há uma lente de código de visualização. Selecione a lente de código, ela Azure AD manifesto com base no ambiente selecionado.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add codelens.png" alt-text="addcodelens":::

### <a name="placeholder-argument-code-lens"></a>Lente de código de argumento de espaço reservado

A lente de código do argumento de espaço reservado ajuda você a examinar rapidamente os valores para depuração local e desenvolver o ambiente. Se o mouse passar o mouse sobre o argumento de espaço reservado, ele mostrará a caixa de dica de ferramenta para os valores de todo o ambiente.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add arguments.png" alt-text="addarguments":::

### <a name="required-resource-access-code-lens"></a>Lente de código de acesso de recurso necessária

Ele é diferente do esquema de [](/azure/active-directory/develop/reference-app-manifest) manifesto Azure AD oficial que e a ID `requiredResourceAccess` na propriedade só dá suporte a UUID, modelo de manifesto Azure AD no Teams Toolkit também dá suporte a cadeias de caracteres e permissões que podem ser lidas `Microsoft Graph` `Office 365 SharePoint Online` pelo usuário.`resourceAppId` `resourceAccess` Se você inserir UUID, a lente de código mostrará cadeias de caracteres legível pelo usuário; caso contrário, ela mostrará UUID.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add resource.png" alt-text="Addresource":::

### <a name="pre-authorized-applications-code-lens"></a>Lente de código de aplicativos pré-autorizados

A lente de código mostra o nome do aplicativo para a ID do aplicativo por autorizado para a `preAuthorizedApplications` propriedade.

## <a name="deploy-azure-ad-application-changes-for-local-environment"></a>Implantar Azure AD do aplicativo para o ambiente local

1. Selecione a `Preview` lente de código em `aad.template.json`.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy1.png" alt-text="deploy1":::

2. Selecione o `local` ambiente.
  
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

1. Copie a Azure AD ID `state.xxx.json` do cliente do aplicativo (xxx é o nome do ambiente que você implantou o Azure AD aplicativo) na `fx-resource-aad-app-for-teams` propriedade.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view1.png" alt-text="view1":::

2. Vá para [portal do Azure](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) e faça logon na Microsoft 365 conta.
  
> [!NOTE]
> Verifique se as credenciais de logon Teams aplicativo e conta M365 são iguais.

3. Abra [a página de registros de aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), pesquise o aplicativo Azure AD usando a ID do cliente que você copiou antes.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view2.png" alt-text="Mododeexibição2":::

4. Selecione Azure AD aplicativo no resultado da pesquisa para exibir as informações detalhadas.
  
5. Na Azure AD informações do aplicativo, selecione `Manifest` o menu para exibir o manifesto deste aplicativo. O esquema do manifesto é o mesmo do arquivo `aad.template.json` . Para obter mais informações sobre o manifesto, [consulte Azure Active Directory manifesto do aplicativo](/azure/active-directory/develop/reference-app-manifest).
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view3.png" alt-text="view3":::

6. Você pode selecionar **Outro Menu** para exibir ou configurar Azure AD aplicativo por meio do portal.
  
## <a name="use-an-existing-azure-ad-application"></a>Usar um aplicativo Azure AD existente

Você pode usar o aplicativo Azure AD existente para o projeto Teams, para obter mais informações, consulte Usar um aplicativo Azure AD existente para seu Teams [aplicativo](https://github.com/OfficeDev/TeamsFx/wiki/Customize-provision-behaviors#use-an-existing-aad-app-for-your-teams-app).

## <a name="azure-ad-application-in-teams-application-development-lifecycle"></a>Azure AD aplicativo no ciclo de vida Teams desenvolvimento de aplicativos

Você precisa interagir com o Azure AD durante vários estágios do ciclo de vida Teams desenvolvimento de aplicativos.

1. **Para criar Project**

      Você pode criar um projeto com Teams Toolkit que vem com suporte a SSO por padrão, como `SSO-enabled tab`. Para obter mais informações para criar um novo aplicativo, consulte [criar Teams aplicativo usando Teams Toolkit](create-new-project.md). Um Azure AD de manifesto é criado automaticamente para você: `templates\appPackage\aad.template.json`. Teams Toolkit cria ou atualiza o aplicativo Azure AD durante o desenvolvimento local ou enquanto você move o aplicativo para a nuvem.

2. **Para adicionar o SSO ao bot ou à guia**

      Depois de criar um Teams sem SSO interno, o Teams Toolkit ajuda a adicionar o SSO ao projeto de forma incremental. Como resultado, um Azure AD de manifesto é criado automaticamente para você: `templates\appPackage\aad.template.json`.

      Teams Toolkit criar ou atualizar o aplicativo Azure AD durante a próxima sessão de depuração local ou enquanto você move o aplicativo para a nuvem.

3. **Para compilar localmente**

    Teams Toolkit executa as seguintes funções durante o desenvolvimento local (conhecido como F5):

    * Leia o `state.local.json` arquivo para localizar um aplicativo Azure AD existente. Se um Azure AD já existir, Teams Toolkit reutilize o aplicativo Azure AD existente, caso contrário, você precisará criar um novo aplicativo usando o `aad.template.json` arquivo

    * Inicialmente ignora algumas propriedades no arquivo de manifesto que exigem contexto adicional (como a propriedade replyUrls que requer um ponto de extremidade de depuração local) durante a criação de um novo aplicativo Azure AD com o arquivo de manifesto.

    * Após a inicialização do ambiente de desenvolvimento local com êxito, os identifierUris do aplicativo Azure AD, replyUrls e outras propriedades que não estão disponíveis durante o estágio de criação são atualizados adequadamente

    * As alterações feitas em seu aplicativo Azure AD serão carregadas durante a próxima sessão de depuração local. Você pode ver as [Azure AD do aplicativo para](https://github.com/OfficeDev/TeamsFx/wiki/) aplicar as alterações manualmente Azure AD do aplicativo

4. **Para provisionar recursos de nuvem**

      Você precisa provisionar recursos de nuvem e implantar seu aplicativo ao mover seu aplicativo para a nuvem. Nos estágios, como o desenvolvimento local, Teams Toolkit será:

      * Leia o `state.{env}.json` arquivo para localizar um aplicativo Azure AD existente. Se um Azure AD já existir, Teams Toolkit reutilize o aplicativo Azure AD existente, caso contrário, você precisará criar um novo aplicativo usando o `aad.template.json` arquivo

      * Inicialmente ignora algumas propriedades no arquivo de manifesto que exigem contexto adicional (como a propriedade replyUrls requer front-end ou ponto de extremidade do bot) durante a criação de um novo aplicativo Azure AD com o arquivo de manifesto

      * Depois que o provisionamento de outros recursos for concluído, Azure AD identifierUris e replyUrls do aplicativo serão atualizados de acordo com os pontos de extremidade corretos

5. **Para criar aplicativo**

    * Implantar no comando de nuvem implanta seu aplicativo nos recursos provisionados. Ele não inclui a implantação de Azure AD de aplicativo que você fez

    * Você pode ver, Implantar [alterações Azure AD aplicativo para](#deploy-azure-ad-application-changes-for-remote-environment) o ambiente remoto para implantar Azure AD de aplicativo para o ambiente remoto

    * Teams Toolkit atualiza o aplicativo Azure AD de acordo com o arquivo de modelo Azure AD manifesto

## <a name="limitations"></a>Limitações

1. Teams Toolkit extensão não dá suporte a todas as propriedades listadas no esquema Azure AD manifesto.
  
      A tabela a seguir lista as propriedades que não têm suporte Teams Toolkit extensão:

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

    * Registrar um novo Azure AD aplicativo no [portal do Azure](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps)
    * Selecione `API permissions` na página Azure AD aplicativo
    * Selecione `add a permission` para adicionar a permissão desejada
    * Selecione `Manifest`, na `requiredResourceAccess` propriedade, você pode encontrar as IDs de API e permissões

## <a name="see-also"></a>Confira também

* [Personalizar o manifesto do aplicativo no Kit de Ferramentas](TeamsFx-manifest-customization.md)
* [Visualizar manifesto do aplicativo no Kit de Ferramentas](TeamsFx-manifest-preview.md)
