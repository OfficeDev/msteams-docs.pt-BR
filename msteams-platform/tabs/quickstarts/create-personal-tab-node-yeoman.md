---
title: 'QuickStart: criar uma guia pessoal personalizada com node. js e o gerador Yeoman para o Microsoft Teams'
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o gerador Yeoman para o Microsoft Teams.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: 2d1b17360b92a161179091c1f6ba06ffa194e958
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672446"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>QuickStart: criar uma guia pessoal personalizada com node. js e o gerador Yeoman para o Microsoft Teams

>[!NOTE]
>Este QuickStart segue as etapas descritas no [Build Your First Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) wiki encontrado no repositório do GitHub do Microsoft OfficeDev.

Neste QuickStart, veremos como criar uma guia pessoal personalizada usando o [gerador Yeoman do teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App). Também carregaremos o aplicativo para a equipe.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Você deseja criar uma guia configurável ou estática?**

Use as teclas de seta para selecionar a guia estático.

>[!IMPORTANT]
>O componente de caminho *yourDefaultTabNameTab*, referenciado neste QuickStart, é o valor que você inseriu no gerador para o *nome de guia padrão* mais a *guia*Word.
>
>Por exemplo: DefaultTabName: *MyTab* => */MyTabTab/*

## <a name="create-your-personal-tab"></a>Criar sua guia pessoal

Para adicionar uma guia pessoal a este aplicativo, você criará uma página de conteúdo e atualizará os arquivos existentes:

- No editor de códigos, crie um novo arquivo HTML, **Personal. html** e adicione a marcação a seguir:

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

- Salve **Personal. html** na pasta **da Web** do seu aplicativo:

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- Abra **manifest. JSON** em seu editor de código:

```bash
./src/manifest/manifest.json/
```

Adicione o seguinte à matriz vazia `staticTabs` (`staticTabs":[]`) e adicione o seguinte objeto JSON:

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

Lembre-se de atualizar o componente de caminho **"contentURL"** **yourDefaultTabNameTab** com seu nome de guia real.

- Salve o **manifesto. JSON**atualizado.

- A página de conteúdo deve ser fornecida em um IFrame. Abra **Tab. TS** no editor de código:

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- Adicione o seguinte à lista de decoradores de IFrame:

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- Certifique-se de salvar o arquivo **Tab atualizado. TS** . O código da guia está completo.

## <a name="build-and-run-your-application"></a>Criar e executar o aplicativo

Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para exibir sua guia pessoal, vá para`http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![captura de tela pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia esteja disponível na nuvem usando pontos de extremidade HTTPS. O Microsoft Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local para uma URL voltada para a Internet.

Para testar sua extensão de guia, você usará o [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo. O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS publicamente disponíveis do servidor Web em execução localmente. Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual em sua máquina local. Quando o computador é desligado ou vai para a suspensão, o serviço não estará mais disponível.

No prompt de comando, saia do localhost e digite o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que a guia tiver sido carregada no Microsoft Teams, via *ngrok*e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel seja encerrada.

## <a name="upload-your-application-to-teams"></a>Carregar seu aplicativo para o Microsoft Teams

- Abra o cliente do Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.
- No painel *YourTeams* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.
- No painel principal, selecione **aplicativos** na barra de guias e escolha **carregar um aplicativo personalizado** localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./Package** , selecione a pasta zip, clique com o botão direito do mouse e escolha **abrir**. Sua guia será carregada no Microsoft Teams.

## <a name="view-your-personal-tabs"></a>Exibir suas guias pessoais

Na barra de navegação localizada na extrema esquerda do cliente Teams, selecione o `...` menu e escolha seu aplicativo na lista.
