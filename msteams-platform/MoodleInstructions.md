---
title: Instalando a integração do Moodle com o Microsoft Teams
description: Como instalar e configurar o aplicativo de integração do Moodle para o Microsoft Teams
keywords: Moodle de integração do aplicativo Teams
ms.date: 01/31/2019
ms.openlocfilehash: 2b48cfb0bbef9a531e69ae5620c11a8258acdc64
ms.sourcegitcommit: 058b7bbd817af5f513e0e018f2ef562dc3086a84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43120294"
---
# <a name="installing-the-moodle-integration-with-microsoft-teams"></a>Instalando a integração do Moodle com o Microsoft Teams

> [!VIDEO https://www.youtube.com/embed/OHlPt22nKoE]

[Moodle](https://moodle.org/), o sistema de gerenciamento de aprendizado (LMS) mais popular e de código-fonte aberto do mundo agora está integrado ao Microsoft Teams! Essa integração ajuda professores e professores a colaborar em torno de cursos do Moodle, fazer perguntas sobre suas notas e notas e permanecer atualizadas com notificações--diretamente no Microsoft Teams!

Para ajudar os administradores de ti a definir facilmente essa integração, atualizamos nosso plug-in do Office 365 Moodle de código aberto com os seguintes recursos:

* Registro automático do seu servidor do Moodle com o Azure AD.
* Implantação de um clique do seu bot Assistant do Moodle para o Azure.
* Provisionamento automático do Microsoft Teams e da sincronização automática de inscrições de equipe para todos ou selecionar cursos do Moodle.
* Instalação automática da guia Moodle e do bot Assistant do Moodle em cada equipe sincronizada. (Em breve)
* Publicação de um clique do aplicativo Moodle em sua loja de aplicativos do Private Teams. (Em breve)

Para saber mais sobre a funcionalidade que essa integração fornece, acesse [aqui](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

Para instalar e configurar este aplicativo, você precisará de:

1. Credenciais de administrador do Moodle
2. Credenciais de administrador do Azure AD
3. Uma assinatura do Azure você pode criar novos recursos no

## <a name="step-1-install-the-office-365-moodle-plugin"></a>Etapa 1: instalar o plug-in Moodle do Office 365

> [!VIDEO https://www.youtube.com/embed/SETEC5nzMgk]

A integração do Moodle no Microsoft Teams é alimentada pelo [conjunto de plug-ins do Office 365 Moodle](https://github.com/Microsoft/o365-moodle)de Open Source. Para instalar o plug-in no servidor do Moodle:

1. Primeiro, baixe o [conjunto de plug-ins do Office 365](https://moodle.org/plugins/pluginversions.php?plugin=local_o365) e salve-o no computador local. Você precisará usar a versão 3,5 ou mais recente.
    * A instalação do plug-in de local_o365 também instalará os plug-ins [auth_oidc](https://moodle.org/plugins/auth_oidc) e [boost_o365Teams](https://moodle.org/plugins/pluginversions.php?plugin=theme_boost_o365teams) .
1. Faça logon no servidor do Moodle como administrador e selecione **Administração de site** no painel de navegação à esquerda.
1. Selecione a guia **plug-ins** e clique em **instalar plugins**.
1. Na seção **instalar o plug-in do arquivo zip** , clique no botão **escolher um arquivo** .
1. Selecione as opções **carregar um arquivo** da navegação à esquerda, procure o arquivo baixado acima e clique em **carregar este arquivo**.
1. Selecione a opção **Administração do site** no painel de navegação à esquerda novamente para retornar ao painel de administração. Role para baixo até os **plug-ins locais** e clique no link **integração do Microsoft Office 365** . Mantenha essa página de configuração aberta em uma guia separada do navegador, como você a usará em todo o resto desse processo.

Você pode encontrar mais informações sobre como instalar os plug-ins do Moodle na [documentação do Moodle](https://docs.moodle.org/34/en/Installing_plugins).

**Observação importante:** Mantenha a página de configuração do plug-in do Office 365 Moodle aberta em uma guia separada do navegador, pois você retornará a este conjunto de páginas durante todo esse processo.

*Ainda não tem um site do Moodle?* Convém conferir o nosso Moodle no [repositório](https://github.com/azure/moodle) do Azure, onde você pode implantar rapidamente uma instância do Moodle no Azure e personalizá-la conforme suas necessidades.

## <a name="step-2-configure-the-connection-between-the-office-365-plugin-and-azure-active-directory"></a>Etapa 2: configurar a conexão entre o plug-in do Office 365 e o Azure Active Directory

> [!VIDEO https://www.youtube.com/embed/FpGEezaJ3SA]

Em seguida, você precisará registrar o Moodle como um aplicativo no Azure Active Directory. Fornecemos um script do PowerShell para ajudá-lo a concluir esse processo. O script do PowerShell provisiona um novo aplicativo do Azure AD para o locatário do Office 365, que será usado pelo plug-in Moodle do Office 365. O script provisionará o aplicativo para o locatário do O365, configurar todas as URLs e permissões de resposta necessárias para o aplicativo provisionado e retornar a AppID e a chave. Você pode usar a AppID e a chave gerados na página de configuração do plugin Moodle do O365 para configurar seu servidor do Moodle com o Azure AD. Se quiser ver as etapas manuais detalhadas que o script do PowerShell está automatizando, você pode encontrá-las na documentação completa [do plug-in](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="moodle-tab-for-microsoft-teams-information-flow"></a>Guia Moodle para o fluxo de informações do Microsoft Teams

<img width="530px" src="~/assets/images/MoodleTabInformationFlow.png" title="Guia Moodle para o fluxo de informações do Microsoft Teams" />

1. Na página plugin de integração do Microsoft Office 365, selecione a guia **configuração** .
1. Clique no botão **baixar script do PowerShell** e salve-o no computador local.
1. Você precisará preparar o script do PowerShell do arquivo ZIP. Para fazer isso:
    * Baixe e extraia `Moodle-AzureAD-Powershell.zip` o arquivo.
    * Abra a pasta extraída.
    * Clique com o `Moodle-AzureAD-Script.ps1` botão direito do mouse no arquivo e selecione **Propriedades**.
    * Na guia **geral** da janela Propriedades, marque a `Unblock` caixa ao lado do atributo de **segurança** na parte inferior.
    * Clique em **OK**.
    * Copie o caminho de diretório da pasta extraída.
1. Em seguida, você executará o PowerShell como administrador:
    * Clique em Iniciar.
    * Digite PowerShell.
    * Clique com o botão direito do mouse em Windows PowerShell.
    * Clique em "executar como administrador".
1. Navegue até o diretório descompactado digitando `cd ...\...\Moodle-AzureAD-Powershell` onde `...\...` é o caminho do diretório.
1. Execute o script do PowerShell por:
    * Inserir `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    * Inserir `.\Moodle-AzureAD-Script.ps1`.
    * Faça logon na sua conta de administrador do O365 na janela pop-up.
    * Insira o nome do aplicativo do Azure AD (ex. Plug-in Moodle/Moodle).
    * Insira a URL do seu servidor do Moodle.
    * Copie a **ID do aplicativo** e a **chave do aplicativo** gerado pelo script e salve-os.
1. Em seguida, você precisará adicionar o ID e a chave ao plug-in Moodle do Office 365. Retorne à página de administração do plug-in (administração do site > plug-ins > Microsoft Office 365 Integration).
1. Na guia **configuração** , adicione a **ID do aplicativo** e a **chave do aplicativo** que você copiou anteriormente e clique em **salvar alterações**.
1. Depois que a página for atualizada, você verá uma nova seção **escolha o método de conexão**. Clique na caixa de seleção rotulada **como padrão** e clique em **salvar alterações** novamente.
1. Depois que a página for atualizada, você verá outro consentimento de administrador de seção novo **& informações adicionais**.
    * Clique no link **fornecer consentimento do administrador** , insira suas credenciais de administrador global do Office3 365 e, em seguida, **aceite** para conceder as permissões.
    * Ao lado do campo **locatário do Azure ad** , clique no botão **detectar** .
    * Ao lado da **URL do onedrive for Business** , clique no botão **detectar** .
    * Após preencher os campos, clique no botão **salvar alterações** novamente.
1. Clique no botão **Atualizar** para verificar a instalação e, em seguida, **salve as alterações**.
1. Em seguida, você precisará sincronizar os usuários entre o seu servidor do Moodle e o Active Directory do Azure. Dependendo do seu ambiente, você pode selecionar opções diferentes durante esse estágio. Observe que a configuração definida aqui será executada com cada execução do Moodle cron (normalmente, uma vez por dia) para manter tudo em sincronia. Para começar:
    * Alternar para a **guia Configurações de sincronização**
    * Na seção **sincronizar usuários com o Azure ad** , marque as caixas de seleção que se aplicam ao seu ambiente. Normalmente, você deve selecionar pelo menos:
        * Criar contas no Moodle para usuários no Azure AD
        * Atualizar todas as contas no Moodle para usuários no Azure AD
    * Na seção **restrição de criação de usuário** , você pode configurar um filtro para limitar os usuários do Azure AD que serão sincronizados com o Moodle.
    * A seção **mapeamento de campos de usuário** permitirá que você personalize o mapeamento de campo de perfil de usuário do Azure ad para Moodle.
    * Na seção **sincronização do Microsoft Teams** , você pode optar por criar automaticamente grupos (ou seja, equipes) para alguns ou todos os seus cursos existentes do Moodle.
1. Para validar os trabalhos cron (e executá-los manualmente, se você quiser para a primeira execução), clique no link da **página de gerenciamento de tarefas agendadas** na seção **sincronizar usuários com o Azure ad** . Isso levará você à página **tarefas agendadas** .
    * Role para baixo e encontre o trabalho de **sincronização de usuários com o Azure Active Directory** e clique em **executar agora**.
    * Se você optar por criar grupos com base em cursos existentes, também poderá executar o trabalho **criar grupos de usuários no Office 365** .
1. Retorne à página Administração do plug-in (administração do site > plug-ins > Microsoft Office 365 Integration) e selecione a página **configurações do teams** . Você precisará definir algumas configurações de segurança para habilitar a integração do aplicativo do teams.
    * Para habilitar o OpenID Connect, clique no link **gerenciar autenticação** e clique no ícone de olho na linha de **conexão OpenID** se estiver acinzentado.
    * Em seguida, você precisará habilitar a inserção de quadros. Clique no link de **segurança http** e, em seguida, clique na caixa de seleção ao lado de **permitir inserção de quadro**.
    * A próxima etapa é habilitar os serviços Web que habilitarão os recursos da API do Moodle. Clique no link **recursos avançados** e, em seguida, certifique-se de que a caixa de seleção ao lado de **habilitar serviços Web** esteja marcada.
    * Por fim, você precisará habilitar os serviços externos para o Office 365. Clique no link **serviços externos** e, em seguida:
        * Clique em **Editar** na linha **Moodle Office 365 WebServices** .
        * Marque a caixa de seleção ao lado de **habilitado**e clique em **salvar alterações**
    * Em seguida, você precisará editar suas permissões de usuário autenticado para permitir que eles criem tokens de serviço Web. Clique no link **Editar usuário autenticado da função** . Role para baixo e encontre o recurso **criar um token de serviço Web** e marque a caixa de seleção **permitir** .

## <a name="step-3-deploy-the-moodle-assistant-bot-to-azure"></a>Etapa 3: implantar o bot do assistente do Moodle no Azure

> [!VIDEO https://www.youtube.com/embed/gbkJxf8FlfY]

O assistente gratuito do Moodle Assistant para o Microsoft Teams ajuda professores e alunos a responder perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle. O bot também envia notificações Moodle para estudantes e professores diretamente no Teams. Este bot é um projeto de código-fonte aberto mantido pela Microsoft e está [disponível no GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
> Nesta seção, você implantará recursos em sua assinatura do Azure e todos os recursos serão configurados usando a camada **gratuita** . Dependendo do uso do bot, talvez seja necessário dimensionar esses recursos.
> Se você deseja usar apenas a guia Moodle sem o bot, pule para a [etapa 4](#step-4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações do bot Moodle

<img width="530px" src="~/assets/images/MoodleBotInformationFlow.png" title="Moodle bot para o fluxo de informações do Microsoft Teams" />

Para instalar o bot, primeiro você precisará registrá-lo na [plataforma de identidade da Microsoft](https://identity.microsoft.com/Landing). Isso permite que seu bot autentique em seus pontos de extremidade da Microsoft. Para registrar seu bot:

1. Retorne à página Administração de plug-in (administração do site > plug-ins > Microsoft Office 365 Integration) e selecione a guia **configurações do teams** .
1. Clique no link do **portal de registro de aplicativos da Microsoft** e faça logon com sua ID da Microsoft.
1. Insira um nome para seu aplicativo (por exemplo, MoodleBot) e clique no botão **criar** .
1. Copie a **ID do aplicativo** e cole-a no campo **ID do aplicativo bot** na página **configurações da equipe** .
1. Clique no botão **gerar nova senha** . Copie a senha gerada e cole-a no campo **senha do aplicativo bot** na página **configurações da equipe** .
1. Role até a parte inferior do formulário e clique em **salvar alterações**.

Agora que você gerou a ID e a senha do aplicativo, é hora de implantar seu bot no Azure. Clique no botão **implantar no Azure** e preencha o formulário com as informações necessárias (a ID do aplicativo bot, a senha do aplicativo bot e o segredo Moodle estão na página **configurações da equipe** e as informações do Azure estão na página **configuração** ). Depois de preencher o formulário, clique na caixa de seleção para concordar com os termos e condições e, em seguida, clique no botão **comprar** (todos os recursos do Azure são implantados na camada gratuita).

Após a implantação dos recursos no Azure, você precisará configurar o plug-in de Moodle do Office 365 com o ponto de extremidade de mensagem. Primeiro, você precisará obter o ponto de extremidade do bot no Azure. Para isso:

1. Se ainda não estiver, faça logon no [portal do Azure](https://portal.azure.com).
2. No painel esquerdo, selecione **grupos de recursos**.
3. Na lista, selecione o grupo de recursos que você acabou de usar (ou criado) durante a implantação do bot.
4. Selecione o recurso **bot do webapp** na lista de recursos do grupo.
5. Copie o **ponto de extremidade de mensagens** da seção **visão geral** .
6. No Moodle, abra a página de **configurações de equipe** do seu plug-in do Office 365 Moodle.
7. No campo **ponto de extremidade do bot** , Cole a URL que você copiou e altere as *mensagens* do Word para *webhook*. A URL agora deve se parecer com`https://botname.azurewebsites.net/api/webhook`
8. Clique em **salvar alterações**
9. Após salvar as alterações, volte para a guia **configurações da equipe** , clique no botão **baixar arquivo de manifesto** e salve o pacote de manifesto no computador (você o usará na próxima seção).

## <a name="step-4-deploy-your-microsoft-teams-app"></a>Etapa 4: implantar seu aplicativo do Microsoft Teams

> [!VIDEO https://www.youtube.com/embed/2rMb7gtM_ZM]

Agora que você tem seu bot implantado no Azure e configurado para falar com o servidor do Moodle, é hora de implantar seu aplicativo Microsoft Teams. Para fazer isso, você carregará o arquivo de manifesto baixado da página Configurações da equipe de plugin do Office 365 Moodle na etapa anterior.

Antes de poder instalar o aplicativo, você precisará verificar se os aplicativos externos e o carregamento de aplicativos estão habilitados. Para fazer isso, você pode seguir [estas etapas](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-tenant). Depois de ter certeza de que os aplicativos externos estão habilitados, você pode seguir as etapas abaixo para implantar seu aplicativo.

1. Abra o Microsoft Teams.
2. Clique no ícone do **repositório** no canto inferior esquerdo da barra de navegação.
3. Clique no link **carregar um aplicativo personalizado** na lista de opções. *Observação:* Se você estiver conectado como um administrador global, terá a opção de carregar o aplicativo para a loja de aplicativos da sua organização, caso contrário, você só poderá carregar o aplicativo para uma equipe da qual você é membro.
4. Selecione o `manifest.zip` pacote que você baixou anteriormente e clique em **salvar**. Se você ainda não tiver baixado o pacote de manifesto, poderá fazê-lo na guia **configurações da equipe** da página configuração do plug-in no Moodle.

Agora que o aplicativo está instalado, você pode adicionar a guia a qualquer canal ao qual você tenha acesso. Para fazer isso, clique no **+** símbolo e selecione seu aplicativo na lista. Siga as instruções para concluir a adição da guia do curso do Moodle a um canal.

Isso é tudo. Você e sua equipe agora podem começar a trabalhar com seus cursos do Moodle diretamente do Microsoft Teams.

Para compartilhar as solicitações de recursos ou comentários conosco, acesse nossa [página de voz do usuário](https://microsoftteams.uservoice.com/forums/916759-moodle).
