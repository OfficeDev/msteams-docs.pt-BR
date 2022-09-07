---
title: Fazer sideload e testar o aplicativo no ambiente do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como fazer sideload e testar o aplicativo em um ambiente diferente
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: ee1d3ee3a4f545a6c988c421fb18626a4a7276b7
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617052"
---
# <a name="sideload-and-test-app-in-teams-environment"></a>Fazer sideload e testar o aplicativo no ambiente do Teams

Depois de adicionar a conexão de API, você pode testar a conexão de API no ambiente local do Kit de Ferramentas do Teams e implantar seu aplicativo na nuvem. No pipeline de CI/CD, após a configuração com uma plataforma diferente, você precisa criar uma entidade de serviço do Azure para provisionar e implantar recursos.

Nesta seção, você aprenderá

* [Testar a conexão de API no ambiente local](#test-api-connection-in-local-environment)
* [Implantar seu aplicativo no Azure](#deploy-your-application-to-azure)
* [Provisionar e implantar recursos de CI/CD](#provision-and-deploy-cicd-resources)

## <a name="test-api-connection-in-local-environment"></a>Testar a conexão de API no ambiente local

As etapas a seguir ajudam a testar a conexão de API no ambiente local do Kit de Ferramentas do Teams:

 1. **Executar a instalação do npm**

    Execute `npm install` em ou `bot` pasta `api` para instalar pacotes adicionados.

 2. **Adicionar credenciais de API às configurações do aplicativo local**

    O Kit de Ferramentas do Teams não solicita credenciais, mas deixa espaços reservados no arquivo de configurações do aplicativo local. Substitua os espaços reservados com as credenciais apropriadas para acessar a API. O arquivo de configurações do aplicativo local é `.env.teamsfx.local` o arquivo na `bot` pasta `api` ou na pasta.

 3. **Usar o cliente de API para fazer solicitações de API**

    Importe o cliente de API do código-fonte que precisa de acesso à API:

    ```BASH
    import { yourApiClient } from '{relative path to the generated file}'
    ```

 4. **Gerar solicitações http(s) para a API de destino (com a Axios)**

    O cliente de API gerado é um cliente da API do Axios. Use o cliente Axios para fazer solicitações à API.

     > [!Note]
     > [O Axios](https://www.npmjs.com/package/axios) é um pacote nodejs popular que ajuda você com solicitações http(s). Para obter mais informações sobre como fazer solicitações http(s), consulte a documentação de exemplo do [Axios](https://axios-http.com/docs/example) para saber como fazer http(s).

## <a name="deploy-your-application-to-azure"></a>Implantar seu aplicativo no Azure

Para implantar seu aplicativo no Azure, você precisa adicionar a autenticação às configurações do aplicativo para o ambiente apropriado. Por exemplo, sua API pode ter credenciais diferentes para `dev` e `prod`. Com base nas necessidades do ambiente, configure o Kit de Ferramentas do Teams.

O Kit de Ferramentas do Teams configura seu ambiente local. O código de exemplo inicializado contém comentários que informam quais configurações de aplicativo você precisa definir. Para obter mais informações sobre as configurações do aplicativo, consulte [Adicionar configurações de aplicativo](https://github.com/OfficeDev/TeamsFx/wiki/%5BDocument%5D-Add-app-settings)

## <a name="provision-and-deploy-cicd-resources"></a>Provisionar e implantar recursos de CI/CD

Para provisionar e implantar recursos direcionados ao Azure dentro de CI/CD, você deve criar uma entidade de serviço do Azure para uso.

Execute as seguintes etapas para criar entidades de serviço do Azure:

1. Registre um aplicativo do Microsoft Azure Active Directory (Azure AD) em um único locatário.
2. Atribua uma função ao seu aplicativo do Azure AD para acessar sua assinatura do Azure. A `Contributor` função é recomendada.
3. Crie um novo segredo do aplicativo do Azure AD.

> [!TIP]
> Salve sua ID de locatário, ID do aplicativo (AZURE_SERVICE_PRINCIPAL_NAME) e o segredo (AZURE_SERVICE_PRINCIPAL_PASSWORD) para uso futuro.

Para obter mais informações, consulte[Diretrizes de entidades de serviço do Azure](/azure/active-directory/develop/howto-create-service-principal-portal). A seguir estão as três maneiras de criar entidades de serviço:

* [Portal do Microsoft Azure](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [CLI do Microsoft Azure](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="see-also"></a>Confira também

* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
