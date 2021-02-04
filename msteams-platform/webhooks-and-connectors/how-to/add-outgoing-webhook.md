---
title: Adicionar bots personalizados ao Microsoft Teams com webhooks de saída
description: descreve como adicionar um webhook de saída
ms.topic: conceptual
ms.author: lajanuar
keywords: teams tabs outgoing webhook actionable message verify webhook
ms.openlocfilehash: 20d30be7a35b33b94dc4a856439c51d5d0cc441c
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093250"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Adicionar bots personalizados ao Teams com webhooks de saída

## <a name="what-are-outgoing-webhooks-in-teams"></a>O que são webhooks de saída no Teams?

Os webhooks são uma maneira mais fácil de o Teams se integrar a aplicativos externos. Um webhook é essencialmente uma solicitação POST enviada para uma URL de retorno de chamada. Os webhooks de saída permitem que os usuários enviem mensagens para seu serviço Web sem passar pelo processo completo de criação de bots por meio do [Microsoft Bot Framework.](https://dev.botframework.com/)

O webhook de saída envia dados do Teams para qualquer serviço escolhido capaz de aceitar uma carga JSON. Depois de adicionar os webhooks de saída a uma equipe, ele atua como um bot e procura mensagens em canais usando **\@ menção.** Ele envia notificações para serviços Web externos e responde com mensagens rich messages, que incluem cartões e imagens.

## <a name="outgoing-webhook-key-features"></a>Recursos de chave de webhook de saída

| Recurso | Descrição |
| ------- | ----------- |
| Configuração com escopo| Os webhooks têm escopo no nível da equipe. Você deve passar pelo processo de configuração para cada equipe em que deseja adicionar seu webhook de saída. |
| Mensagens reativas| Os usuários devem usar @mention webhook para receber mensagens. Atualmente, os usuários só podem enviar mensagens para um webhook de saída em canais públicos e não dentro do escopo pessoal ou privado. |
|Troca de mensagens HTTP padrão|As respostas aparecem na mesma cadeia que a mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem de estrutura de bot, por exemplo, rich text, imagens, cartões e emojis. Embora os webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto para `openURL` .|
| Suporte ao método da API do Teams|O webhook de saída envia um HTTP POST para um serviço Web e processa uma resposta de volta. Eles não podem acessar outras APIs, como recuperar a lista ou a lista de canais em uma equipe.|

## <a name="creating-actionable-messages"></a>Criar mensagens acionáveis

Os cartões do conector incluem três botões visíveis no cartão. Cada botão é definido na `potentialAction` propriedade da mensagem usando `ActionCard` ações. Cada `ActionCard` um contém um tipo de entrada; um campo de texto, um selador de data ou uma lista de várias opções. Cada `ActionCard` ação tem uma ação associada, por exemplo, `HttpPOST` .

Os cartões do conector oferecem suporte a três tipos de ações:

| Ação | Descrição |
| ------- | ----------- |
| `ActionCard` |Apresenta um ou mais tipos de entrada e ações associadas.|
| `HttpPOST` | Envia uma solicitação POST para uma URL. |
| `OpenUri` |  Abre um URI em um navegador ou aplicativo separado, opcionalmente direciona URIs diferentes com base em sistemas operacionais.|

A ação `ActionCard` oferece suporte a três tipos de entrada:

| Tipo de entrada | Descrição |
| ------- | ----------- |
| `TextInput` | Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional. |
| `DateInput` | Um seletor de data com um seletor de hora opcional. |
| `MultichoiceInput` | Uma lista de opções especificada, oferecendo uma única seleção ou várias seleções.|

`MultichoiceInput` oferece suporte a `style` uma propriedade que controla a exibição de uma lista totalmente expandida. O valor padrão `style` depende do `isMultiSelect` valor.

| `isMultiSelect` value  | `style` valor padrão  |
| --- | --- |
| `false` ou não especificado  | O estilo padrão é `compact`|
| `true` | O estilo padrão é `expanded` |

> [!NOTE]
> * Insira ambos e, se você quiser que a lista de várias `"isMultiSelect": true` seleções seja exibida em um estilo `"style": true` compacto.
> * Selecionar a propriedade no Teams é o mesmo que selecionar a `compact` `style` propriedade no Microsoft `normal` `style` Outlook.
> * Os webhooks suportam apenas cartões de retorno de mensagens e cartões adaptáveis do Office 365.

Para todos os outros detalhes sobre ações de cartão do conector, consulte **[Ações](/outlook/actionable-messages/card-reference#actions)** na referência de cartão de mensagem a actionable.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Adicionando webhooks de saída ao seu aplicativo

**Cenário:** notificações de status de alteração por push em um servidor de banco de dados de canal do Teams para seu aplicativo.  
**Exemplo:** você tem um aplicativo de linha de negócios que rastreia todas as operações CRUD feitas nos registros dos funcionários pelos usuários do RH do canal do Teams em um local do Office 365.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON

Seu serviço recebe mensagens em um esquema padrão de mensagens do serviço de bot do Azure. O conector de estrutura de bot é um serviço RESTful que capacita seu serviço a processar a troca de mensagens formatadas JSON por meio de protocolos HTTPS, conforme documentado na API do Serviço de Bot do [Azure.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) Como alternativa, você pode seguir o [SDK do Microsoft Bot Framework] para processar e analisar mensagens. Consulte também [Sobre o Serviço de Bot do Azure.](/azure/bot-service/bot-service-overview-introduction)


Os webhooks de saída têm como escopo o `team` nível e são visíveis para todos os membros da equipe. Assim como um bot, os usuários precisam **\@ mencionar** o nome do webhook de saída para invocá-lo no canal.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Crie um método para verificar o token HMAC do webhook de saída

#### <a name="hmac-signature-for-testing-with-code-example"></a>Assinatura HMAC para teste com exemplo de código

Usando exemplo de mensagem de entrada e id: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do header da solicitação.

Para garantir que seu serviço receba chamadas apenas de clientes reais do Teams, o Teams fornece um código HMAC no `hmac` cabeçalho HTTP. Sempre incluiu o código no protocolo de autenticação.

Seu código deve sempre validar a assinatura HMAC incluída na solicitação:

* Gere o token HMAC do corpo da solicitação da mensagem. Há bibliotecas padrão para fazer isso na maioria das plataformas (consulte [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js ou veja o Exemplo de [Webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) do Teams para \# C). O Microsoft Teams usa criptografia HMAC padrão SHA256. Você precisa converter o corpo em uma matriz de byte em UTF8.
* Calcule o hash da matriz de byte do token de segurança fornecido pelo **Teams** quando você registrou o webhook de saída no cliente do Teams]. Consulte [Criar um webhook de saída.](#create-an-outgoing-webhook)
* Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.
* Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Crie um método para enviar uma resposta de sucesso ou falha

As respostas de seus webhooks de saída aparecem na mesma cadeia de resposta que a mensagem original. Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para seu serviço e seu código tem cinco segundos para responder à mensagem antes que a conexão se esmaeça e termine.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Criar um webhook de saída

1. Selecione a equipe apropriada e escolha **Gerenciar equipe** no menu suspenso (&#8226;&#8226;&#8226;) menu suspenso.
1. Escolha a **guia Aplicativos** na barra de navegação.
1. No canto inferior direito da janela, selecione **Criar um webhook de saída.**
1. Na janela pop-up resultante, preencha os campos necessários:

>* **Nome** - o título do webhook e o @mention tocar.
>* **URL de retorno** de chamada - O ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST do Teams.
>* **Descrição** - Uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel do aplicativo no nível da equipe.
>* **Imagem de perfil** um ícone de aplicativo opcional para seu webhook.
>* Selecione o **botão** Criar no canto inferior direito da janela pop-up e o webhook de saída será adicionado aos canais da equipe atual.
>* A próxima janela de diálogo exibe um token de segurança [HMAC (Código](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) de Autenticação de Mensagem Baseado em Hash) usado para autenticar chamadas entre o Teams e o serviço externo designado.
>* O webhook de saída estará disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação do servidor e do cliente são iguais, por exemplo, um handshake HMAC.

## <a name="code-samples"></a>Exemplos de código

Você pode exibir exemplos de código de webhook de saída no GitHub:

### <a name="nodejs"></a>Node.js

[OfficeDev/msteams-samples-outgoing-webhook-nodejs](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs)

### <a name="c"></a>C\#

[OfficeDev/microsoft-teams-sample-outgoing-webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook)
