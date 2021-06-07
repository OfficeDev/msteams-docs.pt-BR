---
title: Configuração de aplicativo no Portal do Desenvolvedor
description: Saiba como configurar e gerenciar seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams
keywords: iniciando equipes do portal do desenvolvedor
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: ce290bd7daa46467be279aae7c608321e75e2d57
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763121"
---
# <a name="app-configuration"></a>Configuração do aplicativo

A parte mais significativa de um pacote Microsoft Teams aplicativo é sua manifest.jsno arquivo. Esse arquivo deve estar em conformidade com [o esquema Teams App](~/resources/schema/manifest-schema.md). O manifest.jsno arquivo contém metadados, o que permite Teams apresentar corretamente seu aplicativo aos usuários.

Você pode executar as seguintes ações na seção **Configurar** do Portal do Desenvolvedor:

* Crie um pacote de aplicativo facilmente.
* Descreva o aplicativo.
* Upload seus ícones.
* Produza um .zip para facilitar a distribuição.

> [!NOTE]
> O Portal do Desenvolvedor não produz código funcional para seu aplicativo ou hospeda seu aplicativo. Seu aplicativo já deve estar hospedado e sendo executado na URL listada no manifesto para que o processo de carregamento do aplicativo resulte em um aplicativo funcional.

:::image type="content" source="~/assets/images/tdp/tdp_configure_1.png" alt-text="Captura de tela mostrando a página Configurar Teams Portal do Desenvolvedor.":::

## <a name="basic-information-and-branding"></a>Informações básicas e identidade visual

As **seções Informações** básicas e **Identidade** Visual definem a descrição de alto nível do aplicativo que você está criando. Isso inclui o nome, a descrição e a identidade visual do aplicativo. As informações nesta seção serão usadas na listagem de Teams do aplicativo e no diálogo de instalação do aplicativo.

## <a name="capabilities"></a>Recursos

A **seção Recursos** da Configuração tem os detalhes de recursos do aplicativo listados.

> [!NOTE]
> O recurso de personalização do aplicativo está disponível apenas na visualização do desenvolvedor.
> 
> Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo. Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

A seguir estão os recursos:

:::image type="content" source="~/assets/images/tdp/tdp_capabilities.png" alt-text="Captura de tela mostrando a página Configurar Teams Portal do Desenvolvedor.":::

* **Aplicativo pessoal** 

  Esta seção permite definir um conjunto de guias que são apresentadas por padrão na experiência do aplicativo pessoal, ou seja, a experiência que um usuário tem com seu aplicativo fora do contexto de uma equipe ou canal. Nesta seção, forneça os seguintes detalhes:

  * O nome da guia.
  * Um identificador exclusivo.
  * A URL que aponta para a interface do usuário a ser exibida Teams.
  * A URL a ser usada se um usuário optar por exibir a guia em um navegador. Esta é uma informação opcional.
  * Quaisquer domínios adicionais dos quais a guia espera carregar ou vincular.

* **Aplicativo de grupo e canal**

  Uma Teams se torna parte de um canal e fornece acesso rápido às informações e recursos da equipe. Por exemplo, a guia Planner para um canal contém um único plano, Power BI guia mapeia para um relatório específico. Os usuários podem fazer uma busca detalhada pelo contexto relevante, mas eles não devem ser capazes de navegar fora da guia. Por exemplo, a guia Power BI não habilita a navegação para outros relatórios do Power BI, mas habilita o botão **Ir para o site** que inicia o relatório no site principal do Power BI.

    > [!NOTE]
    > Para as guias de equipe, você deve fornecer uma URL de Configuração para apresentar opções e coletar informações, que o ajudarão a personalizar o conteúdo e a experiência de sua guia. Esta página HTML iframed é exibida quando um usuário adiciona a guia pela primeira vez a um canal.
    > Você também deve fornecer outros domínios a partir dos quais a guia espera carregar ou se vincular. 

