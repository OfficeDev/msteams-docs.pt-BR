---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração do Moodle para Microsoft Teams
keywords: Teams plug-ins de integração do aplicativo Moodle
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: cbce3d51d902301f6aca422bfe2c8112e50f6b31
ms.sourcegitcommit: 6f1bd36b1071e256bdc14e6ccb31dfdda9ca6d6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66049001"
---
# <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Neste artigo, você aprenderá a instalar o Moodle LMS.

> [!NOTE]
> Para ajudar os administradores de TI a configurar facilmente a integração do Moodle e do Teams, os plug-ins de software livre Microsoft 365 Moodle são atualizados para o seguinte:
>
> * Registro automático do servidor Moodle com [Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Implantação com um clique do bot do Assistente do Moodle no Azure.
>
> * Provisionamento automático de equipes e sincronização automática de registros de equipe para todos ou selecionar cursos do Moodle.
>
> * Instalação automática da guia Moodle e do bot do assistente do Moodle em cada equipe sincronizada.
>
> Para saber mais sobre a funcionalidade que essa integração fornece, [consulte Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

Estes são os pré-requisitos para instalar o Moodle:

* Credenciais de administrador do Moodle.

* Azure AD credenciais de administrador.

* Uma assinatura do Azure em que você pode criar novos recursos.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Instalar os plug-ins Microsoft 365 Moodle

A integração do Moodle Microsoft Teams é alimentada pelo conjunto código aberto [Microsoft 365 plug-ins do Moodle](https://github.com/Microsoft/o365-moodle).

### <a name="requisite-applications-and-plugins"></a>Aplicativos e plug-ins necessários

Instale e baixe o seguinte antes de continuar com a instalação Microsoft 365 plug-ins do Moodle:

1. Instale uma versão [estável atual do Moodle](https://download.moodle.org/releases/latest/).

1. Baixe e salve o Moodle [OpenID Conexão](https://moodle.org/plugins/auth_oidc) e os [plug-ins Microsoft 365 Integration do Moodle](https://moodle.org/plugins/local_o365) em seu computador local.

    > [!NOTE]
    > A instalação dos plug-ins Conexão OpenID Microsoft 365 Integration é necessária para a integração Teams aplicativo.
    >
    > Além disso, os [plug-ins Microsoft 365 Teams Tema](https://moodle.org/plugins/theme_boost_o365teams) são altamente recomendados.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 plug-ins do Moodle

1. Entre no servidor Moodle como administrador e selecione Administração de **site** no bloco [Configurações localizado no](https://docs.moodle.org/22/en/Settings_block) painel de navegação esquerdo.

1. Selecione a **guia Plug-ins** e, em seguida, **selecione Instalar plug-ins**.

1. Na seção **Instalar plug-ins do arquivo ZIP** , selecione **Escolher um arquivo**.

1. Selecione **Upload uma opção de** arquivo no painel de navegação esquerdo, procure o arquivo que você baixou e selecione **Upload esse arquivo**.

1. Selecione **Administração do site** no painel de navegação esquerdo para retornar ao painel de administração. Role para baixo até os **plug-ins locais** e selecione o link **Microsoft 365 Integração**.

    > [!IMPORTANT]
    >
    > * Mantenha sua página Microsoft 365 configuração de Plug-ins do Moodle aberta em uma guia separada do navegador, pois você precisa retornar a esse conjunto de páginas em todo o processo.  
    >
    > * Se você não tiver um site do Moodle existente, acesse o repositório [Moodle no Azure](https://github.com/azure/moodle) e implante rapidamente uma instância do Moodle e personalize-a de acordo com suas necessidades.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Configurar a conexão entre os plug-ins Microsoft 365 e Azure AD

Você deve configurar a conexão entre os plug-ins Microsoft 365 e Azure AD.

### <a name="requisites"></a>Requisitos

Registre o Moodle como um aplicativo em seu Azure AD, usando o script do PowerShell. O script provisiona o seguinte:

* Um novo Azure AD para seu locatário Microsoft 365, que é usado pelos plug-ins Microsoft 365 Moodle.
* O aplicativo para seu Microsoft 365 locatário, configure as URLs de resposta e as permissões necessárias para o aplicativo provisionado e retorna o `AppID` e `Key`.

Use o gerado e `AppID` na página `Key` de configuração Microsoft 365 plug-ins do Moodle para configurar o site do servidor Moodle com Azure AD.

> [!IMPORTANT]
>
> * O script do PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve concluir a configuração manualmente seguindo as etapas descritas nas páginas de versão do Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) .
>
> * Para obter mais informações sobre como registrar sua instância do Moodle manualmente, consulte [Registrar sua instância do Moodle como um aplicativo](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia Moodle para o fluxo Microsoft Teams informações

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página Microsoft 365 plug-ins de integração, selecione a **guia** Instalação.

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

1. Navegue até o diretório descompactado digitando `cd .../.../Moodle-AzureAD-Powershell` onde `.../...` está o caminho para o diretório.

1. Execute o script do PowerShell:

    1. Digite `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Digite `./Moodle-AzureAD-Script.ps1`.
    1. Entre em sua conta Microsoft 365 administrador na janela pop-up.
    1. Insira o nome do aplicativo Azure AD, por exemplo, plug-ins Moodle ou Moodle.
    1. Insira a URL do servidor Moodle.
    1. Copie a **ID do Aplicativo (`AppID`)** e **a Chave do Aplicativo (`Key`)** geradas pelo script e salve-as.

1. Em seguida, você deve adicionar e `AppID` `Key` aos plug-ins Microsoft 365 Moodle. Retorne à página de administração de plug-ins, Administração de site > Plug-ins > Microsoft 365 Integração.

1. Na guia **Instalação** , adicione o `AppID` e você `Key` copiou anteriormente e selecione **Salvar alterações**. Depois que a página for atualizada, você poderá ver uma nova seção Escolher **método de conexão**.

1. No método **Escolher conexão, marque** a caixa de seleção rotulada **como Padrão** e, em seguida, **selecione Salvar alterações** novamente.

1. Depois que a página for atualizada, você poderá ver outra nova seção de consentimento do **administrador & informações adicionais**.
    1. Selecione **Fornecer Consentimento do Administrador**, insira suas Microsoft 365 de Administrador Global e **aceite para conceder** as permissões.
    1. Ao lado do campo **Azure AD** Locatário, selecione o **botão** Detectar.
    1. Ao lado da **URL OneDrive for Business,** selecione o **botão** Detectar.
    1. Depois que os campos forem preenchidos, selecione o **botão Salvar alterações** novamente.

1. Selecione o **botão Atualizar** para verificar a instalação e, em seguida, **selecione Salvar alterações**.

1. Sincronize os usuários entre o servidor Moodle e Azure AD. Para começar:

    > [!NOTE]
    > Dependendo do seu ambiente, você pode selecionar opções diferentes durante esse estágio.

1. Sincronize os usuários entre o servidor Moodle e Azure AD. Dependendo do seu ambiente, você pode selecionar opções diferentes durante esse estágio. Para começar:
    1. Alterne para **a guia Configurações Sincronização**.

    1. Na seção **Sincronizar usuários com Azure AD**, marque as caixas de seleção que se aplicam ao seu ambiente. Você deve selecionar o seguinte:  

        ✔ Crie contas no Moodle para usuários no Azure AD.

        ✔ Atualize todas as contas no Moodle para usuários no Azure AD.

    1. Na seção **Restrição de Criação de** Usuário, você pode configurar um filtro para limitar os Azure AD que são sincronizados com o Moodle.
    1. A **seção Mapeamento de Campo de** Usuário permite que você personalize o Azure AD para o mapeamento de campo perfil de usuário do Moodle.
    1. Na seção **Teams Sincronização**, você pode optar por criar grupos automaticamente, como equipes para alguns ou todos os cursos existentes do Moodle.

13. Para [validar trabalhos cron](https://docs.moodle.org/310/en/Cron) e execute-os manualmente para a primeira execução, selecione **o link da** página gerenciamento de tarefas agendadas na seção Sincronizar usuários **com Azure AD**. Isso leva você para a página **Tarefas Agendadas** .

    1. Role para baixo e **localize os usuários de sincronização Azure AD** trabalho e selecione **Executar agora**.
    1. Se você optar por criar Grupos com base em cursos existentes, também poderá executar os grupos de usuários Criar **no Microsoft 365** trabalho.

    > [!NOTE]
    >
    > O Moodle [Cron](https://docs.moodle.org/310/en/Cron) é executado de acordo com o agendamento da tarefa. O agendamento padrão é uma vez por dia. No entanto, o cron deve ser executado com mais frequência para manter tudo em sincronia.

1. Retorne à página de administração de plug-ins, administração de **site > Plug-ins > Microsoft 365 Integração** e selecione a **página Teams Configurações** site.

1. Na página **Teams Configurações**, defina as configurações necessárias para habilitar a integração Teams aplicativo.

    1. Para **habilitar o OpenID Conexão**, selecione **o link Gerenciar** Autenticação e selecione o ícone de olho na linha Conexão **OpenId** se ele não estiver disponível.
    1. Para habilitar a inserção de quadros, selecione o link segurança **HTTP** e, em seguida, marque a caixa de seleção ao lado de Permitir **inserção de quadro**.
    1. Para habilitar os serviços Web, que habilitam os recursos da API do Moodle, selecione **o link Recursos** Avançados e, em seguida, marque a caixa de seleção ao lado de Habilitar **serviços Web** .
    1. Para habilitar os serviços externos Microsoft 365, selecione o link **Serviços externos** e, em seguida:  

        ✔ Selecione **Editar** na **linha Moodle Microsoft 365 Webservices**.

        ✔ Marque a caixa de seleção ao lado **de Habilitado e**, em seguida, **selecione Salvar Alterações**

    1. Edite suas permissões de usuário autenticadas para permitir que eles criem tokens de serviço Web.

        ✔ Selecione o **link do usuário autenticado da função de** Edição.

        ✔ Role para baixo e **localize a funcionalidade Criar um token** de serviço Web e marque a **caixa de** seleção Permitir.

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Implantar o Bot do Moodle Assistant no Azure

O bot gratuito de assistente do Moodle para Microsoft Teams ajuda professores e alunos a responder perguntas sobre seus cursos, tarefas, notas e outras informações no Moodle. O bot também envia notificações do Moodle para alunos e professores dentro Teams. O bot é um projeto de software livre mantido pela Microsoft e está disponível no [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
>
> * Implante recursos em sua assinatura do Azure. Todos os recursos foram configurados usando a **camada** gratuita. Dependendo do uso do bot, talvez seja necessário dimensionar esses recursos.
>
> * Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações do bot do Moodle

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade da Microsoft](https://identity.microsoft.com/Landing). Isso permite que o bot se autentique nos pontos de extremidade da Microsoft.

Para registrar seu bot:

1. Vá para a página de administração de plug-ins e selecione **Plug-ins**. Em **Microsoft 365 Integração**, selecione a **Teams Configurações** configuração.

1. Selecione o link **do Portal de Registro de** Aplicativos da Microsoft e entre com sua ID da Microsoft.

1. Insira um nome para seu aplicativo, como MoodleBot, e selecione o **botão** Criar.

1. Copie a **ID do** Aplicativo e cole-a no campo **ID** do Aplicativo de Bot na **página Configurações** Equipe.

1. Selecione o **botão Gerar Nova** Senha. Copie a senha gerada e cole-a no campo Senha do Aplicativo de **Bot** na **página Configurações** Equipe.

1. Role até a parte inferior do formulário e selecione **Salvar Alterações**.

Depois de gerar a ID do aplicativo e a senha, implante o bot no Azure:

> [!div class="checklist"]
>
> * Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como a ID do Aplicativo bot, a Senha do Aplicativo de Bot e o Segredo do Moodle na **Teams Configurações página.** As informações do Azure estão na página **De instalação** .
> * Depois de concluir o formulário, marque a caixa de seleção para concordar com os termos e condições.
> * Selecione **Comprar**. Todos os recursos do Azure são implantados na camada gratuita.

Depois que os recursos tiverem concluído a implantação no Azure, você deverá configurar os plug-ins Microsoft 365 Moodle com um ponto de extremidade de mensagens. Você deve obter o ponto de extremidade do bot no Azure:

1. Entre no [Portal do Microsoft Azure](https://portal.azure.com).

1. No painel esquerdo, selecione Grupos de  recursos e selecione o grupo de recursos que você usou ou criou ao implantar o bot.

1. Selecione o **recurso de Bot do WebApp** na lista de recursos no grupo.

1. Copie o **ponto de extremidade de mensagens** da seção **Visão** geral.

1. No Moodle, abra a **página Configurações** equipe dos plug-ins Microsoft 365 Moodle.

1. No campo **Ponto de Extremidade do Bot** , cole a URL que você acabou de copiar e altere as mensagens *de palavra* para *webhook*. A URL deve aparecer da seguinte maneira: `https://botname.azurewebsites.net/api/webhook`

1. Clique em **Salvar alterações**.

1. Depois de salvar as alterações, volte para a  guia Configurações Equipe, selecione o botão Baixar arquivo  de manifesto e salve o pacote de manifesto do aplicativo em seu computador para uso adicional.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Implantar seu Microsoft Teams aplicativo

Depois que o bot foi implantado no Azure e configurado para se comunicar com o servidor Moodle, você deve implantar seu Microsoft Teams aplicativo. Para fazer isso, você deve carregar o arquivo de manifesto do aplicativo que você baixou da página Microsoft 365 equipe de plug-ins do Moodle Configurações na etapa anterior.

Antes de instalar o aplicativo, você deve garantir a habilitação de aplicativos externos e o carregamento de aplicativos. Para obter mais informações, consulte [Preparar seu Microsoft 365 locatário](../concepts/build-and-test/prepare-your-o365-tenant.md).

Para implantar seu aplicativo:

1. Abra o **Microsoft Teams**.

1. Selecione o **ícone** aplicativo na área inferior esquerda da barra de navegação.

1. Selecione o **Upload um link de aplicativo** personalizado na lista de opções.

   > [!NOTE]
   > Se você estiver conectado como um administrador global, deverá ter a opção de carregar o aplicativo no catálogo de aplicativos da sua organização; caso contrário, você só poderá carregar o aplicativo para uma equipe na qual você é membro.

4. Selecione o `manifest.zip` pacote baixado anteriormente e selecione **Salvar**. Se você não tiver baixado o pacote de manifesto do aplicativo, poderá baixar na guia **Configurações** equipe da página de configuração de plug-ins no Moodle.

Agora que o aplicativo está instalado, você pode adicionar a guia a qualquer canal ao qual tenha acesso. Para fazer isso, navegue até o canal, selecione o símbolo de **adição** (➕) e selecione seu aplicativo na lista. Siga os prompts para concluir a adição da guia de curso do Moodle a um canal.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Permitir a criação automática de guias Moodle no Microsoft Teams

Embora as guias do Moodle sejam criadas manualmente no Microsoft Teams, você pode decidir crie-as automaticamente quando as equipes forem criadas a partir da sincronização do curso. Para fazer isso, você deve configurar a ID do aplicativo Microsoft Teams carregado no Moodle.

Para permitir a criação automática de guias do Moodle:

1. Abra o Microsoft Teams.

1. Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.

1. Localize o aplicativo **Moodle** carregado > selecione o ícone **de** opções > selecionar **o link de cópia**.

1. Em um editor de texto, cole o conteúdo copiado. Ele deve conter uma URL como `https://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff`. Copie a última parte da URL, como `00112233-4455-6677-8899-aabbccddeeff`, que é a ID do Microsoft Teams aplicativo.

1. No Moodle, abra a **guia Teams aplicativo Moodle** na página de configuração Microsoft 365 plug-ins do Moodle.

1. Cole a ID do aplicativo Microsoft Teams no campo ID do aplicativo Moodle e salve as alterações.

Quando um curso do Moodle é sincronizado, o Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral do Teams e configura-o para conter a página do curso do Moodle do qual ele está sincronizado. Agora você pode começar a trabalhar com seus cursos do Moodle diretamente Microsoft Teams.

> [!NOTE]
> Para compartilhar solicitações de recursos ou comentários conosco, visite nossa página [voz do usuário](https://support.microsoft.com/en-us/office/uservoice-pages-430e1a78-e016-472a-a10f-dc2a3df3450a).

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Documentação do Moodle](https://docs.moodle.org/34/en/Installing_plugins).
