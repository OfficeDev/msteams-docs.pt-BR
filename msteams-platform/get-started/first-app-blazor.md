---
title: Começar - Criar seu primeiro aplicativo Teams com o Blazor
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Microsoft Teams Toolkit e o .NET Blazor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: c14f55d014af120cab88044d31ee8600017e3c57
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254304"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a>Criar e executar seu primeiro aplicativo Microsoft Teams com o Blazor

Neste tutorial, você aprenderá a criar um novo aplicativo Microsoft Teams no .NET/Blazor que implementa um aplicativo pessoal simples para obter informações do microsoft Graph. Por exemplo, um *aplicativo pessoal* inclui um conjunto de guias para uso individual. Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.

O aplicativo que é compilado exibe informações básicas para o usuário atual.  Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.

## <a name="before-you-begin"></a>Antes de você começar

Certifique-se de que seu ambiente de desenvolvimento está definido instalando os pré-requisitos.

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](prerequisites.md)

## <a name="create-your-project"></a>Criar seu projeto

Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

1. Abra Visual Studio 2019.

1. Selecione **Criar um novo projeto**.

1. Selecione **Microsoft Teams App** e, em seguida, selecione **Próximo**.  Para ajudá-lo a encontrar o modelo, use o tipo de projeto **Microsoft Teams**.

1. Insira um nome e selecione **Next**.

1. Insira o nome do aplicativo e o nome da empresa.

1. Selecione **Criar**.  O nome do aplicativo e o nome da empresa são exibidos para os usuários finais. O seu aplicativo do Teams será criado em alguns segundos.  Depois que o projeto for criado, configurar o logom único com o M365:

   1. Selecione **Project**  >  **Configuração do TeamsFx**  >  **para SSO...**.
   1. Quando solicitado, entre em sua conta de administrador do M365.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

1. Abra um Terminal e selecione o diretório onde você deseja criar o projeto.

1. Execute `dotnet new -i` para instalar o modelo de NuGet:

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   Você só precisa fazer isso na primeira vez ou ao atualizar o modelo. Verifique [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) a versão mais recente deste pacote.

1. Criar um diretório:

   ``` bash
   mkdir helloworld
   ```

1. Execute `dotnet new` para criar um novo projeto:

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. Após o scaffolding, configure o projeto para Teams implantação:

   ``` bash
   teamsfx init
   ```

   Agora você pode abrir a solução em Visual Studio para depuração.

---

## <a name="take-a-tour-of-the-source-code"></a>Faça um tour pelo código-fonte

Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).

Após a Teams Toolkit configura seu projeto, você terá os componentes para criar um aplicativo pessoal básico para Teams. Os diretórios e arquivos do projeto são exibidos na área Do Explorador de Soluções Visual Studio 2019.

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para um aplicativo pessoal Visual Studio 2019.":::

- Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.
- O manifesto do aplicativo para publicação por meio do Portal do Desenvolvedor para Teams é armazenado em `Properties/manifest.json` .
- Um controlador back-end é fornecido para `Controllers/BackendController.cs` ajudar na autenticação.

Desde que você criou um aplicativo de tabulação durante a instalação, o Teams Toolkit estrutura todo o código necessário para uma guia básica como [um Servidor Blazor](/aspnet/core/blazor).

- `Pages/Tab.razor` é o ponto de entrada do aplicativo front-end.
- `TeamsFx.cs`e `JS/src/index.js` é usado para inicializar comunicações com o Teams host.

Você pode adicionar funcionalidade de back-end adicionando ASP.NET Core controladores adicionais ao seu aplicativo.

## <a name="run-your-app-locally"></a>Executar seu aplicativo localmente

O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.  Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:

- Um aplicativo está registrado no Azure Active Directory.  Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.
- Uma API da Web é hospedada (por meio IIS Express) para ajudar com tarefas de autenticação, atuando como um proxy entre o aplicativo e Azure Active Directory.  
- Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.  O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.

Depois que isso for feito, o aplicativo poderá ser carregado no cliente Teams cliente.  Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.

Para compilar e executar seu aplicativo localmente:


1. Na Visual Studio Code, pressione a **tecla F5** para executar seu aplicativo no modo de depuração.


1. Se solicitado, instale o certificado SSL auto-assinado para depuração local.

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. O Teams é carregado em um navegador da Web e você será solicitado a entrar. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Entre com sua conta do M365.

1. Quando solicitado a instalar o aplicativo no Teams, selecione **Adicionar**.

   Seu aplicativo agora será exibido:

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Captura de tela do aplicativo concluído":::

   Você pode executar as atividades de depuração como se fosse qualquer outro aplicativo Web, como a definição de pontos de interrupção. O aplicativo dá suporte à recarga dinâmica.  Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</summary>

Quando você pressiona a **tecla F5,** o Teams Toolkit:

1. Registra seu aplicativo com Azure Active Directory.
1. Registra seu aplicativo para "side loading" no Microsoft Teams.
1. Inicia o back-end do aplicativo em execução localmente.
1. Inicia o front-end do aplicativo hospedado localmente.
1. Inicia Microsoft Teams em um navegador da Web com um comando para instruir Teams carregar o aplicativo de lado (a URL é registrada dentro do manifesto do aplicativo).

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</summary>

Para executar seu aplicativo com êxito Teams, você deve ter uma conta Microsoft 365 de desenvolvimento que permita o carregamento do lado do aplicativo. Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).

