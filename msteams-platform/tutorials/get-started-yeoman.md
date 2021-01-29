---
title: 'Tutorial : Criar seu primeiro aplicativo usando o gerador Yeoman'
description: Saiba como começar a criar aplicativos do Microsoft Teams com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: f7f0fb3ba1be28dfa7d343be3af9d122b4ad090d
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037001"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Criar seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman

>[!Note]
>Este tutorial vem do gerador [Yeoman para wiki do Teams.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)

Neste tutorial, vamos dar um passo a passo para criar seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman do Microsoft Teams. Ele supõe que você tenha uma conta do Teams que permite o [sideload do aplicativo.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

![yeoman generator git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Configurar e preparar seu computador

Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman.

### <a name="install-nodejs"></a>Instale o Node.js.

Você precisa ter Node.js instalado em seu computador. Você deve usar a versão [mais recente do LTS.](https://nodejs.org)

### <a name="install-a-code-editor"></a>Instalar um editor de códigos

Você também precisa de um editor de código, sinta-se à vontade para usar o editor de texto de sua preferência. No entanto, a maioria desta documentação e capturas de tela se refere ao uso do [Visual Studio Code.](https://code.visualstudio.com)

### <a name="install-yeoman-and-gulp-cli"></a>Instalar Yeoman e Gulp CLI

Para fazer scaffold dos projetos usando o gerador do Teams, você precisa instalar a ferramenta Yeoman, bem como o gerenciador de tarefas da CLI gulp.

Abra um prompt de comando e digite o seguinte:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a>Instalar o gerador

Instale o gerador Yeoman do Teams com o seguinte comando:

```bash
npm install generator-teams --global
```

Para instalar versões de visualização do gerador, execute este comando:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Gerar seu projeto

Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto e, nesse diretório, execute o `yo teams` comando.

Isso inicia o gerador, que solicita um conjunto de perguntas.

![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando Enter. A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual. Como já estamos no diretório que queremos, basta pressionar Enter.

A etapa a seguir solicita um título do seu projeto. Esse título será usado no manifesto e na descrição do seu aplicativo. E, em seguida, você será solicitado a usar um nome de empresa, que também será usado no manifesto.

A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar. Para este `v1.5` tutorial, selecione , que é o esquema disponível geral atual.

Depois disso, o gerador perguntará quais itens você deseja adicionar ao seu projeto. Você pode selecionar um único item ou qualquer combinação de itens. Por enquanto, basta selecionar *uma guia*.

![seleção de itens](~/assets/yeoman-images/teams-first-app-2.png)

Com base nos itens selecionados, você será solicitado a fazer um conjunto de perguntas de acompanhamento.

Agora você precisa inserir uma URL de onde hospedará sua solução. Pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL de Sites do Azure.

O gerador tem muitos recursos avançados integrados que você pode optar ou não. Seguindo a pergunta da URL, você será solicitado se quiser incluir testes de unidade para sua solução, o padrão é Sim. Se você escolher isso, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded. Para este tutorial, opte por não incluir uma estrutura de teste.

Para facilitar o registro em log para você, você também será perguntado se deseja usar o Azure Application Insights para registrar em log. Se você escolher Sim, precisará fornecer uma chave do Insights do Aplicativo do Azure. Para este tutorial, opte por não usar o Application Insights.

O próximo conjunto de perguntas será baseado em sua seleção de itens anteriormente. Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma Web Part do SharePoint Online. Depois de ter fornecido esse nome, o gerador gerará o projeto e instalará todas as dependências. Isso levará um minuto ou dois.

## <a name="add-some-code-to-your-tab"></a>Adicionar código à guia

Quando o gerador for feito, você poderá abrir a solução em seu editor de código favorito. Leve um minuto ou dois e familiarize-se com a forma como o código é organizado. Você pode ler mais sobre isso na documentação da [Estrutura do](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) Projeto.

A guia estará localizada no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo. Esta é a classe baseada em TypeScript React para sua guia. Localize o método e adicione uma linha de código dentro do controle para `render()` que ele tenha esta `<PanelBody>` aparência:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Salve o arquivo e retorne ao prompt de comando.

## <a name="build-your-app"></a>Criar seu aplicativo

Agora você pode criar seu projeto. Isso é feito em duas etapas (ou em uma etapa, veja abaixo).

Primeiro, você precisa criar o arquivo de manifesto do aplicativo Teams, que você carrega/faz sideload no Microsoft Teams. Isso é feito pela tarefa `gulp manifest` gulp. Isso validará o manifesto e criará um arquivo zip no `./package` diretório.

Para criar sua solução, use o `gulp build` comando. Isso transpile sua solução para a `./dist` pasta. 

## <a name="run-your-app"></a>Executar seu aplicativo

Para executar seu aplicativo, use o `gulp serve` comando. Isso criará e iniciará um servidor Web local para você testar seu aplicativo. O comando também recriará o aplicativo sempre que você salvar um arquivo em seu projeto. 

Agora você deve ser capaz de navegar para `http://localhost:3007/myFirstAppTab/` garantir que sua guia seja renderização. No entanto, ainda não está no Microsoft Teams.

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Executar seu aplicativo no Microsoft Teams

O Microsoft Teams não permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como o ngrok.

Uma boa notícia é que o projeto com scaffolded tem esse projeto integrado. Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS exclusiva e pública e ele também empacota o manifesto com essa URL exclusiva e, em seguida, faz exatamente o mesmo `gulp ngrok-serve` que `gulp serve` .

Depois de executar, crie uma nova equipe do Microsoft Teams e, quando ela for criada, clique no nome da equipe, para ir para as configurações de equipe e, em seguida, `gulp ngrok-serve` selecione *Aplicativos.* No canto inferior direito, você verá um link Carregar um aplicativo personalizado, selecione-o e navegue até *a* pasta do projeto e a subpasta `package` chamada. Selecione o arquivo zip nessa pasta e escolha abrir. Seu aplicativo agora está em sideload no Microsoft Teams.

![aplicativo de sideload](~/assets/yeoman-images/teams-first-app-4.png)

Volte para o *canal Geral* e selecione adicionar uma *+* nova guia. Você deverá ver sua guia na lista de guias.

![configurar guia](~/assets/yeoman-images/teams-first-app-5.png)

Escolha sua guia e siga as instruções para adicioná-la. Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem. Selecione *Salvar* para adicionar sua guia ao canal. Quando terminar, sua guia deverá ser carregada no Microsoft Teams!

![guia em execução nas equipes](~/assets/yeoman-images/teams-first-app-6.png)

**Parabéns! Você criou e implantou seu primeiro aplicativo Microsoft Teams**
