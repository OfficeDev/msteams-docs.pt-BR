---
title: Solução de problemas de autenticação para guias usando o SSO no Teams
description: Solução de problemas de autenticação de SSO no Teams e como usá-la em guias
ms.topic: how-to
ms.localizationpriority: medium
keywords: perguntas sobre erros de SSO Microsoft Azure Active Directory (Azure AD) do Teams
ms.openlocfilehash: d738c992b008028456dc9318b2a0720178f6f66f
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503722"
---
# <a name="troubleshoot-sso-authentication-in-teams"></a>Solucionar problemas de autenticação de SSO no Teams

Aqui está uma lista de problemas e perguntas sobre o SSO e como você pode corrigi-los.
<br>

## <a name="support-for-microsoft-graph"></a>Suporte para o Microsoft Graph

<br>
<details>
<summary>1. O API do Graph funciona no Postman?</summary>
<br>
Você pode usar a coleção postman do Microsoft Graph com APIs do Microsoft Graph.

Para obter mais informações, confira [Usar o Postman com a API do Microsoft Graph](/graph/use-postman).
</details>
<br>
<details>
<summary>2. O API do Graph no Explorador do Microsoft Graph?</summary>
<br>
Sim, API do Graph funciona no Explorador do Microsoft Graph.

Para obter mais informações, consulte [Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer).

</details>
<br>

## <a name="error-messages-and-how-to-handle-them"></a>Mensagens de erro e como lidar com elas

<br>
<details>
<summary>1. Erro: consentimento ausente.</summary>
<br>
Quando Azure AD recebe uma solicitação para acessar um recurso do Microsoft Graph, ele verifica se o usuário (ou o administrador do locatário) deu consentimento para esse recurso. Se não houver nenhum registro de consentimento do usuário ou administrador, o Azure AD enviará uma mensagem de erro ao serviço Web.

Seu código deve informar ao cliente (por exemplo, no corpo de uma resposta 403 Proibido) como lidar com o erro:

- Se o aplicativo guia precisar de escopos do Microsoft Graph para os quais apenas um administrador pode dar consentimento, seu código deverá gerar um erro.
- Se os únicos escopos necessários puderem ser consentidos pelo usuário, o código deverá retornar a um sistema alternativo de autenticação de usuário.

</details>
<br>
<details>
<summary>2. Erro: escopo ausente (permissão).</summary>
<br>
Esse erro é visto somente durante o desenvolvimento.

Para lidar com esse erro, o código do lado do servidor deve enviar uma resposta 403 Proibido ao cliente. Ele deve registrar o erro no console ou registrá-lo em um log.
</details>
<br>
<details>
<summary>3. Erro: Público inválido no token de acesso do Microsoft Graph.</summary>
<br>
O código do lado do servidor deve enviar uma resposta 403 Proibido ao cliente para mostrar uma mensagem ao usuário. É recomendável que ele também registre o erro no console ou registre-o em um log.
</details>
<br>
<details>
<summary>4. Erro: o nome do host não deve ser baseado em um domínio já pertencente.</summary>
<br>
Você pode obter esse erro em um dos dois cenários:

1. O domínio personalizado não é adicionado ao Azure AD. Para adicionar um domínio personalizado Azure AD registrá-lo, siga o procedimento adicionar [](/azure/active-directory/fundamentals/add-custom-domain) um nome de domínio personalizado ao Azure AD e siga as etapas para Configurar o escopo do [token](tab-sso-register-aad.md#configure-scope-for-access-token) de acesso novamente.
1. Você não está conectado com as credenciais de Administrador no locatário do Microsoft 365. Entre no Microsoft 365 como administrador.

</details>
<br>
<details>
<summary>5. Erro: NOME UPN (Nome UPN) não recebido no token de acesso retornado.</summary>
<br>
Você pode adicionar o UPN como uma declaração opcional no Azure AD.

Para obter mais informações, [consulte Fornecer declarações opcionais para seu aplicativo e](/azure/active-directory/develop/active-directory-optional-claims) [tokens de acesso](/azure/active-directory/develop/access-tokens).
</details>
<br>
<details>
<summary>6. Erro: Erro do SDK do Teams: resourceDisabled.</summary>
<br>
Para evitar esse erro, verifique se o URI da ID do aplicativo está configurado corretamente Azure AD registro de aplicativo e no cliente do Teams.

Para obter mais informações sobre o URI da ID do aplicativo, consulte [Para expor uma API](tab-sso-register-aad.md#to-expose-an-api).

</details>
<br>

<details>
<summary>7. Erro: erro genérico ao executar o aplicativo guia.</summary>
<br>
Um erro genérico pode aparecer quando uma ou mais configurações de aplicativo feitas Azure AD estão incorretas. Para resolver esse erro, verifique se os detalhes do aplicativo configurados no código e no manifesto do Teams correspondem aos valores Azure AD.

A imagem a seguir mostra um exemplo dos detalhes do aplicativo configurados Azure AD.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-app-details.png" alt-text="Valores de configuração de aplicativo Azure AD" border="false":::

Verifique se os seguintes valores correspondem entre o Azure AD, o código do lado do cliente e o manifesto do aplicativo Teams:

- **ID do** aplicativo: a ID do aplicativo que você gerou Azure AD deve ser a mesma no código e no arquivo de manifesto do Teams. Verifique se a ID do aplicativo no manifesto do Teams corresponde à **ID** do aplicativo (cliente) Azure AD.

- **Segredo do** aplicativo: o segredo do aplicativo configurado no back-end do aplicativo deve corresponder às **credenciais** do cliente no Azure AD.
    Você também deve verificar se o segredo do cliente expirou.

- **URI da ID** do aplicativo: o URI da ID do aplicativo no código e no arquivo de manifesto do aplicativo teams deve corresponder ao **URI da ID** do aplicativo Azure AD.

- **Permissões de aplicativo**: verifique se as permissões definidas no escopo estão de acordo com o requisito do aplicativo. Nesse caso, verifique se eles foram concedidos ao usuário no token de acesso.

- **Administração consentimento**: se qualquer escopo exigir consentimento do administrador, verifique se o consentimento foi concedido para o escopo específico para o usuário.

Além disso, inspecione o token de acesso que foi enviado ao aplicativo guia para verificar se os seguintes valores estão corretos:

- **Público-alvo (aud)**: verifique se a ID do aplicativo no token está correta, conforme fornecido em Azure AD.
- **ID do locatário(tid)**: verifique se o locatário mencionado no token está correto.
- **Identidade do usuário (preferred_username)**: verifique se a identidade do usuário corresponde ao nome de usuário na solicitação de token de acesso para o escopo que o usuário atual deseja acessar.
- **Escopos (scp):** verifique se o escopo para o qual o token de acesso é solicitado está correto e conforme definido em Azure AD.
- **Azure AD versão 1.0 ou 2.0 (ver)**: verifique se Azure AD versão está correta.

Você pode usar [o JWT](https://jwt.ms) para inspecionar o token.

</details>
