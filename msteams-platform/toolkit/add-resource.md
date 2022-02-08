---
title: Adicionar recursos aos aplicativos de Teams de usuário
author: MuyangAmigo
description: Descreve Adicionar Recursos de Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---

# <a name="add-cloud-resources-to-your-teams-app"></a>Adicionar recursos de nuvem ao seu Teams app

O TeamsFx ajuda a provisionar recursos de nuvem para sua hospedagem de aplicativos. Você também pode, opcionalmente, adicionar recursos de nuvem que se ajustem às suas necessidades de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

[Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo no Visual Studio Code.

## <a name="add-cloud-resources-using-teams-toolkit"></a>Adicionar recursos de nuvem usando Teams Toolkit

> [!IMPORTANT]
> Você precisa provisionar cada ambiente depois de adicionar um recurso.

1. Abra **Microsoft Visual Studio Código**.
1. Selecione **Teams Toolkit** no painel esquerdo.
1. No painel Teams Toolkit barra lateral, selecione **Adicionar recursos de nuvem**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add cloudresources.png" alt-text="Adicionar recursos":::

   Você também pode abrir a paleta de comandos e inserir Teams **: Adicionar recursos de nuvem**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addcloud.png" alt-text="adicionar recursos de nuvem":::

1. No pop-up, selecione os recursos de nuvem que você deseja adicionar ao seu projeto Teams aplicativo:

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addresources.png" alt-text="add":::

1. Selecione **OK**.

Os recursos selecionados são adicionados com sucesso ao seu projeto.

## <a name="add-cloud-resources-using-teamsfx-cli-in-command-window"></a>Adicionar recursos de nuvem usando a CLI do TeamsFx na janela de comando

1. Altere o diretório para o **diretório do projeto**.
1. Execute o seguinte comando para adicionar recursos diferentes em seu projeto:

|Recurso cloud|Comando|
|---------------|----------|
| Função do Azure|`teamsfx resource add azure-function --function-name your-func-name`|
| Banco de dados SQL Azure|`teamsfx resource add --function-name your-func-name`|
| Gerenciamento de API do Azure|`teamsfx resource add azure-apim`|
| Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Tipos de recursos de nuvem

O TeamsFx se integra aos serviços do Azure para os seguintes cenários:

- [Funções do Azure](/azure/azure-functions/functions-overview): uma solução sem servidor para atender aos seus requisitos sob demanda, como a criação de APIs da Web para seu back-end de aplicativos Teams aplicativos.
- [Banco de dados do Azure SQL](/azure/azure-sql/database/sql-database-paas-overview): uma plataforma como um mecanismo de banco de dados de serviço (PaaS) para servir como seu armazenamento de dados Teams aplicativos.
- [Gerenciamento de API do Azure](/azure/azure-sql/database/sql-database-paas-overview): um gateway de API que pode ser usado para administrar APIs criadas para aplicativos Teams e publicá-las para consumir em outros aplicativos, como aplicativos do Power.
- [Azure Key Vault](/azure/key-vault/general/overview): Proteja chaves criptográficas e outros segredos usados por aplicativos e serviços na nuvem.

## <a name="add-cloud-resources"></a>Adicionar recursos de nuvem

Depois de adicionar qualquer recurso, as alterações em seu projeto são as seguinte:

- Novos parâmetros podem ser adicionados ao azure.parameter. {env}.json para fornecer informações necessárias para provisionamento.
- O novo conteúdo é acrescentado ao ARM em pasta `templates/azure` , exceto `templates/azure/teamsfx` os arquivos em pasta para criar os recursos adicionados do Azure.
- Os arquivos em `templates/azure/teamsfx` pasta são regenerados para garantir que a configuração necessária do TeamsFx está atualizada para os recursos adicionados do Azure.
- `.fx/projectSettings.json` é atualizado para rastrear os recursos presentes em seu projeto.

Depois de adicionar resouces, as alterações adicionais em seu projeto são as seguinte:

|Recursos|Altera|Descrição|
|---------------|---------------|-----------------------------|
|Funções do Azure|Um código de modelo de funções do Azure é adicionado a uma subpasta com caminho `yourProjectFolder/api`</br></br>`launch.json` e `task.json` atualizado em `.visual studio code` pasta.| Inclui um modelo de gatilho http hello world em seu projeto.</br></br> Inclui scripts necessários para Visual Studio Code serem executados quando você deseja depurar seu aplicativo localmente.|
|Gerenciamento de API do Azure|Um arquivo de especificação de API aberto adicionado a uma subpasta com caminho `yourProjectFolder/openapi`|Define sua API após a publicação, é o arquivo de especificação da API .|

## <a name="limitation"></a>Limitação

Você não poderá adicionar recursos se tiver criado um projeto de guia SPFx com base.

## <a name="see-also"></a>Confira também

[Provisionar recursos de nuvem](provision.md)
