---
title: Introdução ao gerador Yeoman para o Microsoft Teams
description: Introdução à criação de aplicativos ótimos com o gerador Yeoman para o Microsoft Teams
keywords: introdução node.js NodeJS Yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: f9b3f165d3b5387f8e7d30563134ed4889920ca5
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237990"
---
# <a name="build-your-first-microsoft-teams-app"></a>Criar seu primeiro aplicativo do Microsoft Teams

>[!Note]
>Este tutorial é proveniente do [gerador Yeoman para o Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)

Neste tutorial, vamos examinar a criação de seu primeiro aplicativo do Microsoft Teams usando o gerador Yeoman do Microsoft Teams. Ele pressupõe que você [habilitou o carregamento lateral de aplicativos do Microsoft Teams](~/concepts/build-and-test/prepare-your-o365-tenant.md).

![gerador Yeoman git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Configurar e preparar sua máquina

Você precisa instalar o seguinte em sua máquina antes de começar a usar o gerador de Teams.

### <a name="install-node"></a>Nó de instalação

Você precisa ter o NodeJS instalado em sua máquina. Você deve usar a versão mais recente do [LTS](https://nodejs.org).

### <a name="install-a-code-editor"></a>Instalar um editor de códigos

Você também precisa de um editor de códigos, fique à vontade para usar qualquer editor de texto que preferir. No entanto, a maioria desta documentação e capturas de tela se referem ao uso do [Visual Studio Code](https://code.visualstudio.com).

### <a name="install-yeoman-and-gulp-cli"></a>Instalar a CLI do Yeoman e do Gulp

Para poder estruturarr projetos usando o gerador de equipes, você precisa instalar a ferramenta Yeoman, bem como o Gerenciador de tarefas CLI do Gulp.

Abra um prompt de comando e digite o seguinte:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-microsoft-teams-apps-generator---yo-teams"></a>Instalar o gerador de aplicativos do Microsoft Teams-Yo

O gerador Yeoman para os aplicativos do Microsoft Teams é instalado com o seguinte comando:

```bash
npm install generator-teams --global
```

#### <a name="install-preview-versions"></a>Instalar versões prévias

Se você deseja instalar versões prévias do gerador de Teams com este comando:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Gerar seu projeto

Abra um prompt de comando e crie um novo diretório no qual você deseja criar seu projeto e, nesse diretório, digite o comando `yo teams` . Isso iniciará o gerador de aplicativos do Teams e você será solicitado a fornecer um conjunto de perguntas.

![Times Yo](~/assets/yeoman-images/teams-first-app-1.png)

A primeira pergunta é sobre o nome do projeto, você pode deixá-lo como está pressionando ENTER. A pergunta seguinte pergunta se você deseja criar um novo diretório ou usar o atual. Como já estamos no diretório desejado, basta pressionar Enter.

A etapa a seguir solicita um título do seu projeto, este título será usado no manifesto e na descrição do seu aplicativo. E, em seguida, você será solicitado a fornecer um nome de empresa, que também será usado no manifesto.

A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar. Para este tutorial `v1.5` , selecione, que é o esquema geral disponível atual.

Depois disso, o gerador solicitará quais itens você deseja adicionar ao seu projeto. Você pode selecionar um único ou qualquer combinação de itens. Por enquanto, basta selecionar *uma guia*.

![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

Com base nos itens selecionados, você será solicitado a fornecer um conjunto de perguntas de acompanhamento.

Agora você precisa inserir uma URL de onde você hospedará sua solução. Pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL de sites do Azure.

O gerador tem vários recursos avançados internos que você pode optar por aceitar ou recusar o. Após a pergunta de URL, você será perguntado se deseja incluir testes de unidade para sua solução, o padrão é sim. Se você escolher este projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens sendo estruturado. Para este tutorial, opte por não incluir uma estrutura de teste.

Para facilitar o registro em log, você também será perguntado se deseja usar o Azure Application insights para registro em log. Se você escolher Sim, será necessário fornecer uma chave do Azure Application insights. Para este tutorial, opte por usar o Application insights.

O próximo conjunto de perguntas será baseado na seleção de itens anteriormente. Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja poder usar este aplicativo como uma Web Part do SharePoint Online. Depois de fornecer esse nome, o gerador gerará o projeto e instalará todas as dependências. Isso levará um minuto ou dois.

## <a name="add-some-code-to-your-tab"></a>Adicionar um código à sua guia

Depois que o gerador for concluído, você poderá abrir a solução em seu editor de código favorito. Reserve um minuto ou dois e familiarize-se com o modo como o código está organizado-você pode ler mais sobre isso na documentação da [estrutura do projeto](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) .

Sua guia estará localizada no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo. Esta é a classe baseada em reagir do TypeScript para sua guia. Localize o `render()` método e adicione uma linha de código dentro do `<PanelBody>` controle para que ele tenha a seguinte aparência:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Salve o arquivo e retorne ao prompt de comando.

## <a name="build-your-app"></a>Criar seu aplicativo

Agora você pode criar seu projeto. Isso é feito em duas etapas (ou uma etapa, veja abaixo).

Primeiro, você precisa criar o arquivo de manifesto do aplicativo Teams, que você carrega/Sideload no Microsoft Teams. Isso é feito pela tarefa Gulp `gulp manifest` . Isso validará o manifesto e criará um arquivo zip no `./package` diretório.

Para compilar a solução, use o `gulp build` comando. Isso irá transcompilar sua solução na `./dist` pasta. 

## <a name="run-your-app"></a>Executar o aplicativo

Para executar o aplicativo, use o `gulp serve` comando. Isso criará e iniciará um servidor Web local para testar seu aplicativo. O comando também recriará o aplicativo sempre que você salvar um arquivo em seu projeto. 

Agora você poderá navegar até `http://localhost:3007/myFirstAppTab/` para garantir que sua guia está sendo renderizada. No entanto, ainda não no Microsoft Teams.

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Executar o aplicativo no Microsoft Teams

O Microsoft Teams não permite que seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy, como ngrok.

Boa notícia é que o projeto estruturado tem esse interno. Quando você executar `gulp ngrok-serve` o serviço ngrok será iniciado em segundo plano, com uma entrada DNS exclusiva e pública e também empacotará o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa que `gulp serve` .

Depois de executar `gulp ngrok-serve` o, criar uma nova equipe do Microsoft Teams e quando ela for criada clique no nome da equipe, vá para as configurações do Teams e selecione *aplicativos*. No canto inferior direito, você verá um link *carregar um aplicativo personalizado*, selecione-o e navegue até a pasta do projeto e a subpasta chamada `package` . Selecione o arquivo zip nessa pasta e escolha abrir. Seu aplicativo agora está suplementos foi feito no Microsoft Teams.

![aplicativo Suplementos foi feito](~/assets/yeoman-images/teams-first-app-4.png)

Volte para o canal *geral* e selecione *+* para adicionar uma nova guia. Você deve ver sua guia na lista de guias.

![guia Configurar](~/assets/yeoman-images/teams-first-app-5.png)

Escolha sua guia e siga as instruções para adicioná-la. Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual é possível editar a fonte. Selecione *salvar* para adicionar sua guia ao canal. Após a conclusão, a guia deve ser carregada no Microsoft Teams!

![guia executando no Teams](~/assets/yeoman-images/teams-first-app-6.png)

**Parabéns! Você criou e implantou seu primeiro aplicativo do Microsoft Teams**
