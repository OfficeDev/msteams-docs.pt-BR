---
title: Começar - Criar e executar seu primeiro aplicativo
author: girliemac
description: Crie rapidamente um Microsoft Teams que exibe um "Hello, World!" usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2021
ms.topic: quickstart
ms.openlocfilehash: 6c3d215a3f2c1aa89a9a2bf28aad081d98c6dc33
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101720"
---
# <a name="create-your-first-microsoft-teams-app"></a>Criar seu primeiro Microsoft Teams app

Esse início rápido ensina você a criar e executar um Microsoft Teams que exibe "Hello, World!"

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, você precisa configurar seu locatário de desenvolvimento [Teams](#set-up-your-teams-development-tenant) e instalar suas [ferramentas Teams de desenvolvimento.](#install-your-development-tools)

### <a name="set-up-your-teams-development-tenant"></a>Configurar seu locatário Teams desenvolvimento

Um **locatário** é como um contêiner para uma organização. Em Teams, um locatário é onde as pessoas dessa organização conversam, compartilham arquivos e executem reuniões. Como desenvolvedor, você precisa de um locatário para fazer sideload e testar o Teams aplicativos que você está criando.  

# <a name="do-not-have-a-tenant"></a>[Não tem um locatário](#tab/do-not-have-a-tenant)

Você pode obter uma conta Teams de teste gratuita, que inclui um locatário que permite o sideload de aplicativos, juntando-se ao programa Microsoft 365 desenvolvedor. O processo de registro leva aproximadamente dois minutos.

**Para obter um locatário**

1. Vá para o programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)
1. Selecione **Ingressar agora** e siga as instruções na tela.
1. Na tela De boas-vindas, selecione **Configurar assinatura do E5**.
1. Configurar sua conta Microsoft 365 desenvolvedor. 
   Depois de concluir, a tela a seguir será exibida:

   :::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa Microsoft 365 desenvolvedor.":::

1. Entre no Teams com sua nova conta.
1. No cliente Teams, selecione **Aplicativos**.
1. Verifique se você pode ver o Upload **uma opção de aplicativo** personalizada. Se fizer isso, isso significa que você pode fazer sideload de aplicativos.

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

# <a name="have-a-tenant"></a>[Ter um locatário](#tab/have-a-tenant)

Se você já tiver um locatário, verifique se pode fazer sideload de aplicativos Teams.

**Verifique se você pode fazer sideload de seus aplicativos** 

1. No cliente Teams, selecione **Aplicativos**. 
1.  Verifique se você pode ver o Upload **uma opção de aplicativo** personalizada. Se fizer isso, isso significa que você pode fazer sideload de aplicativos. 

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

---

### <a name="install-your-development-tools"></a>Instalar suas ferramentas de desenvolvimento

Para criar esse aplicativo, você usará o Teams Toolkit para Visual Studio Code começar rapidamente. Você também pode criar Teams aplicativos com qualquer uma de suas ferramentas prefered. 

> [!NOTE]
> Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS. Para depurar determinados tipos de aplicativos localmente, como um bot, você aprenderá a usar o ngrok para configurar um túnel seguro entre o Teams e seu aplicativo.
> 
> Os Teams de produção são hospedados na nuvem.

**Para instalar Microsoft Teams ferramentas**

