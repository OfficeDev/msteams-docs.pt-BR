---
title: Adicionar recursos aos aplicativos de Teams de usuário
author: MuyangAmigo
description: Descreve Adicionar Recursos de Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: dcaa4475db62be2cebbbe2b1b74e0bbbd7fb5398
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227674"
---
# <a name="add-cloud-resources-to-your-teams-app"></a>Adicionar recursos de nuvem ao seu Teams app

O TeamsFx ajuda a provisionar recursos de nuvem para sua hospedagem de aplicativos. Você também pode, opcionalmente, adicionar recursos de nuvem que se ajustem às suas necessidades de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Você já deve ter um projeto Teams aplicativo.

## <a name="add-cloud-resources-using-teams-toolkit"></a>Adicionar recursos de nuvem usando Teams Toolkit

> [!IMPORTANT]
> Você precisa provisionar cada ambiente depois de adicionar um recurso.

1. Abra **Visual Studio Code**.
1. Selecione **Teams Toolkit** no painel esquerdo:

    ![Ativar Teams Toolkit](./images/activate-teams-toolkit.png)

1. No painel Teams Toolkit barra lateral, selecione **Adicionar recursos de nuvem**:

    ![Adicionar recursos de nuvem](./images/add-cloud-resources.png)

    Você também pode abrir a paleta de comandos e inserir **Teams: Adicionar recursos de nuvem**:
    
    > [!NOTE]
    > Siga o mesmo processo que é disparado a partir do Modo de Exibição de Árvore:

    ![Recursos alternativos de nuvem](./images/alternate-cloud-resources.png)

1. No pop-up, selecione todos os recursos de nuvem que você deseja adicionar ao seu projeto Teams aplicativo:

     ![Selecionar recursos de nuvem](./images/select-cloud-resources.png)

1. Selecione **OK**.

## <a name="add-cloud-resources-using-teamsfx-cli-in-command-window"></a>Adicionar recursos de nuvem usando a CLI do TeamsFx na Janela de Comando

1. Altere o diretório para o **diretório do projeto.**
1. Execute o comando para adicionar recursos diferentes.

A tabela a seguir descreve os recursos de nuvem e os comandos correspondentes para adicioná-los:

|Recursos de nuvem|Comando|
|---------------|----------|
| Função do Azure|`teamsfx resource add azure-function --function-name your-func-name`|
| Banco de dados SQL Azure|`teamsfx resource add --function-name your-func-name`|
| Gerenciamento de API do Azure|`teamsfx resource add azure-apim`|

## <a name="what-cloud-resources-can-be-added"></a>Quais recursos de nuvem podem ser adicionados

O TeamsFx fornece integrações perfeitas com os serviços do Azure que são comuns para os seguintes cenários de aplicativo:

- [Funções do Azure](/azure/azure-functions/functions-overview): uma solução sem servidor para atender aos seus requisitos sob demanda, como a criação de APIs da Web para seu back-end de aplicativos Teams aplicativos.
- Banco de dados do [Azure SQL](/azure/azure-sql/database/sql-database-paas-overview): uma plataforma totalmente gerenciada como um mecanismo de banco de dados de serviço (PaaS) para servir como seu armazenamento de dados Teams aplicativos.
- Gerenciamento de API do [Azure](/azure/azure-sql/database/sql-database-paas-overview): um gateway de API que pode ser usado para administrar APIs criadas para aplicativos Teams e publicá-las para consumir em outros aplicativos, como Power Apps.

## <a name="what-happens-when-you-add-resources"></a>O que acontece quando você adiciona recursos

As seguintes alterações ocorrerão ao seu projeto quando você adicionar recursos:

- Novos parâmetros podem ser adicionados ao azure.parameter. {env}.json para fornecer informações necessárias para provisionamento.
- O novo conteúdo é acrescentado ao ARM em pasta (exceto arquivos na pasta) para criar os `templates/azure` `templates/azure/teamsfx` recursos adicionados do Azure.
- Os arquivos em pasta são regenerados para garantir que a configuração necessária do TeamsFx está atualizada `templates/azure/teamsfx` para os recursos adicionados do Azure.
- `.fx/projectSettings.json` é atualizado para rastrear os recursos presentes em seu projeto.

Enquanto isso, há algumas alterações adicionais para cada tipo de recurso:

|Recursos adicionados|O que mudou|Por que essas alterações são feitas|
|---------------|---------------|-----------------------------|
|Azure Functions|Um código de modelo de funções do Azure é adicionado a uma subpasta com caminho `yourProjectFolder/api`</br></br>`launch.json` e `task.json` atualizado em `.vscode` pasta.| Inclua um modelo de gatilho http hello world em seu projeto.</br></br> Para incluir scripts necessários para Visual Studio Code executados quando você deseja depurar seu aplicativo localmente.|
|Gerenciamento de API do Azure|Um arquivo de Especificação da API Aberta adicionado a uma subpasta com caminho `yourProjectFolder/openapi`|Este é o arquivo de especificação da API que define sua API após a publicação.|

## <a name="limitations"></a>Limitações

- Você só pode adicionar um Aplicativo de Função /Banco de Dados SQL do Azure / Serviço DE APIM ao seu projeto.
- Não é possível adicionar recursos se seu projeto não contém o aplicativo de guia.

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Provisione recursos de nuvem](provision.md)
