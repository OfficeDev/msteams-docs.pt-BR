---
title: Adicionar recursos aos aplicativos Teams aplicativos
author: MuyangAmigo
description: Descreve adicionar recursos de Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---

# <a name="add-capabilities-to-your-teams-apps"></a>Adicionar recursos aos aplicativos Teams aplicativos

Você pode criar um novo Teams com um dos recursos Teams aplicativo. Durante o desenvolvimento de aplicativos, você pode Teams Toolkit adicionar mais recursos ao seu Teams app. A tabela a seguir lista os recursos Teams aplicativos:

|**Recursos**|**Descrição**|
|--------|-------------|
| Guias |  Guias são marcas HTML simples que apontam para domínios declarados no manifesto do aplicativo. Você pode adicionar guias como parte do canal dentro de uma equipe, chat em grupo ou aplicativo pessoal para um usuário individual.|
| Bots |  Os bots ajudam a interagir com seu serviço Web por meio de texto, cartões interativos e módulos de tarefa.|
| Extensões de mensagens | As extensões de mensagens ajudam a interagir com seu serviço Web por meio de botões e formulários no Microsoft Teams cliente.|

## <a name="prerequisite"></a>Pré-requisito

[Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto em código VS.

## <a name="add-capabilities-using-teams-toolkit"></a>Adicionar recursos usando Teams Toolkit

> [!IMPORTANT]
> Você precisa executar o provisionamento para cada ambiente depois de adicionar recursos com êxito ao seu Teams app.

1. Abra **Microsoft Visual Studio Código**.
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

1. Altere o diretório para o **diretório do projeto**.
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
|Guias com o Azure|Bot e extensão de mensagens|
|Bot|Guias|
|Extensão de mensagem|Guias e bot|
|Guias e bot|Guias e extensão de mensagem|
|Guias e extensão de mensagens|Guias e bot|
|Guias, bot e extensão de mensagens|Guias|
|Guias |Bot e extensão de mensagem|

## <a name="add-capabilities"></a>Adicionar recursos

Depois de adicionar bot e extensão de mensagens, as alterações em seu projeto são as seguinte:

- Um código de modelo de bot é adicionado a uma subpasta com caminho `yourProjectFolder/bot`. Isso inclui um modelo de aplicativo de bot hello **world** em seu projeto.
- `launch.json`e `task.json` em `.vscode` pasta são atualizados, o que inclui scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente. 
- `manifest.remote.template.json`e `manifest.local.template.json` o arquivo em `templates/appPackage` pasta são atualizados, o que inclui informações relacionadas ao bot no arquivo de manifesto que representa seu aplicativo na plataforma Teams. As alterações são:
  - A ID do seu bot.
  - Os escopos do bot.
  - Os comandos aos que o aplicativo de bot hello world pode responder.
- Os arquivos em `templates/azure/teamsfx` baixo serão atualizados e o `templates/azure/provision/xxx`arquivo .bicep será regenerado.
- Os arquivos em `.fx/config` baixo são regenerados, o que garante que seu projeto seja definido com configurações certas para a funcionalidade recém-adicionada.

Depois de adicionar a guia, as alterações em seu projeto são as seguinte:

- Um código de modelo de guia front-end é adicionado a uma subpasta `yourProjectFolder/tab`com caminho , que inclui um modelo de aplicativo de guia **hello world** em seu projeto.
- `launch.json`e `task.json` em `.vscode` pasta são atualizados, o que inclui scripts necessários para Visual Studio Code e é executado quando você deseja depurar seu aplicativo localmente. 
- `manifest.remote.template.json`e `manifest.local.template.json` o arquivo `templates/appPackage` em pasta são atualizados, o que inclui informações relacionadas a guias no arquivo de manifesto que representa seu aplicativo na plataforma Teams, as alterações são as seguinte:
  - As guias configuráveis e estáticas.
  - Os escopos das guias.
- Os arquivos em `templates/azure/teamsfx` baixo serão atualizados e o `templates/azure/provision/xxx`arquivo .bicep será regenerado.
- O arquivo em `.fx/config` baixo é regenerado, o que garante que seu projeto seja definido com configurações certas para a funcionalidade recém-adicionada.

## <a name="limitations"></a>Limitações

As limitações ao TeamsFx ao adicionar mais recursos são as seguinte:

* Você pode adicionar guias até 16 instâncias.
* Você pode adicionar bot e extensão de mensagens para uma instância cada.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar novo Teams projeto](create-new-project.md)