1. Instale o [Node.js](https://nodejs.org/en/).
1. Se você planeja criar um bot ou extensão de mensagens, instale [o ngrok](https://ngrok.com/download) e exponha seu localhost à [Internet usando ngrok](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok).
1. Instale a versão mais recente [do Visual Studio Code](https://code.visualstudio.com/download). 
   
   > [!NOTE]
   > O kit de ferramentas não dá suporte a versões anteriores Visual Studio Code.

1. Na barra de atividades esquerda, selecione **Extensões** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: .
1. Em **Microsoft Teams Toolkit,** selecione **Instalar**.

   :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração mostrando onde Visual Studio Code você pode instalar a extensão Microsoft Teams Toolkit.":::

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

1. Abra Visual Studio Code.
1. Selecione **Microsoft Teams Toolkit** :::image type="icon" source="../assets/icons/vsc-toolkit.png":::  >  **Criar um novo Teams app**.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-02.png" alt-text="Captura de tela mostrando como criar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
   
1. Entre com sua conta Microsoft 365 de desenvolvimento. A que você acabou de criar ou a conta que você já tinha que permite o sideload do aplicativo.
1. Na tela **Selecionar projeto,** vá para **Aplicativo Pessoal** e selecione **JS** (JavaScript) > **Próximo.**

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-03.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

1. Insira um nome para seu Teams app.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-04.png" alt-text="Captura de tela mostrando como adicionar um nome ao seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

1. Selecione **Concluir**. 
   Seu projeto agora está configurado. 

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do aplicativo

Depois que o kit de ferramentas configurar seu projeto de aplicativo, você terá os componentes para criar seu "Hello, World!" Teams aplicativo. Os diretórios e arquivos do projeto estão localizados no Visual Studio Code Explorer. 

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-05.png" alt-text="Captura de tela mostrando o scaffolding em seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

O kit de ferramentas cria automaticamente o scaffolding de aplicativos no `src` diretório com base nos recursos adicionados durante a instalação. Desde que você criou uma guia durante a instalação, o arquivo no diretório lida com a inicialização e o `App.js` `src/components` roteamento do seu aplicativo. O arquivo também chama o Microsoft Teams SDK do cliente JavaScript para estabelecer a comunicação entre seu aplicativo e Teams. 

## <a name="3-build-and-run-your-app"></a>3. Crie e execute seu aplicativo

Crie e execute seu aplicativo localmente para economizar tempo. 

**Para criar e executar seu aplicativo**

1. Em Visual Studio Code, selecione **Exibir**  >  **Terminal**.
1. Executar `npm install` .
1. Executar `npm start` .
  
  Compilado **com êxito!** aparece no terminal. Seu aplicativo agora está sendo executado em seu localhost em `https://localhost:3000` . 

## <a name="4-sideload-your-app-in-teams"></a>4. Fazer sideload do aplicativo no Teams

Sideload é o processo de instalação de um aplicativo no Teams que não foi aprovado pelo administrador ou pela Microsoft. O sideload é comum ao testar e depurar Teams aplicativos.

Por padrão, Teams não permite o sideload do aplicativo. Você pode alterar essa configuração no Teams de administração.

**Para habilitar o sideload de aplicativos Teams**

1. Entre no centro de administração [Microsoft 365 com](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) suas credenciais de administrador.  
1. Selecione **Mostrar todos os**  >  **Teams**. 

   ![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

   > [!Note] 
   > Pode levar até 24 horas para que a opção **Teams** apareça. 

1. Vá para **Teams políticas de instalação**  >  **de**  >  **aplicativos Global** (padrão em toda a organização).

   ![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

1. Ativar a **alternância carregar aplicativos personalizados.**

1. Selecione **Salvar** para salvar as alterações.

   Seu locatário de teste agora permite o sideload de aplicativo personalizado.

   > [!Note]
   > Verifique se há problemas antes de fazer sideload do aplicativo usando o recurso de validação no App Studio, que está incluído no kit de ferramentas. Correção dos erros para fazer sideload com êxito do aplicativo.


### <a name="sideload-your-app"></a>Fazer sideload do aplicativo

1. Em Visual Studio Code, abra o Teams Toolkit.
1. Vá para **App Studio**.  
1. Selecione **Testar e Distribuir**  >  **Instalar**.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-appstudio.png" alt-text="Captura de tela mostrando como fazer sideload do aplicativo para Teams cliente com o Visual Studio Code Teams Toolkit.":::

**Como alternativa**

1. Selecione a **chave F5** para abrir a janela do navegador para instalar. Isso ignorará o processo de instalação no **App Studio** e Teams no navegador.
1. Na caixa de diálogo instalação, selecione **Adicionar** para instalar seu aplicativo Teams.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install.png" alt-text="Captura de tela mostrando como fazer sideload do aplicativo para Teams cliente.":::

   > [!Note]
   > O App Studio também está disponível como um aplicativo autônomo para Teams cliente.

### <a name="troubleshoot-sideloading-issues"></a>Solucionar problemas de sideload

**Falha na instalação**

Se a `Manifest parsing has failed` mensagem de erro for exibida durante a instalação do aplicativo, verifique se as informações do aplicativo foram inseridas corretamente.

**Para verificar as informações do aplicativo**

* Na Teams Toolkit, vá para **Detalhes** do App Studio App e verifique se todas as informações necessárias  >   foram inseridas corretamente.
*  Se você editou manualmente o arquivo, verifique se o JSON está bem definido na ferramenta Manifesto do Aplicativo `manifest.json` no App Studio. 

**Conteúdo de tabulação não exibido**

Verifique se seu aplicativo está em execução. Se não estiver, vá para o terminal e execute `npm start` .

## <a name="see-also"></a>Confira também

* [Preparar o locatário do Microsoft 365](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant)
* [Escolher uma instalação para testar e depurar seu Microsoft Teams app](../concepts/build-and-test/debug.md)
* [Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript Microsoft Teams JavaScript](../tabs/how-to/using-teams-client-sdk.md)
* [Preparar para envio do AppSource](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Desenvolva aplicativos rapidamente com o App Studio para Microsoft Teams](../concepts/build-and-test/app-studio-overview.md)
* [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia pessoal para Microsoft Teams](../build-your-first-app/build-personal-tab.md)
