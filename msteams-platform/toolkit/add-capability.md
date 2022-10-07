---
title: Adicionar recursos aos aplicativos do Teams
author: surbhigupta
description: Neste módulo, saiba como adicionar funcionalidades do Kit de Ferramentas do Teams
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 29ba0fff62678a18222f0229701546515b7d4c38
ms.sourcegitcommit: 637b8f93b103297b1ff9f1af181680fca6f4499d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2022
ms.locfileid: "68499185"
---
# <a name="add-capabilities-to-teams-apps"></a>Adicionar recursos a aplicativos do Teams

Adicionar recursos com o Kit de Ferramentas do Teams ajuda você a incluir recursos adicionais ao aplicativo Microsoft Teams existente. A vantagem de adicionar mais recursos é que você pode adicionar mais funções ao seu aplicativo adicionando automaticamente códigos-fonte usando o Kit de Ferramentas do Teams. Você também pode escolher diferentes recursos com base no projeto que você criou em seu aplicativo do Teams. A tabela a seguir lista os recursos do aplicativo Teams:

|Funcionalidade|Descrição|Outros recursos com suporte|
|--------|-------------|-----------------|
|**Aplicativo Básico do Teams**|              |
| Tab |  As guias são marcas HTML simples que se referem a domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual.|Guia, bot de notificação, bot de comando, bot, extensão de mensagem|
|Guia SPFx| Os aplicativos da guia SPFx são hospedados no Microsoft 365 e dão suporte ao desenvolvimento e hospedagem da solução SPFx do lado do cliente|Nenhum|
|Guia habilitada para SSO|Você pode criar um aplicativo guia habilitado para SSO que permite ao usuário o recurso de logon único|Guia habilitada para SSO, bot de notificação, bot de comando, bot, extensão de mensagem|
| Bot |  Os bots ajudam a interagir com seu serviço Web por meio de texto, cartões interativos e módulos de tarefa.|Extensão de mensagem, guia habilitada para SSO, guia|
| Extensão de mensagem | As extensões de mensagem ajudam a interagir com seu serviço Web por meio de botões e formulários no cliente do Microsoft Teams.|Bot, guia habilitada para SSO, guia|
|**Aplicativo Teams baseado em cenário**|             |
| Bot de notificação | O bot de notificação envia mensagens proativamente no canal do Teams, chat em grupo ou chat pessoal. Você pode disparar o bot de notificação com uma solicitação HTTP, como cartões ou textos. |Guia habilitada para SSO, guia|
| Bot de comando | O bot de comando permite automatizar tarefas repetitivas usando um bot de comando. Ele responde a comandos simples enviados em chats com cartões adaptáveis. |Guia habilitada para SSO, guia|

> [!NOTE]
> Você pode adicionar guias até 16 instâncias. Quanto ao seu bot e extensão de mensagem, você pode adicionar um para cada instância por vez.

## <a name="add-capabilities"></a>Adicionar recursos

Você pode adicionar recursos pelos seguintes métodos:

* [Usando o Kit de Ferramentas do Teams no Microsoft Visual Studio Code](#using-teams-toolkit-in-microsoft-visual-studio-code)
* [Usando a paleta de comandos](#using-the-command-palette)
* [Usando a CLI do TeamsFx](#using-teamsfx-cli)

### <a name="using-teams-toolkit-in-microsoft-visual-studio-code"></a>Usando o Kit de Ferramentas do Teams no Microsoft Visual Studio Code

   1. Abra o **Visual Studio Code**.
   1. Selecione **o Kit de Ferramentas do Teams** na barra de atividades.
   1. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="Adicionar recursos do Kit de Ferramentas do Teams":::

      > [!NOTE]
      > Depois de adicionar com êxito os recursos em seu aplicativo do Teams, você precisa provisionar para cada ambiente.

### <a name="using-the-command-palette"></a>Usando a paleta de comandos

   1. Selecione **Exibir** > **Paleta de Comandos...** ou **Ctrl+Shift+P**.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add-capabilities-command-palette.png" alt-text="Adicionar recursos do paladar de comando":::

   1. Insira **o Teams: adicionar recursos**.
   1. Pressione Enter.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/teams-add-features.png" alt-text="Para adicionar recursos usando a paleta de comandos.":::

   1. No pop-up, selecione a funcionalidade que você precisa adicionar ao seu projeto.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Notificação":::

### <a name="using-teamsfx-cli"></a>Usando a CLI do TeamsFx

* Altere o diretório para seu **diretório de projeto**.
* A tabela a seguir lista os recursos e os comandos necessários:

  |Funcionalidade e cenário| Comando|
  |-----------------------|----------|
  |Para adicionar o bot de notificação |`teamsfx add notification`|
  |Para adicionar o bot de comando |`teamsfx add command-and-response`|
  |Para adicionar a guia habilitada para SSO |`teamsfx add sso-tab`|
  |Para adicionar guia |`teamsfx add tab`|
  |Para adicionar bot |`teamsfx add bot`|
  |Para adicionar a extensão de mensagem |`teamsfx add message extension`|

## <a name="changes-after-adding-capabilities"></a>Alterações após a adição de recursos

A tabela a seguir mostra as alterações que podem ser vistas nos arquivos do aplicativo ao adicionar os recursos:

|Adicionar funcionalidade|Descrição| Altera|
|------------|------------------------|---------|
|Bot, extensão de mensagem e guia|Inclui um modelo **de aplicativo de** guia ou bot hello world &nbsp;em seu projeto.|Um bot de front-end ou código de modelo de guia é adicionado a uma subpasta com caminho `yourProjectFolder/bot` ou `yourProjectFolder/tab` respectivamente.|
| Bot, extensão de mensagem e guia |Inclui scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente. |Os arquivos `launch.json` e `task.json` a `.vscode` pasta são atualizados.|
| Extensão de bot e mensagem|Inclui informações relacionadas a bots ou guias no arquivo de manifesto que representa seu aplicativo na Plataforma teams.|O`manifest.template.json` arquivo `templates/appPackage` na pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Plataforma teams. As alterações são visíveis na ID do bot, nos escopos do bot e nos comandos aos quais o aplicativo hello world bot ou tab pode responder.|
|Tab|Inclui informações relacionadas a bots ou guias no arquivo de manifesto que representa seu aplicativo na Plataforma teams.|O `manifest.template.json` arquivo `templates/appPackage` na pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Plataforma teams. As alterações são visíveis em guias configuráveis e estáticas e escopos das guias.|
|Bot, extensão de mensagem e guia|Inclui informações relacionadas a bots&nbsp;ou guias no teamsfx e provisionar arquivos que são para a integração de funções do Azure.|Os arquivos em `templates/azure/teamsfx` baixo são atualizados e `templates/azure/provision/xxx`os arquivos .bicep são regenerados.|
|Bot, extensão de mensagem e guia|Garante que seu projeto esteja definido com as configurações corretas para a funcionalidade recém-adicionada.|Os arquivos sob `.fx/config` são regenerados|

## <a name="step-by-step-guide"></a>Guias passo a passo

* Siga o [guia passo a passo](../sbs-gs-commandbot.yml) para criar o bot de comando no Microsoft Teams

* Siga o [guia passo a passo](../sbs-gs-notificationbot.yml) para criar um bot de notificação no Microsoft Teams.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar novo projeto do Teams](create-new-project.md)
