---
title: Registrar seu aplicativo de guia com o Azure AD.
description: Configure o SSO (logon único) com o Azure AD configurando o URI da ID do aplicativo, o escopo do token de acesso e pré-autorizar clientes confiáveis.
ms.topic: how-to
ms.localizationpriority: high
keywords: 'guias de autenticação do Teams escopo de locação de SSO (logon único) de token de acesso do Microsoft Azure Active Directory (Azure AD) '
ms.openlocfilehash: 4cbe07c37a12ef3f2902c2a2760ed07ed99e4af6
ms.sourcegitcommit: 937ea793889fc1efa9ec6a52374d5098be1117e0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67653193"
---
# <a name="register-your-tab-app-in-azure-ad"></a>Registrar o aplicativo de guia no Azure AD

O Azure AD fornece acesso ao seu aplicativo de guia com base na identidade do usuário do aplicativo no Teams. Você precisará registrar seu aplicativo de guia no Azure AD para que o usuário do aplicativo que entrou no Teams possa ter acesso ao seu aplicativo de guia.

## <a name="enabling-sso-on-azure-ad"></a>Como habilitar o SSO no Azure AD

Registrar seu aplicativo de guia no Azure AD e habilitá-lo para SSO requer a criação de configurações de aplicativo, como a geração de ID do aplicativo, a definição do escopo da API e a pré-autorização de IDs do cliente para aplicativos confiáveis.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-azure-ad.png" alt-text="Configurar o Azure AD para enviar o token de acesso ao aplicativo Cliente do Teams":::

Crie um novo registro de aplicativo no Azure AD e exponha sua API (Web) usando escopos (permissões). Configure uma relação de confiança entre a API exposta no Azure AD e seu aplicativo. Ele permite que o Cliente do Teams obtenha um token de acesso em nome do seu aplicativo e do usuário conectado. Você pode adicionar IDs do cliente para os aplicativos móveis, da área de trabalho e da Web confiáveis que você deseja pré-autorizar.

Talvez você também precise configurar detalhes adicionais, como a autenticação de usuários de aplicativos na plataforma ou no dispositivo em que você deseja direcionar seu aplicativo de guia.

Há suporte apenas para API do Graph no nível do usuário, ou seja, email, perfil, offline_access, OpenId. Se você precisa ter acesso a outros escopos do Graph, como `User.Read` ou `Mail.Read`, confira [Obter um token de acesso com permissões do Graph](tab-sso-graph-api.md).

A configuração do Azure AD habilita o SSO para seu aplicativo de guia no Teams. Ele responde com um token de acesso para validar o usuário do aplicativo.

> [!NOTE]
> O Kit de Ferramentas do Microsoft Teams registra o aplicativo Azure AD em um projeto de SSO.

### <a name="before-you-register-with-azure-ad"></a>Antes de se registrar no Azure AD

É bom que você aprenda sobre a configuração para registrar seu aplicativo no Azure AD com antecedência. Verifique se você se preparou para configurar os seguintes detalhes antes de registrar seu aplicativo:

- **Opções de** locatário único ou multilocatário: seu aplicativo será usado apenas no locatário do Microsoft 365 em que ele está registrado ou muitos locatários do Microsoft 365 o usarão? Os aplicativos escritos para uma empresa normalmente são de locatário único. Os aplicativos escritos por um fornecedor de software independente e usados por muitos clientes precisam ser multilocatário para que o locatário de cada cliente possa acessar o aplicativo.
- **URI de ID de aplicativo**: é um URI globalmente exclusivo que identifica a API Web que você expõe para o acesso do seu aplicativo por meio de escopos. Ele também é conhecido como URI de identificador. O URI da ID do aplicativo inclui a ID do aplicativo e o subdomínio em que seu aplicativo está hospedado. O nome de domínio do aplicativo e o nome de domínio que você registra para o aplicativo do Azure AD devem ser os mesmos. Atualmente, não há suporte para vários domínios por aplicativo.
- **Escopo**: é a permissão que um usuário de aplicativo autorizado ou seu aplicativo pode receber para acessar um recurso exposto pela API.

> [!NOTE]
>
> - **Aplicativos LOB**: sua organização pode disponibilizar aplicativos LOB por meio da Microsoft Store. Esses aplicativos são personalizados para sua organização. Eles são internos ou específicos em sua organização ou empresa.
> - **Aplicativos de propriedade do cliente**: o SSO também tem suporte para aplicativos de propriedade do cliente dentro dos locatários do Azure AD B2C.

