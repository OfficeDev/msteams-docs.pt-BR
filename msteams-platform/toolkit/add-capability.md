---
title: Adicionar recursos aos seus aplicativos Teams aplicativos
author: MuyangAmigo
description: Descreve a adição de recursos do Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9d2e3d559bd9d561e3afae8b0db9544ab2ad86cc
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073528"
---
# <a name="add-capabilities-to-your-teams-apps"></a>Adicionar recursos aos aplicativos do Teams

Durante o desenvolvimento de aplicativos, você pode criar um novo Teams com Teams de aplicativo. A tabela a seguir lista as Teams do aplicativo:

|**Recursos**|**Descrição**|
|--------|-------------|
| Guias |  As guias são marcas HTML simples que apontam para domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual|
| Bots |  Os bots ajudam a interagir com o serviço Web por meio de texto, cartões interativos e módulos de tarefa|
| Extensões de mensagens | As extensões de mensagens ajudam a interagir com seu serviço Web por meio de botões e formulários no Microsoft Teams cliente|

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto no VS Code.

## <a name="limitations"></a>Limitações

As limitações do TeamsFx ao adicionar mais recursos são as seguintes:

* Você pode adicionar guias até 16 instâncias
* Você pode adicionar o bot e a extensão de mensagens para uma instância cada
## <a name="add-capabilities"></a>Adicionar recursos

> [!Note]
> Você precisa executar o provisionamento para cada ambiente, depois de adicionar recursos com êxito ao Teams aplicativo.
* Você pode adicionar recursos usando Teams Toolkit no Visual Studio Code
    1. Abrir **Microsoft Visual Studio código**
    1. Selecione **Teams Toolkit** no painel esquerdo
    1. Selecionar **Adicionar funcionalidades**

        :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add capabilities.png" alt-text="capabilities":::

*   Você também pode abrir a paleta de comandos e inserir Teams: Adicionar Recursos:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/tree view capabilities.png" alt-text="Recursos alternativos":::


    1. No pop-up, selecione os recursos a serem incluídos em seu projeto:

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select capabilities.png" alt-text="select":::

    2. Selecionar **OK**

Os recursos selecionados são adicionados com êxito ao seu projeto. O Teams Toolkit gerar código-fonte para recursos recém-adicionados

## <a name="add-capabilities-using-teamsfx-cli-in-command-window"></a>Adicionar recursos usando a CLI do TeamsFx na janela comando

1. Alterar o diretório para o diretório **do projeto**
1. Execute o seguinte comando para adicionar recursos diferentes ao seu projeto:

   |Funcionalidade e cenário| Comando|
   |-----------------------|----------|
   |Para adicionar guia|`teamsfx capability add tab`|
   |Para adicionar bot|`teamsfx capability add bot`|
   |Para adicionar a extensão de mensagens|`teamsfx capability add messaging-extension`|

## <a name="supported-capabilities"></a>Recursos compatíveis

Além dos recursos que seu Teams aplicativo já tem, você pode optar por adicionar diferentes recursos ao seu Teams aplicativo. A tabela a seguir fornece as diferentes funcionalidades Teams aplicativo:

|Funcionalidades existentes|Outros recursos com suporte|
|--------------------|--------------------|
|Guias com SPFx|Nenhum|
|Guias com o Azure|Extensão de bot e mensagens|
|Bot|Guias|
|Extensão de mensagem|Guias e bot|
|Guias e bot|Guias e extensão de mensagem|
|Guias e extensão de mensagens|Guias e bot|
|Guias, bot e extensão de mensagens|Guias|
|Guias |Extensão de bot e mensagem|

## <a name="add-bot-tab-and-messaging-extension"></a>Adicionar extensão de bot, guia e mensagens

Depois de adicionar um bot e uma extensão de mensagens, as alterações em seu projeto são as seguintes:

* Um código de modelo de bot é adicionado a uma subpasta com caminho `yourProjectFolder/bot`. Isso inclui um modelo **de aplicativo de bot hello world** em seu projeto
* `launch.json`e `task.json` na `.vscode` pasta são atualizados, o que inclui os scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente
* `manifest.template.json`O arquivo `templates/appPackage`  em pasta é atualizado, o que inclui as informações relacionadas ao bot no arquivo de manifesto que representa seu aplicativo na Teams Platform. As alterações são:
  * A ID do bot
  * Os escopos do bot
  * Os comandos aos quais o aplicativo de bot Olá, Mundo pode responder
* Os arquivos abaixo `templates/azure/teamsfx` são atualizados e os `templates/azure/provision/xxx`arquivos .bicep são regenerados
* Os arquivos sob são `.fx/config` regenerados, o que garante que seu projeto seja definido com as configurações corretas para a funcionalidade recém-adicionada

Depois de adicionar a guia, as alterações em seu projeto são as seguintes:

* Um código de modelo de guia de front-end é adicionado a uma subpasta `yourProjectFolder/tab`com caminho, que inclui um modelo de aplicativo da guia **Olá,** Mundo em seu projeto
* `launch.json`e `task.json` na `.vscode` pasta são atualizados, o que inclui os scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente
* `manifest.template.json`O arquivo `templates/appPackage`  em pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Teams Platform. As alterações são:
  * As guias configuráveis e estáticas
  * Os escopos das guias
* Os arquivos sob `templates/azure/teamsfx` serão atualizados e o `templates/azure/provision/xxx`arquivo .bicep será regenerado
* O arquivo abaixo `.fx/config` é regenerado, o que garante que seu projeto seja definido com as configurações corretas para a funcionalidade recém-adicionada



## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar um novo Teams projeto](create-new-project.md)
