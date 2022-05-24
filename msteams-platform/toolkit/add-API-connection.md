---
title: Conexão apIs existentes
author: MuyangAmigo
description: Descreve a conexão com APIs existentes
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 133ec7fa80950fde59529a2e1abe0415d6620171
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65655079"
---
# <a name="connect-to-existing-apis"></a>Conexão apIs existentes

Teams Toolkit ajuda você a acessar APIs existentes para criar Teams aplicativos. Essas APIs são desenvolvidas pela sua organização ou por terceiros.

## <a name="advantage"></a>Vantagem

Teams Toolkit o código de exemplo de inicialização para acessar as APIs se você não tiver SDKs apropriados para acessar essas APIs.

## <a name="connect-to-the-api"></a>Conexão à API

Quando você usa Teams Toolkit para se conectar a uma API existente, Teams Toolkit executa a seguinte função:

* Gerar código de exemplo em `./bot` ou pasta `./api`
* Adicionar uma referência ao `@microsoft/teamsfx` pacote a `package.json`
* Adicionar configurações de aplicativo para sua API que  `.env.teamsfx.local` define a depuração local

### <a name="connect-to-api-in-visual-studio-code"></a>Conexão à API no Visual Studio Code

* Você pode adicionar conexão de API usando Teams Toolkit no Visual Studio Code:

    1. Abra o Microsoft Visual Studio Code.
    2. Selecione Teams Toolkit :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="de API na"::: barra de navegação esquerda.
    3. Selecione **Adicionar recursos** em **DESENVOLVIMENTO**:

        :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="api add features":::

       * Você também pode abrir a paleta de comandos e inserir **Teams: Adicionar recursos de nuvem**.

    4. No pop-up, selecione a Conexão **de API** que você deseja adicionar ao seu projeto Teams aplicativo:

        :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-select-features.png" alt-text="recursos de seleção de API":::

    5. Selecione **OK**.

    6. Insira o ponto de extremidade para a API. Ele é adicionado às configurações de aplicativo local do projeto e é a URL base para solicitações de API.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-endpoint.png" alt-text="ponto de extremidade de api":::

         > [!NOTE]
         > Verifique se o ponto de extremidade é uma URL http(s) válida.

    7. Selecione o componente que acessa a API.

    8. Selecione **OK**.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-invoke.png" alt-text="invocação de api":::

    9. Insira um alias para a API. O alias gera um nome de configuração de aplicativo para a API que é adicionada à configuração de aplicativo local do projeto.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-alias.png" alt-text="alias de api":::

    10. Selecione a autenticação necessária para a solicitação de API do tipo **de autenticação de API**. Ele gera o código de exemplo apropriado e adiciona as configurações de aplicativo local correspondentes com base em sua seleção.

         :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-auth.png" alt-text="autenticação de api":::

         > [!NOTE]
         > Com base no tipo de autenticação selecionado, é necessária uma configuração adicional.

### <a name="api-connection-in-teamsfx-cli"></a>Conexão de API na CLI do TeamsFx

O comando base desse recurso é `teamsfx add api-connection [authentication type]`. A tabela a seguir fornece uma lista de diferentes tipos de autenticação e seus comandos de exemplo correspondentes:

 > [!Tip]
 > Você pode usar para `teamsfx add api-connection [authentication type] -h` obter o documento de ajuda.

   |**Tipo de autenticação**|**Comando de exemplo**|
   |-----------------------|------------------|
   |Básico|teamsfx add api-connection basic --endpoint <https://example.com> --component bot --alias example --user-name exampleuser --interactive false|
   |Chave de API|teamsfx add api-connection apikey --endpoint <https://example.com> --component bot --alias example --key-location header --key-name example-key-name --interactive false|
   |Azure AD|teamsfx add api-connection aad --endpoint <https://example.com> --component bot --alias example --app-type custom --tenant-id your_tenant_id --app-id your_app_id --interactive false|
   |Certificado|teamsfx add api-connection cert --endpoint <https://example.com> --component bot --alias example --interactive false|
   |Personalizado|teamsfx add api-connection custom --endpoint <https://example.com> --component bot --alias example --interactive false|

## <a name="understand-toolkit-updates-to-your-project"></a>Entender Toolkit atualizações do seu projeto

 Teams Toolkit modificações ou `bot` pastas `api` com base em suas seleções:

1. Gerar `{your_api_alias}.js/ts` arquivo. O arquivo inicializa um cliente de API para sua API e exporta o cliente de API.

2. Adicionar `@microsoft/teamsfx` pacote a `package.json`. O pacote fornece suporte para os métodos comuns de autenticação de API.

3. Adicione variáveis de ambiente a `.env.teamsfx.local`. Elas são as configurações para o tipo de autenticação selecionado. O código gerado lê valores das variáveis de ambiente.

## <a name="test-api-connection-in-local-environment"></a>Testar a conexão de API no ambiente local

