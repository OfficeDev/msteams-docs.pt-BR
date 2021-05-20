---
title: Tutorial - Crie seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a construir aplicativos Microsoft Teams com o gerador Yeoman.
keywords: começando node.js nodejs yeoman
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
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Crie seu primeiro aplicativo de Microsoft Teams usando o gerador Yeoman

> [!Note]
> Este tutorial vem do [gerador Yeoman para Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).

Neste tutorial, vamos percorrer a criação do seu primeiro aplicativo Microsoft Teams usando o gerador Microsoft Teams Yeoman. Ele também o acompanha no processo de atualizar seu Teams usando o gerador Yeoman. O pré-requisito para começar com este tutorial é que você tenha uma conta Teams que permite [o sideloading do aplicativo](~/concepts/build-and-test/prepare-your-o365-tenant.md).

![yeoman gerador git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Configure e prepare sua máquina

Você precisa instalar o seguinte em sua máquina antes de começar a usar o gerador Yeoman.

### <a name="install-nodejs"></a>Instale o Node.js.

Você precisa ter Node.js instalado em sua máquina. Você deve usar a [versão LTS](https://nodejs.org)mais recente .

### <a name="install-a-code-editor"></a>Instalar um editor de códigos

Você precisa de um editor de código. A maioria desta documentação e imagens referem-se ao uso [de Visual Studio Code](https://code.visualstudio.com). No entanto, sinta-se livre para usar qualquer editor de texto que você preferir.

### <a name="install-yeoman-and-gulp-cli"></a>Instale Yeoman e Gulp CLI

Para projetos de andaimes usando o gerador, você deve instalar a ferramenta Yeoman e o gerente de tarefas Gulp CLI.

Abra um prompt de comando e digite o seguinte:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a>Instale o gerador

Instale o gerador yeoman Teams com o seguinte comando:

```bash
npm install generator-teams --global
```

Instale a versão de visualização do gerador com o seguinte comando:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Gere seu projeto

Esta seção o percorre as etapas para gerar seu projeto.

**Para gerar seu projeto**

1. Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto, e nesse diretório execute o comando `yo teams` . O gerador começa.
1. Responda ao conjunto de perguntas solicitadas pelo gerador:

   ![yo equipes](~/assets/yeoman-images/teams-first-app-1.png)

   1. A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando enter.
   1. A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual. Como você já está no diretório que você quer, basta pressionar enter.
   1. Na próxima pergunta, digite o título do seu projeto. Este título será usado no manifesto e descrição do seu aplicativo. 
   1. Em seguida, será solicitado um nome da empresa, que também será usado no manifesto.
   1. A quinta pergunta pergunta sobre qual versão do manifesto você quer usar. Para este tutorial selecione `v1.5` , que é o esquema geral disponível atual.
   1. Em seguida, o gerador perguntará quais itens você deseja adicionar ao seu projeto. Você pode selecionar uma única ou qualquer combinação de itens. Para este tutorial, basta selecionar *uma guia*:

    ![seleção de itens](~/assets/yeoman-images/teams-first-app-2.png)

1. Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na etapa 2.
1. Digite uma URL de onde você hospedará sua solução. 

   > [!NOTE]
   > A URL pode ser qualquer URL, mas por padrão o gerador sugere uma URL do site do Azure.

1. Na próxima pergunta, confirme se você deseja incluir testes unitários para sua solução. A resposta padrão é *sim*. Se você optar por incluir testes unitários, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo andaimes. 
   > [!NOTE]
   > * Para este tutorial, opte por não incluir uma estrutura de teste.
   > * O gerador tem um monte de recursos avançados incorporados que você pode optar ou optar por não participar.

1. A fim de facilitar a assinatura para você, você também será perguntado se você quer usar o Azure Application Insights para fazer login. Se você escolher *Sim,* você precisará fornecer uma chave de Insights de Aplicativos Azure. 

   > [!NOTE]
   > Para este tutorial opt-out de usar o Application Insights.

O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente. Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se você quiser ser capaz de usar este aplicativo como uma SharePoint parte da Web Online. Depois de fornecer o nome, o gerador irá gerar o projeto e instalar todas as dependências. Isso vai levar um minuto ou dois.

## <a name="add-some-code-to-your-tab"></a>Adicione algum código à sua guia

Depois que o gerador estiver pronto, você pode abrir a solução no seu editor de código favorito. Tire um minuto ou dois e familiarize-se com a forma como o código é organizado. Para obter mais informações, consulte [Project documentação da Estrutura.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)

Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo. Esta é a classe TypeScript React para sua guia. Localize o `render()` método e adicione uma linha de código dentro do controle para que ele se pareça com `<PanelBody>` este:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Salve o arquivo e retorne ao prompt de comando.

## <a name="build-your-app"></a>Criar seu aplicativo

Agora você pode construir seu projeto. Isso é feito em duas etapas (ou um passo, veja abaixo).

Primeiro você precisa criar o arquivo manifesto do aplicativo Teams, que você carrega/sideload em Microsoft Teams. Isso é feito pela tarefa `gulp manifest` Gulp. Isso validará o manifesto e criará um arquivo zip no `./package` diretório.

Para construir sua solução, você usa o `gulp build` comando. Isso transpilará sua solução para a `./dist` pasta. 

## <a name="run-your-app"></a>Execute seu aplicativo

Para executar seu aplicativo, você usa o `gulp serve` comando. Isso irá construir e iniciar um servidor web local para você testar seu aplicativo. O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto. 

Agora você deve ser capaz de navegar `http://localhost:3007/myFirstAppTab/` para garantir que sua guia esteja renderizando. No entanto, ainda não Microsoft Teams:

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Execute seu aplicativo em Microsoft Teams

Microsoft Teams não permite que você tenha seu aplicativo hospedado no site local, então você precisa publicá-lo em uma URL pública ou usar um proxy como ngrok.

A boa notícia é que o projeto do andaime tem esse embutido. Quando você executar `gulp ngrok-serve` o serviço ngrok será iniciado em segundo plano, com uma entrada DNS única e pública e também embalará o manifesto com essa URL única e, em seguida, fará exatamente a mesma coisa que `gulp serve` .

Depois de `gulp ngrok-serve` executar, crie uma nova equipe de Microsoft Teams e quando for criada clique no nome da Equipe, para ir às configurações das equipes e, em seguida, selecionar *Aplicativos*. No canto inferior direito, você deve ver um link *Upload um aplicativo personalizado,* selecione-o e, em seguida, navegue até a pasta do projeto e a subpasta chamada `package` . Selecione o arquivo zip nessa pasta e escolha abrir. Seu aplicativo está agora carregado de lado para Microsoft Teams:

![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)

Volte para o canal *Geral* e selecione *+* adicionar uma nova Guia. Você deve ver sua guia na lista de guias:

![configurar aba](~/assets/yeoman-images/teams-first-app-5.png)

Escolha sua guia e siga as instruções para adicioná-la. Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a fonte. Selecione *Salvar* para adicionar sua guia ao canal. Uma vez feita sua guia deve ser carregada dentro Microsoft Teams!

![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a>Microsoft Teams de upgrade

Você também pode atualizar sua versão atual Microsoft Teams para a versão mais recente usando o gerador Microsoft Teams Yeoman.

**Para atualizar Microsoft Teams**

1. Obtenha a versão atual de Teams com o seguinte comando:

   ```PowerShell
    yo teams --version
   ```
2. Use o seguinte comando para selecionar atualizar seu gerador:

   ```PowerShell
    yo
   ```
3. Use as teclas de seta para escolher **Atualizar seus geradores:**

   ![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. Selecione o gerador que deseja na lista de geradores:
   > [!NOTE]
   > Use a barra de espaço para selecionar ou limpar uma versão Teams selecionada das opções disponíveis.

    ![imagem do UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > Leva alguns segundos a minutos para Teams instalação ser concluída.

5. Após a instalação ser concluída, use o seguinte comando para verificar a versão instalada:

   ```PowerShell
    yo teams --version
   ```
   
**Parabéns! Você construiu e implantou seu primeiro aplicativo de Microsoft Teams. Você também atualizou Microsoft Teams.**
