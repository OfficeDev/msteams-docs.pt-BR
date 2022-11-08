---
title: Aplicativo de sideload e teste no ambiente do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como carregar e testar o aplicativo em um ambiente diferente
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
ms.openlocfilehash: 721b3a30bcc8c2fa49bb06491f4ab24bbeb844fd
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68832999"
---
# <a name="sideload-and-test-app-in-teams-environment"></a>Aplicativo de sideload e teste no ambiente do Teams

Depois de adicionar conexão de API, você pode testar a conexão de API no ambiente local do Teams Toolkit e implantar seu aplicativo na nuvem. No pipeline de CI/CD, após a configuração com uma plataforma diferente, você precisa criar a entidade de serviço do Azure para provisionar e implantar recursos.

Nesta seção, você aprenderá

* [Testar a conexão de API no ambiente local](#test-api-connection-in-local-environment)
* [Implantar seu aplicativo no Azure](#deploy-your-application-to-azure)
* [Provisionar e implantar recursos de CI/CD](#provision-and-deploy-cicd-resources)

## <a name="test-api-connection-in-local-environment"></a>Testar a conexão de API no ambiente local

As etapas a seguir ajudam a testar a conexão de API no ambiente local do Teams Toolkit:

 1. **Executar a instalação do npm**

    Execute `npm install` em `bot` ou `api` pasta para instalar pacotes adicionados.

 2. **Adicionar credenciais de API às configurações do aplicativo local**

    O Teams Toolkit não pede credenciais, mas deixa espaços reservados no arquivo de configurações do aplicativo local. Substitua os espaços reservados pelas credenciais apropriadas para acessar a API. O arquivo de configurações do aplicativo local é o `.env.teamsfx.local` arquivo na `bot` pasta ou `api` .

 3. **Usar o cliente de API para fazer solicitações de API**

    Importe o cliente de API do código-fonte que precisa de acesso à API:

    ```BASH
    import { yourApiClient } from '{relative path to the generated file}'
    ```

 4. **Gerar solicitações http(s) para a API de destino (com a Axios)**

    O cliente de API gerado é um cliente de API do Axios. Use o cliente Axios para fazer solicitações à API.

     > [!Note]
     > [O Axios](https://www.npmjs.com/package/axios) é um pacote de nodejs popular que ajuda você com solicitações http(s). Para obter mais informações sobre como fazer solicitações http(s), confira [Documentação de exemplo do Axios](https://axios-http.com/docs/example) para saber como fazer http(s).

## <a name="deploy-your-application-to-azure"></a>Implantar seu aplicativo no Azure

Para implantar seu aplicativo no Azure, você precisa adicionar a autenticação às configurações do aplicativo para o ambiente apropriado. Por exemplo, sua API pode ter credenciais diferentes para `dev` e `prod`. Com base nas necessidades de ambiente, configure o Teams Toolkit.

O Kit de Ferramentas do Teams configura seu ambiente local. O código de exemplo inicializado contém comentários que dizem quais configurações de aplicativo você precisa configurar. Para obter mais informações sobre as configurações do aplicativo, consulte [Adicionar configurações de aplicativo](https://github.com/OfficeDev/TeamsFx/wiki/%5BDocument%5D-Add-app-settings)

## <a name="provision-and-deploy-cicd-resources"></a>Provisionar e implantar recursos de CI/CD

Para provisionar e implantar recursos direcionados ao Azure dentro de CI/CD, você deve criar uma entidade de serviço do Azure para uso.

Execute as seguintes etapas para criar entidades de serviço do Azure:

1. Registre um aplicativo do Microsoft Azure Active Directory (Azure AD) em um único locatário.
2. Assign a role to your Azure AD application to access your Azure subscription. The `Contributor` role is recommended.
3. Crie um novo segredo do aplicativo do Azure AD.

> [!TIP]
> Salve sua ID de locatário, ID do aplicativo (AZURE_SERVICE_PRINCIPAL_NAME) e o segredo (AZURE_SERVICE_PRINCIPAL_PASSWORD) para uso futuro.

Para obter mais informações, consulte[Diretrizes de entidades de serviço do Azure](/azure/active-directory/develop/howto-create-service-principal-portal). A seguir estão as três maneiras de criar entidades de serviço:

* [Portal do Microsoft Azure](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [CLI do Microsoft Azure](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="see-also"></a>Confira também

[Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
