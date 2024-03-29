---
title: Adicionar autenticação ao seu bot do Teams
author: surbhigupta
description: Saiba como habilitar a autenticação usando o provedor OAuth de terceiros para um aplicativo de bot no Teams usando Azure AD.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: db760f81195634431fe0d3415b1a9c3797b519e7
ms.sourcegitcommit: 176bbca74ba46b7ac298899d19a2d75087fb37c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68376631"
---
# <a name="add-authentication-to-your-teams-bot"></a>Adicionar autenticação ao seu bot do Teams

Há ocasiões em que talvez seja necessário criar no Microsoft Teams bots que possam acessar recursos em nome do usuário, como um serviço de e-mail.

Este artigo demonstra como usar a autenticação do SDK do Serviço de Bots do Azure v4, baseada no OAuth 2.0. Isso facilita o desenvolvimento de um bot que pode usar tokens de autenticação baseados nas credenciais do usuário. A chave em tudo isso é o uso de **provedores de identidade**, como veremos mais tarde.

O OAuth 2.0 é um padrão aberto de autenticação e autorização usado pelo Microsoft Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é pré-requisito para trabalhar com autenticação no Teams.

Confira o artigo [OAuth 2 Simplificado](https://aka.ms/oauth2-simplified) para uma compreensão básica e [OAuth 2.0](https://oauth.net/2/) para obter a especificação completa.

Para obter mais informações sobre como o Serviço de Bots do Azure lida com a autenticação, confira o artigo [Autenticação de usuário dentro de uma conversa](https://aka.ms/azure-bot-authentication).

Neste artigo, você aprenderá:

- **Como criar um bot habilitado para autenticação**. Você usará o recurso [cs-auth-sample][teams-auth-bot-cs] para lidar com as credenciais de login do usuário e gerar o token de autenticação.
- **Como implantar o bot no Azure e associá-lo a um provedor de identidade**. O provedor emite um token com base nas credenciais de login do usuário. O bot pode usar o token para acessar recursos que exigem autenticação, como um serviço de e-mail. Para obter mais informações, consulte  [o fluxo de autenticação do Microsoft Teams para bots](auth-flow-bot.md).
- **Como integrar o bot dentro do Microsoft Teams**. Após o bot ter sido integrado, você poderá entrar e trocar mensagens com ele em um chat.

## <a name="prerequisites"></a>Pré-requisitos

- Conhecimento de [noções básicas de bots][concept-basics], [status de gerenciamento][concept-state], [biblioteca de diálogos][concept-dialogs] e de como [implementar um fluxo de conversa sequencial][simple-dialog].
- Conhecimento do Azure e do desenvolvimento do OAuth 2.0.
- Versões atuais do Microsoft Visual Studio e do Git.
- Uma conta do Azure. Se necessário, você pode criar uma [conta gratuita do Azure](https://azure.microsoft.com/free/).
- O exemplo a seguir,

    | uma amostra de | versão do BotBuilder, | demonstra |
    |:---|:---:|:---|
    | **uma autenticação de bot** no [cs-auth-sample][teams-auth-bot-cs] | v4 | com suporte a OAuthCard |
    | **uma autenticação de bot** no [js-auth-sample][teams-auth-bot-js] | v4| com suporte a OAuthCard  |
    | **uma autenticação de bot** no [py-auth-sample][teams-auth-bot-py] | v4 | com suporte a OAuthCard |

## <a name="create-the-resource-group"></a>Criar o grupo de recursos

O grupo de recursos e o plano de serviços não são estritamente necessários, mas permitem que você lance convenientemente os recursos que criar. Trata-se de uma boa prática para manter seus recursos organizados e gerenciáveis.

Você usa um grupo de recursos para criar recursos individuais para o Bot Framework. Para garantir o desempenho, certifique-se de que esses recursos esteiam localizados na mesma região do Azure.

1. No seu navegador, entre no [**portal do Microsoft Azure**][azure-portal].
1. No painel de navegação esquerdo, selecione **Grupos de recursos**.
1. No canto superior esquerdo da janela exibida, selecione a guia **Adicionar** para criar um novo grupo de recursos. Você será solicitado a fornecer o seguinte:
    1. **Assinatura**. Use sua assinatura existente.
    1. **Grupo de recursos**. Digite o nome do grupo de recursos. Um exemplo poderia ser *TeamsResourceGroup*. Lembre-se de que o nome deve ser único.
    1. No menu suspenso **Região**, selecione *Oeste dos EUA* ou uma região próxima dos seus aplicativos.
    1. Selecione o botão **Rever e criar**. Você deverá ver uma faixa com o texto *Validação aprovada*.
    1. Selecione o botão **Criar**. Poderá levar alguns minutos para criar o grupo de recursos.

> [!TIP]
> Assim como ocorre com os recursos que você criará mais adiante neste tutorial, é uma boa ideia fixar esse grupo de recursos no seu painel de controle para facilitar o acesso. Caso queira fazê-lo, selecione o ícone de pino &#128204; no canto superior direito do painel de controle.

## <a name="create-the-service-plan"></a>Criar o plano de serviço

1. No [**Portal do Azure**][azure-portal], no painel de navegação esquerdo, selecione **Criar um recurso**.
1. Na caixa de pesquisa, digite *Plano de Serviço do Aplicativo* (em inglês: App Service Plan). Selecione o cartão do **Plano de Serviço do Aplicativo** nos resultados da pesquisa.
1. Selecione **Criar**.
1. Você será solicitado a fornecer as seguintes informações:
    1. **Assinatura**. Você pode usar uma assinatura existente.
    1. **Grupo de Recursos**. Selecione o grupo que você criou anteriormente.
    1. **Nome**. Digite o nome do plano de serviço. Um exemplo pode ser *TeamsServicePlan*. Lembre-se de que o nome deve ser único dentro do grupo.
    1. **Sistema Operacional**. Selecione *Windows* ou seu sistema operacional aplicável.
    1. **Região**. Selecione *Oeste dos EUA* ou uma região próxima dos seus aplicativos.
    1. **Nível de preço**. Certifique-se de que *Standard S1* esteja selecionado. Esse deve ser o valor padrão.
    1. Selecione o botão **Rever e criar**. Você deverá ver uma faixa com o texto *Validação aprovada*.
    1. Selecione **Criar**. Poderá levar alguns minutos para criar o plano de serviço do aplicativo. O plano será listado no grupo de recursos.

## <a name="create-azure-bot-resource-registration"></a>Criar um registro de recursos do Bot do Azure

O registro de recursos do Bot do Azure registra seu serviço Web como um bot com o Bot Framework, que fornece uma ID do Aplicativo da Microsoft e uma senha do aplicativo (segredo do cliente).

> [!IMPORTANT]
> Você só precisa registrar seu bot se ele não estiver hospedado no Azure. Se você [criou um bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) por meio do Portal do Azure, ele já estará registrado junto ao serviço. Se você criou seu bot por meio do [Bot Framework](https://dev.botframework.com/bots/new) ou do [Portal do Desenvolvedor](../../../concepts/build-and-test/teams-developer-portal.md), seu bot não estará registrado no Azure.

1. Visite o [**Portal do Azure**][azure-portal] e pesquise **Bot do Azure** na seção **Criar um recurso**.
1. Abra o **Bot do Azure** e selecione **Criar**.
1. Digite o nome do identificador do bot no campo **Identificador do bot**.
1. Selecione sua **Assinatura** na lista suspensa.
1. Selecione seu **Grupo de recursos** na lista suspensa.
1. Selecione o **Tipo de Aplicativo** **Multilocatário** para a **ID de Aplicativo da Microsoft**.

   :::image type="content" source="../../../assets/images/adaptive-cards/multi-tenant.png" alt-text="Esta captura de tela mostra como selecionar vários locatários para o Microsoft AppID.":::

1. Selecione **Rever + criar**.

   :::image type="content" source="../../../assets/images/adaptive-cards/create-azure-bot.png" alt-text="Esta captura de tela mostra como criar um bot do Azure.":::

1. Se a validação for aprovada, selecione **Criar**.

    Levará alguns minutos para o serviço de bot ser provisionado.

   :::image type="content" source="../../../assets/images/adaptive-cards/validation-pane.png" alt-text="Esta captura de tela mostra como a validação de bot do Azure é aprovada.":::

1. Selecione **Vá para o recurso**. O bot e os respectivos recursos estão listados no grupo de recursos.

   :::image type="content" source="../../../assets/images/adaptive-cards/go-to-resource-card.png" alt-text="Esta captura de tela mostra como selecionar o grupo de recursos.":::

    Agora seu bot do Azure foi criado.

   :::image type="content" source="../../../assets/images/adaptive-cards/azure-bot-ui.png" alt-text="Esta captura de tela mostra como criar recursos de bot do Azure.":::

Para criar um segredo do cliente:

1. Em **Configurações**, selecione **Configurar**. Salve a **ID de Aplicativo da Microsoft** (ID do cliente) para referência futura.

   :::image type="content" source="../../../assets/images/adaptive-cards/config-microsoft-app-id.png" alt-text="Esta captura de tela mostra como adicionar a ID do Aplicativo da Microsoft para criar o segredo do cliente.":::

1. Ao lado da **ID do Aplicativo da Microsoft**, selecione **Gerenciar**.

   :::image type="content" source="~/assets/images/manage-bot-label.png" alt-text="Esta captura de tela mostra como criar o bot de gerenciamento.":::

1. Na seção **Segredos do cliente**, selecione **Novo segredo do cliente**. A janela **Adicionar um segredo do cliente** irá aparecer.

   :::image type="content" source="../../../assets/images/meetings-side-panel/newclientsecret.PNG" alt-text="Esta captura de tela mostra como criar um novo segredo do cliente.":::

1. Digite uma **Descrição** e selecione **Adicionar**.

   :::image type="content" source="../../../assets/images/adaptive-cards/client-secret.png" alt-text="A captura de tela mostra como inserir a descrição do segredo do cliente.":::

1. Na coluna **Valor**, selecione **Copiar para a área de transferência** e salve a ID do segredo do cliente para referência futura.

   :::image type="content" source="../../../assets/images/adaptive-cards/client-secret-value.png" alt-text="A captura de tela mostra como salvar a ID do segredo do cliente para referência futura.":::

Para adicionar o canal do Microsoft Teams:

1. Vá para a **Página Inicial**.

   :::image type="content" source="../../../assets/images/adaptive-cards/bot-home-page.png" alt-text="Esta captura de tela mostra a home page do bot.":::

1. Abra o bot, que está listado na seção **Recursos recentes**.

1. Selecione **Canais** no painel esquerdo e selecione **Microsoft Teams** :::image type="icon" source="../../../assets/icons/teams-icon.png":::.

   :::image type="content" source="../../../assets/images/adaptive-cards/channel-teams.png" alt-text="Esta captura de tela mostra como selecionar o Teams em canais.":::

1. Marque a caixa de seleção para aceitar os termos de serviço e selecione **Concordar**.</br>

   :::image type="content" source="../../../assets/images/adaptive-cards/select-terms-of-service.png" alt-text="Esta captura de tela mostra como definir os termos se o serviço.":::

1. Selecione **Salvar**.

   :::image type="content" source="../../../assets/images/adaptive-cards/select-teams.png" alt-text="Esta captura de tela mostra como adicionar o canal do Microsoft Teams.":::

Para obter mais informações, confira [Criar um bot para o Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Criar o provedor de identidade

Você precisa de um provedor de identidade que possa ser usado para a autenticação.
Neste procedimento, você usará um provedor de Azure AD; outros Azure AD provedores de identidade com suporte também podem ser usados.

1. No painel de navegação esquerdo do [**Portal do Azure**][azure-portal], clique em **Azure Active Directory**.
    > [!TIP]
    > Você precisará criar e registrar esse recurso do Azure AD em um locatário no qual você possa consentir em delegar as permissões solicitadas por um aplicativo.
    > Para obter instruções sobre como criar um locatário, confira o artigo [Acessar o portal e criar um locatário](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. No painel esquerdo, selecione **Registros de aplicativos**.
1. No painel direito, selecione a guia **Novo registro**, no canto superior esquerdo.
1. Você será solicitado a fornecer as seguintes informações:
   1. **Nome**. Digite o nome para o aplicativo. Um exemplo poderia ser *BotTeamsIdentity*. Lembre-se de que o nome deve ser único.
   1. Selecione **Tipos de conta com suporte** para seu aplicativo. Selecione *Contas em qualquer diretório organizacional (qualquer Microsoft Azure Active Directory (Azure AD) – Multilocatário) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.
   1. Para o **URI de redirecionamento**:<br/>
       &#x2713;Select **Web**. <br/>
       &#x2713; Defina o URL como `https://token.botframework.com/.auth/web/redirect`.
   1. Selecione **Registrar**.

1. Depois de criado, o Azure exibe **a página Visão** geral do aplicativo. Copie e salve as seguintes informações em um arquivo:

    1. O valor **ID do aplicativo (cliente)**. Você usará esse valor mais tarde como a *ID do cliente* ao registrar esse aplicativo de identidade do Azure junto ao seu bot.
    1. O valor **ID do diretório (locatário)**. Você também usará esse valor mais tarde como a *ID do locatário* para registrar esse aplicativo de identidade do Azure junto ao seu bot.

1. No painel esquerdo, selecione **Certificados e segredos** para criar um segredo do cliente para seu aplicativo.

   1. Na guia **Segredos do cliente**, selecione &#x2795; **Novo segredo do cliente**.
   1. Adicione uma descrição para identificar esse segredo e diferenciá-lo de outros que você talvez precise criar para esse aplicativo, como, por exemplo, *Identidade do aplicativo de bot no Teams*.
   1. Configure **Expira em** para a sua seleção.
   1. Selecione **Adicionar**.
   1. Antes de sair desta página, **grave o segredo**. Você usará esse valor mais tarde como *Segredo do cliente* quando registrar seu aplicativo do Azure AD junto ao seu bot.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Configurar a conexão do provedor de identidade e registrá-la junto ao bot

Observe que há duas opções para Provedores de Serviços aqui– Azure AD V1 e Azure AD V2.  As diferenças entre os dois provedores estão resumidas [aqui](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), mas, de modo geral, a V2 oferece mais flexibilidade com relação às alterações de permissões do bot.  As permissões de Graph API estão listadas no campo de escopos e, à medida que novas forem adicionadas, os bots permitirão que os usuários deem seu consentimento às novas permissões no próximo login.  No caso do V1, o consentimento do bot deve ser excluído pelo usuário para que novas permissões sejam solicitadas na caixa de diálogo do OAuth.

#### <a name="microsoft-azure-active-directory-azure-ad-v1"></a>Microsoft Azure Active Directory (Azure AD) V1

1. No [**Portal do Azure**][azure-portal], selecione seu grupo de recursos no painel de controle.
1. Selecione o link de registro do bot.
1. Abra a página de recursos e selecione **Configurar**, na guia **Configurações**.
1. Selecione **Adicionar configurações de conexão OAuth**.
   A imagem a seguir exibe a seleção correspondente na página de recursos:

   ![Configuração de SampleAppDemoBot](~/assets/images/authentication/sample-app-demo-bot-configuration.png)

1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome**. Digite um nome para a conexão. Você usará esse nome no seu bot no arquivo `appsettings.json`. Por exemplo, *BotTeamsAuthADv1*.
    1. **Provedor de serviços**. Selecione **Microsoft Azure Active Directory (Azure AD)**. Após selecionar, os campos específicos do Azure AD serão exibidos.
    1. **ID do cliente**. Digite a ID do aplicativo (cliente) que você gravou para o aplicativo do provedor de identidade do Azure nas etapas acima.
    1. **Segredo do cliente**. Digite o segredo que você gravou para o seu aplicativo de provedor de identidade do Azure nas etapas acima.
    1. **Tipo de Concessão**. Digite `authorization_code`.
    1. **URL de login**. Digite `https://login.microsoftonline.com`.
    1. **ID do locatário**: digite a **ID do diretório (locatário)** que você gravou anteriormente para o seu aplicativo de identidade do Azure ou **comum**, dependendo do tipo de conta com suporte selecionado quando você criou o aplicativo do provedor de identidade. Para decidir qual valor atribuir, siga estes critérios:

        - Se você selecionou Contas somente neste diretório organizacional *(somente Microsoft* – Locatário único) ou Contas em qualquer diretório organizacional *(Microsoft Azure Active Directory (Azure AD) – Multilocatário)* , insira a **ID** de locatário que você registrou anteriormente para o Microsoft Azure Active Directory (Azure AD) . Esse será o locatário associado aos usuários que podem ser autenticados.

        - Se você selecionou Contas em qualquer diretório organizacional (qualquer Microsoft Azure Active Directory (Azure AD) – contas microsoft multilocatário e pessoais, por exemplo *, Skype, Xbox, Outlook)* insira a palavra comum  em vez de uma ID de locatário. Caso contrário, o Azure AD (Azure AD) verifica por meio do locatário cuja ID foi selecionada e exclui contas pessoais da Microsoft.

    h. Para o **URL do recurso**, digite `https://graph.microsoft.com/`. Isso não é usado no exemplo de código atual.  
    i. Deixe **Escopos** em branco. A imagem a seguir é um exemplo:

    :::image type="content" source="../../../assets/images/authentication/auth-bot-identity-connection-adv1.PNG" alt-text="Esta captura de tela mostra como adicionar a conexão de identidade do bot de autenticação do Teams adv1.":::

1. Selecione **Salvar**.

#### <a name="microsoft-azure-active-directory-azure-ad-v2"></a>Microsoft Azure Active Directory (Azure AD) V2

1. No [**Portal do Azure**][azure-portal], selecione seu Bot do Azure no painel de controle.
1. Na página de recursos, selecione **Configurar**, na guia **Configurações**.
1. Selecione **Adicionar configurações de conexão OAuth**.  
   A imagem a seguir exibe a seleção correspondente na página de recursos:

   :::image type="content" source="../../../assets/images/authentication/sample-app-demo-bot-configuration.png" alt-text="Esta captura de tela mostra a seleção correspondente na página de recursos.":::

1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome**. Digite um nome para a conexão. Você usará esse nome no seu bot no arquivo `appsettings.json`. Por exemplo, *BotTeamsAuthADv2*.
    1. **Provedor de serviços**. Selecione **Microsoft Azure Active Directory v2**. Depois de selecionar isso, Azure AD campos específicos serão exibidos.
    1. **ID do cliente**. Digite a ID do aplicativo (cliente) que você gravou para o aplicativo do provedor de identidade do Azure nas etapas acima.
    1. **Segredo do cliente**. Digite o segredo que você gravou para o seu aplicativo de provedor de identidade do Azure nas etapas acima.
    1. **URL da troca de tokens**. Deixe em branco.
    1. **ID do locatário**: digite a **ID do diretório (locatário)** que você gravou anteriormente para o seu aplicativo de identidade do Azure ou **comum**, dependendo do tipo de conta com suporte selecionado quando você criou o aplicativo do provedor de identidade. Para decidir qual valor atribuir, siga estes critérios:

        - Se você selecionou Contas somente neste diretório organizacional *(somente Microsoft* – Locatário único) ou Contas em qualquer diretório organizacional *(Microsoft Azure Active Directory – Multilocatário)*, insira a **ID** de locatário que você registrou anteriormente para o Azure AD aplicativo. Esse será o locatário associado aos usuários que podem ser autenticados.

        - Se você selecionou Contas em qualquer diretório organizacional (qualquer Microsoft Azure Active Directory (Azure AD) – contas microsoft multilocatário e pessoais, por exemplo *, Skype, Xbox, Outlook)* insira a palavra comum  em vez de uma ID de locatário. Caso contrário, o Azure AD verifica por meio do locatário cuja ID foi selecionada e exclui contas pessoais da Microsoft.

    1. Para **Escopos**, insira uma lista delimitada por espaço de permissões de grafo que este aplicativo requer, por exemplo: User.Read User.ReadBasic.All Mail.Read

1. Selecione **Salvar**.

### <a name="test-the-connection"></a>Testar a conexão

1. Selecione a entrada de conexão para abrir a conexão que você criou.
1. Selecione **Testar Conexão** na parte superior do painel de controle da **Configuração de Conexão do Provedor de Serviços**.
1. Da primeira vez que você fizer isso, será aberta uma nova janela do navegador solicitando que você selecione uma conta. Selecione a que você quer usar.
1. Em seguida, você será solicitado a permitir que o provedor de identidade use seus dados (credenciais). A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-connection-test-accept.PNG" alt-text="A captura de tela mostra como adicionar a cadeia de conexão de autenticação de bot do Teams adv1.":::

1. Selecione **Aceitar**.
1. Isso deverá redirecioná-lo para uma página **Teste da conexão com \<your-connection-name> bem-sucedido**. Atualize a página caso receba uma mensagem de erro. A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-connection-test-token.PNG" alt-text="A captura de tela mostra como adicionar a cadeia de conexão de autenticação do aplicativo Teams adv1.":::

O nome da conexão é usado pelo código do bot para recuperar tokens de autenticação do usuário.

## <a name="prepare-the-bot-sample-code"></a>Preparar a amostra de código do bot

Com as configurações preliminares concluídas, vamos nos concentrar na criação do bot a ser usado neste artigo.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. Clonar a [cs-auth-sample][teams-auth-bot-cs].
1. Inicie o Visual Studio.
1. Na barra de ferramentas, selecione **Arquivo -> Abrir -> Projeto/Solução** e abra o projeto de bot.
1. Em C#, **atualize appsettings.json** da seguinte maneira:

    - Defina `ConnectionName` como o nome da conexão do provedor de identidade que você adicionou ao registro do bot. O nome que usamos nesse exemplo foi *BotTeamsAuthADv1*.
    - Defina `MicrosoftAppId` como a **ID do aplicativo de bot** que você salvou no momento do registro do bot.
    - Defina `MicrosoftAppPassword` como o **segredo do cliente** que você salvou no momento do registro do bot.

    Dependendo dos caracteres do segredo do seu bot, talvez seja necessário que o XML escape da senha. Por exemplo, todos os caracteres E comerciais (&) precisarão ser codificados como `&amp;`.

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. No Gerenciador de Soluções, vá `TeamsAppManifest` para a pasta, `botId` `manifest.json` `id` abra e defina e para a ID do aplicativo **de bot** que você salvou no momento do registro do bot.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Clonar a [node-auth-sample][teams-auth-bot-js].
1. Em um console, vá para o projeto: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Instale os módulos</br></br>
`npm install`
1. Atualize a configuração **.env** conforme se segue:

    - Defina `MicrosoftAppId` como a **ID do aplicativo de bot** que você salvou no momento do registro do bot.
    - Defina `MicrosoftAppPassword` como o **segredo do cliente** que você salvou no momento do registro do bot.
    - Configure o `connectionName` como o nome da conexão do provedor de identidade.
    Dependendo dos caracteres do segredo do seu bot, talvez seja necessário que o XML escape da senha. Por exemplo, todos os caracteres E comerciais (&) precisarão ser codificados como `&amp;`.

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Na pasta `teamsAppManifest`, abra `manifest.json` e defina `id` como sua **ID de Aplicativo da Microsoft** e `botId` para a **ID de Aplicativo do bot** que você salvou no momento do registro do bot.

# <a name="python"></a>[Python](#tab/python)

1. Clonar a [py-auth-sample][teams-auth-bot-py] do repositório do GitHub.
1. Atualize o **config.py**:

    - Defina `ConnectionName` como o nome da configuração de conexão OAuth que você adicionou ao seu bot.
    - Defina `MicrosoftAppId` e `MicrosoftAppPassword` como a ID do aplicativo e o segredo do aplicativo do seu bot.

      Dependendo dos caracteres do segredo do seu bot, talvez seja necessário que o XML escape da senha. Por exemplo, todos os caracteres E comerciais (&) precisarão ser codificados como `&amp;`.

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Implantar o bot no Azure

Para implantar o bot, siga as etapas em Como [implantar seu bot no Azure](https://aka.ms/azure-bot-deployment-cli).

Alternativamente, enquanto estiver no Visual Studio você pode seguir as etapas abaixo:

1. No Visual Studio *Gerenciador de Soluções*, selecione e segure (ou clique com o botão direito do mouse) no nome do projeto.
1. No menu suspenso, selecione **Publicar**.
1. Na janela que aparece, selecione o **Novo** link.
1. Na janela de diálogo, selecione **Serviço do Aplicativo** à esquerda e **Criar Novo** à direita.
1. Selecione o botão **Publicar**.
1. Na próxima janela de diálogo, insira as informações solicitadas. O que se segue é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-app-service.png" alt-text="Esta captura de tela mostra como inserir as informações necessárias para o serviço de aplicativo de autenticação.":::

1. Selecionar **Criar**.
1. Se a implantação for concluída com sucesso, você deverá vê-la refletida no Visual Studio. Além disso, uma página será exibida no seu navegador padrão com os dizeres *Seu bot está pronto!* O URL será parecido com o seguinte: `https://botteamsauth.azurewebsites.net/`. Salve-o em um arquivo.
1. No navegador, vá para o [**portal do Azure**][azure-portal].
1. Verifique seu grupo de recursos. O bot deve estar listado junto com os outros recursos. A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-app-service-in-group.png" alt-text="Esta captura de tela mostra como verificar o grupo de recursos e o bot.":::

1. No grupo de recursos, selecione o nome de registro do bot (link).
1. No painel esquerdo, selecione **Configurações**.
1. Na caixa **Ponto de extremidade de mensagens**, digite o URL obtido acima, seguido de `api/messages`. Esse é um exemplo: `https://botteamsauth.azurewebsites.net/api/messages`.
    > [!NOTE]
    > Somente um ponto de extremidade de mensagens é permitido para um bot.
1. Selecione o botão **Salvar** no canto superior esquerdo.

## <a name="test-the-bot-using-the-emulator"></a>Testar o bot usando o Emulador

Se ainda não o tiver feito, instale o [Emulador de Bot Framework da Microsoft](https://aka.ms/bot-framework-emulator-readme). Confira também [Depurar com o Emulador](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Para que o login de exemplo do bot funcione, você precisa configurar o Emulador.

### <a name="configure-the-emulator-for-authentication"></a>Configurar o Emulador para a autenticação

Se um bot exigir autenticação, você precisará configurar o Emulador. Para configurar:

1. Inicie o Emulador.
1. No Emulador, selecione o ícone de engrenagem &#9881; na parte inferior esquerda ou na guia **Configurações	do Emulador**, no canto superior direito.
1. Marque a caixa próxima a **Usar tokens de autenticação versão 1.0**.
1. Digite o caminho local para a ferramenta **ngrok**. *Confira* o [wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)) de integração entre o Emulador de Bot Framework e a criação de túneis do ngrok. Para obter mais informações sobre a ferramenta, confira o [ngrok](https://ngrok.com/).
1. Marque a caixa próxima a **Executar o ngrok ao iniciar o Emulador**.
1. Selecione o botão **Salvar**.

Quando o bot exibe um cartão de login e o usuário seleciona o botão de login, o Emulador abre uma página que o usuário pode usar para entrar com o provedor de autenticação.
Após o usuário ter feito isso, o provedor gera um token de usuário e o envia para o bot. A partir daí o bot pode agir em nome do usuário.

### <a name="test-the-bot-locally"></a>Testar o bot localmente

Depois de configurar o mecanismo de autenticação, você poderá executar o teste de bot real.  

1. Por exemplo, execute a amostra do bot localmente no seu computador por meio do Visual Studio.
1. Inicie o Emulador.
1. Selecione o botão **Abrir bot**.
1. No **URL do bot**, digite o URL local do bot. Normalmente, `http://localhost:3978/api/messages`.
1. No campo **ID de Aplicativo da Microsoft**, digite a ID do aplicativo do bot da `appsettings.json`.
1. No campo **Senha do Aplicativo da Microsoft**, digite a senha do aplicativo do bot da `appsettings.json`.
1. Selecione **Conectar**.
1. Quando o bot estiver ativado e funcionando, digite um texto qualquer para exibir o cartão de login.
1. Selecione o botão **Entrar**.
1. Uma caixa de diálogo pop-up é exibida para **Confirmar abrir o URL**. Isso irá permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta de usuário aplicável.
1. Dependendo da configuração usada para o Emulador, você obtém uma das seguintes opções:
    1. **Usar um código de verificação de login**  
      &#x2713; Uma janela se abre mostrando o código de validação.  
      &#x2713; Copie e insira o código de validação na caixa de chat para concluir o login.
    1. **Usar tokens de autenticação**.  
      &#x2713; Você está conectado com base nas suas credenciais.

    A imagem a seguir é um exemplo da interface de usuário do bot após você ter entrado:

    :::image type="content" source="../../../assets/images/authentication/auth-bot-login-emulator.PNG" alt-text="Esta captura de tela mostra um exemplo da interface do usuário do bot depois que você tiver feito logon.":::

1. Se você selecionar **Sim** quando o bot perguntar, deseja exibir o *token?* Você receberá uma resposta semelhante à seguinte:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-login-emulator-token.png" alt-text="Esta captura de tela mostra como selecionar o consentimento.":::

1. Digite **sair** na caixa de digitação do chat para sair. Isso libera o token de usuário e o bot não poderá mais agir em seu nome até que você entre novamente.

> [!NOTE]
> A autenticação do bot requer o uso do **Serviço de Conector do Bot**. O serviço acessa as informações de registro de bots do seu bot.

## <a name="test-the-deployed-bot"></a>Testar o bot implantado

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. No navegador, vá para o [**portal do Azure**][azure-portal].
1. Localize seu grupo de recursos.
1. Selecione o link do recurso. A página de recursos é exibida.
1. Na página de recursos, selecione **Testar no web chat**. O bot é iniciado e mostra as saudações predefinidas.
1. Digite qualquer coisa na caixa de chat.
1. Selecione a caixa **Login**.
1. Uma caixa de diálogo pop-up é exibida para **Confirmar abrir o URL**. Isso irá permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta de usuário aplicável.
    A imagem a seguir é um exemplo da interface de usuário do bot após você ter entrado:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-login-deployed.PNG" alt-text="Esta captura de tela mostra um exemplo da interface do usuário do bot do Teams depois que você tiver feito logon.":::

1. Selecione o botão **Sim** para exibir seu token de autenticação. A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-login-deployed-token.PNG" alt-text="Esta captura de tela mostra como selecionar o botão Sim para exibir o token de autenticação.":::

1. Digite sair para sair.

   :::image type="content" source="../../../assets/images/authentication/auth-bot-deployed-logout.PNG" alt-text="Esta captura de tela mostra como inserir o logout para sair.":::

> [!NOTE]
> Se estiver tendo problemas para entrar, tente testar a conexão novamente conforme descrito nas etapas anteriores. É possível que isso recrie o token de autenticação.
> Com o cliente de Chat na Web do Bot Framework no Azure talvez seja necessário entrar várias vezes antes de a autenticação ser estabelecida corretamente.

## <a name="install-and-test-the-bot-in-teams"></a>Instalar e testar o bot no Teams

1. No seu projeto de bot, verifique se a pasta `TeamsAppManifest` contém `manifest.json` juntamente com os arquivos `outline.png` e `color.png`.
1. Em Gerenciador de Soluções, vá para a `TeamsAppManifest` pasta. Edite `manifest.json` atribuindo os seguintes valores:
    1. Certifique-se de que a **ID do aplicativo de bot** recebida no momento do registro do bot foi atribuída a `id` e `botId`.
    1. Atribua o valor: `validDomains: [ "token.botframework.com" ]`.
1. Selecione e **zipe** os arquivos `manifest.json`, `outline.png` e `color.png`.
1. Abra o **Microsoft Teams**.
1. No painel esquerdo, na parte de baixo, selecione o **Ícone de aplicativos**.
1. No painel direito, na parte de baixo, selecione **Carregar um aplicativo personalizado**.
1. Vá para a pasta `TeamsAppManifest` e carregue o manifesto compactado.
O seguinte assistente é exibido:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-teams-upload.png" alt-text="Esta captura de tela mostra um exemplo do bot depois que ele é carregado no Teams.":::

1. Selecione o botão **Adicionar a uma equipe**.
1. Na próxima janela, selecione a equipe na qual você deseja usar o bot.
1. Selecione o botão **Configurar um bot**.
1. Selecione os três pontos (&#x25cf;&#x25cf;&#x25cf;) no painel esquerdo. Em seguida, selecione **o ícone do Portal do** Desenvolvedor.
1. Selecione a guia **Editor do manifesto**. Você deverá ver o ícone do bot que você carregou.
1. Além disso, você deve conseguir ver o bot listado como um contato na lista de chats que você pode usar para trocar mensagens com o bot.

### <a name="testing-the-bot-locally-in-teams"></a>Testar o bot localmente no Teams

O Teams é um produto totalmente baseado em nuvem, ele requer que todos os serviços que acessam sejam disponibilizados na nuvem usando pontos de extremidade HTTPS. Portanto, para habilitar o bot (nossa amostra) e permitir que funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar uma instância em execução local acessível externamente por meio de uma ferramenta de **criação de túnel**. Recomendamos o [ngrok](https://ngrok.com/download), que cria um URL endereçável externamente para uma porta que você abre localmente no seu computador.
Para configurar o ngrok em preparação para executar seu aplicativo teams localmente, siga estas etapas:

1. Em uma janela do terminal, vá para o diretório onde você instalou o `ngrok.exe`. Sugerimos que você configure o caminho da *variável de ambiente* apontando para ele.
1. Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978`. Substitua o número da porta conforme necessário.
Isso irá iniciar o ngrok e fazer com que escute na porta que você especificar. Em troca, ele irá lhe fornecer um URL endereçável externamente e válido enquanto o ngrok estiver em execução. A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-ngrok-start.PNG" alt-text="Esta captura de tela mostra a cadeia de conexão de autenticação do aplicativo bot do Teams adv1":::

1. Copie o endereço de encaminhamento em HTTPS. Deve se parecer com o seguinte: `https://dea822bf.ngrok.io/`.
1. Acrescente `/api/messages` para obter `https://dea822bf.ngrok.io/api/messages`. Esse é o **ponto de extremidade de** mensagens para o bot em execução localmente em seu computador e acessível pela Web em um chat no Teams.
1. Uma etapa final a ser executada é atualizar o ponto de extremidade de mensagens do bot implantado. No exemplo, implantamos o bot no Azure. Portanto, vamos executar as seguintes etapas:
    1. No navegador, vá para o [**portal do Azure**][azure-portal].
    1. Selecione seu **Registro de Bots**.
    1. No painel esquerdo, selecione **Configurações**.
    1. No painel direito, na caixa **Ponto de extremidade de mensagens**, digite o URL do ngrok: no nosso exemplo, `https://dea822bf.ngrok.io/api/messages`.
1. Inicie seu bot localmente, por exemplo, no modo de depuração do Visual Studio.
1. Teste o bot durante a execução local usando o **Web chat de teste** do portal do Bot Framework. Como ocorre com o Emulador, esse teste não permite que você acesse uma funcionalidade específica do Teams.
1. Na janela do terminal onde o `ngrok` está em execução, você pode ver o tráfego HTTP entre o bot e o cliente de web chat. Se quiser uma visualização mais detalhada, digite em uma janela do navegador o `http://127.0.0.1:4040` que você obteve na janela anterior do terminal. A imagem a seguir é um exemplo:

   :::image type="content" source="../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png" alt-text="Esta captura de tela mostra o teste de ngrok das equipes de bot de autenticação.":::

> [!NOTE]
> Se você parar e reiniciar o ngrok, o URL será alterado. Para usar o ngrok no seu projeto e dependendo dos recursos que estiver usando, você precisará atualizar todas as referências de URL.

## <a name="additional-information"></a>Informações adicionais

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Este manifesto contém as informações necessárias para que o Teams se conecte ao bot:  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0.0",
  "id": "",
  "developer": {
    "name": "TeamsBotAuth",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.teams.com/privacy",
    "termsOfUseUrl": "https://www.teams.com/termsofuse"
  },
  "icons": {
    "color": "color.png",
    "outline": "outline.png"
  },
  "name": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "description": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "accentColor": "#FFFFFF",
  "bots": [
    {
      "botId": "",
      "scopes": [
        "groupchat",
        "team"
      ],
      "supportsFiles": false,
      "isNotificationOnly": false
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [ "token.botframework.com" ]
}
```

Com a autenticação, o Teams se comporta um pouco diferente dos outros canais, conforme explicado abaixo.

### <a name="handling-invoke-activity"></a>Como lidar com a Atividade de Invocação

Uma **Atividade de Invocação** é enviada ao bot, em vez da Atividade de Evento usada por outros canais.
Isso é feito por meio da subclassificação do **ActivityHandler**.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-sample)

**Bots/DialogBot.cs**

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

**Bots/TeamsBot.cs**

A *Atividade de Invocação* precisará ser encaminhada para a caixa de diálogo se o **OAuthPrompt** estiver sendo usado.

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a>TeamsActivityHandler.cs

```csharp

protected virtual Task OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    switch (turnContext.Activity.Name)
    {
        case "signin/verifyState":
            return OnSigninVerifyStateAsync(turnContext, cancellationToken);

        default:
            return Task.CompletedTask;
    }
}

protected virtual Task OnSigninVerifyStateAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    return Task.CompletedTask;
}
```

# <a name="javascript"></a>[JavaScript](#tab/node-js-dialog-sample)

**bots/dialogBot.js**

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

**bots/teamsBot.js**

A *Atividade de Invocação* precisará ser encaminhada para a caixa de diálogo se o **OAuthPrompt** estiver sendo usado.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**dialogs/mainDialog.js**

Em uma etapa de diálogo, use `beginDialog` para iniciar o prompt OAuth, que solicita o login do usuário.

- Se o usuário já estiver conectado, isso irá gerar um evento de resposta do token sem a solicitação ao usuário.
- Caso contrário, o usuário será solicitado a entrar. O Serviço de Bot do Azure envia o evento de resposta do token após a tentativa de login do usuário.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Na etapa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior. Se não for nulo, o usuário entrou com êxito.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

A *Atividade de Invocação* precisará ser encaminhada para a caixa de diálogo se o **OAuthPrompt** estiver sendo usado.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**dialogs/main_dialog.py**

Em uma etapa de diálogo, use `begin_dialog` para iniciar o prompt OAuth, que solicita o login do usuário.

- Se o usuário já estiver conectado, isso irá gerar um evento de resposta do token sem a solicitação ao usuário.
- Caso contrário, o usuário será solicitado a entrar. O Serviço de Bot do Azure envia o evento de resposta do token após a tentativa de login do usuário.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Na etapa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior. Se não for nulo, o usuário entrou com êxito.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**dialogs/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

## <a name="code-sample"></a>Exemplo de código

Esta seção fornece um exemplo de SDK de autenticação de bot v3.

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Autenticação de bot | Este exemplo mostra como começar a usar a autenticação em um bot para o Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| SSO de guia, bot e extensão de mensagem (ME) | Este exemplo mostra o SSO para Tab, Bot e ME – pesquisa, ação, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Não disponível |

## <a name="see-also"></a>Confira também

[Adicionar autenticação por meio do Serviço de Bot do Azure](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: /azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: /azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: /azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: /azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth
