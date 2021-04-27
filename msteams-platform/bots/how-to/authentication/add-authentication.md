---
title: Adicionar autenticação ao bot do Teams
author: clearab
description: Como adicionar autenticação OAuth a um bot no Microsoft Teams.
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: d54d7fadb13626bb38de3a907b966f026cc6c485
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020945"
---
# <a name="add-authentication-to-your-teams-bot"></a>Adicionar autenticação ao bot do Teams

Há momentos em que você pode precisar criar bots no Microsoft Teams que podem acessar recursos em nome do usuário, como um serviço de email.

Este artigo demonstra como usar a autenticação do Azure Bot Service v4 SDK, com base no OAuth 2.0. Isso facilita o desenvolvimento de um bot que pode usar tokens de autenticação com base nas credenciais do usuário. A chave em tudo isso é o uso de **provedores de identidade**, como veremos mais adiante.

O OAuth 2.0 é um padrão aberto para autenticação e autorização usadas pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.

Consulte [OAuth 2 Simplificado para](https://aka.ms/oauth2-simplified) um entendimento básico e [OAuth 2.0](https://oauth.net/2/) para a especificação completa.

Para obter mais informações sobre como o Serviço de Bot do Azure lida com a autenticação, consulte [Autenticação do usuário em uma conversa](https://aka.ms/azure-bot-authentication).

Neste artigo, você aprenderá:

- **Como criar um bot habilitado para autenticação.** Você usará [o cs-auth-sample][teams-auth-bot-cs] para manipular as credenciais de login do usuário e a geração do token de autenticação.
- **Como implantar o bot no Azure e associá-lo a um provedor de identidade.** O provedor emite um token com base nas credenciais de login do usuário. O bot pode usar o token para acessar recursos, como um serviço de email, que exige autenticação. Para obter mais informações,  [consulte Fluxo de autenticação do Microsoft Teams para bots](auth-flow-bot.md).
- **Como integrar o bot ao Microsoft Teams**. Depois que o bot tiver sido integrado, você poderá entrar e trocar mensagens com ele em um chat.

## <a name="prerequisites"></a>Pré-requisitos

- Conhecimento de [noções básicas do bot,][concept-basics] [estado de][concept-state]gerenciamento, biblioteca [de caixas][concept-dialogs]de diálogo e como implementar o fluxo de conversa [sequencial.][simple-dialog]
- Conhecimento do desenvolvimento do Azure e do OAuth 2.0.
- As versões atuais de Visual Studio e Git.
- Conta do Azure. Se necessário, você pode criar uma conta gratuita [do Azure.](https://azure.microsoft.com/free/)
- O exemplo a seguir.

    | Amostra | Versão botBuilder | Demonstra |
    |:---|:---:|:---|
    | **Autenticação bot** [em cs-auth-sample][teams-auth-bot-cs] | v4 | Suporte ao OAuthCard |
    | **Autenticação bot** [no js-auth-sample][teams-auth-bot-js] | v4| Suporte ao OAuthCard  |
    | **Autenticação bot** [em py-auth-sample][teams-auth-bot-py] | v4 | Suporte ao OAuthCard |

## <a name="create-the-resource-group"></a>Criar o grupo de recursos

O grupo de recursos e o plano de serviço não são estritamente necessários, mas permitem que você libere convenientemente os recursos que você criar. Essa é uma boa prática para manter seus recursos organizados e gerenciáveis.

Você usa um grupo de recursos para criar recursos individuais para a Estrutura de Bots. Para desempenho, verifique se esses recursos estão localizados na mesma região do Azure.

1. No navegador, entre no [**portal do Azure.**][azure-portal]
1. No painel de navegação esquerdo, selecione **Grupos de recursos**.
1. No canto superior esquerdo da janela exibida, selecione **Adicionar** guia para criar um novo grupo de recursos. Você será solicitado a fornecer o seguinte:
    1. **Assinatura**. Use sua assinatura existente.
    1. **Grupo de recursos**. Insira o nome do grupo de recursos. Um exemplo pode ser  *TeamsResourceGroup*. Lembre-se de que o nome deve ser exclusivo.
    1. No menu **suspenso** Região, selecione *Oeste dos EUA* ou uma região próxima aos seus aplicativos.
    1. Selecione o **botão Revisar e** criar. Você deve ver um banner que lê *Validação passada*.
    1. Selecione o **botão Criar.** Pode levar alguns minutos para criar o grupo de recursos.

> [!TIP]
> Assim como com os recursos que você criará mais adiante neste tutorial, é uma boa ideia fixar esse grupo de recursos em seu painel para facilitar o acesso. Se você quiser fazer isso, selecione o ícone de pino &#128204; no canto superior direito do painel.

## <a name="create-the-service-plan"></a>Criar o plano de serviço

1. No portal [**do Azure**][azure-portal], no painel de navegação esquerdo, selecione **Criar um recurso**.
1. Na caixa de pesquisa, digite *Plano de Serviço de Aplicativo*. Selecione o **cartão Plano de Serviço de Aplicativo** nos resultados da pesquisa.
1. Selecione **Criar**.
1. Você será solicitado a fornecer as seguintes informações:
    1. **Assinatura**. Você pode usar uma assinatura existente.
    1. **Grupo de Recursos**. Selecione o grupo criado anteriormente.
    1. **Nome**. Insira o nome do plano de serviço. Um exemplo pode ser  *TeamsServicePlan*. Lembre-se de que o nome deve ser exclusivo, dentro do grupo.
    1. **Sistema Operacional**. Selecione *Windows* ou seu sistema operacional aplicável.
    1. **Região**. Selecione *Oeste dos EUA* ou uma região próxima aos seus aplicativos.
    1. **Camada de preços**. Certifique-se *de que o Padrão S1* está selecionado. Esse deve ser o valor padrão.
    1. Selecione o **botão Revisar e** criar. Você deve ver um banner que lê *Validação passada*.
    1. Selecione **Criar**. Pode levar alguns minutos para criar o plano de serviço do aplicativo. O plano será listado no grupo de recursos.

## <a name="create-the-bot-channels-registration"></a>Criar o registro de canais bot

O registro de canais de bot registra seu serviço Web como um bot com a Estrutura de Bot, desde que você tenha uma ID do Aplicativo microsoft e senha do aplicativo (segredo do cliente).

> [!IMPORTANT]
> Você só precisará registrar seu bot se ele não estiver hospedado no Azure. Se você [criou um bot por](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) meio do portal do Azure, ele já está registrado com o serviço. Se você criou seu bot por meio da [Estrutura de Bot](https://dev.botframework.com/bots/new) ou [AppStudio,](~/concepts/build-and-test/app-studio-overview.md) seu bot não está registrado no Azure.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> O recurso Registro de Canais de Bot mostrará a **região Global** mesmo se você tiver selecionado o Oeste dos EUA. Isso é esperado.

Para obter mais informações, [consulte Create a bot for Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Criar o provedor de identidade

Você precisa de um provedor de identidade que possa ser usado para autenticação.
Neste procedimento, você usará um provedor do Azure AD; outros provedores de identidade com suporte do Azure AD também podem ser usados.

1. No portal [**do Azure**][azure-portal], no painel de navegação esquerdo, selecione **Azure Active Directory**.
    > [!TIP]
    > Você precisará criar e registrar esse recurso do Azure AD em um locatário no qual você pode autorizar a delegação de permissões solicitadas por um aplicativo.
    > Para instruções sobre como criar um locatário, [consulte Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. No painel esquerdo, selecione **Registros de aplicativo .**
1. No painel direito, selecione a guia **Novo registro,** no canto superior esquerdo.
1. Você será solicitado a fornecer as seguintes informações:
   1. **Nome**. Insira o nome do aplicativo. Um exemplo pode ser  *BotTeamsIdentity*. Lembre-se de que o nome deve ser exclusivo.
   1. Selecione os **tipos de conta com suporte** para seu aplicativo. Selecione Contas em qualquer diretório organizacional (Qualquer diretório *do Azure AD - Multitenant) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.
   1. Para o **URI de redirecionamento**:<br/>
       &#x2713;Selecione **Web**. <br/>
       &#x2713; definir a URL como `https://token.botframework.com/.auth/web/redirect` .
   1. Selecione **Registrar**.

1. Depois de criado, o Azure exibe a página **Visão** Geral do aplicativo. Copie e salve as seguintes informações em um arquivo:

    1. O **valor da ID do aplicativo (cliente).** Você usará esse valor posteriormente como a *ID do* Cliente quando registrar esse aplicativo de identidade do Azure com seu bot.
    1. O valor da ID do Diretório **(locatário).** Você também usará esse valor posteriormente como a ID do *Locatário* para registrar esse aplicativo de identidade do Azure com seu bot.

1. No painel esquerdo, selecione **Certificados & segredos para** criar um segredo do cliente para seu aplicativo.

   1. Em **Segredos do cliente,** selecione &#x2795; **Novo segredo do cliente.**
   1. Adicione uma descrição para identificar esse segredo de outras pessoas que você pode precisar criar para este aplicativo, como *o aplicativo de identidade bot no Teams*.
   1. Set **Expires** to your selection.
   1. Selecione **Adicionar**.
   1. Antes de sair desta página, **grave o segredo**. Você usará esse valor posteriormente como o _segredo do cliente_ ao registrar seu aplicativo do Azure AD com seu bot.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Configurar a conexão do provedor de identidade e registrá-la com o bot

Observação: há duas opções para Provedores de Serviços aqui-Azure AD V1 e Azure AD V2.  As diferenças entre os dois provedores são resumidas [aqui](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), mas, em geral, a V2 oferece mais flexibilidade em relação à alteração de permissões de bot.  As permissões de API do Graph são listadas no campo escopos e, à medida que novas são adicionadas, os bots permitirão que os usuários consentam com as novas permissões na próxima vez em que entrar.  Para V1, o consentimento do bot deve ser excluído pelo usuário para que novas permissões sejam solicitados na caixa de diálogo OAuth. 

#### <a name="azure-ad-v1"></a>Azure AD V1

1. No [**portal do Azure,**][azure-portal]selecione seu grupo de recursos no painel.
1. Selecione o link de registro do canal bot.
1. Na página recurso, selecione **Configurações**.
1. Em **Configurações de Conexão OAuth próximas** à parte inferior da página, selecione **Adicionar Configuração**.
1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome**. Insira um nome para a conexão. Você usará esse nome em seu bot no `appsettings.json` arquivo. Por *exemplo, BotTeamsAuthADv1*.
    1. **Provedor de Serviços**. Selecione **Azure Active Directory**. Depois de selecionar isso, os campos específicos do Azure AD serão exibidos.
    1. **ID do cliente**. Insira a ID de aplicativo (cliente) que você gravou para seu aplicativo provedor de identidade do Azure nas etapas acima.
    1. **Segredo do cliente**. Insira o segredo que você gravou para seu aplicativo provedor de identidade do Azure nas etapas acima.
    1. **Tipo de concessão**. Insira `authorization_code` .
    1. **URL de logon**. Insira `https://login.microsoftonline.com` .
    1. **ID do** locatário , insira a ID de Diretório **(locatário)** que você gravou anteriormente para seu aplicativo de identidade do Azure ou **comum,** dependendo do tipo de conta com suporte selecionado ao criar o aplicativo do provedor de identidade. Para decidir qual valor atribuir siga estes critérios:

        - Se você selecionou contas somente neste diretório organizacional *(somente Microsoft -* Locatário único) ou Contas em qualquer diretório organizacional *(diretório Microsoft AAD - Multi locatário)* insira a **ID** de locatário que você gravou anteriormente para o aplicativo AAD. Esse será o locatário associado aos usuários que podem ser autenticados.

        - Se você selecionou Contas em qualquer diretório organizacional (qualquer diretório AAD - Contas da Microsoft de vários locatários e pessoais, por *exemplo, Skype, Xbox, Outlook)* insira a palavra **comum** em vez de uma ID de locatário. Caso contrário, o aplicativo AAD verificará por meio do locatário cuja ID foi selecionada e excluirá contas pessoais da Microsoft.

    h. Para **URL do Recurso,** insira `https://graph.microsoft.com/` . Isso não é usado no exemplo de código atual.  
    i. Deixar **escopos em** branco. A imagem a seguir é um exemplo:

    ![teams bots app auth connection adv1 view](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Selecione **Salvar**.

#### <a name="azure-ad-v2"></a>Azure AD V2

1. No [**portal do Azure,**][azure-portal]selecione seu grupo de recursos no painel.
1. Selecione o link de registro do canal bot.
1. Na página recurso, selecione **Configurações**.
1. Em **Configurações de Conexão OAuth próximas** à parte inferior da página, selecione **Adicionar Configuração**.
1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome**. Insira um nome para a conexão. Você usará esse nome em seu bot no `appsettings.json` arquivo. Por *exemplo, BotTeamsAuthADv2*.
    1. **Provedor de Serviços**. Selecione **Azure Active Directory v2**. Depois de selecionar isso, os campos específicos do Azure AD serão exibidos.
    1. **ID do cliente**. Insira a ID de aplicativo (cliente) que você gravou para seu aplicativo provedor de identidade do Azure nas etapas acima.
    1. **Segredo do cliente**. Insira o segredo que você gravou para seu aplicativo provedor de identidade do Azure nas etapas acima.
    1. **URL do Exchange de tokens**. Deixe isso em branco.
    1. **ID do** locatário , insira a ID de Diretório **(locatário)** que você gravou anteriormente para seu aplicativo de identidade do Azure ou **comum,** dependendo do tipo de conta com suporte selecionado ao criar o aplicativo do provedor de identidade. Para decidir qual valor atribuir siga estes critérios:

        - Se você selecionou contas somente neste diretório organizacional *(somente Microsoft -* Locatário único) ou Contas em qualquer diretório organizacional *(diretório Microsoft AAD - Multi locatário)* insira a **ID** de locatário que você gravou anteriormente para o aplicativo AAD. Esse será o locatário associado aos usuários que podem ser autenticados.

        - Se você selecionou Contas em qualquer diretório organizacional (qualquer diretório AAD - Contas da Microsoft de vários locatários e pessoais, por *exemplo, Skype, Xbox, Outlook)* insira a palavra **comum** em vez de uma ID de locatário. Caso contrário, o aplicativo AAD verificará por meio do locatário cuja ID foi selecionada e excluirá contas pessoais da Microsoft.

    1. Para **Escopos,** insira uma lista delimitada por espaço de permissões gráficas que este aplicativo exige, por exemplo: User.Read User.ReadBasic.All Mail.Read 

1. Selecione **Salvar**.

### <a name="test-the-connection"></a>Testar a conexão

1. Selecione a entrada de conexão para abrir a conexão que você acabou de criar.
1. Selecione **Conexão de Teste** na parte superior do painel Configuração de Conexão do Provedor **de** Serviços.
1. A primeira vez que você fizer isso abrirá uma nova janela do navegador solicitando que você selecione uma conta. Selecione o que você deseja usar.
1. Em seguida, você será solicitado a permitir que o provedor de identidade use seus dados (credenciais). A imagem a seguir é um exemplo:

    ![teams bot auth connection adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Selecione **Aceitar**.
1. Em seguida, você deve redirecionar para uma página Conexão de Teste **\<your-connection-name> para Êxito.** Atualize a página se você receber um erro. A imagem a seguir é um exemplo:

  ![teams bots app auth connection str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

O nome da conexão é usado pelo código bot para recuperar tokens de autenticação do usuário.

## <a name="prepare-the-bot-sample-code"></a>Preparar o código de exemplo do bot

Com as configurações preliminares feitas, vamos nos concentrar na criação do bot a ser usado neste artigo.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. Clone [cs-auth-sample][teams-auth-bot-cs].
1. Iniciar Visual Studio.
1. Na barra de ferramentas, selecione **Arquivo -> Abrir -> Project/Solution** e abra o projeto bot.
1. Em C# Atualizar **appsettings.json** da seguinte forma:

    - De `ConnectionName` acordo com o nome da conexão do provedor de identidade que você adicionou ao registro do canal bot. O nome usado neste exemplo é *BotTeamsAuthADv1*.
    - De `MicrosoftAppId` acordo com a **ID do** aplicativo bot que você salvou no momento do registro do canal bot.
    - De `MicrosoftAppPassword` acordo com o segredo do **cliente** salvo no momento do registro do canal bot.

    Dependendo dos caracteres em seu segredo de bot, talvez seja necessário que XML escape da senha. Por exemplo, qualquer ampersands (&) precisará ser codificado como `&amp;` .

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. No Explorador de Soluções, navegue até a pasta, abra e desem conjunto e até a ID do aplicativo de bot que você salvou no momento do registro do canal `TeamsAppManifest` `manifest.json` `id` `botId` bot. 

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Clone [node-auth-sample][teams-auth-bot-js].
1. Em um console, navegue até o projeto: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Instalar módulos</br></br>
`npm install`
1. Atualize a **configuração .env** da seguinte forma:

    - De `MicrosoftAppId` acordo com a **ID do** aplicativo bot que você salvou no momento do registro do canal bot.
    - De `MicrosoftAppPassword` acordo com o segredo do **cliente** salvo no momento do registro do canal bot.
    - De definir `connectionName` o para o nome da conexão do provedor de identidade.
    Dependendo dos caracteres em seu segredo de bot, talvez seja necessário que XML escape da senha. Por exemplo, qualquer ampersands (&) precisará ser codificado como `&amp;` .

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Na `teamsAppManifest` pasta, abra e desacordo para sua ID do Microsoft App e para a ID do aplicativo de bot que você salvou no momento do registro do canal `manifest.json` `id`  `botId` bot. 

# <a name="python"></a>[Python](#tab/python)

1. Clone [py-auth-sample][teams-auth-bot-py] do repositório github.
1. Atualizar **config.py**:

    - De `ConnectionName` acordo com o nome da configuração de conexão OAuth adicionada ao bot.
    - Definir `MicrosoftAppId` e para a `MicrosoftAppPassword` ID do aplicativo do bot e o segredo do aplicativo.

      Dependendo dos caracteres em seu segredo de bot, talvez seja necessário que XML escape da senha. Por exemplo, qualquer ampersands (&) precisará ser codificado como `&amp;` .

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Implantar o bot no Azure

Para implantar o bot, siga as etapas em como [implantar seu bot no Azure](https://aka.ms/azure-bot-deployment-cli).

Como alternativa, enquanto estiver Visual Studio, você pode seguir estas etapas:

1. Em Visual Studio *Solution Explorer* selecione e segure (ou clique com o botão direito do mouse) no nome do projeto.
1. No menu suspenso, selecione **Publicar**.
1. Na janela exibida, selecione o **link Novo.**
1. Na janela de diálogo, selecione **Serviço de Aplicativo** à esquerda e Criar **Novo** à direita.
1. Selecione o **botão Publicar.**
1. Na próxima janela de diálogo, insira as informações necessárias. Veja um exemplo a seguir:

   ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Selecione **Criar**.
1. Se a implantação for concluída com êxito, você deverá vê-la refletida Visual Studio. Além disso, uma página é exibida no navegador padrão dizendo *que Seu bot está pronto!*. A URL será semelhante a esta: `https://botteamsauth.azurewebsites.net/` . Salve-o em um arquivo.
1. No navegador, navegue até o [**portal do Azure.**][azure-portal]
1. Verifique seu grupo de recursos, o bot deve ser listado junto com os outros recursos. A imagem a seguir é um exemplo:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. No grupo de recursos, selecione o nome de registro do canal bot (link).
1. No painel esquerdo, selecione **Configurações**.
1. Na caixa **Ponto de extremidade Mensagens,** insira a URL obtida acima seguida de `api/messages` . Este é um exemplo: `https://botteamsauth.azurewebsites.net/api/messages` .
1. Selecione o **botão Salvar** no canto superior esquerdo.

## <a name="test-the-bot-using-the-emulator"></a>Testar o bot usando o Emulador

Se você ainda não fez isso, instale o [Emulador](https://aka.ms/bot-framework-emulator-readme)da Estrutura do Microsoft Bot. Consulte também [Depurar com o Emulador](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Para que o logon de exemplo de bot funcione, você deve configurar o Emulador conforme mostrado abaixo.

### <a name="configure-the-emulator-for-authentication"></a>Configurar o Emulador para autenticação

Se um bot exigir autenticação, você deve configurar o Emulador conforme mostrado abaixo.

1. Inicie o Emulador.
1. No Emulador, selecione o ícone de engrenagem &#9881; na parte inferior esquerda ou a guia Configurações do **Emulador** no canto superior direito.
1. Marque a caixa por **Usar tokens de autenticação versão 1.0**.
1. Insira o caminho local para a **ferramenta ngrok.** *Consulte* o Emulador de Estrutura de Bot/integração de túnel ngrok [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)). Para obter mais informações sobre a ferramenta, consulte [ngrok](https://ngrok.com/).
1. Marque a caixa por **Executar ngrok quando o Emulador for iniciado**.
1. Selecione o **botão Salvar.**

Quando o bot exibe um cartão de login e o usuário seleciona o botão de login, o Emulador abre uma página que o usuário pode usar para entrar com o provedor de autenticação.
Depois que o usuário faz isso, o provedor gera um token de usuário e o envia para o bot. Depois disso, o bot pode agir em nome do usuário.

### <a name="test-the-bot-locally"></a>Testar o bot localmente

Depois de configurar o mecanismo de autenticação, você poderá executar o teste de bot real.  

1. Execute o exemplo de bot localmente em seu computador, por Visual Studio por exemplo.
1. Inicie o Emulador.
1. Selecione o **botão Abrir bot.**
1. Na **URL do Bot,** insira a URL local do bot. Normalmente, `http://localhost:3978/api/messages` .
1. Na **ID do Microsoft App,** insira a ID do aplicativo do bot de `appsettings.json` .
1. Na senha **do Microsoft App,** insira a senha do aplicativo do bot a partir do `appsettings.json` .
1. Selecione **Conectar**.
1. Depois que o bot está em execução, insira qualquer texto para exibir o cartão de entrada.
1. Selecione o **botão Entrar.**
1. Uma caixa de diálogo pop-up é exibida para **Confirmar URL aberta**. Isso é para permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta do usuário aplicável.
1. Dependendo da configuração usada para o Emulador, você obterá um dos seguintes:
    1. **Usando o código de verificação de login**  
      &#x2713; Uma janela é aberta exibindo o código de validação.  
      &#x2713; copie e insira o código de validação na caixa de chat para concluir a entrada.
    1. **Usando tokens de autenticação**.  
      &#x2713; Você está conectado com base em suas credenciais.

    A imagem a seguir é um exemplo da interface do usuário do bot depois que você fez logor:

    ![emulador de logon de bot de auth](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Se você selecionar **Sim** quando o bot perguntar Você gostaria de exibir *seu token?*, você obterá uma resposta semelhante à seguinte:

    ![Token do emulador de logon do bot de auth](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Insira **logout** na caixa de chat de entrada para sair. Isso libera o token de usuário, e o bot não poderá agir em seu nome até que você entre novamente.

> [!NOTE]
> A autenticação bot requer o uso do **Serviço de Conector de Bot.** O serviço acessa as informações de registro de canais bots para seu bot.

## <a name="test-the-deployed-bot"></a>Testar o bot implantado

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. No navegador, navegue até o [**portal do Azure.**][azure-portal]
1. Encontre seu grupo de recursos.
1. Selecione o link de recurso. A página de recursos é exibida.
1. Na página de recursos, selecione **Testar no Chat da Web.** O bot inicia e exibe as saudações predefinida.
1. Digite qualquer coisa na caixa de chat.
1. Selecione a **caixa Entrar.**
1. Uma caixa de diálogo pop-up é exibida para **Confirmar URL aberta**. Isso é para permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta do usuário aplicável.
    A imagem a seguir é um exemplo da interface do usuário do bot depois que você fez logor:

    ![Logon de bot de auth implantado](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Selecione o **botão Sim** para exibir seu token de autenticação. A imagem a seguir é um exemplo:

    ![Token implantado de logon de bot de auth](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Insira logout para sair.

    ![logout implantado do bot de auth](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Se você estiver com problemas para entrar, tente testar a conexão novamente, conforme descrito nas etapas anteriores. Isso pode recriar o token de autenticação.
> Com o cliente de Web Chat da Estrutura de Bots no Azure, talvez seja necessário entrar várias vezes antes que a autenticação seja estabelecida corretamente.

## <a name="install-and-test-the-bot-in-teams"></a>Instalar e testar o bot no Teams

1. Em seu projeto de bot, certifique-se de que a `TeamsAppManifest` pasta contém o junto com um e `manifest.json` `outline.png` `color.png` arquivos.
1. No Explorador de Soluções, navegue até a `TeamsAppManifest` pasta. Edite `manifest.json` atribuindo os seguintes valores:
    1. Verifique se a **ID do aplicativo** bot que você recebeu no momento em que o registro do canal bot está atribuído `id` e `botId` .
    1. Atribua esse valor: `validDomains: [ "token.botframework.com" ]` .
1. Selecione e **feche os** arquivos `manifest.json` , `outline.png` `color.png` e.
1. Abra **o Microsoft Teams**.
1. No painel esquerdo, na parte inferior, selecione o ícone **Aplicativos**.
1. No painel direito, na parte inferior, selecione **Carregar um aplicativo personalizado**.
1. Navegue até `TeamsAppManifest` a pasta e carregue o manifesto de zipped.
O assistente a seguir é exibido:

    ![upload de equipes de bot de auth](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Selecione o botão **Adicionar a uma equipe**.
1. Na próxima janela, selecione a equipe onde você deseja usar o bot.
1. Selecione o **botão Configurar um bot.**
1. Selecione os três pontos (&#x25cf;&#x25cf;&#x25cf;) no painel esquerdo. Em seguida, selecione **o ícone do App Studio.**
1. Selecione a **guia Editor de** manifesto. Você deve ver o ícone do bot que você carregou.
1. Além disso, você deve ser capaz de ver o bot listado como um contato na lista de chat que você pode usar para trocar mensagens com o bot.

### <a name="testing-the-bot-locally-in-teams"></a>Testando o bot localmente no Teams

O Microsoft Teams é um produto totalmente baseado em nuvem, ele exige que todos os serviços que acessa sejam disponibilizados na nuvem usando pontos de extremidade HTTPS. Portanto, para permitir que o bot (nosso exemplo) funcione no Teams, você precisa publicar o código na nuvem  de sua escolha ou tornar uma instância em execução localmente acessível externamente por meio de uma ferramenta de túnel. Recomendamos  [ngrok](https://ngrok.com/download), que cria uma URL de endereço externo para uma porta que você abre localmente em seu computador.
Para configurar o ngrok em preparação para executar seu aplicativo do Microsoft Teams localmente, siga estas etapas:

1. Em uma janela de terminal, vá para o diretório onde `ngrok.exe` você instalou. Sugerimos definir o *caminho da variável do* ambiente para apontar para ele.
1. Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978` . Substitua o número da porta conforme necessário.
Isso inicia o ngrok para ouvir a porta especificada. Em troca, ele fornece uma URL que pode ser abordada externamente, válida enquanto o ngrok está em execução. A imagem a seguir é um exemplo:

    ![teams bot app auth connection adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Copie o endereço HTTPS de encaminhamento. Deve ser semelhante ao seguinte: `https://dea822bf.ngrok.io/` .
1. Anexar `/api/messages` para obter `https://dea822bf.ngrok.io/api/messages` . Este é o **ponto de extremidade de** mensagens para o bot que está sendo executado localmente em seu computador e acessível pela Web em um chat no Microsoft Teams.
1. Uma etapa final a executar é atualizar o ponto de extremidade de mensagens do bot implantado. No exemplo, implantamos o bot no Azure. Portanto, **vamos executar estas etapas:
    1. No navegador, navegue até o [**portal do Azure.**][azure-portal]
    1. Selecione seu **Registro de Canal bot.**
    1. No painel esquerdo, selecione **Configurações**.
    1. No painel direito, na caixa Ponto de extremidade **Mensagens,** insira a URL ngrok, em nosso exemplo, `https://dea822bf.ngrok.io/api/messages` .
1. Inicie seu bot localmente, por exemplo, Visual Studio modo de depuração.
1. Teste o bot durante a execução local usando o chat da Web de Teste do portal da Estrutura de **Bot.** Como o Emulador, esse teste não permite que você acesse a funcionalidade específica do Teams.
1. Na janela do terminal onde `ngrok` está sendo executado, você pode ver o tráfego HTTP entre o bot e o cliente de chat da Web. Se você quiser uma exibição mais detalhada, em uma janela do navegador insira `http://127.0.0.1:4040` você obtido na janela do terminal anterior. A imagem a seguir é um exemplo:

    ![Teste de ngrok de equipes de bot de auth](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será mudada. Para usar o ngrok em seu projeto e, dependendo dos recursos que você está usando, você deve atualizar todas as referências de URL.
 

## <a name="additional-information"></a>Informações adicionais

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Este manifesto contém informações necessárias para que o Microsoft Teams se conecte ao bot.  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0.0",
  "id": "",
  "packageName": "com.teams.auth.bot",
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

Com a autenticação, o Teams se comporta um pouco diferente de outros canais, conforme explicado a seguir.

### <a name="handling-invoke-activity"></a>Manipulando a atividade invocar

Uma **Atividade invocar** é enviada ao bot em vez da Atividade de Evento usada por outros canais.
Isso é feito sub-classificando **o ActivityHandler**.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-sample)

**Bots/DialogBot.cs**

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

**Bots/TeamsBot.cs**

A *Atividade de Invocação* deve ser encaminhada para a caixa de diálogo se **o OAuthPrompt** for usado.

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

A *Atividade de Invocação* deve ser encaminhada para a caixa de diálogo se **o OAuthPrompt** for usado.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**dialogs/mainDialog.js**

Em uma etapa de caixa de diálogo, use `beginDialog` para iniciar o prompt OAuth, que pede ao usuário para entrar.

- Se o usuário já estiver assinado, isso gerará um evento de resposta de token, sem solicitar ao usuário.
- Caso contrário, isso solicitará que o usuário entre. O Serviço bot do Azure envia o evento de resposta de token após o usuário tentar entrar.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Na etapa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior. Se não for nulo, o usuário se inscreveu com êxito.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

A *Atividade de Invocação* deve ser encaminhada para a caixa de diálogo se **o OAuthPrompt** for usado.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**dialogs/main_dialog.py**

Em uma etapa de caixa de diálogo, use `begin_dialog` para iniciar o prompt OAuth, que pede ao usuário para entrar.

- Se o usuário já estiver assinado, isso gerará um evento de resposta de token, sem solicitar ao usuário.
- Caso contrário, isso solicitará que o usuário entre. O Serviço bot do Azure envia o evento de resposta de token após o usuário tentar entrar.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Na etapa de diálogo a seguir, verifique a presença de um token no resultado da etapa anterior. Se não for nulo, o usuário se inscreveu com êxito.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**dialogs/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [Saiba mais sobre como adicionar autenticação por meio do Serviço de Bot do Azure](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
