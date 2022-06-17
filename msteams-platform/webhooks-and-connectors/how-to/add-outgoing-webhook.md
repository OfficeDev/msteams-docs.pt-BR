---
title: Criar um Webhook de Saída
author: laujan
description: Neste módulo, você aprenderá a criar um Webhook de Saída no Microsoft Teams, seus principais recursos e exemplos de código
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: 5c86fd5e3885fd859d02489c81f81aa0502b965a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143281"
---
# <a name="create-outgoing-webhook"></a>Criar Webhook de saída

O Webhook de Saída atua como um bot e pesquisa mensagens em canais usando **@mencionar**. Ele envia notificações para serviços Web externos e responde com mensagens avançadas, que incluem cartões e imagens. Ele ajuda a ignorar o processo de criação de bots por meio do [Microsoft Bot Framework](https://dev.botframework.com/).

<!--- TBD: Edit this article.
* Admonitions/alerts may be overused in this article. Check once.
* An important alert at the end of this table does not make sense. Also, it has a code snippet inside it.
* Some screenshots like teamschannel.png may be redundant. Check once.
* Some headings use title case. We use sentence case for titles.
* Check for markdownlint errors. 
* Try using &nbsp; to add spaces in codeblocks for indentation and remove the hard tabs.
* Table with just a row is not really needed. Provide the content without tabulating it.
--->

## <a name="key-features-of-outgoing-webhook"></a>Principais recursos do Webhook de Saída

A tabela a seguir fornece os recursos e a descrição do Webhook de Saída:

| Recursos | Descrição |
| ------- | ----------- |
| Configuração com escopo| Os webhooks são definidos no nível da equipe. O processo de configuração obrigatório para cada um adiciona um Webhook de Saída. |
| Mensagens reativas| Os usuários devem usar @mencionar para que o webhook receba as mensagens. Atualmente, os usuários só podem enviar mensagens a um Webhook de Saída em canais públicos e não dentro do escopo pessoal ou privado. |
|Troca de mensagens HTTP padrão|As respostas aparecem na mesma cadeia da mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem do Bot Framework. Por exemplo, rich text, imagens, cartões e emojis. Embora os Webhooks de Saída possam utilizar cartões, eles não podem utilizar nenhuma ação de cartão, exceto para `openURL`.|
| Suporte ao método de API do Teams|Webhooks de saída enviam um HTTP POST para um serviço Web e obtém uma resposta. Eles não podem acessar nenhuma outra API, como recuperar a lista de participantes ou a lista de canais em uma equipe.|

## <a name="create-outgoing-webhooks"></a>Criar Webhooks de saída

Criar Webhooks de Saída e adicionar bots personalizados ao Teams.

Para criar um Webhook de Saída, siga estas etapas:

1. Selecione **Teams** no painel esquerdo. A  página do **Teams** é exibida:

    ![Canal do Teams](~/assets/images/teamschannel.png)

1. Na página **Teams**, selecione a equipe necessária para criar um Webhook de Saída e selecione &#8226;&#8226;&#8226;&#8226;. No menu suspenso, selecione **Gerenciar equipe**:

    ![Criar Webhook de saída](~/assets/images/outgoingwebhook1.png)

1. Selecione a guia **Aplicativos** na página do canal:

    ![Criar um Webhook de Saída](~/assets/images/outgoingwebhook2.png)

1. Selecione **Criar um Webhook de Saída**:

    ![Criar Webhooks de saída](~/assets/images/outgoingwebhook3.png)

1. Digite os seguintes detalhes na página **Criar um Webhook de Saída**:

    * **Nome**: o título do webhook e a guia @mencionar.
    * **URL de retorno de chamada**: o ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST do Teams.
    * **Descrição**: uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel do aplicativo no nível da equipe.
    * **Imagem do perfil**: um ícone de aplicativo para seu webhook, que é opcional.

1. Selecione **Criar**. O Webhook de Saída é adicionado ao canal da equipe atual:

    ![criar Webhooks de saída](~/assets/images/outgoingwebhook.png)

Uma caixa de diálogo [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) é exibida. É um token de segurança usado para autenticar chamadas entre o Teams e o serviço externo designado. O token de segurança do HMAC não expira e é exclusivo para cada configuração.

>[!NOTE]
> O Webhook de Saída estará disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação do servidor e do cliente forem iguais. Por exemplo, um handshake HMAC.

O cenário a seguir fornece os detalhes para adicionar um Webhook de Saída:

* Cenário: enviar notificações de status de alteração por push em um servidor de banco de dados de canal do Teams para seu aplicativo.
* Exemplo: Você tem um aplicativo de linha de negócios que rastreia todas as operações CRUD (criar, ler, atualizar e excluir). Essas operações são feitas nos registros de funcionários por usuários de RH do canal do Teams em uma locação do Office 365.

# <a name="url-json-payload"></a>[Carga JSON da URL](#tab/urljsonpayload)

**Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON**

Seu serviço recebe mensagens em um esquema de mensagens padrão do serviço de bot do Azure. O conector do Bot Framework é um serviço RESTful que permite processar o intercâmbio de mensagens formatadas em JSON por meio de protocolos HTTPS, conforme documentado na [API do Serviço de Bot do Azure](/bot-framework/rest-api/bot-framework-rest-connector-api-reference). Como alternativa, você pode seguir o SDK do Microsoft Bot Framework para processar e analisar mensagens. Para obter mais informações, consulte [Visão geral do Serviço de Bot do Azure](/azure/bot-service/bot-service-overview-introduction).

Os Webhooks de saída têm como escopo o nível `team` e são visíveis para todos os membros da equipe. Os usuários precisam **\@mencionar** o nome do Webhook de Saída para invocá-lo no canal.

# <a name="verify-hmac-token"></a>[Verificar o token HMAC](#tab/verifyhmactoken)

**Criar um método para verificar o token HMAC do Webhook de Saída**

Usando o exemplo de mensagem de entrada e ID: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKey/N2bOmlM31zaA=" }.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do cabeçalho da solicitação.

Para garantir que seu serviço esteja recebendo chamadas somente de clientes reais do Teams, o Teams fornece um código HMAC no cabeçalho de autorização http `hmac` acesso. Sempre inclua o código em seu protocolo de autenticação.

Seu código sempre deve validar a assinatura HMAC incluída na solicitação da seguinte maneira:

* Gere o token HMAC do corpo da solicitação da mensagem. Há bibliotecas padrão para fazer isso na maioria das plataformas, como o [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) para Node.js e exemplo de webhook do [Teams](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) para C\#. O Microsoft Teams usa criptografia HMAC SHA256 padrão. Você deve converter o corpo em uma matriz de bytes em UTF8.
* Compute o hash da matriz de bytes do token de segurança fornecido pelo Teams quando você registrou o Webhook de Saída no cliente do Teams. Consulte [criar um webhook de saída](#create-outgoing-webhook).
* Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.
* Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.

# <a name="method-to-respond"></a>[Método para responder](#tab/methodtorespond)

**Criar um método para enviar uma resposta de êxito ou falha**

As respostas de seus Webhooks de Saída aparecem na mesma cadeia de resposta que a mensagem original. Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para seu serviço e seu código obtém cinco segundos para responder à mensagem antes que a conexão termine e termine.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

---

> [!NOTE]
>
> * Você pode enviar mensagens de texto, Cartão Hero e Cartão Adaptável como anexo com o Webhook de Saída.
> * Os cartões dão suporte à formatação. Para obter mais informações, [formatar cartões com markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).
> * O Cartão Adaptável em Webhooks de Saída suporta apenas `openURL` ações de cartão.

Os códigos a seguir são exemplos de uma resposta de Cartão Adaptável:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
string content = await this.Request.Content.ReadAsStringAsync();
Activity incomingActivity = JsonConvert.DeserializeObject<Activity>(content);

var Card = new AdaptiveCard(new AdaptiveSchemaVersion("1.4"))
{
    Body = new List<AdaptiveElement>()
    {
        new AdaptiveTextBlock(){Text= $"Request sent by: {incomingActivity.From.Name}"},
        new AdaptiveImage(){Url=new Uri("https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6")},
        new AdaptiveTextBlock(){Text="Sample image for Adaptive Card.."}
    }
};

var attachment = new Attachment()
{
    ContentType = AdaptiveCard.ContentType,
    Content = Card
};

var sampleResponseActivity = new Activity
{
    Attachments = new [] { attachment }
};

return sampleResponseActivity;
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
var receivedMsg = JSON.parse(payload);
var responseMsg = JSON.stringify({
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "contentUrl": null,
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: " + receivedMsg.from.name
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card."
                    }
                ]
            },
            "name": null,
            "thumbnailUrl": null
        }
    ]
});
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
 "type": "message",
 "attachments": [
  {
   "contentType": "application/vnd.microsoft.card.adaptive",
   "content": {
    "type": "AdaptiveCard",
    "version": "1.4",
    "body": [
     {
      "type": "TextBlock",
      "text": "Request sent by: Megan"
     },
     {
      "type": "Image",
      "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
     },
     {
      "type": "TextBlock",
      "text": "Sample image for Adaptive Card.."
     }
    ]
   }
  }
 ]
}
```

---

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Webhooks de Saída | Exemplos de criação de bots personalizados para uso no Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [passo a passo para](../../sbs-outgoing-webhooks.yml) webhooks de saída no Teams.

## <a name="see-also"></a>Confira também

* [Criar um webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
