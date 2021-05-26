---
title: Começar - Criar seu primeiro aplicativo Teams com SPFx
author: zhenyasav
description: Saiba como criar uma guia personalizada com a Estrutura do SharePoint
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 54886b47bbe70fed5dd1f010517e6c91d8d5a50d
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646608"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a>Crie e execute seu primeiro aplicativo Microsoft Teams com Estrutura do SharePoint (SPFx)

Neste tutorial, você criará um novo aplicativo Microsoft Teams no Estrutura do SharePoint (SPFx) que implementa um aplicativo pessoal simples. (Um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.) Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar o aplicativo localmente e como implantar o aplicativo SharePoint.

## <a name="before-you-begin"></a>Antes de começar

Certifique-se de que seu ambiente de desenvolvimento está definido instalando os [pré-requisitos](prerequisites.md)

> [!div class="nextstepaction"]
> [Pré-requisitos de instalação](prerequisites.md)

## <a name="get-organized"></a>Organizar-se

Além dos pré-requisitos, você também precisa ser administrador de um conjunto SharePoint Site.  É aqui que você implantará seu aplicativo para hospedagem.  Se você estiver usando um locatário de programa de desenvolvedor do M365, use a conta de administrador configurada quando se registrou no programa.  

## <a name="create-your-project"></a>Criar seu projeto

Use o Teams Toolkit para criar seu primeiro projeto:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra Visual Studio código.
1. Abra o Teams Toolkit selecionando o ícone Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O Teams ícone na barra Visual Studio Code lateral.":::

1. Selecione **Criar Novo Project**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Local do link Criar novo Project na barra Teams Toolkit lado.":::

1. Selecione **Criar um novo Teams app**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar novo Project":::

1. Na etapa **Selecionar recursos,** o recurso **Tab** já estará selecionado.  Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar recursos ao seu novo aplicativo.":::

1. Na etapa **de tipo de hospedagem frontend,** selecione **Estrutura do SharePoint (SPFx)**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar hospedagem para seu novo aplicativo.":::

1. Na etapa **Estrutura,** selecione **React**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Selecionar Estrutura":::

1. Quando solicitado a um **Nome da Webpart,** pressione **Enter** para aceitar o padrão.

1. Quando solicitado para a **Descrição da Webpart,** pressione **Enter** para aceitar o padrão.

1. Quando solicitado a linguagem **de programação,** pressione **Enter** para aceitar o padrão.

1. Selecione uma pasta de espaço de trabalho.  Uma pasta será criada em sua pasta de espaço de trabalho para o projeto que você está criando.

1. Insira um nome adequado para seu aplicativo, como `helloworld` .  O nome do aplicativo deve consistir apenas em caracteres alfanuméricos.  Pressione **Enter** para continuar.

Seu Teams aplicativo será criado em alguns segundos.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Use a `teamsfx` CLI para criar seu primeiro projeto.  Comece na pasta onde você deseja criar a pasta do projeto.

``` bash
teamsfx new
```

A CLI orienta algumas perguntas para criar o projeto.  Cada pergunta lhe dirá como respondê-la (por exemplo, para usar teclas de seta para selecionar uma opção).  Quando tiver respondido à pergunta, confirme sua escolha pressionando **Enter**.

1. Selecione **Criar um novo Teams app**.
1. Escolha o **recurso Tab.**
1. Selecione **Estrutura do SharePoint (SPFx)** de frontend.
1. Selecione **React** estrutura.
1. Pressione **Enter** para o **Nome da Webpart**.
1. Pressione **Enter** para a **Descrição da Webpart**.
1. Pressione **Enter** para a **Linguagem de Programação**.
1. Pressione **Enter** para selecionar a pasta de espaço de trabalho padrão.
1. Insira um nome adequado para seu aplicativo, como `helloworld` .  O nome do aplicativo deve consistir apenas em caracteres alfanuméricos.

Depois que todas as perguntas foram respondidas, seu projeto será criado.

---

