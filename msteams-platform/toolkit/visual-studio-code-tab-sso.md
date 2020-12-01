---
title: Autenticação de logon único com o Teams Toolkit e o Visual Studio Code for Tabs
description: Criar uma guia que ofereça suporte a chamadas de logon único e Microsoft Graph diretamente dentro do Visual Studio Code com o Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit guias de autenticação do Azure Graph plataforma de identidade do Azure
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: fe734143975688cd35c510cd68cd0779a2200a18
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49477730"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Autenticação de logon único com o Teams Toolkit e o Visual Studio Code for Tabs

O Microsoft Teams Toolkit permite que você crie autenticação de logon único (SSO) para aplicativos de guia diretamente no Visual Studio Code. O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa, incluindo o provisionamento do registro da plataforma de identidade da Microsoft no portal do Azure.

## <a name="get-started--create-a-project"></a>Introdução — criar um projeto

1. Criar um novo projeto no kit de ferramentas.
1. Selecione Tab como o tipo de extensão que você deseja criar.
1. Selecione a opção para dar suporte ao SSO.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de atividade de código do Visual Studio. Caso contrário, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.

## <a name="configure-your-project"></a>Configurar seu projeto

1. Para habilitar o SSO no Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure. O Teams Toolkit provisionará o registro de aplicativo em seu nome.
1. Insira a URL onde seu aplicativo será hospedado e selecione **Avançar**. O registro do aplicativo será configurado usando a URL fornecida.
1. Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do seu projeto.

Se quiser saber mais sobre como o registro do seu aplicativo do Azure será provisionado, _Confira_  nosso [suporte de logon único (SSO) para a documentação de guias](../tabs/how-to/authentication/auth-aad-sso.md) .

> [!TIP]
> Você precisará ir para **registros de aplicativo do Azure** e atualizar seu *URI de API* e *redirecionar URLs* sempre que você alterar essa URL.

## <a name="run-your-project"></a>Executar o projeto

1. Selecione **NPM instalar** na `api-server` pasta. Em seguida, **NPM iniciar**.
1. Selecione **NPM instalar** na `.src` pasta. Em seguida, **NPM iniciar**.
1. Se você estiver usando um serviço de encapsulamento como o [ngrok](https://ngrok.com/), execute-o e verifique se a URL corresponde ao que você inseriu no assistente de criação de projeto. Caso contrário, você precisará atualizar seu URI de _API_ e _redirecionar a URL_ no registro de aplicativo que foi criado no Azure.
1. Navegue até a barra de atividade no lado esquerdo da janela de código do Visual Studio.
1. Selecione o ícone **executar** para exibir o modo de exibição **executar e depurar** .
1. Você também pode usar o atalho de teclado **Ctrl + Shift + D**.

> [!TIP]
> Você pode não ver a caixa de diálogo instalar aplicativo no navegador se as janelas pop-up estiverem desabilitadas para seu navegador. Se isso acontecer, habilite as janelas pop-up e atualize a página.

> [!div class="nextstepaction"]
> [Saiba mais: criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code](visual-studio-code-overview.md)