Para criar e configurar seu aplicativo no Azure AD para habilitar o SSO:

- [Registre e configure o aplicativo Azure AD.](#create-an-app-registration-in-azure-ad)
- [Configure o escopo para o token de acesso.](#configure-scope-for-access-token)
- [Configure a versão do token de acesso.](#configure-access-token-version)

## <a name="create-an-app-registration-in-azure-ad"></a>Crie um registro de aplicativo no Azure AD

Registre um novo aplicativo no Azure AD e configure a locação e a plataforma do aplicativo. Você gerará uma nova ID de aplicativo que será atualizada posteriormente no arquivo de manifesto do aplicativo Teams.

### <a name="to-register-a-new-app-in-azure-ad"></a>Para registrar um novo aplicativo no Azure AD

1. No navegador da Web, vá para o [Portal do Azure](https://ms.portal.azure.com/).
   A página do Portal do Microsoft Azure AD é aberta.

2. Selecione o ícone **Registros de aplicativo**.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal.png" alt-text="Página do Portal do Azure AD.":::

   A página **Registros de aplicativo** é exibida.

3. Selecione o ícone **+ Novo registro**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-registrations.png" alt-text="Página Novo registro no Portal do Azure AD.":::

    A página **Registrar um aplicativo** é exibida.

4. Insira o nome do aplicativo que você deseja exibir para o usuário do aplicativo. Você pode alterar esse nome em um estágio posterior, se desejar.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-app.png" alt-text="Página Registro de aplicativo no Portal do Azure AD.":::

5. Selecione o tipo de conta de usuário que pode acessar seu aplicativo. Você pode escolher entre opções de locatário único ou multilocatário ou uma conta Microsoft privada.

    <details>
    <summary><b>Opções para tipos de conta com suporte</b></summary>

    | Opção | Selecione essa opção para... |
    | --- | --- |
    | Contas somente nesse diretório organizacional (Apenas Microsoft - Locatário único) | Crie um aplicativo para uso somente por usuários (ou convidados) em seu locatário. <br> Geralmente chamado de aplicativo LOB, ele é um aplicativo de locatário único na plataforma de identidade da Microsoft. |
    | Contas em qualquer diretório organizacional (qualquer diretório do Azure AD - Multilocatário) | Permite que os usuários em qualquer locatário do Azure AD usem seu aplicativo. Essa opção é apropriada se, por exemplo, você estiver criando um aplicativo SaaS e pretende dispo-lo para várias organizações. <br> Esse tipo de aplicativo é conhecido como aplicativo multilocatário na plataforma de identidade da Microsoft.|
    | Contas em qualquer diretório organizacional (qualquer diretório do Azure AD – multilocatário) e contas pessoais da Microsoft | Destina-se ao conjunto mais amplo de clientes. <br> Ao selecionar essa opção, você está registrando um aplicativo multilocatário que pode dar suporte a usuários de aplicativos que também têm contas pessoais da Microsoft. |
    | Contas pessoais da Microsoft | Crie um aplicativo somente para usuários que têm contas pessoais da Microsoft. |

    </details>

    > [!NOTE]
    > Você não precisa inserir o **URI de Redirecionamento** para habilitar o SSO para um aplicativo de guia.

7. Selecione **Registrar**.
    Uma mensagem é exibida no navegador informando que o aplicativo foi criado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-created-msg.png" alt-text="Registre o aplicativo no Portal do Azure AD.":::

    A página com a ID do aplicativo e outras configurações é exibida.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tab-app-created.png" alt-text="O registro de aplicativo foi bem-sucedido.":::

8. Anote e salve a ID do aplicativo da **ID do Aplicativo (cliente).** Você precisará dele para atualizar o manifesto do aplicativo Teams mais tarde.

    Seu aplicativo está registrado no Azure AD. Agora você deve ter a ID do aplicativo para seu aplicativo de guia.

## <a name="configure-scope-for-access-token"></a>Configurar o escopo para o token de acesso

Depois de criar um novo registro de aplicativo, configure as opções de escopo (permissão) para enviar o token de acesso ao Cliente do Teams e autorizar aplicativos cliente confiáveis para habilitar o SSO.

Para configurar o escopo e autorizar aplicativos cliente confiáveis, você precisará:

- [Para expor uma API](#to-expose-an-api): configurar opções de escopo (permissão) para seu aplicativo. Você exporá uma API Web e configurará o URI da ID do aplicativo.
- [Para configurar o escopo da API](#to-configure-api-scope): defina o escopo para a API e os usuários que podem consentir um escopo. Você pode permitir que somente administradores forneçam consentimento para permissões com privilégios mais altos.
- [Para configurar o aplicativo cliente autorizado](#to-configure-authorized-client-application): crie IDs do cliente autorizadas para aplicativos que você deseja pré-autorizar. Isso permite que o usuário do aplicativo acesse os escopos do aplicativo (permissões) que você configurou, sem a necessidade de qualquer consentimento adicional. Autorize previamente somente os aplicativos cliente em que você confia, pois os usuários do aplicativo não terão a oportunidade de recusar o consentimento.

### <a name="to-expose-an-api"></a>Para expor uma API

1. Selecione **Gerenciar** > **Expor uma API** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Opção de menu Expor uma API.":::

    A página **Expor uma API** é exibida.

1. Selecione **Definir** para gerar o URI de ID do Aplicativo no formato de `api://{AppID}`.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="Definir o URI da ID do aplicativo":::

    A seção para definir o URI da ID do aplicativo é exibida.

1. Insira o URI da ID do aplicativo no formato explicado aqui.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="URI da ID do Aplicativo":::

    - O **URI da ID do aplicativo** está preenchido previamente com a ID do aplicativo (GUID) no formato `api://{AppID}`.
    - O formato do URI da ID do aplicativo deve ser: `api://fully-qualified-domain-name.com/{AppID}`.
    - Insira `fully-qualified-domain-name.com` entre `api://` e `{AppID}` (ou seja, a GUID). Por exemplo, api://example.com/{AppID}.

    Em que:
    - `fully-qualified-domain-name.com` é o nome de domínio legível por humanos a partir do qual o aplicativo de guia é atendido. O nome de domínio do aplicativo e o nome de domínio que você registra para o aplicativo do Azure AD devem ser os mesmos.

      Se você estiver usando um serviço de túnel, como ngrok, deverá atualizar esse valor sempre que o subdomínio ngrok mudar.
    - `AppID` é a ID do aplicativo (GUID) que foi gerada quando você registrou seu aplicativo. Você pode exibi-lo na seção **Visão geral**.

    > [!IMPORTANT]
    >
    > - **URI da ID do aplicativo para aplicativo com vários recursos**: se você estiver criando um aplicativo com um bot, uma extensão de mensagens e uma guia, insira o URI da ID do aplicativo como `api://fully-qualified-domain-name.com/BotId-{YourClientId}`, em que o BotID é sua ID do aplicativo bot.
    >
    > - **Formatar para nome de domínio**: use letras minúsculas para o nome de domínio. Não use maiúsculas.
    >
    >   Por exemplo, para criar um serviço de aplicativo ou aplicativo Web com o nome do recurso, 'demoapplication':
    >
    >   | Se o nome do recurso base usado for | A URL será... | Há suporte para o formato em... |
    >   | --- | --- | --- |
    >   | *demoapplication* | **<https://demoapplication.example.net>** | Todas as plataformas.|
    >   | *DemoApplication* | **<https://DemoApplication.example.net>** | Somente área de trabalho, Web e iOS. Não há suporte para ele no Android. |
    >
    >    Use a opção minúscula *demoapplication* como o nome do recurso base.

1. Selecione **Salvar**.

    Uma mensagem é exibida no navegador informando que o URI da ID do aplicativo foi atualizado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="Mensagem do URI da ID do Aplicativo":::

    O URI da ID do aplicativo é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="URI da ID do aplicativo atualizado":::

1. Copie e salve o URI da ID do aplicativo. Você precisará dele para atualizar o manifesto do aplicativo Teams mais tarde.

### <a name="to-configure-api-scope"></a>Para configurar o escopo da API

1. Selecione **+ Adicionar um escopo** nos **Escopos definidos por esta seção de API**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Selecionar escopo":::

    A página **Adicionar um escopo** é exibida.

1. Insira os detalhes para configurar o escopo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Adicionar detalhes de escopo":::

    1. Insira o nome do escopo. Este é um campo obrigatório.
    2. Selecione o usuário que pode dar consentimento para este escopo. A opção padrão é **Somente administradores**.
    3. Insira o **Nome de exibição de consentimento do administrador**. Este é um campo obrigatório.
    4. Insira a descrição do consentimento do administrador. Este é um campo obrigatório.
    5. Insira o **Nome de exibição do consentimento do usuário**.
    6. Insira a descrição para o consentimento do usuário.
    7. Selecione a opção **Habilitado** para o estado.
    8. Selecione **Adicionar escopo**.

    Uma mensagem é exibida no navegador informando que o escopo foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Mensagem de escopo adicionado":::

    O novo escopo que você definiu é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Escopo adicionado e exibido":::

### <a name="to-configure-authorized-client-application"></a>Para configurar o aplicativo cliente autorizado

1. Percorra a página **Expor uma API** até a seção **Aplicativo cliente autorizado** e selecione **+ Adicionar um aplicativo cliente**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Aplicativo cliente autorizado":::

    A página **Adicionar um aplicativo cliente** será exibida.

1. Insira a ID de cliente apropriada do Microsoft 365 para o Cliente do Teams para os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo.

    Selecione :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Adicionar um aplicativo cliente":::.

    > [!NOTE]
    >
    > - As IDs de cliente do Microsoft 365 para aplicativos móveis, da área de trabalho e da Web para o Teams, o Office e o Outlook são as IDs reais que você deve adicionar.
    > - Para um aplicativo de guia do Teams, você precisará da Web ou SPA, pois não pode haver um aplicativo cliente móvel ou de área de trabalho do Teams.

    1. Escolha uma das seguintes IDs de cliente:

       | Usar a ID do cliente | Para autorizar... |
       | --- | --- |
       | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 | Aplicativo da área de trabalho ou móvel do Teams. |
       | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 | Aplicativo Web do Teams. |
       | 4765445b-32c6-49b0-83e6-1d93765276ca | Aplicativo Web do Office |
       | 0ec893e0-5785-4de6-99da-4ed124e5296c | Aplicativo da área de trabalho do Office |
       | d3590ed6-52b3-4102-aeff-aad2292ab01c | Área de trabalho do Outlook, aplicativo móvel |
       | bc59ab01-8403-45c6-8796-ac3ef710b3e3 | Aplicativo Web do Outlook |

    1. Selecione o URI da ID do aplicativo que você criou para seu aplicativo em **Escopos autorizados** para adicionar o escopo à API Web que você expôs.

    1. Selecione **Adicionar aplicativo**.

    Uma mensagem é exibida no navegador informando que o aplicativo cliente autorizado foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Mensagem de aplicativo cliente adicionado":::

    A ID do cliente é exibida na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Aplicativo cliente adicionado e exibido":::

> [!NOTE]
> Você pode autorizar mais de um aplicativo cliente. Repita as etapas deste procedimento para configurar outro aplicativo cliente autorizado.

## <a name="configure-access-token-version"></a>Configurar a versão do token de acesso

Você deve definir a versão do token de acesso aceitável para seu aplicativo. Essa configuração é feita no manifesto do aplicativo do Azure AD.

### <a name="to-define-the-access-token-version"></a>Para definir a versão do token de acesso

1. Selecione **Gerenciar** > **Manifesto** no painel esquerdo.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-manifest.png" alt-text="Manifesto do portal do Azure AD.":::

    O manifesto do aplicativo do Azure AD é exibido.

1. Insira **2** como o valor da propriedade `accessTokenAcceptedVersion`.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-manifest-value.png" alt-text="Valor da versão do token de acesso aceito":::

1. Selecione **Salvar**

    Uma mensagem é exibida no navegador informando que o manifesto foi atualizado com êxito.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-aad-manifest-msg.png" alt-text="Mensagem de Manifesto atualizado":::

Parabéns! Você concluiu a configuração do aplicativo no Azure AD necessária para habilitar o SSO para seu aplicativo de guia.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar código para habilitar o SSO](tab-sso-code.md)

## <a name="see-also"></a>Confira também

- [Locação no Diretório do Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps)
- [Estender o aplicativo de guia com permissões e escopo do Microsoft Graph](tab-sso-graph-api.md)
- [Início rápido: registrar um aplicativo na plataforma de identidade da Microsoft](/azure/active-directory/develop/quickstart-register-app)
- [Início rápido: configurar um aplicativo para expor uma API Web](/azure/active-directory/develop/quickstart-configure-app-expose-web-apis)
- [Fluxo de código de autorização do OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow)
