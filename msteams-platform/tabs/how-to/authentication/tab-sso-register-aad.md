---
title: Registre seu aplicativo guia com Azure AD
description: Descreve o registro do aplicativo guia com o Azure AD
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do Teams Microsoft Azure Active Directory (Azure AD) escopo de locação de token de acesso
ms.openlocfilehash: 01cb6cd54cf150af05b54617aec3159e9483d260
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558594"
---
# <a name="register-your-tab-app-in-azure-ad"></a>Registrar o aplicativo de guia no Azure AD

Azure AD fornece acesso ao seu aplicativo guia com base na identidade do Teams do usuário do aplicativo. Você precisará registrar seu aplicativo guia com o Azure AD para que o usuário do aplicativo que entrou no Teams possa ter acesso ao seu aplicativo guia.

## <a name="enabling-sso-on-azure-ad"></a>Habilitando o SSO no Azure AD

Registrar seu aplicativo de guia no Azure AD e habilitá-lo para SSO requer a configuração de aplicativos, como a geração de ID do aplicativo, a definição do escopo da API e a pré-autorização de IDs de cliente para aplicativos confiáveis.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-azure-ad.png" alt-text="Configurar Azure AD para enviar o token de acesso para o aplicativo cliente do Teams":::

Crie um novo registro de aplicativo no Azure AD e exponha sua API (Web) usando escopos (permissões). Configure uma relação de confiança entre a API exposta Azure AD seu aplicativo. Isso permite que o Cliente do Teams obtenha um token de acesso em nome do seu aplicativo e do usuário conectado. Você pode adicionar IDs de cliente para os aplicativos móveis, da área de trabalho e da Web confiáveis que você deseja pré-autorizar.

Talvez você também precise configurar detalhes adicionais, como autenticar usuários de aplicativos na plataforma ou dispositivo para o qual você deseja direcionar seu aplicativo guia.

Há suporte API do Graph permissões no nível do usuário, ou seja, email, perfil, offline_access e OpenId. Se você precisar de acesso a escopos adicionais do Graph, `User.Read` como ou `Mail.Read`, consulte [Obter um token de acesso com permissões do Graph](tab-sso-graph-api.md).

Azure AD configuração habilita o SSO para seu aplicativo guia no Teams. Ele responde com um token de acesso para validar o usuário do aplicativo.

> [!NOTE]
> O Microsoft Teams Toolkit registra o Azure AD aplicativo em um projeto de SSO.

### <a name="before-you-register-with-azure-ad"></a>Antes de se registrar no Azure AD

É útil se você aprender sobre a configuração para registrar seu aplicativo no Azure AD com antecedência. Verifique se você se preparou para configurar os seguintes detalhes antes de registrar seu aplicativo:

- **Opções de** locatário único ou multilocatário: seu aplicativo será usado apenas no locatário do Microsoft 365 em que ele está registrado ou muitos locatários do Microsoft 365 o usarão? Os aplicativos escritos para uma empresa normalmente são de locatário único; aplicativos escritos por um fornecedor de software independente e usados por muitos clientes precisam ser multilocatário para que o locatário de cada cliente possa acessar o aplicativo.
- **URI da ID** do aplicativo: é um URI globalmente exclusivo que identifica a API Web que você expõe para o acesso do aplicativo por meio de escopos. Ele também é conhecido como um URI de identificador. O URI da ID do aplicativo inclui a ID do aplicativo e o subdomínio em que seu aplicativo está hospedado. O nome de domínio do aplicativo e o nome de domínio que você registra para Azure AD aplicativo deve ser o mesmo. Atualmente, não há suporte para vários domínios por aplicativo.
- **Escopo**: é a permissão que um usuário de aplicativo autorizado ou seu aplicativo pode receber para acessar um recurso exposto pela API.

> [!NOTE]
>
> - **Aplicativos LOB**: sua organização pode disponibilizar aplicativos LOB por meio da Microsoft Store. Esses aplicativos são personalizados para sua organização. Eles são internos ou específicos em sua organização ou empresa.
> - **Aplicativos de propriedade do** cliente: o SSO também tem suporte para aplicativos de propriedade do cliente nos locatários Azure AD B2C.

