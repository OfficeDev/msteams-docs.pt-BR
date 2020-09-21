---
title: Criar e executar o primeiro aplicativo Teams
author: heath-hamilton
ms.author: lajanuar
description: Execute seu primeiro aplicativo do Microsoft Teams.
ms.date: 08/31/2020
ms.topic: quickstart
ms.openlocfilehash: 441b70480d9c177e9c6140342df8c9ea29494a29
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964623"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo do Microsoft Teams

Você pode ir diretamente para o desenvolvimento na plataforma do Microsoft Teams, criando e executando rapidamente uma guia pessoal básica.

## <a name="create-your-app-project"></a>Criar seu projeto de aplicativo

Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
:::image type="content" source="../doc-links/images/create-teams-app.png" alt-text="criar imagem do aplicativo do teams":::
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.
:::image type="content" source="../doc-links/images/choose-tab.png" alt-text="criar o modo de exibição imagem do aplicativo do teams":::
1. Verifique a opção de **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="understand-important-app-project-components"></a>Compreender os principais componentes do projeto de aplicativo

Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams. Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.

:::image type="content" source="../doc-links/images/app-project-files.png" alt-text="Arquivos de projeto de aplicativo no Visual Studio Code.":::

Vamos dar tempo para entender alguns dos principais arquivos que os desenvolvedores de aplicativos do teams trabalham com.

### <a name="app-manifest-manifestjson"></a>Manifesto do aplicativo ( `manifest.json` )

Localizado no `.publish` diretório, o manifesto do aplicativo é o ponto de partida para qualquer projeto de aplicativo. O manifesto define os atributos fundamentais do aplicativo e aponta para os recursos necessários. Quando você instala um aplicativo, o Teams analisa o manifesto para entender como renderizar seu aplicativo no cliente.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.

Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo. Ele chama o [SDK do Microsoft Teams](../../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.

### <a name="app-package-developmentzip"></a>Pacote de aplicativos ( `Development.zip` )

Localizado no `.publish` diretório, você precisará do pacote de aplicativos para [Sideload seu aplicativo](../../concepts/deploy-and-publish/overview.md#upload-your-app-directly) no Microsoft Teams. O pacote também é usado durante [a publicação no catálogo de aplicativos da sua organização](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) ou no [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).

Veja alguns detalhes sobre os arquivos de pacote de aplicativos:

|Nome|Tipo|Size|Local do manifesto|Nome do arquivo de kit|
|---|---|:---:|:---:|-----|
|**Manifesto do aplicativo**|`.json`| — | — |`.publish/manifest.json`|
|**Logotipo colorido**|`.png`|192 &times; 192 pixels|`icon.color`|`.publish/color.png`|
|**Logotipo da estrutura de tópicos**|`.png`|32 &times; 32 pixels|`icon.outline`|`.publish/outline.png`|

## <a name="run-your-app"></a>Executar o aplicativo

Nos juros de tempo, você criará e executará seu aplicativo localmente. Os aplicativos de equipe de nível de produção são hospedados na nuvem.

(Essas informações também estão disponíveis no kit de ferramentas `README` .)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` . Após a conclusão, há uma **compilação bem-sucedida!** mensagem no terminal.
1. Abra um navegador e vá para `https://localhost:3000` para exibir uma página da Web em branco chamada **Guia do Microsoft Teams**. (Não se preocupe se você não consegue ver conteúdo na página.)<br/>
   :::image type="content" source="../doc-links/images/local-host-tab.png" alt-text="Exibir o aplicativo em um navegador.":::

## <a name="set-up-a-secure-tunnel-to-your-app"></a>Configurar um túnel seguro para seu aplicativo

Seu aplicativo está em execução no servidor Web local. Para executar seu aplicativo no Teams, você deve tornar seu `localhost` acessível por meio de HTTPS.

Instale o [ngrok](https://ngrok.com/download) se ainda não tiver feito isso. Ao executar essa ferramenta, você cria duas URLs disponíveis globalmente que apontam para o servidor Web local ( `http://localhost:3000` ). Você precisa da URL de encaminhamento que começa com `HTTPS` .

1. Abra um novo terminal e execute `ngrok http 3000` .
1. Copie a URL HTTPS que você está vendo (Confira o exemplo a seguir).
:::image type="content" source="../doc-links/images/ngrok-running.png" alt-text="imagem em execução do ngrok":::
1. Em seu `.publish` diretório, abra `Development.env` .
1. Substitua o `baseUrl0` valor pela URL copiada. (Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ba5.ngrok.io` .)

O manifesto do aplicativo agora aponta para onde você está hospedando o aplicativo.

## <a name="sideload-your-app-in-teams"></a>Sideload seu aplicativo no Microsoft Teams

Com o aplicativo em execução e acessível via HTTPS, você está pronto para carregá-lo no Microsoft Teams.

> [!TIP]
> Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação do kit de ferramentas](../../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool). Os erros devem ser corrigidos para Sideload com êxito o aplicativo.

1. Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/building-real-world-app.md#set-up-your-development-account).)
1. Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.
1. Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` . Uma janela restrita de instalação é exibida.
:::image type="content" source="../doc-links/images/add-teams-app.png" alt-text="Adicionar aplicativo do teams":::
1. Selecione **Adicionar** para instalar seu aplicativo.
:::image type="content" source="../doc-links/images/tab-running.png" alt-text="Captura de tela mostrando um exemplo de Olá, mundo! aplicativo no Teams.":::

🎉 Parabéns! Seu aplicativo está em execução no Microsoft Teams.

## <a name="next-step"></a>Próxima etapa

Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.

> [!div class="nextstepaction"]
> [Adicionar à sua guia pessoal](../build-your-first-app/add-personal-tab.md)
> [!div class="nextstepaction"]
> [Criar uma guia de canal](../build-your-first-app/add-channel-tab.md)
> [!div class="nextstepaction"]
> [Criar um bot](../build-your-first-app/add-bot.md)
