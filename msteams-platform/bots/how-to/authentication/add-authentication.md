---
title: Adicione autenticação ao seu bot Teams
author: clearab
description: Como adicionar autenticação OAuth a um bot em Microsoft Teams.
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 36cb6f3de6f97af1d01512175923b79f69f630ad
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565941"
---
# <a name="add-authentication-to-your-teams-bot"></a>Adicione autenticação ao seu bot Teams

Há momentos em que você pode precisar criar bots em Microsoft Teams que podem acessar recursos em nome do usuário, como um serviço de correio.

Este artigo demonstra como usar a autenticação V4 SDK do Azure Bot Service, com base no OAuth 2.0. Isso torna mais fácil desenvolver um bot que pode usar tokens de autenticação com base nas credenciais do usuário. A chave em tudo isso é o uso de provedores de **identidade,** como veremos mais tarde.

O OAuth 2.0 é um padrão aberto para autenticação e autorização usadas pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Um entendimento básico do OAuth 2.0 é um pré-requisito para trabalhar com autenticação em Teams.

Consulte [OAuth 2 Simplificado](https://aka.ms/oauth2-simplified) para um entendimento básico e [OAuth 2.0](https://oauth.net/2/) para a especificação completa.

Para obter mais informações sobre como o Azure Bot Service lida com a autenticação, consulte [a autenticação do usuário dentro de uma conversa](https://aka.ms/azure-bot-authentication).

Neste artigo você aprenderá:

- **Como criar um bot habilitado para autenticação**. Você usará [cs-auth-sample][teams-auth-bot-cs] para lidar com credenciais de login do usuário e gerar o token de autenticação.
- **Como implantar o bot no Azure e associá-lo a um provedor de identidade**. O provedor emite um token com base em credenciais de login do usuário. O bot pode usar o token para acessar recursos, como um serviço de correio, que requerem autenticação. Para obter mais informações, consulte [Microsoft Teams fluxo de autenticação para bots](auth-flow-bot.md).
- **Como integrar o bot dentro de Microsoft Teams**. Uma vez que o bot tenha sido integrado, você pode fazer login e trocar mensagens com ele em um chat.

## <a name="prerequisites"></a>Pré-requisitos

- Conhecimento do básico do [bot,][concept-basics] [estado de gestão,][concept-state] [biblioteca de diálogos][concept-dialogs]e como [implementar fluxo de conversação sequencial][simple-dialog].
- Conhecimento do desenvolvimento do Azure e OAuth 2.0.
- As versões atuais de Visual Studio e Git.
- Conta azul. Se necessário, você pode criar uma [conta gratuita do Azure.](https://azure.microsoft.com/free/)
- A seguinte amostra:

    | Amostra | Versão BotBuilder | Demonstra |
    |:---|:---:|:---|
    | **Autenticação de bot** em [cs-auth-sample][teams-auth-bot-cs] | v4 | Suporte ao OAuthCard |
    | **Autenticação de bot** em [js-auth-sample][teams-auth-bot-js] | v4| Suporte ao OAuthCard  |
    | **Autenticação de bot** em [py-auth-sample][teams-auth-bot-py] | v4 | Suporte ao OAuthCard |

## <a name="create-the-resource-group"></a>Crie o grupo de recursos

O grupo de recursos e o plano de serviço não são estritamente necessários, mas permitem que você libere convenientemente os recursos que você cria. Esta é uma boa prática para manter seus recursos organizados e gerenciáveis.

Você usa um grupo de recursos para criar recursos individuais para o Bot Framework. Para desempenho, garanta que esses recursos estejam localizados na mesma região do Azure.

1. No seu navegador, entre no portal do [**Azure.**][azure-portal]
1. No painel de navegação à esquerda, selecione **Grupos de recursos**.
1. No canto superior esquerdo da janela exibida, selecione **Adicionar** guia para criar um novo grupo de recursos. Você será solicitado a fornecer o seguinte:
    1. **Assinatura**. Use sua assinatura existente.
    1. **Grupo de recursos**. Digite o nome do grupo de recursos. Um exemplo pode ser  *o TeamsResourceGroup*. Lembre-se que o nome deve ser único.
    1. No menu suspenso **da Região,** selecione *West US* ou uma região próxima às suas aplicações.
    1. Selecione o **botão Revisão e crie.** Você deve ver um banner que diz *validação passada*.
    1. Selecione o botão **Criar.** Pode levar alguns minutos para criar o grupo de recursos.

> [!TIP]
> Assim como com os recursos que você criará mais tarde neste tutorial, é uma boa ideia fixar esse grupo de recursos no seu painel para fácil acesso. Se quiser fazê-lo, selecione o ícone de pino &#128204; no canto superior direito do painel.

## <a name="create-the-service-plan"></a>Crie o plano de serviço

1. No [**portal Azure**][azure-portal], no painel de navegação à esquerda, selecione **Criar um recurso**.
1. Na caixa de pesquisa, digite *App Service Plan*. Selecione o cartão **App Service Plan** a partir dos resultados da pesquisa.
1. Selecione **Criar**.
1. Você será solicitado a fornecer as seguintes informações:
    1. **Assinatura**. Você pode usar uma assinatura existente.
    1. **Grupo de Recursos**. Selecione o grupo que você criou anteriormente.
    1. **Nome.** Digite o nome do plano de serviço. Um exemplo pode ser  *o TeamsServicePlan*. Lembre-se que o nome deve ser único, dentro do grupo.
    1. **Sistema Operacional**. Selecione *Windows* ou o sistema operacional aplicável.
    1. **Região**. Selecione *West US* ou uma região próxima às suas aplicações.
    1. **Nível de preços**. Certifique-se de que *o Standard S1* está selecionado. Este deve ser o valor padrão.
    1. Selecione o **botão Revisão e crie.** Você deve ver um banner que diz *validação passada*.
    1. Selecione **Criar**. Pode levar alguns minutos para criar o plano de serviço do aplicativo. O plano será listado no grupo de recursos.

## <a name="create-the-bot-channels-registration"></a>Crie o registro dos canais de bot

O registro de canais de bot registra seu serviço web como um bot com o Bot Framework, desde que você tenha uma senha de Aplicativo microsoft e app (segredo do cliente).

> [!IMPORTANT]
> Você só precisa registrar seu bot se ele não estiver hospedado no Azure. Se você [criou um bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) através do portal Azure, então ele já está cadastrado no serviço. Se você criou seu bot através do [Bot Framework](https://dev.botframework.com/bots/new) ou [AppStudio,](~/concepts/build-and-test/app-studio-overview.md) seu bot não está registrado no Azure.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> O recurso de registro de canais de bot mostrará a região **global** mesmo se você selecionou o Oeste dos EUA. Isso é esperado.

Para obter mais informações, consulte [Criar um bot para Teams](../create-a-bot-for-teams.md).

## <a name="create-the-identity-provider"></a>Crie o provedor de identidade

Você precisa de um provedor de identidade que possa ser usado para autenticação.
Neste procedimento, você usará um provedor de Azure AD; outros provedores de identidade suportados pelo Azure AD também podem ser usados.

1. No [**portal do Azure,**][azure-portal]no painel de navegação à esquerda, selecione **Azure Active Directory**.
    > [!TIP]
    > Você precisará criar e registrar este recurso Azure AD em um inquilino no qual você pode consentir em delegar permissões solicitadas por um aplicativo.
    > Para obter instruções sobre a criação de um inquilino, consulte [Acessar o portal e criar um inquilino](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).
1. No painel esquerdo, selecione **registros de aplicativos**.
1. No painel direito, selecione a guia **de registro Novo,** no canto superior esquerdo.
1. Você será solicitado a fornecer as seguintes informações:
   1. **Nome.** Digite o nome da inscrição. Um exemplo pode ser  *o BotTeamsIdentity*. Lembre-se que o nome deve ser único.
   1. Selecione os **tipos de conta suportada** para sua aplicação. Selecione *Contas em qualquer diretório organizacional (qualquer diretório de Azure AD - Multitenant) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.
   1. Para o **Redirecionamento URI**:<br/>
       &#x2713;Select **Web**. <br/>
       &#x2713; defina a URL para `https://token.botframework.com/.auth/web/redirect` .
   1. Selecione **Registrar**.

1. Uma vez criado, o Azure exibe a página **Visão Geral** do aplicativo. Copie e salve as seguintes informações em um arquivo:

    1. O valor **de ID do Aplicativo (cliente).** Você usará esse valor mais tarde como o *ID do Cliente* ao registrar este aplicativo de identidade Azure com o seu bot.
    1. O valor **de ID do Diretório (inquilino).** Você também usará esse valor mais tarde como o *ID do Inquilino* para registrar este aplicativo de identidade Azure com o seu bot.

1. No painel esquerdo, selecione **Certificados & segredos** para criar um segredo de cliente para sua aplicação.

   1. Em **segredos do Cliente,** selecione &#x2795; **novo segredo do cliente**.
   1. Adicione uma descrição para identificar esse segredo de outras pessoas que você pode precisar criar para este aplicativo, como *o aplicativo de identidade Bot em Teams*.
   1. O conjunto **expira** para sua seleção.
   1. Selecione **Adicionar**.
   1. Antes de sair desta página, **regisse o segredo.** Você usará esse valor mais tarde como o segredo do _Cliente_ quando registrar seu aplicativo Azure AD com seu bot.

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a>Configure a conexão do provedor de identidade e registre-a no bot

Nota- há duas opções para provedores de serviços aqui-Azure AD V1 e Azure AD V2.  As diferenças entre os dois provedores são resumidas [aqui,](/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)mas, em geral, a V2 fornece mais flexibilidade no que diz respeito à alteração das permissões de bots.  Graph As permissões de API são listadas no campo de escopos e, à medida que novas são adicionadas, os bots permitirão que os usuários consentam com as novas permissões no próximo login.  Para V1, o consentimento do bot deve ser excluído pelo usuário para que novas permissões sejam solicitadas na caixa de diálogo OAuth. 

#### <a name="azure-ad-v1"></a>Azure AD V1

1. No [**portal do Azure,**][azure-portal]selecione seu grupo de recursos no painel.
1. Selecione seu link de registro de canal de bot.
1. Abra a página de recursos e selecione **Configuração** em **Configurações**. 
1. Selecione **Adicionar Configurações de conexão OAuth**.    
A imagem a seguir exibe a seleção correspondente na página de recursos:  
![Configuração do SampleAppDemoBot](~/assets/images/authentication/sample-app-demo-bot-configuration.png)
1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome.** Digite um nome para a conexão. Você usará esse nome no seu bot no `appsettings.json` arquivo. Por exemplo, *BotTeamsAuthADv1*.
    1. **Prestador de Serviços**. Selecione **Azure Active Directory**. Uma vez selecionados, os campos específicos do Azure AD serão exibidos.
    1. **Id cliente**. Digite o ID do aplicativo (cliente) que você gravou para o seu aplicativo de provedor de identidade Azure nas etapas acima.
    1. **Segredo do cliente.** Digite o segredo que você gravou para o seu aplicativo de provedor de identidade Azure nas etapas acima.
    1. **Tipo de Subvenção**. Entre `authorization_code` .
    1. **URL de login**. Entre `https://login.microsoftonline.com` .
    1. **ID do inquilino**, digite o **ID do Diretório (inquilino)** que você gravou anteriormente para o seu aplicativo de identidade Azure ou **comum,** dependendo do tipo de conta suportada selecionada quando você criou o aplicativo do provedor de identidade. Para decidir qual valor atribuir siga esses critérios:

        - Se você selecionou contas *neste diretório organizacional apenas (apenas Microsoft - Único inquilino)* ou *Contas em qualquer diretório organizacional (diretório Microsoft AAD - Multi tenant)* digite o **ID do inquilino** que você gravou anteriormente para o aplicativo AAD. Este será o inquilino associado aos usuários que podem ser autenticados.

        - Se você selecionou *Contas em qualquer diretório organizacional (qualquer diretório AAD - Multi tenant e contas pessoais da Microsoft, por exemplo, Skype, Xbox, Outlook)* digite a palavra **comum** em vez de um ID de inquilino. Caso contrário, o aplicativo AAD verificará através do inquilino cujo ID foi selecionado e excluirá contas pessoais da Microsoft.

    h. Para **URL de recursos,** digite `https://graph.microsoft.com/` . Isso não é usado na amostra de código atual.  
    i. Deixe **scopes** em branco. A imagem a seguir é um exemplo:

    ![equipes bots app auth conexão adv1 visualização](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. Selecione **Salvar**.

#### <a name="azure-ad-v2"></a>Azure AD V2

1. No [**portal do Azure,**][azure-portal]selecione seu grupo de recursos no painel.
1. Selecione seu link de registro de canal de bot.
1. Abra a página de recursos e selecione **Configuração** em **Configurações**. 
1. Selecione **Adicionar Configurações de conexão OAuth**.  
A imagem a seguir exibe a seleção correspondente na página de recursos:        
![Configuração do SampleAppDemoBot](~/assets/images/authentication/sample-app-demo-bot-configuration.png) 

1. Preencha o formulário de acordo com as instruções a seguir:

    1. **Nome.** Digite um nome para a conexão. Você usará esse nome no seu bot no `appsettings.json` arquivo. Por exemplo, *BotTeamsAuthADv2*.
    1. **Prestador de Serviços**. Selecione **Azure Active Directory v2**. Uma vez selecionados, os campos específicos do Azure AD serão exibidos.
    1. **Id cliente**. Digite o ID do aplicativo (cliente) que você gravou para o seu aplicativo de provedor de identidade Azure nas etapas acima.
    1. **Segredo do cliente.** Digite o segredo que você gravou para o seu aplicativo de provedor de identidade Azure nas etapas acima.
    1. **URL de Exchange de token**. Deixe isso em branco.
    1. **ID do inquilino**, digite o **ID do Diretório (inquilino)** que você gravou anteriormente para o seu aplicativo de identidade Azure ou **comum,** dependendo do tipo de conta suportada selecionada quando você criou o aplicativo do provedor de identidade. Para decidir qual valor atribuir siga esses critérios:

        - Se você selecionou contas *neste diretório organizacional apenas (apenas Microsoft - Único inquilino)* ou *Contas em qualquer diretório organizacional (diretório Microsoft AAD - Multi tenant)* digite o **ID do inquilino** que você gravou anteriormente para o aplicativo AAD. Este será o inquilino associado aos usuários que podem ser autenticados.

        - Se você selecionou *Contas em qualquer diretório organizacional (qualquer diretório AAD - Multi tenant e contas pessoais da Microsoft, por exemplo, Skype, Xbox, Outlook)* digite a palavra **comum** em vez de um ID de inquilino. Caso contrário, o aplicativo AAD verificará através do inquilino cujo ID foi selecionado e excluirá contas pessoais da Microsoft.

    1. Para **escopos, insira** uma lista de permissões de gráficos delimitadas pelo espaço que este aplicativo requer, por exemplo: Usuário.Leia Usuário.ReadBasic.All Mail.Read 

1. Selecione **Salvar**.

### <a name="test-the-connection"></a>Teste a conexão

1. Selecione a entrada de conexão para abrir a conexão que você acabou de criar.
1. Selecione **Conexão de teste** na parte superior do painel Configuração de **conexão do provedor de serviços.**
1. A primeira vez que você fizer isso abrirá uma nova janela do navegador pedindo que você selecione uma conta. Selecione o que deseja usar.
1. Em seguida, você será solicitado a permitir que o provedor de identidade use seus dados (credenciais). A imagem a seguir é um exemplo:

    ![equipes bot auth conexão string adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. Selecione **Aceitar**.
1. Isso deve então redirecioná-lo para uma página **de teste para \<your-connection-name> sucesso.** Atualize a página se você tiver um erro. A imagem a seguir é um exemplo:

    ![equipes bots app auth conexão str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

O nome da conexão é usado pelo código do bot para recuperar tokens de autenticação do usuário.

## <a name="prepare-the-bot-sample-code"></a>Prepare o código de amostra do bot

Com as configurações preliminares feitas, vamos focar na criação do bot para usar neste artigo.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

1. Clone [cs-auth-sample][teams-auth-bot-cs].
1. Lançar Visual Studio.
1. Na barra de ferramentas selecione **Arquivo -> Abra -> Project/Solução** e abra o projeto bot.
1. Em C# Update **appsettings.jso** seguinte:

    - Defina `ConnectionName` o nome da conexão do provedor de identidade adicionada ao registro do canal bot. O nome que usamos neste exemplo é *BotTeamsAuthADv1*.
    - Definido `MicrosoftAppId` para o **iD do aplicativo bot** que você salvou no momento do registro do canal do bot.
    - Defina `MicrosoftAppPassword` o segredo do **cliente** que você salvou no momento do registro do canal bot.

    Dependendo dos caracteres do seu segredo de bot, você pode precisar de XML para escapar da senha. Por exemplo, quaisquer ampersands (&) precisarão ser codificados como `&amp;` .

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. No Solution Explorer, navegue até a `TeamsAppManifest` pasta, abra `manifest.json` e defina `id` e até `botId` o **ID do aplicativo bot** que você salvou no momento do registro do canal do bot.

# <a name="javascript"></a>[JavaScript](#tab/node-js)

1. Clone [node-auth-sample][teams-auth-bot-js].
1. Em um console, navegue até o projeto: </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. Instalar módulos</br></br>
`npm install`
1. Atualize a configuração **.env** da seguinte forma:

    - Definido `MicrosoftAppId` para o **iD do aplicativo bot** que você salvou no momento do registro do canal do bot.
    - Defina `MicrosoftAppPassword` o segredo do **cliente** que você salvou no momento do registro do canal bot.
    - Defina `connectionName` o nome da conexão do provedor de identidade.
    Dependendo dos caracteres do seu segredo de bot, você pode precisar de XML para escapar da senha. Por exemplo, quaisquer ampersands (&) precisarão ser codificados como `&amp;` .

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. Na `teamsAppManifest` pasta, abra `manifest.json` e defina `id`  para o **ID do aplicativo microsoft** e para o `botId` **ID do aplicativo bot** que você salvou no momento do registro do canal do bot.

# <a name="python"></a>[Python](#tab/python)

1. Clone [py-auth-sample][teams-auth-bot-py] do repositório github.
1. Atualização **config.py:**

    - Defina `ConnectionName` o nome da configuração de conexão OAuth adicionada ao seu bot.
    - Defina `MicrosoftAppId` e `MicrosoftAppPassword` para o ID do aplicativo do seu bot e segredo do aplicativo.

      Dependendo dos caracteres do seu segredo de bot, você pode precisar de XML para escapar da senha. Por exemplo, quaisquer ampersands (&) precisarão ser codificados como `&amp;` .

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a>Implante o bot para o Azure

Para implantar o bot, siga os passos de como [implantar seu bot no Azure](https://aka.ms/azure-bot-deployment-cli).

Alternativamente, enquanto em Visual Studio, você pode seguir estes passos:

1. Em Visual Studio *Solution Explorer* selecione e segure (ou clique com o botão direito) do nome do projeto.
1. No menu suspenso, selecione **Publicar**.
1. Na janela exibida, selecione o **link Novo.**
1. Na janela de diálogo, selecione **App Service** à esquerda e Crie **o Novo** à direita.
1. Selecione o botão **Publicar.**
1. Na próxima janela de diálogo, digite as informações necessárias. Veja um exemplo a seguir:

    ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. Selecione **Criar**.
1. Se a implantação for concluída com sucesso, você deve vê-la refletida em Visual Studio. Além disso, uma página é exibida no seu navegador padrão dizendo que *seu bot está pronto!*. A URL será semelhante a esta: `https://botteamsauth.azurewebsites.net/` . Guarde-o para um arquivo.
1. No seu navegador, navegue até o [**portal do Azure.**][azure-portal]
1. Verifique seu grupo de recursos, o bot deve ser listado junto com os outros recursos. A imagem a seguir é um exemplo:

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. No grupo de recursos, selecione o nome de registro do canal bot (link).
1. No painel esquerdo, selecione **Configurações**.
1. Na caixa **de ponto final de mensagens,** digite a URL obtida acima seguida por `api/messages` . Este é um exemplo: `https://botteamsauth.azurewebsites.net/api/messages` .
1. Selecione o botão **Salvar** no canto superior esquerdo.

## <a name="test-the-bot-using-the-emulator"></a>Teste o bot usando o Emulador

Se você ainda não fez isso, instale o [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme). Veja também [Debug com o Emulador](https://aka.ms/bot-framework-emulator-debug-with-emulator).

Para que o login da amostra do bot funcione, você deve configurar o Emulador.

### <a name="configure-the-emulator-for-authentication"></a>Configure o Emulador para autenticação

Se um bot exigir autenticação, você deve configurar o Emulador. Para configurar:

1. Inicie o Emulador.
1. No Emulador, selecione o ícone de engrenagem &#9881; no canto inferior esquerdo ou a guia **Emulador Configurações** no canto superior direito.
1. Verifique a caixa usando **tokens de autenticação da versão 1.0**.
1. Insira o caminho local para a ferramenta **ngrok.** *Veja* a integração de tunelamento Bot Framework Emulator / ngrok [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)). Para obter mais informações sobre ferramentas, consulte [ngrok](https://ngrok.com/).
1. Verifique a caixa por **Run ngrok quando o Emulador é iniciado**.
1. Selecione o botão **Salvar.**

Quando o bot exibe um cartão de login e o usuário seleciona o botão de login, o Emulador abre uma página que o usuário pode usar para fazer login com o provedor de autenticação.
Uma vez que o usuário faz isso, o provedor gera um token de usuário e envia-o para o bot. Depois disso, o bot pode agir em nome do usuário.

### <a name="test-the-bot-locally"></a>Teste o bot localmente

Depois de configurar o mecanismo de autenticação, você pode realizar o teste real do bot.  

1. Execute a amostra do bot localmente em sua máquina, através de Visual Studio por exemplo.
1. Inicie o Emulador.
1. Selecione o botão **Abrir bot.**
1. Na URL do **Bot,** digite a URL local do bot. Normalmente, `http://localhost:3978/api/messages` .
1. No **Microsoft App ID** digite o ID do aplicativo do bot de `appsettings.json` .
1. Na **senha** do Microsoft App digite a senha do aplicativo do bot a partir do `appsettings.json` .
1. Selecione **Conexão**.
1. Depois que o bot estiver funcionando, digite qualquer texto para exibir o cartão de login.
1. Selecione o botão **Entrar.**
1. Uma caixa de diálogo pop-up é exibida para **confirmar URL aberto**. Isso é para permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta do usuário aplicável.
1. Dependendo da configuração que você usou para o Emulador, você recebe uma das seguintes:
    1. **Usando código de verificação de login**  
      &#x2713; Uma janela é aberta exibindo o código de validação.  
      &#x2713; Copiar e digitar o código de validação na caixa de bate-papo para concluir o login.
    1. **Usando tokens de autenticação**.  
      &#x2713; Você está logado com base em suas credenciais.

    A imagem a seguir é um exemplo da interface do usuário do bot depois de você ter logado:

    ![emulador de login do bot auth](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. Se você selecionar **Sim** quando o bot perguntar *Gostaria de visualizar seu token?*

    ![token emulador de login do bot auth](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. Digite **logout** na caixa de bate-papo de entrada para sair. Isso libera o token do usuário, e o bot não poderá agir em seu nome até que você faça login novamente.

> [!NOTE]
> A autenticação do bot requer o uso do **Serviço de Conector de Bot**. O serviço acessa as informações de registro dos canais do bot para o seu bot.

## <a name="test-the-deployed-bot"></a>Teste o bot implantado

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. No seu navegador, navegue até o [**portal do Azure.**][azure-portal]
1. Encontre seu grupo de recursos.
1. Selecione o link de recursos. A página de recursos é exibida.
1. Na página de recursos, selecione **Teste no Web Chat**. O bot inicia e exibe as saudações predefinidas.
1. Digite qualquer coisa na caixa de bate-papo.
1. Selecione a caixa **Sinal na** caixa.
1. Uma caixa de diálogo pop-up é exibida para **confirmar URL aberto**. Isso é para permitir que o usuário do bot (você) seja autenticado.  
1. Selecione **Confirmar**.
1. Se solicitado, selecione a conta do usuário aplicável.
    A imagem a seguir é um exemplo da interface do usuário bot depois de você ter logado:

    ![login do bot auth implantado](../../../assets/images/authentication/auth-bot-login-deployed.PNG).

1. Selecione o botão **Sim** para exibir seu token de autenticação. A imagem a seguir é um exemplo:

    ![auth bot login implantado token](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG).

1. Digite logout para sair.

    ![auth bot implantado logout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> Se você está tendo problemas para fazer login, tente testar a conexão novamente como descrito nas etapas anteriores. Isso poderia recriar o token de autenticação.
> Com o cliente Bot Framework Web Chat no Azure, você pode precisar fazer login várias vezes antes que a autenticação seja estabelecida corretamente.

## <a name="install-and-test-the-bot-in-teams"></a>Instale e teste o bot em Teams

1. Em seu projeto bot, certifique-se de que a `TeamsAppManifest` pasta contém o junto com um e `manifest.json` `outline.png` `color.png` arquivos.
1. No Solution Explorer, navegue até a `TeamsAppManifest` pasta. Editar `manifest.json` atribuindo os seguintes valores:
    1. Certifique-se de que o **ID do aplicativo bot** recebido no momento do registro do canal do bot seja atribuído `id` e `botId` .
    1. Atribua este valor: `validDomains: [ "token.botframework.com" ]` .
1. Selecione e **feche** os `manifest.json` `outline.png` arquivos e `color.png` .
1. Aberto **Microsoft Teams**.
1. No painel esquerdo, na parte inferior, selecione o **ícone Aplicativos**.
1. No painel direito, na parte inferior, selecione **Upload um aplicativo personalizado**.
1. Navegue até a `TeamsAppManifest` pasta e carregue o manifesto com zíper.
O seguinte assistente é exibido:

    ![auth bot equipes upload](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. Selecione o botão **Adicionar a uma equipe**.
1. Na próxima janela, selecione a equipe onde deseja usar o bot.
1. Selecione o botão **Configurar um bot.**
1. Selecione os três pontos (&#x25cf;&#x25cf;&#x25cf;) no painel esquerdo. Em seguida, selecione o ícone **App Studio.**
1. Selecione a guia **'Manifesto'.** Você deve ver o ícone do bot que você carregou.
1. Além disso, você deve ser capaz de ver o bot listado como um contato na lista de bate-papo que você pode usar para trocar mensagens com o bot.

### <a name="testing-the-bot-locally-in-teams"></a>Testando o bot localmente em Teams

Microsoft Teams é um produto inteiramente baseado em nuvem, requer que todos os serviços que acessa estejam disponíveis na nuvem usando pontos finais HTTPS. Portanto, para permitir que o bot (nossa amostra) funcione em Teams, você precisa publicar o código na nuvem de sua escolha, ou tornar uma instância de execução local acessível externamente através de uma ferramenta **de tunelamento.** Recomendamos  [ngrok](https://ngrok.com/download), que cria uma URL externamente endereçada para uma porta que você abre localmente em sua máquina.
Para configurar ngrok em preparação para executar seu aplicativo de Microsoft Teams localmente, siga estas etapas:

1. Em uma janela terminal, vá ao diretório onde você `ngrok.exe` instalou. Sugerimos definir o caminho variável do *ambiente* para apontar para ele.
1. Corra, por `ngrok http 3978 --host-header=localhost:3978` exemplo, . Substitua o número da porta conforme necessário.
Isso lança ngrok para ouvir na porta que você especificar. Em troca, ele lhe dá uma URL externamente endereçada, válida enquanto ngrok estiver sendo executado. A imagem a seguir é um exemplo:

    ![equipes bot app auth conexão string adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG).

1. Copie o endereço HTTPS de encaminhamento. Deve ser semelhante ao seguinte: `https://dea822bf.ngrok.io/` .
1. Anexar `/api/messages` para obter `https://dea822bf.ngrok.io/api/messages` . Este é o ponto final das **mensagens** para o bot rodando localmente em sua máquina e acessível pela web em um bate-papo em Microsoft Teams.
1. Um passo final a ser realizado é atualizar o ponto final das mensagens do bot implantado. No exemplo, implantamos o bot no Azure. Então **vamos executar essas etapas:
    1. No seu navegador navegue até o [**portal do Azure.**][azure-portal]
    1. Selecione seu **Registro de Canal de Bot**.
    1. No painel esquerdo, selecione **Configurações**.
    1. No painel direito, na caixa **de ponto final de mensagens,** digite a URL ngrok, em nosso exemplo, `https://dea822bf.ngrok.io/api/messages` .
1. Inicie seu bot localmente, por exemplo, no modo de depuração de Visual Studio.
1. Teste o bot enquanto estiver sendo executado localmente usando o chat da Web de teste do portal **Bot** Framework . Como o Emulador, este teste não permite que você acesse Teams funcionalidade específica.
1. Na janela do terminal onde `ngrok` está sendo executado, você pode ver o tráfego HTTP entre o bot e o cliente do web chat. Se você quiser uma exibição mais detalhada, em uma janela do navegador `http://127.0.0.1:4040` digite você obtido na janela do terminal anterior. A imagem a seguir é um exemplo:

    ![auth bot equipes ngrok teste](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png).

> [!NOTE]
> Se você parar e reiniciar ngrok, a URL será alterado. Para usar ngrok em seu projeto e, dependendo dos recursos que você está usando, você deve atualizar todas as referências de URL.
 

## <a name="additional-information"></a>Informações adicionais

### <a name="teamsappmanifestmanifestjson"></a>TeamsAppManifest/manifest.json

Este manifesto contém informações necessárias por Microsoft Teams para se conectar com o bot:  

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

Com a autenticação, Teams se comporta de forma ligeiramente diferente de outros canais, como explicado abaixo.

### <a name="handling-invoke-activity"></a>Manipulação da atividade de invocação

Uma **Atividade de Invocação** é enviada ao bot em vez da Atividade de Evento usada por outros canais.
Isso é feito sub-classificando o **ActivityHandler**.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-sample)

**Bots/DialogBot.cs**

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

**Bots/TeamsBot.cs**

A *Atividade de Invocação* deve ser encaminhada para o diálogo se o **OAuthPrompt** for usado.

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

A *Atividade de Invocação* deve ser encaminhada para o diálogo se o **OAuthPrompt** for usado.

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

**diálogos/mainDialog.js**

Dentro de uma etapa de diálogo, use `beginDialog` para iniciar o prompt OAuth, que pede ao usuário para fazer login.

- Se o usuário já estiver conectado, isso gerará um evento de resposta a tokens, sem solicitar ao usuário.
- Caso contrário, isso solicitará ao usuário fazer login. O Serviço Azure Bot envia o evento de resposta ao token após o usuário tentar fazer login.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

Dentro da etapa de diálogo a seguir, verifique se há presença de um token no resultado da etapa anterior. Se não for nulo, o usuário fez o seu primeiro-dia.

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

**bots/logoutDialog.js**

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[Python](#tab/python-sample)

**bots/dialog_bot.py**

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

**bots/teams_bot.py**

A *Atividade de Invocação* deve ser encaminhada para o diálogo se o **OAuthPrompt** for usado.

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

**diálogos/main_dialog.py**

Dentro de uma etapa de diálogo, use `begin_dialog` para iniciar o prompt OAuth, que pede ao usuário para fazer login.

- Se o usuário já estiver conectado, isso gerará um evento de resposta a tokens, sem solicitar ao usuário.
- Caso contrário, isso solicitará ao usuário fazer login. O Serviço Azure Bot envia o evento de resposta ao token após o usuário tentar fazer login.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

Dentro da etapa de diálogo a seguir, verifique se há presença de um token no resultado da etapa anterior. Se não for nulo, o usuário fez o seu primeiro-dia.

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

**diálogos/logout_dialog.py**

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

## <a name="see-also"></a>Confira também

[Adicionar autenticação através do Azure Bot Service](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: /azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: /azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: /azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: /azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
