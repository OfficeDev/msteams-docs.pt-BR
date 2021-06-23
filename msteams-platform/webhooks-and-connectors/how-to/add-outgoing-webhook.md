---
title: Adicionar bots personalizados para Microsoft Teams com webhooks de saída
description: descreve como adicionar um webhook de saída
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: guias do teams webhook de saída mensagem ativas verificar webhook
ms.openlocfilehash: 2fac6f42e27a4c8cb3d079ea281d458a4dfe41ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069180"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Adicionar bots personalizados para Teams com webhooks de saída

## <a name="outgoing-webhooks-in-teams"></a>Webhooks de saída em Teams

Webhooks são uma maneira proeminente de Teams se integrar com aplicativos externos. Um webhook é essencialmente uma solicitação POST enviada para uma URL de retorno de chamada. Webhooks de saída permitem que os usuários enviem mensagens para seu serviço Web sem passar pelo processo completo de criação de bots por meio do [Microsoft Bot Framework](https://dev.botframework.com/).

O webhook de saída envia dados de Teams para qualquer serviço escolhido capaz de aceitar uma carga JSON. Depois de adicionar os webhooks de saída a uma equipe, ele age como um bot e procura mensagens em canais usando **\@ menção**. Ele envia notificações para serviços Web externos e responde com mensagens ricas, que incluem cartões e imagens.

## <a name="outgoing-webhook-key-features"></a>Recursos de chave de webhook de saída

| Recurso | Descrição |
| ------- | ----------- |
| Configuração com escopo| Os webhooks têm escopo no nível da equipe. Você deve passar pelo processo de instalação de cada equipe onde deseja adicionar seu webhook de saída. |
| Mensagens reativas| Os usuários devem usar @mention webhook para receber mensagens. Atualmente, os usuários só podem enviar um webhook de saída em canais públicos e não no escopo pessoal ou privado. |
|Troca de mensagens HTTP padrão|As respostas aparecem na mesma cadeia que a mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem de estrutura de bot, por exemplo, texto rico, imagens, cartões e emojis. Embora os webhooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto `openURL` por .|
| Teams Suporte ao método API|O webhook de saída envia um HTTP POST para um serviço Web e processa uma resposta de volta. Eles não podem acessar outras APIs, como recuperar a lista ou a lista de canais em uma equipe.|

## <a name="creating-actionable-messages"></a>Criar mensagens acionáveis

Os cartões de conector incluem três botões visíveis no cartão. Cada botão é definido na `potentialAction` propriedade da mensagem usando `ActionCard` ações. Cada `ActionCard` um contém um tipo de entrada; um campo de texto, um selador de datas ou uma lista de várias opções. Cada `ActionCard` ação tem uma ação associada, por exemplo, `HttpPOST` .

Os cartões do conector oferecem suporte a três tipos de ações:

| Ação | Descrição |
| ------- | ----------- |
| `ActionCard` |Apresenta um ou mais tipos de entrada e ações associadas.|
| `HttpPOST` | Envia uma solicitação POST a uma URL. |
| `OpenUri` |  Abre um URI em um navegador ou aplicativo separado, opcionalmente direciona URIs diferentes com base em sistemas operacionais.|

A ação `ActionCard` oferece suporte a três tipos de entrada:

| Tipo de entrada | Descrição |
| ------- | ----------- |
| `TextInput` | Um campo de texto de linha única ou multilinha com um limite de comprimento opcional. |
| `DateInput` | Um seletor de datas com um seletor de hora opcional. |
| `MultichoiceInput` | Uma lista especificada de opções, oferecendo uma única seleção ou várias seleções.|

`MultichoiceInput` suporta uma `style` propriedade que controla a exibição de uma lista totalmente expandida. O valor padrão de `style` depende do `isMultiSelect` valor.

| `isMultiSelect` value  | `style` valor padrão  |
| --- | --- |
| `false` ou não especificado  | O estilo padrão é `compact`|
| `true` | O estilo padrão é `expanded` |

> [!NOTE]
> * Insira ambos e , se você quiser que a lista `"isMultiSelect": true` `"style": true` multiseleccionada seja exibida em um estilo compacto.
> * Selecionar para a propriedade no Teams é o mesmo que `compact` selecionar para a propriedade no Microsoft `style` `normal` `style` Outlook.
> * Os Webhooks suportam apenas Office 365 de retorno de mensagens e cartões adaptáveis.

Para obter todos os outros detalhes sobre ações de cartão de conector, consulte **[Actions](/outlook/actionable-messages/card-reference#actions)** na referência do cartão de mensagem a actionable.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Adicionar webhooks de saída ao seu aplicativo

**Cenário**: Notificações de status de alteração por push em um servidor de banco de dados Teams canal para seu aplicativo.  
**Exemplo:** você tem um aplicativo de linha de negócios que rastreia todas as operações CRU Teams D feitas em registros de funcionários por usuários de RH de canal em uma Office 365 de terceiros.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Crie uma URL no servidor do aplicativo para aceitar e processar uma solicitação POST com uma carga JSON

Seu serviço recebe mensagens em um esquema de mensagens de serviço de bot padrão do Azure. O conector de estrutura de bot é um serviço RESTful que capacita seu serviço a processar o intercâmbio de mensagens formatadas JSON por meio de protocolos HTTPS, conforme documentado na API de Serviço de Bot do [Azure.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) Como alternativa, você pode seguir o [Microsoft Bot Framework SDK] para processar e analisar mensagens. Consulte também [Sobre o serviço bot do Azure.](/azure/bot-service/bot-service-overview-introduction)


Os webhooks de saída têm escopo para o `team` nível e são visíveis para todos os membros da equipe. Assim como um bot, os usuários precisam **\@ mencionar** o nome do webhook de saída para invocá-lo no canal.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Crie um método para verificar o token HMAC de webhook de saída

#### <a name="hmac-signature-for-testing-with-code-example"></a>Assinatura HMAC para teste com exemplo de código

Usando exemplo de mensagem de entrada e id: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" na autorização do header de solicitação.

Para garantir que seu serviço receba chamadas somente de clientes Teams reais, o Teams fornece um código HMAC no `hmac` cabeçalho HTTP. Sempre incluiu o código em seu protocolo de autenticação.

Seu código deve sempre validar a assinatura HMAC incluída na solicitação:

* Gere o token HMAC do corpo da solicitação da mensagem. Há bibliotecas padrão para fazer isso na maioria das plataformas (consulte [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js ou [consulte Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). Microsoft Teams usa criptografia HMAC SHA256 padrão. Você precisa converter o corpo em uma matriz de byte em UTF8.
* Compute o hash da matriz de byte do token de segurança fornecido pelo **Teams** quando você registrou o webhook de saída no cliente Teams]. Consulte [Criar um webhook de saída.](#create-an-outgoing-webhook)
* Converta o hash em uma cadeia de caracteres usando a codificação UTF-8.
* Compare o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Crie um método para enviar uma resposta de sucesso ou falha

As respostas de seus webhooks de saída aparecem na mesma cadeia de resposta que a mensagem original. Quando o usuário executa uma consulta, Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço e seu código obtém cinco segundos para responder à mensagem antes que a conexão seja encerrada e terminada.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

> [!NOTE]
> * Você pode enviar mensagens de texto e cartão adaptável como anexo com webhook de saída.
> * Os cartões suportam formatação. Para obter mais informações, consulte [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown).

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

## <a name="create-an-outgoing-webhook"></a>Criar um webhook de saída

1. Selecione a equipe apropriada e escolha **Gerenciar equipe** no menu suspenso (&#8226;&#8226;&#8226;) suspenso.
1. Escolha a **guia Aplicativos** na barra de navegação.
1. No canto inferior direito da janela, selecione **Criar um webhook de saída.**
1. Na janela pop-up resultante, conclua os campos necessários:

>* **Nome**: o título de webhook e @mention toque
>* **URL de retorno** de chamada : o ponto de extremidade HTTPS que aceita cargas JSON e recebe solicitações POST de Teams
>* **Descrição**: uma cadeia de caracteres detalhada que aparece no cartão de perfil e no painel de aplicativos no nível da equipe
>* **Imagem do** perfil : um ícone de aplicativo opcional para seu webhook
>* Selecione o **botão Criar** no canto inferior direito da janela pop-up e o webhook de saída é adicionado aos canais da equipe atual.
>* A próxima janela de diálogo exibe um token de segurança [HMAC (Código](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) de Autenticação de Mensagem) baseado em hash que é usado para autenticar chamadas entre Teams e o serviço externo designado.
>* O webhook de saída está disponível para os usuários da equipe, somente se a URL for válida e os tokens de autenticação de servidor e cliente são iguais, por exemplo, um aperto de mão HMAC.

## <a name="code-sample"></a>Exemplo de código
|**Exemplo de nome** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Webhooks de saída | Exemplos para criar **Bots Personalizados** a serem usados em Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

