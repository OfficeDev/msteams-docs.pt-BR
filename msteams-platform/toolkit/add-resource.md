---
title: Adicionar Recursos aos Seus aplicativos do Teams
author: MuyangAmigo
description: Descreve Adicionar Recursos do Kit de ferramentas do Teams
ms.author: zhany
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d2377dae24c26679125d9d50b354b7e9f549be31
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111854"
---
# <a name="add-cloud-resources-to-your-teams-app"></a>Adicionar recursos de nuvem ao seu aplicativo Teams

O TeamsFx ajuda a provisionar recursos de nuvem para sua hospedagem de aplicativos. Você também pode adicionar opcionalmente recursos de nuvem que atendam às suas necessidades de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

[Instalar o Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Certifique-se de ter o projeto de aplicativo do Teams no Visual Studio Code.

## <a name="add-cloud-resources-using-teams-toolkit"></a>Adicionar recursos de nuvem usando o Kit de Ferramentas do Teams

> [!IMPORTANT]
> Você precisa provisionar cada ambiente depois de adicionar um recurso.

1. Abra o **Microsoft Visual Studio Code**.
1. Selecione **Kit de ferramentas do Teams** no painel esquerdo.
1. No painel da barra lateral do Kit de Ferramentas do Teams, selecione **Adicionar recursos de nuvem**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add cloudresources.png" alt-text="Adicionar recursos":::

   Você também pode abrir a paleta de comandos e digitar **Equipes: adicionar recursos de nuvem**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addcloud.png" alt-text="adicionar recursos de nuvem":::

1. No pop-up, selecione os recursos de nuvem que você deseja adicionar ao seu projeto de aplicativo do Teams:

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addresources.png" alt-text="adicionar":::

1. Selecione **OK**.

Os recursos selecionados são adicionados com sucesso ao seu projeto.

## <a name="add-cloud-resources-using-teamsfx-cli-in-command-window"></a>Adicione recursos de nuvem usando TeamsFx CLI na janela de comando

1. Altere o diretório para seu **diretório de projeto**.
1. Execute o seguinte comando para adicionar diferentes recursos ao seu projeto:

|Recurso de Nuvem|Comando|
|---------------|----------|
| Função do Azure|`teamsfx resource add azure-function --function-name your-func-name`|
| Banco de dados SQL do Azure|`teamsfx resource add --function-name your-func-name`|
| Gerenciamento de API do Azure|`teamsfx resource add azure-apim`|
| Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Tipos de recursos de nuvem

O TeamsFx se integra aos serviços do Azure para os seguintes cenários:

- [Funções do Azure](/azure/azure-functions/functions-overview): uma solução sem servidor para atender aos seus requisitos sob demanda, como a criação de APIs da Web para o back-end de aplicativos do Teams.
- [Banco de dados SQL do Azure](/azure/azure-sql/database/sql-database-paas-overview): um mecanismo de banco de dados de plataforma como serviço (PaaS) para servir como seu armazenamento de dados de aplicativos do Teams.
- [Gerenciamento de API do Azure](/azure/azure-sql/database/sql-database-paas-overview): um gateway de API que pode ser usado para administrar APIs criadas para aplicativos do Teams e publicá-las para consumo em outros aplicativos, como Power apps.
- [Azure Key Vault](/azure/key-vault/general/overview): proteja chaves criptográficas e outros segredos usados ​​por aplicativos e serviços de nuvem.

## <a name="add-cloud-resources"></a>Adicionar recursos de Nuvem

Após adicionar qualquer recurso, as alterações em seu projeto são as seguintes:

- Novos parâmetros podem ser adicionados a azure.parameter.{env}.json para fornecer as informações necessárias para provisionamento.
- Novo conteúdo é anexado ao modelo ARM na pasta `templates/azure`, exceto os arquivos na pasta `templates/azure/teamsfx` para criar os recursos do Azure adicionados.
- Os arquivos na pasta `templates/azure/teamsfx` são regenerados para garantir que a configuração necessária do TeamsFx esteja atualizada para recursos do Azure adicionados.
- `.fx/projectSettings.json` é atualizado para rastrear os recursos presentes em seu projeto.

Após adicionar recursos, as alterações adicionais em seu projeto são as seguintes:

|Recursos|Altera|Descrição|
|---------------|---------------|-----------------------------|
|Funções do Azure|Um código de modelo de funções do Azure é adicionado a uma subpasta com caminho `yourProjectFolder/api`</br></br>`launch.json` e `task.json` atualizados na pasta `.visual studio code`.| Inclui um modelo de gatilho http hello world em seu projeto.</br></br> Inclui os scripts necessários para que o Visual Studio Code seja executado quando você deseja depurar seu aplicativo localmente.|
|Gerenciamento de API do Azure|Um arquivo de especificação de API aberto adicionado a uma subpasta com caminho `yourProjectFolder/openapi`|Define sua API após a publicação, é o arquivo de especificação da API.|

## <a name="limitation"></a>Limitação

Você não pode adicionar recursos se tiver criado um projeto de guia baseado em SPFx.

## <a name="see-also"></a>Confira também

[Provisionar recursos de nuvem](provision.md)
