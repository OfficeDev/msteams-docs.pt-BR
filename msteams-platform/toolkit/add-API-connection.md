---
title: Integrar APIs de terceiros existentes
author: MuyangAmigo
description: Neste artigo, saiba como o kit de ferramentas ajuda você a inicializar o acesso de exemplo às APIs existentes. Ele fornece uma lista de diferentes tipos de autenticação.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
ms.openlocfilehash: 6377f7d8a38054dacca76c0f87e39e51f466d925
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833139"
---
# <a name="integrate-existing-third-party-apis"></a>Integrar APIs de terceiros existentes

O Teams Toolkit ajuda você a acessar APIs existentes para criar aplicativos do Teams. Essas APIs são desenvolvidas por sua organização ou terceiros. Quando você usa o Teams Toolkit para se conectar a uma API existente, o Teams Toolkit executa a seguinte função:

* Gerar código de exemplo em `./bot` ou `./api` pasta.
* Adicione uma referência ao pacote a `@microsoft/teamsfx` `package.json`.
* Adicione configurações de aplicativo para sua API na  `.env.teamsfx.local` qual configura a depuração local.

## <a name="steps-to-connect-to-api"></a>Etapas para se conectar à API

Você pode adicionar conexão de API usando Visual Studio Code e comando CLI.

### <a name="add-api-connection-using-visual-studio-code"></a>Adicionar conexão de API usando Visual Studio Code

As etapas a seguir ajudam você a adicionar conexão de API usando Visual Studio Code:

1. Abra o Microsoft Visual Studio Code.
2. Selecione Ícone de :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="api"::: do Teams Toolkit na barra de ferramentas Visual Studio Code.
3. Selecione **Adicionar recursos** em **DESENVOLVIMENTO**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-add-features.png" alt-text="api add features":::

    * Você também pode abrir a paleta de comandos e inserir **o Teams: Adicionar recursos de nuvem**.

4. No pop-up, selecione a **Conexão de API** que você deseja adicionar ao seu projeto de aplicativo do Teams:

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-select-features.png" alt-text="api selecionar recursos":::

5. Selecione **OK**.

6. Insira ponto de extremidade para a API. Ele é adicionado às configurações de aplicativo local do projeto e é a URL base para solicitações de API.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-endpoint.png" alt-text="ponto de extremidade da api":::

     > [!NOTE]
     > Verifique se o ponto de extremidade é uma URL http(s) válida.

7. Selecione o componente que acessa a API.

8. Selecione **OK**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-invoke.png" alt-text="invocação de api":::

9. Insira um alias para a API. O alias gera um nome de configuração de aplicativo para a API que é adicionada à configuração do aplicativo local do projeto.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/api-alias.png" alt-text="api alias":::

10. Selecione a autenticação necessária para a solicitação de API no **tipo de autenticação de API**. Ele gera o código de exemplo apropriado e adiciona configurações de aplicativo locais correspondentes com base na sua seleção.

     :::image type="content" source="../assets/images/teams-toolkit-v2/add-API/myAPI connection.png" alt-text="api auth":::

     Com base no tipo de autenticação selecionado, as etapas a seguir são necessárias para concluir a configuração extra

# <a name="basic"></a>[Básica](#tab/basic)

* Insira o nome de usuário do Auth básico.

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="certification"></a>[Certificação](#tab/certification)

   Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="azure-active-directory"></a>[Azure Active Directory](#tab/AAD)

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="api-key"></a>[Chave de API](#tab/apikey)

* Selecione a posição de chave da API necessária na solicitação.

* Insira um nome de chave de API.

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

# <a name="custom-auth-implementation"></a>[Implementação de Auth personalizada](#tab/CustomAuthImplementation)

  Agora, o código de exemplo foi gerado para chamar sua API em bot\myAPI.js.

---

## <a name="add-api-connection-using-cli"></a>Adicionar conexão de API usando a CLI

O comando base desse recurso é `teamsfx add api-connection [authentication type]`. A tabela a seguir fornece uma lista de diferentes tipos de autenticação e seus comandos de exemplo correspondentes:

 > [!TIP]
 > Você pode usar `teamsfx add api-connection [authentication type] -h` para obter o documento de ajuda.

   |**Tipo de autenticação**|**Comando de amostra**|
   |-----------------------|------------------|
   |Básico|teamsfx add api-connection basic--endpoint <https://example.com> --component bot-alias example--user-name exampleuser--interactive false|
   |Chave de API|teamsfx add api-connection apikey--endpoint <https://example.com> --component bot--alias example--key-location header--key-name example-key-name-interactive false|
   |Microsoft Azure AD|teamsfx add api-connection aad--endpoint <https://example.com> --component bot--alias example--app-type custom--tenant-id your_tenant_id--app-id your_app_id-interactive false|
   |Certificado|teamsfx add api-connection cert-endpoint <https://example.com> --component bot-alias example--interactive false|
   |Personalizado|teamsfx add api-connection custom--endpoint <https://example.com> --component bot-alias example-- interactive false|

---

## <a name="directory-structure-updates-to-your-project"></a>Atualizações de estrutura de diretório para seu projeto

 O Teams Toolkit modifica `bot` ou `api` pasta com base em suas seleções:

1. Gerar `{your_api_alias}.js/ts` arquivo. O arquivo inicializa um cliente de API para sua API e exporta o cliente de API.

2. Adicionar `@microsoft/teamsfx` pacote a `package.json`. O pacote fornece suporte para os métodos comuns de autenticação de API.

3. Adicione variáveis de ambiente a `.env.teamsfx.local`. São as configurações do tipo de autenticação selecionado. O código gerado lê valores das variáveis de ambiente.

## <a name="advantages"></a>Vantagens

O Teams Toolkit ajuda você a inicializar o código de exemplo para acessar as APIs, se você não tiver SDKs apropriados para acessar essas APIs.

## <a name="see-also"></a>Confira também

[Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
