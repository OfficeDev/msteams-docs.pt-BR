---
title: Enviar e receber arquivos por meio do bot
description: Descreve como enviar e receber arquivos por meio do bot
keywords: envio de arquivos de bots do Teams
ms.date: 05/20/2019
ms.topic: how-to
ms.openlocfilehash: 1699b9339bd6a49194240130d16795e8febcb76e
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037050"
---
# <a name="send-and-receive-files-through-the-bot"></a>Enviar e receber arquivos por meio do bot

> [!IMPORTANT]
> Os artigos deste documento são baseados no SDK da Estrutura de Bot v4.

Há duas maneiras de enviar e receber arquivos de um bot:

* **Usando as APIs do Microsoft Graph:** Esse método funciona para bots em todos os escopos do Microsoft Teams:
  * `personal`
  * `channel`
  * `groupchat`

* **Usando as APIs de bot do Teams:** Esses arquivos só são suportados em `personal` contexto.

## <a name="using-the-graph-apis"></a>Usando as APIs do Graph

Postar mensagens com anexos de cartão que se referem a arquivos existentes do SharePoint, usando as APIs do Graph para [OneDrive e SharePoint.](/onedrive/developer/rest-api/) Para usar as APIs do Graph, obtenha acesso a um dos seguintes por meio do fluxo de autorização padrão do OAuth 2.0:
* Pasta e arquivos do OneDrive de `personal` `groupchat` um usuário.
* Os arquivos no canal de uma equipe para `channel` arquivos.

As APIs do Graph funcionam em todos os escopos do Teams.

## <a name="using-the-teams-bot-apis"></a>Usando as APIs de bot do Teams

> [!NOTE]
> As APIs de bot do Teams funcionam somente no `personal` contexto. Eles não funcionam no `channel` contexto `groupchat` ou no contexto.

Usando as APIs do Teams, o bot pode enviar e receber arquivos diretamente com os usuários no contexto, também `personal` conhecido como chats pessoais. Implemente recursos, como relatórios de despesas, reconhecimento de imagem, arquivamento de arquivos e assinaturas eletrônicas envolvendo a edição do conteúdo do arquivo. Os arquivos compartilhados no Teams normalmente aparecem como cartões e permitem a exibição rica no aplicativo.

As seções a seguir descrevem como enviar conteúdo de arquivo como uma interação direta do usuário, como enviar uma mensagem. Essa API é fornecida como parte da plataforma de bot do Teams.

### <a name="configuring-the-bot-to-support-files"></a>Configurando o bot para dar suporte a arquivos

Para enviar e receber arquivos no bot, de definida `supportsFiles` a propriedade no manifesto como `true` . Essa propriedade é descrita na seção [bots](~/resources/schema/manifest-schema.md#bots) da referência do manifesto.

A definição tem esta aparência, `"supportsFiles": true` . Se o bot não `supportsFiles` habilitar, os recursos listados nesta seção não funcionarão.

### <a name="receiving-files-in-personal-chat"></a>Recebendo arquivos no chat pessoal

Quando um usuário envia um arquivo para o bot, o arquivo é carregado pela primeira vez no armazenamento do OneDrive for Business do usuário. Em seguida, o bot recebe uma atividade de mensagem notificando o usuário sobre o carregamento do usuário. A atividade contém metadados de arquivo, como seu nome e a URL de conteúdo. O usuário pode ler diretamente dessa URL para buscar seu conteúdo binário.

#### <a name="message-activity-with-file-attachment-example"></a>Exemplo de atividade de mensagem com anexo de arquivo

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.file.download.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "downloadUrl" : "https://download.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C9D",
      "fileType": "txt",
      "etag": "123"
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Finalidade |
| --- | --- |
| `downloadUrl` | URL do OneDrive para buscar o conteúdo do arquivo. O usuário pode emitir uma `HTTP GET` diretamente dessa URL. |
| `uniqueId` | ID exclusiva do arquivo. Essa é a ID do item de unidade do OneDrive, caso o usuário envie um arquivo para o bot. |
| `fileType` | Tipo de arquivo, como .pdf ou .docx. |

Como prática prática, confirme o carregamento do arquivo enviando uma mensagem de volta para o usuário.

### <a name="uploading-files-to-personal-chat"></a>Carregando arquivos para chat pessoal

As etapas a seguir são necessárias para carregar um arquivo para um usuário:

1. Envie uma mensagem para o usuário solicitando permissão para gravar o arquivo. Essa mensagem deve conter `FileConsentCard` um anexo com o nome do arquivo a ser carregado.
2. Se o usuário aceitar o download do arquivo, o bot receberá uma atividade de invocação com uma URL de local.
3. Para transferir o arquivo, o bot executa uma `HTTP POST` ação diretamente para a URL de local fornecida.
4. Opcionalmente, remova o cartão de consentimento original se não quiser que o usuário aceite uploads posteriores do mesmo arquivo.

#### <a name="message-requesting-permission-to-upload"></a>Mensagem solicitando permissão para carregar

A seguinte mensagem da área de trabalho contém um objeto anexo simples solicitando permissão do usuário para carregar o arquivo:

![Cartão de consentimento solicitando permissão do usuário para carregar o arquivo](../../assets/images/bots/bot-file-consent-card.png)

A seguinte mensagem móvel contém um objeto anexo solicitando permissão do usuário para carregar o arquivo:

![Cartão de consentimento solicitando permissão do usuário para carregar o arquivo no celular](../../assets/images/bots/mobile-bot-file-consent-card.png)

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.consent",
    "name": "file_example.txt",
    "content": {
      "description": "<Purpose of the file, such as: this is your monthly expense report>",
      "sizeInBytes": 1029393,
      "acceptContext": {
      },
      "declineContext": {
      }
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Finalidade |
| --- | --- |
| `description` | Descreve a finalidade do arquivo ou resume seu conteúdo. |
| `sizeInBytes` | Fornece ao usuário uma estimativa do tamanho do arquivo e da quantidade de espaço que ele ocupa no OneDrive. |
| `acceptContext` | Contexto adicional que é transmitido silenciosamente para o bot quando o usuário aceita o arquivo. |
| `declineContext` | Contexto adicional que é transmitido silenciosamente para o bot quando o usuário recusa o arquivo. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Invocar atividade quando o usuário aceita o arquivo

Uma atividade de invocação é enviada para o bot se e quando o usuário aceita o arquivo. Ele contém a URL de espaço reservado do OneDrive for Business para a qual o bot pode emitir um arquivo `PUT` para transferir o conteúdo do arquivo. Para saber mais sobre como carregar para a URL do OneDrive, confira [Carregar bytes na sessão de carregamento.](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session)

O exemplo a seguir mostra uma versão concisa da atividade de invocação que o bot recebe:

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "accept",
    "context": {
    },
    "uploadInfo": {
      "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
      "name": "file_example.txt",
      "uploadUrl": "https://upload.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
      "etag": "123"
    }
  }
}
```

Da mesma forma, se o usuário recusar o arquivo, o bot receberá o seguinte evento com o mesmo nome de atividade geral:

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "decline",
    "context": {
    }
  }
}
```

