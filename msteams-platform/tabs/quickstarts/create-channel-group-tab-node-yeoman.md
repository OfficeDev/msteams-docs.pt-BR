---
title: Crie um canal personalizado e tab em grupo com Node.js e o Gerador Yeoman para Microsoft Teams
author: laujan
description: Um guia rápido para criar uma guia de canal e grupo com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 559393884e3b8a4aad1787ea4ca8f9f4de54d151
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566639"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Crie uma guia personalizada de canal e grupo usando Node.js e o Gerador Yeoman para Microsoft Teams

>[!NOTE]
>Esta rápida partida segue os passos descritos no [Aplicativo Build Your First Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório de GitHub Microsoft OfficeDev.

Nesta partida rápida, vamos caminhar criando um canal personalizado e uma guia de grupo usando o [gerador Teams Yeoman](https://github.com/OfficeDev/generator-teams/).

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Deseja criar uma guia configurável ou estática?**

Use as teclas de seta para selecionar a guia configurável.

**Quais escopos você pretende usar para o seu Tab?**

Você pode selecionar uma equipe e/ou um bate-papo em grupo

**Você deseja que esta guia esteja disponível em SharePoint Online? (Y/n)** 

Selecione **n**.

>[!IMPORTANT]
>O componente de caminho **que o seuDefaultTabNameTab,** referenciado nesta partida rápida, é o valor inserido no gerador para **nome de guia padrão** mais a palavra **Guia**.
>
>Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

Em seu diretório de projetos, navegue até o seguinte:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

É aí que você encontrará sua lógica de guia. Localize o `render()` método e adicione a seguinte tag e conteúdo à parte superior do código do `<div>` `<PanelBody>` contêiner:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Certifique-se de salvar o arquivo atualizado.

## <a name="build-and-run-your-application"></a>Construa e execute sua aplicação

Abra uma solicitação de comando em seu diretório de projetos para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para exibir sua página de configuração de guia vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Você verá o seguinte:

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabeleça um túnel seguro para sua guia

Microsoft Teams é um produto inteiramente baseado em nuvem e exige que seu conteúdo de guia esteja disponível na nuvem usando pontos finais HTTPS. Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local a uma URL voltada para a Internet.

Para testar a extensão da guia, você usará [o ngrok](https://ngrok.com/docs), que é incorporado neste aplicativo. O Ngrok é uma ferramenta de software proxy reversa que criará um túnel para os pontos finais HTTPS disponíveis publicamente do servidor web. Os pontos finais da web do servidor estarão disponíveis durante a sessão atual na sua máquina local. Quando a máquina estiver desligada ou dormir, o serviço não estará mais disponível.

Em seu prompt de comando, saia do localhost e digite o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for enviada para equipes da Microsoft e salva com sucesso, você pode visualizá-la na galeria de guias, adicioná-la à barra de guias e interagir com ela até que a sessão do túnel ngrok termine. Se você reiniciar sua sessão ngrok, você precisará atualizar seu aplicativo com a nova URL.

## <a name="upload-your-application-to-teams"></a>Upload sua inscrição para Teams

- Abra o cliente Microsoft Teams. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .
- No painel *Suas Equipes* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolher Gerenciar **equipe**.
- No painel principal selecione **Aplicativos** na barra de guia e escolha **Upload um aplicativo personalizado** localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip do pacote do aplicativo e escolha **Abrir**. Sua guia será enviada para Teams.
- Retorne à sua equipe, escolha o canal onde deseja exibir a guia, selecione ➕ na barra de guia e escolha sua guia na galeria.
- Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para sua guia canal/grupo.
- Selecione **Salvar** e sua guia será adicionada à barra de guias do canal.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia de canal e grupo personalizada com ASP.NETCore](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)