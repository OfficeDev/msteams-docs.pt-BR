---
title: Adicionar recursos aos aplicativos Teams aplicativos
author: MuyangAmigo
description: Descreve adicionar recursos de Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 8aedcef132eee34a72f0f2f873bdae3a45529c7c
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768507"
---
# <a name="add-capabilities-to-your-teams-apps"></a>Adicionar recursos aos aplicativos Teams aplicativos

Você pode criar um novo Teams com um dos recursos Teams aplicativo. Durante o desenvolvimento de aplicativos, você pode Teams Toolkit adicionar mais recursos ao seu Teams app. A tabela a seguir lista os recursos Teams aplicativos:

|**Recursos**|**Descrição**|
|--------|-------------|
| Guias |  Guias são marcas HTML simples que apontam para domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual.|
| Bots |  Os bots ajudam a interagir com seu serviço Web por meio de texto, cartões interativos e módulos de tarefa.|
| Extensões de mensagens | As extensões de mensagens ajudam a interagir com seu serviço Web por meio de botões e formulários no Microsoft Teams cliente.|

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto em código VS.

## <a name="add-capabilities-using-teams-toolkit"></a>Adicionar recursos usando Teams Toolkit

> [!IMPORTANT]
> Você precisa executar o provisionamento para cada ambiente depois de adicionar recursos com êxito ao seu Teams app.

1. Abra **Visual Studio Code**.
1. Selecione **Teams Toolkit** no painel esquerdo.
1. Selecione **Adicionar recursos**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add capabilities.png" alt-text="capabilities":::

   Você também pode abrir a paleta de comandos e inserir **Teams: Adicionar Recursos**: 
      
    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/tree view capabilities.png" alt-text="Recursos alternativos":::

1. No pop-up, selecione os recursos a incluir em seu projeto:

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select capabilities.png" alt-text="select":::

1. Selecione **OK**.

Os recursos selecionados são adicionados com sucesso ao seu projeto. O Teams Toolkit gerar código-fonte para recursos recém-adicionados.

## <a name="add-capabilities-using-teamsfx-cli-in-command-window"></a>Adicionar recursos usando a CLI do TeamsFx na janela de comando

1. Altere o diretório para o **diretório do projeto.**
1. Execute o seguinte comando para adicionar diferentes recursos ao seu projeto:

   |Funcionalidade e Cenário| Comando|
   |-----------------------|----------|
   |Para adicionar guia|`teamsfx capability add tab`|
   |Para adicionar bot|`teamsfx capability add bot`|
   |Para adicionar extensão de mensagens|`teamsfx capability add messaging-extension`|

## <a name="supported-capabilities-matrix"></a>Matriz de recursos com suporte

Além dos recursos que seu Teams app já tem, você pode optar por adicionar diferentes recursos ao seu Teams app. A tabela a seguir fornece os diferentes recursos Teams aplicativos: 

|Recursos existentes|Outros recursos com suporte podem ser adicionados|
|--------------------|--------------------|
|Guias com SPFx|Nenhum|
|Guias com o Azure|Bots e extensões de mensagens|
|Bots|Guias|
|Extensões de mensagens|Guias|
|Guias e bots|Nenhum|
|Guias e extensões de mensagens|Nenhum|
|Guias, bots e extensões de mensagens|Nenhum|

## <a name="add-capabilities"></a>Adicionar recursos

Depois de adicionar bot e extensão de mensagens, as alterações em seu projeto são as seguinte:

- Um código de modelo de bot é adicionado a uma subpasta com caminho `yourProjectFolder/bot` . Isso inclui um modelo de aplicativo de bot hello **world** em seu projeto.
- `launch.json`e em pasta são atualizados, o que inclui scripts necessários para Visual Studio Code e é executado quando você deseja `task.json` `.vscode` depurar seu aplicativo localmente. 
- `manifest.remote.template.json`e o arquivo em pasta é atualizado, o que inclui informações relacionadas ao bot no arquivo de manifesto que representa seu aplicativo `manifest.local.template.json` `templates/appPackage` na plataforma Teams. As alterações são:
  - A ID do seu bot.
  - Os escopos do bot.
  - Os comandos aos que o aplicativo de bot hello world pode responder.
- Os arquivos em `templates/azure/teamsfx` baixo serão atualizados e o `templates/azure/provision/xxx` arquivo .bicep será regenerado.
- Os arquivos em baixo são regenerados, o que garante que seu projeto seja definido com configurações `.fx/config` certas para a funcionalidade recém-adicionada.

Depois de adicionar a guia, as alterações em seu projeto são as seguinte:

- Um código de modelo de guia front-end é adicionado a uma subpasta com caminho , que inclui um modelo de aplicativo de guia `yourProjectFolder/tab` **hello world** em seu projeto.
- `launch.json`e em pasta são atualizados, o que inclui scripts necessários para Visual Studio Code e é executado quando você deseja `task.json` `.vscode` depurar seu aplicativo localmente. 
- `manifest.remote.template.json`e o arquivo em pasta são atualizados, o que inclui informações relacionadas a guias no arquivo de manifesto que representa seu aplicativo na plataforma Teams, as alterações são as `manifest.local.template.json` `templates/appPackage` seguinte:
  - As guias configuráveis e estáticas.
  - Os escopos das guias.
- Os arquivos em `templates/azure/teamsfx` baixo serão atualizados e o `templates/azure/provision/xxx` arquivo .bicep será regenerado.
- O arquivo em baixo é regenerado, o que garante que seu projeto seja definido com configurações `.fx/config` certas para a funcionalidade recém-adicionada.

## <a name="limitations"></a>Limitações

As limitações com o TeamsFx ao adicionar mais recursos são as seguinte:

- Não é possível adicionar recursos de projeto para mais de uma instância.
- Não é possível adicionar recursos de bot se seu projeto contiver extensão de mensagens.
- Não é possível adicionar extensão de mensagens se seu projeto contiver um bot.

> [!NOTE]
> Se você quiser incluir recursos de bot e extensão de mensagens, selecione-os ao mesmo tempo. Você só pode adicioná-los quando criar um novo projeto ou um aplicativo de tabulação.

## <a name="see-also"></a>Confira também

* [Provisione recursos de nuvem](provision.md)
* [Criar novo Teams projeto](create-new-project.md)
