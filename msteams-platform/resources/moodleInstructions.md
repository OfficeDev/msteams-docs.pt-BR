---
title: Instalando a integração do Moodle com o Microsoft Teams
description: Como instalar e configurar o aplicativo de integração M integration para o Microsoft Teams
keywords: Plug-in de integração do aplicativo Teams M chrome
ms.topic: how-to
ms.author: lajanuar
author: laujan
ms.openlocfilehash: bb3de6b3897105ff3564ecd332cba28a0db85b0f
ms.sourcegitcommit: a16590b2ccc46e1b6d17cbb367762a3c16ff779c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50115738"
---
# <a name="installing-the-moodle-integration-with-microsoft-teams"></a>Instalando a integração do Moodle com o Microsoft Teams

[Mhari](https://moodle.org/), um popular LMS (Sistema de Gerenciamento de Aprendizagem de Código Aberto), agora está integrado ao Microsoft Teams. Essa integração ajuda os educadores e professores a colaborarem em torno de cursos de idiomas, fazer perguntas sobre notas e tarefas e manter-se atualizado com notificações diretamente no Teams.

Para ajudar os administradores de IT a configurar facilmente essa integração, atualizamos nosso Plug-in microsoft 365 M chrome de código aberto com os seguintes recursos:

* Registro automático do seu servidor Moodle com [o Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (Azure AD).
* Implantação de um clique do bot do Assistente de Mção no Azure.
* Provisionamento automático de equipes e sincronização automática de inscrições de equipe para todos ou cursos selecionados no M meio.
* Instalação automática da guia Mtter e do bot do Assistente de Montagem em cada equipe sincronizada.

Para saber mais sobre as funcionalidades  que essa integração fornece, consulte [Microsoft Teams e M meio-](https://education.microsoft.com/resource/3dffb3a8)

## <a name="prerequisites"></a>Pré-requisitos

Para instalar e configurar esse aplicativo, você precisará de:

1. Credenciais de administrador mioque.

1. Credenciais de administrador do Azure AD.

1. Uma assinatura do Azure onde você pode criar novos recursos.

## <a name="step-1-install-the-microsoft-365-moodle-plugins"></a>Etapa 1: instalar os plug-ins do Microsoft 365 M plugins

A integração M chrome no Microsoft Teams é alimentada pelo conjunto de plug-ins [do Microsoft 365 M plugin de código aberto.](https://github.com/Microsoft/o365-moodle) Para instalar o plug-in em seu servidor M chrome, você precisa ter o seguinte instalado:

1. Uma [versão estável atual do Mhari.](https://download.moodle.org/releases/latest/)

1. Os plug-ins de integração do M google [OpenID Connect](https://moodle.org/plugins/auth_oidc) e do [Microsoft 365](https://moodle.org/plugins/local_o365) foram baixados e salvos no computador local.

> [!NOTE]
> A instalação dos plug-ins de integração do OpenID Connect e do Microsoft 365 é necessária para a integração com o Teams. Além disso, o [plug-in de tema do Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) é altamente recomendado.

3. Faça logon no servidor Mhari como administrador e selecione **Administração do site** no bloco [Configurações](https://docs.moodle.org/22/en/Settings_block) localizado no painel de navegação esquerdo.

1. Selecione a **guia Plug-ins** e, em seguida, escolha **Instalar plug-ins.**

1. Na seção **Instalar plug-in do arquivo ZIP,** selecione **o botão** Escolher um arquivo.

1. Selecione as **opções para** Carregar um arquivo na navegação à esquerda, procure o arquivo que você baixou acima e escolha Carregar **este arquivo.**

1. Selecione a **opção de administração do site** no painel de navegação esquerdo para retornar ao seu painel de administração. Role para baixo até **os plug-ins locais** e selecione o link **de Integração do Microsoft 365.** **Mantenha essa página de configuração aberta em uma guia separada do navegador durante todo o processo de instalação.**

Você pode encontrar mais informações sobre como instalar plug-ins M chrome na documentação [M chrome](https://docs.moodle.org/34/en/Installing_plugins).

> [!IMPORTANT]
>
> * Mantenha sua página de configuração do Plug-in Mfox do Microsoft 365 aberta em uma guia separada do navegador — você retornará a esse conjunto de páginas durante todo o processo.  <br/><br/>
>* Se você não tiver um site M widget existente, poderá fazer [](https://github.com/azure/moodle) check-out do M widget no Azure, onde você pode implantar rapidamente uma instância M widget e personalizá-la de acordo com suas necessidades.

## <a name="step-2-configure-the-connection-between-the-microsoft-365-plugin-and-azure-active-directory-azure-ad"></a>Etapa 2: Configurar a conexão entre o plug-in do Microsoft 365 e o Azure Active Directory (Azure AD)

Em seguida, você precisará registrar Ostra como um aplicativo no Azure AD. Fornecemos um script do PowerShell para ajudá-lo a concluir esse processo. O script do PowerShell provisiona um novo aplicativo do Azure AD para seu locatário do Microsoft 365, que será usado pelo Plug-in Mshell do Microsoft 365. O script provisionará o aplicativo para seu locatário do Microsoft 365, configurará as URLs e permissões de resposta necessárias para o aplicativo provisionado e retornará o `AppID` e `Key` . Você pode usar a gerada e na página de configuração do Plug-in M plugin do Microsoft 365 para configurar o site do servidor M chrome com o `AppID` `Key` Azure AD.

>[!IMPORTANT]
> O script do PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você terá que concluir a configuração manualmente seguindo as etapas descritas nas páginas de versão M latest [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2.](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) </br></br>
> Para exibir as etapas manuais que o script do PowerShell está automatizando em *detalhes,* consulte Registrar sua instância [Mhari como um aplicativo](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia M meio do fluxo de informações do Microsoft Teams

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página do plug-in de integração do Microsoft 365, selecione a **guia** Configuração.

1. Selecione o **botão Baixar Script do PowerShell** e salve-o no computador local.

1. Você precisará preparar o script do PowerShell do arquivo ZIP. Para fazer isso:

    * Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.
    * Abra a pasta extraída.
    * Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades.**
    * Na guia **Geral** da janela Propriedades, marque a caixa ao lado do atributo Security localizado `Unblock` na parte inferior da janela. 
    * Selecione **OK**.
    * Copie o caminho do diretório para a pasta extraída.

1. Em seguida, você executará o PowerShell como administrador:

    * Selecione Iniciar.
    * Digite PowerShell.
    * Clique com o botão direito do mouse no Windows PowerShell.
    * Selecione "Executar como Administrador".

1. Navegue até o diretório des lado a lado digitando `cd .../.../Moodle-AzureAD-Powershell` onde está o caminho para o `.../...` diretório.

1. Execute o script do PowerShell:

    * Insira `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` .
    * Insira `./Moodle-AzureAD-Script.ps1` .
    * Faça logon na sua conta de administrador do Microsoft 365 na janela pop-up.
    * Insira o nome do Aplicativo do Azure AD (por exemplo, plug-in M meio-e-M meio-dia).
    * Insira a URL do seu servidor Moodle.
    * Copie a **ID do Aplicativo** **e a Chave do** Aplicativo geradas pelo script e salve-as.

1. Em seguida, você precisará adicionar e ` AppID` ao Plug-in `Key` do Microsoft 365 M plugin. Retorne à página de administração do plug-in (administração do site ➡ plug-ins ➡ integração com o Microsoft 365).

1. Na guia **Configuração,** adicione  a **ID** do Aplicativo e a Chave do Aplicativo que você copiou anteriormente e selecione **Salvar alterações.**

1. Depois que a página é atualizada, você deve ver uma nova seção **Escolher o método de conexão.** Marque a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações** novamente.

1. Depois que a página é atualizada, você verá outra nova seção consentimento do **administrador & informações adicionais.**
    * Selecione o link **Fornecer Consentimento de** Administrador, insira suas credenciais  de Administrador Global do Microsoft 365 e Aceite para conceder as permissões.
    * Ao lado do campo **Locatário do Azure AD,** selecione o **botão** Detectar.
    * Ao lado da **URL do OneDrive for Business,** selecione o **botão** Detectar.
    * Depois que os campos são preenchidos, selecione **o botão Salvar alterações** novamente.

1. Selecione o **botão Atualizar** para verificar a instalação e salvar **as alterações.**

1. Em seguida, você precisará sincronizar os usuários entre o servidor Mhari e o Azure AD. Dependendo do ambiente, você pode selecionar opções diferentes durante esse estágio. Para começar:
    * Alternar para a **guia Configurações de Sincronização**
    * Na seção **Sincronizar usuários com o Azure AD,** marque as caixas de seleção que se aplicam ao seu ambiente. Normalmente, você faria, no mínimo, selecionar o seguinte:  

        ✔ criar contas no M meio para usuários no Azure AD. 
        ✔ atualizar todas as contas no M meio para os usuários no Azure AD.  

    * Na seção **Restrição de Criação de** Usuário, você pode configurar um filtro para limitar os usuários do Azure AD que serão sincronizados com o M playback.
    * A **seção Mapeamento de Campo de** Usuário permitirá que você personalize o mapeamento de campo do Perfil de Usuário do Azure AD para M meio.
    * Na seção **Sincronização do Teams,** você pode optar por criar grupos automaticamente (ou seja, equipes) para alguns ou todos os cursos existentes do M courses.

> [!NOTE]
> O Mhari [Cron](https://docs.moodle.org/310/en/Cron) será executado de acordo com o agendamento da tarefa (uma vez por dia por padrão). No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.

13. Para [validar trabalhos com](https://docs.moodle.org/310/en/Cron) mais de um usuário (e/ou executar manualmente na primeira vez) selecione o **link** da página Gerenciamento de tarefas agendadas na seção Sincronizar usuários com o **Azure AD.** Isso levará você para a página **Tarefas Agendadas.**

    * Role para baixo e encontre os usuários de sincronização com o trabalho do **Azure AD** e selecione **Executar agora.**
    * Se você escolher criar Grupos com base em cursos existentes, também poderá executar o trabalho Criar grupos de usuários **no Microsoft 365.**

1. Retorne à página de administração do plug-in (Administração do site ➡ Plug-ins ➡ Integração com o Microsoft 365) e selecione a página Configurações **do Teams.** Você precisará definir algumas configurações para habilitar a integração de aplicativos do Teams.

    * Para **habilitar OpenID Connect,** selecione o **link** Gerenciar Autenticação e selecione o ícone de olho na **linha OpenId Connect** se ele estiver acinzentado.
    * Em seguida, você precisará habilitar a incorporação de quadros. Selecione o link **Segurança HTTP** e marque a caixa de seleção ao lado de **Permitir incorporação de quadro.**
    * A próxima etapa é habilitar os serviços Web que habilitarão os recursos da API Mhari. Selecione o link **Recursos Avançados** e verifique se a caixa de seleção ao lado de **Habilitar serviços Web** está marcada.
    * Por fim, você precisará habilitar os serviços externos para o Microsoft 365. Selecione o **link Serviços externos** e, em seguida:  

        ✔ Selecione **Editar** na **linha M google Microsoft 365 Webservices.**  
        ✔ Marque a caixa de seleção ao lado **de Habilitado** e selecione **Salvar Alterações**

    * Em seguida, você precisará editar suas permissões de usuário autenticado para permitir que eles criem tokens de serviço Web. Selecione o link **da função de Edição 'Usuário autenticado'.** Role para baixo, encontre **o recurso Criar um token** de serviço Web e marque a caixa **de** seleção Permitir.

## <a name="step-3-deploy-the-moodle-assistant-bot-to-azure"></a>Etapa 3: Implantar o Bot do Assistente de Mção no Azure

O bot do assistente gratuito Mtter para o Microsoft Teams ajuda professores e alunos a responder perguntas sobre seus cursos, tarefas, notas e outras informações no Mhari. O bot também envia notificações Desaquedos para alunos e professores no Teams. O bot é um projeto de código aberto mantido pela Microsoft e está disponível no [GitHub.](https://github.com/microsoft/Moodle-Teams-Bot)

> [!NOTE]
> Nesta seção, você implantará recursos para sua assinatura do Azure. Todos os recursos serão configurados usando a **camada** gratuita. Dependendo do uso do bot, talvez seja necessário dimensionar esses recursos.
> Se você quiser usar a guia M meio-dia sem o bot, pule para a [etapa 4.](#step-4-deploy-your-microsoft-teams-app)

### <a name="moodle-bot-information-flow"></a>Fluxo de informações de bot m correção

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, primeiro você precisará registrá-lo na [Plataforma de Identidade da Microsoft.](https://identity.microsoft.com/Landing) Isso permite que seu bot seja autenticado nos pontos de extremidade da Microsoft. Para registrar seu bot:

1. Volte para a página de administração do plug-in (Administração do site ➡ Plug-ins ➡ Integração com o Microsoft 365) e selecione a guia Configurações **do Teams.**

1. Selecione o link **do Portal de Registro de Aplicativos** da Microsoft e faça logon com sua ID da Microsoft.

1. Insira um nome para seu aplicativo (por exemplo, MoodleBot) e selecione o **botão** Criar.

1. Copie a **ID do Aplicativo** e a colar no campo **ID** do Aplicativo bot na página **Configurações da** Equipe.

1. Selecione o **botão Gerar Nova** Senha. Copie a senha gerada e a colar no campo **Senha** do Aplicativo bot na página **Configurações da** Equipe.

1. Role até a parte inferior do formulário e selecione **Salvar Alterações.**

Agora que você gerou sua ID de aplicativo e senha, é hora de implantar seu bot no Azure:

> [!div class="checklist"]
> * Selecione o botão Implantar no **Azure** e preencha o formulário com as informações necessárias (a ID do Aplicativo bot, a Senha do Aplicativo bot e o Segredo M button estão na página Configurações **da** Equipe. As informações do Azure estão na página **Configuração).** 
> * Depois de concluir o formulário, marque a caixa de seleção para concordar com os termos e condições.
> * Selecione o **botão Comprar** (todos os recursos do Azure são implantados na camada gratuita).

Depois que os recursos concluirem a implantação no Azure, você precisará configurar o plug-in do Microsoft 365 M plugin com um ponto de extremidade de mensagens. Você precisará obter o ponto de extremidade do seu bot no Azure:

1. Faça logoff no [portal do Azure.](https://portal.azure.com)

1. No painel esquerdo, selecione **Grupos de recursos** e escolha o grupo de recursos que você usou (ou criou) durante a implantação do bot.

1. Selecione o **recurso de Bot do WebApp** na lista de recursos do grupo.

1. Copie o **ponto de extremidade de mensagens** da seção **Visão** geral.

1. In Mhari, open the **Team Settings** page of your Microsoft 365 M meio plug-in.

1. In the **Bot Endpoint** field paste the URL you just copied and change the word *messages* to *webhook*. Agora, a URL deve aparecer da seguinte forma:  `https://botname.azurewebsites.net/api/webhook`

1. Selecione **Salvar Alterações.**

1. Depois que suas alterações foram **salvas,** volte para  a guia Configurações da Equipe, selecione o botão Baixar arquivo de manifesto e salve o pacote de manifesto do aplicativo no computador (você o usará na próxima seção).

## <a name="step-4-deploy-your-microsoft-teams-app"></a>Etapa 4: implantar seu aplicativo Microsoft Teams

Agora que você tem seu bot implantado no Azure e configurado para falar com seu servidor M meio-dia, é hora de implantar seu aplicativo Microsoft Teams. Para fazer isso, você carregará o arquivo de manifesto do aplicativo que baixou da página Configurações da Equipe de Plug-in-loco do Microsoft 365 na etapa anterior.

Antes de instalar o aplicativo, você precisará garantir que os aplicativos externos e o carregamento de aplicativos estão habilitados. Para fazer isso, você pode seguir as etapas na documentação de locatários do [Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) do Teams. Depois de garantir que os aplicativos externos estão habilitados, você pode seguir as etapas abaixo para implantar seu aplicativo:

1. Abra **o Microsoft Teams.** 

1. Selecione o **ícone** do aplicativo na área inferior esquerda da barra de navegação.

1. Selecione o **link Carregar um aplicativo** personalizado na lista de opções.

> [!Note]
> Se estiver conectado como um administrador global, você terá a opção de carregar o aplicativo no catálogo de aplicativos da sua organização, caso contrário, só poderá carregar o aplicativo para uma equipe da qual você é membro.

4. Selecione o `manifest.zip` pacote baixado anteriormente e selecione **Salvar.** Se você não tiver baixado o pacote de manifesto  do aplicativo, poderá fazer isso na guia Configurações da Equipe da página de configuração do plug-in no M chrome.

Agora que o aplicativo está instalado, você pode adicionar a guia a qualquer canal ao que tenha acesso. Para fazer isso, navegue até  o canal, selecione o símbolo de adição (➕) e selecione seu aplicativo na lista. Siga os prompts para concluir a adição da guia do curso M meio-guia a um canal.

## <a name="step-5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>Etapa 5: Permitir a criação automática de guias M play no Microsoft Teams

Embora as guias M meio-lado a lado possam ser criadas manualmente no Microsoft Teams, você pode decidir que elas serão criadas automaticamente quando as equipes são criadas a partir da sincronização do curso. Para fazer isso, você configurará a ID do aplicativo Do Microsoft Teams carregado no M play play:

1. Abra o Microsoft Teams.

1. Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.

1. Localize o aplicativo **Mphone carregado** ➡ selecione o ícone **de** opções ➡ selecione o link **de cópia.**

1. Em um editor de texto, copie o conteúdo. Ele deve conter uma URL como ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Copie a última parte da URL, por exemplo, que é a `00112233-4455-6677-8899-aabbccddeeff` ID do aplicativo Microsoft Teams.

1. No M chrome, abra a **guia do aplicativo Teams M chrome** na página de configuração do Plug-in M meio do Microsoft 365.

1. Colar a ID do aplicativo Microsoft Teams no campo ID do aplicativo Mphone e salvar as alterações.

Agora, quando um curso Desempejo é sincronizado, o Microsoft Teams instalará automaticamente o aplicativo Mphone na equipe, criará uma guia M play play no canal Geral do Teams e o configurará para conter a página de curso para o curso de M meio do qual ele está sincronizado.

### <a name="thats-it-you-and-your-team-can-now-start-working-with-your-moodle-courses-directly-from-microsoft-teams"></a>Isso é tudo. Agora você e sua equipe podem começar a trabalhar com seus cursos M courses diretamente do Microsoft Teams.

Para compartilhar solicitações de recursos ou comentários conosco, visite nossa [página de Voz do Usuário.](https://microsoftteams.uservoice.com/forums/916759-moodle)
