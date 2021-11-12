---
title: Introdução ao App Studio para Microsoft Teams
description: Comece a criar ótimos aplicativos no Microsoft Teams usando o App Studio
keywords: introdução ao app studio teams
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 92f24fbb7d4a41a192178ead1e2cb40dd7446b25
ms.sourcegitcommit: 781f34af2a95952bf437d0b7236ae995f4e14a08
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60948632"
---
# <a name="manage-your-apps-with-app-studio-for-microsoft-teams"></a>Gerenciar seus aplicativos com o App Studio para Microsoft Teams

> [!TIP]
> **Experimente o Portal do Desenvolvedor**: o App Studio evoluiu. Configure, distribua e gerencie seus aplicativos Teams com o novo [Portal do Desenvolvedor.](https://dev.teams.microsoft.com/)

O App Studio torna fácil começar a criar ou integrar seus próprios aplicativos Microsoft Teams, quer você desenvolva aplicativos personalizados para sua empresa ou aplicativos SaaS para equipes em todo o mundo, fornecendo um fluxo de criação do manifesto e do pacote para seu aplicativo e fornecendo ferramentas úteis como o Editor de Cartões e uma biblioteca de controle de Reação.

> [!IMPORTANT]
> No momento, o App Studio não está disponível nos seguintes tipos de Teams orgs:
>
> * Nuvem Comunitária Governamental (GCC)
> * CCG Alto
> * DoD

## <a name="installing-app-studio"></a>Instalando o App Studio

O App Studio é um aplicativo do Teams que pode ser encontrado na loja do Teams. Siga este link para baixar diretamente [o App Studio](https://aka.ms/InstallTeamsAppStudio). Você também pode encontrar o aplicativo na loja de aplicativos.

Na loja, procure pelo App Studio.

![Entrada da loja para o app studio](~/assets/images/get-started/storeteamsappstudio.png)

Selecione o bloco App Studio para abrir a página de instalação do aplicativo:

![Configurar o app studio](~/assets/images/get-started/teamsappstudioconfiguration.png)

Selecione **Instalar**.

![app Studio](~/assets/images/get-started/teamsappstudio.png)

Quando estiver no App Studio, clique na guia **Editor de manifesto**, na qual você pode importar um aplicativo existente ou criar um novo aplicativo.

## <a name="app-studio-features"></a>Recursos do App Studio

Esta seção abrange recursos, como conversa, editor de manifesto, detalhes e recursos. Você pode personalizar seus recursos usando a personalização do aplicativo.

### <a name="conversation"></a>Conversa

É aqui que você pode ver como estão os [cartões que cria no App Studio](#card-editor) no Teams quando os testa enviando para si mesmo.

### <a name="manifest-editor"></a>Editor de Manifesto

Conforme mencionado anteriormente, a parte mais significativa de um pacote de aplicativos do Microsoft Teams é seu arquivo manifest.json. Este arquivo, que deve estar em conformidade com o [ esquema do Teams App](~/resources/schema/manifest-schema.md), contém metadados que permitem ao Teams apresentar corretamente seu aplicativo aos usuários.

A guia Editor de Manifestos no App Studio simplifica a criação do manifesto, permitindo que você descreva o aplicativo, carregue seus ícones, adicione recursos do aplicativo e produza um arquivo .zip que pode ser facilmente carregado no Teams para teste ou distribuído para outras pessoas usarem. Observe que o App Studio não produz código funcional para seu aplicativo nem hospeda seu aplicativo. Seu aplicativo já deve estar hospedado e sendo executado na URL listada no manifesto para que o processo de carregamento do aplicativo resulte em um aplicativo funcional.

#### <a name="details"></a>Detalhes

A seção de detalhes do Editor de Manifesto define a descrição de alto nível do aplicativo que você está fazendo. Isso inclui coisas como o nome, a descrição e a identidade visual do aplicativo. Você pode gerar automaticamente um GUID para seu aplicativo e fornecer URLs para sua política de privacidade e termos de uso.

#### <a name="capabilities"></a>Recursos

A seção de recursos do Editor de Manifesto é onde os recursos do aplicativo são definidos e onde os detalhes de cada um desses recursos são listados.

> [!NOTE]
> Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

##### <a name="tabs"></a>Guias

* **Guias da Equipe.** Uma guia de equipe torna-se parte de um canal e fornece acesso rápido a informações e recursos da equipe. Por exemplo, a guia Planner para um canal contém um único plano. A guia Power BI mapeia para um relatório específico. Os usuários podem fazer uma busca detalhada pelo contexto relevante, mas eles não devem ser capazes de navegar fora da guia. Por exemplo, a guia Power BI não habilita a navegação para outros relatórios do Power BI, mas habilita o botão *Ir para o site* que inicia o relatório no site principal do Power BI.

  Para guias de equipe, você deve fornecer uma *URL de configuração* apresentar opções e reunir informações para que os usuários possam personalizar o conteúdo e a experiência da guia. Essa página HTML iframed é exibida quando um usuário adiciona a guia pela primeira vez a um canal.

  Você também deve fornecer outros domínios a partir dos quais a guia espera carregar ou se vincular. 

* **Guias pessoais.** Esta seção permite definir um conjunto de guias que são apresentadas por padrão na experiência do aplicativo pessoal (experiência que um usuário tem com seu aplicativo fora do contexto de uma equipe ou canal). Nesta seção, forneça o nome da guia, um identificador exclusivo, a URL que aponta para a interface do usuário a ser exibida no Teams e, opcionalmente, a URL a ser usada se um usuário optar por exibir a guia em um navegador. Com Teams guias, forneça quaisquer domínios adicionais dos quais a guia espera carregar ou vincular.

##### <a name="bots"></a>Bots

Esta seção permite que você adicione um [bot de conversação](~/bots/what-are-bots.md) ao seu aplicativo. Se você já tiver um bot registrado com o Bot Framework, poderá adicionar esse bot clicando em *Configurar* e fornecendo o nome do bot, a ID do Bot Framework e definindo os escopos em que o bot funcionará.

Se você ainda não registrou um bot com o Bot Framework, clique em **Register** para criar um novo. Depois de terminar de registrar seu bot, volte a esta seção do Editor de Manifesto para inserir seu nome e a ID do Bot Framework.

Depois de fornecer as informações do bot, agora você pode definir opcionalmente uma lista de comandos que seu bot pode sugerir aos usuários. Adicione o nome do comando, uma descrição do comando que indica sua sintaxe e argumentos, e o(s) escopo(s) ao qual este comando deve ser aplicado.

> [!NOTE]
> Se você tiver definido seu bot para dar suporte a apenas um escopo, os comandos especificados para o escopo sem suporte serão ignorados. Você pode editar os escopos que seu bot oferece suporte a qualquer momento.

##### <a name="connectors"></a>Conectores

Esta seção permite adicionar um conector ao aplicativo. Se você já registrou um conector do Office 365, escolha **Configurar** e insira o nome e a ID do conector. Se quiser um novo conector clique em **Registrar** para ser levado até o Painel do Desenvolvedor do Conector em seu navegador.

##### <a name="messaging-extensions"></a>Extensões de Mensagens

[As extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) são uma maneira eficiente para os usuários se envolverem com seu aplicativo no Microsoft Teams. Os usuários podem consultar informações do seu serviço e postar essas informações na forma de cartões, bem no canal ou na conversa de chat.

As extensões de mensagens são da plataforma Bot Framework e exigem que um bot configurado funcione. Se você tiver o nome e a ID do Bot Framework do bot que você gostaria que guiasse a extensão de mensagem, insira-os. Caso contrário, clique em **Registrar** para criar um registro e insira as informações posteriormente. Selecione se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.

Depois de configurar o bot subjacente, defina os comandos e os parâmetros que a extensão de mensagens pode aceitar.

Cada comando requer um título e uma ID. O comando pode conter, opcionalmente, uma descrição para o usuário. Cada comando pode dar suporte a até cinco parâmetros, cada um dos quais requer:

* O nome do parâmetro como ele aparece no cliente Teams e está incluído na solicitação do usuário.
* Um título amigável.
* Uma descrição opcional.

> [!NOTE]
> Para criar extensão de mensagens usando o app studio, consulte [create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).

#### <a name="test-and-distribute"></a>Testar e Distribuir

Depois que você terminar de definir o aplicativo, a seção Testar e Distribuir permite exportar a definição do aplicativo como um arquivo zip, que pode ser compartilhado e carregado no cliente do Teams para teste. Clicar em exportar baixa o arquivo zip como *appname.zip* no seu diretório de download padrão.

##### <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams
Na página inicial do seu projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para os usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams. Seu administrador de TI revisará esses envios. Você pode retornar à página *Publicar* para verificar o status do envio e saber se o aplicativo foi aprovado ou rejeitado pelo administrador de TI. Esse também é o local onde você deverá enviar atualizações para o aplicativo ou cancelar os envios ativos no momento.

### <a name="card-editor"></a>Editor do Cartões

Um cartão é um contêiner para informações curtas ou relacionadas. O Microsoft Teams dá suporte a cartões, que podem ter várias propriedades e anexos. Os cartões são uma maneira fundamental para que bots e conectores retransmitam informações ativas para os usuários. 

Para tornar esse processo mais fácil e menos propenso a erros, a guia Editor de Cartões permite que você crie Cartões Hero ou Cartões de Miniatura usando um formulário e verifique e teste o cartão resultante (exatamente como um usuário o verá) por meio de um bot. Ele também fornece o código JSON, C# ou Node.js correspondente para o cartão que você pode copiar/colar no código-fonte do aplicativo.

Se você já tiver um cartão que gostaria de verificar no Teams, poderá colar o JSON desse cartão na guia JSON em *Adicionar informações do cartão* e enviá-lo para si mesmo para ver como ele fica em um chat.

### <a name="react-control-library"></a>Biblioteca de Controle de Reação

>[!Note]
> Essa React de controle é preterida no futuro. Considere usar os [controles de Fluent-interface](https://microsoft.github.io/fluent-ui-react/) do usuário como uma interface do usuário stardust alternativa anteriormente.

Criar um aplicativo que acompanhe as práticas recomendadas do Teams é uma ótima maneira de dar ao seu aplicativo uma aparência e sensação que se encaixem  perfeitamente com a experiência do cliente do Teams. Os controles da interface do usuário que você usa são essenciais para alcançar esse fim. Para facilitar a criação de uma interface de usuário consistente, o App Studio fornece várias categorias de controles de interface do usuário que seguem princípios de design do Teams.

Exemplos de controles e componentes de Reação correspondentes são fornecidos e estão prontos para usar na criação do aplicativo.

#### <a name="controls"></a>Controles

Os controles incluem:

* Botões
* Listas suspensas
* Caixas de seleção
* Botão de Opção
* Alternâncias
* Áreas de Texto
* Links
* Guias
* Tabelas
* Ícones

## <a name="see-also"></a>Confira também

[Gerenciar seus aplicativos com o Portal do Desenvolvedor para Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)