---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração Moodle para o Microsoft Teams
keywords: Plug-in de integração de aplicativos do Teams Moodle
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 091192054c5add7cfbdc1e7baabc86e34cef7631
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020582"
---
# <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Moodle é um LMS (Sistema de Gerenciamento de Aprendizagem) de código aberto popular. Agora, ele está integrado ao Microsoft Teams. Essa integração ajuda educadores e professores a colaborarem em torno de cursos de miojo, fazer perguntas sobre notas e atribuições e manter-se atualizados com notificações diretamente no Teams.

Para ajudar os administradores de IT a configurar facilmente essa integração, o Plug-in de miojo do Microsoft 365 de código aberto é atualizado com os seguintes recursos:

* Registro automático do servidor Moodle com [o Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (Azure AD).
* Implantação de um clique do bot do Assistente de miojo no Azure.
* Provisionamento automático de equipes e sincronização automática de inscrições de equipe para todos ou selecione Cursos de miojo.
* Instalação automática da guia Moodle e do bot do assistente de miojo em cada equipe sincronizada.

Para saber mais sobre a funcionalidade que essa integração fornece, consulte [Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

A seguir estão os pré-requisitos para instalar e configurar o aplicativo Moodle: 

1. Credenciais de administrador de miojo.

1. Credenciais de administrador do Azure AD.

1. Uma assinatura do Azure onde você pode criar novos recursos.

**Para instalar e configurar o aplicativo Moodle** 

Execute as etapas a seguir para instalar e configurar o aplicativo Moodle: 

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Instalar os Plug-ins de miojo do Microsoft 365

A integração do Moodle no Microsoft Teams é alimentada pelo conjunto de plug-in do [Microsoft 365 Moodle](https://github.com/Microsoft/o365-moodle)de código aberto. Para instalar o plug-in no servidor Moodle, você deve ter os seguintes aplicativos instalados:

1. Uma [versão estável atual de Moodle](https://download.moodle.org/releases/latest/).

1. O Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) e os plug-ins de integração do [Microsoft 365](https://moodle.org/plugins/local_o365) baixados e salvos no computador local.

   > [!NOTE]
   > A instalação dos plug-ins de integração do OpenID Connect e do Microsoft 365 é necessária para a integração do Teams. Além disso, o [plug-in do Tema do Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) é altamente recomendado.

1. Entre no servidor Moodle como administrador e selecione Administração do **site** no bloco [Configurações](https://docs.moodle.org/22/en/Settings_block) localizado no painel de navegação esquerdo.

1. Selecione a **guia Plug-ins** e selecione **Instalar plug-ins**.

1. Na seção **Instalar plug-in do arquivo ZIP,** selecione **Escolher um botão de** arquivo.

1. Selecione **Carregar uma opção de** arquivo na navegação à esquerda, procure o arquivo que você baixou e selecione Carregar esse **arquivo**.

1. Selecione a **administração do site** no painel de navegação esquerdo para retornar ao painel de administração. Role para baixo até os **plug-ins locais** e selecione o link Integração do **Microsoft 365.** 

> [!IMPORTANT]
>
> * Mantenha sua página de configuração do Plug-in de miojo do Microsoft 365 aberta em uma guia de navegador separada, pois você precisa retornar a esse conjunto de páginas ao longo do processo.  <br/><br/>
> * Se você não tiver um site Moodle existente, poderá fazer check-out Moodle no [repo](https://github.com/azure/moodle) do Azure, onde você pode implantar rapidamente uma instância de Moodle e personalizá-la de acordo com suas necessidades.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugin-and-azure-active-directory-azure-ad"></a>2. Configurar a conexão entre o plug-in do Microsoft 365 e o Azure Active Directory (Azure AD)

Você deve registrar Moodle como um aplicativo no Azure AD. Use o script do PowerShell para concluir esse processo. O script do PowerShell provisiona um novo aplicativo do Azure AD para seu locatário do Microsoft 365, que é usado pelo Plug-in de miojo do Microsoft 365. O script provisiona o aplicativo para seu locatário do Microsoft 365, configura as URLs e permissões de resposta necessárias para o aplicativo provisionado e retorna `AppID` o e `Key` . Você pode usar a página de configuração do Plug-in do Microsoft 365 Moodle gerada para configurar seu site de servidor `AppID` `Key` Moodle com o Azure AD.

> [!IMPORTANT]
> * O script do PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve concluir a configuração manualmente seguindo as etapas descritas nas páginas de versão Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2.](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) </br></br>
> * Para exibir as etapas manuais que o script do PowerShell está automatizando em detalhes, consulte [Register your Moodle instance as an Application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia Moodle para fluxo de informações do Microsoft Teams

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página plug-in de integração do Microsoft 365, selecione a **guia Instalação.**

1. Selecione o **botão Baixar Script do PowerShell** e salve-o no computador local.

1. Você deve preparar o script do PowerShell do arquivo ZIP. Execute as etapas a seguir para preparar o script do PowerShell a partir do arquivo ZIP:

    1. Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.
    1. Abra a pasta extraída.
    1. Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades**.
    1. Na guia **Geral** da janela Propriedades, marque a caixa ao lado `Unblock` do atributo **Security** localizado na parte inferior da janela.
    1. Selecione **OK**.
    1. Copie o caminho do diretório para a pasta extraída.

1. Execute o PowerShell como administrador:

    1. Selecione Iniciar.
    1. Digite PowerShell.
    1. Clique com o botão direito Windows PowerShell.
    1. Selecione **Executar como Administrador**.

1. Navegue até o diretório desacortado digitando `cd .../.../Moodle-AzureAD-Powershell` onde está o caminho para o `.../...` diretório.

1. Execute o script do PowerShell:

    1. Insira `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` .
    1. Insira `./Moodle-AzureAD-Script.ps1` .
    1. Entre na sua conta de administrador do Microsoft 365 na janela pop-up.
    1. Insira o nome do Aplicativo do Azure AD (por exemplo, plug-in Moodle/Moodle).
    1. Insira a URL do servidor Moodle.
    1. Copie a **ID do Aplicativo** **e a Chave de** Aplicativo gerada pelo script e salve-as.

1. Em seguida, você deve adicionar `AppID` e ao Plug-in de miojo do Microsoft `Key` 365. Volte para a página de administração do plug-in. O fluxo é: Administração de sites ➡ Plug-ins ➡ Integração do Microsoft 365.

1. Na guia **Instalação,** adicione a **ID** do Aplicativo e a **Chave** de Aplicativo que você copiou anteriormente e selecione **Salvar alterações**.

1. Após a atualização da página, você pode ver uma nova seção **Escolher método de conexão**. Selecione a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações novamente.**

1. Após a atualização da página, você pode ver outra nova seção Consentimento do **administrador & informações adicionais**.
    1. Selecione **Fornecer o** link Fornecer Consentimento de Administrador, insira suas credenciais de Administrador Global do Microsoft 365 e aceite para conceder as permissões. 
    1. Ao lado do **campo Locatário do Azure AD,** selecione o **botão Detectar.**
    1. Ao lado da **URL do OneDrive for Business,** selecione o **botão Detectar.**
    1. Depois que os campos preencherem, selecione o **botão Salvar alterações** novamente.

1. Selecione o **botão Atualizar** para verificar a instalação e salve **as alterações**.

1. Sincronizar usuários entre seu servidor Moodle e o Azure AD. Dependendo do ambiente, você pode selecionar diferentes opções durante este estágio. Para começar:
    1. Alternar para a **guia Configurações de Sincronização**
    1. Na seção **Sincronizar usuários com o Azure AD,** selecione as caixas de seleção que se aplicam ao seu ambiente. Você deve selecionar o seguinte:  

        ✔ Criar contas no Moodle para usuários no Azure AD . 
        ✔ atualizar todas as contas no Moodle para usuários no Azure AD.  

    1. Na seção **Restrição de** Criação de Usuário, você pode configurar um filtro para limitar os usuários do Azure AD sincronizados com moodle.
    1. A **seção Mapeamento de** Campo do Usuário permite que você personalize o mapeamento de campo do Azure AD para Moodle User Profile.
    1. Na seção **Sincronização do Teams,** você pode selecionar para criar automaticamente Grupos, como equipes para alguns ou todos, de seus cursos de Moodle existentes.

> [!NOTE]
> O Moodle [Cron](https://docs.moodle.org/310/en/Cron) é executado de acordo com o cronograma da tarefa. O agendamento padrão é uma vez por dia. No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.

13. Para [validar trabalhos de](https://docs.moodle.org/310/en/Cron) cron e execute-os manualmente para a primeira executar, selecione o **link** da página Gerenciamento de tarefas agendadas na seção Sincronizar usuários com **o Azure AD.** Isso o leva à página **Tarefas Agendadas.**

    1. Role para baixo e encontre o trabalho **Sincronizar usuários com o Azure AD** e selecione **Executar agora**.
    1. Se você selecionar criar Grupos com base em cursos existentes, também poderá executar o trabalho Criar grupos de usuários **no Microsoft 365.**

1. Volte para a página de administração do plug-in. O fluxo de navegação é: Administração do site ➡ Plug-ins ➡ Microsoft 365 Integratio. Em seguida, selecione a **página Configurações do Teams.** Você deve configurar algumas configurações para habilitar a integração de aplicativos do Teams.

    1. Para **habilitar o OpenID Connect,** selecione o link **Gerenciar Autenticação** e selecione o ícone do olho na linha **OpenId Connect** se ele estiver acinzentado.
    1. Habilitar a incorporação de quadro. Selecione o link **Segurança HTTP** e selecione a caixa de seleção ao lado de Permitir **a incorporação de quadro**.
    1. Habilitar serviços Web que habilitam os recursos da API Moodle. Selecione o link **Recursos Avançados** e verifique se a caixa de seleção ao lado de **Habilitar serviços Web** está marcada.
    1. Habilita os serviços externos do Microsoft 365. Selecione o **link Serviços externos** em seguida:  

        ✔ Selecione **Editar** na **linha Moodle Microsoft 365 Webservices.**  
        ✔ Marque a caixa de seleção ao lado **de Habilitado,** selecione **Salvar Alterações**

    1. Edite suas permissões de usuário autenticadas para permitir que eles criem tokens de serviço Web. Selecione o **link Da função de edição 'Usuário autenticado'.** Role para baixo e encontre **o recurso Criar um token** de serviço Web e marque a caixa **de** seleção Permitir.

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Implantar o Moodle Assistant Bot no Azure

O bot de assistente de miojo gratuito do Microsoft Teams ajuda professores e alunos a responder a perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle. O bot também envia notificações Moodle para alunos e professores no Teams. O bot é um projeto de código aberto mantido pela Microsoft e está disponível no [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
> * Nesta seção, você deve implantar recursos em sua assinatura do Azure. Todos os recursos configurados usando a **camada** gratuita. Dependendo do uso do bot, você deve dimensionar esses recursos.
> * Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações de bot de miojo

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade da Microsoft.](https://identity.microsoft.com/Landing) Isso permite que o bot se autenture nos pontos de extremidade da Microsoft. 

**Para registrar seu bot**:

1. Vá para a página administração do plug-in. Vá para **Plug-ins**. Em Integração com o **Microsoft 365,** selecione a **guia Configurações do Teams.**

1. Selecione o link do Portal de Registro de **Aplicativos** da Microsoft e entre com sua ID da Microsoft.

1. Insira um nome para seu aplicativo, como MoodleBot e selecione o **botão Criar.**

1. Copie a **ID do** Aplicativo e a colar no campo **ID** do Aplicativo Bot na página **Configurações da** Equipe.

1. Selecione o **botão Gerar Nova Senha.** Copie a senha gerada e a colar no campo Senha do Aplicativo **Bot** na página **Configurações da** Equipe.

1. Role até a parte inferior do formulário e selecione **Salvar Alterações**.

À medida que você gerou sua ID de Aplicativo e Senha, a próxima etapa é implantar seu bot no Azure:

> [!div class="checklist"]
> * Selecione o botão **Implantar no Azure** e preencha o formulário com as informações necessárias, como a ID do Aplicativo Bot, a Senha do Aplicativo Bot e o Segredo do Moodle estão na página Configurações **da** Equipe. As informações do Azure estão na página **Instalação).** 
> * Depois de concluir o formulário, marque a caixa de seleção para concordar com os termos e condições.
> * Selecione o **botão Comprar.** Todos os recursos do Azure são implantados na camada gratuita.

Após a conclusão da implantação dos recursos no Azure, você deve configurar o plug-in do Moodle do Microsoft 365 com um ponto de extremidade de mensagens. Você deve obter o ponto de extremidade do bot no Azure:

**Configurar o plug-in do Moodle do Microsoft 365 com um ponto de extremidade de mensagens**  
1. Entre no [portal do Azure](https://portal.azure.com).

1. No painel esquerdo, selecione **Grupos** de recursos e selecione o grupo de recursos que você usou ou criou ao implantar o bot.

1. Selecione o **recurso Bot do WebApp** na lista de recursos no grupo.

1. Copie o **Ponto de Extremidade de Mensagens** da seção **Visão** Geral.

1. No Moodle, abra a **página Configurações da** Equipe do plug-in de miojo do Microsoft 365.

1. No campo **Ponto de Extremidade bot,** cole a URL que você acabou de copiar e altere as mensagens *de* palavra para *webhook*. A URL agora deve aparecer da seguinte forma: `https://botname.azurewebsites.net/api/webhook`

1. Selecione **Salvar Alterações**.

1. Depois de salvar as alterações, volte para a guia Configurações da Equipe, selecione o botão **Baixar** arquivo de manifesto e salve o pacote de manifesto do aplicativo em seu computador para uso posterior. 

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Implantar seu aplicativo do Microsoft Teams

Depois que seu bot foi implantado no Azure e configurado para falar com seu servidor Moodle, você deve implantar seu aplicativo do Microsoft Teams. Para fazer isso, você deve carregar o arquivo de manifesto do aplicativo que você baixou na página Configurações de Equipe do Plug-in do Microsoft 365 Moodle na etapa anterior.

Antes de instalar o aplicativo, você deve garantir a habilitação de aplicativos externos e o carregamento de aplicativos. Para fazer isso, você pode seguir as etapas na documentação de locatário do [Microsoft 365 Prepare your Microsoft 365.](../concepts/build-and-test/prepare-your-o365-tenant.md) Você pode executar as seguintes etapas para implantar seu aplicativo: 

**Para implantar seu aplicativo**

1. Abra **o Microsoft Teams**. 

1. Selecione o **ícone aplicativo** na área inferior esquerda da barra de navegação.

1. Selecione o **link Carregar um aplicativo personalizado** na lista de opções.

   > [!NOTE]
   > Se você estiver conectado como um administrador global, deverá ter a opção de carregar o aplicativo no catálogo de aplicativos da sua organização, caso contrário, você só poderá carregar o aplicativo para uma equipe na qual você é membro.

4. Selecione o `manifest.zip` pacote que você baixou anteriormente e selecione **Salvar**. Se você não tiver baixado o pacote de  manifesto do aplicativo, poderá baixar na guia Configurações da Equipe da página de configuração do plug-in no Moodle.

Agora que você tem o aplicativo instalado, você pode adicionar a guia a qualquer canal ao que tiver acesso. Para fazer isso, navegue até o canal, selecione o símbolo **mais** (➕) e selecione seu aplicativo na lista. Siga os prompts para concluir a adição de sua guia de curso miojo a um canal.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Permitir a criação automática de guias Moodle no Microsoft Teams

Embora as guias Moodle sejam criadas manualmente no Microsoft Teams, você pode decidir que elas sejam criadas automaticamente quando as equipes são criadas a partir da sincronização do curso. Para fazer isso, você deve configurar a ID do aplicativo do Microsoft Teams carregado no Moodle:

1. Abra o Microsoft Teams.

1. Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.

1. Localize o aplicativo **Moodle** carregado ➡ selecione o ícone **de** opções ➡ selecione **copiar link**.

1. Em um editor de texto, colar o conteúdo copiado. Ele deve conter uma URL como ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Copie a última parte da URL, como , que é a  `00112233-4455-6677-8899-aabbccddeeff` ID do aplicativo do Microsoft Teams.

1. No Moodle, abra a guia **Aplicativo miojo** do Teams na página de configuração do Plug-in de miojo do Microsoft 365.

1. Colar a ID do aplicativo Microsoft Teams no campo ID do aplicativo Moodle e salvar alterações.

Quando um curso Moodle é sincronizado, o Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral do Teams e o configura para conter a página de curso para o curso Moodle do qual ele é sincronizado. Agora você pode começar a trabalhar com seus cursos de Moodle diretamente do Microsoft Teams.

Para compartilhar qualquer solicitação de recurso ou comentários conosco, visite nossa [página user voice](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)

> [!div class="nextstepaction"]
> [Moodle](https://moodle.org/)

> [!div class="nextstepaction"]
> [Documentação de miojo](https://docs.moodle.org/34/en/Installing_plugins).
