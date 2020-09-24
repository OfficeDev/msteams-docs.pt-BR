---
title: Criar e executar um "Olá, mundo!" Aplicativo de equipes
author: heath-hamilton
description: Criar e executar seu primeiro aplicativo do Microsoft Teams, uma guia pessoal que exibe "Olá, mundo!"
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: quickstart
ms.openlocfilehash: 244a899670f71b9446c8c3d3e404c9fd7c7b510c
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237829"
---
# <a name="build-a-hello-world-teams-app"></a>Crie um "Olá, mundo!" Aplicativo de equipes

Você pode ir direto para o desenvolvimento da plataforma do Microsoft Teams criando uma guia pessoal que exibe "Olá, mundo!"

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
:::image type="content" source="../assets/images/build-your-first-app/create-teams-app.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. Verifique a opção de **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-understand-important-app-project-components"></a>2. compreender os principais componentes do projeto de aplicativos

Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams. Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal no Visual Studio Code.":::

Vamos reservar alguns momentos para entender alguns dos principais arquivos que os desenvolvedores de aplicativos do teams trabalham.

### <a name="app-manifest-manifestjson"></a>Manifesto do aplicativo ( `manifest.json` )

Localizado no `.publish` diretório, o manifesto do aplicativo é o ponto de partida para qualquer projeto de aplicativo. O manifesto define os atributos fundamentais do aplicativo e aponta para os recursos necessários. Quando você instala um aplicativo, o Teams analisa o manifesto para entender como renderizar seu aplicativo no cliente.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.

Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo. Ele chama o [SDK do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.

### <a name="app-package-developmentzip"></a>Pacote de aplicativos ( `Development.zip` )

Localizado no `.publish` diretório, você precisará do pacote de aplicativos para [Sideload seu aplicativo](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) no Microsoft Teams. O pacote também é usado durante [a publicação no catálogo de aplicativos da sua organização](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) ou no [AppSource](../concepts/deploy-and-publish/appsource/publish.md).

Veja alguns detalhes sobre os arquivos de pacote de aplicativos:

|Nome|Tipo|Size|Local do manifesto|Nome do arquivo de kit|
|---|---|:---:|:---:|-----|
|**Manifesto do aplicativo**|`.json`| — | — |`.publish/manifest.json`|
|**Logotipo colorido**|`.png`|192 &times; 192 pixels|`icon.color`|`.publish/color.png`|
|**Logotipo da estrutura de tópicos**|`.png`|32 &times; 32 pixels|`icon.outline`|`.publish/outline.png`|

## <a name="3-run-your-app"></a>3. Execute seu aplicativo

Nos juros de tempo, você criará e executará seu aplicativo localmente.

(Essas informações também estão disponíveis no kit de ferramentas `README` .)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` . Após a conclusão, há uma **compilação bem-sucedida!** mensagem no terminal.
1. Abra um navegador e vá para `https://localhost:3000` para exibir uma página da Web em branco chamada **Guia do Microsoft Teams**. (Não se preocupe se você não consegue ver conteúdo na página.)<br/>
   :::image type="content" source="../assets/images/build-your-first-app/local-host-tab.png" alt-text="Captura de tela mostrando como exibir seu aplicativo em execução em um navegador.":::

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a>4. configurar um túnel seguro para seu aplicativo

Seu aplicativo está em execução no servidor Web local. Para executar seu aplicativo no Teams, você deve tornar seu `localhost` acessível por meio de HTTPS.

Instale o [ngrok](https://ngrok.com/download) se ainda não tiver feito isso. Ao executar essa ferramenta, você cria duas URLs disponíveis globalmente que apontam para o servidor Web local ( `http://localhost:3000` ). Você precisa da URL de encaminhamento que começa com `HTTPS` .

1. Abra um novo terminal e execute `ngrok http 3000` .
1. Copie a URL HTTPS que você está vendo (Confira o exemplo a seguir).
:::image type="content" source="../assets/images/build-your-first-app/ngrok-running.png" alt-text="Captura de tela mostrando um terminal com o ngrok em execução.":::
1. Em seu `.publish` diretório, abra `Development.env` .
1. Substitua o `baseUrl0` valor pela URL copiada. (Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ba5.ngrok.io` .)

O manifesto do aplicativo agora aponta para onde você está hospedando o aplicativo.

## <a name="5-sideload-your-app-in-teams"></a>5. Sideload seu aplicativo no Microsoft Teams

Com o aplicativo em execução e acessível via HTTPS, você está pronto para carregá-lo no Microsoft Teams.

> [!TIP]
> Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação do kit de ferramentas](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool). Os erros devem ser corrigidos para Sideload com êxito o aplicativo.

1. Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)
1. Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.
1. Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` . Uma janela restrita de instalação é exibida.
:::image type="content" source="../assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando um exemplo de janela restrita de instalação de aplicativos do Microsoft Teams.":::
1. Selecione **Adicionar** para instalar seu aplicativo.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal "Olá, mundo!" executado no Teams.":::

🎉 Parabéns! Seu aplicativo está em execução no Microsoft Teams.

## <a name="next-step"></a>Próxima etapa

Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.

> [!div class="nextstepaction"]
> [Adicionar à sua guia pessoal](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
