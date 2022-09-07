---
title: Adicionar recursos a aplicativos do Teams
author: MuyangAmigo
description: Neste módulo, saiba como adicionar recursos do Kit de Ferramentas do Teams, vantagens, limitações e funcionalidades
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: fc58610802a51af19efc32e579566fbf5e36feca
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616507"
---
# <a name="add-cloud-resources-to-microsoft-teams-app"></a>Adicionar recursos de nuvem ao aplicativo Microsoft Teams

O Kit de Ferramentas do Teams ajuda você a provisionar os recursos de nuvem para sua hospedagem de aplicativos. Você pode adicionar os recursos de nuvem opcionalmente, que se ajustam às suas necessidades de desenvolvimento. A vantagem de adicionar mais recursos de nuvem no TeamsFx é que você pode gerar automaticamente todos os arquivos de configuração e conectar-se ao aplicativo Teams usando o Kit de Ferramentas do Teams.

> [!NOTE]
> Se você tiver criado um projeto de guia baseado em SPFx, não poderá adicionar recursos de nuvem do Azure.

## <a name="add-cloud-resources"></a>Adicionar recursos da nuvem

Você pode adicionar recursos de nuvem pelos seguintes métodos:

### <a name="to-add-cloud-resources-by-using-teams-toolkit-in-visual-studio-code"></a>Para adicionar recursos de nuvem usando o Kit de Ferramentas do Teams no Visual Studio Code

   1. Abra o **Visual Studio Code**.
   1. Selecione **o Kit de Ferramentas do Teams** na barra de atividades.
   1. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/select-feature-updated.png" alt-text="Adicionar recurso do Kit de Ferramentas do Teams":::

### <a name="to-add-cloud-resources-by-using-command-palette"></a>Para adicionar recursos de nuvem usando a paleta de comandos

   1. Selecione **Exibir** > **Paleta de Comandos...** ou **Ctrl+Shift+P**.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features.png" alt-text="Adicionar recurso da paleta de comandos":::

   1. Insira **o Teams: adicionar recursos**.
   1. Pressione **Enter**.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features1.png" alt-text="Digite adicionar recurso e insira":::

   1. No pop-up, selecione os recursos **de nuvem** a serem adicionados ao seu projeto.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/updated-final-cloud.png" alt-text="final":::

  > [!NOTE]
  > Você precisa provisionar para cada ambiente, depois de ter adicionado com êxito o recurso em seu aplicativo do Teams.

### <a name="add-cloud-resources-using-teamsfx-cli"></a>Adicionar recursos de nuvem usando a CLI do TeamsFx

* Altere o diretório para seu **diretório de projeto**.
* A tabela a seguir lista os recursos e os comandos necessários:

  |Recurso de Nuvem|Comando|
  |---------------|----------|
  | Função do Azure|`teamsfx add azure-function`|
  | Banco de dados SQL do Azure|`teamsfx add azure-sql`|
  | Gerenciamento de API do Azure|`teamsfx add azure-apim`|
  | Azure Key Vault|`teamsfx add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Tipos de recursos de nuvem

Nos cenários a seguir, o TeamsFx integra-se aos serviços do Azure:

* [Funções do Azure](/azure/azure-functions/functions-overview): uma solução sem servidor para atender aos seus requisitos sob demanda, como a criação de APIs da Web para o back-end de aplicativos do Teams.
* [Banco de dados SQL do Azure](/azure/azure-sql/database/sql-database-paas-overview): um mecanismo de banco de dados de plataforma como serviço (PaaS) para servir como seu armazenamento de dados de aplicativos do Teams.
* Gerenciamento [de API do Azure](deploy.md): um gateway de API pode ser usado para administrar APIs criadas para aplicativos do Teams e publicá-las para consumir em outros aplicativos, como o Power Apps.
* [Azure Key Vault](/azure/key-vault/general/overview): proteja chaves criptográficas e outros segredos usados ​​por aplicativos e serviços de nuvem.

## <a name="changes-after-adding-cloud-resources"></a>Alterações após a adição de recursos de nuvem

As seguintes alterações aparecem após a adição de recursos em seu projeto:

* Novos parâmetros adicionados a azure.parameter. {env}.json para fornecer as informações necessárias para provisionamento.
* O novo conteúdo é incluído no modelo do ARM `templates/azure`, exceto que os arquivos estão na `templates/azure/teamsfx` pasta para adicionar os recursos do Azure.
* Os arquivos na pasta `templates/azure/teamsfx` são regenerados para garantir que a configuração necessária do TeamsFx esteja atualizada para recursos do Azure adicionados.
* `.fx/projectSettings.json` é atualizado para acompanhar os recursos disponíveis em seu projeto.

As seguintes alterações adicionais aparecem após a adição de recursos em seu projeto:

|Recursos|Altera|Descrição|
|---------------|---------------|-----------------------------|
|Funções do Azure|Um código de modelo de funções do Azure é adicionado a uma subpasta com caminho `yourProjectFolder/api`</br></br>`launch.json` e `task.json` atualizados na pasta `.visual studio code`.| Inclui um modelo de gatilho http hello world em seu projeto.</br></br> Inclui os scripts necessários para que o Visual Studio Code seja executado quando você deseja depurar seu aplicativo localmente.|
|Gerenciamento de API do Azure|Um arquivo de especificação de API aberto adicionado a uma subpasta com caminho `yourProjectFolder/openapi`|Define sua API após a publicação. É o arquivo de especificação da API.|

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Criar um novo aplicativo do Teams](create-new-project.md)
* [Adicionar recursos a aplicativos do Teams](add-capability.md)
* [Implantar na nuvem](deploy.md)
