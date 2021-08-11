---
title: Autenticação de login único com Teams Toolkit e Visual Studio Code para guias
description: Crie uma guia que dá suporte a chamadas de logom único Graph Microsoft diretamente no Visual Studio Code com o Microsoft Teams Toolkit
keywords: Guias do kit de ferramentas de código visual studio do teams sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 9854ac7dff400a5ef9b4695eab2f1679966043ac5fe5b65a2df5d4c5c7c6da8b
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707404"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Autenticação de login único com Teams Toolkit e Visual Studio Code para guias

> [!IMPORTANT]
> **Este documento se refere a uma versão antiga do Teams Toolkit**
>
> Para obter informações atuais, leia [os pré-requisitos](../get-started/prerequisites.md) e siga um dos tutoriais mais novos.

A Microsoft Teams Toolkit permite que você crie autenticação de logom único (SSO) para aplicativos de tabulação diretamente no Visual Studio Code. O kit de ferramentas orienta você pelo processo e fornece tudo o que você precisa, incluindo provisionar seu registro plataforma de identidade da Microsoft no portal do Azure.

## <a name="get-started--create-a-project"></a>Começar — criar um projeto

1. Crie um novo projeto no kit de ferramentas.
1. Selecione a guia como o tipo de extensão que você gostaria de criar.
1. Selecione a opção para dar suporte ao SSO.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de Visual Studio Code de atividade. Se não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** fixar o kit de ferramentas para facilitar o acesso.

## <a name="configure-your-project"></a>Configurar seu projeto

1. Para habilitar o SSO Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure. O Teams Toolkit provisione o registro do aplicativo em seu nome.
1. Insira a URL onde seu aplicativo será hospedado e selecione **o próximo**. O registro do aplicativo será configurado usando a URL fornecida.
1. Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do projeto.

Se você quiser saber mais sobre como o registro do aplicativo  do Azure será provisionado, consulte nosso suporte de [SSO (login único)](../tabs/how-to/authentication/auth-aad-sso.md) para obter a documentação de guias.

> [!TIP]
> Você precisará ir para Registros do **Aplicativo do Azure** e atualizar o *URI* da API e redirecionar *URLs* sempre que alterar essa URL.

## <a name="run-your-project"></a>Executar seu projeto

1. Selecione **npm install** na `api-server` pasta. Em **seguida, npm start**.
1. Selecione **npm install** na `.src` pasta. Em **seguida, npm start**.
1. Se você estiver usando um serviço de tunelamento como [ngrok,](https://ngrok.com/)execute-o e certifique-se de que a URL corresponde ao que você entrou no assistente de criação do projeto. Se isso não ocorrer, você precisará atualizar o _URI_ da API e _redirecionar a URL_ no registro do aplicativo criado no Azure.
1. Navegue até a barra de atividades no lado esquerdo da janela Visual Studio Code.
1. Selecione o **ícone Executar** para exibir o **exibição Executar e Depurar.**
1. Você também pode usar o atalho de teclado **Ctrl+Shift+D**.

> [!TIP]
> Você pode não ver o diálogo de instalação do aplicativo no navegador se as janelas pop-up estão desabilitadas para o navegador. Se isso acontecer, habilita as janelas pop-up e atualize a página.

## <a name="see-also"></a>Confira também

[Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code](visual-studio-code-overview.md)
