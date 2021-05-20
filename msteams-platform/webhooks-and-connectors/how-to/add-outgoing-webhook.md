---
title: Adicione bots personalizados a Microsoft Teams com webhooks de saída
description: descreve como adicionar um webhook de saída
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: equipes guias saída webhook mensagem acionável verificar webhook
ms.openlocfilehash: a5a0cdfc9080ac4567f438b6fb6fd0671df8c19f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566527"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Adicione bots personalizados a Teams com webhooks de saída

## <a name="outgoing-webhooks-in-teams"></a>Webhooks de saída em Teams

Webhooks são uma maneira eminente para Teams se integrarem com aplicativos externos. Um webhook é essencialmente uma solicitação POST enviada para uma URL de retorno de chamada. Webhooks de saída permitem que os usuários enviem mensagens para o seu serviço web sem passar por todo o processo de criação de bots através do [Microsoft Bot Framework](https://dev.botframework.com/).

O webhook de saída envia dados de Teams para qualquer serviço escolhido capaz de aceitar uma carga JSON. Depois de adicionar os webhooks de saída a uma equipe, ele age como um bot e procura mensagens em canais usando **\@ menção**. Ele envia notificações para serviços web externos e responde com mensagens ricas, que incluem cartões e imagens.

## <a name="outgoing-webhook-key-features"></a>Recursos principais de webhook de saída

| Recurso | Descrição |
| ------- | ----------- |
| Configuração escopo| Os webhooks são escopo no nível da equipe. Você deve passar pelo processo de configuração de cada equipe onde deseja adicionar seu webhook de saída. |
| Mensagens reativas| Os usuários devem usar @mention para que o webhook receba mensagens. Atualmente, os usuários só podem enviar mensagens de saída em canais públicos e não no âmbito pessoal ou privado. |
|Troca de mensagens HTTP padrão|As respostas aparecem na mesma cadeia da mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem de estrutura de bot, por exemplo, texto rico, imagens, cartões e emojis. Embora webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto . `openURL`|
| Teams Suporte ao método API|O webhook de saída envia um HTTP POST para um serviço web e processa uma resposta de volta. Eles não podem acessar outras APIs, como recuperar a lista ou lista de canais em uma equipe.|

## <a name="creating-actionable-messages"></a>Criar mensagens acionáveis

As placas do conector incluem três botões visíveis no cartão. Cada botão é definido na `potentialAction` propriedade da mensagem usando `ActionCard` ações. Cada `ActionCard` um contém um tipo de entrada; um campo de texto, um batedor de data ou uma lista de várias opções. Cada `ActionCard` ação tem uma ação associada, por exemplo, `HttpPOST` .

Os cartões do conector oferecem suporte a três tipos de ações:

| Ação | Descrição |
| ------- | ----------- |
| `ActionCard` |Apresenta um ou mais tipos de entrada e ações associadas.|
| `HttpPOST` | Envia uma solicitação POST para uma URL. |
| `OpenUri` |  Abre um URI em um navegador ou aplicativo separado, opcionalmente tem como alvo diferentes URIs com base em sistemas operacionais.|

A ação `ActionCard` oferece suporte a três tipos de entrada:

| Tipo de entrada | Descrição |
| ------- | ----------- |
| `TextInput` | Um campo de texto de linha única ou multiline com limite de comprimento opcional. |
| `DateInput` | Um seletor de datas com um seletor de tempo opcional. |
| `MultichoiceInput` | Uma lista especificada de opções, oferecendo uma única seleção ou várias seleções.|

`MultichoiceInput` suporta uma `style` propriedade que controla a exibição de uma lista totalmente expandida. O valor padrão `style` depende do `isMultiSelect` valor.

| `isMultiSelect` valor  | `style` valor padrão  |
| --- | --- |
| `false` ou não especificado  | O estilo padrão é `compact`|
| `true` | O estilo padrão é `expanded` |

> [!NOTE]
> * Digite ambos `"isMultiSelect": true` e , se você quiser que a lista `"style": true` multi-selecionada seja exibida em um estilo compacto.
> * Selecionar `compact` para a `style` propriedade em Teams é o mesmo que selecionar para a propriedade no Microsoft `normal` `style` Outlook.
> * Os webhooks suportam apenas cartões de Office 365 de troca de mensagens e cartões adaptativos.

Para obter todos os outros detalhes sobre as ações do cartão conector, consulte **[Ações](/outlook/actionable-messages/card-reference#actions)** na referência do cartão de mensagem acionável.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Adicionando webhooks de saída ao seu aplicativo

**Cenário**: Pressione as notificações de status de alteração em um servidor de banco de dados de Teams canal para o seu aplicativo.  
**Exemplo**: Você tem um aplicativo de linha de negócios que rastreia todas as operações crud feitas aos registros de funcionários por usuários de RH Teams canal em um Office 365 aluguel.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Crie uma URL no servidor do seu aplicativo para aceitar e processar uma solicitação POST com uma carga útil JSON

Seu serviço recebe mensagens em um esquema padrão de mensagens de serviço de botS Azure. O conector de estrutura de bot é um serviço RESTful que permite que seu serviço processe o intercâmbio de mensagens formatadas JSON através de protocolos HTTPS, conforme documentado na API do [Azure Bot Service](/bot-framework/rest-api/bot-framework-rest-connector-api-reference). Alternativamente, você pode seguir o [Microsoft Bot Framework SDK] para processar e analisar mensagens. Veja também [sobre o serviço de bots do Azure](/azure/bot-service/bot-service-overview-introduction).


Os webhooks de saída são escopo para o `team` nível e são visíveis para todos os membros da equipe. Assim como um bot, os usuários precisam **\@ mencionar** o nome do webhook de saída para invocá-lo no canal.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Crie um método para verificar o token HMAC webhook de saída

#### <a name="hmac-signature-for-testing-with-code-example"></a>Assinatura do HMAC para testes com exemplo de código

Usando exemplo de mensagem de entrada e id: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do cabeçalho de solicitação.

Para garantir que seu serviço esteja recebendo chamadas apenas de clientes Teams reais, Teams fornece um código HMAC no `hmac` cabeçalho HTTP. Sempre incluí o código em seu protocolo de autenticação.

Seu código deve sempre validar a assinatura do HMAC incluída na solicitação:

* Gere o token HMAC a partir do corpo de solicitação da mensagem. Existem bibliotecas padrão para fazer isso na maioria das plataformas (consulte [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js ou veja [Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). Microsoft Teams usa criptografia HMAC padrão SHA256. Você precisa converter o corpo em uma matriz byte em UTF8.
* Calcule o hash a partir do conjunto byte do token de segurança **fornecido pelo Teams** quando você registrou o webhook de saída no Teams cliente]. Consulte [Criar um webhook de saída](#create-an-outgoing-webhook).
* Converta o hash em uma string usando codificação UTF-8.
* Compare o valor de sequência do hash gerado com o valor fornecido na solicitação HTTP.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Crie um método para enviar uma resposta de sucesso ou falha

As respostas de seus webhooks de saída aparecem na mesma cadeia de respostas da mensagem original. Quando o usuário realiza uma consulta, Microsoft Teams emite uma solicitação HTTP síncron sua para o seu serviço e seu código recebe cinco segundos para responder à mensagem antes que a conexão se esvai e termine.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Criar um webhook de saída

1. Selecione a equipe apropriada e escolha **Gerenciar equipe** no menu suspenso (&#8226;&#8226;&#8226;).
1. Escolha a guia **Aplicativos** na barra de navegação.
1. A partir do canto inferior direito da janela selecione **Criar um webhook de saída**.
1. Na janela pop-up resultante complete os campos necessários:

>* **Nome**: O título do webhook e @mention toque
>* **URL de callback**: O ponto final HTTPS que aceita cargas JSON e recebe solicitações POST de Teams
>* **Descrição**: Uma sequência detalhada que aparece no cartão de perfil e no painel do aplicativo em nível de equipe
>* **Imagem do perfil**: Um ícone de aplicativo opcional para o seu webhook
>* Selecione o botão **Criar** no canto inferior direito da janela pop-up e o webhook de saída é adicionado aos canais da equipe atual.
>* A próxima janela de diálogo exibe um token de segurança [HMAC (Message Authentication Code, código de autenticação de mensagem baseado em Hash)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) usado para autenticar chamadas entre Teams e o serviço externo designado.
>* O webhook de saída está disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação do servidor e cliente forem iguais, por exemplo, um aperto de mão do HMAC.

## <a name="code-sample"></a>Exemplo de código
|**Nome da amostra** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Webhooks de saída | Amostras para criar **Bots personalizados** para serem usados em Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

