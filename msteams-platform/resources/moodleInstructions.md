---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração Moodle para Microsoft Teams
keywords: Teams plug-ins de integração do aplicativo Moodle
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: d4a7c150b777702e7724575ac4db04860a281978
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63399202"
---
# <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Neste artigo, você aprenderá a instalar o Moodle LMS.

> [!NOTE]
> Para ajudar os administradores de IT a configurar facilmente o Moodle e Teams integração, os Plug-ins de Moodle de código aberto Microsoft 365 Moodle são atualizados para o seguinte:
>
> * Registro automático do servidor Moodle [com Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Implantação de um clique do bot do Assistente de miojo no Azure.
>
> * Provisionamento automático de equipes e sincronização automática de inscrições de equipe para todos ou selecione Cursos de miojo.
>
> * Instalação automática da guia Moodle e do bot do assistente de miojo em cada equipe sincronizada.
>
> Para saber mais sobre a funcionalidade que essa integração fornece, [consulte Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

A seguir estão os pré-requisitos para instalar o Moodle:

* Credenciais de administrador de miojo.

* Credenciais de administrador do Azure AD.

* Uma assinatura do Azure onde você pode criar novos recursos.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Instalar os plug-ins Microsoft 365 Moodle

A integração de miojo Microsoft Teams é alimentada pelo conjunto de [plug-ins Microsoft 365 Moodle de código aberto](https://github.com/Microsoft/o365-moodle).

### <a name="requisite-applications-and-plugins"></a>Requisito de aplicativos e plug-ins

Certifique-se de instalar e baixar o seguinte antes de prosseguir com a instalação Microsoft 365 plug-ins Moodle:

1. Certifique-se de instalar [uma versão estável atual do Moodle](https://download.moodle.org/releases/latest/).

1. Baixe e salve o Moodle [OpenID Conexão](https://moodle.org/plugins/auth_oidc) e os [plug-ins de integração Microsoft 365](https://moodle.org/plugins/local_o365) no computador local.

    > [!NOTE]
    > A instalação dos plug-ins de integração Conexão e Microsoft 365 OpenID é necessária para Teams integração.
    >
    > Além disso, os [plug-ins Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) são altamente recomendados.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 plug-ins Moodle

1. Entre no servidor Moodle como administrador e selecione Administração de **site** no bloco [Configurações localizado no](https://docs.moodle.org/22/en/Settings_block) painel de navegação esquerdo.

1. Selecione a **guia Plug-ins** e selecione **Instalar plug-ins**.

1. Na seção **Instalar plug-ins do arquivo ZIP** , selecione **Escolher um arquivo**.

1. Selecione **Upload uma opção de** arquivo no painel de navegação esquerdo, procure o arquivo que você baixou e selecione **Upload este arquivo**.

1. Selecione **Administração do site** no painel de navegação esquerdo para retornar ao painel de administração. Role para baixo até os **plug-ins locais** e selecione o link **Microsoft 365 Integração**.

    > [!IMPORTANT]
    >
    > * Mantenha sua Microsoft 365 de configuração do Moodle Plugins aberta em uma guia de navegador separada, pois você precisa retornar a esse conjunto de páginas ao longo do processo.  
    >
    > * Se você não tiver um site Moodle existente, vá para o [Moodle no repo do Azure](https://github.com/azure/moodle) e implante rapidamente uma instância de Moodle e personalize-a de acordo com suas necessidades.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Configurar a conexão entre os plug-ins Microsoft 365 e o Azure AD

Você deve configurar a conexão entre o Microsoft 365 plug-ins e o Azure AD.

### <a name="requisites"></a>Requisitos

Registre Moodle como um aplicativo no Azure AD, usando o script do PowerShell. O script provisiona o seguinte:

* Um novo aplicativo do Azure AD para seu locatário Microsoft 365, que é usado pelo Microsoft 365 Plug-ins de Moodle.
* O aplicativo para seu Microsoft 365 locatário, configurar as URLs de resposta e permissões necessárias para o aplicativo provisionado e retorna o `AppID` e `Key`.

Use a página de `AppID` instalação de `Key` Plug-ins de miojo gerados e em sua página de instalação de Microsoft 365 Moodle para configurar seu site de servidor Moodle com o Azure AD.

> [!IMPORTANT]
>
> * O script do PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve concluir a configuração manualmente seguindo as etapas descritas nas páginas de versão Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) .
>
> * Para obter mais informações sobre como registrar sua instância Moodle manualmente, consulte [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia Moodle para Microsoft Teams de informações

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página Microsoft 365 plug-ins de integração, selecione a **guia** Instalação.

1. Selecione o **botão Baixar Script do PowerShell** e salve-o como uma pasta ZIP no computador local.

1. Prepare o script do PowerShell do arquivo ZIP da seguinte forma:

    1. Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.
    1. Abra a pasta extraída.
    1. Clique com o botão direito do mouse no arquivo `Moodle-AzureAD-Script.ps1` e selecione **Propriedades**.
    1. Na guia **Geral** da janela Propriedades, selecione `Unblock` a caixa de seleção ao lado do atributo **Security** localizado na parte inferior da janela.
    1. Clique em **OK**.
    1. Copie o caminho do diretório para a pasta extraída.

1. Execute o PowerShell como administrador:

    1. Selecione Iniciar.
    1. Digite PowerShell.
    1. Clique com o botão direito **do mouse Windows PowerShell**.
    1. Selecione **Executar como Administrador**.

1. Navegue até o diretório desacortado digitando `cd .../.../Moodle-AzureAD-Powershell` onde `.../...` está o caminho para o diretório.

1. Execute o script do PowerShell:

    1. Insira `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Insira `./Moodle-AzureAD-Script.ps1`.
    1. Entre na sua conta Microsoft 365 administrador na janela pop-up.
    1. Insira o nome do Aplicativo do Azure AD, por exemplo, plug-ins Moodle ou Moodle.
    1. Insira a URL do servidor Moodle.
    1. Copie a **ID do Aplicativo (`AppID`)** **e o Application Key(`Key`)** gerados pelo script e salve-os.

1. Em seguida, você deve adicionar o `AppID` e `Key` ao Microsoft 365 Moodle Plugins. Volte para a página de administração de plug-ins, Administração de site > Plug-ins > Microsoft 365 Integração.

1. Na guia **Instalação** , adicione o `AppID` e `Key` você copiou anteriormente e selecione **Salvar alterações**. Após a atualização da página, você pode ver uma nova seção **Escolher método de conexão**.

1. No método **Escolher conexão**, selecione a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações novamente** .

1. Após a atualização da página, você pode ver outra nova seção **Consentimento do administrador & informações adicionais**.
    1. Selecione **Fornecer o** link Fornecer Consentimento de Administrador, insira Microsoft 365 suas credenciais de Administrador Global e **aceite conceder as** permissões.
    1. Ao lado do **campo Locatário do Azure AD** , selecione o **botão Detectar** .
    1. Ao lado da **URL OneDrive for Business,** selecione o **botão Detectar**.
    1. Depois que os campos preencherem, selecione o **botão Salvar alterações** novamente.

1. Selecione o **botão Atualizar** para verificar a instalação e, em seguida, selecione **Salvar alterações**.

1. Sincronizar usuários entre seu servidor Moodle e o Azure AD. Para começar:

    > [!NOTE]
    > Dependendo do ambiente, você pode selecionar diferentes opções durante este estágio.

1. Sincronizar usuários entre seu servidor Moodle e o Azure AD. Dependendo do ambiente, você pode selecionar diferentes opções durante este estágio. Para começar:
    1. Alternar para a **guia Sincronizar Configurações.**

    1. Na seção **Sincronizar usuários com o Azure AD** , selecione as caixas de seleção que se aplicam ao seu ambiente. Você deve selecionar o seguinte:  

        ✔ Criar contas no Moodle para usuários no Azure AD.

        ✔ Atualize todas as contas no Moodle para usuários no Azure AD.

    1. Na seção **Restrição de Criação de** Usuário, você pode configurar um filtro para limitar os usuários do Azure AD sincronizados com moodle.
    1. A **seção Mapeamento de** Campo do Usuário permite que você personalize o mapeamento de campo do Azure AD para Moodle User Profile.
    1. Na seção **Teams Sincronização**, você pode selecionar para criar automaticamente Grupos, como equipes para alguns ou todos, de seus cursos de Moodle existentes.

13. Para [validar trabalhos de](https://docs.moodle.org/310/en/Cron) cron e execute-os manualmente para a primeira executar, selecione **o link da** página Gerenciamento de tarefas agendadas na seção **Sincronizar usuários com o Azure AD** . Isso o leva à página **Tarefas Agendadas** .

    1. Role para baixo e encontre **o trabalho Sincronizar usuários com o Azure AD** e selecione **Executar agora**.
    1. Se você selecionar criar Grupos com base em cursos existentes, também poderá executar o **trabalho Criar** grupos de usuários Microsoft 365.

    > [!NOTE]
    >
    > O Moodle [Cron](https://docs.moodle.org/310/en/Cron) é executado de acordo com o cronograma da tarefa. O agendamento padrão é uma vez por dia. No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.

1. Retorne à página de administração de plug-ins, administração de **site > Plugins > Microsoft 365 Integração** e selecione a página **Teams Configurações**.

1. Na página **Teams Configurações**, configure as configurações necessárias para habilitar a integração Teams aplicativo.

    1. Para **habilitar o Conexão OpenID**, selecione **o link Gerenciar** Autenticação e selecione o ícone do olho na linha **Conexão OpenId** se estiver esguiçada.
    1. Para habilitar a incorporação de quadro, selecione o link **Segurança HTTP** e selecione a caixa de seleção ao lado **de Permitir a incorporação de quadro**.
    1. Para habilitar os serviços Web, que habilitam os recursos da API Moodle, selecione **o link Recursos** Avançados e, em seguida, verifique se a caixa de seleção ao lado de Habilitar serviços **Web** está selecionada.
    1. Para habilitar os serviços externos para Microsoft 365, selecione o link **Serviços externos** e, em seguida:  

        ✔ Selecione **Editar** na **linha Moodle Microsoft 365 Webservices**.

        ✔ Selecione a caixa de seleção ao lado **de Habilitado** e selecione **Salvar Alterações**

    1. Edite suas permissões de usuário autenticadas para permitir que eles criem tokens de serviço Web.

        ✔ Selecione o **link De usuário autenticado da função de** edição.

        ✔ Role para baixo e encontre **o recurso Criar um token** de serviço Web e selecione a **caixa de** seleção Permitir.

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Implantar o Moodle Assistant Bot no Azure

O bot de assistente de miojo gratuito para Microsoft Teams ajuda professores e alunos a responder a perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle. O bot também envia notificações Moodle para alunos e professores no Teams. O bot é um projeto de código aberto mantido pela Microsoft e está disponível no [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
>
> * Implante recursos em sua assinatura do Azure. Todos os recursos foram configurados usando a **camada** gratuita. Dependendo do uso do bot, você pode ter que dimensionar esses recursos.
>
> * Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações de bot de miojo

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade da Microsoft](https://identity.microsoft.com/Landing). Isso permite que o bot se autenture nos pontos de extremidade da Microsoft.

Para registrar seu bot:

1. Vá para a página de administração de plug-ins e selecione **Plug-ins**. Em **Microsoft 365 Integração**, selecione a **guia Teams Configurações**.

1. Selecione o **link do Portal de Registro de Aplicativos da Microsoft** e entre com sua ID da Microsoft.

1. Insira um nome para seu aplicativo, como MoodleBot e selecione o **botão Criar** .

1. Copie a **ID do** Aplicativo e a colar no campo **ID** do Aplicativo Bot na **página Equipe Configurações**.

1. Selecione o **botão Gerar Nova Senha** . Copie a senha gerada e a colar no campo Senha do Aplicativo **Bot** na **página Configurações** Equipe.

1. Role até a parte inferior do formulário e selecione **Salvar Alterações**.

Depois de gerar a ID e a senha do aplicativo, implante seu bot no Azure:

> [!div class="checklist"]
>
> * Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como a ID do Aplicativo Bot, a Senha do Aplicativo Bot e o Segredo do Moodle na página **Teams Configurações.** As informações do Azure estão na página **Instalação** .
> * Depois de concluir o formulário, selecione a caixa de seleção para concordar com os termos e condições.
> * Selecione **Comprar**. Todos os recursos do Azure são implantados na camada gratuita.

Após a conclusão da implantação dos recursos no Azure, você deve configurar os plug-ins Microsoft 365 Moodle com um ponto de extremidade de mensagens. Você deve obter o ponto de extremidade do bot no Azure:

1. Entre no [Portal do Microsoft Azure](https://portal.azure.com).

1. No painel esquerdo, selecione **Grupos** de recursos e selecione o grupo de recursos que você usou ou criou ao implantar o bot.

1. Selecione o **recurso Bot do WebApp** na lista de recursos no grupo.

1. Copie o **Ponto de Extremidade de Mensagens** da seção **Visão** Geral.

1. No Moodle, abra a **página Equipe Configurações** do seu Microsoft 365 Moodle Plugins.

1. No campo **Ponto de Extremidade bot** , cole a URL que você copiou e altere as mensagens *de palavra* para *webhook*. A URL deve aparecer da seguinte forma: `https://botname.azurewebsites.net/api/webhook`

1. Clique em **Salvar alterações**.

1. Depois de salvar as alterações, volte para a guia **Equipe** Configurações, selecione o botão **Baixar** arquivo de manifesto e salve o pacote de manifesto do aplicativo em seu computador para uso posterior.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Implante seu aplicativo Microsoft Teams aplicativo

Depois que seu bot foi implantado no Azure e configurado para falar com seu servidor Moodle, você deve implantar seu Microsoft Teams aplicativo. Para fazer isso, você deve carregar o arquivo de manifesto do aplicativo que você baixou da página Microsoft 365 Equipe de Plug-ins de Moodle Configurações na etapa anterior.

Antes de instalar o aplicativo, você deve garantir a habilitação de aplicativos externos e o carregamento de aplicativos. Para obter mais informações, [consulte Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).

Para implantar seu aplicativo:

1. Abra **Microsoft Teams**.

1. Selecione o **ícone aplicativo** na área inferior esquerda da barra de navegação.

1. Selecione o **Upload um link de aplicativo** personalizado na lista de opções.

   > [!NOTE]
   > Se você estiver conectado como um administrador global, deverá ter a opção de carregar o aplicativo no catálogo de aplicativos da sua organização, caso contrário, você só poderá carregar o aplicativo para uma equipe na qual você é membro.

4. Selecione o `manifest.zip` pacote que você baixou anteriormente e selecione **Salvar**. Se você não tiver baixado o pacote de manifesto do aplicativo, poderá baixar **Configurações guia Equipe** da página de configuração de plug-ins no Moodle.

Agora que você tem o aplicativo instalado, você pode adicionar a guia a qualquer canal ao que tiver acesso. Para fazer isso, navegue até o canal, selecione o símbolo **de adição** (➕) e selecione seu aplicativo na lista. Siga os prompts para concluir a adição de sua guia de curso miojo a um canal.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Permitir a criação automática de guias Moodle no Microsoft Teams

Embora as guias Moodle sejam criadas manualmente no Microsoft Teams, você pode decidir cria-las automaticamente quando as equipes são criadas a partir da sincronização do curso. Para fazer isso, você deve configurar a ID do aplicativo Microsoft Teams carregado no Moodle.

Para permitir a criação automática de guias Moodle:

1. Abra o Microsoft Teams.

1. Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.

1. Localize o aplicativo **Moodle carregado >** selecione o ícone **de** opções > selecione **copiar link**.

1. Em um editor de texto, colar o conteúdo copiado. Ele deve conter uma URL como `https://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff`. Copie a última parte da URL, como `00112233-4455-6677-8899-aabbccddeeff`, que é a ID do Microsoft Teams app.

1. No Moodle, abra **a guia Teams aplicativo Moodle** na página de configuração Microsoft 365 Moodle Plugins.

1. Colar a ID do aplicativo Microsoft Teams no campo ID do aplicativo Moodle e salvar alterações.

Quando um curso Moodle é sincronizado, o Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral do Teams e o configura para conter a página de curso para o curso Moodle a partir do qual é sincronizado. Agora você pode começar a trabalhar com seus cursos de miojo diretamente Microsoft Teams.

> [!NOTE]
> Para compartilhar qualquer solicitação de recurso ou comentários conosco, visite nossa [página User Voice](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Documentação de miojo](https://docs.moodle.org/34/en/Installing_plugins).
