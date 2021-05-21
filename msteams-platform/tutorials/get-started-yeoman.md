---
title: Tutorial - Criar seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a criar Microsoft Teams aplicativos com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 96a4f64d487e1d16bf25abd978759fedeac1061c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566821"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Criar seu primeiro Microsoft Teams usando o gerador Yeoman

> [!Note]
> Este tutorial vem do gerador [Yeoman para Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).

Neste tutorial, vamos continuar criando seu primeiro aplicativo Microsoft Teams usando o Microsoft Teams yeoman. Ele também orienta você pelo processo de atualização do seu Teams usando o gerador Yeoman. O pré-requisito para começar com este tutorial é que você tem uma conta Teams que permite o [sideload de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md).

![git do gerador yeoman](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Configurar e preparar seu computador

Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman.

### <a name="install-nodejs"></a>Instale o Node.js.

Você precisa ter Node.js instalado em seu computador. Você deve usar a versão [LTS mais recente.](https://nodejs.org)

### <a name="install-a-code-editor"></a>Instalar um editor de códigos

Você precisa de um editor de código. A maioria dessa documentação e imagens se refere ao uso [Visual Studio Code](https://code.visualstudio.com). No entanto, sinta-se à vontade para usar qualquer editor de texto que preferir.

### <a name="install-yeoman-and-gulp-cli"></a>Instalar Yeoman e Gulp CLI

Para scaffold projetos usando o gerador, você deve instalar a ferramenta Yeoman e o gerenciador de tarefas cli gulp.

Abra um prompt de comando e digite o seguinte:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a>Instalar o gerador

Instale o Teams yeoman com o seguinte comando:

```bash
npm install generator-teams --global
```

Instale a versão de visualização do gerador com o seguinte comando:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Gerar seu projeto

Esta seção orienta você pelas etapas para gerar seu projeto.

**Para gerar seu projeto**

1. Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto e, nesse diretório, execute o comando `yo teams` . O gerador é iniciado.
1. Responda ao conjunto de perguntas solicitado pelo gerador:

   ![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando enter.
   1. A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual. Como você já está no diretório que deseja, pressione enter.
   1. Na próxima pergunta, digite o título do seu projeto. Esse título será usado no manifesto e na descrição do seu aplicativo. 
   1. Em seguida, será solicitado um nome da empresa, que também será usado no manifesto.
   1. A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar. Para este tutorial, selecione `v1.5` , que é o esquema disponível geral atual.
   1. Em seguida, o gerador perguntará quais itens você deseja adicionar ao seu projeto. Você pode selecionar um único ou qualquer combinação de itens. Para este tutorial, basta selecionar *uma guia*:

    ![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

1. Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na etapa 2.
1. Insira uma URL de onde você hospedará sua solução. 

   > [!NOTE]
   > A URL pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL do site do Azure.

1. Na próxima pergunta, confirme se você deseja incluir testes de unidade para sua solução. A resposta padrão é *sim*. Se você optar por incluir teste de unidade, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded. 
   > [!NOTE]
   > * Para este tutorial, escolha não incluir uma estrutura de teste.
   > * O gerador tem muitos recursos avançados integrados que você pode optar ou não.

1. Para facilitar a sua assinatura, você também será perguntado se deseja usar o Azure Application Insights para entrar. Se você escolher *Sim*, será necessário fornecer uma chave do Azure Application Insights. 

   > [!NOTE]
   > Para este tutorial, opt-out of using Application Insights.

O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente. Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma web part SharePoint Online. Depois de fornecer o nome, o gerador gerará o projeto e instalará todas as dependências. Isso levará um minuto ou dois.

## <a name="add-some-code-to-your-tab"></a>Adicionar algum código à sua guia

Depois que o gerador for feito, você poderá abrir a solução no editor de código favorito. Tome um minuto ou dois e familiarize-se com como o código é organizado. Para obter mais informações, [consulte Project Documentação de](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) estrutura.

Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo. Esta é a classe typeScript React baseada em sua guia. Localize `render()` o método e adicione uma linha de código dentro do controle para que ele tenha esta `<PanelBody>` aparência:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Salve o arquivo e retorne ao prompt de comando.

## <a name="build-your-app"></a>Criar seu aplicativo

Agora você pode criar seu projeto. Isso é feito em duas etapas (ou em uma etapa, consulte abaixo).

Primeiro, você precisa criar o arquivo de manifesto Teams App, que você carrega/carrega no Microsoft Teams. Isso é feito pela tarefa `gulp manifest` Gulp. Isso validará o manifesto e criará um arquivo zip no `./package` diretório.

Para criar sua solução, use o `gulp build` comando. Isso transpile sua solução para a `./dist` pasta. 

## <a name="run-your-app"></a>Executar seu aplicativo

Para executar seu aplicativo, use o `gulp serve` comando. Isso criará e iniciará um servidor Web local para você testar seu aplicativo. O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto. 

Agora você deve ser capaz de navegar para `http://localhost:3007/myFirstAppTab/` garantir que sua guia seja renderização. No entanto, ainda não Microsoft Teams:

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Execute seu aplicativo em Microsoft Teams

Microsoft Teams permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como ngrok.

A boa notícia é que o projeto scaffolded tem esse projeto integrado. Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS pública e exclusiva e ele também empacota o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa `gulp ngrok-serve` que `gulp serve` .

Depois de executar, crie uma nova equipe Microsoft Teams e, quando for criada, clique no nome da equipe, para ir até as configurações de equipe e selecione `gulp ngrok-serve` *Aplicativos*. No canto inferior direito, você deve ver um link Upload um aplicativo personalizado, selecione-o e navegue até *sua* pasta de projeto e a subpasta chamada `package` . Selecione o arquivo zip nessa pasta e escolha abrir. Seu aplicativo agora é sideload em Microsoft Teams:

![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)

Volte para o *canal Geral* e selecione para adicionar uma *+* nova Guia. Você deve ver sua guia na lista de guias:

![configurar guia](~/assets/yeoman-images/teams-first-app-5.png)

Escolha sua guia e siga as instruções para adicioná-la. Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem. Selecione *Salvar* para adicionar sua guia ao canal. Depois de terminar, sua guia deve ser carregada dentro Microsoft Teams!

![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a>Atualizar Microsoft Teams

Você também pode atualizar sua versão Microsoft Teams atual para a versão mais recente usando o Microsoft Teams gerador Yeoman.

**Para atualizar Microsoft Teams**

1. Obter a versão atual do Teams com o seguinte comando:

   ```PowerShell
    yo teams --version
   ```
2. Use o seguinte comando para selecionar atualizar seu gerador:

   ```PowerShell
    yo
   ```
3. Use as teclas de seta para escolher **Atualizar seus Geradores**:

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
   
**Parabéns! Você criou e implantou seu primeiro Microsoft Teams aplicativo. Você também atualizou Microsoft Teams.**
