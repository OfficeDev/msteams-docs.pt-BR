---
title: Integrar com o Portal do Desenvolvedor no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como integrar-se ao Portal do Desenvolvedor no Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
ms.openlocfilehash: b54e833f5c8292c0b426e859e63d858102860a47
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617054"
---
# <a name="integrate-with-developer-portal"></a>Integrar com o Portal do Desenvolvedor

Você pode configurar e gerenciar seu aplicativo no portal do desenvolvedor no Kit de Ferramentas do Teams.

## <a name="to-publish-app-using-developer-portal"></a>Para publicar o aplicativo usando o Portal do Desenvolvedor

As etapas a seguir ajudam você a publicar seu aplicativo no Portal do Desenvolvedor:

1. Selecione **o Portal do Desenvolvedor para Teams** em **IMPLANTAÇÃO**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/dev-portal-ttk.png" alt-text="Portal do Desenvolvedor do Teams":::

   Agora o Portal do Desenvolvedor é aberto em um navegador.

1. Entre no portal do [desenvolvedor do Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
1. Importe o pacote do aplicativo em zip e selecione o **aplicativo de Importação** > **de Aplicativos**.
1. Selecione **Publicar** > **Publicar em sua organização**.

## <a name="to-update-manifest-file-and-app-package"></a>Para atualizar o arquivo de manifesto e o pacote do aplicativo

Se houver alterações relacionadas ao arquivo de manifesto do aplicativo Teams, você poderá atualizar o manifesto e publicar o aplicativo do Teams novamente. Para publicar o aplicativo do Teams manualmente, você pode aproveitar o [Portal do Desenvolvedor para o Teams](https://dev.teams.microsoft.com/home).

1. Entre no portal do [desenvolvedor do Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
1. Importe o pacote do aplicativo em zip e selecione o **aplicativo de Importação** > **de Aplicativos**.<br>
   Você precisa substituir o aplicativo que você carregou anteriormente no Portal do Desenvolvedor.
1. Para publicar seu aplicativo, selecione **Publicar** > **Publicar em sua organização**.

Você pode fazer a seguinte configuração no Portal do Desenvolvedor:

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
* **Logon único**: você pode configurar seu aplicativo para autenticar usuários com SSO (logon único).
* **Idiomas**: você pode configurar ou alterar o idioma do seu aplicativo.
* **Domínio**: você pode adicionar os domínios para carregar seus aplicativos no cliente do Teams (por exemplo: *.example.com).

## <a name="see-also"></a>Confira também

* [Portal do Desenvolvedor do Teams](../concepts/build-and-test/teams-developer-portal.md)
* [Gerenciar seus aplicativos no Portal do Desenvolvedor](../concepts/build-and-test/manage-your-apps-in-developer-portal.md)
