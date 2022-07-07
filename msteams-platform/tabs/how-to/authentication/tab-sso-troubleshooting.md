---
title: Solução de problemas de autenticação para guias que usam o logon único no Teams
description: Solução de problemas de autenticação de logon único no Teams e como usá-la em guias
ms.topic: how-to
ms.localizationpriority: high
keywords: guias de autenticação das equipes no Microsoft Azure Active Directory (Azure AD), perguntas de erro de logon único
ms.openlocfilehash: fa17ffef08f85124a230f76419158f4216f55416
ms.sourcegitcommit: 07f41abbeb1572a306a789485953c5588d65051e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66658953"
---
# <a name="troubleshoot-sso-authentication-in-teams"></a>Solucionar problemas de autenticação de logon único no Teams

Aqui está uma lista de problemas e perguntas sobre o logon único e como você pode corrigi-los.
<br>

## <a name="support-for-microsoft-graph"></a>Suporte para o Microsoft Graph

<br>
<details>
<summary>1. A API do Graph funciona no Postman?</summary>
<br>
Você pode usar a coleção do Microsoft Graph Postman com as APIs do Microsoft Graph.

Para obter mais informações, confira [Usar o Postman com a API do Microsoft Graph](/graph/use-postman).
</details>
<br>
<details>
<summary>2. A API do Graph funciona no Explorador do Graph da Microsoft?</summary>
<br>
Sim, a API do Graph funciona no Explorador do Graph da Microsoft.

Para saber mais, consulte [Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer).

</details>
<br>

## <a name="error-messages-and-how-to-handle-them"></a>Mensagens de erro e como lidar com elas

<br>
<details>
<summary>1. Erro: consentimento ausente.</summary>
<br>
Quando o Azure AD recebe uma solicitação para acessar um recurso do Microsoft Graph, ele verifica se o usuário (ou o administrador de locatários) deu consentimento para este recurso. Se não houver registro de consentimento do usuário ou administrador, o Azure AD envia uma mensagem de erro ao seu serviço Web.

Seu código deve informar ao cliente (por exemplo, no corpo de uma resposta 403 Forbidden) a como lidar com o erro:

- Se o aplicativo guia precisar de escopos do Microsoft Graph para os quais apenas um administrador pode dar consentimento, seu código deve gerar um erro.
- Se os únicos escopos necessários puderem ser consentidos pelo usuário, o código deverá retornar a um sistema alternativo de autenticação de usuário.

</details>
<br>
<details>
<summary>2. Erro: escopo ausente (permissão).</summary>
<br>
Este erro é visto somente durante o desenvolvimento.

Para lidar com este erro, seu código do lado do servidor deve enviar uma resposta 403 Forbidden ao cliente. Ele deve registrar o erro no console ou registrá-lo em um log.
</details>
<br>
<details>
<summary>3. Erro: audiência inválida no token de acesso para o Microsoft Graph.</summary>
<br>
O código do lado do servidor deve enviar uma resposta 403 Forbidden ao cliente para mostrar uma mensagem ao usuário. É recomendável que ele também registre o erro no console, ou registre-o em um log.
</details>
<br>
<details>
<summary>4. Erro: o nome do host não deve ser baseado em um domínio já possuído.</summary>
<br>
Você pode obter este erro em um dos dois cenários:

1. O domínio personalizado não é adicionado ao Azure AD. Para adicionar um domínio personalizado ao Azure AD e registrá-lo, siga o procedimento [adicionar um nome de domínio personalizado ao Azure AD](/azure/active-directory/fundamentals/add-custom-domain), e então siga as etapas para [Configurar o escopo do token de acesso](tab-sso-register-aad.md#configure-scope-for-access-token) novamente.
1. Você não está conectado com as credenciais de Administrador no locatário do Microsoft 365. Entre no Microsoft 365 como um administrador.

</details>
<br>
<details>
<summary>5. Erro: Nome Principal de Usuário (UPN) não recebido no token de acesso devolvido.</summary>
<br>
Você pode adicionar o UPN como uma declaração opcional no Azure AD.

Para saber mais, consulte [Fornecer declarações opcionais ao seu aplicativo](/azure/active-directory/develop/active-directory-optional-claims) e a [tokens de acesso](/azure/active-directory/develop/access-tokens).
</details>
<br>
<details>
<summary>6. Erro: Erro SDK do Teams: resourceDisabled.</summary>
<br>
Para evitar este erro, certifique-se que o URI da ID do aplicativo esteja configurado corretamente no registro do aplicativo Azure AD e em seu Cliente Teams.

Para saber mais sobre o URI da ID do aplicativo, consulte [Para expor uma API](tab-sso-register-aad.md#to-expose-an-api).

</details>
<br>

<details>
<summary>7. Erro: erro genérico ao executar o aplicativo guia.</summary>
<br>
Um erro genérico pode aparecer quando uma ou mais configurações de aplicativo feitas no Azure AD estão incorretas. Para resolver este erro, verifique se os detalhes do aplicativo configurado em seu código e no manifesto do Teams correspondem aos valores no Azure AD.

A seguinte imagem mostra um exemplo dos detalhes do aplicativo configurado no Azure AD.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-app-details.png" alt-text="Valores de configuração de aplicativo no Azure AD":::

Verifique se os seguintes valores correspondem entre o Azure AD, o código do lado do cliente e o manifesto do aplicativo Teams:

- **ID do aplicativo**: a ID do aplicativo que você gerou no Azure AD deve ser a mesma no código e arquivo de manifesto do Teams. Verifique se a ID do aplicativo no manifesto do Teams corresponde à **ID do aplicativo (cliente)** no Azure AD.

- **Segredo do aplicativo**: o segredo do aplicativo configurado no back-end do seu aplicativo deve corresponder às **Credenciais do cliente** no Azure AD.
    Você também deve verificar se o segredo do cliente está expirado.

- **URI da ID do aplicativo**: o URI da ID do aplicativo no código e no arquivo de manifesto do aplicativo Teams deve corresponder ao **URI da ID do aplicativo** no Azure AD.

- **Permissões de aplicativo**: verifique se as permissões que você definiu no escopo estão de acordo com o requisito do seu aplicativo. Neste caso, verifique se elas foram concedidas ao usuário no token de acesso.

- **Consentimento do administrador**: se qualquer escopo exigir consentimento do administrador, verifique se o consentimento foi concedido para o escopo particular ao usuário.

Além disso, inspecionar o token de acesso que foi enviado para o aplicativo guia para verificar se os seguintes valores estão corretos:

- **Audiência (aud)**: verifique se a ID do aplicativo no token está correta, conforme fornecida no Azure AD.
- **ID do locatário(tid)**: verifique se o locatário mencionado no token está correto.
- **Identidade do usuário (preferred_username)**: verifique se a identidade do usuário corresponde ao nome de usuário na solicitação de token de acesso para o escopo que o usuário atual quer acessar.
- **Escopos (scp)**: verifique se o escopo para o qual o token de acesso é solicitado está correto e conforme definido no Azure AD.
- **Azure AD versão 1.0 ou 2.0 (ver)**: verifique se a versão do Azure AD está correta.

Você pode usar o [JWT](https://jwt.ms) para inspecionar o token.

</details>
