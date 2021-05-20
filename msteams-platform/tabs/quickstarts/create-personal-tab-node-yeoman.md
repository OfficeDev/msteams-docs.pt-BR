---
title: 'Quickstart: Crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para Microsoft Teams'
author: laujan
description: Um guia rápido para criar uma guia pessoal com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 88ad05aacaed69d695bc918e3e8a44ec18e560ae
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566597"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams

>[!NOTE]
>Esta rápida partida segue os passos descritos no [Aplicativo Build Your First Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório de GitHub Microsoft OfficeDev.

Nesta partida rápida, vamos caminhar criando uma guia pessoal personalizada usando o [gerador Teams Yeoman](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App). Também enviaremos o aplicativo para a Equipe.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Crie uma guia configurável ou estática**

Use as teclas de seta para selecionar a guia estática.

>[!IMPORTANT]
>O componente de caminho *que o seuDefaultTabNameTab,* referenciado nesta partida rápida, é o valor inserido no gerador para *nome de guia padrão* mais a palavra *Guia*.
>
>Por exemplo: DefaultTabName: *MyTab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Crie sua guia pessoal

Para adicionar uma guia pessoal a este aplicativo, você criará uma página de conteúdo e atualizará arquivos existentes:

- Em seu editor de código, crie um novo arquivo HTML, **personal.html** e adicione a seguinte marcação:

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

- Salve **personal.html** na pasta **web** do seu aplicativo:

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- Abra **manifest.jsno** seu editor de código:

    ```bash
    ./src/manifest/manifest.json/
    ```

Adicione o seguinte à matriz vazia `staticTabs` `staticTabs":[]` () e adicione o seguinte objeto JSON:

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

Lembre-se de atualizar o componente de caminho **"contentURL"** **seuDefaultTabNameTab** com seu nome de guia real.

- Salve os **manifest.jsatualizados.**

- Sua página de conteúdo deve servida em um IFrame. Abra **tab.ts** no seu editor de código:

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- Adicione o seguinte à lista de decoradores iFrame:

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- Certifique-se de salvar o arquivo **Tab.ts** atualizado. Seu código de guia está completo.

## <a name="build-and-run-your-application"></a>Construa e execute sua aplicação

Abra uma solicitação de comando em seu diretório de projetos para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para ver sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![captura de tela de guia pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabeleça um túnel seguro para sua guia

Microsoft Teams é um produto inteiramente baseado em nuvem e exige que seu conteúdo de guia esteja disponível na nuvem usando pontos finais HTTPS. Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local a uma URL voltada para a Internet.

Para testar a extensão da guia, você usará [o ngrok](https://ngrok.com/docs), que é incorporado neste aplicativo. O Ngrok é uma ferramenta de software proxy reversa que criará um túnel para os pontos finais HTTPS disponíveis publicamente do servidor web. Os pontos finais da web do servidor estarão disponíveis durante a sessão atual na sua máquina local. Quando a máquina estiver desligada ou dormir, o serviço não estará mais disponível.

Em seu prompt de comando, saia do localhost e digite o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for enviada para equipes da Microsoft, via **ngrok**, e salva com sucesso, você pode visualizá-la em Teams até que sua sessão de túnel termine.

## <a name="upload-your-application-to-teams"></a>Upload sua inscrição para Teams

- Abra o cliente Microsoft Teams. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .
- No painel **Suas Equipes** à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolher Gerenciar **equipe**.
- No painel principal selecione **Aplicativos** na barra de guia e escolha **Upload um aplicativo personalizado** localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip, clique com o botão direito do mouse e escolha **Abrir**. Sua guia será enviada para Teams.

## <a name="view-your-personal-tabs"></a>Veja suas guias pessoais

No navbar localizado à esquerda do cliente Teams, selecione o `...` menu e escolha seu aplicativo na lista.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia pessoal usando o ASP.NETCore](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