### <a name="notifying-the-user-about-an-uploaded-file"></a>Notificar o usuário sobre um arquivo carregado

Depois de carregar um arquivo no OneDrive do usuário, envie uma mensagem de confirmação para o usuário. A mensagem deve conter o seguinte anexo que o usuário pode selecionar, para visualizar ou `FileCard` abri-la no OneDrive, ou baixar localmente:

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
    }
  }]
}
```

A tabela a seguir descreve as propriedades de conteúdo do anexo:

| Propriedade | Finalidade |
| --- | --- |
| `uniqueId` | ID do item de unidade do OneDrive ou do SharePoint. |
| `fileType` | Tipo de arquivo, como .pdf ou .docx. |

### <a name="basic-example-in-c"></a>Exemplo básico em C #

O exemplo a seguir mostra como lidar com carregamentos de arquivos e enviar solicitações de consentimento de arquivo na caixa de diálogo do bot:

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    string filename = "teams-logo.png";
    string filePath = Path.Combine("Files", filename);
    long fileSize = new FileInfo(filePath).Length;
    await SendFileCardAsync(turnContext, filename, fileSize, cancellationToken);
}

private async Task SendFileCardAsync(ITurnContext turnContext, string filename, long filesize, CancellationToken cancellationToken)
{
    var consentContext = new Dictionary<string, string>
    {
        { "filename", filename 
        },
    };

    var fileCard = new FileConsentCard
    {
        Description = "This is the file I want to send you",
        SizeInBytes = filesize,
        AcceptContext = consentContext,
        DeclineContext = consentContext,
    };

    var asAttachment = new Attachment
    {
        Content = fileCard,
        ContentType = FileConsentCard.ContentType,
        Name = filename,
    };

    var replyActivity = turnContext.Activity.CreateReply();
    replyActivity.Attachments = new List<Attachment>() { asAttachment 
    };
    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}

protected override async Task OnTeamsFileConsentAcceptAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    try
    {
        JToken context = JObject.FromObject(fileConsentCardResponse.Context);

        string filePath = Path.Combine("Files", context["filename"].ToString());
        long fileSize = new FileInfo(filePath).Length;
        var client = _clientFactory.CreateClient();
        using (var fileStream = File.OpenRead(filePath))
        {
            var fileContent = new StreamContent(fileStream);
            fileContent.Headers.ContentLength = fileSize;
            fileContent.Headers.ContentRange = new ContentRangeHeaderValue(0, fileSize - 1, fileSize);
            await client.PutAsync(fileConsentCardResponse.UploadInfo.UploadUrl, fileContent, cancellationToken);
        }

        await FileUploadCompletedAsync(turnContext, fileConsentCardResponse, cancellationToken);
    }
    catch (Exception e)
    {
        await FileUploadFailedAsync(turnContext, e.ToString(), cancellationToken);
    }
}

protected override async Task OnTeamsFileConsentDeclineAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    JToken context = JObject.FromObject(fileConsentCardResponse.Context);

    var reply = MessageFactory.Text($"Declined. We won't upload file <b>{context["filename"]}</b>.");
    reply.TextFormat = "xml";
    await turnContext.SendActivityAsync(reply, cancellationToken);
}

private async Task FileUploadCompletedAsync(ITurnContext turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    var downloadCard = new FileInfoCard
    {
        UniqueId = fileConsentCardResponse.UploadInfo.UniqueId,
        FileType = fileConsentCardResponse.UploadInfo.FileType,
    };

    var asAttachment = new Attachment
    {
        Content = downloadCard,
        ContentType = FileInfoCard.ContentType,
        Name = fileConsentCardResponse.UploadInfo.Name,
        ContentUrl = fileConsentCardResponse.UploadInfo.ContentUrl,
    };

    var reply = MessageFactory.Text($"<b>File uploaded.</b> Your file <b>{fileConsentCardResponse.UploadInfo.Name}</b> is ready to download");
    reply.TextFormat = "xml";
    reply.Attachments = new List<Attachment> { asAttachment 
    };

    await turnContext.SendActivityAsync(reply, cancellationToken);
}

private async Task FileUploadFailedAsync(ITurnContext turnContext, string error, CancellationToken cancellationToken)
{
    var reply = MessageFactory.Text($"<b>File upload failed.</b> Error: <pre>{error}</pre>");
    reply.TextFormat = "xml";
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
```
