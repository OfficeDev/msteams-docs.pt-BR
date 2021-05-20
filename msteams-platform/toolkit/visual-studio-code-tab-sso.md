---
title: Autenticação de login único com Teams Toolkit e Visual Studio Code para guias
description: Crie uma guia que suporte chamadas de login único e microsoft Graph diretamente dentro de Visual Studio Code com o Microsoft Teams Toolkit
keywords: equipes visual estúdio code toolkit tabs sso graph authentication Azure plataforma de identidade
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 11e642ce335dae4344f1c730b73763e9172fd76c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566828"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Autenticação de login único com Teams Toolkit e Visual Studio Code para guias

O Microsoft Teams Toolkit permite criar autenticação SSO (Single Sign-on) para aplicativos de guia diretamente dentro de Visual Studio Code. O kit de ferramentas orienta você durante o processo e fornece tudo o que você precisa, incluindo fornecer seu registro de plataforma de identidade da Microsoft no portal Azure.

## <a name="get-started--create-a-project"></a>Comece — crie um projeto

1. Crie um novo projeto no kit de ferramentas.
1. Selecione a guia como o tipo de extensão que você gostaria de criar.
1. Selecione a opção para suportar OSO.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de atividades Visual Studio Code. Caso não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para fácil acesso.

## <a name="configure-your-project"></a>Configure seu projeto

1. Para habilitar o SSO dentro Teams, seu aplicativo deve ter um recurso de registro de aplicativo Azure. O Teams Toolkit irá providenciar o registro do aplicativo em seu nome.
1. Digite a URL onde seu aplicativo será hospedado e selecione **o próximo**. Seu registro de aplicativo será configurado usando a URL fornecida.
1. Os detalhes de configuração do registro do aplicativo serão `.env` armazenados nos arquivos no código-fonte do seu projeto.

Se você quiser saber mais sobre como seu registro de aplicativo do Azure será provisionado, _consulte_  nosso [suporte de login único (SSO) para](../tabs/how-to/authentication/auth-aad-sso.md) documentação de guias.

> [!TIP]
> Você precisará ir aos **Registros de Aplicativos do Azure** e atualizar sua *API URI* e *redirecionar URLs* sempre que você alterar esta URL.

## <a name="run-your-project"></a>Execute seu projeto

1. Selecione **a instalação npm** da `api-server` pasta. Então **npm começar**.
1. Selecione **a instalação npm** da `.src` pasta. Então **npm começar**.
1. Se você estiver usando um serviço de tunelamento como [ngrok,](https://ngrok.com/)execute-o e certifique-se de que a URL corresponda ao que você inseriu no assistente de criação do projeto. Se isso não acontecer, você precisará atualizar sua _API URI_ e _redirecionar_ URL no registro do aplicativo que foi criado no Azure.
1. Navegue até a barra de atividade no lado esquerdo da janela Visual Studio Code.
1. Selecione o ícone **Executar** para exibir a **exibição de Executar e Depurar.**
1. Você também pode usar o atalho de teclado **Ctrl+Shift+D**.

> [!TIP]
> Você pode não ver o aplicativo instalar diálogo no navegador se as janelas pop-up forem desativadas para o seu navegador. Se isso acontecer, habilite janelas pop-up e atualize a página.

## <a name="see-also"></a>Confira também

- [Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio Code](visual-studio-code-overview.md)
