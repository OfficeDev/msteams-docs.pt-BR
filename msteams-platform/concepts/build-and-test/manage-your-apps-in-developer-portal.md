---
title: Gerencie seus aplicativos com o Portal do Desenvolvedor
description: Neste artigo, saiba como configurar, distribuir e gerenciar seus aplicativos usando o Portal do Desenvolvedor para o Microsoft Teams.
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 02b9272c2c0d325501c28d150ac728230ac65255
ms.sourcegitcommit: 9ebb516ac448627e1deb42e18703791fc2ad583d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68098915"
---
# <a name="manage-your-apps-in-developer-portal"></a>Gerenciar seus aplicativos no Portal do Desenvolvedor

Depois de criar ou carregar seu aplicativo, você pode gerenciar seus aplicativos no Portal do Desenvolvedor com o seguinte:

* [Visão geral](#overview)
* [Configurar](#configure)
* [Avançado](#advanced)
* [Publish](#publish)

## <a name="overview"></a>Visão geral

Na seção **Visão** geral, você pode ver os seguintes componentes para gerenciar seu aplicativo:

* Painel

  * Na seção **Painel** , em **Visão** geral, você pode ver os seguintes componentes para seu aplicativo:
    * **Validação da loja do Teams**: a ferramenta de validação de aplicativo verifica o pacote do aplicativo em relação aos casos de teste que a Microsoft usa ao revisar seu aplicativo.
    * **Comunicado**: Atualizações mais recentes de seus aplicativos no Portal do Desenvolvedor para Teams
    * **Usuários ativos (versão prévia)**: mostra a contagem de usuários ativos
    * **Informações básicas**: mostra a ID do aplicativo, a versão, a versão do manifesto e assim por diante.

    :::image type="content" source="../../assets/images/tdp/dashboard-page.png" alt-text="A captura de tela é um exemplo que mostra a página Visão geral do aplicativo que você criou no Portal do Desenvolvedor para Teams.":::

* Análise

    Na página **Análise** , na **seção Visão** geral, você pode ver o número total de usuários ativos para seu aplicativo. Para obter mais informações, [consulte Analisar o uso do aplicativo](analyze-your-apps-usage-in-developer-portal.md).

## <a name="configure"></a>Configurar

Para instalar e renderizar seu aplicativo no Teams, você deve incluir um conjunto de configurações que o Teams reconhece. Para carregar seus aplicativos no Teams, você precisa ter o manifesto do aplicativo, que contém todos os detalhes do aplicativo para exibir seu aplicativo no Teams. Isso pode ser feito com a ajuda de componentes e ferramentas que estão disponíveis no Portal do Desenvolvedor.

Na seção **Configurar** , você pode ver os seguintes componentes para gerenciar e acessar seu aplicativo:

* **Informações** básicas: esta seção mostra e permite editar o nome do aplicativo, a ID do aplicativo, as descrições, a versão, as informações do desenvolvedor, as URLs do aplicativo, a ID do aplicativo (cliente) e a ID do Microsoft Partner Network.
* **Identidade visual**: esta página mostra os detalhes do ícone do aplicativo.
* **Recursos do** aplicativo: você pode adicionar os seguintes recursos ao seu aplicativo:
  * Aplicativo pessoal
  * Bot
  * Connector
  * Cena
  * Aplicativo de grupo e canal
  * Extensão de mensagem
  * Extensão da reunião
  * Notificação do feed de atividades
* **Permissões**: esta seção permite conceder permissões de dispositivo, permissões de equipe, permissões de chat ou reunião e permissões de usuário para seu aplicativo.
* **Logon único**: o bot registrado no Azure AD dá suporte ao SSO (Sign-On único). Se um bot estiver registrado no Portal do Bot Framework (ou no Portal do Desenvolvedor em Gerenciamento de Bot), esses bots não darão suporte ao SSO e você precisará registrar seu bot no Azure AD para dar suporte ao SSO. Para um bot registrado no Azure AD, adicione o **URI da ID do Aplicativo**. Para obter o URI da ID do aplicativo Azure AD, [consulte Usar a autenticação de SSO para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).
* **Idiomas**: você pode configurar ou alterar o idioma do seu aplicativo.
* **Domínio**: você pode adicionar os domínios para carregar seus aplicativos no cliente do Teams (por exemplo: *.example.com).

:::image type="content" source="../../assets/images/tdp/configure.png" alt-text="A captura de tela é um exemplo que mostra como configurar recursos para gerenciar e acessar seu aplicativo no Portal do Desenvolvedor.":::

## <a name="advanced"></a>Advanced

Na seção **Avançado** , você pode ver os seguintes componentes para gerenciar seu aplicativo no Portal do Desenvolvedor:

* **Owners**

    Cada aplicativo inclui uma página **Proprietários** , na qual você pode compartilhar o registro do aplicativo com outras pessoas em sua organização. Você pode adicionar **a função** administrador **e** operacional para gerenciar quem pode alterar as configurações do seu aplicativo. A **função Operativa** tem as mesmas permissões que a função **administrador** , exceto para excluir um aplicativo.

    Para adicionar um proprietário:

    1. Na seção **Avançado** , selecione **Proprietários**.
    1. Selecione **Adicionar um proprietário**.
    1. Insira um nome e selecione uma ID de usuário na lista suspensa.
    1. Em **Função**, selecione **Agente** ou **Administrador**.
    1. Selecione **Adicionar**.

* **Conteúdo do** aplicativo: você pode configurar seu aplicativo com os seguintes recursos adicionais:
  
  * Indicador de carregamento: exibe um indicador para permitir que os usuários saibam que o conteúdo do aplicativo hospedado (por exemplo: guias e módulos de tarefa) está sendo carregado.
  * Modo de tela inteira: exibe um aplicativo pessoal sem um cabeçalho de aplicativo. Ele só tem suporte para os aplicativos publicados em sua organização.

* **Ambientes**

    Você pode configurar ambientes e variáveis globais para ajudar a fazer a transição do aplicativo do runtime local para a produção. As variáveis globais são usadas em todos os ambientes.

    Para configurar um ambiente:

    1. No Portal do Desenvolvedor, selecione **os Aplicativos** que você está trabalhando.
    1. Vá para **Ambientes na** **seção Avançado** e selecione **+ Adicionar um ambiente**.
    1. Selecione **Adicionar**.

  * **Variáveis globais**

      1. Selecione **Adicionar uma variável global** para criar variáveis de configuração para seu ambiente.

      Para usar variáveis globais:

      Use os nomes de variáveis em vez de valores embutidos em código para definir as configurações do aplicativo.

      1. Insira `{{` em qualquer campo no Portal do Desenvolvedor. Uma lista suspensa com todas as variáveis que você criou para o ambiente escolhido juntamente com as variáveis globais é exibida.  
      1. Antes de baixar o pacote do aplicativo (por exemplo, ao se preparar para publicar na loja do Teams), selecione o ambiente que você deseja usar. As configurações do aplicativo são atualizadas automaticamente com base no ambiente.

* **Plano e preços**: você pode vincular uma oferta de SaaS criada no Partner Center para seu aplicativo.
* **Administração configurações**:
  * Personalização de aplicativo: você pode personalizar seu aplicativo
  * Bloquear aplicativo por padrão: você pode bloquear seu aplicativo por padrão para os usuários até que um administrador de locatários opte por habilite-o.

## <a name="publish"></a>Publicar

Você pode publicar seu aplicativo em sua organização ou na loja do Teams.

* **Publique seu aplicativo na organização**:

   1. Na página Visão **geral do** aplicativo, em **Publicar**, selecione **Publicar na Organização**.
   1. Selecione **Publicar seu Aplicativo**.

* **Publique seu aplicativo na loja**:

   1. Na página Visão **geral do** aplicativo, em **Publicar**, selecione **Publicar na Loja**.
   1. Selecionar **Publicar**.

   > [!NOTE]
   > A ferramenta de validação de aplicativo verifica o pacote do aplicativo em relação aos casos de teste que a Microsoft usa para examinar seu aplicativo. Resolva erros ou avisos e leia a lista **de verificação de envio do** aplicativo antes de enviar seu aplicativo.

   Você pode baixar o pacote do aplicativo **selecionando o botão Baixar pacote do** aplicativo na página Publicar na loja.

* **Pacote do** aplicativo: o pacote do aplicativo descreve como seu aplicativo é configurado, incluindo recursos do aplicativo, recursos necessários e outros atributos importantes no manifesto. A guia Ícone mostra o ícone usado para seu aplicativo.

## <a name="test-your-app-directly-in-teams"></a>Testar seu aplicativo diretamente no Teams

O Portal do Desenvolvedor fornece opções para testar e depurar seu aplicativo:

* Na página **Visão geral** , você pode ver um instantâneo se seu aplicativo está configurado e é validado em casos de teste da loja do Teams.
* O **botão Visualizar no Teams** inicia seu aplicativo rapidamente no cliente do Teams para depuração.

## <a name="use-tools-to-create-app-features"></a>Usar ferramentas para criar recursos de aplicativo

O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar os principais recursos dos aplicativos do Teams. Estas são as ferramentas:

* **Estúdio de cena**: crie [cenas personalizadas do Modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md) para reuniões do Teams.
* **Editor de Cartões Adaptáveis**: crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.
* **Gerenciamento da plataforma de identidade da Microsoft**: registre seus aplicativos com o Azure Active Directory para ajudar os usuários a entrar e fornecer acesso às APIs.
* **Validação de aplicativo da loja do Teams**: verifique o pacote do aplicativo em relação aos casos de teste que a Microsoft usa para examinar seu aplicativo.
* **Gerenciamento de bots**: adicione bots de conversa ao seu aplicativo que se comunicam com os usuários, respondem às suas perguntas e os notificam proativamente sobre alterações e outros eventos.

Para adicionar um bot:

1. No Portal do Desenvolvedor, selecione **Ferramentas** no painel esquerdo.
1. Selecione o **gerenciamento de bot**.
1. Na página Gerenciamento de Bot, selecione **Novo Bot**.
1. Insira o nome e selecione **Adicionar**.

   :::image type="content" source="../../assets/images/tdp/tools-in-dev-portal.png" alt-text="A captura de tela é um exemplo que mostra as ferramentas no portal do desenvolvedor, que ajuda você a criar os principais recursos.":::

No Portal do Desenvolvedor, você pode acessar o Portal do Bot Framework e configurar o bot para atualizar o ícone e outras propriedades.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