As etapas a seguir ajudam a testar a conexão de API no ambiente Teams Toolkit local:

 1. **Executar npm instalação**

    Execute `npm install` em ou `bot` pasta `api` para instalar pacotes adicionados.

 2. **Adicionar credenciais de API às configurações do aplicativo local**

    Teams Toolkit não solicita credenciais, mas deixa espaços reservados no arquivo de configurações do aplicativo local. Substitua os espaços reservados com as credenciais apropriadas para acessar a API. O arquivo de configurações do aplicativo local é `.env.teamsfx.local` o arquivo na `bot` pasta `api` ou na pasta.

 3. **Usar o cliente de API para fazer solicitações de API**

    Importe o cliente de API do código-fonte que precisa de acesso à API:

    ```BASH
    import { yourApiClient } from '{relative path to the generated file}'
    ```

 4. **Gerar solicitações http(s) para a API de destino (com a Axios)**

    O cliente de API gerado é um cliente da API do Axios. Use o cliente Axios para fazer solicitações à API.

     > [!Note]
     >[O Axios](https://www.npmjs.com/package/axios) é um pacote nodejs popular que ajuda você com solicitações http(s). Para obter mais informações sobre como fazer solicitações http(s), consulte a documentação de exemplo do [Axios](https://axios-http.com/docs/example) para saber como fazer http(s).

## <a name="deploy-your-application-to-azure"></a>Implantar seu aplicativo no Azure

Para implantar seu aplicativo no Azure, você precisa adicionar a autenticação às configurações do aplicativo para o ambiente apropriado. Por exemplo, sua API pode ter credenciais diferentes para `dev` e `prod`. Com base nas necessidades do ambiente, configure Teams Toolkit.

Teams Toolkit configura seu ambiente local. O código de exemplo inicializado contém comentários que informam quais configurações de aplicativo você precisa definir. Para obter mais informações sobre as configurações do aplicativo, consulte [Adicionar configurações de aplicativo](https://github.com/OfficeDev/TeamsFx/wiki/%5BDocument%5D-Add-app-settings).

## <a name="advanced-scenarios"></a>Cenários avançados

  A seção a seguir explica os cenários avançados:

<br>

<details>
<summary><b>Provedor de autenticação personalizado</b></summary>

Além do provedor de autenticação incluído no `@microsoft/teamsfx` pacote, `AuthProvider` você também pode implementar o provedor de autenticação personalizado que implementa a interface e usá-la em `createApiClient(..)` função:

```Bash
import { AuthProvider } from '@microsoft/teamsfx'

class CustomAuthProvider implements AuthProvider {
    constructor() {
        // You can add necessary parameters for your customized logic in constructor
    }

    AddAuthenticationInfo: (config: AxiosRequestConfig) => Promise<AxiosRequestConfig> = async (
        config
    ) => {
        /*
        * The config parameter contains all the request information and can be updated to include extra authentication info.
        * Refer https://axios-http.com/docs/req_config for detailed document for the config object.
        * 
        * Add your customized logic that returns updated config
        */
    };
}
```
</details>
<details>
<summary><b>Conexão a APIs para Azure AD permissões</b></summary>
Azure AD autentica alguns serviços. A lista a seguir ajuda a acessar esses serviços para configurar permissões de API.

* [Usar acLs (listas de Controle de Acesso)](#access-control-lists-acls)
* [Usar Azure AD de aplicativo](#azure-ad-application-permissions)

A obtenção de um token com os escopos de recurso corretos para sua API depende da implementação da API.

Você pode seguir as etapas para acessar essas APIs ao usar:

#### <a name="access-control-lists-acls"></a>acLs (listas de Controle de Acesso)

   1. Inicie a depuração local no ambiente de nuvem do seu projeto. Ele cria um registro Azure AD aplicativo em seu Teams aplicativo.
  
   2. Abra `.fx/states/state.{env}.json`e anote o valor da `clientId` propriedade `fx-resource-aad-app-for-teams` abaixo.

   3. Forneça a ID do cliente ao provedor de API para configurar ACLs no serviço de API.

#### <a name="azure-ad-application-permissions"></a>Azure AD de aplicativo

  1. Abra `templates/appPackage/aad.template.json` e adicione o seguinte conteúdo à `requiredResourceAccess` propriedade:

```JSON
 {
     "resourceAppId": "The AAD App Id for the service providing the API you are connecting to",
     "resourceAccess": [
         {
             "id": "Target API's application permission Id",
             "type": "Role"
         }
     ]
 }
```

   2. Inicie a depuração local no ambiente de nuvem do seu projeto. Ele cria um registro Azure AD aplicativo em seu Teams aplicativo.

   3. Abra `.fx/states/state.{env}.json` e anote o valor da `clientId` propriedade `fx-resource-aad-app-for-teams` abaixo. É a ID do cliente do aplicativo.

   4. Conceda consentimento do administrador para a permissão de aplicativo necessária. Para obter mais informações, consulte [conceder consentimento do administrador](/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-in-app-registrations).

        > [!NOTE]
        > Para permissão de aplicativo, use a ID do cliente.
</details>

## <a name="see-also"></a>Confira também

* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
