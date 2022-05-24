---
title: Adicionar recursos a Teams aplicativos
author: MuyangAmigo
description: Descreve Adicionar Recursos do Kit de ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 27e46454658bdc95e5baf5e7453fd50b1b92f03f
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654809"
---
# <a name="add-cloud-resources-to-teams-app"></a>Adicionar recursos de nuvem ao aplicativo Teams

O TeamsFx ajuda a provisionar os recursos de nuvem para sua hospedagem de aplicativo. Você pode adicionar os recursos de nuvem opcionalmente, que se ajustam às suas necessidades de desenvolvimento.

## <a name="advantages"></a>Vantagens

A lista a seguir oferece vantagens para adicionar mais recursos de nuvem no TeamsFx:

* Fornece conveniência
* Gera automaticamente todos os arquivos de configuração e conecta-se Teams aplicativo usando Teams Toolkit

## <a name="limitation"></a>Limitação

Se você criou um SPFx guia baseado, não poderá adicionar recursos de nuvem do Azure.

## <a name="add-cloud-resources"></a>Adicionar recursos da nuvem

**Você pode adicionar recursos de nuvem pelos seguintes métodos:**

* Para adicionar recursos de nuvem usando Teams Toolkit no Visual Studio Code
* Para adicionar recursos de nuvem usando a paleta de comandos

  > [!NOTE]
  > Você precisa provisionar para cada ambiente, depois de ter adicionado com êxito o recurso em seu Teams aplicativo.
  
* **Para adicionar recursos de nuvem usando Teams Toolkit no Visual Studio Code:**

   1. Abra o **Visual Studio Code**.
   1. Selecione **Teams Toolkit** painel esquerdo.
   1. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/select-feature-updated.png" alt-text="adicionar recurso" border="true":::

* **Para adicionar recursos de nuvem usando a paleta de comandos:**

   1. Abra **a paleta de comandos**.
   1. Insira **Teams:Adicionar recursos**.
   1. Pressione **Enter**.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features.png" alt-text="Nuvem" border="true":::

   1. No pop-up, selecione os recursos de nuvem a serem adicionados ao seu projeto.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/updated-final-cloud.png" alt-text="final" border="true":::

## <a name="add-cloud-resources-using-teamsfx-cli"></a>Adicionar recursos de nuvem usando a CLI do TeamsFx

* Altere o diretório para seu **diretório de projeto**.
* A tabela a seguir lista os recursos e os comandos necessários:

  |Recurso de Nuvem|Comando|
  |---------------|----------|
  | Função do Azure|`teamsfx add azure-function`|
  | Banco de dados SQL do Azure|`teamsfx add azure-sql`|
  | Gerenciamento de API do Azure|`teamsfx resource add azure-apim`|
  | Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Tipos de recursos de nuvem

Nos cenários a seguir, o TeamsFx integra-se aos serviços do Azure:

- [Funções do Azure](/azure/azure-functions/functions-overview): uma solução sem servidor para atender aos seus requisitos sob demanda, como a criação de APIs da Web para o back-end de aplicativos do Teams.
- [Banco de dados SQL do Azure](/azure/azure-sql/database/sql-database-paas-overview): um mecanismo de banco de dados de plataforma como serviço (PaaS) para servir como seu armazenamento de dados de aplicativos do Teams.
- Gerenciamento de [API do Azure](deploy.md): um gateway de API pode ser usado para administrar APIs criadas para aplicativos Teams e publicá-los para consumir em outros aplicativos, como o Power Apps.
- [Azure Key Vault](/azure/key-vault/general/overview): proteja chaves criptográficas e outros segredos usados ​​por aplicativos e serviços de nuvem.

## <a name="add-cloud-resources"></a>Adicionar recursos de Nuvem

As seguintes alterações aparecem após a adição de recursos em seu projeto:

- Novos parâmetros adicionados a azure.parameter. {env}.json para fornecer as informações necessárias para provisionamento.
- O novo conteúdo é incluído no modelo do ARM `templates/azure`, exceto que os arquivos estão na `templates/azure/teamsfx` pasta para adicionar os recursos do Azure.
- Os arquivos na pasta `templates/azure/teamsfx` são regenerados para garantir que a configuração necessária do TeamsFx esteja atualizada para recursos do Azure adicionados.
- `.fx/projectSettings.json` é atualizado para acompanhar os recursos disponíveis em seu projeto.

As seguintes alterações adicionais aparecem após a adição de recursos em seu projeto:

|Recursos|Altera|Descrição|
|---------------|---------------|-----------------------------|
|Funções do Azure|Um código de modelo de funções do Azure é adicionado a uma subpasta com caminho `yourProjectFolder/api`</br></br>`launch.json` e `task.json` atualizados na pasta `.visual studio code`.| Inclui um modelo de gatilho http hello world em seu projeto.</br></br> Inclui os scripts necessários para que o Visual Studio Code seja executado quando você deseja depurar seu aplicativo localmente.|
|Gerenciamento de API do Azure|Um arquivo de especificação de API aberto adicionado a uma subpasta com caminho `yourProjectFolder/openapi`|Define sua API após a publicação. É o arquivo de especificação da API.|

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar um novo aplicativo do Teams](create-new-project.md)
* [Adicionar recursos a Teams aplicativos](add-capability.md)
* [Implantar na nuvem](deploy.md)