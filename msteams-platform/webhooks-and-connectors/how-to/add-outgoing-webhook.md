---
title: Adicionar bots personalizados ao Microsoft Teams com WebHooks de saída
author: laujan
description: como adicionar um webhook de saída
keywords: guias do Microsoft Teams saída de webhook *
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 61dc8441795925b53e5c8459f9c6eed5a28856e1
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552462"
---
# <a name="add-custom-bots-to-microsoft-teams-with-outgoing-webhooks"></a>Adicionar bots personalizados ao Microsoft Teams com WebHooks de saída

## <a name="what-are-outgoing-webhooks-in-teams"></a>O que são WebHooks de saída no Microsoft Teams?

Os WebHooks são uma ótima maneira de a integração do Microsoft Teams com aplicativos externos. Um webhook é essencialmente uma solicitação POST enviada para uma URL de retorno de chamada. No Teams, os WebHooks de saída fornecem uma maneira simples de permitir que os usuários enviem mensagens para o seu serviço Web sem precisar passar por todo o processo de criação de bots por meio da [Microsoft bot Framework](https://dev.botframework.com/). Os WebHooks de saída postam dados do teams para qualquer serviço escolhido capaz de aceitar uma carga JSON. Após um webhook de saída ser adicionado a uma equipe, ele atua como bot, ouvindo canais para mensagens usando **\@ menção**, enviando notificações para serviços Web externos e respondendo com mensagens avançadas que podem incluir cartões e imagens.

## <a name="outgoing-webhook-key-features"></a>Recursos de chave de webhook de saída

| Recurso | Descrição |
| ------- | ----------- |
| Configuração com escopo| Os WebHooks têm escopo no nível da equipe. Você precisará passar pelo processo de instalação para cada equipe à qual deseja adicionar o webhook de saída. |
| Mensagens reativas| Os usuários devem usar @mention para o webhook para receber mensagens. Atualmente, os usuários só podem enviar uma mensagem para um webhook de saída em canais públicos e não dentro do escopo pessoal ou privado |
|Troca de mensagens HTTP padrão|As respostas aparecerão na mesma cadeia da mensagem de solicitação original e podem incluir qualquer conteúdo de mensagem da estrutura de bot (Rich Text, imagens, cartões e emojis). **Observação**: embora os WebHooks de saída possam usar cartões, eles não podem usar nenhuma ação de cartão, exceto para `openURL` .|
| Suporte ao método de API do teams|No Teams, os WebHooks de saída enviam um HTTP POST para um serviço Web e processam uma resposta de retorno. Eles não podem acessar nenhuma outra API como recuperar a lista ou a lista de canais em uma equipe.|

## <a name="adding-outgoing-webhook-processing-to-your-app"></a>Adicionando processamento de webhook de saída ao seu aplicativo

**Cenário**: enviar notificações de status de alteração em um servidor de banco de dados de canal do teams para seu aplicativo.  
**Exemplo**: você tem um aplicativo de linha de negócios que controla todas as operações CRUD feitas a registros de funcionários por usuários de canal de RH de canal de equipe em uma locação do Office 365.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. criar uma URL no servidor de seu aplicativo para aceitar e processar uma solicitação POST com uma carga JSON

Seu serviço receberá mensagens no esquema de mensagens do serviço bot do Azure padrão. O conector da estrutura de bot é um serviço RESTful que permite que seu serviço processe o intercâmbio de mensagens formatadas por JSON por meio de protocolos HTTPS, conforme documentado na [API do serviço de bot do Azure](/bot-framework/rest-api/bot-framework-rest-connector-api-reference). Como alternativa, você pode seguir o [Microsoft bot Framework SDK] para processar e analisar mensagens. *Consulte também*  [sobre o serviço de bot do Azure](/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).

Os WebHooks de saída têm escopo para o `team` nível e são visíveis para todos os membros da equipe. Assim como um bot, os usuários precisam **\@ mencionar** o nome do webhook de saída para chamá-lo no canal.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Crie um método para verificar o token HMAC de saída de webhook

#### <a name="hmac-signature-for-testing-with-code-example"></a>Assinatura HMAC para teste com o exemplo de código

Usando um exemplo de ID e mensagem de entrada: "contoso" de SigningKeyDictionary de {"contoso", "vqF0En + Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA ="}.

Use o valor "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs + mO41mPL + R1e1U =" na autorização do cabeçalho da solicitação.

Para garantir que o serviço esteja recebendo chamadas apenas de clientes do Microsoft Teams, o Microsoft Teams fornece um código HMAC no `hmac` cabeçalho HTTP que deve sempre ser incluído no seu protocolo de autenticação.

O código deve sempre validar a assinatura HMAC incluída na solicitação:

* *Gere* o token HMAC do corpo da solicitação da mensagem. Há bibliotecas padrão para fazer isso na maioria das plataformas (*consulte* [crypto](https://nodejs.org/api/crypto.html#crypto_crypto) para Node.js ou  *consulte* [Teams webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). O Microsoft Teams usa a criptografia HMAC de SHA256 padrão. Você precisará converter o corpo em uma matriz de bytes em UTF8.
* *Compute* o hash da matriz de bytes do token de segurança **fornecido pelo Microsoft Teams** quando você registrou o webhook de saída no cliente do teams]. *Confira* [criar um webhook de saída](#create-an-outgoing-webhook), abaixo.
* *Converta* o hash em uma cadeia de caracteres usando a codificação UTF-8.
* *Compare* o valor da cadeia de caracteres do hash gerado com o valor fornecido na solicitação HTTP.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. criar um método para enviar uma resposta de êxito ou falha

As respostas do webhook de saída aparecerão na mesma cadeia de resposta da mensagem original. Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para o seu serviço e seu código terá 5 segundos para responder à mensagem antes que o tempo limite da conexão expire e seja encerrado.

### <a name="example-response"></a>Resposta de exemplo

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Criar um webhook de saída

1. Selecione a equipe apropriada e selecione **Gerenciar equipe** no menu suspenso (&#8226;&#8226;&#8226;).
1. Escolha a guia **aplicativos** na barra de navegação.
1. No canto inferior direito da janela, selecione **criar um webhook de saída**.
1. Na janela pop-up resultante, preencha os campos obrigatórios:

>* **Nome** -o título do webhook e o @mention toque.
>* **URL de retorno de chamada** : o ponto de extremidade HTTPS que aceita cargas JSON e receberá solicitações post do teams.
>* **Descrição** -uma cadeia de caracteres detalhada que aparecerá no cartão de perfil e no painel de aplicativos de nível de equipe.
>* **Imagem de perfil** (opcional) um ícone de aplicativo para seu webhook.
>* Selecione o botão **criar** no canto inferior direito da janela pop-up e o webhook de saída será adicionado aos canais da equipe atual.
>* A próxima janela de diálogo exibirá um token [de segurança HMAC (código de autenticação de mensagens baseado em hash)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) que será usado para autenticar chamadas entre o Teams e o serviço externo designado.
>* Se a URL for válida e os tokens de autenticação de servidor e cliente forem iguais (ou seja, um handshake HMAC), o webhook de saída estará disponível para os usuários da equipe.

## <a name="code-samples"></a>Exemplos de código

Você pode exibir exemplos de código de webhook de saída no GitHub:

### <a name="nodejs"></a>Node.js

[OfficeDev/msteams-amostras-saída-webhook-NodeJS](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs)

### <a name="c"></a>Unidade\#

[OfficeDev/Microsoft-Teams-Sample-saída-webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook)
