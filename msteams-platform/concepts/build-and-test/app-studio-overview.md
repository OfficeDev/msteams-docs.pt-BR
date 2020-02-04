---
title: Introdução ao app Studio para o Microsoft Teams
description: Introdução à criação de aplicativos ótimos no Microsoft Teams usando o app Studio
keywords: Introdução ao app Studio Teams
ms.date: 03/20/2019
ms.openlocfilehash: 9a88c6be552905a1dbd41d691c160a39f0123710
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672832"
---
# <a name="quickly-develop-apps-with-app-studio-for-microsoft-teams"></a>Desenvolver aplicativos rapidamente com o app Studio para o Microsoft Teams

O app Studio facilita o início da criação ou integração de seus próprios aplicativos do Microsoft Teams, independentemente de você desenvolver aplicativos personalizados para aplicativos de sua empresa ou SaaS para equipes em todo o mundo, simplificando a criação do manifesto e pacote para seu aplicativo e fornecer ferramentas úteis como o editor de cartão e uma biblioteca de controle de reagir.

## <a name="installing-app-studio"></a>Instalando o app Studio

O app Studio é um aplicativo do teams que pode ser encontrado no repositório do teams. Siga este link para download direto: [app Studio](https://aka.ms/InstallTeamsAppStudio) (você também pode encontrar o aplicativo na loja de aplicativos).

Na loja, procure por app Studio.

![Entrada de repositório para o app Studio](~/assets/images/get-started/storeteamsappstudio.png)

Selecione o bloco do App Studio para abrir a página de instalação do aplicativo:

![Configurar o app Studio](~/assets/images/get-started/teamsappstudioconfiguration.png)

Selecione *instalar*.

![App Studio](~/assets/images/get-started/teamsappstudio.png)

Quando estiver no app Studio, clique na guia *Editor de manifesto* , onde você pode importar um aplicativo existente ou criar um novo aplicativo.

## <a name="app-studio-features"></a>Recursos do App Studio

### <a name="conversation"></a>Conversa

É aqui que você pode ver quais [cartões você cria no app Studio](#card-editor) são parecidos no Teams ao testá-los, enviando-os para você mesmo.

### <a name="manifest-editor"></a>Editor de manifesto

Como mencionado anteriormente, a parte mais significativa de um pacote de aplicativos do Microsoft Teams é seu arquivo manifest. JSON. Este arquivo, que deve estar em conformidade com o esquema de aplicativos do Microsoft [Teams](~/resources/schema/manifest-schema.md), contém metadados que permitem que o Microsoft Teams apresente corretamente o aplicativo aos usuários.

A guia Editor de manifesto no app Studio simplifica a criação do manifesto, permitindo que você descreva o aplicativo, carregue seus ícones, adicione recursos de aplicativo e produza um arquivo. zip que pode ser carregado facilmente no Teams para teste ou distribuído para outros usuários. Observe que o app Studio não produz código funcional para seu aplicativo ou hospeda seu aplicativo. Seu aplicativo já deve estar hospedado e em execução na URL listada no manifesto para o processo de carregamento do aplicativo resultar em um aplicativo em funcionamento.

#### <a name="details"></a>Detalhes

A seção detalhes do editor de manifesto define a descrição de alto nível do aplicativo que você está fazendo. Isso inclui itens como o nome do aplicativo, a descrição e a marca visual. Você pode gerar automaticamente um GUID para seu aplicativo e fornecer URLs para sua declaração de privacidade e termos de uso.

#### <a name="capabilities"></a>Funcionalidades

A seção Capabilities do editor de manifesto é onde os recursos do aplicativo são definidos e onde os detalhes de cada uma dessas funcionalidades são listados.

##### <a name="tabs"></a>Guias

* **Guias de equipe.** Uma guia de equipe se torna parte de um canal e fornece acesso rápido a informações e recursos da equipe. Por exemplo, a guia planejador de um canal contém um único plano; a guia Power BI é mapeada para um relatório específico. Os usuários podem se aprofundar no contexto relevante, mas não devem ser capazes de navegar fora da guia. A guia Power BI, por exemplo, não permite a navegação para outros relatórios do Power BI, mas habilita o botão *ir para o site* que inicia o relatório no site principal do Power bi.

  Para guias de equipe, você deve fornecer uma *URL de configuração* para apresentar opções e coletar informações para que os usuários possam personalizar o conteúdo e a experiência da sua guia. Esta página HTML por iframe é exibida quando um usuário adiciona a guia a um canal pela primeira vez.

  Você também deve fornecer todos os domínios adicionais para os quais a guia espera carregar ou vincular.

* **Guias pessoais.** Esta seção permite que você defina um conjunto de guias que são apresentadas por padrão na experiência do aplicativo pessoal (ou seja, a experiência de um usuário com seu aplicativo fora do contexto de uma equipe ou canal). Nesta seção, forneça o nome da guia, um identificador exclusivo, a URL que aponta para a interface do usuário a ser exibida no Microsoft Teams e, opcionalmente, a URL a ser usada se um usuário optar por exibir a guia em um navegador. Como nas guias do Microsoft Teams, forneça todos os domínios adicionais dos quais a guia espera carregar ou vincular.

##### <a name="bots"></a>Bots

Esta seção permite que você adicione um [bot de conversação](~/bots/what-are-bots.md) ao seu aplicativo. Se você já tem um bot registrado na estrutura de bot, é possível adicionar esse bot clicando em *Configurar* e fornecendo o nome do bot, a ID da estrutura do bot e definindo os escopos nos quais o bot funcionará.

Se você ainda não tiver registrado um bot com a estrutura do bot, clique em *registrar* para criar um novo. Após concluir o registro do bot, volte para esta seção do editor de manifesto para inserir seu nome e ID da estrutura de bot.

Depois de fornecer as informações do seu bot, você pode, agora, definir uma lista de comandos que o seu bot pode sugerir aos usuários. Adicione o nome do comando, uma descrição do comando que indica a sintaxe e os argumentos e os escopos aos quais este comando deve ser aplicado.

Observe que, se você tiver definido seu bot para suportar apenas um escopo, os comandos especificados para o escopo sem suporte serão ignorados. Você pode editar os escopos com suporte no bot a qualquer momento.

##### <a name="connectors"></a>Conectores

Esta seção permite que você adicione um conector ao seu aplicativo. Se você já tiver registrado um conector do Office 365, escolha *Configurar* e insira o nome e a ID do conector. Se quiser um novo conector, clique em *registrar* para ser levado para o painel do desenvolvedor do conector no navegador.

##### <a name="messaging-extensions"></a>Extensões de mensagens

[As extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) são uma maneira poderosa para os usuários entrarem com seu aplicativo no Microsoft Teams. Os usuários podem consultar informações do seu serviço e postá-las na forma de cartões, diretamente no canal ou na conversa de chat.

As extensões de mensagens são ativadas pelos bots da estrutura do bot, portanto, elas exigem que um bot configurado opere. Se você tiver o nome e a ID da estrutura de bot do bot que gostaria de poder alimentar a extensão de mensagens, digite-a. Caso contrário, clique em *registrar* para criar uma e insira as informações posteriormente. Selecione se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.

Após a configuração do bot subjacente, defina os comandos e parâmetros que a extensão de mensagens pode aceitar.

Cada comando requer um título e uma ID. Opcionalmente, o comando pode conter uma descrição para o usuário. Cada comando pode suportar até cinco parâmetros, cada um deles requer:

* O nome do parâmetro como ele aparece no cliente Teams e está incluído na solicitação do usuário
* Um título amigável
* Uma descrição opcional

#### <a name="test-and-distribute"></a>Testar e distribuir

Depois de concluir a definição do aplicativo, a seção de teste e distribuição permite exportar a definição do aplicativo como um arquivo zip, que pode ser compartilhado e carregado no cliente do teams para teste. Clique em exportar para baixar o arquivo zip como *AppName. zip* no diretório de download padrão.

### <a name="card-editor"></a>Editor de cartão

Um cartão é um contêiner para partes de informação curtas ou relacionadas. O Microsoft Teams suporta cartões, que podem ter várias propriedades e anexos. Os cartões são uma forma importante para que os bots e conectores transmitam informações acionáveis aos usuários. 

Para tornar esse processo mais fácil e menos propenso a erros, a guia Editor de cartões permite criar cartões herói ou cartões de miniatura usando um formulário e verificar e testar o cartão resultante (exatamente como o usuário veria) por meio de um bot. Ele também fornece o código JSON, C# ou node. js correspondente para o cartão que você pode copiar/colar no código-fonte do seu aplicativo.

Se você já tem um cartão que gostaria de verificar dentro do Teams, você pode colar o JSON para aquele cartão na guia JSON em *adicionar informações sobre o cartão* e enviá-lo para si mesmo para ver a sua aparência em um chat.

### <a name="react-control-library"></a>Biblioteca de controle de reagir

>[!Note]
> Esta biblioteca de controle de reagir será preterida no futuro. Considere usar os [controles de reagir de interface do usuário fluente como uma alternativa](https://microsoft.github.io/fluent-ui-react/) (anteriormente Stardust UI).

A criação de um aplicativo que segue as práticas recomendadas do Microsoft Teams é uma ótima maneira de dar uma aparência ao aplicativo que se ajuste perfeitamente com a experiência do cliente do Microsoft Teams. Os controles de interface do usuário que você usa são fundamentais para atingir essa extremidade. Para facilitar a criação de uma interface do usuário consistente, o app Studio oferece várias categorias de controles da interface do usuário que seguem os princípios de design da equipe.

Exemplos de controles e componentes de reagir correspondentes são fornecidos e prontos para uso na criação do aplicativo.

#### <a name="controls"></a>Controles

Os controles incluem:

* Botões
* Menus suspensos
* Caixas
* Botões de opção
* Alterna
* Áreas de texto
* Links
* Guias
* Tabelas
* Ícones
