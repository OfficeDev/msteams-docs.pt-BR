---
title: Criar um Webhook de Saída
author: laujan
description: descreve como criar um Webhook de Saída
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
keywords: guias do teams webhook de saída mensagem ativas verificar webhook
ms.openlocfilehash: 2039ffdbc307b266e7bc0f93c1638450a8be9037
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155155"
---
# <a name="create-outgoing-webhook"></a>Criar Webhook de saída

O Webhook de saída age como um bot e pesquisa mensagens em canais usando **@mention**. Ele envia notificações para serviços Web externos e responde com mensagens ricas, que incluem cartões e imagens. Ele ajuda a ignorar o processo de criação de bots por meio do [Microsoft Bot Framework](https://dev.botframework.com/).

## <a name="key-features-of-outgoing-webhook"></a>Principais recursos do Webhook de Saída

A tabela a seguir fornece os recursos e a descrição dos Webhooks de saída:

| Recursos | Descrição |
| ------- | ----------- |
| Configuração com escopo| Os webhooks têm escopo no nível da equipe. O processo de configuração obrigatório para cada um adiciona um Webhook de saída. |
| Mensagens reativas| Os usuários devem usar @mention webhook para receber mensagens. Atualmente, os usuários só podem enviar um Webhook de Saída em canais públicos e não no escopo pessoal ou privado. |
|Troca de mensagens HTTP padrão|As respostas aparecem na mesma cadeia que a mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem da Estrutura de Bot, por exemplo, texto rico, imagens, cartões e emojis. Embora os Webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto `openURL` por .|
| Teams Suporte ao método API|Webhooks de saída envia um HTTP POST para um serviço Web e obtém uma resposta. Eles não podem acessar outras APIs, como recuperar a lista ou a lista de canais em uma equipe.|

## <a name="create-outgoing-webhooks"></a>Criar Webhooks de saída

Crie Webhooks de saída e adicione bots personalizados Teams.

**Para criar um Webhook de Saída**

1. Selecione **Teams** no painel esquerdo. A **Teams** página é exibida:

    ![Canal do Teams](~/assets/images/teamschannel.png)

1. Na página **Teams,** selecione a equipe necessária para criar um Webhook de saída e selecione o &#8226;&#8226;&#8226;. No menu suspenso, selecione **Gerenciar equipe**:

    ![Criar Webhook de saída](~/assets/images/outgoingwebhook1.png)

1. Selecione a **guia Aplicativos** na página do canal:

    ![Criar um Webhook de Saída](~/assets/images/outgoingwebhook2.png)

1. Selecione **Criar um Webhook de Saída:**

    ![Criar Webhooks de saída](~/assets/images/outgoingwebhook3.png)

1. Digite os seguintes detalhes na página **Criar um Webhook de** Saída:

    * **Nome**: o título de webhook e @mention guia.
    * **URL de retorno** de chamada : o ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST de Teams.
    * **Descrição**: uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel de aplicativos no nível da equipe.
    * **Imagem do** perfil : um ícone de aplicativo para seu webhook, que é opcional.

1. Selecione **Criar**. O Webhook de saída é adicionado ao canal atual da equipe:

    ![criar Webhook de saída](~/assets/images/outgoingwebhook.png)

Uma [caixa de diálogo HMAC (Código](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) de Autenticação de Mensagem baseado em hash) é exibida. É um token de segurança usado para autenticar chamadas entre Teams e o serviço externo designado.

>[!NOTE]
> O Webhook de Saída está disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação do servidor e do cliente são iguais. Por exemplo, um handshake HMAC.

O cenário a seguir fornece os detalhes para adicionar um Webhook de saída:

* Cenário: Push change status notifications on a Teams channel database server to your app.
* Exemplo: você tem um aplicativo de linha de negócios que rastreia todas as operações CRUD, como criar, ler, atualizar e excluir. Essas operações são feitas nos registros dos funcionários por usuários de RH Teams canal em um Office 365 de terceiros.

# <a name="url-json-payload"></a>[Carga JSON de URL](#tab/urljsonpayload)
**Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON**

Seu serviço recebe mensagens em um esquema de mensagens de serviço de bot padrão do Azure. O conector da Estrutura de Bots é um serviço RESTful que permite processar o intercâmbio de mensagens formatadas JSON por meio de protocolos HTTPS, conforme documentado na API de Serviço de Bot do [Azure.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) Como alternativa, você pode seguir o Microsoft Bot Framework SDK para processar e analisar mensagens. Para obter mais informações, consulte [overview of Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).

Os Webhooks de saída são limitados ao `team` nível e ficam visíveis para todos os membros da equipe. Os usuários precisam **\@ mencionar** o nome do Webhook de Saída para invocá-lo no canal.

# <a name="verify-hmac-token"></a>[Verificar token HMAC](#tab/verifyhmactoken)
**Criar um método para verificar o token HMAC do Webhook de Saída**

Usando exemplo de mensagem de entrada e ID: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do header de solicitação.

Para garantir que seu serviço receba chamadas somente de clientes Teams reais, o Teams fornece um código HMAC no cabeçalho de autorização `hmac` HTTP. Sempre inclua o código em seu protocolo de autenticação.

Seu código deve sempre validar a assinatura HMAC incluída na solicitação da seguinte forma:

* Gere o token HMAC do corpo da solicitação da mensagem. Há bibliotecas padrão para fazer isso na maioria das plataformas, como [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js e [Teams webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) para C \# ). Microsoft Teams usa criptografia HMAC SHA256 padrão. Você deve converter o corpo em uma matriz de byte em UTF8.
* Calcule o hash da matriz de byte do token de segurança fornecido pelo Teams quando você registrou o Webhook de Saída no cliente Teams. Consulte [create an Outgoing Webhook](#create-outgoing-webhook).
* Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.
* Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.

# <a name="method-to-respond"></a>[Método para responder](#tab/methodtorespond)
**Criar um método para enviar uma resposta de sucesso ou falha**

As respostas de seus Webhooks de saída aparecem na mesma cadeia de resposta que a mensagem original. Quando o usuário executa uma consulta, Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço e seu código obtém cinco segundos para responder à mensagem antes que a conexão seja encerrada e terminada.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```
---

> [!NOTE]
> * Você pode enviar mensagens de texto e cartão adaptável como anexo com o Webhook de saída.
> * Os cartões suportam formatação. Para obter mais informações, consulte [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).

Os códigos a seguir são exemplos de uma resposta do Cartão Adaptável:

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

* * *

## <a name="code-sample"></a>Exemplo de código

|**Nome do exemplo** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Webhooks de saída | Exemplos para criar bots personalizados a serem usados em Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

## <a name="see-also"></a>Confira também
* [Criar um Webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
