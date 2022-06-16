---
title: Adicionar recursos aos seus aplicativos Teams aplicativos
author: MuyangAmigo
description: Descreve a adição de recursos do Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 18c1379a630e637bea95209c35b823306b35a5de
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123994"
---
# <a name="add-capabilities-to-teams-apps"></a>Adicionar recursos a Teams aplicativos

Adicionar funcionalidade no Teams Toolkit ajuda você a adicionar funcionalidade adicional ao seu aplicativo Teams existente. A tabela a seguir lista as Teams do aplicativo:

|**Recursos**|**Descrição**|
|--------|-------------|
| Guias |  As guias são marcas HTML simples que se referem a domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual.|
| Bots |  Os bots ajudam a interagir com seu serviço Web por meio de texto, cartões interativos e módulos de tarefa.|
| Extensões de mensagens | As extensões de mensagem ajudam a interagir com seu serviço Web por meio de botões e formulários no Microsoft Teams cliente.|

## <a name="advantages"></a>Vantagens

A lista a seguir oferece vantagens para adicionar mais recursos no TeamsFx:

* Fornece conveniência.
* Adiciona mais funções ao seu aplicativo adicionando automaticamente códigos-fonte usando Teams Toolkit.

## <a name="limitations"></a>Limitações

A lista a seguir fornece limitações para adicionar mais recursos no TeamsFx:

* Você pode adicionar guias até 16 instâncias.
* Você pode adicionar um bot e uma extensão de mensagem para uma instância cada.

## <a name="add-capabilities"></a>Adicionar recursos

**Você pode adicionar recursos pelos seguintes métodos:**

* Para adicionar recursos usando Teams Toolkit no Visual Studio Code.
* Para adicionar recursos usando a paleta de comandos.

  > [!Note]
  > Você precisa provisionar para cada ambiente, depois de adicionar com êxito os recursos em seu Teams aplicativo.

* **Para adicionar recursos usando Teams Toolkit no Visual Studio Code:**

   1. Abra o **Visual Studio Code**.
   1. Selecione **Teams Toolkit** painel esquerdo.
   1. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="um atualizado" border="true":::

* **Para adicionar recursos usando a paleta de comandos:**

   1. Abra **a paleta de comandos**.
   1. Insira **Teams:Adicionar recursos**.
   1. Pressione **Enter**.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/Teams-add-features.png" alt-text="recurso de equipe" border="true":::

   1. No pop-up, selecione a funcionalidade a ser adicionada ao seu projeto.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Notificação" border="true":::

## <a name="add-capabilities-using-teamsfx-cli"></a>Adicionar recursos usando a CLI do TeamsFx

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

## <a name="available-capabilities-to-add-for-different-teams-project"></a>Recursos disponíveis a serem adicionados para diferentes Teams projeto

Você pode optar por adicionar recursos diferentes com base no projeto criado no Teams aplicativo.
A tabela a seguir lista os recursos disponíveis a serem adicionados ao seu projeto:

|Funcionalidades existentes|Outros recursos com suporte|
|--------------------|--------------------|
|SPFx guia |Nenhuma|
|Guia habilitada para SSO |Guia habilitada para SSO, bot de notificação, bot de comando, bot, extensão de mensagem|
|Bot de notificação |Guia habilitada para SSO, guia|
|Bot de comando |Guia habilitada para SSO, guia|
|Tab |Guia, bot de notificação, bot de comando, bot, extensão de mensagem|
|Bot |Extensão de mensagem, guia habilitada para SSO, guia|
|Extensão de mensagem |Bot, guia habilitada para SSO, guia |

## <a name="add-bot-tab-and-message-extension"></a>Adicionar extensão de bot, guia e mensagem

Depois de adicionar um bot e uma extensão de mensagem, as alterações em seu projeto são as seguintes:

* Um código de modelo de bot é adicionado a uma subpasta com caminho `yourProjectFolder/bot`. Isso inclui um modelo **de aplicativo** de bot hello world em seu projeto.
* `launch.json`e `task.json` na `.vscode` pasta são atualizados, o que inclui os scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente.
* `manifest.template.json`O arquivo `templates/appPackage`  em pasta é atualizado, o que inclui as informações relacionadas ao bot no arquivo de manifesto que representa seu aplicativo na Teams Platform. As alterações são:
  * A ID do bot
  * Os escopos do bot
  * Os comandos aos quais o aplicativo de bot Olá, Mundo pode responder
* Os arquivos em `templates/azure/teamsfx` baixo são atualizados e os `templates/azure/provision/xxx`arquivos .bicep são regenerados.
* Os arquivos sob são `.fx/config` regenerados, o que garante que seu projeto seja definido com as configurações corretas para a funcionalidade recém-adicionada.

Depois de adicionar a guia, as alterações em seu projeto são as seguintes:

* Um código de modelo de guia de front-end é adicionado a uma subpasta `yourProjectFolder/tab`com caminho, que inclui um modelo de aplicativo da guia **Olá** , Mundo em seu projeto.
* `launch.json`e `task.json` na `.vscode` pasta são atualizados, o que inclui os scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente.
* `manifest.template.json`O arquivo `templates/appPackage`  em pasta é atualizado, o que inclui informações relacionadas à guia no arquivo de manifesto que representa seu aplicativo na Teams Platform. As alterações são:
  * As guias configuráveis e estáticas
  * Os escopos das guias
* Os arquivos abaixo `templates/azure/teamsfx` serão atualizados e o `templates/azure/provision/xxx`arquivo .bicep será regenerado.
* O arquivo em `.fx/config` baixo é regenerado, o que garante que seu projeto seja definido com as configurações corretas para a funcionalidade recém-adicionada.

## <a name="step-by-step-guide"></a>Guias passo a passo

* Siga o [guia passo a passo](../sbs-gs-commandbot.yml) para criar o bot de comando no Microsoft Teams

* Siga o [guia passo a passo](../sbs-gs-notificationbot.yml) para criar um bot de notificação no Microsoft Teams.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar um novo Teams projeto](create-new-project.md)