- [Saiba mais sobre o desenvolvimento para Estrutura do SharePoint](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a>Fazer um tour pelo código-fonte

Se quiser ignorar essa seção por enquanto, você pode [executar seu aplicativo localmente.](#run-your-app-locally)

Depois que Teams Toolkit configura seu projeto, você tem os componentes para criar um aplicativo pessoal básico para Teams que está hospedado no Estrutura do SharePoint.  Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para um aplicativo pessoal Visual Studio Code.":::

O Toolkit cria automaticamente o scaffolding para você no diretório do projeto com base nos recursos adicionados durante a instalação. O Teams Toolkit mantém seu estado para seu aplicativo no `.fx` diretório.  Entre outros itens neste diretório:

- Os ícones do aplicativo são armazenados como arquivos PNG `color.png` em `outline.png` e .
- O manifesto do aplicativo para publicação no Portal do Desenvolvedor para Teams é armazenado em `manifest.source.json` .
- As configurações escolhidas ao criar o projeto são armazenadas em `settings.json` .

Como você selecionou um SPFx webpart, os seguintes arquivos são relevantes para sua interface do usuário:

- A pasta `SPFx/src/webparts/{webpart}` contém sua SPFx webpart.
- O arquivo `.vscode/launch.json` descreve as configurações de depuração disponíveis na paleta de depuração.

Para obter mais informações sobre SharePoint Webparts para Teams, [consulte a documentação SharePoint.](/sharepoint/dev/spfx/build-for-teams-overview)

## <a name="run-your-app-locally"></a>Executar seu aplicativo localmente

Teams Toolkit permite que você hospede seu aplicativo localmente e execute-o por meio do [Estrutura do SharePoint Workbench](/sharepoint/dev/spfx/debug-in-vscode).

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a>Criar e executar seu aplicativo localmente Visual Studio Code

Para criar e executar seu aplicativo localmente:

1. De Visual Studio Code, pressione **F5**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Captura de tela mostrando como iniciar um SPFx em um workbench local.":::

   > [!NOTE]
   > Quando você executar o aplicativo pela primeira vez, todas as dependências serão baixadas e o aplicativo será criado.  Uma janela do navegador é aberta automaticamente e carrega o SharePoint Workbench quando a com build estiver concluída.  Isso pode levar de 3 a 5 minutos para ser concluído.

   Depois que o SharePoint Workbench for carregado.

   >[!NOTE]
   > A Toolkit solicitará que você instale um certificado local, se necessário. Esse certificado permite Teams carregar seu aplicativo de `https://localhost` . Selecione sim quando a caixa de diálogo a seguir for exibida:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como o prompt para instalar um certificado SSL para permitir Teams carregar seu aplicativo do localhost.":::

1. Pressione um dos ícones **Adicionar Webpart** (+) para adicionar sua webpart.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma webpart mostrando.":::

1. Escolha sua webpart no menu.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma seleção de webpart.":::

Seu aplicativo agora deve estar em execução.  Você pode fazer atividades normais de depuração como se fosse qualquer outra webpart SPFx (como definir pontos de interrupção).

> [!TIP]
> Tente colocar pontos de interrupção no método render de `SPFx/src/webparts/{webpart}/{webpart}.ts` e recarregar a janela do navegador. VS Code parar em pontos de interrupção em seu código.

## <a name="deploy-your-app-to-sharepoint"></a>Implantar seu aplicativo para SharePoint

Verifique se existe SharePoint catálogo de aplicativos em sua implantação.  Se um não existir, [crie um](/sharepoint/use-app-catalog).  Pode levar até 15 minutos para que o catálogo de aplicativos seja totalmente criado.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra Visual Studio Code.
1. Selecione a Teams Toolkit na barra lateral selecionando o ícone Teams.
1. Selecione **Provisionamento na Nuvem**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

1. Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito.  Após alguns segundos, você verá o seguinte aviso:

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento.":::

1. Depois que o provisionamento for concluído, selecione **Implantar na nuvem**.

1. Atualmente, a implantação automatizada não está disponível.  Uma caixa de diálogo será exibida solicitando que você crie e implante manualmente. Pressione **Build SharePoint Package**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Captura de tela para a caixa de diálogo Criar Pacote do Sharepoint":::

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Em sua janela de terminal:

1. Executar `teamsfx provision` .

   ``` bash
   teamsfx provision
   ```

   Você pode ser solicitado a fazer logoff na sua assinatura do Azure.  Se necessário, você será solicitado a selecionar uma assinatura do Azure a ser usada para os recursos do Azure.

   > [!NOTE]
   > Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.

1. Executar `teamsfx deploy` .

   ``` bash
   teamsfx deploy
   ```

1. Quando solicitado, selecione **Criar SharePoint Pacote**.

---

O SharePoint pacote está localizado `SPFx/sharepoint/solution` no seu projeto.  Upload pacote para SharePoint:

1. Faça logon no Console de Administração do M365 e navegue até o SharePoint App Catalog.

   - Abra `https://admin.microsoft.com/AdminPortal/Home` .
   - Em **Centros de administração,** selecione o **SharePoint** de administração.
   - Selecione **Mais recursos** no menu barra lateral.
   - Pressione **Abrir** em **Aplicativos**.
   - Selecione **Catálogo de Aplicativos**.

1. Selecione **Distribuir aplicativos para SharePoint**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Distribuir aplicativos para SharePoint.":::

1. Selecione **Upload**.

1. Pressione **Escolher Arquivo**.

1. Localize `{project}.sppkg` seu arquivo, localizado na `SPFx/sharepoint/solution` pasta dentro do seu projeto.  Pressione **Abrir**.

1. Pressione **OK**.

1. O SharePoint de implantação será automaticamente iniciar.  **Certifique-se de tornar essa solução disponível para todos os sites na** organização está marcada e pressione **Implantar**.

1. Selecione a **guia ARQUIVOS.**

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Selecione a guia arquivos no catálogo SharePoint App.":::

1. selecione o pacote implantado e pressione **Sincronizar para Teams** na faixa de opções.

    > [!Note]
    > O processo Sincronizar Teams pode levar alguns minutos.  Você verá uma mensagem no lado direito do navegador indicando que o aplicativo foi sincronizado com êxito com Teams.

Abra o Teams aplicativo (ou entre `https://teams.microsoft.com` em ).  Pressione o ponto triplo na barra lateral e selecione **Todos os aplicativos**.  O aplicativo será colocado nos **Aplicativos construídos para sua categoria organizacional.**  Você pode adicionar o aplicativo a partir daí.

:::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Captura de tela mostrando o aplicativo dentro Teams":::

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre outros métodos para criar Teams aplicativos:

- [Criar um Teams com React](first-app-react.md)
- [Criar um Teams com o Blazor](first-app-blazor.md)
- [Criar um aplicativo bot de conversação](first-app-bot.md)
- [Criar uma extensão de mensagens](first-message-extension.md)
