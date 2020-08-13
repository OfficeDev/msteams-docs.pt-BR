---
title: Criar e executar seu primeiro aplicativo do Microsoft Teams
author: heath-hamilton
description: Execute seu primeiro aplicativo do Microsoft Teams.
ms.openlocfilehash: 98af8d8d6d89007e36c24bd34661ec21b33cbdf1
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651862"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo do Microsoft Teams

Você pode ir diretamente para o desenvolvimento na plataforma do Microsoft Teams, criando e executando rapidamente um aplicativo básico.

> [!NOTE]
> É útil ter conhecimento de trabalho do JavaScript (reagir especificamente) ao seguir estes tutoriais.

## <a name="set-up-your-development-account"></a>Configurar sua conta de desenvolvimento

Para criar aplicativos para o Microsoft Teams, você precisa de uma conta do Microsoft Teams que permite o Sideload (sua conta já pode fornecer isso). Caso contrário, registre-se para uma assinatura de desenvolvedor do Microsoft 365 para que você possa obter um locatário de teste.

1. Verifique se você pode Sideload aplicativos no Microsoft Teams:
    1. No cliente do Microsoft Teams, selecione **aplicativos**.
    1. Procure uma opção para **carregar um aplicativo personalizado**.
1. Se você tiver essa opção, pode começar a criar. Caso contrário, faça o seguinte:
    1. Registre-se para uma [assinatura de desenvolvedor do Microsoft 365](../doc-links/prepare-your-o365-tenant.md).
    1. [Habilitar o Sideload de aplicativos personalizado](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) para sua conta de teste.

## <a name="get-your-development-tools"></a>Obtenha suas ferramentas de desenvolvimento

Você pode criar aplicativos do teams com suas ferramentas preferidas, mas aqui está o que você precisa para começar rapidamente com o Visual Studio Code e o Microsoft Teams Toolkit.

1. Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download).
1. No Visual Studio Code, selecione **Extensions** ![ Visual Studio Toolkit View ](../doc-links/images/vs-code-extensions.png) na barra de atividades à esquerda e instale o **Microsoft Teams Toolkit**.
1. Instale o [Node.js](https://nodejs.org/en/).

## <a name="create-an-app-project"></a>Criar um projeto de aplicativo

O Microsoft Teams Toolkit pode ajudar você a configurar seu primeiro projeto de aplicativo.

1. No Visual Studio Code, abra o kit de ferramentas selecionando o ícone do Microsoft Teams ![ícone do teams](../doc-links/images/favicon-16x16.png) na barra de atividades à esquerda.
1. Selecione **criar um novo aplicativo do teams**.
1. Quando solicitado, insira um nome para o seu aplicativo. Este é o nome padrão para seu aplicativo e também o nome do diretório do projeto em sua máquina local.
1. Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.
1. Marque a opção **guia pessoal** e selecione **concluir** para configurar seu projeto.

![Kit de ferramentas Adicionar exibição de guias](../doc-links/images/toolkit-add-tabs.PNG)

Após a conclusão, você tem os componentes de scaffolding de aplicativo para criar uma guia pessoal.

## <a name="run-your-app"></a>Executar o aplicativo

Siga o `README.md` em seu projeto para compilar, executar e implantar seu aplicativo no Microsoft Teams. Em geral, essas instruções ajudam você a fazer o seguinte:

* Hospedar o aplicativo `localhost` .
* [Configure um túnel seguro com o ngrok](../doc-links/debug.md#locally-hosted) para que o Microsoft Teams possa acessar seu aplicativo. (Instale o [ngrok](https://ngrok.com/download).)
* [Sideload seu aplicativo](../doc-links/apps-upload.md) no cliente do teams usando o `Development.zip` na `.publish` pasta.

Depois que você Sideload seu aplicativo, ele deve ter a seguinte aparência no cliente Teams.

![Guia de exemplo Hello World](../doc-links/images/tab-running.png)

## <a name="important-app-project-files"></a>Arquivos de projeto de aplicativo importantes

Com seu projeto de aplicativo e o scaffolding configurados, Reserve algum tempo para entender alguns dos principais arquivos da equipe de aplicativos do teams que trabalham com o.

### <a name="app-manifest-manifestjson"></a>Manifesto do aplicativo ( `manifest.json` )

Localizado no `.publish` diretório, o manifesto do aplicativo é o ponto de partida para qualquer projeto de aplicativo. O manifesto define os atributos fundamentais do aplicativo e aponta para os recursos necessários. Quando você instala um aplicativo, o Teams analisa o manifesto para entender como renderizar seu aplicativo no cliente.

Nos tutoriais a seguir, você se concentrará nas seções do manifesto de aplicativo para criar as guias pessoal e canal.

### <a name="package-developmentzip"></a>Package ( `Development.zip` )

Também localizado no `.publish` diretório, você precisará do pacote de aplicativos para [Sideload seu aplicativo](../../overview.md#how-can-you-share-your-teams-app) no Microsoft Teams. Também é usada ao [publicar no catálogo de aplicativos da sua organização](../../overview.md#how-can-you-share-your-teams-app) ou no [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).

Veja alguns detalhes sobre os arquivos de pacote de aplicativos:

|Nome|Tipo|Size|Local do manifesto|Nome do arquivo de kit|
|---|---|:---:|:---:|-----|
|**Manifesto do aplicativo**|`.json`| — | — |`.publish/manifest.json`|
|**Logotipo colorido**|`.png`|192 &times; 192 pixels|`icon.color`|`.publish/color.png`|
|**Logotipo da estrutura de tópicos**|`.png`|32 &times; 32 pixels|`icon.outline`|`.publish/outline.png`|

### <a name="scaffolding-src"></a>Scaffolding ( `src` )

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.

No entanto, alguns arquivos são criados independentemente do tipo de aplicativo que você tem. Por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata a inicialização e o roteamento do seu aplicativo. O mais importante é que ele chama o [SDK do Microsoft Teams](../doc-links/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.

Você pode saber mais sobre o scaffolding nos tutoriais para criar guias pessoais e de canal.

## <a name="next-step"></a>Próxima etapa

🎉 Parabéns! Você tem um aplicativo do teams em execução. Selecione o botão a seguir para saber como adicionar um recurso do mundo real a ele.

> [!div class="nextstepaction"]
> [Criar uma guia pessoal](add-personal-tab.md)
