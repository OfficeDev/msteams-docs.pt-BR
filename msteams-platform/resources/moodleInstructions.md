---
title: Instalar o Moodle LMS
description: Neste artigo, você aprenderá a instalar e configurar o aplicativo de integração do Moodle para o Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: c2276c720ca4d7014b3317365411a9c3d7fe6a73
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243175"
---
# <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Neste artigo, você aprenderá a instalar o Moodle LMS.

> [!NOTE]
> Para ajudar os administradores de TI a configurar facilmente a integração do Moodle e do Teams, os Plug-ins do Moodle do Microsoft 365 de software livre são atualizados para o seguinte:
>
> * Registro automático do servidor Moodle com [Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Implantação com um clique do bot do Assistente do Moodle no Azure.
>
> * Provisionamento automático de equipes e sincronização automática de registros de equipe para todos ou selecionar cursos do Moodle.
>
> * Instalação automática da guia Moodle e do bot do assistente do Moodle em cada equipe sincronizada.
>
> Para saber mais sobre a funcionalidade que essa integração fornece, consulte [Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

Estes são os pré-requisitos para instalar o Moodle:

* Credenciais de administrador do Moodle.

* Azure AD credenciais de administrador.

* Uma assinatura do Azure em que você pode criar novos recursos.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Instalar os plug-ins do Microsoft 365 Moodle

A integração do Moodle no Microsoft Teams é da plataforma código aberto [plug-ins do Microsoft 365 Moodle.](https://moodle.org/plugins/browse.php?list=set&id=72)

### <a name="requisite-applications-and-plugins"></a>Aplicativos e plug-ins necessários

Instale e baixe o seguinte antes de prosseguir com a instalação dos plug-ins do Microsoft 365 Moodle:

1. Instale uma versão [estável atual do Moodle](https://download.moodle.org/releases/latest/).

1. Baixe e salve o Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) e os plug-ins de Integração do [Microsoft 365](https://moodle.org/plugins/local_o365) em seu computador local.

    > [!NOTE]
    > A instalação dos plug-ins do OpenID Connect e do Microsoft 365 Integration é necessária para a integração do Teams.
    >
    > Além disso, o [plug-in tema do Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) é altamente recomendado.

### <a name="microsoft-365-moodle-plugins"></a>Plug-ins do Microsoft 365 Moodle

1. Baixe os plug-ins, extraia-os e carregue-os em suas pastas correspondentes. Por exemplo, extraia o plug-in do OpenID Connect (auth_oidc) para uma pasta chamada **oidc** e carregue na pasta  de autenticação da raiz do documento do Moodle. 

1. Entre no servidor Moodle como administrador e selecione **Administração do site**.

1. Após a detecção de novos plug-ins a serem instalados, o Moodle deverá redirecionar você para a página instalar novos plug-ins. Se isso não acontecer, na página Administração do **site**, selecione Notificações na  guia Geral, isso  deve disparar a instalação dos plug-ins.

1. Depois que os plug-ins forem instalados, acesse a guia **Plug-ins** na página  Administrador do **site**, selecione o link da seção Autenticação e habilite **o OpenID Connect**. Não há problema em deixar a configuração do plug-in em branco– elas serão preenchidas mais tarde.

1. Na página **Administrador do site** , role para baixo até a seção **Plug-ins locais** e selecione o link **integração do Microsoft 365** .

    > [!IMPORTANT]
    >
    > * Mantenha sua página de configuração de Plug-ins do Microsoft 365 Moodle aberta em uma guia separada do navegador, pois você precisa retornar a esse conjunto de páginas em todo o processo.  
    >
    > * Se você não tiver um site do Moodle existente, acesse o repositório [Moodle no Azure](https://github.com/azure/moodle) e implante rapidamente uma instância do Moodle e personalize-a de acordo com suas necessidades.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Configurar a conexão entre os plug-ins do Microsoft 365 e o Azure AD

Você deve configurar a conexão entre os plug-ins do Microsoft 365 e Azure AD.

### <a name="requisites"></a>Requisitos

Registre o Moodle como um aplicativo em seu Azure AD, usando o script do PowerShell. O script provisiona o seguinte:

* Um novo Azure AD para seu locatário do Microsoft 365, que é usado pelos Plug-ins do Moodle do Microsoft 365.
* O aplicativo para seu locatário do Microsoft 365, configure as URLs de resposta e as permissões necessárias para o aplicativo provisionado e retorna o `AppID` e `Key`.

Use o gerado e `AppID` na página `Key` de configuração de Plug-ins do Microsoft 365 Moodle para configurar o site do servidor Moodle com Azure AD.

> [!IMPORTANT]
>
> * Para obter mais informações sobre como registrar sua instância do Moodle manualmente, consulte [Registrar sua instância do Moodle como um aplicativo](https://docs.moodle.org/400/en/Microsoft_365#Azure_App_Creation_and_Configuration).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia Moodle para o fluxo de informações do Microsoft Teams

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página plug-ins de Integração do Microsoft 365, selecione a **guia** Configuração.

1. Selecione o **botão Baixar Script do PowerShell** e salve-o como uma pasta ZIP no computador local.

1. Prepare o script do PowerShell do arquivo ZIP da seguinte maneira:

    1. Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.
    1. Abra a pasta extraída.
    1. Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades**.
    1. Na guia **Geral** do janela Propriedades, `Unblock` marque a caixa de seleção ao lado do atributo **Segurança** localizado na parte inferior da janela.
    1. Selecione **OK**.
    1. Copie o caminho do diretório para a pasta extraída.

1. Execute o PowerShell como administrador:

    1. Selecione Iniciar.
    1. Digite PowerShell.
    1. Clique com o botão direito **do mouse Windows PowerShell**.
    1. Selecione **Executar como Administrador**.

1. Vá para o diretório descompactado digitando `cd .../.../Moodle-AzureAD-Powershell` onde `.../...` está o caminho para o diretório.

1. Execute o script do PowerShell:

    1. Digite `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Digite `./Moodle-AzureAD-Script.ps1`.
    1. Entre em sua conta de administrador do Microsoft 365 na janela pop-up.
    1. Insira o nome do aplicativo Azure AD, por exemplo, plug-ins Moodle ou Moodle.
    1. Insira a URL do servidor Moodle.
    1. Copie a **ID do Aplicativo (`AppID`)** e **a Chave do Aplicativo (`Key`)** geradas pelo script e salve-as.

1. Em seguida, você deve adicionar e `AppID` aos `Key` Plug-ins do Moodle do Microsoft 365. Retorne à página de administração de plug-ins, administração de site > plug-ins > Integração do Microsoft 365.

1. Na guia **Instalação** , adicione o `AppID` e você `Key` copiou anteriormente e selecione **Salvar alterações**. Depois que a página for atualizada, você poderá ver uma nova seção Escolher **método de conexão**.

1. No método **Escolher conexão, marque** a caixa de seleção rotulada **como Padrão** e, em seguida, **selecione Salvar alterações** novamente.

1. Depois que a página for atualizada, você poderá ver outra nova seção **Administração consentimento & informações adicionais**.
    1. Selecione **Fornecer Administração De** consentimento, insira suas credenciais de Administrador Global do Microsoft 365 e aceite para conceder as  permissões.
    1. Ao lado do campo **Azure AD** Locatário, selecione o **botão** Detectar.
    1. Ao lado da **URL OneDrive for Business,** selecione o **botão** Detectar.
    1. Depois que os campos forem preenchidos, selecione o **botão Salvar alterações** novamente.

1. Selecione o **botão Atualizar** para verificar a instalação e, em seguida, **selecione Salvar alterações**.

1. Sincronize os usuários entre o servidor Moodle e Azure AD. Para começar:

    > [!NOTE]
    > Dependendo do seu ambiente, você pode selecionar opções diferentes durante esse estágio.

    1. Alterne para a **guia Configurações de Sincronização**.

    1. Na seção **Sincronizar usuários com Azure AD**, marque as caixas de seleção que se aplicam ao seu ambiente. Você deve selecionar o seguinte:  

        ✔ Crie contas no Moodle para usuários no Azure AD.

        ✔ Atualize todas as contas no Moodle para usuários no Azure AD.

    1. Na seção **Restrição de Criação de** Usuário, você pode configurar um filtro para limitar os Azure AD que são sincronizados com o Moodle.

1. Para [validar trabalhos cron](https://docs.moodle.org/400/en/Cron) e execute-os manualmente para a primeira execução, selecione **o link da** página gerenciamento de tarefas agendadas na seção Sincronizar usuários **com Azure AD**. Isso leva você para a página **Tarefas Agendadas** .

    1. Role para baixo e **localize os usuários de sincronização Azure AD** trabalho e selecione **Executar agora**.
    1. Se você optar por criar Grupos com base em cursos existentes, também poderá executar o trabalho Criar grupos de usuários **no Microsoft 365** .

    > [!NOTE]
    >
    > O Moodle [Cron](https://docs.moodle.org/310/en/Cron) é executado de acordo com o agendamento da tarefa. O agendamento padrão é uma vez por dia. No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.

1. Retorne à página de administração de plug-ins, administração de **site > Plug-ins > Integração do Microsoft 365** e selecione a página Configurações **do Teams** .

1. Na página Configurações do **Teams** , defina as configurações necessárias para habilitar a integração de aplicativos do Teams clicando no link Verificar configurações do **Moodle** atualizará todas as configurações necessárias para que a integração do Teams funcione. 

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Implantar o Bot do Moodle Assistant no Azure

O bot gratuito de assistente do Moodle para o Microsoft Teams ajuda professores e alunos a responder a perguntas sobre seus cursos, tarefas, notas e outras informações no Moodle. O bot também envia notificações do Moodle para alunos e professores no Teams. O bot é um projeto de software livre mantido pela Microsoft e está disponível no [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
>
> * Implante recursos em sua assinatura do Azure. Todos os recursos foram configurados usando a **camada** gratuita. Dependendo do uso do bot, talvez seja necessário dimensionar esses recursos.
>
> * Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações do bot do Moodle

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade da Microsoft](https://identity.microsoft.com/Landing). Isso permite que o bot se autentique nos pontos de extremidade da Microsoft.

Para registrar seu bot:

1. Vá para a página de administração de plug-ins e selecione **Plug-ins**. Em **Integração do Microsoft 365**, selecione a **guia Configurações do Teams** .

1. Selecione o link **do Portal de Registro de** Aplicativos da Microsoft e entre com sua ID da Microsoft.

1. Insira um nome para seu aplicativo, como MoodleBot, e selecione o **botão** Criar.

1. Copie a **ID do Aplicativo** e cole-a no campo **ID** do Aplicativo de Bot na página **Configurações da** Equipe.

1. Selecione o **botão Gerar Nova** Senha. Copie a senha gerada e cole-a no campo **Senha** do Aplicativo de Bot na página **Configurações da** Equipe.

1. Role até a parte inferior do formulário e selecione **Salvar Alterações**.

Depois de gerar a ID do aplicativo e a senha, implante o bot no Azure:

> [!div class="checklist"]
>
> * Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como a ID do Aplicativo bot, a Senha do Aplicativo de Bot e o Segredo do Moodle na página Configurações **do Teams** . As informações do Azure estão na página **De instalação** .
> * Depois de concluir o formulário, marque a caixa de seleção para concordar com os termos e condições.
> * Selecione **Comprar**. Todos os recursos do Azure são implantados na camada gratuita.

Depois que os recursos tiverem concluído a implantação no Azure, você deverá configurar os plug-ins do Microsoft 365 Moodle com um ponto de extremidade de mensagens. Você deve obter o ponto de extremidade do bot no Azure:

1. Entre no [Portal do Microsoft Azure](https://portal.azure.com).

1. No painel esquerdo, selecione Grupos de  recursos e selecione o grupo de recursos que você usou ou criou ao implantar o bot.

1. Selecione o **recurso de Bot do WebApp** na lista de recursos no grupo.

1. Copie o **ponto de extremidade de mensagens** da seção **Visão** geral.

1. No Moodle, abra a **página Configurações de** Equipe dos plug-ins do Microsoft 365 Moodle.

1. No campo **Ponto de Extremidade do Bot** , cole a URL que você copiou e altere as mensagens *de palavra* para *webhook*. A URL deve aparecer da seguinte maneira: `https://botname.azurewebsites.net/api/webhook`

1. Clique em **Salvar alterações**.

1. Depois de salvar as alterações, volte para a  guia Configurações da Equipe, selecione  o botão Baixar arquivo de manifesto e salve o pacote de manifesto do aplicativo em seu computador para uso adicional.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Implantar seu aplicativo Microsoft Teams

Depois que o bot for implantado no Azure e configurado para se comunicar com o servidor Moodle, você deverá implantar o aplicativo Microsoft Teams. Para fazer isso, você deve carregar o arquivo de manifesto do aplicativo baixado da página Configurações da Equipe de Plug-ins do Microsoft 365 Moodle na etapa anterior.

Antes de instalar o aplicativo, você deve garantir a habilitação de aplicativos externos e o carregamento de aplicativos. Para obter mais informações, consulte [Preparar seu locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md).

Para implantar seu aplicativo:

1. Abra o **Microsoft Teams**.

1. Selecione o **ícone Aplicativos** na área inferior esquerda da barra de navegação.

1. Selecione o **link Gerenciar seus aplicativos** no menu de navegação.

1. Clique **em Publicar um aplicativo** e selecione **Carregar um aplicativo no catálogo de aplicativos da sua organização**.

   > [!NOTE]
   > Se você estiver conectado como um administrador global, deverá ter a opção de carregar o aplicativo no catálogo de aplicativos da sua organização; caso contrário, você só poderá carregar o aplicativo para uma equipe na qual você é membro.

4. Selecione o `manifest.zip` pacote baixado anteriormente e selecione **Salvar**. Se você não tiver baixado o pacote de manifesto do aplicativo, poderá baixar na guia  Configurações da Equipe da página de configuração de plug-ins no Moodle.

Agora que o aplicativo está instalado, você pode adicionar a guia a qualquer canal ao qual tenha acesso. Para fazer isso, vá para o canal, selecione o símbolo de **adição** (➕) e selecione seu aplicativo na lista. Siga os prompts para concluir a adição da guia de curso do Moodle a um canal.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Permitir a criação automática de guias do Moodle no Microsoft Teams

Embora as guias do Moodle sejam criadas manualmente no Microsoft Teams, você pode decidir criar automaticamente quando as equipes são criadas a partir da sincronização do curso. Para fazer isso, você deve configurar a ID do aplicativo Microsoft Teams carregado no Moodle.

Para permitir a criação automática de guias do Moodle:

1. No Moodle, abra a guia **do aplicativo Teams Moodle** na página de configuração de Plug-ins do Microsoft 365 Moodle.

1. Se o aplicativo do Azure tiver a permissão recomendada, para a configuração de **ID do aplicativo Moodle** , ele deverá mostrar um valor detectado automaticamente **, copie** esse valor para a configuração.

1. Se o valor detectado automaticamente não estiver presente, siga a instrução na página para localizar a ID do aplicativo Moodle e preencher a configuração.

Quando um curso do Moodle é sincronizado, o Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral do Teams e o configura para conter a página do curso do Moodle do qual ele é sincronizado. Agora você pode começar a trabalhar com seus cursos do Moodle diretamente do Teams.

> [!NOTE]
> Para compartilhar solicitações de recursos ou comentários conosco, visite nossa página [voz do usuário](https://support.microsoft.com/en-us/office/uservoice-pages-430e1a78-e016-472a-a10f-dc2a3df3450a).

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Documentação do Moodle](https://docs.moodle.org/400/en/Installing_plugins)
* [Página de integração do Microsoft 365 e do Moodle no Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365)