</details>

## <a name="deploy-your-app-to-azure"></a>Implantar seu aplicativo no Azure

A implantação consiste em duas etapas: 

1. Recursos de nuvem necessários são criados. Isso também é conhecido como provisionamento.
1. Comece a codificar e copie seu aplicativo para os recursos de nuvem criados.

> **Visualizar**
>
> O suporte para aplicativos Blazor é novo no Teams Toolkit.  O provisionamento e a implantação são feitos com uma combinação de Visual Studio 2019 e o Portal do Desenvolvedor para Teams.

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a>Provisionar e implantar seu aplicativo no Serviço de Aplicativo do Azure

1. No Explorador de Soluções, clique com o botão direito do mouse no nó do projeto e selecione **Publicar**. Você também pode usar o item de menu **Criar**  >  **Publicar.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Selecione a operação Publicar no projeto":::

1. Na janela **Publicar,** selecione **Azure** e selct **Next**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Selecione O Azure como o destino de publicação":::

1. Selecione Serviço de Aplicativo do **Azure (Windows)** e selecione **Próximo**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Selecione Serviço de Aplicativo do Azure como o destino de publicação":::

1. Selecione **+** para criar uma nova instância do Serviço de Aplicativo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Crie uma nova instância.":::

1. Na caixa de diálogo Criar Serviço de Aplicativo **(Windows),** os campos  de entrada **Nome,** Nome da **Assinatura,** Grupo de Recursos e Plano de Hospedagem são preenchidos.  Se você já tiver um Serviço de Aplicativo em execução, as configurações existentes serão selecionadas.  Você pode optar por criar um novo grupo de recursos e um plano de hospedagem.  Quando estiver pronto, selecione **Criar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Selecionar plano de hospedagem e assinatura":::

1. Na caixa **de diálogo Publicar,** a instância recém-criada foi selecionada automaticamente.  Quando estiver pronto, selecione **Concluir**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Selecione a nova instância.":::

1. Selecione o **ícone Editar** (lápis) ao lado de **Modo de** Implantação e selecione **Autocontiver**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Selecione o modo de implantação autoconstrutivo.":::

1. Selecionar **Publicar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Publicar seu aplicativo no serviço de aplicativo":::

   Visual Studio implanta o aplicativo no Serviço de Aplicativo do Azure e o aplicativo Web é carregado no navegador.  Adicione `/tab` ao final da URL para ver sua página.

   O painel **Publicar propriedades** do projeto mostra a URL do site e outros detalhes. Anote a URL do site.

## <a name="create-an-environment-for-your-app"></a>Criar um ambiente para seu aplicativo

O Portal do Desenvolvedor para Teams gerencia de onde as guias do seu aplicativo são carregadas com um **Environment**.  

**Para criar um ambiente:**

1. Abra o [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com).  Entre com sua conta administrativa do M365.

1. Na barra lateral, selecione **Aplicativos**.

1. Se você tiver apenas um aplicativo, ele será selecionado automaticamente.  Caso não seja, selecione seu aplicativo na lista.

1. Selecione **Ambientes**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Selecionar ambientes":::

1. Selecione **Criar seu primeiro ambiente**.

1. Insira um nome para seu ambiente e selecione **Adicionar**. Por exemplo, `_Production_`.

1. Selecione **Criar sua primeira variável de ambiente**.

1. Insira `azure_app_url` para o **nome**.  Insira a URL do site do Azure sem `https://` o valor . 

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Criar variável de ambiente":::

   Pressione **Adicionar**.

## <a name="update-the-app-manifest"></a>Atualizar o manifesto do aplicativo

O manifesto do aplicativo carrega a guia de uma `localhost` URL.  Nesta seção, você configurará o manifesto do aplicativo para carregar a guia da URL listada no ambiente que você acabou de criar.

1. Na barra lateral, selecione **Informações básicas**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Selecionar informações básicas":::

1. Há vários locais dentro do manifesto que listam uma `locahost:XXXXX` como parte de uma URL.  Substitua todas as ocorrências `{{azure_app_url}}` por , incluindo as chaves.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Ajustar informações básicas para o ambiente":::

1. Quando estiver concluído, selecione **Salvar**.

1. Na barra lateral, selecione **Recursos**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Selecionar recursos":::

1. Selecione **Guia Pessoal**.
1. Ao lado da **Guia Pessoal,** selecione os pontos tríplices e selecione **Editar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Editar configurações de tabulação pessoal":::

1. Substitua a URL pela variável de ambiente nos campos **Url de Conteúdo** e Url **do** Site.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Editar URLs de tabulação pessoal":::

1. Selecione **Atualizar**.

1. Selecione **Salvar**.

1. Na barra lateral, selecione **Single Sign-On**.

1. Substitua o `localhost` URI de **ID do aplicativo** por `{{azure_app_url}}` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Editar URI de ID de aplicativo de login único":::

1. Selecione **Salvar**.

1. Na barra lateral, selecione **Domínios**.

1. Selecione **Adicionar um domínio**.

1. Se `{{azure_app_url}}` não estiver listado como um domínio válido, adicione-o como um domínio válido e selecione **Adicionar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Adicionar um domínio":::

   Agora você pode usar a **opção Visualizar Teams** na parte superior da página para iniciar seu aplicativo dentro Teams.

## <a name="see-also"></a>Confira também

* [Visão geral dos tutoriais](code-samples.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)
