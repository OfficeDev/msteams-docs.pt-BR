---
title: Integrar APIs de terceiros existentes
author: MuyangAmigo
description: Neste artigo, saiba como o kit de ferramentas ajuda você a inicializar o acesso de exemplo às APIs existentes. Ele fornece uma lista de tipos de autenticação diferentes.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 5933227f9ba4c8b684d624a8857304c044761578
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616804"
---
# <a name="integrate-existing-third-party-apis"></a>Integrar APIs de terceiros existentes

O Kit de Ferramentas do Teams ajuda você a acessar APIs existentes para a criação de aplicativos do Teams. Essas APIs são desenvolvidas pela sua organização ou por terceiros. Quando você usa o Kit de Ferramentas do Teams para se conectar a uma API existente, o Kit de Ferramentas do Teams executa a seguinte função:

* Gere código de exemplo em `./bot` ou pasta `./api` .
* Adicione uma referência ao `@microsoft/teamsfx` pacote a `package.json`.
* Adicione configurações de aplicativo para sua API que  `.env.teamsfx.local` define a depuração local.

## <a name="steps-to-connect-to-api"></a>Etapas para se conectar à API

Você pode adicionar conexão de API usando Visual Studio Code comando e CLI.

### <a name="add-api-connection-using-visual-studio-code"></a>Adicionar conexão de API usando Visual Studio Code

As etapas a seguir ajudam você a adicionar conexão de API usando Visual Studio Code:

1. Abra o Microsoft Visual Studio Code.
2. Selecione o ícone da :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="API do Kit de Ferramentas do"::: Teams na Visual Studio Code de ferramentas.
3. Selecione **Adicionar recursos** em **DESENVOLVIMENTO**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="api add features":::

    * Você também pode abrir a paleta de comandos e inserir **o Teams: Adicionar recursos de nuvem**.

4. No pop-up, selecione a Conexão **de API** que você deseja adicionar ao seu projeto de aplicativo do Teams:

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

     :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/myAPI connection.png" alt-text="autenticação de api":::

     Com base no tipo de autenticação selecionado, as etapas a seguir são necessárias para concluir a configuração extra

# <a name="basic"></a>[Básica](#tab/basic)

* Insira o nome de usuário para autenticação básica.

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="certification"></a>[Certificação](#tab/certification)

   Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="azure-active-directory"></a>[Azure Active Directory](#tab/AAD)

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="api-key"></a>[Chave de API](#tab/apikey)

* Selecione a posição da chave de API necessária na solicitação.

* Insira um nome de chave de API.

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="custom-auth-implementation"></a>[Implementação de autenticação personalizada](#tab/CustomAuthImplementation)

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

---

## <a name="add-api-connection-using-cli"></a>Adicionar conexão de API usando a CLI

O comando base desse recurso é `teamsfx add api-connection [authentication type]`. A tabela a seguir fornece uma lista de diferentes tipos de autenticação e seus comandos de exemplo correspondentes:

 > [!TIP]
 > Você pode usar para `teamsfx add api-connection [authentication type] -h` obter o documento de ajuda.

   |**Tipo de autenticação**|**Comando de amostra**|
   |-----------------------|------------------|
   |Básico|teamsfx add api-connection basic--endpoint <https://example.com> --component bot--alias example--user-name exampleuser--interactive false|
   |Chave de API|teamsfx add api-connection apikey--endpoint <https://example.com> --component bot--alias example--key-location header--key-name example-key-name--interactive false|
   |Microsoft Azure AD|teamsfx add api-connection aad--endpoint <https://example.com> --component bot--alias example--app-type custom--tenant-id your_tenant_id--app-id your_app_id--interactive false|
   |Certificado|teamsfx add api-connection cert--endpoint <https://example.com> --component bot--alias example--interactive false|
   |Personalizado|teamsfx add api-connection custom--endpoint <https://example.com> --component bot--alias example--interactive false|

---

## <a name="directory-structure-updates-to-your-project"></a>Atualizações de estrutura de diretório para seu projeto

 O Kit de Ferramentas do Teams modifica `bot` ou `api` pasta com base em suas seleções:

1. Gerar `{your_api_alias}.js/ts` arquivo. O arquivo inicializa um cliente de API para sua API e exporta o cliente de API.

2. Adicionar `@microsoft/teamsfx` pacote a `package.json`. O pacote fornece suporte para os métodos comuns de autenticação de API.

3. Adicione variáveis de ambiente a `.env.teamsfx.local`. Elas são as configurações para o tipo de autenticação selecionado. O código gerado lê valores das variáveis de ambiente.

## <a name="advantages"></a>Vantagens

O Kit de Ferramentas do Teams ajuda você a inicializar o código de exemplo para acessar as APIs, se você não tiver SDKs apropriados para acessar essas APIs.

## <a name="see-also"></a>Confira também

* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