Para criar e configurar seu aplicativo no Azure AD para habilitar o SSO:

- [Registre e configure o Azure AD aplicativo.](#create-an-app-registration-in-azure-ad)
- [Configure o escopo para o token de acesso.](#configure-scope-for-access-token)
- [Configurar a versão do token de acesso.](#configure-access-token-version)

## <a name="create-an-app-registration-in-azure-ad"></a>Criar um registro de aplicativo no Azure AD

Registre um novo aplicativo no Azure AD e configure a locação e a plataforma do aplicativo. Você gerará uma nova ID do aplicativo que será atualizada posteriormente no arquivo de manifesto do aplicativo Teams.

### <a name="to-register-a-new-app-in-azure-ad"></a>Para registrar um novo aplicativo no Azure AD

1. Abra o [portal do Azure](https://ms.portal.azure.com/) no navegador da Web.
   A página Microsoft Azure AD Portal do Azure é aberta.

2. Selecione o **Registros de aplicativo** ícone.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal.png" alt-text="Azure AD portal.":::

   A **Registros de aplicativo** página é exibida.

3. Selecione **+ Novo ícone de** registro.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-registrations.png" alt-text="Nova página de registro no Azure AD Portal.":::

    A página **Registrar um aplicativo** é exibida.

4. Insira o nome do aplicativo que você deseja exibir para o usuário do aplicativo. Você pode alterar esse nome em um estágio posterior, se desejar.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-app.png" alt-text="Página de registro de aplicativo Azure AD Portal.":::

5. Selecione o tipo de conta de usuário que pode acessar seu aplicativo. Você pode escolher entre opções de locatário único ou multilocatário ou conta Privada da Microsoft.

    <details>
    <summary><b>Opções para tipos de conta com suporte</b></summary>

    | Opção | Selecione esta opção para... |
    | --- | --- |
    | Contas somente neste diretório organizacional (somente Microsoft – locatário único) | Crie um aplicativo para uso somente por usuários (ou convidados) em seu locatário. <br> Geralmente chamado de aplicativo LOB, esse aplicativo é um aplicativo de locatário único no plataforma de identidade da Microsoft. |
    | Contas em qualquer diretório organizacional (qualquer Azure AD diretório – multilocatário) | Permitir que os usuários em qualquer locatário Azure AD usem seu aplicativo. Essa opção é apropriada se, por exemplo, você estiver criando um aplicativo SaaS e pretende dispo-lo para várias organizações. <br> Esse tipo de aplicativo é conhecido como um aplicativo multilocatário no plataforma de identidade da Microsoft.|
    | Contas em qualquer diretório organizacional (qualquer diretório Azure AD – multilocatário) e contas pessoais da Microsoft | Direções ao conjunto mais amplo de clientes. <br> Ao selecionar essa opção, você está registrando um aplicativo multilocatário que pode dar suporte a usuários de aplicativos que também têm contas pessoais da Microsoft. |
    | Somente contas pessoais da Microsoft | Crie um aplicativo somente para usuários que têm contas pessoais da Microsoft. |

    </details>

    > [!NOTE]
    > Você não precisa inserir o **URI de** Redirecionamento para habilitar o SSO para um aplicativo de guia.

7. Selecione **Registrar**.
    Uma mensagem aparece no navegador informando que o aplicativo foi criado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-created-msg.png" alt-text="Registre o aplicativo Azure AD Portal.":::

    A página com a ID do aplicativo e outras configurações é exibida.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tab-app-created.png" alt-text="O registro do aplicativo foi bem-sucedido.":::

8. Anote e salve a ID do aplicativo **da ID do aplicativo (cliente**). Você precisará dele para atualizar o manifesto do aplicativo Teams mais tarde.

    Seu aplicativo está registrado no Azure AD. Agora você deve ter a ID do aplicativo para seu aplicativo guia.

## <a name="configure-scope-for-access-token"></a>Configurar o escopo para o token de acesso

Depois de criar um novo registro de aplicativo, configure as opções de escopo (permissão) para enviar o token de acesso ao Cliente do Teams e autorizar aplicativos cliente confiáveis para habilitar o SSO.

Para configurar o escopo e autorizar aplicativos cliente confiáveis, você precisará de:

- [Para expor uma API](#to-expose-an-api): configure opções de escopo (permissão) para seu aplicativo. Você exporá uma API Web e configurará o URI da ID do aplicativo.
- [Para configurar o escopo da API](#to-configure-api-scope): defina o escopo para a API e os usuários que podem consentir um escopo. Você pode permitir que apenas administradores forneçam consentimento para permissões com privilégios mais altos.
- [Para configurar o aplicativo cliente autorizado](#to-configure-authorized-client-application): crie IDs de cliente autorizadas para aplicativos que você deseja pré-autorizar. Ele permite que o usuário do aplicativo acesse os escopos do aplicativo (permissões) que você configurou, sem precisar de mais consentimento. Autorize previamente somente os aplicativos cliente em que você confia, pois os usuários do aplicativo não terão a oportunidade de recusar o consentimento.

### <a name="to-expose-an-api"></a>Para expor uma API

1. Selecione **Gerenciar** > **Expor uma API** no painel esquerdo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Expor uma opção de menu de API.":::

    A **página Expor uma API** é exibida.

1. Selecione **Definir** para gerar o URI da ID do aplicativo na forma de `api://{AppID}`.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="Definir o URI da ID do aplicativo":::

    A seção para definir o URI da ID do aplicativo é exibida.

1. Insira o URI da ID do aplicativo no formato explicado aqui.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="URI da ID do aplicativo":::

    - O **URI da ID do** Aplicativo é preenchido previamente com a ID do aplicativo (GUID) no formato `api://{AppID}`.
    - O formato de URI da ID do aplicativo deve ser: `api://fully-qualified-domain-name.com/{AppID}`.
    - Insira o `fully-qualified-domain-name.com` entre `api://` e `{AppID}` (que é, GUID). Por exemplo, api://example.com/{AppID}.

    Onde
    - `fully-qualified-domain-name.com` é o nome de domínio legível por humanos do qual seu aplicativo guia é atendido. O nome de domínio do aplicativo e o nome de domínio que você registra para Azure AD aplicativo deve ser o mesmo.

      Se você estiver usando um serviço de túnel, como o ngrok, deverá atualizar esse valor sempre que o subdomínio ngrok for alterado.
    - `AppID` é a ID do aplicativo (GUID) que foi gerada quando você registrou seu aplicativo. Você pode exibi-lo na seção **Visão** geral.

    > [!IMPORTANT]
    >
    > - **URI da ID** do aplicativo para o aplicativo com vários recursos: se você estiver criando um aplicativo com um bot, uma extensão de mensagens e uma guia, insira o URI `api://fully-qualified-domain-name.com/BotId-{YourClientId}`da ID do aplicativo como , em que o BotID é sua ID de aplicativo de bot.
    >
    > - **Formato para nome de domínio**: use letras minúsculas para o nome de domínio. Não use maiúsculas.
    >
    >   Por exemplo, para criar um serviço de aplicativo ou aplicativo Web com o nome do recurso, 'demoapplication':
    >
    >   | Se o nome do recurso base usado for | A URL será... | Há suporte para o formato em... |
    >   | --- | --- | --- |
    >   | *Demoapplication* | **<https://demoapplication.example.net>** | Todas as plataformas.|
    >   | *Demoapplication* | **<https://DemoApplication.example.net>** | Somente desktop, Web e iOS. Não há suporte para ele no Android. |
    >
    >    Use a opção de *rebaixamento de letras minúsculas como* o nome do recurso base.

1. Selecione **Salvar**.

    Uma mensagem aparece no navegador informando que o URI da ID do aplicativo foi atualizado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="Mensagem de URI da ID do aplicativo":::

    O URI da ID do aplicativo é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="URI da ID do aplicativo atualizado":::

1. Anote e salve o URI da ID do Aplicativo. Você precisará dele para atualizar o manifesto do aplicativo Teams mais tarde.

### <a name="to-configure-api-scope"></a>Para configurar o escopo da API

1. Selecione **+ Adicionar um escopo** nos **Escopos definidos por esta seção de API** .

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Selecionar escopo":::

    A **página Adicionar um escopo** é exibida.

1. Insira os detalhes para configurar o escopo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Adicionar detalhes do escopo":::

    1. Insira o nome do escopo. Este é um campo obrigatório.
    2. Selecione o usuário que pode dar consentimento para esse escopo. A opção padrão é **somente Administradores**.
    3. Insira o nome **Administração de exibição de consentimento.** Este é um campo obrigatório.
    4. Insira a descrição do consentimento do administrador. Este é um campo obrigatório.
    5. Insira o nome **de exibição de consentimento do usuário**.
    6. Insira a descrição da descrição de consentimento do usuário.
    7. Selecione a **opção Habilitado** para estado.
    8. Selecione **Adicionar escopo**.

    Uma mensagem aparece no navegador informando que o escopo foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Mensagem de escopo adicionada":::

    O novo escopo definido é exibido na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Escopo adicionado e exibido":::

### <a name="to-configure-authorized-client-application"></a>Para configurar o aplicativo cliente autorizado

1. Mova a página **Expor uma API para a** **seção aplicativo cliente** autorizado e selecione **+ Adicionar um aplicativo cliente**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Aplicativo cliente autorizado":::

    A **página Adicionar um aplicativo cliente** é exibida.

1. Insira a ID de cliente apropriada para o Cliente do Teams para os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Adicionar um aplicativo cliente":::

    > [!NOTE]
    >
    > - As IDs do cliente para aplicativos Web, de área de trabalho e móveis do Teams são as IDs reais que você deve adicionar.
    > - Para um aplicativo de guia do Teams, você precisará da Web ou do SPA, pois não pode ter um aplicativo cliente móvel ou de área de trabalho no Teams.

    1. Escolha uma das seguintes IDs de cliente:

       | Usar a ID do cliente | Para autorizar... |
       | --- | --- |
       | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 | Aplicativo móvel ou de área de trabalho do Teams |
       | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 | Aplicativo Web do Teams |

    1. Selecione o URI da ID do aplicativo que você criou para seu aplicativo em **escopos autorizados** para adicionar o escopo à API Web que você expôs.

    1. Selecione **Adicionar aplicativo**.

    Uma mensagem aparece no navegador informando que o aplicativo cliente autorizado foi adicionado.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Mensagem adicionada pelo aplicativo cliente":::

    A ID do cliente é exibida na página.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Aplicativo cliente adicionado e exibido":::

> [!NOTE]
> Você pode autorizar mais de um aplicativo cliente. Repita as etapas deste procedimento para configurar outro aplicativo cliente autorizado.

## <a name="configure-access-token-version"></a>Configurar a versão do token de acesso

Você deve definir a versão do token de acesso que é aceitável para seu aplicativo. Essa configuração é feita no manifesto Azure AD aplicativo.

### <a name="to-define-the-access-token-version"></a>Para definir a versão do token de acesso

1. Selecione **Gerenciar** > **Manifesto** no painel esquerdo.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-manifest.png" alt-text="manifesto Azure AD portal do Azure AD":::

    O Azure AD manifesto do aplicativo é exibido.

1. Insira **2** como o valor da `accessTokenAcceptedVersion` propriedade.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-manifest-value.png" alt-text="Valor da versão do token de acesso aceito":::

1. Selecione **Salvar**

    Uma mensagem aparece no navegador informando que o manifesto foi atualizado com êxito.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-aad-manifest-msg.png" alt-text="Mensagem atualizada do manifesto":::

Parabéns! Você concluiu a configuração do aplicativo Azure AD necessário para habilitar o SSO para seu aplicativo guia.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Configurar código para habilitar o SSO](tab-sso-code.md)

## <a name="see-also"></a>Confira também

- [Locação no Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps)
- [Estender o aplicativo guia com permissões e escopo do Microsoft Graph](tab-sso-graph-api.md)
- [Início Rápido – Registrar um aplicativo com o plataforma de identidade da Microsoft](/azure/active-directory/develop/quickstart-register-app)
- [Início Rápido: Configurar um aplicativo para expor uma API Web](/azure/active-directory/develop/quickstart-configure-app-expose-web-apis)
- [Fluxo de código de autorização do OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow)
