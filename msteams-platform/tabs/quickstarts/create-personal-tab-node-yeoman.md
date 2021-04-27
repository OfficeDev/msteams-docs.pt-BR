---
title: 'Início rápido: crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para o Microsoft Teams'
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o Gerador Yeoman para o Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 30143fa3c84a68ae6c34176b252badaa4cef9613
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019549"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Início rápido: crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para o Microsoft Teams

>[!NOTE]
>Esse início rápido segue as etapas descritas no [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório do GitHub do Microsoft OfficeDev.

Neste início rápido, vamos passo a passo criando uma guia pessoal personalizada usando o [gerador Yeoman do Teams.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Também carregaremos o aplicativo para a Equipe.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Você deseja criar uma guia configurável ou estática?**

Use as teclas de seta para selecionar a guia estática.

>[!IMPORTANT]
>O componente de *caminho que seuDefaultTabNameTab*, referenciado neste início rápido, é o valor que você inscrevia no gerador para *Nome* da Guia Padrão mais a *palavra Tab*.
>
>Por exemplo: DefaultTabName: *MyTab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Criar sua guia pessoal

Para adicionar uma guia pessoal a esse aplicativo, você criará uma página de conteúdo e atualizará arquivos existentes:

- No editor de código, crie um novo arquivo HTML, **personal.html** e adicione a seguinte marcação:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>
            <!-- Todo: add your a title here -->
        </title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!-- inject:css -->
        <!-- endinject -->
    </head>
        <body>
            <h1>Personal Tab</h1>
            <p><img src="/assets/icon.png"></p>
            <p>This is your personal tab!</p>
        </body>
</html>
```

- Salve **personal.html** na pasta web do **aplicativo:**

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- Abra **manifest.jsno** editor de código:

```bash
./src/manifest/manifest.json/
```

Adicione o seguinte à matriz `staticTabs` vazia ( ) e adicione o seguinte objeto `staticTabs":[]` JSON:

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

Lembre-se de atualizar o componente de caminho **"contentURL"** **yourDefaultTabNameTab** com o nome da guia real.

- Salve omanifest.js **atualizado em**.

- Sua página de conteúdo deve ser atendida em um IFrame. Abra **Tab.ts no** editor de código:

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- Adicione o seguinte à lista de decoradores IFrame:

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- Salve o arquivo **Tab.ts** atualizado. Seu código de tabulação está completo.

## <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para exibir sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![captura de tela de guia pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS. O Teams não permite a hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.

Para testar sua extensão de tabulação, você usará [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo. O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente. Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual no computador local. Quando o computador é desligado ou vai para o sono, o serviço não estará mais disponível.

No prompt de comando, saia do localhost e insira o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for carregada para o Microsoft Teams, por meio do *ngrok* e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel termine.

## <a name="upload-your-application-to-teams"></a>Carregar seu aplicativo no Teams

- Abra o cliente do Microsoft Teams. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)
- No painel *YourTeams* à esquerda, selecione o menu ao lado da equipe que você está usando para testar sua guia e `...` escolha Gerenciar **equipe**.
- No painel principal, selecione **Aplicativos** na barra de guias e escolha **Carregar** um aplicativo personalizado localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip, clique com o botão direito do mouse e escolha **Abrir**. Sua guia será carregada no Teams.

## <a name="view-your-personal-tabs"></a>Exibir suas guias pessoais

Na barra de entrada localizada à extrema esquerda do cliente do Teams, selecione o menu e `...` escolha seu aplicativo na lista.