* **Bot**

  Esta seção permite que você adicione um [bot de conversação](~/bots/what-are-bots.md) ao seu aplicativo. Se você já tiver um bot registrado com o Bot Framework, poderá adicionar esse bot clicando em **Configurar** e fornecendo o nome do bot, a ID do Bot Framework e definindo os escopos em que o bot funcionará.

  Se você ainda não registrou o bot com a Estrutura de Bot, clique **em Registrar** para criar um novo. Depois de registrar seu bot, volte para esta seção do Editor de Manifesto para inserir seu nome e a ID da Estrutura de Bot.

  Depois de fornecer as informações do bot, agora você pode definir opcionalmente uma lista de comandos que seu bot pode sugerir aos usuários. Adicione o nome do comando, uma descrição do comando que indica sua sintaxe e argumentos, e o(s) escopo(s) ao qual este comando deve ser aplicado.

  Observe que se você tiver definido seu bot para dar suporte apenas a um escopo, os comandos especificados para o escopo sem suporte serão ignorados. Você pode editar os escopos que seu bot oferece suporte a qualquer momento.

* **Connector**

  Esta seção permite adicionar um conector ao aplicativo. Se você já tiver registrado um conector Office 365, selecione **Configurar** e insira o nome e a ID do conector. Se quiser um novo conector clique em **Registrar** para ser levado até o Painel do Desenvolvedor do Conector em seu navegador.

  > [!NOTE]
  > A personalização do aplicativo permite que os administradores alterem a aparência dos aplicativos carregados por meio de bots, extensões de mensagens, guias e conectores. Por exemplo, se o administrador Teams personalizar o nome de um aplicativo de até , o aplicativo aparecerá com o novo `Contoso` `Contoso Agent` nome para os `Contoso Agent` usuários. No entanto, ao adicionar um conector a um chat, na lista, os conectores ainda mostrarão o nome do aplicativo como `Contoso` .

* **Extensões de Mensagens**

  [As extensões de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) são uma maneira eficiente para os usuários se envolverem com seu aplicativo no Microsoft Teams. Os usuários podem consultar informações do seu serviço e postar essas informações na forma de cartões, bem no canal ou na conversa de chat.

  As extensões de mensagens são da plataforma Bot Framework e exigem que um bot configurado funcione. Se você tiver o nome e a ID do Bot Framework do bot que você gostaria que guiasse a extensão de mensagem, insira-os. Caso contrário, clique em *Registrar* para criar um registro e insira as informações posteriormente. Selecione se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.

  Depois de configurar o bot subjacente, defina os comandos e parâmetros que a extensão de mensagens pode aceitar.

  Cada comando requer um título e uma ID. O comando pode conter, opcionalmente, uma descrição para o usuário. Cada comando pode dar suporte a até cinco parâmetros, cada um deles requer o seguinte:

  * O nome do parâmetro como ele aparece no cliente Teams e está incluído na solicitação do usuário.
  * Um título amigável.
  * Uma descrição opcional.

  > [!NOTE]
  > Para criar extensão de mensagens usando o app studio, consulte [create messaging extension using app studio](~/resources/create-messaging-extension-using-appstudio.md).

* **Extensão de reunião**

  TODO: Rajesh R.

* **Cena**

  Cenas no Modo Juntos é um artefato criado pelo desenvolvedor de cena usando o estúdio do Microsoft Scene que reúne as pessoas junto com seu fluxo de vídeo em uma configuração criativa como concebida pelo criador da cena. Em uma configuração de cena concebida, os participantes têm assentos designados com fluxos de vídeo renderizados nesses bancos. Para obter mais informações, [consulte Teams Modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md).

## <a name="permissions"></a>Permissões

Você pode enriquecer seu Teams com recursos de dispositivo nativos, como câmera, microfone e local.

## <a name="languages"></a>Idiomas

Configurar ou alterar os idiomas que seu aplicativo oferece suporte.

## <a name="single-sign-on"></a>Logon Único

Configure seu aplicativo para autenticar usuários com SSO (login único).

## <a name="domains"></a>Domínios

Uma lista de domínios válidos para sites que o aplicativo espera carregar no Teams cliente. Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` . Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` . Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.

Não é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .

Teams aplicativos que exigem que suas próprias URLs do sharepoint funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="advanced"></a>Advanced
Todo por Karthig

### <a name="app-content"></a>Conteúdo do aplicativo
Todo por Karthig

### <a name="first-party-settings"></a>Configurações de primeira parte
Todo por Karthig

## <a name="see-also"></a>Confira também

* [Visão geral do Teams Portal do Desenvolvedor](~/concepts/build-and-test/teams-developer-portal.md)
* [Distribuir Teams Portal do Desenvolvedor](~/concepts/tdp-distribute.md)
* [Ferramentas no Teams Portal do Desenvolvedor](~/concepts/tdp-tools.md)