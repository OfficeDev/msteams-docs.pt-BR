---
title: Criar uma guia de canal e grupo personalizado com Node.js e o gerador Yeoman para o Microsoft Teams
author: laujan
description: Um guia de início rápido para criar uma guia de canal e grupo com o gerador Yeoman para o Microsoft Teams.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 77081f83c753f812032ccfebe2accd3cb8859f99
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818931"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Criar uma guia de canal e grupo personalizado com Node.js e o gerador Yeoman para o Microsoft Teams

>[!NOTE]
>Este QuickStart segue as etapas descritas no [Build Your First Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) wiki encontrado no repositório do GitHub do Microsoft OfficeDev.

Neste QuickStart, vamos examinar a criação de uma guia de canal e de grupo personalizada usando o [gerador Yeoman do teams](https://github.com/OfficeDev/generator-teams/).

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Você deseja criar uma guia configurável ou estática?**

Use as teclas de seta para selecionar a guia configurável.

**Quais escopos você pretende usar para sua guia?**

Você pode selecionar uma equipe e/ou um chat de grupo

**Deseja que esta guia esteja disponível no SharePoint Online? (S/n)** 

Selecione **n**.

>[!IMPORTANT]
>O componente de caminho **yourDefaultTabNameTab**, referenciado neste QuickStart, é o valor que você inseriu no gerador para o **nome de guia padrão** mais a **guia**Word.
>
>Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

No diretório do projeto, navegue até o seguinte:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

É aí que você encontrará sua lógica de tabulação. Localize o `render()` método e adicione a seguinte `<div>` marca e conteúdo à parte superior do `<PanelBody>` código do contêiner:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Certifique-se de salvar o arquivo atualizado.

## <a name="build-and-run-your-application"></a>Criar e executar o aplicativo

Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para exibir a página de configuração de guia, vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Você verá o seguinte:

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia esteja disponível na nuvem usando pontos de extremidade HTTPS. O Microsoft Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local para uma URL voltada para a Internet.

Para testar sua extensão de guia, você usará o [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo. O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS publicamente disponíveis do servidor Web em execução localmente. Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual em sua máquina local. Quando o computador é desligado ou vai para a suspensão, o serviço não estará mais disponível.

No prompt de comando, saia do localhost e digite o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que a guia tiver sido carregada no Microsoft Teams e salva com êxito, você poderá exibi-la na Galeria de guias, adicioná-la à barra de guias e interagir com ela até que a sessão de túnel do ngrok seja encerrada. Se você reiniciar sua sessão do ngrok, será necessário atualizar seu aplicativo com a nova URL.

## <a name="upload-your-application-to-teams"></a>Carregar seu aplicativo para o Microsoft Teams

- Abra o cliente do Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.
- No painel *YourTeams* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.
- No painel principal, selecione **aplicativos** na barra de guias e escolha **carregar um aplicativo personalizado** localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./Package** , selecione a pasta zip do pacote de aplicativos e escolha **abrir**. Sua guia será carregada no Microsoft Teams.
- Retorne à sua equipe, escolha o canal onde você deseja exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.
- Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para a guia canal/grupo.
- Selecione **salvar** e sua guia será adicionada à barra de guias do canal.
