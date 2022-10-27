---
title: Adicionar recursos aos aplicativos do Teams
author: surbhigupta
description: Neste módulo, saiba como adicionar recursos do Teams Toolkit
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: abcda0dd19388d1cdce2f2b440ecbae833b5f9c3
ms.sourcegitcommit: 6926cf5eee55d5047c11ca13afc7f6f23e270396
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68740601"
---
# <a name="add-capabilities-to-teams-apps"></a>Adicionar recursos aos aplicativos do Teams

Adicionar recursos com o Teams Toolkit ajuda você a incluir recursos adicionais ao aplicativo Microsoft Teams existente. A vantagem de adicionar mais recursos é que você pode adicionar mais funções ao seu aplicativo adicionando automaticamente códigos-fonte usando o Teams Toolkit. Você também pode escolher diferentes funcionalidades com base no projeto que você criou em seu aplicativo do Teams. A tabela a seguir lista os recursos do aplicativo Teams:

|Funcionalidade|Descrição|Outros recursos com suporte|
|--------|-------------|-----------------|
|**Aplicativo Básico do Teams**|              |
| Tab |  As guias são marcas HTML simples que se referem a domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual.|Tab, bot de notificação, bot de comando, bot, extensão de mensagem|
|Guia SPFx| Os aplicativos de guia SPFx são hospedados no Microsoft 365 e dão suporte ao desenvolvimento e hospedagem da solução SPFx do lado do cliente|Nenhum|
|Guia habilitada para SSO|Você pode criar um aplicativo de guia habilitado para SSO que permite que o usuário com um único recurso de logon|Guia habilitada para SSO, bot de notificação, bot de comando, bot, extensão de mensagem|
| Bot |  Os bots ajudam a interagir com seu serviço Web por meio de texto, cartões interativos e módulos de tarefa.|Extensão de mensagem, guia habilitada para SSO, guia|
| Extensão de mensagem | As extensões de mensagem ajudam a interagir com seu serviço Web por meio de botões e formulários no cliente do Microsoft Teams.|Guia Bot, habilitado para SSO|
|**Aplicativo teams baseado em cenário**|             |
| Bot de notificação | O bot de notificação envia mensagens proativamente no canal do Teams ou chat em grupo ou chat pessoal. Você pode disparar o bot de notificação com uma solicitação HTTP, como cartões ou textos. |Guia, guia habilitada para SSO|
| Bot de comando | O bot de comando permite automatizar tarefas repetitivas usando um bot de comando. Ele responde a comandos simples enviados em chats com cartões adaptáveis. |Guia, guia habilitada para SSO|
| Bot de fluxo de trabalho| O bot de fluxo de trabalho permite que os usuários interajam com um Cartão Adaptável habilitado pelo recurso manipulador de ação Cartão Adaptável no aplicativo bot de fluxo de trabalho.|Guia, guia habilitada para SSO|

> [!NOTE]
> Você pode adicionar guias até 16 instâncias. Quanto ao bot e à extensão de mensagem, você pode adicionar uma para cada instância de cada vez.

## <a name="add-capabilities"></a>Adicionar recursos

Você pode adicionar recursos pelos seguintes métodos:

