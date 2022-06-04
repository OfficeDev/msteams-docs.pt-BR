---
title: Autenticação de logon único com o Kit de Ferramentas do Teams e Visual Studio Code para guias
description: Crie uma guia que dê suporte a logon único e chamadas do Microsoft Graph diretamente no Visual Studio Code com o Kit de Ferramentas do Microsoft Teams
keywords: guias do kit de ferramentas do visual studio code do teams para autenticação de grafo de sso da plataforma de identidade do Azure
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: 38ff0e88cabe5f6cf3b8703fba139a525620ee25
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887580"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a>Autenticação de logon único com o Kit de Ferramentas do Teams e Visual Studio Code para guias

> [!IMPORTANT]
> **Este documento refere-se a uma versão antiga do Kit de Ferramentas do Teams**
>
> Para obter informações atuais, leia [os pré-requisitos](../get-started/prerequisites.md) e siga um dos tutoriais mais recentes.

O Microsoft Teams Toolkit permite que você crie autenticação de SSO (logon único) para aplicativos de guia diretamente no Visual Studio Code. O kit de ferramentas orienta você pelo processo e fornece tudo o que você precisa, incluindo o provisionamento do registro da plataforma de identidade da Microsoft no portal do Microsoft Azure.

## <a name="get-started--create-a-project"></a>Introdução – criar um projeto

1. Crie um novo projeto no kit de ferramentas.
1. Selecione a guia como o tipo de extensão que você deseja criar.
1. Selecione a opção para dar suporte ao SSO.

> [!TIP]
> Após a instalação, você deverá ver o Kit de Ferramentas do Teams na barra de atividades do Visual Studio Code. Caso contrário, clique com o botão direito do mouse na barra de atividades e selecione **o Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.

## <a name="configure-your-project"></a>Configurar seu projeto

1. Para habilitar o SSO no Teams, seu aplicativo deve ter um recurso de registro de aplicativo do Azure. O Kit de Ferramentas do Teams provisionará o registro do aplicativo em seu nome.
1. Insira a URL em que seu aplicativo será hospedado e selecione **o próximo**. O registro do aplicativo será configurado usando a URL fornecida.
1. Os detalhes de configuração do registro do aplicativo serão armazenados nos `.env` arquivos no código-fonte do projeto.

Se você quiser saber mais sobre como o registro de aplicativo do Azure será provisionado *, confira*  nosso suporte de [SSO (](../tabs/how-to/authentication/tab-sso-overview.md) logon único) para a documentação de guias.

> [!TIP]
> Você precisará acessar os Registros de **Aplicativo do Azure** e atualizar o *URI da API* e redirecionar *URLs* sempre que alterar essa URL.

## <a name="run-your-project"></a>Executar seu projeto

1. Selecione **a instalação do npm** na `api-server` pasta. Em **seguida, npm start**.
1. Selecione **a instalação do npm** na `.src` pasta. Em **seguida, npm start**.
1. Se você estiver usando um serviço de túnel como [o ngrok](https://ngrok.com/), execute-o e verifique se a URL corresponde ao que você inseriu no assistente de criação do projeto. Caso contrário, você precisará atualizar o *URI da API* e redirecionar *a URL* no registro do aplicativo que foi criado no Azure.
1. Navegue até a barra de atividades no lado esquerdo da janela do Visual Studio Code.
1. Selecione o **ícone** Executar para exibir o **modo de exibição Executar e Depurar** .
1. Você também pode usar o atalho de teclado **Ctrl+Shift+D**.

> [!TIP]
> Talvez você não veja a caixa de diálogo de instalação do aplicativo no navegador se as janelas pop-up estiverem desabilitadas para o navegador. Se isso acontecer, habilite as janelas pop-up e atualize a página.

## <a name="see-also"></a>Confira também

[Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e Visual Studio Code](visual-studio-code-overview.md)
