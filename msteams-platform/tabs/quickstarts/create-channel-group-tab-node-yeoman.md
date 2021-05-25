---
title: Criar um canal personalizado e uma guia de grupo com Node.js e o Gerador Yeoman para Microsoft Teams
author: laujan
description: Um guia de início rápido para criar um canal e uma guia de grupo com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 70b1dbe5a5abafa44ddbdf9045c55a33cf8fcb20
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630234"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Crie um canal personalizado e uma guia de grupo usando Node.js e o Gerador Yeoman para Microsoft Teams

>[!NOTE]
>Esse início rápido segue as etapas descritas no [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório do Microsoft OfficeDev GitHub.

Neste início rápido, vamos passo a passo criando um canal personalizado e uma guia de grupo usando o gerador [yeoman Teams .](https://github.com/OfficeDev/generator-teams/)

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Você deseja criar uma guia configurável ou estática?**

Use as teclas de seta para selecionar a guia configurável.

**Quais escopos você pretende usar para sua Guia?**

Você pode selecionar uma equipe e/ou um chat em grupo

**Deseja que essa guia seja disponibilizada no SharePoint Online? (Y/n)** 

Selecione **n**.

>[!IMPORTANT]
>O componente de **caminho que seuDefaultTabNameTab**, referenciado neste início rápido, é o valor que você inscrevia no gerador para **Nome** da Guia Padrão mais a **palavra Tab**.
>
>Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

No diretório do projeto, navegue até o seguinte:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

É aí que você encontrará sua lógica de tabulação. Localize `render()` o método e adicione a seguinte marca e conteúdo à parte superior do código do `<div>` `<PanelBody>` contêiner:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Certifique-se de salvar o arquivo atualizado.

## <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Para exibir sua página de configuração de tabulação, vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Você verá o seguinte:

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS. Teams não permite a hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.

Para testar sua extensão de tabulação, você usará [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo. O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente. Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual no computador local. Quando o computador é desligado ou vai para o sono, o serviço não estará mais disponível.

No prompt de comando, saia do localhost e insira o seguinte:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for carregada para as equipes da Microsoft e salva com êxito, você poderá exibi-la na galeria de guias, adicioná-la à barra de guias e interagir com ela até que sua sessão de túnel de ngrok termine. Se você reiniciar sua sessão de ngrok, precisará atualizar seu aplicativo com a nova URL.

## <a name="upload-your-application-to-teams"></a>Upload seu aplicativo para Teams

- Abra o Microsoft Teams cliente. Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)
- No painel *YourTeams* à esquerda, selecione o menu ao lado da equipe que você está usando para testar sua guia e `...` escolha Gerenciar **equipe**.
- No painel principal, selecione **Aplicativos** **na** barra de guias e escolha Upload um aplicativo personalizado localizado no canto inferior direito da página.
- Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip do pacote do aplicativo e escolha **Abrir**. Sua guia será carregada no Teams.
- Retorne à sua equipe, escolha o canal onde você gostaria de exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.
- Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para sua guia canal/grupo.
- Selecione **Salvar** e sua guia será adicionada à barra de guias do canal.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um Canal Personalizado e Uma Guia de Grupo com ASP.NETCore](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)