* [Usando o Teams Toolkit no Microsoft Visual Studio Code](#using-teams-toolkit-in-microsoft-visual-studio-code)
* [Usando a Paleta de Comandos](#using-the-command-palette)
* [Usando a CLI do TeamsFx](#using-teamsfx-cli)

### <a name="using-teams-toolkit-in-microsoft-visual-studio-code"></a>Usando o Teams Toolkit no Microsoft Visual Studio Code

   1. Abra o **Visual Studio Code**.
   1. Selecione **Kit de Ferramentas do Teams** na barra de atividades.
   1. Selecione **Adicionar recursos** em **DESENVOLVIMENTO**.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="Adicionar recursos do Teams Toolkit":::

      > [!NOTE]
      > Depois de adicionar com êxito os recursos em seu aplicativo teams, você precisa provisionar para cada ambiente.

### <a name="using-the-command-palette"></a>Usando a Paleta de Comandos

   1. Selecione **Exibir** > **Paleta de Comandos...** ou **Ctrl+Shift+P**.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add-capabilities-command-palette.png" alt-text="Adicionar recursos do paladar de comando":::

   1. **Insira Teams: adicionar recursos**.
   1. Pressione enter.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/teams-add-features.png" alt-text="Para adicionar recursos usando a paleta de comandos.":::

   1. No pop-up, selecione a funcionalidade necessária para adicionar em seu projeto.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Notificação":::

### <a name="using-teamsfx-cli"></a>Usando a CLI do TeamsFx

* Altere o diretório para seu **diretório de projeto**.
* A tabela a seguir lista os recursos e os comandos necessários:

  |Funcionalidade e cenário| Comando|
  |-----------------------|----------|
  |Para adicionar bot de notificação |`teamsfx add notification`|
  |Para adicionar bot de comando |`teamsfx add command-and-response`|
  |Para adicionar a guia habilitada para SSO |`teamsfx add sso-tab`|
  |Para adicionar guia |`teamsfx add tab`|
  |Para adicionar bot |`teamsfx add bot`|
  |Para adicionar extensão de mensagem |`teamsfx add message extension`|

## <a name="changes-after-adding-capabilities"></a>Alterações após adicionar recursos

A tabela a seguir mostra as alterações que podem ser vistas nos arquivos do aplicativo ao adicionar os recursos:

|Adicionar funcionalidade|Descrição| Altera|
|------------|------------------------|---------|
|Bot, extensão de mensagem e guia|Inclui um modelo de aplicativo **hello world**&nbsp;bot ou tab em seu projeto.|Um código de modelo de front-end ou de guia é adicionado a uma subpasta com o caminho `yourProjectFolder/bot` ou `yourProjectFolder/tab` , respectivamente, .|
| Bot, extensão de mensagem e guia |Inclui scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente. |Os arquivos `launch.json` e `task.json` em `.vscode` pasta são atualizados.|
| Extensão de bot e mensagem|Inclui informações relacionadas a bots ou guias no arquivo de manifesto que representa seu aplicativo na Plataforma do Teams.|O arquivo`manifest.template.json` em `templates/appPackage` pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Plataforma do Teams. As alterações estão visíveis na ID do bot, nos escopos do bot e nos comandos aos quais o bot ou aplicativo de guia hello world pode responder.|
|Tab|Inclui informações relacionadas a bots ou guias no arquivo de manifesto que representa seu aplicativo na Plataforma do Teams.|O arquivo `manifest.template.json` em `templates/appPackage` pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Plataforma do Teams. As alterações são visíveis em guias configuráveis e estáticas e nos escopos das guias.|
|Bot, extensão de mensagem e guia|Inclui informações relacionadas a&nbsp;bot ou tab nos arquivos teamsfx e provisionamento que são para integrar funções do Azure.|Os arquivos em `templates/azure/teamsfx` são atualizados e `templates/azure/provision/xxx`os arquivos .bicep são regenerados.|
|Bot, extensão de mensagem e guia|Garante que seu projeto esteja definido com configurações corretas para a funcionalidade recém-adicionada.|Os arquivos em `.fx/config` são regenerados|

## <a name="step-by-step-guide"></a>Guias passo a passo

* Siga o guia [passo a passo](../sbs-gs-commandbot.yml) para criar um bot de comando no Microsoft Teams.

* Siga o guia [passo a passo](../sbs-gs-notificationbot.yml) para criar o bot de notificação no Microsoft Teams.

* Siga o guia [passo a passo](../sbs-gs-workflow-bot.yml) para criar um bot de fluxo de trabalho no Microsoft Teams.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar um projeto do Teams](create-new-project.md)
