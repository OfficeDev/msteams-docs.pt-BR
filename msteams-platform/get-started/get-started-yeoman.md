---
title: Tutorial - Criar seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a criar Microsoft Teams aplicativos com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
ms.localizationpriority: medium
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 90bd997de1e5bbfc92e366d466c156f052cbe3bf
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155194"
---
# <a name="build-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Crie seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman

> [!Note]
> Este tutorial vem do gerador [Yeoman para Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).

Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando o Microsoft Teams yeoman. Ele também orienta você pelo processo de atualização do seu Teams usando o gerador Yeoman. Antes de começar, você deve ter uma conta Teams que permita o [sideload de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md).

![git do gerador yeoman](~/assets/yeoman-demo.gif)

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Obter Pré-requisitos

Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman:

* Node.js

   Você precisa ter Node.js instalado em seu computador. Você deve usar a versão [LTS mais recente.](https://nodejs.org)

* Um editor de código

   Você precisa de um editor de código. A maioria dessa documentação e imagens se refere ao uso [Visual Studio Code](https://code.visualstudio.com). No entanto, sinta-se à vontade para usar qualquer editor de texto que preferir.

* Yeoman e Gulp CLI

   Para scaffold projetos usando o gerador, você deve instalar a ferramenta Yeoman e o gerenciador de tarefas cli gulp.

   Abra um prompt de comando e digite o seguinte:

   ```bash
   npm install yo gulp-cli --global
   ```

## <a name="install-the-generator"></a>Instalar o gerador

Instale o Teams yeoman com o seguinte comando:

```bash
npm init yo teams
```

Instale a versão de visualização do gerador com o seguinte comando:

```bash
npm init yo teams@preview
```

## <a name="generate-your-project"></a>Gerar seu projeto

Esta seção orienta você pelas etapas para gerar seu projeto.

**Para gerar seu projeto**

1. Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto.
1. Vá para o diretório e execute o comando `yo teams` . O gerador é iniciado.
1. Responda ao conjunto de perguntas solicitado pelo gerador:

   ![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. Insira um nome para seu projeto. Você pode deixá-lo como está pressionando Enter.
   1. Insira um caminho para o novo diretório se quiser criar um novo diretório. Como você já está no diretório que deseja, pressione Enter.
   1. Insira o título do seu projeto. Esse título será usado no manifesto e na descrição do seu aplicativo. 
   1. Insira um nome da empresa que também será usado no manifesto.
   1. Insira a versão do manifesto que você deseja usar. Para este tutorial, selecione `v1.5` , que é o esquema disponível geral atual.
   1. Selecione os itens que você deseja adicionar ao seu projeto. Você pode selecionar um único ou qualquer combinação de itens. Para este tutorial, basta selecionar *uma guia*:

    ![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

1. Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na Etapa 3.
1. Insira uma URL para o local onde você hospedará sua solução. 

   > [!NOTE]
   > A URL pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL do site do Azure.

1. Confirme se você deseja incluir testes de unidade para sua solução. A resposta padrão é **Sim**. Se você optar por incluir teste de unidade, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded. 
   > [!NOTE]
   > * Para este tutorial, escolha não incluir uma estrutura de teste.
   > * O gerador tem muitos recursos avançados integrados que você pode optar ou não.

1. Para facilitar a sua assinatura, você também será perguntado se deseja usar o aplicativo do Azure Insights para entrar. Se você selecionar **Sim**, será necessário fornecer uma chave de Insights aplicativo do Azure. 

   > [!NOTE]
   > Para este tutorial, opte por usar o aplicativo Insights.

   O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente. Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma web part SharePoint Online. Depois de fornecer o nome, o gerador gerará o projeto e instalará todas as dependências. Isso levará um minuto ou dois.

## <a name="add-code-to-your-tab"></a>Adicionar código à guia

Depois que o gerador for feito, você poderá abrir a solução no editor de código favorito. Tome um minuto ou dois e familiarize-se com como o código é organizado. Para obter mais informações, [consulte Project Documentação de](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) estrutura.

Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo. Esta é a classe typeScript React baseada em sua guia. 

1. Localize `render()` o método e adicione uma linha de código dentro do controle para que ele tenha esta `<PanelBody>` aparência:

   ``` TypeScript
   <PanelBody>
      <div style={styles.section}>
      Hello World! Yo Teams rocks!
      </div>
   </PanelBody>
   ```
1. Salve o arquivo e retorne ao prompt de comando.

## <a name="build-your-app"></a>Criar seu aplicativo

Agora você pode criar seu projeto. Isso é feito em duas etapas.

1. Crie o Teams de manifesto do aplicativo para o aplicativo que você carregou no Microsoft Teams. Isso é feito pela tarefa `gulp manifest` Gulp. Isso validará o manifesto e criará um arquivo zip no `./package` diretório.
1. Execute o `gulp build` comando para criar a solução. Isso transpile sua solução para a `./dist` pasta. 

## <a name="run-your-app"></a>Execute seu aplicativo

Para executar seu aplicativo, use o `gulp serve` comando. Isso criará e iniciará um servidor Web local para você testar seu aplicativo. O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto. 

Agora você deve ir para e `http://localhost:3007/myFirstAppTab/` garantir que sua guia está renderização. No entanto, ainda não Microsoft Teams. 

**Para renderizar sua guia em Microsoft Teams**

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

### <a name="run-your-app-in-microsoft-teams"></a>Execute seu aplicativo em Microsoft Teams

Microsoft Teams permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como ngrok. A boa notícia é que o projeto scaffolded tem esse projeto integrado. 

**Para executar seu aplicativo em Teams**

1. Execute `gulp ngrok-serve` no Terminal. Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS pública e exclusiva e ele também empacota o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa `gulp ngrok-serve` que `gulp serve` .
1. Crie uma nova Microsoft Teams equipe.
1. Selecione o nome da equipe > Teams Configurações > Aplicativos.
1. No canto inferior direito, selecione **Upload um aplicativo personalizado.**
1. Vá para a `package` pasta em sua pasta de projeto. 
1. Selecione o arquivo zip nessa pasta e selecione abrir. 
   Seu aplicativo agora é sideload em Microsoft Teams:

   ![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)
1. Volte para o **canal Geral** e selecione para adicionar uma **+** nova Guia. Você deve ver sua guia na lista de guias: ![ configurar guia](~/assets/yeoman-images/teams-first-app-5.png)
1. Selecione sua guia e siga as instruções para adicioná-la. Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem. Selecione *Salvar* para adicionar sua guia ao canal. Sua guia agora é carregada dentro Microsoft Teams!

   ![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

### <a name="upgrade-microsoft-teams"></a>Atualizar Microsoft Teams

Você também pode atualizar sua versão Microsoft Teams atual para a versão mais recente usando o Microsoft Teams gerador Yeoman.

**Para atualizar Microsoft Teams**

1. Obter a versão atual do Teams com o seguinte comando:

   ```PowerShell
    yo teams --version
   ```
2. Use o seguinte comando para selecionar e atualizar seu gerador:

   ```PowerShell
    yo
   ```
3. Use as teclas de seta para selecionar **Atualizar seus Geradores**:

   ![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. Selecione o gerador que você deseja na lista de geradores:
   > [!NOTE]
   > Use a barra de espaços para selecionar ou limpar uma versão Teams selecionada das opções disponíveis.

    ![imagem de UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > Leva alguns segundos para que a instalação Teams seja concluída.

5. Depois que a instalação for concluída, use o seguinte comando para verificar a versão instalada:

   ```PowerShell
    yo teams --version
   ```
   Parabéns! Você criou e implantou seu primeiro Microsoft Teams aplicativo. Você também atualizou Microsoft Teams.

 ## <a name="see-also"></a>Confira também

* [Visão geral dos tutoriais](code-samples.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)
