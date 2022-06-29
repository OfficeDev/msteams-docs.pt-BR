---
title: Introdução ao App Studio para Microsoft Teams
description: Neste artigo, você aprenderá a criar e gerenciar seus aplicativos com o App Studio para Microsoft Teams e a instalar o App Studio.
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 6ec2e1dfc064302de096cb356641a773e7dceb35
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485703"
---
# <a name="manage-your-apps-with-app-studio-for-microsoft-teams"></a>Gerenciar seus aplicativos com o App Studio para Microsoft Teams

> [!WARNING]
> **Experimente o Portal do Desenvolvedor**: o App Studio evoluiu. Configure, distribua e gerencie seus aplicativos do Teams com o novo [Portal do Desenvolvedor](https://dev.teams.microsoft.com/). <br> O App Studio será preterido até 01 de agosto de 2022.

O App Studio torna fácil começar a criar ou integrar seus próprios aplicativos Microsoft Teams, quer você desenvolva aplicativos personalizados para sua empresa ou aplicativos SaaS para equipes em todo o mundo, fornecendo um fluxo de criação do manifesto e do pacote para seu aplicativo e fornecendo ferramentas úteis como o Editor de Cartões e uma biblioteca de controle de Reação.

> [!IMPORTANT]
> Atualmente, o App Studio não está disponível nos seguintes tipos de organizações do Teams:
>
> * Nuvem Comunitária Governamental (GCC)
> * CCG Alto
> * DoD

## <a name="installing-app-studio"></a>Instalando o App Studio

O App Studio é um aplicativo do Teams, que pode ser encontrado na loja do Teams. Siga este link para baixar diretamente [o App Studio](https://aka.ms/InstallTeamsAppStudio). Você também pode encontrar o aplicativo na loja de aplicativos.

Na loja, procure pelo App Studio.

:::image type="content" source="../../assets/images/get-started/StoreTeamsAppStudio.png" alt-text="Entrada da loja para o app studio":::

Selecione o bloco App Studio para abrir a página de instalação do aplicativo:

:::image type="content" source="../../assets/images/get-started/teamsAppStudioConfiguration.png" alt-text="Configurar o app studio":::

Selecione **Instalar**.

:::image type="content" source="../../assets/images/get-started/TeamsAppStudio.png" alt-text="app Studio":::

Quando estiver no App Studio, selecione na guia **Editor** de manifesto, na qual você pode importar um aplicativo existente ou criar um novo aplicativo.

## <a name="app-studio-features"></a>Recursos do App Studio

Esta seção aborda recursos, como conversa, editor de manifesto, detalhes e funcionalidades. Você pode personalizar seus recursos usando a personalização do aplicativo.

### <a name="conversation"></a>Conversa

É aqui que você pode ver como estão os [cartões que cria no App Studio](#card-editor) no Teams quando os testa enviando para si mesmo.

### <a name="manifest-editor"></a>Editor de Manifesto

Conforme mencionado anteriormente, a parte mais significativa de um pacote de aplicativos do Teams é seu arquivo manifest.json. Esse arquivo, que deve estar em conformidade com o esquema do [Aplicativo Teams](~/resources/schema/manifest-schema.md), contém metadados, que permitem que o Teams apresente corretamente seu aplicativo aos usuários.

A guia Editor de Manifesto no App Studio simplifica a criação do manifesto, permitindo que você descreva o aplicativo, carregue seus ícones, adicione recursos de aplicativo e produza um arquivo .zip, que pode ser facilmente carregado no Teams para teste ou distribuído para outras pessoas usarem. O App Studio não produz código funcional para seu aplicativo ou hospeda seu aplicativo. Seu aplicativo já deve estar hospedado e sendo executado na URL listada no manifesto para que o processo de carregamento do aplicativo resulte em um aplicativo funcional.

#### <a name="details"></a>Detalhes

A seção de detalhes do Editor de Manifesto define a descrição de alto nível do aplicativo que você está criando. Isso inclui coisas como o nome, a descrição e a identidade visual do aplicativo. Você pode gerar automaticamente um GUID para seu aplicativo e fornecer URLs para sua política de privacidade e termos de uso.

#### <a name="capabilities"></a>Recursos

A seção de recursos do Editor de Manifesto é onde os recursos do aplicativo são definidos e onde os detalhes de cada um desses recursos são listados.

> [!NOTE]
> Como prática recomendada, você deve fornecer diretrizes de personalização para que os usuários e clientes do aplicativo sigam ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).

##### <a name="tabs"></a>Guias

* **Guias da Equipe.** Uma guia de equipe torna-se parte de um canal e fornece acesso rápido a informações e recursos da equipe. Por exemplo, a guia Planner para um canal contém um único plano. A guia Power BI mapeia para um relatório específico. Os usuários podem fazer drill down para o contexto relevante, mas não devem ser capazes de navegar para fora da guia. A guia Power BI, por exemplo, não habilita a navegação para outros relatórios do Power BI, mas habilita o  botão Ir para o site que inicia o relatório no site principal do Power BI.

  Para guias de equipe, você deve fornecer uma *URL de configuração* apresentar opções e reunir informações para que os usuários possam personalizar o conteúdo e a experiência da guia. Essa página HTML iframed é exibida quando um usuário adiciona a guia pela primeira vez a um canal.

  Você também deve fornecer outros domínios a partir dos quais a guia espera carregar ou se vincular. 

* **Guias pessoais.** Você pode definir um conjunto de guias que são apresentadas por padrão na experiência de aplicativo pessoal (experiência que um usuário tem com seu aplicativo fora do contexto de uma equipe ou canal). Nesta seção, forneça o nome da guia, um identificador exclusivo, a URL que aponta para a interface do usuário a ser exibida no Teams e, opcionalmente, a URL a ser usada se um usuário optar por exibir a guia em um navegador. Com as guias do Teams, forneça outros domínios dos quais a guia espera carregar ou vincular.

##### <a name="bots"></a>Bots

Esta seção permite que você adicione um [bot de conversação](~/bots/what-are-bots.md) ao seu aplicativo. Se você já tiver um bot registrado no Bot Framework, poderá adicionar esse bot clicando em Configurar  e fornecendo o nome do bot, a ID do Bot Framework e definindo os escopos em que o bot funciona.

Se você ainda não registrou um bot com o Bot Framework, selecione **Registrar** para criar um novo. Depois de terminar de registrar seu bot, volte a esta seção do Editor de Manifesto para inserir seu nome e a ID do Bot Framework.

Depois de ter fornecido as informações do bot, agora você pode definir opcionalmente uma lista de comandos que seu bot pode sugerir aos usuários. Adicione o nome do comando, uma descrição do comando, que indica sua sintaxe e argumentos e os escopos aos quais esse comando deve se aplicar.

> [!NOTE]
> Se você tiver definido o bot para dar suporte apenas a um escopo, os comandos especificados para o escopo sem suporte serão ignorados. Você pode editar os escopos que seu bot oferece suporte a qualquer momento.

##### <a name="connectors"></a>Conectores

Esta seção permite adicionar um conector ao aplicativo. Se você já registrou um conector do Office 365, escolha **Configurar** e insira o nome e a ID do conector. Se você quiser que um novo conector selecione **Registrar** para ser levado para o Painel do Desenvolvedor do Conector em seu navegador.

##### <a name="message-extensions"></a>Extensões de mensagem

[As extensões de mensagem](~/messaging-extensions/what-are-messaging-extensions.md) são uma maneira poderosa para os usuários se envolverem com seu aplicativo no Teams. Os usuários podem consultar informações do seu serviço e postar essas informações na forma de cartões, bem no canal ou na conversa de chat.

As extensões de mensagem são alimentadas por bots do Bot Framework, portanto, elas exigem um bot configurado para operar. Se você tiver o nome e a ID do Bot Framework do bot que deseja ligar a extensão de mensagem, insira-a. Caso contrário, **selecione Registrar** para criar um e insira as informações posteriormente. Selecione se a configuração de uma extensão de mensagem pode ser atualizada pelo usuário.

Depois de configurar o bot subjacente, defina os comandos e os parâmetros que a extensão de mensagem pode aceitar.

Cada comando requer um título e uma ID. O comando pode conter, opcionalmente, uma descrição para o usuário. Cada comando pode dar suporte a até cinco parâmetros, cada um dos quais requer:

* O nome do parâmetro como ele aparece no cliente do Teams e está incluído na solicitação do usuário.
* Um título amigável.
* Uma descrição opcional.

> [!NOTE]
> Para criar a extensão de mensagem usando o App Studio, consulte [criar a extensão de mensagem usando o App Studio](~/resources/create-messaging-extension-using-appstudio.md).

#### <a name="test-and-distribute"></a>Testar e Distribuir

Depois de terminar de definir seu aplicativo, a seção Testar e Distribuir permite exportar a definição do aplicativo como um arquivo zip, que pode ser compartilhado e carregado no cliente do Teams para teste. Clicar em exportar baixa o arquivo zip como *appname.zip* no seu diretório de download padrão.

##### <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Na página inicial do seu projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para os usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams. O administrador de TI revisa esses envios. Você pode retornar à página *Publicar* para verificar o status do envio e saber se o aplicativo foi aprovado ou rejeitado pelo administrador de TI. Esse também é o local onde você deverá enviar atualizações para o aplicativo ou cancelar os envios ativos no momento.

### <a name="card-editor"></a>Editor do Cartões

Um cartão é um contêiner para informações curtas ou relacionadas. O Teams dá suporte a cartões, que podem ter várias propriedades e anexos. Os cartões são uma maneira fundamental para que bots e conectores retransmitam informações ativas para os usuários.

Para tornar esse processo mais fácil e menos propenso a erros, a guia Editor de Cartões permite que você crie Cartões Hero ou Cartões em Miniatura usando um formulário e verifique e teste o cartão resultante (exatamente como um usuário o verá) por meio de um bot. Ele também fornece o código JSON, C# ou Node.js correspondente para o cartão que você pode copiar/colar no código-fonte do aplicativo.

Se você já tiver um cartão que gostaria de verificar no Teams, poderá colar o JSON desse cartão na guia JSON em *Adicionar informações do cartão* e enviá-lo para si mesmo para ver como ele fica em um chat.

### <a name="react-control-library"></a>Biblioteca de Controle de Reação

>[!Note]
> Essa React de controle de banco de dados é preterida no futuro. Considere usar os [controles react fluent-UI como uma interface do](https://microsoft.github.io/fluent-ui-react/) usuário alternativa anteriormente stardust.

Criar um aplicativo que acompanhe as práticas recomendadas do Teams é uma ótima maneira de dar ao seu aplicativo uma aparência e sensação que se encaixem  perfeitamente com a experiência do cliente do Teams. Os controles da interface do usuário que você usa são essenciais para alcançar esse fim. Para facilitar a criação de uma interface do usuário consistente, o App Studio fornece várias categorias de controles de interface do usuário, que seguem os princípios de design do Teams.

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

## <a name="app-studio-to-developer-portal"></a>App Studio para Portal do Desenvolvedor

O App Studio será preterido, você pode usar o Portal do Desenvolvedor. A tabela a seguir fornece as informações detalhadas dos recursos com suporte no Portal do Desenvolvedor:

| Recursos | App Studio | Portal do Desenvolvedor |
| --- | --- | --- |
| Análise de aplicativo* | ❌ | ✔️ |
| Funcionalidades do aplicativo – Bots | ✔️ | ✔️ |
| Funcionalidades do aplicativo – Conectores | ✔️ | ✔️ |
| Funcionalidades do aplicativo – Extensão de mensagens | ✔️ | ✔️ |
| Funcionalidades do aplicativo – Extensão de reunião | ❌ | ✔️ |
| Funcionalidades do aplicativo – Aplicativos pessoais | ✔️ | ✔️ |
| Funcionalidades do aplicativo – Guias | ✔️ | ✔️ |
| Ambientes de aplicativo | ❌ | ✔️ |
| Idiomas do aplicativo | ✔️ | ✔️ |
| Visualização e download do manifesto do aplicativo | ✔️ | ✔️ |
| Planos de aplicativo e preços | ❌ | ✔️ |
| Publicação de aplicativos | ✔️ | ✔️ |
| Permissões de aplicativos | ❌ | ✔️ |
| Compartilhamento de aplicativos com co-desenvolvedores | ❌ | ✔️ |
| Validação de aplicativo | ✔️ | ✔️ |
| Criar um novo aplicativo | ✔️ | ✔️ |
| Inserir um pacote zip | ✔️ | ✔️ |

\**A análise de aplicativos estará disponível para GA em breve.*

## <a name="see-also"></a>Confira também

[Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md)
