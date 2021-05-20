---
title: Instalar o Moodle LMS
description: Como instalar e configurar o aplicativo de integração Moodle para Microsoft Teams
keywords: Teams Plugins de integração de aplicativos Moodle
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: d7fddad80ca08fd4ca8dee352cdcbc46e8e97dcd
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566716"
---
# <a name="install-moodle-lms"></a>Instalar o Moodle LMS

Neste artigo você aprenderá como instalar o Moodle LMS.

> [!NOTE]
> Para ajudar os administradores de TI a configurar facilmente o Moodle e a integração Teams, o Microsoft 365 Moodle Plugins de código aberto é atualizado para o seguinte:
>
> * Registro automático do seu servidor Moodle com [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Implantação de um clique do seu bot Moodle Assistant para o Azure.
>
> * Auto-provisionamento de equipes e sincronização automática de matrículas em equipe para todos ou cursos de Moodle.
>
> * Instalação automática da guia Moodle e do bot assistente Moodle em cada equipe sincronizada.
>
> Para saber mais sobre a funcionalidade que essa integração proporciona, consulte [Microsoft Teams e Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Pré-requisitos

A seguir estão os pré-requisitos para instalar o Moodle:

* Credenciais de administrador moodle.

* Credenciais de administrador azure ad.

* Uma assinatura do Azure onde você pode criar novos recursos.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Instale os plugins moodle Microsoft 365

A integração moodle no Microsoft Teams é alimentada pelo conjunto de [plugins Moodle de](https://github.com/Microsoft/o365-moodle)código aberto Microsoft 365 .

### <a name="requisite-applications-and-plugins"></a>Aplicativos e plugins necessários

Certifique-se de instalar e baixar o seguinte antes de prosseguir com a instalação de plugins Microsoft 365 Moodle:

1. Certifique-se de instalar uma [versão estável atual do Moodle](https://download.moodle.org/releases/latest/).

1. Baixe e salve os Conexão Moodle [OpenID](https://moodle.org/plugins/auth_oidc) e os plugins [de Integração Microsoft 365](https://moodle.org/plugins/local_o365) para o seu computador local.

    > [!NOTE]
    > A instalação dos plugins de integração Conexão e Microsoft 365 do OpenID é necessária para a integração Teams.
    >
    > Além disso, os plugins [temáticos Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) são altamente recomendados.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Plugins moodle

1. Faça login no servidor Moodle como administrador e selecione **a administração** do site no [bloco Configurações](https://docs.moodle.org/22/en/Settings_block) localizado no painel de navegação à esquerda.

1. Selecione a guia **Plugins** e selecione **Instalar plugins**.

1. Na **seção Instalar plugins da** seção de arquivos ZIP, selecione **Escolher um arquivo**.

1. Selecione **Upload uma** opção de arquivo no painel de navegação esquerdo, navegue pelo arquivo que você baixou e selecione Upload este **arquivo**.

1. Selecione **a administração** do site no painel de navegação esquerdo para retornar ao painel de administração. Desça até os **plugins locais** e selecione o link **Microsoft 365 Integração.**

    > [!IMPORTANT]
    >
    > * Mantenha sua página de configuração Microsoft 365 Moodle Plugins aberta em uma guia de navegador separada, pois você precisa retornar a este conjunto de páginas durante todo o processo.  
    >
    > * Se você não tiver um site moodle existente, vá para o [Moodle on Azure](https://github.com/azure/moodle) repo e implante rapidamente uma instância moodle e personalize-a às suas necessidades.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a>2. Configure a conexão entre os plugins Microsoft 365 e Azure Active Directory (Azure AD)

Você deve configurar a conexão entre os plugins Microsoft 365 e o Azure AD.

### <a name="requisites"></a>Requisitos

Registre moodle como um aplicativo em seu Azure AD, usando o script PowerShell. O script Powershell fornece o seguinte:

* Um novo aplicativo Azure AD para seu inquilino Microsoft 365, que é usado pelo Microsoft 365 Moodle Plugins.
* O aplicativo para o seu inquilino Microsoft 365, configure as URLs de resposta necessárias e as permissões para o aplicativo provisionado e devote o `AppID` e `Key` .

Use a página de configuração gerada `AppID` e em sua Microsoft 365 `Key` Moodle Plugins para configurar seu site de servidor Moodle com Azure AD.

> [!IMPORTANT]
>
> * O script PowerShell não é atualizado com os itens de configuração mais recentes, portanto, você deve completar a configuração manualmente seguindo as etapas descritas nas páginas de versão Moodle [3.8.0.4 e 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) e [3.8.0.5 e 3.9.2.](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release)
>
> * Para obter mais informações sobre o registro manual da sua instância Moodle, consulte [Registrar sua instância Moodle como um aplicativo](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>A guia Moodle para Microsoft Teams fluxo de informações

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Na página Microsoft 365 plugins Integração, selecione a guia **Configuração.**

1. Selecione o botão **Download PowerShell Script** e salve-o como uma pasta ZIP para o computador local.

1. Prepare o script PowerShell do arquivo ZIP da seguinte forma: 

    1. Baixe e extraia o `Moodle-AzureAD-Powershell.zip` arquivo.
    1. Abra a pasta extraída.
    1. Clique com o botão direito do mouse no `Moodle-AzureAD-Script.ps1` arquivo e selecione **Propriedades**.
    1. Na guia **Geral** da janela Propriedades, selecione a caixa de `Unblock` seleção ao lado do atributo **Segurança** localizado na parte inferior da janela.
    1. Selecione **OK**.
    1. Copie o caminho do diretório para a pasta extraída.

1. Execute o PowerShell como administrador:

    1. Selecione Iniciar.
    1. Digite PowerShell.
    1. Clique com o botão direito do mouse **em Windows PowerShell**.
    1. Selecione **Executar como administrador**.

1. Navegue até o diretório descompactado digitando `cd .../.../Moodle-AzureAD-Powershell` onde está o caminho para o `.../...` diretório.

1. Execute o script PowerShell:

    1. Entre `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` .
    1. Entre `./Moodle-AzureAD-Script.ps1` .
    1. Faça login na sua conta de administrador Microsoft 365 na janela pop-up.
    1. Digite o nome do aplicativo Azure AD, por exemplo, plugins Moodle ou Moodle.
    1. Digite a URL do servidor Moodle.
    1. Copie o ID do **aplicativo ( `AppID` )** e a **chave de aplicativo( `Key` )** gerado pelo script e salve-os.

1. Em seguida, você deve adicionar o `AppID` e `Key` ao Microsoft 365 Moodle Plugins. Retorne à página de administração de plugins, administração do site > Plugins > Microsoft 365 Integration.

1. Na guia **Configuração** adicione a `AppID` e `Key` copiou anteriormente e, em seguida, selecione **Salvar alterações**. Após a atualização da página, você pode ver uma nova seção **Escolha o método de conexão**.

1. No **método Escolher conexão,** selecione a caixa de seleção rotulada **Padrão** e selecione **Salvar alterações** novamente.

1. Após a atualização da página, você pode ver outra nova seção **consentimento do administrador & informações adicionais**.
    1. Selecione Fornecer link **de consentimento de administrador,** digite suas credenciais de administrador global Microsoft 365 e, em seguida, **aceite** conceder as permissões.
    1. Ao lado do campo **Inquilino Azure AD,** selecione o botão **Detectar.**
    1. Ao lado da **URL OneDrive for Business,** selecione o botão **Detectar.**
    1. Após o preenchimento dos campos, selecione novamente o botão **Salvar alterações.**

1. Selecione o botão **Atualizar** para verificar a instalação e selecione **Salvar alterações**.

1. Sincronize os usuários entre o servidor Moodle e o Azure AD. Para começar:

    > [!NOTE]
    > Dependendo do seu ambiente, você pode selecionar diferentes opções durante esta etapa.

1. Sincronize os usuários entre o servidor Moodle e o Azure AD. Dependendo do seu ambiente, você pode selecionar diferentes opções durante esta etapa. Para começar:
    1. Mude para a **guia Sincronizar Configurações**.

    1. Na seção Sincronizar com a seção **Azure AD,** selecione as caixas de seleção aplicáveis ao seu ambiente. Você deve selecionar o seguinte:  

        ✔ Criar contas no Moodle para usuários no Azure AD.

        ✔ Atualize todas as contas no Moodle para usuários no Azure AD.

    1. Na seção **Restrição de Criação do Usuário,** você pode configurar um filtro para limitar os usuários do Azure AD que está sincronizado com o Moodle.
    1. A seção **de mapeamento de campo do usuário** permite personalizar o mapeamento de campo do Azure AD para o Moodle User Profile.
    1. Na seção **Teams Sync,** você pode selecionar para criar automaticamente Grupos, como equipes para alguns ou todos, de seus cursos moodle existentes.

13. Para validar [os trabalhos do cron](https://docs.moodle.org/310/en/Cron) e executá-los manualmente para a primeira execução, selecione o link de página de gerenciamento de **tarefas programadas** na seção Sincronizar com a seção **Azure AD.** Isso leva você à página **Tarefas Programadas.**

    1. Role para baixo e encontre os usuários do Sync com o trabalho **do Azure AD** e selecione **Executar agora**.
    1. Se você selecionar para criar grupos com base em cursos existentes, você também pode executar os **grupos de usuários Criar em Microsoft 365** trabalho.

    > [!NOTE]
    >
    > O Moodle [Cron](https://docs.moodle.org/310/en/Cron) funciona de acordo com o cronograma de tarefas. O cronograma padrão é uma vez por dia. No entanto, o cron deve correr com mais frequência para manter tudo em sincronia.

1. Retorne à página de administração de plugins, **administração do site > Plugins > Microsoft 365 Integration** e selecione a página **Teams Configurações.**

1. Na página **Teams Configurações,** configure as configurações necessárias para ativar a integração Teams aplicativo.

    1. Para ativar **o OpenID Conexão,** selecione o link **Gerenciar autenticação** e selecione o ícone de olho na linha **Conexão OpenId** se ele estiver cinza.
    1. Para ativar a incorporação de quadros, selecione o link **de segurança HTTP** e selecione a caixa de seleção ao lado para permitir a **incorporação do quadro**.
    1. Para habilitar os serviços web, que habilitam os recursos da API Moodle, selecione o link **Recursos Avançados** e, em seguida, certifique-se de que a caixa de seleção ao lado **de Ativar serviços web** seja selecionada.
    1. Para habilitar os serviços externos para Microsoft 365, selecione o link **de serviços externos** e, em seguida,:  

        ✔ Selecione **Editar** na linha **Moodle Microsoft 365 Webservices.**

        ✔ Selecione a caixa de seleção ao lado **habilitada** e selecione **Salvar alterações**

    1. Edite suas permissões autenticadas do usuário para permitir que eles criem tokens de serviço web.

        ✔ Selecione a **função De edição Autenticado** link do usuário.

        ✔ Role para baixo e encontre o recurso **Criar um token de serviço web** e selecione a caixa de seleção **Permitir.**

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Implantar o Moodle Assistant Bot para o Azure

O bot assistente moodle gratuito para Microsoft Teams ajuda professores e alunos a responder perguntas sobre seus cursos, atribuições, notas e outras informações no Moodle. O bot também envia notificações moodle para alunos e professores dentro de Teams. O bot é um projeto de código aberto mantido pela Microsoft, e está disponível em [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
>
> * Implante recursos para sua assinatura do Azure. Todos os recursos foram configurados usando o nível **livre.** Dependendo do uso do seu bot, você pode ter que dimensionar esses recursos.
>
> * Para usar a guia Moodle sem o bot, pule para [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Fluxo de informações do bot Moodle

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Para instalar o bot, você deve registrá-lo na [Plataforma de Identidade Microsoft](https://identity.microsoft.com/Landing). Isso permite que seu bot se autue contra seus pontos finais da Microsoft. 

**Para registrar seu bot**

1. Vá para a página de administração de plugins e, em seguida, selecione **Plugins**. Em **Microsoft 365 Integração**, selecione a **Teams Configurações** guia.

1. Selecione o link do **Portal de Registro de Aplicativos da Microsoft** e faça login com seu ID Microsoft.

1. Digite um nome para o seu aplicativo, como MoodleBot e selecione o botão **Criar.**

1. Copie o **ID do aplicativo** e cole-o no campo **de ID do aplicativo bot** na página Configurações **equipe.**

1. Selecione o botão **Gerar nova senha.** Copie a senha gerada e cole-a no campo Senha do **aplicativo bot** na página **Team Configurações.**

1. Role até a parte inferior do formulário e selecione **Salvar alterações**.

Depois de gerar seu ID e senha do aplicativo, implante seu bot no Azure:

> [!div class="checklist"]
> * Selecione **Implantar no Azure** e preencha o formulário com as informações necessárias, como o ID do aplicativo bot, a senha do aplicativo bot e o segredo moodle na página **Teams Configurações.** As informações do Azure estão na página **Configuração.** 
> * Após preencher o formulário, selecione a caixa de seleção para concordar com os termos e condições.
> * Selecione **Compra**. Todos os recursos do Azure são implantados no nível livre.

Depois que os recursos terminarem a implantação no Azure, você deve configurar os plugins Microsoft 365 Moodle com um ponto final de mensagens. Você deve obter o ponto final do seu bot no Azure:

1. Entre no [portal do Azure](https://portal.azure.com).

1. No painel esquerdo, selecione **grupos de recursos** e selecione o grupo de recursos que você usou ou criou, enquanto implanta seu bot.

1. Selecione o recurso **Do WebApp Bot** na lista de recursos do grupo.

1. Copie o **ponto final de mensagens** da seção **Visão Geral.**

1. Em Moodle, abra a página **de Configurações da equipe** de seus plugins moodle Microsoft 365.

1. No campo **Bot Endpoint** cole a URL que você acabou de copiar e altere as *mensagens* de palavras para *webhook*. A URL deve aparecer da seguinte forma: `https://botname.azurewebsites.net/api/webhook`

1. Selecione **Salvar alterações**.

1. Depois de salvar as alterações, volte para a guia **Team Configurações,** selecione o botão **de arquivo manifesto Download** e salve o pacote manifesto do aplicativo para uso adicional.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Implante seu aplicativo de Microsoft Teams

Depois que seu bot foi implantado no Azure e configurado para falar com seu servidor Moodle, você deve implantar seu aplicativo Microsoft Teams. Para fazer isso, você deve carregar o arquivo manifesto do aplicativo que você baixou da página Microsoft 365 Moodle Plugins Team Configurações na etapa anterior.

Antes de instalar o aplicativo, você deve garantir para habilitar aplicativos externos e upload de aplicativos. Para obter mais informações, consulte [Prepare seu inquilino Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md). 

**Para implantar seu aplicativo** 

1. Aberto **Microsoft Teams**. 

1. Selecione o ícone **App** na área inferior esquerda da barra de navegação.

1. Selecione o Upload um link **de aplicativo personalizado** na lista de opções.

   > [!NOTE]
   > Se você estiver logado como administrador global, você deve ter a opção de carregar o aplicativo para o catálogo de aplicativos da sua organização, caso contrário, você só pode carregar o aplicativo para uma equipe na qual você é um membro.

4. Selecione o `manifest.zip` pacote que você baixou anteriormente e selecione **Salvar**. Se você não baixou o pacote de manifesto do aplicativo, você pode baixar na **guia Team Configurações** da página de configuração de plugins no Moodle.

Agora que você tem o aplicativo instalado, você pode adicionar a guia a qualquer canal a que você tenha acesso. Para isso, navegue até o canal, selecione o símbolo **de mais** (➕) e selecione seu aplicativo na lista. Siga as instruções para terminar de adicionar sua guia de curso Moodle a um canal.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Permitir a criação automática de guias Moodle em Microsoft Teams

Embora as guias Moodle sejam criadas manualmente em Microsoft Teams, você pode decidir criá-las automaticamente quando as equipes são criadas a partir da sincronização do curso. Para fazer isso, você deve configurar o ID do aplicativo Microsoft Teams carregado no Moodle.

**Para permitir a criação automática de guias Moodle**

1. Abra o Microsoft Teams.

1. Selecione o ícone Aplicativos na área inferior esquerda da barra de navegação.

1. Localize o **aplicativo Moodle** carregado > selecione o ícone de **opções** > selecionar **link de cópia**.

1. Em um editor de texto, cole o conteúdo copiado. Ele deve conter uma URL como ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Copie a última parte da URL, como `00112233-4455-6677-8899-aabbccddeeff` , que é o ID do aplicativo Microsoft Teams.

1. No Moodle, abra a guia **do aplicativo Teams Moodle** na sua página de configuração do Microsoft 365 Moodle Plugins.

1. Cole o ID do aplicativo Microsoft Teams no campo de ID do aplicativo Moodle e salve as alterações.

Quando um curso moodle é sincronizado, Microsoft Teams instala automaticamente o aplicativo Moodle na equipe, cria uma guia Moodle no canal Geral de Teams e configura-o para conter a página do curso para o curso Moodle do qual ele é sincronizado. Agora você pode começar a trabalhar com seus cursos moodle diretamente a partir de Microsoft Teams.

> [!NOTE]
> Para compartilhar quaisquer solicitações de recursos ou feedback conosco, visite nossa [página de Voz do Usuário](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Confira também

- [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
- [Moodle](https://moodle.org/)
- [Documentação moodle](https://docs.moodle.org/34/en/Installing_plugins).

